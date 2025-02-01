
# **Advanced Physical Design Using OpenLane/Sky130**  
## **Section 1: Inception of Open-Source EDA, OpenLANE, and Sky130 PDK**  

### **Overview**  
This section introduces key concepts in open-source Electronic Design Automation (EDA), OpenLANE, and SkyWater 130nm Process Design Kit (PDK). It covers fundamental aspects of ASIC design, including packaging, RISC-V architecture, and the open-source digital ASIC design flow.  

---

## **QFN-48 Package: Structure and Benefits**  

### **What is QFN-48?**  
The Quad Flat No-Lead (QFN-48) package is a compact, surface-mount IC package with 48 pins. It is widely used for microcontrollers, RF devices, and power management ICs due to its excellent thermal dissipation, low electrical parasitics, and cost-effectiveness.  

### **Key Components:**  
- **Chip (IC):** The core functional unit containing electronic circuits for processing and logic operations.  
- **Pads:** Metallic contact points on the silicon die, ensuring electrical connectivity.  
- **Core:** The processing unit within the chip, containing logic gates, memory, and computational elements.  
- **Die:** A single slice of a silicon wafer that holds the semiconductor circuits.  
- **IPs (Intellectual Property blocks):** Pre-designed functional modules like CPU cores, memory blocks, and communication interfaces (SPI, I2C, USB, etc.).  

### **Advantages of QFN-48:**  
✔️ Small form factor, ideal for compact devices.  
✔️ Enhanced thermal and electrical performance with exposed pad design.  
✔️ Low parasitic inductance, suitable for high-speed applications.  
✔️ Cost-effective and easy to manufacture.  

---

## **Introduction to RISC-V**  

### **What is RISC-V?**  
RISC-V (pronounced "risk-five") is an open-source, Reduced Instruction Set Computing (RISC) architecture that provides flexibility, scalability, and energy efficiency. Unlike proprietary ISAs (e.g., ARM, x86), RISC-V is royalty-free, fostering innovation and reducing development costs.  

### **Key Features:**  
- **Open-source:** Free to use and modify.  
- **Modular Architecture:** Supports various instruction set extensions (e.g., floating-point, vector processing).  
- **Scalability:** Suitable for devices ranging from microcontrollers to supercomputers.  
- **Energy Efficiency:** Optimized for low-power applications.  
- **Customization:** Enables custom processor designs without licensing restrictions.  

### **Applications:**  
- Embedded systems (IoT, microcontrollers).  
- AI and Machine Learning accelerators.  
- Data centers and cloud computing.  
- Automotive and industrial automation.  
- Custom hardware research and development.  

### **Why is RISC-V Important?**  
RISC-V is transforming the semiconductor industry by offering an open, royalty-free alternative to traditional ISAs. It is backed by leading companies and research institutions worldwide.  

---

## **Open-Source Digital ASIC Design: Key Components**  

### **What is Digital ASIC Design?**  
An Application-Specific Integrated Circuit (ASIC) is a custom-designed semiconductor chip for specialized applications (e.g., CPUs, GPUs, AI accelerators). Open-source ASIC design provides a cost-effective alternative to proprietary EDA tools.  

### **ASIC Design Flow:**  
1. **RTL Design (Verilog/VHDL):** Defines chip logic and functionality.  
2. **Logic Synthesis (Yosys):** Converts RTL into a gate-level netlist.  
3. **Floorplanning & Power Planning (OpenROAD):** Optimizes chip layout and power distribution.  
4. **Placement (RePLace):** Arranges logic cells efficiently.  
5. **Clock Tree Synthesis (TritonCTS):** Distributes clock signals with minimal skew.  
6. **Routing (FastRoute, TritonRoute):** Establishes physical connections between components.  
7. **Signoff Checks (Magic, Netgen, OpenSTA):** Ensures compliance with design rules and timing constraints.  
8. **GDSII Export:** Final layout is generated for fabrication.  

✔️ **Fully open-source flow** eliminates the need for proprietary tools.  
✔️ **Optimized for SkyWater 130nm PDK**, an open-source manufacturing process.  

---

## **Introduction to OpenLANE & Strive Chipsets**  

