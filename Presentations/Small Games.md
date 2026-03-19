# The smallest possible games - roads to optimizations && procedural generation

## Why small games started the optimizations loophole
### Historically: *Non-Negotiable*
- Games were optimized because hardware was very limited
    - ROM: 2–32 KB
    - RAM: hundreds of bytes
    - No disk streaming
    - No OS safety net

---
### This constraint shaped:
- Assembly-level thinking
- Procedural generation
- Data-oriented design
- Extreme reuse of logic

---
## Today's take: size is about control, NOT necessity
- *Q*: How does the size affect modern games?
- *A*: Small binaries force:
    - Minimal deps
    - Deterministic behavior
    - Fewer moving parts *(less friction)*
    - Clear mental models
- Basically, fitting an engine into a size as small as possible => understand everything that's happening with it

---
## Procedural generation
- *"It's small because it is compressing most of the things"* - **WRONG**
- Secrete sauce: **storing as little as possible**
    - *Textures*: **math equations**
    - *Audio*: **synthesis / MIDI**
    - *Levels*: **parametric**
    - *Animations*: **functions**
---
### Game examples:
- **Minecraft (2011)**: procedurally generated world (terrain, biome, etc.)
- **No Man's Sky (2016)**: procedurally generated galaxies, planet biomes, star system types, trades
- **.kkreiger(2004)**: textures, 3D models, sound effects 

---
## .kkreiger
- Sound effects(multifunctional synthetizer named V2, was fed continuous MIDI)
- This game in particular is 97 kilobytes. Impressive even for 2004
- Still in demoscene :(
- Proved that what we think a game needs is stored data
    - Reality: it's fundamental and revolutionary thinking

---
### Why is it impressive?
- Changes perspective
- Most games:
    - Textures, meshes, sounds, stored as files
    - Loaded at runtime
- .kkreiger:
    - No stored assets
    - Textures: noise, gradients and distortions
    - Materials: shader parameters + procedural maps
    - Meshes: parametric shapes
    - Sounds: synthetized waveforms (created procedurally and in-place)

---
### Graph-like texture system (ahead of its time)
- Internally uses a node-based (graph-like) texture generator where:
- Nodes: create blurs, noise, color operations, transforms 
- Edges: data flow (constant)
- Final output: GPU texture
- Combines all below into a single flow: 
    - Adobe Substance Designer (95% of AAA games use this tool)
    - Blender texture nodes 
    - Unreal material graphs
- YEARS before they were commonly used

---
### Runtime content compilation
- Modern engines pipeline: precompile shaders, initialize textures, preprocess meshes
- .kkreiger:
    - Compiles everything at startup
    - Generated textures, sounds and meshes at startup
    - Piped everything to GPU/audio buffers

---
### Modern rendering features it packed in 97kb
- Per-pixel lighting
- Normal & shadow mapping
- Post-processing effects

---
### Aggressive code reuse
- Generating textures and heightmaps
- Define geometry and collision
- Visuals and gameplay mechanics

---
# Influence in current games
- Procedural materials
- Runtime shaders
- Generated worlds
- Synthetized audio
- Data-driven pipelines

---
# Thank you!
