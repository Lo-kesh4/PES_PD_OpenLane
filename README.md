# pes_pd
# Day-1 Inception of open source EDA ,openLANE and Sky130 PDK


</details>	

 <details>
 <summary> How to talk to computers  </summary>

### Introduction to QFN-48 package,chip,pads,core,die and IPs

 
 ![pd1](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/7da74702-9420-4872-960e-81339d4c0f8e)

 
 Block diagram of Arduino board


 ![pd2](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/c87f0870-8bba-4e3f-b347-d7e33db6a4e2)

 IC in board (Package : QFN -48 Quad flat No-leads)
 
 

![pd3](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/16bd0abf-d166-416b-bcb4-5539bab55247)

example:

![pd4](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/5b85bbf4-ab29-49d3-a71d-2b7c22dd01c8)

> chip is at the centre of the package


> the way the chip is connected to package is by **wirebounce**


> through **wirebounce** ,able to transfer all the signal from outside world


chip:

![pd5](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/4c47281f-2f94-4289-9a0a-b9da48318f34)

components:

1. **PADS** :through which, can send signal inside the chip and viceverse
2. **core** : where all digital logic sits

3. **Die** : size of the entire chip,manufactured on the silicon 

RISC SoC:


![pd7](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/90631909-0ff7-45ba-8ea5-073f0d41694d)


Foundary Ips(intellectual properties) 

Macros : pure digital logic


### Introduction to RISC-V


![pd8](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/5b59a5bc-328d-464d-b3ca-56bc98a9dac8)


### From software Application to hardware

![Screenshot (182)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/e26f7e75-d474-40ac-9198-7e1f7bb8582b)


> c or any other language converted in to assembly level language by complier then assembly in turn converted in to binary code which hardware can understand


> there are two main interface


1. instructions (also called architecture of computer)

2.assembler,which converts assembly level to binary code





**Example:clock**

![Screenshot (181)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/d5d9eeac-e267-49fa-a5a2-ba479e3730ce)



</details>	
	
 <details>
 <summary> SoC Design and OpenLANE  </summary


### Introduction to all components of open-source digital asic design

**open source digital asic design**


![Screenshot (185)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/dbdd9025-835f-4ca5-8c54-b08c3c323585)



**Process Design Kit(PDK)**: 

> In the field of semiconductor manufacturing, a PDK is a set of files and data used by semiconductor designers to create and verify the physical layout of an integrated circuit (IC) on a silicon wafer.
> It includes information about the fabrication process, device models, and design rules


> PDK is the interface between fabrication and the designer


> google worked out an agreement with sky water the open source PDK for the 130nm process by skywater

> june 30 2020 google relewased first ever PDK open source

![Screenshot (186)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/b1174e08-aa59-4b6d-99e8-4e7b01beb6e9)


is 130nm fast?
yes it is ,
here are two examples:

![Screenshot (187)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/c1849600-fda9-4a21-947f-45e0bc84ae4c)


### simplified ASIC design flow:

![Screenshot (188)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/ed8c20fc-a6ac-4685-b23c-d92cd12742d0)

1. **synthesis**:
> coverts RTL to a circuit out of components from the standard cell library(SCL)

![Screenshot (190)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/767567d2-fcae-4695-b640-e8a096ca7893)

> standard cells,each cell has different views/models

--> Electrical, HDL,SPICE

--> Layout (Abstract and Detailed)


2. **floor /power planning**:


it depends on whether we are implementing the single component (MacroFloor planning)or whole chip(chip Floor planning)

macro Floor planning : Dimensions, pin locations,rows definition

![Screenshot (192)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/9917b9e9-f970-4233-b6ea-7462d67d0882)



chip Floor planning: partition the chip die between different system building blocks and place the I/O pads

![Screenshot (193)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/0cf29d23-1247-4fbf-9223-ea32c1d6fd4c)



3.**placement**

placements are done in tw steps:


--> global placemnts find optimal positions for old cells,cells may overlap

--> Detailed placements


4.**clocl tree synthesis**:

--> To deliver the clock to all sequential elements (e.g., FF) with minimum skew And in agood shape

-->Tree(H,X,...)


5. **routing**

--> implement the interconnect using the available metal layers

--> Metal tracks form a routing grid

--> Routing grid is huge 

--> Divide and Conquer


-- **Global Routin**g:Generates routing guides 


-- **Detailed Routing** : Uses the Routing guides to implement the actual wiring


6. **sign off**


--> **physical Verifications**

--Design rules Checking(DRC)


--Layout vs.Schematic(LVS)


