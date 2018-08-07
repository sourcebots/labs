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
