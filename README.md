# RTL2GDS-flow
Mixed signal RISC-V based SOC Physical design implemantation using open source tools
DAY-1
RISC-V based SOC design picorv32 Synthesis using yosys, follow the below steps to get RTL in the form of gate level netlist.
open the VM terminal as shown below

<img width="640" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/5cb1b378-7f8a-46ef-bbb8-b236132d4b56">

Then go to following directory-
Desktop/work/tools/openlane_working_dir/openlane

<img width="622" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/3d32c46e-aa39-437b-90d1-da671e9ac14e">
Type command "docker" on the terminal
Then run the below command to invoke the openlane tool 
"./flow.tcl -interactive" 
The Screenshot for the above step is depicted after running above command:

<img width="632" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/3c1060e3-624b-4087-bad4-fab9b9332c4e">

As well as package and design prep command to create the run directory as mention below:
package require openlane 0.9
prep -design picorv32a
The Screenshot for the above step is depicted after running above command:

![Uploading image.png

Enter the the below command to run the synthesis using yosys and ABC syntheis tools
"run_synthesis"
The Screenshot for the above step is depicted after running above command:
Now we can see the total negative slack, worst negative slack

<img width="636" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/bd159926-8533-4307-877e-a435aa58912f">

Task : Calculate the raito between D flip flop to total cells presennt in the netlist
We can see the many more parameter like number of flip flops and gates present in netlist as shown below:

<img width="634" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/636017be-9e0f-41e5-812f-1e241636c93a">

we can see out of 14876 cells, total 1613 dfxtp_2 (D flip-flop) present in the netlist
so the ratio will come as 
1613/14876 = 0.18642, approx 0.8 percentage of total cells

DAY-2

We will move forward for PNR flow started with Floorplanning
Floorplanning is the process of creating core area, specifying core to I/O boundary spacing, standard cell rows, placing I/O pins, placing macros using macro guidelines and adding placement blockages and halo.
The PPA of the design at later stages depends upon the quality of a floorplan. 
Go to the below directory and open the floorplan.tcl file to see and understand the different switches are assigned with some default values and we can changes these values based oj our design requiremnt:

<img width="641" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/d8b2f63b-0f4a-4cb3-88df-0a224ca4c0ef">

<img width="635" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/894e00cc-ee7f-49f2-a46c-89ab19ae79c0">

Will have to specify the aspect ratio = width of core/height of core
Utilization factor (area utilize for std cells and macros without considering routing area)
Die area and many more as we can see in readme file

<img width="634" alt="image" src="https://github.com/ashawari11/RTL2GDS-flow/assets/113604711/904270ad-d4f0-45b1-8f56-eab345fc9fbb">

Enter the below command to perform Floorplan
"run_floorplan"






















 
