# Formal Verification of DID-based A2A Delegation Protocol

This repository contains the Tamarin Prover models used for the formal verification of our protocol.

## Overview

We verify a secure DID-based agent authentication and delegation protocol under the Dolev–Yao adversary model.

To avoid state-space explosion, verification is modularized into:

- DH authentication model
- Direct execution model
- Delegation setup model
- Delegated execution model
- Response verification model

---

## Structure
tamarin-a2a-delegation/
│
├── models/
│   ├── model_dh.spthy
│   ├── model_direct_only.spthy
│   ├── model_delegation_setup.spthy
│   ├── model_delegation_exec.spthy
│   ├── model_delegation_response.spthy
│   ├── model_compromise_only.spthy
├── README.md
├── LICENSE
└── .gitignore


## Requirements

- Tamarin Prover (>= 1.6)

Install:

```bash
sudo apt install tamarin-prover (https://tamarin-prover.com/install.html)

## Run Verification
DH Authentication
tamarin-prover --prove models/model_dh.spthy
Direct Execution
tamarin-prover --prove models/model_direct_only.spthy
Delegation
tamarin-prover --prove models/model_delegation_setup.spthy
tamarin-prover --prove models/model_delegation_exec.spthy
tamarin-prover --prove models/model_delegation_response.spthy

## Verified Properties
Authentication (agreement, injective agreement)
Confidentiality (task secrecy)
Delegation correctness
Response authenticity
Executability
