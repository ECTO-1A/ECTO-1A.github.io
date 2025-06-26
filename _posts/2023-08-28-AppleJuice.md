---
featured: false
layout: post
title: Experimenting with Apple Device Proximity Pairing Using Bluetooth Low Energy
author: chris
date: 2023-08-28 14:30:00 -0500
categories: [Cybersecurity, Coding Projects]
tags: [portfolio, coding projects, ai, mac, ios]     # TAG names should always be lowercase
image: assets/images/66.png
---

# Apple Device Proximity Pairing Reverse Engineering

I recently created a new GitHub repository called [**AppleJuice**](https://github.com/ECTO-1A/AppleJuice) to explore proximity pairing between Apple devices using Bluetooth Low Energy (BLE). This came about after seeing some interesting BLE messaging spoofing at DEF CON 31, where researchers were able to make iPhones display fake AppleTV pairing prompts.

I wanted to dig deeper into how this works, so I built upon prior research projects and reverse engineering done by others in this space. So far, I’ve managed to reverse engineer over 15 Apple BLE alerts and build individual scripts to trigger each one. The scripts in this repo will continually send spoofed pairing messages to trigger the popups on nearby iPhones and iPads.

The goal of this project is purely educational - to learn more about Apple's Continuity protocols and how BLE pairing works under the hood. All testing has been done in a controlled, ethical manner and these scripts should not be used for any illegal or malicious purposes.

So far, I've gotten it working reliably with various Apple device models like AirPods Pro and AirPods Max, AppleTV, New Device Setup and even a couple I didn’t know existed (TV Color Calibration?). The range is pretty limited at 20-50 feet indoors using a long-range BLE adapter and a bit further outdoors. There's still a lot more I want to dig into and improve on here, like increasing range and porting some of the controls to the FlipperZero.


If you're interested in Bluetooth security, Apple protocols, or just tinkering with fun side projects like this, feel free to check out the code on GitHub. I've documented the process step-by-step so others can easily replicate this on a Linux machine or RaspberryPi with a BLE adapter. Also shoutout to the researchers who pioneered work in this area that I was able to build upon.

Let me know if you have any other ideas for what next steps I could take with this project!

[**AppleJuice GitHub Repository**](https://github.com/ECTO-1A/AppleJuice)