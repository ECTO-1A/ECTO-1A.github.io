---
featured: true
layout: post
title: "Detecting Stingrays and IMSI Catchers with Rayhunter by EFF"
date: 2025-06-25
categories: [Cybersecurity, Privacy, Tools]
tags: [Rayhunter, EFF, stingray, IMSI catcher, cellular spying]
author: chris
image: /assets/images/rayhunter.webp
---

If you’ve ever worried that your phone might be talking to a secret police-grade snoop disguised as a cell tower, you’re not alone. Law-enforcement “Stingray” devices, also called IMSI catchers or cell-site simulators (CSS), can impersonate legitimate towers to pinpoint your location, harvest unique device IDs, and—if they choose—even intercept communications :contentReference[oaicite:0]{index=0}. But until now, detecting these shady rigs meant either gutting an Android phone or spending big on software-defined radios. Enter **Rayhunter**: a $20, open-source tool from the Electronic Frontier Foundation (EFF) that runs on an off-the-shelf mobile hotspot and lets anyone spot potential Stingray activity in real time :contentReference[oaicite:1]{index=1}.

---

## Why Rayhunter Matters

- **Affordability:**  Rayhunter runs on an Orbic RC400L (or similar) mobile hotspot you can snag for about \$20—no expensive SDR gear required :contentReference[oaicite:2]{index=2}.  
- **Simplicity:**  With a simple traffic-light display (green = all clear, red = suspicious), you don’t need to be a radio geek to stay informed :contentReference[oaicite:3]{index=3}.  
- **Transparency:**  The software is fully open-source on GitHub, so researchers can audit, enhance, and map Stingray deployments worldwide :contentReference[oaicite:4]{index=4}.

Rayhunter shifts the power dynamic: instead of blindly trusting networks, you can push back against opaque surveillance and contribute data on where and when Stingrays are used.

---

## How Rayhunter Works

At its core, Rayhunter intercepts and analyzes **control traffic**—the signaling data exchanged between your hotspot and the cell tower—***without*** touching your personal communications (no web browsing, messaging, or calls are monitored) :contentReference[oaicite:5]{index=5}. It looks for telltale signs of CSS behavior, such as:

- **Forced 2G Downgrades:** Older 2G connections lack modern encryption, making them vulnerable to man-in-the-middle attacks. A tower that tries to push your device down to 2G is suspicious :contentReference[oaicite:6]{index=6}.  
- **Unusual IMSI Requests:** IMSI catchers often request your SIM’s unique identifier under non-standard conditions. Rayhunter flags these anomalies :contentReference[oaicite:7]{index=7}.  

When such events occur, the hotspot’s screen (or a connected laptop UI) switches from green/blue to red, and Rayhunter logs a PCAP file you can download for further analysis or legal evidence.

---

## Getting Started with Rayhunter

1. **Grab the Hardware**  
   - Purchase an Orbic RC400L (or any compatible Linux/Qualcomm 4G hotspot) from Amazon or eBay for around \$20 :contentReference[oaicite:8]{index=8}.  
2. **Flash the Device**  
   - Follow EFF’s step-by-step guide on GitHub to flash Rayhunter onto the hotspot. The repo includes scripts for macOS and Linux to automate installation :contentReference[oaicite:9]{index=9}.  
3. **Power & Connect**  
   - Charge the hotspot, turn it on, and connect your laptop or phone to its Wi-Fi network.  
4. **Launch Rayhunter**  
   - Open the Rayhunter UI (via SSH or web interface) to start monitoring. A clear green light means “all good,” while red warns of potential Stingray activity.  
5. **Review & Share**  
   - Download the PCAP logs for deep dives, and consider uploading sanitized geolocation metadata to community mapping projects to track Stingray deployments.

---

## Best Practices & Tips

- **Keep It Mobile:**  Sling Rayhunter in your backpack or glovebox. It’s small enough to fit in a pocket and can run for hours on battery power.  
- **Legal Check:**  While EFF believes Rayhunter is legal in the U.S., regulations vary—double-check local laws before deployment :contentReference[oaicite:10]{index=10}.  
- **Community Mapping:**  Join projects like the **Stingray Tracker** on GitHub to share anonymized sightings and build a global heatmap.  
- **Stay Updated:**  EFF frequently patches the software to adapt to new CSS tricks—`git pull` often.  

---

## The Road Ahead

Rayhunter represents a critical step toward demystifying street-level surveillance, but it’s not a silver bullet. Future work includes:

- **Broader Device Support:**  Testing on additional hotspot models and custom Qualcomm boards to expand hardware compatibility.  
- **Advanced Detection:**  Machine-learning models trained on aggregated control-traffic datasets to spot subtler CSS fingerprints.  
- **Integration with Mobile Apps:**  Bringing Rayhunter’s detection to a smartphone app for on-the-go alerts (without needing a separate hotspot).  

Each new contribution—whether a code tweak, hardware port, or shared dataset—helps strengthen the collective shield against invasive surveillance.

---

## Conclusion

From journalists covering protests to travelers in regions with lax oversight, Rayhunter puts a simple, cost-effective Stingray detector in everyone’s hands. By coupling the EFF’s expertise with open-source collaboration, we’re closer than ever to shining light on the clandestine world of IMSI catchers. Ready to join the hunt? Flash your hotspot, power up Rayhunter, and let’s map out cellular spying—one red alert at a time. 🕵️‍♂️🔦

---

*Resources & Links:*  
- EFF Rayhunter GitHub: https://github.com/eff/rayhunter  
- Boing Boing: “EFF creates a $20 device to detect cellular spying: Rayhunter” :contentReference[oaicite:11]{index=11}  
- BleepingComputer: “Open-source tool ‘Rayhunter’ helps users detect Stingray attacks” :contentReference[oaicite:12]{index=12}  
