# nRFNT - Comprehensive Documentation

## Project Overview

The **nRFNT (nRF Network Tool)** is an all-in-one wireless security testing and research device designed for exploring, analyzing, and interacting with various wireless communication protocols. It combines the ESP32 microcontroller with multiple NRF24L01 modules, OLED display, and other components to create a multifunctional wireless toolkit.

## Current Hardware Configuration

Based on the source code analysis, the nRFNT uses:

- **Main Controller**: ESP32 Wroom32U (38-pin variant)
- **Radio Modules**: 3x NRF24L01 modules (RadioA, RadioB, RadioC)
- **Display**: 128x64 OLED (SSD1306, I2C interface)
- **User Interface**: 5 push buttons (Up, Down, Left, Right, Select)
- **Visual Indicator**: 1x NeoPixel RGB LED
- **Storage**: SD card slot for firmware updates
- **Power**: Battery charging via TP4056 module

## Pin Configuration

### NRF24L01 Modules
- **Radio A**: CE=5, CSN=17
- **Radio B**: CE=16, CSN=4  
- **Radio C**: CE=15, CSN=2

### Push Buttons
- **Up**: GPIO 26
- **Down**: GPIO 32
- **Select**: GPIO 33
- **Right**: GPIO 27
- **Left**: GPIO 25

### Other Components
- **NeoPixel LED**: GPIO 14
- **SD Card CS**: GPIO 5
- **OLED Display**: I2C (SDA/SCL default pins)

## Core Functionality

### 1. Scanner (✅ Working - High Reliability)
**Purpose**: Scans the 2.4GHz frequency band to detect active channels and devices.

**How it works**:
- Uses NRF24L01 Radio A to sweep across 64 channels
- Samples each channel multiple times for accuracy
- Displays real-time spectrum analysis on OLED
- Saves scan history to EEPROM for persistence
- Visual feedback via purple NeoPixel during scanning

**Technical Details**:
- Channel range: 2.400-2.525 GHz (128 channels mapped to 64 display channels)
- Sampling rate: 50 samples per channel
- Uses RPD (Received Power Detector) register for signal detection
- Real-time graphical display with scrolling history

### 2. Analyzer (✅ Working - High Reliability)
**Purpose**: Provides detailed analysis of detected signals with visual spectrum display.

**How it works**:
- Similar to scanner but with enhanced visualization
- Shows signal strength across frequency spectrum
- Real-time bar graph display
- Uses carrier detection for signal analysis

**Technical Details**:
- 128-point frequency analysis
- Visual bar chart representation
- Carrier detection using RPD register
- Frequency labels: 1, 5, 10, 25, 50, 80, 128

### 3. WLAN Jammer (✅ Working - High Reliability)
**Purpose**: Jams wireless communication on selected channels for network robustness testing.

**How it works**:
- Uses all 3 NRF24 radios simultaneously for maximum effectiveness
- Configurable parameters: channel, power level, data rate
- Multiple jamming methods available
- Interactive menu system for configuration

**Technical Details**:
- **Channels**: 1-14 (WiFi channels)
- **Power Levels**: MIN, LOW, HIGH, MAX
- **Data Rates**: 250KBPS, 1MBPS, 2MBPS
- **Jamming Pattern**: 0xAA, 0x55 alternating pattern
- **Coverage**: Sweeps multiple frequencies per channel for effectiveness

### 4. Proto Kill Mode (✅ Working - High Reliability)
**Purpose**: Advanced multi-protocol jamming system targeting various wireless protocols.

**How it works**:
- Targets specific protocol frequency ranges
- Uses all 3 radios with different channel groups
- Protocol-specific channel hopping
- Visual protocol selection interface

**Supported Protocols**:
- **WiFi**: Channels 1-12
- **Bluetooth Classic**: 21 specific channels (32, 34, 46, 48, 50, 52, 0, 1, 2, 4, 6, 8, 22, 24, 26, 28, 30, 74, 76, 78, 80)
- **BLE**: 3 advertising channels (2, 26, 80)
- **USB Wireless**: Channels 40, 50, 60
- **Video TX**: Channels 70, 75, 80
- **RC Controllers**: Channels 1, 3, 5, 7
- **Zigbee**: Channels 11, 15, 20, 25
- **NRF24**: Channels 76, 78, 79

### 5. BLE Jammer (✅ Working - High Reliability)
**Purpose**: Specifically targets Bluetooth Low Energy devices.

**How it works**:
- Focuses on BLE advertising channels (2, 26, 80)
- Random channel hopping for maximum disruption
- Uses multiple radios for coverage
- Real-time status display

### 6. BLE Spoofer (✅ Working - Low Reliability)
**Purpose**: Simulates various BLE devices for testing and research.

