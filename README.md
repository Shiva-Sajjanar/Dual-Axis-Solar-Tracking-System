# ☀️ Dual Axis Solar Tracking System

## 📌 Project Overview

This project presents an Arduino-based dual axis solar tracking system designed to maximize solar energy capture by continuously aligning the panel with the sun’s position.

---

## 🎯 Objective

To improve the efficiency of solar panels by dynamically adjusting their orientation based on sunlight intensity.

---

## 🛠️ Components Used

* Arduino UNO
* LDR Sensors (4 units)
* Servo Motors (2 units – horizontal & vertical movement)
* Resistors
* Solar Panel
* Breadboard & Jumper Wires

---

## ⚙️ Working Principle

* LDR sensors detect sunlight intensity from different directions
* Arduino compares sensor values
* Based on difference, it rotates servo motors
* Panel moves in both axes (horizontal + vertical)
* Ensures maximum sunlight exposure throughout the day

---

## 💻 Code

```cpp
#include <Servo.h>

Servo servoX;
Servo servoY;

int ldr1 = A0;
int ldr2 = A1;
int ldr3 = A2;
int ldr4 = A3;

int posX = 90;
int posY = 90;

void setup() {
  servoX.attach(9);
  servoY.attach(10);
}

void loop() {
  int val1 = analogRead(ldr1);
  int val2 = analogRead(ldr2);
  int val3 = analogRead(ldr3);
  int val4 = analogRead(ldr4);

  int avgTop = (val1 + val2) / 2;
  int avgBottom = (val3 + val4) / 2;
  int avgLeft = (val1 + val3) / 2;
  int avgRight = (val2 + val4) / 2;

  if (avgTop > avgBottom) posY++;
  else if (avgBottom > avgTop) posY--;

  if (avgLeft > avgRight) posX++;
  else if (avgRight > avgLeft) posX--;

  posX = constrain(posX, 0, 180);
  posY = constrain(posY, 0, 180);

  servoX.write(posX);
  servoY.write(posY);

  delay(100);
}
```

---

## 📊 Output

* Solar panel automatically tracks sunlight
* Moves in both horizontal and vertical directions
* Improves energy efficiency compared to fixed panels

---
## 🚀 Features

* Dual-axis tracking (horizontal + vertical)
* Real-time sunlight detection
* Improved solar efficiency
* Low-cost implementation

---

## 📈 Future Improvements

* Add IoT monitoring system
* Use MPPT for better efficiency
* Add battery storage system
* Use stepper motors for higher precision

---

## 🎓 Learning Outcomes

* Embedded systems programming
* Sensor interfacing (LDR)
* Servo motor control
* Real-world renewable energy application

---

## 🤝 Contributing

Feel free to fork and improve this project.

---

## 📄 License

This project is open-source under the MIT License.
