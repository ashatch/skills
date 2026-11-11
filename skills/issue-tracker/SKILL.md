---
name: issue-tracker
description: Track and manage project issues in GitHub Issues, Jira, or a structured Markdown issue folder. Use when creating, triaging, updating, or closing project work; follow the tracker declared in project instructions.
---

# Track project issues

## Select the source of truth

- Before changing an issue, inspect the project's Copilot or other agent instructions for an explicit `Issue tracker` setting. Supported values are `GitHub Issues`, `Jira`, and `Markdown issues`.
- If instructions disagree or do not declare a tracker, ask the user which tracker is authoritative before creating or changing any issue. Do not infer the choice from installed tools, existing issue files, or repository hosting.
- After the user chooses, record `Issue tracker: <chosen value>` in the existing project Copilot/agent instructions. For Jira, also record the project key, for example `Issue tracker: Jira (project key: TRIT)`. If no such file exists, create `.github/copilot-instructions.md` for this setting, preserving any existing project guidance.
- Follow only the declared tracker. If it is unavailable or access is denied, explain the blocker; do not silently fall back, migrate, or mirror issues to another tracker.
- If the user explicitly requests a one-off action in a different tracker, honor that request only for that action. Do not change the project's recorded default unless asked.

## Use GitHub Issues

- Use GitHub Issues as the source of truth when the setting is `GitHub Issues`.
- Search for a matching issue before creating one. Preserve its context and do not invent field values.
- Do not create a matching Markdown issue file.

## Use Jira

- Use Jira as the source of truth when the setting is `Jira`, and use the recorded project key for Jira issues. If no project key is recorded, ask the user which Jira project to use and record its key in the project instructions.
- Search for a matching issue before creating one. Preserve its context and do not invent field values.
- Do not create a matching GitHub issue or Markdown issue file.

## Use structured Markdown issues

Apply this section **only** when the setting is `Markdown issues`. Treat the configured, structured issue folder as the source of truth; do not use hosted tracker APIs or create duplicate hosted records unless the user explicitly asks.

### Set up the issue folder

- Inspect the repository for an existing issue directory, schema, and conventions; follow them. If none exist, use `issues/` with subdirectories by issue type, such as `tasks/`, `stories/`, and `bugs/`.
- Store each issue in its own Markdown file with a stable, descriptive slug, such as `issues/bugs/login-redirect-loop.md`. Check for path collisions and keep paths stable after creation.
- Maintain `issues/index.md` as a directory listing grouped by type or status, with links and short descriptions. Keep it in sync when creating, renaming, or closing issues.

### Write and maintain issues

- Use YAML frontmatter with a descriptive OKF `type` value such as `Task`, `Story`, or `Bug`. Also use `title` and `status`; use `priority`, `created_on`, or labels when useful and consistent with the project.
- Treat fields other than `type` as this tracker's conventions, not OKF requirements. See the [Open Knowledge Format specification](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md) for the full format.
- Keep the body concise and actionable. Include context, desired outcome, and acceptance criteria for tasks or stories. For bugs, capture reproduction steps, expected behavior, and actual behavior.
- Use Markdown links to connect related issues and relevant project files. Record dependencies and blockers clearly.
- Use the project's existing status vocabulary. If none exists, use `open`, `in-progress`, `blocked`, `done`, and `wont-do`. Update status in frontmatter rather than moving the issue file; retain declined issues for history. Once a story, task, or bug is complete, you may delete its file and remove its index entry if the issue is already present in Git history; verify with `git log --follow -- <path>`. If it has never been committed, keep it.
- When updating an issue, preserve its context and edit only what the requested change requires. Do not invent decisions, acceptance criteria, owners, or priorities.

### Collaborate through Git

- Treat issue files and indexes as normal source files: review diffs and collaborate through the repository's existing branch and pull-request workflow.
- Check for concurrent edits before resolving conflicts. Do not discard another contributor's issue changes.
- Commit issue-file changes only when requested or as part of the project's established workflow.
