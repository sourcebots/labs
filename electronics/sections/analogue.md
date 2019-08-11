# Analogue Inputs and Potential Dividers

### Robot Progress
* Creation of analogue force sensors

### Knowledge
* Potential divider circuit theory
* Analogue sensor operation
* Basic understanding of analogue to digital conversion

### Skills
* Constructing a simple force sensor
* Using a multimeter or oscilloscope for testing

## Analogue and Digital Signals
An analogue signal is one which is continuous in time and in value, meaning that it can have any possible value at any possible point in time. For example, mass is an analogue quantity. Digital signals have **discrete** values, meaning that it can only have a predetermined set of possible values. For example, shoe size is a discrete quantity. In the case of a digital signal, the allowed values are either "1" or "0". 

## Analogue inputs for Arduino

The Arduino you have been given for your robot has some analogue input pins. These pins are connected to the input of an Analogue-to-Digital Converter (ADC), which takes a sample of the input at a point in time and converts it to a binary value suitable for a microcontroller to handle. The Arduino has a 10 bit ADC, which divides the range between 0V and 5V into 1024 steps. The change required in the analogue signal required for a 1 bit change in the value produced by the ADC is known as its "resolution". The resolution of the ADC can be calculated as follows:

$$\text{Resolution} = \frac{5}{1024}$$

This gives the resolution of the ADC as 4.9mV. This function of the Arduino can be accessed using the **analogRead(analogpin)** function on anything connected to the Arduino's dedicated analogue pins. Your Arduino has 6 such pins, noted by A0, A1, A2, A3, A4 and A5 (although A4 and A5 are reserved for I2C communication so you can't use them). This may be useful for some of your sensors, as some of them do not return a digital value, and instead return a range of analogue values.

## Potential Dividers
A potential divider is a circuit that consists of 2 or more resistors. This is useful for bringing a voltage that is out of range of your Arduino down to a lower voltage which is in range for your robot, typically reducing a signal from 5V to 3.3V. Here, Ohm's law causes a drop in voltage across the first resistor (R1) which is proportional to its resistance, This leaves the second resistor (R2) to drop the remaining voltage.

\begin{center}  \includegraphics[width=\textwidth]{img/potentialdivider.png} \end{center}

Above is an example of a potential divider, where the output voltage (Vout) is given by:

$$\text{Vout} = \text{V1} \times \frac{\text{R2}}{\text{R1+R2}}$$

If one of the resistors changes value the output voltage will also change. This means potential dividers can be used as part of a sensor circuit. For example, a light sensor can be made if one of the resistor is a light dependent resistor.

## Force Sensitive Resistors (FSR)

You may find at some point that you not only need to know if your robot is touching something, but how hard it is pressing against something. Force sensitive resistors provide one way to do this. You can make your own FSR out of some of the conductive foam that you can find in the lab and two sheets of any non conducting material (ideally something that does not compress very much) so that as much of the force as possible is transfered to the foam, rather than just deforming the material on the outside.

The resistance of any object is defined by three factors, the object's length (L), it's cross-sectional area (A), and a constant known as resistivity ($\rho$). The resistance is calculated by the equation:

$$R= \rho \times \frac{L}{A}$$

If you place your foam sensor in a potential divider configuration with a resistor of a known value, you can work out the resistance of your sensor relative to the other resistor by the voltage across each of them.

### Task 1 - Build an analogue force sensor
* Take a small piece of conductive foam and insert two wires into it. Make sure to strip the ends of the wire first! 
* Use a multimeter to measure the resistance between the two terminals. You should see the resistance drop significantly when you press on the sensor. The harder you press, the further it should drop.  
* Cover the foam and a small part of the wires with electrical tape to make sure it holds together nicely.
* Optionally add a piece of rigid material on either side of the foam to more evenly distribute the force applied.

### Task 2 - Experiment with your sensor
* Connect the sensor in a potential divider with another resistor and record the range of voltages when a force is applied.
* Test a few other values of fixed resistor. How does this affect the range of voltage?

**Things to consider:**

* Which value of fixed resistor gives the greatest variation? You might be able to investigate mathematically.
* Is greater sensitivity always better?
* How could this type of sensor be useful for your robot?

\pagebreak