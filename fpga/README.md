# FPGA Team

## Goal

Algorithms Team의 SOH MLP를 Fixed-Point RTL Hardware로 구현 및 Cora Z7에서 Hardware Inference 수행.

## Target

**Board:** Digilent Cora Z7-07S
**FPGA:** Xilinx Zynq-7000 XC7Z007S
**Tool:** AMD Vivado

## Responsibilities

* Fixed-Point Arithmetic
* MAC Unit
* Dense Layer RTL
* ReLU
* Weight / Bias Storage
* MLP Controller
* UART Interface
* Simulation
* Synthesis
* Hardware Verification

## Input ← Algorithms

* Model Architecture
* Weights
* Biases
* Quantization Specification
* Golden Test Vectors

## Input ← STM32

`SOH Feature Vector`

## Output → STM32

`Estimated SOH`

## Architecture

```text
UART RX
   ↓
Feature Buffer
   ↓
Dense Layer 1
   ↓
ReLU
   ↓
Dense Layer 2
   ↓
ReLU
   ↓
Output Layer
   ↓
SOH
   ↓
UART TX
```

## Initial MLP

`N → 16 → 8 → 1`

최종 구조 → Algorithms Team Model 기준

## Development Flow

```text
Fixed-Point Specification
        ↓
MAC Unit
        ↓
Dense Layer
        ↓
ReLU
        ↓
MLP Integration
        ↓
Simulation
        ↓
Synthesis
        ↓
Cora Z7
        ↓
STM32 Integration
```

## Verification

### Unit

* MAC Unit
* Dense Layer
* ReLU
* UART RX / TX

### Model

`Python Golden Model ↔ RTL Simulation`

### Hardware

`Golden Feature Vector → Cora Z7 → SOH`

## Analysis

* LUT
* FF
* DSP
* BRAM
* Maximum Clock Frequency
* Inference Latency

## Definition of Done

* [ ] Fixed-Point Arithmetic
* [ ] MAC Unit
* [ ] Dense Layer
* [ ] ReLU
* [ ] Complete MLP RTL
* [ ] UART RX / TX
* [ ] RTL Simulation
* [ ] Python vs. RTL Verification
* [ ] Synthesis
* [ ] Cora Z7 Inference
* [ ] STM32 Integration
