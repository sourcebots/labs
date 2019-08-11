# Infrared Tripwires

### Robot Progress
* Creation of tripwire sensors
* Creation of reflection sensors

### Knowledge
* Basic understanding of LED and transistor operation
* Calculating and selecting suitable resistors for a circuit

### Skills
* Breadboard prototyping
* More complex soldering
* Using a multimeter to take measurements

## Introduction

Many electronic systems can be used to produce digital inputs. In the first tutorial, we considered physical switches. In this tutorial we're going to look at another source of a digital input.
Something which robots can make good use of is tripwires. This can tell a robot whether or not it has collected an item. Tripwires can be made by generating a beam of light and then detecting that beam of light with a sensor.
If we use visible light for the tripwire it will have a lot of *interference* from the arena lights, so it would be better to use something less common. For short ranges Infrared is a good choice.
The IR tripwire circuit contains four components: Two resistors, an IR LED, and an IR phototransistor. 
The IR LED is used to create the IR beam and the phototransistor detects this beam.

## Diodes and LEDs

LEDs are a form of diode. A diode is an electronic component which will only conduct in one direction. The terminals are called the *cathode* and *anode*. The diode will only conduct from anode to cathode.

\begin{center}  \includegraphics[height=8cm]{img/Led.png} \end{center}

LEDs have a high *forward voltage* (the potential difference needed for it to conduct); roughly 1.2V for the IR LEDs that you will be using here. Each Coulomb of charge passing through it will lose 1.2J of energy, which is converted to Infrared radiation.

## Wiring up the LED

LEDs are polarized devices. If you plug them in backwards they will not work. LEDs have two features to help you tell anode from cathode. Firstly, LEDs have one long and one short leg. The long leg is the anode (+). The other feature is that LEDs will have a round side and a flat edge. The flat edge shows you where the cathode (-) is.

A useful way to remember this is **short to nought**.

Our IR LED is an L-53F3C. From the datasheet we can find that the LED uses a forward voltage of 1.2V and a forward current of 20mA. So we will need a resistor to limit the current.

\begin{center}  \includegraphics[width=18cm]{img/led-spec.png} \end{center}

This is the circuit that we will be using:

\begin{center}  \includegraphics[width=5cm]{img/ir-circuit.png} \end{center}

We can now figure out the value of R needed using R = V/I. V is the voltage drop across the resistor (5 – 1.2 = 3.8V) and I is the current flowing through it (20mA). This gives us a value for R of:

$$R = \frac{3.8}{0.02} = 190\Omega$$

We could make this up from a $180\Omega$ resistor and a $10\Omega$ resistor in series, but according to the datasheet the absolute maximum current is 50mA, so a $180\Omega$ will be close enough!


**Wire this circuit up on a breadboard. A smart phone camera or webcam can see IR light so you can use it to test if your circuit works. (Ask if you need help).**

## Transistors and Phototransistors

Transistors can be used to make very complicated devices, but for our purposes they will be used as an infrared detector. A transistor is a three terminal device. It has a collector, an emitter and a base. The key feature of the transistor is that the current that flows into the base determines the current that flows into the collector.

$$I_{Collector} = \text{Gain} \times I_{Base}$$

A typical transistor will have a gain of 100.

\begin{center}  \includegraphics[height=5cm]{img/transistor.png} \end{center}

When no current flows into the base, the transistor acts like a huge resistor and very little current can flow through it. When a small current flows into the base the transistor acts like a resistor with a small value, so a lot of current can flow through it. This is essentially the same as a switch, with base current instead of a physical force.

A phototransistor behaves in the same way, only instead of having a base wire phototransistors are triggered by light. When light shines on the phototransistor a current is allowed to flow from the collector through the emitter. More light gives a bigger current.

## Wiring up the phototransistor

The phototransistor we are using is the L-53P3C.

\begin{center}  \includegraphics[height=5cm]{img/ir_sensor.png} \end{center}
\begin{center}  \includegraphics[height=5cm]{img/phototransistor_symbol.png} \end{center}


In the collision tutorial, we used a pull-down resistor to help us read the state of the switch. In this case we'll use a pull-up resistor. The voltage across the phototransistor will tell us if IR light is shining on it.

\begin{center}  \includegraphics[width=5cm]{img/photo-circuit.png} \end{center}

Choosing a value for R is slightly harder than before. Let's start with the datasheet for the L-53P3C phototransistor.

When the beam is blocked, there will be a very small current in the circuit. From the datasheet:

\begin{center}  \includegraphics[width=18cm]{img/photo-dark.png} \end{center}

So the current will be around 100nA when the beam is blocked.

In an ideal case you would read exactly 5V when no light reached the transistor, and 0V at the output when maximum light reached the transistor. In digital electronics values are relative to a threshold voltage, where if they are higher they read as "1", and lower as "0", even if they are not exactly 5V or 0V.

The Arduino will read a digital input as *high* or "1" if there is at least 4V across the phototransistor, so 1V across the resistor.  When the current through the transistor increases, a larger current also flows through R1 so the voltage drop across R1 is increased (as $V = IR$). 

To calculate the maximum resistor size you can use the usual equation:

$$R = \frac{1}{100 \times 10^{-9}} = 10000000\Omega$$

So a $10M\Omega$ resistor would be suitable.

When the beam is not blocked a larger current will flow. From the datasheet the maximum allowed current is 3mA.

\begin{center}  \includegraphics[width=18cm]{img/photo-state.png} \end{center}

So for the on state we want a current of no more than 3mA, and a voltage across the phototransistor of 1V. This means we want 4V across the resistor.

Using the equation again:

$$R = \frac{4}{3 \times 10^{-3}} = 1333\Omega$$

Now that you have a maximum and minimum, you can experiment to find what resistor value gives you the best high and low level outputs. Higher resistor values will make the detector more sensitive.

### Reflection sensor

The tokens this year are covered in reflective foil. This gives you lots of options for using your IR LEDs in creative ways. You could point the IR LED and the phototransistor at a token and see if the light is reflected. If it is, your robot must be approaching the token at right angles, otherwise the reflected light would miss the detector. You could even work out which direction to turn based on the reflection if you had a few phototransistors on your robot.

### Task - Make an infrared tripwire sensor for your robot
 
 Try assembling the circuit that has been described. All the parts you need are available in the lab. If you need help, remember that you can always ask a mentor. Start on breadboard and test the circuit using a multimeter. Try different resistors to change the sensitivity. Once you are happy with the values, solder the circuits onto stripboard.
 Afterward, see if you can turn your tripwire sensor into a reflection-style sensor. Discuss with your team how you might use theses sensors on your robot.

**Things to consider:**

- Is a more sensitive detector necessarily better?
- Will the distance between the LED and phototransistor make a difference? Why?
- How could you make the IR beam from the LED narrower? Why might this be useful?

\pagebreak