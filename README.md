# Ava Pro · Home Assistant's Android Companion

[![DeepWiki](https://img.shields.io/badge/DeepWiki-AI_Docs-003366?style=for-the-badge&labelColor=002244&logoColor=white)](https://deepwiki.com/knoop7/Ava)
![GitHub Downloads](https://img.shields.io/github/downloads/knoop7/ava/total?style=for-the-badge&logo=github&color=0D1117&labelColor=21262d&logoColor=white&label=DOWNLOADS)
[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/knoop7)

For more practical guides, visit the [Wiki](https://deepwiki.com/knoop7/Ava).


Share a project I've been working on: **Ava**, an Android voice assistant app that turns old tablets, phones, **car head units, smart mirrors, and Android-powered appliances** into powerful smart home control panels. **Compatible with the full range of Android ecosystems.**

## Background

This project is based on [brownard/Ava](https://github.com/brownard/Ava) with extensive modifications and extensions. The original was a great ESPHome voice satellite implementation, but with basic features. I researched existing solutions: [Fully Kiosk](https://www.fully-kiosk.com/) is powerful but paid. [WallPanel](https://wallpanel.xyz/) is no longer maintained. The Android smart home panel space has been stagnant for years. So I decided to combine the best of these projects, using Ava as the foundation to build something truly useful.

One Android device can become a voice satellite, Bluetooth proxy node, local intercom, floating overlay display, and smart control panel.

Ava Pro does not require MQTT, HACS, or a custom Home Assistant integration. It is discovered through the ESPHome flow, and the core APK is designed to stay under 20 MB so old and low-end devices remain practical.

---

### Floating Overlays

Ava Pro does not need to take over the whole screen. It can run as a background satellite service and show floating windows over other Android apps, including official apps, fullscreen dashboards, media players, browser panels, and normal Android apps.

This lets you keep using the app already on screen while Ava Pro shows voice replies, subtitles, clocks, weather, media feedback, quick controls, and assistant responses above it.


---

## Core Benefits

| Benefit | What it means |
|---|---|
| **Bluetooth Proxy** | Reuse Android Bluetooth hardware to extend Home Assistant Bluetooth coverage |
| **Local Voice Network** | Send voice messages or start room-to-room calls between Ava Pro devices on your LAN |
| **Floating Overlay UI** | Show assistant feedback, clocks, weather, media, and controls over other Android apps |
| **Privacy-conscious** | Voice messages and calls are local-first; voiceprint learning stays on the device |
| **Lightweight Core** | Designed to keep the core APK under 20 MB for older Android devices |

---

## Key Features

### 1. Bluetooth Proxy & Room Presence

Ava Pro turns spare Android devices into distributed Bluetooth coverage nodes for Home Assistant. Instead of buying and flashing ESP32 Bluetooth proxies for every room, you can reuse Android devices you already have.

This helps Home Assistant see BLE sensors, wearables, tags, plant sensors, temperature sensors, locks, and presence devices that may be too far from the main server.

| Feature | What it does | Why it helps |
|---|---|---|
| **BLE Proxy** | Extends Home Assistant Bluetooth coverage | Uses Android devices already placed around the home |
| **Presence Detection** | Detects phones, watches, bands, and tags | Enables room-aware or home/away automations |
| **RSSI Threshold** | Tunes Bluetooth distance sensitivity | Reduces false room detection |
| **Away Delay** | Delays away state after signal loss | Prevents brief Bluetooth drops from triggering false exits |
| **Scan Power Control** | Adjusts scan strength | Balances responsiveness, heat, power use, and device performance |
| **Multi-device Coverage** | Uses several Ava Pro devices as coverage points | Improves Bluetooth visibility across rooms or floors |

> Bluetooth proxy source code is not open source and is only available in release builds.

### 2. Local Voice Messages & Calls

Ava Pro devices can communicate directly on the local network. A kitchen panel can send a voice message to a bedroom display, a hallway tablet can call the living room, and a bedside device can keep a replayable voice note for later.

This makes Ava Pro more than a voice satellite. It can also act as a lightweight home intercom for families, shared spaces, reminders, elderly care, and always-on wall panels.

| Feature | What it does | Why it helps |
|---|---|---|
| **Voice Messages** | Sends short voice notes between Ava Pro devices | Useful for quick room-to-room messages |
| **Message Board** | Keeps received messages visible and replayable | Helps family members see missed messages |
| **Live Calls** | Starts real-time calls between Ava Pro devices | Turns panels into a simple home intercom |
| **Delayed Messages** | Shows or plays messages later | Useful for reminders and scheduled notices |
| **LAN-first Design** | Works without a cloud relay for local calls/messages | Keeps local home communication simple and private |

---

## Feature Overview

| Area | Included features |
|---|---|
| **Voice Satellite** | Wake word, dual wake word, voiceprint, Home Assistant voice pipeline, continuous conversation, wake sound, mic gain |
| **Audio Processing** | Noise suppression, AGC, hardware AEC, software AEC, audio source modes, audio profiles |
| **Browser & View Assist** | WebView browser, optional GeckoView engine, View Assist frontend, browser scale, touch controls, overlay response UI |
| **Floating Overlays** | Dream Clock, Simple Clock, Weather, Subtitles, Vinyl/media overlay, Light Switch overlay, Quick Entity panel, global overlay back button |
| **Scenes & Screensaver** | Notification scenes, custom scene URL, scene duration, notification sound, screensaver URL, idle display |
| **Music & Media** | Music Assistant display, Home Assistant media state, album art, media overlay, Sendspin playback |
| **Device Controls** | Screen toggle, lock display, brightness, orientation, keep screen on, display size/scale |
| **Sensors & Camera** | Light, proximity, battery, Wi-Fi, storage, memory, uptime, snapshot, recording, face detection |
| **Android Integration** | Sidebar, app launcher, intent launcher, auto update, AvaMod / Mod Store, Portal support |
| **Permissions** | Normal Android permissions, overlay, Shizuku, Root, Device Admin support |

Most features are configured from `Settings`, including `Voice Config`, `Bluetooth`, `Extensions`, `Web Browser`, `Media Player`, `Device Controls`, `Screensaver`, `Sidebar`, `Permissions`, and `Mod Store`.

---

## Quick Start

### Step 1: Install

Download the latest APK from [GitHub Releases](https://github.com/knoop7/Ava/releases), install it on your Android device, and grant the required permissions.

### Step 2: Connect to Home Assistant

In Home Assistant, go to **Settings -> Devices & Services -> Integrations**, add **ESPHome**, and configure the discovered Ava Pro device.

### Step 3: Use Ava Pro

Enable the wake word, open your dashboard, turn on Bluetooth proxy, use floating overlays, send voice messages, or set up local room-to-room calls depending on your device and setup.

---

## Requirements

Android 5.0 or higher is supported. Home Assistant is required. Some advanced features depend on device hardware, Android version, permissions, Shizuku, root, or optional AvaMod modules.

Ava Pro works without root for normal use. Shizuku or root can unlock deeper device control where the device allows it.

---

## Permissions

| Permission | Used for |
|---|---|
| **Microphone** | Voice satellite, wake word, voice messages, and calls |
| **Overlay Window** | Floating clocks, subtitles, browser overlays, scenes, and media controls |
| **Foreground Service** | Keeps the satellite service running in the background |
| **Network** | Home Assistant connection, discovery, Sendspin, and local calls |
| **Bluetooth / Location** | Bluetooth proxy and BLE presence detection |
| **Camera** | Snapshots, video, and face detection |
| **System Settings** | Brightness, orientation, screen control, and display behavior |
| **Shizuku / Root / Device Admin** | Optional deeper control on supported devices |

---

## Lineage & Credits

Ava Pro is based on the original [brownard/Ava](https://github.com/brownard/Ava) project and has been significantly expanded for practical Home Assistant Android satellite use.

Powered by [ESPHome](https://esphome.io/) and designed for the [Home Assistant](https://www.home-assistant.io/) ecosystem.

---

*Last Updated: 2026-06-22*
