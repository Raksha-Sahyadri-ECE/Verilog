# 2:1 MUX
A 2:1 MUX selects between two 1-bit inputs (`A` and `B`) based on a select line `S`. When `S = 0`, the output is `A`; when `S = 1`, the output is `B`.

## Design code:
module mux_2to1(A, B, S, Y);

  input A, B, S;
  
  output reg Y;

  always @(*)
  
  begin
  
    if (S == 0)
    
      Y = A;
      
    else
    
      Y = B;
      
  end
  
endmodule

## Testbench:
module mux_2to1_test();

  reg A, B, S;
  
  wire Y;

  mux_2to1 uut(.A(A), .B(B), .S(S), .Y(Y));

  initial
  
  begin
  
    $dumpfile("mux_2to1.vcd");
    
    $dumpvars(0, mux_2to1_test);

    A = 0; B = 0; S = 0;
    
    #10 A = 0; B = 1; S = 0;
    
    #10 A = 1; B = 0; S = 1;
    
    #10 A = 1; B = 1; S = 1;

    #10 $finish;
  end
endmodule
