# Metal Object Sensor

For this year's game. We will have metal tape at various points around the arena and as you are probably aware, the cans are also metal!

Using what you have learned in previous labs about switches, you can place metal contacts on your robot so you can detect when you have passed a strip or are touching a can.

The schematic below illustrates the basic circuit setup. Anything inside of the black border is in your robot:


\begin{center}  \includegraphics[height=8cm]{img/schem.png} \end{center}

*Figure 1: Pull-up configuration for the sensor circuit.*

In the above figure, the green lines represent metal contacts and the grey box is a metal object. The circuit essentialy functions like a switch, when both contacts hit a metal object, the circuit completes and the Arduino will read a **LOW** value on the pin.

When the contacts are not on a metal object. The Arduino pin is pulled **HIGH** by **R1**.

## Tasks

 - Using the theory learned above, build a circuit that will implement the above functionality and think about how you could use this for your robot.
     - To build the metal contacts,

 - Connect an LED to an unused GPIO pin on the Arduino and make it turn on when the circuit is completed. You will need to put a resistor in series with the diode to avoid damaging it. We'd reccomend a value of 4.7K.

 - Write a program that keeps track of how many times you have completed the circuit and make it buzz or iluminate an LED after the circuit has been completed three times.

## Simon Says (Extension)
Let's have a bit of fun, load the file simon_says.py from [INSERT LINK HERE] and put it onto your robot USB!

Wire up two more of the metal contact circuits and two more LED circuits and plug them into [LED GPIO PINS HERE].

Run the Simon Says game on your robot and play the game!
