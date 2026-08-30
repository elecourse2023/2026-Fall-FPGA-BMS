# SOH Specification

## Definition

**SOH:** Capacity-Based State of Health

`SOH (%) = Current Capacity / Initial Capacity × 100`

## Ground Truth

**Initial Capacity:** 최초 Capacity Test

**Current Capacity:** 현재 Capacity Test

**Ground Truth SOH:** Capacity 기반 계산값

---

# Dataset

**Cell:** Samsung INR18650-30Q

### Data

* Cycling Data
* RPT Data
* Capacity
* DCIR
* Voltage
* Current
* Temperature
* Processed Features

---

# Dataset Split

**기준:** Cell-Based Split

`Training / Validation / Test`

동일 Cell의 데이터를 Train / Test에 무작위 혼합 금지.

---

# Feature Engineering

## Criteria

* SOH Prediction Accuracy
* 실제 Battery 측정 가능성
* STM32 Extraction 가능성
* FPGA 구현 효율성
* Redundancy 최소화

## Candidate

* DCIR
* Voltage Curve Features
* Voltage Interval Time
* Charge / Discharge Time
* Temperature Features

**초기 후보:** 20~30 Features
**최종 목표:** 5~10 Features

최종 Feature List → Dataset 분석 후 확정

---

# MLP

## Initial Architecture

`N → 16 → 8 → 1`

### Hidden Layer

ReLU

### Output

SOH (%)

최종 Architecture → Model Evaluation 결과 기반 확정

---

# Quantization

**Training Model:** Floating-Point

**FPGA Model:** Fixed-Point

Algorithms Team 제공:

* Fixed-Point Format
* Weights
* Biases
* Input Scaling
* Output Scaling
* Golden Test Vectors

---

# Verification

## Software

`Test Dataset → Python MLP → Predicted SOH`

## RTL

`Golden Feature → RTL MLP → SOH`

## Hardware

`Golden Feature → Cora Z7 → SOH`

## Real Battery

`Battery → Feature Extraction → FPGA → Estimated SOH`

## Ground Truth

`Capacity Test → Actual SOH`

## Final Validation

`Actual SOH ↔ Estimated SOH`

### Metrics

* MAE
* RMSE
* Maximum Error
