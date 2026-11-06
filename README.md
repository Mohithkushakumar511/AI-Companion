# AI Companion 🐱⚡

[![GitHub release](https://img.shields.io/github/v/release/Mohithkushakumar511/AI-Companion?include_prereleases&style=flat-square&color=blue)](https://github.com/Mohithkushakumar511/AI-Companion)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Electron](https://img.shields.io/badge/Electron-35.x-47848F?style=flat-square&logo=electron&logoColor=white)](https://www.electronjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-6.x-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev/)
[![Groq Vision AI](https://img.shields.io/badge/AI-Groq%20Vision%20(Qwen%203.8--27B)-F05032?style=flat-square)](https://groq.com/)
[![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-0078D6?style=flat-square&logo=windows&logoColor=white)](https://microsoft.com/windows)

> **AI Companion** is an intelligent, floating desktop companion for Windows built with Electron and TypeScript. It sits quietly on your screen as a friendly animated cat, observing your workspace in real-time, catching coding mistakes, typos, syntax errors, and bugs as you write them, and delivering concise spoken and visual suggestions powered by ultra-fast **Groq Vision AI** (`qwen/qwen3.8-27b`).

---

## 📸 Overview

```
       |\      _,,,---,,_
 Zzz   /,`.-'`'    -.  ;-;;,_
      |,4-  ) )-,_. ,\ (  `'-'
     '---''(_/--'  `-'\_)  🐱 "Hey! Check line 42, missing closing brace!"
```

- **Interactive Animated Cat**: A transparent, frameless, always-on-top companion that you can drag anywhere on your screen.
- **Real-Time Code Assistant**: Spots bugs, logic errors, and syntax issues as you code and physically points to them.
- **Privacy-First & DPAPI Secured**: Zero plain-text API key storage; pauses automatically whenever sensitive or private windows are in focus.

---

## 🌟 Key Features

### 🐱 Expressive Desktop Cat Overlay
- **Frameless & Transparent**: Floats cleanly over IDEs (VS Code, Visual Studio, JetBrains, etc.), terminals, and browsers.
- **Smooth Drag & Drop**: Click and drag the cat to reposition it anywhere across multi-monitor setups.
- **Stateful Animations**:
  - 😴 **Idle & Breathing**: Gentle breathing, subtle ear twitches, tail wags, and eye blinks.
  - 💭 **Thinking Mode**: Animated pulsing indicators while Groq AI analyzes your code.
  - 🗣️ **Speaking Mode**: Dynamic mouth movements synchronized with voice and speech bubbles.
  - 🎯 **Interactive Bug Pointing**: Points directly toward detected code mistakes on screen.
  - 🙈 **Privacy Blindfold**: Wears a red blindfold whenever sensitive applications are active.
  - 💤 **Sleeping State**: Snoozes peacefully when monitoring is paused.

### ⚡ Groq Vision AI (`qwen/qwen3.8-27b`)
- Powered by Groq's high-speed inference endpoint (`https://api.groq.com/openai/v1/chat/completions`).
- Employs a specialized pair-programming vision prompt engineered to detect:
  - Syntax errors & missing punctuation/brackets.
  - Runtime exceptions, undefined variables, and broken imports.
  - Typos in variable names, methods, or strings.
  - Logical flaws or unhandled promises/edge cases.
- Structured JSON output with urgency levels (`low`, `medium`, `high`) and confidence scoring.

### 🔒 Windows DPAPI Key Encryption (`safeStorage`)
- Your Groq API key is encrypted directly using the **Windows Data Protection API (DPAPI)** via Electron's `safeStorage`.
- Keys are **never** written to plain text, never logged, and never committed to version control.

### 🛡️ Privacy Shield & Active Window Blocker
- Real-time active window detection powered by a fast, non-blocking native watcher (`resources/active_window.ps1` with C# fallback).
- **Instant Auto-Pause**: Monitoring immediately halts when sensitive apps or private browsing windows are in the foreground:
  - Password managers (`1Password`, `Bitwarden`, `KeePass`, `LastPass`, etc.).
  - Private / Incognito browsing modes in Chrome, Edge, Firefox, Brave, Opera, and Tor.
  - Windows with sensitive titles containing keywords like `password`, `bank`, `credential`, `auth`, `token`, etc.
- Custom process and keyword blacklist configurable via the **Settings** menu.

### 🧠 Smart Pixel Diffing (Quota & Bandwidth Saver)
- Compares downsampled pixel buffers between capture intervals.
- Skips AI calls when your screen is static, dramatically reducing API quota usage and network traffic.
- Configurable change threshold slider in Settings.

### 🗣️ Natural Text-to-Speech (TTS)
- Uses Windows local Text-to-Speech voices (e.g., Microsoft David, Zira, Mark) with zero external network latency.
- Adjustable speech rate and pitch.
- **Mute Toggle**: Easily mute audio while continuing to receive visual speech bubbles on screen.

### 📊 Quota Tracking & History Retention
- Set custom daily API request limits with automatic midnight resets.
- Temporary screenshot buffers are encrypted locally and automatically deleted based on your chosen retention window (Immediate, 1 hour, 6 hours, 24 hours), with a one-click manual purge option.

---

## 🚀 Getting Started

### Prerequisites

- **Operating System**: Windows 10 or Windows 11 (64-bit)
- **Node.js**: v18.0.0 or higher (v20+ recommended)
- **npm**: v9.0.0 or higher
- **Groq API Key**: Free API key from [Groq Console](https://console.groq.com/keys)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Mohithkushakumar511/AI-Companion.git
   cd AI-Companion
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Build the application**:
   ```bash
   npm run build
   ```

4. **Launch AI Companion**:
   ```bash
   npm start
   ```

---

## 🔑 Setting Up Your Groq API Key

1. Start AI Companion using `npm start`.
2. On first run, the **Settings & Privacy** window opens automatically. (You can also open it anytime by double-clicking the cat, clicking the ⚙ gear button, or pressing <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>S</kbd>).
3. Switch to the **⚡ Groq AI Config** tab.
4. Paste your Groq API key (`gsk_...`) into the input box.
5. Click **Save Key** — the key is immediately encrypted using Windows DPAPI.
6. Click **⚡ Test Groq Connection** to verify key validity and network connectivity.

---

## ⌨️ Global Keyboard Shortcuts

| Shortcut | Action | Description |
|---|---|---|
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>M</kbd> | **Pause / Resume** | Toggles screen monitoring and puts cat into sleep/active state |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>S</kbd> | **Settings** | Opens the Settings & Privacy configuration dashboard |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>D</kbd> | **Dismiss** | Closes any currently displayed speech bubble |

---

## 📦 Building & Packaging for Windows

### Development Scripts

- **Type Check**:
  ```bash
  npm run typecheck
  ```
- **Build Main & Preload**:
  ```bash
  npm run build:main
  ```
- **Build Renderer with Vite**:
  ```bash
  npm run build:renderer
  ```
- **Full Build**:
  ```bash
  npm run build
  ```

### Standalone Windows Installer

To build a standalone Windows installer (`.exe` NSIS package):

```bash
npm run package:win
```

The output installer and binaries will be generated inside the `release/` folder.

---

## 📁 Project Architecture

```
AI-Companion/
├── resources/
│   ├── active_window.ps1     # Native Windows foreground window watcher (Device Guard safe)
│   ├── ActiveWindow.cs       # C# P/Invoke source for compiled fallback
│   └── active_window.exe     # Compiled native helper binary
├── src/
│   ├── main/
│   │   ├── main.ts           # Electron lifecycle, window creation, system tray, hotkeys
│   │   └── services/
│   │       ├── secureStore.ts   # Windows DPAPI safeStorage for credentials & encrypted history
│   │       ├── privacyShield.ts # Active foreground window watcher & sensitive app auto-pause
│   │       ├── screenMonitor.ts # desktopCapturer, pixel diff engine, Groq vision loop
│   │       ├── groqClient.ts    # Groq API vision client, JSON parser, error sanitizer
│   │       ├── quotaTracker.ts  # Daily request limits & midnight rollover scheduler
│   │       └── settingsStore.ts # Persistent configuration store
│   ├── preload/
│   │   └── preload.ts        # Secure, context-isolated IPC bridge for renderers
│   ├── renderer/
│   │   ├── cat/              # Floating Cat UI (CSS keyframe animations, SpeechSynthesis, canvas)
│   │   └── settings/         # Settings UI (DPAPI key manager, Shield blacklist, TTS config)
│   └── shared/
│       └── types.ts          # Strongly typed TypeScript interfaces & IPC contracts
├── package.json              # Project metadata & build scripts
├── tsconfig.json             # Root TypeScript bundler configuration
├── tsconfig.main.json        # Main process CommonJS TypeScript configuration
├── vite.config.ts            # Vite multi-page renderer bundling configuration
└── README.md                 # Complete project documentation
```

---

## 🛡️ Privacy & Security Principles

- **No Remote Telemetry**: AI Companion does not track, store, or sell user telemetry.
- **Direct Groq Transmission**: Screen captures are transmitted solely to your own personal Groq API account over HTTPS.
- **Device-Bound Security**: Cryptographic keys are bound to your Windows user account via DPAPI and cannot be decrypted on other machines.
- **Automatic Blacklist Shielding**: The application immediately pauses capture when switching to sensitive apps like password managers and banking sites.

---

## 👤 Author

**Mohith Kusha Kumar**
- GitHub: [@Mohithkushakumar511](https://github.com/Mohithkushakumar511)
- Repository: [AI-Companion](https://github.com/Mohithkushakumar511/AI-Companion)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) - see the [LICENSE](LICENSE) file for details.
