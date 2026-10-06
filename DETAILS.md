# LiveRundown — Full Manual

This is the detailed reference for LiveRundown: every feature, every control, and how to set it up. For the quick pitch, see [README.md](README.md).


## Navigation

* Tap / click anywhere: Advance one line
* Double-tap a line: Jump directly to that line
* Arrow Down / F13: Advance one line
* Arrow Up: Go back one line

## Page scale

* **Open the ⚙️ Settings button** (top-right corner) to adjust the page's zoom level from 50% to 500%, via slider or direct number entry
* Scales the entire interface — script, dashboard, and every panel — exactly like a browser's native zoom

## Sync

* **Open the SYNC button** (bottom-right of the dashboard)
* **To broadcast:** toggle "Broadcast my index?" on, optionally set your name
* **To follow:** leave the toggle off and tap a broadcaster from the Available broadcasts list
* **To disconnect:** tap the active broadcaster again

If a follower's connection drops mid-show, their view simply stays put — it doesn't know the broadcaster has kept advancing. While it's down, the sync icon turns 🟠, so a frozen screen never looks live; a toast announces the drop and the reconnect. Once reconnected, it jumps straight to the broadcaster's current index.

* **Auto-pair** On page load, LiveRundown briefly checks for a single active broadcaster and — if it finds exactly one — follows it automatically, with a toast confirming who you were paired to. It detects a broadcaster with one of two ways: instantly if another LiveRundown tab/window is open in the *same browser*, or via the same *public network* (matched by public IP) if it's a different browser or a different device. If it finds no broadcaster, or more than one, it does nothing — same as opening the app normally  Controlled by `AUTO_PAIR` in index.html (see [Edit index.html](#edit-indexhtml))

* **Handover** * While you're broadcasting, every other broadcaster in the list shows a **Handover** button (instead of the follower's green dot). Tap it to make an offer
 * The other broadcaster gets an **Accept / Decline** card, pinned above their notifications. Nothing moves until they accept — and only *your* followers are ever affected, so an offer landing on a different rehearsal is harmless
 * **Accept:** they take over from exactly the line you were on, all of your followers switch to them, and your device stops broadcasting
 * **Decline** or no answer within `HANDOVER_OFFER_TIMEOUT_MS` (30 seconds): you get a toast and nothing changes
 * A follower who was offline during the handover is still redirected when they reconnect (for `HANDOVER_POINTER_TTL_MS`, 2 minutes)
 * The recipient must be broadcasting themselves — a follower can't accept
 * Handover keeps a short-lived pointer under `handovers/` in Firebase. The open rules from the setup guide already allow it; if you've locked your rules down, allow read/write on `broadcasts/` and `handovers/`

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

## Notepad

A rich-text notes panel for jotting observations during a read-through or live run, independent of script position.

