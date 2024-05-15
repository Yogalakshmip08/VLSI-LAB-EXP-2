SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

VERILOG CODE:
DECODER 3 TO 8:
```
module decoder1(a,y);
input [2:0]a;
output[7:0]y;
and(y[0],~a[2],~a[1],~a[0]);
and(y[1],~a[2],~a[1],a[0]);
and(y[2],~a[2],a[1],~a[0]);
and(y[3],~a[2],a[1],a[0]);
and(y[4],a[2],~a[1],~a[0]);
and(y[5],a[2],~a[1],a[0]);
and(y[6],a[2],a[1],~a[0]);
and(y[7],a[2],a[1],a[0]);
endmodule
```
OUTPUT:
![WhatsApp Image 2024-04-22 at 13 47 14_c806feda](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/ed73d8c1-6f46-44f4-a315-a8ccd69d78b1)
![WhatsApp Image 2024-04-22 at 14 52 00_2c74fe1b](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/6efb030f-8a21-442f-ae61-3e10af4b2266)

VERILOG CODE:
DEMULTIPLEXER 1 TO 8:
```
module demux_8(s,a,y);
input [2:0]s;
input a;
output [7:0]y;
and(y[0],a,~s[2],~s[1],~s[0]);
and(y[1],a,~s[2],~s[1],s[0]);
and(y[2],a,~s[2],s[1],~s[0]);
and(y[3],a,~s[2],s[1],s[0]);
and(y[4],a,s[2],~s[1],~s[0]);
and(y[5],a,s[2],~s[1],s[0]);
and(y[6],a,s[2],s[1],~s[0]);
and(y[7],a,s[2],s[1],s[0]);
endmodule
```
OUTPUT:
![WhatsApp Image 2024-04-22 at 14 52 22_bff78932](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/c8ae23bf-a2ac-4cf3-ab02-e55ed3d4ae52)
![WhatsApp Image 2024-04-22 at 14 52 29_ea18a047](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/75ddac4b-10fc-4bf3-a6fb-ab81cfe01a0d)

VERILOG CODE:
ENCODER 8 TO 3:
```
module encoder(a,y);
input [7:0]a;
output[2:0]y;
or(y[2],a[6],a[5],a[4],a[3]);
or(y[1],a[6],a[5],a[2],a[1]);
or(y[0],a[6],a[4],a[2],a[0]);
endmodule
```
OUTPUT:
![WhatsApp Image 2024-04-22 at 14 52 35_a103d148](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/bd6b0103-cf1c-4565-bdf2-a50515bae2c7)
![WhatsApp Image 2024-04-22 at 14 52 42_9d12c451](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/d0d6be44-40fd-4cc3-9126-adc2a080b28e)

VERILOG CODE:
MAGNITUDE COMPARATOR:
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
 begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
```
OUTPUT:
![WhatsApp Image 2024-04-22 at 14 52 50_552d6e88](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/fbbae9ae-5dc2-4fae-b8e4-24dc6e23ac4c)
![WhatsApp Image 2024-04-22 at 14 52 55_fb7ff0d7](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/ed099ad9-cc82-4a81-98b9-0b4f927d34c4)

VERILOG CODE:
MULTIPLEXER:
```
module mux(s,c,a);
input [2:0]s;
input [7:0]a;
wire [7:0]w;
output c;
and(w[0],a[0],~s[2],~s[1],~s[0]);
and(w[1],a[1],~s[2],~s[1],s[0]);
and(w[2],a[2],~s[2],s[1],~s[0]);
and(w[3],a[3],~s[2],s[1],s[0]);
and(w[4],a[4],s[2],~s[1],~s[0]);
and(w[5],a[5],s[2],~s[1],s[0]);
and(w[6],a[6],s[2],s[1],~s[0]);
and(w[7],a[7],s[2],s[1],s[0]);
or (c,w[0],w[1],w[2],w[3],w[4],w[5],w[6],w[7]);
endmodule
```
OUTPUT:

![WhatsApp Image 2024-04-22 at 14 53 11_f0478544](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/60409f84-3c06-4581-a196-75fbc8c43888)

![WhatsApp Image 2024-04-22 at 14 53 24_f8a24744](https://github.com/Yogalakshmip08/VLSI-LAB-EXP-2/assets/161303457/ffc879df-28e4-443c-ab06-6cb0c30b6b9a)

RESULT:

The simulation and synthesis of Logic Gates, Adders and Subtractor using Vivado Software are successfully verified







