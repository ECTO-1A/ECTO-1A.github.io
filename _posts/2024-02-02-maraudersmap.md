---
layout: post
title: "Encrypting AI Prompts in Images with Python & Steganography"
date: 2024-01-27
author: chris
categories: [AI, Coding Projects, Cybersecurity]
tags: [python, encryption, steganography, ai, chatbot]
image: assets/images/81.png 
---
MaraudersMapAI combines the power of Fernet encryption and steganography to hide information within images, ensuring that the system prompt for an AI chatbot remains secure and undisclosed to prying eyes.

---

# MaraudersMapAI

MaraudersMapAI encrypts a chatbot system prompt with Fernet and embeds it in an image via steganography. At runtime, the prompt is recovered and decrypted, enabling covert prompt delivery for red‑teaming and jailbreak research.

## What It Does

- Encrypts sensitive prompts with a symmetric key.
- Hides the ciphertext inside a PNG using steganography.
- Recovers and decrypts the prompt at runtime for the chatbot.
- Keeps prompts out of plain text in code, logs, and configs.

## How It Works

1. Author the prompt in `prompt.py` (`user_input`).
2. `mischief_managed.py` encrypts the prompt with `SECRET_KEY` and writes a PNG with embedded data.
3. `marauders_map.py` extracts and decrypts the prompt.
4. Your chatbot consumes the decrypted string at runtime.

## Components

- `mischief_managed.py`: Encrypt + embed prompt into an image.
- `marauders_map.py`: Extract + decrypt prompt from the image.
- `prompt.py`: Source for the system prompt text.

## Setup

- `.env`: Provide `SECRET_KEY` (Fernet key).
- `Prompt/`: Folder used to store `output.png`.
- Install dependencies:

```sh
pip install -r requirements.txt
```

## Usage

Encrypt and hide:

```python
from mischief_managed import encrypt_message
import prompt

encrypt_message(prompt.user_input)
```

Reveal and decrypt:

```python
from marauders_map import up_to_no_good

decrypted_prompt = up_to_no_good()
# Use decrypted_prompt in your chatbot
```

## Notes

- This is encryption + obfuscation for delivery; downstream systems may still surface content depending on your stack.
- Treat the embedded image as sensitive. Anyone with the key can recover the prompt.
- Use for controlled research and red teaming; follow applicable policies and laws.

Repository: https://github.com/ECTO-1A/MaraudersMapAI