* **Open the NOTES button** to show a draggable, resizable window with a small rich-text editor (bold, italic, underline)
* **Shorthand keybinds** insert a formatted reference to a script line at the cursor while typing:
  * **Backtick (`` ` ``)** inserts a reference to the *current* line
  * **Tilde (`~`)** inserts a reference to the most recent `<LOG>`-marked line reached
* **Export** saves the note content as its own `.md` file
* Content stays in the panel for the session but is not saved between reloads

## Timer & session log

* **Open the TIMER button** to start/pause a running clock for the session, independent of script position

* Any line prefixed with `<LOG>` in `script.md` is timestamped automatically the moment it's reached — but only while the timer is running
* Download the session's log as a plain-text file from the same panel, one timestamped entry per line, in the order they occurred

## Notify

Sends an instant toast notification to every connected device — broadcaster and all followers alike.

* **Automatic:** any `<NOTIFY>` line in `script.md` fires the moment it's reached while advancing forward. Formatted as: `<NOTIFY> Message`
* **Manual:** the **🔔 Notify button** (broadcaster only — hidden for followers, since there's nothing for them to page out to) opens a free-text prompt and sends it the same way
* Notifications stay on screen until you tap their **✕**, or until `NOTIFY_TIMEOUT_MS` (1 minute by default) passes — so prompters, who can't tap, never end up with a stuck message. The timeout starts when a notification is shown, and a shrinking bar along its bottom edge shows the time left
* Up to `NOTIFY_MAX_VISIBLE` (3) notifications stack at once; any more wait in a queue and appear as earlier ones close
* No history — closed or expired notifications are gone, nothing is logged or saved
* A device that reconnects mid-show won't see a stale notification replayed — only genuinely new ones show up

## Checklist

An optional, read-only companion list — for props, costume changes, or any per-show checklist — rendered from its own file, entirely separate from `script.md`.

* If a `checklist.md` file sits alongside `script.md`, the **📋 Checklist button** appears automatically; if it's missing, the button simply doesn't show
* Renders standard markdown: `#`/`##`/`###` headers, plain text, and `---` as a horizontal rule
* `- [ ] Item text` lines become tappable checkboxes — tap to check/uncheck, checked items grey out and strike through
* Checked state lives only on this device, for this session — never synced to other devices, never saved between reloads

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
| `<LOG> Line` | Prefixed onto any line | Marks that line for the Timer's session log; the rest of the line still parses and displays normally |
| `<NOTIFY> Message` | Its own line, anywhere | Sends the given text as a toast to every connected device the moment the line is reached (forward advances only) — see [Notify](#notify) |

You may change those markers, by editing index.html (see [Edit index.html](#edit-indexhtml))

## Interface controls

* **Hide Bar:** collapses the entire bottom dashboard out of view (with a confirmation step), for a fully distraction-free script view
* **Collapsible button group:** the bottom-right buttons collapse into a single compact indicator showing live sync status (🔴/🟢/🔵) — purely a UI declutter, doesn't touch the sync connection itself


## Markdown format

Standard raw script text, one line per entry:

```
ACTOR (action) Dialogue text here
```

Use `*italics*` or `***italics***` within dialogue for emphasis (rendered as italic text, not literal asterisks).

## Edit index.html

To set up and customize your edition of LiveRundown, edit the ✏️ **CONFIG** block at the very top of [index.html](index.html) (or search for '✏️' with Ctrl+F). From there, you can edit:
* **`FIREBASE_CONFIG`** - Your Firebase credentials, in order to use Sync
* **Markdown syntax markers** - What markers the app uses, to trigger hidden actions (see [Script Markers](#script-markers))
* **`colorPalette`** - The list of colors used for each actor, in order (first pinned actors, then by first appearance)
* **Countdown dashboard proximity warnings** - Toggle if countdown warnings are displayed (`SHOW_COUNTDOWN_WARNINGS`), if flashing effects are allowed (`FLASHING_EFFECTS`), and how many lines are remaining to trigger the "approaching" state (`WARNING_THRESHOLD`). (see [Countdown Dashboard](#countdown-dashboard))
* **`AUTO_PAIR`** - Toggle automatic pairing to a lone live broadcaster on launch. (see [Sync → Auto-pair](#sync))
* **`RTL`** - Mirror the interface for right-to-left languages: buttons, panels and notifications move to the other side, and each script line takes its direction from its own text (so an English stage direction inside a Hebrew script keeps its normal order). The PDF export mirrors its layout as well (colored tag on the right, page number on the left). **Known limit:** the PDF can't typeset Hebrew/Arabic *text* — its built-in font has no such letters and its layout engine has no right-to-left support — so RTL-script scripts should be printed from the browser for now
* **`AUTO_COLLAPSE_ON_FOLLOW`** - Toggle whether the bottom button row auto-collapses when this device starts following a broadcaster
* **`KEEP_SCREEN_AWAKE`** - While a script is loaded, keep the device screen from dimming or sleeping (default `true`). 
* **`NOTEPAD_SHORTHAND_CURRENT_LINE_KEY` / `NOTEPAD_SHORTHAND_LOG_LINE_KEY`** - The keybinds for the Notepad's line-reference shorthand, or disable either by setting it to `''` (see [Notepad](#notepad))
* **`NOTEPAD_MARKDOWN`** - Toggle Markdown typing shortcuts in the Notepad (`*italic*`, `**bold**`, `***bold italic***`)
* **`SYNC_COLORS`** / **`ANIMALS`** - Sync state colors, and the random animal names given to new broadcasters
* **PDF export defaults, page scale limits and timings** - `EXPORT_DEFAULT_*`, `SCALE_*`, `TOAST_DURATION_MS`, `MY_LINES_HOLD_MS`, `BROADCAST_*`

Right below it, the ✏️ **STRINGS** block holds every piece of text the app shows (button labels, panels, toasts, and downloaded file names), so you can translate the whole app in one place. File names support `{YYYY}` `{YY}` `{MM}` `{DD}` `{HH}` `{mm}` `{ss}` tokens (e.g. `notes-{YYYY}-{MM}-{DD}`).
