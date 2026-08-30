# Battery Safety

## Principle

Li-ion Battery 연결 전 회로 및 Firmware 검증 필수.

**Battery Datasheet / Component Rating / Lab Safety Rule 우선 적용**

---

# Before Battery Connection

* [ ] Schematic Review
* [ ] Short Circuit 확인
* [ ] Power Supply 기반 회로 Test
* [ ] Voltage Measurement 검증
* [ ] Current Measurement 검증
* [ ] Current Limit 설정
* [ ] Protection Logic 확인
* [ ] Battery Polarity 확인

---

# Initial Test

실제 Battery 대신 Bench Power Supply 사용.

```text
Bench Power Supply
        ↓
Measurement Circuit
        ↓
INA228 / STM32
        ↓
Reference Measurement
```

정상 동작 확인 후 Battery 연결.

---

# Battery Handling

* Battery Polarity 확인
* Short Circuit 방지
* 허용 Voltage 초과 금지
* 허용 Current 초과 금지
* 허용 Temperature 초과 금지
* 손상 Cell 사용 금지
* 충전 중 무인 방치 금지

세부 Limit → Samsung INR18650-30Q 공식 Datasheet 기준

---

# Charge / Discharge Test

* Current Limit 설정
* Voltage Limit 설정
* Temperature Monitoring
* Emergency Stop 준비
* Protection Circuit 활성화

---

# Fault Conditions

* Over Voltage
* Under Voltage
* Over Current
* Over Temperature
* Communication Failure
* Sensor Failure

Fault 발생 시 Charge / Discharge 중단 우선.

---

# Hardware Modification

Battery 연결 상태에서 회로 수정 금지.

순서:

`Power OFF → Battery Disconnect → Circuit Modification → Verification → Reconnect`

---

# First Battery Test

최초 Battery Test → Electrical Team Leader 또는 운영진 확인 후 진행
