Saptiya
# Ultrasonic Distance Measurement System using Arduino
## Overview
This project uses an ultrasonic sensor (HC-SR04) with Arduino to measure the distance of an object in real-time.
The system calculates distance by sending ultrasonic waves and measuring the time it takes for the echo to return.
Measured distance can be displayed on a 16x2 LCD or via Serial Monitor.
## Features
Measures distance of objects using ultrasonic waves.
Real-time distance displayed on LCD or Serial Monitor.
Can detect obstacles or monitor object presence.
Simple and cost-effective setup.
Easy to integrate with other IoT or automation systems.
## Hardware Used
Arduino Uno / Nano
Ultrasonic Sensor (HC-SR04)
16x2 LCD Display
Potentiometer (for LCD contrast adjustment)
Jumper Wires & Breadboard
USB Cable / 9V Battery for Arduino Power
## Simulation
Wokwi project link: https://wokwi.com/projects/451597646935043073
## Code: #include <Wire.h>
#include <LiquidCrystal_I2C.h>

// LCD address 0x27, 16 columns, 2 rows
LiquidCrystal_I2C lcd(0x27, 16, 2);

#define trigPin 9
#define echoPin 10

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  lcd.init();
  lcd.backlight();

  lcd.setCursor(0, 0);
  lcd.print("Distance Meter");
}

void loop() {
  long duration;
  int distance;

  // Send ultrasonic pulse
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Read echo time
  duration = pulseIn(echoPin, HIGH);

  // Calculate distance (cm)
  distance = duration * 0.034 / 2;

  // Display on LCD
  lcd.setCursor(0, 1);
  lcd.print("Dist: ");
  lcd.print(distance);
  lcd.print(" cm   ");

  delay(500);
}

Main file: ultrasonic_distance.ino
## Circuit image: Ultrasonic_distance_circuit.png
Avolothana
