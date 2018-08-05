# Ultrasound Sensor Guide

## About the sensor

Each team has been provided with two HC-SR04 ultrasonic distance sensors.

You have also been provided with two four pin female headers.

[INSERT IMAGE]

The sensor has four pins, labelled **Vcc**, **Trig**, **Echo** and **GND**.

* **Vcc** is the positive voltage pin and must be connected to 5V.
* **GND** is the ground pin and must be connected to the Arduino GND.
* **Trig** is used to start a measurement. When it is pulled HIGH(5V) the sensor will send out a pulse of ultrasound.
* **Echo** will send out a pulse proportional in length to the distance measured by the sensor.

The `Robot` library will automatically measure the time between the trigger and when the echo is received, then calculate the distance. It can detect an object up to around 4m away.

## Setting up the sensor

To use the sensor, you will need to do some soldering. 

1. Solder the female header onto a piece of stripboard.
2. Solder one length of wire in the same line as each pin. Make sure you use a **red wire** for Vcc and a **black wire** for GND. Other wires should be in any other colour of your choice.
3. Connect the red wire to 5V on the Arduino and the black wire to GND on the Arduino.
4. Connect the **Trig** and **Echo** wires to any digital IO lines on the Arduino.
5. See the [docs][docs] for information on using the sensor.

[docs]: https://docs.sourcebots.org
