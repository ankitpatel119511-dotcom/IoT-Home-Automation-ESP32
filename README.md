# IoT-Home-Automation-ESP32
IoT-based Smart Home Automation System using ESP32 and Blynk for remote appliance control over WiFi.
# IoT Home Automation System using ESP32

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
