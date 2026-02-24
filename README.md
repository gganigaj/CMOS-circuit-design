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
- When (Vgs-Vds= Vt), the gate-to-channel voltage at the drain end becomes exactly equal to the threshold voltage needed to sustain inversion. At this point, the drain-side surface is just entering inversion and the inversion charge density there reduces to zero.Because the inversion layer vanishes at the drain end, the channel no longer reaches all the way to the drain terminal. This condition is known as pinch-off.<br>
- Even though the channel is pinched off at the drain side, current flow does not cease. Charge carriers that arrive at the pinch-off point are accelerated through the depletion region toward the drain by the strong electric field present there. Consequently, the drain current stops increasing linearly with (Vds).<br>
     <div align="center">
     <img width="593" height="293" alt="image" src="https://github.com/user-attachments/assets/e57f7900-a9f4-4f51-a729-48102de42900" />
       <div align="center">
     dia:15 Pinch_off condition:(VGS − VDS) ≤ Vt
      </div>
      </div><br>
        When ( Vds) becomes greater than (Vgs-Vt), the MOSFET operates in the saturation region. Under this condition, the drain end can no longer maintain inversion, leading to pinch-off close to the drain terminal.<br>
- Because the channel potential varies along its length, it reduces the effective gate-to-channel voltage locally. The effective overdrive voltage at any position (x) in the channel is ( Vgs- V(x)).<br>
-  As the channel voltage (V(x)) rises from the source toward the drain, the inversion charge density gradually decreases in that direction.<br>
If (Vds) is increased further beyond (Vgs-Vt), the pinch-off point shifts slightly toward the source end of the channel.<br>

### 9-L6 Drain current model for saturation region of operation <br>
   When the condition (VGS − VDS) ≤ Vt is met the inversion layer vanishes near the drain terminal.<br>
- In the saturation region, the channel potential is roughly fixed at (Vgs-Vt), whereas in the linear (ohmic) region, the channel voltage changes gradually along the channel length as a function of position (V(x)).<br>
- Under ideal saturation conditions (ignoring channel-length modulation), the drain current no longer depends on (Vds). Instead, it is primarily controlled by the overdrive voltage (Vgs-Vt).
The drain current in saturation can therefore be expressed as:<br>
<img width="180" height="59" alt="image" src="https://github.com/user-attachments/assets/ef275299-5ff4-41c9-952e-6e44bd7b2591" /><br>
<img width="223" height="169" alt="image" src="https://github.com/user-attachments/assets/6330c9d7-585a-44cf-9379-ff45016eb6cd" /><br>
- When we reduce the channel length the drain current increases that will occur due to velocity saturation.while looking at the formula the drain current is fuction of all constant but that's not true.<br> 
- The effective conductive channel length is modulated by applied Vds.when we increase the Vds depletion region at drain is also increase and the effective channel length decreases.when we are tuning the Vds the channel length is also tune.<br>
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
    </div>
The first list is consider as "netlist discription" and next list as ".include xxxx_lum_model.mod". The simulation command is based on the way of voltage what we given.<br>
- Here the voltage is 2.5, we need to sweep the voltage 0 to 2.5v.

### 13-L4 First SPICE simulation and 14_L5 SPICE Lab with sky130 models<br>
The discribtion of the netlist is well understand by the SPICE. The next step is to give the model for the nmos. For the nmos we have the constant values of Vth,Id(linear and saturation region). and the model parameter which already define in previous lecture.The similar way is used for pmos.
   <div align="center">
 <img width="953" height="525" alt="Screenshot 2026-02-23 075557" src="https://github.com/user-attachments/assets/23ea6e21-8aa2-472d-8052-9e10eba3f7ad" />
<div align="center">
   dia:19 Simulation code
  </div>
    </div><br>
     <div align="center">
        <img width="913" height="542" alt="Screenshot 2026-02-23 075617" src="https://github.com/user-attachments/assets/14c2b035-8f81-4527-b827-317e1bb02634" />

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
  </div>
