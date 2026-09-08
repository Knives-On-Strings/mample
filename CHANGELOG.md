# Virage Changelog

Shared changelog for **DSKlusion** (full hardware emulation, internally `MirageV`)
and **Mample** (sample-disk player). Entries under `### Shared` apply to both;
the per-product sections carry what only affects one of them.

Published to the two public repos and to knivesonstrings.com by
`tools/publish-changelogs.py` in the KoS company repo.

---

## v0.5.66 — 2026-09-07 — A 400+ disk catalogue, content-hash recognition, and one shared engine across both products

Everything since v0.4.12 (2026-08-16), consolidated.


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
- **Disks in HFE and EDM containers boot in HLEv2 mode** on both products, and a
  disk load now reaches sounds 2 and 3 instead of being hard-wired to lower/upper
  1. The sample loop window is armed from the P63:P64 pair rather than the
  sample-end page, which is what the hardware does.
- **The on-screen keyboard no longer misses note releases.** Pointer capture was
  reworked; a key you slide off no longer sticks on.
- The keyboard is half its old height on both products, and the waveform panels
  are about 30% smaller, so more of the window is the thing you came for.


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
