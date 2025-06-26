---
layout: post
title: "GPU Powered Cracking with Hashcat on Apple Silicon M-Series Macs"
date: 2025-06-25
categories: [Cybersecurity, macos, hashcat]
tags: [hashcat, apple-silicon, gpu, cracking, password, security]
---

If you’ve got one of Apple’s M-series Macs (M1, M1 Pro/Max, M2, M2 Pro/Max, M3, etc.) and you want to unleash its GPU on password cracking, Hashcat’s Metal backend is your friend. Gone are the days of CPU-only runs or Rosetta hacks. Hashcat v6.2.5+ speaks Metal natively, tapping into all those GPU cores.

> **Heads up:** Metal support in Hashcat is labeled “experimental,” but in my tests (and others’), it’s stable enough for real-world use. Benchmarks below.  

---

## TL;DR

1. Install Hashcat via Homebrew.  
2. Ensure you’re on Hashcat v6.2.5 or later (Metal added in v6.2.5).  
3. Run your first GPU benchmark:  
   ```bash
   hashcat -b
```

If installed correctly, it should auto-detect the GPU and use it without needing any flags.




---

## 1. Install or Upgrade Hashcat

Homebrew will get you the latest stable release:

```bash
brew update
brew install hashcat
# or, if already installed:
brew upgrade hashcat
```

Verify you’re at v6.2.5+:

```bash
$ hashcat --version
6.2.5
```

---

## 2. Identify Your GPU Device

Hashcat under Metal lists your GPU as device #1 (OpenCL GPU is skipped). Let’s see it in action:

```bash
hashcat -I
```

You should see something like:

```
 % hashcat -I
hashcat (v6.2.6) starting in backend information mode

Metal Info:
===========

Metal.Version.: 343.14

Backend Device ID #1 (Alias: #2)
  Type...........: GPU
  Vendor.ID......: 2
  Vendor.........: Apple
  Name...........: Apple M1 Max
  Processor(s)...: 32
  Clock..........: N/A
  Memory.Total...: 21845 MB (limited to 8192 MB allocatable in one block)
  Memory.Free....: 10880 MB
  Local.Memory...: 32 KB
  Phys.Location..: built-in
  Feature.Set....: macOS GPU Family 2 v1
  Registry.ID....: 2767
  Max.TX.Rate....: N/A
  GPU.Properties.: headless 0, low-power 0, removable 0

OpenCL Info:
============

OpenCL Platform ID #1
  Vendor..: Apple
  Name....: Apple
  Version.: OpenCL 1.2 (Feb 10 2024 00:43:19)

  Backend Device ID #2 (Alias: #1)
    Type...........: GPU
    Vendor.ID......: 2
    Vendor.........: Apple
    Name...........: Apple M1 Max
    Version........: OpenCL 1.2 
    Processor(s)...: 32
    Clock..........: 1000
    Memory.Total...: 21845 MB (limited to 2048 MB allocatable in one block)
    Memory.Free....: 10880 MB
    Local.Memory...: 32 KB
    OpenCL.Version.: OpenCL C 1.2 
    Driver.Version.: 1.2 1.0

```


---

## 3. Benchmark Your GPU

Run the full Metal GPU benchmark:

```bash
hashcat -b
```

Example results on an **M1 Max (32 MCU)**:

