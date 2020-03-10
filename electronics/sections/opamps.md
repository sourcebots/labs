# Use of Operational Amplifiers (Op Amps)

An operational amplifier is a "differential" device. That means it takes 2 inputs, measures the difference between them, then outputs this voltage increased by a factor known as "gain". The two inputs of are normally identified as the "inverting" and "non-inverting", indicated on the schematic by "-" and "+" respectively.

## Outcomes

### Robot Progress
* Implementing a comparator system

### Knowledge
* Op-amp operation
* Configuring op-amps as comparators

### Skills
* Breadboard prototyping
* Basic soldering

## Theory
An operational amplifier is a device that takes 2 inputs, measures the difference between them, then outputs this voltage increased by a factor known as "gain". The two inputs of are normally identified as the *inverting* and *non-inverting*, indicated on the schematic by "-" and "+" respectively.

\begin{center} \includegraphics [height=5cm] {img/opamp.png} \end{center}

An op-amp requires two different supply voltages to function. Op-amps can be either single supply, which require a positive supply and ground, or dual supply, which require a positive and negative supply along with a ground connection.

These supplies determine the maximum and minimum output voltages of the op-amp as it will be unable to exceed these voltages, regardless of its gain. When the output is at a maximum or minimum we say the op-amp is *saturated*. For a real op-amp the saturation output is usually slightly lower than the power supply voltage.

The open-loop gain of an op-amp is typically on the order of 100,000. In other words, if the supply were large enough, a 1 mV difference between the inputs would result in a 100V output.

The simplest use of an op-amp is a *comparator* circuit, as shown below.

\begin{center} \includegraphics[height=5cm] {img/comparator.png} \end{center}
\begin{center} \includegraphics[height=8cm] {img/Op-amp-breadboard.png} \end{center}

In this configuration the output will be high if the non-inverting output is higher than the inverting input. Otherwise the output will be low.

## Task - Building a comparator circuit
* Build the circuit shown above, connecting the signal generator in place of voltage supply V2. 
* Set the signal generator to produce a sinusoidal output with a peak to peak amplitude of 5 volts and a DC offset of 2.5 volts. 

- What happens if you change the values of R1 and R2?
- What happens if you connect your phototransistor in place of the signal generator?

**Things to consider:**

- How could a comparator circuit be useful for your robot?
- What is the advantage of using this circuit instead of analogue readings from the Arduino?

\pagebreak