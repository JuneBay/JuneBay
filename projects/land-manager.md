# MyLandManager — Geospatial Decision Support System

*[← MACROBAY 메인으로 / Back to portfolio](../README.md)*

**Patent-Pending · $0 Infrastructure · Production · Available for Similar Projects**

> 비슷한 작업 의뢰 가능합니다. 외주 문의는 [Upwork](https://www.upwork.com/freelancers/~01b49808a51af3b53c) · [Fiverr](https://www.fiverr.com/sellers/junebay) · [크몽](https://kmong.com/@JuneBay) · [위시켓](https://www.wishket.com/partners/p/somster/) 으로.

[![Live Demo](https://img.shields.io/badge/Vercel-Live_Demo-black?style=for-the-badge&logo=vercel)](https://my-land-manager.vercel.app)
[![GitHub](https://img.shields.io/badge/GitHub-Showcase-black?style=for-the-badge&logo=github)](https://github.com/JuneBay/My-Land-Manager-Showcase)

---

## 🎯 Project Overview

**MyLandManager** is a serverless geospatial decision support system for integrated land parcel management. It combines public cadastral data with surrounding infrastructure information to enable pre-calculation and risk assessment—achieving **$0 infrastructure costs** while processing **100MB+ geospatial data** efficiently.

### Key Metrics
- **$0 infrastructure costs** (Vercel Free Tier + VWorld OpenAPI)
- **80%+ time reduction** in repetitive workflows
- **100MB+ geospatial data** optimization
- **Patent-pending** dispute risk management features
- **Government portal integration** (Toji-eum, Supreme Court Registry)

---

## 🚀 Key Achievements

### Innovation & Commercialization
- **Patent-Pending Features**: Developed proprietary geospatial analysis algorithms, currently in commercialization phase
- **Dispute Risk Management**: Pre-calculate litigation and professional survey costs through virtual surveying simulation—addressing Korea's severe cadastral mismatch issues
- **One-Stop Workflow**: Seamlessly integrated with government land portals (Toji-eum, Supreme Court Registry), enabling users to transition from analysis to document issuance without context switching

### Technical Excellence
- **Zero Infrastructure Cost**: $0 monthly operation cost through pure client-side serverless architecture
- **High Performance**: 100MB+ contiguous cadastral map processing in-browser using chunk loading strategies
- **Stateful Workflow**: Save/load/edit analysis at any stage, ensuring work continuity
- **Batch Reporting**: Multi-parcel batch analysis reducing manual administrative time

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Client Browser (Pure JS)                  │
├─────────────────────────────────────────────────────────────┤
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Leaflet    │  │   Turf.js    │  │  LocalStorage │      │
│  │  Map Engine  │  │  Geospatial  │  │  Project Mgmt │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│         │                  │                  │              │
│         └──────────────────┴──────────────────┘              │
│                          │                                   │
│                 ┌────────▼────────┐                          │
│                 │  VWorld OpenAPI │                          │
│                 │ (Government API)│                          │
│                 └─────────────────┘                          │
└─────────────────────────────────────────────────────────────┘
                          │
              ┌───────────┴───────────┐
              │                       │
    ┌─────────▼────────┐   ┌─────────▼──────────┐
    │   Toji-eum       │   │ Supreme Court      │
    │ (Land Registry)  │   │   Registry         │
    └──────────────────┘   └────────────────────┘
```

**Key Architecture Decisions:**
- **No Backend**: Pure client-side application (zero server costs)
- **Public APIs Only**: VWorld OpenAPI (government-provided, free)
- **Browser Storage**: LocalStorage + File API for unlimited project capacity
- **Government Integration**: Direct links to Toji-eum and Supreme Court portals

---

## 🎨 Core Design Principles

### 1. Zero Infrastructure Cost Architecture
- **Serverless Design**: Pure client-side application (no backend servers)
- **Public API Integration**: VWorld OpenAPI (government-provided, free)
- **Free Hosting**: Vercel Free Tier for static hosting
- **Result**: **$0 operational costs** while handling enterprise-scale data

### 2. Large-Scale Data Optimization
- **Chunk Loading**: 100MB+ geospatial data processed in 1,000-feature chunks
- **Dynamic Loading**: Only visible map areas loaded to minimize memory usage
- **Intelligent Caching**: LocalStorage for frequently accessed data
- **Result**: **80% memory reduction** compared to full dataset loading

### 3. Stateful Project Management
- **LocalStorage Persistence**: Automatic project state saving (5-10MB limit)
- **File API Export/Import**: Unlimited project size via JSON files
- **IndexedDB Integration**: File handle persistence for seamless UX
- **Result**: **80%+ workflow time reduction** through project reuse

### 4. Public Data Integration
- **VWorld OpenAPI**: Cadastral maps, land valuation, address search
- **Real-time Data**: Live property information without database maintenance
- **CORS Handling**: JSONP fallback for cross-origin requests
- **Result**: Always up-to-date data without infrastructure overhead

### 5. Dispute Risk Management (Patent-Pending)
- **Virtual Surveying**: Simulate professional boundary surveys before expensive legal proceedings
- **Cost Pre-calculation**: Estimate litigation and professional survey costs based on parcel complexity
- **Risk Assessment**: Identify high-risk parcels with cadastral mismatches
- **Government Portal Integration**: Direct workflow to Toji-eum and Supreme Court Registry for document issuance
- **Result**: **Prevent costly disputes** through early risk identification and data-driven decision support

---

## 💻 Technical Implementation Highlights

### Geospatial Data Processing
The system implements efficient chunk-based loading and processing for large-scale geospatial datasets. See [`Geospatial_Logic_Snippet.js`](./Geospatial_Logic_Snippet.js) for detailed implementation.

**Key Features:**
- **Pagination Strategy**: 1,000 features per API request (up to 20,000 parcels per region)
- **Memory Optimization**: Features loaded incrementally, not all at once
- **Error Recovery**: Automatic retry with fallback to WMS layers
- **Performance**: Sub-second response for cached regions

### Zero Infrastructure Cost Strategy
| Component | Technology | Cost | Optimization |
|-----------|-----------|------|--------------|
| **Hosting** | Vercel Free Tier | $0.00 | Static site hosting |
| **Backend** | None (Client-side) | $0.00 | Pure JavaScript application |
| **Database** | LocalStorage + File API | $0.00 | Browser-native storage |
| **Maps API** | VWorld OpenAPI | $0.00 | Government-provided free API |
| **Total** | | **$0.00** | Complete serverless architecture |

---

## 🔧 Solved Technical Challenges

### 1. Large-Scale Geospatial Data Processing
**Challenge**: 100MB+ GeoJSON files freeze browsers  
**Solution**: Chunk-based loading (1,000 features/chunk) + dynamic viewport rendering  
**Result**: Smooth performance even with 20,000+ parcels

### 2. LocalStorage Capacity Limitation
**Challenge**: 5-10MB LocalStorage limit insufficient for large projects  
**Solution**: Hybrid storage (LocalStorage for active + File API for archive)  
**Result**: Unlimited project capacity while maintaining fast access

### 3. VWorld API CORS Handling
**Challenge**: Cross-origin restrictions blocking direct API calls  
**Solution**: JSONP fallback + WMS layer alternative  
**Result**: 100% API availability across all browsers

### 4. Responsive Map Interface
**Challenge**: Complex UI with multiple data layers and controls  
**Solution**: Leaflet.js + custom control panels + mobile-first design  
**Result**: Seamless experience across desktop/tablet/mobile

### 5. Project State Management
**Challenge**: Complex analysis workflows requiring state persistence  
**Solution**: Stateful architecture with save/load/resume capabilities  
**Result**: 80%+ time reduction through work continuity

---

## 📊 Performance Metrics
| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| **Work Time** | 20-35 minutes/session | 1-2 minutes/session | **80%+ reduction** |
| **Infrastructure Cost** | Server + DB costs | **$0** (Serverless) | **100% reduction** |
| **Data Processing** | Manual entry | Automatic calculation | **Full automation** |
| **Memory Usage** | Full dataset load | Chunk-based loading | **80% reduction** |
| **Project Storage** | Limited by LocalStorage | Unlimited (File API) | **Unlimited capacity** |
| **Scalability** | Region-specific builds | Nationwide coverage | **Universal system** |

---

## 🚀 Real-World Usage
**MyLandManager** is actively deployed and used in production:

- **Live Service**: [my-land-manager.vercel.app](https://my-land-manager.vercel.app)
- **Deployment**: Vercel (Free Tier)
- **Status**: Production-ready, actively maintained
- **Users**: Government officials, real estate professionals, developers

### Use Cases
1. **Government Officials**: Land registry management, dispute prevention, field survey preparation
2. **Real Estate Agents**: Property management, client consultation, market price checking
3. **Developers**: Site selection, risk assessment, project feasibility review
4. **Agriculture/Forestry**: Farm management, crop planning, subsidy applications

### Dispute Prevention Workflow
1. **Identify Risk**: Detect cadastral mismatches in target parcels
2. **Virtual Survey**: Simulate professional boundary survey
3. **Cost Estimation**: Calculate potential litigation/survey expenses
4. **Decision Support**: Provide data-driven recommendations
5. **Government Integration**: Direct link to Toji-eum or Supreme Court Registry for document issuance

---

## 🛠️ Technology Stack

### Frontend
- **Vanilla JavaScript** (ES6+) - Zero framework overhead
- **HTML5/CSS3** - Semantic markup, responsive design

### Mapping Libraries
- **Leaflet.js** - Interactive map rendering
- **Turf.js** - Geospatial calculations (area, distance, intersection)

### APIs & Services
- **VWorld OpenAPI** - Cadastral maps, land valuation
- **Kakao Maps API** - Address search, geocoding
- **Government Portals** - Toji-eum, Supreme Court Registry integration

### Data Storage
- **LocalStorage** - Active project state (5-10MB)
- **File API** - Project export/import (unlimited)
- **IndexedDB** - File handle persistence

---

## 📁 Project Structure
```
My-Land-Manager/
├── index.html              # Main application entry
├── main.js                 # Core application logic
├── map_script.js           # Map initialization & controls
├── Geospatial_Logic_Snippet.js  # Chunk loading implementation
├── styles.css              # Application styling
└── README.md               # This file
```

---

## 🎓 Architectural Insights

### Why This Architecture?
1. **Cost Efficiency**: $0 infrastructure costs enable sustainable operation
2. **Scalability**: Client-side processing scales with user hardware
3. **Reliability**: No server dependencies = no downtime
4. **Privacy**: All data processing happens locally in the browser
5. **Accessibility**: Free public APIs ensure long-term viability

### Key Architectural Decisions
- **Client-side Only**: Eliminates server costs and maintenance
- **Chunk Loading**: Enables processing of datasets larger than available RAM
- **Stateful Design**: Reduces repetitive work through project persistence
- **Government Integration**: One-stop workflow from analysis to document issuance
- **Patent-Pending Features**: Proprietary dispute risk management algorithms

---

## 📈 Business Impact
- **Commercialization**: Patent-pending features driving product development
- **Market Fit**: Addresses critical pain points in Korean land management
- **Scalability**: Zero marginal cost per additional user
- **Sustainability**: $0 operational costs ensure long-term viability

---

## 🔗 Related Resources
- **Live Demo**: [my-land-manager.vercel.app](https://my-land-manager.vercel.app)
- **GitHub**: [JuneBay/My-Land-Manager-Showcase](https://github.com/JuneBay/My-Land-Manager-Showcase)
- **LinkedIn**: [linkedin.com/in/junebay](https://linkedin.com/in/junebay)

---

## 💼 외주 문의 / Project Inquiries

**비슷한 프로젝트 의뢰 가능합니다 — Available for similar projects.**

### 이런 작업이면 처리해드릴 수 있습니다
- 정부 OpenAPI 통합 (VWorld, 토지이음, 인터넷등기소, NABZ 등)
- 대용량 지리정보 데이터 (100MB+) 브라우저 처리 / 청크 로딩
- 서버리스 / $0 인프라 설계 (Vercel + 공공 API 조합)
- 부동산·지적·도시계획 결정 지원 시스템
- LocalStorage + File API 기반 상태 영속화 / 프로젝트 관리
- 분쟁 위험 시뮬레이션 / 비용 사전 계산 모델

### 진행 방식
1. 데이터 출처와 사용 시나리오 먼저 확인 (1~2일)
2. 1주 안에 최소 작동 프로토타입
3. 검증 후 본 빌드 + 매주 진행 공유
4. 운영 매뉴얼 + 데이터 파이프라인 함께 인계

### 문의 채널
[![Upwork](https://img.shields.io/badge/Upwork-14A800?style=flat&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/~01b49808a51af3b53c)
[![Fiverr](https://img.shields.io/badge/Fiverr-1DBF73?style=flat&logo=fiverr&logoColor=white)](https://www.fiverr.com/sellers/junebay)
[![Kmong](https://img.shields.io/badge/크몽-FF6B35?style=flat)](https://kmong.com/@JuneBay)
[![Wishket](https://img.shields.io/badge/위시켓-3B6BFF?style=flat)](https://www.wishket.com/partners/p/somster/)
