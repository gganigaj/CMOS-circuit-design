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
Select Use an existing virtual hard disk file
Click the folder icon
Browse to the unzipped CMOS VDI file
Click Open
Click Next
Click Finish<br>
## NgspiceSky130-Day 1-Basics of NMOS Drain current(Id) vs Drain-to-source voltage(Vds)<br>
### Introduction to Circuit Design and SPICE simulation<br>
#### 0-L1 Why do we need SPICE simulations?<br>
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
  The delays are actually comes from the SPICE simulations. The delay models are accurate by having the same input and output load which is matching in the SPICE simulation we get the delay values.
     
 

  
  

     

