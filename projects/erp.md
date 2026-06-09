# ERP & Business Systems — Build · Integrate · Automate

<div align="center">
  <img src="../cards/erp.jpg" alt="ERP & Business Systems — Build · Integrate · Automate" width="100%">
</div>

*[← MACROBAY 메인으로 / Back to portfolio](../README.md)*

**Custom Operational ERP · AI Procurement Agent · Zero-Loss System Integration**

> 비슷한 작업 의뢰 가능합니다. 외주 문의는 [Upwork](https://www.upwork.com/freelancers/~01b49808a51af3b53c) · [Fiverr](https://www.fiverr.com/sellers/junebay) · [크몽](https://kmong.com/@JuneBay) · [위시켓](https://www.wishket.com/partners/p/somster/) 으로.

---

## 🎯 Overview

세 가지 축으로 기업의 운영 시스템을 다룹니다 — **직접 구축(Build)**, **AI 자동화(Automate)**, **시스템 연동(Integrate)**. 비전문가 사장님도 "엑셀처럼 쉽게" 쓰는 것을 1순위로, **이론적 완벽함보다 현실 운영 가능성**을 기준으로 설계합니다.

Three pillars for business operations — **Build** a custom ERP, **Automate** the back-office with AI agents, and **Integrate** existing tools without data loss. Designed for non-technical owners ("as easy as Excel") with operational sustainability over theoretical perfection.

---

## 🧱 Pillar 1 — Build: 맞춤형 운영 ERP

기성 ERP(이카운트 등)로 안 맞던 다브랜드 수입·유통 비즈니스를 위한 **단일 웹 ERP** — 입고 → 재고 → 판매 → 정산 전 과정. *(현재 진행 중인 실 구축 프로젝트, 일반화하여 소개)*

- **단일 재고 원장** — SKU × 지점 × 상태(일반/전시/샘플) 통합
- **다브랜드 · 다채널 · 다지점** 가격·정산 규칙
- **상품 마스터 자동 채번** — 브랜드 접두 + 모델 + 컬러 규칙, 기존 코드 재사용, 중복 해소 (수백 SKU 자동 매칭)
- **바코드 입고 + 1회 실사 리베이스** + 채널별 주문·정산·마진 리포트
- **파일 변경 감시 → 팀 알림** (Google Drive 공유 폴더 → Telegram)

---

## 🤖 Pillar 2 — Automate: ERP 구매·정산 AI 에이전트

ERP 백오피스의 반복 업무(구매 마감·대사·세금계산서 등록)를 대화형 AI 에이전트로 자동화. *(동작하는 PoC — 가상 ERP + MSSQL 연동 설계 기준)*

- **대화형 인텐트 → 툴 라우팅** — OpenAI function calling 4툴(마감 집계 / 거래처 메일 / 대사 / 월간 리포트), API 키 없이도 도는 **규칙기반 폴백(Mock 모드)**
- **거래처 회신 검증** — 불일치(금액·수량) 자동 탐지
- **Staging-Table 무결성 패턴** — AI는 staging 테이블에만 기록 → **사람 승인** → 트랜잭션 배치 커밋 + 롤백. ERP 본 데이터는 사람이 승인한 것만 들어감
- **월마감 리포트 자동 생성** (Excel · PPT)
- 대상 ERP: MSSQL 기반(예: UNIERP) 읽기 + staging 설계

---

## 🔗 Pillar 3 — Integrate: 무손실 시스템 연동

서로 다른 커머스·ERP 솔루션 사이 데이터 동기화 — **전송 실패 시에도 단 한 건도 잃지 않는 것**이 핵심. *(동작하는 PoC)*

- **무손실 실패 원장** — 전송 실패 시 원본 payload + 사유를 영구 저장, 버튼 한 번으로 재시도
- **주문번호 UNIQUE → 중복 전송 차단**
- **코드 매핑 사전 점검** → 미매핑 건 "보류" 처리
- **실패 건 Excel/CSV 내보내기** → 수동 업로드 대비
- **스케줄러 ON/OFF** (일 1~2회 자동 동기화) · 로컬 전용 PC 운영 옵션(클라우드 불요)
- 예: 커머스 플랫폼(이지어드민 등) → ERP(이카운트 등) 판매·반품 전표 동기화

---

## 📊 At a Glance
| Aspect | Detail |
|--------|--------|
| **Build** | 다브랜드 수입·유통 웹 ERP (입고→재고→판매→정산), 상품마스터 자동채번, 바코드 실사 |
| **Automate** | 구매·정산 AI 에이전트 — function calling + 규칙 폴백, staging-table 무결성, 메일·대사·리포트 |
| **Integrate** | 커머스↔ERP 무손실 동기화 — 실패 원장·중복차단·재시도·Excel export |
| **Stack** | Python · FastAPI · MSSQL/PostgreSQL · SQLite · OpenAI(function calling) · LangGraph · openpyxl · python-pptx · APScheduler · Telegram |
| **Deploy** | Railway · Render · 로컬 전용 PC 옵션 · HTTP Basic Auth + rate limit + 보안 헤더 |

---

## 🛠️ Technology Stack

- **Backend** — Python 3.11 · FastAPI · Uvicorn · Pydantic v2
- **AI** — OpenAI GPT-4o-mini function calling (인텐트→툴), 규칙기반 폴백, (설계) LangGraph 조건부 라우팅 + GPT-4o Vision 세금계산서 파싱
- **DB** — MSSQL(pyodbc) · PostgreSQL · SQLite (가상 ERP/스테이징)
- **문서** — openpyxl(Excel) · python-pptx(PPT 리포트)
- **스케줄/연동** — APScheduler · SMTP(거래처 메일) · Telegram Bot
- **배포/보안** — Railway · Render.com · HTTP Basic Auth · per-IP rate limit · CORS allowlist · 보안 헤더 · OpenAPI docs 비활성

---

## 💼 외주 문의 / Project Inquiries

**비슷한 프로젝트 의뢰 가능합니다 — Available for similar projects.**

### 이런 작업이면 처리해드릴 수 있습니다
- 기성 ERP가 안 맞는 비즈니스용 **맞춤형 웹 ERP** (재고·판매·정산·다지점)
- **ERP 백오피스 자동화** (구매 마감·대사·세금계산서·리포트) — AI 에이전트 또는 규칙기반
- **솔루션 간 데이터 연동/마이그레이션** (커머스 ↔ ERP, 무손실 보장)
- 엑셀 업무의 시스템화 · 바코드/재고 실사 · 채널별 정산
- 비전문가도 쓰기 쉬운 운영 UI

### 진행 방식
1. 현재 업무 흐름·데이터·연동 대상(ERP/커머스 API) 먼저 확인 (1~2일)
2. 1주 안에 핵심 1개 흐름 시범 구현 + 화면 프로토타입
3. 검증 후 전체 확장 + 자동화 + 데이터 마이그레이션
4. 운영 매뉴얼 + 인계 — 단순 코드가 아닌 **운영 가능한 시스템**으로

### 문의 채널
[![Upwork](https://img.shields.io/badge/Upwork-14A800?style=flat&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/~01b49808a51af3b53c)
[![Fiverr](https://img.shields.io/badge/Fiverr-1DBF73?style=flat&logo=fiverr&logoColor=white)](https://www.fiverr.com/sellers/junebay)
[![Kmong](https://img.shields.io/badge/크몽-FF6B35?style=flat)](https://kmong.com/@JuneBay)
[![Wishket](https://img.shields.io/badge/위시켓-3B6BFF?style=flat)](https://www.wishket.com/partners/p/somster/)
