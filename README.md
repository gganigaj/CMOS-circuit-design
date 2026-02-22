# CMOS circuit design and SPICE simulations using sky130
## **VirtualBox installation process**  
explains how to open the provided CMOS VDI file using Oracle VirtualBox.
### 1. Install VirtualBox
Download and install Oracle VirtualBox: https://www.virtualbox.org/wiki/Downloads
### 2. Create Virtual Machine
- Open VirtualBox<br>
- Click New<br>
- Set us<br>
Type : Linux<br>
Version	: Ubuntu 18.04 Bionic Beaver (64-bit)
- Click Next
### 3. Allocate Memory
- Assign RAM as required (Recommended: 4096 MB)
- Click Next
### 4. Attach CMOS VDI File
- Select Use an existing virtual hard disk file
- Click the folder icon
- Browse to the unzipped CMOS VDI file
- Click Open
- Click Next
- Click Finish<br>
### 5. Start the virtual mode
- select the created VM
- click start
## NgspiceSky130-Day 1-Basics of NMOS Drain current(Id) vs Drain-to-source voltage(Vds)<br>
### **Introduction to Circuit Design and SPICE simulation**
### 0-L1 Why do we need SPICE simulations?<br>
   About circuit,let as cosider an inverter which has PMOS and NMOS.the drain of both are tigh together and the voltage is connected to both NMOS AND PMOS.<br>
 <div align="center">
   <img width="220" height="241" alt="image" src="https://github.com/user-attachments/assets/1bac8540-e2d7-4607-9623-d16754ad19ab" />
    <div align="center">
    dia:1 Circuit Design
 </div>
    </div>
The connection of PMOS and NMOS transistor will gives as the output of AND,OR,NAND gate.circuit design from the above figure will have simulation waveform to identify the output character.<br>
  <div align="center">
  <img width="601" height="259" alt="image" src="https://github.com/user-attachments/assets/c849b3b9-e93b-4b11-91f7-03d84db19c8e" />
   <div align="center">
      dia:2 Characteristic Waveform
  </div>
   </div>
  From the above characteristic simulation  shows the NMOS and PMOS waveform which will discribe the both transistor characteristics.<br>
  
   <div align="center">
   <img width="456" height="365" alt="Screenshot 2026-02-18 102130" src="https://github.com/user-attachments/assets/5903fbe9-9200-47b3-84d7-8a8adc65c3cc" />
      <div align="center">
    dia:3 SPICE simulation
  </div> 
      </div> 
 The characteristic waveform are simulated by using SPICE.This waveform decide the delay of the waveform.based on the value of delay we can tune the width of the transistor,the width and length of the ratio will decide the value of current.<br>
 SPICE helps analyze clock delay and signal integrity check crosstalk analysis the will very much needed.<br>
  <div align="center">
 <img width="1163" height="449" alt="Screenshot 2026-02-18 104332" src="https://github.com/user-attachments/assets/a8b98558-bd06-4e98-88cd-4b2b1262e500" />
     <div align="center">
 dia:3 Example of buffer
   </div> 
     </div> 
  The above diagram is the example of SPICE.Here we are taking two buffer level and the each tree node is measured as femtofarads,which was mention in the above dia:3.We already have delay table so don't want to run SPICE AT everytime.<br>
  <div align="center">
   <img width="586" height="321" alt="Screenshot 2026-02-18 105829" src="https://github.com/user-attachments/assets/ba4e64aa-a2ca-4ce2-b955-cfe2f139b5a1" />
   <div align="center">
   dia:4 Delay table
   </div> 
   </div> 
  In that delay table the value of input and output will interset then that will consider as the delay time. The import note the each PMOS and NMOS transistor may have differnt shades from the nearby transistor.<br>
  The delays are actually comes from the SPICE simulations. The delay models are accurate by having the same input and output load which is matching in the SPICE simulation we get the delay values.<br>
 
  ###  1-L2 Introduction to basic element in Circuit design-NMOS <br>
