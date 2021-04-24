<div align="right">
   <img src="img/teclogo.png">
</div>

# PWM Signal Generation

## Objectives

* To generate Pulse Width Modulation signals using VHDL and to be able to modulate the pulse width by code.
* To drive a servomotor at different shaft positions through HDL-generated PWM signals 

## Pre-lab work
Answer the following questions:
1. What is Pulse Width Modulation?
2. How the shaft position of a servo motor is related to the pulse width of a PWM signal? Give some examples for any servo motor you find online. 
2. By hand, draw three PWM signals with a period of 20 ms and duty cycles of 10%, 50% and 90%. In miliseconds, what is the corresponding **active** time (_e.g._ PWM = `1`) for each signal? 
3. The following table shows the __*Position vs. PWM duty cycle*__ of the SG-5010 servo motor, where, for a particular __*Shaft position*__, an specific PWM __*PWM duty cycle*__ is required, which is achieved by keeping the PWM signal high by a determined amount of clock cycles (__*Clock cycle count*__) for a 100 MHz clock frequency. 

<div align="center">

_Shaft position_ | _Clock cycle count_ | _PWM duty cycle_ 
:---: | :---: | :---:
0&deg; | 50,000 | 2.5 % [0.5 ms]
45&deg; | 100,000 | 5% [1 ms]
90&deg; | 150,000 | 7.5% [1.5 ms]
135&deg; | 200,000 | 10% [2 ms]
180&deg; | 250,000 | 12.5% [2.5 ms]
</div>

5. Given the following VHDL code for PWM signal generation, determine which line you need to change to position the shaft of the servo motor on 0&deg;, 45&deg;, 90&deg;, 135&deg; and 180&deg;. Add a column to the table above showing the corresponding VHDL line that accomplishes such shaft positioning. 

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.NUMERIC_STD.ALL;

entity main_pwm is  
port (
    clk100m : in std_logic;			--- Internal Nexys 4 Board clock signal
    btn_in  : in std_logic;			--- Push-button input
    pwm_out : out std_logic			--- PWM signal to servo motor
);
end main_pwm;

architecture Behavioral of main_pwm is

subtype u20 is INTEGER range 0 to 2_000_000;	        -- Data type INTEGER only for range from 1 to 2,000,000
signal counter      : u20 := 0;

constant clk_freq   : integer := 100_000_000;           -- Clock frequency in Hz (10 ns)
constant pwm_freq   : integer := 50;                    -- PWM signal frequency in Hz (20 ms)
constant period     : integer := clk_freq/pwm_freq;     -- Clock cycle count per PWM period
constant duty_cycle : integer := 50_000;                -- Clock cycle count per PWM duty cycle

signal pwm_counter  : std_logic := '0';                 -- Internal PWM signal

begin
    pwm_generator : process(clk100m) is
    variable cur : INTEGER range 0 to period := 0;      -- CLK pulse counter
    begin
        if (rising_edge(clk100m) and btn_in = '1') then
            counter <= cur;                             -- SIGNAL that allows to see CLK pulse count on simulation
            cur := cur + 1;  
            if (cur <= duty_cycle) then                 -- Duty cycle (PWM high)
                pwm_counter <= '1'; 
            elsif (cur > duty_cycle) then               -- PWM low
                pwm_counter <= '0';
                if (cur = period) then                  -- Counter reset when period reached
                    cur := 0;
                end if;
            end if;  
        end if;
    end process pwm_generator;
    pwm_out <= pwm_counter;
end Behavioral;
```
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
   * The initial position is 0&deg;. An input pulse in `POS` by the push-button moves the shaft to 45&deg;. Subsequent button pulses move the shaft to 90&deg;, 135&deg;, 180&deg;, and back to 0&deg; 
   * The 7-segment displays shows the angle position of the motors shaft
   * Play the following video to show the expected behavior:

<div align="center">

[![Demo video](https://img.youtube.com/vi/WJTofpTIy2Y/0.jpg)](https://www.youtube.com/watch?v=WJTofpTIy2Y)
</div>

## Deliverables
The design and implementation process should be documented in the technical report, along with the full VHDL code and a demonstration video (3 minutes maximum). Your report must include the following sections:

1. Introduction
   * Explain what you did in this laboratory.
   * Include a brief explanation of each _.vhdl_ file wrirten for your project (_e.g.,_ main entity, lower hierarchy RTL descriptions, peripheral drivers, etc.). Consider technical specifications such as the included libraries, data types used, and other relevant information.
2. Results
   * Screenshots of the working implementation on the development board
   * Link to video of the demo session
   * Link to GitHub with the VHDL source code
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