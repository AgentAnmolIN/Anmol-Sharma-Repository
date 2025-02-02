
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
# **Section 2: Good vs. Bad Floorplans and Library Cells**

## **Overview**
This section explains the basics of floorplanning in digital chip design. We’ll cover things like how much space is used (utilization factor), the shape of the layout (aspect ratio), pre-placed cells, power planning, and pin placement. We’ll also introduce library cells and how they are tested.

---

## **Utilization Factor and Aspect Ratio**

### **Utilization Factor**
- This tells us how much of the chip’s area is filled with logic cells, power connections, and other parts.
- A **high utilization factor** means space is used well, but too much usage can lead to problems like overheating and congestion.

### **Aspect Ratio**
- This is the ratio of a chip’s width to its height.
- A **balanced aspect ratio** helps with:
  - Easier routing of wires.
  - Even power distribution.
  - Better heat management.
- A **skewed aspect ratio** can cause longer wire connections and more power consumption.

---

## **What Are Pre-Placed Cells?**
- These are certain cells placed on the chip before the main design process starts.
- They help with:
  - **Clock distribution** (making sure timing is correct).
  - **Power delivery** (ensuring power reaches all parts evenly).
  - **Reset logic** (keeping everything stable when the chip starts up).
- Placing these ahead of time makes the design more efficient.

---

## **What Are Decoupling Capacitors (Decaps)?**
- These are small components placed between power and ground.
- They help by:
  - Preventing voltage drops.
  - Filtering out unwanted noise.
  - Keeping signals stable.

---

## **Power Planning**
- This makes sure power is delivered properly across the chip.
- It includes:
  - **Designing power grids** to avoid voltage drops.
  - **Managing voltage drops** to keep signals reliable.
  - **Using decoupling capacitors** to reduce noise.
- Good power planning helps the chip run smoothly.

---

## **Pin Placement and Blocked Areas**

### **Pin Placement**
- This determines where **input/output (I/O) pins** go.
- Good pin placement reduces:
  - Wire length.
  - Congestion.
  - Timing delays.

### **Blocked Areas for Cell Placement**
- Some areas are off-limits for standard cells due to design needs.
- Reasons include:
  - Pre-placed cells.
  - Reserved regions (like power grids or clock trees).
- Managing these blockages improves routing and timing.

---

## **Mapping the Netlist and Initial Placement**

### **Netlist Binding**
- This means matching the logical design (netlist) to actual physical cells.
- Cells are chosen based on:
  - **Their function** (AND, OR, Flip-Flops, etc.).
  - **Performance needs** (speed, power, size).

### **Initial Placement**
- This step places cells on the chip based on how they connect.
- The goal is to **reduce wire length and congestion** while keeping timing in check.

---

## **Optimizing Placement Using Wire Length and Capacitance**

### **Wire Length Optimization**
- Shorter wires mean less resistance and delay.
- This helps signals move faster.

### **Capacitance Optimization**
- Reducing capacitance prevents unwanted interference between wires.
- This improves speed and lowers power use.
- Adjusting placement can help optimize performance.

---

## **Final Placement Optimization**
- Uses special techniques to improve design:
  - **Timing optimization:** Making sure signals arrive on time.
  - **Power optimization:** Reducing power use while keeping performance.
  - **Area optimization:** Using space efficiently for lower cost.

---

## **Why Do We Need Libraries and Characterization?**

### **Libraries**
- These are collections of pre-made circuit components (like AND gates, OR gates, Flip-Flops, etc.).
- They are tested for:
  - **Speed** (how fast they work).
  - **Power use**.
  - **Size**.
  - **Voltage needs**.

### **Characterization**
- This is the process of testing how well these components work.
- It helps with:
  - **Timing analysis** (checking signal delays).
  - **Power estimation** (predicting power use).
  - **Better placement and routing**.

---

## **Avoiding Congestion Using RePlAce**
- A tool that helps balance cell placement.
- Prevents crowded areas that make routing harder.
- Helps improve timing and overall performance.

---

## **What Goes Into Cell Design?**
- **Design Specifications:** What the cell needs to do.
- **Process Technology:** Defines transistor sizes and wiring layers.
- **Electrical Characteristics:** Includes power and timing rules.
- **Library Constraints:** Makes sure the cell follows design rules.

