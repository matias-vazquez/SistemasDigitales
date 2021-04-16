# Lab 10. VGA Controller

## Objectives
To design a VGA controller using HDL throughout sync generation. 

## Pre lab work

* Answer the following questions using as a reference Section 9 of the _Nexys 4 DDR Reference Manual_.
  1. Which VGA signals we aim to control from the Artix'7 FPGA and to which pins are these signals mapped in the development board?

  2. Setting `HIGH` or `LOW` signals `R`, `G` and `B`, which color can we obtain?

  3. Why there are some time intervals that we cannot display any information?

  4. Which clock frequency is necessary to generate for a 640x480 screen resolution with a 60 Hz refresh rate?

* HS and VS signal generation
  1. How could you generate _Horizontal Sync_ and _Vertical Sync_ signals using the Nexys 4 DDR board. Write the corresponding VHDL code. 

## Lab procedure
Design in VHDL a VGA controller. Consider the following inputs and outputs:

<div align="center">

Inputs | Length | Properties
:--- | :--- | :---
`Clock` | [1 bit] | @ 100 MHz
`Reset` | [1 bit] | Push-button

Outputs | Length | Properties
:--- | :--- | :---
`HS` | [1 bit]
`VS` | [1 bit]
`VIDEO_ON` | [1 bit]
`COLUMN` | [10 bits]
`ROW` | [10 bits]
</div>

### `HS` and `VS` signals
<div align="center">
<img src="img/HSVS.png">
</div>

### `VIDEO_ON_H` and `VIDEO_ON_V` signals
<div align="center">
<img src="img/VIDEO_ON.png">
</div>

`VIDEO_ON = VIDEO_ON_H AND VIDEO_ON_V`

Write a testbench to carry out signal verification on the simulation stage. Check that `HS` and `VS` meet the timming criteria described in the datasheet.

<div align="center">
<img src="img/row1.png">
<img src="img/row1.png">
</div>

Once the signals are verified on simulation, use an oscilloscope to verify the generated signals on the VGA port of the development board. 

## Deliverables



