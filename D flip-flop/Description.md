# D Flip-Flop (D-FF) in Verilog

This module implements a **positive-edge triggered D Flip-Flop** with an enable signal (`En`). The D Flip-Flop stores the input value `D` on the rising edge of the clock, only when `En` is high.

- **Inputs:**
  - `clock` – Clock signal (positive edge triggered)
  - `En` – Enable signal
  - `D` – 1-bit data input

- **Output:**
  - `Q` – 1-bit stored output


## Design code:
module d_flipflop_with_enable(clock,En,D,Q);

  input clock, En,D;
  
  output reg Q = 1'b0;

  always @(posedge clk)
  begin
  
    if (En)
    
      Q <= D;
      
    else
    
      Q <= Q;
      
  end

endmodule

## Testbench:
module d_flipflop_test();

  reg clk, en, d;
  
  wire q;

  d_flipflop uut(.clock(clk), .En(en), .D(d), .Q(q));

  initial
  begin
    $dumpfile("d_flipflop.vcd");
    
    $dumpvars(0, d_flipflop_test);
    
    clk = 1'b0;
    
    forever #5 clk = ~clk;
    
  end

  initial begin
  
    en = 1'b0; d = 1'b0;
    
    #10 en = 1'b1; d = 1'b0;
    
    #10 en = 1'b0; d = 1'b1;
    
    #10 en = 1'b1; d = 1'b1;
    
    #10 $finish;
    
  end
  
endmodule
