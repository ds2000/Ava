# Ava Pro · Home Assistant's Android Companion

[![DeepWiki](https://img.shields.io/badge/DeepWiki-AI_Docs-003366?style=for-the-badge&labelColor=002244&logoColor=white)](https://deepwiki.com/knoop7/Ava)
![GitHub Downloads](https://img.shields.io/github/downloads/knoop7/ava/total?style=for-the-badge&logo=github&color=0D1117&labelColor=21262d&logoColor=white&label=DOWNLOADS)
[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/knoop7)



For more practical guides, visit the [Wiki](https://deepwiki.com/knoop7/Ava).


Share a project I've been working on: **Ava**, an Android voice assistant app that turns old tablets, phones, **car head units, smart mirrors, and Android-powered appliances** into powerful smart home control panels. **Compatible with the full range of Android ecosystems.**

## Background

This project is based on [brownard/Ava](https://github.com/brownard/Ava) with extensive modifications and extensions. The original was a great ESPHome voice satellite implementation, but with basic features. I researched existing solutions: [Fully Kiosk](https://www.fully-kiosk.com/) is powerful but paid. [WallPanel](https://wallpanel.xyz/) is no longer maintained. The Android smart home panel space has been stagnant for years. So I decided to combine the best of these projects, using Ava as the foundation to build something truly useful.

## Core Philosophy

`No Extra Integrations`
No MQTT, no HACS. Devices are discovered natively by Home Assistant, just like ESPHome nodes.

`Built for Low-End Hardware`
Supports Android 5–16, including 32-bit devices. Cheap tablets and old phones work reliably.

---

## Bluetooth Proxy - Exclusive Feature

**This is a feature no other Android panel app has.**

Your Android device becomes a complete Bluetooth gateway, extending Home Assistant's Bluetooth coverage. No ESP32 needed - just use your spare Android device!

**Features:**
`BLE Proxy` Forwards all Bluetooth Low Energy data to Home Assistant.
`Whole-Home Coverage` Deploy multiple Ava devices, each extends Bluetooth range.
`Presence Detection` Auto-detect phones, smartwatches, bands; trigger home/away automations.
`All BLE Devices Compatible` Temperature sensors, plant monitors, smart locks, all supported.

**Why This Matters:**
ESP32 Bluetooth proxies need firmware flashing and configuration. Ava works out of the box - your Android device is already a powerful Bluetooth transceiver. Perfect for apartments or multi-story homes where one Bluetooth source isn't enough. Turn that dusty old tablet in the bedroom into a Bluetooth relay point.

**Presence Detection Use Cases:**
Phone enters Bluetooth range → Auto lights on, AC on, play welcome message. Phone leaves for a while → Auto lights off, security mode on. Detect specific family member devices → Personalized scene triggers. Adjustable RSSI threshold and away delay for precise sensitivity control.

This feature alone is worth trying if you've struggled with Bluetooth coverage in Home Assistant.

> **Note:** Bluetooth proxy source code is not open source, only available in release builds. All other feature code is available on GitHub.

---

## Voice Messages & Calls - Local Home Intercom

Turn multiple Ava devices into a simple voice network inside your home. Send a quick voice message to another room, keep messages on a small message board, or start a live call between Ava devices on the same local network.

**Features:** **Voice Messages** - Record and send short messages to selected Ava devices. **Message Board** - Keep received messages on screen and replay them later. **Live Calls** - Call another Ava device directly for room-to-room conversation. **Local Network First** - Designed for LAN use, without a cloud account or external relay.

**Why This Matters:** A wall tablet should not only listen to Home Assistant. It should also help people at home talk to each other. Ava can become a kitchen-to-living-room intercom, a bedside message board, or a quick way to call the study without picking up a phone.

**Home Use Cases:** Kitchen says dinner is ready → living room Ava plays the message. Parent leaves a delayed reminder for a child's room → message stays available for replay. Bedroom calls the hallway panel → quick conversation without phones or extra apps.

---

## What is Ava?

Ava is a voice assistant app based on the ESPHome protocol. It turns your Android device into a voice satellite for Home Assistant.

**What can you do with it?**
Control smart home devices with voice (lights, AC, music, etc.). Display beautiful screensavers and clocks. Show real-time weather information. Display full-screen notifications (doorbell, alerts, etc.). Play music with album cover display. Take photos and stream video.

Put your old phone or tablet at home, and it becomes a smart control panel!

**System Requirements:**
Android 7.0 or higher. Home Assistant connection required.

> This makes Ava suitable for turning *any* phone or tablet into a native-looking Home Assistant panel, consistent with the rest of your HA ecosystem.

> Ava does not impose a custom UI identity.
> Instead, it deliberately follows Home Assistant’s visual language and iconography.
> This ensures that any device running Ava feels like an extension of Home Assistant itself, not a third-party layer on top.

---

## Quick Start

### Step 1: Install

1. Download the Ava APK file from [GitHub Releases](https://github.com/knoop7/Ava/releases) Built-in auto-update feature.
2. Tap to install.
3. Allow all permission requests (microphone, overlay, etc.).

### Step 2: Connect to Home Assistant

**In Home Assistant:**
1. Go to **Settings** → **Devices & Services** → **Integrations**.
2. Search and add **ESPHome** integration.
3. Ava will be discovered automatically, tap **Configure**.

### Step 3: Talk!

Say the wake word (default is "Hey Jarvis"), then say your command: "Turn on the living room light". "What time is it". "Play music". "What's the weather tomorrow".

---

## Permissions

**Required:**
`Microphone` To hear you speak.
`Overlay` To show screensaver, notifications, weather, etc.
`Foreground Service` To keep service running.

**Optional:**
`Camera` For photos and video.
`Bluetooth` To detect if you're home.
`Location` Required for Bluetooth scanning.
`System Settings` Screen brightness control.

**Root (Recommended):**
Better background protection, boot scripts, screen control, reboot. Works without Root, but more stable with it.

---

## Credits

*   Original Project: [brownard/Ava](https://github.com/brownard/Ava)
*   ESPHome: https://esphome.io/
*   Home Assistant: https://www.home-assistant.io/

---

*Last Updated: 2026-06-14*
