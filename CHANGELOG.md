## v0.6.46 — 2026-10-13 — A flaky internal test made repeatable

- **No change to either product.** The internal test that compares DSKlusion
  and Mample now gives both the same simulated filter components, so it no
  longer fails about one run in twenty. Each plug-in instance still gets its
  own analogue component spread, exactly as before.

## v0.6.45 — 2026-10-13 — Plug-in validation passes; sample loading starts from the Mirage's own settings

- **Pitch Bend's displayed value now reads back exactly.** Hosts that type
  or store the parameter as text no longer see the last digit drift. It now
  shows 4 decimals; its range, default and automation are unchanged.
- Both products now pass clap-validator, the CLAP format's standard checker,
  as well as pluginval at its strictest level.

## v0.6.44 — 2026-10-13 — Tests can no longer touch your own settings

- **No change to either product.** Every internal test now runs in test mode,
  where settings and logs go to a temporary folder. 30 tests could previously
  run without it and so reach the user's own `Documents\KnivesOnStrings`
  folder. The test run now checks this first and stops if any test would
  run outside test mode.

## v0.6.43 — 2026-10-13 — Damaged disk images say so; window scaling in Live is tested

- **A damaged disk image now says so when it loads.** An `.hfe` with missing
  or unreadable sectors -- typically a partial conversion -- still loads, since
  its intact sounds may play, but the status line names the image and what is
  affected, for example *15 of 480 sectors missing and 1 unreadable (OS,
  Lower 1 parameters, Lower 1 samples)*.
- **A disk whose system parameters are out of range is no longer trusted.** If
  a disk's OS 3.2 system block holds a global the Mirage's own panel cannot
  set (for example a master tune above 99), HLEv2 ignores the block and keeps
  its defaults, instead of detuning every voice. The log says which value it
  refused.

## v0.6.42 — 2026-10-12 — HLEv2 plays out-of-range notes as the Mirage does; velocity parameters keep their whole byte

These affect the HLEv2 engine in both Mample and DSKlusion.

- **MIDI notes outside the Mirage's keyboard (36–96) now play the key the
  Mirage folds them to**, by octave: the folded key's pitch, wavesample and
  half. Two notes an octave apart both sound. Retrigger and the sustain pedal
  work per incoming note, and pedal-up releases only that note's own voice.
- **Velocity parameters P45/P46/P48/P49 and P55/P56/P58/P59 keep their whole
  stored byte**, as OS 3.2 does, so edits, undo, copy and save no longer lose
  the low bits. The amp release's velocity shift (P59) now comes off the
  rate-table step, as on the Mirage. The panel still shows the byte divided by
  4, capped at 31.

## v0.6.41 — 2026-10-12 — Up to 32 tags per sound half

- **A sound half can now carry up to 32 tags** (it was 16). Each tag is still
  up to 64 characters. ADD CATALOG TAGS counts only the tags that fit.

## v0.6.40 — 2026-10-12 — Tag your sounds, and share your labels

- **Tag your sounds.** In the disk library's editor, each half of a sound --
  Lower and Upper -- can carry tags: your own words, up to 16 per half, 64
  characters each, with suggestions that start from keys, strings, brass &
  wind, synth, percussion and voice. Tags match without regard to A-Z case;
  accented letters are different tags ("É" and "é"). **Apply to both
  halves** copies one half's tags to the other. A comma separates tags, typed
  or pasted, and the editor says when a tag is longer than will be kept.
- **Your labels file.** Tags and program names live in your own labels file,
  `disk_catalog.user.json`, beside the catalogue; SAVE never writes them into
  `disk_catalog.json`. A disk or sound name you change with SAVE goes into
  both files, and the labels file wins.
- **Find sounds by tag.** The library's search matches tags as well as names,
  and clicking a tag on a sound shows only the disks that carry it. The tag
  you are filtering by shows as a chip you click to clear.
- **EXPORT MY LABELS…** in the disk library saves your labels to a file you
  can send us, so they can go into the catalogue everyone gets: your labels
  file, plus the disk, sound and program names you saved before this version.
  It holds only the disks' content IDs and your labels: no file names, folders
  or user names. Tags you added before this version were never saved, so
  there are none to export.
