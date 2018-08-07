# Infrared Tripwires

Many electronic systems can be used to produce digital inputs. In the first tutorial, we considered physical switches. In this tutorial we're going to look at another source of a digital input.
Something which robots can make good use of is tripwires. This can tell a robot whether or not it has collected an item. Tripwires can be made by generating a beam of light and then detecting that beam of light with a sensor.
If we use visible light for the tripwire it will have a lot of **interference** from the arena lights, so it would be better to use something less common. For short ranges Infrared is a good choice.
The IR tripwire circuit contains four components that you would need to wire to your robot. Two resistors, an IR LED, and an IR phototransistor. The IR LED is used to create the IR beam, and the phototransistor detects this beam.

## Diodes and LEDs

LEDs are a form of diode. A diode is an electronic component which will only conduct in one direction. A diode has a cathode and an anode (see below). The diode will only conduct from anode to cathode.

\begin{center}  \includegraphics[height=4cm]{img/diode.png} \end{center}

LEDs have a particularly high forward voltage; roughly 1.2V. Each Coulomb of charge passing through it will lose 1.2J of energy, which is converted to Infrared radiation.

## Wiring up the LED

LEDs are polar devices. If you plug them in backwards they may break. LEDs have two features to help you tell anode from cathode. Firstly, LEDs have one long and one short leg. The long leg is the anode (+). The other feature is that LEDs will have a round side and a flat edge. The flat edge shows you where the cathode (-) is.

A useful way to remember this is **short to nought**.

Our IR LED is an L-53F3C. From the datasheet we can find that the LED uses a forward voltage of 1.2V and a forward current of 20mA. So we will need a resistor to limit the current.

\begin{center}  \includegraphics[width=18cm]{img/led-spec.png} \end{center}

We can now figure out the value of R needed by using R = V/I. V is the voltage drop across the resistor (5 – 1.2) and I is the current flowing through it (20mA). This gives us a value for R of:

$$R = \frac{3.8}{0.02} = 190\Omega$$

We could make this up from a $180\Omega$ resistor and a $10\Omega$ resistor in series, but according to the datasheet the absolute maximum current is 50mA, so a $180\Omega$ will be close enough!

\begin{center}  \includegraphics[width=5cm]{img/ir-circuit.png} \end{center}

**Wire this circuit up on a breadboard and use a smart phone or webcam to see if it works. (Ask if you need help).**
