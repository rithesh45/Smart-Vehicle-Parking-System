# Smart Parking System Using Arduino 🚗

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Arduino](https://img.shields.io/badge/Arduino-Compatible-success)](https://www.arduino.cc/)

An automated parking system using Arduino, IR sensors, and an LCD display to manage parking slots efficiently.

![Demo](Images/system_demo.jpg)

---

## 📋 Features
- Real-time parking slot monitoring
- Automated entry/exit with servo motors
- LCD display for slot availability
- Cost-effective and scalable

## 🛠️ Installation & Setup
### Hardware Components
- Arduino Uno
- IR Sensors (x4)
- Servo Motor (SG90)
- 16x2 LCD Display
- Jumper Wires

### Software
1. Install [Arduino IDE](https://www.arduino.cc/en/software).
2. Upload the code from `Code/smart_parking.ino`.

### Pin Connections
| Component | Arduino Pin |
|-----------|-------------|
| IR Sensor 1 | D2         |
| Servo Motor | D9         |
| LCD SDA     | A4         |

## 🎥 Working Mechanism
1. IR sensors detect vehicle entry/exit.
2. Servo motor opens/closes the gate.
3. LCD updates available slots in real-time.

## 📸 Results
![Output](Images/working_mechanism.gif)

## 🚀 Future Enhancements
- Mobile app for remote monitoring
- IoT-based data tracking
- Smart payment integration

## 👥 Contributors
- [Your Name](https://github.com/yourusername)

## 📚 References
1. [IoT-Based Smart Parking Systems](https://example.com/research-paper)

## 📝 License
MIT License. See [LICENSE](LICENSE) for details.

**Demo Video ▶️**: [YouTube Link](https://youtube.com/example)
