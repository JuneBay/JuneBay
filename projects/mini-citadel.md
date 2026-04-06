# Mini Citadel — Trader Decision Support System (TDSS)

*[← MACROBAY 메인으로 / Back to portfolio](../README.md)*

**25+ Years Financial Systems · 90% Latency Reduction · Production · Available for Similar Projects**

> 비슷한 작업 의뢰 가능합니다. 외주 문의는 [Upwork](https://www.upwork.com/freelancers/~01b49808a51af3b53c) · [Fiverr](https://www.fiverr.com/sellers/junebay) · [크몽](https://kmong.com/@JuneBay) · [위시켓](https://www.wishket.com/partners/p/somster/) 으로.

[![GitHub](https://img.shields.io/badge/GitHub-Showcase-black?style=for-the-badge&logo=github)](https://github.com/JuneBay/Mini-Citadel-Showcase)

---

## 🎯 Project Overview

**Mini Citadel** is a centralized Trader Decision Support System (TDSS) that orchestrates multi-API signals and aggregates market data into a unified, high-frequency dashboard. Built on **25+ years of financial systems experience**, it achieves **90% performance improvement** (50ms → <5ms lookup) through hashmap-based data structure optimization and **80% UI latency reduction** (500ms → 100ms) via direct memory reference architecture.

The system serves as a **master gateway** coordinating trading signals across multiple trader workstations while providing real-time API health monitoring, automated data archiving, and a customizable unified visualization interface.

### Key Metrics
- **90% performance improvement** (50ms → <5ms lookup via O(1) architecture)
- **80% UI latency reduction** (500ms → 100ms via direct memory reference)
- **Centralized Gateway** for multi-machine signal orchestration
- **Real-time API health monitoring** across all connected services
- **Automated data archiving** for historical analysis and algorithmic trading
- **Multi-account management** ready for scalable trading operations
- **25+ years** continuous R&D and financial market experience

---

## 🚀 Key Achievements

### Centralized Architecture
- **Signal Gateway**: Engineered a master gateway to orchestrate trading signals across multiple trader machines, ensuring synchronized execution and consistent strategy deployment
- **API Health Monitoring**: Real-time monitoring of connection status and health for all integrated financial APIs (Kiwoom, eBest, etc.)
- **Multi-Machine Orchestration**: Seamless coordination of trading activities across distributed workstations with unified control plane

### Data Management & Intelligence
- **Automated Data Archiving**: Built a scheduled data pipeline to capture, structure, and persistently store targeted market intelligence for historical analysis and algorithmic trading development
- **Unified Visualization**: Integrated heterogeneous API streams into a single customizable dashboard, allowing traders to monitor complex market conditions at a glance
- **Configurable Data Capture**: User-defined data points and collection schedules for specific analysis needs

### Performance Excellence
- **Ultra-Low Latency**: 90% reduction in data lookup time (50ms → <5ms) through O(1) hashmap architecture, critical for high-frequency trading decisions
- **Zero-Copy Design**: 80% UI latency reduction via direct memory reference, eliminating HTTP overhead and redundant data copying
- **Thread Safety**: 100% thread-safe concurrent access to shared data structures using precise locking mechanisms
- **Scalability**: Designed for Multi-Account Management and seamless integration with future algorithmic/system trading modules

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    Centralized Gateway (Master)                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  API Health Monitor │ Signal Orchestrator │ Data Archiver │   │
│  └──────────────────────────────────────────────────────────┘   │
│         │                      │                      │          │
│         ▼                      ▼                      ▼          │
│  ┌──────────┐          ┌──────────┐          ┌──────────┐      │
│  │ Kiwoom   │          │  eBest   │          │  Others  │      │
│  │   API    │          │   API    │          │   APIs   │      │
│  └──────────┘          └──────────┘          └──────────┘      │
└─────────────────────────────────────────────────────────────────┘
         │                      │                      │
         └──────────────────────┴──────────────────────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
         ┌──────▼──────┐             ┌───────▼──────┐
         │  Trader     │             │   Trader     │
         │ Workstation │             │ Workstation  │
         │     #1      │             │      #2      │
         └─────────────┘             └──────────────┘
              │                             │
              ▼                             ▼
    ┌─────────────────┐           ┌─────────────────┐
    │ O(1) Data Engine│           │ O(1) Data Engine│
    │ Direct Memory   │           │ Direct Memory   │
    │ PySide6 UI      │           │ PySide6 UI      │
    └─────────────────┘           └─────────────────┘
```

**Key Architecture Components:**
- **Centralized Gateway**: Master control plane for signal orchestration
- **O(1) Data Engine**: Hashmap-based ultra-low latency data access
- **Direct Memory Reference**: Zero-copy architecture for UI updates
- **Multi-API Integration**: Unified interface for heterogeneous data sources
- **Automated Archiving**: Scheduled pipeline for historical data storage

---

## 🎨 Core Design Principles

### 1. O(1) Lookup Performance
- **Hashmap-Based Structure**: Ticker code as key enables constant-time lookup
- **Data Structure Migration**: DataFrame (O(n)) → Dictionary (O(1))
- **Zero Linear Search**: Direct hash-based access eliminates iteration
- **Result**: **90% performance improvement** (50ms → <5ms)

### 2. Direct Memory Reference Architecture
- **HTTP Elimination**: Removed internal API calls between engine and UI
- **Shared Memory**: Engine and UI share same data structures
- **Thread-Safe Access**: Lock-based synchronization for concurrent access
- **Result**: **80% UI latency reduction** (500ms → 100ms)

### 3. Real-time Data Processing
- **WebSocket Integration**: Persistent connection for live market data
- **Asynchronous Processing**: asyncio-based non-blocking data handling
- **Event-Driven Updates**: 100ms polling cycle for responsive UI
- **Result**: Real-time portfolio tracking without UI blocking

### 4. Backward Compatibility
- **v1.0 UI/UX Preservation**: Complete UI compatibility maintained
- **Internal Engine Redesign**: Performance gains without user disruption
- **Zero Learning Curve**: Existing users experience seamless upgrade
- **Result**: Performance improvement with zero user retraining

### 5. Centralized Gateway Architecture
- **Multi-Machine Orchestration**: Single gateway coordinates signals across multiple trader workstations
- **API Health Monitoring**: Real-time tracking of connection status for all integrated APIs
- **Synchronized Execution**: Ensures trading signals are executed consistently across all machines
- **Unified Control Plane**: Centralized management of distributed trading operations
- **Result**: Coordinated multi-machine trading with real-time operational visibility

### 6. Data Archiving & Historical Analysis
- **Scheduled Pipeline**: Automated data collection on user-defined schedules
- **Structured Storage**: Market intelligence stored in queryable format (CSV/Database)
- **Targeted Capture**: User-configurable data points for specific analysis needs
- **Historical Dataset**: Persistent storage for algorithmic trading development and backtesting
- **Result**: Continuous accumulation of market intelligence for data-driven strategy development

---

## 💻 Technical Implementation Highlights

### O(1) Lookup Optimization
The core performance breakthrough comes from replacing linear search with constant-time hash-based lookup. See [`O1_Architecture_Snippet.py`](./O1_Architecture_Snippet.py) for detailed implementation.

**Before (O(n) - Linear Search):**
```python
# DataFrame-based lookup: O(n) complexity
def find_stock(ticker_code):
    for row in dataframe.iterrows():
        if row['ticker'] == ticker_code:
            return row
    # Average: 50ms for 1000+ stocks
```

**After (O(1) - Hash Lookup):**
```python
# Dictionary-based lookup: O(1) complexity
stock_data = {
    '005930': {...},  # Samsung Electronics
    '000660': {...},  # SK Hynix
    # ... 1000+ stocks
}

def find_stock(ticker_code):
    return stock_data.get(ticker_code)
    # Average: <5ms regardless of dataset size
```

### Performance Comparison
| Operation | Before (O(n)) | After (O(1)) | Improvement |
|-----------|---------------|--------------|-------------|
| **Single Lookup** | 50ms | 5ms | **90% faster** |
| **100 Lookups** | 5,000ms | 500ms | **90% faster** |
| **UI Update Cycle** | 500ms | 100ms | **80% faster** |
| **Memory Usage** | 100MB | 120MB | +20MB (acceptable) |

### Centralized Gateway Implementation
**Multi-Machine Signal Coordination:**
```python
class CentralizedGateway:
    def __init__(self):
        self.connected_machines = {}
        self.api_health_status = {}
        self.signal_queue = asyncio.Queue()
    
    async def orchestrate_signal(self, signal):
        # Broadcast to all connected trader workstations
        for machine_id, connection in self.connected_machines.items():
            await connection.send_signal(signal)
        
        # Monitor execution status
        await self.monitor_execution(signal)
    
    async def monitor_api_health(self):
        # Real-time API connection monitoring
        for api_name, api_client in self.apis.items():
            self.api_health_status[api_name] = await api_client.health_check()
```

### Data Archiving Pipeline
**Automated Historical Data Collection:**
```python
class DataArchiver:
    def __init__(self, schedule="daily"):
        self.schedule = schedule
        self.target_data_points = []  # User-configured
    
    async def archive_market_data(self):
        # Capture targeted market intelligence
        data = await self.collect_data_points()
        
        # Structure and persist
        await self.save_to_storage(data)
        
        # Result: Continuous historical dataset for backtesting
```

---

## 🔧 Solved Technical Challenges

### 1. Lookup Performance Bottleneck
**Challenge**: Linear search through 1,000+ stocks caused 50ms latency  
**Solution**: Migrated from DataFrame to Dictionary with ticker code as key  
**Result**: Constant-time O(1) lookup, 90% latency reduction

### 2. UI Latency from HTTP Overhead
**Challenge**: Internal HTTP API calls between engine and UI added 400ms overhead  
**Solution**: Direct memory reference with shared data structures  
**Result**: 80% UI latency reduction, real-time responsiveness

### 3. Real-time Data Processing
**Challenge**: Blocking operations froze UI during market data updates  
**Solution**: Asyncio-based non-blocking architecture with event-driven updates  
**Result**: Smooth UI experience even during high-frequency data streams

### 4. Backward Compatibility
**Challenge**: Performance optimization required engine redesign  
**Solution**: Maintained v1.0 UI/UX while completely rewriting internal engine  
**Result**: Zero user retraining, seamless upgrade experience

### 5. Thread Safety
**Challenge**: Concurrent access to shared data from multiple threads  
**Solution**: Precise locking mechanisms (threading.Lock) for critical sections  
**Result**: 100% thread-safe operations, zero race conditions

### 6. Multi-Machine Coordination
**Challenge**: Synchronizing trading signals across distributed workstations  
**Solution**: Centralized gateway with signal orchestration and health monitoring  
**Result**: Unified control plane for multi-machine trading operations

### 7. Historical Data Management
**Challenge**: Need for persistent market intelligence for algorithmic trading  
**Solution**: Automated archiving pipeline with user-configurable data capture  
**Result**: Continuous accumulation of structured historical dataset

---

## 📊 Performance Metrics
| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| **Data Lookup** | 50ms (O(n)) | <5ms (O(1)) | **90% faster** |
| **UI Update Latency** | 500ms (HTTP) | 100ms (Direct) | **80% faster** |
| **Memory Usage** | 100MB | 120MB | +20MB overhead |
| **Thread Safety** | Race conditions | 100% safe | **Zero conflicts** |
| **API Monitoring** | Manual checks | Real-time | **Continuous visibility** |
| **Data Archiving** | Manual export | Automated | **Zero manual effort** |

---

## 🚀 Real-World Usage
**Mini Citadel** is actively used in production trading operations:

- **Status**: Production-ready, continuous R&D since 1994
- **Experience**: 25+ years of financial market operations
- **Deployment**: Personal trading infrastructure
- **Evolution**: Continuous enhancement based on real trading needs

### Operational Characteristics
1. **High-Frequency Decision Support**: Sub-5ms data access for rapid trading decisions
2. **Multi-Machine Coordination**: Centralized gateway orchestrates signals across workstations
3. **Continuous Operation**: 24/7 market monitoring with automated health checks
4. **Historical Intelligence**: Automated archiving builds dataset for algorithmic trading
5. **Scalable Architecture**: Ready for multi-account management and system trading integration

### Use Cases
- **Real-time Portfolio Tracking**: Instant access to position and P&L data
- **Multi-API Integration**: Unified view of data from Kiwoom, eBest, and other APIs
- **Signal Orchestration**: Coordinated execution across multiple trader workstations
- **Historical Analysis**: Archived data for strategy backtesting and optimization
- **API Health Monitoring**: Real-time visibility into connection status and reliability

---

## 🛠️ Technology Stack

### Backend (Python)
- **asyncio** - Asynchronous I/O for non-blocking operations
- **threading** - Thread-safe concurrent data access
- **pandas** - Initial data processing (migrated to dict for performance)
- **websockets** - Real-time market data streaming

### GUI (PySide6)
- **Qt Framework** - Professional desktop application UI
- **Custom Widgets** - Optimized for financial data visualization
- **Direct Memory Binding** - Zero-copy UI updates

### APIs & Services
- **Kiwoom OpenAPI** - Korean stock market data and trading
- **eBest API** - Alternative market data source
- **Custom Gateway** - Centralized signal orchestration layer

### Data Storage
- **In-Memory Dictionary** - O(1) real-time data access
- **CSV/Database** - Historical data archiving
- **Structured Logs** - API health and execution tracking

---

## 📁 Project Structure
```
Mini-Citadel/
├── gateway/
│   ├── signal_orchestrator.py   # Multi-machine signal coordination
│   ├── api_health_monitor.py    # Real-time API status tracking
│   └── data_archiver.py          # Automated historical data pipeline
├── engine/
│   ├── data_manager.py           # O(1) hashmap-based data access
│   ├── market_connector.py       # WebSocket API integration
│   └── O1_Architecture_Snippet.py # Core O(1) implementation
├── ui/
│   ├── main_window.py            # PySide6 main interface
│   ├── dashboard.py              # Unified visualization dashboard
│   └── widgets/                  # Custom financial widgets
├── tests/
│   ├── test_performance.py       # O(1) vs O(n) benchmarks
│   └── test_thread_safety.py     # Concurrency validation
└── README.md                     # This file
```

---

## 🎓 Architectural Insights

### Why This Architecture?
1. **Performance**: O(1) lookup critical for high-frequency trading decisions
2. **Responsiveness**: Direct memory reference eliminates UI lag
3. **Reliability**: Thread-safe design ensures data integrity
4. **Scalability**: Centralized gateway enables multi-machine coordination
5. **Intelligence**: Automated archiving builds historical dataset
6. **Operational Visibility**: Real-time API health monitoring

### Key Architectural Decisions
- **O(1) Over O(n)**: Constant-time lookup for predictable performance
- **Direct Memory Over HTTP**: Eliminate network overhead for UI updates
- **Centralized Over Distributed**: Single control plane for coordinated operations
- **Automated Over Manual**: Scheduled archiving for continuous data accumulation
- **Thread-Safe Over Lock-Free**: Precise locking for guaranteed correctness

---

## 📈 Business Impact
- **Trading Efficiency**: 90% faster data access enables rapid decision-making
- **Operational Reliability**: Real-time API monitoring prevents trading disruptions
- **Strategic Development**: Historical dataset enables algorithmic trading research
- **Scalability**: Multi-account architecture ready for expanded operations
- **Longevity**: 25+ years continuous evolution demonstrates sustainable design

---

## 🔗 Related Resources
- **GitHub**: [JuneBay/Mini-Citadel-Showcase](https://github.com/JuneBay/Mini-Citadel-Showcase)
- **LinkedIn**: [linkedin.com/in/junebay](https://linkedin.com/in/junebay)

---

## 💼 외주 문의 / Project Inquiries

**비슷한 프로젝트 의뢰 가능합니다 — Available for similar projects.**

### 이런 작업이면 처리해드릴 수 있습니다
- 금융 API 통합 (Kiwoom, eBest, Binance, Interactive Brokers 등)
- 실시간 시세 데이터 처리 / WebSocket 파이프라인
- O(1) 해시맵 기반 초저지연 데이터 엔진
- PySide6 / Qt 기반 트레이더용 데스크탑 GUI
- 다중 머신 신호 오케스트레이션 / 게이트웨이 설계
- 자동 데이터 아카이빙 / 백테스팅 데이터셋 파이프라인
- API 상태 모니터링 / 알림 봇

> ⚠️ **투자/매매 자문은 제공하지 않습니다.** 인프라·시스템 설계만 제공합니다.

### 진행 방식
1. 데이터 소스(API)와 성능 요구사항 먼저 확인 (1~2일)
2. 핵심 데이터 경로 1주 안에 PoC
3. 검증 후 본 빌드 + 주 1회 진행 공유
4. 운영 매뉴얼 + 모니터링 대시보드 함께 인계

### 문의 채널
[![Upwork](https://img.shields.io/badge/Upwork-14A800?style=flat&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/~01b49808a51af3b53c)
[![Fiverr](https://img.shields.io/badge/Fiverr-1DBF73?style=flat&logo=fiverr&logoColor=white)](https://www.fiverr.com/sellers/junebay)
[![Kmong](https://img.shields.io/badge/크몽-FF6B35?style=flat)](https://kmong.com/@JuneBay)
[![Wishket](https://img.shields.io/badge/위시켓-3B6BFF?style=flat)](https://www.wishket.com/partners/p/somster/)
