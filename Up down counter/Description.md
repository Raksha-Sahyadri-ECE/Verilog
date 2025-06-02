# 4-Bit Up-Down Counter in Verilog

This module implements a **4-bit synchronous up-down counter**. The direction of counting is controlled by an input signal `M` — it counts **up** when `M = 0` and **down** when `M = 1`.

- **Inputs:**
  - `clock` – Clock signal (positive edge triggered)
  - `reset` – Asynchronous active-low reset
  - `M` – Mode control: 0 for count up, 1 for count down

- **Output:**
  - `Count` – 4-bit counter value
