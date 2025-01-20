- **Name:** MADHAVI ARADHYULA  
- **Company:** CODTECH IT SOLUTIONS  
- **ID:** CT08DOW  
- **Domain:** VLSI  
- **Duration:** Dec 2024 to Jan 2024  
- **Mentor:** SRAVANI GOUNI
---

# **RISC Pipelined Structure*
- ![image](https://github.com/user-attachments/assets/83086d0b-4872-4760-805e-3e93b2483a68)
## **RISC Pipelined Structure**

The RISC pipelined processor structure is designed to enhance performance by executing multiple instructions simultaneously. The pipeline is divided into the following stages:

1. **Fetch (IF)**:
   - Fetches the instruction from memory using the Program Counter (PC).

2. **Decode (ID)**:
   - Decodes the fetched instruction and determines the operation to perform. 
   - Reads the required source registers.

3. **Execute (EX)**:
   - Performs arithmetic or logical operations using the ALU.

5. **Write Back (WB)**:
   - Writes the result back to the destination register.

### **Pipeline Challenges**
While pipelining improves throughput, it introduces several challenges:
- **Data Hazards**: Occurs when an instruction depends on the result of a previous instruction.
- **Control Hazards**: Arises from branch instructions (e.g., BEQ).
- **Structural Hazards**: Happens when hardware resources are insufficient.

---

## **Pipeline Control Logic**

The **Pipeline Control Logic** handles hazards to maintain proper instruction execution without errors. Below is the explanation of how the control logic addresses hazards:

### **1. Data Hazard Detection**
- **Registers Involved**:  
  `exir` (instruction register in Write-Back Pipe) and `idir` (instruction register in Execute Pipe).  
- Detection ensures no conflicts arise when instructions depend on each other's data.

### **2. Control Hazard Detection**
- **Registers Involved**:  
  `idir` (instruction register in Execute Pipe), `ifir` (instruction register in Decode Pipe), and the `zero` signal from the comparator.  
- Ensures proper execution of branch instructions (e.g., BEQ).

### **3. Data Forwarding**
- **How It Works**:  
  Forwarding is performed by checking `exir` and `idir` instruction registers.  
  It avoids stalling when dependencies between instructions occur.

### **4. RAW Hazard (Read After Write) Handling**
- **Case 1**: Two R-type Instructions (e.g., ADD/AND):  
  No stalling is required. Data forwarding in the controller unit resolves the hazard.
  
- **Case 2**: BEQ Following an R-type Instruction:  
  - One bubble is inserted in the Execute Pipe.  
  - Corresponding hold is enforced in the PC register and Decode Pipe.

### **5. Control Hazard Handling**
- **BEQ Instruction**:  
  One bubble is inserted in the Decode Pipe to handle the control hazard.

### **6. Combined Control and Data Hazards**
- **When Both Occur Simultaneously**:  
  - **Present Clock Cycle**: Data hazard is resolved.  
  - **Next Clock Cycle**: Control hazard is handled.

---

## **Tools Used**

- **Xilinx Vivado**:
  - Used for simulation and synthesis of the RISC pipelined structure and control logic.

 