### **Steps in Circuit Design**
1. **Logic Design:** Defines what the cell does (e.g., AND, OR, XOR).
2. **Schematic Design:** Creates the circuit using transistors.
3. **Simulation & Verification:** Tests if it works correctly.
4. **Optimization:** Adjusts transistor size and placement for better performance.

### **Steps in Layout Design**
1. **Transistor Layout:** Arranges transistors and wires.
2. **Routing:** Connects metal layers properly.
3. **Design Rule Checking (DRC):** Ensures it can be manufactured.
4. **Layout vs. Schematic (LVS):** Confirms the layout matches the original design.

---

## **How Are Library Cells Tested?**

### **Simulation Setup**
- Uses tools to model how the cell works under different conditions.

### **Timing Analysis**
- Checks delays (how long signals take to travel).

### **Power Analysis**
- Measures power use in different situations.

### **Testing for Process Variations**
- Looks at how temperature, voltage, and manufacturing differences affect performance.
- Makes sure the cell works in all conditions.

### **Characterization Data**
- Stores timing, power, and noise data for use in chip design.

---

## **Important Timing Terms**
- **Vih (Input High Voltage):** The lowest voltage needed for a logic HIGH.
- **Vil (Input Low Voltage):** The highest voltage allowed for a logic LOW.
- **Voh (Output High Voltage):** The minimum output voltage for HIGH.
- **Vol (Output Low Voltage):** The maximum output voltage for LOW.
- **These values ensure signals are understood correctly.**

---

## **Propagation Delay and Signal Transition Time**
- **Propagation Delay:** Time it takes for a signal to move from input to output.
  - **tPLH:** Time for a LOW-to-HIGH change.
  - **tPHL:** Time for a HIGH-to-LOW change.
- **Transition Time:** How long it takes for a signal to move from 10% to 90% of its voltage.
- Faster transitions improve circuit speed and efficiency.

---
#### Section 2 Tasks

1. Run 'picorv32a' floorplan using OpenLANE flow and get the Output
2. Calculate the area of a die
3. Load floorplan in Magic tool and explore it
4. Run 'picorv32a' design placement using OpenLANE flow and get the output.
5. Load placement in Magic tool and explore it

>>> Run 'picorv32a' floorplan using OpenLANE flow and get the Output

1. Go to Openlane Directory

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
2. Run the command Docker

```bash
docker
```
3. Go to interactive mode
```tcl
#Use this command to go to interactive mode
./flow.tcl -interactive

#input required packages using this command
package require openlane 0.9


#The OpenLANE flow is now set up to handle any design. Before running a specific design like 'picorv32a', we first need to create important files and directories to prepare the environment using this command

prep -design picorv32a

#run synthesis using this command
run_synthesis

# Now we can run floorplan
run_floorplan
```

### **Snapsohots Of Running A Floor Plan** ###
START:-
![Screenshot 2025-02-01 222014](https://github.com/user-attachments/assets/73bb781f-edcb-449b-b7b5-d014d981d87c)
END:-
![Screenshot 2025-02-01 222122](https://github.com/user-attachments/assets/bef95e49-ea19-435a-bc7a-3a63abc31a32)


## 2. Calculate die area ##

#### **Screenshot of contents in Floorplan(YELLOW BOX SHOWS THE DIE WIDTH AND HEIGHT)** ####

![Screenshot 2025-02-01 222632](https://github.com/user-attachments/assets/33b0dcb0-0cae-4a7e-98ad-8cc07ebd8a9b)

```math
1000\ Unit\ Distance = 1\ Micron
```
```math
Die\ width\ in\ unit\ distance = 660685 - 0 = 660685
```
```math
Die\ height\ in\ unit\ distance = 671405 - 0 = 671405
```
```math
Distance\ in\ microns = \frac{Value\ in\ Unit\ Distance}{1000}
```
```math
Die\ width\ in\ microns = \frac{660685}{1000} = 660.685\ Microns
```
```math
Die\ height\ in\ microns = \frac{671405}{1000} = 671.405\ Microns
```
```math
Area\ of\ die\ in\ microns = 660.685 * 671.405 = 443587.212425\ Square\ Microns
```

### **Commands to run floorplan in magic** ###

```bash
# Change directory to floorplan
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/01-02_05-07/results/floorplan/

# Command to run the floorplan in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
