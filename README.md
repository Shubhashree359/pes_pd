# PES Physical Design
Week 1 - Introduction;

Week 2 - RTL;

Week 3 - Physical Design

## Contents of Week 3
</details><details>
  <summary>Contents of Day 1</summary>
  
  ### Inception of open-source EDA, OpenLANE and Sky130 PDK 
  
 * How to talk to computers.
   * Introduction to QFN-48 Package, chip, pads, core, die and IPs
   * Introduction to RISC-V
   * From Software Applications to Hardware
* Soc Design and Openlane
    * Introduction to all components of open-source digital asic design
    * Simplified RTL2GDS flow
    * Introduction to OpenLANE and Strive chipsets
    * Introduction to OpenLANE detailed ASIC design flow
 * Open Source EDA Tools.
    * OpenLANE Directory structure in detail
    * Design Preparation Step
    * Review files after design prep and run synthesis
    * OpenLANE Project Git Link Description
    * Steps to characterize synthesis results

</details><details>
  <summary>Contents of Day 2</summary>
  
  ### Good floorplan vs bad floorplan and introduction to library cells
  * Chip Floor planning considerations.
    * Utilization factor and aspect ratio
    * Concept of pre-placed cells
    * De-coupling capacitors
    * Power planning
    * Pin placement and logical cell placement blockage
    * Steps to run floorplan using OpenLANE
    * Review floorplan files and steps to view floorplan
    * Review floorplan layout in Magic

* Library Binding and Placement.
   * Netlist binding and initial place design
   * Optimize placement using estimated wire-length and capacitanc
   * Final placement optimization
   * Need for libraries and characterization
   * Congestion aware placement using RePlAce

* Cell Design and Characterisation flow.
  * Inputs for cell design flow
  * Circuit design step
  * Layout design step
  * Typical characterization flow

* General timinig and Characterisation parameters.
  * Timing threshold definitions
  * Propagation delay and transition time

</details><details>
  <summary>Contents of Day 3</summary>
  
### Design library cell using Magic Layout and ngspice characterization
* Labs for CMOS inverter ngspice simulations.
   * IO placer revision
   * SPICE deck creation for CMOS inverter
   * SPICE simulation lab for CMOS inverter
   * Switching Threshold Vm
   * Static and dynamic simulation of CMOS inverter
   * Lab steps to git clone vsdstdcelldesign
* Inception of Layout CMOS fabrication process.
   * Create Active regions
   * Formation of N-well and P-well
   * Formation of gate terminal
   * Lightly doped drain (LDD) formation
   * Source and drain formation
   * Local interconnect formation
   * Higher level metal formation
   * Lab introduction to Sky130 basic layers layout and LEF using inverter
   * Lab steps to create std cell layout and extract spice netlist
* sky130 Tech file Labs
   * Lab steps to create final SPICE deck using Sky130 tech
   * Lab steps to characterize inverter using sky130 model files
   * Lab introduction to Magic tool options and DRC rules
   * Lab introduction to Sky130 pdk's and steps to download labs
   * Lab introduction to Magic and steps to load Sky130 tech-rules
   * Lab exercise to fix poly.9 error in Sky130 tech-file
   * Lab exercise to implement poly resistor spacing to diff and tap
   * Lab challenge exercise to describe DRC error as geometrical construct
   * Lab challenge to find missing or incorrect rules and fix them

</details><details>
  <summary>Contents of Day 4</summary>
  
### Pre-layout timing analysis and importance of good clock tree
* Timing modeling using delays.
   * Lab steps to convert grid info to track info
   * Lab steps to convert magic layout to std cell LEF
   * Introduction to timing libs and steps to include new cell in synthesis
   * Introduction to delay tables
   * Delay table usage Part 1
   * Delay table usage Part 2
   * Lab steps to configure synthesis settings to fix slack and include vsdinv
* Timing analysis with ideal clocks using openSTA
   * Setup timing analysis and introduction to flip-flop setup time
   * Introduction to clock jitter and uncertainty
   * Lab steps to configure OpenSTA for post-synth timing analysis
   * Lab steps to optimize synthesis to reduce setup violations
   * Lab steps to do basic timing ECO
* Clock tree synthesis TritonCTS and signal integrity.
   * Clock tree routing and buffering using H-Tree algorithm
   * Crosstalk and clock net shielding
   * Lab steps to run CTS using TritonCTS
   * Lab steps to verify CTS runs
