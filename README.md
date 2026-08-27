# Multi-Language Code Editor

A browser-based code editor with syntax highlighting (color coding), line numbers,
language switching, and plain-text export. Built with [CodeMirror 5](https://codemirror.net/5/)
(loaded via CDN) and deployed as a static site on **GitHub Pages**.

## Live Demo

Once GitHub Pages is enabled for this repo, the editor will be live at:

```
https://andredavisme.github.io/multi-language-code-editor/
```

## Features

- **Color-coded syntax highlighting** for:
  - T-SQL (Microsoft SQL Server dialect)
  - PostgreSQL / PL/pgSQL
  - Java
  - JavaScript
  - HTML
  - CSS
  - ANSI SQL
- **Line numbers** synced to the editor gutter
- **Language switcher** dropdown — re-parses and re-colors the buffer instantly
- **Starter templates** per language showing idiomatic structure
- **Bracket matching, auto-closing brackets/tags, active-line highlight**
- **Export to `.txt`** with a custom filename
- Dark theme (Dracula) for readability

## Why CodeMirror + CDN?

This build assumes the app is served from **GitHub Pages**, which is standard static
hosting with full internet access for the end user's browser. That means we can load
CodeMirror's core, language modes, and theme from a CDN (cdnjs) instead of bundling
everything inline — this is what unlocks real color coding versus the offline single-file
version, which had no highlighting because it couldn't assume network access.

If CDN resources fail to load (e.g., no internet), the page falls back to a plain
textarea and shows a warning banner, so the editor still functions without crashing.

## Local Development

Just open `index.html` in a browser — no build step required. To preview exactly as
GitHub Pages will serve it, run a simple local server:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deploying / Updating

1. Push changes to the `main` branch.
2. GitHub Pages (configured to serve from `main` / root) rebuilds automatically.
3. Changes are live within ~1 minute at the Pages URL above.

## Roadmap Ideas

- Add more languages (Python, C#, JSON) by including additional CodeMirror modes.
- Persist editor content to `localStorage` so a refresh doesn't lose work.
- Add a "Copy to clipboard" button alongside export.
- Add light/dark theme toggle.
