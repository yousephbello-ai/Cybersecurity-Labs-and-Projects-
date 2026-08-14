# Inside a Computer System - Writeup & Notes

##  Room Overview
* **Module:** Inside a Computer System
* **Platform:** TryHackMe
* **Category:** Core Fundamentals / Systems Architecture


## Key Takeaways & Core Concepts

# 1. Computer Architecture & Components
* **CPU (Central Processing Unit):** The "brain" executing arithmetic/logic operations (ALU, Control Unit, Registers).
* **RAM & Cache:** High-speed volatile memory providing fast instruction access to minimize CPU latency.
* **Busses:** System pathways (Data, Address, Control) that move signals between hardware components.

# 2. Instruction Cycle (Fetch-Decode-Execute)
1. **Fetch:** Retrieve the instruction from RAM using the Program Counter (PC).
2. **Decode:** Decode the instruction in the Control Unit.
3. **Execute:** Perform the operation (ALU/Registers) and store the output.

# 3. Relevance to Security
* **Memory Corruption:** Understanding stack/heap memory models is crucial for identifying buffer overflows.
* **Low-Level Analysis:** Helps in reading Assembly/Disassembly during malware analysis or reverse engineering.
