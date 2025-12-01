# Repository Guidelines

This guide explains how to work in this Next.js 16 + TypeScript project so contributions stay consistent and easy to review.

## Project Structure & Module Organization
- `app/` uses the App Router; `layout.tsx` sets fonts/theme, `page.tsx` is the landing view. Add routes as `app/(feature)/page.tsx` and colocate UI in `app/(feature)/components/`.
- `app/globals.css` imports Tailwind CSS v4; prefer utilities over expanding global rules. Shared tokens live in the inline `@theme`.
- Static assets live in `public/`. Configuration sits in `next.config.ts`, `tsconfig.json` (strict, `@/*` alias to repo root), `eslint.config.mjs`, and `postcss.config.mjs`.
- Keep environment-specific values in `.env.local` (not committed). Prefix client-exposed values with `NEXT_PUBLIC_`.

## Build, Test, and Development Commands
- `npm run dev` — start the dev server on port 3000 with hot reload.
- `npm run lint` — run ESLint with Next.js core-web-vitals rules; fix what you can before sending a PR.
- `npm run build` — create a production build in `.next/`.
- `npm run start` — serve the production build; run after `npm run build` to verify deployment readiness.

## Coding Style & Naming Conventions
- TypeScript is strict; type props/returns and prefer explicit `React.FC`-less function components.
- Components use PascalCase; route segment folders are kebab-case; hooks use `useX` names. Shared utilities can live under `app/(components)/` or a new `app/(lib)/`.
- Use Tailwind utilities and theme tokens; limit custom CSS to `globals.css` when unavoidable.
- Follow ESLint guidance; auto-fix with `npm run lint -- --fix` before manual edits. Default indentation is 2 spaces.

## Testing Guidelines
- No test runner is committed yet. When adding tests, prefer React Testing Library with Jest or Vitest, and place specs as `*.test.tsx` alongside the component or under `__tests__/`.
- Cover new logic you introduce; exercise accessibility states for UI and include simple rendering/interaction checks at minimum.
- Until a test suite exists, run `npm run lint` as your pre-flight check.

## Commit & Pull Request Guidelines
- Use short, imperative commit messages (`Add hero section`, `Fix lint errors`), mirroring the existing history.
- PRs should include: a brief summary of changes, linked issue or task ID (if any), screenshots or GIFs for UI updates, and notes on how you validated the change (`npm run lint`, manual steps, upcoming tests).
- Keep PRs scoped and self-contained; mention any follow-up work explicitly.***
