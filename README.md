
# Compliant Private Tokens Workshop - Token Template

This is the Leo project scaffolding for the Aleo compliant private tokens workshop.  For more information, head over to the [main repository](https://github.com/alex-aleo/private-token-workshop).


## Deployment Information

- **Program Name:** `ndyboy_token.aleo`  
- **Blockchain:** Aleo Testnet  
- **Dependency Module:** `workshop_ofac.aleo` (for compliance verification)  
- **Deployment ID:** `at1paz0ctkllwl9x5nsz8fau3rhnd7t38rexlhqrj5pydnrt5n9lsqsltnng9`  
- **Deployment URL:** [View on Aleo Testnet](https://testnet.aleo123.io/program/ndyboy_token.aleo)   

---

## Execution Information
- **mint_public ID:** `at14h4xlh3t8hycxmw6d3vc7zxk645fjd5y7rprt6rd2uh3a46aksys90wgyy`
- **mint_private ID:** `at19t056tptf45yapar0hjwhsqmcpf2hkqjaudau0dp5upmluq8xqfqwckj8r`

---

## Project Overview

The **Compliance Token** represents a compliant digital asset that balances **regulatory enforcement** and **user privacy**.  
It integrates a compliance layer through `workshop_ofac.aleo`, ensuring that all public and private operations — from minting to transfers — undergo address verification before execution.

This project reflects Aleo’s vision: **privacy and compliance can coexist** within decentralized systems.

---

## Purpose

This project was created to help participants of the **Aleo Workshop in Uyo** learn how to:

- Build privacy-first token contracts using **Leo**.  
- Understand **public mappings** vs. **private record storage**.  
- Integrate compliance verification through **asynchronous functions (Future + await)**.  
- Deploy and interact with Aleo programs confidently.  

---

## Core Principles

### **1. Public Ledger Operations**

Public functions operate on transparent on-chain mappings of balances.  
Each address and its balance are visible but verified before any update.

Example functions include:

- `mint_public`: Mints tokens to an address after compliance check.  
- `transfer_public`: Transfers visible balances between two verified addresses.

mapping balances: address => u64;
Examples:

mint_public: Mints tokens to a recipient after verification.

transfer_public: Transfers tokens between verified public addresses.

All balances remain visible, ensuring auditability and accountability.

---

### **2. Private Record Operations**

Private functions utilize Aleo’s record system to maintain confidentiality of ownership and balances.

record Token {
    owner: address,
    amount: u64
}


Examples:

mint_private: Mints tokens privately as encrypted records.

transfer_private: Transfers value privately using record consumption and regeneration.

Records are cryptographically bound to owners and never publicly revealed, protecting user privacy.

---

### **3. Integrated Compliance Layer**

Every operation interacts with the compliance module:

let address_check: Future = workshop_ofac.aleo/address_check(recipient);
address_check.await();


This mechanism validates every address against restricted lists before any minting or transfer occurs, ensuring regulatory alignment.

---

 ## Functional Overview
 
| Function           | Visibility | Description                                                     |
| ------------------ | ---------- | --------------------------------------------------------------- |
| `mint_public`      | Public     | Adds tokens to recipient’s balance after compliance validation. |
| `mint_private`     | Private    | Issues a new token record privately to the recipient.           |
| `transfer_public`  | Public     | Moves visible tokens between two public accounts.               |
| `transfer_private` | Private    | Privately transfers tokens via record regeneration.             |

---

## Build, Run, and Deploy

**Build the project:**

```bash
leo build
```

**Deploy to Aleo Testnet:**

```bash
leo deploy
```

**Run sample functions:**

```bash
leo run mint_public recipient_address 100u64
leo run transfer_public recipient_address 100u64
leo run mint_private recipient_address 100u64
leo run transfer_private sender_record recipient_address 20u64
```
---


## Use Case Scenarios

- **Regulated Token Deployments:** Enables compliant issuance of digital assets.
- **Privacy-Preserving Transactions:** Supports confidential transfers while maintaining compliance.
- **Enterprise & Institutional Use:** Ideal for CBDCs, corporate tokens, and other regulated assets.

---

## Educational Value

This project represents the practical component of the Aleo Workshop in Uyo.
It bridges theoretical understanding and hands-on zero-knowledge development, teaching participants how to:

* Write Leo contracts with compliance logic.
* Manage private and public state.
* Deploy, test, and verify privacy-preserving applications.

---
<img width="855" height="361" alt="decrypted rec" src="https://github.com/user-attachments/assets/d4413193-2e91-40f1-a6ba-31281ad1453a" />

