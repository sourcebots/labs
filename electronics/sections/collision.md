# Collision Sensors

### Robot Progress
* Creation of collision/bump detectors

### Knowledge
* Basic electronics concepts
* Switches and the need for pull-up/pull-down resistors

### Skills
* Breadboard prototyping
* Basic soldering

## Basic Theory
Before you can do any practical electronics, you need to have some understanding of the following concepts:

* Charge
* Current
* Potential Difference (Voltage)
* Resistance

**Charge** is a fundamental property of matter. This means it is something we can observe but not explain in other terms. In this case we can observe that some particles attract each other, some repel, and some experience no force. There are three possible states of charge: positive, negative and neutral (no charge). Charge is measured in **Coulombs (C)**.

**Current** is the **rate of flow** of charge. This means the amount of charge flowing in one second. In the case of a wire **electrons will flow**. Current is measured in **Amperes (A)**. If a wire carries a current of 1 Amp, 1 Coulomb of charge ($6.25 \times 10^{18}$ electrons) moves through that wire every second!

**Potential difference** (Voltage) is the amount of work done (in Joules) to move 1 Coulomb of charge from one point to another. Since it is the *difference* between two points, all voltages are measured relative to another point. This is usually the *0V* or *ground* line. Potential difference is measured in **Volts (V)**.

**Resistance** is defined as the ratio of potential difference to current. You can think of it as a way of measuring how difficult it is for current to flow through something. It is calculated as:

$$\text{Resistance} = \frac{\text{Potential Difference}}{\text{Current}}$$

$$R = \frac{V}{I}$$ 

or, rearranging:

$$V = IR$$

Resistance is measured in Ohms ($\Omega$).

Now that we know some theory, we can do something useful. You can use the chart in the appendix to work out the resistor's value from it's colours.

## Building a simple sensor

Take a look at the following circuit:

\begin{center}  \includegraphics[height=8cm]{img/collision-circuit.png} \end{center}

When the switch is closed (conducting), the output terminal is directly connected to the 5V line so the output is at 5V. 
When the switch is open (not conducting), there is no current in the resistor. The voltage drop across a resistor is proportional to the current through it ($V = IR$), so if there is no current there will be no voltage drop across the resistor, and the output is at 0V.

**Important note!** You might wonder why you can’t just connect a switch between 5V and the output. If you do this, when the switch is open the output will not be connected to anything. This is called a *floating line*. The voltage between this point and the Arduino 0V line will be unpredictable, picking up random signals from the surroundings. 
Connecting the output to 0V through a resistor like as shown above makes sure the voltage at the output is 0V when the switch is not pressed; we call this a *pull-down resistor* which "pulls the output low" when the switch is open. 
We choose a resistor with a fairly high value of about $10k\Omega$ because we want to avoid drawing a large amount current when the switch is closed.

This circuit can be used as an input to a digital system. Your Arduino board can read the state of this input using the *digital read* command. See the programming docs for more detail.

In order to wire up the above circuit, three connections would be required:

* A connection between the ground (0V) of the Arduino and the ground of the sensor.
* A connection between a digital input on the Arduino and the output between the switch and the resistor.
* A connection between the 5V pin on the Arduino and the switch.

### Task - Make a collision detector for your robot

Now that you know how to make a switch work as a digital input, try assembling some switches that could be used on your robot. Start by assembling it on a breadboard. When you're sure it works, you can solder it onto stripboard (ask a SourceBots volunteer for help).

You’ll find some switches, prototyping board, resistors and wire in the lab.

**Some things to consider are:**

* How could your robot use a digital collision sensor?
* How will you mount the switch to your robot?
* Could you use more than one sensor?

\pagebreak