[# 🚀 Meta Quest "Freedom Protocol" (v2026.04)

This repository provides surgical ADB scripts to optimize the Meta Quest 3 and 3S for high-performance PCVR gaming while hardening the device for child safety. 

---

## 🚀 Meta Quest "Freedom Protocol" (v2026.04)

Welcome to the **Freedom Protocol**. This repository provides surgical ADB scripts to optimize the Meta Quest 3 and 3S for high-performance PCVR gaming while hardening the device for strict child safety. 

This project transforms the Quest from a tracked, ad-heavy social device into a dedicated, private gaming console.

---

## 🛠️ Developer Testing Environment
These scripts have been rigorously tested and benchmarked under the following conditions:
* **Headset:** Meta Quest 3S (Firmware v85+)
* **Terminal:** Quest Games Optimizer (QGO) Native ADB Shell
* **PCVR Host:** AMD Ryzen 7950X3D / NVIDIA RTX 4060 Workstation
* **Hardware Profile:** BoboVR M3 (loosened slightly for minimal face pressure) paired with the AMVR FC5 facial interface. *Note for 3S users: The AMVR FC5 for the Quest 3S does not feature the side adjustment dials found on the standard Quest 3 version. We highly recommend using the "Ice Silk" pad variant to prevent the itching commonly associated with PU leather during intense gaming sessions.*

---

## 📚 Command Reference Guide

Before running any script, understand exactly what is happening to your headset. There are no "mystery" commands here.

| Target Package | Category | Purpose | Why Disable It? |
| :--- | :--- | :--- | :--- |
| `com.oculus.unifiedtelemetry` | **Performance** | Main data-mining engine. | Stops constant "phone-home" pings, reclaiming CPU cycles. |
| `com.oculus.gatekeeperservice` | **Stability** | Server-side feature flag checker. | Prevents background network checks that cause micro-stutters. |
| `com.oculus.notification_proxy` | **UI / Social** | Social & system notifications. | Quiets the OS and stops social popups during PCVR streaming. |
| `com.oculus.bugreporter` | **Resources** | Background crash reporting. | Saves RAM. No need to send logs if you aren't a beta tester. |
| `com.oculus.os.logcollector` | **Resources** | Gathers system logs for Meta. | Reduces background storage I/O overhead. |
| `com.oculus.socialpresence` | **Privacy** | Tracks "Online" status/activity. | Makes you a "Ghost." Meta/Friends can't see what you play. |
| `com.oculus.messenger` | **Safety** | Meta Messenger/Chat app. | **Child Safety:** Blocks all direct messaging and social contact. |
| `com.oculus.people` | **UI Cleanup** | Friends list / Social connections. | Removes the social tab to focus strictly on your App Library. |
| `com.oculus.contacts` | **Privacy** | Phone & Facebook contact sync. | Prevents Meta from linking VR activity to real-world contacts. |
| `com.oculus.horizon` | **Safety** | Horizon Worlds (Social VR). | **Child Safety:** Blocks access to unmonitored multiplayer spaces. |
| `com.oculus.venues` | **Safety** | Live social event spaces. | Prevents children from entering live virtual crowd environments. |
| `com.oculus.explore` | **Ad Blocker**| "Suggested Content" boot feed. | Removes the "Ad Wall" and defaults boot directly to games. |
| `com.oculus.vrshell.home` | **UI Cleanup** | Interactive home environment. | Simplifies the UI shell to be leaner and boot faster. |
| `com.oculus.nux.ota` | **Anti-Brick** | Auto-update service. | **Critical:** Prevents update-bricks if battery dies during play. |
| `com.meta.ai` | **AI / RAM** | 2026 Background AI Assistant. | Reclaims ~150MB of RAM for heavy QGO Ultra profiles. |
| `com.oculus.voice.assistant` | **Privacy** | Legacy "Hey Facebook" listener. | Stops the microphone from constantly listening for wake words. |

---

## ⚡ Script 1: PC-to-Quest (The "GitHub Standard")
Use this script if you are running the commands from a PC, Mac, or Linux terminal via a USB-C connection. Ensure ADB is installed and USB Debugging is enabled on your Quest.

```bash
#!/bin/bash
# --- QUEST FREEDOM PROTOCOL (PC VERSION) ---

echo "Applying Performance & Telemetry Optimizations..."
adb shell pm disable-user --user 0 com.oculus.unifiedtelemetry
adb shell pm disable-user --user 0 com.oculus.gatekeeperservice
adb shell pm disable-user --user 0 com.oculus.notification_proxy
adb shell pm disable-user --user 0 com.oculus.bugreporter
adb shell pm disable-user --user 0 com.oculus.os.logcollector

echo "Applying Child Safety & Privacy Ghost Mode..."
adb shell pm disable-user --user 0 com.oculus.socialpresence
adb shell pm disable-user --user 0 com.oculus.messenger
adb shell pm disable-user --user 0 com.oculus.people
adb shell pm disable-user --user 0 com.oculus.contacts
adb shell pm disable-user --user 0 com.oculus.horizon
adb shell pm disable-user --user 0 com.oculus.venues

echo "Applying UI Cleanup & Anti-Brick Safeguards..."
adb shell pm disable-user --user 0 com.oculus.explore
adb shell pm disable-user --user 0 com.oculus.vrshell.home
adb shell pm disable-user --user 0 com.oculus.nux.ota

echo "Applying AI Debloat & RAM Recovery..."
adb shell pm disable-user --user 0 com.meta.ai
adb shell pm disable-user --user 0 com.oculus.voice.assistant

echo "Protocol Complete! Please restart your headset."
---

## ⚡ Section 1: Optimization Scripts (Freedom)

### **Option A: PC-to-Quest (USB/ADB)**


# Apply Freedom Protocol via PC
adb shell pm disable-user --user 0 com.oculus.unifiedtelemetry
adb shell pm disable-user --user 0 com.oculus.gatekeeperservice
adb shell pm disable-user --user 0 com.oculus.notification_proxy
adb shell pm disable-user --user 0 com.oculus.bugreporter
adb shell pm disable-user --user 0 com.oculus.os.logcollector
adb shell pm disable-user --user 0 com.oculus.socialpresence
adb shell pm disable-user --user 0 com.oculus.messenger
adb shell pm disable-user --user 0 com.oculus.people
adb shell pm disable-user --user 0 com.oculus.contacts
adb shell pm disable-user --user 0 com.oculus.horizon
adb shell pm disable-user --user 0 com.oculus.venues
adb shell pm disable-user --user 0 com.oculus.explore
adb shell pm disable-user --user 0 com.oculus.vrshell.home
adb shell pm disable-user --user 0 com.oculus.nux.ota
adb shell pm disable-user --user 0 com.meta.ai
adb shell pm disable-user --user 0 com.oculus.voice.assistant
# REBOOT HEADSET

Option B: Headset-Native (QGO Terminal)

# Paste directly into QGO ADB Terminal
pm disable-user --user 0 com.oculus.unifiedtelemetry
pm disable-user --user 0 com.oculus.gatekeeperservice
pm disable-user --user 0 com.oculus.notification_proxy
pm disable-user --user 0 com.oculus.bugreporter
pm disable-user --user 0 com.oculus.os.logcollector
pm disable-user --user 0 com.oculus.socialpresence
pm disable-user --user 0 com.oculus.messenger
pm disable-user --user 0 com.oculus.people
pm disable-user --user 0 com.oculus.contacts
pm disable-user --user 0 com.oculus.horizon
pm disable-user --user 0 com.oculus.venues
pm disable-user --user 0 com.oculus.explore
pm disable-user --user 0 com.oculus.vrshell.home
pm disable-user --user 0 com.oculus.nux.ota
pm disable-user --user 0 com.meta.ai
pm disable-user --user 0 com.oculus.voice.assistant
# REBOOT HEADSET

🔄 Section 2: Restoration Scripts (Revert)
Option A: PC-to-Quest (USB/ADB)

# Revert via PC
adb shell pm enable com.oculus.unifiedtelemetry
adb shell pm enable com.oculus.gatekeeperservice
adb shell pm enable com.oculus.notification_proxy
adb shell pm enable com.oculus.bugreporter
adb shell pm enable com.oculus.os.logcollector
adb shell pm enable com.oculus.socialpresence
adb shell pm enable com.oculus.messenger
adb shell pm enable com.oculus.people
adb shell pm enable com.oculus.contacts
adb shell pm enable com.oculus.horizon
adb shell pm enable com.oculus.venues
adb shell pm enable com.oculus.explore
adb shell pm enable com.oculus.vrshell.home
adb shell pm enable com.oculus.nux.ota
adb shell pm enable com.meta.ai
adb shell pm enable com.oculus.voice.assistant
# COLD REBOOT REQUIRED

################################################## 

Option B: Headset-Native (QGO Terminal)

# Revert via QGO
pm enable com.oculus.unifiedtelemetry
pm enable com.oculus.gatekeeperservice
pm enable com.oculus.notification_proxy
pm enable com.oculus.bugreporter
pm enable com.oculus.os.logcollector
pm enable com.oculus.socialpresence
pm enable com.oculus.messenger
pm enable com.oculus.people
pm enable com.oculus.contacts
pm enable com.oculus.horizon
pm enable com.oculus.venues
pm enable com.oculus.explore
pm enable com.oculus.vrshell.home
pm enable com.oculus.nux.ota
pm enable com.meta.ai
pm enable com.oculus.voice.assistant
# COLD REBOOT REQUIRED
](https://www.meta.com/en-gb/help/quest/172903867975450/?srsltid=AfmBOoqZhwpgBZGwAb84AYmY2F9Ft0jRDB6sixQpsV-hhvP3OvGSNypn)