* Timing analysis with real clocks using openTA
   * Setup timing analysis using real clocks
   * Hold timing analysis using real clocks
   * Lab steps to analyze timing with real clocks using OpenSTA
   * Lab steps to execute OpenSTA with right timing libraries and CTS assignment
   * Lab steps to observe impact of bigger CTS buffers on setup and hold timing

</details><details>
  <summary>Contents of Day 5</summary>
  
### Final steps for RTL2GDS using tritonRoute and openSTA
* Routing and Design rule check(DRC)
   * Introduction to Maze Routing and Lee's algorithm
   * Lee's Algorithm conclusio
   * Design Rule Check
* Power Distribution Network and routing.
   * Lab steps to build power distribution network
   * Lab steps from power straps to std cell powe
   * Basics of global and detail routing and configure TritonRoute
* TritonRoute Features.
   * TritonRoute feature 1 - Honors pre-processed route guides
   * TritonRoute Feature2 & 3 - Inter-guide connectivity and intra- & inter-layer routing
   * TritonRoute method to handle connectivity
   * Routing topology algorithm and final files list post-route
  
### Course
</details><details>
   <summary>  Week 3 -> Day 1 </summary>

   ### How to talk to computers.
   Any board is the processor/SoC with interfaces. Packages have predefined pins and these are connected to the chip using wires. Packages have components like pads (signals going inside the chip or out of the chip go through the pads), core (where all the digital logic sits),die, foundry IPs (like SRAM, ADC, DAC, PLL) and macros (like the SoC and SPI).
   
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

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/e2b9eedf-6f4a-4327-92ef-d803c0856c31)

ISA acts as the abstract interface between C language and the Hardware(Architecture of the Hardware)

ISA --> Assembler --> Binary --> RTL --> synthesis of RTL(netlist) --> Hardware(Physical Implementation of netlist

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/dcae4776-32de-4cca-831e-f8d6f8305b6d)

### SoC Design Using Openlane
ASIC - Application Specific Integrated Circits

TO build ASIC, we need
* RTL Design
* EDA Tools
* PDK Data

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/ecb28c75-782d-4c38-a116-9d4d8fb4a57e)

PDK(Process Design Kit) is the interface between the FAB and the designers. It contains process design rules, device models, digital standard cell libraries, IO libraries and much more

#### To go from RTL to GDS we need to follow the following steps:
 synthesis, floor/power planning, placement, clock tree synthesis, routing and sign off.

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/b2d5eb12-3bfe-40cc-8ed4-16434f1222dd)

* Synthesis – converts RTL into a circuit of components from the standard cell library.

* Floor and power planning – partition the chip die between different system building blocks and place the IO pads or define the dimensions, pin locations and routing tracks.

* Placement - place the cells on the floorplan rows. We have global and detailed placement.

* Clock tree synthesis – create clock distribution network with minimum clock skew.

* Routing – Implement interconnects using the available metal layers. We have global and detailed routing.

* Sign off – DRC, LVS and STA

### Intoduction to openLANE and Strives chipsets
 OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen and custom methodology scripts for design exploration and optimization.

strive is a family of open everything SOC's->open EDA,PDK's,RTL

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/34b1a11e-b6f2-48b2-9533-34770c47ce06)

Main goal is to produce GDSII with no human intervention (no-human-in-the-loop),no LVS violations, no DRC violation.

OpenLANE can be used to harden macros and chips.

openLANE has 2 modes of operation->autonomous or interactive

openLANE has design space exploration

openLANE comes with large number of design examples,there are 43 with best configurations

### Introduction to OpenLANE detailed ASIC design flow

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/ee368cb7-0ae1-4d25-861b-0bf23fb242f2)

* RTL Synthesis with constraints is done using Yosys and abc
* The design exploration utility is also used for regression testing.
* Openlane can run 70 designs and compare the results and find the best one.
* Scan Insertion
* automatic Test Pattern Generation
* Test Patter Compaction
* Fault Coverage
* Fault Simulation
* Physical Implementation - F&PF,Placement,CTS,Routing
* Verification is performed everytime netlist is modified.
* LEC is used to formally confirm that the function did not change after modifying the netlist.
* Antenna Checker
* RC Extraction
* Static timing Analysis
* DRC and LVS

Tool we will be working on pdk variant called sky130_fd_sc_hd

* sky130 : is the process name
* fd : skywater foundary
* sc : standard cell
* hd(high density) : variant of pdk

we will be using sky130 pdk

