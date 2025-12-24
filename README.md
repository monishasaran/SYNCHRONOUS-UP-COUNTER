### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**
1.	Type the program in Quartus software.
2.	Compile and run the program.
3.	Generate the RTL schematic and save the logic diagram.
4.	Create nodes for inputs and outputs to generate the timing diagram.
5.	For different input combinations generate the timing diagram.




**PROGRAM**

module EXPR6(q, clk, reset); 
output [3:0] q;
input clk, reset;
T_FF tffo(q[0], clk, reset); 
T_FF tff1(q[1], q[0], reset); 
T_FF tff2(q[2], q[1], reset); 
T_FF tff3(q[3], q[2], reset); 
endmodule

module D_FF(q, d, clk, reset); 
output q;
input d, clk, reset;
reg q;
always @(posedge reset or negedge clk)
 if (reset)
q = 1'b0;
 else
q = d;
endmodule

module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); // not is Verilog-provided primitive. 
endmodule

Developed by:Monisha.S  RegisterNumber:25017984


**RTL LOGIC UP COUNTER**
<img width="1167" height="447" alt="Screenshot 2025-12-19 120211" src="https://github.com/user-attachments/assets/08f7c885-8c3d-4f2d-acb0-6dbb1d74f87b" />



**TIMING DIAGRAM FOR IP COUNTER**
<img width="1646" height="438" alt="Screenshot 2025-12-19 120437" src="https://github.com/user-attachments/assets/b286d88e-cc3c-45ac-b8f9-d0b0c7ee7cd9" />


**TRUTH TABLE**
<img width="867" height="434" alt="Screenshot 2025-12-24 194200" src="https://github.com/user-attachments/assets/89b9a981-6a24-4c72-82e1-3026b67a2924" />


**RESULTS**

Thus the 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables is verified.
