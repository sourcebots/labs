# Ultrasound Sensor

## About the sensor

Each team has been provided with two HC-SR04 ultrasonic distance sensors.

\begin{center}  \includegraphics[height=4cm]{img/ultra-sensor.png} \end{center}

The sensor has four screw terminals, labelled **Vcc**, **Trig**, **Echo** and **GND**.

* **Vcc** is the positive voltage pin and must be connected to 5V.
* **GND** is the ground pin and must be connected to the Arduino GND.
* **Trig** is used to start a measurement. When it is pulled HIGH(5V) the sensor will send out a pulse of ultrasound.
* **Echo** will send out a pulse proportional in length to the distance measured by the sensor.

The `Robot` library will automatically measure the time between the trigger and when the echo is received, then calculate the distance. It can detect an object up to around 4m away.

## Setting up the sensor

To use the sensor, you will need to do some wiring.

\begin{center}  \includegraphics[height=4cm]{img/ultra-strip.png} \end{center}

1. Cut and strip 4 wires (one red, one black, 2 in colours of your choice)
2. Screw the red wire into VCC
3. Screw the black wire into GND
4. Screw the other two wires into Trig and Echo.
5. Connect the red wire to 5V on the Arduino and the black wire to GND on the Arduino.
6. Connect the **Trig** and **Echo** wires to any digital IO lines on the Arduino.
7. See the [docs][docs] for information on using the sensor.

[docs]: https://docs.sourcebots.org
