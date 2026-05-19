SOUND EFFECTS

The app ships with built-in Duolingo-style celebration sounds, synthesized
at runtime via the Web Audio API. They work immediately on iOS, Android,
and web — zero bundle weight, no files needed.

This folder is OPTIONAL. Drop in MP3 files with the names below and they
will replace the built-in tones at next reload.

  correct.mp3   — short positive ding (~250ms) — fires on every correct answer
  wrong.mp3     — gentle muted thud (~200ms) — fires on every wrong answer
  complete.mp3  — celebration chime (~1000ms) — fires on session/quiz complete
  levelup.mp3   — phase milestone fanfare (~1500ms) — fires on phase completion
  streak.mp3    — short fire whoosh (~400ms) — fires on streak-freeze earned
  tap.mp3       — barely audible click (~80ms) — reserved for primary CTAs

REQUIREMENTS (only if you're providing MP3s)
  • Format: MP3, mono, 44.1 kHz
  • Size: under 100 KB per file (smaller = faster first-play)
  • License: any (CC0 recommended)

WHERE TO SOURCE (free, royalty-free)
  • https://pixabay.com/sound-effects/  — best for short UI sounds
  • https://mixkit.co/free-sound-effects/game/  — game/level-up sounds
  • https://freesound.org  — large library; filter by CC0

AFTER ADDING FILES
  Run: npm run build && npx cap sync ios

NOTES
  • If a file is missing, the app silently falls back to the synth tone.
  • Volume of MP3s is pre-ducked: tap=0.18, wrong=0.45, all others=0.55.
  • iOS silent switch will mute these (this is normal/expected).
  • Toggle on/off in Settings → الإعدادات → الأصوات والاحتفالات.

DEFAULT SYNTH PROFILES (if you want to tweak them, see _synthesizeSfx in
src/App.jsx — each sound is a few lines of Web Audio nodes):
  correct  → two-note rising bell (E6 → A6) + sparkle on top
  wrong    → low descending dud (G3 → C3, soft)
  complete → C-major arpeggio (C5 E5 G5 C6) + sustained chord finale
  levelup  → 5-note fanfare (G4 C5 E5 G5 C6) + triad finale + sparkle
  streak   → quick rising whoosh (440Hz → 1320Hz)
  tap      → percussive sine click (1200Hz, 50ms)
