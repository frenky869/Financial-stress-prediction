# 💰 Financial Stress Prediction - Mobile Money Transaction Analysis

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Zindi](https://img.shields.io/badge/Zindi-Competition-orange.svg)](https://zindi.africa/competitions/financial-stress-prediction)

---

## 📋 Table of Contents
- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Dataset Description](#dataset-description)
- [Technical Implementation](#technical-implementation)
- [File Structure](#file-structure)
- [Installation & Usage](#installation--usage)
- [Model Performance](#model-performance)
- [Feature Importance](#feature-importance)
- [Competition Strategy](#competition-strategy)
- [References](#references)
- [Contributing](#contributing)
- [License](#license)

---

## 📋 Overview

This project predicts financial stress (liquidity stress) among mobile money customers using six months of transaction history. The model identifies customers likely to experience financial hardship in the next 30 days, enabling financial institutions to provide timely support.

### 🎯 Competition Context
- **Platform**: Zindi
- **Evaluation**: 60% Log Loss + 40% ROC-AUC
- **Goal**: Output calibrated probability predictions
- **Target**: `liquidity_stress_next_30d` (binary)
- **Output**: `ID` and `Target` probability (0-1)

---

## 🎯 Problem Statement

Mobile money is central to everyday financial life across Africa. It helps millions of households and small businesses receive income, send money, pay bills, access services, and manage day-to-day expenses.

When financial pressure begins to build, customers often show early warning signs in their transaction behavior before any formal default occurs. Detecting these signals early can help financial institutions provide timely support and reduce the risk of deeper financial hardship.

### 🏆 Prizes
- 🥇 1st place: $150
- 🥈 2nd place: $100
- 🥉 3rd place: $50

---

## 📊 Dataset Description

The dataset contains mobile money transaction records over six months (m1-m6). Each row represents a customer's recent activity at a specific date.

### Feature Categories

| Category | Description | Examples |
|----------|-------------|----------|
| **Demographics** | Customer profile | `age`, `gender`, `region`, `smartphone`, `segment`, `earning_pattern` |
| **Revenue** | Customer value | `arpu` (Average Revenue Per User) |
| **Transaction Activity** | Counts per type | `paybill_volume`, `withdraw_volume`, `send_volume` |
| **Transaction Values** | Monetary amounts | `paybill_total_value`, `withdraw_total_value` |
| **Transaction Extrema** | Highest single transaction | `*_highest_amount` |
| **Counterparty Diversity** | Unique counterparties | `agents`, `recipients`, `senders`, `banks`, `merchants` |
| **Balance Metrics** | Daily average balances | `m1_daily_avg_bal` through `m6_daily_avg_bal` |

### Transaction Types (Monthly)
1. **Paybill** - Bill payments
2. **Merchant Payment** - Point-of-sale purchases
3. **Transfer from Bank** - Bank-to-mobile transfers
4. **MM Send** - Mobile money sends
5. **Received** - Mobile money receipts
6. **Deposit** - Cash deposits
7. **Withdraw** - Cash withdrawals

### Metrics Per Transaction Type
- `volume` - Number of transactions
- `total_value` - Total monetary value
- `highest_amount` - Maximum single transaction
- `counterparty_count` - Unique counterparties (agents, recipients, etc.)

### Data Files
| File | Description | Size |
|------|-------------|------|
| `Train.csv` | Training dataset | 34.9 MB |
| `Test.csv` | Testing dataset | 26.1 MB |
| `SampleSubmission.csv` | Submission format | 556.7 KB |
| `data_dictionary.csv` | Variable descriptions | 31.6 KB |

### Target Variable
- **`liquidity_stress_next_30d`**: Binary indicator (0/1) of whether the customer experienced liquidity stress in the 30 days following the observation date

---

## 🛠️ Technical Implementation

### Dependencies

```bash
pip install -r requirements.txt
