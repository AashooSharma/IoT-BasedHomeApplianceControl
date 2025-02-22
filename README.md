# IoT-BasedHomeApplianceControl
IoT nexus event 
Aapke **"IoT-Based Home Appliance Control"** project me **PIR Motion Sensor, Ultrasonic Sensor, LDR, aur RFID Module** implement karne ke liye **NodeMCU ESP8266** ka circuit connection **(Wiring Diagram)** kuch is tarah hoga:  

---

## **🛠️ Required Components:**  
1. **NodeMCU ESP8266**  
2. **PIR Motion Sensor (HC-SR501)**  
3. **Ultrasonic Sensor (HC-SR04)**  
4. **LDR (Light Dependent Resistor) + 10KΩ Resistor**  
5. **RFID RC522 Module**  
6. **Relay Module (For Appliance Control)**  
7. **Jumper Wires**  
8. **5V Power Supply**

---

## **🔌 Circuit Connection:**

### **1️⃣ PIR Motion Sensor (HC-SR501) Connection**
| **PIR Sensor Pin** | **NodeMCU Pin** |
|-------------------|----------------|
| VCC (5V)         | Vin (NodeMCU)   |
| GND              | GND             |
| OUT              | D2 (GPIO4)      |

📌 **Function:** Motion detect hone par relay/light ON ho jayegi.

---

### **2️⃣ Ultrasonic Sensor (HC-SR04) Connection**
| **HC-SR04 Pin** | **NodeMCU Pin**  |
|----------------|----------------|
| VCC (5V)      | Vin (NodeMCU)   |
| GND           | GND             |
| TRIG          | D5 (GPIO14)     |
| ECHO          | D6 (GPIO12)     |

📌 **Function:** Distance measure karega, aur door automation ya water level monitoring ke liye use hoga.

---

### **3️⃣ LDR (Light Sensor) Connection**
| **LDR & Resistor Pin** | **NodeMCU Pin** |
|------------------------|----------------|
| LDR **One End**       | 3.3V (NodeMCU)  |
| LDR **Other End**      | A0 (Analog Pin) |
| Resistor (10KΩ)       | GND (NodeMCU)   |

📌 **Function:** Room brightness check karega, aur automatic lights ON/OFF karega.

---

### **4️⃣ RFID Module (RC522) Connection**
| **RC522 Pin** | **NodeMCU Pin**  |
|--------------|----------------|
| VCC         | 3.3V (NodeMCU)  |
| RST         | D1 (GPIO5)      |
| GND         | GND             |
| MISO        | D6 (GPIO12)     |
| MOSI        | D7 (GPIO13)     |
| SCK         | D5 (GPIO14)     |
| SS (SDA)    | D8 (GPIO15)     |

📌 **Function:** RFID card scan karke door ya appliance control karega.

---

### **5️⃣ Relay Module (For Appliance Control)**
| **Relay Pin** | **NodeMCU Pin** |
|--------------|----------------|
| VCC         | Vin (5V)        |
| GND         | GND             |
| IN          | D3 (GPIO0)      |

📌 **Function:** Motion, RFID ya light detection ke basis pe fan/light ON/OFF karega.

---

## **💡 Working Features:**
✅ **Motion Detection** → PIR detect karega aur **light/fan ON** karega.  
✅ **Ultrasonic Sensor** → Distance detect karega aur **door ya water level system automate** karega.  
✅ **LDR Sensor** → Room brightness detect karega aur **lights ON/OFF** karega.  
✅ **RFID Module** → Smart card se **appliance ya door control** hoga.  
✅ **Relay Module** → Appliances (fan, light, AC) control karega.  

---