- **Both products show the same labels.** A name or tag you give a disk in one
  product shows in the other the next time its disk library is opened.
- **A disk without a content ID can't be given tags or program names**; the
  editor says so, and its names can still be changed.
- **When your labels can't be saved, the library says so** and puts back
  whatever was not kept, rather than showing an edit that was lost. After a
  SAVE in the editor it says which part was kept: the names, or nothing.
- **Merged labels reach existing installs.** When a release ships a newer
  catalogue, the tags of every half you haven't tagged yourself follow it,
  and every name you haven't changed -- a disk's title, a sound's name, a
  sound's program names -- takes its name. A name you changed keeps yours,
  name by name: renaming one sound no longer stops the rest of the disk
  following the catalogue. A disk saved by an earlier version keeps all its
  names.
- **Your own labels always win over catalogue updates.** A newer catalogue
  never replaces a name you changed or the tags you gave a half; only USE, or
  ADD CATALOG TAGS, brings the catalogue's back.
- **"Catalog: <name>", with USE.** Where a title, sound name or program name
  in the editor differs from the catalogue's own, a line under it shows the
  catalogue's name; **USE** puts it back at once, in your labels file and the
  catalogue, and from then on that name follows the catalogue again.
- **ADD CATALOG TAGS.** A sound half with tags of your own is offered the
  catalogue's tags it lacks: **ADD CATALOG TAGS (n)** adds them all after
  yours, a faint **+tag** chip adds one. Nothing is removed; 16 at most.
- The shipped catalogue is now version 2.4.

- **Program names can be edited** in the disk library's edit panel.
- **The loaded sound shows your names.** The Disk: line, the waveform panels
  and the library's LOADED marker use the names in your labels file, so a sound
  renamed in DSKlusion reads the same in Mample, and stays marked LOADED.

## v0.6.38 — 2026-10-11 — HLEv2 reads a disk's MIDI channel settings from the right place

- **Internal: HLEv2 reads a disk's MIDI omni and channel settings from where
  OS 3.2 keeps them.** There is no change to how either product responds to
  MIDI: each still filters on its own receive channel.

## v0.6.37 — 2026-10-11 — Mix-mode sounds play the Mirage's wavesample pairs; Keyboard Balance works

These affect the HLEv2 engine in both Mample and DSKlusion.

- **With mix mode on (P28), each key plays the wavesample pair the Mirage
  plays**: two at a time, with the second layer the next wavesample up. This
  fixes several piano and MELPRO sounds that played the wrong wavesample on
  some keys.
- **Keyboard Balance (P24) now balances the two halves as the Mirage does.**
  Every library disk ships it centred, so loading a sound sounds the same;
  editing it is now audible.
- **Relative Amplitude (P69) sets levels exactly as the Mirage decodes it.**
- **The second layer of a mix-mode sound plays at the first layer's P69
  level**, as on the Mirage. This changes the level of about 20 library
  sounds; for example, the second layer of #7 clarinets was silent and now
  sounds.

## v0.6.36 — 2026-10-11 — Master tune and bend range are one setting for the whole instrument

These affect the HLEv2 engine in both Mample and DSKlusion, except the last
item, which affects both editors.

- **Master tune, bend range, velocity curve, keyboard balance and link
  (P21–P25) and P78–P80 are one setting for the whole instrument**, as on the
  Mirage. A master-tune edit retunes both halves, and notes already held.
- **The pitch wheel's range follows P22**, as measured on the Mirage.
- **MIDI controllers 2–7 and channel pressure now reach the engine** where the
  sound assigns them (P78/P79).
- **Window resizes run in the host window's DPI context**, so the editor
  sizes correctly under Ableton Live's plug-in auto-scale.

- **Pitch bend lands exactly, including at rest.**

## v0.6.35 — 2026-10-11 — Decay follows the key; two-layer sounds mix as on the Mirage

These affect the HLEv2 engine in both Mample and DSKlusion.

- **Decay now scales by key (P47/P57)**, as on the Mirage: on sounds that use
  it (about 20% of the library), higher notes decay faster.
