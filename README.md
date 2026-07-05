# Sens Finder

[![Wasmer](https://img.shields.io/badge/Deployed%20on-Wasmer%20Edge-7c3aed?style=flat-square)](https://wasmer.io)
[![MIT License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

**Sens Finder** is a browser-based tool that helps you find your optimal mouse sensitivity for VALORANT and other FPS games through data-driven aim trials. It automatically tests 5 sensitivity points around your current setting using Flick, Tracking, and Switching exercises — then recommends the best value based on your performance and playstyle.

---

## Live Demo

Deployed on Wasmer Edge: [https://aimfinder.wasmer.app](https://aimfinder.wasmer.app)

## Features

- **Flick Test** — 8 targets appear one by one at random positions. Click as fast and accurately as possible.
- **Tracking Test** — A single target moves for 8 seconds. Keep your crosshair on it.
- **Switching Test** — 2 targets alternate. Click the active one as fast as possible.
- **Playstyle Weights** — Choose Duelist, Balanced, or Sentinel priority for weighted recommendations.
- **Data-Driven** — Results are normalized and scored based on accuracy, reaction time, and consistency.

## How It Works

| Sens Multiplier | Value (base 0.4) |
|----------------|------------------|
| 0.5×           | 0.2              |
| 0.75×          | 0.3              |
| 1×             | 0.4              |
| 1.25×          | 0.5              |
| 1.5×           | 0.6              |

The tool runs all 3 tasks at each sensitivity level and calculates a composite score using:

```
score = (flick * weight_flick + tracking * weight_tracking + switching * weight_switching) × 0.85
        + consistency × 0.15
```

## Deployment

### Wasmer Edge (via GitHub)

1. Fork or push this repository to GitHub.
2. Connect your repo in [Wasmer Edge Dashboard](https://wasmer.io/apps).
3. Wasmer automatically detects this as a static site from the `wasmer.toml` configuration.
4. Your site is live at `https://<app-name>-<owner>.wasmer.app`.

### Local Development

```bash
# Serve the public/ directory locally
wasmer run . --net -- --port 9000
# or use any static file server
npx serve public
```

## Project Structure

```
aimfinder/
├── public/
│   └── index.html       # Main application (single-file)
├── settings/            # Wasmer runtime settings
├── wasmer.toml          # Wasmer package configuration
├── app.yaml             # Wasmer app configuration
├── Staticfile           # Static web server config
├── README.md
├── LICENSE
└── .gitignore
```

## Tech Stack

- **Vanilla JS** — No framework, no build step, no dependencies.
- **HTML5 Canvas** — Real-time rendering for aim trials.
- **CSS Custom Properties** — Dark theme with accent colors.
- **Pointer Lock API** — Native mouse input during tests.

## Disclaimer

This tool provides an initial estimate based on browser aim tests, which differ from actual in-game conditions (input lag, engine, crosshair resolution, etc.). Use the results as a starting point and fine-tune manually during real gameplay sessions.

---

---

# Sens Finder — Bahasa Indonesia

**Sens Finder** adalah alat berbasis browser untuk menemukan sensitivitas mouse optimal di VALORANT dan game FPS lainnya melalui uji coba aim berbasis data. Sistem otomatis menguji 5 titik sensitivitas di sekitar pengaturan Anda saat ini menggunakan latihan Flick, Tracking, dan Switching — lalu merekomendasikan nilai terbaik berdasarkan performa dan gaya bermain Anda.

## Fitur

- **Flick Test** — 8 target muncul satu per satu di posisi acak. Klik secepat dan seakurat mungkin.
- **Tracking Test** — Satu target bergerak selama 8 detik. Arahkan crosshair agar tetap menempel.
- **Switching Test** — 2 target tampil bergantian. Klik target yang aktif secepat mungkin.
- **Bobot Gaya Main** — Pilih prioritas Duelist, Balanced, atau Sentinel untuk rekomendasi tertimbang.
- **Berbasis Data** — Hasil dinormalisasi dan diskor berdasarkan akurasi, reaction time, dan konsistensi.

## Lisensi

MIT
