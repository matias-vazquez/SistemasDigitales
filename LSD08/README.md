# PWM Signal Generation (draft)

## Objectives

* To generate Pulse Width Modulation signals using VHDL and to be able to modulate the pulse width by code.
* To drive a servomotor at different shaft positions through HDL-generated PWM signals 

## Pre-lab work

1. What is Pulse Width Modulation?
2. Design a VHDL component with an input clock signal of 100 MHz, and an output signal with a 50 Hz (20 ms period), 1.5 ms work cycle, as the one shown below:

## Lab work

1. Design in VHDL a servomotor driver to control the motor shaft on 5 different positions. For this, your entity must have the following ports:

### Inputs

<div align="center">

Signal | Length | Comments
:--- | :--- | :----
`CLK` | 1 bit | 100 MHz
`POS` | 1 bit | Push-button to control shaft position
</div>

### Outputs

<div align="center">

Signal | Length | Comments
:--- | :--- | :---
`PWM` | 1 bit | Servomotor driving signal
`SEGM` | 8 bits | Cathodes for quad 7-segment display
`AN` | 4 bits | Enable for quad 7-segment display
</div>

2. Account for the following restrictions in your design:
   * Use the _numeric bit_ library
   * The initial position is 0. An input pulse in `POS` by the push-button moves the shaft to 45. Subsequent button pulses move the shaft to 90, 135, 180, and back to 0 
   * The 7-segment displays shows the angle position of the motors shaft
   * Play the following video to show the expected behavior:

<div align="center">

[![Demo video](https://img.youtube.com/vi/WJTofpTIy2Y/0.jpg)](https://www.youtube.com/watch?v=WJTofpTIy2Y)
</div>

## Deliverables
The design and implementation process should be documented in the technical report, along with the full VHDL code and a demonstration video (3 minutes maximum). Your report must include the following sections:

<div>

<iframe width="560" height="315" src="https://www.youtube.com/embed/WJTofpTIy2Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>

1. Introduction
   * Explain what you did in this laboratory.
   * Include a brief explanation of each .vhdl file writen for your project, such as the main entity, lower hierarchy RTL descriptions, peripheral drivers, and other relevant components (consider technical specifications such as the included libraries, data types used, and further relevant information)
2. Results
   * Screenshots of the working implementation on the development board
   * Link to video of the demo session
   * Link to GitHub with the VHDL source code
3. Individual conclusions
   * Interpretation of results
   * Applications of and improvements of exercises
   *Justification in case of any errors

## Evaluation
<div align="center">

Criteria | Weight 
:--- | :---:
Attendance | 5%
Pre-lab | 10%
Lab report | 25%
Demonstration | 60%
</div>