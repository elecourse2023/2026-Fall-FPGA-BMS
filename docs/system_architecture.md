# System Architecture

## Goal

Samsung INR18650-30Q 상태 측정 및 FPGA 기반 SOC·SOH Estimation BMS Prototype.

## Architecture

```text
                 Samsung INR18650-30Q
                           │
                  ┌────────┴────────┐
                  │                 │
            Measurement      Diagnostic Test
                  │                 │
             INA228 / NTC      Charge / Load
                  │                 │
                  └────────┬────────┘
                           │
                         STM32
                           │
                ┌──────────┴──────────┐
                │                     │
               SOC               SOH Features
                │                     │
           Fault State               UART
                │                     │
                │                    FPGA
                │                     │
                │               Fixed-Point MLP
                │                     │
                │                Estimated SOH
                │                     │
                └──────────┬──────────┘
                           │
                          OLED
```

## Subsystems

### Electrical

`Battery → V / I / T`

### Firmware

`V / I / T → SOC / Fault / SOH Features`

### Algorithms

`Dataset → Features → MLP → Quantized Model`

### FPGA

`SOH Features → Fixed-Point MLP → SOH`

## SOC Flow

`Current → STM32 → Coulomb Counting → SOC`

## SOH Flow

`Diagnostic Data → Feature Extraction → FPGA MLP → Estimated SOH`

## Validation Flow

`Capacity Test → Actual SOH ↔ Estimated SOH`

## Team Interfaces

| From       | To       | Data                           |
| ---------- | -------- | ------------------------------ |
| Electrical | Firmware | V / I / T                      |
| Algorithms | Firmware | Feature Specification          |
| Algorithms | FPGA     | Model / Weights / Quantization |
| Firmware   | FPGA     | Feature Vector                 |
| FPGA       | Firmware | Estimated SOH                  |
| Firmware   | OLED     | System Status                  |
