# PES Physical Design
Week 1 - Introduction
Week 2 - RTL
Week 3 - Physical Design

## Contents of Week 3

### Contents of Day 1
* How to talk to computers.
* Soc Design and Openlane
* Open Source EDA Tools.

### Contents of Day 2
* Chip Floor planning considerations.
* Library Binding and Placement*
* Cell Design and Characterisation flow.
* General timinig and Characterisation parameters.

### Contents of Day 3
* Labs for CMOS inverter ngspice simulations.
* Inception of Layout CMOS fabrication process.
* sky130 Tech file Labs

### Contents of Day 4
* Timing modeling using delays.
* Timing analysis with ideal clocks using openSTA
* Clock tree synthesis TritonCTS and signal integrity.
* Timing analysis with real clocks using openTA
### Contents of Day 5
* Routing and Design rule check(DRC)
* Power Distribution Network and routing.
* TritonRoute Features.
  
### Course
</details><details>
   <summary>  Week 3 -> Day 1 </summary>

   ### How to talk to computers.
   Chip design 
   
   ![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/a63f89c9-d705-4a6a-9057-e5d69cbfd519)
   
   let get inside a chip
   
   ![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/270db554-ae5b-4077-8aeb-8b26f6dbc2a0)
   ![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/392f63b6-3e0c-4f33-ac7a-790bc7017c7c)

   PADS - the ways signal comes inside or goes outside
   
CORE - all the digital logic recides

DIE - size of the chip

Foundry IP's - PLL,adc,dac,sram

foundry - factory where chip get manufactured

macros - Soc, SPI

ISA the way we talk to the computer

How to run a C Program on a cpu, there is a certain flow

RISC Architecture -> Implementation(RTL) -> Layout

C program -> Assemble Level program -> Machine level program

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/0ef7bac7-76fc-4991-94cc-065b2c3bc55e)

Applicatioin software -> System software -> Hardware

System software has complier and assembler

OS handles IO Operation, allocates memory ans low level system functions.

Application --> OS --> C code --> Complier --> ISA --> Assembler --> Binary Code --> Hardware
