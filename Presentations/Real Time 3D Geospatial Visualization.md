# Real Time 3D Geospatial Visualization (in the web)
- Interesting but why/how/when?

---

<!--toc:start-->
- [Real Time 3D Geospatial Visualization (in the web)](#real-time-3d-geospatial-visualization-in-the-web)
- [History, demand, approach](#history-demand-approach)
  - [It started with 2D GIS (Geographic Information System)](#it-started-with-2d-gis-geographic-information-system)
  - [What was the demand (Limitations of 2D GIS's / What it couldn't do)](#what-was-the-demand-limitations-of-2d-giss-what-it-couldnt-do)
    - [First implementation](#first-implementation)
  - [The turning point](#the-turning-point)
  - [Data Explosion](#data-explosion)
- [Technicalities](#technicalities)
  - [Main issue](#main-issue)
  - [Break it all](#break-it-all)
  - [LOD - Critical](#lod-critical)
  - [Frustum culling](#frustum-culling)
  - [Data Streaming (But how, geometrically speaking)](#data-streaming-but-how-geometrically-speaking)
  - [GPU Rendering](#gpu-rendering)
- [How does Cesium do it?](#how-does-cesium-do-it)
  - [3D Tiles Structure](#3d-tiles-structure)
<!--toc:end-->


---

# History, demand, approach
Let's look closely

## It started with 2D GIS (Geographic Information System)
- Layered data (roads, buildings, terrain)
- Used vector + raster formats
- Some of the first tools:
    - [ArcGIS](https://www.arcgis.com/index.html)
        - Released in 1999
    - [QGIS](https://qgis.org/)

---

## What was the demand (Limitations of 2D GIS's / What it couldn't do)
- Elevation
- Height
- Visibility / Line of sight

### First implementation
- Done in 2001 by [Keyhole Inc.](https://www.gearthblog.com/blog/archives/2012/07/google_earth_a_to_z_keyhole_and_kml.html) 
- It one-upped the 2D GIS 

---

## The turning point
- Google acquired Keyhole and developed it into *Google Earth*
- Now we have the first 3D globe
- Intuitive geospatial data
- Non-experts could interact with such data
- **SYSTEM:** Satellite imagery + Terrain + Basic 3D buildings

---

## Data Explosion
- Now: there is *too much* data 
- Data sources: LiDAR scans (billions of points), drones, satellites, IoT
- **CHALLENGE**: Datasets in TB range -> real-time streaming, rendering in browsers
- **APPROACH**: 3D Tiles, GPU Rendering, LOD (Level Of Detail)

---

# Technicalities
- Let's look under the hood and see how this is done

---

## Main issue
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

## Break it all
- Now we do *Spatial Partitioning*: split the data into manageable chunks
    - Quadtrees (2D)
    - Octrees (3D)
    - BVH (Bounding Volume Hierarchy)
- Instead of loading *'the city'*, now you render *'the building', 'this chunk of points'*
- This put bases of: streaming, culling, LOD

---

## LOD - Critical
- What is LOD in a nuthsell:
    - Far away - low detail 
    - Close - high detail
    - Example: building loaded using a mesh, if far -> 50 triangles, if mid -> 1000, if close -> 100000
- Without LOD: GPU dies, FPS plummets (unless you have beast computers)
- With LOD: stable performance, scalable rendering
- In systems like CesiumJS, LOD is dynamically selected per tile, based on camera distance + screen-space error

---

## Frustum culling
- Principle: don't render what you can't see
- Camera sees a pyramid, that is named [frustum](https://learnopengl.com/Guest-Articles/2021/Scene/Frustum-Culling)
- Anything outside: not loaded / rendered, else loaded
- *BIG* consequences: 
    - Massive performance gains
    - Zero visual downside

---

## Data Streaming (But how, geometrically speaking)
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

## GPU Rendering
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

# How does Cesium do it?
- Most 'production-ready' framework, also most restrictive

---

## 3D Tiles Structure
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

## The Traversal Algorithm
- [Image example, slide 5](https://www.slideserve.com/gefen/chc-coherent-hierarchical-culling-revisited-powerpoint-ppt-presentation)
