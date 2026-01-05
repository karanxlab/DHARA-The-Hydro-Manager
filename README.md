# 🌱 DHARA: The Ultimate Aqua-Hydro Manager

![IoT](https://img.shields.io/badge/IoT-Enabled-blue)
![Arduino](https://img.shields.io/badge/Arduino-Uno-00979D)
![ESP32](https://img.shields.io/badge/ESP32-Microcontroller-red)
![Aquaponics](https://img.shields.io/badge/Aquaponics-Sustainable-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview

**DHARA** (The Ultimate Aqua-Hydro Manager) is an intelligent IoT-based automation system that seamlessly integrates **aquaponics** and **hydroponics** into a single, self-regulating hybrid ecosystem. The system maintains optimal conditions for both fish health and plant growth through real-time monitoring, automated control, and cloud-based dashboard management.

This project represents a breakthrough in sustainable agriculture technology, combining biological balance with embedded intelligence to create a water-efficient, eco-friendly farming solution suitable for urban environments, research institutions, and commercial farms.

---

## 🎯 Key Features

- ✅ **Hybrid Aquaponic-Hydroponic System** - Symbiotic fish-plant ecosystem with shared water circulation
- ✅ **Real-Time IoT Monitoring** - Continuous tracking via UdiBot cloud dashboard
- ✅ **Multi-Sensor Integration** - pH, TDS, turbidity, temperature, and humidity monitoring
- ✅ **Automated pH Regulation** - Acid/base pump control for maintaining ideal water chemistry
- ✅ **Smart Nutrient Management** - Automated dosing every 12 hours
- ✅ **Remote Control & Alerts** - Web/mobile dashboard with customizable thresholds
- ✅ **Energy Efficient** - Operates on portable 5V power bank (~4.6W total consumption)
- ✅ **70% Water Conservation** - Closed-loop recirculation system
- ✅ **Modular & Scalable** - Adaptable to various fish-plant combinations

---

## 🏗️ System Architecture

### Hardware Components

| Component | Specification | Function |
|-----------|--------------|----------|
| **Arduino Uno** | ATmega328P, 5V | pH sensor controller & UART communication |
| **ESP32** | Dual-core 240MHz, WiFi/BT | Main IoT controller and data processor |
| **pH Sensor** | Industrial Kit v2.0, 0-14 pH | Water acidity/alkalinity monitoring |
| **TDS Sensor** | Grove TDS, 0-5000 ppm | Nutrient concentration measurement |
| **DHT11** | 0-50°C, 20-90% RH | Temperature & humidity sensing |
| **Turbidity Sensor** | 0-1000 NTU | Water clarity monitoring |
| **4-Channel Relay** | 5V, 10A | Pump automation control |
| **Mini Water Pumps** | 3-6V submersible (×4) | Acid, base, nutrient, and drain pumps |
| **LCD Display** | 16×2 I2C | Local real-time data display |
| **Power Bank** | 10,000 mAh, 5V | Portable power supply |

### Software Stack

- **Arduino IDE** - Firmware development
- **C/C++** - Core programming language
- **ArduinoJson** - Data serialization for cloud transmission
- **UdiBot IoT Platform** - Cloud dashboard and remote control
- **UART Protocol** - Arduino-ESP32 communication
- **I2C Protocol** - LCD display interface

---

## 🔄 How It Works

### System Operation Flow

```
┌─────────────┐
│   Sensors   │ → pH, TDS, Turbidity, Temp, Humidity
└──────┬──────┘
       ↓
┌─────────────────────────────────────┐
│  Arduino Uno  ←→  ESP32 (UART)      │
│  • pH Reading     • Data Processing │
│  • Calibration    • IoT Upload      │
│                   • Relay Control    │
└──────┬──────────────────┬───────────┘
       ↓                  ↓
┌─────────────┐    ┌────────────────┐
│  UdiBot     │    │  4-Ch Relay    │
│  Dashboard  │    │  Module        │
│  • Monitor  │    │  • Acid Pump   │
│  • Alert    │    │  • Base Pump   │
│  • Control  │    │  • Nutrient    │
└─────────────┘    │  • Drain       │
                   └────────────────┘
```

### Automated Control Logic

1. **pH Regulation**
   - pH < min threshold → Activate base pump
   - pH > max threshold → Activate acid pump
   - Duration: 10 seconds per activation

2. **Nutrient Management**
   - Automatic activation every 12 hours
   - Duration: 30 seconds
   - Delivers organic supplements via misting

3. **Water Quality Monitoring**
   - TDS > 500 ppm → Alert user for water dilution
   - Turbidity > 600 NTU → Alert for cleaning
   - Temperature outside 25-30°C → Environmental warning

4. **Manual Override**
   - Drain pump controllable via dashboard button
   - All parameters adjustable through UdiBot interface

---

## 🚀 Getting Started

### Prerequisites

- Arduino IDE (version 1.8.13 or later)
- ESP32 board support package
- Required libraries:
  - `WiFi.h`
  - `ArduinoJson.h`
  - `DHT.h`
  - `Wire.h` (I2C)
  - `LiquidCrystal_I2C.h`

### Hardware Setup

1. **Power Connections**
   - Connect Arduino Uno to 5V power bank via USB
   - Connect ESP32 to 5V rail (use 3.3V pin for logic)
   - Connect relay module VCC to 5V, GND to common ground

2. **Sensor Wiring**
   - pH sensor → Arduino A0
   - TDS sensor → ESP32 A1 (GPIO 34)
   - Turbidity sensor → ESP32 A2 (GPIO 35)
   - DHT11 → ESP32 GPIO 13

3. **UART Communication**
   - Arduino TX → ESP32 RX (via voltage divider: 5V → 3.3V)
   - Common GND between Arduino and ESP32

4. **Relay Connections**
   - IN1 → ESP32 GPIO 25 (Acid pump)
   - IN2 → ESP32 GPIO 26 (Base pump)
   - IN3 → ESP32 GPIO 27 (Nutrient pump)
   - IN4 → ESP32 GPIO 14 (Drain pump)

5. **Pump Wiring**
   - Relay COM → 5V
   - Relay NO → Pump positive
   - Pump negative → GND

### Software Installation

1. **Clone Repository**
   ```bash
   git clone https://github.com/yourusername/DHARA-Aqua-Hydro-Manager.git
   cd DHARA-Aqua-Hydro-Manager
   ```

2. **Configure WiFi & UdiBot**
   - Open `ESP32_Main_Controller.ino`
   - Update WiFi credentials:
     ```cpp
     const char* ssid = "YOUR_WIFI_SSID";
     const char* password = "YOUR_WIFI_PASSWORD";
     ```
   - Add UdiBot API token:
     ```cpp
     const char* UBIDOTS_TOKEN = "YOUR_UBIDOTS_TOKEN";
     ```

3. **Upload Code**
   - Upload `Arduino_pH_Controller.ino` to Arduino Uno
   - Upload `ESP32_Main_Controller.ino` to ESP32

4. **Calibrate pH Sensor**
   - Use buffer solutions (pH 4.0, 7.0, 10.0)
   - Follow two-point calibration procedure in documentation

---

## 📊 Dashboard Setup (UdiBot)

### Creating Variables

Create the following variables in your UdiBot device:

| Variable Name | Type | Unit | Description |
|--------------|------|------|-------------|
| `ph` | Number | pH | Water pH level |
| `tds` | Number | ppm | Total dissolved solids |
| `turbidity` | Number | NTU | Water clarity |
| `temperature` | Number | °C | Ambient temperature |
| `humidity` | Number | % | Relative humidity |

### Setting Thresholds

Configure alert ranges via dashboard sliders:
- **pH**: 6.5 - 7.5
- **TDS**: 200 - 500 ppm
- **Turbidity**: 0 - 600 NTU
- **Temperature**: 25 - 30°C
- **Humidity**: 60 - 70%

### Widget Configuration

- **Gauge Charts** - Real-time sensor readings
- **Line Graphs** - Historical data trends
- **Slider Controls** - Min/max threshold adjustment
- **Button Widgets** - Manual pump control
- **Notification Rules** - Email/SMS alerts

---

## 🧪 Testing & Validation

### Sensor Accuracy

| Sensor | Measured Range | Accuracy | Response Time |
|--------|----------------|----------|---------------|
| pH | 0-14 pH | ±0.1 pH | <2 seconds |
| TDS | 0-5000 ppm | ±10 ppm | <3 seconds |
| Turbidity | 0-1000 NTU | ±5% | <2 seconds |
| Temperature | 0-50°C | ±2°C | <5 seconds |
| Humidity | 20-90% RH | ±5% | <5 seconds |

### System Performance

- **Pump Response Time**: <1 second from trigger
- **Dashboard Update Rate**: Every 10 seconds
- **Battery Life**: 7-8 hours continuous operation
- **WiFi Range**: Up to 50 meters (line of sight)

---

## 💰 Cost Analysis

### Bill of Materials

| Component | Quantity | Unit Price (₹) | Total (₹) |
|-----------|----------|----------------|-----------|
| ESP32 D Series | 1 | 350 | 350 |
| Arduino Uno | 1 | 400 | 400 |
| pH Sensor Kit v2.0 | 1 | 2,000 | 2,000 |
| TDS Sensor | 1 | 500 | 500 |
| DHT11 Sensor | 1 | 150 | 150 |
| Turbidity Sensor | 1 | 400 | 400 |
| 4-Channel Relay | 1 | 250 | 250 |
| Mini Water Pumps | 4 | 150 | 600 |
| LCD Display | 1 | 350 | 350 |
| Miscellaneous | - | 1,000 | 1,000 |
| **TOTAL** | | | **₹6,000** |

### ROI Analysis

- **Traditional Manual Monitoring**: ₹2,000/month (testing kits + chemicals)
- **DHARA Operating Cost**: <₹50/month (electricity only)
- **Savings**: ₹1,950/month
- **Break-even Period**: ~3 months
- **Water Conservation**: 70% reduction vs conventional farming

---

## 🌍 Environmental Impact

- ♻️ **70% Water Savings** through closed-loop recirculation
- 🌱 **Zero Chemical Fertilizers** - nutrients from fish waste
- 🐟 **Sustainable Fish Farming** - optimal living conditions maintained
- 🏙️ **Urban Agriculture Enabler** - suitable for rooftop/indoor farming
- ⚡ **Low Energy Footprint** - <5W total system consumption

---

## 🔬 Research & Development

### Suitable Fish-Plant Combinations

| Fish Species | Plants | pH Range | Temp Range |
|-------------|---------|----------|------------|
| Tilapia | Okra, Lettuce, Spinach | 6.8-8.5 | 25-30°C |
| Catfish | Basil, Tomatoes | 6.5-8.0 | 24-28°C |
| Koi | Watercress, Mint | 7.0-8.5 | 15-25°C |
| Goldfish | Herbs, Leafy Greens | 7.0-8.0 | 18-24°C |

*Note: DHARA is user-configurable for any compatible combination*

### Nutrient Management

**Fish Waste Provides:**
- Nitrogen (N) - from ammonia conversion
- Phosphorus (P) - from fish feed
- Potassium (K) - partial supply

**Supplemental Nutrients (via misting):**
- Iron Chelate
- Seaweed Extract
- Worm Tea
- Trace minerals (Zn, Mn, B, Cu)

---

## 📈 Future Enhancements

### Planned Features

- [ ] **AI-Powered Prediction** - Machine learning for nutrient optimization
- [ ] **Mobile Application** - Native Android/iOS app with offline SMS control
- [ ] **Solar Power Integration** - Off-grid renewable energy operation
- [ ] **Dissolved Oxygen Sensor** - Enhanced fish health monitoring
- [ ] **Automated Feeding System** - Scheduled fish feed dispenser
- [ ] **Camera Module** - Visual monitoring and fish/plant health assessment
- [ ] **Multi-Tank Management** - Centralized control for commercial farms
- [ ] **Data Analytics Dashboard** - Yield prediction and performance metrics

### Research Extensions

- Branch prediction algorithms for pH drift
- Modular sensor expansion ports
- Integration with national agricultural databases
- Climate-adaptive farming protocols

---

## 📚 References

1. Acharya, B. S., et al. (2021). "Unmanned aerial vehicles in hydrology and water management." *Water Resources Research*.

2. Engle, C. R. (2015). *Economics of Aquaponics*. SRAC Publisher.

3. FAO (2014). *The State of Food Insecurity in the World*. Rome: IFAD and WEP.

4. Martins, C., et al. (2010). "New developments in recirculating aquaculture systems in Europe." *Aquaculture Engineering*, 43, 83-93.

5. Liang, J. Y., & Chien, Y. H. (2013). "Effects of feeding frequency and photoperiod on water quality and crop production in a tilapia–water spinach raft aquaponics system." *International Biodeterioration and Biodegradation*, 85, 693-700.

---

## 📜 License

This project is developed for **educational and research purposes** under VIT Bhopal University. The system design and implementation are subject to patent considerations under VIT IPR Policy.

For commercial use or collaboration inquiries, please contact the authors.

---

## 🤝 Contributing

We welcome contributions to improve DHARA! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/enhancement`)
3. Commit your changes (`git commit -m 'Add new sensor support'`)
4. Push to branch (`git push origin feature/enhancement`)
5. Open a Pull Request

### Areas for Contribution

- Code optimization and bug fixes
- Additional sensor integration
- Mobile app development
- Documentation improvements
- Testing and validation reports

---

## 📧 Contact

**GitHub**: [@karanxlab](https://github.com/karanxlab)  
**Email**: karangandha504@gmail.com

<div align="center">

**🌱 Sustainable Agriculture | 🤖 Smart Automation | 🌍 Environmental Conservation**

**⭐ If this project inspires you, please give it a star! ⭐**

*DHARA - Where Nature Meets Technology*

</div>
