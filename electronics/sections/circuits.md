# Introduction to Circuit Construction and Testing
This section of the lab aims to equip you with the skills you need to construct circuits for your robot. In its most simple form, a circuit provides a path for current to flow from a voltage source to ground, usually doing some useful work on the way.

## Constructing Circuits
### Breadboards
A breadboard is a way of quickly prototyping circuits. A breadboard consists of a piece of plastic with small holes arranged in a grid. 
Underneath the plastic surface, each column has a metal component. This metal piece has two purposes. Firstly, it provides an electrical connection between each of the components in a row, and secondly, clamping onto the leg of a component to hold it in place.
While this provides a fast, easy way to test whether your circuit will work, the components are not held in place strongly enough 
for this to be a long term solution.

Along with the connections in each column of the breadboard, which are often split into two sides along a centre line, which is marked by a deep channel,
the breadboard has two long rows along the top and bottom. These are split along the middle (marked by a W), and are useful for providing
supplies to your circuit, for example 5V and Ground.

### Stripboard
As mentioned previously, breadboard is often not suitable for creating a circuit permanently. This is what stripboard (also known as protoboard) is used for
Protoboard allows you to solder your components into place for a more permanent solution. Stripboard is arranged in the same way as breadboard. Place the components legs through from the plastic coated side,
and then solder the legs to the exposed copper on the bottom. One area where stripboard is more flexible than breadboard is the ability to break the copper trace.
This allows multiple components to be placed in the same column without connecting them. A specialist tool is used to do this.

## Testing Circuits
### Powering your Circuit
The best way to initially test your circuit is to use one of the power supplies on your desk. These come in two forms in our lab, 30V,2A and 15V,5A. These power supplies come with adjustable voltage (in both coarse and fine increments) and 
current limit. The current limit should always be used as it prevents excessive short circuit currents. This can prevent damage if it is set appropriately. Generally, you should calculate how much current your circuit should draw and 
set the current limit slightly above that. In order to use these supplies, they must first be turned on using the switch to the left, which will allow you to set voltage
and current limits, and then the output must be enabled by pressing the button to the right. The output being enabled is indicated by a small LED. This can be connected to your circuit by using the screw terminals labled "+" and "-" using wire.

### Taking Measurements from Circuits
In the lab, you will find that your desk has both an oscilloscope and a digital multimeter. 
These are both useful tools for investigating issues within your circuit, but have different functions.
#### Multimeters
A Digital Multimeter (DMM) is a useful tool for general debugging of a circuit, being able to measure a number of different physical properties. On the front panel of the device
there are buttons to choose what the DMM will measure. This allows you to take readings of resistance, capacitance, current, voltage, diode polarity, and continuity.
While these are extremely useful for identifying components, and checking circuit information such as supply voltages, they are often lacking 
when it comes to observing rapidly changing signals. DMMs are generally used with the red and black test leads found on your desk.

#### Oscilloscopes
Oscilloscopes are far more specialist than DMMs, generally providing only a measure of voltage or current. 
However, where these devices excel is in providing a visual representation of the signal. This can be much more useful than the information
that a DMM would provide in instances where a signal is only present for a short time. These use probes rather than test leads to take measurements, and generally require 
more setup than a DMM to provide any usable data. 

In order to monitor a signal, there are 3 main things that require set up: The channel that the oscilloscope is reading from (this can be multiple channels simultaneously,
and unused ones can be turned off if they are getting in the way), along with both the horizontal and vertical scales. The horizontal scale represents time, while the vertical scale represents signal magnitude.
The selected timescale is used for all channels, while the vertical scale is set per channel.

The oscilloscopes in the lab also have an autoset function. This is normally worth trying first, however, it is not always suitable, depending on the signal contents.

## General Circuit Debugging Tips
- Visually inspect your circuit. Are there any solder bridges between components? Does something look like it isn't soldered in or is lose in the breadboard.
- Is your circuit drawing the amount of current that you expect it to?
- Check your supply rails, are they at the voltages that you expect them to be?
- Is the power supply showing the voltage you set it at? If not, this usually indicates either a short circuit (normally this would result in lower than the set voltage between the terminals, and more current than expected being drawn) or 
the current limit being set too low. Think about how much current you expected.
- Does anything in your circuit feel hot?
- Think about what you would expect your signals to be doing. Use the oscilloscope to verify this is happening. Start from the beginning of your circuit, and work forward.
Find where you stop seeing things that you are expecting. This is generally where the fault lies.
