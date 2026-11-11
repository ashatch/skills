---
name: skill-authoring
description: Guides writing Agent Skills, covering SKILL.md frontmatter, directory structure, instruction style, supporting files, and validation with skills-ref. Use when creating, revising, or reviewing a skill or its SKILL.md.
---

Use [the specification](references/specification.md) as the source of truth for skill format, metadata, directory structure, supporting files, and validation.

Write the skill body as instructions for the person or agent using it, not as a description of what an agent should do.

- Address the reader directly with clear imperatives: “Ask the user to review the test” rather than “The agent should ask the user to review the test.”
- State when an instruction applies, then give the action to take. Include decision points or exceptions when they affect the behavior.
- Make each skill as concise as possible while still complete. Remove repetition, keep instructions specific, and move detailed reference material to supporting files. Explain rationale only when it helps the reader make the right decision.
- Use bullets for concise, scannable guidance. Use numbered steps only when the order genuinely matters.
- Write the front-matter `description` to explain what the skill does and when to use it, using specific terms that help agents recognize relevant tasks.

For example, write “During exploration, prefer to work without tests. For production changes, define or review the expected behavior before writing tests.” Avoid abstract descriptions such as “Agents can use TDD for production code.”

Keep `SKILL.md` focused on the instructions needed when the skill is activated. Put detailed material in supporting files and refer to them with relative links, as described in [the specification](references/specification.md). Keep links one level deep from `SKILL.md`.

Place each skill directory one level deep (for example `skill-name/SKILL.md`), not inside grouping folders. The specification doesn't say whether agents scan sub-directories, so a nested skill may not be discovered.

After creating or revising a skill, run `skills-ref validate ./<skill-name>` to check the frontmatter and naming. See [sources](references/sources.md) for the specification source and complementary writing guidance.
