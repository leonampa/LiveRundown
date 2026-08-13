# LiveRundown — Full Manual

This is the detailed reference for LiveRundown: every feature, every control, and how to set it up. For the quick pitch, see [README.md](README.md).


## Navigation

* Tap / click anywhere: Advance one line
* Double-tap a line: Jump directly to that line
* Arrow Down / F13: Advance one line
* Arrow Up: Go back one line


## Sync

* **Open the SYNC button** (bottom-right of the dashboard)
* **To broadcast:** toggle "Broadcast my index?" on, optionally set your name
* **To follow:** leave the toggle off and tap a broadcaster from the Available broadcasts list
* **To disconnect:** tap the active broadcaster again

If a follower's connection drops mid-show, their view simply stays put — it doesn't know the broadcaster has kept advancing. Once reconnected, it jumps straight to the broadcaster's current index.


## Countdown dashboard

A fixed bottom row shows one block per actor, counting down the lines remaining until their next cue (or highlighting when it's their line right now).

* **Automatic color allocation:** each actor gets a distinct color the moment they first appear in the script (or via `<PIN>`, see below), used consistently on their dashboard block and every actor-tag in the script body.
* **Proximity warnings:** a countdown shifts to black-on-white once "approaching" (within a configurable line threshold), then solid or flashing white-on-red once "imminent" (0–1 lines away).


## My Lines

Lets one actor visually isolate their own track in a busy multi-actor script.

* **Press-and-hold** any actor's countdown box for ~3 seconds to add or remove them from your personal filter (a grey ripple animates while held; releasing early cancels the toggle with no effect)

* Selected actors' boxes move to the front of the dashboard, in their normal registration order among themselves
* Every line and countdown box belonging to a non-selected actor dims to 70% opacity
* A line with multiple actors (e.g. "A & B") stays full-brightness if *any* of its actors are selected
* Action/stage-direction rows are unaffected either way
* Multiple actors can be selected at once — deselecting the last one restores the normal view
* Nothing here is saved between reloads


## Timer & session log

* **Open the TIMER button** to start/pause a running clock for the session, independent of script position

* Any line prefixed with `<LOG>` in `script.md` is timestamped automatically the moment it's reached — but only while the timer is running
* Download the session's log as a plain-text file from the same panel, one timestamped entry per line, in the order they occurred


## PDF export

* **Open the EXPORT button**, set your preferred font size and page size, and generate a print-ready PDF of the loaded script — no build step, generated client-side via `pdfmake`

* Actor-tag columns carry the same auto-assigned colors as the live dashboard, proportionally scaled to fit multi-actor lines
* Long dialogue blocks wrap and paginate cleanly rather than being dropped or misrendered


## Script markers

Plain-text tags placed directly in `script.md`. All are invisible on the live page.

| Marker | Where | Effect |
|---|---|---|
| `NAME <PIN>` (or `NAME1 & NAME2 <PIN>`) | Very top of the file, before any other lines | Pins that actor (or actors) to the front of the countdown dashboard's default order, ahead of first-appearance order |
| `<PAGEBREAK>` | Its own line, anywhere | Forces a hard page break at that point in the PDF export only |
| `<LOG>` | Prefixed onto any line | Marks that line for the Timer's session log; the rest of the line still parses and displays normally |

You may change those markers, by editing index.html (see [Edit index.html](#edit-indexhtml))

## Interface controls

* **Hide Bar:** collapses the entire bottom dashboard out of view (with a confirmation step), for a fully distraction-free script view
* **Collapsible button group:** the Hide Bar / Export / Timer / Sync buttons collapse into a single compact indicator showing live sync status (🔴/🟢/🔵) — purely a UI declutter, doesn't touch the sync connection itself


## Markdown format

Standard raw script text, one line per entry:

```
ACTOR (action) Dialogue text here
```

Use `*italics*` or `***italics***` within dialogue for emphasis (rendered as italic text, not literal asterisks).

## Edit index.html

To set up and customize your edition of LiveRundown, edit [index.html](index.html) between lines 897 and 925 (or search for '✏️' with Ctrl+F). From there, you can edit:
* **`FIREBASE_CONFIG`** - Your Firebase credentials, in order to use Sync
* **Markdown syntax markers** - What markers the app uses, to trigger hidden actions (see [Script Markers](#script-markers))
* **`colorPalette`** - The list of colors used for each actor, in order (first pinned actors, then by first appearance)
* **Countdown dashboard proximity warnings** - Toggle if countdown warnings are displayed (`SHOW_COUNTDOWN_WARNINGS`), if flashing effects are allowed (FLASHING_EFFECTS), and how many lines are remaining to trigger the "approaching" state (WARNING_THRESHOLD). (see [Countdown Dashboard](#countdown-dashboard))