### **What is OpenLANE?**  
OpenLANE is an open-source ASIC design flow developed by Efabless, integrating multiple EDA tools:  
- **Yosys:** Logic synthesis.  
- **OpenROAD:** Placement, CTS, and routing.  
- **Magic & KLayout:** Layout visualization and DRC checks.  
- **Netgen:** LVS verification.  
- **Fault:** DRC rule checking.  

### **Strive Chipsets**  
Strive chipsets are RISC-V-based open-source ASICs designed using OpenLANE, showcasing a fully open-source implementation.  

---

## **Detailed OpenLANE ASIC Design Flow**  

### **Step-by-Step OpenLANE Flow:**  
1. **Design Setup:** Define clock speed, power constraints, and Verilog design files.  
2. **Synthesis (Yosys & ABC):** Convert RTL to a gate-level netlist with logic optimizations.  
3. **Floorplanning (OpenROAD):** Define power distribution and chip layout.  
4. **Placement & Optimization (RePLace, OpenROAD):** Arrange standard cells for efficiency.  
5. **Clock Tree Synthesis (TritonCTS):** Minimize clock skew for timing accuracy.  
6. **Routing (FastRoute, TritonRoute):** Assign metal layers for connectivity.  
7. **Signoff Checks (Magic, Netgen, OpenSTA):**  
   - **DRC (Design Rule Check):** Ensures manufacturability compliance.  
   - **LVS (Layout vs. Schematic):** Verifies layout matches netlist.  
   - **STA (Static Timing Analysis):** Confirms timing constraints are met.  
8. **GDSII Export:** Final layout is saved for fabrication.  

### **Why Open-Source ASIC Design Matters?**  
✔️ **No Licensing Fees:** Unlike commercial tools (Synopsys, Cadence).  
✔️ **Full Customization:** Modify and adapt standard libraries freely.  
✔️ **Encourages Innovation:** Ideal for startups, universities, and research labs.  
✔️ **Fabrication Ready:** Compatible with **SkyWater 130nm PDK** for real-world chip manufacturing.  

---
## **Section 1:**
1. Run "picorav32a" synthesis using OpenLane and generat output.
2. Calculate flop ration.
3. Run "picorav32a" synsthesis using OpenLane and generat output.
### **1. Go to Openlane Directory.**
```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
### **2. Run the command 'Docker'**

```bash
docker
```
### **3. Going to- interactive mode**
```tcl
# By using this command we can go to interactive mode
./flow.tcl -interactive

#input the required packages using the command given below:
package require openlane 0.9


#The OpenLANE flow is now set up to handle any design. Before running a specific design like 'picorv32a', we first need to create important files and directories to prepare the environment using this command

prep -design picorv32a

#Finally run synthesis using this command
run_synthesis

```
![Screenshot 2025-02-01 184339](https://github.com/user-attachments/assets/c16f3ee2-09d0-46b5-8323-ddd324194c41)

![Screenshot 2025-02-01 184555](https://github.com/user-attachments/assets/5a528e39-ac19-4f76-8da9-a1a2c2e01066)

![Screenshot 2025-02-01 184339](https://github.com/user-attachments/assets/2e5fe5f0-32f6-4370-8a40-8f9dea3cc57a)


### **2. Calculating the flop ratio:**

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
```math
Percentage\ of\ D Flip Flops's = Flop\ Ratio * 100
```


```tcl
# As earlier you had run a synthesis, they all are stored in a specific folder and it isn't necessary to run the sinthesis again and again

#so """"""""""""""I'll tell you a short cut """"""""", as given below:

cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-08_10-49/reports/synthesis

ls -ltr

less yosys_2.stat.rpt

#**AND HERE YOU GO **

#****TOP SECRET**** CONFIDENTIAL!
```

### D FLIP FLOP ###
![Screenshot 2025-02-01 205046](https://github.com/user-attachments/assets/119389c1-931f-4646-89fa-6e1cc0ca4216)
### TOTAL NUMBER OF CELLS ###
![Screenshot 2025-02-01 205111](https://github.com/user-attachments/assets/46ac26ac-b5be-4db8-aff7-f75106034c2f)

### Calculation of Flop Ratio and D Flip Flop's % ###

```math
Flop\ Ratio = \frac{1613}{14876} = 0.1084296853993009
```
```math
Percentage\ of\ D Flip Flops's = 0.1084296853993009 * 100 = 10.84296853993009\ \%
```
