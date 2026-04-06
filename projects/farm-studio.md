# FarmStudio — Serverless IoT Monitoring Platform

*[← MACROBAY 메인으로 / Back to portfolio](../README.md)*

**$0 Server · >99% Delivery · 1+ Year Operation · Available for Similar Projects**

> 비슷한 작업 의뢰 가능합니다. 외주 문의는 [Upwork](https://www.upwork.com/freelancers/~01b49808a51af3b53c) · [Fiverr](https://www.fiverr.com/sellers/junebay) · [크몽](https://kmong.com/@JuneBay) · [위시켓](https://www.wishket.com/partners/p/somster/) 으로.

[![GitHub](https://img.shields.io/badge/GitHub-Showcase-black?style=for-the-badge&logo=github)](https://github.com/JuneBay/FarmStudio-Showcase)

---

## 🎯 Project Overview

**FarmStudio** is a serverless IoT data collection system for remote farm monitoring, collecting sensor and image data from ESP32 devices located 100km+ away without dedicated infrastructure. The system achieves **$0 operational costs** through an email-based asynchronous data pipeline and maintains **1+ year continuous operation** with zero-touch maintenance.

Engineered with a "No-Database" architecture using Email protocols, the platform achieves **>99% data delivery rate** in unstable rural network environments by leveraging email's inherent store-and-forward reliability and **self-healing data** mechanisms (regex normalization + time-series interpolation).

### Key Metrics
- **$0 server costs** (email-based data pipeline)
- **>99% data delivery rate** in unstable rural networks
- **5 ESP32 devices** managed remotely (100km+ distance)
- **OTA firmware updates** for zero-touch maintenance
- **1+ year** continuous operation without intervention
- **Self-healing data** through regex normalization and interpolation

---

## 🚀 Key Achievements

### Innovation & Cost Efficiency
- **No-Database Architecture**: Engineered a creative solution using Email protocols (SMTP/IMAP) as backend, demonstrating innovative problem-solving under extreme resource constraints
- **Zero Operating Cost**: Replaced commercial IoT cloud services (AWS IoT, Azure IoT Hub) with custom Gmail SMTP/IMAP pipeline, achieving **$0 monthly fixed costs**
- **High Availability**: Achieved **>99% data delivery rate** in unstable rural network environments through email's store-and-forward reliability

### Network Resilience
- **Email Store-and-Forward**: Leveraged SMTP's inherent reliability to ensure data delivery even during extended network outages
- **Asynchronous Architecture**: Decoupled data collection from network availability, enabling continuous operation in intermittent connectivity
- **Self-Healing Data**: Implemented regex-based normalization and time-series interpolation to recover from sensor errors and data corruption

### Operational Excellence
- **Long-Term Stability**: 1+ year continuous operation without manual intervention or system failures
- **Remote Management**: OTA (Over-The-Air) firmware updates enable zero-touch maintenance for devices 100km+ away
- **Multi-Format Integration**: Unified data pipeline handles heterogeneous ESP32 sensors with varying data formats

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    Remote Farm (100km+ away)                     │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  ESP32 #1  │  ESP32 #2  │  ESP32 #3  │  ESP32 #4  │ #5  │   │
│  │  (Temp)    │  (Humidity)│  (Camera)  │  (Soil)    │ ... │   │
│  └──────────────────────────────────────────────────────────┘   │
│                          │                                       │
│                          ▼                                       │
│                   ┌─────────────┐                                │
│                   │ SMTP Client │                                │
│                   │ (Email Send)│                                │
│                   └─────────────┘                                │
└─────────────────────────────────────────────────────────────────┘
                          │
                          │ (Unstable Network)
                          │ Store-and-Forward
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                      Gmail SMTP/IMAP                             │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  Inbox (Data Storage) │ Sent (C2 Commands)               │   │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Data Processing Server                        │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  IMAP Poller │ Regex Parser │ Interpolator │ Visualizer │   │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

**Key Architecture Components:**
- **ESP32 IoT Devices**: Remote sensors with SMTP client firmware
- **Gmail SMTP/IMAP**: Zero-cost backend replacing commercial IoT clouds
- **Regex Normalization**: Self-healing parser for heterogeneous data formats
- **Time-Series Interpolation**: Gap-filling for missing data points
- **OTA Update System**: Remote firmware management

---

## 🎨 Core Design Principles

### 1. Zero Operational Cost Architecture
- **Email as Backend**: SMTP for data uplink, IMAP for Command & Control (C2)
- **No Cloud Fees**: Gmail's free tier replaces AWS IoT ($0.08/million messages)
- **No Database Costs**: Email inbox serves as persistent storage
- **Result**: **$0 monthly operational costs**

### 2. Asynchronous Data Pipeline
- **Store-and-Forward**: SMTP's inherent reliability ensures data delivery
- **Network Independence**: Devices queue data during outages, send when connected
- **Batch Processing**: IMAP poller retrieves data on flexible schedules
- **Result**: **>99% data delivery rate** in unstable networks

### 3. Long-Term Operational Stability
- **OTA Firmware Updates**: Remote code deployment without physical access
- **Self-Healing Data**: Regex normalization + interpolation recover from errors
- **Zero-Touch Maintenance**: 1+ year operation without manual intervention
- **Result**: Sustainable operation in remote locations

### 4. Multi-Format Data Standardization
- **Regex-Based Normalization**: Unified parser for heterogeneous ESP32 sensors
- **Time-Series Interpolation**: Gap-filling for missing or corrupted data
- **Format Agnostic**: Handles JSON, CSV, plain text sensor outputs
- **Result**: Seamless integration of diverse sensor types

---

## 💻 Technical Implementation Highlights

### Email-Based Data Pipeline
The system leverages SMTP/IMAP protocols as a serverless backend, eliminating cloud infrastructure costs. See [`Email_Pipeline_Snippet.py`](./Email_Pipeline_Snippet.py) for detailed implementation.

**SMTP Data Uplink (ESP32):**
```cpp
// ESP32 sends sensor data via SMTP
void sendSensorData() {
    String data = "Temp: 25.3C, Humidity: 60%";
    smtp.send("farm@gmail.com", "Sensor Data", data);
    // Email stored in Gmail inbox = persistent storage
}
```

**IMAP Data Retrieval (Server):**
```python
# Server polls Gmail inbox for new sensor data
def collect_sensor_data():
    imap = imaplib.IMAP4_SSL('imap.gmail.com')
    imap.login(EMAIL, PASSWORD)
    imap.select('INBOX')
    
    # Fetch unread emails (sensor data)
    status, messages = imap.search(None, 'UNSEEN')
    for msg_id in messages[0].split():
        data = parse_email(msg_id)
        process_sensor_data(data)
```

### Self-Healing Data Mechanisms

**Regex Normalization Engine:**
```python
# Handles heterogeneous sensor data formats
SENSOR_PATTERNS = {
    'temp': r'Temp[:\s]+(\d+\.?\d*)°?C',
    'humidity': r'Hum[:\s]+(\d+\.?\d*)%',
    'soil': r'Soil[:\s]+(\d+\.?\d*)'
}

def normalize_sensor_data(raw_text):
    normalized = {}
    for sensor, pattern in SENSOR_PATTERNS.items():
        match = re.search(pattern, raw_text, re.IGNORECASE)
        if match:
            normalized[sensor] = float(match.group(1))
    return normalized
```

**Time-Series Interpolation:**
```python
# Fill gaps in sensor data
def interpolate_missing_data(timeseries):
    df = pd.DataFrame(timeseries)
    df['timestamp'] = pd.to_datetime(df['timestamp'])
    df = df.set_index('timestamp')
    
    # Linear interpolation for missing values
    df = df.resample('1H').interpolate(method='linear')
    return df
```

### Zero Operational Cost Strategy
| Component | Commercial IoT | FarmStudio | Cost Savings |
|-----------|----------------|------------|--------------|
| **Data Ingestion** | AWS IoT ($0.08/M msgs) | Gmail SMTP (Free) | **100%** |
| **Data Storage** | DynamoDB ($0.25/GB) | Gmail Inbox (Free) | **100%** |
| **Command & Control** | AWS IoT ($0.08/M msgs) | Gmail IMAP (Free) | **100%** |
| **Total (1 year)** | ~$50-100 | **$0** | **100%** |

---

## 🔧 Solved Technical Challenges

### 1. Serverless IoT Data Collection
**Challenge**: Commercial IoT clouds (AWS IoT, Azure) too expensive for hobby/small farm  
**Solution**: Repurposed Gmail SMTP/IMAP as zero-cost backend  
**Result**: $0 operational costs while maintaining reliability

### 2. Multi-Format Data Integration
**Challenge**: Heterogeneous ESP32 sensors produce varying data formats  
**Solution**: Regex-based normalization engine with pattern matching  
**Result**: Unified data pipeline for diverse sensor types

### 3. Email Parsing Reliability
**Challenge**: Email body parsing fragile to format changes  
**Solution**: Robust regex patterns with fallback parsing strategies  
**Result**: >99% successful data extraction rate

### 4. OTA Firmware Updates
**Challenge**: Physical access impossible for devices 100km+ away  
**Solution**: IMAP-based command channel triggers OTA updates  
**Result**: Zero-touch remote firmware management

### 5. Sensor Error Handling
**Challenge**: Sensor failures and data corruption in harsh environments  
**Solution**: Self-healing data through regex normalization + time-series interpolation  
**Result**: Continuous operation despite occasional sensor errors

---

## 📊 Performance Metrics
| Metric | Target | Achieved | Notes |
|--------|--------|----------|-------|
| **Data Delivery Rate** | >95% | **>99%** | Email store-and-forward reliability |
| **Operational Cost** | <$10/month | **$0** | Gmail free tier |
| **Uptime** | >90% | **>99%** | 1+ year continuous operation |
| **OTA Success Rate** | >90% | **100%** | All remote updates successful |
| **Data Parsing Success** | >95% | **>99%** | Regex normalization engine |

---

## 🚀 Real-World Usage
**FarmStudio** is actively deployed in production farm monitoring:

- **Status**: Production-ready, 1+ year continuous operation
- **Deployment**: 5 ESP32 devices across remote farm (100km+ from base)
- **Use Cases**: Temperature, humidity, soil moisture, camera surveillance
- **Network**: Unstable rural 4G/LTE with frequent outages

### Operational Characteristics
1. **Zero-Touch Maintenance**: OTA updates enable remote management
2. **Network Resilience**: Email store-and-forward handles intermittent connectivity
3. **Cost Sustainability**: $0 operational costs enable long-term deployment
4. **Self-Healing**: Regex + interpolation recover from sensor errors
5. **Scalability**: Email-based architecture scales to dozens of devices

---

## 🛠️ Technology Stack

### IoT Hardware
- **ESP32** - WiFi-enabled microcontroller
- **DHT22** - Temperature/humidity sensor
- **Soil Moisture Sensor** - Capacitive soil sensor
- **ESP32-CAM** - Camera module for visual monitoring

### Data Collection
- **SMTP** - Email-based data uplink from ESP32
- **IMAP** - Server-side data retrieval and C2
- **Gmail** - Zero-cost backend infrastructure

### Data Storage
- **Gmail Inbox** - Persistent sensor data storage
- **CSV Files** - Local archival for long-term analysis

### Visualization
- **Python** - Data processing and analysis
- **Pandas** - Time-series data manipulation
- **Matplotlib** - Sensor data visualization

---

## 📁 Project Structure
```
FarmStudio/
├── esp32/
│   ├── main.ino                  # ESP32 firmware
│   ├── smtp_client.cpp           # SMTP data uplink
│   └── ota_updater.cpp           # OTA firmware update
├── server/
│   ├── imap_poller.py            # Email data retrieval
│   ├── regex_parser.py           # Data normalization
│   ├── interpolator.py           # Time-series gap filling
│   └── Email_Pipeline_Snippet.py # Core email pipeline
├── visualization/
│   └── dashboard.py              # Sensor data visualization
└── README.md                     # This file
```

---

## 🎓 Architectural Insights

### Why This Architecture?
1. **Cost Efficiency**: $0 operational costs enable sustainable deployment
2. **Network Resilience**: Email store-and-forward handles unstable connectivity
3. **Operational Simplicity**: Zero-touch maintenance for remote locations
4. **Proven Reliability**: Email protocols battle-tested over decades
5. **Accessibility**: No cloud expertise required, standard email protocols

### Key Architectural Decisions
- **Email Over MQTT**: SMTP/IMAP more reliable than MQTT in unstable networks
- **Gmail Over Self-Hosted**: Free tier eliminates server costs
- **Regex Over Structured**: Flexible parsing handles heterogeneous sensors
- **Interpolation Over Strict**: Self-healing data tolerates sensor errors
- **OTA Over Physical**: Remote updates essential for 100km+ distance

---

## 📈 Business Impact
- **Cost Accessibility**: $0 operational costs democratize IoT monitoring
- **Rural Deployment**: Email resilience enables monitoring in remote areas
- **Sustainability**: Zero-touch operation reduces maintenance burden
- **Scalability**: Email-based architecture scales without infrastructure investment

---

## 🔗 Related Resources
- **GitHub**: [JuneBay/FarmStudio-Showcase](https://github.com/JuneBay/FarmStudio-Showcase)
- **LinkedIn**: [linkedin.com/in/junebay](https://linkedin.com/in/junebay)

---

## 💼 외주 문의 / Project Inquiries

**비슷한 프로젝트 의뢰 가능합니다 — Available for similar projects.**

### 이런 작업이면 처리해드릴 수 있습니다
- ESP32 / ESP8266 기반 IoT 장치 펌웨어 설계
- 원격 센서 데이터 수집 (온도·습도·토양·카메라 등)
- 불안정 네트워크 환경 데이터 파이프라인 (시골, 산간, 해외)
- 이메일·MQTT·HTTPS 기반 store-and-forward 아키텍처
- OTA(Over-The-Air) 펌웨어 업데이트 시스템
- 자가복구 데이터 처리 (정규식 정규화 + 시계열 보간)
- 스마트팜 / 환경 모니터링 / 양식장 / 수처리 / 재고 관리 모니터링

### 진행 방식
1. 측정 대상·환경 조건·통신 가능 채널 먼저 확인 (1~2일)
2. 1주 안에 1~2개 장치 시범 운영
3. 검증 후 전체 장치 확장 + 모니터링 대시보드
4. 운영 매뉴얼 + OTA 업데이트 절차 함께 인계

### 문의 채널
[![Upwork](https://img.shields.io/badge/Upwork-14A800?style=flat&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/~01b49808a51af3b53c)
[![Fiverr](https://img.shields.io/badge/Fiverr-1DBF73?style=flat&logo=fiverr&logoColor=white)](https://www.fiverr.com/sellers/junebay)
[![Kmong](https://img.shields.io/badge/크몽-FF6B35?style=flat)](https://kmong.com/@JuneBay)
[![Wishket](https://img.shields.io/badge/위시켓-3B6BFF?style=flat)](https://www.wishket.com/partners/p/somster/)
