## Quick context

This repository is a tiny static birthday-card web page located in `cartão-aniversário/`.
The app is a single HTML file (`index.html`) that includes inline CSS and a small inline script. The only asset is `musica.mp3` which is referenced directly by the `<audio>` element.

## Big picture (what to expect)

- Single-page static site (no build system, no Node/npm config). Edit `index.html` directly.
- Visual structure lives in the `<style>` block in the head; interactive behavior is at the bottom in plain JavaScript (functions `mostrarMensagem()` and `toggleMusica()`).
- Audio is loaded from `musica.mp3` in the same folder and toggled via `document.getElementById('musica')`.

## Files and important symbols to reference

- `cartão-aniversário/index.html` — the whole app. Key selectors and symbols:
  - CSS classes: `.envelope`, `.heart`, `.btn`, `.mensagem` (used for styling and layout)
  - JS functions: `mostrarMensagem()` — reveals the message div (`id="mensagem"`), `toggleMusica()` — plays/pauses the `<audio id="musica">` element
  - Asset: `musica.mp3` — the audio source referenced in `<audio><source src="musica.mp3">`.

## Development / test workflow

1. There is no build step. To preview locally, either open `cartão-aniversário/index.html` in a browser or run a simple static server from the repo root, for example:

```bash
# from /Users/yagosilvamkt/DevClub
python3 -m http.server 8000
# or, if you prefer Node-based servers and have npm installed:
# npx http-server -p 8000
```

2. Then open `http://localhost:8000/cartão-aniversário/` in a browser. Confirm:
  - The page loads and renders the envelope UI
  - Clicking "Abrir Cartão 🎁" reveals the message (`id="mensagem"`)
  - Clicking "🎵 Música" toggles playback of `musica.mp3`

## Project-specific conventions & gotchas

- Filename and path encoding: the folder name contains a non-ASCII character (`cartão-aniversário`). Some tools, CI runners, or URLs may percent-encode or mishandle characters — prefer UTF-8-aware tools and test paths in CI if you later add automation.
- Language is Portuguese (`<html lang="pt-br">`) and the file uses UTF-8 meta charset. Preserve encoding when editing.
- Styles are inline in `index.html`. If you extract CSS/JS, update the single file references and keep relative paths consistent.

## What changes usually look like here

- Small UI tweaks: edit CSS inside the `<style>` block.
- Behavior changes: modify the inline script functions at the bottom of `index.html`.
- Replacing the music: swap `musica.mp3` (keep the same filename or update the `<source>` element accordingly).

## Integration & external dependencies

- There are no external dependencies or third-party services configured. The app depends only on browser capabilities (audio playback, CSS animations).

## Quick examples you can search for when making edits

- Search `mostrarMensagem` to find the message reveal logic.
- Search `musica` to find the audio element and its usage.

## Minimal acceptance criteria for a PR in this repo

1. Page still loads from `cartão-aniversário/index.html` in a browser served from a static server.
2. `Abrir Cartão` reveals the message and remains readable on small screens (simple responsiveness present at max-width:480px).
3. Audio playback toggles when clicking the music button (if you change the audio, ensure the `<audio>` source is correct and accessible).

---

If any part of the project layout or workflows above are incorrect or you want more detail (CI, linting, or a different local server command), tell me which area to expand and I'll update this file.
