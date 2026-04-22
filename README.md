# Daily Reflection Tree

A deterministic end-of-day reflection tool built for the DeepThought Fellowship assignment. No LLM at runtime — the entire conversation is a structured tree walked by a simple engine.

## Repository Structure

```
tree/
  reflection-tree.json    ← Part A: the complete tree as structured data (36 nodes)
  tree-diagram.md         ← Part A: Mermaid branching diagram + node count

agent/
  index.html              ← Part B: single-file web agent (open in any browser)

transcripts/
  persona-1-transcript.md ← External/Entitlement/Self path (Priya)
  persona-2-transcript.md ← Internal/Contribution/Other path (Marcus)

write-up.md               ← Part A: design rationale (2 pages)
README.md                 ← This file
```

## How to Run the Agent

Open `agent/index.html` in any modern browser. No server, no build step, no dependencies. The tree is embedded directly in the file.

**Keyboard shortcut:** Press `Enter` to advance through the conversation.

The agent:
- Loads the full tree from the embedded JSON
- Walks nodes in order, branching deterministically based on selections
- Auto-advances through `start`, `bridge` nodes (no user input required)
- Waits for input at `question` nodes
- Shows `reflection` nodes with a Continue button
- Accumulates signals per axis and renders one of 12 authored summary reflections

## How to Read the Tree File

`reflection-tree.json` is a flat array of node objects. Each node has:

```json
{
  "id": "A1_Q1",
  "parentId": "A0_BRIDGE",
  "type": "question",
  "text": "When something didn't go as planned today, where did your mind go first?",
  "options": [
    { "label": "...", "value": "internal_a" },
    ...
  ],
  "target": null,
  "signal": null
}
```

**Decision nodes** have `routing` instead of `options`:
```json
{
  "id": "A1_D1",
  "type": "decision",
  "routing": [
    { "condition": "answer=internal_a|internal_b", "target": "A1_Q2_INT" },
    { "condition": "answer=external_a|external_b", "target": "A1_Q2_EXT" }
  ]
}
```

To trace a path manually: start at `START`, follow `target` fields or match routing conditions to find `target` node IDs.

## The Three Axes

| Axis | Spectrum | Psychology |
|---|---|---|
| 1 — Locus | Victim ↔ Victor | Rotter (1954) Locus of Control + Dweck (2006) Growth Mindset |
| 2 — Orientation | Entitlement ↔ Contribution | Campbell et al. (2004) + Organ (1988) OCB |
| 3 — Radius | Self-Centrism ↔ Altrocentrism | Maslow (1969) Self-Transcendence + Batson (2011) Perspective-Taking |

## Signal Tallying

As the employee answers questions, each node with a `signal` field adds +1 to the appropriate axis pole:

```
"signal": "axis1:internal"  →  state.signals.axis1.internal += 1
"signal": "axis2:contribution"  →  state.signals.axis2.contribution += 1
```

At the end, the dominant pole per axis is computed and used to key into one of **12 authored summary templates**.

## Stats

- **36 total nodes**
- **11 question nodes** (3+ per axis)
- **7 decision nodes**
- **12 reflection nodes** (4+ per axis)
- **3 bridge nodes**
- **72 possible full conversation paths**
- **12 distinct summary reflections**
- **0 LLM calls at runtime**