-->**Timimg Verification**


--Static Timing Analysis



### Intoduction to openLANE and Strives chipsets

The problem is tougher when using Open source EDA


> Tools Qualificationa

> Tools Calibration

> Missing tools




**OpenLANE**

> Started as an Open Source Flow for a True Open Source Tape-out Experiment

> striVe is a family of Open everything SoCs

-- Open PDK, Open EDA,Open RTL


striVes has different members :

1. striVe : Sky 130 SCL + Synthesized 1Kbytes SRAM

2. striVe 2 : Sky 130 SCL +  1Kbytes Open RAM block

3. striVe 2a : striVe 2 with a single chip core module

4. strive 3 : OSU SCL + Synthesized 1Kbytes SRAM

5. striVe 5 : Sky 130 SCL + 8 x 1 Kbytes openRAM banks

6. striVe 6 : striVe 2 with DFT


![Screenshot (195)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/2860f943-a999-467e-9d83-35c8c37ebb62)



> The main goal of OpenLANE is to produce NO LVS violations , NO DRC violations and timing violations



> OpenLANE Tuned for SkyWater 130n Open PDK

OpenLANE has two modes of operation:

-- Autonomous or interactive

-- DesignSpace Exploration: find the best set of flow configuration



> OpenLANE has more number of design examples there are 43 design with their best configuration


### Introduction to OpenLANE detailed ASIC design flow

![Screenshot (196)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/e3d53506-ef0e-4020-a950-33ae9aff0e95)


![Screenshot (197)](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/ac9d7579-40e5-4c39-9efd-64748a9f175b)



**Design For Test(DFT)**

> Scan Insertion

> Automatic Test Pattern Generation(ATPG)

> Test Patterns Compaction

> Fault Coverage

> Fault Simultion



**Logic Equivalence Check(LEC)**:

This is done by using **yosys**



>  Every time the netlist is modified ,verification must be performed

- CTS modifies the netlist

- post placement  optimizations modifies the netlist



> LEC is ude3s to formally confirm that the function did not change after modifying the netlist



**Dealing with Antenna Rules Violations:**

>  When ametal wire segment is fabricated ,it can act as an antenna.

- Reactive ion etching causes charge to accumulate on the wire

- Transistore gates can be damaged during fabrication

so for this problem we have two solutions :



1.Bridging attaches ahigher layer intermediary (requires Router awareness)


2. Add antenna diode cell to leak away charges (Antenna diodes are provides by the SCL)

- Add a fake Antenna Diode next to every cell input after placement


- Run the Antenna checker (Magic) in the routed layout

- if the checker reports a Violation on tthe cell input pin,replace the Fake Diode cell bu a real one




**Static Timing Analysis :**

> RC Extraction : DEF2SPEF

> STA: openSTA (openROAD)

</details>	
	
 <details>
 <summary> Get familiar to Open-source EDA tools  </summary>

 ### openlane Directory structure 

Sky 130A is pdk variant
which has two sub directries 

1. lib.ref : all the processor specific files

we will be working on pdk variant called sky130_fd_sc_hd

- sky130  : is the process name 

- fd : skywater foundary

- sc : standard cell

- hd(high density) : variant of pdk

2. lib.tech :specific to the tool



 ![Screenshot from 2023-09-09 15-55-07](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/6bcaf760-d917-4601-9aca-3872e9dc8024)


![Screenshot from 2023-09-09 16-02-27](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/cf9c5c18-c378-48ca-b00a-d941e9db811e)


### Design Preperation step



 after installing the openlane flow

 go to the terminal and run following command for access the openlane:

 > cd/desktop/works/tools/openlane_workshop__dir/openlane

> docker

> ./flow.tcl -interactive

> package require openlane 0.9



![Screenshot from 2023-09-09 16-30-35](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/cc22233d-3a1b-4a79-8860-365f30f16333)





![Screenshot from 2023-09-09 22-14-04](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/8113bfae-c09e-4e24-ac7a-0f7825e02d05)




![Screenshot from 2023-09-09 22-14-35](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/73b39a21-749b-48b2-a612-a2f70cae03cf)

### review files after design and run synthesis


![Screenshot from 2023-09-09 22-15-40](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/54068f86-6344-4a54-8e80-46ba7f3a6c06)



![Screenshot from 2023-09-10 15-59-02](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/6b132569-9151-4b67-8b6c-59c6565f7971)


![Screenshot from 2023-09-10 15-59-59](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/c2457dc5-a570-49a0-94c3-fcc1b6d3e68c)


