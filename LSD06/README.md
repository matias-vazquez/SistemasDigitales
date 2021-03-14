# The Library numeric_std

## Objectives

* To become familiar with the implementation of the numeric_std library in a VHDL system for arithmetic operations, by developing a simple signed 8-bit calculator.

## Pre-lab

* Investigate the internal wiring of a 4x4 matrix keypad, and the 

## Lab work

Design in VHDL a signed calculator with the following inputs and outputs:

* Inputs
  * Clock
  * Operand A
  * Operand B
  * Operation selector
  * Display selector 
* Outputs
  * Sign bit
  * Operation LEDs 
  * 7-segment display data
  * 7-segment display enable

Consider the following restrictions
  
  * Only numeric_std library is allowed to called
  * The calculator must carry out three basic arithmetic operations: addition, subtraction, and multiplication
  * Numbers A and B are represented using 4 slide switches from the Nexys 4 DDR board
  * Negative numbers have to be introduced using two’s complement representation
  * Three more slide switches are used as operation selectors (OS) as follows:

OS value (binary)  | Arithmetic operation
:----------------: | --------------------
001                | Addition
010                | Subtraction
100                | Multiplication

In any other case, no operation in carried out and output is zero. Also, consider that eventhough the corresponding button is pressed and released, the selection should be saved and performed.

  * The 7-segment display is used to display both operands and result in unsigned representation. Negative numbers are accompanied by a minus sign (-) in the immediate digit to their left. See the figure below as a reference (```-2 + -6 = -8```):

![7-segment display setup](img/fig01.png)

## Report

Turn in a technical report including the following:
•	Links to GitHub of Activities of part I and II
•	Links to YouTube with demo videos of your working code
•	Screenshots of the Terminal showing the output of your programs
•	Conclusions
