---
featured: true
layout: post
title: Crashing iPhones with Flipper Zero and The Story Behind CVE-2023-42941
author: chris
date: 2024-01-20 14:30:00 -0500
categories: [Cybersecurity, Coding Projects]
tags: [portfolio, coding projects, mac, ios, ble]     # TAG names should always be lowercase
image: assets/images/66.png
---

# Crashing iPhones with Flipper Zero: Inside CVE-2023-42941

In late 2023, a critical vulnerability in Apple’s Bluetooth Low Energy (BLE) protocol made headlines—and for good reason. CVE-2023-42941, as it’s formally known, allowed a small open-source gadget called the Flipper Zero to crash iPhones by sending spoofed Bluetooth pairing requests. What began as a personal research project soon turned into an international cybersecurity incident.

## Flipper Zero: From Penetration Tester to iPhone Jammer

The Flipper Zero was originally designed for hobbyists and cybersecurity professionals. It’s a Swiss Army knife for wireless protocols—capable of reading RFID cards, emulating NFC tags, and spoofing Bluetooth signals. But when I ([ECTO-1A](https://github.com/ecto-1a)) began reverse engineering Apple’s BLE stack, I discovered that iOS was extremely vulnerable to BLE spam.

By mimicking Apple’s BLE advertisements—used in AirDrop, Handoff, and even Apple Watch pairing—the Flipper Zero could send continuous pop-up requests to iPhones. These requests couldn’t be dismissed easily and, in many cases, would cause system freezes and forced reboots. It effectively turned the Flipper into a denial-of-service (DoS) weapon against nearby Apple devices.

## Collaboration with willyJL

In developing the tool to demonstrate this vulnerability, I collaborated with [willyJL](https://github.com/willyjl) from the [Momentum Flipper Firmware](https://github.com/Momentum-Development/Momentum) project. Our goal was to responsibly demonstrate how BLE spoofing could disrupt iPhones in the wild and highlight the need for better protections in iOS.

WillyJL also shared his perspective on the project and the broader conversation around BLE spoofing in his post, ["The controversy behind Apple BLE Spam"](https://willyjl.dev/blog/the-controversy-behind-apple-ble-spam), which provides additional context on how the tool was developed, tested, and received by the public and press.

## Real-World Consequences

While the bug itself was fascinating from a research standpoint, the real-world fallout was swift and chaotic. Other cybersecurity researchers approached the media claiming credit for the discovery. Students across various schools began abusing the exploit, leading to suspensions and lockdowns. Reports began surfacing of commuters on public trains experiencing sudden iPhone reboots en masse.

One particularly memorable story involved Jeroen van der Ham, who documented his experience on a train in the Netherlands. His phone, along with many others nearby, was rendered unusable until forcibly rebooted.

News of the vulnerability spread quickly, gaining attention from tech outlets including [9to5Mac](https://9to5mac.com/2023/10/24/flipper-zero-bluetooth-crash-iphones/), [MacRumors](https://www.macrumors.com/2023/10/25/iphone-flipper-zero-popups/), [Malwarebytes](https://www.malwarebytes.com/blog/news/2023/10/flipper-zero-can-make-your-iphone-go-crazy), and [Gizmodo](https://www.gizmodo.com.au/2023/10/flipper-zero-hack-iphone-bluetooth/).

## Setting the Record Straight

Several outlets initially credited the exploit to a different alias "Techryptic" but but ultimately I was able to provide evidence that I, under the handle ECTO-1A, was solely responsible for the discovery. My research built upon extensive BLE packet analysis and culminated in the creation of "AppleJuice," a proof-of-concept BLE spoofer hosted on [GitHub](https://github.com/ecto-1a/AppleJuice).

## Apple’s Response in iOS 17.2

<img src="{{ '/assets/images/cve.png' | relative_url }}" alt="iOS 17.2" width="120" style="vertical-align: middle; margin-left: 8px;">

Apple addressed the exploit with the release of iOS 17.2 in December 2023. The patch introduced a timeout mechanism for BLE pairing requests, effectively neutralizing the DoS attack vector. According to tests by [ZDNet](https://www.zdnet.com/article/ios-17-2-update-patches-flipper-zero-bluetooth-exploit/), iPhones now resist the crash loop, though some users may still see fleeting pop-ups.

While this fix is effective, it also raises questions about how such a fundamental flaw in BLE handling went unnoticed for so long.

## Lessons Learned

The saga of CVE-2023-42941 underscores the double-edged sword of accessible cybersecurity tools. While devices like the Flipper Zero empower learning and experimentation, they can also expose systemic weaknesses when paired with deep technical curiosity. In this case, the exploit prompted urgent attention to how Apple handles unsolicited BLE interactions.

The good news? Apple patched it. The bad news? There’s always another vector waiting to be found.

## Explore More

- Full write-up by ECTO-1A: [AppleJuice CVE-2023-42941](https://ecto-1a.github.io/AppleJuice_CVE/)
- Source code & technical details: [GitHub – AppleJuice BLE PoC](https://github.com/ecto-1a/AppleJuice)
- Blog post by willyJL: [The controversy behind Apple BLE Spam](https://willyjl.dev/blog/the-controversy-behind-apple-ble-spam)
- Exploit demonstration and community discussions:
  - [YouTube: Flipper Zero iPhone Spam Demo](https://www.youtube.com/watch?v=bm7dV0H9o5I)
  - [LiveOverflow’s BLE Security Breakdown](https://www.youtube.com/watch?v=GSuV-KM7yRk)
- Related coverage:
  - [9to5Mac](https://9to5mac.com/2023/10/24/flipper-zero-bluetooth-crash-iphones/)
  - [Malwarebytes](https://www.malwarebytes.com/blog/news/2023/10/flipper-zero-can-make-your-iphone-go-crazy)
  - [ZDNet on Apple’s Fix](https://www.zdnet.com/article/ios-17-2-update-patches-flipper-zero-bluetooth-exploit/)
  - [Gizmodo](https://www.gizmodo.com.au/2023/10/flipper-zero-hack-iphone-bluetooth/)

