# Hardware Specification

## Battery

**Model:** Samsung INR18650-30Q
**Type:** Li-ion 18650

세부 전압 / 전류 / 온도 기준 → 공식 Datasheet 기준 적용

## Voltage / Current Monitor

**Device:** INA228AIDGSR

### Role

* Bus Voltage Measurement
* Shunt Voltage Measurement
* Current Measurement

### Interface

`INA228 ↔ I²C ↔ STM32`

## Temperature

**Sensor:** External NTC Thermistor

### Role

* Cell Surface Temperature Measurement
* Over-Temperature Detection

### Interface

`NTC → Voltage Divider → STM32 ADC`

## MCU

**Device:** STM32G031K8T6

### Role

* Sensor Communication
* Measurement Processing
* SOC
* Fault Detection
* SOH Feature Extraction
* FPGA Communication
* OLED Control

## FPGA

**Board:** Digilent Cora Z7-07S
**Device:** Xilinx Zynq-7000 XC7Z007S

### Role

* Fixed-Point MLP
* SOH Hardware Inference

## Display

**Device:** 0.96" I²C OLED

### Output

* Voltage
* Current
* Temperature
* SOC
* SOH
* State

## Communication

### INA228 ↔ STM32

`I²C`

### OLED ↔ STM32

`I²C`

### STM32 ↔ FPGA

`UART`

## Additional Hardware

* Shunt Resistor
* Protection Circuit
* Charge Path
* Discharge Path / Electronic Load

최종 Component 및 Rating → Electrical Design 완료 후 확정
