# First Houdini Project - Time Estimate

For a first completed version, budget approximately **150 active hours**, with a realistic range of **125-180 hours**.

This assumes:

- One short shot and one locked camera
- One principal RBD event
- A small FLIP domain
- Cached RBD driving FLIP collisions
- One hero refinement region
- Limited POP spray/debris
- Pyro mist only if necessary
- No high-resolution two-way RBD-FLIP coupling
- A straightforward Solaris render

## Work breakdown

| Work | Estimated time |
|---|---:|
| Course and custom instruction | 30-35 hours |
| Follow-along exercises and small tests | 15-20 hours |
| Shot design and primitive animatic | 4-6 hours |
| Scene structure, attributes, proxies and caches | 8-12 hours |
| Global proxy RBD | 10-15 hours |
| RBD-to-FLIP handoff and global FLIP | 15-25 hours |
| Interaction map and local refinement | 12-20 hours |
| POP/Pyro secondary detail | 5-10 hours |
| Assembly, materials, lighting and rendering | 10-15 hours |
| Debugging, failed tests and resimulation | 15-25 hours |
| **Total** | **124-183 hours** |

Use **150 hours** as the working estimate.

## Calendar equivalents

| Weekly commitment | Likely duration |
|---:|---:|
| 8 hours/week | 16-23 weeks |
| 10 hours/week | 13-18 weeks |
| 15 hours/week | 9-12 weeks |
| 20 hours/week | 7-9 weeks |
| 30 hours/week | 4-6 weeks |

Unattended simulations and rendering may add another **20-50 hours of machine time**, but much of that can run while studying or preparing downstream work.

## Scope-dependent outcomes

### Technical proof of concept - 60-90 hours

Proxy RBD, low-resolution FLIP, one interaction mask and a basic render.

### Recommended first finished project - 125-180 hours

One refined region, secondary particles, proper caches, lighting and a final sequence.

### Full original ambition - 200-300+ hours

Multiple refined regions, local FLIP, detailed RBD, POPs, Pyro, extensive look development and substantial iteration.

## Recommendation

For a first project, enforce a **150-hour ceiling** and treat anything beyond one successful local refinement as optional. The most valuable outcome is proving the entire pipeline once, not maximizing the number of effects.
