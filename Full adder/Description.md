# 1-Bit Full Adder in Verilog

This repository demonstrates two implementations of a **1-bit Full Adder**:

- **Structural Design** using two half adders and an OR gate
- **Dataflow Design** using Verilog operators

## Full adder in dataflow:
### Design code:
module full_adder(A,B,C,Sum,Carry);

  input A,B,C;
  
  output Sum,Carry;
  
  assign Sum = A ^ B ^ C;
  
  assign Carry = (A&B) | (B&C) | (C&A);
  
endmodule

## Full adder using half adders
### Deesign code:
module full_adder(A,B,C,Sum,Carry);

  input A,B,C;
  
  output Sum,Carry;
  
  wire w1,w2,w3;
  
  half_adder HA1(A,B,w1,w2);
  
  half_adder HA2(w1,C,Sum,w3);
  
  or_gate OR(w3,w2,Carry);
  
endmodule

//Half adder

module half_adder(x,y,s,c);

  input x,y;
  
  output s,c;
  
  assign s = x ^ y;
  
  assign c = x & y;
  
endmodule

//OR gate

module or_gate(p,q,r);

  input p,q;
  
  output r;
  
  assign r = p | q;
  
endmodule

## Testbench:
module full_adder_test();

  reg a,b,c;
  
  wire sum,carry;
  
  full_adder uut(.A(a),.B(b),.C(c),.Sum(sum),.Carry(carry));
  
  initial
  
    begin
    
      $dumpfile("full_adder.vcd");
      
      $dumpvars(0,full_adder_test);
      
      a = 1'b0; b = 1'b0; c = 1'b0;
      
      #10 a = 1'b0; b = 1'b0; c = 1'b1;
      
      #10 a = 1'b0; b = 1'b1; c = 1'b0;
      
      #10 a = 1'b0; b = 1'b1; c = 1'b1;
      
      #10 a = 1'b1; b = 1'b0; c = 1'b0;
      
      #10 a = 1'b1; b = 1'b0; c = 1'b1;
      
      #10 a = 1'b1; b = 1'b1; c = 1'b0;
      
      #10 a = 1'b1; b = 1'b1; c = 1'b1;
      
      #10 $finish;
      
    end
    
endmodule





