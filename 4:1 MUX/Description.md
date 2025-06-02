# 4:1 MUX
A 4:1 MUX selects one of four 1-bit inputs (I[0], I[1], I[2], I[3]) based on a 2-bit select line S.

- When S = 2'b00, the output is I[0]
- When S = 2'b01, the output is I[1]
- When S = 2'b10, the output is I[2]
- When S = 2'b11, the output is I[3]

This design can be implemented using a case statement or nested if-else conditions in Verilog.

## Design code:
module mux_4to1(I, S, Y);

  input [3:0] I;
  
  input [1:0] S;   
  
  output reg Y;
         
  always @(S or I)
  
    begin
    
      case (S)
      
        2'b00: Y = I[0];
        
        2'b01: Y = I[1];
        
        2'b10: Y = I[2];
        
        2'b11: Y = I[3];
        
      endcase
      
    end
    
endmodule

## Testbench:
module mux_4to1_test();

  reg [3:0] i;
  
  reg [1:0] s; 
  
  wire y;
  
  mux_4to1 uut(.I(i), .S(s), .Y(y));
  
  initial
  
  begin
  
    $dumpfile("mux_4to1.vcd");
    
    $dumpvars(0, mux_4to1_test);
    
    
    i = 4'b1010;
    
    s = 2'b00;
    
    #10 s = 2'b01;
    
    #10 s = 2'b10;
    
    #10 s = 2'b11;
    
    #10 $finish;
    
  end
  
endmodule



