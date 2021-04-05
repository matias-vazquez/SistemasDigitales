<div align="right">

[![Support Server](https://img.shields.io/discord/591914197219016707.svg?color=7289da&label=ComputaciónTEC&logo=discord&style=flat-square)](https://discord.gg/xfB33VMq)
<!--- https://naereen.github.io/badges/ --->
</div>

# Lab 7. Design of Counters and Shift Registers

## Contents
* [Objectives](#objectives)
* [Pre-lab work](#pre-lab-work)
* [Lab procedure](#lab-procedure)
  * [Exercise 1. 8-bit Bidirectional Shift Register Implementation](#exercise-1-8-bit-bidirectional-shift-register)
  * [Exercise 2. BCD Up/Down Counter](#exercise-2-bcd-updown-counter)
* [Technical report](#technical-report)
* [Evaluation](#evaluation)

## Objectives
To use a HDL to implement by software two specific-purpose and commercially-available digital integrated circuits in a FPGA: the 74LS194 (4-Bit Bidirectional Universal Shift Register) and the 74LS169 (4-bit Up/Down Binary Synchronous Counter). For this, the specific objectives of this laboratory are
1. Understand the contents available in an integrated circuit datasheet to identify key design parameters to represent a low-complexity digital circuit by Register-Transfer Level (RTL) abstraction using VHDL
2. Design medium-complexity digital logics to implement in the FPGA using instances of RTL representations of digital integrated circuits. 

## Pre-lab work 
Complete the steps below:
1. Read the description and logic diagram of the __4-Bit Bidirectional Universal Shift Register (74LS194)__ and the __4-bit Up/Down Binary Synchronous Counter (74LS169)__ to understand the internal schematics, configuration parameters and input/ouput signals of both integrated circuits. 

<div align="center">

[![Generic badge](https://img.shields.io/badge/DATASHEET-74LS194-orange.svg)](http://pdf.datasheetcatalog.com/datasheets/70/375495_DS.pdf)
[![Generic badge](https://img.shields.io/badge/DATASHEET-74LS169-orange.svg)](http://pdf.datasheetcatalog.com/datasheet/philips/N74F169D.pdf)

</div>

2. Using two **74LS194** ICs, design an 8-bit bidirectional shift register. Draw the schematic diagram of your circuit, showing all inputs, outputs and internal nodes. 

3. Using two **74LS169** ICs, design an bidirectional BCD counter going from 00 up to 99, and from 99 down to 00. Draw the schematic diagram of your circuit, showing all inputs, outputs and internal nodes. 

4. Verify your designs using a digital circuit simulation tool of your choice. *In case you don't have a simulation software installed yet, Proteus 8 Professional is available for free for Tec community*.

<div align="center">

[![Generic badge](https://img.shields.io/badge/DOWNLOAD-PROTEUS-red.svg)](https://sites.google.com/tec.mx/canvas/proteus)

</div>

5. Turn in a pre-lab report that includes the schematics and simulation results for both designs. 

## Lab procedure

### **Exercise 1. 8-bit Bidirectional Shift Register** [![Generic badge](https://img.shields.io/badge/GITHUB-REPO-blue.svg)](https://experiencia21.tec.mx/)[![Generic badge](https://img.shields.io/badge/SCREEN-CAPTURE-blue.svg)](https://experiencia21.tec.mx/)[![Generic badge](https://img.shields.io/badge/DEMO-VIDEO-blue.svg)](https://experiencia21.tec.mx/)
1. Based on the 74LS194 description below, an from your readings on the datasheet, design an 8-bit  bidirectional shift register in VHDL. For this, begin by writing the RTL logic corresponding to the 74LS194 IC and then use two instances of it in your main entity. an unconnected block diagram of your entity is shown in the figure below: 

<div align="center">

<img width=400, src=img/ex01.png>

</div>

As a reference, use the pinout description of 74LS194 integrated circuit in the table below:

Port | Description
:--- | :---
`CLR` | Active low, asynchronous input. When active, the rest of inputs are ignored and Q outputs are 0
`D0-D3` | Data inputs. These bits are loaded in parallel to the register when S1=1 and S0=1
`Q0-Q3` | Shifting data outputs.
`S0, S1` | Control inputs. Depending upon their state, the shift register acts in consequence. 
→ `S0=1 S1=1` | Register is loaded in pararell with contents of D1-D4
→ `S0=0 S1=1` | Register is right-shifted and SR is loaded into Q3
→ `S0=1 S1=0` | Register is left-shifted and SL is loaded into Q0
→ `S1=0 S0=0` | No action
`SR, SL` | Direction bits. **S**hift **R**ight and **S**hift **L**eft, respectively

2. Once you entity is ready, create the constraints file to map the `D0-D7`, `S0` and `S1` to ten slide-switches for parallel loading and shifting control; `SR`, `SL`, `CLR` to three push-buttons; and finally, the `Q0-Q7` outputs to eight LEDs on the development board.

3. Setup your shift register to carry out a continuous left shifting sequence starting with a pre-loaded 8-bit value from `D0-D7`, and at a 5 Hz pace.

4. Change the settings, so this time, the pre-loaded byte is continuously right-shifted at 5 Hz.

### **Exercise 2. BCD Up/Down Counter**[![Generic badge](https://img.shields.io/badge/GITHUB-REPO-blue.svg)](https://experiencia21.tec.mx/)[![Generic badge](https://img.shields.io/badge/SCREEN-CAPTURE-blue.svg)](https://experiencia21.tec.mx/)[![Generic badge](https://img.shields.io/badge/DEMO-VIDEO-blue.svg)](https://experiencia21.tec.mx/)
1. Based on the 74LS169 description below, an from your reading of the datasheet, design a bidirectional BCD counter from 00 to 99 and viceversa. For this, begin by writing the RTL logic corresponding to the 74LS169 IC and then use two instances of it in your main entity. The resulting entity is shown in the figure below:

<div align="center">

<img width=400, src=img/ex02.png>

</div>

As a reference, use the pinout description of 74LS169 integrated circuit in the table below:

Port | Description
:--- | :---
`D0-D3` | Parallel data inputs
`CEP, CET`   | **C**ount **E**nable **P**arallel input (active low) and **C**ount **E**nable **T**rickle input (active low). Both inputs have to be active to enable count mode.
`PE`    | **P**arallel **E**nable input (active low). When active, data at D0-D3 is loaded into the register on the following positive clock transition.
`U/D`  | Up/Down count control input. High=Count up, Low=Count down
`Q0-Q3` | Flip-flop outputs. Maximum value should be 9 and minimum should be 0. 
`TC`    | **T**erminal **C**ount output (active low). Active when counter reaches 0x9 on Count Up mode, and when reaches 0x0 on Count Down mode. 

2. Once you entity is ready, create the constraints file to map the `D0-D7` to eight slide-switches for parallel loading: 4 for units and 4 for tens. Additionally, connect `CEP`, `CET`, `PE` and `U/D` to other four slide-switches for counting control. Finally, connect `Q0-Q8` outputs to two 7-segment displays on the development board through your previously developed BCD to 7-segment encoder.

3. Setup your counter to carry out a continuous upcount starting from 00 up to 99, on a 5 Hz pace.

4. Change the settings, this time for a continuous count down from 99 to 00 at a 5 Hz pace.

## Technical report

The design and implementation process should be documented in the technical report, along with the full VHDL code and demonstration video. Your report must include the following sections:

* Introduction
  * Explain what you did in this laboratory. 
  * Include a brief explanation of each *.vhdl* file writen for your project, such as the main entity, low-hierarchy RTL descriptions, peripheral drivers, and other relevant components. 
  * Consider technical specifications such as the included libraries, data types used, and further important information.
* Results
  * Screenshots of the working implementation on the development board
  * Link to video of the demo session
  * Link to GitHub with the VHDL source code
* Individual conclusions
  * Intepretation of results
  * Applications of and improvements of exercises
  * Justification in case of any errors
<div align="center">

[![forthebadge](https://forthebadge.com/images/badges/fuck-it-ship-it.svg)](https://experiencia21.tec.mx/)

</div>

## Evaluation

<div align="center">

Criteria      | Weight [%]
:-----------: | :---:
Demonstration | 60
Report        | 25
Pre-lab       | 10
Attendance    | 5

</div>

<div align="right">

Last updated: June 4, 2021 [![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

</div>

<div align="right">

[![forthebadge](https://forthebadge.com/images/badges/made-with-markdown.svg)](https://forthebadge.com)
</div>