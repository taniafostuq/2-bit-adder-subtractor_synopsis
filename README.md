# 2-bit-adder-subtractor_synopsis
# 2-Bit Adder/Subtractor Design & Simulation

This repository contains the transistor-level schematic design, cell symbol creation, testbench setups, and transient response simulations for a **2-Bit Adder/Subtractor** implemented in Synopsys Custom Compiler using a 32nm PDK[cite: 14].

---

## 🛠️ Design Hierarchy & Architecture

The project is built modularly from fundamental CMOS logic gates up to a full 2-bit addition and subtraction architecture[cite: 14].

| Level | Module | Description |
| :--- | :--- | :--- |
| **Level 1** | **NAND Gate** | Transistor-level CMOS NAND schematic, symbol creation, and transient testbench[cite: 14]. |
| **Level 1** | **XOR Gate** | CMOS XOR schematic, symbol creation, and functional waveform verification[cite: 14]. |
| **Level 2** | **1-Bit Full Adder** | Constructed using instantiated NAND and XOR sub-blocks, verified via transient analysis[cite: 14]. |
| **Level 3** | **2-Bit Adder/Subtractor** | Hierarchical design cascading two 1-bit full adders with XOR gates for conditional bit inversion (`CIN0` control line for addition/subtraction)[cite: 14]. |

---

## 📐 Circuit Specifications & Sub-Modules

### 1. NAND Gate (`NAND`)
* **Components:** PMOS and NMOS transistor schematic (`w=0.2u`, `l=30nm`)[cite: 14].
* **Outputs:** Complementary AND output (`AnandB`)[cite: 14].
* **Verification:** Simulated with pulse inputs (`V1=1V`, `V2=0V`, `tr=10ps`) across a 4$\mu$s transient window[cite: 14].

### 2. XOR Gate (`XOR`)
* **Components:** Transistor-level XOR implementation utilizing complementary inputs (`Ai`, `Bi`)[cite: 14].
* **Outputs:** Exclusive-OR result (`AxorB`)[cite: 14].
* **Verification:** Validated using 4$\mu$s transient analysis under load capacitance (`C1=1pF`)[cite: 14].

### 3. 1-Bit Full Adder (`adder`)
* **Inputs:** Operands `A`, `B`, and carry-in `Cin`[cite: 14].
* **Outputs:** Sum (`A+B`) and carry-out (`Cout`)[cite: 14].
* **Structure:** Interconnected NAND and XOR logic symbol instances[cite: 14].
* **Verification:** Transient analysis run over 10$\mu$s to verify all binary input combinations[cite: 14].

### 4. 2-Bit Adder/Subtractor (`2bit_adder`)
* **Inputs:** 2-bit operand A (`A0`, `A1`), 2-bit operand B (`B0`, `B1`), and mode/carry-in control (`CIN0`)[cite: 14].
* **Outputs:** 2-bit result (`S0`, `S1`) and final carry-out (`Cout`)[cite: 14].
* **Operation:** 
  * `CIN0 = 0`: Operates as a standard 2-bit binary adder[cite: 14].
  * `CIN0 = 1`: Inverts operand B via XOR gates and adds 1 (2's complement subtraction)[cite: 14].
* **Verification:** Transient simulation run across 20$\mu$s stop time in PrimeSim[cite: 14].

---

## ⚙️ Simulation Toolchain & Environment

* **Schematic Editor:** Synopsys Custom Compiler[cite: 14]
* **Simulation Engine:** Synopsys PrimeSim / PrimeWave[cite: 14]
* **Waveform Viewer:** Synopsys WaveView[cite: 14]
* **Process Design Kit (PDK):** `SAED32nm_PDK_02_2024`[cite: 14]
