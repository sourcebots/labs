# Metal Object Sensor

For this year's game the scoring zones will be marked out with metal tape.

Using what you have learned in previous labs about switches, you can place metal contacts on your robot so you can detect when you have passed one of these strips.

The schematic below illustrates the basic circuit setup. Anything inside of the black border is in your robot:


\begin{center} \includegraphics[height=8cm]{img/metal_strip.png} \end{center}


In the above figure, the grey box is a metal object. When the contacts are not on a metal object the Arduino pin is pulled **HIGH** by **R1**, but when the contacts are connected by a metalic object, the pin is pulled **LOW** through the object (The object and **R1** actually form a potential divider where the resistance across the object is *very low*, less than $1\Omega$. What is the voltage between the Arduino pin and 0V in this potential divider?).

## Tasks

 - Using the theory learned above, build a circuit that will implement the above functionality and think about how you could use this for your robot.

 - Connect an LED to pin 2 on the Arduino and make it turn on when the circuit is completed. You will need to put a resistor in series with the diode to avoid damaging it. We'd recommend a value of $330\Omega$.

The diagram below illustrates the required circuit for above:

\begin{center} \includegraphics[height=8cm]{img/led-series.png} \end{center}


 - Write a program that keeps track of how many times you have completed the circuit and make it iluminate an LED after the circuit has been completed three times. Connect the metal contact into pin 5.

### Switch bounce

 You might find that your counting circuit from the previous task is quite unreliable and seems to register lots of contacts each time you touch something. This is because the contacts can easily 'bounce' when they are connected. This effect happens very quickly, so you won't be able to see it but your Arduino can read it's input pins fast enough for it to count each small bounce as a new time a connection has been made. To make your counter more reliable you need to make sure it only counts once each time you connect the metal contacts.
- One way of doing this is to force the Arduino to wait for a few milliseconds after detecting a connection has been made so that all the 'bouncing' has stopped before it carries on running it's code. This means it is spending time doing nothing though - including not controlling your robot so we need to find a "non-blocking" way of dealing with this instead.
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

- Try to improve your counting circuit / code to deal with switch bounce. If you use a capacitor, this is where it should go:

\begin{center} \includegraphics[height=8cm]{img/debounced_metal_strip.png} \end{center}
