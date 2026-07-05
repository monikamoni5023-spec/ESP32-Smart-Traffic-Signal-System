# ESP32-Smart-Traffic-Signal-System
AI-based Smart Traffic Signal Management System using ESP32 with adaptive signal timing, emergency vehicle priority, and accident detection — simulated on Wokwi.
🚦 AI Based Smart Traffic Signal Management System using ESP32
An IoT-based smart traffic signal system that adapts signal timing based on simulated vehicle density, gives priority to emergency vehicles, and simulates accident detection with automated alerts. Built and simulated using ESP32 on Wokwi.
📌 Objective
To design a traffic management system that:
Detects traffic density and adjusts signal timing accordingly
Gives priority to emergency vehicles (ambulance, fire truck, etc.)
Detects and responds to accident scenarios with alerts
🛠 Components Used
Component
Purpose
ESP32
Main Controller
12 LEDs
Traffic Lights (Red, Yellow, Green × 4 Roads)
4 Push Buttons
Traffic Sensor Simulation
OLED Display (SSD1306, I2C)
Status Display
Servo Motor
Automatic Barrier Gate
Buzzer
Emergency/Accident Alert
Resistors (220-330Ω for LEDs, 10kΩ for buttons)
Current limiting / Pull-down
📍 Pin Connections
Road
Red LED
Yellow LED
Green LED
Button
A
GPIO 13
GPIO 12
GPIO 14
GPIO 32
B
GPIO 27
GPIO 26
GPIO 25
GPIO 33
C
GPIO 19
GPIO 18
GPIO 5
GPIO 34
D
GPIO 2
GPIO 16
GPIO 17
GPIO 35
Module
Pin
ESP32 GPIO
OLED
SDA / SCL
21 / 22
Servo
Signal
4
Buzzer
+
15
⚙️ Working Principle
Startup – ESP32 boots, OLED shows "SMART TRAFFIC SYSTEM"
Normal Cycle – Roads A → B → C → D get Green signal in round-robin order. Button press on a road simulates vehicle detection, extending its Green time.
Emergency Mode – Holding any button for 1.5+ seconds triggers emergency priority for that road: all other roads turn Red, barrier opens, buzzer beeps once.
Accident Mode – Pressing two or more buttons simultaneously triggers accident simulation: all roads turn Red, barrier closes, buzzer sounds continuously, OLED displays "ACCIDENT - HELP SENT".
Barrier Gate – Servo opens (90°) on Green signal and closes (0°) on Red signal.
🧪 Simulation
This project was built and tested using Wokwi, an online ESP32/Arduino simulator.
Test Files Included
smart_traffic_system.ino – Main project code
led_test.ino – Verifies all 12 traffic LEDs
servo_test.ino – Verifies barrier gate servo
buzzer_test.ino – Verifies buzzer wiring
button_test.ino – Verifies all 4 sensor buttons
📚 Libraries Required
ESP32Servo
Adafruit GFX Library
Adafruit SSD1306
🎓 Key Learnings
GPIO strapping pin behavior and input-only pins (GPIO 34/35) on ESP32
Pull-up vs external pull-down resistor design for buttons
Non-blocking programming using millis() for real-time multi-event handling
Integrating multiple sensors and actuators (LEDs, servo, buzzer, OLED) into one coordinated embedded system
🚀 Future Scope
Replace push buttons with ultrasonic/IR sensors or camera-based vehicle detection
RFID/GPS-based automatic emergency vehicle recognition
Cloud dashboard for real-time traffic monitoring (Firebase/AWS IoT)
SMS/API-based automatic alert to traffic police/ambulance on accident detection
👤 Author
Feel free to connect and share feedback!
