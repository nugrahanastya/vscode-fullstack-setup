# The Ultimate Full-Stack VS Code Setup

A production-grade VS Code workspace kit for full-stack developers. Not just a list of extensions — this is a complete development environment with smart defaults, custom snippets, debug configs, CI pipelines, AI coding rules, git hooks, and API testing tools.

Built for people who use VS Code (or forks like Cursor, Windsurf, etc.) as their daily driver.

---

## Quick Start

```bash
git clone https://github.com/nugrahanastya/vscode-fullstack-setup.git
cd vscode-fullstack-setup
```

Open the folder in VS Code. A notification will ask if you want to install recommended extensions — click **Install**. Done.

Everything else (formatting, linting, snippets, debug configs) activates automatically when you're inside this workspace.

---

## What's Inside

This repo is modular. Copy the entire `.vscode/` folder into any project to get the full experience, or cherry-pick individual files based on what you need.

| File / Folder | What it does | Pick if you... |
|---|---|---|
| `.vscode/extensions.json` | Recommends 15 extensions on open | Want a curated, zero-bloat extension set |
| `.vscode/settings.json` | Auto-format, auto-lint, file nesting | Want consistent settings across machines |
| `.vscode/fullstack.code-snippets` | Custom code generators (`!btn-tailwind`, etc.) | Want to scaffold boilerplate instantly |
| `.vscode/launch.json` | One-click debug for Node, Vite, Next.js | Want to stop using `console.log` for debugging |
| `.vscode/tasks.json` | Run dev server, lint, format via `Ctrl+Shift+B` | Want terminal shortcuts inside VS Code |
| `.github/copilot-instructions.md` | Rules for GitHub Copilot AI | Want Copilot to follow your coding standards |
| `.cursorrules` | Rules for Cursor AI | Use Cursor IDE instead of VS Code |
| `.github/workflows/ci.yml` | Automated CI pipeline on push/PR | Want GitHub to auto-check your code quality |
| `.husky/pre-commit` | Block bad commits locally | Want a safety net before pushing broken code |
| `.editorconfig` | Cross-editor formatting consistency | Work with people who don't use VS Code |
| `.commitlintrc.json` | Enforce `feat:` / `fix:` commit messages | Want clean git history and auto-changelogs |
| `.env.example` | Template for environment variables | Want new teammates to onboard without guessing |
| `.gitignore` | Comprehensive ignore rules | Starting a new Node/React project |
| `requests/api.http` | Test API endpoints from inside VS Code | Want to ditch Postman |
| `fullstack.code-workspace` | Multi-root workspace for monorepos | Have separate frontend/ and backend/ folders |
| `keybindings.md` | Keyboard shortcuts cheat sheet | Want to code faster without touching the mouse |

---

## Extensions Breakdown

### Formatting & Code Quality
- **Prettier** (`esbenp.prettier-vscode`) — Hit save, code gets formatted. No debates about style.
- **ESLint** (`dbaeumer.vscode-eslint`) — Catches bugs and enforces patterns before runtime.
- **Error Lens** (`usernamehw.errorlens`) — Shows errors inline, right on the line where they happen. No more hovering over squiggly lines.
- **EditorConfig** (`editorconfig.editorconfig`) — Makes sure tabs, line endings, and charset stay consistent even across different editors.

### Frontend Velocity
- **Auto Rename Tag** (`formulahendry.auto-rename-tag`) — Change `<div>` to `<section>`, closing tag follows automatically.
- **Tailwind CSS IntelliSense** (`bradlc.vscode-tailwindcss`) — Autocomplete for Tailwind classes, shows computed CSS on hover.
- **Live Server** (`ritwickdey.liveserver`) — Local dev server with hot reload for vanilla HTML/CSS projects.
- **Import Cost** (`wix.vscode-import-cost`) — Shows the bundle size of every `import` statement inline. Keeps you honest about performance.

### JavaScript & React
- **Path Intellisense** (`christian-kohler.path-intellisense`) — Autocompletes file paths in `import` statements.
- **ES7+ Snippets** (`dsznajder.es7-react-js-snippets`) — Type `rfce` → full React component. Type `useState` → full hook setup.

### AI Assistants
- **GitHub Copilot** (`github.copilot`) — AI pair programmer that autocompletes code based on context.
- **Codeium** (`Codeium.codeium`) — Free alternative to Copilot. Fast, accurate, no subscription needed.

