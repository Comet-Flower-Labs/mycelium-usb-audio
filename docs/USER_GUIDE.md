# Zoom G1X Four USB Audio Out Patch — Public Testing Guide

**Firmware Build:** Comet Flower USB Audio Tap (Stereo 44.1 kHz 16-bit PCM)  
**Target Hardware:** Zoom G1 Four / Zoom G1X Four (Hardware Rev 1.00 - 2.00)  
**Updater Executable:** `build/public_release/ZOOM G1X FOUR USB Audio Patch (Comet Flower TEST).exe`  
**Updater SHA-256:** `FF52DE98392E4C3A0F8CD47C35F5ED304155727D9BFA49B95700E207C65FF88B`  
**Safety Classification:** NON-DESTRUCTIVE FIRMWARE-ONLY (Flash `0x33000` only)

---

## 1. What This Patch Does

Stock Zoom G1 Four / G1X Four pedals do not support USB audio streaming out of the box (Zoom restricted USB to MIDI and patch editing via Guitar Lab). 

This patch adds **real-time 44.1 kHz 16-bit stereo USB audio streaming** directly from the pedal's DSP output over the standard USB connection, turning your G1 Four / G1X Four into a zero-latency USB audio recording interface for your PC or laptop.

### Non-Destructive Guarantee:
- **Presets Preserved (100%):** Does **NOT** erase or touch factory presets or user patches (`0x28000` and `0xC0000`). All your patches remain exactly as you left them.
- **Effects Library Preserved (100%):** Does **NOT** touch the effect filesystem (`0x102000`). All stock Zoom effects and any installed custom effects are completely untouched.
- **Settings & Calibration Preserved (100%):** Does **NOT** erase or touch the pedal calibration sector (`0xBF000`). Your expression pedal and footswitch calibrations remain intact.
- **Update Mode Safe:** Does **NOT** touch the bootloader (`0x00000..0x28000`). Update mode is permanently preserved.
- **100% Reversible:** You can return to completely stock Zoom v2.00 firmware at any time by running Zoom's official updater in Update Mode.

### Branding & Identity:
- **Comet Flower Logo:** Replaces the standard Zoom startup graphic during boot.
- **Stock G1X Four Splash & Presets:** Keeps the stock "G1X FOUR" model splash screen and patch bank.
- **Standard USB MIDI Compatibility:** Retains standard MIDI naming so Guitar Lab and ToneLib Zoom continue to function normally.

---

## 2. Flashing Instructions

### Requirements:
1. Zoom G1 Four or G1X Four pedal.
2. Micro-USB data cable (ensure it is a full data cable, not a power-only charging cable).
3. Windows 10 or Windows 11 PC.

### Step-by-Step Procedure:

1. **Enter Firmware Update Mode:**
   - Disconnect the USB cable and power from the pedal.
   - Press and hold **both footswitches** (FS1 and FS2) simultaneously.
   - While holding both footswitches, plug in the USB cable connected to your PC.
   - Release the footswitches when the screen displays:
     ```
     FIRMWARE UPDATE
     Ready for update
     ```
2. **Execute the Patch Updater:**
   - Launch `ZOOM G1X FOUR USB Audio Patch (Comet Flower TEST).exe`.
   - The official Zoom updater GUI will appear.
   - Verify the detected version shows `v2.00` and click **Execute**.
   - Wait for the progress bar to complete (~1-2 minutes).
   - When the screen indicates `Complete!`, unplug the USB cable.

---

## 3. How to Enable & Use USB Audio

USB Audio is designed to be **off by default** on standard boot to ensure 100% stock electrical and USB compatibility, and turns on only when requested.

### Method A: Fast Boot Shortcut (Recommended)
1. Hold down the **Slot 1 button** (the button above the first virtual stompbox on the screen).
2. While holding the Slot 1 button, power on the pedal (or connect USB).
3. The pedal boots directly into **USB Audio Mode**.

### Method B: On-Pedal Settings Menu
1. Power on the pedal normally.
2. Press the **SETTINGS** button.
3. Turn **Knob 1** clockwise past `PRESET` and `CALIBRATE` until you reach the **COMET FLOWER** menu page.
4. Turn **Knob 2** to switch `USB: OFF` -> `USB: AUDIO`.
5. If the USB cable is already connected, the pedal performs an automatic software replug, and the USB audio interface enumerates immediately on your PC.

---

## 4. Recording Setup on PC

### Windows Sound Configuration:
1. Open Windows **Sound Settings** -> **Recording** (or `mmsys.cpl`).
2. You will see a new recording input device:
   ```
   Line (ZOOM G Series powered by Comet Flower)
   ```
3. Set the default format to **2 channel, 16 bit, 44100 Hz (CD Quality)**.

### In Your DAW or Recording Software (Audacity, OBS, Reaper, etc.):
- **Audio Input Device:** Select `Line (ZOOM G Series powered by Comet Flower)` (WASAPI, DirectSound, or MME).
- **MIDI Port Device:** Shows as `ZOOM G Series (Comet Flower)`.
- **Channels:** 2 Channels (Stereo).
- **Sample Rate:** `44,100 Hz`.
- **Monitoring:** Monitor through the pedal's headphone / output jack for direct zero-latency analog hardware monitoring.

---

## 5. How to Revert to Stock Zoom Firmware

If you ever wish to remove the patch and restore the pedal to 100% factory Zoom firmware:
1. Put the pedal into **FIRMWARE UPDATE** mode (hold both footswitches while connecting USB).
2. Run Zoom's official `ZOOM G1X FOUR System v2.00 Updater.exe` downloaded from zoomcorp.com.
3. Click Execute. The pedal will be restored to unmodified factory firmware.

---

## 6. Safety & Flash Verification Summary

| Flash Address Range | Sector / Region | Action in Patch | Safety Verification |
|---|---|---|---|
| `0x000000 - 0x028000` | Bootloader & Update Mode | **SKIPPED (Untouched)** | Verified by `check_updater_stages.py` |
| `0x028000 - 0x033000` | Factory Presets & Splash | **SKIPPED (Untouched)** | User presets preserved |
| `0x033000 - 0x0BF000` | Main Firmware Program | **Erased & Written** | Contains USB Audio & Menu |
| `0x0BF000 - 0x0C0000` | Settings & Calibration | **SKIPPED (Untouched)** | Hardware calibration preserved |
| `0x0C0000 - 0x102000` | Live User Patches | **SKIPPED (Untouched)** | Patches 1-50 preserved |
| `0x102000 - 0x400000` | Effect File System (.ZD2) | **SKIPPED (Untouched)** | All installed effects preserved |