- **Two-layer programs mix as measured on OS 3.2.** At P35 = 0 the mod wheel
  crossfades the two layers live, while the note sounds; at P35 above 1,
  velocity feeds the mix.
- **The second layer keeps sounding at the DOC volume floor** (about −27 dB)
  where it used to go silent, as on the Mirage.

- **The envelope picture says which key it is drawn at.**

## v0.6.34 — 2026-10-10 — Each half vibratos with its own LFO

These affect the HLEv2 engine in both Mample and DSKlusion.

- **Each half's sound now vibratos with its own LFO speed and depth (P31/P32)**,
  as the Mirage does. This matters when the Lower and Upper halves come from
  different sounds or disks: each keeps its own vibrato instead of both
  following the Lower half's.
- **The LFO no longer moves the filter.** It never did on the Mirage. Sounds
  with vibrato may sound slightly different.
- **Layer B keeps its vibrato and pitch bend through the release.**
- **LFO edits take effect on the next note**, as on the Mirage.

## v0.6.32 — 2026-10-10 — Four tests now check in Release builds

- **No change to either product.** Four internal tests now run their checks
  in Release builds as well as Debug, and a dead internal test-tone helper
  was removed.

## v0.6.31 — 2026-10-10 — Mample's VOLUME knob works on older macOS

- **The VOLUME knob now works on older macOS versions.** It did nothing
  there because the plugin's controls script was written for newer WebKit
  than those systems ship. Fixes Knives-On-Strings/mample#3.
- **The knob no longer jumps on first touch.** A drag now starts from the
  volume the plugin is actually at, not from a default.
- **If the plugin's controls can't load, the knob says so.** It shows
  "Volume unavailable" instead of turning with no effect.

- The shared web bundle's JUCE script is now built for older WebKit too, so
  DSKlusion's controls load on the same older macOS versions.

---

## v0.6.30 — 2026-10-10 — LLE sample loads and edits reach the running OS safely

- Two internal tests were made reliable: one no longer depends on thread
  timing, and one now checks its parameter layout in release builds too.
  Neither product's behaviour changes.

## v0.6.29 — 2026-10-10 — The macOS floor is stated per Mac

- **Both products state the macOS they need for each kind of Mac:** macOS
  10.15 Catalina or later on an Intel Mac, macOS 11 Big Sur or later on an
  Apple Silicon Mac. The installer welcome text, the disk-image README and
  the Mample manual now say so; before, they gave 10.15 for both.
- **The macOS packager checks it.** Every packaged build is verified to
  start on exactly those versions, for each architecture.

## v0.6.14 — 2026-10-05 — A Windows installer for Mample, and no ASIO

- **ASIO is no longer supported.** On Windows the standalone apps play through
  Windows Audio (WASAPI) or DirectSound. Plugins in a DAW are unaffected: there,
  audio devices belong to the host. The ASIO notices are gone from the About
  box and the licence texts with it.
- **The About box says "Beta Tester Version"** under the version.

- **A Windows installer.** It installs the VST3, CLAP and standalone app, the
  licence texts and the changelog, and sets up Microsoft's WebView2 runtime if
  it is missing. It asks you to accept the End User Licence Agreement before
  anything is installed, and it can install for everyone on the computer or
  just for you. Uninstalling removes everything it installed and leaves your
  settings and sounds alone. It is not code-signed yet, so Windows SmartScreen
  may warn before it runs.
- The manual's Settings page says which audio device types the standalone app
  offers on Windows.

## v0.6.13 — 2026-10-04 — Mample's network code is the shared client

- **Fixed: closing Mample just after reporting a problem could crash the
  host.** With no network, Report an Issue started a check that could still
  be running when you closed Mample a few seconds later, after Mample had
  gone. Closing Mample now stops that check first.
- **Usage statistics no longer include your operating system's name.** Where
  the report has a place for the host's version — which Mample can't read —
  it now says "unknown", as Knives on Strings' telemetry rules require.
- Mample's telemetry and issue reporting now use the same shared, verified
  code as Knives on Strings' other plugins. Nothing else about what is sent,
  or when, has changed, and it still sends nothing until you allow it.

## v0.6.11 — 2026-10-03 — Open Disk loads both halves

