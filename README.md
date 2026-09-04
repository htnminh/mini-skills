# Mini Skills

Small, focused skills for coding agents. Each does one job, lives in one readable `SKILL.md`, and can be installed independently.

Mini Skills is deliberately not an agent framework. It has no runtime, hooks, scripts, background services, or required companion agents. The skills use only `name` and `description` frontmatter so they remain useful across different coding harnesses.

## Skills

| Skill | What it does | Use it when |
|---|---|---|
| [commit-push](./skills/commit-push/SKILL.md) | Reviews the working tree, creates a Conventional Commit, and pushes safely. | You want to ship all current changes without repeating the Git ceremony. |
| [handoff](./skills/handoff/SKILL.md) | Writes a secure, resumable conversation handoff into the operating system's temporary directory. | You want another session, agent, or harness to continue without rediscovering context. |
| [learn-by-doing](./skills/learn-by-doing/SKILL.md) | Builds a scratch project and teaches one concept per runnable file, leaving at most 3 lines for you to write. | You want to learn a framework or concept hands-on instead of being handed finished code. |
| [orchestrate](./skills/orchestrate/SKILL.md) | Routes coding work across implementation, exploration, lightweight analysis, and final-review agents. | You explicitly want coordinated sub-agents for a coding task. |
| [question](./skills/question/SKILL.md) | Splits the message into tasks and keeps the one it is attached to read-only. | You want one request investigated rather than implemented, without freezing the rest of the message. |
| [read-only](./skills/read-only/SKILL.md) | Keeps an entire turn strictly read-only, however the message is phrased. | You want investigation only, with no chance of a change slipping through. |
| [save-memory](./skills/save-memory/SKILL.md) | Writes durable knowledge into every memory store the harness has, including instruction files. | You want the next session to start with what this one learned instead of rediscovering it. |
| [tldr](./skills/tldr/SKILL.md) | Answers a question or summarizes the previous response in under 15 words, without tool calls. | You want the shortest possible answer instead of a full write-up. |
| [verify-brainstorm](./skills/verify-brainstorm/SKILL.md) | Checks whether the premise is sound before generating and comparing options. | You want to think through a problem or decision before anyone starts building. |
| [wait-what](./skills/wait-what/SKILL.md) | Re-explains the previous message in Simplified Technical English using the project's own terminology. | The agent's last message did not land and you want it re-pitched clearly. |
| [wrap-up](./skills/wrap-up/SKILL.md) | Closes a session with a persistent chronological audit log, then saves what is worth carrying forward. | You are finishing up and want the session's history kept and its knowledge preserved. |

## Why mini?

- One clear job per skill.
- One Markdown file per skill.
- No hidden dependencies.
- Install only what you want.
- Existing skills are never overwritten automatically.
- Stronger maintained skills are linked instead of repackaged.

## Install

Paste this into the coding agent where you want the skills installed:

```text
Run `curl -fsSL https://raw.githubusercontent.com/htnminh/mini-skills/main/install.md`, then follow the returned instructions.
```

You can review the instructions first in [install.md](./install.md).

## Related skills and inspiration

These maintained skills are not bundled; the installer asks whether you also want to install them:

- [Caveman by Julius Brussee](https://github.com/JuliusBrussee/caveman) keeps agent responses terse without sacrificing technical meaning.
- [Grilling by Matt Pocock](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling) pressure-tests plans one decision at a time.
- [Show Me by HumanLayer](https://github.com/humanlayer/skills/blob/main/plugins/show-me/skills/show-me/SKILL.md) explains the current topic visually with diagrams, code-shape sketches, and focused HTML artifacts.

Two bundled skills started from Matt Pocock's work: `handoff` was inspired by [his handoff skill](https://github.com/mattpocock/skills/blob/main/skills/productivity/handoff/SKILL.md) and independently expanded around secure, cross-harness continuation, and `wait-what` adapts [his wait-what skill](https://github.com/mattpocock/skills/blob/main/skills/productivity/wait-what/SKILL.md) with portable frontmatter only, project-agnostic terminology instead of a repo-specific `CONTEXT.md`, and a self-contained ASD-STE100 reminder. Thanks to both authors.

## License

[MIT](./LICENSE)
