# no-ai-slop

A skill that edits drafts into sharper, more human writing while preserving the
writer's personal voice, or detects AI-slop patterns without rewriting.

- `SKILL.md` — the editing rules and workflow.
- `eval.md` — pass/fail checks the skill runs on its own edits.

## Usage

Invoke it on a draft:

```
/no-ai-slop

[your draft]
```

You get back the edited draft plus a short **What changed** section.

Detect mode — ask whether a piece reads as AI, without a rewrite:

```
/no-ai-slop is this AI slop?

[the text]
```

## Source

Vendored from [petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop),
MIT licensed. See `LICENSE`.