- **Fixed: closing Mample on a busy computer could stall your host for two
  seconds.** Mample's background usage-statistics thread ran at the lowest
  priority Windows has, so when every core was busy — a bounce, a build — it
  could wait seconds for a turn. Closing Mample then held up the host while
  it waited, and could leave that thread running after Mample had closed. The
  thread now runs at ordinary priority and stops promptly.

## v0.6.6 — 2026-09-29 — A damaged catalogue is never saved over

- **A damaged disk catalogue is never saved over.** If the catalogue file
  that holds your disk names and protection tabs could not be read, the next
  library scan or details save used to replace it with a fresh one, and every
  name and tab in it was lost. Now nothing is written to it: the disks still
  list, and the file stays as it is so it can be recovered.
- **Merging two catalogue entries for the same disk keeps its protection.**
  When the same disk turned up under two names, the entries were merged and
  only one of them decided whether the disk stayed protected, so a protected
  factory disk could come out writable. Now the merged disk is protected if
  either entry was, and stays marked as factory if either entry was.

## v0.6.5 — 2026-09-28 — Renames and protection tabs survive a bad save

- **Saving a disk's details writes only the disk's own information to the
  catalogue.** Some of what the disk browser shows about a row, such as the
  folder it sits in, used to be saved into the catalogue along with the
  disk's names. It no longer is.

- **Saving a disk's details in Mample never changes its write protection.**
  Mample and DSKlusion share one disk catalogue, and a details save in Mample
  could write back an out-of-date protection tab, leaving a disk you had
  protected in DSKlusion writable. Mample now keeps the catalogue's own tab.

## v0.6.4 — 2026-09-28 — Filters sit where the Mirage puts them

- **Every sound's filter now sits where the Mirage puts it.** Where a sound's
  filter rests, and how far its envelope opens, used to sit a fixed step too
  bright, and ignored the filter offset each wavesample carries. Both now
  follow the Mirage's own rule, including each wavesample's filter limit, and
  the filter envelope graph shows the new levels. Most sounds come out
  darker, some of them clearly. Sounds whose filter envelope opens fully
  sound the same.

## v0.6.1 — 2026-09-24 — Oversampling without the grit

The first release on the 0.6 line.

- Closing Mample, or removing it from a project, while it was sending usage
  data to a server it could not reach could force-stop that sending thread,
  and on some systems bring the host down with it. It now waits briefly,
  cancels the send, and lets go.

## v0.5.120 — 2026-09-23 — The filter at every sample rate

The last release on the 0.5 line.

### Both products

- Reopening a project now tells the host to re-read the plugin's parameters,
  so automation lanes and generic editors show the restored values instead of
  stale ones. CLAP hosts were the most affected.
- The window opens faster after the first time in a session. Every window in
  one DAW now shares a single browser profile instead of building a fresh one
  on each open, and closing a window no longer leaves a few megabytes behind
  on disk.
- Plugin scanners and validators now get a fully prepared plugin, rather than
  one that skipped its setup when it recognised them.

## v0.5.119 — 2026-09-22 — Window scale for Mample

- **Settings → Appearance → Window Scale** resizes Mample's window and
  everything in it: 50 %, 75 %, 100 %, 150 % or 200 %. Each option shows the
  size in pixels it will produce. The choice is saved with the project, so
  each instance in a session can be its own size. Dialogs keep their own size
  at every scale.

## v0.5.118 — 2026-09-22 — Notices, corrected

### Both products

- The third-party notices now state that ASIO support is part of every
  Windows build — VST3, CLAP and Standalone alike — and use Steinberg's
  current trademark wording.

## v0.5.117 — 2026-09-22 — Naming the keyboard button

### Both products

- The show/hide keyboard button in the header now carries its own name for
  screen readers instead of relying on its tooltip, which is never shown on a
  touch screen. The name follows the button, so it says "Hide keyboard" when
  the keyboard is up and "Show keyboard" when it is not.

## v0.5.115 — 2026-09-22 — A brighter Mample icon

- A new application icon. The old one was drawn so dark that the disk body
  barely separated from the background behind it — in a taskbar or a plugin
  list it read as a faint outline. The artwork is the same floppy; it is now
  bright enough to be a shape. Every size ships regenerated: the Windows icon
  and its seven embedded resolutions, and the macOS set.

