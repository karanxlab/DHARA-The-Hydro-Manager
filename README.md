DHARA: Smart Aquaponics System
Show Image Show Image Show Image Show Image
What is DHARA?
An automated IoT system that grows fish and plants together in a symbiotic ecosystem. It monitors water quality continuously, adjusts pH levels automatically, and provides remote control via cloud dashboard. Ideal for urban farming and sustainable agriculture.

Key Features
CRITICAL FUNCTIONS:

Automated pH Control - Maintains optimal water chemistry for fish and plants
Real-Time Monitoring - Tracks pH, TDS, turbidity, temperature, and humidity
Cloud Dashboard - Monitor and control remotely via UdiBot platform

Additional Features:

70% water conservation through closed-loop recirculation
Smart nutrient dosing every 12 hours
Energy efficient operation (runs on portable power bank)
Customizable alert thresholds


Hardware Components
ESSENTIAL:
ComponentSpecificationPurposeArduino UnoATmega328PpH sensor controllerESP32Dual-core, WiFiMain IoT controllerpH Sensor0-14 pH rangeWater acidity monitoring4-Channel Relay5V, 10APump automationMini Water Pumps (×4)3-6V submersibleAcid, base, nutrient, drain control
Secondary:

TDS Sensor (nutrient concentration)
DHT11 (temperature & humidity)
Turbidity Sensor (water clarity)
LCD Display (local viewing)

Total Cost: ₹6,000 (~$75 USD)

System Architecture
┌─────────────┐
│   Sensors   │ (pH, TDS, Turbidity, Temp, Humidity)
└──────┬──────┘
       ↓
┌──────────────────────┐
│ Arduino ←→ ESP32     │ (UART Communication)
│ • pH Control         │
│ • Data Processing    │
│ • Cloud Upload       │
└──────┬───────────────┘
       ↓
┌──────────────────────┐
│  Automated Control   │
│ • Acid Pump          │
│ • Base Pump          │
│ • Nutrient Pump      │
│ • Drain Pump         │
└──────────────────────┘

How It Works
AUTOMATED CONTROL LOGIC:
pH Regulation (CRITICAL):

pH < minimum threshold → Base pump activates (10 seconds)
pH > maximum threshold → Acid pump activates (10 seconds)
Target range: 6.5-7.5 pH

Nutrient Management:

Automatic dosing every 12 hours
Duration: 30 seconds per cycle

Alert System:

TDS > 500 ppm → Water dilution required
Turbidity > 600 NTU → Cleaning needed
Temperature outside 25-30°C → Environmental warning


Setup Overview
IMPORTANT STEPS:
1. Hardware Connections

Connect pH sensor to Arduino A0
Wire TDS sensor to ESP32 GPIO 34
Link Arduino TX to ESP32 RX (use voltage divider: 5V → 3.3V)
Connect relay module to ESP32 (GPIOs 25, 26, 27, 14)
Wire pumps to relay outputs

2. Software Configuration

Update WiFi credentials in ESP32 code
Add UdiBot API token for cloud connectivity
Calibrate pH sensor using buffer solutions (pH 4.0, 7.0, 10.0)
Upload firmware to both Arduino and ESP32

3. Dashboard Setup (CRITICAL)

Create variables: ph, tds, turbidity, temperature, humidity
Set alert thresholds via sliders
Configure notification rules for alerts


Dashboard Configuration
Required Variables:
VariableTypeUnitThreshold RangephNumberpH6.5 - 7.5tdsNumberppm200 - 500turbidityNumberNTU0 - 600temperatureNumber°C25 - 30humidityNumber%60 - 70
Dashboard Widgets:

Gauge charts for real-time readings
Line graphs for historical trends
Slider controls for threshold adjustment
Button widgets for manual pump control


Performance Metrics
Sensor Accuracy:

pH: ±0.1 pH (response time: <2 seconds)
TDS: ±10 ppm (response time: <3 seconds)
Temperature: ±2°C

System Performance:

Pump response time: <1 second
Dashboard update rate: Every 10 seconds
Battery life: 7-8 hours continuous
WiFi range: Up to 50 meters


Environmental Impact
Water Conservation:

70% reduction vs conventional farming
Closed-loop recirculation system

Sustainability:

Zero chemical fertilizers (fish waste provides nutrients)
Low energy footprint (<5W total consumption)
Suitable for urban agriculture

Cost Savings:

Traditional monitoring: ₹2,000/month
DHARA operating cost: <₹50/month
Break-even period: 3 months


Compatible Fish-Plant Combinations
Fish SpeciesSuitable PlantspH RangeTemperatureTilapiaOkra, Lettuce, Spinach6.8-8.525-30°CCatfishBasil, Tomatoes6.5-8.024-28°CGoldfishHerbs, Leafy Greens7.0-8.018-24°CKoiWatercress, Mint7.0-8.515-25°C

Future Enhancements
Planned Features:

AI-powered nutrient optimization
Native mobile application
Solar power integration
Dissolved oxygen monitoring
Automated fish feeding system
Visual monitoring via camera module
Multi-tank management for commercial scaling


Technical Documentation
Communication Protocols:

UART: Arduino-ESP32 data exchange
I2C: LCD display interface
WiFi: Cloud connectivity

Power Requirements:

Input: 5V DC (power bank compatible)
Total consumption: ~4.6W
Individual pump power: <1W each


Contact
GitHub: @karanxlab
Email: karangandha504@gmail.com

License: Educational and research purposes under VIT Bhopal University
Star this repository if you support sustainable agriculture technology
DHARA - Where Nature Meets Technology