The above diagram show the linear and saturation region (Vds=Vgs-Vt). When the W/L is constant the drain current is same.
let us take differt situation ,SPICE waveform: W=0.375u, L=0.25u device (W/L=1.5)

### 16-L2 Drain current vs gate voltage for long and short channel device
In this lecture the observation of  W=1.8u, L=1.2u device and W=0.375u, L=0.25u device. 
<div align="center">
<img width="623" height="265" alt="Screenshot 2026-02-22 183627" src="https://github.com/user-attachments/assets/6dc5dee6-5418-44be-95ac-f603c87e278d" />
<div align="center">
   dia:21 observation from waveform
  </div>
</div><br>
From the above diagram we can see that, The drain current at each and every gate voltage at this shows the quadratic dependence.From the saturation region of drain current will prove that it is quadratic region. <br>

### Comparison Between Long-Channel and Short-Channel MOSFET Behavior

| Effect                     | Long Device (W=1.8µm, L=1.2µm)                              | Short Device (W=0.375µm, L=0.25µm)                                  |
|----------------------------|--------------------------------------------------------------|-----------------------------------------------------------------------|
| Id–Vgs Behavior            | More quadratic; closely follows square-law model            | Deviation from square-law due to velocity saturation                 |
| Saturation Region Shape    | Strong and well-defined saturation                          | Softer saturation; gradual transition                                |
| Output Resistance (ro)     | High output resistance; flatter saturation curve            | Lower output resistance; noticeable slope in saturation              |
| Id–Vds Slope in Saturation | Nearly flat (ideal quadratic behavior)                      | Sloped due to channel length modulation                              |
| Overall Device Behavior    | Approximates ideal long-channel square-law MOSFET          | Exhibits short-channel effects; quasi-linear characteristics         |<br>
<img width="689" height="541" alt="Screenshot 2026-02-23 092147" src="https://github.com/user-attachments/assets/395e7840-012c-48c7-813b-637b915dd958" />
<img width="682" height="536" alt="Screenshot 2026-02-23 092558" src="https://github.com/user-attachments/assets/245b2170-3d38-4634-9525-271ae9900d20" />
<img width="642" height="620" alt="Screenshot 2026-02-23 094636" src="https://github.com/user-attachments/assets/463885a5-f387-4b3c-9d8c-ad468eb49bb1" />
<img width="639" height="620" alt="Screenshot 2026-02-23 094731" src="https://github.com/user-attachments/assets/37237736-bee0-434e-8b32-e9e5ccfb0f8a" />
<div align="center">
   dia:22 simulation waveform
  </div>
</div><br>

### 17-L3 Velocity saturation at lower and higher electric fields
<div align="center">
<img width="627" height="294" alt="Screenshot 2026-02-23 095145" src="https://github.com/user-attachments/assets/25021a6a-7368-4a9a-8580-3b90afb3a3a3" />
<div align="center">
   dia:23 simulation waveform
  </div>
</div>

### velocity saturation effect
velocity Vn(x)=mobility.electric field<br>
At higher fields, velocity becomes constant due to scattering effect.
<img width="227" height="165" alt="Screenshot 2026-02-23 095712" src="https://github.com/user-attachments/assets/44b6693d-5f1d-42dc-af41-a39360308469" />
<div align="center">
   dia:24 velocity saturation
  </div>
</div>There is a boundary over the graph<br> 
<img width="172" height="29" alt="Screenshot 2026-02-23 100033" src="https://github.com/user-attachments/assets/48c06b7a-005f-4b1c-8e43-69c3651c89ec" /><br>
<img width="203" height="39" alt="image" src="https://github.com/user-attachments/assets/0c9e8b96-9e45-4a20-b5e2-190813f12ae0" /><br>
<img width="401" height="102" alt="image" src="https://github.com/user-attachments/assets/10d169c7-006d-4d91-9009-1a04f578c466" /><br>

### Velocity Saturation Effect: Long Channel vs Short Channel MOSFET