The NMOS is a four terminal device, which consist of P-substrate. if it is PMOS then it will have an N-substrate.
     <div align="center">
     <img width="559" height="489" alt="Screenshot 2026-02-18 114450" src="https://github.com/user-attachments/assets/a6f35d2a-c338-499c-bf3d-916148da5c9e" />
     <div align="center">
     dia:5 structure of NMOS devic 
     </div>
       </div><br>
       The p-substrate has an two isolation region which are used to differentiate between two transistor behaviour. It has an n+ diffusion region, which are called as source and drain terminal. The gate oxide is placed over the p-substrate. The poly-si or metal gate is placed on tha gate oxide layer.<br>
       
 #### Threshold voltage <br>
  The minimum gate to source voltage (VGS) needed to create a conductive channel between the drain and source. <br>
<div align="center">
 <img width="245" height="182" alt="image" src="https://github.com/user-attachments/assets/c6c31b23-6fd5-4c62-9d0a-1b63bb4084d1" />
 <div align="center">
  dia:6 Vgs=0
  </div>
   </div><br>
     if Vgs=0 and the drain,source,bulk are connected to the ground.The substrate-source and substrate-drain will form p-n junction diode.now both the junctions are in off mode so, source-drain resistance is high.<br>
 <div align="center">
  <img width="244" height="195" alt="image" src="https://github.com/user-attachments/assets/a188174f-d286-44f7-a274-1e260c20010f" />
   <div align="center">
   dia:7 Vgs>0
   </div>
 </div> <br>
    When we are apply small voltage to the gate,it will repell all the positive charge which is present over the substrate.mobile holes are repelled by the +ve charge at 'G' and they leave behind the -ve charges.The -ve charge will start to accumulate.<br>

### 2-L3 Strong inversion and threshold voltage <br> 
   In the pn-junction whenever we are applying reverse bias on the voltage, depletion region will occur. <br>
   Increasing the gate voltage level,depletion region width is also increase.so that small region in tha p-substrate is converted into n-substrate this phenomenon is called as strong inversion. <br>
The Vgs voltage at which strong inversion occurs is called threshold voltage(Vt).
 <div align="center">
<img width="251" height="202" alt="image" src="https://github.com/user-attachments/assets/ba3f74c6-ec46-46af-88d2-1ad7d8d5ef07" />
 <div align="center">
dia:8 strong inversion
 </div>
  </div><br>   
    When the Vgs is further increases, the channel width get increases but there is no change in depletion layer width.The electrons from heavily doped n+ source region are drawn in region under gate.<br>
    The continuous n-channel formation from source to drain,whose conductivity is modulated by Vgs.<br>
  <div align="center">
   <img width="566" height="222" alt="Screenshot 2026-02-18 144543" src="https://github.com/user-attachments/assets/8c9429be-ac3f-4c64-82f3-c8427b3fba5a" />
    <div align="center">
    dia:9 Vsb=0 and Vsb=+ve
     </div>
      </div><br>
   The above diagram shows that the Vsb=0 and Vsb=+ve value.The +ve Vsb will have the high depletion width compare to the Vsb=0.Because there is a additional reverse bias that is applied to the +Vsb the n-type area is connected to the positive source and p-substrate is connected to the negative souce.<br>

### 3-L4 Threshold voltage with positive substrate potential <br>
 On the application of gate voltage to the Vsb=0 and Vsb=+ve.while in Vsb=+ve the depletion region increases the accumulation of negative charge in source is increases. <br>
    Due to +ve Vsb,few charges from channel are pulled towards source and there is no surface inversion will happen at +ve Vsb. while in Vsb=0 the semiconductor surface inverts to n-type material at voltage Vgs=Vto. <br>
    <div align="center">
    <img width="556" height="232" alt="image" src="https://github.com/user-attachments/assets/b64359ca-a2ce-4791-a924-4afb871dafc1" />
      <div align="center">
      dia:10 surface inversion 
       </div>
        </div>
    To make the surface inversion in Vsb +ve the semiconductor surface inverts to n-type material at voltage Vgs=Vto+v1.In the presence of substrate bias 'Vsb',additional potential is required for strong inversion.</br>    
