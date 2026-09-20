# Phone2Phone USB-OTG Hardware Flasher 🔌📱

[![Android](https://img.shields.io/badge/Platform-Android-green.svg)](https://www.android.com)
[![Kotlin](https://img.shields.io/badge/Language-Kotlin-purple.svg)](https://kotlinlang.org)
[![Jetpack Compose](https://img.shields.io/badge/UI-Jetpack_Compose-blue.svg)](https://developer.android.com/jetpack/compose)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Phone2Phone USB-OTG Flasher** is an advanced, unrooted Android application that turns an Android host device into a low-level USB-OTG flashing and debugging station. It communicates directly with another device's SoC Boot ROM (Qualcomm EDL 9008, MediaTek BROM, Fastboot) over raw USB endpoints before Android ever loads—requiring **zero root privileges** on the Host phone.

---

## 🌟 Key Features

### 1. 🎯 OTG Target Discovery & Auto-Detection
* Scans connected USB-OTG targets in real-time (`UsbManager`).
* Displays VID, PID, manufacturer, serial numbers, and interface counts.
* **Automated SoC Auto-Detection**: Instantly fingerprints connected hardware (e.g., `0x05C6:0x9008` for Qualcomm EDL or MediaTek BROM) and auto-selects the correct protocol mode.
* **Pulsing Radar Animation**: Visual scanning radar when searching for targets.

### 2. ⚡ Chunked Firmware Streamer & Payload Flasher
* Select any `.bin` or `.img` firmware partition file using Android's system file picker.
* Streams payloads in optimized 64KB blocks over USB bulk endpoints with a real-time progress bar and completion tracker.
* **Host Battery & Thermal Interlock**: Verifies host battery health (>15%) before executing heavy firmware transfers to prevent unexpected power loss.

### 3. 🛠️ Interactive Fastboot Terminal
* Dedicated fastboot console allowing you to send raw host commands (`devices`, `getvar:version`, `getvar:all`, `reboot`, `reboot-bootloader`).
* One-tap shortcut buttons for common bootloader diagnostic queries.

### 4. 📜 Automated Flash Scripts
* Run pre-packaged multi-step batch scripts (such as *Qualcomm EDL Init Batch* or *Fastboot Info Batch*) that execute handshakes and command sequences automatically.

### 5. 🔍 USB Packet Sniffer & GPT Partition Dumper
* **Hex + ASCII Inspector**: Inspect raw binary packets and responses sent over USB endpoints.
* **GPT Dumper**: Read GPT partition table sectors (LBA 0/1) directly from raw bulk IN endpoints.
* **Throughput Benchmark**: Push synthetic 1MB test buffers to measure raw USB-OTG transfer speeds (`MB/s`).

### 6. 🎨 Hacker Terminal Themes & Easter Eggs
* **Theme Customizer**: Toggle between *Material 3 Standard*, *Hacker Green Terminal*, and *Amber Monochrome* themes.
* **Haptic Feedback**: Tactile vibrations upon successful connection and flash completion.
* **Secret Easter Egg**: Tap the top app title 5 times to unlock the *"Elite USB Operative"* achievement badge!

---

## 🛠️ Tech Stack

* **Language**: 100% Kotlin
* **UI Toolkit**: Jetpack Compose & Material 3
* **USB Host API**: `android.hardware.usb` (`UsbManager`, `UsbDeviceConnection`, `UsbEndpoint`, Bulk Transfers)
* **Concurrency**: Kotlin Coroutines & Flows

---

## 📱 Getting Started

1. **Hardware Requirements**:
   - Host Phone: Android device running this app.
   - Target Phone: Device to be flashed/debugged.
   - Cable: **USB-C to USB-C** cable or USB-C to USB-A OTG adapter with data lines.
2. **Setup**:
   - Clone the repository and open the project in **Android Studio**.
   - Connect an Android device and click **Run**.
3. **Usage**:
   - Boot your target device into EDL / BROM / Fastboot mode.
   - Plug it into the Host phone via OTG.
   - Open the app, grant USB permission, and use the Flasher or Fastboot tools!

---

## ⚠️ Disclaimer
Low-level SoC flashing and Boot ROM communication interact directly with device hardware. Use correct firmware binaries and loaders for your specific device model. Improper flashing can result in permanent device bricking. Use at your own risk.

---

## 📜 License
Licensed under the [MIT License](LICENSE).
