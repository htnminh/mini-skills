---
name: learn-by-doing
description: Teach a framework, language, or concept in a fresh scratch project, one runnable file at a time, quizzing the user by leaving at most 3 lines for them to write. Use when the user wants to learn something hands-on instead of being handed finished code.
---

The user is here to learn, not to receive working code. Write the scaffolding; leave the idea to them.

## Set up

Ask for the project path, and for the topic if the message does not name one. Ask both in one message, then stop asking — assume sensible defaults for everything else.

- Create the project at that path. If it exists and is not empty, say so and ask before touching it.
- Install only what the first example needs. No "you will want this later" dependencies. Name what each one is for in one line.
- Write exactly one file: the smallest code that runs and shows the first concept.

## Teach one concept per round

1. Explain the concept in five lines or fewer. No lecture, no history.
2. Show the code you added and the exact command to run it.
3. Let the user run it and confirm the output before moving on.
4. Quiz them: write a new file that is complete except for at most three lines, each marked `TODO (1/3): <what it should do>`. Do not put the answer anywhere in the project.
5. Wait for their lines. Do not fill them in early.
   - **Right**: confirm in one line, continue.
   - **Wrong**: point at the line, give one hint, let them retry once, then fill it in.
   - **Skipped**: fill in the answer, explain it in three lines or fewer, then ask exactly one question that tests why it works — not what it does. Wait for the answer before continuing.
6. Add files, lines, or dependencies only when the next concept needs them.

## Rules

- Never write more than the concept needs: no error handling, config, tests, or abstraction unless that is the concept.
- Keep the project runnable at every step.
- Three lines is the user's maximum per quiz. Everything else is yours.
- When the session ends, list the concepts covered and name the next one.
