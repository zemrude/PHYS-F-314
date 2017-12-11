
![](https://www.ulb.ac.be/dre/com/img/logo3lp-illu.jpg)

# Digital Laboratory

<small>
PHYS-F-314<br>
G. de Lentdecker, J. A. Aguilar<br>
ULB Service de Physique des particules élémentaries
</small>


<small><small>K. Hason 2010, inital version J. A. Aguilar 2017, revision </small></small>


### Introduction

The 74HC ICs will tolerate a power supply between 2 V and 6 V however 3.3 V and 5 V are common choices for real circuits today. We will use 5 V through this laboratory. The laboratory power supplies are variable up to 30 V. We will use a linear 3‐terminal regulator, the 7805, which will produce 5 V output for an input of approximately 7 V or higher (it has a “dropout” voltage of 1.7 V as specified in the [datasheet](https://www.sparkfun.com/datasheets/Components/LM7805.pdf)).

### 555 Timer Setup

You are going to need to make your own clock circuit to drive the sequential logic in the following portion of this laboratory. The Intersil ICM7555 will be the basis of your clock. Consult the datasheets for information on how to connect the external components to make a clock. You should use the “astable” alternate configuration with two external resistors and one external capacitor which produces a clock with a programmable duty cycle between 50 and 100%. Choose values of the resistance and capacitance to allow a clock with a frequency between 10 and 20 kHz and a duty cycle between 80 and 90%. Measure the clock with an oscilloscope and verify the frequency and duty cycle.

![](555.svg)

### CMOS Inverter

Using a pair of MOSFETS we can create an inverter using the following circuit:

![](CMOS.svg)

> **ATTENTION:** Be sure to connect the source (S) of the  ZVP3306A to the positive rail and the drain (D) to the drain of the ZVN3306A. Connect the input of the completed inverter to the output of the timer to obtain a clock with duty cycle between 10 and 20%. Verify by examination of the output with an oscilloscope.

### 2-Bit Adder

Implement the 2‐bit adder shown below. Use the 4-way DIP switches to encode the two 2-bit numbers. Use LEDs (with at least 100$\Omega$ in series to ground!) to indicate the 3-bit output (2-bit sum plus carry). You will need one [74HC86](https://assets.nexperia.com/documents/data-sheet/74HC_HCT86.pdf), one [74HC00](https://assets.nexperia.com/documents/data-sheet/74HC_HCT00.pdf), one [74HC02](https://assets.nexperia.com/documents/data-sheet/74HC_HCT02.pdf) and one [74HC04](https://datasheet.lcsc.com/szlcsc/74HC04D_C5590.pdf) to implement the gates (AND and OR are formed from NAND and NOR with an inverter)


![](adder.svg)

> **ATTENTION:** when using the multiple‐gate ’00 and ’02 be sure to connect either to ground or to Vcc all unused inputs -otherwise you will observe very strange behavior. Using the DIP switch step through all possible combinations of two‐bit inputs (16 combinations in total) and verify that the circuit adds the numbers correctly.



### SR Flip-Flop (Debouncer)

Connect two NAND or two NOR gates (1/2 x 74HC00 or 74HC02 – remember to not leave floating the unused inputs!!) in the SR flip-flop configuration. Add 2 pull‐down resistors to the inputs 1A and 2A and connect 1Y to 2B and 2Y to 1A. Observe what happens when you ‘pull‐up’ the inputs to the +5V rail by shorting a small length of connect wire to the +5V rail. Does this circuit correctly implement the truth table of the SR flip‐flop? As in the last exercise use LEDs with > 100 Ω in series to ground to indicate the output state, red for the Q and green for Q̅ output.

![](SR.svg)

### 4-bit ripple counter

Implement the 4‐bit ripple counter shown in Figure 4, again taking care to ensure that all inputs are properly connected and not left floating. Note that we have the 74HC109 Flip-Flops which are dual positive edge‐triggered devices and which additionally have the K input inverted – it’s a JK’ flip‐flop so please pay close attention to the [datasheet](https://assets.nexperia.com/documents/data-sheet/74HC_HCT109.pdf).

Using LEDs (yep, with 100 $\Omega$ or greater series resistors), setup an indicator for the output “count” currently being counted in the arrangement of registers.
Using an oscilloscope, note the propagation delays between the various outputs. What is the maximum speed at which you could clock such a circuit?

![](counter.svg)
