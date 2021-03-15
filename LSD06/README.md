# The Library numeric_std

## Objectives

* To become familiar with the implementation of the numeric_std library in a VHDL system for arithmetic operations, by developing a simple signed 8-bit calculator.
* To develop a VHDL testbench for design simulation from scratch.
* To implement a 4x4 keypad as input peripheral to the FPGA and write the corresponding driver in VHDL.

## Pre-lab

### Background on *numeric_std*

Read the online documentation of the *numeric_std* library for VHDL and answer the following questions:
  1. What type of signals must be used to perform arithmetic operations using *numeric_std*?
  2. If your signed calculator design considers both, signed and unsigned numbers, which type of signal must be declared for the operands and result vectors?
  3. Show the syntax to convert from ```std_logic_vector``` to ``signed`` and ``unsigned`` signal types, and viceversa.
  4. Show the syntax to convert from ```integer``` to an 8-bit ```std_logic_vector``` data types, and viceversa.
  5. Show the correct VHDL syntax to carry out a multiplication of two vectors initially defined as ```std_logic_vector(7 downto 0)``` using the *numeric_std* library?
  
### 4x4 Keypad Interfacing

  1. Investigate the internal wiring of a 4x4 matrix keypad, and explain how to read and identify a pressed key.
  2. Write the pseudo-code of the keypad driver. Clearly identify the inputs and outputs.
  3. Draw the schematic diagram of the keypad including pull-up resistors with values, and connections to the FPGA. Depict with arrows all port directions (in, out or inout) from the FPGA point of view. 

## Lab work

Design in VHDL a signed calculator and implement your design in the Artix 7 FPGA. Consider that only the *std_logic_1164* and *numeric_std* libraries are allowed to be called in.  Consider the following inputs and outputs:

* Inputs
  * Clock (E3 pin from development board)
  * Operand A
  * Operand B
  * Operation selector
* Outputs
  * Sign bit
  * Operation LEDs 
  * 7-segment display data
  * 7-segment display enable

Moreover, consider the following restrictions:
  
  * The calculator must carry out three basic arithmetic operations: addition, subtraction, and multiplication.
  * Operands A and B, and the operation selection are introduced using a 4x4 keypad connected to GPIO pin header A of the Nexys 4 DDR board [see Reference Manual](https://reference.digilentinc.com/reference/programmable-logic/nexys-4-ddr/reference-manual).
  * Negative numbers have to be introduced using two’s complement representation
  * Three more slide switches are used as operation selectors (OS) as follows:

OS value (binary)  | Arithmetic operation
:----------------: | --------------------
001                | Addition
010                | Subtraction
100                | Multiplication

In any other case, no operation in carried out and output is zero. Also, consider that eventhough the corresponding button is pressed and released, the selection should be saved and performed.

  * The 7-segment display is used to display both operands and result in unsigned representation. Negative numbers are accompanied by a minus sign (-) at the immediate digit to their left. See the figure below as a reference (-7 + -8 = -15):

<p align="center">
  <img width=500 src="img/fig01.png">
</p>

Write a Testbench for your calculator design. Here, set Operand A as ```x"08"```


## Report

Turn in a technical report including the following:
•	Links to GitHub of Activities of part I and II
•	Links to YouTube with demo videos of your working code
•	Screenshots of the Terminal showing the output of your programs
•	Conclusions

## Evaluation

<div align="center">

Criteria      | Weight [%]
:-----------: | :---:
Demonstration | 60
Report        | 25
Pre-lab       | 10
Attendance    | 5

</div>

<p align="right">Last update: March 14th, 2021 by Matías Vázquez</p>