# 👟 Smart Shoe Using Arduino

An IoT-based smart shoe designed using Arduino and ultrasonic sensors to assist visually impaired individuals. The shoe detects obstacles and alerts the user using a buzzer, enhancing mobility and safety.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Components Used](#components-used)
- [Working Principle](#working-principle)
- [Circuit Diagram](#circuit-diagram)
- [Code](#code)
- [Advantages](#advantages)
- [Conclusion](#conclusion)
- [References](#references)
- [Credits](#credits)

---

## 🧠 Overview

The project aims to provide acoustic assistance to visually impaired people by alerting them to obstacles in their path using ultrasonic sensors and a buzzer. This Arduino-powered wearable helps users navigate safely and independently, whether indoors or outdoors.

---

## ✨ Features

- Obstacle detection using HC-SR04 sensor
- Buzzer alert on detecting nearby obstacles
- Simple and low-cost wearable solution
- User-friendly and lightweight
- Applicable for both indoor and outdoor environments

---

## 🔧 Components Used

| Component                 | Quantity |
|--------------------------|----------|
| Arduino UNO              | 1        |
| HC-SR04 Ultrasonic Sensor| 1        |
| 9V Battery               | 1        |
| Battery Connector        | 1        |
| Jumper Wires             | As needed|
| Rocker Switch            | 1        |
| Buzzer                   | 1        |

---

## ⚙️ Working Principle

- The ultrasonic sensor emits sound waves and receives echoes reflected from nearby obstacles.
- The Arduino calculates the distance based on the time delay.
- If an obstacle is detected within a threshold (e.g., 50 cm), the buzzer is activated to alert the user.
- When the path is clear, the buzzer turns off.

---

## 🔁 Circuit Diagram

> 📷 https://github.com/BejjamCharitha/Smart-Shoe-Blind-Navigation/blob/main/Circuit-diagram.jpeg

Connections:
- **HC-SR04**
  - VCC → 5V
  - GND → GND
  - TRIG → Pin 6
  - ECHO → Pin 7
- **Buzzer** → Pin 3 and GND
- **Battery Connector** → VIN and GND

---

## 💻 Code

```cpp
const int TRIG_PIN   = 6;
const int ECHO_PIN   = 7;
const int BUZZER_PIN = 3;
const int DISTANCE_THRESHOLD = 50;

float duration_us, distance_cm;

void setup() {
  Serial.begin(9600);
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(BUZZER_PIN, OUTPUT);
}

void loop() {
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  duration_us = pulseIn(ECHO_PIN, HIGH);
  distance_cm = 0.017 * duration_us;

  if (distance_cm < DISTANCE_THRESHOLD)
    digitalWrite(BUZZER_PIN, HIGH);
  else
    digitalWrite(BUZZER_PIN, LOW);

  Serial.print("Distance: ");
  Serial.print(distance_cm);
  Serial.println(" cm");

  delay(500);
}

✅ Advantages
  Easy to use and low maintenance

  Reduces chances of collision for visually impaired individuals

  Compact and lightweight design

  Cost-effective solution

  Can be enhanced with GPS or Bluetooth for advanced tracking

📚 References
  IJCRT Smart Shoe Paper

  ResearchGate Article

  YouTube Demo

👩‍💻 Credits
Project by:
🧑‍🎓 BEJJAM CHARITHA (22BQ1A4710)
Department of CSE (IoT, Cybersecurity including Blockchain Technology)
Vasireddy Venkatadri Institute of Technology (VVIT), Guntur

Guided by:
👨‍🏫 Mr. K. Ravi Kumar, Associate Professor