![Screenshot from 2023-09-10 16-18-50](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/fcfc0075-200f-4d4c-8264-4a7ca123bd5c)


![Screenshot from 2023-09-10 16-20-34](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/bf37658d-f413-4f51-b630-2d58bd594e10)



![Screenshot from 2023-09-10 16-40-56](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/e49811bd-91ce-43dd-99d0-394689276fb2)


**we will calculate filflops ratio**


</details>

# Day-2 Good floorplan vs bad floorplan and introduction to library cells

 <details>
 <summary> Chip Floor planning considerations  </summary

 ### Utilization factor and aspect ratio

 **Define width and height of core and die**

 
 
![Untitled1](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/89e7c398-e484-48ed-9d72-3ca319762fcb)

minimum area requires for nelist given above

![Untitled2](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/792a84ef-1036-4cac-9c1a-f89f1ca53f79)


 calculating  area occupied by the above netlist on a silicon  wafer

 ![Untitled3](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/73dd995b-fe4a-4a24-aa1d-3cddcf8ee056)



utilization factor =(areaoccupied by netlist)/(Total area of the core)


for the above netlist there is 100 % utilization and utlization factor is 1
> if this  the case we cannot add extra components(for optimization) to the die since there is no spcae in die (i.e., utlization is 100%)


> so in many cases we will keep utilization factor approximately 0.5 or 0.6.



**aspect ratio**


aspect ratio=(height)/(width)


> here for above netlist aspect ratio is 1 whuch signifies that the chip is square shaped .id ratio is other than 1 then chip is rectangle shaped.


### pre-placed cells


![Untitled4](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/af7b7365-e798-4e33-a7da-7bb1de82ede3)



![Untitled5](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/dad5dcf7-c7c5-4571-92fb-8cb3578790c9)



similarly there are ither IP's available

- memory

- clock gating cell

- camparator

-mux


> the arrangement of these IP's  is reffered as floorplanning

> these IP's have user defined locations ,and hence are placed  in chip before automated placement -and-routing and are called **pre-placed cells**

>  Automated placement and routing tools places the remaining logical cells in the design onto chip


### de-coupling capacitor 


![Untitled1](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/2131e526-9a01-4529-9b6d-f8e3fe8a09f0)


- During switching operation, the circuit demands switching current  i.e., peak current

- due to the presence ofRdd and Ldd there will be a voltage drop across them and the voltage atnode'A' would be Vdd

  
Noise margin Graph


![Untitled1](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/24c9d75e-692d-442b-b8e9-6aab437bda58)

- any voltage lies between vOL to VIL ----logic 0


- any voltage lies between VOH to VIH ----logic 1

- in the undefined region any voltage can go either areas (0 or 1) which is danger(grey area).so in this we have problem of large physical distance ,here comes the concept of **De-coupling**

> De-coupling capacitors are huge capacitors filled with charge


> as name says decoupling it de couples circuit from main supply


**no switching activities are missed** by using decoupling capacitor



### power planning


after solving the problem current demand  using de-coupling 
now we have problem of signal power supply ,i.e.,

if a particular macro is repeated multiple times on chip then the current demand for each and every elemt of macro

![Untitled3](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/435a7f46-0568-4c5b-a2b8-a4f123ca1358)


- assume signal(0-1) has been sent from driver to load

- we should make sure that load is receiving the same signal from driver

![Untitled4](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/d1fe97ee-2e23-4ae8-a185-e2b10d5f0a4d)


NOTE: we sont have any decoupling capacitor in the path from driver to load 


> assume 16 bit bus is connected to inverter

in this case all the charged capacitior should discharge and discharged should be charged


![Untitled5](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/19b41112-dc22-485b-94b3-84e1ebaf61e6)


![Untitled6](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/12682a9b-2d8f-4333-87df-ce188601db3d)

> in the above case all the charged capcitor are discharging at the same time and having same ground ,here we can see **ground bounce** and , it either goes to 1 or 0 which not predictable

![Untitled7](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/fe53bf89-4543-41d2-a84e-719433b32191)


> in the above case all the discharges capacitor are charging at the same time and they have only one power supply so we can see **voltage bounce**

**problem is due to singal power supply**

we can solve this using multiple power supply

> by using multiple power supplies capacitors takes current from nearest power supply and dump the current to the nearest ground



![Untitled8](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/5dcec9e9-c056-4256-b686-753c8b749317)


![Untitled9](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/77369ad2-c7d1-418e-a1e3-0a5233032a07)




### pin planning


ordering of input and output ports are random



