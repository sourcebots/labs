# Ultrasound Sensor

## About the sensor

Each team has been provided with two HC-SR04 ultrasonic distance sensors.

You have also been provided with two four pin female headers.

\begin{center}  \includegraphics[height=4cm]{img/ultra-sensor.png} \end{center}

The sensor has four pins, labelled **Vcc**, **Trig**, **Echo** and **GND**.

* **Vcc** is the positive voltage pin and must be connected to 5V.
* **GND** is the ground pin and must be connected to the Arduino GND.
* **Trig** is used to start a measurement. When it is pulled HIGH(5V) the sensor will send out a pulse of ultrasound.
* **Echo** will send out a pulse proportional in length to the distance measured by the sensor.

The `Robot` library will automatically measure the time between the trigger and when the echo is received, then calculate the distance. It can detect an object up to around 4m away.

## Setting up the sensor

Using the provided PCB, connect the ultrasound sensor to the female header on one side of the board. On the other side of the board, there is a screw terminal. Connect the VCC pin to 5V from a bench power supply and connect the ground pin to the ground connection on the power supply. Connect the trigger to the red wire from the signal generator and the black wire to ground. Then using two channels on the oscilloscope, connect one channel to the trigger pin, and connect a second to the echo pin, connect both their ground connections to the ground of the ultrasound.

[docs]: https://docs.sourcebots.org

## Calculating the speed of sound

In order to estimate range using your ultrasound, you will need to calculate the speed of sound. Since velocity is given by:
 
\begin{center} $$ velocity = \frac{distance}{time} $$

You can calculate the speed of sound by taking a known distance, and seeing how long it takes for a response from the ultrasound. 

Set the signal generator to produce a square wave with a frequency of 20Hz, with a low level of 0V, and a high level of 5V. Adjust the duty cycle of your square wave until the 5V period is approximately 10$\mu$s. You can verify this by looking at the value of each square on the oscilloscope's screen.

After 10$\mu$s the ultrasound sensor will then transmit. In order to get an accurate reading, you may need to adjust your oscilloscope's "Trigger" settings. Press the trigger menu button towards the right of the oscilloscope, and set your triggering on the same channel as the trigger pin of your ultrasound sensor, along with setting the coupling to DC and the trigger type to edge. You can also adjust the trigger level, which is the threshold that will trigger your oscilloscope to take a reading. What happens if you move it? What about if you take it outside of the wave?

See if you can find a section where the echo signal goes high (You may need to adjust your time scale to do this)
Using the oscilloscope, find the time difference between the start of transmission and the echo signal going high. Since the ultrasound signal has to go outward and then return to the sensor, divide this time by 2.

- What is your measured speed of sound? Is this close to the expected value?
- How could you integrate this into your robot? How would you modify your code to measure range?
