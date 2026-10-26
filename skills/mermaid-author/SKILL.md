---
name: mermaid-author
description: Express processes and software behavior in standard Mermaid syntax. Use when authoring or reviewing diagrams to choose meaningful blocks, branches, loops, asynchronous flows, tooltips, and links between diagrams.
---

# Mermaid Author

Turn the user's knowledge into diagrams that are simple to follow, precise, and useful beyond a high-level summary. Use standard Mermaid `.mmd` syntax and preserve the user's language and established conventions. This skill is about expressing meaning through notation and works independently of any editor.

## Start with the supplied meaning

- Identify what is being explained: one function, a use case, an interaction, or a lifecycle. Work from the supplied description; read the relevant implementation when asked to document code. Distinguish proposed behavior from existing behavior and leave unknown details explicit.
- Preserve the meaningful actions, inputs, outcomes, conditions, side effects, and their order. Do not add business rules, retries, error handling, or guarantees merely to make the diagram look complete.
- Choose `flowchart` for an algorithm, `sequenceDiagram` for who communicates with whom and in what order, `stateDiagram-v2` for legal state transitions, and `erDiagram` for data relationships. Use the type that answers the reader's question.

## Translate meaning into notation

Read [references/notation.md](references/notation.md) for the block-selection table and patterns for conditions, loops, async work, tooltips, and child diagrams. The linked [load-profile](examples/load-profile.mmd) and [merge-profile](examples/merge-profile.mmd) examples illustrate an HTTP call, database read, decision, and local function call; their fictional behavior is not a template to impose on unrelated processes.

- Choose each shape by what the step does: rectangle for local work, diamond for a decision, subroutine for a function or remote call, cylinder for a database operation, horizontal cylinder for a queue interaction, and terminator for a start or an outcome. Name the operation and object: “Read active zones” conveys more than “Database”.
- Keep a node to one meaningful action, condition, or outcome. Group routine steps when their order and effects remain clear. Expose decisions that change the path; a generic “Process request” box must not hide the algorithm the diagram is meant to explain.
- Label decision exits with complementary conditions or explicit cases. Show a retry as a back-edge with its actual continuation and stop conditions. Show a failure as an outcome or a recovery path, not just a differently styled arrow.
- Distinguish a choice from concurrency. For asynchronous work, show the dispatch point, the continuing caller, and the worker's own outcome. Draw a join only when the caller actually waits. Queue acceptance is not consumer completion.
- Use a child diagram for a cohesive operation whose internals would obscure the parent. Keep the call, relevant result checks, and caller-specific handling visible in the parent. There is no fixed node limit and no need to split trivial assignments into files.
- Put secondary explanations in tooltips: lookup criteria, field meanings, constraints, or why a step exists. Keep actions, branches, failure paths, transaction boundaries, and completion conditions visible when they matter to the explanation.

## Write portable MMD

- Use stable descriptive IDs such as `load_user` and `has_access`, with quoted human-readable labels. Use `finish` instead of the reserved lowercase `end` as a node ID.
- Prefer one node declaration and one edge per line. Use `TD` or `LR` consistently. Add a frontmatter `title` and short `%% Input:` / `%% Returns:` comments when they help establish the scope.
- Use `click node href "./child.mmd" "Short explanation"` for a linked node. For an unlinked node, an HTML label with `title` provides a hint where HTML labels are supported. Do not invent tooltip properties, fake links, or callbacks.
- Resolve child links relative to the containing file and use real targets. Preserve inbound references when moving files. A navigation link identifies another diagram; it does not itself specify waiting, a return, or asynchronous execution.
- Shapes and line styles express authoring conventions. HTTP, gRPC, queues, and async behavior gain their meaning from clear labels and paths; Mermaid does not execute them or enforce their semantics.

## Review the expression

Check whether the diagram expresses the supplied knowledge faithfully: appropriate shapes, clear branch labels, meaningful ends, explicit loop/async behavior, and correct child references. Make the intended control flow understandable without opening every tooltip. State any unresolved meaning briefly.

An authoring or notation review does not by itself request a broader audit of the application's business rules. Compare against other requirements or implementation only when that is part of the user's task. Keep edits within the requested diagrams or documentation.
