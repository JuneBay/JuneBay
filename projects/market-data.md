# Market Data Systems — Stock Data Integration · Processing · Automation

<div align="center">
  <img src="../cards/market-data.jpg" alt="Market Data Systems — Stock Data Integration · Processing · Automation" width="100%">
</div>

*[← MACROBAY 메인으로 / Back to portfolio](../README.md)*

**Brokerage-API Data Integration · 2차 가공 · 실시간 대시보드 · 다중 알림 · 자동매매 미포함**

> 비슷한 작업 의뢰 가능합니다. 외주 문의는 [Upwork](https://www.upwork.com/freelancers/~01b49808a51af3b53c) · [Fiverr](https://www.fiverr.com/sellers/junebay) · [크몽](https://kmong.com/@JuneBay) · [위시켓](https://www.wishket.com/partners/p/somster/) 으로.

---

## 🎯 Overview

증권·금융 데이터를 **수집 → 2차 가공 → 실시간 대시보드·알림**까지 자동화하는 시스템을 만들어 드립니다. 25년+ 금융 실무 경험 기반으로, 비전문가도 쓰기 쉽게 설계합니다.

A system that **collects, processes, and surfaces** stock/financial data — from brokerage-API ingestion to real-time dashboards and multi-channel alerts. Built on 25+ years of finance-domain experience.

> ⚠️ **자동매매·투자판단·종목 추천은 포함하지 않습니다** — "사실 데이터·알림 only" 원칙으로 손실·법적 리스크를 회피합니다.
> No auto-trading, no investment advice, no stock recommendations — facts & alerts only.

---

## 🧩 What It Does

- **증권사 API 데이터 통합·수집 자동화** — 키움 등 REST/WebSocket, 계좌·종목·시장 영역
- **2차 가공(파생 지표)** — 정렬·합계·비중(%)·증감률 등 의미 있는 형태로 재가공
- **국내외 소스 통합** — 여러 데이터 소스를 하나의 정규화된 스냅샷으로
- **실시간 대시보드** — PC/모바일, 라이브 값 + 시계열 차트
- **다중 알림** — 텔레그램 · 슬랙 · 이메일 (사실 기반 트리거)
- **데이터 저장·자동 백업** — SQLite 캐싱 + 아카이빙(분석/검증용)

---

## 📊 At a Glance
| Aspect | Detail |
|--------|--------|
| **수집** | 증권사 API (REST/WebSocket) · 계좌·종목·시장 |
| **가공** | 파생 지표 2차 가공 (정렬·합계·비중·증감률) · 다중 소스 통합 |
| **표시** | 실시간 대시보드 (PC/모바일) · 시계열 차트 |
| **알림** | 텔레그램 · 슬랙 · 이메일 (사실 기반) |
| **저장** | SQLite + 자동 백업 |
| **범위 외** | 자동매매 · 투자판단 · 종목 추천 (의도적 미포함) |

---

## 🛠️ Technology Stack

- **Python** — 데이터 수집·가공 파이프라인, 비동기 처리
- **증권사 API** — 키움 REST + WebSocket (실시간 시세)
- **WebSocket** — 실시간 데이터 스트리밍
- **SQLite** — 데이터 캐싱 · 아카이빙 · 자동 백업
- **FastAPI / Flask** — API · 대시보드 백엔드
- **Telegram / Slack / SMTP** — 다중 알림 채널

---

## 💼 외주 문의 / Project Inquiries

**비슷한 프로젝트 의뢰 가능합니다 — Available for similar projects.**

### 이런 작업이면 처리해드릴 수 있습니다
- 증권사 API(키움 등) 데이터 수집·통합 자동화
- 시장·계좌·종목 데이터 2차 가공 + 리포트
- 실시간 대시보드 + 다중 알림(텔레그램·슬랙·이메일)
- 데이터 저장·아카이빙·자동 백업
- 비전문가도 쓰기 쉬운 운영 UI

### 진행 방식
1. 데이터 소스·조회 항목(TR)·환경·알림 채널 먼저 확인 (1~2일)
2. 1주 안에 1~2개 영역 시범 연동 + 대시보드 프로토타입
3. 검증 후 전체 확장 + 가공 + 알림 + 데이터 로깅
4. 운영 매뉴얼 + 인계 — 단순 코드가 아닌 **운영 가능한 시스템**으로

### 문의 채널
[![Upwork](https://img.shields.io/badge/Upwork-14A800?style=flat&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/~01b49808a51af3b53c)
[![Fiverr](https://img.shields.io/badge/Fiverr-1DBF73?style=flat&logo=fiverr&logoColor=white)](https://www.fiverr.com/sellers/junebay)
[![Kmong](https://img.shields.io/badge/크몽-FF6B35?style=flat)](https://kmong.com/@JuneBay)
[![Wishket](https://img.shields.io/badge/위시켓-3B6BFF?style=flat)](https://www.wishket.com/partners/p/somster/)
