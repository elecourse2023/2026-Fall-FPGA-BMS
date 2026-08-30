# System Integration

## Goal

Electrical / Firmware / Algorithms / FPGA Subsystem의 End-to-End Integration.

## System Flow

```text
Samsung 30Q
     │
     ▼
INA228 / NTC
     │
     ▼
   STM32
     │
 ┌───┴──────┐
 │          │
SOC    SOH Features
 │          │
 │        UART
 │          ▼
 │        FPGA
 │          │
 │       MLP SOH
 │          │
 └────┬─────┘
      ▼
     OLED
```

# Interfaces

## Electrical → Firmware

**Data**

* Voltage
* Current
* Temperature

**Required Specification**

* Unit
* Range
* Resolution
* Calibration

---

## Algorithms → Firmware

**Data**

* Final Feature List
* Feature Definition
* Extraction Method
* Scaling Method

---

## Algorithms → FPGA

**Data**

* Model Architecture
* Weights
* Biases
* Fixed-Point Format
* Golden Test Vector
* Expected Output

---

## Firmware → FPGA

**Communication:** UART

**Payload:** SOH Feature Vector

Final Packet Format → Integration 과정에서 확정

필수 정의:

* Header
* Feature Count
* Feature Order
* Data Type
* Fixed-Point Format
* Endianness
* Checksum
* Terminator

---

## FPGA → Firmware

**Communication:** UART

**Payload:** Estimated SOH

필수 정의:

* Data Type
* Fixed-Point Format
* Scale
* Error / Valid Signal

---

# Integration Test

## Test 1 — Electrical ↔ Firmware

`Reference Input → INA228 / NTC → STM32 → Measurement 비교`

## Test 2 — Firmware ↔ FPGA

`STM32 Test Vector → UART → FPGA → UART → STM32`

## Test 3 — Algorithms ↔ FPGA

`Golden Feature Vector → RTL → Golden Output 비교`

## Test 4 — End-to-End

`Battery → Measurement → Feature → FPGA → SOH → OLED`

---

# Golden Test Vector

Algorithms Team 제공

```text
Input Features
      ↓
Python Golden Model
      ↓
Expected SOH
```

동일 Input → FPGA 입력 → 결과 비교

---

# Final Demo

### Live BMS

* Voltage
* Current
* Temperature
* SOC
* Fault State

### SOH

* Feature Extraction
* STM32 → FPGA
* FPGA MLP Inference
* FPGA → STM32
* OLED SOH

### Validation

`Actual Capacity SOH ↔ FPGA Estimated SOH`

## Definition of Done

* [ ] Electrical ↔ Firmware
* [ ] Firmware ↔ FPGA UART
* [ ] Algorithms ↔ FPGA
* [ ] Golden Vector Verification
* [ ] OLED Integration
* [ ] Real Battery SOH Estimation
* [ ] End-to-End Demo
