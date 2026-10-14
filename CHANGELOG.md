## v0.6.48 — 2026-10-14 — Shorter release notes

- **Improved:** Release notes are shorter and tagged New, Improved or Fixed, so they are quicker to scan.

## v0.6.45 — 2026-10-13 — Validation passes; sample loading fixed

- **Improved:** Passes clap-validator and pluginval (strictest level) in both products.
- **Fixed:** Pitch Bend's displayed value drifted when a host stored it as text.

## v0.6.43 — 2026-10-13 — Damaged disk images flagged

- **Improved:** A damaged disk image still loads, and the status line names what is missing or unreadable.
- **Fixed:** In HLEv2, a disk with out-of-range system settings, such as a master tune above 99, no longer detunes every voice.

## v0.6.42 — 2026-10-12 — Out-of-range notes; velocity values

- **Improved:** In HLEv2, notes outside the Mirage's keyboard (36–96) fold by octave onto the key the Mirage plays, with retrigger and sustain per note.
- **Fixed:** Velocity parameters P45/P46/P48/P49 and P55/P56/P58/P59 keep their full value through edits, undo, copy and save.
- **Fixed:** The amp release's velocity shift (P59) works as on the Mirage.

## v0.6.41 — 2026-10-12 — 32 tags per sound half

- **Improved:** A sound half can carry up to 32 tags; ADD CATALOG TAGS adds only those that fit.

## v0.6.40 — 2026-10-12 — Sound tags and your labels

- **New:** Tag each half of a sound in the disk library's editor: up to 16 tags of 64 characters, with suggestions. **Apply to both halves** copies them across.
- **New:** Tags and program names are kept in your own labels file, `disk_catalog.user.json`, which wins over the catalogue.
- **New:** Search matches tags, and clicking a tag filters the library by it.
- **New:** **EXPORT MY LABELS…** saves your labels to a file you can send us for the shared catalogue: content IDs and labels only, no file names or user names.
- **New:** Where a name differs from the catalogue's, the editor shows "Catalog: <name>"; **USE** restores it.
- **New:** **ADD CATALOG TAGS (n)** adds the catalogue's tags a half lacks; a **+tag** chip adds one.
- **Improved:** Names and tags you give a disk show in both products.
- **Improved:** Catalogue updates rename and retag only what you haven't changed yourself.
- **Improved:** The shipped catalogue is version 2.4.
- **Improved:** A disk without a content ID can't take tags or program names, and the editor says so.
- **Improved:** When labels can't be saved, the library says so and puts back what wasn't kept.

- **New:** Program names can be edited in the disk library.
- **Improved:** The loaded sound shows your own names, so a sound renamed in DSKlusion reads the same in Mample.

## v0.6.37 — 2026-10-11 — Mix mode and Keyboard Balance

- **Fixed:** In HLEv2 with mix mode on (P28), each key plays the Mirage's wavesample pair, fixing piano and MELPRO sounds.
- **Fixed:** Keyboard Balance (P24) balances the two halves as on the Mirage.
- **Fixed:** Relative Amplitude (P69) sets levels exactly as on the Mirage.
- **Fixed:** A mix-mode sound's second layer plays at the first layer's P69 level, changing about 20 library sounds.

## v0.6.36 — 2026-10-11 — One master tune and bend range

- **Fixed:** In HLEv2, master tune, bend range, velocity curve, balance and link (P21–P25) and P78–P80 are one setting for the whole instrument, as on the Mirage.
- **Fixed:** In HLEv2, the pitch wheel's range follows P22.
- **Fixed:** In HLEv2, MIDI controllers 2–7 and channel pressure work where a sound assigns them (P78/P79).
- **Fixed:** The editor sizes correctly under Ableton Live's plug-in auto-scale.

- **Fixed:** Pitch bend lands exactly, including at rest.

## v0.6.35 — 2026-10-11 — Key-scaled decay; two-layer mix

