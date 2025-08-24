# Basic Computer Circuit with Custom Instructions

This project implements a **basic computer architecture** with support for **six new instructions**, showcasing how instructions are stored, decoded, and executed using **RAM**, **ROM**, and **micro-operations**.  

It demonstrates fundamental concepts of **computer organization**, **instruction set design**, and **control logic mapping** for a simple CPU.

---

## System Architecture

### RAM
- Stores **instructions**.
- Size: **4096 x 16** (2¹² memory words, each 16 bits).

### ROM
- Stores **micro-operations** for control logic.
- Size: **128 x 12** (2⁷ memory words, each 12 bits).

### Instruction Format
Each instruction is defined by an **opcode** (3 bits) and operands.  
Mapping procedure assigns opcode bits into the **Control Address Register (CAR)**.

---

## Implemented Instructions

| Opcode | Instruction | Operation                          |
|--------|-------------|------------------------------------|
| 000    | NOR         | `AC ← (AC + DR)’`                 |
| 001    | NOTDR       | `DR ← DR’`                        |
| 010    | MUL         | `AC ← (AC * DR)`                  |
| 011    | XOR         | `AC ← (AC ^ DR)`                  |
| 100    | COPY        | `AC ← DR`                         |
| 101    | CLRDR       | `DR ← 0`                          |

---

## Micro-Operations in ROM
- Each ROM word = **12 bits**, divided as:
  - `Destination (bits 9–11)`
  - `Source-2 (bits 6–8)`
  - `Source-1 (bits 3–5)`
  - `Operation (bits 0–2)`

This mapping defines how data moves between registers (`AR`, `AC`, `DR`, `Memory`) and how operations are executed.

---

## Mapping Procedure
- **Opcode (3 bits)** is mapped into the **Control Address Register (CAR)**.
- CAR bits:
  - `CAR(0,1,2,6) ← 0`
  - `CAR(3,4,5) ← Opcode`
- This ensures each instruction has a unique mapping to its micro-operations in ROM.

---

## Example Destinations, Sources, and Operations
- **Destinations:** `NOP`, `AR`, `AC`, `DR`, `CLRDR`
- **Sources:** `Memory`, `AR`, `AC`, `DR`
- **Operations:** `NOR`, `NOT`, `MUL`, `XOR`, `COPY`

---

## Project Significance
- Demonstrates how **new instructions** can be integrated into a CPU.  
- Provides a hands-on example of **RAM/ROM interaction** in computer architecture.  
- Useful for **learning CPU design, control units, and instruction mapping**.  

---

## About This Project
A simplified model of a **basic computer system** that introduces new instructions, defines their **opcodes, micro-operations, and control mappings**, and simulates their execution with RAM and ROM.  
It bridges the gap between **digital logic design** and **instruction set architecture (ISA)**.
