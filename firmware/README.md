# Firmware Team

## Goal

STM32 기반 Battery Measurement 처리, SOC 계산, SOH Feature Extraction 및 System Control 구현.

## Target

**MCU:** STM32G031K8T6

**IDE:** STM32CubeIDE

## Responsibilities

* INA228 Communication
* NTC ADC
* Measurement Conversion
* Calibration
* SOC Coulomb Counting
* SOH Feature Extraction
* Fault Detection
* UART Communication
* OLED Control
* Data Logging
* System Integration

## Input ← AFE

* Voltage
* Current
* Temperature

## Output → FPGA

`SOH Feature Vector`

## Input ← FPGA

`Estimated SOH`

## Output → OLED

* Voltage
* Current
* Temperature
* SOC
* SOH
* System State

## Main Flow

```text
Initialize
    ↓
Measurement
    ↓
Calibration
    ↓
SOC Update
    ↓
Fault Check
    ↓
Feature Extraction
    ↓
FPGA Communication
    ↓
OLED Update
```

## Initial Task Rate

| Task              |                 Rate |
| ----------------- | -------------------: |
| Voltage / Current |                10 Hz |
| Temperature       |                10 Hz |
| SOC               |                10 Hz |
| Fault Check       |                10 Hz |
| OLED              |                 2 Hz |
| SOH               | Diagnostic Test 완료 시 |

## Communication

### INA228

`STM32 ↔ I²C ↔ INA228`

### OLED

`STM32 ↔ I²C ↔ OLED`

### FPGA

`STM32 ↔ UART ↔ Cora Z7`

UART Format 기준: [`integration/README.md`](../integration/README.md)

## Definition of Done

* [ ] INA228 Communication
* [ ] NTC Measurement
* [ ] SOC Coulomb Counting
* [ ] Fault Detection
* [ ] Feature Extraction
* [ ] STM32 → FPGA UART
* [ ] FPGA → STM32 SOH
* [ ] OLED Display
* [ ] End-to-End Integration
