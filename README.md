# 🔀 16-to-1 Multiplexer using 4-to-1 MUX Modules (Verilog)

## 📘 Overview

This project implements a **16-to-1 multiplexer (MUX)** using **4-to-1 MUX submodules** in Verilog HDL. The design demonstrates **hierarchical modeling**, where smaller modules are used as building blocks to create a larger and more complex design.

---

## 🧩 Project Structure

```
Bb_MUX16_to_1/
├── MUX_16_to_1_BB.v       # Top-level module (16-to-1 MUX)
├── MUX_16_to_1_tb.v       # Testbench for waveform simulation
└── README.md              # Project documentation
```

---

## ⚙️ Design Description

### 🧠 Top Module: `MUX_16_to_1_BB`

* Implements a **16:1 multiplexer**.
* Uses four 4:1 MUX modules (`mux_4_to_1`) to reduce complexity.
* Selection lines `sel[3:0]` choose which of the 16 inputs is passed to output `out`.
* Hierarchical connections:

  * `M0`–`M3` handle groups of 4 inputs each.
  * `M4` selects the final output from the intermediate results.

### 🔹 4-to-1 MUX Module: `mux_4_to_1`

* Inputs: `in[3:0]`
* Select lines: `sel[1:0]`
* Output: `out`
* Implements direct selection using `assign out = in[sel];`

---

## 🧪 Testbench: `MUX_16_to_1_tb.v`

* Generates stimulus to test all selection lines (`sel[3:0]`).
* Uses `$monitor` to display `Time`, `sel`, `in`, and `out` values.
* Loops through all 16 select combinations.
* Example input vectors are applied to verify correct functionality.

### Example Simulation Snippet

```
in = 16'b0000_0001_0010_0100;
sel = 4'b0000;
repeat (16) begin
    #10 sel = sel + 1;
end
```

* Can be run in simulators like **Xilinx ISE**, **ModelSim**, or **eSim**.

* ### 🔸 RTL Capture

![Output Capture](Capture.PNG)

### 🔸 RTL Capture

![Output Capture](Capture.PNG)

### 🔸 RTL Capture

![Output Capture](Capture.PNG)

---

## 📊 Waveform Verification

1. Compile both `MUX_16_to_1_BB.v` and `MUX_16_to_1_tb.v`.
2. Run simulation.
3. Observe `out` waveform corresponding to all `sel` values.
4. Verify that output matches the selected input.

---

## 📝 Notes

* Ensure the `timescale` directive is correctly written for your simulator:

```verilog
`timescale 1ns / 1ps
```

* Module and file names must match exactly.
* Hierarchical design allows easy expansion to larger multiplexers.

---

## 🎯 Key Learning Points

* Hierarchical design in Verilog.
* Multiplexer implementation and testing.
* Testbench creation for waveform generation.
* Verification of combinational logic using simulation.

---

## 📂 References

* Verilog HDL Reference Manual
* Xilinx ISE / Vivado Documentation
* FPGA and Digital Design textbooks
