# WaveID-Zero-Touch-Transit-Access-Control-
Zero Touch Hands-Free Transit Access Control via Cryptographic BLE &amp; Physical RF Fingerprinting.



# Project AegisGate
> Zero-Touch Hands-Free Transit Access Control via Cryptographic BLE & Physical RF Fingerprinting

## 1. Overview
AegisGate is a next-generation "Be In / Be Out" (BIBO) access control system designed to eliminate manual QR scanning and ticket bottlenecking at transit gates. By combining rotating cryptographic tokens broadcasted over Bluetooth Low Energy (BLE) with physical-layer radio frequency (RF) signal analysis, AegisGate provides frictionless, stride-speed verification with zero-trust security.

## 2. Key Features
* **Zero-Touch Access:** Users walk through the gate without taking their smartphone out of their pocket.
* **Cryptographic Anti-Replay:** Background mobile app broadcasts rotating Time-Based One-Time Passwords (TOTP) embedded inside BLE advertising packets.
* **Dual-Layer Physical Verification:** Analyzes raw analog radio wave properties (Carrier Frequency Offset and phase characteristics) to prevent hardware cloning and signal relay attacks.
* **Graceful Degradation:** Automatic anomaly fallback to manual verification (QR/NFC) if a signal spoof or multi-person tailgate is detected.

## 3. System Architecture
```
[ Smartphone Emitter ] 
       │ (BLE Broadcast w/ TOTP Payload)
       ▼
[ SDR Receiver Array ] ───▶ [ DSP Edge Pipeline (Python) ]
                                    │ (Extracts Features + Decodes Token)
                                    ▼
                          [ Authority Backend (Node.js) ]
                                    │ (Validates Account & Auth)
                                    ▼
                          [ Gate Hardware Controller ]
```

## 4. Tech Stack
* **Emitter:** Android / Cross-Platform Mobile Service (BLE Advertising)
* **Signal Capture & DSP:** Python 3, GNU Radio / SciPy, NumPy (RTL-SDR v4 / LimeSDR)
* **Backend Engine:** Node.js, Express, REST APIs
* **Hardware Integration:** Embedded Edge Node (Raspberry Pi / x86) + Actuator/Servo Control

## 5. Repository Structure
```
├── backend/          # Node.js transit authority server & TOTP validator
├── dsp/              # Python scripts for SDR signal capture & feature extraction
├── mobile/           # BLE advertising mobile client app
├── docs/             # Circuit schematics, 3D CAD models, & system architecture
└── README.md
```

## 5. Getting Started
### Prerequisites
* Node.js v18+
* Python 3.10+
* SDR Hardware (RTL-SDR v4 or equivalent)
 
## 6. License & Project Status
Developed as an engineering research prototype for high-density transit access.
Status: Active Prototype / In Development.
