# Custom Configurable AES Encryption

A Python-based encryption tool that extends standard AES with a configurable nonce, available as both a web application and a command-line interface. The project was built as part of my final year at Chandigarh University and later published at IEEE GCWCN 2025.

**Live demo:** https://custom-configurable-aes.onrender.com

---

## What It Does

Standard AES implementations use a fixed nonce generation strategy. This project lets you inject custom data into the nonce — giving you more control over the encryption parameters without breaking the underlying AES standard.

You can encrypt any plaintext using AES in CTR mode, choose your key size, and define a custom nonce prefix. The tool then returns the ciphertext, the key, and the nonce — all of which you need to decrypt it back.

---

## Features

- AES encryption and decryption using CTR mode
- Configurable nonce with custom data injection
- Selectable key size (128-bit, 192-bit, or 256-bit)
- Simple web interface built with Flask
- REST API endpoints for encrypt and decrypt
- Deployed and accessible online via Render

---

## How It Works

1. User inputs plaintext and an optional custom nonce string via the web interface
2. A key is generated using `secrets.token_bytes()` at the specified key size
3. A custom nonce is constructed by combining random bytes with the user-supplied data
4. AES-CTR encryption is applied using Python's `cryptography` library
5. The ciphertext, key, and nonce are returned in hex format
6. Decryption reverses the process using the same key and nonce

---

## Project Structure

```
Custom_Configurable_AES_Updated/
│
├── static/           # CSS and JS for the web interface
├── templates/        # HTML templates (index.html)
├── app.py            # Flask app with encrypt/decrypt routes
├── requirements.txt  # Python dependencies
└── README.md
```

---

## Tech Stack

- **Python** — core logic
- **Flask** — web framework
- **cryptography** — AES-CTR encryption via `hazmat` primitives
- **secrets** — cryptographically secure key and nonce generation
- **HTML / CSS / JavaScript** — frontend interface
- **Render** — deployment platform

---

## Running Locally

```bash
# Install dependencies
pip install -r requirements.txt

# Run the app
python app.py
```

Then open `http://localhost:5000` in your browser.

---

## API Endpoints

**POST /encrypt**
- `plaintext` — text to encrypt
- `key_size` — key size in bytes (16, 24, or 32)
- `custom_nonce` — optional string to embed in the nonce

Returns: `ciphertext`, `key`, `nonce` (all in hex)

**POST /decrypt**
- `ciphertext` — hex-encoded ciphertext
- `key` — hex-encoded key
- `nonce` — hex-encoded nonce

Returns: `decrypted_text`

---

## Publication

This project was extended into a research paper and published at:

> **Extended AES with Custom Configurable Encryption** — IEEE GCWCN 2025

---

## Built With

Developed as a final year academic project at Chandigarh University (Jan–May 2024).
