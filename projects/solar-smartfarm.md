# Solar Smart-Farm — RS485/Modbus Monitoring & Control System

<div align="center">
  <img src="../cards/solar-smartfarm.jpg" alt="Solar Smart-Farm — RS485/Modbus Monitoring & Control" width="100%">
</div>

*[← MACROBAY 메인으로 / Back to portfolio](../README.md)*

**라즈베리파이 게이트웨이 · 6개 장치 RS485/Modbus 버스 · 태양광(MPPT)+DC-DC 전원 · 실시간 Firebase 대시보드 · 릴레이 제어 · 원격 관리**
**Raspberry Pi Gateway · 6-Device RS485/Modbus Bus · Solar (MPPT) + DC-DC Power · Real-time Firebase Dashboard · Relay Control · Remote-Managed**

> 비슷한 작업 의뢰 가능합니다 — Available for similar projects.
> 문의: [Upwork](https://www.upwork.com/freelancers/~01b49808a51af3b53c) · [Fiverr](https://www.fiverr.com/sellers/junebay) · [크몽](https://kmong.com/@JuneBay) · [위시켓](https://www.wishket.com/partners/p/somster/)

---

## 🎯 프로젝트 개요 / Project Overview

**[KR]** **라즈베리파이 게이트웨이**를 중심으로 구축한 턴키 **스마트팜 모니터링·제어 시스템**입니다. 게이트웨이는 **6개 장치로 구성된 RS485/Modbus 버스**를 폴링하고, 측정값을 60초마다 **Firebase Realtime Database**로 전송하며, 수동 + 규칙 기반 **릴레이 제어**, 시계열 차트, CSV 내보내기를 갖춘 **반응형 실시간 웹 대시보드**를 제공합니다. 현장은 **태양광 전원**으로 운영되므로, 환경 센서와 함께 **MPPT 충전 컨트롤러**와 **DC-DC 컨버터**도 모니터링합니다. 전체 장비는 **원격으로** 관리되어, 설치 이후 현장 방문이 전혀 필요하지 않습니다.

**[EN]** A turnkey **smart-farm monitoring & control system** built around a **Raspberry Pi gateway** that polls a **6-device RS485/Modbus bus**, pushes readings to **Firebase Realtime Database** every 60 seconds, and serves a **responsive real-time web dashboard** with manual + rule-based **relay control**, time-series charts, and CSV export. The site runs off **solar power**, so an **MPPT charge controller** and **DC-DC converter** are monitored alongside the environmental sensors. The entire unit is managed **remotely** — zero on-site visits required after install.

### 주요 기능 / Key Features

**[KR]**
- **2개 시리얼 포트에 6개 RS485/Modbus 장치** — 깔끔한 주소 체계, 버스 충돌 없음
- **태양광 전원 모니터링** — MPPT 충전 컨트롤러(PV 전압 / 전류 / 상태) + DC-DC 컨버터(입력/출력/전류)
- **3상 양방향 전력계** (Modbus-RTU)
- **환경 센싱** — RS485 온습도 2개 + IP68 방수 조도 센서 (0–200,000 lx)
- **3채널 릴레이 제어** — 수동 토글 + 자동 규칙 (시간 / 온도 / 습도, 3조건 AND)
- **실시간 대시보드** — PC/모바일 반응형, 실시간 값, 시계열 차트 4종, CSV 내보내기, 시스템 헬스 패널
- **원격 관리** — 현장 방문 없이 유지보수·설정·업데이트를 위한 보안 원격 접속

**[EN]**
- **6 RS485/Modbus devices on 2 serial ports** — clean addressing, no bus contention
- **Solar power monitoring** — MPPT charge controller (PV voltage / current / status) + DC-DC converter (in/out/current)
- **3-phase bidirectional power meter** (Modbus-RTU)
- **Environmental sensing** — 2× RS485 temperature/humidity + IP68 waterproof lux sensor (0–200,000 lx)
- **3-channel relay control** — manual toggle + automated rules (time / temperature / humidity, 3-condition AND)
- **Real-time dashboard** — PC/mobile responsive, live values, 4 time-series charts, CSV export, system-health panel
- **Remote management** — secure remote access for maintenance, config, and updates without site visits

---

## 🏗️ 동작 원리 / How It Works

<div align="center">
  <img src="../cards/arch/solar-smartfarm_arch.jpg" alt="How it works — Solar + Sensors → Smart Gateway → Real-time Cloud → Monitor & Control" width="100%">
</div>

**[KR]** 태양광으로 구동되는 현장 센서들이 소형 온사이트 **게이트웨이**로 데이터를 보내면, 게이트웨이는 정해진 주기로 이를 읽어 자동 규칙을 적용하고 모든 데이터를 **실시간 클라우드**로 전송합니다. 거기서부터 웹 **대시보드**를 통해 운영자가 어디서든 현장을 모니터링하고 제어할 수 있습니다 — 완전 원격, 현장 방문 없음.

**[EN]** Solar-powered field sensors feed a small on-site **gateway**, which reads them on a fixed cycle, applies automatic rules, and pushes everything to a **real-time cloud**. From there a web **dashboard** lets the operator monitor and control the site from anywhere — fully remote, no site visits.

**[KR] 안정적 버스 설계:** 트래픽이 많은 전원 소스를 별도 시리얼 라인에 두어 센서 버스와 격리했습니다. 두 버스가 절대 충돌하지 않아 폴링 신뢰성이 유지됩니다.

**[EN] Stable bus design:** the high-traffic power source sits on its own serial line, isolated from the sensor bus, so the two never contend — keeping polling reliable.

---

## 🔧 해결한 기술 과제 / Solved Technical Challenges

### 1. 다중 장치 RS485/Modbus 통합 / Multi-Device RS485/Modbus Integration

**[KR]**
**과제**: 레지스터 맵, 통신 속도(baud rate), 주소가 서로 다른 6개의 이기종 Modbus 장치(MPPT, DC-DC, 3상 전력계, 온습도 ×2, 조도)를 공유 버스에서 운용.
**해결**: 2포트 토폴로지 + 장치별 주소 할당 + 각 장치의 레지스터를 단일 정규화 스냅샷으로 매핑하는 통합 Modbus 리더.
**결과**: 버스 충돌 없이 전 장치 60초 폴링 안정 동작.

**[EN]**
**Challenge**: Six heterogeneous Modbus devices (MPPT, DC-DC, 3-phase meter, temp/humidity ×2, lux) with different register maps, baud rates, and addresses on a shared bus.
**Solution**: Two-port topology + per-device address assignment + a unified Modbus reader that maps each device's registers into a single normalized snapshot.
**Result**: Stable 60-second polling of all devices with no bus collisions.

### 2. 태양광 / 오프그리드 전원 모니터링 / Solar / Off-Grid Power Monitoring

**[KR]**
**과제**: 장비가 태양광으로 구동되므로, 작물 센서와 함께 전원 가용성 및 배터리/충전 상태가 보여야 함.
**해결**: MPPT 충전 컨트롤러(PV 전압, 전류, 상태)와 DC-DC 컨버터(입력/출력/전류)를 Modbus로 읽어 대시보드에 표시.
**결과**: 운영자가 발전량과 부하를 한눈에 확인 — 오프그리드 환경에서 전원 문제 조기 경보.

**[EN]**
**Challenge**: The unit runs on solar, so power availability and battery/charge state must be visible alongside the crop sensors.
**Solution**: Read the MPPT charge controller (PV voltage, current, status) and DC-DC converter (in/out/current) over Modbus and surface them on the dashboard.
**Result**: Operators can see generation and load at a glance — early warning for power issues in an off-grid setup.

### 3. 3상 양방향 전력 계측 / 3-Phase Bidirectional Power Metering

**[KR]**
**과제**: 3상 Modbus-RTU 전력계는 단상 장치와 레지스터 레이아웃이 다름.
**해결**: 3상 전력계 전용 레지스터 맵과 디코딩을 동일 폴링 루프에 통합.
**결과**: 나머지 텔레메트리와 통합된 정확한 에너지 측정값.

**[EN]**
**Challenge**: 3-phase Modbus-RTU power meters use a different register layout from single-phase units.
**Solution**: Dedicated register map and decoding for the 3-phase meter, integrated into the same polling loop.
**Result**: Accurate energy readings unified with the rest of the telemetry.

### 4. 제어 기능을 갖춘 실시간 대시보드 / Real-Time Dashboard with Control

**[KR]**
**과제**: 실시간 데이터를 보여주는 동시에, 운영자가 어디서든 릴레이 제어 / 자동 규칙 변경을 할 수 있어야 함.
**해결**: Firebase Realtime DB를 실시간 채널로 사용 — Pi가 `/latest`에 기록하고 대시보드가 구독; 릴레이 토글과 자동 설정은 `/settings`에 다시 기록되어 Pi가 적용.
**결과**: 모바일을 포함해 개방형 웹에서 양방향 실시간 모니터링 + 제어.

**[EN]**
**Challenge**: Show live data AND let the operator control relays / change auto-rules from anywhere.
**Solution**: Firebase Realtime DB as the live channel — Pi writes `/latest`, dashboard subscribes; relay toggles and auto-settings write back to `/settings`, which the Pi applies.
**Result**: Bi-directional real-time monitoring + control over the open web, mobile included.

### 5. 규칙 기반 자동화 / Rule-Based Automation

**[KR]**
**과제**: 릴레이가 환경에 따라 자동으로 전환되되, 수동 오버라이드도 가능해야 함.
**해결**: 3조건(시간대 AND 온도 AND 습도) 자동 제어, 채널별 자동/수동 모드.
**결과**: 필요 시 오버라이드가 가능한 무인 운영.

**[EN]**
**Challenge**: Relays must switch automatically by environment, with manual override.
**Solution**: 3-condition (time window AND temperature AND humidity) auto-control with per-channel auto/manual modes.
**Result**: Hands-off operation with override when needed.

### 6. 원격, 무방문 유지보수 / Remote, Zero-Visit Maintenance

**[KR]**
**과제**: 현장 장비의 설정 변경, 수정, 표시 조정을 현장 방문 없이 처리해야 함.
**해결**: Pi에 대한 보안 원격 접속 + 클라우드 호스팅 대시보드; 권한 복구, 포맷 변경, 업데이트 모두 원격 처리.
**결과**: 현장 방문 없이 당일 이슈 해결.

**[EN]**
**Challenge**: Field unit needs config changes, fixes, and display tweaks without driving to site.
**Solution**: Secure remote access to the Pi + cloud-hosted dashboard; permission restores, format changes, and updates all done remotely.
**Result**: Issues resolved same-day without a site visit.

---

## 📊 한눈에 보기 / At a Glance
| 항목 / Aspect | 내용 / Detail |
|--------|--------|
| **게이트웨이 / Gateway** | 라즈베리파이 · Python · systemd 서비스 · 60초 루프 / Raspberry Pi · Python · systemd service · 60s loop |
| **필드 버스 / Field bus** | RS485 / Modbus-RTU · 6개 장치 · 2개 시리얼 포트 / RS485 / Modbus-RTU · 6 devices · 2 serial ports |
| **전원 / Power** | 태양광 MPPT 충전 컨트롤러 + DC-DC 컨버터 (오프그리드) / Solar MPPT charge controller + DC-DC converter (off-grid) |
| **계측 / Metering** | 3상 양방향 Modbus-RTU 전력계 / 3-phase bidirectional Modbus-RTU power meter |
| **센서 / Sensors** | RS485 온습도 ×2 · IP68 조도 (0–200,000 lx) / 2× RS485 temp/humidity · IP68 lux (0–200,000 lx) |
| **제어 / Control** | 3채널 릴레이 · 수동 + 3조건 자동 규칙 / 3-channel relay · manual + 3-condition auto-rules |
| **클라우드 / Cloud** | Firebase Realtime DB + Hosting |
| **대시보드 / Dashboard** | 반응형 웹 · 실시간 카드 · 시계열 차트 4종 · CSV 내보내기 · 시스템 헬스 / Responsive web · live cards · 4 time-series charts · CSV export · system health |
| **운영 / Ops** | 원격 관리 · 현장 방문 제로 / Remote-managed · zero on-site visits |

---

## 🛠️ 기술 스택 / Technology Stack

### 하드웨어 / 현장 / Hardware / Field

**[KR]**
- **라즈베리파이** — 엣지 게이트웨이
- **RS485 / Modbus-RTU** — 현장 장치 버스 (USB-RS485 포트 2개)
- **MPPT 태양광 충전 컨트롤러**, **DC-DC 컨버터** — 오프그리드 전원
- **3상 양방향 전력계** (Modbus-RTU)
- **RS485 온습도 ×2**, **IP68 조도 센서**
- **GPIO 릴레이 모듈** (3채널 사용)

**[EN]**
- **Raspberry Pi** — edge gateway
- **RS485 / Modbus-RTU** — field device bus (2× USB-RS485 ports)
- **MPPT solar charge controller**, **DC-DC converter** — off-grid power
- **3-phase bidirectional power meter** (Modbus-RTU)
- **RS485 temp/humidity ×2**, **IP68 lux sensor**
- **GPIO relay module** (3 channels used)

### 소프트웨어 / Software

**[KR]**
- **Python** — `pymodbus` 폴링, `gpiozero` 릴레이 제어, 자동 제어 로직
- **Firebase Realtime Database** — 실시간 텔레메트리 + 설정 채널
- **Firebase Hosting** — 대시보드 전송
- **Chart.js** — 시계열 시각화
- **반응형 HTML/CSS/JS** — PC + 모바일 대시보드
- **systemd** — 복원력 있는 상시 동작 서비스
- **보안 원격 접속** — 무방문 유지보수

**[EN]**
- **Python** — `pymodbus` polling, `gpiozero` relay control, auto-control logic
- **Firebase Realtime Database** — live telemetry + settings channel
- **Firebase Hosting** — dashboard delivery
- **Chart.js** — time-series visualization
- **Responsive HTML/CSS/JS** — PC + mobile dashboard
- **systemd** — resilient always-on service
- **Secure remote access** — zero-visit maintenance

---

## 🚀 실제 사용 사례 / Real-World Usage

**[KR]** **태양광 구동 스마트팜 현장**에 배포되어 단계적으로 커미셔닝되었습니다 — 게이트웨이가 클라우드 대시보드로 실시간 측정값을 전송하는 동안, 현장 장치는 운영자 일정에 맞춰 순차적으로 온라인 연결됩니다. 모든 튜닝, 수정, 설정 변경은 단 한 번의 현장 방문 없이 **원격으로 당일** 처리됩니다(대시보드 조정, 데이터 로깅 조정, 접속 복구). 하드웨어는 표준 기성품 RS485/Modbus 장비를 사용하여, 비용과 유지보수성을 현실적으로 유지합니다.

**[EN]** Deployed at a **solar-powered smart-farm site** and commissioned in phases — the gateway pushes live readings to the cloud dashboard while field devices are brought online on the operator's own schedule. All tuning, fixes, and configuration changes are handled **remotely and same-day** (dashboard adjustments, data-logging tweaks, access restoration) without a single site visit. Hardware is standard off-the-shelf RS485/Modbus equipment, keeping cost and serviceability practical.

---

## 💼 외주 문의 / Project Inquiries

**비슷한 프로젝트 의뢰 가능합니다 — Available for similar projects.**

### 이런 작업이면 처리해드릴 수 있습니다 / What I can take on
- RS485 / Modbus-RTU 다중 장치 통합 (센서·전력계·인버터·MPPT·DC-DC 등) / RS485 / Modbus-RTU multi-device integration (sensors, meters, inverters, MPPT, DC-DC, etc.)
- 라즈베리파이 / 산업용 게이트웨이 기반 데이터 수집·제어 / Raspberry Pi / industrial gateway-based data acquisition & control
- 태양광·오프그리드 전원 모니터링 (MPPT·배터리·부하) / Solar & off-grid power monitoring (MPPT, battery, load)
- 실시간 웹 대시보드 + 릴레이 원격 제어 + 자동 제어 규칙 / Real-time web dashboard + remote relay control + auto-control rules
- 클라우드 연동 (Firebase 등) + CSV 데이터 로깅 / Cloud integration (Firebase, etc.) + CSV data logging
- 스마트팜 / 환경 모니터링 / 양식장 / 수처리 / 설비 모니터링 / Smart-farm / environmental monitoring / aquaculture / water treatment / facility monitoring
- 비대면 원격 설치 안내 + 유지보수 / Remote install guidance + maintenance

### 진행 방식 / How it works
1. 측정 대상·장치(Modbus 맵)·환경·통신 채널 먼저 확인 (1~2일) / Confirm measurement targets, devices (Modbus map), environment, and comms channels first (1–2 days)
2. 1주 안에 1~2개 장치 시범 연동 + 대시보드 프로토타입 / 1–2 device pilot integration + dashboard prototype within a week
3. 검증 후 전체 장치 확장 + 자동 제어 + 데이터 로깅 / Expand to all devices + auto-control + data logging after validation
4. 운영 매뉴얼 + 원격 유지보수 절차 함께 인계 / Handover with operations manual + remote maintenance procedures

### 문의 채널 / Contact
[![Upwork](https://img.shields.io/badge/Upwork-14A800?style=flat&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/~01b49808a51af3b53c)
[![Fiverr](https://img.shields.io/badge/Fiverr-1DBF73?style=flat&logo=fiverr&logoColor=white)](https://www.fiverr.com/sellers/junebay)
[![Kmong](https://img.shields.io/badge/크몽-FF6B35?style=flat)](https://kmong.com/@JuneBay)
[![Wishket](https://img.shields.io/badge/위시켓-3B6BFF?style=flat)](https://www.wishket.com/partners/p/somster/)
