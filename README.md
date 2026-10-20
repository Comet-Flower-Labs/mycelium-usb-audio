# Comet Flower Audio Labs: Mycelium USB Audio Bridge
### Real-Time USB Audio Out for Zoom G1 Four / G1X Four

[![Release](https://img.shields.io/github/v/release/DanCorona/Comet-flower-mycelium-?include_prereleases&color=brightgreen)](https://github.com/DanCorona/Comet-flower-mycelium-/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Target: Zoom G1X Four](https://img.shields.io/badge/Target-Zoom%20G1%20%2F%20G1X%20Four-orange.svg)]()

Unlocks real-time **44.1 kHz 16-bit stereo PCM USB audio streaming** directly from the DSP of the Zoom G1 Four and G1X Four over the standard USB connection, turning your multi-effects pedal into a zero-latency audio recording interface for PC, Mac, and Linux.

---

## Features

* **Plug-and-Play USB Audio Interface:** Streams real-time 16-bit 44.1 kHz stereo audio directly from the pedal's digital output to your computer. Works natively with Windows (WASAPI / DirectSound / MME), macOS (CoreAudio), and Linux (ALSA / JACK).
* **Zero Host Monitoring Latency:** Monitor directly through the pedal’s headphone / output jack with analog zero latency while tracking in your DAW, OBS, or Audacity.
* **On-Pedal Hardware Toggle:** Adds a new **`COMET FLOWER`** settings page directly on the pedal's screen (`USB: OFF / AUDIO`) with live software USB replug.
* **Fast Boot Shortcut:** Power on while holding the **Slot 1 button** to boot straight into USB Audio mode without opening any menus.
* **100% Non-Destructive Guarantee:** Flashes **ONLY** the main firmware partition (`0x33000`).
  * Preserves 100% of your saved patches (Patches 1–50 remain untouched).
  * Preserves 100% of your installed effects library and stock effects.
  * Preserves 100% of your hardware pedal calibration.
  * 100% reversible anytime using Zoom's official factory updater.

---

## Quick Start & Flashing Instructions

### Requirements:
1. Zoom G1 Four or G1X Four multi-effects pedal.
2. Micro-USB data cable (ensure it is a full data cable, not power-only).
3. Windows 10 or Windows 11 PC.

### Step-by-Step:
1. **Download the latest release:**  
   Grab `ZOOM G1X FOUR USB Audio Patch (Comet Flower TEST).exe` from the [Releases](https://github.com/DanCorona/Comet-flower-mycelium-/releases) tab.
2. **Enter Firmware Update Mode:**
   * Disconnect USB and power from the pedal.
   * Press and hold **both footswitches** (FS1 and FS2) simultaneously.
   * While holding both footswitches, plug in the USB cable connected to your PC.
   * Release when the screen displays:
     ```text
     FIRMWARE UPDATE
     Ready for update
     ```
3. **Run the Updater:**
   * Launch `ZOOM G1X FOUR USB Audio Patch (Comet Flower TEST).exe`.
   * Click **Execute** and wait for the progress bar to complete (~1 minute).
   * When the pedal displays `Complete!`, disconnect the USB cable.

---

## How to Enable & Use USB Audio

By default, the pedal boots in standard pedal mode (USB Audio OFF) for complete stock electrical compatibility.

### Method A: Fast Boot Shortcut (Recommended)
1. Hold down the **Slot 1 button** (the button above the first effect slot on screen).
2. Connect power or USB while holding Slot 1.
3. The pedal boots directly into **USB Audio Mode**.

### Method B: On-Pedal Settings Menu
1. Power on normally.
2. Press the **SETTINGS** button.
3. Turn **Knob 1** clockwise past `PRESET` and `CALIBRATE` to the **COMET FLOWER** menu page.
4. Turn **Knob 2** to switch `USB: OFF` -> `USB: AUDIO`.
5. The pedal automatically re-enumerates the USB connection, and Windows immediately detects the audio interface without unplugging the cable.

---

## Recording on PC

### Windows Sound Settings:
1. Open Windows **Sound Settings** -> **Recording** (or run `mmsys.cpl`).
2. You will see the new recording input device:
   ```text
   Line (ZOOM G Series powered by Comet Flower)
   ```
3. Set default format to **2 channel, 16 bit, 44100 Hz (CD Quality)**.

### In Your DAW / Recording Software (Audacity, OBS, Reaper, etc.):
* **Audio Input:** Select `Line (ZOOM G Series powered by Comet Flower)` (WASAPI, DirectSound, or MME).
* **Channels:** 2 Channels (Stereo).
* **Sample Rate:** `44,100 Hz`.
* **Hardware Monitoring:** Plug headphones or studio monitors into the pedal's output jack for zero-latency direct monitoring.

---

## How to Revert to Factory Stock

If you ever want to revert your pedal to completely stock factory Zoom v2.00 firmware:
1. Put the pedal in **FIRMWARE UPDATE** mode (hold both footswitches while connecting USB).
2. Download and run Zoom's official `ZOOM G1X FOUR System v2.00 Updater.exe` from [zoomcorp.com](https://zoomcorp.com).
3. Click Execute. The pedal will be restored to unmodified factory Zoom firmware.

---

## Credits & Acknowledgments

This project stands on the shoulders of the multi-effects reverse-engineering community:
* **Simon Wood ([mungewell/zoom-zt2](https://github.com/mungewell/zoom-zt2))**: For reverse-engineering the Zoom ZT2 MIDI SysEx protocol and file container specifications.
* **Thomas Hammer ([thammer/stomphacks](https://github.com/thammer/stomphacks))**: For pioneering work proving the Zoom Multistomp architecture runs compiled C6000 DSP code.
* **`w1ne` ([w1ne/zoom-g1four](https://github.com/w1ne/zoom-g1four))**: For early hardware teardowns confirming the Texas Instruments TMS320C6745 DSP architecture.

---

## Disclaimer

This project is an independent community research project and is **unaffiliated with Zoom Corporation**. "ZOOM", "G1 Four", and "G1X Four" are registered trademarks of Zoom Corporation. This firmware patch is provided for educational and interoperability purposes under fair use.

---

## Website & Future Releases
Visit [cometflower.com](https://cometflower.com) for updates, custom DSP effects, and news.
