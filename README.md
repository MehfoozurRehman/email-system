# Email System

A desktop shell for an email tool, built with Electron, React and TypeScript on electron-vite.

**Status:** Starter. The repo is the electron-vite React and TypeScript template with its build, lint and packaging setup in place. The renderer still shows the template's welcome screen, and the main process only opens one window. No email features exist yet.

## The problem

The intent, from the repo name, is a desktop app for email work. The code does not yet show what that means: there is no mail account setup, no sending or reading, and no storage. What is in place is the desktop shell that such an app would be built on.

## What it does

- **Opens a desktop window:** `src/main/index.ts` creates a `BrowserWindow`, loads the Vite dev server in development or the built HTML in production, and reopens the window on macOS when the dock icon is clicked.
- **Shows app and runtime versions:** `src/renderer/src/components/Versions.tsx` displays the Electron, Chrome and Node versions through the preload bridge.
- **Opens developer tools:** in development, F12 toggles DevTools through `electron-toolkit`'s window shortcut watcher.
- **Packages installers:** `electron-builder` is configured for Windows, macOS and Linux, with icons in `build/` and `resources/`.

## How it's built

- Electron with electron-vite, which builds the main process, the preload script and the React renderer separately.
- React 18 and TypeScript in the renderer, with separate TypeScript configs for the Node and web sides (`tsconfig.node.json` and `tsconfig.web.json`).
- A preload script in `src/preload/index.ts` exposes a small API to the renderer, following Electron's context isolation model.
- ESLint, Prettier and `typecheck:node` and `typecheck:web` scripts are set up.

## Running it locally

Requires Node.js. The project uses pnpm in the lockfile, and yarn or npm also work.

```bash
npm install
npm run dev          # electron-vite dev
npm run typecheck    # both TypeScript projects
npm run build:win    # or build:mac, build:linux
```

## What's left

- The renderer still shows the template welcome text and links in `src/renderer/src/App.tsx`.
- No email features are built: no account setup, no reading, sending or storage.
- The app name and the `setAppUserModelId` value are still template defaults (`com.electron`).
- No tests exist.