## v0.5.114 — 2026-09-22 — Settings and the disk list, from the keyboard

### Both products

- The option lists in Settings — engine mode, window scale, display style,
  theme — can now be reached and chosen with the keyboard, and a screen
  reader announces them as a group and says which option is selected. They
  were previously mouse-only, and selection was shown in colour alone.

- Disk rows in the browser can now be reached and chosen with the keyboard,
  and the selected row is announced rather than only highlighted.

## v0.5.113 — 2026-09-22 — The ASIO notice both products owed

### Both products

- The About dialog now carries the ASIO trademark notice. Mample and
  DSKlusion can both use ASIO audio drivers on Windows, and Steinberg's
  licence requires the notice wherever an About box credits anyone else.
  Mample's manual gains the same line, and lists ASIO among the components
  the plugin is built with.

## v0.5.111 — 2026-09-22 — The privacy link the tour was hiding

- **The tour's consent step no longer runs off the bottom of the window,
  taking the privacy policy link with it.** The card was placed from a fixed
  170-pixel guess at its own height. That is about right for the four steps
  that show you around, and about half of what the consent step needs — a
  disclosure paragraph, two buttons and a link — so the card was positioned
  as though it were short, and the last 36 pixels of it fell outside
  Mample's window and were clipped away. What fell outside was "View
  privacy policy": drawn, reachable by keyboard, and off the screen. The
  card is now measured rather than guessed, kept inside the window
  whatever it contains, and scrolls if it is ever taller than the window
  itself. The four other steps are unmoved.

---

## v0.5.110 — 2026-09-22 — Saying that the identifier is sent

- **The privacy wording now names the anonymous install identifier.** Every
  place Mample describes what it sends — the first-run question, the tour's
  consent step, Settings → PRIVACY and the user manual — listed the plugin
  version, your operating system, your host and its version, sample rate,
  buffer size and session length, and stopped there. A random install id
  rides on every record as well, as the published privacy policy already
  said, so the wording inside the plugin was narrower than the policy it
  points you at. All four places now read the same sentence, with "and a
  random install id created when you opt in" in the list.

---

## v0.5.109 — 2026-09-22 — An identifier that waits until it is needed

- **Opening Mample no longer creates an anonymous install identifier.** That
  identifier exists only to tell one anonymous install from another in usage
  data, and it is meant to be created the first time it is needed. It was
  being created the first time you opened the plugin window instead — before
  you had been asked anything, and whether or not you ever said yes. It is now
  created at the moment something is actually about to be sent, so an install
  that never sends anything never has one.
- **If you declined, or were never asked, there is now nothing to find.** For
  anyone who has already agreed to send usage data nothing changes: the same
  identifier, unchanged. Settings → PRIVACY shows it once it exists and shows
  no line at all before that.

---

## v0.5.108 — 2026-09-21 — Show Tour stops being a promise

- **A short guided tour, the first time you run Mample.** It opens by
  itself a moment after the window is ready and walks through four steps:
  what Mample is, where disks come from, what a loaded disk is telling
  you, and how to play it.
- **The disks step opens your disk library for you** rather than pointing
  at the button that opens it, so the one thing a new user has to find is
  on screen while it is being explained.
- **However you leave the tour** — finishing it, skipping it, or pressing
  Escape — it will not open by itself again.
- **A fifth step appears only if you have not yet answered the privacy
  question.** It asks once whether Mample may send anonymous usage data,
  lists what that would and would not include, and links to the privacy
  policy. You answer it one way or the other; there is no Next to press
  past it, so the question is put to you rather than slipped by you. Skip
  the tour before reaching that step and Mample asks in its own prompt
  instead.
- **You can see the tour again at any time** from Settings → APPEARANCE →
  Show Tour. Once you have answered the privacy question — in the tour or in
  Mample's own prompt, it makes no difference — running it again gives you
  the four steps; run it again without having answered and the question is
  still there.
- **The tour is remembered in your settings, not in the browser cache**, so
  clearing the WebView cache to fix something else does not bring it back.