```
hashcat -b
hashcat (v6.2.6) starting in benchmark mode

Benchmarking uses hand-optimized kernel code by default.
You can use it in your cracking session by setting the -O option.
Note: Using optimized kernel code limits the maximum supported password length.
To disable the optimized kernel code in benchmark mode, use the -w option.

* Device #2: Apple's OpenCL drivers (GPU) are known to be unreliable.
             You have been warned.

METAL API (Metal 343.14)
========================
* Device #1: Apple M1 Max, 10880/21845 MB, 32MCU

OpenCL API (OpenCL 1.2 (Feb 10 2024 00:43:19)) - Platform #1 [Apple]
====================================================================
* Device #2: Apple M1 Max, skipped

Benchmark relevant options:
===========================
* --optimized-kernel-enable

-------------------
* Hash-Mode 0 (MD5)
-------------------

Speed.#1.........: 13215.7 MH/s (80.36ms) @ Accel:1024 Loops:1024 Thr:32 Vec:1

----------------------
* Hash-Mode 100 (SHA1)
----------------------

Speed.#1.........:  5405.3 MH/s (48.80ms) @ Accel:256 Loops:1024 Thr:32 Vec:1

---------------------------
* Hash-Mode 1400 (SHA2-256)
---------------------------

Speed.#1.........:  1954.6 MH/s (67.67ms) @ Accel:512 Loops:256 Thr:32 Vec:1

---------------------------
* Hash-Mode 1700 (SHA2-512)
---------------------------

Speed.#1.........:   395.7 MH/s (83.93ms) @ Accel:256 Loops:64 Thr:64 Vec:1

-------------------------------------------------------------
* Hash-Mode 22000 (WPA-PBKDF2-PMKID+EAPOL) [Iterations: 4095]
-------------------------------------------------------------

Speed.#1.........:   247.8 kH/s (65.57ms) @ Accel:512 Loops:128 Thr:32 Vec:1

-----------------------
* Hash-Mode 1000 (NTLM)
-----------------------

Speed.#1.........: 21123.8 MH/s (49.95ms) @ Accel:2048 Loops:512 Thr:32 Vec:1

---------------------
* Hash-Mode 3000 (LM)
---------------------

Speed.#1.........:   668.6 MH/s (52.74ms) @ Accel:16 Loops:1024 Thr:128 Vec:1

--------------------------------------------
* Hash-Mode 5500 (NetNTLMv1 / NetNTLMv1+ESS)
--------------------------------------------

Speed.#1.........: 13590.9 MH/s (78.14ms) @ Accel:512 Loops:1024 Thr:64 Vec:1

----------------------------
* Hash-Mode 5600 (NetNTLMv2)
----------------------------

Speed.#1.........:   915.6 MH/s (72.43ms) @ Accel:64 Loops:256 Thr:128 Vec:1

--------------------------------------------------------
* Hash-Mode 1500 (descrypt, DES (Unix), Traditional DES)
--------------------------------------------------------

Speed.#1.........: 18597.5 kH/s (183.61ms) @ Accel:4 Loops:1024 Thr:32 Vec:1

------------------------------------------------------------------------------
* Hash-Mode 500 (md5crypt, MD5 (Unix), Cisco-IOS $1$ (MD5)) [Iterations: 1000]
------------------------------------------------------------------------------

Speed.#1.........:  5298.5 kH/s (94.24ms) @ Accel:512 Loops:500 Thr:64 Vec:1

----------------------------------------------------------------
* Hash-Mode 3200 (bcrypt $2*$, Blowfish (Unix)) [Iterations: 32]
----------------------------------------------------------------

Speed.#1.........:     9342 H/s (51.95ms) @ Accel:2 Loops:32 Thr:8 Vec:1

--------------------------------------------------------------------
* Hash-Mode 1800 (sha512crypt $6$, SHA512 (Unix)) [Iterations: 5000]
--------------------------------------------------------------------

* Device #1: Skipping (hash-mode 1800)
             This is due to a known Metal runtime and/or device driver issue (not a hashcat issue)
             You can use --force to override, but do not report related errors.

--------------------------------------------------------
* Hash-Mode 7500 (Kerberos 5, etype 23, AS-REQ Pre-Auth)
--------------------------------------------------------

Speed.#1.........:   180.1 MH/s (92.27ms) @ Accel:256 Loops:64 Thr:32 Vec:1

-------------------------------------------------
* Hash-Mode 13100 (Kerberos 5, etype 23, TGS-REP)
-------------------------------------------------

Speed.#1.........:   180.8 MH/s (91.95ms) @ Accel:256 Loops:64 Thr:32 Vec:1

---------------------------------------------------------------------------------
* Hash-Mode 15300 (DPAPI masterkey file v1 (context 1 and 2)) [Iterations: 23999]
---------------------------------------------------------------------------------

Speed.#1.........:    43357 H/s (64.01ms) @ Accel:512 Loops:128 Thr:32 Vec:1

---------------------------------------------------------------------------------
* Hash-Mode 15900 (DPAPI masterkey file v2 (context 1 and 2)) [Iterations: 12899]
---------------------------------------------------------------------------------

Speed.#1.........:     6748 H/s (47.74ms) @ Accel:128 Loops:16 Thr:64 Vec:1

------------------------------------------------------------------
* Hash-Mode 7100 (macOS v10.8+ (PBKDF2-SHA512)) [Iterations: 1023]
------------------------------------------------------------------

Speed.#1.........:    89131 H/s (88.48ms) @ Accel:128 Loops:31 Thr:64 Vec:1

---------------------------------------------
* Hash-Mode 11600 (7-Zip) [Iterations: 16384]
---------------------------------------------

Speed.#1.........:   251.7 kH/s (62.38ms) @ Accel:32 Loops:4096 Thr:64 Vec:1

------------------------------------------------
* Hash-Mode 12500 (RAR3-hp) [Iterations: 262144]
------------------------------------------------

Speed.#1.........:    32033 H/s (63.45ms) @ Accel:8 Loops:16384 Thr:128 Vec:1

--------------------------------------------
* Hash-Mode 13000 (RAR5) [Iterations: 32799]
--------------------------------------------

Speed.#1.........:    24212 H/s (84.02ms) @ Accel:512 Loops:128 Thr:32 Vec:1

--------------------------------------------------------------------------------
* Hash-Mode 6211 (TrueCrypt RIPEMD160 + XTS 512 bit (legacy)) [Iterations: 1999]
--------------------------------------------------------------------------------

Speed.#1.........:   168.6 kH/s (47.83ms) @ Accel:64 Loops:128 Thr:64 Vec:1

-----------------------------------------------------------------------------------
* Hash-Mode 13400 (KeePass 1 (AES/Twofish) and KeePass 2 (AES)) [Iterations: 24569]
-----------------------------------------------------------------------------------

Speed.#1.........:    73676 H/s (73.66ms) @ Accel:128 Loops:512 Thr:64 Vec:1

----------------------------------------------------------------
* Hash-Mode 6800 (LastPass + LastPass sniffed) [Iterations: 499]
----------------------------------------------------------------

Speed.#1.........:  1532.7 kH/s (65.67ms) @ Accel:256 Loops:124 Thr:64 Vec:1

--------------------------------------------------------------------
* Hash-Mode 11300 (Bitcoin/Litecoin wallet.dat) [Iterations: 200459]
--------------------------------------------------------------------

Speed.#1.........:     1789 H/s (92.88ms) @ Accel:1024 Loops:32 Thr:32 Vec:1

Started: Wed Jun 25 18:22:25 2025
Stopped: Wed Jun 25 18:28:53 2025
```

