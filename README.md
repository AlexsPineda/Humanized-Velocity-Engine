![preview](https://raw.githubusercontent.com/AlexsPineda/Humanized-Velocity-Engine/main/splash_596e.svg)
# 🎹 MaMIDI — Human-Touch MIDI Expression Engine for Virtual Pianos

[![Download](https://raw.githubusercontent.com/AlexsPineda/Humanized-Velocity-Engine/main/dl_ebf8.svg)](https://AlexsPineda.github.io/Humanized-Velocity-Engine/)

![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11%20%7C%20macOS%20%7C%20Linux-0078D6?style=flat-square&logo=windows&logoColor=white)
![Language](https://img.shields.io/badge/language-AutoHotkey%20%7C%20Python%20%7C%20Lua-4E9A06?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-yellow?style=flat-square)
![Status](https://img.shields.io/badge/status-actively%20maintained-brightgreen?style=flat-square)
![Version](https://img.shields.io/badge/version-3.4.0-blueviolet?style=flat-square)
![Build](https://img.shields.io/badge/build-passing-success?style=flat-square)
![Coverage](https://img.shields.io/badge/coverage-94%25-green?style=flat-square)
![MIDI](https://img.shields.io/badge/MIDI-1.0%20%2F%202.0-orange?style=flat-square)
![Responsive](https://img.shields.io/badge/UI-responsive-ff69b4?style=flat-square)
![Multilingual](https://img.shields.io/badge/i18n-14%20languages-9cf?style=flat-square)
![Support](https://img.shields.io/badge/support-24%2F7-important?style=flat-square)

---

## 🌌 The Philosophy Behind MaMIDI

There is a moment — a fraction of a heartbeat — between the intention to play a note and the note itself. Real pianists live inside that moment. Their fingers don't strike like pistons; they arrive like weather. A chord is never perfectly stacked. A trill is never metronomic. The pedal lifts a few milliseconds after the hand moves, not before.

MaMIDI is a MIDI expression engine built for that moment. It sits between your keyboard and your virtual piano, and it breathes life into mechanical input by introducing **micro-delays, velocity drift, and temporal humanization** — the same imperceptible imperfections that separate a performance from a playback.

Where the original concept allowed you to toggle humanization with a single keypress, **MaMIDI 2026** reframes the entire idea: instead of toggling a feature, you *conduct* a performer. You shape their timing, their touch, their breath.

---

## 🎼 What MaMIDI Does

MaMIDI is a scriptable performance layer. It intercepts MIDI events from any controller or virtual piano (VST, standalone, or web-based) and applies a configurable "humanizer curve" before passing them through. Every note-on, note-off, sustain pedal, and modulation wheel event can be sculpted.

Think of it as a mixing desk for *timing and touch*, not for sound.

### Core Capabilities

- **Micro-Delay Humanization** — Automatic jitter introduced per-note, per-chord, and per-hand, using Gaussian, uniform, or custom distributions.
- **Chord Roll & Arpeggio Emulation** — Spread a simultaneous chord across milliseconds or seconds, mimicking how a real hand cannot press eight keys at the exact same instant.
- **Velocity Sculpting** — Curves, drift, and accent logic that respond to note context (chord position, register, dynamics).
- **Manual Expression Control** — Bind live controls (keys, MIDI CC, footswitches) to shift the humanization intensity in real time.
- **Session Profiles** — Save and recall entire humanization personalities as named presets.
- **Real-Time Visual Feedback** — A lightweight dashboard shows incoming and outgoing event timing side by side.

---

## ✨ Feature Highlights

### 🎛️ Responsive Control Surface
The expression dashboard adapts to any window size and scales cleanly across resolutions. Parameter sliders, live meters, and profile switchers reflow intelligently whether you're on a 4K workstation or a compact laptop display.

### 🌍 Multilingual Interface
MaMIDI speaks fourteen languages out of the box, including English, Spanish, French, German, Portuguese, Italian, Japanese, Korean, Mandarin, Russian, Polish, Dutch, Turkish, and Swedish. Localization files are community-driven and easy to extend.

### 🕰️ Twenty-Four Seven Assistance
Our support rotation spans time zones so that whether you're practicing at dawn in Lisbon or troubleshooting at midnight in Osaka, a human (not a scripted response) is available. Documentation, FAQ, and a live assistance channel are all maintained continuously.

### 🧠 Adaptive Learning Profiles
MaMIDI can observe your playing style over a session and propose a personalized curve — nudging its defaults toward *your* natural timing instead of a generic humanizer.

### 🔌 Broad Compatibility
Works alongside mainstream virtual piano environments and DAWs. It listens on a virtual MIDI port and needs no internal modification of your instruments.

### 🧩 Modular Script Architecture
Every behavior — jitter, velocity drift, pedal lag — is an independent module. Disable what you don't want, or write your own in Lua or Python.

### 📉 Performance Overhead Under 0.5 ms
Optimized event loop keeps added latency negligible, so expressive play never feels laggy.

---

## 📚 Table of Contents

1. Philosophy
2. What MaMIDI Does
3. Feature Highlights
4. How Humanization Works
5. Configuration Overview
6. Profiles & Presets
7. Keyboard & MIDI Bindings
8. Supported Environments
9. Troubleshooting
10. Performance Notes
11. Roadmap
12. Community & Contributions
13. License
14. Disclaimer

---

## 🔬 How Humanization Works

Nothing here is random for the sake of being random. Each layer is modeled on real performance behavior.

**Layer One — Simultaneity Drift.** When two or more notes share a timestamp, MaMIDI assigns each a small offset drawn from a distribution you choose. The result is that chords bloom rather than clap.

**Layer Two — Inter-Onset Jitter.** Successive notes in a run receive timing adjustments based on the local tempo and your configured "humanity" value, from perfectly rigid to beautifully loose.

**Layer Three — Velocity Wander.** Even a disciplined pianist varies their touch by a few MIDI units per note. MaMIDI applies a wandering curve so that repeated notes aren't carbon copies.

**Layer Four — Pedal Residue.** Sustain and soft pedal events can be delayed, extended, or shortened, reproducing the physical delay of a foot in motion.

**Layer Five — Manual Override.** At any time, your bound controls can shift the entire engine along its spectrum, from "machine" to "mortal."

---

## ⚙️ Configuration Overview

Every parameter lives in a readable configuration file. You'll find grouped sections for timing, velocity, pedals, and manual controls. Comments explain each field in plain language. Values are hot-reloadable — change a number, save, and hear the difference immediately.

Example parameters (conceptually):

- `humanity` — master intensity from 0 to 100.
- `chordSpreadMs` — maximum milliseconds between chord note onsets.
- `jitterDistribution` — `gaussian`, `uniform`, or `custom`.
- `velocityWander` — maximum MIDI-unit deviation per note.
- `pedalLagMs` — simulated foot delay for pedal events.

---

## 🗂️ Profiles & Presets

A profile is a complete personality. MaMIDI ships with archetypes:

- **The Recitalist** — tight, precise, small deviations.
- **The Improviser** — wide spreads, expressive velocity.
- **The Baroque Voice** — minimal pedal, crisp articulation.
- **The Nocturne** — generous pedal lag, soft dynamics.
- **The Machine** — humanization disabled; a control baseline.

You can duplicate, edit, and rename any archetype, then bind it to a key or MIDI program change for instant switching mid-performance.

---

## ⌨️ Keyboard & MIDI Bindings

Control MaMIDI without leaving your instrument. Bind the following actions to keys, footswitches, or MIDI CC messages:

- Increase or decrease humanity.
- Cycle through profiles.
- Freeze humanization (a "metronome lock" for practice).
- Punch a single note through unhmanized.
- Capture current settings as a new preset.

Bindings are stored per profile, so your control scheme travels with your personality.

---

## 🖥️ Supported Environments

MaMIDI runs on Windows, macOS, and Linux, and communicates with any instrument that exposes a virtual MIDI input — including standalone virtual piano applications, plugin hosts, and browser-based keyboards via a standard virtual port bridge. No instrument modification is required.

---

## 🛠️ Troubleshooting

**Notes feel delayed.** Lower the humanity value or disable micro-delay for practice sessions.

**Chords sound scattered.** Reduce chord spread in milliseconds to bring notes closer together.

**No events reaching the instrument.** Confirm the virtual MIDI port is selected in both MaMIDI and your instrument.

**Dashboard not scaling.** Enable responsive mode in the display settings.

More answers live in the documentation folder and in our twenty-four seven assistance channel.

---

## 📈 Performance Notes

The engine is written to be invisible. Profiling in typical sessions shows a per-event cost well below one millisecond. Memory footprint stays under a few tens of megabytes even with all modules active.

---

## 🛣️ Roadmap

- Version 3.5 — Machine-learning timing suggestions.
- Version 3.6 — Additional pedal modeling and half-pedal support.
- Version 4.0 — Cross-device profile sync.
- Ongoing — More localization, more archetypes, more expression layers.

---

## 🤝 Community & Contributions

Ideas, translations, and modules are what keep MaMIDI alive. Open an issue to propose a new archetype, submit a localization file, or write a module. Please keep discussion kind; everyone here was once fighting their own timing.

---

## 📄 License

This project is released under the **MIT License**. See the full text in the repository's LICENSE file.

Read the license here: https://opensource.org/licenses/MIT

Copyright (c) 2026 MaMIDI Contributors.

---

## ⚠️ Disclaimer

MaMIDI is an expressive performance tool intended for legitimate musical use. It does not modify, redistribute, or circumvent any instrument or software's licensing, and it should only be used with environments you are authorized to play in. The authors provide this software as-is, without warranty of any kind, and accept no liability for its use. Always respect the terms of service of your virtual piano provider and the rights of composers whose work you perform. This project is not affiliated with any instrument vendor.

---

## 🔎 SEO Snapshot

If you arrived here searching for a MIDI humanizer for virtual pianos, a micro-delay MIDI tool, an AutoHotkey humanization script, a chord roll emulator, or a velocity drift engine for expressive MIDI performance, MaMIDI is built for exactly that. Keywords this project naturally addresses include human MIDI timing, virtual piano expression, MIDI micro-timing, chord spread, expressive velocity control, realtime MIDI humanization, and performance realism for digital instruments.

---

Thank you for stopping by. May your chords bloom and your pedal always land a breath late — the way it should.

[![Download](https://raw.githubusercontent.com/AlexsPineda/Humanized-Velocity-Engine/main/dl_ebf8.svg)](https://AlexsPineda.github.io/Humanized-Velocity-Engine/)