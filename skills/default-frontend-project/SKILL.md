---
name: default-frontend-project
description: Scaffold quick frontend apps with Node.js, TypeScript, Vite, React, and Mantine, preferring pnpm and dark mode for new projects. Use when asked to make a quick front end, prototype, or small web UI, especially when no stack is specified.
---

# Quick frontend projects

- When asked to make a quick frontend, prototype, or small web UI, use Node.js, TypeScript, Vite, and React unless the request or an existing project calls for a different stack.
- For new projects, use Mantine as the default component library and configure dark mode as the default color scheme. Follow an existing project's UI library and theme conventions unless the user asks to change them.
- Unless the user specifies otherwise, render a simple "Hello World" in a prominent hero header as the default app screen.
- Make the default layout responsive for both desktop and mobile.
- Inspect the repository first. Preserve existing conventions and files; integrate with the current project instead of replacing its setup.
- For a new project, prefer pnpm unless the user specifies another package manager. In an existing project, follow its lockfile and conventions. Keep dependencies minimal and add libraries only when the request needs them.
- Implement the requested UI and run the project's available checks.
