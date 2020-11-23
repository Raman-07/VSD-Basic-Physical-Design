# VSD-Basic-Physical-Design
This repository elucidates the 5-day workshop of VSD Beginner Physical Design conducted by VLSI System Design (VSD) using opensource EDA tools. The workshop is categorised between two parts one is learning skills and second is MCQs. The detailed description of the workshop is given below. 

## DAY-1
Day 1 is dedicated to the introduction of open acess tools used during the workshop and RISC-V architecture. The workshop is purely cloud based and linux based labs are provided through Virtual Network Computing (VNC) to get a good hands on experience on open acess EDA tools.

### Concepts Introduced
- Die, Core, I/O pads, Bonding wires
- IC pacakages (QFN)
- Macros and Foundary IPs
- RISC-V architecture and RTL to GDS flow
- EDA tools
 
The process of communication between application software and hardware was explained with the example of RISC-V ISA. In RISC-V flow, the high level language (C, JAVA etc.) program is converted to RISC-V instruction set using compiler. Further, the implementation of RISC-V ISA is done using a Hardware Description Language (HDL) which is finally converted into machine language by an assembler. Thus, the communication takes place as Apps >> System Software (Compiler + Assembler) >> Hadware (Layout).

**RTL to GDS flow:**

**1. Synthesis :** Synthesis is the process of mapping an RTL (Synthesizable Verilog code) to technology specific gate level netlist. This gate level netlist includes all the information of nets, sequential and combinational cells and their connectivity.  
- Tool used : **ysosys**

**2. Floorplan & Power Planning :** Floorplanning deals with the macro placements, power and ground grid placement and I/O pads placement. Floorplannig is an arrangement of all the logical blocks (i.e. AND, Inverters, Multiplexers), power grids and macros on silicon chip.
- Tool used : **graywolf**

**3. Placement :** Placement is process of assigning correct physical locations to predesigned cells on the chip. Placement is done in such a way so that interconnect delays can be minimum. Firstly global placement is done which is nothing just a rough placement and then detailed placement is done which further improves the global placement in iterative manners.
- Tool used : **graywolf**

**4. Clock Tree Synthesis :** Clock tree synthesis (CTS) includes the clock routing patterns. It is done to ensure that clock is arrived at the same time to all the sequential circuits. This step holds significant importance because clock is going to ensure that all the data is transmitted in its true manner.
- Tool used : **graywolf**

**5. Routing :** During routing, clock routing is done at the first with the help of CTS andthen other signal's routing takes place. Routing is the process of connecting all the cells and blocks using a set of wires in horizontal and vertical manner with the help of certain routing algorithms.
- Tool used : **Qrouter**

**6. Static Timing Analysis :** Static Timing Analysis (STA) is the process in which all the possible timing violations are considered. Basically setup time and hold time violation is examined and adequate measures are taken to solve these issues.
- Tool used : **Opentimer**

**7. Layout :** After all the abovementioned steps the layout of the design is done in which includes Design Rule Check (DRC), Layout Versus Schematic (LVS), Parasitic extraction and post layout simulations. Post layout simulation results are compared with the prelayout simulations and after this verification a gds file is extracted and send for the fabrication.
- Tool used : **Magic**

## DAY-4
On Day 4, we were introduced to power aware clock gating technique which helps in the reduction of power consumption by a chip. Thereafter, a concept of delay table, STA with ideal clock, CTS , cross talk and net-shielding alongwith timming analysis with real clock was explained in detail.

- **Delay Table :** 
During process of routing, clock signals are routed from i/p pin of chip to different flip-flops (FF) in a design. During such process buffers are added in the path. These buffers have a delay associated with them and to represent such delay, a delay table is used. This delay table is based on input signal transition at the input of buffer and capacitive load at its output.

- **STA with ideal clock :** 
A concept of STA with ideal clock was introduced in which ideal clock refers to clock reaches to all the flip-flops at the same time instant. Thereafter, how setup and hold time vioalations effect the design functionality and how to mitigate such setup and hold time violations using setup/hold time equation was discussed in detail. For example, the set-up time equation is:

Combinational delay + Clock network delay(launch FF) < clock period + Clock network delay(capture FF) - Set-up time(capture FF) - Set-up uncertainity(capture FF)

- **Clock Tree Synthesis (CTS) :** 
In clock tree synthesis, the importance of good tree, bad tree, H tree clock distribution network with its advantages were discussed.

- **Cross-talk and Net-shielding:** 
Cross-talk happens when two wires get routed very close to each other. Such cross-talk causes glitch in the data which needs to be removed to transmit the true data. Therefore, to avoid the effect of cross-talk net-shielding concept is used.

- **STA with real clock:**
In real clock, all the possible delays such as wire dealys are considred. To provide proper voltage levels of clock signal to different blocks, repeaters are added in their path. At this stage, STA is performed with the modified set-up/hold time equation which includes all the clock network delays. Eventually, STA is done to ensure that clock skew is zero or positive where clock skew is the difference between clock network delay at launch FF and clock network delay at capture FF.

### Lab Assessment
The abovementioned theoretical concepts were made us to understand via carrying out STA in Qflow. The lab details that includes STA commands and analysis are as follows:













