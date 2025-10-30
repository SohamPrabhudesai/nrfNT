

## Review 1: Project Proposal

  

**Course:** ECS 3001

**Team Members:**

- 23bce7761 - Soham Prabhudesai

- 23bce7478 - Chirag Tharad

- 23bce7679 - Alam Divya Sree

- 23bce7223 - Shaksham Pathak

- 23bce7736 - Archisha Das

- 23bce7197 - Ira Aditi

  

**Advisor:** Rajan D Lanjekar

**Date:** 08/08/2025

**Institution:** VIT-AP University

  

---

  

## 1. Identification of the Problem and Title of the Project

  

### Project Title:

**nRFNT (nRF Network Tool) -Network Tool for Analysis, and Security testing of WiFi, Bluetooth and 2.4 G bands**

  

### Problem Identification:

Current wireless security education lacks accessible, hands-on tools that can demonstrate multiple attack vectors across different protocols. Students and security professionals need practical experience with:

  

- RF spectrum analysis and signal detection

- Wireless protocol vulnerabilities

- Jamming and interference techniques

- BLE security weaknesses

- WiFi deauthentication attacks

  

**Existing Solutions Limitations:**

- High cost barriers for educational use

- Single-protocol focus (WiFi only, Bluetooth only)

- Complex setup requirements

- Limited educational documentation

  

**Our Solution:**

An affordable, comprehensive wireless security tool specifically designed for educational use, providing multi-protocol support in a single device at <₹2000 cost.

  

---

  

## 2. Identification of Required Components

  

### Core Hardware Components:

  

| Component                | Specification                 | Quantity                 | Cost (Rs)   | Purpose                                          |
| ------------------------ | ----------------------------- | ------------------------ | ----------- | ------------------------------------------------ |
| **ESP32 DevKit V1**      | 38-pin, WiFi+BT               | 1                        | 343         | Main controller, WiFi/BLE functions              |
| **nRF24L01+PA+LNA**      | 2.4GHz, +20dBm, SMA antenna   | 3                        | 135x3 = 405 | RF analysis, jamming, protocol testing<br>1 each |
| **128x64 OLED Display**  | SSD1306, I2C interface        | 1                        | 220         | User interface, status display                   |
| **Tactile Push Buttons** | 12x12mm, momentary contact    | 10 (5 needed, 5 backups) | 3.68x10=37  | Navigation and control                           |
| **Breadboard**           |                               |                          | -           | Prototyping platform                             |
| **Jumper Wires**         | Male-to-male, various lengths | 40                       | -           | Connections                                      |
| **Total**:               |                               |                          | 1005        |                                                  |




### Software Requirements:

- **IDE:** Arduino IDE 2.x

- **Framework:** Arduino Core for ESP32

- **Libraries:** RF24, U8g2, WiFi, BLE

- **Version Control:** Git

  


  

---

  

## 3. Plan of Action

  

### Phase 1: Research & Design 

- **Literature Review:** Study existing wireless security tools and vulnerabilities

- **Component Research:** Finalize component specifications and suppliers

- **System Architecture:** Design hardware connections and software structure

  

### Phase 2: Hardware Assembly

- **Component Procurement:** Order all required components

- **Breadboard Assembly:** Build initial prototype

- **Power System:** Implement battery charging and power management

- **Basic Testing:** Verify component functionality and connections

  

### Phase 3: Software Development

- **Core Framework:** Develop menu system and hardware abstraction

- **RF Modules:** Implement scanner, analyzer, and jammer functions

- **WiFi Modules:** Develop network scanner and deauth capabilities

- **BLE Modules:** Create device scanner and spoofer functions

- **User Interface:** Design intuitive OLED-based interface

  

### Phase 4: Integration & Testing

- **System Integration:** Combine all modules into unified firmware

- **Functional Testing:** Verify all features work as designed

- **Performance Testing:** Measure range, sensitivity, and effectiveness

- **Safety Testing:** Ensure compliance with power and emission limits

  


  

---

  

## 4. Timeline of Progress

  

### Detailed Project Timeline:

| Week | Phase | Deliverables | Team Responsibilities |
|------|-------|--------------|----------------------|
| **1-2** | Research & Design | System architecture, component list | All team members research |
| **3** | Procurement | All components ordered | Soham, Chirag - procurement |
| **4** | Hardware Assembly | Working breadboard prototype | Divya, Shaksham - assembly |
| **5** | Core Software | Menu system, hardware drivers | Archisha, Ira - core development |
| **6** | RF Development | Scanner and analyzer modules | Soham, Divya - RF programming |
| **7** | WiFi Development | Network scanner, deauth module | Chirag, Shaksham - WiFi features |
| **8** | BLE Development | BLE scanner and spoofer | Archisha, Ira - BLE features |
| **9** | Integration | Unified firmware build | All team members |
| **10** | Testing | Performance validation | All team members |
| **11** | Documentation | Technical documentation | Soham, Archisha - documentation |
| **12** | Educational Materials | Tutorials and guides | Chirag, Divya - educational content |
| **13** | Demo Preparation | Presentation materials | Shaksham, Ira - presentation |
| **14** | Final Presentation | Project demonstration | All team members |


### Project Gantt Chart:

```
Task/Week                    1  2  3  4  5  6  7  8  9 10 11 12 13 14
────────────────────────────────────────────────────────────────────
Research & Design           ██ ██
Component Procurement             ██
Hardware Assembly                   ██
Core Software Development              ██
RF Module Development                     ██
WiFi Module Development                      ██
BLE Module Development                          ██
System Integration                                ██
Testing & Validation                                ██
Technical Documentation                               ██
Educational Materials                                   ██
Demo Preparation                                          ██
Final Presentation                                           ██

Milestones:
● Week 4:  Hardware Prototype Complete
● Week 8:  All Software Modules Complete  
● Week 10: System Integration Complete
● Week 12: Documentation Complete
● Week 14: Project Delivery
```
  

### Critical Path Analysis:

**Primary Dependencies:**
- Hardware assembly must complete before software integration
- Component procurement blocks hardware assembly
- Core software framework required before module development
- All modules must complete before system integration

**Parallel Development Opportunities:**
- RF, WiFi, and BLE modules can be developed simultaneously
- Documentation can begin alongside module development
- Educational materials can be prepared during testing phase

  

### Risk Mitigation:

- **Component Delays:** Order components early with backup suppliers

- **Technical Challenges:** Allocate buffer time for debugging

- **Team Coordination:** Weekly progress meetings and clear task assignments

- **Scope Creep:** Maintain focus on core objectives, document future enhancements

  

---


## 5. Comparative analysis



| Tool                        | Cost (Rs.) | Protocols      | Range     | Educational Use       |
| --------------------------- | ---------- | -------------- | --------- | --------------------- |
| **HackRF One**              | 25,000+    | All RF         | Variable  | Complex               |
| **WiFi Pineapple**          | 15,000+    | WiFi only      | 300m      | Moderate              |
| **Ubertooth**               | 8000+      | Bluetooth Only | 100m      | Moderate              |
| **RTL-SDR**                 | 1500+      | RX only        | N/A       | Good                  |
| **Flipper Zero**            | 18,000+    | Multi          | 100m      | Good                  |
| **nRFNT**<br>(This Project) | 1005       | Multi          | 800-1000m | Excellent <br>(D.I.Y) |

## **Key Advantages of nRFNT:**

### **Cost Advantage:**

- **95% cheaper** than nearest competitor
    
- **25x cheaper** than HackRF One
    
- **15x cheaper** than WiFi Pineapple


### **Educational Advantage:**

- **Open source** - students can modify and learn
    
- **Arduino ecosystem** - familiar development environment
    
- **Comprehensive documentation** - built for education
    
- **Breadboard design** - visible connections for learning
    

### **Technical Advantage:**

- **Multi-protocol** in single device
    
- **1km range** - better than most commercial tools
    
- **Real-time display** - immediate feedback
    
- **Customizable** - add new protocols easily




## Expected Outcomes

  

### Technical Deliverables:

- Fully functional wireless security research platform

- Comprehensive source code with documentation

- Performance benchmarks and validation results

  

### Educational Impact:

- Affordable platform for wireless security education

- Hands-on learning experience for students

- Open-source design for community improvement

- Integration potential with cybersecurity curricula

  

### Success Metrics:

- **Cost Target:** <₹2000 total project cost

- **Functionality:** Multi-protocol support (WiFi, BLE, 2.4GHz)

- **Performance:** 800m+ range, 95%+ accuracy

  

---

  

**Document Status:** Review 1 Submission

**Next Review:** Review 2 (Date: TBD)

