
# SIMULATION AND IMPLEMENTATION OF 4X1 MUX#
# AIM:
To design and simulate a 4:1 Multiplexer (MUX) using Verilog HDL in four different modeling styles—Gate-Level, Data Flow, Behavioral, and Structural—and to verify its functionality through a testbench using the Vivado 2023.1 simulation environment. The experiment aims to understand how different abstraction levels in Verilog can be used to describe the same digital logic circuit and analyze their performance.

# APPARATUS REQUIRED:
Vivado 2023.1

# Procedure

1.Launch Vivado Open Vivado 2023.1 by double-clicking the Vivado icon or searching for it in the Start menu.

2.Create a New Project Click on "Create Project" from the Vivado Quick Start window. In the New Project Wizard: Project Name: Enter a name for the project (e.g., Mux4_to_1). Project Location: Select the folder where the project will be saved. Click Next. Project Type: Select RTL Project, then click Next. Add Sources: Click on "Add Files" to add the Verilog files (e.g., mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.). Make sure to check the box "Copy sources into project" to avoid any external file dependencies. Click Next. Add Constraints: Skip this step by clicking Next (since no constraints are needed for simulation). Default Part Selection: You can choose a part based on the FPGA board you are using (if any). If no board is used, you can choose any part, for example, xc7a35ticsg324-1L (Artix-7). Click Next, then Finish.


3.Add Verilog Source Files In the "Sources" window, right-click on "Design Sources" and select Add Sources if you didn't add all files earlier. Add the Verilog files (mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.) and the testbench (mux4_to_1_tb.v).

4.Check Syntax Expand the "Flow Navigator" on the left side of the Vivado interface. Under "Synthesis", click "Run Synthesis". Vivado will check your design for syntax errors. If any errors or warnings appear, correct them in the respective Verilog files and re-run the synthesis.


5.Simulate the Design In the Flow Navigator, under "Simulation", click on "Run Simulation" → "Run Behavioral Simulation". Vivado will open the Simulations Window, and the waveform window will show the signals defined in the testbench.


6.View and Analyze Simulation Results The simulation waveform window will display the signals (S1, S0, A, B, C, D, Y_gate, Y_dataflow, Y_behavioral, Y_structural). Use the time markers to verify the correctness of the 4:1 MUX output for each set of inputs. You can zoom in/out or scroll through the simulation time using the waveform viewer controls.


7.Adjust Simulation Time To run a longer simulation or adjust timing, go to the Simulation Settings by clicking "Simulation" → "Simulation Settings". Under "Simulation", modify the Run Time (e.g., set to 1000ns).


8.Generate Simulation Report Once the simulation is complete, you can generate a simulation report by right-clicking on the simulation results window and selecting "Export Simulation Results". Save the report for reference in your lab records.


9.Save and Document Results Save your project by clicking File → Save Project. Take screenshots of the waveform window and include them in your lab report to document your results. You can include the timing diagram from the simulation window showing the correct functionality of the 4:1 MUX across different select inputs and data inputs.

10.Close the Simulation Once done, close the simulation by going to Simulation → "Close Simulation".

# Logic Diagram
![368836171-d4ab4bc3-12b0-44dc-8edb-9d586d8ba856](https://github.com/user-attachments/assets/22e17f8a-bc44-46a7-a604-fa0e1418c65a)


# Truth Table
![368836230-c850506c-3f6e-4d6b-8574-939a914b2a5f](https://github.com/user-attachments/assets/af5a88c8-239e-4ac5-aa1c-b9c9c86ca1b3)


# Verilog Code
#4:1 MUX Behavioral Implementation
~~~
module mux4_1(i,s,y);
input [3:0]i;
input[1:0]s;
output reg y;
always @(i,s)
case(s)
2'b00:y=i[0];
2'b01:y=i[1];
2'b10:y=i[2];
2'b11:y=i[3];
default:y=4'b0;
endcase
endmodule
~~~
# Testbench Implementation
~~~
module mux4_1tb;
reg [3:0]i;
reg [1:0]s;
wire y;
mux4_1 dut(i,s,y);
initial
begin
i=4'b1100;
s=2'b00;
#100
s=2'b01;
#100
s=2'b10;
#100
s=2'b11;
#100
$display("no value assigned");
end
endmodule
~~~
# Sample Output
![370662068-a3db5672-c48c-4c77-b738-05819970462e](https://github.com/user-attachments/assets/3e3a577b-31dc-4990-a9f1-887c269f372e)


# Conclusion:
In this experiment, a 4:1 Multiplexer was successfully designed and simulated using Verilog HDL across four different modeling styles: Gate-Level, Data Flow, Behavioral, and Structural. The simulation results verified the correct functionality of the MUX, with all implementations producing identical outputs for the given input conditions.
