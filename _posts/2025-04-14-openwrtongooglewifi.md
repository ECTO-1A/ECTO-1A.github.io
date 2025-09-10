---
featured: false
layout: post
title: "Installing OpenWRT on Google Wifi (OnHub)"
date: 2025-04-14
categories: [Coding Projects, Cybersecurity]
tags: [openwrt, googlewifi, tutorial]
author: chris
image: assets/images/googlewifi.png 
---

If you're looking to flash **OpenWRT** onto your **Google Wifi (OnHub)** device, follow these instructions adapted from the [official OpenWRT guide](https://openwrt.org/toh/google/wifi). This walkthrough involves flashing a recovery image first, then installing the OpenWRT firmware.

---

## Requirements

You'll need:

- Powered USB Hub
- Two USB sticks (optional but helpful for handling multiple images)
- Chrome Browser
- [OnHub Recovery Utility Chrome Extension](https://chrome.google.com/webstore/detail/onhub-recovery-utility)

---

## Step 1: Create the Recovery USB

1. Install the OnHub Recovery Utility extension in Chrome.
2. Use the extension to create a recovery USB stick.  
   > ⚠️ No need to download a recovery image manually — it’s embedded in the tool.

---

## Step 2: Flash the Recovery Image

1. Power the USB hub.
2. Press and hold the **Reset** button on the front of the Google Wifi.
3. Connect the powered USB Hub (without the USB stick yet) to the device.
4. Wait for the LED to change:
   - White → Flashing Blue → Keep holding Reset
   - After ~16 seconds, it should **blink orange** → Release Reset
5. Insert the USB stick **with the recovery image** now.
6. LED turns off (this means recovery has started).
7. After ~5-6 minutes, device reboots → Solid Blue → Pulsing Blue.
8. Recovery complete.

Now you're ready to flash OpenWRT!

---

## Step 3: Flash OpenWRT Image

1. Connect a network cable from your PC to the **LAN port** of the Google Wifi.
2. Plug the **OpenWRT USB drive** into the **USB-C hub with power delivery (PD)**.
3. Connect a USB-C power source to the hub.
4. Press and hold the **Reset** button.
5. Connect the USB-C hub into the Google Wifi device.
6. Wait for the LED to transition:
   - White → Blinking Blue → After 16 sec → Blinking Orange → Release Reset
7. After 3 seconds: LED pulses orange and amber → Press **SW7** button.
8. Device blinks purple → Reboots.
9. After boot:
   - Device blinks blue → Blinks purple again → Press **SW7** again.
10. LED turns off → Device boots from OpenWRT USB.
11. LED blinks blue rapidly → Then solid blue.
12. From a terminal on your PC, run:

   ```bash
   ping 192.168.1.1
   ```

   If successful, you're connected!  
   > ⚠️ If your PC gets a self-assigned IP, the OpenWRT boot failed.

---

## Step 4: Final Flash to Internal Storage

1. Open a terminal on your PC.
2. `cd` into the directory where you downloaded the OpenWRT image:

   ```
   openwrt-24.10.0-ipq40xx-chromium-google_wifi-squashfs-factory.bin
   ```

3. Copy the image to the device:

   ```bash
   scp -O openwrt-24.10.0-ipq40xx-chromium-google_wifi-squashfs-factory.bin root@192.168.1.1:/tmp
   ```

4. SSH into the device and write the image to internal storage:

   ```bash
   ssh root@192.168.1.1 -C "dd if=/dev/zero bs=512 seek=7634911 of=/dev/mmcblk0 count=33 && \
   dd if=/tmp/openwrt-24.10.0-ipq40xx-chromium-google_wifi-squashfs-factory.bin of=/dev/mmcblk0"
   ```

---

You’re done! Your Google Wifi should now be running OpenWRT!
