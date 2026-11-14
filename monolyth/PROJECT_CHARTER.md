# Project MONOLYTH

**Status:** Active — human-directed Houdini learning and code-assisted production.

## 1. Purpose and priorities

**Primary objective:** Learn to use Houdini by constructing real work through iterative, human-directed, code-assisted operations. The human specifies what Houdini should do. ChatGPT writes and explains the relevant code, the human executes and inspects the result, and both diagnose discrepancies until the operation works.

**Secondary objective:** Construct MONOLYTH, a procedural monolithic warning artefact, as the accumulating practical application of that learning.

**Long-term possibility, not the present default:** Increase automation only for procedures whose mechanisms have been understood, executed, tested and verified.

The project produces two outputs at every meaningful iteration: **a working artefact or verified scene change** and **an explanation of how the mechanism works**. Progress cannot be evaluated solely by the appearance of a finished render.

## 2. Collaboration and responsibilities

| Participant | Responsibility |
|---|---|
| Human | Specify creative intent and next action; decide priorities; execute and inspect Houdini operations; judge aesthetic and semantic success |
| ChatGPT | Translate the requested operation into executable code; explain its Houdini concepts, parameters and relationships; define expected output and tests; diagnose discrepancies |
| Code | Express repeatable operations using Houdini Python/HOM, VEX, SOP networks and related interfaces as appropriate |
| Houdini | Evaluate the resulting scene, geometry, attributes, simulations and renders; provide observable evidence |
| Codex | Maintain and refactor project code, tests and multi-file changes when delegated; support reproducibility |
| GitHub | Store the authoritative charter, reproducible scripts, verified outputs, troubleshooting notes and metaanalysis |

ChatGPT does not assume that code executes successfully merely because it looks valid. Actual execution state, screenshots, logs, node information and inspection results are evidence.

The human retains creative direction. ChatGPT and Codex assist execution and learning; they do not independently redefine the project's intent.

## 3. Operating loop

```text
HUMAN: specifies desired result
    |
    v
CHATGPT: translates intent into a bounded Houdini operation
    |  - runnable code and where to execute it
    |  - expected scene changes and observable tests
    |  - explanation of the underlying Houdini mechanism
    v
CODE: Python/HOM, VEX, SOPs or other appropriate means
    |
    v
HOUDINI: executes and exposes actual state
    |
    v
HUMAN + CHATGPT: compare actual state with expected state
    |  - identify the smallest causal discrepancy
    |  - correct one bounded mechanism at a time
    |  - rerun and verify
    |
    +------> repeat until acceptance
    |
    v
GITHUB: commit working code, evidence and lessons learnt
    |
    +------> human selects next objective
```

### Five-stage iteration protocol

1. **Objective:** Define the immediate intended result, necessary constraints and observable evidence of success.
2. **Implementation:** Provide runnable code, exact execution location, expected network/output changes and any safety or overwrite considerations.
3. **Explanation:** Explain the nodes, attributes, parameter relationships and why the implementation works.
4. **Execution and troubleshooting:** Run in Houdini; compare actual with expected; diagnose and correct specific causes without unnecessarily replacing successful components.
5. **Consolidation:** Preserve verified code, scene states, reusable patterns, failures and fixes in GitHub.

When an operation has not been executed or verified, explicitly label it **untested**.

## 4. Learning outcomes

| Level | Learning target | Evidence |
|---|---|---|
| Operational | Make Houdini perform a requested action | Execute supplied code and observe the result |
| Structural | Understand node networks, geometry, attributes and parameters | Explain and modify the generated relationships |
| Generative | Construct and adapt systems independently | Predict the consequences of controlled modifications |

Learning is driven by the current creative problem, rather than a rigid sequence of disconnected beginner exercises.

**Automate repetitive execution, not understanding.** Node networks should be legible, with descriptive names and inspectable intermediate states. Where useful, the human should predict what a parameter or connection change will do before changing it.

## 5. Choosing code versus direct Houdini interaction

| Task | Default approach | Reason |
|---|---|---|
| Create/connect many nodes; configure repeated parameters | Code | Precision, repeatability and inspectability |
| Construct procedural networks and geometry relationships | Code with visible Houdini nodes | Reproducible structure without concealing the mechanism |
| Learn an unfamiliar node or attribute | Houdini interface | Direct examination of actual state |
| Inspect geometry, attributes, viewport and composition | Houdini interface | Essential visual and structural feedback |
| Experiment with parameters | Either | Choose the approach that improves understanding and control |
| Troubleshoot unexpected results | Both | Code reports state; interface reveals behaviour |
| Automate established procedures | Code | Reduce repetitive work after verification |

These are defaults, not permanent restrictions. The preferred boundary between code and manual interaction should be tested and revised from experience.

## 6. MONOLYTH design intent (secondary production brief)

The accumulating artefact is a monolithic warning structure intended to communicate:

- **Danger:** Something fundamentally threatening exists here.
- **Permanence:** The structure was intended to endure beyond its creators.
- **Hostility:** Its geometry discourages approach, occupation and interaction.
- **Decay:** The structure has survived prolonged environmental deterioration.
- **Uncertainty:** Its origins and exact meaning remain disturbing and ambiguous.

The design hypothesis is that these properties should arise from relationships between geometry, scale, materials and spatial organisation, rather than depending solely on decorative symbols or written descriptions.

This brief supplies continuity and practical exercises; it must not override the primary learning objective or force premature technical complexity.

## 7. Verification and progression

Each completed operation should record:

- **Intended change:** What the human requested and what would count as success.
- **Implementation:** Script, nodes and parameters used, with a reproducible entry point.
- **Observed outcome:** What Houdini actually produced; attach a screenshot, scene file, logs or diagnostics where applicable.
- **Explanation:** The causal Houdini mechanism and what was learnt.
- **Discrepancies and corrections:** Failed assumptions, error messages, targeted changes and the verified result.
- **Next action:** Selected by the human.

Construction can gradually advance from basic SOPs and node manipulation to procedural variation, material weathering, rendering, animation, and, if useful, simulations. Those stages are opportunities rather than a fixed curriculum.

## 8. Future research direction

The original charter's more ambitious hypothesis remains available for later investigation: an agent-driven procedural system may preserve strategic intent across substantially different MONOLYTH variants.

Possible future tests include parameterised variation, reproducibility, independent evaluation of semantic coherence, and adversarial changes to proportions, topology, materials and environment. Successful procedures may eventually be consolidated into reusable Houdini Digital Assets and automated workflows.

These are **future possibilities**, not current acceptance requirements. Human-directed learning and dependable execution come first.

## 9. Governing principles

**The human determines intent and direction. ChatGPT translates intent into executable Houdini operations and explains their mechanisms. Houdini provides the observable result. Human and AI jointly diagnose discrepancies, preserve working knowledge and progressively construct the final artefact.**

**Every operation should produce two outputs: an artefact and an explanation of the mechanism that produced it.**

For the eventual design system: **Strategic intent is invariant. Geometry is negotiable.**

## 10. Decision record

- **2026-11-14:** Changed primary project goal from autonomous MONOLYTH production to learning Houdini through iterative human-directed, code-assisted construction. The previous charter remains available in Git history.
- Metaanalysis: [Human-directed Houdini learning and production model](metaanalysis/2026-11-14-human-directed-houdini-learning.md).
