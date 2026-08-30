# Electrical Team

## Goal

Samsung INR18650-30Q의 Voltage / Current / Temperature 측정 및 Battery Protection Hardware 구현.

## Target

* Samsung INR18650-30Q
* INA228AIDGSR
* NTC Thermistor
* Shunt Resistor
* Protection Circuit

## Responsibilities

* INA228 Measurement Circuit
* Voltage Measurement
* Current Measurement
* NTC Temperature Measurement
* Shunt Resistor Design
* Battery Charge / Discharge Path
* DCIR Test Hardware
* Protection Circuit
* Hardware Calibration

## Input

`Samsung INR18650-30Q`

## Output → Firmware

* Voltage
* Current
* Temperature
* Measurement Range
* Calibration Data

## Development Flow

```text
Schematic
   ↓
Prototype Circuit
   ↓
Power Supply Test
   ↓
Measurement Verification
   ↓
Calibration
   ↓
Battery Connection
   ↓
Firmware Integration
```

## Verification

### Voltage

`INA228 Measurement ↔ Multimeter`

### Current

`INA228 Measurement ↔ Reference Current`

### Temperature

`NTC Measurement ↔ Reference Temperature`

### DCIR

`Current Pulse → ΔV / ΔI`

## Safety

실제 Battery 연결 전 Bench Power Supply 기반 회로 검증 필수.

Battery Safety 기준: [`docs/safety.md`](../docs/safety.md)

## Definition of Done

* [ ] Voltage Measurement
* [ ] Current Measurement
* [ ] Temperature Measurement
* [ ] Measurement Calibration
* [ ] DCIR Measurement
* [ ] Protection Circuit
* [ ] Firmware Interface 검증
