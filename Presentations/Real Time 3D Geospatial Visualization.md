# 0. Real Time 3D Geospatial Visualization (in the web)
- Interesting but why/how/when?

---

<!--toc:start-->
- [0. Real Time 3D Geospatial Visualization (in the web)](#0-real-time-3d-geospatial-visualization-in-the-web)
- [1. History, demand, approach](#1-history-demand-approach)
  - [1.1 It started with 2D GIS (Geographic Information System)](#11-it-started-with-2d-gis-geographic-information-system)
  - [1.2 What was the demand (Limitations of 2D GIS's / What it couldn't do)](#12-what-was-the-demand-limitations-of-2d-giss-what-it-couldnt-do)
    - [1.2.1 First implementation](#121-first-implementation)
  - [1.3 The turning point](#13-the-turning-point)
  - [1.4 Data Explosion](#14-data-explosion)
- [2. Technicalities](#2-technicalities)
  - [2.1 Main issue](#21-main-issue)
  - [2.2 Break it all](#22-break-it-all)
  - [2.3 LOD - Critical](#23-lod-critical)
  - [2.4 Frustum culling](#24-frustum-culling)
  - [2.5 Data Streaming (But how, geometrically speaking)](#25-data-streaming-but-how-geometrically-speaking)
  - [2.6 GPU Rendering](#26-gpu-rendering)
- [3. How does Cesium do it?](#3-how-does-cesium-do-it)
  - [3.1 3D Tiles Structure](#31-3d-tiles-structure)
  - [3.2 The Traversal / Selection  Algorithm](#32-the-traversal-selection-algorithm)
  - [3.3 Screen Space Error (SSE) and Geometric Error (GE)](#33-screen-space-error-sse-and-geometric-error-ge)
  - [3.4 Refinement strategies](#34-refinement-strategies)
  - [3.5 Bounding Volumes](#35-bounding-volumes)
  - [3.6 Real Bottlenecks (What Actually Hurts Performance)](#36-real-bottlenecks-what-actually-hurts-performance)
- [4. CONCLUSION](#4-conclusion)
  - [3D Tiles rendering is a continuous optimization problem solved every frame based on camera state.](#3d-tiles-rendering-is-a-continuous-optimization-problem-solved-every-frame-based-on-camera-state)
<!--toc:end-->


---

# 1. History, demand, approach
Let's look closely

## 1.1 It started with 2D GIS (Geographic Information System)
- Layered data (roads, buildings, terrain)
- Used vector + raster formats
- Some of the first tools:
    - [ArcGIS](https://www.arcgis.com/index.html)
        - Released in 1999
    - [QGIS](https://qgis.org/)

---

## 1.2 What was the demand (Limitations of 2D GIS's / What it couldn't do)
- Elevation
- Height
- Visibility / Line of sight

### 1.2.1 First implementation
- Done in 2001 by [Keyhole Inc.](https://www.gearthblog.com/blog/archives/2012/07/google_earth_a_to_z_keyhole_and_kml.html) 
- It one-upped the 2D GIS 

---

## 1.3 The turning point
- Google acquired Keyhole and developed it into *Google Earth*
- Now we have the first 3D globe
- Intuitive geospatial data
- Non-experts could interact with such data
- **SYSTEM:** Satellite imagery + Terrain + Basic 3D buildings

---

## 1.4 Data Explosion
- Now: there is *too much* data 
- Data sources: LiDAR scans (billions of points), drones, satellites, IoT
- **CHALLENGE**: Datasets in TB range -> real-time streaming, rendering in browsers
- **APPROACH**: 3D Tiles, GPU Rendering, LOD (Level Of Detail)

---

# 2. Technicalities
- Let's look under the hood and see how this is done

---

## 2.1 Main issue
- You **CAN NOT** load everything at once
- Realistic datasets examples: City-scale 3D model, Point Cloud, Terrain (multi-res meshes)
- The constraints are real hard:
    - Limited browser memory (a few GB at most)
    - GPU memory
    - Slow network / latency
- From this we deduce the rule:
    - **Never render the whole dataset**
- Everything that follows exists to ensure this

---

## 2.2 Break it all
- Now we do *Spatial Partitioning*: split the data into manageable chunks
    - Quadtrees (2D)
    - Octrees (3D)
    - BVH (Bounding Volume Hierarchy)
- Instead of loading *'the city'*, now you render *'the building', 'this chunk of points'*
- This put bases of: streaming, culling, LOD

---

## 2.3 LOD - Critical
- What is LOD in a nuthsell:
    - Far away - low detail 
    - Close - high detail
    - Example: building loaded using a mesh, if far -> 50 triangles, if mid -> 1000, if close -> 100000
- Without LOD: GPU dies, FPS plummets (unless you have beast computers)
- With LOD: stable performance, scalable rendering
- In systems like CesiumJS, LOD is dynamically selected per tile, based on camera distance + screen-space error

---

## 2.4 Frustum culling
- Principle: don't render what you can't see
- Camera sees a pyramid, that is named [frustum](https://learnopengl.com/Guest-Articles/2021/Scene/Frustum-Culling)
- Anything outside: not loaded / rendered, else loaded
- *BIG* consequences: 
    - Massive performance gains
    - Zero visual downside

---

## 2.5 Data Streaming (But how, geometrically speaking)
- Data is fetched on demand based on camera position
- Mechanism is: 3D Tiles
    - Hierarchical Tiles
    - What's a tile? *Geometry Chunk + Metadata*
    - Supports LOD natively
- Flow:
    - Move the camera
    - Engine determines needed tiles
    - Send request for them
    - Load -> render tiles
- We achieve: low -> high quality, PROGRESSIVELY

---

## 2.6 GPU Rendering
- Rendering is indeed done using GPU
- How? **WebGL** (There is also *WebGPU* emerging)
- Why the GPU for the browser?
    - Parallelism!
    - With this, they can handle millions of vertices
- Frameworks have simple API's that usually don't allow you to interact with WebGL directly
- So then, how do you use it efficiently?
    - Instancing (reuse geometry)
    - Shaders (custom rendering)
    - Buffer Geometry (efficient memory layout)

---

# 3. How does Cesium do it?
- Most 'production-ready' framework, also most restrictive

---

## 3.1 3D Tiles Structure
- This is the thing we're actually streaming
<br>
Core pieces:
<br>
- *tileset.json*
    - root of everything
    - defines:
        - geometric error (LOD metric)
        - hierarchy (tree of tiles)
        - bounding volumes
- Tiles (nodes in the tree)
    - Each tile contains:
        - bounding volume (box / sphere / region)
        - geometric error
        - optional content (geometry)
- Tile content formats:
    - B3DM → batched 3D models (buildings)
    - PNTS → point clouds
    - internally often glTF

---

## 3.2 The Traversal / Selection  Algorithm
- [Example](https://cesium.com/learn/cesium-native/ref-doc/selection-algorithm-details.html)
```md
Root tile
    ↓
Check if visible
    ↓
If not visible → Discard
    ↓
If visible:
    Check LOD (Geometric error vs Screen size)
        ↓
    If good enough → Render this tile
    Else → Refine (load children)
```
---

## 3.3 Screen Space Error (SSE) and Geometric Error (GE)
[GE](https://www.sensat.co/news/tessera-how-to-calculate-geometric-error-in-3d-tiles)

[SSE in relation with GE](https://www.programmersought.com/article/13969093609/)
- SSE is computed by the engine in relation based on GE
- This is how the engine decides: 'Is this detailed enough?'
    - ***Q***: How? ***A***: Project said GE into screen space (pixels basically)
- Key points:
    - SSE <= threshold (user-defined, can be dynamic) => Refine (load children)
    - SSE > threshold => render current tile
- This is the main cause of: 
    - Zoom in -> more data (more detailed)
    - Zooming out -> less data (less detailed)

---

## 3.4 Refinement strategies
- **REPLACE**
    - Parent disappears when children load
- **ADD**
    - Children are added on top of the parents
    - Smoother transitions
    - Often used in Point Clouds

---

## 3.5 Bounding Volumes
- Each tile has a bounding volume:
    - Box
    - Sphere
    - Region (lat/lon/height)
- Where it used:
    - Frustum culling
    - Distance estimation (for SSE)
    - Refinement decisions
- If the bounding volumes are incorrect, everything can break (bad culling, wrongful LOD)

---

## 3.6 Real Bottlenecks (What Actually Hurts Performance)

- CPU:
    - Traversal every frame
    - JSON parsing 
- GPU:
    - Too many draw calls
    - Heavy shaders
    - Large vertex buffers (too big of a vertex count)
- Network:
    - Latency
    - Too many small requests
- Memory:
    - Cache limits
    - GPU buffer exhaustion

---

# 4. CONCLUSION

## 3D Tiles rendering is a continuous optimization problem solved every frame based on camera state.
