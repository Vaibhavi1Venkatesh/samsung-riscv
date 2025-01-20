# samsung-riscv
 Welcome to the Samsung RISC-V  repository. This repository contains my work for the first task of the program. The task involves setting up and using the RISC-V toolchain to compile and run simple programs, as well as documenting the process.

# Samsung RISC-V Task 1

This repository contains the work for Tasks of the RISC-V Talent Development Program.

## Contents
- `task1`: RISC-V based screenshots.

### Disassembly Output
This image shows the disassembly of a compiled RISC-V program in a terminal using the objdump command.  
![mainriscv](https://github.com/user-attachments/assets/4a12fdf2-25e1-4502-a498-678b109654c8)
![riscv1](https://github.com/user-attachments/assets/d72e20b8-ff21-4457-b203-70c20d434685)
![ssriscv](https://github.com/user-attachments/assets/4b729cbb-04b1-4e1a-8a5e-4efc9dd774e7)

### Terminal View of objdump
An enlarged view of a terminal running the objdump command on a RISC-V program.  
 ![riscvtask1](https://github.com/user-attachments/assets/9be9b746-7ee4-45fe-8b51-d40b3b194af1)

 - `task1`: C based lab screenshots.
 ### C outputs
 Screenshot of a terminal session in a VirtualBox environment running Ubuntu, showing the execution of a C program that calculates the sum of numbers from 1 to 5. The project directory structure contains relevant C source files (.c) and associated files
  
![newctask1](https://github.com/user-attachments/assets/bf35f697-bec6-4f20-8f3e-8bac6a699b6d)


# Samsung RISC-V Task 2

This repository contains a simple RISC-V program to compute the sum of numbers from 1 to a given limit. It includes source code, scripts for compilation and execution, and documentation for setting up and using the RISC-V toolchain and Spike simulator.By using "Ofast"
## task 2:using Ofast
![ofasttask23](https://github.com/user-attachments/assets/0134b8a6-f265-49b1-93bf-e73ab331afc0)
![ofasttask21](https://github.com/user-attachments/assets/929d4332-d749-4f2b-a1fb-87bddc9fe453)
![ofasttask2a2assembly](https://github.com/user-attachments/assets/b7c78b0b-4379-47f3-aa20-823a579a0dad)

## task 2:using O1
This repository contains a simple RISC-V program to compute the sum of numbers from 1 to a given limit. It includes source code, scripts for compilation and execution, and documentation for setting up and using the RISC-V toolchain and Spike simulator.By using "O1"

![o1task2ss](https://github.com/user-attachments/assets/00ef31d0-5999-4351-8d92-89b7a16fcadd)
![task22c](https://github.com/user-attachments/assets/622f3fed-8fd5-427c-806d-6a48e9ccdc63)
![o1task2assembly](https://github.com/user-attachments/assets/7ec3695a-16a0-4364-adcd-c181189337e6)
![assemblytask2](https://github.com/user-attachments/assets/077e37b2-eafe-4f69-bfd0-b1b53978dd45)
![o1task2assembly - Copy](https://github.com/user-attachments/assets/84d90257-37f1-4af4-83f8-ff4cc889435e)


<details>
<summary><h2>Task 3<h2></summary>
<br>
Instruction types - RISC-V instructions are classified into different types based on their field structure. Each type consists of specific fields, such as opcode, funct3, funct7, immediate values, and register identifiers. 

### **R-type: Register type**
Used for arithmetic and logic operations where all operands are in registers.  
- **Fields**:  
  | **Bits** | **Field**   | **Description**             |
  |----------|-------------|-----------------------------|
  | 0–6      | `opcode`    | Operation code             |
  | 7–11     | `rd`        | Destination register        |
  | 12–14    | `funct3`    | Function code (operation)   |
  | 15–19    | `rs1`       | Source register 1           |
  | 20–24    | `rs2`       | Source register 2           |
  | 25–31    | `funct7`    | Function code (extension)   |

**Example**: `add x1, x2, x3`  
  - `opcode`: 0110011  
  - `funct3`: 000  
  - `funct7`: 0000000  

### **I-type: Immediate type**
Used for arithmetic, logical, load, and immediate operations.  
- **Fields**:  
  | **Bits** | **Field**   | **Description**             |
  |----------|-------------|-----------------------------|
  | 0–6      | `opcode`    | Operation code             |
  | 7–11     | `rd`        | Destination register        |
  | 12–14    | `funct3`    | Function code (operation)   |
  | 15–19    | `rs1`       | Source register 1           |
  | 20–31    | `imm[11:0]` | Immediate value (12 bits)   |

**Example**: `addi x1, x2, -5`  
  - `opcode`: 0010011  
  - `funct3`: 000  

### **S-type: Store type**
Used for store operations (e.g., storing data to memory).  
- **Fields**:  
  | **Bits** | **Field**       | **Description**               |
  |----------|-----------------|-------------------------------|
  | 0–6      | `opcode`        | Operation code               |
  | 7–11     | `imm[4:0]`      | Immediate (low bits)         |
  | 12–14    | `funct3`        | Function code (operation)    |
  | 15–19    | `rs1`           | Source register 1 (address)  |
  | 20–24    | `rs2`           | Source register 2 (data)     |
  | 25–31    | `imm[11:5]`     | Immediate (high bits)        |

**Example**: `sw x2, 8(x1)`  
  - `opcode`: 0100011  
  - `funct3`: 010  

### **B-type: Branch type**
Used for conditional branches.  
- **Fields**:  
  | **Bits** | **Field**       | **Description**               |
  |----------|-----------------|-------------------------------|
  | 0–6      | `opcode`        | Operation code               |
  | 7–11     | `imm[11]`       | Immediate bit 11 (sign bit)  |
  | 12–14    | `funct3`        | Function code (operation)    |
  | 15–19    | `rs1`           | Source register 1            |
  | 20–24    | `rs2`           | Source register 2            |
  | 25–30    | `imm[10:5]`     | Immediate bits 10–5          |
  | 31       | `imm[12]`       | Immediate bit 12             |

**Example**: `beq x1, x2, offset`  
  - `opcode`: 1100011  
  - `funct3`: 000  

### **U-type: Upper immediate type**
Used for operations involving upper 20 bits of immediate data.  
- **Fields**:  
  | **Bits** | **Field**       | **Description**               |
  |----------|-----------------|-------------------------------|
  | 0–6      | `opcode`        | Operation code               |
  | 7–11     | `rd`            | Destination register          |
  | 12–31    | `imm[31:12]`    | Immediate value (upper 20 bits) |

**Example**: `lui x1, 0x12345`  
  - `opcode`: 0110111  

### **J-type: Jump type**
Used for jump operations.  
- **Fields**:  
  | **Bits** | **Field**       | **Description**               |
  |----------|-----------------|-------------------------------|
  | 0–6      | `opcode`        | Operation code               |
  | 7–11     | `rd`            | Destination register          |
  | 12–19    | `imm[19:12]`    | Immediate bits 19–12          |
  | 20       | `imm[11]`       | Immediate bit 11              |
  | 21–30    | `imm[10:1]`     | Immediate bits 10–1           |
  | 31       | `imm[20]`       | Immediate bit 20 (sign bit)   |

**Example**: `jal x1, offset`  
  - `opcode`: 1101111

<details>
<summary><h3>Machine Code:<h3></summary>
<br>
  
![obj_dump_O1 Image](https://github.com/Tech-Hades/samsung-riscv/raw/main/Task%203/obj_dump_O1.png)

### **1. Instruction: `addi sp, sp, -32`**
- **Machine Code**: `fe010113`
- **Instruction Type**: I-type  
- **Opcode**: `0010011` (bits [6:0])  
- **Immediate**: `1111111111110000` (-32 in two's complement)  
- **rs1**: `00010` (sp = x2)  
- **funct3**: `000` (add immediate)  
- **rd**: `00010` (sp = x2)

### **2. Instruction: `sd ra, 24(sp)`**
- **Machine Code**: `01113223`
- **Instruction Type**: S-type  
- **Opcode**: `0100011` (bits [6:0])  
- **Immediate**: `00000000011000` (24 split across bits [31:25] and [11:7])  
- **rs1**: `00010` (sp = x2)  
- **rs2**: `00001` (ra = x1)  
- **funct3**: `011` (store doubleword)

### **3. Instruction: `li s1, 16`**
- **Machine Code**: `01000513`
- **Instruction Type**: I-type  
- **Pseudo-instruction**: `li` maps to `addi s1, zero, 16`  
- **Opcode**: `0010011` (bits [6:0])  
- **Immediate**: `00000000001000` (16 in decimal)  
- **rs1**: `00000` (zero = x0)  
- **funct3**: `000` (add immediate)  
- **rd**: `01001` (s1 = x9)

### **4. Instruction: `mv a0, s0`**
- **Machine Code**: `00040513`
- **Instruction Type**: I-type  
- **Pseudo-instruction**: `mv` maps to `addi a0, s0, 0`  
- **Opcode**: `0010011` (bits [6:0])  
- **Immediate**: `00000000000000` (0 in decimal)  
- **rs1**: `01000` (s0 = x8)  
- **funct3**: `000` (add immediate)  
- **rd**: `00101` (a0 = x10)

### **5. Instruction: `jal ra, 101e0 <__muldi3>`**
- **Machine Code**: `0ac000ef`
- **Instruction Type**: J-type  
- **Opcode**: `1101111` (bits [6:0])  
- **Immediate**: `00000010101100` (address offset for 101e0 in decimal)  
- **rd**: `00001` (ra = x1)

### **6. Instruction: `sext.w a1, a0`**
- **Machine Code**: `0005059b`  
- **Instruction Type**: R-type  
- **Opcode**: `0011011` (bits [6:0])  
- **funct7**: `0000000` (bits [31:25])  
- **rs1**: `00101` (a0 = x10)  
- **funct3**: `000` (sign-extend word)  
- **rd**: `01011` (a1 = x11)

### **7. Instruction: `addiw s0, s0, 1`**
- **Machine Code**: `00140093`
- **Instruction Type**: I-type  
- **Opcode**: `0011011` (bits [6:0])  
- **Immediate**: `00000000000001` (1 in decimal)  
- **rs1**: `01000` (s0 = x8)  
- **funct3**: `000` (add immediate word)  
- **rd**: `01000` (s0 = x8)

### **8. Instruction: `bne s0, s1, 101a0 <main+0x1c>`**
- **Machine Code**: `fe941ae3`
- **Instruction Type**: B-type  
- **Opcode**: `1100011` (bits [6:0])  
- **Immediate**: `00000111011110` (address offset for main+0x1c in decimal)  
- **rs1**: `01000` (s0 = x8)  
- **rs2**: `01001` (s1 = x9)  
- **funct3**: `001` (branch not equal)

### **9. Instruction: `andi a3, a1, 1`**
- **Machine Code**: `0015f693`
- **Instruction Type**: I-type  
- **Opcode**: `0010011` (bits [6:0])  
- **Immediate**: `00000000000001` (1 in decimal)  
- **rs1**: `01011` (a1 = x11)  
- **funct3**: `111` (AND immediate)  
- **rd**: `00111` (a3 = x14)

### **10. Instruction: `beqz a3, 101f4 <__muldi3+0x14>`**
- **Machine Code**: `00068663`
- **Instruction Type**: B-type  
- **Pseudo-instruction**: `beqz` maps to `beq a3, zero, 101f4`  
- **Opcode**: `1100011` (bits [6:0])  
- **Immediate**: `00000000001100` (address offset for 101f4 in decimal)  
- **rs1**: `00111` (a3 = x14)  
- **rs2**: `00000` (zero = x0)  
- **funct3**: `000` (branch equal)

### **11. Instruction: `add a0, a0, a2`**
- **Machine Code**: `00c50533`
- **Instruction Type**: R-type  
- **Opcode**: `0110011` (bits [6:0])  
- **funct7**: `0000000` (bits [31:25])  
- **rs1**: `00110` (a2 = x12)  
- **rs2**: `00101` (a0 = x10)  
- **funct3**: `000` (add)  
- **rd**: `00101` (a0 = x10)

### **12. Instruction: `srli a1, a1, 0x1`**
- **Machine Code**: `00105593`
- **Instruction Type**: I-type  
- **Opcode**: `0010011` (bits [6:0])  
- **funct7**: `0000000` (bits [31:25])  
- **Immediate**: `00000000000001` (1 in decimal)  
- **rs1**: `01011` (a1 = x11)  
- **funct3**: `101` (shift right logical immediate)  
- **rd**: `01011` (a1 = x11)

### **13. Instruction: `slli a2, a2, 0x1`**
- **Machine Code**: `00161613`
- **Instruction Type**: I-type  
- **Opcode**: `0010011` (bits [6:0])  
- **funct7**: `0000000` (bits [31:25])  
- **Immediate**: `00000000000001` (1 in decimal)  
- **rs1**: `00110` (a2 = x12)  
- **funct3**: `001` (shift left logical immediate)  
- **rd**: `00110` (a2 = x12)

### **14. Instruction: `bnez a1, 101e8 <__muldi3+0x8>`**
- **Machine Code**: `fe0596e3`
- **Instruction Type**: B-type  
- **Pseudo-instruction**: `bnez` maps to `bne a1, zero, 101e8`  
- **Opcode**: `1100011` (bits [6:0])  
- **Immediate**: `11111111110000` (address offset for 101e8 in decimal)  
- **rs1**: `01011` (a1 = x11)  
- **rs2**: `00000` (zero = x0)  
- **funct3**: `001` (branch not equal)

### **15. Instruction: `ret`**
- **Machine Code**: `00008067`
- **Instruction Type**: I-type  
- **Opcode**: `1100011` (bits [6:0])  
- **funct3**: `000`  
- **rd**: `00000`  
- **rs1**: `00001` (ra = x1)
</details>
</details>  

### Screenshots
![Screenshot 2025-01-18 001724](https://github.com/user-attachments/assets/a0b4a656-40e2-4717-8150-50e5986d4aa4)
![3task](https://github.com/user-attachments/assets/89a44781-650c-410d-af9d-49a89bfea188)
![3task15](https://github.com/user-attachments/assets/e15d869f-ed43-4e8b-88c2-f203ecf0d315)



<details>
<summary><h2>Task 4<h2></summary>
<br>
A simulation environment (iverilog, gtkwave) is set up and the functional simulation of the RISC-V core Verilog netlist and testbench is run and the functional correctness of the core is checked by observing the output waveform.  

<h4>Verilog netlist code: </h4>  

[Verilog netlist code](https://github.com/Tech-Hades/samsung-riscv/blob/main/Task%204/Verilog%20netlist%20code)

<h4>Verilog testbench code: </h4>  

  [Verilog testbench code](https://github.com/Tech-Hades/samsung-riscv/blob/main/Task%204/Verilog%20testbench%20code)

<h4>GTKWave analyzer: </h4>  

![2 task4](https://github.com/user-attachments/assets/3276e64a-fc93-430a-879e-89f061404208)


### Output Waveforms

### **1. Instruction: `ADD R6, R2, R1`**  
![task4 123](https://github.com/user-attachments/assets/f72d1b67-3a9c-44a1-b497-d0e2675158e7)


### **2. Instruction: `SUB R7, R1, R2`**  
![task4 13-1](https://github.com/user-attachments/assets/deedf05f-7ae9-4607-849e-3581cfd3503e)



### **3. Instruction: `AND R8, R1, R3`**  
![task4 251](https://github.com/user-attachments/assets/4f5be13b-8115-4bf8-bb46-c61177d5d24d)


### **4. Instruction: `OR R9, R2, R5`**  
![task4 147](https://github.com/user-attachments/assets/b2f9a555-381a-421e-abc7-6a0e87c94d2c)



### **5. Instruction: `XOR R10, R1, R4`**  
![task4 245](https://github.com/user-attachments/assets/e4c165eb-a021-4240-a5a2-7a0a592be26a)



### **6. Instruction: `SLT R1, R2, R4`**  
![task4 451](https://github.com/user-attachments/assets/eeb4fc33-600a-43e5-b02f-1963a6c90385)



### **7. Instruction: `ADDI R12, R4, 5`**  
![task4 1229](https://github.com/user-attachments/assets/1f473649-7e26-4fd8-be11-6910c91d4d56)


### **8. Instruction: `BEQ R0, R0, 15`**  
![task4 25 11](https://github.com/user-attachments/assets/26408669-726b-4142-b209-b8bfe7b427b7)



### **9. Instruction: `BNE R0, R1, 20`**  
![task4 4 27](https://github.com/user-attachments/assets/0e35cf92-8acd-4d56-86a9-80505366b94d)



### **10. Instruction: `SLL R15, R1, R2`**  
![task4 0 xx 3](https://github.com/user-attachments/assets/e5e1d5ed-bfce-4999-bb2a-aa97a7b681bb)





