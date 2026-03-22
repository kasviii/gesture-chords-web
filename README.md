# Gesture Chords — Web Version

A deployable, browser-based instrument that uses your webcam and hand gestures to play musical chords in real time. No installation required.

**Live demo:** https://gesture-controlled-chords.netlify.app/

---

## What It Does

Open the site, allow camera access, and make hand gestures in front of your webcam. Each gesture triggers a different chord with reverb and chorus effects. The hand skeleton glows in the chord's color, a waveform visualizer pulses at the bottom, and a confidence score shows how clearly the gesture was detected.

Press **REC** to record your session — both your voice and the chord sounds are mixed together and downloaded as a `.webm` file when you stop.

---

## Gesture Map

| Gesture | Chord | Vibe |
|---|---|---|
| ✋ Open Palm | C Major | Bright & Open |
| ✊ Closed Fist | A Minor | Dark & Moody |
| ✌️ Peace/Victory | G Major | Hopeful |
| 🤟 ILoveYou | E Minor | Dramatic |
| 👍 Thumb Up | F Major | Warm & Resolved |
| 👆 Pointing Up | B Minor | Melancholic |
| 👎 Thumb Down | F Minor | Deeply Emotional |

---

## How To Use

Just open the link. No installation, no account, no cost.

1. Click **ENABLE CAMERA**
2. Allow camera and microphone permissions
3. Hold a gesture in front of your webcam
4. Press **REC** to record, **STOP** to save

Works best in Chrome or Edge on desktop.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| MediaPipe Tasks Vision JS | Real-time gesture recognition in browser |
| Tone.js | Chord synthesis with reverb and chorus |
| Web Audio API | Mixing mic + chords for clean recording |
| MediaRecorder API | Recording and downloading sessions |
| Vanilla HTML/CSS/JS | No framework, single file |

Deployed on Netlify. Total cost: $0.

---

## How It Works

The gesture recognizer runs a CNN model entirely in the browser — no server, no API calls. Google's MediaPipe model file (~5MB) downloads once from their public CDN on first load.

When a gesture is detected, Tone.js synthesizes the corresponding chord through a PolySynth with triangle oscillators, reverb, and chorus. The chord color drives the hand skeleton glow, the waveform visualizer, and the UI highlight.

Recording works by creating a Web Audio mixer that combines the microphone input and the synthesizer output into a single stream before passing it to MediaRecorder — this fixes the earphone problem that affected the Python version.

---