---

## 4. Running a Real Attack

Let’s crack an MD5 hash using your GPU:

1. **Prepare** `hashes.txt`:

   ```
   5f4dcc3b5aa765d61d8327deb882cf99
   ```
2. **Run**:

   ```bash
   hashcat -m 0 -a 0  hashes.txt /path/to/wordlist.txt
   ```

   * `-m 0` → MD5
   * `-a 0` → straight (dictionary)

You’ll see your GPU’s blazing speed tearing through that wordlist.

---

## 5. Pro Tips & Tricks

* **Optimized Kernels**: Use `-O` to cap password length but boost speed.
* **Session Persistence**: `--session NAME` + `--restore` to pause/resume.
* **Masks & Rules**: Combine mask (`-a 3`) + rule (`-r`) attacks for surgical strikes.
* **Device List**: `-I` to list devices, `-d` to pick them.
* **Monitor Temps**:

  ```bash
  sudo powermetrics --samplers smc
  ```
* **Benchmark Logs**:

  ```bash
  hashcat -b -d 2 | tee gpu-bench-$(date +%F).txt
  ```

---

Keep an eye on the [Hashcat GitHub issues](https://github.com/hashcat/hashcat/issues?q=Metal) for improvements and Metal-specific tips.

---

## Wrapping Up

Apple Silicon’s GPUs aren’t just for graphics or running local AI models. With Hashcat and Metal, they’re cracking beasts in disguise. Whether you’ve got an M1 Pro or an M3 Max, the Metal backend lets you run high-speed attacks right from your MacBook, Mac Studio, or Mac Pro.


*Happy cracking!* 🐾

```
::contentReference[oaicite:2]{index=2}
```

[1]: https://gist.github.com/Chick3nman/ccfb883d2d267d94770869b09f5b96ed?utm_source=chatgpt.com "Hashcat v6.2.5-340 benchmark on the Apple M1 Ultra - GitHub Gist"
