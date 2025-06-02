# 4:1 MUX
A 4:1 MUX selects one of four 1-bit inputs (I[0], I[1], I[2], I[3]) based on a 2-bit select line S.

- When S = 2'b00, the output is I[0]
- When S = 2'b01, the output is I[1]
- When S = 2'b10, the output is I[2]
- When S = 2'b11, the output is I[3]

This design can be implemented using a case statement or nested if-else conditions in Verilog.

