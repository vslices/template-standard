# Materialization model

VSlices Template Standard separates semantic artifact state from its human-facing realization.

A Document question graph is semantic knowledge owned by Docs Standard. A heading level, table column, list item, callout, diagram, or other visual construct is a materialization choice owned by Template Standard.

## Core distinction

```text
semantic question graph
  !=
visual document tree
```

For example, a question at semantic depth 2 may be represented as:

- an H3 heading;
- a table column;
- a callout inside its parent;
- a list field;
- another reconstructible representation.

None of those choices changes the semantic parent/child relation.

## Required directionality

A human-editable template must support both directions:

```text
semantic state
  -> materialize(template)
  -> human-editable representation

human-editable representation
  -> read(template)
  -> semantic state
```

The intended law is semantic:

```text
read(template, materialize(template, state))
  == equivalent(state)
```

Byte-for-byte identity is not required.

## Identity and presentation

Visible question text is presentation.

Stable question identity remains owned by Docs Standard.

A template may use visible question text when rendering, but reconstruction must not silently treat wording as durable identity when stronger structural evidence exists.

If a template cannot reconstruct identity unambiguously, it must reject the materialization rather than invent a match.

## First witness: markdown.question-tree

The first template is intentionally evidence-limited.

It is proven against the current Context and Structure witnesses:

```text
Document type
  -> root question

root question
  -> one immediate child
```

That lets Tooling reconstruct:

```text
artifact.type
  -> root identity

parent identity + unique child
  -> child identity
```

without using the visible heading text as identity.

The Markdown heading level is only the current realization of semantic depth:

```text
root      -> H1
child     -> H2
grandchild-> H3
```

This mapping belongs to this template, not to Docs Standard.

## Current boundary

The current template does not claim to solve arbitrary branching.

If one parent has multiple materializable children and the representation does not preserve enough evidence to distinguish them, reconstruction is ambiguous and must fail closed.

That is the next real design pressure for the template language.

## Domain Vocabulary pressure

Historical Domain Vocabulary documents demonstrate why semantic depth and Markdown heading depth cannot be the same concept.

Several documentary questions are represented together as table columns. For example, the questions behind a term's definition, example, ambiguity, and related-term information can be materialized as fields of one row rather than as nested headings.

That means a future Domain Vocabulary template may map:

```text
question
  -> table column
```

while preserving the exact same Docs Standard question identity.

Template Standard may define that layout only after the corresponding Domain Vocabulary question vocabulary is normative in Docs Standard.
