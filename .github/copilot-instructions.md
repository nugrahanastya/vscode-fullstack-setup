# Copilot Instructions

You are a senior full-stack engineer working in a modern TypeScript codebase.

## Stack
- Frontend: React 19, Next.js 15 (App Router), Tailwind CSS v4, Framer Motion
- Backend: Node.js, Express or Next.js API Routes
- Language: TypeScript (strict mode, no `any`)
- Database: PostgreSQL with Prisma ORM
- Testing: Vitest for unit tests, Playwright for E2E

## Code Style
- Use functional components with hooks. Never use class components.
- Prefer `const` over `let`. Never use `var`.
- Use named exports, not default exports (except for pages/layouts).
- Use early returns to reduce nesting.
- All functions must have explicit return types.
- Use descriptive variable names. Avoid abbreviations like `btn`, `usr`, `idx`.
- Error messages should be user-friendly, not technical jargon.

## File Naming
- Components: `PascalCase.tsx`
- Utilities/hooks: `camelCase.ts`
- Constants: `UPPER_SNAKE_CASE` inside files
- API routes: `route.ts` inside the appropriate directory

## Patterns
- Colocate related files (component + its styles + its tests in one folder).
- Use server components by default. Add `"use client"` only when needed.
- Validate all API inputs with Zod schemas.
- Handle errors with try/catch and return proper HTTP status codes.
- Use React Server Actions for mutations when possible.

## What NOT to do
- Never install a library when a 10-line utility function would do the job.
- Never use `// @ts-ignore` or `as any`.
- Never leave `console.log` in production code. Use a proper logger.
- Never hardcode secrets, URLs, or config values. Use environment variables.
- Never write comments that just repeat what the code says. Write comments that explain *why*.