| Parameter                  | Long Channel MOSFET (> 250 nm)                | Short Channel MOSFET (< 250 nm)                |
|----------------------------|-----------------------------------------------|-----------------------------------------------|
| Electric Field in Channel  | Relatively low                                | Very high                                     |
| Carrier Velocity           | v_d = μE (linear with electric field)         | Quickly reaches saturation velocity (v_sat)   |
| Velocity Saturation        | Negligible                                    | Significant                                   |
| Drain Current Equation     | I_D ∝ (V_GS − V_T)² (Square-law behavior)    | I_D ∝ (V_GS − V_T) (Linear dependence)        |
| Current Limiting Mechanism | Pinch-off at drain end                        | Velocity saturation near source               |
| Saturation Region Cause    | Channel pinch-off                             | Carriers reach saturation velocity (v_sat)    |
| Transconductance (g_m)     | Higher (strong quadratic dependence)          | Reduced due to velocity saturation             |
| Output Characteristics     | Clear quadratic characteristics               | More linear, reduced gain                     |
| Device Performance         | Predictable classical behavior                | Limited by high-field effects                 |
| Dominant Physical Model    | Long-channel model                            | High-field transport model                    |<br>
<br>
When Id=0 for Vgt<0,cutoff mode and for all other modes,lets use the below model.<br>
<img width="206" height="45" alt="Screenshot 2026-02-23 101411" src="https://github.com/user-attachments/assets/4fbd186b-28b1-4494-87a9-2782a0ba41a1" /><br>

### 18-L4 Velocity saturation drain current model
We know that Vdsat is a technology parameter that we will get from Fab.Substituting Vgs-Vt in the simpler equation. Means Vgt is Minimum and behaves in a saturation regime.When Vds is Minimum, it behaves in a resistive regime.<br>
<img width="291" height="46" alt="Screenshot 2026-02-23 102242" src="https://github.com/user-attachments/assets/571f9cdf-b581-42e4-ab87-42f02ee0b4f8" /><br>
<img width="296" height="32" alt="Screenshot 2026-02-23 102436" src="https://github.com/user-attachments/assets/4408f479-7c9a-4beb-95bd-2eaeec4e2d3e" /><br>
We can have Vdsat minimum for lower nodes devices, so that is only applicable to devices length <250nm.<br>
<img width="556" height="76" alt="Screenshot 2026-02-23 102551" src="https://github.com/user-attachments/assets/bbd46ff8-ccc6-439f-a72b-40f3d4df9a12" />

### 19-L5 Labs Sky130 Id-Vgs
<div align="center">
<img width="394" height="396" alt="Screenshot 2026-02-23 103207" src="https://github.com/user-attachments/assets/90669cd8-ecb1-4230-bf75-dab2e1df94df" />
<div align="center">
   dia:25 velocity saturation simulation (Id vs Vdd)
  </div>
</div><br>
for lower region its showing quadratic behaviour and for higher region it shows linear behaviour. 

 ### 20-L6 Labs Sky130 Vt
 <div align="center">
 <img width="489" height="394" alt="Screenshot 2026-02-23 103830" src="https://github.com/user-attachments/assets/ba140985-8c11-47a6-9de4-1793ee0486bf" />
 <div align="center">
   dia:26 threshold voltage (Id vs Vgs)
  </div>
</div>

### ***CMOS voltage transfer characteristics(VTC)***<br>
### 21- L1 MOSFET as a switch
- A MOSFET used as a switching device operates in two basic modes that are controlled by the gate voltage: the OFF state acting like an open circuit and the ON state acting like a closed circuit.
- For switching applications, the device is intentionally driven either completely ON or completely OFF to control current flow efficiently, rather than operating in the intermediate region where it would function as an amplifier.
<div align="center">
<img width="527" height="331" alt="Screenshot 2026-02-23 104642" src="https://github.com/user-attachments/assets/62c77c70-0399-498b-8fc8-54cfc98c5224" />
<div align="center">
   dia:27 MOS device character
  </div>
</div>

