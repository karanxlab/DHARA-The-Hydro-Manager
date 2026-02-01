DHARA: Aqua-Hydro Manager

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
