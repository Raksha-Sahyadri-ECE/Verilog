# 4-Bit Up-Down Counter in Verilog

This module implements a **4-bit synchronous up-down counter**. The direction of counting is controlled by an input signal `M` — it counts **up** when `M = 0` and **down** when `M = 1`.

- **Inputs:**
  - `clock` – Clock signal (positive edge triggered)
  - `reset` – Asynchronous active-low reset
  - `M` – Mode control: 0 for count up, 1 for count down

- **Output:**
  - `Count` – 4-bit counter value
 
## Design code:
  module counter_4bit(clock,reset,M,Count);
  
  input clock,reset,M;
  
  output reg [3:0] Count;      
  
  always@(posedge clock or posedge reset)
  
    begin
    
      if (reset == 0)
      
        Count = 4'b0000;
        
      else if (M == 0)
      
        Count = Count + 1;
        
      else
      
        Count = Count - 1;
        
    end
    
endmodule


## Test bench:

module counter_4bit_test();

  reg clk,rst,m;
  
  wire [3:0] count; 
  
  counter_4bit uut(.clock(clk),.reset(rst),.M(m),.Count(count));
  
  initial
  
      begin
      
      clk = 1'b0;
      
      forever #5 clk = ~clk;
      
      end
      
      initial
      
        begin
        
          rst = 1'b0;
          
          #10 rst = 1'b1;
          
        end
  
      initial
      
        begin
        
          m = 1'b0;
          
          #100 m = 1'b1;
          
          #200 $finish;
          
    end
  
  
  initial 
  
    begin
    
      $dumpfile("counter_4bit.vcd");
      
      $dumpvars(0,counter_4bit_test);
      
    end
    
endmodule