### 22-L2 Introduction to standard MOS voltage current parameters
- In a CMOS circuit, the output node and the load capacitor are driven by a pair of complementary transistors: one PMOS and one NMOS. These two devices operate in opposite states to control the output voltage.
- When the input voltage Vin is equal to Vdd logic HIGH, the NMOS and PMOS act as complementary switches. For the NMOS transistor, the gate to source voltage Vgs = Vin - Vss = Vdd, which exceeds its threshold voltage. As a result, the NMOS turns ON and behaves like a low-resistance path to ground. A drain-to-source current flows through it, creating a discharge path for the output node.
- At the same time, the PMOS transistor has both its gate and source terminals close to Vdd. Therefore, its gate to source voltage is approximately zero, which is smaller than the magnitude of its threshold voltage. This keeps the PMOS in the OFF state, effectively acting as an open circuit. Consequently, there is no conductive path from Vdd to the output node.
- Because of this complementary action, the load capacitor discharges through the conducting NMOS transistor, causing the output voltage Vout to drop to 0 logic LOW.<br>
<div align="center">
<img width="831" height="418" alt="Screenshot 2026-02-23 105614" src="https://github.com/user-attachments/assets/98a834d6-d54c-4c4e-8ec3-eef36db95cc7" />
<div align="center">
   dia:28 MOS Voltage and Current character
  </div>
</div>

### 23-L3 PMOS/NMOS drain current vs drain voltage
- The naming conversion of volyage across NMOS and PMOS. The current direction is totally inverse, when Vin = Vdd,Vout =0.
- For the charge discharge, when Vin = 0,Vout = Vdd. While going to euqtion it shows everything which we go around digital circuits is based on what the input voltage we are giving and what the output voltage we are getting.<br>
For voltage observation<br>
<img width="119" height="107" alt="image" src="https://github.com/user-attachments/assets/902a26dc-6a17-433c-9d5c-50b598ae2d51" />
<img width="88" height="44" alt="image" src="https://github.com/user-attachments/assets/3a950233-89b0-49a9-9f33-22b76cd3d468" /><br>
The positive Idsp is inverted to negative Idsn and there is negative potential for PMOS.<br>
<img width="418" height="219" alt="image" src="https://github.com/user-attachments/assets/6b748eb7-e434-42d7-88db-9f7943c89d8b" /><br>

### 24-L4 Step 1-Convert PMOS gate-souce-voltage to Vin
- From the Id-Vd curve of the CMOS, while we are seeing in inverting view there will be only Vin and Vout. In that way we can able relate the value of Vin and Vout.<br>
<div align="center">
<img width="622" height="339" alt="image" src="https://github.com/user-attachments/assets/357ea955-c79f-43b3-b586-9d5fc119bd44" />
<div align="center">
   dia:29 MOS Voltage and Current in CMOS
  </div>
</div><br>
Below are the steps to obtain voltage transfer characteristics(VTC) for static CMOS inverter:<br>
let us assume below values(Vdd = 2v)<br>
<img width="75" height="120" alt="image" src="https://github.com/user-attachments/assets/e81650ed-42e4-4e33-a084-39c8e1dbc374" /><br>
In one table of Vgsp and its five different value of Vgsp. The load is going to lower for using Vdd in the equation(Vin).<br>

### Vin=Vgsp+Vdd
For calculating Vin we have Vdd value and Vgsp value to substitute it.<br>
<img width="180" height="115" alt="image" src="https://github.com/user-attachments/assets/b6a416e5-5468-4ae4-a29f-750c41824caf" /><br>
The Vin and the Id value will shift the graph plot<br>
<div align="center">
<img width="182" height="183" alt="image" src="https://github.com/user-attachments/assets/ff582fef-f48f-4ec4-aadb-04f16e371775" />
<div align="center">
   dia:30 CMOS -Vdsp vs Idsn
  </div>
</div><br>

