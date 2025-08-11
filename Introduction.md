## Introduction to the 1010 Non-Overlapping Mealy Sequence Detector

This project implements a digital circuit that detects the binary sequence **"1010"**. The design uses a **Mealy finite state machine (FSM)** and operates on a **non-overlapping** principle.

### Mealy Finite State Machine (Mealy FSM)

In a Mealy model, the output depends on both the current state and the current input. This allows the system to produce an output immediately upon receiving a specific input, which is more efficient and often has lower latency compared to the Moore model.



### Non-Overlapping Principle

This detector adheres to the non-overlapping principle. This means that once the **"1010"** sequence is successfully detected, the machine resets to its initial state to wait for a completely new sequence. It does not use any part of the detected sequence as a prefix for the next one. For example:

- For the input sequence `...1010**1010**...`, the detector will output a detection signal twice.
- However, for the input sequence `...1010**10**...`, it will only output a detection signal for the first sequence and ignore the subsequent `10` prefix.

### Project Goal

The primary goal of this project is to provide a clear and efficient implementation of a **"1010"** sequence detector using the principles of a non-overlapping Mealy FSM. This repository includes the Verilog/VHDL source code and the state diagram, which clearly illustrate the circuit's functionality.
