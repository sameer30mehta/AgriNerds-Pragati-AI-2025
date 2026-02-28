# 🌾 AgriNerds — Pragati AI 2025

**AgriNerds** is a comprehensive agricultural platform that combines a multilingual Flutter mobile app with a blockchain-powered marketplace. It empowers farmers and companies with AI-driven crop advisories, real-time weather data, agricultural news, and transparent peer-to-peer contract management on the Ethereum blockchain.

---

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Flutter App Setup](#flutter-app-setup)
  - [Blockchain Marketplace Setup](#blockchain-marketplace-setup)
- [Supported Languages](#supported-languages)
- [Smart Contract Overview](#smart-contract-overview)
- [Team](#team)
- [License](#license)

---

## Features

| Feature | Description |
|---|---|
| 🌦️ **Weather Dashboard** | Real-time weather data via the Open-Meteo API with location-based forecasts |
| 🤖 **AI Assistant (Scheme AI)** | LLM-powered farming assistant with voice input/output (text-to-speech & speech-to-text) |
| 📰 **Agricultural News** | Curated news feed relevant to the farming community |
| 🌱 **Crop Management** | Track crops, get AI-based advisories, and chat per crop |
| 📝 **Contract Marketplace** | Create, browse, and apply for agricultural supply contracts (local SQLite storage + blockchain) |
| ⛓️ **Blockchain Contracts** | Transparent, tamper-proof peer-to-peer contracts between farmers and companies on Ethereum |
| 🌐 **Multilingual** | Full localization in 6 languages |
| 🌙 **Dark / Light Theme** | User-selectable theme |

---

## Architecture

```
AgriNerds-Pragati-AI-2025/
├── agrinerds/          # Flutter mobile application
│   ├── lib/
│   │   ├── config/     # API endpoints, theme configuration
│   │   ├── constants/  # App-wide constants
│   │   ├── l10n/       # Localization (ARB files for 6 languages)
│   │   ├── models/     # Data models (Crop, Contract, Weather, AI Response)
│   │   ├── pages/      # Screens (Home, Market, Crops, Scheme AI)
│   │   ├── services/   # Business logic (Weather, AI, Crop, Contract, News, etc.)
│   │   ├── state/      # App state management
│   │   └── widgets/    # Reusable UI components
│   └── assets/         # Images, fonts, contract addresses
│
└── marketplace/        # Hardhat blockchain project
    ├── contracts/      # Solidity smart contracts
    ├── scripts/        # Deployment & data-seeding scripts
    └── test/           # Smart contract tests
```

---

## Tech Stack

### Flutter App (`agrinerds/`)

| Category | Technology |
|---|---|
| Framework | Flutter (Dart) |
| Local Storage | SQLite (`sqflite`), `shared_preferences` |
| Networking | `http` |
| Location | `geolocator` |
| Voice I/O | `flutter_tts`, `speech_to_text` |
| Media | `image_picker` |
| Internationalization | `intl`, `flutter_localizations` |

### Blockchain Marketplace (`marketplace/`)

| Category | Technology |
|---|---|
| Smart Contracts | Solidity 0.8.28 |
| Development Framework | Hardhat 2.23+ |
| Contract Libraries | OpenZeppelin Contracts 5.3+ |
| Testing | Chai, Ethers.js |

---

## Getting Started

### Prerequisites

- **Flutter** ≥ 3.9.0 — [Install Flutter](https://docs.flutter.dev/get-started/install)
- **Node.js** ≥ 18 — [Install Node.js](https://nodejs.org/)
- **Android Studio** or **Xcode** (for mobile emulators)

### Flutter App Setup

```bash
# Navigate to the Flutter project
cd agrinerds

# Install dependencies
flutter pub get

# Generate launcher icons (optional)
flutter pub run flutter_launcher_icons

# Run the app
flutter run
```

The app supports **Android**, **iOS**, **Web**, **Linux**, **macOS**, and **Windows**.

### Blockchain Marketplace Setup

```bash
# Navigate to the marketplace project
cd marketplace

# Install dependencies
npm install

# Compile the smart contracts
npx hardhat compile

# Run the test suite
npx hardhat test

# Start a local Hardhat node
npx hardhat node

# Deploy the contract (in a separate terminal)
npx hardhat run scripts/deploy.js --network localhost

# (Optional) Deploy with sample data
npx hardhat run scripts/prepopulate.js --network localhost
```

The deployment script saves the contract address to `agrinerds/assets/contracts/address.json` so the Flutter app can connect to the deployed contract.

---

## Supported Languages

| Language | Code |
|---|---|
| English | `en` |
| Hindi | `hi` |
| Marathi | `mr` |
| Telugu | `te` |
| Malayalam | `ml` |
| Tamil | `ta` |

---

## Smart Contract Overview

The **Marketplace.sol** contract manages peer-to-peer agricultural supply agreements between farmers and companies.

### Contract Types

- **Offer** — A farmer creates an offer to sell a crop directly to a company.
- **Request** — A company posts a request for a crop; multiple farmers can submit commitments.
- **Commitment** — A farmer's bid in response to a company's request.

### Lifecycle

```
Pending → Agreed → DeliveryConfirmed → PaymentConfirmed → Completed
                                                      ↘ Rejected
                                                      ↘ Cancelled
```

### Key Functions

| Function | Description |
|---|---|
| `createOffer()` | Farmer lists a crop for sale |
| `acceptOffer()` | Company accepts a farmer's offer |
| `createRequest()` | Company posts a crop purchase request |
| `submitCommitment()` | Farmer bids on a company request |
| `acceptCommitment()` | Company accepts a farmer's commitment |
| `confirmDelivery()` | Buyer confirms crop delivery |
| `confirmPaymentReceived()` | Seller confirms payment received |
| `cancelContract()` | Either party cancels a pending contract |

---

## Team

**AgriNerds** — Built for Pragati AI 2025

---

## License

This project is part of the Pragati AI 2025 hackathon. 