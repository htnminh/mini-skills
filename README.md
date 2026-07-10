# Mini Skills

Four small, focused skills for coding agents. Each does one job, lives in one readable `SKILL.md`, and can be installed independently.

Mini Skills is deliberately not an agent framework. It has no runtime, hooks, scripts, background services, or required companion agents. The skills use only `name` and `description` frontmatter so they remain useful across different coding harnesses.

## Skills

| Skill | What it does | Use it when |
|---|---|---|
| [commit-push](./skills/commit-push/SKILL.md) | Reviews the working tree, creates a Conventional Commit, and pushes safely. | You want to ship all current changes without repeating the Git ceremony. |
| [handoff](./skills/handoff/SKILL.md) | Writes a secure, resumable conversation handoff into the operating system's temporary directory. | You want another session, agent, or harness to continue without rediscovering context. |
| [question](./skills/question/SKILL.md) | Keeps a turn strictly read-only. | You want investigation, explanation, or debugging analysis without surprise implementation. |
| [verify-brainstorm](./skills/verify-brainstorm/SKILL.md) | Checks whether the premise is sound before generating and comparing options. | You want to think through a problem or decision before anyone starts building. |

## Why mini?

- One clear job per skill.
- One Markdown file per skill.
- No hidden dependencies.
- Install only what you want.
- Existing or overlapping skills are never replaced automatically.
- Stronger maintained skills are linked instead of repackaged.

## Install

Paste this into the coding agent where you want the skills installed:

```text
Run `curl -fsSL https://raw.githubusercontent.com/htnminh/mini-skills/main/install.md`, then follow the returned instructions.
```

You can review the instructions first in [install.md](./install.md).

## Related skills and inspiration

Mini Skills intentionally does not bundle these excellent maintained skills:

- [Caveman by Julius Brussee](https://github.com/JuliusBrussee/caveman) keeps agent responses terse without sacrificing technical meaning.
- [Grill Me by Matt Pocock](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me), together with its shared [Grilling](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling) primitive, pressure-tests plans one decision at a time.

Inspired by [Matt Pocock's handoff skill](https://github.com/mattpocock/skills/blob/main/skills/productivity/handoff/SKILL.md); this version was independently expanded around secure, cross-harness continuation.

Massive respect to both authors for publishing the ideas that helped shape this collection.

## License

[MIT](./LICENSE)
