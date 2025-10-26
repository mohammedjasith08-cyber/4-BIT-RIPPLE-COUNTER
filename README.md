# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

/* write all the steps invloved */

**PROGRAM**
// Assign internal register to output
assign q = q_int;

always @(posedge clk or posedge reset) begin
    if (reset) 
        q_int[0] <= 1'b0; // Reset the first bit to 0
    else 
        q_int[0] <= ~q_int[0]; // Toggle the first bit on clock edge
end

// Generate the other flip-flops based on the output of the previous one
genvar i;
generate
    for (i = 1; i < 4; i = i + 1) begin : ripple
        always @(posedge q_int[i-1] or posedge reset) begin
            if (reset) 
                q_int[i] <= 1'b0; // Reset the bit to 0
            else 
                q_int[i] <= ~q_int[i]; // Toggle the bit on clock edge of previous stage
        end
    end
endgenerate

/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

 Developed by:Mohammed Jashith.j RegisterNumber:25011638
*/

**RTL LOGIC FOR 4 Bit Ripple Counter**
<img width="963" height="332" alt="image" src="https://github.com/user-attachments/assets/8d279c91-ec02-4bd4-8c8a-6ebefb2b056f" />

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
<img width="1068" height="250" alt="image" src="https://github.com/user-attachments/assets/271cdc7b-70d2-4548-9ff5-ba2432690c87" />


**RESULTS**
