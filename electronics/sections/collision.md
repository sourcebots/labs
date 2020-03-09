# Collision Sensors

Before you can do any practical electronics, you need to have some understanding of the following concepts:

* Charge
* Current
* Potential Difference (Voltage)
* Resistance

**Charge** is a fundamental property of matter. This means it is something we can observe but not explain in other terms. In this case we can observe that some particles attract each other, some repel, and some experience no force. There are three possible states of charge: positive, negative and neutral (no charge). Charge is measured in **Coulombs (C)**.

**Current** is the **rate of flow** of charge. This means the amount of charge flowing in one second. In the case of a wire **electrons will flow**. Current is measured in **Amperes (A)**. If a wire carries a current of 1 Amp, 1 Coulomb of charge ($6.25 \times 10^{18}$ electrons) moves through that wire every second!

**Potential difference** (Voltage) is the amount of work done (in Joules) to move 1 Coulomb of charge from one point to another. There isn't a way to measure voltage as an absolute quantity, so all voltages are measured relative to another point. Potential difference is measured in **Volts (V)**.

**Resistance** is a way of measuring how difficult it is for current to flow through something. You might be familiar with the following equation: 

$$\text{Resistance} = \frac{\text{Potential Difference}}{\text{Current}}$$

$$R = \frac{V}{I}$$ 

or, rearranging:

$$V = IR$$

Resistance is measured in Ohms ($\Omega$).

Now that we know some theory, we can do something useful.

Take a look at the following circuit:

\begin{center}  \includegraphics[height=8cm]{img/collision-circuit.png} \end{center}

What is the voltage between the points labeled "Output" and "0V" when the switch is open (not conducting) and closed (is conducting)? When the switch is closed, the output terminal is directly connected to the 5V line, so the output is at 5V. When the switch is open, the output is at 0V *because of the resistor*. When the switch is open, there is no current in the resistor. The voltage drop across a resistor is proportional to the current through it ($V = IR$), so if there is no current there will be no voltage drop across the resistor, hence the output is at 0V.
**Important note!** You might wonder why you can’t just connect a switch between 5V and the output. If you do this, when the switch is open the output will not be connected to either 5V or 0V. This is called a *floating line*, and there is no way of knowing what potential it is at. Remember that potential *difference* has to be measured between two points - a floating line isn't connected to the circuit, so there is no way of measuring it's potential relative to the 0V of your Arduino. Connecting the output to 0V through a resistor like is shown above makes sure the voltage at the output is 0V when the switch is not pressed; we say the resistor is a "pull-down resistor" and that it "pulls the output low" when the switch is open.
We choose a resistor with a fairly high value of about $10k\Omega$ because we want to avoid drawing a large amount current when the switch is closed.

This circuit can be used as an input to a digital system. Your Arduino board can read the state of this input using the digital read command. See the programming docs for more detail.

In order to wire up the above circuit, three connections would be required:

* A connection between the ground (0V) of the Arduino and the ground of the sensor.
* A connection between a digital input on the Arduino and the output between the switch and the resistor.
* A connection between the 5V pin on the Arduino and the switch.

**Task**: Make a collision detector for your robot. Use the oscilloscope or multimeter to check that it outputs high (5V) and low (0V) signals correctly.

Now that you know how to make a switch work as a digital input, try assembling some switches that could be used on your robot. Start by assembling it on a breadboard. When you're sure it works, you can solder it onto stripboard (ask a SourceBots volunteer for help).

You’ll find some switches, prototyping board, resistors and wire in the lab.

**Some things to consider are:**

* How could your robot use a digital collision sensor?
* How will you mount the switch to your robot?
* Could you use more than one sensor?

### Switch bounce

 You might find that when you press the switch it seems to register lots of contacts each time you touch something. This is because the contacts can easily 'bounce' when they are connected. This effect happens very quickly, so you won't be able to see it but your Arduino can read it's input pins fast enough for it to count each small bounce as a new time a connection has been made. To make your counter more reliable you need to make sure it only counts once each time you connect the metal contacts.
- One way of doing this is to force the Arduino to wait for a few milliseconds after detecting a connection has been made so that all the 'bouncing' has stopped before it carries on running it's code. There is a problem with this method though - this means your code is spending time doing *nothing* - including not controlling your robot! We need to find a "non-blocking" way of dealing with this instead.
- It is possible to find out how many milliseconds have passed since the Arduino turned on (ask for help if you need it). You could use this to keep track of when each connection is detected and only count the ones that aren't caused by bounces.
- You can also solve it in hardware, by adding a capacitor to your circuit. The behaviour of a capacitor is dependent on *the rate of change of voltage* across it. This means it will smooth out voltage spikes, including getting rid of the bouncing.

\begin{center}  \includegraphics[height=8cm]{img/Series_RC_capacitor_voltage.png} \end{center}

When the voltage across the capacitor changes (like the step input above) the voltage across the capacitor takes time to reach the supply. That rise is exponential, described by the time constant $\tau = RC$. Think about what capacitance values might be suitable.
- There are also far more complicated circuits you could use for this that would work better (if you are interested, have a look at [Schmitt triggers](https://en.wikipedia.org/wiki/Schmitt_trigger)). However like most engineering problems, you need to weigh up the pros and cons of each option based on:

    - Performance
    - Cost
    - Simplicity
    - Reliability
as well as other factors based on your specific project. Which method do you think is the best for your robot?

- Try to improve your circuit to deal with switch bounce. If you use a capacitor, it should go between the 'output' and ground.
