# Counter_4bit_up-down
**Aim:**

&emsp;&emsp;To write a verilog code for 4bit up/down counter and verify the functionality using Test bench.<br>

**Tools used for ASIC Flow:**

&emsp;&emsp;nclaunch- Used for Functional Simulation<br>
   
**Design Information and Bock Diagram:**

&emsp;&emsp;An up/down counter is a digital counter which can be set to count either from 0 to MAX_VALUE or MAX_VALUE to 0.<br>

&emsp;&emsp;The direction of the count(mode) is selected using a single bit input. The module has 3 inputs - clk, reset which is active high and a Up Or Down mode input.The output is Counter which is 4 bit in size.<br>

&emsp;&emsp;When Up mode is selected, counter counts from 0 to 15 and then again from 0 to 15.<br>

&emsp;&emsp;When Down mode is selected, counter counts from 15 to 0 and then again from 15 to 0.<br>

&emsp;&emsp;Changing mode doesn't reset the Count value to zero.<br>

&emsp;&emsp;You have to apply high value to reset, to reset the Counter output.<br>
 
![image](https://github.com/user-attachments/assets/efe1095e-989e-4005-b53b-e9dc50d4025c)

**Fig 1: 4 Bit Up/Down Counter**

**Creating a Work space :**

&emsp;&emsp;Create a folder in your name (Note: Give folder name without any space) and Create a new sub-Directory name it as Exp2 or counter_design for the Design and open a terminal from the Sub-Directory. 

**Functional Simulation:**

&emsp;&emsp;Invoke the cadence environment by type the below commands <br>

&emsp;&emsp;tcsh (Invokes C-Shell) <br>

&emsp;&emsp;source /cadence/install/cshrc (mention the path of the tools) <br>

&emsp;&emsp;(The path of cshrc could vary depending on the installation destination)<br>
      
&emsp;&emsp;After this you can see the window like below <br>

![image](https://github.com/user-attachments/assets/15177ef2-725b-4f4c-8ab5-e400084ed0a5)

**Fig 2: Invoke the Cadence Environment**


**Creating Source Code:**

&emsp;&emsp;In the Terminal, type gedit <filename>.v or <filename>.vhdl depending on the HDL Language you are to use (ex: 4b_up_downCount.v).<br>

&emsp;&emsp;A Blank Document opens up into which the following source code can be typed down.<br>

&emsp;&emsp;(Note : File name should be with HDL Extension)<br>

**Verilog code for 4-Bit Up-Down Counter:**


&emsp;&emsp;Use Save option or Ctrl+S to save the code or click on the save option from the top most right corner and close the text file.<br>

**Creating Test bench:**

&emsp;&emsp;Similarly, create your test bench using gedit <filename_tb>.v or <filename_tb>.vhdl to open a new blank document (4bitup_down_count_tb.v).<br>

**Test-bench code for 4-Bit Up-Down Counter:**


**To Launch Simulation tool**
&emsp;&emsp;linux:/> nclaunch -new&            // “-new” option is used for invoking NCVERILOG for the first time for any design<br>

&emsp;&emsp;linux:/> nclaunch&                 // On subsequent calls to NCVERILOG<br>

&emsp;&emsp;It will invoke the nclaunch window for functional simulation we can compile,elaborate and simulate it using Multiple step<br>

![image](https://github.com/user-attachments/assets/cd9afdf0-290b-4320-961c-b966748268d9)

**Fig 3: Setting Multi-step simulation**

&emsp;&emsp;Select Multiple Step and then select “Create cds.lib File” as shown in below figure<br>

&emsp;&emsp;Click the cds.lib file and save the file by clicking on Save option<br>

![image](https://github.com/user-attachments/assets/9c02f570-c422-44c1-8375-9ac00f46a5a0)

**Fig 4: cds.lib file Creation**

&emsp;&emsp;Save cds.lib file and select the correct option for cds.lib file format based on the  HDL Language and Libraries used.<br>

&emsp;&emsp;Select “Don’t include any libraries (verilog design)” from “New cds.lib file” and click on “OK” as in below figure<br>

&emsp;&emsp;We are simulating verilog design without using any libraries<br>

**Fig 5: Selection of Don’t include any libraries**

&emsp;&emsp;A Click “OK” in the “nclaunch: Open Design Directory” window<br>

&emsp;&emsp;A ‘NCLaunch window’ appears as shown in figure below<br>

&emsp;&emsp;Left side you can see the HDL files. Right side of the window has worklib and snapshots directories listed.<br>

&emsp;&emsp;Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation<br>

![WhatsApp Image 2024-10-05 at 9 31 05 AM](https://github.com/user-attachments/assets/39a61eb6-9c5b-4f7b-9592-82c632b32ba4)


**Fig 6: Nclaunch Window**

&emsp;&emsp;To perform the function simulation, the following three steps are involved Compilation, Elaboration and Simulation.<br>

**Step 1: Compilation:– Process to check the correct Verilog language syntax and usage** 

&emsp;&emsp;Inputs: Supplied are Verilog design and test bench codes <br>

&emsp;&emsp;Outputs: Compiled database created in mapped library if successful, generates report else error reported in log file <br>

**Steps for compilation:**

&emsp;&emsp;1. Create work/library directory (most of the latest simulation tools creates automatically)<br>
  
&emsp;&emsp;2. Map the work to library created (most of the latest simulation tools creates automatically)<br>
  
&emsp;&emsp;3. Run the compile command with compile options<br>

&emsp;&emsp;i.e Cadence IES command for compile: ncverilog +access+rwc -compile fa.v<br>

&emsp;&emsp;Left side select the file and in Tools : launch verilog compiler with current selection will get enable. Click it to compile the code <br>

&emsp;&emsp;Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation <br>

![WhatsApp Image 2024-10-05 at 9 31 05 AM](https://github.com/user-attachments/assets/fb63f3a1-8d35-4db2-9e94-4b1adebefbe9)


**Fig 7: Compiled database in worklib**

&emsp;&emsp;After compilation it will come under worklib you can see in right side window<br>

&emsp;&emsp;Select the test bench and compile it. It will come under worklib. Under Worklib you can see the module and test-bench. <br>

&emsp;&emsp;The cds.lib file is an ASCII text file. It defines which libraries are accessible and where they are located.<br>

&emsp;&emsp;It contains statements that map logical library names to their physical directory paths. For this Design, you will define a library called “worklib”<br>

**Step 2: Elaboration:– To check the port connections in hierarchical design** 

&emsp;&emsp;Inputs: Top level design / test bench Verilog codes<br>

&emsp;&emsp;Outputs: Elaborate database updated in mapped library if successful, generates report else error reported in log file <br>

&emsp;&emsp;Steps for elaboration – Run the elaboration command with elaborate options <br>

&emsp;&emsp;It builds the module hierarchy<br>
	
&emsp;&emsp;Binds modules to module instances<br>
  
&emsp;&emsp;Computes parameter values<br>
  
&emsp;&emsp;Checks for hierarchical names conflicts<br>
  
&emsp;&emsp;It also establishes net connectivity and prepares all of this for simulation<br>
    
&emsp;&emsp;After elaboration the file will come under snapshot. Select the test bench and simulate it. <br>

![image](https://github.com/user-attachments/assets/10539fba-4379-4be5-b2ae-7601a717e2c5)

**Fig 8: Elaboration Launch Option**

**Step 3: Simulation: – Simulate with the given test vectors over a period of time to observe the output behaviour.** 

&emsp;&emsp;Inputs: Compiled and Elaborated top level module name <br>

&emsp;&emsp;Outputs: Simulation log file, waveforms for debugging <br>

&emsp;&emsp;Simulation allow to dump design and test bench signals into a waveform <br>

&emsp;&emsp;Steps for simulation – Run the simulation command with simulator options<br>

![image](https://github.com/user-attachments/assets/e7d30f31-3e49-41ed-b292-41070d2d948c)

**Fig 9: Design Browser window for simulation**

![image](https://github.com/user-attachments/assets/aa886610-4cc7-400f-8477-aa52237042aa)

**Fig 10: Simulation Waveform Window**

![image](https://github.com/user-attachments/assets/fce258f9-dc5d-4ec3-a671-e2edd3834652)

**Fig 11: Simulation Waveform Window**