![Untitled1](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/0193fd1b-0c39-48e6-aff5-94231e4b95c9)



### steps to run flooeplan using openLANE

![Screenshot from 2023-09-19 11-59-00](https://github.com/Lo-kesh4/PES_PD_OpenLane/assets/131575546/0a9c2630-698d-4825-84e0-ed2b5ea865a7)



![Screenshot from 2023-09-17 16-06-59](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/23a54bfd-0cd1-4d09-adc6-3450de2a9754)




![Screenshot from 2023-09-17 16-08-05](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/fb49d854-1003-49a8-abf2-2e6ebedf9a1a)



![Screenshot from 2023-09-17 16-11-48](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/bc4ece4f-db54-463d-809c-f3d391673ff5)



now to acsess the layout design we need to follow the following commands


-  /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-09_11-57/results/floorplan

-  less picorv32a.floorplan.def

- shift q

- magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &



![Screenshot from 2023-09-17 18-28-59](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/8aae29a9-27de-4896-ad71-dc42368ca167)


![Screenshot from 2023-09-17 18-23-35](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/1db34670-07af-4c1c-9c6d-5e5b4c3eee3d)


![Screenshot from 2023-09-17 18-24-47](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/57e5d94f-fee6-443a-b786-71b8cb3238f5)



![Screenshot from 2023-09-17 18-26-35](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/109e3682-13aa-4529-ada8-053a49661462)


![Screenshot from 2023-09-17 18-28-09](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/858c6fd0-b8d5-4780-a6d9-c5b5155051f2)


</details>

<details>
<summary> Library Binding and placement </summary>

### netlist binding and initial place design
![Untitled2](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/841327a2-722f-45b3-819d-539fd0ffcaa0)

![3](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/ac7cafe2-94cd-4503-abf8-a24e997f3bd2)


![4](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/a4b8bae4-3795-4412-92e8-25a6007b34ce)


Library --it contains informsation of delay of gates,shapes andsize of the cells

larger the size least is resistance 

**placing netlist on to the floorplan**

![5](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/98aa6adc-6ced-46a3-94d5-97256a8f2f1f)


sice there huge distance between the some flipflops we can fix it by optimizing



### optimize placement using estimated wire length and capacitance

here comes the concept of repeaters to minmize the distance between flipflop 

Repeaters are buffer which recondition the original signal ,replicated original signal and send so that the integrity of the signal remains same but there is lose of area.


![6](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/e2b7c34d-dfc5-4129-9830-18d9cd003d72)


### Need for characterization

**design flow for implementing design on to chip**

1) **logic synthesis** :convert functionality in to legal hardware.

- output of logic synthesis is arrangement of gates  representing the original functionality using RTL


2) **Floorplanning**: import the output of logic synthesis

- decide the size and shape of core and die

3) **placement**:logic cells in logic synthesis are placed on the chip

4) **clock tree synthesis**: clock signal reaching every point of cells

5) **Routing**

6) **static time analysis**:set up time, whole time ,maximum acheivable frequency of circuit


![7](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/99a61ef2-797f-4c8b-b030-42461ff4a7e3)



![8](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/46d0e20d-8a57-4b74-b031-dfd41c150ead)



![9](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/5ade5dfc-216d-4366-9c4c-0cd72f871857)




### congestion aware placement using RePlAce 


![Screenshot from 2023-09-17 20-13-09](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/6a2a1c0c-ea18-4fcc-8fae-4f361ffbf696)


</details>
<details>
<summary>cell design and characterization flow</summary>

 ### inputs for cell design flow

 ![10](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/89f0cb28-da4d-4f69-9474-b92044a9d54a)


 cell design flow has 3 parts 

 1) Inputs

 2) Design steps

 3) Outputs


**1) Inputs:** Process design kits


- DRC and LVS rules ,SPICE models,library and user defined specs

![11](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/3a90cc15-4ea0-488f-847a-3d3edb95a692)


**Use defined specs**

- cell height -- seperation between the power grill and ground grill(Dry strenghth) should be maintained

![12](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/15b04593-6d9c-4de7-bfc4-5afa55271cce)

- supply voltage : take care of noise margin level with resppect to voltage

- Metal layers
- 
![13](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/fa182eff-d76b-4205-818d-26044fc5608c)

- pin location

- Drawn gate-length


**2)Design Steps :** Circuit design,layout design,characterization

![14](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/964b5148-5fdc-47e9-997e-a4fcba047298)


![15](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/e77f458a-3763-48ad-87ae-74754a2a2112)

