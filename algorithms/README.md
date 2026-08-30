# Algorithms Team

## Goal

Samsung INR18650-30Q Aging Dataset 기반 SOH Estimation Model 개발 및 FPGA 구현용 Quantized Model 생성.

## Dataset

**Battery:** Samsung INR18650-30Q

**Data**

* Cycling Data
* RPT Data
* Capacity Data
* DCIR Data
* Voltage / Current / Temperature
* Processed Features

## Responsibilities

* Dataset Analysis
* SOH Label Generation
* Feature Engineering
* Feature Selection
* MLP Training
* Model Evaluation
* Quantization
* Golden Model
* Golden Test Vector

## Pipeline

```text
Dataset
   ↓
Data Cleaning
   ↓
SOH Label
   ↓
Feature Engineering
   ↓
Feature Selection
   ↓
MLP Training
   ↓
Evaluation
   ↓
Quantization
   ↓
FPGA Export
```

## SOH Definition

**Capacity-Based SOH**

`SOH (%) = Current Capacity / Initial Capacity × 100`

Capacity Test 결과 → Ground Truth Label

## Dataset Split

**Cell-Based Split**

```text
Training
Validation
Test
```

동일 Cell의 Cycle Data를 Train / Test에 무작위 혼합 금지.

## Feature Selection Criteria

* SOH Prediction Accuracy
* 실제 Battery 측정 가능성
* STM32 Feature Extraction 가능성
* FPGA 구현 효율성
* Feature Redundancy 최소화

## Candidate Features

* DCIR @ Selected SOC
* Voltage Curve Features
* Voltage Interval Time
* Charge / Discharge Time
* Temperature Features
* Dataset-derived Health Indicators

**초기 후보:** 약 20~30 Features
**최종 목표:** 약 5~10 Features

## Initial MLP

`N → 16 → 8 → 1`

**Hidden Activation:** ReLU
**Output:** SOH (%)

최종 Architecture → Accuracy / FPGA Resource 기반 결정

## Evaluation

* MAE
* RMSE
* Maximum Error
* Unseen Cell Performance

## Output → Firmware

* Final Feature List
* Feature Definition
* Feature Extraction Specification

## Output → FPGA

* Model Architecture
* Weights
* Biases
* Quantization Specification
* Golden Test Vectors
* Expected Outputs

## Definition of Done

* [ ] Master Dataset
* [ ] Cell-Based Split
* [ ] SOH Labels
* [ ] Feature Selection
* [ ] MLP Training
* [ ] Test Set Evaluation
* [ ] Quantized Model
* [ ] Golden Test Vectors
* [ ] FPGA Model Verification
