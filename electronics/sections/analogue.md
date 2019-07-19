# Analogue Inputs and Potential Dividers
## Analogue and Digital Signals
An analogue signal is one which is continuous in time and in value, meaning that it can have any possible value at any possible point in time. This is in contrast to a digital signal, which is discrete in value, meaning that it can only have a predetermined set of possible values, in the case of a digital signal, either "1" or "0". 

### Analogue inputs for Arduino

The Arduino you have been given for your robot has some analogue input pins. In the case of a microcontroller, these pins are connected to the input of an Analogue-to-Digital Converter (ADC), which takes a sample of the input at a point in time and converts it to a binary value suitable for a microcontroller to handle. The Arduino has a 10 bit ADC, which divides the range between 0V and 5V into 1024 steps. The change required in the analogue signal required for a 1 bit change in the value produced by the ADC is known as its "resolution". The resolution of the ADC can be calculated as follows:

$$\text{Resolution} = \frac{5}{1024}$$

This gives the resolution of the ADC as 4.9mV. This function of the Arduino can be accessed using the **analogread(analogpin)** function on anything connected to the Arduino's dedicated analogue pins. Your Arduino has 6 such pins, noted by A0, A1, A2, A3, A4 and A5. This may be useful for some of your sensors, as some of them do not return a digital value, and instead return a range of analogue values, particularly if you need more detail from the sensors than simply on or off.

## Potential Dividers
A potential divider is a circuit that consists of 2 or more resistors. This is useful for bringing a voltage that is out of range of your Arduino down to a lower voltage which is in range, for your robot, this will typically be reducing a signal from 5V to 3.3V. Here, Ohm's law causes a drop in voltage across the first resistor (R1) which is proportional to its resistance, This leaves the second resistor (R2) to drop the remaining voltage.

\begin{center}  \includegraphics[width=\textwidth]{img/potentialdivider.png} \end{center}

Above is an example of a potential divider, where the output voltage (Vout) is given by:

$$\text{Vout} = \text{V1} \times \frac{\text{R2}}{\text{R1+R2}}$$


## Force Sensitive Resistors (FSR)

You may find at some point that you not only need to know if your robot is touching something, but how hard it is pressing against something. Force sensitive resistors provide one way in which you could do this. You can make your own FSR out of some of the conductive foam that you can find in the lab, and two sheets of any non conducting material, ideally something that does not compress very much, so that as much of the force as possible is transfered to the foam, rather than just deforming the material on the outside.

The resistance of any object is defined by three factors, the object's length (L), it's cross-sectional area (A), and a constant known as resistivity ($\rho$), this gives the resistance equation as:

$$R= \rho \times \frac{L}{A}$$

If you place this in a potential divider configuration with a resistor of a known value, you can work out the resistance of your sensor relative to the other resistor by the voltage across each of them.

* Can you build one of these sensors?
* What value should your other resistor be? Are there any advantages or disadvantages for lesser/greater resistances?
