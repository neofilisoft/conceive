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
```

<a name="ภาษาไทย"></a>
## ภาษาไทย ### 
ภาพรวมโครงการ คลังข้อมูลนี้รวบรวมโมดูลจำลองระบบตัวตนดิจิทัลและการสืบพันธุ์สายพันธุ์จำลอง พัฒนาด้วยภาษา Wyrm (`.wyr`) โดยตัวระบบสามารถจำลองอัตราการตั้งครรภ์ ความน่าจะเป็นทางพันธุกรรม ค่าศักยภาพ บุคลิกภาพเชิงพุทธิปัญญา และอวัยวะดิจิทัล พร้อมทั้งส่งออกข้อมูลในรูปแบบมาตรฐานทั้ง JSON และ YAML 
### โมดูลหลักในระบบ 
#### 1. `conseive.wyr` (ระบบจำลองการผสมพันธุ์และสายเลือด) 
ทำหน้าที่คำนวณความน่าจะเป็นในการตั้งครรภ์และการส่งต่อลักษณะเฉพาะไปยังรุ่นลูก: 
* **การคำนวณอัตราความสำเร็จตามคู่สายพันธุ์**: 
 * มนุษย์ + มนุษย์ (Human + Human): อัตราสำเร็จ 70% ถึง 90%[cite: 1] 
 * เอลฟ์ + เอลฟ์ (Elf + Elf): อัตราสำเร็จ 40% ถึง 50%[cite: 1] 
 * มนุษย์ + เอลฟ์ / เอลฟ์ + มนุษย์ (Human + Elf / Elf + Human): อัตราสำเร็จ 28% ถึง 45%[cite: 1] 
 * สายพันธุ์อื่นๆ: ยังไม่รองรับในเวอร์ชันปัจจุบัน[cite: 1] 
* **การตรวจสอบการตั้งครรภ์ (Conception Check)**: จำลองการทอยลูกเต๋า d100 เพื่อเทียบกับอัตราร้อยละของการตั้งครรภ์ที่คำนวณได้[cite: 1] 
* **การสร้างตัวตนของรุ่นลูก (Child Identity Generation)**: 
 * คำนวณค่าศักยภาพ (`potential`) จากผลลัพธ์การทอยแต้มปรับด้วยค่าสุ่มผันแปรระหว่าง -10 ถึง +10 โดยจำกัดค่าให้อยู่ในช่วง 1 ถึง 100[cite: 1] 
 * คำนวณคุณสมบัติพื้นฐาน ได้แก่ ตรรกะ (`logic`), ความสามารถในการปรับตัว (`adaptability`), และความมั่นคง (`stability`)[cite: 1] 
 * กำหนดรหัสระบุตัวตนแบบกระจายศูนย์ (`did:soken:...`) และรหัส Soul Signature สำหรับยืนยันตัวตน[cite: 1] 
 * ส่งออกโครงสร้างข้อมูลประวัติสายเลือดผ่านไลบรารีมาตรฐาน `std.json` และ `std.yaml`[cite: 1] 
 
#### 2. `oae.wyr` (ระบบสร้างอัตลักษณ์ดิจิทัล Soken) 
ทำหน้าที่สร้างข้อมูลอัตลักษณ์สังเคราะห์ระดับเต็มรูปแบบตามข้อกำหนดมาตรฐาน `soken_identity_v1`:[cite: 2] 
* **ข้อมูลตัวตนและที่มา (Identity and Provenance)**: 
 * สถาปัตยกรรม Soulbound: ไม่สามารถสับเปลี่ยนได้ มีเอกลักษณ์เฉพาะตัว ไม่สามารถโอนย้ายได้ และผูกกับนโยบาย `soul-consensus-v1`[cite: 2] 
 * กำหนดรหัส Decentralized Identifier ในรูปแบบ `did:world:0x...` พร้อมระบุโหนดเจ้าของ (`AetherLab:Node-*`)[cite: 2] 
 * รองรับการกำหนดภูมิภาค ได้แก่ `TH`, `SEA`, `GLOBAL`, และ `LAB`[cite: 2] 
* **รหัสพันธุกรรมดิจิทัล (DDNA)**: 
 * สถาปัตยกรรมบุคลิก (Archetypes): Analytic-Guardian, Stoic-Strategist, Curious-Explorer, Empathic-Mediator, Genesis-Hybrid[cite: 2] 
 * ติดตามลำดับรุ่น (Generation 1 ถึง 12) พร้อมอัตราการกลายพันธุ์แบบสุ่ม[cite: 2]  
 * คุณลักษณะแกนกลาง: ตรรกะ (Logic), ความเข้าอกเข้าใจ (Empathy), ความอยากรู้อยากเห็น (Curiosity), และวินัย (Discipline)[cite: 2] 
* **ระบบการรู้คิดและการทำงานของจิต (Cognitive Profile)**: 
 * ลักษณะบุคลิก (Personas): Stoic-Analytic, Balanced-Strategist, Adaptive-Learner, Resilient-Core[cite: 2]
 * * พารามิเตอร์ด้านจิตวิทยา: ความสอดคล้อง (Alignment), ความผันผวน (Volatility), ความมั่นใจ (Confidence), อัตราการเรียนรู้ (Learning Rate), และระดับอารมณ์กระทบ (Affect Level)[cite: 2] * **อวัยวะดิจิทัล (Digital Organs)**: * แขนขวา (`arm_right`): สกีมา `motor_v2_power` (ผันแปรได้)[cite: 2] * ขา (`legs`): สกีมา `motor_v2_endurance` (คงที่)[cite: 2] * แกนบันทึกความจำ (`memory_core`): สกีมา `cognitive_v1_memory` (คงที่)[cite: 2] 

#### 3. ระบบสุ่มแบบ Deterministic Jitter RNG ทั้งสองสคริปต์ทำงานผ่านอัลกอริทึม Linear Congruential Generator (LCG) ในตัว โดยตั้งค่า Seed ผ่านรอบหมุนคำนวณ Jitter หลายขั้นตอน (`init_rng_from_jitter`) เพื่อสร้างตัวเลขสุ่มเทียมที่พกพาไปทำงานได้ทุกระบบโดยไม่ต้องพึ่งพาระบบเวลาของระบบปฏิบัติการ[cite: 1, 2] 
### โครงสร้างโปรเจกต์ 
```text
.
├── conseive.wyr    # Conception rate calculator and child identity generator
├── oae.wyr         # Digital identity generator with DDNA and organ matrices
└── README.md       # Project documentation
```