## v0.5.104 — 2026-09-19 — A light theme for Mample

- **Mample can now run light.** Settings → APPEARANCE has a new THEME choice,
  Dark or Light. Dark is still the default, so nothing changes until you pick
  Light. The panels, the disk browser and the settings all lighten together,
  out to the edges of the window.
- **A display that is showing something stays dark.** With a disk loaded, the
  waveform and envelope graphs keep their black screen and their glowing
  trace in either theme, and so do the VU and CPU meters — they are the
  instrument's screens, and they read the way they always have. The text
  readouts around them follow the theme.
- **A display that is showing nothing does not.** Before you load anything the
  envelope panel now comes up pale in Light, matching the two empty waveform
  panels beside it instead of sitting there as a black slab. A screen that is
  off should read as an empty control, not as a hole in the window.
- **Your choice is remembered**, and the standalone and the plugin share it:
  set it in one and the other opens that way next time.
- **A Mample that is already open keeps the look it started with.** The window
  you changed the setting in switches straight away, but a second one open at
  the same time — the standalone beside the plugin, or two plugin instances
  in one project — stays as it was until you close and reopen it.

---

## v0.5.92 — 2026-09-16 — Two windows open at once no longer break the UI

- **Running a second window no longer blanks or crops the first's UI.** Each
  open editor now keeps its own private WebView data folder instead of one
  shared per product, so the standalone and the plugin — or two plugin
  instances in one project — can be open together on Windows without one
  coming up white or with its bottom cut off. Folders left behind by a
  closed instance are cleaned up automatically.

---

## v0.5.91 — 2026-09-16 — Built on JUCE 9.0.2

- **Built on JUCE 9.0.2**, up from 9.0.1.

---

## v0.5.87 — 2026-09-13 — Settings look the same everywhere

- **Help text in Settings now has one typeface and colour** in both
  products. Several of DSKlusion's rows (Boot ROM, OS disk images, sound
  disks, disk writes, audio and logging) had fallen back to a typewriter face.
- Folder and file rows share one design, and their Browse buttons match the
  other buttons in Settings.
- An empty folder or file row now reads "(default)" everywhere. Each of these
  settings falls back to a real default location, so "(not set)" was wrong.

---

## v0.5.85 — 2026-09-13 — The standalone apps keep your settings

- **Settings chosen in the standalone apps are kept.** A folder chosen in the
  standalone Mample or DSKlusion (sound disks, OS disk images) could be gone
  the next time the app started, along with other settings changed in the same
  session: the app's own audio, MIDI and window state was saved over them. That
  state now has a file of its own, `Mample.standalone.settings` or
  `DSKlusion.standalone.settings`, and your audio device, MIDI inputs and
  window position carry over the first time the new version starts. A folder
  lost this way needs choosing once more.

## v0.5.84 — 2026-09-12 — About links go somewhere, and credit the right people

- **The About box's buttons led nowhere.** Manual pointed at a page that did
  not exist, and GitHub at a private repository, so both failed for everyone
  who clicked them. Website and GitHub now open each product's own page and
  its public repository. The Manual button appears in Mample, which has a
  manual, and no longer appears in DSKlusion, which does not.
- **Credits link to the projects behind them**: JUCE, React, Tailwind CSS,
  Vite, the mc6809 CPU core, the HxC Floppy Emulator project, and each of the
  five typefaces. Links open in your web browser.
- **The mc6809 CPU core is now credited to its author.** It is elmerucr's MIT
  licensed MC6809. The About box and the Mample manual both named someone
  else.
- **The HFE credit now credits the format.** It read as though Virage used
  borrowed parsing code; Virage reads HFE disk images with its own code, and
  the format comes from the HxC Floppy Emulator project.
- The credit descriptions shortened in v0.5.83 are back in full. The About box
  scrolls when it needs to.

---

## v0.5.83 — 2026-09-12 — The About box credits the typefaces

- **Both products' About box now credits the fonts they ship.** Inter, Noto
  Sans Symbols 2, Noto Sans Math, Courier Prime and IBM Plex Mono are all used
  under the SIL Open Font License 1.1, which asks that its notice travel with
  the software. Mample's manual has named them since v0.5.78, but DSKlusion has
  no manual, so until now it credited them nowhere.
