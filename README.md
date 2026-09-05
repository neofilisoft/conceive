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

ภาษาไทย
ภาพรวมโครงการ
คลังข้อมูลนี้รวบรวมโมดูลจำลองระบบตัวตนดิจิทัลและการสืบพันธุ์สายพันธุ์จำลอง พัฒนาด้วยภาษา Wyrm (.wyr) โดยตัวระบบสามารถจำลองอัตราการตั้งครรภ์ ความน่าจะเป็นทางพันธุกรรม ค่าศักยภาพ บุคลิกภาพเชิงพุทธิปัญญา และอวัยวะดิจิทัล พร้อมทั้งส่งออกข้อมูลในรูปแบบมาตรฐานทั้ง JSON และ YAML

โมดูลหลักในระบบ
1. conseive.wyr (ระบบจำลองการผสมพันธุ์และสายเลือด)
ทำหน้าที่คำนวณความน่าจะเป็นในการตั้งครรภ์และการส่งต่อลักษณะเฉพาะไปยังรุ่นลูก:

การคำนวณอัตราความสำเร็จตามคู่สายพันธุ์:

มนุษย์ + มนุษย์ (Human + Human): อัตราสำเร็จ 70% ถึง 90%

เอลฟ์ + เอลฟ์ (Elf + Elf): อัตราสำเร็จ 40% ถึง 50%

มนุษย์ + เอลฟ์ (Human + Elf): อัตราสำเร็จ 28% ถึง 45%

สายพันธุ์อื่นๆ: ยังไม่รองรับในเวอร์ชันปัจจุบัน

การทอยลูกเต๋า (Roll Result): จำลองการทอยแต้ม 1 ถึง 100 เพื่อเทียบกับอัตราร้อยละของการตั้งครรภ์

การสร้างตัวตนของรุ่นลูก (Child Identity):

คำนวณค่าศักยภาพ (potential) จากผลลัพธ์การทอยแต้มและค่าความผันแปรสุ่ม (-10 ถึง +10) ควบคุมช่วงค่าให้อยู่ระหว่าง 1 ถึง 100

คำนวณคุณสมบัติพื้นฐาน ได้แก่ ตรรกะ (logic), ความสามารถในการปรับตัว (adaptability), และความมั่นคง (stability)

กำหนดรหัสระบุตัวตนแบบกระจายศูนย์ (did:soken:...) และรหัส Soul Signature

ส่งออกโครงสร้างข้อมูลของลูกผ่านโมดูล std.json และ std.yaml

2. oae.wyr (ระบบสร้างอัตลักษณ์ดิจิทัล Soken)
ทำหน้าที่สร้างข้อมูลอัตลักษณ์ดิจิทัลตามสเปก soken_identity_v1:

ข้อมูลตัวตนและที่มา (Identity & Provenance):

ออกแบบในลักษณะ Soulbound: ไม่สามารถสับเปลี่ยนได้ มีเอกลักษณ์เฉพาะตัว ไม่สามารถโอนย้ายได้ และผูกกับนโยบาย soul-consensus-v1

กำหนด Decentralized Identifier ในรูปแบบ did:world:0x... และระบุโหนดเจ้าของ (AetherLab:Node-*)

รองรับการกำหนดภูมิภาค ได้แก่ TH, SEA, GLOBAL, และ LAB

รหัสพันธุกรรมดิจิทัล (DDNA):

สถาปัตยกรรมบุคลิก (Archetypes): Analytic-Guardian, Stoic-Strategist, Curious-Explorer, Empathic-Mediator, Genesis-Hybrid

ติดตามลำดับรุ่น (Generation 1 ถึง 12) พร้อมอัตราการกลายพันธุ์ (Mutation Rate)

คุณลักษณะแกนกลาง: ตรรกะ, ความเข้าอกเข้าใจ, ความอยากรู้อยากเห็น, และวินัย

ระบบการรู้คิดและการทำงานของจิต (Cognition):

ลักษณะบุคลิก (Persona): Stoic-Analytic, Balanced-Strategist, Adaptive-Learner, Resilient-Core

พารามิเตอร์ด้านจิตวิทยา: ความสอดคล้อง (Alignment), ความผันผวนทางอารมณ์ (Volatility), ความมั่นใจ (Confidence), อัตราการเรียนรู้ (Learning Rate)

อวัยวะดิจิทัล (Digital Organs):

แขนขวา (arm_right): สกีมา motor_v2_power (ผันแปรได้)

ขา (legs): สกีมา motor_v2_endurance (คงที่)

แกนความจำ (memory_core): สกีมา cognitive_v1_memory (คงที่)

3. ระบบสุ่มแบบ Pure-Jitter RNG
ทั้งสองไฟล์ทำงานผ่านอัลกอริทึม Linear Congruential Generator (LCG) ที่กำหนดค่าเริ่มต้น (Seed) ผ่านการประมวลผลลูปหลายหมื่นรอบ เพื่อสร้างค่าสุ่มที่ทำงานได้ด้วยตนเองโดยไม่ต้องพึ่งพาระบบเวลาของระบบปฏิบัติการ