**3)outputs:** circuit description language,GDS2 ,LEF,extracted spice netlist(.cir),Timing ,noise ,power .libs,function

### Typical characterization flow

1) read model files

2) read extracted spice netlist

3) define behaviour of buffer

4) read sub circuit of cell

5) attach the neccessary pwer sources

6) apply the stimulus

7) providing neccessary output capacitance

8) necessary stimulation command


![16](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/ee406128-9df3-4eb7-9c05-38d08fec7a9a)



![17](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/6e146a8c-e2ff-4d2e-ba7a-1cf5b462a64e)



![18](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/258ff183-c124-4308-aa10-d40f812620bc)


</details>
<details>
<summary>General timimg characterization parameter</summary>

### Timing threshold definitions

threshold point of waveforms

**two inverters back to back**

![19](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/14bd6b9f-523b-41bd-b104-5bd984628fda)


slew low rise threshold: defines the point towards the lower side of power supply.Typical value is 20
%

slew high rise threshold: defines the point towards the higher side of power supply.Typical value is 20
%

in rise threshold:generally take 50% of input waveform

outrise threshold:generally take 50% of output waveform


![20](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/7b691f03-c72a-4b6a-b727-1f93017380bc)

### propagation delay and transition delay

#### propogation delay


![21](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/1dab8904-3c32-46dd-91ab-1b4fcb31244c)

- case where threshold are choosen in a right way and circuit is designed properly

![23](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/f47dbcca-a67d-4c29-b768-aa71a424c1aa)

- case where threshold value are not choosen in a right way
  
![22](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/6371ea3f-5fdc-45a2-890b-6b525033de4a)


- case where threshold are choosen in a right way but circuit design is not in proper way


![26](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/8a0c2370-b9f1-4d56-a791-fc5781d301de)




![25](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/5167cb0b-9ad9-42c8-9a31-081c4dacb794)



#### transition delay


![27](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/7f6d3884-94e2-430d-8007-a6cc1e968307)



![28](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/aa634a66-ad47-4765-a83d-085c56b1bcb6)



![29](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/b96e44fc-219f-4c6a-b1e3-7888bcdb3c8f)

</details>

# Day-3 Design library cell using Magic Layout and ngspice characterization

</details>
<details>
<summary>Labs for CMOS inverter ngspice simulations</summary>

### IO placer revision

to cahnge the io pin configuration :


![Screenshot from 2023-09-18 05-51-12](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/30493a87-5f2c-43e4-9a6d-196620ef10be)

![Screenshot from 2023-09-18 05-54-11](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/bb01be30-8c2c-42eb-9fbd-b789bd5512a1)



### Spice deck creation for CMOS inverter

**SPICE deck**

-it contains connectivity information about netlist,inputs to the stimulation,tap points and outputs

![30](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/68a04d74-d01b-4ec3-a6cf-339f3087a47c)



![31](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/071b3a78-14a5-4ef4-8348-8fb71dea6a92)

![33](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/b1a4dd97-835d-45d5-b6e0-e5fa664d82c8)


- Cload ,connected between output and 0,the value of cload is 10f

- supply voltage connected between 0 and 2.5

- input voltage connected 0 and 2.5

 **simulation command**
- .op

-.dc vin 0 2.5 0.05


complete description of NMOS and PMOS:   .LIB "tsmc_025um_model.mod" CMOS+MODELS

-  .end

### switching threshold Vm
**SPICE waveform**

![34](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/08fb9eda-c8e9-4619-b5b1-8cecdc35ae60)



- PMOS is bigger in size than NMOS

- shapes of wavefoems are same

- switching threshold ,Vin = Vout

- we can observe in to above waveform at the intersection both NMOS and PMOS are insaturation region,where in there are high chances of leakage


![35](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/8d0dc63b-1980-40a8-a3ad-6de69ed3ee7f)


### static and dynamic simulation of CMOS inverter



![36](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/87e925ab-89e7-4a1f-8eb4-d47d8207475b)

### Lab steps to git clone vsdstdcelldesign

- git cloning the repo of **https://github.com/nickson-jose/vsdstdcelldesign.git**




magic -T sky130A.tech sky130_inv.mag &



</details>
<details>
<summary>Inception of Layout CMOS fabrication</summary>

### create Active regions


**16 mask CMOS process**


1)selecting a substrate: Ptype silicon substarte (high resistivity (5~50 ohms),doping level(10^15 cm^-3),orientation 100)


- doping level mained low than well doping



2) creating active region for transistors:

-silicon di oxide(~40nm sio2)


-depoist layer silicon nitride(~80nm si3n4)


