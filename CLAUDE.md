# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Core Development
- `pnpm dev` - Start development server
- `pnpm build` - Build production version
- `pnpm preview` - Preview production build

### Code Quality
- `pnpm lint` - Run Prettier and ESLint checks
- `pnpm format` - Format code with Prettier
- `pnpm check` - Run Svelte type checking
- `pnpm check:watch` - Run Svelte type checking in watch mode

### Testing
- `pnpm test` - Run all tests once
- `pnpm test:unit` - Run tests in watch mode
- Tests use Vitest with two environments:
  - Browser tests: `*.svelte.{test,spec}.{js,ts}` files (uses Playwright)
  - Node tests: `*.{test,spec}.{js,ts}` files (excludes Svelte tests)

## Project Architecture

### Tech Stack
- **Framework**: SvelteKit with Svelte 5
- **Language**: TypeScript with strict mode
- **Styling**: Tailwind CSS v4
- **Testing**: Vitest with browser testing via Playwright
- **Build**: Vite
- **Deployment**: Vercel adapter configured
- **Package Manager**: pnpm

### Project Structure
```
src/
├── routes/           # SvelteKit routes
│   ├── +layout.svelte    # Root layout
│   └── +page.svelte      # Home page
├── lib/              # Shared utilities and components
├── app.html          # HTML template
├── app.css           # Global styles
└── app.d.ts          # TypeScript declarations
```

### Key Configuration Details
- Uses Vercel adapter for deployment
- Tailwind CSS v4 integrated via Vite plugin
- ESLint configured with TypeScript, Svelte, and Prettier
- Prettier configured with 4-space indentation, double quotes, 100 character line width
- Vitest configured with separate browser and node test environments
- TypeScript strict mode enabled with modern module resolution

### Testing Strategy
- Component tests use `vitest-browser-svelte` with Playwright
- Server/utility tests run in Node environment
- Test files follow naming convention: `*.{test,spec}.{js,ts}` for Node, `*.svelte.{test,spec}.{js,ts}` for browser