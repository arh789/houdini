# Smallest Lossless Houdini Project Implementation

The smallest lossless implementation is a **3-4 second, single-camera RBD-to-FLIP shot with one automatically selected refinement region**.

It preserves every important claim of the larger project while removing almost all decorative complexity.

## Minimal shot

A small rigid object - such as a fractured concrete slab - falls into a shallow rectangular water tank.

```text
12-piece proxy RBD
        |
        v
cached transforms
        |
        v
low-resolution global FLIP
        |
        v
one automatically detected impact event
        |
        v
one local POP splash/debris pass
        |
        v
cache-only Solaris assembly
```

Use:

- 72-96 frames at 24 fps
- One static camera
- One destructible object
- Approximately 8-20 packed pieces
- One small water domain
- One impact region
- One local secondary pass
- Simple materials and lighting
- 1280x720 final output

## Components that must remain

| Component | Why it cannot be removed |
|---|---|
| Proxy RBD simulation | Establishes global motion and causality |
| Global FLIP simulation | Proves cross-system interaction |
| Cached RBD-to-FLIP collision handoff | Proves modular solver separation |
| Interaction event | Connects simulation results to refinement decisions |
| Procedural refinement mask | Proves that detail is allocated rather than manually placed |
| One local detail simulation | Demonstrates coarse-to-fine refinement |
| Separate caches | Proves hardware-manageable production |
| Cache-only assembly | Proves the result no longer depends on live solvers |

## Minimal interaction map

Do not build a general-purpose interaction-analysis system yet. Record one event:

```text
event_id
impact_frame
P
N
v
impact_speed
radius
start_frame
end_frame
```

The event can be generated when the leading RBD piece crosses the water level above a velocity threshold.

Use it to drive:

- POP splash position
- Emission direction
- Particle count
- Refinement radius
- Local simulation frame range

If the RBD timing changes, the impact event and secondary pass must move automatically. That is the critical proof.

## Minimal local refinement

Use a short POP particle pass for splash droplets or debris.

Do not begin with local FLIP. Local FLIP introduces boundary matching, velocity initialization, meshing and seam problems that are unnecessary for proving the architecture.

The local pass should:

- Begin shortly before the impact
- Inherit position and velocity from the event
- Run only around the selected region
- Be independently cacheable
- Disappear cleanly when disabled

## Cache structure

```text
cache/
|-- rbd_proxy/
|-- flip_global/
|-- interaction_event/
|-- pop_detail/
`-- render_geometry/
```

The final assembly must work with all simulation solvers bypassed.

## Remove from the first implementation

- High-resolution two-way RBD-FLIP coupling
- Multiple impact regions
- Local FLIP
- Whitewater solver
- Pyro mist or dust
- Secondary RBD fracture
- Moving camera
- Multiple assets
- Complex constraints
- Detailed materials
- Elaborate USD layering
- TOPs/PDG
- 1080p or 4K output
- Extensive AOVs and compositing

These improve presentation but do not further validate the central method.

## Success criteria

The implementation is complete when:

1. The proxy RBD motion is cached.
2. FLIP reacts to the cached animated collider.
3. The impact event is generated automatically.
4. The event drives one local particle refinement.
5. Each stage can be regenerated independently.
6. The final scene renders entirely from caches.
7. Changing the RBD impact frame moves all downstream detail without manual correction.

## Time estimate

| Work | Time |
|---|---:|
| Minimum required instruction | 18-25 hours |
| Shot and proxy construction | 5-8 hours |
| RBD and caching | 6-10 hours |
| FLIP collision and global pass | 10-15 hours |
| Interaction event and POP refinement | 8-12 hours |
| Assembly and rendering | 6-10 hours |
| First-project debugging allowance | 10-15 hours |
| **Total** | **63-95 hours** |

Use **80 hours** as the working budget.

The compact project rule is:

> **One object, one impact, one refinement, one camera, one cached render.**