- depoist photoresist(1um )

![37](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/24c09664-156e-495d-8d4d-f0e5bc66a515)

  

-  next up on the photoresist material apply mask 1

where ever ther is mask the uv light will not reach 

the area which area protected by the mask will be washed out

![44](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/baa40c4e-d817-43aa-a979-47bd4d45b5a9)

![38](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/9fbb5c4a-ed7e-4af5-bfb1-aaabc8e076c3)

- removal of mask
![39](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/1c5413c6-bd05-4086-9f41-d44d96b58296)

- si3n4 etched
![40](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/60102e53-931b-41eb-966c-c7be90d3fe21)

- removal of photoresistor because the si3n4 acts as protection layer
![41](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/981b4a45-f341-47ec-b218-707f2b6ae40a)

- furnace
![42](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/dbd15f87-75df-427f-a244-5135d89b80a3)

- Local oxodation of silicon called **locos**
![43](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/f34e0e56-dc8d-47ce-ac55-0d6a5aea1c19)

- si3N4 etched by hot phosphoric acid


![45](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/ab03bdf9-76e0-4956-8c90-26a1de6f4e13)


3)Formation of nwell and pwell

- for p well use boron material
![46](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/c3b087f3-2570-402c-b288-d99763f63d08)

- for nwell use phosphorous material


![47](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/138e8f82-c524-48d7-8f8b-b41675d48558)



![48](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/48619e6d-1475-4948-a813-1a16835f542d)


4)Formation of Gate: photolithography

5)Lightly Doped Drain Formation(LDD):

6)Source and Drain Formation

7)Steps to form Contacts and Interconnects(local)
 
 tiN etched off by ussing RCA cleaning :


 - deionized water

 - Ammonium hydroxide (NH4oH)

 - Hydrogen peroxide (H2o2)

8) Higher Level Metal Formation



### lab introduction to Sky130 basic layers layout and LEFusing inverter



to check the error in the layout

- drc--->drc find error

- in tkcon.tcl it shows the error

- 
![Screenshot from 2023-09-18 12-10-23](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/336d65eb-acfc-4ad6-8974-09c5c453d59a)


  to access the spice netlist(in tkcon.tcl):
  

  
![Screenshot from 2023-09-18 12-17-14](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/65561f72-29b2-485a-8810-caa831f2ea2d)

to copy the parasitic capacitance we do **ext2spice cthresh 0 rthresh 0**


We can observe sky130_inv.ext file is created


</details>

<details>
<summary> Sky130 Tech File Labs</summary>

### Lab Steps to create final SPICE deck using sky130 tech

press g for grid

![Screenshot from 2023-09-18 13-52-43](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/0eda826e-8686-48e1-b49f-7e309ecef8c5)


to acess the spice file 

 - gedit sky130_inv.spice

![Screenshot from 2023-09-18 13-55-00](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/b8b4936f-2f35-41ad-8279-0b141d442fee)



### Lab Steps to characterize  inverter using sky130 model files

ngspice sky130_inv.spice : to access the ngspice file



![Screenshot from 2023-09-18 14-06-11](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/61142445-036d-440f-bd1b-dcca20760c4f)


for plotting: plot y vs time a

![Screenshot from 2023-09-18 14-12-31](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/648d1d8e-2a20-4221-991f-d74a901df5f5)


![Screenshot from 2023-09-18 14-18-05](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/aab7dded-909b-46aa-b372-d01c61cc90dc)


Rise Time: time taken to rise from 20% to 80% of the max value -> 2.25075e-09 - 2.184e-09 = 0.006675e-09 s.

![Screenshot from 2023-09-18 14-20-18](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/cba3ce25-53c5-44c5-a44a-8d752190879d)



### Sky130 PDKS and Steps to Download Magic Tool

-  wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz


-mv drc_tests.tgz Desktop/   (move te file to Desktop)

-tar xfz drc_tests.tgz 

- magic -d XR

now go to the files open met3.mag