### Git & Visual
- **GitLens** (`eamodio.gitlens`) — See who wrote each line, when, and in which commit. Full git history without leaving the file.
- **VSCode Icons** (`vscode-icons-team.vscode-icons`) — Distinct icons for every file type. Your sidebar becomes instantly scannable.

### API Testing
- **REST Client** (`humao.rest-client`) — Send HTTP requests directly from `.http` files. No Postman needed.

---

## Custom Snippets

Open any `.tsx` or `.ts` file in VS Code and type these prefixes:

| Prefix | What you get |
|---|---|
| `!btn-tailwind` | A glassmorphism button component with Framer Motion hover/tap animations and Tailwind styling. |
| `!api-next` | A Next.js App Router API route with GET handler, try/catch error handling, and proper status codes. |
| `!rfc-type` | A TypeScript React functional component with a typed Props interface. |

Want to add your own? Edit `.vscode/fullstack.code-snippets` and follow the same pattern.

---

## AI Coding Instructions

Two files control how AI assistants behave in your codebase:

- **`.github/copilot-instructions.md`** — Read by GitHub Copilot when generating suggestions.
- **`.cursorrules`** — Read by Cursor IDE's AI features.

Both files contain the same rules by default. They tell the AI things like:
- Always use TypeScript strict mode
- Prefer named exports over default exports
- Use early returns to reduce nesting
- Never use `any`, `// @ts-ignore`, or `console.log` in production
- Validate API inputs with Zod

**To customize:** Open either file and edit the rules to match your stack and preferences. The AI will follow whatever you write.

---

## Debug Configurations

Press `F5` or go to Run & Debug (`Ctrl+Shift+D`) to see three ready-to-use configs:

1. **Launch Node.js Script** — Debug any `index.js` backend file with breakpoints.
2. **Launch Chrome against localhost** — Attach the VS Code debugger to a running Vite/React app on port 5173.
3. **Debug Next.js (Server-side)** — Debug Next.js server components and API routes.

---

## VS Code Tasks

Press `Ctrl+Shift+B` to see available tasks:

| Task | What it runs |
|---|---|
| Dev Server (Frontend) | `npm run dev` with Vite problem matcher |
| Build Project | `npm run build` (default build task) |
| Lint Fix | `npx eslint . --fix` |
| Format All Files | `npx prettier --write` on everything |
| Type Check | `npx tsc --noEmit` |
| Clean Install | Nukes `node_modules` and reinstalls fresh |

---

## Git Hooks (Husky)

The `.husky/pre-commit` script runs three checks before every commit:
1. TypeScript type check (`tsc --noEmit`)
2. ESLint lint (`eslint --max-warnings 0`)
3. Prettier format check (`prettier --check`)

If any check fails, the commit is blocked until you fix the issue. To activate this in a real project, run:

```bash
npm install -D husky
npx husky init
cp .husky/pre-commit .husky/pre-commit
```

---

## CI/CD Pipeline

The `.github/workflows/ci.yml` file runs on every push and pull request:
1. Installs dependencies (`npm ci`)
2. Runs TypeScript type check
3. Runs ESLint
4. Runs Prettier format check
5. Builds the project

If everything passes, you get a green checkmark on your PR. If something fails, GitHub tells you exactly what broke.

---

## REST Client

Instead of switching to Postman or Insomnia, use the `requests/api.http` file. Click "Send Request" above any endpoint to fire it directly from VS Code.

The file includes templates for:
- Health checks
- Auth (register/login)
- CRUD operations (GET, POST, PATCH, DELETE)
- File uploads

Edit the URLs and payloads to match your own API.

---

## How to Use This in Your Projects

**Option A: Copy everything**
```bash
cp -r vscode-fullstack-setup/.vscode your-project/
cp vscode-fullstack-setup/.editorconfig your-project/
cp vscode-fullstack-setup/.gitignore your-project/
cp vscode-fullstack-setup/.env.example your-project/
```

**Option B: Cherry-pick what you need**

Only want snippets and settings? Just copy `.vscode/settings.json` and `.vscode/fullstack.code-snippets`. Each file works independently.

**Option C: Fork and customize**

Fork this repo, edit the AI instructions and snippets to match your stack, and use it as a template for every new project.

---

## Contributing

Found a useful snippet or setting? Open a PR. The bar is simple: if it saves time and doesn't add bloat, it belongs here.

## License

MIT — do whatever you want with it.