![WhatsApp Image 2026-02-18 at 3 21 11 PM](https://github.com/user-attachments/assets/c50135ce-2c1a-4948-86e6-193d0548e64a)<br>
- Vto is the threshold voltage at Vsb=0
- γ is the body effect coefficient, which indicates how strongly the threshold voltage changes with body bias. It depends on substrate doping and oxide capacitance.<BR>
<img width="299" height="136" alt="image" src="https://github.com/user-attachments/assets/fad87888-91c0-4eed-8065-04cd1ad1cf43" /><br>
- φF is the Fermi potential of the substrate, representing the energy difference between the intrinsic level and the Fermi level in the semiconductor.<br>
  <img width="312" height="68" alt="image" src="https://github.com/user-attachments/assets/aa9add35-0e7e-4de9-8245-40ab6bde1dad" /><br>
- These values are obtained from the foundry and fed into the SPICE model for device modelling and simulation.<br>

## NMOS resistive region and saturation region of operation<br>
### 4-L1 Resistive region of operation with small drain-source voltage<br>
  when the Vgs>Vt ,the channel width will increases more and it shows the induced charges(Qi) is proportional to the (Vgs-Vt).This excess voltage, known as the overdrive voltage, creates additional mobile electrons in the channel, increasing the drain current.<br>
   <div align="center">
  <img width="347" height="236" alt="image" src="https://github.com/user-attachments/assets/8e478cc9-8522-45e7-8697-5cc33e3bf689" />
   <div align="center">
   dia:11 Induced charges
    </div>
   </div>
   Let  Vgs=1V , small Vds(0.05V) and Vt(NMOS)=0.45V.<br>
   Since VGS > Vt, the transistor is ON and a conducting inversion channel is formed between source and drain.Because the source is grounded and the drain is at a positive voltage, a voltage gradient develops along the channel from source to drain.<br>
If we plot a graph with the x-axis as the channel length (from 0 to L, considering L ≈ Leff) and the y-axis representing channel charge/strength:<br>
        In the absence of VDS, every point along the channel sees the same gate overdrive voltage (VGS − Vt).<br>
        When VDS is applied, the local channel potential becomes V(x), which varies from 0 at the source to VDS at the drain.<br>
        Therefore, the effective overdrive at any point x becomes (VGS − V(x) − Vt), meaning the channel charge gradually decreases from source to drain.
        <div align="center">
        <img width="334" height="237" alt="image" src="https://github.com/user-attachments/assets/0ead9e30-68d9-41c6-b59a-5a38b5402866" />
          <div align="center">
           dia:12 
          </div>
 </div>
channel length(L):The physical distance between the source and drain defined during fabrication (layout dimension).<br>
 Effective Channel Length (Leff) :The actual conductive channel length after accounting for lateral diffusion and short-channel effects<br>

 ### 5-L2 Drift current theory
 In the channel (yellow region below), the induced inversion charge at any point x depends on the local gate overdrive voltage.Since the channel potential varies along its length, the effective gate voltage at position x is VGS − V(x).Therefore, the inversion charge per unit area at point x is proportional to the local overdrive voltage.<br>
  <div align="center">
 <img width="542" height="377" alt="image" src="https://github.com/user-attachments/assets/eeccb8e7-d51e-4ffc-b070-b26da6d4c8d4" />
    <div align="center">
     dia:13 Vgs-V(x)
   </div>
     </div>
     <img width="191" height="200" alt="image" src="https://github.com/user-attachments/assets/4c4e229a-fdd5-49b6-9803-293a8e045a63" /> <br>
There are two types of current:
- Drift current - Current that flows due to an applied electric field, which causes charge carriers to move in a specific direction.<br>
- Diffusion current - Current that flows due to a concentration gradient, where charge carriers move from a region of higher concentration to a region of lower concentration.<br>
<img width="520" height="297" alt="image" src="https://github.com/user-attachments/assets/2472fe34-2d80-4c54-94bb-312c0deab373" /><br>
Drift current (Id) = Velocity of charge carriers x Available charge (over the channel width)<br>

### 6-L3 Drain current model for linear region of operation
Drift current (Id)=-Vn(x).Qi(x).W<br>
where,<br>
   Velocity Vn(x)= mobility.electric field<br>
   Substituting and integrating dx over channel length L will give the V-I relation of NMOS transistor.<br>
   <img width="205" height="59" alt="image" src="https://github.com/user-attachments/assets/396106a3-1765-4b10-b049-e519495ee4a7" /><br>
   Integrate over length'L' on LHS and over drain-source voltage Vds on RHS,we get the below<br>
   <img width="192" height="60" alt="image" src="https://github.com/user-attachments/assets/e6982f21-0ab4-462f-acd9-fc48799aeb26" /><br>
   Considering kn= unCox, where kn is the process transconductance, which determines how effectively the device converts gate voltage into drain current.<br>
   <img width="153" height="13" alt="image" src="https://github.com/user-attachments/assets/bf75a3ca-57cc-404f-b469-5f6eb327df70" /><br>
Therefore, for all values of VDS ≤ (VGS − Vt), the MOSFET operates in the resistive (linear) region.In this region, the channel is continuous from source to drain, and the device behaves like a voltage-controlled resistor.<br>

### 7-L4 SPICE conclusion to resistive operation<br>
   To study how the gate-to-source voltage (VGS) and drain-to-source voltage (VDS) affect the drain current (ID), we examine several values of both voltages.     For a fixed VGS, the MOSFET operates in the linear (triode) region as long as VDS is less than (VGS − Vt).<br>
   To determine ID for different VGS values, we select one specific VGS and vary VDS from 0 up to (VGS − Vt). Within this range, the drain current is described by the linear-region equation. SPICE simulations can then be performed to generate and confirm the ID–VDS curves corresponding to each chosen VGS.<br>
   <img width="624" height="160" alt="image" src="https://github.com/user-attachments/assets/736002a0-28fd-4709-a2f9-a31958f4fa58" /><br>

   ### 8-L5 Pinch-off region condition
   If (Vgs - Vds) remains greater than (Vt), the gate-to-channel voltage at the drain end is still above the threshold level. As a result, an inversion layer is present even near the drain terminal.<br>
Because inversion charge exists continuously from the source (x = 0) to the drain (x = L), an uninterrupted conductive channel connects the two terminals.<br>
 <div align="center">
  <img width="589" height="303" alt="image" src="https://github.com/user-attachments/assets/64d1d450-52f2-4bb7-b286-f00b3abf5601" />
   <div align="center">
   dia:14 Channel Voltage
  </div>
   </div><br>
    Under these conditions, the MOSFET operates in the linear region. For small values of (Vds), the drain current varies approximately linearly with (Vds).<br>
    When (Vgs-Vds= Vt), the gate-to-channel voltage at the drain end becomes exactly equal to the threshold voltage needed to sustain inversion. At this point, the drain-side surface is just entering inversion and the inversion charge density there reduces to zero.Because the inversion layer vanishes at the drain end, the channel no longer reaches all the way to the drain terminal. This condition is known as pinch-off.<br>
    Even though the channel is pinched off at the drain side, current flow does not cease. Charge carriers that arrive at the pinch-off point are accelerated through the depletion region toward the drain by the strong electric field present there. Consequently, the drain current stops increasing linearly with (Vds).<br>
     <div align="center">
     <img width="593" height="293" alt="image" src="https://github.com/user-attachments/assets/e57f7900-a9f4-4f51-a729-48102de42900" />
       <div align="center">
     dia:15 Pinch_off condition:(VGS − VDS) ≤ Vt
      </div>
      </div><br>
        When ( Vds) becomes greater than (Vgs-Vt), the MOSFET operates in the saturation region. Under this condition, the drain end can no longer maintain inversion, leading to pinch-off close to the drain terminal.<br>
        Because the channel potential varies along its length, it reduces the effective gate-to-channel voltage locally. The effective overdrive voltage at any position (x) in the channel is ( Vgs- V(x)).<br>
        As the channel voltage (V(x)) rises from the source toward the drain, the inversion charge density gradually decreases in that direction.<br>
If (Vds) is increased further beyond (Vgs-Vt), the pinch-off point shifts slightly toward the source end of the channel.<br>

### 9-L6 Drain current model for saturation region of operation <br>
   When the condition (VGS − VDS) ≤ Vt is met the inversion layer vanishes near the drain terminal.<br>
   In the saturation region, the channel potential is roughly fixed at (Vgs-Vt), whereas in the linear (ohmic) region, the channel voltage changes gradually along the channel length as a function of position (V(x)).<br>
   Under ideal saturation conditions (ignoring channel-length modulation), the drain current no longer depends on (Vds). Instead, it is primarily controlled by the overdrive voltage (Vgs-Vt).
The drain current in saturation can therefore be expressed as:<br>
<img width="180" height="59" alt="image" src="https://github.com/user-attachments/assets/ef275299-5ff4-41c9-952e-6e44bd7b2591" /><br>
<img width="223" height="169" alt="image" src="https://github.com/user-attachments/assets/6330c9d7-585a-44cf-9379-ff45016eb6cd" /><br>
   When we reduce the channel length the drain current increases that will occur due to velocity saturation.while looking at the formula the drain current is fuction of all constant but that's not true.<br> 
   The effective conductive channel length is modulated by applied Vds.when we increase the Vds depletion region at drain is also increase and the effective channel length decreases.when we are tuning the Vds the channel length is also tune.<br>
    <img width="172" height="26" alt="image" src="https://github.com/user-attachments/assets/9262ab52-72cd-464b-b39b-dcc96ebf1c4e" /><br>
   <div align="center">
   <img width="235" height="182" alt="image" src="https://github.com/user-attachments/assets/7779a53d-7609-4fbd-842b-a1389bdc6e36" />
    <div align="center">
  dia:16 Drain current in MOSFET
    </div>
     </div>

## Introduction to SPICE
### 10-L1 Basic SPICE setup
The SPICE is basically a software that have an predefined model, We have to feed the value in that source then the SPICE will derive the waveform for that related value.<br>
- Create a correct SPICE setup and feed the model to the SPICE engine. The MOSFET we are using having Vds,Vgs. Using the voltage threshold equation and linear region equation for identify the drain current.<BR>
- When the MOSFET go for the saturation region and the equation of the drain current is shown below.<br>
   <img width="217" height="243" alt="image" src="https://github.com/user-attachments/assets/516b389e-129c-41e3-b187-5a1efb679277" /><br>
- The SPICE model parameters are consider as constant which was highlighted in the above equation. The model parameter are from correct parameter or not want to check to setup the SPICE.<BR>
- The SPICE parameter and SPICE netlist in the SPICE software we get drain current and voltage axis.<br>
<div align="center">
<img width="303" height="246" alt="image" src="https://github.com/user-attachments/assets/b6dd4524-c12a-4a4b-9005-08b5197aeb9d" />
<div align="center">
   dia:17 SPICE setup
  </div>
    </div><br>
- In SPICE netlist, the MOSFET logical symbol of the NMOS in that protection resistor,gate voltage is connected and the substrate and source are connected to the ground.<br>
<div align="center">
<img width="220" height="128" alt="image" src="https://github.com/user-attachments/assets/47da6374-d791-400f-a8f6-de059fbad30c" />
<div align="center">
   dia:18 NMOS diagram
 </div>
  </div>

### 11-L2 Circuit description in SPICE syntax
The SPICE also have some synthetical way to stimulate the Spice netlist. For that the first strp is to define the node.<br>
- Give some values to the component Vin=2.5V, R1=55ohms, M1=1.8u/1.2u, Vdd=2.5V and we have to put this by the way to understand the SPICE engine to create nodes.<br>
- While coming to define the node there is no obstruction between the wire connected within two component.
  <div align="center">
     <img width="275" height="188" alt="image" src="https://github.com/user-attachments/assets/5db139ab-4cda-406b-b45c-9644b7584ba7" />
<div align="center">
   dia:19 Nodes
 </div>
  </div><br>
MOSFET lies between four different nodes drain,source,gate and substrate.<br>
where,<br>
 M1  = MOSFET<br>
 Vdd = drain voltage<br>
 n1  = gate<br>
 width = 1.8u<br>
 length = 1.2u<br>
 R1 in n1 55<br>
 Vdd 0 to 2.5<br>

 ### 12-L3 Define technology parameters<br>
- In this lecture is about model of NMOS SPICE. For this model we need some parameters like constant value, Which we done in previous chapter.The model code what we mention is as same as SPICE netlist.The attribute name is <br>
- In netlist,<br>
M1 Vdd n1 0 0 nmos W=1.8u L=1,2u<br>
R1 in n1 55<br>
Vdd Vdd 0 2.5<br>
Vin in 0 2.5<br>
- In model,<br>
.MODEL nmos NMOS (TOX = ..+ VTHO = .. U0 = .. GAMMA1 = ..)<br>
As model for pmos,<br>
.MODEL pmos PMOS (TOX = ..+ VTHO = .. U0 = .. GAMMA1 = ..)<br>
- The above list is huge so create one library cmos model and name the model file. Herethe file stores like model.mod to be in a package line file.
 <div align="center">
 <img width="314" height="312" alt="Screenshot 2026-02-22 101331" src="https://github.com/user-attachments/assets/c685fd80-2ed5-42f7-9dd7-50ee1bbea811" />
<div align="center">
   dia:18 Simulation commands
  </div>
    </div><br>
- The first list is consider as "netlist discription" and next list as ".include xxxx_lum_model.mod". The simulation command is based on the way of voltage what we given.<br>
- Here the voltage is 2.5, we need to sweep the voltage 0 to 2.5v.

### 13-L4 First SPICE simulation and 14_L5 SPICE Lab with sky130 models<br>
The discribtion of the netlist is well understand by the SPICE. The next step is to give the model for the nmos. For the nmos we have the constant values of Vth,Id(linear and saturation region). and the model parameter which already define in previous lecture.The similar way is used for pmos.
   <div align="center">
  <img width="545" height="372" alt="Screenshot 2026-02-22 124422" src="https://github.com/user-attachments/assets/e2e8804d-317b-4ced-a665-0353a7f29d1d" />

<div align="center">
   dia:19 Simulation code
  </div>
    </div><br>
     <div align="center">
        <img width="551" height="415" alt="Screenshot 2026-02-22 124534" src="https://github.com/user-attachments/assets/164c9118-a823-45d2-a4cd-25d0a1bb8235" />
<div align="center">
   dia:20 Simulation diagram
  </div>
    </div><br>

## NgspiceSky130-Day 2-Velocity saturation and basics of CMOS inverter VTC<BR>
### ***SPICE simulation for lower nodes and velocity saturation effect***<br>
### 15-L1 SPICE simulation for lower nodes<br>
Let us see the SPICE waveform of W=1.8u, L=1.2u device(W/L=1.5)<br>
- In the below diagram we have drain current(Id) on y-axis and drain to souce voltage(Vds) on the x-axis.
- We can see the zero drain current on the x-axis. Where the minimum channel available for the drain current to flow. (when Vgs=0.5v)<br> 
   <img width="326" height="240" alt="image" src="https://github.com/user-attachments/assets/f743e8e7-d0bc-4a6e-b424-406114bbb11e" />
   <img width="346" height="274" alt="image" src="https://github.com/user-attachments/assets/181bda61-23b4-4548-8870-341b9e647db6" />   
<div align="center">
   dia:20 waveform
  </div><br>
  The above diagram show the linear and saturation region (Vds=Vgs-Vt). When the W/L is constant the drain current is same.<br>
  - let us take differt situation ,SPICE waveform: W=0.375u, L=0.25u device (W/L=1.5)
    


 


   
















   
                 
       
     

 


     
 

  
  

     