![Screenshot from 2023-09-18 14-29-20](https://github.com/vishnupriyapesu/pes_pd/assets/142419649/34b3d15b-d1a8-40f6-9a4e-fdabfb7dbbac)

</details>

# DAY 4 : Pre-Layout timing analysis and importance of good clock tree
<details>
<summary>DAY 4 : Pre-Layout timing analysis and importance of good clock tree</summary>
<br>

## Extraction of LEF 

Place and routing (PnR) is performed using an abstract view of the GDS files generated by Magic. The abstract information will include metal and pin information. The PnR tool will use the abstract view information, formally defined as LEF information, to perform interconnect routing in conjunction to routing guides generated from the PnR flow.

- Technology LEF - Contains layer information, via information, and restricted DRC rules
- Cell LEF - Abstract information of standard cells

From PnR POV, We have to follow certain guidelines to get standard cell set
1. Input and output ports must lie on the intersection of vertical and horizontal tracks
2. Width of the standard cell should be odd multiples of the track pitch and height should be odd multiple of vertical track pitch


Track info can be found at :

``` ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130fd_sc_hd/tracks.info```

![image](https://github.com/Lo-kesh4/PES_PD_OpenLane/assets/131575546/0dc00df1-ec8c-4796-ba3b-ecc0a3873fef)


- 1st value indicates the offset and 2nd value indicates the pitch along provided direction

### Setting grid values using above file info

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/b92d1c29-7d6a-4180-8754-25d768ce45f2)

Layout before setting grid info vs after setting grid info

<img width="333" height="420" alt="image" src="https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/e85123af-bc48-4150-9694-cf105a99493c">
<img width="333" height="420" alt="image" src="https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/1ad46a25-95e6-4fe6-836c-0b1e34d6eef5">
<img width="333" height="420" alt="image" src="https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/d0a2753b-7216-43c9-ad9a-992feffcaa40">

- From the above pic, its confirmed that the pins A and Y are at the intersection of X and Y tracks. So the first condition is met.
- The PR boundary is taking 3 grids on width and 9 grids on height which says that the 2nd condition is also met

## LEF Generation

Since the layout is perfect, we can generate the lef file

#### 1. save the modified layout (with new grid)
   - In console, type ```save sky130_vsdinv.mag```
   - This saves the modified layout in current working directory

#### 2. Open the file and extract LEF
   - Open using ``` magic -T sky130A.tch sky130_vsdinv.mag```
   - in the console opened, type ```lef write``` and a lef file will be generated

![image](https://github.com/Lo-kesh4/PES_PD_OpenLane/assets/131575546/7b9f664d-a6ec-41f2-a5f5-d4b8c8e70a85)

#### 3. Plug the generated lef file into PICORV32a

To do this, we need the lef file, library file that has cells

Change config file so that these libraries and lef file is used

![image](https://github.com/Lo-kesh4/PES_PD_OpenLane/assets/131575546/3485c9c3-bcf8-4a6e-ab54-16668bb19ad2)

#### 4. Make sure the lef file is added

add the below 2 lines in the initial stage of interactive flow and ```run_synthesis```  to see if our inverter has been used and find timing violations if any.

![2lines](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/1c964f50-cefe-426f-9104-4562a1aab570)

![image](https://github.com/Lo-kesh4/PES_PD_OpenLane/assets/131575546/d8cbc0fe-127e-4d3b-a05c-49e07b5bbe2b)

The above figure shows that our vsdinv cell has been used in synthesis process

![Screenshot from 2023-09-14 15-57-05](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/f18b35db-10d4-4f47-b3b7-8a3ef657d57f)

since there is slack, we have to reduce it

VLSI engineers will obtain system specifications in the architecture design phase. These specifications will determine a required frequency of operation. To analyze a circuit's timing performance designers will use static timing analysis tools (STA). When referring to pre clock tree synthesis STA analysis we are mainly concerned with setup timing in regards to a launch clock. STA will report problems such as worst negative slack (WNS) and total negative slack (TNS). These refer to the worst path delay and total path delay in regards to our setup timing restraint. Fixing slack violations can be debugged through performing STA analysis with OpenSTA, which is integrated in the OpenLANE tool. To describe these constraints to tools such as In order to ensure correct operation of these tools two steps must be taken:

- Design configuration files (.conf) - Tool configuration files for the specified design
- Design Synopsys design constraint (.sdc) files - Industry standard constraints file

For the design to be complete, the worst negative slack needs to be above or equal to 0. If the slack is outside of this range we can do one of multiple things:

1. Review our synthesis strategy in OpenLANE
    - Enalbed CELL_SIZING
    - Enabled SYNTH_STRATEGY with parameter as "DELAY 1"
    - The synthesis result is :
  
    ![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/b4a26ed1-6ac8-449c-bc6e-31ed04470c4e)

    The slack has reduced a lot but still didnt meet the requirement. The sdc file used is [my_base.sdc](https://github.com/yagnavivek/PES_OpenLane_PD/blob/main/my_base.sdc) defined in [pre_sta.conf](https://github.com/yagnavivek/PES_OpenLane_PD/blob/main/pre_sta.conf) using the command ```sta pre_sta.conf```

   ![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/f7356fd8-9c7c-4d99-88d6-67ceadfa774f)

    The delay is high when the fanout is high. Therefore we can re-run synthesis by changing the value of ```SYNTH_MAX_FANOUT``` variable
    
2. Enable cell buffering 
3. Perform manual cell replacement on our WNS path with the OpenSTA tool

    - We can see which net is driving most outputs and replace the driver cell with larger form of its own kind

    [image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/f4e05f1d-0c2c-404a-8b43-6b82a097d73d)

4. Optimize the fanout value with OpenLANE tool

Since we have synthesised the core using our vsdinv cell too and as it got successfully synthesized, it should be visible in layout after ```run_placement``` stage which is followed after ```run_floorplan``` stage

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/8893a21d-26c6-4b36-bbc4-a2b9c1637cfb)

## Clock Tree Synthesis

- After all the above steps of fixing slack violations, as we have ```run_synthesis``` in openlane, it would have generated a mapped.v file in synthesis results but we have fixed all the violations using ```pre_sta.conf```. Therefore we write this netlist using ```write_verilog``` and replace the openlane generated mapped file ie., ```picorv32a.synthesis.v```

- now in the openlane flow, continue with ```run_flooorplan``` ```run_placement``` ```run_cts```

- To ensure that the cts step has added buffers and modified the netlist
    
## Post CTS- STA Analysis

OpenLANE has the OpenROAD application integrated into its flow. The OpenROAD application has OpenSTA integrated into its flow. Therefore, we can perform STA analysis from within OpenLANE by invoking OpenROAD.

In OpenROAD the timing analysis is done by creating a .db database file. This database file is created from the post-cts LEF and DEF files. To generate the .db files within OpenROAD:
- Invoke OpenRoad
- Read lef file from tmp folder of runs
- Read def file from results of cts
- write db file
- Read the generated db file
- Read the cts generated verilog file
- read min and max liberty file
- set the clocks
- generate the reports

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/74edcca7-9519-4269-a2b9-2fafdeef4e66)
![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/02cf90b0-d02b-411d-847b-be6159e74502)
![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/a5c62171-3c46-482d-8ad5-d7700774d1ec)

The results wont meet the timing because we are using min and max lib files and openroad doesnot support multi corner optimisation. Therefore we do it using only typical corner lib

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/e3687d97-556d-4b81-8261-0c78aba74d13)

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/843fce06-f1d1-4469-92d4-b9b1b4a82b91)

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/928a49af-78b3-4e0e-a8b2-5c2bf7589f20)