- **Fixed:** In HLEv2, decay scales by key (P47/P57), so higher notes decay faster on about 20% of library sounds.
- **Fixed:** In HLEv2, two-layer programs mix as on the Mirage: by mod wheel at P35 = 0, by velocity above 1.
- **Fixed:** In HLEv2, the second layer stays audible at its quietest level instead of going silent.

- **Improved:** The envelope picture says which key it is drawn at.

## v0.6.34 — 2026-10-10 — Per-half LFO

- **Fixed:** In HLEv2, each half vibratos with its own LFO speed and depth (P31/P32).
- **Fixed:** In HLEv2, the LFO no longer moves the filter, so vibrato sounds may change slightly.
- **Fixed:** In HLEv2, the second layer keeps its vibrato and pitch bend through the release.
- **Fixed:** In HLEv2, LFO edits apply from the next note, as on the Mirage.

## v0.6.31 — 2026-10-10 — VOLUME knob on older macOS

- **Improved:** If the controls can't load, the knob shows "Volume unavailable".
- **Fixed:** The VOLUME knob works on older macOS versions (Knives-On-Strings/mample#3).
- **Fixed:** The VOLUME knob no longer jumps on first touch.

## v0.6.29 — 2026-10-10 — macOS minimum per Mac

- **Improved:** The installers and Mample manual state the macOS minimum: 10.15 on Intel Macs, 11 on Apple Silicon.

## v0.6.25 — 2026-10-09 — Tighter MIDI; clean releases

- **Fixed:** In HLEv2, re-striking a held or sustained key, or a doubled controller, could leave a note sounding.

- **Improved:** MIDI plays at the exact sample the host sends it (up to 12 ms tighter at a 512-sample buffer), so releases no longer sound early.

## v0.6.24 — 2026-10-09 — Top Key keeps to the keyboard

- **Fixed:** P72 Top Key ranges 1–61, as on the Mirage, and defaults to 61.

## v0.6.22 — 2026-10-08 — Fine tune uses its full range

- **Fixed:** P68 Fine Tune uses the Mirage's full 0–255 range, shown in hex. Factory sounds keep their pitch.

## v0.6.20 — 2026-10-08 — Mample manual updated

- **Improved:** The manual covers current requirements (Windows, or macOS 10.15 and later), both installers and uninstalling.

## v0.6.19 — 2026-10-08 — Mac disk-image installer

- **New:** On macOS, each product ships as a signed, notarized disk image with its installer, read-me, licences and uninstaller.
- **Fixed:** The licence agreement no longer opens with an internal draft note.

## v0.6.18 — 2026-10-07 — Contact addresses

- **Improved:** The licence and Mample manual give our legal@, privacy@, support@ and hello@knivesonstrings.com addresses; bug reports still go to GitHub issues.

## v0.6.17 — 2026-10-07 — macOS 10.15 Catalina

- **Improved:** Both products run on macOS 10.15 Catalina on Intel Macs (Apple Silicon needs macOS 11); keep Safari up to date there.

## v0.6.16 — 2026-10-07 — Internal tooling

- **Improved:** The Mample manual gives hello@knivesonstrings.com for general questions.

## v0.6.14 — 2026-10-05 — Mample Windows installer; no ASIO

- **New:** The About box says "Beta Tester Version".
- **Improved:** The Windows standalone apps use WASAPI or DirectSound; ASIO is no longer supported. Plug-ins are unaffected.

- **New:** A Windows installer for the VST3, CLAP and standalone app, for all users or just you; uninstalling keeps your settings and sounds.
- **New:** The installer isn't code-signed yet, so Windows SmartScreen may warn before it runs.
- **Improved:** The manual lists the standalone app's audio device types on Windows.

## v0.6.13 — 2026-10-04 — Mample network fixes

- **Improved:** Usage statistics no longer include your operating system's name, and the host version is sent as "unknown". Nothing is sent until you allow it.
- **Fixed:** Closing Mample just after Report an Issue, with no network, could crash the host.

## v0.6.11 — 2026-10-03 — Panel saves reach your files

- **Fixed:** Closing Mample on a busy computer could stall the host for two seconds.

## v0.6.6 — 2026-09-29 — Damaged catalogue kept

- **Fixed:** A disk catalogue that can't be read is never saved over, so your names and protection tabs can be recovered.
- **Fixed:** Merging duplicate catalogue entries for a disk keeps it protected if either was.

## v0.6.5 — 2026-09-28 — Renames survive a bad save

- **Fixed:** Saving a disk's details writes only the disk's own information to the catalogue.

- **Fixed:** Saving a disk's details in Mample never changes its write protection.

## v0.6.4 — 2026-09-28 — Filters sit where the Mirage puts them

- **Fixed:** Filters sit where the Mirage puts them, honouring each wavesample's filter limit; most sounds are darker.

## v0.6.1 — 2026-09-24 — Clean oversampling

- **Fixed:** Closing Mample while it was sending usage data to an unreachable server could crash some hosts.

## v0.5.120 — 2026-09-23 — The filter at every sample rate

- **Improved:** The window opens faster after the first time in a session, and closing it leaves no files behind.
- **Fixed:** Reopening a project shows the restored parameter values in the host, notably in CLAP hosts.
- **Fixed:** Plug-in scanners and validators get a fully prepared plug-in.

## v0.5.119 — 2026-09-22 — Window scale for Mample

- **New:** Settings → Appearance → Window Scale sizes the window from 50 % to 200 %, saved per project instance.

## v0.5.118 — 2026-09-22 — Notices, corrected

- **Fixed:** The third-party notices state ASIO support correctly.

## v0.5.117 — 2026-09-22 — Naming the keyboard button

- **Fixed:** Screen readers name the show/hide keyboard button "Show keyboard" or "Hide keyboard".

## v0.5.115 — 2026-09-22 — A brighter Mample icon

- **Improved:** A brighter application icon.

## v0.5.114 — 2026-09-22 — Keyboard access to Settings

- **Improved:** Settings option lists work from the keyboard and with screen readers.

- **Improved:** Disk rows in the browser can be chosen from the keyboard.

## v0.5.113 — 2026-09-22 — ASIO notice

- **Fixed:** The About box carries the ASIO trademark notice.

## v0.5.111 — 2026-09-22 — Privacy link back in view

- **Fixed:** The tour's consent step no longer hides the privacy policy link off-screen.

---

## v0.5.110 — 2026-09-22 — Install id disclosed

- **Fixed:** Mample's privacy wording now says a random install id is sent, matching the privacy policy.

---

## v0.5.109 — 2026-09-22 — Install id created only when needed

- **Fixed:** The anonymous install id is created only when something is about to be sent.

---

## v0.5.108 — 2026-09-21 — Mample guided tour

- **New:** A short guided tour the first time you run Mample; Settings → APPEARANCE → Show Tour replays it.
- **New:** If you haven't answered the privacy question, the tour's last step asks it, with a link to the privacy policy.

## v0.5.104 — 2026-09-19 — A light theme for Mample

- **New:** A Light theme in Settings → APPEARANCE, shared by the standalone and the plug-in; active displays stay dark.

---

## v0.5.92 — 2026-09-16 — Two windows at once

- **Fixed:** On Windows, a second open window no longer blanks or crops the first.

---

## v0.5.91 — 2026-09-16 — Built on JUCE 9.0.2

- **Improved:** Built on JUCE 9.0.2.

---

## v0.5.87 — 2026-09-13 — Consistent Settings

- **Improved:** Settings rows look the same in both products.

---

## v0.5.85 — 2026-09-13 — Standalone settings kept

- **Fixed:** The standalone apps keep the settings you choose; a folder lost this way needs choosing once more.

## v0.5.84 — 2026-09-12 — About box links and credits

- **Improved:** Credits link to the projects behind them.
- **Fixed:** The About box's Website, GitHub and Manual buttons open real pages; Manual appears only in Mample.
- **Fixed:** The mc6809 CPU core is credited to its author, and the HFE format to the HxC Floppy Emulator project.

---

## v0.5.83 — 2026-09-12 — Typeface credits

- **Improved:** The About box credits the shipped fonts: Inter, Noto Sans Symbols 2, Noto Sans Math, Courier Prime and IBM Plex Mono.
- **Fixed:** The About box names JUCE 9, not JUCE 8.

- **Fixed:** The About box no longer claims HLE and LLE modes; Mample has one engine, HLEv2.

---

## v0.5.81 — 2026-09-12 — Mample's info panel reports the sound

- **Improved:** The info panel reports each half's key zones and loops, in plain English.
- **Improved:** The parameter boxes read `P36 CUT`, `P37 RES`, `P33 DET` and `P34 BAL`.
- **Fixed:** The `WS` badge counts the sound's zones; it always read eight.

---

## v0.5.79 — 2026-09-12 — One type scale

- **Improved:** Text in both products follows one five-step type scale.

---

## v0.5.77 — 2026-09-11 — Mample visual polish

- **Improved:** Mample uses one typeface, Inter, and live numbers no longer jitter.
- **Improved:** Mample bundles its own symbols, so they match on every system.

---

## v0.5.74 — 2026-09-11 — Mample sees disks in subfolders

- **Fixed:** The library shows and loads disks in subfolders, as collapsible groups; same-named disks in different folders are separate rows.

---

## v0.5.73 — 2026-09-11 — Choose your disk folder

- **New:** Settings → Sound chooses where your sound disks live; an unreachable folder falls back to the default.
- **Fixed:** A restored session names its sounds again.

---

## v0.5.72 — 2026-09-11 — Upper above lower

- **Improved:** Upper sits above lower in the browser's sound list.
- **Improved:** The browser header names the loaded disk.
- **Fixed:** Each waveform panel names its own sound's disk.

---

## v0.5.71 — 2026-09-11 — Waveform panels name their sound

- **Improved:** Each waveform panel names its disk, half, slot and patch.
- **Improved:** All six halves of a three-slot disk fit the browser at once.

---

## v0.5.70 — 2026-09-11 — No pale edge lines

- **Fixed:** The pale line along the bottom of the window is gone.

- **Fixed:** No pale seam where the page meets the window.

---

## v0.5.69 — 2026-09-08 — Opt-in telemetry, switched off

- **New:** Opt-in telemetry and an issue reporter, switched off in every build so far. When on, nothing is sent until you agree, and never audio or samples.

---

## v0.5.66 — 2026-09-07 — Disk catalogue and one shared engine

- **New:** A bundled catalogue of 400+ disks recognises each disk by its content, even renamed or Gotek-numbered.
- **New:** `.edm` images load, and HFE and EDM disks boot in HLEv2.
- **New:** Disk metadata (wavesamples, key ranges, program names) is editable.
- **Improved:** A file that isn't a Mirage disk is reported as invalid.
- **Improved:** The keyboard is half its old height and the waveform panels about 30% smaller.
- **Fixed:** Disk loads reach sounds 2 and 3.
- **Fixed:** A key you slide off the on-screen keyboard no longer sticks.

- **New:** Mample plays through DSKlusion's HLEv2 engine.
- **New:** App icons on Windows, macOS and iOS.
- **Improved:** Four octaves at DSKlusion's key proportions, with buttons to reach the rest.
- **Improved:** The AMP and FLT envelope graphs are combined into one.
- **Improved:** Output level matches DSKlusion.
- **Fixed:** Settings no longer crash on open.
- **Fixed:** The browser opens every disk it lists.
