# IoT-Home-Automation-ESP32
IoT-based Smart Home Automation System using ESP32 and Blynk for remote appliance control over WiFi.

# IoT Home Automation System using ESP 32

## Project Overview
An IoT-based Home Automation System that allows users to control electrical appliances remotely using a smartphone over WiFi. The system uses an ESP32 microcontroller and relay modules to automate home devices like lights, fans, and sockets.
This project demonstrates Embedded Systems, IoT Communication, Mobile App Integration, and Automation concepts for ECE engineering students.

## Features
✅ Control appliances using mobile phone
✅ WiFi-based smart automation
✅ Real-time ON/OFF monitoring
✅ Low-cost and energy efficient
✅ Easy to expand for more devices
✅ Compatible with Blynk IoT platform

## Components Used
Component
Quantity
ESP32 Dev Board
1
4-Channel Relay Module
1
Bulb / LED
1-4
Jumper Wires
As required
Breadboard
1
Power Supply
1
Smartphone with Blynk App
1

## Circuit Connections
ESP32 Pin
Relay Module
GPIO 23
IN1
GPIO 22
IN2
GPIO 21
IN3
GPIO 19
IN4
GND
GND
VIN
VCC

## Working Principle
ESP32 connects to WiFi network.
User opens Blynk mobile app.
Commands are sent through internet.
ESP32 receives commands.
Relay module switches appliances ON/OFF.
Real-time control achieved remotely.

## Overview
An IoT-based smart home automation system that allows users to control electrical appliances remotely using WiFi and the Blynk mobile application.

## Features
- Remote appliance control
- Real-time monitoring
- WiFi-enabled automation
- Multi-device support

## Technologies Used
- ESP32
- Arduino IDE
- Blynk IoT
- Embedded C++

## Hardware Components
- ESP32
- Relay Module
- LEDs/Bulbs
- Jumper Wires

## Blynk Mobile Setup
Install blynk.io⁠� app
Create new template
Add 4 button widgets

## Assign virtual pins:
V0 → Relay1
V1 → Relay2
V2 → Relay3
V3 → Relay4
Upload code to ESP32

Connect appliances

## Circuit Diagram
(Add image here)

## Working Principle
Explain project workflow briefly.

## Results
(Add setup images/screenshots)

## Future Improvements
- Voice control
- Energy monitoring
- AI automation

## Author
Ankit Patel
ECE Engineering Student

## Codes in c++ 
#define BLYNK_TEMPLATE_ID "YourTemplateID"
#define BLYNK_DEVICE_NAME "HomeAutomation"

#define BLYNK_PRINT Serial

#include <WiFi.h>
#include <WiFiClient.h>
#include <BlynkSimpleEsp32.h>

char auth[] = "YourAuthToken";
char ssid[] = "WiFi_Name";
char pass[] = "WiFi_Password";

#define Relay1 23
#define Relay2 22
#define Relay3 21
#define Relay4 19

BLYNK_WRITE(V0)
{
  digitalWrite(Relay1, param.asInt());
}

BLYNK_WRITE(V1)
{
  digitalWrite(Relay2, param.asInt());
}

BLYNK_WRITE(V2)
{
  digitalWrite(Relay3, param.asInt());
}

BLYNK_WRITE(V3)
{
  digitalWrite(Relay4, param.asInt());
}

void setup()
{
  Serial.begin(115200);

  pinMode(Relay1, OUTPUT);
  pinMode(Relay2, OUTPUT);
  pinMode(Relay3, OUTPUT);
  pinMode(Relay4, OUTPUT);

  digitalWrite(Relay1, LOW);
  digitalWrite(Relay2, LOW);
  digitalWrite(Relay3, LOW);
  digitalWrite(Relay4, LOW);

  Blynk.begin(auth, ssid, pass);
}

void loop()
{
  Blynk.run();
}
