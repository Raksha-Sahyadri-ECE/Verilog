# D Flip-Flop (D-FF) in Verilog

This module implements a **positive-edge triggered D Flip-Flop** with an enable signal (`En`). The D Flip-Flop stores the input value `D` on the rising edge of the clock, only when `En` is high.

- **Inputs:**
  - `clock` – Clock signal (positive edge triggered)
  - `En` – Enable signal
  - `D` – 1-bit data input

- **Output:**
  - `Q` – 1-bit stored output
