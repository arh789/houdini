# Project Syllabus: Coarse-to-Fine Houdini Vignette

This syllabus reorganizes the course around production of the coarse-to-fine RBD and FLIP vignette. The Basics lesson titles come from the reconstructed screenshots. For later course sections, the individual lesson titles were not visible, so this document specifies the required subject matter rather than inventing titles.

## Curriculum structure

```text
Shot contract
`-- Houdini data model
    `-- VEX selection logic
        `-- Packed proxies and cache discipline
            `-- Collision representations
                `-- Global RBD
                    `-- RBD-to-FLIP handoff
                        `-- Global FLIP
                            `-- Interaction map
                                `-- Local FX refinement
                                    `-- Cache-only Solaris assembly
```

The study cycle for every phase is:

```text
Learn -> build a small test -> integrate it -> cache it -> pass the gate
```

Do not continue merely because the relevant videos have been watched.

---

## Phase 0 - Define the shot

### Decide

- Final camera and framing
- Scene scale and units
- Frame rate and short frame range
- One principal destruction/water event
- Hero impact and splash regions
- Approximate memory and cache budget
- Which objects the water must actually move

### Build

Create a primitive animatic using boxes, spheres and simple animation.

### Gate A

The event must be understandable from the intended camera without detailed simulation.

---

## Phase 1 - Houdini's geometry and data model

### Required Basics lessons

- Interface I - Basics / Crash Course
- Tree View vs. Networks
- The Geometry Spreadsheet
- Flags / Ghosting
- Interface II: Working with the Node Network
- Contexts
- Scene Organisation
- Transform Objects / Pivots
- Basic Shapes and Test Geometries
- Groups
- Attributes and Attribute Classes
- Vertices vs. Points
- Data Types
- Attribute Promote
- Visualization
- Measure

### Build

Create the complete proxy scene with inspectable attributes such as:

```text
name
id
active
P
orient
v
w
mass
material_class
camera_importance
```

### Gate

Objects retain stable names, groups, IDs and transforms when upstream parameters change.

---

## Phase 2 - Procedural selection and VEX logic

### Required Basics lessons

- Attribute Adjust Nodes
- Parameter Expressions
- VEX and VOPs
- VEX II - Parameters and Variables
- Comparisons
- Attribute Transfer and Attribute Copy
- For Loops
- Masking
- `fitRange()` / Remap

### Dedicated VEX study

Enter the VEX section only far enough to learn:

- Reading and creating attributes
- Vector operations
- Geometry queries
- Spatial searches
- Sampling geometry and volumes
- Constructing groups and masks
- Converting raw values into normalized control fields

### Build

Make a test network that converts impact strength, velocity, distance and camera visibility into:

```text
f@impact_strength
f@camera_importance
f@refine_mask
i@needs_detail
```

### Gate

The viewport clearly shows why one region receives detail while another remains a proxy.

---

## Phase 3 - Packed geometry and cache discipline

Caching belongs near the beginning of the curriculum, not at the end.

### Required Basics lessons

- Packed Geometry
- Pack / Unpack / Convert
- File Access I - Reading / Importing
- File Access II - Exporting
- File Access III - Caching
- Performance Monitor

### Build

Create a small packed-object simulation and prove that it can be:

1. Written to disk
2. Reloaded into a fresh scene
3. Reconnected to render geometry
4. Inspected for stable names and transforms

### Gate B

A reloaded cache preserves:

```text
name and id
position and orientation
linear velocity: v
angular velocity: w
frame range
scene scale
```

Changing fracture topology or piece names after this gate invalidates downstream caches.

---

## Phase 4 - Construct simulation proxies

### Required Basics lessons

- Boolean Node
- Reducing / Remeshing Geometry
- Reducing / Remeshing Geometry II
- Volumes
- VDBs - Volumes 2.0
- SDFs - Signed Distance Fields
- The Magic Node: Point Deform

### Build

Prepare:

- Low-piece-count destruction geometry
- Simple packed collision objects
- Watertight FLIP collision geometry
- Render geometry that can inherit proxy motion
- A collision SDF that can be inspected in the viewport

Use stable piece names and packed transforms for fractured rigid bodies. Point Deform is primarily for continuously deforming proxy-to-detail transfers.

### Gate C

Collision geometry has no unexpected holes, sign errors, popping, excessive resolution or obvious penetration.

---

## Phase 5 - Global proxy RBD simulation

### Required RBD topics

From the RBD section, select lessons covering:

- Packed pieces
- Stable piece names
- Active and passive objects
- Fracturing
- Constraint creation and breaking
- Collision shapes
- Solver stability and substeps
- Linear and angular velocity
- Impact or contact data
- Transform extraction
- RBD caching

### Build

Run the low-resolution destruction pass that establishes the authoritative timing of the event.

### Deliverable

A cached RBD pass containing stable transforms, velocities and impact information.

### Gate

