# Collision Sensors

Before you can do any practical electronics, you need to have some understanding of the following concepts:

* Charge
* Current
* Potential Difference (Voltage)
* Resistance

**Charge** is a fundamental property of matter. This means it is something we can observe but not explain in other terms. In this case we can observe that some particles attract each other, some repel, and some experience no force. There are three possible states of charge: positive, negative and neutral (no charge). Charge is measured in **Coulombs (C)**.

**Current** is the **rate of flow** of charge. This means the amount of charge flowing in one second. In the case of a wire **electrons will flow**. Current is measured in **Amperes (A)**. If a wire carries a current of 1 Amp, 1 Coulomb of charge ( $$6.25 \times 10^18$$ electrons) moves through that wire every second!

**Potential difference** (Voltage) is the amount of work done (in Joules) to move 1 Coulomb of charge from one point to another.There isn't a way to measure voltage as an absolute quantity (think of things like temperature or force), so all voltages are measured relative to another point. Potential difference is measured in **Volts (V)**.

**Resistance** is a way of measuring how difficult it is for current to flow through something. You might be familiar with the following equation: 

$$\text{Resistance} = \frac{\text{Potential Difference}}{\text{Current}}$$

$$R = \frac{V}{I}$$ 

or, rearranging:

$$V = IR$$

So resistance is a measure of the amount of work done to allow 1 Coulomb of current to flow through a device.

Resistance is measured in Ohms ($\Omega$).

Now that we know some theory, we can do something useful.

Take a look at the following circuit:

\begin{center}  \includegraphics[height=8cm]{img/collision-circuit.png} \end{center}

When the switch is closed (pushed), the output terminal is directly connected to the 5V line, so the output is at 5V. The resistor then serves to limit the current that flows from the 5V supply to ground. If there were no resistor here, the 5V supply would be directly connected to ground with nothing in between, known as a short circuit. This would cause a large current to flow through the wire and switch to allow for 5V to be lost along the small resistance of the wire.

When the switch is open (not pushed), there is no current in the resistor. From the equation $$V = IR$$, if there is no current there will be no voltage across the resistor. This means the output is at 0V. This resistor is known as a "pull-down" resistor, and one way to think of it is as though you were placing a "weak" 0V on the output. When the switch is pressed, the output is connected to a "strong" 5V, which is then read as the output of the circuit.

**Important note!** You might wonder why you can’t just use a switch connected between 5V and the output. If you do this, when the switch is open the output will not be connected to either 5V or 0V. This is called a *floating line*, and there is no way of knowing how your Arduino will read it. Connecting to 0V through a resistor makes sure we always know what the voltage at the output is, even when the switch is not pressed.

This circuit can be used as an input to a digital system. Your Arduino board can read the state of this input using the digital read command. See the programming docs for more detail.

In order to wire up the above circuit, three connections would be required:

* A connection between the ground (0V) of the Arduino and the ground of the sensor.
* A connection between a digital input on the Arduino and the output between the switch and the resistor.
* A connection between the 5V pin on the Arduino and the switch.

**Task**: Make a collision detector for your robot

Now that you know how to make a switch work as a digital input, try assembling some switches that could be used on your robot. Start by assembling it on a breadboard. When you're sure it works, you can solder it onto stripboard (ask a SourceBots volunteer for help).

You’ll find some switches, prototyping board, resistors and wire in the lab.

**Some things to consider are:**

* How could your robot use a digital collision sensor?
* How will you mount the switch to your robot?
* Could you use more than one sensor?
