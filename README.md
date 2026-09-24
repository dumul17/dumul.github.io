# Dumul's Observatory

Interactive personal site for **dumul17** — modder, composer, and the three-person Indonesian alternative rock project **DUMUL**.

Live: [dumul17.github.io](https://dumul17.github.io/)

---

## What's here

| Page | File | Description |
|------|------|-------------|
| **Observatory** | `index.html` | Full-screen star field: constellations, black hole, portals, SFX stars, mini music HUD |
| **DUMUL** | `dumul.html` | Band / album page — *Limerence* tracks, synced lyrics, ambient bed |

Entry is the Observatory. The **DUMUL** portal (and Gargantua swallow) leads into `dumul.html`. A “✦ Dumul's Constellation” link brings you back.

---

## Observatory features

- Canvas sky with gravitational lensing around **Gargantua**
- Interactive constellations: **Orion**, **Virgo**, **Canis Major**, **Pleiades**
- Trigger stars with breath pulse + supernova burst + dedicated SFX  
  (`Betelgeuse`, `Rigel`, `Spica`, `Sirius`, `Pleione`)
- Focus system: only the constellation tied to the active SFX lights up
- Audio-reactive spectrum near star labels and in the music HUD
- Mini player (ambient / collapsars) with spectrum that moves into the music logo when the panel is closed
- Portals: DUMUL site, YouTube, etc.
- Boot sequence + potato / reduce-motion paths for weaker devices

## DUMUL page features

- Track list for **Limerence**, **Glitch**, **Nastenka**, **Larung**
- Bottom player bar with seek waveform
- Synced LRC-style lyrics
- Ambient `collapsars.opus` bed when nothing is playing
- Track notes + back-to-top (inline + floating FAB)

---

## Project layout

```text
.
├── index.html          # Observatory (entry)
├── dumul.html          # Band page
├── README.md
│
├── # Star SFX (Observatory)
├── betelgeuse.opus
├── rigel.opus
├── spica.opus
├── sirius.opus
├── pleione.opus
│
├── # Shared / band audio
├── collapsars.opus     # ambient + Gargantua bed
├── limerence.opus
├── glitch.opus
├── nastenka.opus
├── larung.opus
│
└── og.jpg              # Open Graph image (optional but used in meta)
```

Audio paths are relative to the page. Filenames are expected exactly as above (see `srcOf` / `mkAudio` in the HTML).

---

## Run locally

No build step — open the files as static pages.

```bash
# simple local server (avoids some browser file:// audio limits)
npx serve .
# or
python3 -m http.server 8080
```

Then open `http://localhost:8080/` (Observatory) or `/dumul.html`.

---

## Deploy (GitHub Pages)

Repo is set up for user site **`dumul17.github.io`**:

1. Push this folder to the `main` (or `gh-pages`) branch of `https://github.com/dumul17/dumul17.github.io`
2. Settings → Pages → source = that branch, root `/`
3. Canonical URLs already point at `https://dumul17.github.io/` and `.../dumul.html`

Keep **all opus files** next to the HTML on the same origin so `Audio()` and the Web Audio graph can load them.

---

## Notes / behavior

- **Autoplay**: browsers block sound until a user gesture. First tap on a star, track, or the page unlocks audio (including ambient).
- **Star SFX vs music HUD**: mutually exclusive — starting one pauses the other.
- **Performance**: Observatory detects weak devices (`IS_POTATO`) and respects `prefers-reduced-motion`. DUMUL throttles the analyser and delays ambient resume so pause/seek does not thrash `collapsars`.
- **Single-file pages**: CSS/JS are inlined on purpose for zero-build hosting. Splitting to `style.css` is optional and mostly for maintainability, not speed.

---

## Contact

- **YouTube** — [youtube.com/@dumul17](https://www.youtube.com/@dumul17)
- **Instagram** — [instagram.com/dumuldumbowl](https://www.instagram.com/dumuldumbowl/)

---

## Credits

- **DUMUL** — Indonesian alternative rock; album arc *Limerence* → *Glitch* → *Nastenka* → *Larung*
- Site concept & code — dumul17
- Sky / constellation interaction — custom canvas, no framework on `index.html`
- `dumul.html` UI — static export + small vanilla player layer on top

---

## License

Content and original audio: © DUMUL / dumul17.  
Ask before reusing tracks or site code commercially.

---

*"Keep creating, even without the applause."* 🦉