**How it works**:
- Emulates 21 different device types (Apple, Samsung, Google)
- Configurable advertisement types
- Random MAC address generation
- Device-specific advertisement packets

**Supported Devices**:
- **Apple**: AirPods variants, Beats products (17 types)
- **Samsung**: Galaxy Watch 4/5/6 (3 types)
- **Google**: Smart Controller (1 type)

### 7. Sour Apple Attack (✅ Working - Low Reliability)
**Purpose**: Specialized attack targeting Apple device vulnerabilities.

**How it works**:
- Generates Apple-specific BLE advertisement packets
- Random action types and authentication tags
- Continuous advertisement with random MAC addresses
- Real-time packet display

### 8. BLE Scanner (✅ Working - High Reliability)
**Purpose**: Scans for nearby BLE devices and displays detailed information.

**How it works**:
- 5-second active scan duration
- Displays device name, address, and RSSI
- Detailed view for selected devices
- Scrollable device list

### 9. WiFi Scanner (✅ Working - High Reliability)
**Purpose**: Scans for WiFi networks with extended details.

**How it works**:
- Comprehensive WiFi network discovery
- Shows SSID, BSSID, RSSI, and channel
- Detailed view for network information
- Scrollable network list

### 10. WiFi Deauther (✅ Working - High Reliability)
**Purpose**: Sends deauthentication frames to disrupt client connections.

**How it works**:
- Scans for available networks
- Targets specific AP with deauth frames
- Real-time packet statistics
- Channel tracking and adaptation

**Technical Details**:
- Uses ESP32 WiFi raw frame transmission
- Deauth frame structure: 26 bytes
- Packet rate: ~10 packets/second
- Success rate monitoring
- Automatic channel following

### 11. Settings Menu (✅ Working)
**Purpose**: Device configuration and firmware management.

**Features**:
- NeoPixel LED enable/disable
- OLED brightness control (0-100%)
- Firmware update via SD card
- EEPROM settings persistence

## Component Compatibility Analysis

### 1. 2.4GHz NRF24L01 Module with PA+LNA SMA Wireless Transceiver Antenna
**✅ FULLY COMPATIBLE**

The nRFNT is specifically designed around NRF24L01 modules. The PA+LNA (Power Amplifier + Low Noise Amplifier) version with SMA antenna connector is actually **superior** to the basic modules currently used.

**Benefits of PA+LNA version**:
- **Increased Range**: Up to 1000m vs 100m for basic modules
- **Better Sensitivity**: -94dBm vs -82dBm
- **Higher Power Output**: +20dBm vs +0dBm
- **External Antenna**: SMA connector allows better antenna options
- **Same Pinout**: Direct replacement, no code changes needed

**Recommendation**: **Highly Recommended Upgrade** - Will significantly improve all functions.

### 2. ESP32 Development Board (Breadboard Compatible)
**✅ FULLY COMPATIBLE**

**For Breadboard Architecture, Recommended Options:**

**ESP32 DevKit V1 (38-pin) - BEST CHOICE**:
- Through-hole pins, breadboard-friendly
- All required GPIO pins available (2, 4, 5, 14, 15, 16, 17, 25, 26, 27, 32, 33)
- USB-C programming interface
- 3.3V regulator included
- Widely available and inexpensive

**ESP32 Wroom32U with IoT Breakout Board**:
- SMD module on breakout board with pins
- Usually includes additional features (sensors, connectors)
- More expensive but compact
- Verify all required pins are broken out

**NOT Recommended for Breadboard**:
- ❌ Bare ESP32 Wroom32U SMD module (requires soldering to breakout)

**Recommendation**: **ESP32 DevKit V1 (38-pin)** - Perfect for breadboard prototyping, all pins accessible.

### 3. Push Buttons
**✅ FULLY COMPATIBLE**

The nRFNT requires 5 push buttons for navigation:
- Up, Down, Left, Right, Select

**Requirements**:
- Momentary contact (normally open)
- 3.3V compatible
- Low current (microamp range)
- Debouncing handled in software

**Recommendation**: **Any standard momentary push buttons work** - Consider tactile switches for better user experience.

### 4. 128x64 OLED Display
**✅ FULLY COMPATIBLE**

The code is specifically written for SSD1306-based 128x64 OLED displays.

**Requirements**:
- SSD1306 controller
- I2C interface (default ESP32 I2C pins)
- 128x64 resolution
- 3.3V or 5V compatible

**Recommendation**: **Standard SSD1306 OLED modules work perfectly** - Widely available and inexpensive.

### 5. TP4056 Battery Charging Module
**✅ FULLY COMPATIBLE**

