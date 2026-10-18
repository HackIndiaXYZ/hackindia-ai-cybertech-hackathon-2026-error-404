# hackindia-ai-cybertech-hackathon-2026-error-404
Hackathon team repository for Error 404 - [hackindia-team:hackindia-ai-cybertech-hackathon-2026:error-404]

---

# KYC-Tick: AI-Powered Document Integrity & Fraud Prevention Platform

**Live Production Demo:** [https://k-yc-tick.vercel.app](https://k-yc-tick.vercel.app)  
**Main Development Repository:** [https://github.com/jeeva5655/kYC-Tick](https://github.com/jeeva5655/kYC-Tick)

A comprehensive, privacy-first identity document screening and anti-fraud platform designed for the HackIndia AI & CyberTech Hackathon 2026.

## 🚀 Key Features

- **Global Passport Screening**: Complete TD3 MRZ parser, check digit calculations, and visual tamper validation.
- **Indian Domestic ID Verification**: Native support for Aadhaar (QR code cryptographic RSA signature verification via UIDAI public certificates), PAN, Voter ID, and Driving Licence with Verhoeff checksums.
- **5-Gate AI Detection Cascade**: Multi-stage inspection filtering EXIF metadata, Moiré screen patterns, noise variance, frequency/edge analysis, and synthetic FFT signatures.
- **Facial Verification & Liveness**: 1:1 Face comparison between document portrait and live capture selfie.
- **Privacy & Compliance by Design**:
  - In-memory processing (zero persistence of raw biometric images).
  - PII data masking (only last 4 characters visible).
  - Cryptographic HMAC-SHA256 audit digest generation.

## 🛠️ Architecture Overview

The system features a hybrid architecture:
1. **Cloud Frontend & Gateway (Vercel Serverless)**: Hosts the progressive web application (PWA) with 4K canvas animations, handles client uploads, and runs deterministic triage rules.
2. **Local AI Vision Engine (FastAPI Microservice)**: Concurrently dispatches incoming documents across OCR (PaddleOCR), forgery detection (ManTraNet filters), and QR cryptographic checks.

For complete architectural details, see [architecture_diagram.md](architecture_diagram.md).

## 🏃 Run Locally

### 1. Web Application & Gateway (Node.js)
Requires Node.js 20+:
`powershell
node server.js
`
Open [http://127.0.0.1:3000](http://127.0.0.1:3000) in your browser.

Run automated test suites:
`powershell
node --test screening.test.js
`

### 2. Vision Service (Python FastAPI)
From the ision_service/ directory:
`powershell
cd vision_service
python -m venv .venv
.\.venv\Scripts\activate
pip install -r requirements.txt
uvicorn app:app --host 127.0.0.1 --port 8001
`

For mobile or cloud testing with the Vercel frontend, expose port 8001 via Ngrok:
`powershell
ngrok http 8001
`
Paste your Ngrok HTTPS tunnel URL directly into the **Backend API URL** field in the web app or mobile PWA.

---
