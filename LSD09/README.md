<div align="right">
   <img src="img/teclogo.png">
</div>

# 16x2 LCD Display Driver

## Objectives

To write the HDL driver for a 16x2 matrix LCD displays using Finite State Machines (FSM). 

## Pre-lab work
The 16x2 matrix LCD display is driven by the __HD44780 Dot Matrix LCD Controller/Driver__ integrated circuit. The driver datasheet is available on the link below:

<div align="center">

[![LCD Simulator](https://img.shields.io/badge/HD44780-Datasheet-blue.svg)](https://www.crystalfontz.com/controllers/Hitachi/HD44780/)
</div>

Based on the HD44780 datasheet, answer the following questions:

1. Read pages 9 through 12 of the HD44780 LCD display driver datasheet to describe the function of the following flags, registers and memory:

<div align="center">

Function register |   
:--- | 
Instruction Register (IR)
Data register (DR)
Busy flag (BF)
Address Counter (AC)
Display data RAM (DDRAM)
</div>

2. How can we read BF? 

3. Check the driver _Reset Function_ description on Page 23, and the _Instruction Set_ detailed on Table 6 (pages 24 and 25) to draw a flowchart that describes an LCD initialization process that meets the following requirements (use as references Table 13 on page 43-44, and flowchart on page 45):

    * 8-bit interface data
    * Two lines disaply
    * Display __on__
    * Cursor __on__ and __blinking__

4. What us the instruction  to send to the LCD display to write the character `A` on the current cursor position?

4. What is the instruction to send to the LCD display to locate the cursor on the second line, first column?

5. Use the LCD display simulator to write the team members' first name on each line of the display. 

<div align="center">

[![LCD Simulator](https://img.shields.io/badge/LCD-Simulator-blue.svg)](http://www.dinceraydin.com/djlcdsim/djlcdsim.html)
</div>

## Lab procedure

1. Wire up the LCD display to the Nexys 4 DDR board following the connection table below:

<div align="center">

LCD Display | Nexys 4 DDR
:--- | :---
Data bus (__D0:7__) | __JA__ (1:4,7:10) [`C17, D18, E18, G17, D17, E17, F18, G18`]
Register select (__RS__) | __JB1__ [`D14`] 
Read/Write (__R/W__) | __JB2__ [`F16`]
Enable (__E__) | __JB3__ [`G16`]
</div>

2. Write in VHDL the initialization sequence for the LCD display following the requirements from the pre-lab work using Finite State Machines. 

3. Write in VHDL LCD write code to display the team members' first name on each line of the LCD display using Finite State Machines. 

## Deliverables
The design and implementation process should be documented in the technical report, along with the full VHDL code and a demonstration video (3 minutes maximum). Your report must include the following sections:

1. Introduction
   * Explain what you did in this laboratory.
   * Include a brief explanation of each _.vhdl_ file written for your project (_e.g.,_ main entity, lower hierarchy RTL descriptions, peripheral drivers, etc.). Consider technical specifications such as the included libraries, data types used, and other relevant information.
2. Results
   * Screenshots of the working implementation on the development board
   * Link to video of the demo session
   * Link to GitHub repository of the full VHDL source code
3. Individual conclusions
   * Interpretation of results
   * Applications of and improvements of exercises
   * Justification in case of any errors

## Evaluation
<div align="center">

Criteria | Weight 
:--- | :---:
Attendance | 5%
Pre-lab | 10%
Lab report | 25%
Demonstration | 60%
</div>

## References

<div>

<img width="650" src="img/instructions.png">

</div>