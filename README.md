# Arduino Servo Motor Project

This project shows how to control a standard servo motor with an Arduino Uno R3 using the `Servo.h` library. The servo starts at a neutral position and then sweeps continuously from 0° to 180° and back again.

This is a simple beginner-friendly project that is great for learning:
- how Arduino pins work
- how servo motors are powered and controlled
- how to write a loop that moves a motor through a range of angles
- basic circuit wiring with jumper wires

## What you need

You will need:
- 1 x Arduino Uno R3
- 1 x Servo motor
- 3 x jumper wires minimum
- 1 x USB cable for the Arduino
- Optional: breadboard, extra jumper wires, power supply, and a small mount or stand for the servo

## Servo motor wiring

A typical hobby servo has three wires:
- Brown or black wire: GND
- Red wire: +5V
- Orange, yellow, or white wire: signal wire

For this project:
- Servo signal wire -> Arduino digital pin D9
- Servo power wire (+5V) -> Arduino 5V pin
- Servo ground wire (GND) -> Arduino GND pin

If you are using a breadboard, the wiring can be made cleaner and easier to manage.

## Basic wiring layout

Use this connection layout:

- Servo GND -> Arduino GND
- Servo +5V -> Arduino 5V
- Servo signal -> Arduino D9

### Example wiring diagram (text version)

```text
Arduino Uno R3          Servo Motor
-----------------      ----------------
5V -------------------- +5V (red)
GND ------------------- GND (brown/black)
D9 -------------------- Signal (orange/yellow/white)
```

## Circuit setup options

### 1. Simplest setup
The simplest version is to connect the servo directly to the Arduino without a breadboard. This works for basic projects and quick testing.

### 2. Breadboard setup
A breadboard gives you more room to organize the wires and makes troubleshooting easier. This setup is helpful if you are adding more components or want a cleaner project.

### 3. Most direct setup
This is the clearest and least cluttered method if you want to keep the circuit small and easy to understand.

## Arduino code

This project uses the following code:

```cpp
#include <Servo.h>

Servo myServo;

void setup() {
  myServo.attach(9);  // Servo signal wire connected to D9
  myServo.write(90);  // Move servo to center position
  delay(1000);
}

void loop() {
  // Sweep from 0 to 180 degrees
  for (int angle = 0; angle <= 180; angle++) {
    myServo.write(angle);
    delay(15);
  }

  // Sweep back from 180 to 0 degrees
  for (int angle = 180; angle >= 0; angle--) {
    myServo.write(angle);
    delay(15);
  }
}
```

## How the code works

### `#include <Servo.h>`
This line loads the Arduino library that allows the board to control servos.

### `Servo myServo;`
This creates a Servo object named `myServo`.

### `myServo.attach(9);`
This tells the Arduino that the servo signal wire is connected to digital pin 9.

### `myServo.write(90);`
This moves the servo to the 90° position, which is roughly the center of the servo's movement range.

### `for (int angle = 0; angle <= 180; angle++)`
This loop increases the angle from 0° to 180° in steps. Each step moves the servo a little more.

### `for (int angle = 180; angle >= 0; angle--)`
This loop decreases the angle from 180° back to 0°, creating a sweeping motion back and forth.

### `delay(15);`
This pauses between movements so the servo can reach its target position smoothly.

## Uploading the code

1. Open the Arduino IDE.
2. Copy the code above into a new sketch.
3. Connect the Arduino to your computer with the USB cable.
4. Select the correct board:
   - Board: Arduino Uno
5. Select the correct port.
6. Click Upload.
7. The servo should start moving back and forth.

## Troubleshooting

If the servo does not move:
- Check that the signal wire is connected to D9.
- Make sure the red wire is connected to +5V and not the wrong pin.
- Confirm the brown/black wire is connected to GND.
- Verify the Arduino is powered and the USB cable is connected.
- Make sure the servo is receiving enough power.
- If the servo jitters or vibrates, it may not have a stable power connection.

## Important notes

- This project uses the Arduino's 5V pin, which is usually enough for a small hobby servo.
- Some larger servos may draw more current than the Arduino can safely supply. In those cases, use an external 5V power source.
- Be careful with wire polarity. Reversing power and ground may damage the servo or the Arduino.

## Optional improvements

You can expand this project by:
- changing the movement speed by adjusting `delay(15)`
- using `myServo.write(0)` and `myServo.write(180)` for more dramatic movement
- adding buttons or sensors to trigger movement
- using multiple servos with separate pins
- creating a robotic arm or simple pan-and-tilt mechanism

## Helpful resource

If you do not know how to set up Arduino in Tinkercad, watch this video:

[Arduino Servo Motor Basics Tutorial](https://www.youtube.com/watch?v=dI2lGIy-XgY)

## Summary

This project is a simple introduction to controlling a servo with Arduino. By connecting the servo to pin D9 and running the provided code, the servo will sweep continuously across its full range of motion. It is an excellent beginner project for learning the basics of electronics, Arduino coding, and motor control.

If you want, I can also turn this into a cleaner README with:
- a more professional layout
- a labeled wiring diagram image section
- a step-by-step beginner explanation
- a version specifically formatted for GitHub with nicer markdown styling
