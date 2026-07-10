# Install Mini Skills

Follow these instructions as the coding agent currently talking to the user.

## Scope

- Install skills only for the harness currently running this conversation.
- Use that harness's canonical user-level skills directory.
- Do not install into every detected agent or harness.
- If the current harness does not support skills, explain that and make no changes.
- If the correct directory cannot be determined confidently, ask the user before writing.

## Bundled skills

Fetch these source files:

- `commit-push`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/commit-push/SKILL.md
- `handoff`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/handoff/SKILL.md
- `question`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/question/SKILL.md
- `verify-brainstorm`: https://raw.githubusercontent.com/htnminh/mini-skills/main/skills/verify-brainstorm/SKILL.md

Each bundled skill intentionally contains only the portable `name` and `description` frontmatter fields. Preserve the files exactly. Do not add harness-specific metadata.

## Installation procedure

1. Identify the current harness and its canonical user-level skills directory.
2. Inventory every user-level and project-level skill location that this harness currently loads. Read existing skill names and descriptions before changing anything.
3. Fetch all four bundled source files as text. Do not execute remote scripts.
4. Classify each bundled skill:
   - **Already installed:** the same skill and content already exist. Skip it.
   - **Name conflict:** the same name exists with different content. Do not overwrite it.
   - **Semantic overlap:** a differently named existing skill performs substantially the same job. Do not install the bundled skill yet.
   - **Clear to install:** no name conflict or meaningful overlap exists.
5. Install only skills classified as clear:
   - Create `<skills-directory>/<skill-name>/` when needed.
   - Save the fetched file as `SKILL.md`.
6. Do not delete, rename, overwrite, or merge any existing skill during this pass.
7. Report which skills were installed, already present, or held back because of overlap.

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

After installing every clear bundled skill, present:

1. Installed skills.
2. Skills skipped because they were already present.
3. Every conflict or semantic overlap, showing the existing skill and the Mini Skills alternative.
4. The optional maintained skills above.

Then ask one consolidated question:

> Do you want me to resolve any overlaps or install any of the optional maintained skills? I will not replace or adapt anything without your approval.

If the user approves a replacement or external installation, inspect it again, explain the exact change, and modify only the current harness.
