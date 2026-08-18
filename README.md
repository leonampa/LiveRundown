# 🎭 LiveRundown

LiveRundown is an open-source, real-time theatrical rundown engine, designed to replace static paper scripts for backstage crews. Built for low-latency, multi-device synchronization, it ensures stage managers, lighting operators, and audio technicians stay locked to the exact same cue line globally, compiled as a single HTML file, hosted on Netlify, and powered by Firebase.

[![Donate via Revolut](https://img.shields.io/badge/Donate-Revolut-FFFFFF?style=for-the-badge&logo=revolut&logoColor=white)](https://revolut.me/leonampa) [![License: Custom](https://img.shields.io/badge/License-Custom-238636?style=for-the-badge)](LICENSE)

### See live: [https://leonampa.github.io/liverundown/demo](https://leonampa.github.io/liverundown/demo)
> Real-time global device syncing is disabled to protect my Firebase free-tier usage limits from public API abuse. The UI navigation, hardware key bindings, and markdown parser are fully functional locally.

<video src="https://github.com/user-attachments/assets/7b52f6a1-ca9a-42d6-870e-d7ce88039eb3" autoplay muted loop></video>

## The Problem
During theatrical productions involving large ensembles (50+ cast and production crew members), traditional script management breaks down:

* **The "Lost Tracker" Dilemma:** While a Stage Manager or Prompter can keep a finger on a static paper script or PDF, actors moving on stage must look up and use props, immediately losing track of their current line.
* **The Rehearsal Burn Rate:** Up to 5 minutes per scene transition is lost simply getting a massive cast aligned on the correct script index, stalling creative momentum.
* **The Communication Void:** Static PDFs cannot communicate immediate pacing adjustments or line progressions from the tech desk to backstage in real-time.


## The Solution: LiveRundown
LiveRundown digitizes markdown scripts and processes them into a high-visibility, deterministic grid interface. Operating on a broadcaster-receiver architecture powered by a low-overhead real-time database sync, any crew member or actor can track the exact line progression from their individual mobile devices or workstation terminals. On top of live tracking, it doubles as a rehearsal tool, a pacing log, and a print-ready script exporter — all from the same markdown source and the same single HTML file.


## Key Features

* **🌐Live sync** across every device, broadcaster → receivers, powered by Firebase
* **⏳Per-actor countdowns** with automatic color allocation and proximity warnings
* **👤My Lines** — long-press to isolate one or more actors' tracks
* **⏱️Timer & session log** for pacing data
* **📄One-click PDF export** of the loaded script
* **🔘Hardware key bindings** for foot pedals / Stream Decks
* Single dependency-light HTML file — no build step, no install

## Setup

* Go to [Firebase](console.firebase.google.com), and log in with any Google account
* Click "Create a project", name it, disable Google Analytics, click Create Project
* Click "+ Add app", click "</>"/Web, give your app a name, do **NOT** check "Also set up Firebase Hosting", click "Register"
* Firebase now shows you a firebaseConfig object. It looks like a block of JavaScript with an apiKey, authDomain, etc. Copy the whole thing onto a notepad. Click "Continue to console".
* In the left sidebar, go to "Databases & Storage" → "Realtime Database", click "Create Database"
* Choose the server location closest to you
* Click "Start in test mode", click "Enable", and copy the URL that ends with "firebasedatabase.app"
* Go to Rules, change whatever is there, to the below block, click Save

~~~JSON
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
~~~
> ⚠️ These open rules are designed for low-friction setup within trusted, private cast networks. Adjust Firebase Auth/Rules if deploying publicly.
* Download [index.html](index.html) from this repo, open it, and edit the Firebase config (between lines 890 and 924 / search for the ✏️ marker near the top of the file)
* Place index.html and your script.md on a folder, and upload the folder as-is on Netlify
* Visit the given URL on two tabs/windows/devices, and check to see if it works like it should

### 📖 See **[DETAILS.md](DETAILS.md)** for the full manual: script markers, every control, and configuration instructions.


## Architecture & Tech Stack
The engineering philosophy behind LiveRundown prioritizes ultra-low friction deployment and maximum device compatibility. Backstage environments often rely on varying cell signals, older smartphones, and legacy hardware.

* **Frontend:** Vanilla HTML5, CSS3 Variables, ES6 JavaScript
* **Database & Synchronization:** Firebase Realtime Database
* **PDF Generation:** [pdfmake](https://github.com/bpampuch/pdfmake) (loaded via CDN, no build step)
* **Deployment Infrastructure:** Netlify

## Credits

Concept, architecture, and product definition by [@leonampa](https://github.com/leonampa).
Assisted by Anthropic's Claude Sonnet (full code development and feature implementation, debugging, and ongoing development) and Google's Gemini 3.1 (prototyping, GUI mockups, brainstorming, research).