We have to ensure that the skew is withing 10% of clock period ie., should be less than 1.6 in my case

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/dbd809aa-dcda-43a1-97da-9f0ab81fbf08)

[BACK TO TOP](https://github.com/yagnavivek/PES_OpenLane_PD#to-enter-the-automated-flow-use-these-commands)

</details>

# DAY 5 : Final steps for RTL2GDSII

<details>
<summary>DAY 5 : Final steps for RTL2GDSII</summary>
<br>

## Power Distribution Network

After generating our clock tree network and verifying post routing STA checks we are ready to generate the power distribution network ```gen_pdn``` in OpenLANE:

The PDN feature within OpenLANE will create:

- Power ring global to the entire core
- Power halo local to any preplaced cells
- Power straps to bring power into the center of the chip
- Power rails for the standard cells

![image](https://github.com/yagnavivek/PES_OpenLane_PD/assets/93475824/b4fd0fda-f775-4b33-9aa8-c9a252ff19ab)

Note: The pitch of the metal 1 power rails defines the height of the standard cells

## Global and Detailed Routing

OpenLANE uses TritonRoute as the routing engine ```run_routing``` for physical implementations of designs. Routing consists of two stages:

- Global Routing - Routing guides are generated for interconnects on our netlist defining what layers, and where on the chip each of the nets will be reputed
- Detailed Routing - Metal traces are iteratively laid across the routing guides to physically implement the routing guides

If DRC errors persist after routing the user has two options:

- Re-run routing with higher QoR settings
- Manually fix DRC errors specific in tritonRoute.drc file

## SPEF Extraction

After routing has been completed interconnect parasitics can be extracted to perform sign-off post-route STA analysis. The parasitics are extracted into a SPEF file. The SPEF extractor is not included within OpenLANE as of now.

```
cd ~/Desktop/work/tools/SPEFEXTRACTOR
python3 main.py <path to merged.lef in tmp> <path to def in routing>
```

The SPEF File will be generated in the location where def file is present



</details>