### 25-L5 Step2 & Step3-convert PMOS and NMOS drain-source-voltage to Vout
In this we are converting the Vdsp and Idsn to Vout.<br>
Vout=Vdd+Vdsp<br>
- if the vdsp is negative 2v then we add positive 2v we get the Vout.now the Vout will be zero.when the Vout is zero we can see the finite current flowing.<br>
<div align="center">
<img width="624" height="196" alt="Screenshot 2026-02-24 085411" src="https://github.com/user-attachments/assets/641a44f5-a5fa-4087-8f0b-3da117c150c9" />
<div align="center">
   dia:31 Vout
  </div>
</div><br>
TRhe above curve is the load curve for PMOS transistor.<br>
Let us obtain the load curve for NMOS transistor using the equations:<br>
Vgsn=Vin-Vss='Vin'<br>
Vdsn=Vout<br>
The load curve of NMOS, PMOS transistor and CMOS inverter to get the voltage characteristics. 

### 26-L6 Step4-Merge PMOS-NMOS load curves and plot VTC
- We will superimpose the load curve of NMOS on the load curve of PMOS because the Vin ande Vout are common to our PMOS and NMOS. There is a intersection between the PMOS and NMOS curve.
<div align="center">
<img width="619" height="195" alt="Screenshot 2026-02-24 092256" src="https://github.com/user-attachments/assets/58c0ac4f-b00d-442a-86cd-e33d54b30863" />
<div align="center">
   dia:32 loard curve transistor
  </div>
</div><br>

- When Vin is 0, Then the PMOS is on and the NMOS is off. In that case we take Vin=0 line curve of both transistor and find the common point.
- We suoperimpose both the curve and derive the VTC for the CMOS inverter. The range of voltage we are looking is 0 to 2v.
<div align="center"> 
 <img width="604" height="179" alt="Screenshot 2026-02-24 093605" src="https://github.com/user-attachments/assets/e3b6670e-6d4a-4ab1-ad21-491295d89790" />
 <div align="center">
   dia:33 Intersection curve
  </div>
</div><br>
- We have the graph of Vout from 0 to 2v and the Vin for 0 to 2v. Vin and Vout are common to PMOS and NMOS.
- Graphically, we will pick up Vin points from the intersection of corresponding load lines. PMOS is in linear region and NMOS is cutoff region.
 <div align="center">
<img width="207" height="169" alt="Screenshot 2026-02-24 094157" src="https://github.com/user-attachments/assets/f7725d6e-9053-4a97-aac6-96b1ea6d70fd" />
 <div align="center">
   dia:34 CMOS curve
  </div>
</div><br>

## NgspiceSky130-Day 3-CNOS switching threshold and dynamic simulations
### ***Voltage transfer characteristics-SPICE simulations***
### 27-L1 SPICE deck creation for CMOS inverter
Before the simulation first we want to create the SPICE deck.<br>
SPICE deck: The connectivity information about the netlist.
- The significance of the arrow will show the M1 PMOS and M2 NMOS in the diagram.
- The significance of the substrate voltage it tunes the threshold voltage of PMOS and NMOS.
  <div align="center">
  <img width="250" height="215" alt="Screenshot 2026-02-24 101416" src="https://github.com/user-attachments/assets/163d7395-2e78-45de-b65f-29c1f64b5889" />
   <div align="center">
   dia:35 CMOS circuit
  </div>
</div><br>

- The source of PMOS is connected to Vdd and the source of NMOS is connected to Vss. The value of output load capacitance is connected.
- Next is component values and connect the voltage.
- Then define the node between two component and identity it. The m1 is completely define PMOS ans m2 is for NMOS.<br>
<img width="316" height="117" alt="Screenshot 2026-02-24 101704" src="https://github.com/user-attachments/assets/375acbae-97d6-4136-8167-ee32ffda849a" /><br>

