# CPU Execution Flow

This document explains how software instructions
execute as electrical operations inside a CPU.

## Instruction Cycle

1. Fetch instruction from memory
2. Decode opcode in control unit
3. Execute via ALU or FPU
4. Write back results to registers

This will later be mapped to JVM bytecode execution.
