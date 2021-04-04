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

### Excercise 1
Port | Description
:--- | :---
CLRN | Active low, asynchronous input. When active, the rest of inputs are ignored and Q outputs are 0
D1-D4 | Data inputs. These bits are loaded in parallel to the register when S1=1 and S0=1
Q1-Q4 | Data outputs
S0, S1 | Control inputs. Depending upon their state, the shift register acts consequently
SR, SL | Direction bits. Shift right and shift left, respectively

## Report

## Evaluation

