Yeh raha **NodeMCU ESP8266 ka Arduino code** jo **PIR Motion Sensor, Ultrasonic Sensor, LDR, RFID Module, aur Relay** ke liye kaam karega.  

Aap is code ko **Arduino IDE** me upload kar sakte hain.  

---

### **📜 Features in Code:**
✅ **Motion Detection (PIR Sensor)** → Light/Fan ON karega.  
✅ **Distance Measurement (Ultrasonic Sensor)** → Door automation ya water level ke liye.  
✅ **Light Detection (LDR Sensor)** → Room brightness ke basis pe light control.  
✅ **RFID Access Control (RC522 Module)** → Card scan karne par appliance ON/OFF.  
✅ **Relay Control** → Appliances (Fan/Light/AC) ON/OFF karne ke liye.  

---

### **🚀 Complete Arduino Code:**
```cpp
#include <ESP8266WiFi.h>
#include <SPI.h>
#include <MFRC522.h>

// PIR Motion Sensor
#define PIR_PIN D2  

// Ultrasonic Sensor
#define TRIG_PIN D5  
#define ECHO_PIN D6  

// LDR Sensor
#define LDR_PIN A0  

// RFID Module
#define SS_PIN D8
#define RST_PIN D1
MFRC522 mfrc522(SS_PIN, RST_PIN);

// Relay (Appliance Control)
#define RELAY_PIN D3  

void setup() {
  Serial.begin(115200);
  pinMode(PIR_PIN, INPUT);
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(LDR_PIN, INPUT);
  pinMode(RELAY_PIN, OUTPUT);
  digitalWrite(RELAY_PIN, LOW);

  SPI.begin();
  mfrc522.PCD_Init();
  Serial.println("RFID Scanner Ready...");
}

void loop() {
  // ✅ PIR Motion Detection
  if (digitalRead(PIR_PIN) == HIGH) {
    Serial.println("Motion Detected! Turning ON Light...");
    digitalWrite(RELAY_PIN, HIGH);
    delay(5000);
  } else {
    digitalWrite(RELAY_PIN, LOW);
  }

  // ✅ Ultrasonic Sensor - Distance Measurement
  long duration;
  int distance;
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);
  duration = pulseIn(ECHO_PIN, HIGH);
  distance = duration * 0.034 / 2;
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if (distance < 10) {
    Serial.println("Object Detected! Activating Relay...");
    digitalWrite(RELAY_PIN, HIGH);
    delay(3000);
  } else {
    digitalWrite(RELAY_PIN, LOW);
  }

  // ✅ LDR Sensor - Light Detection
  int lightValue = analogRead(LDR_PIN);
  Serial.print("LDR Value: ");
  Serial.println(lightValue);

  if (lightValue < 500) {
    Serial.println("Low Light Detected! Turning ON Light...");
    digitalWrite(RELAY_PIN, HIGH);
  } else {
    digitalWrite(RELAY_PIN, LOW);
  }

  // ✅ RFID Module - Card Scanning
  if (mfrc522.PICC_IsNewCardPresent() && mfrc522.PICC_ReadCardSerial()) {
    Serial.println("RFID Card Detected!");
    Serial.print("UID: ");
    for (byte i = 0; i < mfrc522.uid.size; i++) {
      Serial.print(mfrc522.uid.uidByte[i] < 0x10 ? "0" : "");
      Serial.print(mfrc522.uid.uidByte[i], HEX);
      Serial.print(" ");
    }
    Serial.println();

    Serial.println("Access Granted! Turning ON Appliance...");
    digitalWrite(RELAY_PIN, HIGH);
    delay(5000);
    digitalWrite(RELAY_PIN, LOW);
  }

  delay(1000);
}
```

---

### **💡 How It Works:**
1️⃣ **Motion Detect (PIR Sensor)** → Jab koi move karega, to **light/fan ON** ho jayega.  
2️⃣ **Distance Detect (Ultrasonic Sensor)** → **Agar distance <10cm hai**, to **relay ON** hoga.  
3️⃣ **Light Detect (LDR Sensor)** → **Andhera hone par light ON** ho jayegi.  
4️⃣ **RFID Card Scan** → **Card scan karne par appliance control** hoga.  
5️⃣ **Relay Control** → **Fan/Light ko ON/OFF** karega.  

---

### **📌 Next Steps:**
1. Kya aapko **Blynk ya Web Dashboard** bhi add karna hai?  
2. Kya aapko **Circuit Diagram (Fritzing)** bhi chahiye?  

Agar aapko kuch **extra features ya improvements** chahiye to batao!
