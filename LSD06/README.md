# The Library numeric_std

## Objectives

* To become familiar with the implementation of the numeric_std library in a VHDL system for arithmetic operations, by developing a simple signed 8-bit calculator.

## Pre-lab

* Read the online documentation of the *numeric_std* library for VHDL and answer the following questions:
  1. What type of signals can be declared to perform arithmetic operations using *numeric_std*?
  2. If your design considers both, signed and unsigned numbers, which type of signal is desired to declared in such case?
  3. What is the VHDL syntax to carry out a multiplication of two ```std_logic_vector(7 downto 0)``` signals?

* Investigate the internal wiring of a 4x4 matrix keypad, and the 

## Lab work

Design in VHDL a signed calculator and implement your design in the Artix 7 FPGA. Consider that only the *numeric_std* library is allowed to be called in.  Consider the following inputs and outputs:

* Inputs
  * Clock
  * Operand A
  * Operand B
  * Operation selector
* Outputs
  * Sign bit
  * Operation LEDs 
  * 7-segment display data
  * 7-segment display enable

Consider the following restrictions
  
  
  * The calculator must carry out three basic arithmetic operations: addition, subtraction, and multiplication.
  * Operands A and B, and the operation symbol are introduced using a 4x4 keypad connected to GPIO pin header A of the Nexys 4 DDR board
  * Negative numbers have to be introduced using two’s complement representation
  * Three more slide switches are used as operation selectors (OS) as follows:

OS value (binary)  | Arithmetic operation
:----------------: | --------------------
001                | Addition
010                | Subtraction
100                | Multiplication

In any other case, no operation in carried out and output is zero. Also, consider that eventhough the corresponding button is pressed and released, the selection should be saved and performed.

  * The 7-segment display is used to display both operands and result in unsigned representation. Negative numbers are accompanied by a minus sign (-) at the immediate digit to their left. See the figure below as a reference (-7 + -8 = -15):

![7-segment display setup](img/fig01.png)

Write a Testbench for your design. 


## Report

Turn in a technical report including the following:
•	Links to GitHub of Activities of part I and II
•	Links to YouTube with demo videos of your working code
•	Screenshots of the Terminal showing the output of your programs
•	Conclusions
