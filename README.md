# Soken Digital Identity & Breeding Simulation (Wyrm)

An experimental simulation engine written in the Wyrm programming language (`.wyr`) for generative digital identities, cross-species breeding mechanics, and non-transferable cognitive profiles.

[English](#english) | [ภาษาไทย](#ภาษาไทย)

---

<a name="english"></a>
## English

### Overview
This repository contains simulation modules written in Wyrm for generative lineage and digital soul dynamics. The engine models biological conception odds, inheritable potential, dynamic cognitive traits, and digital organ specifications, exporting structured identity records in both JSON and YAML formats.

### Core Modules

#### 1. `conseive.wyr` (Breeding and Lineage Engine)
Simulates conception mechanics and genetic trait inheritance between different species:
* **Breeding Odds Calculation**:
  * Human + Human: 70% to 90% success rate
  * Elf + Elf: 40% to 50% success rate
  * Human + Elf / Elf + Human: 28% to 45% success rate
  * Other combinations: Currently unsupported
* **Conception Check**: Rolls a d100 dice against the calculated pregnancy rate.
* **Child Identity Generation**:
  * Calculates `potential` (base roll modified by jitter between -10 and +10, clamped between 1 and 100).
  * Derives core baseline traits: `logic`, `adaptability`, and `stability`.
  * Assigns decentralized identifiers (`did:soken:...`) and cryptographic soul signatures.
  * Exports formatted lineage identity records using native `std.json` and `std.yaml` libraries.

#### 2. `oae.wyr` (Soken Digital Identity Generator)
Generates full-scale synthetic digital identity constructs conforming to the `soken_identity_v1` specification:
* **Identity and Provenance**:
  * Soulbound architecture: Non-fungible, unique, non-transferable, bound by `soul-consensus-v1`.
  * Decentralized identifier: `did:world:0x...` with owner designation under `AetherLab:Node-*`.
  * Regional zoning: Supports `TH`, `SEA`, `GLOBAL`, and `LAB`.
* **Digital DNA (DDNA)**:
  * Archetypes: Analytic-Guardian, Stoic-Strategist, Curious-Explorer, Empathic-Mediator, Genesis-Hybrid.
  * Generational tracking (Generations 1 to 12) with randomized mutation rates.
  * Foundational traits: Logic, Empathy, Curiosity, and Discipline.
* **Cognitive Profile**:
  * Personas: Stoic-Analytic, Balanced-Strategist, Adaptive-Learner, Resilient-Core.
  * Parameters: Alignment, Volatility, Confidence, Learning Rate, and Affect Level.
* **Digital Organs**:
  * Right Arm: `motor_v2_power` (Volatile)
  * Legs: `motor_v2_endurance` (Non-volatile)
  * Memory Core: `cognitive_v1_memory` (Non-volatile)

#### 3. Deterministic Jitter RNG
Both scripts implement a self-contained Linear Congruential Generator (LCG) seeded via multi-stage computational jitter (`init_rng_from_jitter`). This provides portable pseudo-randomness without relying on external system clock primitives.

### Project Structure
```text
.
├── conseive.wyr    # Conception rate calculator and child identity generator
├── oae.wyr         # Digital identity generator with DDNA and organ matrices
└── README.md       # Project documentation
