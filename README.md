#  🎵 Emotion Spectrum V2 — AI Acoustic Fusion Music Visualizer

Real-time music visualization with AI-powered mood detection, featuring **Meyda acoustic feature extraction**, **KNN instance learning**, and **dual-engine dynamic fusion** architecture.

**👉Try it online**: [vercel](https://music-visualizer-02.vercel.app/) [maoziyun](https://musicvisualizer02-5svan014b.maozi.io/)

## Features

- **AI Acoustic Fusion Engine** — Meyda extracts 16-dim feature vectors (13 MFCC + spectralCentroid + spectralRolloff + RMS), KNN classifies mood in high-dimensional space
- **Dual-Engine Dynamic Gating** — Rule-based baseline fused with KNN AI predictions via energy × confidence gate, ensuring visual stability
- **5 Mood Modes** — Energetic, Melancholy, Serene, Joyful, Ethereal with unique visual signatures
- **11 Visual Layers** — Background, Stars, Aurora, Rays, Geometry, Spectrum, Particles, Connections, Ripples, Waveform, Flash + Center Glow
- **AI Status Panel** — Real-time Meyda/KNN status indicators and AI gate percentage display
- **MIDI Playback** — Play `.mid`/`.midi` files with Salamander Grand Piano samples via Tone.js
- **Audio File Support** — MP3, WAV, OGG, FLAC with native playback
- **Microphone Input** — Real-time visualization from your mic
- **i18n** — English / Chinese toggle

## Architecture

```
Audio Input → Web Audio API
               ├→ AudioAnalyzer (RMS, brightness, bassRatio) → Rule Baseline Weights
               └→ Meyda (16-dim feature vector @15Hz) → KNN Classifier (@8Hz) → AI Weights
                                                                    ↓
                                              Dynamic Gate = energyGate × confidenceGate
                                                                    ↓
                              Final Weights = Rule Baseline × (1-gate) + AI Weights × gate
                                                                    ↓
                                    11 Visual Layers (smooth interpolation @60fps)
```

## Tech Stack

- Vanilla HTML/CSS/JavaScript (zero build step)
- [Meyda](https://meyda.js.org/) — Web Audio feature extraction (MFCC, spectral features)
- [Tone.js](https://tonejs.github.io/) + [@tonejs/midi](https://github.com/Tonejs/Midi) — MIDI synthesis
- Web Audio API — Real-time audio analysis
- Canvas 2D — Rendering
- [Tailwind CSS](https://tailwindcss.com/) (CDN)
- [Font Awesome](https://fontawesome.com/) (CDN)

## Quick Start

```bash
# Install dependencies (for local dev server only)
npm install

# Start local server
npm start
```

Or simply open `index.html` in a browser.

## Deploy to Vercel

1. Push this folder to a GitHub repository
2. Import the repo on [vercel.com](https://vercel.com)
3. Vercel will auto-detect the static site and deploy

## Deploy to GitHub Pages

1. Push to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, root directory `/`
4. Your site will be live at `https://<username>.github.io/<repo>/`

## CDN Fallback Strategy

Meyda is loaded from multiple CDN sources with automatic fallback:
1. jsDelivr (primary)
2. cdnjs (fallback 1)
3. unpkg (fallback 2)

If all CDN sources fail, the visualizer gracefully falls back to rule-based mood classification (AI features disabled).

## License

MIT License - See [LICENSE](../LICENSE) for details.

---



## ⚠️ Copyright Notice

© 2026 Jeffrey Zhou. All rights reserved.

This repository and its contents are protected by copyright law.  
No part of this project may be copied, reproduced, modified, or distributed without prior written permission from the author.

Commercial use is strictly prohibited.


*Built with ❤️ for music education*


---
