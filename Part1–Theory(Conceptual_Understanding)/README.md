



# Week 2 – BabySoC Fundamentals & Functional Modelling  

This week focuses on building a strong understanding of **System-on-Chip (SoC) fundamentals** and practicing **functional modelling** of the BabySoC using simulation tools such as Icarus Verilog and GTKWave.  

The BabySoC is a simplified open-source SoC model built using three major components:  
- **RVMYTH RISC-V CPU core**  
- **Phase-Locked Loop (PLL)** for clock generation  
- **10-bit Digital-to-Analog Converter (DAC)**  

This design provides an effective way to study how digital and analog blocks interact, while also learning the functional modelling techniques needed before diving into RTL synthesis and physical design.  

---

## What is a System-on-Chip (SoC)?  

A **System-on-Chip (SoC)** is an integrated circuit (IC) that consolidates the essential elements of a complete computer system onto a single silicon die. Instead of relying on multiple chips for the CPU, memory, input/output controllers, and other processing units, an SoC brings them all together, thereby reducing size, power consumption, and cost.  

Key features of SoCs:  
- Integration of **processor, memory, and peripherals**.  
- High performance with reduced communication delays between components.  
- Optimized for **power efficiency** and **scalability**.  
- Designed for a wide variety of applications, from mobile phones and IoT devices to high-performance computing.  
![SoC-Block](https://github.com/user-attachments/assets/54b5e8f9-f03d-4b53-a535-859360589119)  
SoCs are used in almost every modern device, including smartphones, tablets, embedded controllers, and advanced processors like Apple’s M1 or Qualcomm Snapdragon.  

---

## Components of a Typical SoC  

A typical SoC integrates the following:  

- **CPU (Processor)**: The brain of the SoC responsible for executing instructions, performing arithmetic, and controlling data flow. In BabySoC, the CPU is implemented using the RVMYTH RISC-V core.  

- **Memory**: Includes RAM for temporary storage and ROM or flash for permanent program storage. On-chip memory ensures fast access by reducing the need for external memory.  

- **Peripherals**: Interfaces to external devices such as I/O ports, timers, UART, SPI, and other controllers.  

- **Interconnect**: The communication backbone, often implemented as a bus system or a Network-on-Chip (NoC). It connects the CPU, memory, and peripherals for seamless data transfer.  

- **Specialized Blocks**: Depending on the target application, SoCs may include GPUs, DSPs, power management systems, and machine learning accelerators.  

This tightly coupled integration makes SoCs highly efficient and powerful, suitable for real-time, low-power, and cost-sensitive applications.  

---

## Why BabySoC?  

The **BabySoC (VSDBabySoC)** is a simplified model of a real-world SoC, designed for learning and educational purposes. It uses minimal building blocks while retaining essential elements of a modern SoC. This makes it easier to simulate, analyze, and understand SoC design at a fundamental level.  



This structure helps understand both **digital processing** and **analog interfacing**, making it a perfect entry-level SoC.  

![VSDBabySoC Block](https://github.com/user-attachments/assets/38253bb7-b658-496d-a043-15402219e089)  

BabySoC integrates three major IP blocks:  

- **RVMYTH (RISC-V CPU)**: Executes a subset of the RISC-V instruction set. It provides the digital processing capability and allows experimentation with registers, instructions, and basic computation.  

- **PLL (Phase-Locked Loop)**: Generates a clean and stable clock signal from an input source. Clock management is critical in SoC design, and the PLL ensures synchronization across digital and analog domains.  

- **DAC (10-bit Digital-to-Analog Converter)**: Converts digital values (from registers like r17 in the CPU) into analog signals, demonstrating mixed-signal interfacing.  

The BabySoC demonstrates how different subsystems interact in a controlled environment, making it an ideal stepping stone before working on larger and more complex SoCs.  

---

## SoC Design Flow  

Designing an SoC follows a structured multi-step flow:  

1. **Specification and Architecture Definition**  
   Define the SoC’s purpose, the CPU architecture, the memory capacity, and the peripherals.  

2. **RTL Design**  
   Hardware description languages like Verilog or VHDL are used to describe the functional behavior of the system.  

3. **Functional Modelling**  
   Before synthesis and physical implementation, the design is tested at a behavioral level. This helps validate correctness, integration, and early performance.  

4. **Logic Synthesis**  
   RTL is converted into a gate-level netlist using a standard cell library.  

5. **Physical Design**  
   Placement, routing, and optimization for timing, power, and area.  

6. **Fabrication and Testing**  
   The chip is taped-out and manufactured, followed by functional and performance validation on silicon.  

BabySoC focuses on the **functional modelling** stage, which is crucial for identifying and fixing issues early.  

---

## Components of BabySoC in Detail  

### RVMYTH – RISC-V CPU Core  
The CPU is based on the **RV32I instruction set architecture**. It contains general-purpose registers and control logic to execute basic instructions. In BabySoC, specific registers such as r17 are updated in loops to test functional interactions with the DAC. This provides a foundation for understanding how data flows within a CPU and between subsystems.  

### PLL – Phase-Locked Loop  
The PLL stabilizes the input clock signal by synchronizing it with a reference. Without a PLL, SoCs would face clocking issues such as jitter and skew, leading to incorrect operation of sequential circuits. In BabySoC, the PLL ensures that the CPU and DAC both operate on a synchronized and reliable clock.  

### DAC – Digital-to-Analog Converter  
The DAC converts 10-bit digital outputs from the CPU into analog signals. This is critical in applications like audio, video, and control systems. In BabySoC, the DAC demonstrates the transition from digital processing (CPU) to analog interfacing. The generated analog values are written to an output file, which can then be analyzed to study the DAC’s behavior.  

---

## Role of Functional Modelling  

Functional modelling is the process of simulating the **behavioral description of a system** before moving into RTL synthesis or physical design. It ensures that the system operates correctly under different scenarios without incurring the cost and complexity of synthesis and place-and-route.  

Advantages of functional modelling:  
- Detect design errors early in the flow.  
- Validate the integration of multiple IP blocks such as CPU, PLL, and DAC.  
- Reduce the number of silicon re-spins by debugging at an abstract level.  
- Provide confidence that the RTL matches the intended specification.  

In BabySoC, functional modelling was carried out using **Icarus Verilog for simulation** and **GTKWave for waveform analysis**. The simulations confirmed that:  
- The PLL generated a stable clock after reset.  
- The RVMYTH CPU correctly updated registers in loop execution.  
- The DAC converted digital values into corresponding analog signals written into the output.  

---

## Learnings from Week 2  

- Developed a strong understanding of what an SoC is and its essential components.  
- Studied the structure and design flow of SoCs, from specification to fabrication.   
- Practiced functional modelling using open-source tools to verify SoC behavior at the system level.  
- Observed how analog and digital domains interact through the DAC.
  
---


