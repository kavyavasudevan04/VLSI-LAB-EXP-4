# VLSI-LAB-EXP-4
# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

## APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA
**PROCEDURE:**

STEP:1  Launch the Vivado 2023.2 software.<br>
STEP:2  Click on “create project ” from the starting page of vivado.<br>
STEP:3  Choose the design entry method:RTL(verilog/VHDL).<br>
STEP:4  Crete design source  and give name to it and click finish.<br>
STEP:5  Write the verilog code and check the syntax.<br>
STEP:6  Click “run simulation” in the navigator window and click “Run behavioral simulation”.<br>
STEP:7  Verify the output in the simulation window.<br>




## SR Flipflop:
## Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)
**VERILOG CODE:**

```
module sr(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always @ (posedge clk)
begin 
if (rst==1)
q=1'b0;
else
begin
case ({s,r})
2'b00: q = q;
2'b01: q = 1'b0;
2'b10: q = 1'b1;
2'b11: q = 1'bx;
endcase
end
end
endmodule
```
**OUTPUT WAVEFORM:**

![Screenshot 2024-04-06 111951](https://github.com/TharunPR/VLSI-LAB-EXP-4/assets/117915125/ede889cf-b50f-480a-bfe5-920ad5c448c7)





## JK Flipflop:
## Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)
## VERILOG CODE:

```
module jk(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always @ (posedge clk)
begin 
if (rst==1)
q=1'b0;
else
begin
case ({j,k})
2'b00: q = q;
2'b01: q = 1'b0;
2'b10: q = 1'b1;
2'b11: q = ~q;
endcase
end
end
endmodule
```
**OUTPUT WAVEFORM:**

![Screenshot 2024-04-06 112629](https://github.com/TharunPR/VLSI-LAB-EXP-4/assets/117915125/b0ebf4b3-ac7f-4014-b56f-00d8dd10c65a)



## T Flipflop:
## Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)
## VERILOG CODE:

```
module t(t,clk,rst,q);
input t,clk,rst;
output reg q;
always @ (posedge clk)
begin 
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```
**OUTPUT WAVEFORM:**

![Screenshot 2024-04-06 111656](https://github.com/TharunPR/VLSI-LAB-EXP-4/assets/117915125/2f6d1a48-fd1a-40ff-8239-563a66f0564f)





## D Flipflop:
## Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)
## VERILOG CODE:

```
module d(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @ (posedge clk)
begin 
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```
**OUTPUT WAVEFORM:**

![Screenshot 2024-04-06 112153](https://github.com/TharunPR/VLSI-LAB-EXP-4/assets/117915125/80e530a3-9861-4c82-b359-4e49d05f4e7c)



## Counter:
## Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)
## Updown Counter:
## Verilog code:

```
module updowncounter(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always @(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if (updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```
**OUTPUT WAVEFORM:**

![Screenshot 2024-04-02 133943](https://github.com/TharunPR/VLSI-LAB-EXP-4/assets/117915125/47ae4a6f-afc3-4dc7-8ebf-acb7eb0c5bc4)
## Mod 10 Counter:
## VERILOG CODE:


```
module mod10counter(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always @(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```

**OUTPUT WAVEFORM:**

![Screenshot 2024-04-02 135812](https://github.com/TharunPR/VLSI-LAB-EXP-4/assets/117915125/a4534c02-50b7-48b1-92bc-3f98a861df1b)




  
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

VERILOG CODE

   <<< TYPE YOUR VERILOG CODE >>>

OUTPUT WAVEFORM
 <<< PASTE YOUR OUTPUT WAVEFORM >>>

RESULT


