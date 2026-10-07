


# 4-bit Arithmetic Logic Unit (ALU)

A 4-bit Arithmetic Logic Unit (ALU) designed and implemented using **Verilog HDL**.  
The project demonstrates fundamental digital design concepts including arithmetic operations, logic operations, shifting, and status flag generation.

## 📌 Project Overview

An Arithmetic Logic Unit is a fundamental component of a digital processor. It performs arithmetic and logical operations on binary data based on control signals.

In this project, a **4-bit ALU** is designed to perform eight different operations selected using a 3-bit control signal.

## ✨ Features

- 4-bit input operands
- 8 selectable operations
- Arithmetic operations
- Bitwise logical operations
- Left and right shift operations
- Carry flag generation
- Zero flag generation
- Combinational RTL design
- Verilog testbench for functional verification

## 🧩 ALU Operations

| ALU_Sel | Operation | Description |
|:------:|-----------|-------------|
| `000` | Addition | Adds A and B |
| `001` | Subtraction | Subtracts B from A |
| `010` | AND | Bitwise AND of A and B |
| `011` | OR | Bitwise OR of A and B |
| `100` | XOR | Bitwise XOR of A and B |
| `101` | NOT | Bitwise complement of A |
| `110` | Left Shift | Shifts A left by one bit |
| `111` | Right Shift | Shifts A right by one bit |

## 🔌 Inputs and Outputs

### Inputs

| Signal | Width | Description |
|--------|:-----:|-------------|
| `A` | 4-bit | First input operand |
| `B` | 4-bit | Second input operand |
| `ALU_Sel` | 3-bit | Operation selection signal |

### Outputs

| Signal | Width | Description |
|--------|:-----:|-------------|
| `Result` | 4-bit | Result of the selected operation |
| `Carry` | 1-bit | Carry/borrow-related status output |
| `Zero` | 1-bit | Indicates whether the result is zero |

## 🏗️ Design Architecture

```text
             ┌──────────────────┐
     A ─────►│                  │
             │                  │
     B ─────►│      4-bit       │─────► Result
             │       ALU        │
 ALU_Sel ───►│                  │─────► Carry
             │                  │─────► Zero
             └──────────────────┘