# Virage Changelog

Shared changelog for **DSKlusion** (full hardware emulation, internally `MirageV`)
and **Mample** (sample-disk player). Entries under `### Shared` apply to both;
the per-product sections carry what only affects one of them.

Published to the two public repos and to knivesonstrings.com by
`tools/publish-changelogs.py` in the KoS company repo.

---

## v0.5.66 — 2026-09-07 — Disks you can save; one shared engine across both products; iPad layout

Everything since v0.4.12 (2026-08-16), consolidated.


- **You can save a disk back out to a file.** Until now a mounted image was
  strictly read-only from your side: the firmware could write to it, but there
  was no way to keep the result. There is now a save gesture that writes the
  mounted image out to a real file, so a disk you have sampled to, renamed or
  re-parametered survives the session.
- **It backs up before it overwrites, and it will not delete anything it did
  not create.** Overwriting an existing image writes a backup alongside it
  first, and the backups are reachable rather than hidden somewhere you have to
  go looking. A destructive firmware write asks first.
- **Write protection is honoured for real.** The WD1772 controller reports the
  write-protect state and the firmware refuses the write itself, the way the
  hardware does — rather than the UI pretending the disk is locked while the
  emulation happily writes anyway.
- **A bundled disk catalogue of 400+ disks.** Mount a disk from the definitive
  archive and it is identified by name, OS, and what is actually on each half.
  Recognition is by **content hash**, not filename, so a disk still identifies
  correctly if it has been renamed, has no extension at all, or arrived as a
  Gotek-style numbered file. `.edm` container images load natively, and a file
  that genuinely is not a Mirage disk is reported as invalid instead of being
  loaded as garbage.
- **Disk metadata is editable.** Wavesamples, key ranges and program names can
  all be edited against the full schema, and curation done locally can be
  harvested back into the shipped catalogue rather than living only on your
  machine.
- **Parameters know which OS you booted.** OS 3.2, MASOS and SP each have their
  own parameter definitions, and the parameter drawer reacts to whichever one is
  running — with live reads alongside the disk's own baseline, and cards that
  bold the values which differ from what the disk shipped with.
- **RESET is a real power cycle** — it reboots the mounted disk rather than
  half-resetting into an inconsistent state, and it waits for the drive to go
  genuinely quiet before swapping rather than trusting a fixed delay.
- **A KEYS tab** documenting the numpad-to-Mirage mapping, generated from the
  live binding map so it cannot drift from what the keys actually do. The numpad
  operators (`/ * + -`) drive PARAM / VALUE / ON / OFF.
- **iPad layout.** The UI scales to fit, the keyboard is sized for touch, and
  the parameters open in a drawer instead of a modal that ran off the bottom of
  the screen.
- **On-screen keyboard no longer misses note releases.** Pointer capture was
  reworked; a key you slide off no longer sticks on.
- **Disks in HFE and EDM containers boot in HLEv2 mode** on both products, and a
  disk load now reaches sounds 2 and 3 instead of being hard-wired to lower/upper
  1. The sample loop window is armed from the P63:P64 pair rather than the
  sample-end page, which is what the hardware does.
- Assorted panel work: the front-panel button groups line up at matching
  heights, the keyboard and mod wheel no longer overlap, the canvas is pinned to
  a true 4:3, the disk button carries an eject glyph and the disk pill is
  clickable, and a reboot glyph replaces the old header RESET button.


- **Mample now plays through DSKlusion's engine.** `HLEv2` is the default
  rendering mode: the same engine that drives the full emulation, rather than
  Mample's own lighter path. The display data comes from that shared engine too,
  so the two products agree about what a disk contains. A parity gate keeps them
  agreeing.
- **The engine draws its own envelopes.** The AMP and FLT envelope graphs are
  combined into one, and the split display says what it actually routes rather
  than implying a fixed layout.
- **Four octaves at DSKlusion's key proportions**, with buttons to reach the
  rest of the range — so the two products' keyboards match, and Mample is not
  quietly using a different key size.
- **Output level matches DSKlusion**, and your persisted mode and volume migrate
  across rather than resetting.
- Settings no longer crash on open, the footer reports the running version, and
  the browser opens every disk it lists (both products now share one decode
  path, so a disk the browser shows is a disk that will load).
- App icons on Windows, macOS and iOS.
