# VSlices Template Standard

VSlices Template Standard owns reusable materialization knowledge for VSlices artifacts.

It answers a different question from Docs Standard:

```text
Docs Standard
  -> what documentary knowledge exists?
  -> which questions define a Document?
  -> how are those questions related?

Template Standard
  -> how can that semantic artifact state be represented?
  -> how can the representation be reconstructed back into semantic state?
```

Tooling owns the generic mechanism that applies and reconstructs templates. Template Standard owns the materialization vocabulary expressed through that mechanism.

Current working formulation:

> Docs Standard owns documentary semantics. Template Standard owns documentary materialization. Tooling owns the mechanism that connects them.

## Authority boundary

```text
vslices/docs-standard
  = artifact/document vocabulary
  = stable question identities
  = question text and relationships
  = semantic constraints

vslices/template-standard
  = materialization templates
  = layout rules
  = representation/reconstruction contracts

vslices/tooling
  = template loading
  = semantic-state reconstruction
  = rendering/materialization
  = validation and lifecycle

human-authored artifact
  = editable materialization
  = evidence that must remain reconstructible
```

A heading level, table column, callout, list item, or diagram is not documentary semantics merely because a template uses it.

## Current witness

The first template is intentionally small:

```text
markdown/question-tree
```

It materializes a Document question graph as hierarchical Markdown headings. The semantic depth comes from Docs Standard; the number of `#` characters is only a Markdown realization of that depth.

This is the layout currently exercised by Context and Structure Documents.

## Reconstruction requirement

Templates for human-editable artifacts must preserve enough evidence for Tooling to reconstruct the represented semantic state.

The current target law is:

```text
semantic state
  -> materialize(template)
  -> read(template)
  -> equivalent semantic state
```

This is semantic round-trip, not byte-for-byte round-trip.

If a materialization cannot be reconstructed unambiguously, Tooling must fail closed rather than invent semantic identity.

## Domain Vocabulary pressure

Historical Domain Vocabulary artifacts are important design evidence: a question such as “What does this term mean?” may be represented as a table column rather than a heading.

That means:

```text
semantic question depth != Markdown heading depth
```

and more generally:

```text
semantic question graph != visual document tree
```

A future Domain Vocabulary template should be promoted only after its normative question vocabulary exists in Docs Standard. Template Standard must not define those questions itself.

## Current scope

This repository currently standardizes only materialization knowledge proven by real VSlices artifacts.

It does not yet define:

- a complete template language;
- arbitrary custom layouts;
- Domain Vocabulary semantics;
- Support Note, Nexus, or Continuity Path layouts;
- migrations between template versions;
- project-owned template extensions.

Those should be discovered from real materialization pressure rather than added speculatively.
