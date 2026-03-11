# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Workshop course materials for Pro Senectute (Swiss senior organization) teaching macOS/Windows 11 basics to seniors. The curriculum is written in AsciiDoc and published to GitHub Pages via GitHub Actions.

## Build

To build HTML locally from the AsciiDoc source:

```bash
mkdir -p build
find docs -name "*.adoc" -exec asciidoctor -D build {} \;
cp build/kursprogramm.html build/index.html
```

Requires `asciidoctor` to be installed (`brew install asciidoctor` on macOS).

The CI/CD pipeline (`.github/workflows/asciidoctor.yml`) runs this automatically on every push to `main` and deploys to GitHub Pages.

## Architecture

- `docs/kursprogramm.adoc` — the single source document for the entire workshop curriculum (German)
- `.github/workflows/asciidoctor.yml` — converts `.adoc` → HTML, deploys to GitHub Pages as `index.html`
- `INSTRUCTIONS.md` — workshop metadata (reference videos, Pro Senectute course links, schedule)

## Content Notes

- Language: German (Swiss German conventions)
- The `.adoc` file header currently references "Windows 11 Grundkurs" though the repository is named `mac-basic-workshop` — this is a known inconsistency
- 2-day workshop, 3 hours/day (09:00–12:00), 6 modules total with ~19 practical exercises
