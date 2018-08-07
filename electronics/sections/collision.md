# Collision Sensors

Before you can do any practical electronics, you need to have some understanding of the following concepts:

* Charge
* Current
* Potential Difference (aka. Voltage)
* Resistance

**Charge** is a fundamental property of matter. This means it is something we can observe but not explain in other terms. In this case we can observe that some particles attract each other, some repel, and some experience no force. Since there are three possible states they were called positive, negative and neutral (no charge). Charge is measured in **Coulombs (C)**.

**Current** is the **rate of flow** of electric charge. This means the amount of charge flowing in one second. In the case of a wire **electrons will flow**, but in electronics we aren’t very interested in which particles are moving so we assume that positive charges flow to negative. Current is measured in **Amperes (A)**. If a wire carries a current of 1 Amp, then it means that in each second, 1 Coulomb of charge (about 6250000000000000000 electrons) moves through that wire!

**Potential difference** is the difference in potential energy for each Coulomb of charge. For example, if you use a voltmeter to test the voltage across a battery, and your voltmeter says 9 Volts, it means that each coulomb of charge leaves with 9 Joules more energy than it entered with. For a component the voltmeter would tell you the energy lost by each charge. PD is measured in **Volts (V)**.

**Resistance** is the easiest quantity to define. It is defined by the equation:

$$\text{Resistance} = \frac{\text{Potential Difference}}{\text{Current}}$$

$$R = \frac{V}{I}$$

Resistance is measured in Ohms ($\Omega$).

Now that we know some theory, we can do something useful.

Take a look at the following circuit:

\begin{center}  \includegraphics[height=8cm]{img/collision-circuit.png} \end{center}

When the switch is closed (pushed), the output terminal is connected to the 5V line, so the output is at 5V. The resistor is in the circuit to limit the current that flows.

When the switch is open (not pushed), there is no current in the resistor. From the equation $$V = IR$$, if there is no current there will be no voltage across the resistor. This means the output is at 0V.

**Important note!** You might wonder why you can’t just use a switch connected between 5V and the output. If you do this, when the switch is open the output will not be connected to either 5V or 0V. This is called a *floating line*, and will be read as a random value by the Arduino board.

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
