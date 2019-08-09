# Metal Object Sensor

### Robot Progress
* Creation of a metal tape detector

### Knowledge
* Need for a pull-up resistor
* Switch bounce and how to avoid it

### Skills
* Breadboard prototyping
* Component selection
* Basic soldering

For this year's game the scoring zones will be marked out with metal tape.

Using what you have learned in previous labs about switches, you can place metal contacts on your robot so you can detect when you have passed one of these strips.

The schematic below illustrates the basic circuit setup. Anything inside the black border is in your robot:

\begin{center} \includegraphics[height=8cm]{img/metal_strip.png} \end{center}

In the above figure, the grey box is a metal object. When the contacts are not on a metal object the Arduino pin is pulled **HIGH** by **R1**, but when the contacts are connected by a metalic object, the pin is pulled **LOW** through the object (The object and **R1** actually form a potential divider where the resistance across the object is *very low*, less than $1\Omega$).

### Task 1

 - Build a metal object sensor using the theory above

 - Connect an LED to pin 2 on the Arduino and make it turn on when the circuit is completed. You will need to put a resistor in series with the diode to avoid damaging it. We'd recommend a value of $330\Omega$.

\begin{center} \includegraphics[height=8cm]{img/led-series.png} \end{center}


 - Write a program that keeps track of how many times you have completed the circuit and make it iluminate an LED after the circuit has been completed three times. Connect the metal contact into pin 5.

## Switch bounce

 You might find that your counting circuit from the previous task is quite unreliable and seems to register lots of contacts each time you touch something. This is because the contacts will usually 'bounce' when they are connected. This effect happens very quickly so you won't be able to see it, but your Arduino can read it's input pins fast enough for it to count each time a contact is made. To make your counter more reliable you need to make sure it only counts once each time.

### *Debouncing* a switch 
- You can avoid switch bounce in software by programming the robot to wait for a few milliseconds after detecting a connection has been made. This means it is spending time doing nothing - including controlling your robot - so we need to find a "non-blocking" way of dealing with this instead.
- You can also solve it in hardware, by adding a capacitor to your circuit. The potential difference across a capacitor takes time to change, so it will *smooth* the signal from the switch.

\begin{center}  \includegraphics[height=8cm]{img/Series_RC_capacitor_voltage.png} \end{center}

The voltage rise is exponential, described by the time constant $\tau = RC$. Think about what capacitance values might be suitable.

- There are also far more complicated circuits you could use for this that would work better (if you are interested, have a look at [Schmitt triggers](https://en.wikipedia.org/wiki/Schmitt_trigger)). However like most engineering problems, you need to weigh up the pros and cons of each option based on:

    - Performance
    - Cost
    - Simplicity
    - Reliability
as well as other factors based on your specific project. Which method do you think is the best for your robot?

### Task 2 - Debouncing
* Implement a debouncing solution for your metal strip detector.
* If you decide to use a capacitor, your circuit should be:

\begin{center} \includegraphics[height=8cm]{img/debounced_metal_strip.png} \end{center}

**Things to consider:**

- How can you mount this sensor on your robot?
- How many sensors would you need?