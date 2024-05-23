EXP-1

Date:

                     SIMULATION OF LOGIC GATES ,ADDERS AND SUBTRACTORS
                                               
AIM:
To simulate Logic Gates ,Adders and Subtractors using Vivado 2023.2.

APPARATUS REQUIRED:
VIVADO 2023.2


PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

LOGIC GATES LOGIC DIAGRAM:
![301405876-ee17970c-3ac9-4603-881b-88e2825f41a4](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/47efbcee-b1a0-4e29-93d0-661ea1e42f80)


 VERILOG CODE
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
OUTPUT WAVEFORM

![332093072-1dc5e80a-a438-4238-bbad-3dc2c359d995](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/48f566c2-b2cc-4c39-bd8f-00114e48815d)


HALF ADDER LOGIC DIAGRAM
![332093065-94f7fc2a-9cc1-48c1-a6fe-89f8b169c594](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/ba0aa8ac-651d-486d-9c89-1013bda36c7a)


VERILOG CODE
```
module half_adder(a,b,sum,carry);

input a,b;

output sum,carry;

xor g1(sum,a,b);

and g2(carry,a,b);

endmodule
```
OUTPUT WAVEFORM
![332092992-cc5977a8-a641-44be-a45c-60d5a1d16fd5](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/8dfda6b6-a7fd-4cd4-9582-73b6a9cc12c4)


FULL ADDER LOGIC DIAGRAM
![332093001-d63fd6a8-4ea4-407b-8f52-dd8414660634](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/c17080d3-851b-4a5d-920b-1b2b3d050db0)


VERILOG CODE
```
module fulladder(a,b,c,sum,carry);

input a,b,c;

output sum,carry;

wire w1,w2,w3;

xor(w1,a,b);

xor(sum,w1,c);

and(w2,w1,c);

and(w3,a,b);

or(carry,w2,w3);

endmodule
```
OUTPUT WAVEFORM
![332092947-942f02d4-7d08-4afc-a387-f7e297d65841](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/00b0dfae-f184-4819-bf3c-191f53f044f7)


HALF SUBTRACTOR LOGIC DIAGRAM
![332092958-7ba69920-2eb4-48ee-ab02-b09250f4422f](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/d15b778b-13e5-4ad7-b0e2-88a53c4f8112)


VERILOG CODE
```
module halfsub(a,b,diff,borrow);

input a,b;

output diff,borrow;

xor(diff,a,b);

and(borrow,~a,b);

endmodule
```
OUTPUT WAVE
![332092839-9f6d3247-62b7-48b3-bd64-523a62861f32](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/d81e4b3f-f92e-4bb7-964b-e381f84a9a22)


FORM


FULL SUBTRACTOR LOGIC DIAGRAM
![332092871-63495b96-7ba7-4303-8433-21482f32d75a](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/11212aab-184c-4c88-94e6-85f5225d0e24)



VERILOG CODE
```
module fs(a,b,bin,d,bout);

input a,b,bin;

output d,bout;

wire w1,w2,w3;

xor(w1,a,b);

xor(d,w1,bin);

and(w2,~a,b);

and(w3,~w1,bin);

or(bout,w3,w2);

endmodule
```
OUTPUT WAVEFORM
![332092762-8c298efc-9db5-4777-be55-a7e8ac97cc7d](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/3b94daa2-5dac-4d5e-9605-0e323ccb6e84)



RIPPLE CARRY ADDER LOGIC DIAGRAM
![332092772-c9ecbcee-ba64-49b3-9b8f-f3eb26a8d323](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/3c15f8ed-b661-4a91-9045-30036e68db40)



VERILOG CODE
```
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule

module rca_8bit(a,b,cin,s,cout);
input [7:0]a,b;
input cin;
output [7:0]s;
output cout;
wire [7:1]w;
fulladder f1(a[0], b[0], cin, s[0], w[1]);
fulladder f2(a[1], b[1], w[1], s[1], w[2]);
fulladder f3(a[2], b[2], w[2], s[2], w[3]);
fulladder f4(a[3], b[3], w[3], s[3], w[4]);
fulladder f5(a[4], b[4], w[4], s[4], w[5]);
fulladder f6(a[5], b[5], w[5], s[5], w[6]);
fulladder f7(a[6], b[6], w[6], s[6], w[7]);
fulladder f8(a[7], b[7], w[7], s[7], cout);
endmodule
```
OUTPUT WAVEFORM
![332092724-90430024-8e3b-4c43-95a0-3569f1dc30e2](https://github.com/jaggu654/VLSI-LAB-EXP-1/assets/167850134/da74831d-8844-428f-a202-7dd9ad4e30fd)


RESULT:

       simulation of Logic Gates ,Adders and Subtractors using Vivado 2023.2 is verified.
