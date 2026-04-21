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
- Compromised verification model

---

## Repository Structure

```
tamarin-a2a-delegation/
├── models/
│   ├── model_dh.spthy
│   ├── model_direct_only.spthy
│   ├── model_delegation_setup.spthy
│   ├── model_delegation_exec.spthy
│   ├── model_delegation_response.spthy
│   └── model_compromise_only.spthy
├── README.md
├── LICENSE
└── .gitignore
```


## Description

- `model_dh.spthy`  
  DID-based authentication using Diffie–Hellman agreement.

- `model_direct_only.spthy`  
  Direct client–agent interaction, verifying authentication and task secrecy.

- `model_delegation_setup.spthy`  
  Delegation request generation and validation between client and delegated agent.

- `model_delegation_exec.spthy`  
  Delegated task execution, ensuring tasks are executed only with valid delegation.

- `model_delegation_response.spthy`  
  Response verification, ensuring end-to-end integrity of execution results.

- `model_compromise_only.spthy`  
  Compromise scenario analysis, modeling key leakage and evaluating how security properties degrade under adversarial conditions.

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
tamarin-prover --prove models/model_compromise_only.spthy

## Verified Properties
Authentication (agreement, injective agreement)
Confidentiality (task secrecy)
Delegation correctness
Response authenticity
Executability
