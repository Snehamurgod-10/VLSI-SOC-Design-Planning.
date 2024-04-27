# VLSI-SOC-Design-Planning.

1. [Day 1:](#day1)  
•	[Get Familiar with Open-Source EDA Tools](#11).  
•	[Intro to OpenLane](#12).  
•	[Directory Structure of Openlane](#13)  
•	[Steps to characterize synthesis results](#14)  


2. [Day 2:](#day2)  
•	[Steps to run floorplan using OpenLANE](#21)  
•	[Review floorplan layout in Magic](#22)  
•	[Congestion aware placement using Replace](#23)  


3. [Day3:](#day3)  

•	[Lab introduction to Sky130 basic layers layout and LEF using inverted](#31)  
•	[Lab steps to create std cell layout and extract spice netlist](#32)  
•	[Lab introduction to Magic tool options and DRC rules](#33)  
•	[Lab introduction to Magic and steps to load Sky130 tech-rules](#34)  
•	[Lab exercise to fix poly.9 error in Sky130 tech-file](#35)  

 4. [Day4:](#day4)  

•	[Pre-layout timing analysis and importance of good clock tree](#41)  
•	[Lab steps to configure synthesis settings to fix slack and include vsdinv](#42)  
•	[Lab steps to configure OpenSTA for post-synth timing analysis](#43)   
•	[Lab steps to optimize synthesis to reduce setup violations](#44)  
•	[Lab steps to do basic timing ECO](#45)  
•	[Lab steps to run CTS using Triton](#46)  
•	[Lab steps to verify CTS runs](#47)  
•	[Lab steps to execute OpenSTA with right timing libraries and CTS assignment](#48)  

[Day 5:](#day5)  

•	[Final step for RTL2GDS using tritinRoute and openSTA](#51) 


# Day1:<a name ="day1">   </a>


## Get Familiar with Open-Source EDA Tools <a name ="11"> 
### Basic Bash Commands:  
`cd`   : Change directory.  
`ls`   : List all files.  
`mkdir`: Make a directory.  
`pwd`  : Show the current directory.  
`clear`: Clear the terminal.  
`tree` :This command is used to print the hierarchy of the file system from the present directory.  </a>
# Intro to OpenLane:<a name ="12">  
### OpenLane is an automated RTLtoGDSII flow.  
Here we are working in Sky130_fd_sc_hd PDK varient. where, "sky130" is process name or node name."fd" is a foundary name (skyWater foundary)."sc" means standerd cell librery files and the last one "hd" stands for high density(basically one type of varient).

Sky130_fd_sc_hd varient contains many technology files like verilog, spice, techlef, meglef,mag,gds,cdl,lib,lef,etc. (techlef file contains the layer information).  
</a>

## Directory Structure of Openlane:<a name ="13">  

openlane  
├── AUTHORS.md  
├── clean_runs.tcl  
├── configuration  
├── conf.py  
├── CONTRIBUTING.md  
├── default.cvcrc  
├── designs  
├── docker_build  
├── docs  
├── flow.tcl  
├── LICENSE  
├── Makefile  
├── README.md  
├── regression_results  
├── report_generation_wrapper.py  
├── run_designs.py  
└── scripts  
###For Demonstration of tools, we have choosen the picorv32a project.Below are the contents of the picrorv32a.   

picorv32a  
.  
├── config.tcl  
├── runs  
├── sky130A_sky130_fd_sc_hd_config.tcl  
├── sky130A_sky130_fd_sc_hdll_config.tcl  
├── sky130A_sky130_fd_sc_hs_config.tcl  
├── sky130A_sky130_fd_sc_ls_config.tcl  
├── sky130A_sky130_fd_sc_ms_config.tcl  
└── src  
    ├── picorv32a.sdc  
    └── picorv32a.v  
###This config.tlc file contains every details about the design. for example, details about enrollment, clock period, clock period port etc.The setting in the config.tcl has higher precedence compared to the default canfigurations. These settings will override the default settings of the openlane.  
#Design Preparation Step:  
###To access the openlane tool first we have to change the directory to the `/<path to openlane_working_dir>/openlane`, we can access the files . In this folder we have to type  
$  docker  
$ ./flow.tcl --interactive  
###Here we are using -`-interactive` , because we are manually running every tool by overselves.If we just execute `./flow.tcl` The entire process from RTL to GDS will we completed.  

###we need add the required packages , the below command does that.  
https://github.com/Snehamurgod-10/VLSI-SOC-Design-Planning./blob/main/1-1.png
$package require openlane 0.9  
###before running the synthesis , we have to prep the design.  
$ prep -design picorv32a  
###Result for the above command.  