![Screenshot 2023-09-18 225723](https://github.com/Shubhashree359/pes_pd/assets/142501263/450cbbf2-4bd3-42b2-8ba8-65b28efc3318)

tools and process files

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/e7bca9ba-6018-4694-83b5-2a130b66cd4c)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/58653491-8461-4a6d-ae67-d09c51541fcb)

Design Preperation step First we go the the working directory
* cd Desktop/work/tools/
* cd openlane_working_dir/
* cd openlane

Now when we type the 
  docker
command a shell opens . In the shell we type 
  ./flow.tcl -interactive

![Screenshot 2023-09-18 230154](https://github.com/Shubhashree359/pes_pd/assets/142501263/f6afbbdb-32b6-4b93-85f3-5bda01ebb3ba)

list of designs already present in openlane

![Screenshot 2023-09-18 230410](https://github.com/Shubhashree359/pes_pd/assets/142501263/cb24c8d3-93fc-4a2a-975a-8726295d541a)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/6e4cb501-97de-48ad-b919-2ef91e0c3543)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/602ff361-cc4b-4bd3-bd1c-127e8ea2778b)

design setup stage(preparing stage)

prep -design picorv32a

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/d28bc095-8e29-4815-9860-ce1319332abc)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/3f6a6cee-8289-49f5-ac0e-05283a9d81bc)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/dd63de2d-fd0e-49a2-ba3c-c5a8c32e7f5c)

coming back to openlane

lets run the synthesis

run_synthesis

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/936f296b-8f13-4788-9a77-c3916705ee42)

We can observe the results in the runs folder

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/337c722d-139f-42e3-8bcd-a61aafe1d40e)

We are getting flip flop ratio as 10.843%

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/c0434bfa-e853-4792-a671-88387049bb9a)

Netlist generated

</details><details>
   <summary>  Week 3 -> Day 2 </summary>

## Contents of Day 2
* Chip Floor planning considerations.
* Library Binding and Placement
* Cell Design and Characterisation flow.
* General timinig and Characterisation parameters.
  
### Chip Floor planning considerations

How to come up with the Width and Height of the Core and Die.

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/e85fd5e9-e23e-4a40-8826-2ef3253faccd)

* Define the width and height of the core and die: we first begin with a netlist. Calculate the area occupied by the netlist on a silicon wafer. Inside the die, we have a core, where we place our digital logic. A die is a small semiconductor material specimen on which the fundamental circuit is fabricated. Utilization factor = area occupied by the netlist/total area of the core. Aspect ratio = height/width.

* Define the location of preplaced cells: Some cells perform certain tasks and can be re-instantiated multiple times like memory, clock gating cells, comparator, mux, and more. These IPs have user-defined locations and hence are placed on the chip before placement and routing which is why we refer to them as preplaced cells. The location of these cells is not modified during the PNR stages.

* surround pre-placed cells with decoupling capacitors: VDD takes care of the transition from 0 to 1. VSS takes care of the transition from 1 to 0. To connect VDD or VSS to the circuit we require wires, Since wires have physical dimensions, they will have resistance and inductances. These will reduce the supplied voltages. If the voltage drop is not in the noise margin range, the signal will be in an undefined area. So we can't guarantee that signal is 1 or 0. To prevent this, we add decoupling capacitors in parallel with the circuit. Every time the circuit switches, current is drawn from the capacitors. The RL network is used to replenish the charge in the capacitor.

* Power planning: When we have a bus of n bits and some logical operation must be done on it, the lines of the bus will either discharge or charge. When multiple capacitors discharge to VSS, the voltage of VSS might increase (ground bounce). When multiple capacitors charge to VDD, the voltage of VDD might decrease (voltage droop). Thus instead of power coming from one source, if it comes from multiple sources, we can avoid signals going into the undefined area.

* Pin placement: All input pins are on the left-hand side and all the output pins are on the right-hand side.

* Logical cell placement blockage: We block the area occupied by the pins to prevent the PNR tool from placing logical blocks where the pins are present.

* If installation of OpenLane was a local installation, use the following commands to set up magic and PDKs

For magic:

  sudo apt-get update
  sudo apt-get install magic
  
For PDK:
* git clone https://github.com/RTimothyEdwards/open_pdks.git git_open_pdks
* cd ~/git_open_pdks
* ./configure --enable-sky130-pdk --with-sky130-variants=all --prefix=/home/<unixusername>
* make
* make install

