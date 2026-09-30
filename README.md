# AimFinder — Sens Finder Collection

[![Wasmer](https://img.shields.io/badge/Deployed%20on-Wasmer%20Edge-7c3aed?style=flat-square)](https://wasmer.io)
[![MIT License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

**AimFinder** is a browser-based collection for finding your optimal mouse sensitivity for VALORANT, CS2, and other FPS games through 3D aim trials. Landing page (`public/index.html`) lets you pick 1 of 10 frozen variants — PSA, Continuous AI, Valorant theme, Calibration Lab, and prototype — plus full docs at `public/docs.html`.

---

## Live Demo

Deployed on Wasmer Edge: [https://aimfinder.wasmer.app](https://aimfinder.wasmer.app)

- Landing: [/index.html](https://aimfinder.wasmer.app/index.html)
- Docs: [/docs.html](https://aimfinder.wasmer.app/docs.html)
- Recommended start: [/sens.html](https://aimfinder.wasmer.app/sens.html) → [/finder.html](https://aimfinder.wasmer.app/finder.html)

## Variants (order = logs.txt)

| # | File | Family | Notes |
|---|------|--------|-------|
| 1 | `chat.html` | PSA | Sens Finder 3D PSA, 743 lines |
| 2 | `play.html` | PSA | Embed-friendly PSA, 742 lines |
| 3 | `gpt.html` | Prototype | AI Aim Optimizer V3, 255 lines |
| 4 | `deep.html` | Continuous AI | Early continuous, 1317 lines |
| 5 | `seek.html` | Continuous AI | Fullscreen 100dvh, 2300 lines |
| 6 | `aim.html` | Continuous AI | Variant, 2013 lines |
| 7 | `finder.html` | Continuous AI | Flagship full layout, 2686 lines |
| 8 | `valo.html` | VALORANT | Valorant theme (#ff4655), 2822 lines |
| 9 | `rant.html` | Lab | Calibration Lab amber, 1858 lines |
| 10 | `sens.html` | Lab latest | Contrast-fix, recommended, 1860 lines |

> Rule: do not edit the 10 variant files. Only `public/index.html` (landing) and `public/docs.html` may change.

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

### Wasmer Edge (Shipit staticfile)

1. Push this repo to GitHub (`yuumuu/aimfinder`).
2. App already exists: `yuumuu/aimfinder` → `https://aimfinder.wasmer.app` (provider `staticfile`, `static_dir: public`, SWS 2.38.0).
3. Manual redeploy via CLI (logged in as `yuumuu`):
```bash
wasmer deploy --non-interactive --build-remote
```
4. Or Redeploy from Wasmer dashboard → Apps → aimfinder.
5. Verify `/index.html`, `/docs.html`, `/sens.html`.

> `app.yaml` (`App.v0`, `package: .`) + `settings/config.toml` (SWS) + `Staticfile` (`root: public`) wajib ada untuk `wasmer deploy --build-remote` (remote Anybuild, preset `staticfile`, SWS 2.38.0).

### Local Development

```bash
# Serve the public/ directory locally
npx serve public
# or
python -m http.server 9000 --directory public
```

## Project Structure

```
aimfinder/
├── public/
│   ├── index.html       # Landing pemilih versi (boleh diubah)
│   ├── docs.html        # Dokumentasi lengkap (baru)
│   ├── chat.html … sens.html  # 10 varian frozen (jangan diubah)
│   └── valo.html
├── settings/
│   └── config.toml      # Static Web Server config (host/port/root)
├── app.yaml             # Wasmer App.v0 (name/owner/package)
├── Staticfile           # root: public
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
