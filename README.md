# Live translator: English ⇄ Spanish

Speak in English and read Spanish on screen, or the reverse. No installs, no build step: one HTML file.

## Requirements

- A recent desktop **Chrome** or **Edge** (Chrome 138+ recommended for on-device translation)
- A working microphone
- Internet on first run (Chrome's speech recognition uses its speech service, and the translation model downloads once)

## Run it

1. Put `index.html` in a folder.
2. Serve it locally so Chrome remembers your microphone permission:
   - Python: `python -m http.server 8000` in that folder
   - or Node: `npx serve`
3. Open `http://localhost:8000` in Chrome.
4. Click **Start listening** (or press Space) and allow the microphone.
5. Speak. Gray text is what it heard, large text is the translation. Press **⇄** to flip direction.

Double-clicking the file also works, but Chrome will ask for the microphone each time.

## How it works

- **Speech to text:** the browser's Web Speech API, with interim results, so words show while you are still talking.
- **Translation:** Chrome's built-in Translator API runs on your device (fast, private, offline once downloaded). If it isn't available, the app falls back to the free MyMemory web API.
- Partial sentences are translated after a 180 ms pause, and each finished sentence is translated and saved to the history.

## Quick test checklist

1. English → Spanish: say "Where is the nearest train station?" Expect something like "¿Dónde está la estación de tren más cercana?"
2. Press ⇄, then say "Me gustaría reservar una mesa para dos."
3. Click **Copy translations** and paste to confirm the history.

## Known limits

- Firefox and Safari lack the needed speech recognition, so use Chrome or Edge.
- The speech engine is cloud-based in Chrome, so fully offline use isn't possible.
- The MyMemory fallback is slower and rate-limited; the on-device path is the one to rely on.
- Speech recognition accuracy depends on mic quality and accent, and this tool doesn't add custom vocabulary.