The destruction reads correctly from the final camera and remains within the agreed simulation and cache budget.

Do not add fracture density merely to make the proxy pass look final.

---

## Phase 6 - RBD-to-FLIP handoff

### Learn

- Animated collision geometry
- Collision SDF generation
- Collision velocity
- Transform-to-geometry reconstruction
- Importing cached RBD motion into FLIP
- Debugging collision fields

### Default production structure

```text
cached proxy RBD
        |
        v
animated collision geometry and velocity
        |
        v
low-resolution FLIP
```

If the water must materially drive the rigid bodies, run a very small coupled technical test. Otherwise, use art-directed RBD motion and let FLIP react to it.

### Gate

A small FLIP collision test reproduces the RBD timing without popping, penetration or missing velocity.

---

## Phase 7 - Global low-resolution FLIP pass

### Required FLIP topics

- Sources and sinks
- Domain sizing
- Particle separation
- Collision SDFs
- Collision velocity
- Substeps
- Reseeding
- Narrow-band or bounded simulation, where appropriate
- Particle and field caching
- Surface reconstruction

### Build

Run a modest-resolution water simulation using the cached RBD as its animated collision source.

Cache particles or fields first. Mesh the water downstream rather than remeshing during every simulation test.

### Gate D

Approve:

- Broad water displacement
- Collision timing
- Splash direction
- Domain boundaries
- Overall event silhouette

The global pass establishes coherence; it does not need final droplet detail.

---

## Phase 8 - Extract the interaction map

### Record

Create a point or volume cache describing significant interactions:

```text
event_id
piece_name
impact_frame
P
N
v
speed
impact_strength
radius
camera_visibility
refine_mask
local_start_frame
local_end_frame
```

### Apply

Reuse the Geometry Spreadsheet, attributes, VEX, comparisons, masks, Attribute Transfer and `fitRange()`.

Temporally smooth or accumulate transferred masks. A fresh Attribute Transfer on every frame may flicker.

### Deliverable

An inspectable interaction-map cache that identifies exactly where and when refinement is permitted.

### Gate

Every proposed local simulation can be traced to a visible impact or camera requirement. Regenerating the same global pass produces the same refinement regions.

---

## Phase 9 - Selective local refinement

Complete one hero region before creating multiple local passes.

### Recommended order

1. Detailed RBD fracture and foreground pieces
2. POP debris, droplets or spray
3. Whitewater and secondary particles
4. Local FLIP only when particles cannot produce the required result
5. Pyro mist or dust only when it improves the image

### Just-in-time Basics lessons

- Paint Attributes
- Scatter I - Basics
- Randomness
- Noise
- `curlnoise`
- `@rest` Position
- Flipbook

Local FLIP simulations are difficult to stitch invisibly into a global tank. Prefer additive spray, whitewater or POP detail first. If local FLIP is necessary, use a short isolated domain with inherited velocity and boundaries hidden from the camera.

### Gate E

Each local pass:

- Inherits global timing and direction
- Reads only cached upstream data
- Can be disabled independently
- Creates no visible seam or temporal pop
- Adds enough visible value to justify its cost

---

## Phase 10 - Cache-only assembly and rendering

### Required study

From Solaris:

- Importing and referencing caches
- USD hierarchy and layering
- Materials
- Lights and cameras
- Render products
- Sequence rendering

From Basics:

- ACES Basic Settings
- Assets, only if reusable tools need packaging

### Cache structure

```text
global_rbd
global_flip
interaction_map
local_rbd
pops
whitewater
local_flip
pyro
render_geometry
```

### Build

Create a separate assembly scene that reads versioned caches. Production solvers should be bypassed or absent.

### Gate F

The assembly scene can open, scrub, preview and render without evaluating any simulation. Representative frames render successfully before launching the full sequence.

---

## Deferred material

Study these only if the shot develops a concrete requirement for them:

- General industry and career material
- Most generic examples and homework
- UV Mapping
- Full Copernicus branch
- Multi Copy
- Advanced Curve Tools
- Advanced Noise
- Electric Pole
- Implicit Surfaces
- Object Packing
- Differential Growth
- TOPs/PDG
- Vellum, unless cloth, cables, grains or soft bodies appear
- MPM, unless the project uses sand, snow, mud or mixed materials
- Extensive Pyro if mist or dust adds little to the frame

---

## Estimated prerequisite size

The visible Basics syllabus contributes approximately **8-10 hours** of directly useful prerequisite material.

The advanced VEX, RBD, FLIP, POP, Pyro and Solaris study should be consumed just in time. Their exact duration cannot be reconstructed from the screenshots because their lesson lists were not expanded.

The project's essential learning spine is:

```text
Attributes and groups
-> minimal VEX
-> packed geometry
-> cache discipline
-> VDB/SDF collisions
-> proxy RBD
-> RBD-to-FLIP handoff
-> global FLIP
-> interaction map
-> selective secondary detail
-> cache-only Solaris assembly
```