### 28-L2 SPICE simulation for CMOS inverter
The capacitance load for the the below CMOS circuit is 0 to 10f and the Vdd and Vin is 0 to 2.5v.<br>
<img width="591" height="231" alt="Screenshot 2026-02-24 102433" src="https://github.com/user-attachments/assets/220fd68a-2498-4aaa-9cfa-0d06b761a0c8" />
### SPICE waveform:
Wn=Wp=0.375u,Ln,p=0.25u device<br>
(Wn/Ln=Wp/Lp=1.5)<br>
<img width="441" height="350" alt="Screenshot 2026-02-24 104117" src="https://github.com/user-attachments/assets/a4a80340-7715-403b-8d4f-0401386ba84b" /><br>
Wn=Wp=0.375u,Wp=0.9375,Ln,p=0.255u device<br>
(Wn/Ln=Wp/Lp=1.5, Wp/Lp=2.5)<br>
<img width="441" height="355" alt="Screenshot 2026-02-24 105249" src="https://github.com/user-attachments/assets/5cfff85f-d6ef-4471-8d48-f16b8094af79" /><br>

### 29-L3 Labs Sky130 SPICE simulation for CMOS
Inverse VTC<br>
<img width="689" height="536" alt="Screenshot 2026-02-24 110449" src="https://github.com/user-attachments/assets/f423ef77-a74d-4e4e-aa41-15efd57b80bc" /><br>
Vth=0.876v<br>
For rise delay and fall delay

## NgspiceSky130-Day 4-CMOS Noise Margin robustness evaluation
### ***Static behavior evaluaion-CMOS inverter robustness-Noise margin***
### 36-L1 Introduction to noise margin
This chapter is about understanding noise margin of any of the transistor.<br>
***Noise margin:*** In CMOS digital circuits is the measure of how much unwanted noise a signal can tolerate without causing a logic error. It indicates the robustness of a logic gate against voltage disturbances.<br>
In digital logic, signals are interpreted as:
- Logic 1 (HIGH)
- Logic 0 (LOW)
The output drop will not be instant but its gradual resulit of final slope. The Vil is low input voltage. Any input voltage level between 0 and Vil will be treated as logic 0.<br>
<div align="center">
<img width="357" height="167" alt="Screenshot 2026-02-24 143843" src="https://github.com/user-attachments/assets/0372020d-7359-46f5-834a-96fa51cd9ce5" />
<div align="center">
   dia:36 Noise margin
  </div>
</div><br>

### 37-L2 Noise margin voltage parameters
- Any voltage which lies between Vin and Vil will recognise as logic 0 and the output is high
- Any voltage which is above Vil will recognise as logic 1 and the output is low.
- Actual characteristics of a inverter the change in input voltage is positive and the change in output voltage is negative.
- Vol shouild be less than Vil then only recognise logic 0.
 <div align="center"> 
<img width="351" height="172" alt="Screenshot 2026-02-24 145231" src="https://github.com/user-attachments/assets/c160ca38-9025-4d55-90f6-d4dc75d91de6" />
<div align="center">
   dia:37  characteristics of a inverter
  </div>
</div><br>

### 38-L3 Noise margin equation and summary
Noise margin is basically define the input voltage range and the output voltage range.(Voh>Vih)
- The first value we are plotted on the scale is that Voh and then Vih.
- less than Vil is Vol so after Vih thenext is Vil and then VOL.
- In Voh and Vih the noise margin is very high.(Voh-Vih)
- In Vil and Vol the noise margin is very low(Vil-Vol).these are the noise margin which will decide the tolerance of noise.
  <img width="137" height="163" alt="image" src="https://github.com/user-attachments/assets/45e95139-9a58-4922-a977-17c9dca7222c" /><br>
- The region between the two area are the undefined region.  For any signal to be considered as logic 0 and logic1, it should be in the NMl and NMh ranges respectively.

### 39-L4 Noise margin variation with respect to PMOS width
Lets take the Dc trnasfer characteristic for an PMOS = NMOS. Point on that slope which shows negative one. Here the noise margin high is 0.3v and the noise margin low is 0.3v.
- The PMOS and NMOS width is sustain in the high and low margin then it will be logic 1.
- 






















  





 






























   
                 
       
     

 


     
 

  
  

     

