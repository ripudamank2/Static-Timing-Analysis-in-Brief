# Static-Timing-Analysis-in-Brief

The basic STA algorithm can support upto 10 million instances. STA over-estimate the delay of long paths. If there is any short path SAT will ignore them . This will make analysis "fast" and will not suffer from hold-time violations. 



### Timing Analysis are of two types --->  1.Dynamic 2.Static

1. Dynamic : Time is involved during analysis . We actively include time by hand in Dynamic analysis. At input we need to run sweep so timing will be there. 
 
     a. Its will used to analysis IPs and BLOCKs    

2. Static : No time involved in input files or output files.
 
    a. its will done on larger circuts like ASIC/SOC/FPGA.
    
    
##### Dynamic Timing Analysis

Advantages:
 
 1. It can check asynchronous interfaces. 
 2. It can be accurate through SPICE simulation.
 3. No need to specify false, multi-cycle path etc. 

Disadvantages:

 1. Analysis quality depends on stimulus vector (we need to carefully choose the inputs vector (togglings and fixed nodes)).
 2. Non-exhaustive and virtually impossible to check all the paths.
 3. Requires long run-times. 
 4. This can only be done at IP/Block levels.
 5. Test-chip level needs FastSPCIE/Accelerated-SPCIE.
 6. SOC level analysis cannot be done. (we cant write lots of etap points).


##### Static Timing Analysis

Advantages:

 1. Fast-Design is analyzed in one pass for one clk cycles.
 2. Exhaustive and check all topological paths in the design.
 3. Does not require verification env.
 
Disadvantages:

 1. Less accurate.
 2. Must define timing requirements.
 3. Difficult handling asynchronous designs and false paths.


### Why STA is important for ASIC/SOC:

   | Dynamic       | Static        |
   | ------------- | ------------- |
   | Check the functionality of the design.  | Check the static delays of design.  |
   | SPICE based Simulation  | Formula based  |
   | highly accurate  | Critical Path analysis  |
   | very slow run time  | fast run time  |
   | HSPCIE,SPECTRE,ELDO  | PrimeTime,Tempus  |
   | Input files: SPF,SPICE MODELS  | Input files: SDF,SPEF,Verilog,Liberty file |
   
 
 
 
### How STA works Fast: 
 
   
 
![FIG:1](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/sta_work.jpg)



### Need of STA concepts:
   
![FIG:2](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/sta_con.jpg)   


### STA in Digital Design (ASIC/SOC) :

![FIG:3](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/Digital.jpg)


### STA Engine I/O :

![FIG:4](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/sta_engine.jpg)


### STA OUTPUTS :

  1. Register to Register delay
  2. Setup times check of all external synch inputs
  3. Hold time check of synch outputs
  4. CLK to Q delays
  5. Pin to Pin Combinational Delays
  6. Different Analysis Modes-Best, Worst, Typical, On-Chip Variation
  7. Data to Data  checks
  8. Case Analysis
  9. Multiple clocks per Registers
  10. Min Pulse width check
  11. Derived CLK
  12. CLK gating checks
  13. Netlist Editing
  14. Report_clk_timing
  15. Clk re-convergence pessimism
  16. worst-arrival slew propagation
  17. path-based analysis
  18. debugging delay calculation




![FIG:4](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/path_types.jpg)




#### Directed Acyclic Graph (DAG):

   1. Netlist is represented in form of DAG.
   2. Delay values are associated with nodes (cells) and links (nets).
   3. Total path delay is the sum of path delay values.
   4. First all the possible topological paths are extracted.
   5. Next for each path calculated its delay and compare it with endpoints (required) values.
 
 
 #### Max and Min path concept :
 
   1. A Max Path is not the physical maximum length path (more number of gates and delay). Rather it's the path with largest delay.
   2. A Min Path is the path with the smallest delay (less number of gates and delay).
 
 
## STA Delay :

   1. In this static delays such as gate and net delay are considered.
   2. In each path and these delays are compared against their required (RAT) maximum and minimum values.
   3. Actual path delay is the sum of the Net delay and the cell delay along the timing path.
   4. Net delay is the total time for charging and discharging all the parasitics. it is a function of parasitic R and C.
   5. Cell delay is the delay arc corresponding to the input and output ports of the cell. It is the function of Slew , Load and Process Parameters.
   6. Wire Load Models are fetched from the Technology files.


![FIG:5](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/delay.jpg)


![FIG:6](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/delay_cal.jpg)





#### Pre-layout Net delay Calculation :

  1. Wire load Model
  2. Net length is a function of net fan-out and chip-area.
  3. Average of R and C are estimated for different fan-outs.
  4. Net delay is calculated simply by R*C.





 
### CLOCK LATENCY AND SKEW


![FIG:6](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/clock.jpg)



### Setup and Hold time :


![FIG:7](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/setup_hold.jpg)


#### Setup time equation :

![FIG:8](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/setup_equ.jpg)


#### Hold time equation :

![FIG:9](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/hold_equ.jpg)



### False Path and its types :


![FIG:10](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/false_path.jpg)


#### Asynchronous False Path :

![FIG:11](https://github.com/ripudamank2/Static-Timing-Analysis-in-Brief/blob/main/images/Asynchro_f_path.jpg)



#### Static False Path:




#### Non-Functional False Path :




#### Clock Uncertainty Concept :




#### Clock Uncertainty Quantification :




#### Process-Temperature-Voltage Corners & Delay :




#### Process-Temperature-Voltage Corners & Setup/Hold-Violation :




#### On Chip Variations :









  








