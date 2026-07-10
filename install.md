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
- `question`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/question/SKILL.md
- `verify-brainstorm`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/verify-brainstorm/SKILL.md

Each bundled skill intentionally contains only the portable `name` and `description` frontmatter fields. Preserve the files exactly. Do not add harness-specific metadata.

## Installation procedure

1. Identify the current harness and its canonical user-level skills directory.
2. For each bundled skill, check whether the harness currently loads a skill with the exact same name. Do not inventory or read unrelated skills.
3. Classify and handle each bundled skill:
   - **Clear:** If no same-name skill exists, create `<skills-directory>/<skill-name>/` and use `curl -fsSL <source-url> -o <skills-directory>/<skill-name>/SKILL.md` to download it directly. Do not rewrite or modify the downloaded file.
   - **Already installed:** If a same-name skill exists, download the bundled source to a temporary file and read and compare both files. If their contents are identical, keep the existing skill unchanged.
   - **Name conflict:** If the same-name files differ, keep the existing skill unchanged and do not install the bundled version.
4. Report the installed skills, already installed skills, and name conflicts briefly. Omit empty categories.

## Related maintained skills

These are not bundled or installed automatically:

- **Caveman by Julius Brussee**
  - Repository: https://github.com/JuliusBrussee/caveman
  - Source: https://raw.githubusercontent.com/JuliusBrussee/caveman/main/skills/caveman/SKILL.md
  - Use it for persistent, token-efficient responses.
- **Grill Me by Matt Pocock**
  - Repository: https://github.com/mattpocock/skills
  - Front door: https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grill-me/SKILL.md
  - Required primitive: https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/grilling/SKILL.md
  - Install both `grill-me` and `grilling` if the user selects this option.
- **Handoff by Matt Pocock**
  - Source: https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/handoff/SKILL.md
  - This inspired Mini Skills' `handoff`, but the two should be treated as overlapping alternatives.

The external files may contain metadata specific to their authors' preferred harnesses. Do not rewrite or install them without showing the user what will be adapted for the current harness.

## Finish with one question

After reporting the bundled-skill results, always present the optional maintained skills above and ask whether the user wants to install any of them.

If any name conflicts were found, include resolving them in the same question:

> Do you want me to resolve any of these name conflicts or install any of the optional maintained skills? I will not replace or adapt anything without your approval.

If there are no name conflicts, ask:

> Do you want me to install any of the optional maintained skills? I will not adapt anything without your approval.

If the user approves resolving a conflict or installing an external skill, inspect the selected files again, explain the exact change, and modify only the current harness.
