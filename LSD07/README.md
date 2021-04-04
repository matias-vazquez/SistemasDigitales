# Lab 7. Design of Counters and Shift Registers (draft)

## Objectives
To use a HDL to implement by software two specific-purpose and commercially-available digital integrated circuits in a FPGA: the 74LS194 (4-Bit Bidirectional Universal Shift Register) and the 74LS169 (4-bit Up/Down Binary Synchronous Counter). For this, the specific objectives of this laboratory are
1. Understand the contents available in an integrated circuit datasheet to identify key design parameters to represent a low-complexity digital circuit by Register-Transfer Level (RTL) abstraction using VHDL
2. Design medium-complexity digital logics to implement in the FPGA using instances of RTL representations of digital integrated circuits. 

## Pre-lab work 
Complete the steps below:
1. Read and understand the description and logic diagram of the __4-Bit Bidirectional Universal Shift Register (74LS194)__ and the __4-bit Up/Down Binary Synchronous Counter (74LS169)__ to study the internal schematics, configuration parameters and input/ouput signals of both integrated circuits. 

<div align="center">

[![Generic badge](https://img.shields.io/badge/DATASHEET-74LS194-orange.svg)](http://pdf.datasheetcatalog.com/datasheets/70/375495_DS.pdf) 
[![Generic badge](https://img.shields.io/badge/DATASHEET-74LS169-orange.svg)](http://pdf.datasheetcatalog.com/datasheet/philips/N74F169D.pdf)

</div>

2. Using two 74LS194 ICs, design an 8-bit bidirectional shift register. Draw the schematic diagram of your circuit, showing all inputs, outputs and internal nodes. 

3. Using two 74LS169 ICs, design an up/down counter going from 00 up to 99, and from 99 down to 00. Draw the schematic diagram of your circuit, showing all inputs, outputs and internal nodes. 

4. Verify your designs using a digital circuit simulation tool of your choice. *In case you don't have a simulation software installed yet, Proteus 8 Professional is available for free for Tec community*.

<div align="center">

[![Generic badge](https://img.shields.io/badge/DOWNLOAD-PROTEUS-blue.svg)](https://sites.google.com/tec.mx/canvas/proteus)

</div>

## Lab procedure

### **Exercise 1. 8-bit Bidirectional Shift Register Implementation**
1. Based on the 74LS194 description below, an from your reading of the datasheet, design an 8-bit  bidirectional shift register. For this, begin by writing the RTL logic corresponding to the 74LS194 IC and then use two instances of it for your final design. The resulting entity is shown in the figure below:

<div align="center">

<img width=400, src=img/ex01.png>

</div>

Pinout description of 74LS194 integrated circuit pinout. 

Port | Description
:--- | :---
CLRN | Active low, asynchronous input. When active, the rest of inputs are ignored and Q outputs are 0
D0-D3 | Data inputs. These bits are loaded in parallel to the register when S1=1 and S0=1
Q0-Q3 | Shifting data outputs.
S0, S1 | Control inputs. Depending upon their state, the shift register acts in consequence. 
→ S0=1 S1=1 | Register is loaded in pararell with contents of D1-D4
→ S0=0 S1=1 | Register is right-shifted and SR is loaded into Q3
→ S0=1 S1=0 | Register is left-shifted and SL is loaded into Q0
→ S1=0 S0=0 | No action
SR, SL | Direction bits. **S**hift **R**ight and **S**hift **L**eft, respectively

2. Once you entity is ready, create the constraints file to map the D0-D7, S0 and S1 to ten slide-switches for parallel loading and shifting control; SR, SL, CLR to three push-buttons; and finally, the Q outputs to the LEDs on the development board.

3. Setup your shift register to carry out a continuous left shifting sequence starting with a pre-loaded 8-bit value, on a 5 Hz pace. 

4. Change the settings, so this time, the pre-loaded byte is continuously right-shifted at 5 Hz.

### **Exercise 2. BCD Up/Down Counter**
1. Based on the 74LS169 description below, an from your reading of the datasheet, design an up/down BCD counter from 00 to 99 and viceversa. For this, begin by writing the RTL logic corresponding to the 74LS169 IC and then use two instances of it for your final design. The resulting entity is shown in the figure below:

<div align="center">

<img width=400, src=img/ex02.png>

</div>

Pinout description of 74LS169 integrated circuit pinout. 

Port | Description
:--- | :---
D0-D3 | Parallel data inputs
CEP, CET   | **C**ount **E**nable **P**arallel input (active low) and **C**ount **E**nable **T**rickle input (active low). Both inputs have to be active to enable count mode.
PE    | **P**arallel **E**nable input (active low). When active, data at D0-D3 is loaded into the register on the following positive clock transition.
U/D   | Up/Down count control input. High=Count up, Low=Count down
Q0-Q3 | Flip-flop outputs. Maximum value should be 9 and minimum should be 0. 
TC    | **T**erminal **C**ount output (active low). Active when counter reaches 0x9 on Count Up mode, and when reaches 0x0 on Count Down mode. 

2. Once you entity is ready, create the constraints file to map the D0-D7 to eight slide-switches for parallel loading: 4 for units and 4 for decens. Additionally, connect CEP, CET, PE and U/D to other four slide-switches for counting control. Finally, connect Q0-Q8 outputs to two 7-segment displays on the development board through the previously developed encoder.

3. Setup your counter to carry out a continuous upcount starting from 00 up to 99, on a 5 Hz pace. 

4. Change the settings, this time for a continuous count down from 99 to 00 at a 5 Hz pace.

## Report

## Evaluation

