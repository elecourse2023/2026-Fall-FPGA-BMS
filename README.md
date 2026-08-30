# FPGA-Based Battery Management System

Samsung INR18650-30Q의 상태 측정, SOC 추정, FPGA 기반 SOH 추정을 수행하는 BMS Prototype.

## System Architecture

```text
Samsung INR18650-30Q
        │
        ▼
   INA228 / NTC
        │
        ▼
      STM32
        │
   ┌────┴─────┐
   │          │
  SOC    SOH Features
   │          │
   │        UART
   │          ▼
   │        FPGA
   │          │
   │       MLP SOH
   │          │
   └─────┬────┘
         ▼
        OLED
```

## Core Functions

* Voltage / Current / Temperature Measurement
* SOC Coulomb Counting
* Fault Detection
* SOH Feature Extraction
* FPGA MLP SOH Inference
* OLED System Display

## Hardware

| Component                 | Device               |
| ------------------------- | -------------------- |
| Battery                   | Samsung INR18650-30Q |
| Voltage / Current Monitor | INA228AIDGSR         |
| Temperature Sensor        | NTC Thermistor       |
| MCU                       | STM32G031K8T6        |
| FPGA                      | Digilent Cora Z7-07S |
| Display                   | 0.96" I²C OLED       |
| MCU ↔ FPGA                | UART                 |

## Teams

### AFE

Battery Measurement / Protection / Calibration

### Firmware

STM32 Control / SOC / Feature Extraction / Communication

### Algorithms

Dataset / Feature Engineering / MLP / Quantization

### FPGA

Fixed-Point MLP / RTL / Hardware Inference

## Repository Structure

```text
.
├── afe/
├── firmware/
├── algorithms/
├── fpga/
├── integration/
├── docs/
├── .github/
├── CONTRIBUTING.md
└── README.md
```

## System Data Flow

### SOC

`Battery → Current Measurement → STM32 → Coulomb Counting → SOC`

### SOH

`Battery → Diagnostic Test → Feature Extraction → STM32 → FPGA MLP → Estimated SOH`

### Validation

`Capacity Test → Actual SOH ↔ FPGA Estimated SOH`

## Development Workflow

`Issue → Branch → Development → Test → Pull Request → Review → Merge`

`main` Branch 직접 작업 금지.

자세한 협업 규칙: [CONTRIBUTING.md](CONTRIBUTING.md)

## Documentation

* [System Architecture](docs/system_architecture.md)
* [Hardware Specification](docs/hardware_spec.md)
* [SOH Specification](docs/soh_spec.md)
* [Safety](docs/safety.md)
* [Integration](integration/README.md)

## Final Goal

**Samsung INR18650-30Q 기반 FPGA-Accelerated BMS Prototype 구현**

`Measurement → Processing → Estimation → Hardware Acceleration → Validation → Display`
