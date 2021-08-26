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


### Why STA is important for ASIC/SOC

   | Dynamic       | Static        |
   | ------------- | ------------- |
   | Content Cell  | Content Cell  |
   | Content Cell  | Content Cell  |
  










