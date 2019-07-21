# Ultrasound Sensor

## About the sensor

Each team has been provided with two HC-SR04 ultrasonic distance sensors.

The sensor has four screw terminals, labelled **Vcc**, **Trig**, **Echo** and **GND**.

* **Vcc** is the positive voltage pin and must be connected to 5V.
* **GND** is the ground pin and must be connected to the Arduino GND.
* **Trig** is used to start a measurement. When it is pulled HIGH(5V) the sensor will send out a pulse of ultrasound.
* **Echo** will send out a pulse proportional in length to the distance measured by the sensor.

The `Robot` library will automatically measure the time between the trigger and when the echo is received, then calculate the distance. It can detect an object up to around 4m away.

## Setting up the sensor

Using the provided PCB, connect the ultrasound sensor to the female header on one side of the board. On the other side of the board, there is a screw terminal. Connect the VCC pin to 5V from a bench power supply and connect the ground pin to the ground connection on the power supply. Connect the trigger to the red wire from the signal generator and the black wire to ground. Then using two channels on the oscilloscope, connect one channel to the trigger pin, and connect a second to the echo pin, connect both their ground connections to the ground of the ultrasound.

[docs]: https://docs.sourcebots.org

## Calculating the speed of sound
To use the sensor, you will need to do some wiring.

1. Cut and strip 4 wires (one red, one black, 2 in colours of your choice)
2. Screw the red wire into VCC
3. Screw the black wire into GND
4. Screw the other two wires into Trig and Echo.
5. Connect the red wire to 5V on the Arduino and the black wire to GND on the Arduino.
6. Connect the **Trig** and **Echo** wires to any digital IO lines on the Arduino.
7. See the [docs][docs] for information on using the sensor.

In order to estimate range using your ultrasound, you will need to calculate the speed of sound. Since velocity is given by:

$$ velocity = \frac{distance}{time} $$

You can calculate the speed of sound by taking a known distance, and seeing how long it takes for a response from the ultrasound. 

Set the signal generator to produce a square wave with a frequency of 20Hz, with a low level of 0V, and a high level of 5V. Adjust the duty cycle of your square wave until the 5V period is approximately 10$\mu$s. You can verify this by looking at the value of each square on the oscilloscope's screen.

After 10$\mu$s the ultrasound sensor will then transmit. In order to get an accurate reading, you may need to adjust your oscilloscope's "Trigger" settings. Press the trigger menu button towards the right of the oscilloscope, and set your triggering on the same channel as the trigger pin of your ultrasound sensor, along with setting the coupling to DC and the trigger type to edge. You can also adjust the trigger level, which is the threshold that will cause your oscilloscope to take a reading. See if you can find a section where the echo signal goes high (You may need to adjust your time scale to do this).

\begin{center} \includegraphics[height=8cm]{img/ultrasound-scope.png} \end{center}

You should now see something like the image above. Using the oscilloscope, find the length in seconds of the high section of the echo signal. This is the length of time required to get recieve a signal back. Since the ultrasound signal has to go outward and then return to the sensor, divide this time by 2.

- What is your measured speed of sound? Is this close to the expected value?
- How could you integrate this into your robot? How would you modify your code to measure range?
