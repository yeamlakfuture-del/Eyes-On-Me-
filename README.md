# Eyes-On-Me

# Smart Shoulder Assistive Device 

## Overview of EyesOnMe

This project is a wearable assistive device designed to help visually impaired individuals detect obstacles in front of them. It is worn around the shoulders to provide a wider and higher field of detection while being confortable and easy to use compared to traditional tools.

Instead of using sound, the device uses **vibration** to alert the user. This makes the system more private, less disruptive, and more comfortable in public environments.

---

##  Problems

Many visually impaired individuals rely on canes or assistance to navigate. While helpful, these tools may not detect obstacles at upper body level (such as walls, signs, or objects at chest/head height).

Additionally, sound-based alert systems can be distracting or uncomfortable for both the user and people nearby.

---

##  Solutions

This project provides a **wearable, shoulder-mounted obstacle detection system** that:

* Detects obstacles in real time using an ultrasonic sensor
* Uses vibration instead of sound for alerts
* Provides intuitive feedback based on distance
* Is simple, affordable, and easy to build

---

##  How It Works

1. The ultrasonic sensor continuously measures the distance to objects in front of the user.
2. The Arduino processes this data.
3. Based on the distance, the system responds with vibration:

* **Far (>120 cm)** → No vibration
* **Medium (80–120 cm)** → Pulsing vibration
* **Close (<40-80 cm)** → Continuous vibration

4. The user can react accordingly to avoid obstacles.

---

##  Components (BOM)

| Component                   | Quantity | Source            |    Purpose                           |    
| --------------------------- | -------- | ----------------- |  ----------------------------------  |
| Arduino Uno                 | 1        | School            | Main microcontroller                 |
| Ultrasonic Sensor (HC-SR04) | 1        | School            | Distance detection                   |
| Cylindrical vibration motor | 1        | Purchase          | Haptic feedback system               |
| Jumper Wires                | Multiple | School            | Electrical connections               |
| 1kΩ Resistor                | 1        | School            | Limits current to transistor base    |
| Breadboard                  | 1        | School            | Prototyping circuit                  |
| NPN Transistor  2N2222      | 1        | Purchase          | Motor switching control              |
| Flyback Diode (1N4007)      | 1        | Purchase          | Protects circuit from voltage spikes |
| USB Cable                   | 1        | Personal          | Programming and power                |
| USB Power Bank              | 1        | Purchase          | Portable wearable power source       |

 
---

##  Wiring

Typical connections:

Ultrasonic Sensor (HC-SR04)

VCC → 5V (Arduino)

GND → GND (Arduino)

TRIG → Digital Pin 9

ECHO → Digital Pin 10

---

## Cylindrical Vibration Motor (CVM)

The CVM is controlled using an NPN transistor (e.g., 2N2222) because it requires more current than an Arduino digital pin can safely provide.

CVM (+) → +5V external power supply (or Arduino 5V for testing)

CVM (–) → Collector of NPN transistor

Emitter of transistor → GND

Base of transistor → Digital Pin 8 (through 1kΩ resistor)

---

## Power System
Arduino is powered via USB or USB power bank
CVM is powered from a 5V supply but controlled via transistor switching
All grounds (Arduino GND and motor GND) must be connected together (common ground)

---

##  Firmware

The Arduino code reads distance from the ultrasonic sensor and controls the vibration motor based on proximity.

* Located in `/code/main.ino`
* Uses simple distance thresholds
* Designed for real-time feedback

---

##  How to Use

1. Power the device using USB.
2. Wear the device around your shoulders with the sensor facing forward.
3. Walk normally.
4. Feel the vibration feedback:

   * No vibration → safe
   * Pulsing → caution
   * Continuous → obstacle very close

---

##  Design

* The system is mounted on a shoulder strap.
* The ultrasonic sensor is positioned facing forward.
* The vibration motor is placed where the user can feel it clearly (shoulder).
* Components are securely attached using a stable structure (not loose wiring).

(See `/images/` and `/hardware/` for visuals)

---

##  Future Improvements

* Add multiple sensors for left/right detection
* Improve wearable design with custom casing
* Add voice feedback as an optional feature
* Integrate wireless connectivity (ESP32)
* Add AI-based assistance features
* Improve the wearable design with 3D printing
* Make it close to a mini AI companion
* Add map aweareness

---

##  Why I Built This

I wanted to create somethig affordable and a mini companion to visually impaired people giving the independence and allow them to maneuver from one place to another. This project focuses on practical usability by using vibration instead of sound, making it more suitable for real-world environments.
And this passion was driven from my school, which was an inclusive school designed to help blind and deaf and I had a friend that is visually impaired and was not able to go from one place to another and he was allways bumping with walls and poles. So i thought if i was able to give a solution for all blind people and my friend. So i started this project and i was not alone he was giving me adviseing me and give so recommendations all along my journey.

---
 
 # Zine

 


    
---

##  Author

Name: Yeamlak Fekadu

Age: 14

Country: Ethiopia

Grade: 8

---