TP4056 is a standard lithium battery charging IC, perfect for portable operation.

**Features**:
- Charges single-cell Li-ion/Li-Po batteries
- USB input (5V)
- Charging current: up to 1A (adjustable)
- Built-in protection (over-charge, over-discharge, over-current)
- LED charging indicators

**Recommendation**: **Excellent choice** - Provides safe battery charging and power management.

### 6. SD Module (Which One?)
**✅ COMPATIBLE - SPI Interface Required**

The nRFNT uses SD card for firmware updates. Based on the code (SD_CS_PIN = 5):

**Requirements**:
- SPI interface
- 3.3V compatible
- CS pin connected to GPIO 5
- Standard SD card socket

**Recommended SD Modules**:
- **Micro SD Card Module** - Most common, uses SPI
- **SD Card Breakout Board** - For full-size SD cards
- **ESP32 with built-in SD slot** - Some ESP32 boards include SD slots

**Important**: Ensure the module operates at 3.3V and uses SPI interface (not SDIO).

**Recommendation**: **Micro SD Card Module with SPI interface** - Most versatile and widely available.

## Power Consumption Analysis

**Estimated Power Draw**:
- ESP32: ~240mA (active), ~10mA (sleep)
- 3x NRF24L01 PA+LNA: ~115mA each (transmitting), ~13mA each (receiving)
- OLED Display: ~20mA
- NeoPixel LED: ~60mA (full brightness white)
- **Total Active (all radios TX)**: ~685mA
- **Total Scanning**: ~300mA

**Battery Recommendations**:
- **Minimum**: 2000mAh Li-Po for 3-4 hours operation
- **Recommended**: 3000-5000mAh for full-day use
- **Voltage**: 3.7V single-cell Li-Po/Li-ion

## Assembly Recommendations

### PCB Design Considerations
1. **Power Supply**: Ensure adequate current capacity (1A minimum)
2. **Decoupling**: Add capacitors near each NRF24 module
3. **Antenna Placement**: Keep antennas away from digital circuits
4. **Ground Plane**: Solid ground plane for RF performance
5. **Shielding**: Consider RF shielding between modules

### Enclosure Requirements
1. **RF Transparent**: Plastic enclosure for antenna performance
2. **Ventilation**: ESP32 and PA+LNA modules generate heat
3. **Access**: Buttons, display, charging port, SD card access
4. **Size**: Accommodate battery and all components

## Limitations and Considerations

### Current Limitations
1. **Multiple NRF24 Power Draw**: Running 3 modules simultaneously may cause power issues
2. **Range Limitations**: Most effective at short range
3. **Device Variability**: Different devices react differently to jamming
4. **Legal Considerations**: Jamming devices may be illegal in many jurisdictions

### Performance Notes
- **Scanner/Analyzer**: Most reliable functions
- **Jammers**: Effectiveness varies by target device and environment  
- **BLE Spoofer/Sour Apple**: Limited compatibility, best for controlled testing
- **WiFi Deauther**: Highly effective for security testing

## Legal and Ethical Considerations

**⚠️ IMPORTANT WARNING**: 
- Jamming wireless communications may be **illegal** in many countries
- Use only in controlled environments or with proper authorization
- Intended for **security research and education** only
- Check local laws and regulations before use
- Obtain proper permissions for penetration testing

## Breadboard Assembly Guide

### Power Distribution
- Use breadboard power rails for 3.3V and GND
- ESP32 DevKit provides 3.3V output for other modules
- Consider external 3.3V regulator if current draw is high

### Wiring Considerations
- Keep NRF24L01 wires short (< 10cm) to minimize interference
- Use solid core wire for breadboard connections
- Add 10µF capacitors near each NRF24L01 module for power stability
- Separate analog and digital grounds if possible

### Module Placement
- Place NRF24L01 modules away from ESP32 to reduce interference
- Orient antennas in different directions for better coverage
- Keep OLED display away from radio modules

## Conclusion

The nRFNT is a well-designed wireless security research platform with comprehensive functionality. All the components you've listed are **compatible** and will work well with the existing design. The PA+LNA NRF24L01 modules will actually **improve performance significantly**.

**Recommended Breadboard Build Configuration**:
- **ESP32 DevKit V1 (38-pin)** - breadboard-friendly with all pins
- 3x NRF24L01+PA+LNA with SMA antennas
- 5x tactile push buttons
- 128x64 SSD1306 OLED display
- TP4056 charging module with 3000mAh+ Li-Po battery
- Micro SD card module (SPI interface)
- Large breadboard (830 tie-points recommended)
- Jumper wires and 10µF capacitors

This combination will provide excellent performance for wireless security research and education while being easy to prototype and modify.