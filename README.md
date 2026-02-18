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
       </div>
       The p-substrate has an two isolation region which are used to differentiate between two transistor behaviour. It has an n+ diffusion region, which are called as source and drain terminal. The gate oxide is placed over the p-substrate. The poly-si or metal gate is placed on tha gate oxide layer.<br>
 #### Threshold voltage
The minimum gate to source voltage (VGS) needed to create a conductive channel between the drain and source.
<div align="center">
 <img width="245" height="182" alt="image" src="https://github.com/user-attachments/assets/c6c31b23-6fd5-4c62-9d0a-1b63bb4084d1" />
 <div align="center">
  dia:6 Vgs=0
  </div>
   </div>
if Vgs=0 and the drain,source,bulk are connected to the ground.The substrate-source and substrate-drain will form p-n junction diode.now both the junctions are in off mode so, source-drain resistance is high.<br>
 <div align="center">
  <img width="244" height="195" alt="image" src="https://github.com/user-attachments/assets/a188174f-d286-44f7-a274-1e260c20010f" />
   <div align="center">
   dia:7 Vgs>0
   </div>
 </div> 
When we are apply small voltage to the gate,it will repell all the positive charge which is present over the substrate.mobile holes are repelled by the +ve charge at 'G' and they leave behind the -ve charges.The -ve charge will start to accumulate.<br>

### 2-L3 Strong inversion and threshold voltage<br>
In the pn-junction whenever we are applying reverse bias on the voltage, depletion region will occur.Increasing the gate voltage level,depletion region width is also increase.so that small region in tha p-substrate is converted into n-substrate this phenomenon is called as strong inversion.<br>
The Vgs voltage at which strong inversion occurs is called threshold voltage(Vt).
 <div align="center">
<img width="251" height="202" alt="image" src="https://github.com/user-attachments/assets/ba3f74c6-ec46-46af-88d2-1ad7d8d5ef07" />
 <div align="center">
dia:8 strong inversion
 </div>
  </div>
  When the Vgs is further increases, the channel width get increases but there is no change in depletion layer width.The electrons from heavily doped n+ source region are drawn in region under gate.The continuous n-channel formation from source to drain,whose conductivity is modulated by Vgs.<br>
  <div align="center">
   <img width="566" height="222" alt="Screenshot 2026-02-18 144543" src="https://github.com/user-attachments/assets/8c9429be-ac3f-4c64-82f3-c8427b3fba5a" />
    <div align="center">
    dia:9 Vsb=0 and Vsb=+ve
     </div>
      </div>
The above diagram shows that the Vsb=0 and Vsb=+ve value.The +ve Vsb will have the high depletion width compare to the Vsb=0.Because there is a additional reverse bias that is applied to the +Vsb the n-type area is connected to the positive source and p-substrate is connected to the negative souce.<br>

### 3-L4 Threshold voltage with positive substrate potential
On the application of gate voltage to the Vsb=0 and Vsb=+ve.while in Vsb=+ve the depletion region increases the accumulation of negative charge in source is increases.<br>
    Due to +ve Vsb,few charges from channel are pulled towards source and there is no surface inversion will happen at +ve Vsb. while in Vsb=0 the semiconductor surface inverts to n-type material at voltage Vgs=Vto.
    <div align="center">
    <img width="556" height="232" alt="image" src="https://github.com/user-attachments/assets/b64359ca-a2ce-4791-a924-4afb871dafc1" />
      <div align="center">
      dia:10 surface inversion 
       </div>
        </div>
To make the surface inversion in Vsb +ve the semiconductor surface inverts to n-type material at voltage Vgs=Vto+v1.In the presence of substrate bias 'Vsb',additional potential is required for strong inversion.
![WhatsApp Image 2026-02-18 at 3 21 11 PM](https://github.com/user-attachments/assets/c50135ce-2c1a-4948-86e6-193d0548e64a)<br>
- Vto is the threshold voltage at Vsb=0
- γ is the body effect coefficient, which indicates how strongly the threshold voltage changes with body bias. It depends on substrate doping and oxide capacitance.<BR>
<img width="299" height="136" alt="image" src="https://github.com/user-attachments/assets/fad87888-91c0-4eed-8065-04cd1ad1cf43" /><br>
- φF is the Fermi potential of the substrate, representing the energy difference between the intrinsic level and the Fermi level in the semiconductor.<br>
  <img width="312" height="68" alt="image" src="https://github.com/user-attachments/assets/aa9add35-0e7e-4de9-8245-40ab6bde1dad" /><br>
- These values are obtained from the foundry and fed into the SPICE model for device modelling and simulation.<br>

## NMOS resistive region and saturation region of operation
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
There are two types of current:<br>
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
   Considering kn= unCox, where kn is the process transconductance, which determines how effectively the device converts gate voltage into drain current.

   

   
                 
       
     

 


     
 

  
  

     