In this lab we are going to see the floorplan of our previously synthesized design picorv32a. Use the following commands.

* cd OpenLane
* sudo make mount
* ./flow.tcl -interactive
* package require openlane 0.9
* prep -design <file_name>
* run_synthesis
* run_floorplan

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/91b63e93-d6de-41f2-8dc7-8b5b8d6c0e6c)

Once floorplan is complete we need to open it in magic to view the floorplan

  cd ../OpenLane/designs/picorv32a/runs/<most_recent_run>/results/floorplan/
  magic -T ../git_open_pdks/sky130/magic/sky130.tech lef read ../OpenLane/designs/picorv32a/runs/<most_recent_run>/tmp/merged.nom.lef def read picorv32.def &

Once magic opens, we can see the cell. Use s and then v to center the floorplan. Use z to zoom in.

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/ef08025e-1946-484d-8353-6407909a79a1)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/cfd192c6-bae2-43c8-9a73-e40803bbc399)


![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/b3e82c5b-825d-4167-9255-59c36122666d)

## Library Binding and Placement

### Placement and routing
1) bind netlist withphysical cells

shape of the gates represent the functionality of the gates, inreality all gthe gates are represented as boxes each components are given proper shape library has all the height,width,delay informations of a particular cell and the required conditions of the cell,libraries can be further divided by shape/size and delay information. Libraries also contain various flavour of a particular cell

2) Placement 
   
![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/d74ad652-d85a-4875-a358-5bc0d9d56e9c)

3) optimise placement
   ![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/e3b8dd8f-1efd-4962-a47a-fd65804158a0)

We have to maintain signal integrity, so we use repeators,which are buffers that will re-condition the original signals make a new signal and replicates the original signal. There is loss of area despite maintainng signal integrity Signal integrity needs to be maintained in all the cells The distance between each cell is calculated by slew/ transition

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/15bd6ec9-4682-4da1-93c9-5310b94f6e23)

4) STA (static timing analysis
Library characterization and modelling Libraries provide standardized building blocks that enhance design productivity and reusability, while characterization provides the essential data needed to accurately model and simulate the behavior of these components, ensuring that the final design meets its performance, power, and reliability goals.

Congestion aware placement using RePlAce

Placement is of 2 tyoes detailed placement and global placement

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/2b2ab789-d6ea-44a3-9ad2-83f2e3a9a5e6)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/d459717f-7408-4944-9068-2243c962e511)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/2bdc4b41-b853-43de-8749-3044d356154f)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/e8daebbc-128d-4b17-bf92-cd625cc4d990)

## Inputs for cell design flow
Cell design flow refers to the process of creating and optimizing individual digital logic cells that are part of a standard cell library. These libraries contain a set of pre-designed, characterized, and reusable logic gates, flip-flops, and other basic building blocks used in the design of integrated circuits. These libraries include PDK, DRC and LVS rules, SPICE models, libraries, user-defined specifications. User derfined specifications like Pin location, drawn gate lenght are added to the libarary by the library developer


![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/171b85f1-d315-4bd5-81b3-fe21af7dd22b)

Circuit Design

Circuit design:Implment function using nmos and pmos and then derive the network graph. Derive the Euler's path and stick diagram from the graph.

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/a5a70b86-a257-4e35-b942-3b78404bb30f)

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/9914c054-d894-43da-999b-9b359af67f37)


Layout design Convert stick diagram according to the DRC rules Extraction of parasitics,extracted spice list

Characterization timing ,noise power.libs functions Read in the models and tech files and generate extracted spice Netlist. Read the subcircuits and attach power sources. Apply stimulus to characterization setup, provide neccesary output capacitance loads and provide neccesary simulation commands.

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/ff06bf27-fb0f-42e5-ac1f-f35cf1835eef)

## General timing characterization parameters

Timing threshold definitions

![image](https://github.com/Shubhashree359/pes_pd/assets/142501263/9e0456d5-8a30-4fc9-ba50-9d386a1ab269)

Propagation Delay The time difference between when the transitional input reaches 50% of its final value and when the output reaches 50% of its final value.

* Propagation delay=time(out_fall_thr)-time(in_rise_thr)

Transition Time The time it takes the signal to move between states is the transition time , where the time is measured between 10% and 90% or 20% to 80% of the signal levels.

* Rise transition time = time(slew_high_rise_thr) - time (slew_low_rise_thr )
* Fall transition time = time(slew_high_fall_thr) - time (slew_low_fall_thr)


