- **The About box said JUCE 8.** The plugins are built on JUCE 9.
- The credits were tightened so the whole About box fits Mample's window
  without scrolling, with every name and author kept.

- **Its About box no longer claims HLE and LLE modes.** Mample has one engine,
  the same HLEv2 engine DSKlusion uses by default.

---

## v0.5.81 — 2026-09-12 — Mample's info panel says what actually loaded

- **The panel reports the sound, not the machine's memory size.** The row that
  read `65536 + 65536 bytes` was a constant: sample memory is always that size,
  so it never told you anything about your disk. It now reports how many key
  zones each half holds and whether they loop, which is the thing that shows a
  disk read correctly. A percussion kit is many narrow zones and a piano a few
  wide ones, so one zone where you expected eight means the load did not get
  what you asked for.
- **That count used to be the number eight, always.** The engine reported the
  size of a list that is always eight entries long, empty slots included, so
  the `WS` badge on the waveform panels had never once read your disk. It now
  counts the zones the engine can actually reach, by the same rule the note
  router uses to pick one.
- **The other rows read as English.** `L:Snd1 | U:Snd2` is now
  `lower 1, upper 2`, and `L<=B4 U>=C5` is now `lower to B4, upper from C5`.
  Neither of the old forms appears anywhere on the Mirage or in its manual.
- **The four parameter boxes carry their Mirage parameter numbers**, so they
  read `P36 CUT`, `P37 RES`, `P33 DET` and `P34 BAL`. You can dial the same
  parameter up on hardware and check that the two agree. One caption changed
  with it: the machine calls P34 *D.O. Balance*, so the box says BAL rather
  than the MIX the panel used to show.

---

## v0.5.79 — 2026-09-12 — One set of text sizes, across both products

- **Text is now set to a scale rather than to whatever looked about right.**
  Between them the two products wrote 257 font sizes by hand. Mample used 14
  different ones and DSKlusion 15, and on the main window each drew eight at
  once. The three doing nearly all the work sat within two pixels of each
  other, which is not a scale, and it is the reason nothing on either screen
  read as more important than anything else. There are now five steps, each
  named for the job it does, and a component asks for the job. Both windows
  render four of them plus the wordmark.
- **The disk browser had a second, invisible scale.** Nineteen of its sizes
  were set in half-pixels — 7.5, 8.5, 9.5, 10.5, 11.5 and 12.5 — alongside the
  whole-pixel ones. Those are gone.
- Nothing is clipped by the change. Every piece of text in both windows was
  measured against its box before and after, and none of it overflows.
- The product wordmarks keep their own sizes. They are a logo set in type, not
  a heading.

---

## v0.5.77 — 2026-09-11 — Mample looks designed rather than assembled

- **The interface has one typeface.** Mample now renders in Inter, the same
  face XCent uses, instead of whatever sans-serif your system happened to
  supply. Numbers that change while you play — the voice count, the filter and
  mix values — use fixed-width figures, so they no longer jitter and shove
  their neighbours around as they update.
- **Its own symbols come from the plugin, not from your operating system.**
  Every arrow, caret, tick, cross and the eject and edit glyphs were being
  drawn by whichever font Windows offered, which is why they never quite
  matched. They are bundled now, and cost 4 KB to do it.
- **The accent colour means something.** The info panel used to print its
  labels in bright amber and its values in grey, so the word "Disk:" was
  louder than the name of the disk. That is the other way round now, and amber
  is kept for values that are live — the parameters read off the sound you
  loaded.
- **Panels have depth again.** The disk browser was drawn entirely with flat
  one-pixel outlines. The list is now a recess, a sound sits on it, and the
  one you have loaded is pressed into it.

---

## v0.5.74 — 2026-09-11 — Mample sees disks in subfolders

- **Disks filed into subfolders were invisible, and now are not.** Mample's
  library scan only ever looked in the top level of the disks folder, so a
  collection organised into directories showed up empty or half-empty with
  nothing to say why. The scan now reads the whole tree, and the browser
  groups it into folders you can collapse, nested as deeply as your filing
  goes. A library kept in one flat folder looks exactly as it did.
