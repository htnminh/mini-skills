# Install Mini Skills

Follow these instructions as the coding agent currently talking to the user.

## Scope

- Install skills only for the harness currently running this conversation.
- Use that harness's canonical user-level skills directory.
- Do not install into every detected agent or harness.
- If the current harness does not support skills, explain that and make no changes.
- If the correct directory cannot be determined confidently, ask the user before writing.

## Bundled skills

Install from these source files:

- `commit-push`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/commit-push/SKILL.md
- `handoff`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/handoff/SKILL.md
- `learn-by-doing`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/learn-by-doing/SKILL.md
- `orchestrate`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/orchestrate/SKILL.md
- `question`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/question/SKILL.md
- `read-only`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/read-only/SKILL.md
- `save-memory`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/save-memory/SKILL.md
- `tldr`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/tldr/SKILL.md
- `verify-brainstorm`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/verify-brainstorm/SKILL.md
- `wait-what`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/wait-what/SKILL.md
- `wrap-up`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/wrap-up/SKILL.md

Each bundled skill intentionally contains only the portable `name` and `description` frontmatter fields. Preserve the files exactly. Do not add harness-specific metadata.

`orchestrate` is Codex-specific. On a non-Codex harness, read its source and prepare an adaptation of the model and sub-agent names to supported equivalents. Offer the adaptation in the closing question and install only the approved adapted version. Do not read other bundled skills unless a same-name comparison requires it.

## Installation procedure

1. Identify the current harness and its canonical user-level skills directory.
2. For each bundled skill, check whether the harness currently loads a skill with the exact same name. Do not inventory or read unrelated skills.
3. Classify and handle each bundled skill:
   - **Clear:** If no same-name skill exists, create `<skills-directory>/<skill-name>/` and use `curl -fsSL <source-url> -o <skills-directory>/<skill-name>/SKILL.md` to download it directly. Do not rewrite or modify the downloaded file.
   - **Already installed:** If a same-name skill exists, download the bundled source to a temporary file and read and compare both files. If their contents are identical, keep the existing skill unchanged.
   - **Name conflict:** If the same-name files differ, keep the existing skill unchanged and do not install the bundled version.
   - **Harness adaptation needed:** Apply this only to `orchestrate` on a non-Codex harness. Keep it uninstalled until the user approves the proposed adaptation, then install only the approved adapted version.
4. Report the installed skills, already installed skills, name conflicts, and any harness adaptation needed briefly. Omit empty categories.

## Related maintained skills

These are not bundled or installed automatically:

- **Caveman by Julius Brussee**
  - Repository: https://github.com/JuliusBrussee/caveman
  - Source: https://raw.githubusercontent.com/JuliusBrussee/caveman/main/skills/caveman/SKILL.md
  - Use it for persistent, token-efficient responses.
- **Grilling by Matt Pocock**
  - Repository: https://github.com/mattpocock/skills
  - Source: https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grilling/SKILL.md
  - Install `grilling` if the user selects this option.
- **Show Me by HumanLayer**
  - Repository: https://github.com/humanlayer/skills
  - Source: https://raw.githubusercontent.com/humanlayer/skills/main/plugins/show-me/skills/show-me/SKILL.md
  - Install `show-me` if the user selects this option.

The external files may contain metadata specific to their authors' preferred harnesses. If a same-name skill is already installed, fetch the source and compare so the closing question can offer an update. Do not install or rewrite them until the user selects them in the closing question, noting any adaptation for the current harness in the option.

## Finish with one closing question

Fetching and reading remote source files is read-only and safe — do it whenever needed to prepare or carry out the options below, without asking first. Only creating or modifying skills requires the user's selection.

After reporting the bundled-skill results, ask a single multiple-choice question covering every pending decision — use the harness's interactive question tool with multiple selection if available, otherwise plain text. Each pending item is one short do-or-not-do option:

> Do you want to:
> - Install `orchestrate` with the proposed adaptation? My recommendation: <sub-agent names + model names>
> - Update `commit-push` to the bundled version?
> - Install `grilling`?
> - Update `caveman`?

Build the list from whatever applies: one option per harness adaptation (state the concrete recommendation inline), one per name conflict, and one per maintained skill that is uninstalled or outdated. Omit options that do not apply. After the user answers, apply exactly the selected options and nothing else.
