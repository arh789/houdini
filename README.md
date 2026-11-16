# Houdini Learning and Project Repository

This repository supports human-directed, code-assisted Houdini learning through bounded projects, reproducible operations and explicit explanations of how each mechanism works.

## Project areas

### MONOLYTH

[MONOLYTH](./monolyth/PROJECT_CHARTER.md) is the active creative learning project. Its primary objective is to learn Houdini through iterative, human-directed construction; the monolithic warning artefact supplies the accumulating practical brief. Its supporting analysis is stored in [`monolyth/metaanalysis`](./monolyth/metaanalysis/).

### Coarse-to-fine RBD/FLIP vignette

The root planning documents define a resource-efficient first simulation project: a short, single-camera shot in which a fractured rigid object enters a small body of water. Packed RBD motion is cached, reused as a FLIP collider, analysed to produce one impact event, and used to drive a local POP detail pass. The final shot is assembled and rendered from caches in Solaris.

This vignette is both a standalone project plan and a source of techniques that may later support MONOLYTH. It does not replace the MONOLYTH charter or broaden MONOLYTH's current acceptance requirements.

## RBD/FLIP start here

For the shortest route from planning to production, read these files in order:

1. [smallest-lossless-implementation.md](./smallest-lossless-implementation.md) - defines the first project and its completion criteria.
2. [project-syllabus.md](./project-syllabus.md) - converts the project into a phased learning and implementation sequence.
3. [current-free-video-learning-path.md](./current-free-video-learning-path.md) - supplies free, reasonably current instruction for the required techniques.
4. [first-project-time-estimate.md](./first-project-time-estimate.md) - provides the time budget and recommended scope ceiling.

Use the remaining documents as source material and reference rather than additional requirements.

## Repository map

```text
MONOLYTH
|-- monolyth/PROJECT_CHARTER.md
`-- monolyth/metaanalysis/

RBD/FLIP source and rationale
|-- houdini-workflow.txt
`-- syllabus.md

RBD/FLIP course filtering
|-- concise-learning-path.md
`-- task-relevant-learning-path.md

RBD/FLIP definition and execution
|-- project-syllabus.md
|-- smallest-lossless-implementation.md
|-- first-project-time-estimate.md
`-- current-free-video-learning-path.md
```

## File guide

### `houdini-workflow.txt`

The original design brief and conceptual rationale for the coarse-to-fine workflow. It explains why the project uses a bounded vignette, proxy simulations, extracted interaction data, selective detail, separate caches and final reassembly. The MacBook Pro constraint is treated as a design input rather than an inconvenience.

Use this file when evaluating architectural decisions or considering whether a proposed addition supports the original optimisation goal.

### `syllabus.md`

A reconstruction of the Houdini Course Basics syllabus from the supplied screenshots. It records the visible lesson titles, chapter durations, free-lesson markings and known uncertainties.

This is the archival course inventory. It is useful for locating a specific lesson, but it is not the recommended viewing order for this project.

### `concise-learning-path.md`

A general-purpose reduction of the full Basics syllabus. It removes repetition and low-priority contextual material while preserving a broad foundation for progressing into POPs, RBDs, FLIP, Pyro and other simulation sections.

Use this when the goal is wider Houdini competence rather than only completing the current project.

### `task-relevant-learning-path.md`

A project-focused filter of the reconstructed course. It maps the coarse-to-fine workflow to the most relevant Basics lessons and identifies the highest-priority cluster: attributes, groups, VEX, packed geometry, volumes/SDFs and caching.

Use this to decide which lessons in the purchased Houdini Course deserve attention for this particular task.

### `project-syllabus.md`

The detailed curriculum for building the coarse-to-fine vignette. It reorganises study around production phases such as shot definition, data modelling, VEX selection logic, packed proxies, RBD, FLIP, interaction mapping, local refinement and cache-only Solaris assembly. Each phase includes something to build and a gate that must be passed.

This is the main execution sequence. Progress is measured by working tests and caches, not by videos watched.

### `smallest-lossless-implementation.md`

The scope contract for the first build. It reduces the larger workflow to a 3-4 second shot with one static camera, roughly 8-20 RBD pieces, one small FLIP domain, one automatically detected impact event, one POP detail pass and a cache-only final assembly.

This is the authoritative project scope. When another document suggests more complexity, this file takes priority for the first implementation.

### `first-project-time-estimate.md`

The production estimate for a first-time Houdini user. It recommends a working ceiling of approximately 150 active hours, gives a 125-180 hour realistic range, separates machine time from active time and shows calendar equivalents for different weekly commitments.

Use this for scheduling and for deciding whether a proposed feature belongs in the first version.

### `current-free-video-learning-path.md`

A current-first collection of free instructional videos covering foundations, packed RBDs, collider caching, SOP FLIP, RBD/FLIP interaction, VEX, impact data, POP refinement, USD, Solaris and Karma. It favours Houdini 20-22 material while retaining a small amount of older instruction where the underlying workflow remains current.

Use this as the external instruction list. It supplements the project syllabus; it does not add features to the project.

## Sources of truth

- **MONOLYTH purpose and operating model:** `monolyth/PROJECT_CHARTER.md`
- **Project scope:** `smallest-lossless-implementation.md`
- **Implementation and learning order:** `project-syllabus.md`
- **External instruction:** `current-free-video-learning-path.md`
- **Schedule and effort:** `first-project-time-estimate.md`
- **Original architectural rationale:** `houdini-workflow.txt`
- **Original course inventory:** `syllabus.md`

## Scope rule

Complete the smallest lossless implementation before adding local FLIP, whitewater, Pyro, multiple impact regions, a moving camera, elaborate materials or complex USD layering. Those additions may improve presentation, but they are not required to prove the workflow.

## Notes

- The reconstructed syllabus reflects the supplied course screenshots captured on 16 October 2026 and may not reflect later course changes.
- The video list is intended for Houdini 21/22-era work; interface details may differ in the retained Houdini 19.5/20 material.
- The repository currently contains charters, analysis, planning and learning documents only. Houdini scene files, scripts, caches, renders and downloaded course material are not yet included.