- **Loading a disk from a subfolder works.** Once the scan could see them,
  loading still could not reach them: the load looked only in the top level.
  It now follows the folder the disk was actually found in, which also matters
  when two folders hold different disks under the same filename — those are
  now two rows that can be told apart and selected separately, rather than
  one row standing in for both.

---

## v0.5.73 — 2026-09-11 — Choose where your disks live, and a restored session names its sounds

- **You can choose where your sound disks live.** Settings gains a Sound tab
  with a folder chooser for the disk library, so a collection on another drive
  no longer has to be copied into Documents. Changing it rescans immediately,
  and the Open dialog starts there too. A folder that is not reachable — an
  unplugged drive — falls back to the default rather than showing an empty
  library. The disk catalogue itself stays where it was, shared with
  DSKlusion.
- **A restored session names its sounds again.** Reopening the standalone, or
  a project, brought the sounds back and drew their waveforms but left the
  panels showing only the disk's name. The per-half sound identity was only
  ever published when you loaded from the browser, so a restore never sent it.
  Every route into the engine now reports the same three things.

---

## v0.5.72 — 2026-09-11 — Upper above lower, and the browser says what is loaded

- **Upper sits above lower in the browser's sound list.** Every other surface
  in the product reads that way round — the upper waveform panel is the top
  one, and the keyboard's upper half is the right-hand end — so a list running
  lower-first was the only place reading bottom-up.
- **The browser header names the disk you have loaded.** The list is a library
  of disks you could load; the header now says which one you did. Where the
  two halves came from different disks, it names whichever was loaded most
  recently.
- **Each waveform panel names its own disk.** Found while checking the change
  above: with a sound loaded into each half from a different disk, the upper
  panel paired the mounted disk's name with the other disk's sound. Each half
  now names the disk its own sound came from.

---

## v0.5.71 — 2026-09-11 — The waveform panels name their sound, and a disk fits the browser

- **The waveform panels say which sound they are drawing.** Each header now
  reads the disk, the half, the slot and the patch name — for example
  `Upper: Factory Disk C06 - U2 High Voices "AH`. Both panels used to show the
  disk name and nothing else, so they said the same thing as each other and
  neither told you which of the disk's six sounds was loaded there. A half
  with nothing loaded still shows just the disk, rather than borrowing the
  other half's name.
- **A whole disk fits the browser.** The sound list spent about half its
  height on chrome around single lines of text: a heading for every slot, and
  generous padding around each name. The slot number now rides on its own row
  as an `L1` / `U1` tag, and the rows are as tall as the text needs. All six
  halves of a three-slot disk are on screen at once, where before the third
  slot could not be reached. Nothing was removed: the names, the loaded
  marker, the load buttons and the wavesample breakdown all behave as before.

---

## v0.5.70 — 2026-09-11 — Stray pale lines where the page meets the window

- **The keys have a floor.** The white line across the bottom of Mample's
  window was the keyboard itself. The page stood a fraction of a pixel taller
  than the window it was given, so the near-white key faces were clipped flush
  into the bottom edge — which is why the line disappeared whenever the
  keyboard was hidden, and why nothing in the page ever looked like a border.
  The keys now sit on a 10px margin matching the gutter already either side of
  them, and the window grew from 458 to 469 pixels to pay for it. Hiding the
  keyboard leaves that layout exactly as it was.

- **The surface behind the page now matches the page.** The editor's own fill
  and the web view's background colour were a light grey in both products,
  lighter than anything at the top of either window, so any seam between the
  web view and the window hosting it read as a pale line. Both now match the
  header.

---

## v0.5.69 — 2026-09-08 — Opt-in telemetry and an in-plugin issue reporter, compiled out by default

- **Opt-in telemetry and an in-plugin issue reporter, both compiled out by
  default.** Ported from the shared plugin boilerplate as one library both
  products link. When a build enables them, anonymous session data is sent only
  after you have been asked once and said yes — never audio, never your samples,
  never anything that identifies you — and "Report an Issue…" in About opens a
  pre-filled form, or hands you a copyable URL if it cannot reach the server.
  Turned **off** in every build shipped so far.

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
