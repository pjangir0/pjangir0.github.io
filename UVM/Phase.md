## Phases Of UVM
---

![Phase](https://i0.wp.com/www.learnuvmverification.com/wp-content/uploads/2016/04/Uvm_phases.gif?zoom=1.100000023841858&resize=347%2C535)   

#### 1. Build Phase    
overall purpose is to construct, configure and connect the Testbench component hierarchy. All the build phase methods are functions and therefore execute in zero simulation time.

  1. ##### Build
    - It constructs the testbench component hierarchy **from the top downwards**.
    - During the build phase uvm_components are indirectly constructed using the UVM factory  

  2. ##### Connect
    - The connect phase is used to make TLM connections between components or to assign handles to testbench resources.
    - it works from the **bottom-up of the hierarchy upwards**

  3. ##### End_of_elaboration  
    - end_of_elaboration phase is used to make any final adjustments to the structure, configuration or connectivity of the Testbench before simulation starts.
    - it works from the **bottom-up of the hierarchy upwards**

#### 2. Run Phase
The UVM Testbench stimulus is generated and executed during the run time phases

  1. ##### start_of_simulation
    - it is intended to be used for displaying banners; Testbench topology; or configuration information.
    - It is called in **bottom up order**.
  2. ##### Run phase
    - The run phase is implemented as a **task**, and all uvm_component run **tasks are executed in parallel.**

      ***Reset phase*** - Put the DUT/Interface into a default state   
      ***Configure phase*** - DUT into a known state before the stimulus could be applied to the DUT    
      ***Main Phase*** - main phase is where the stimulus specified by the Test case is generated and applied to the DUT    
      ***Shutdown phase*** - The shutdown phase is to ensure that the effects of stimulus generated during the main phase has propagated through the DUT and that the resultant data has drained away.    

#### 3. Cleanup Phases
the clean up phases are used to extract information from Scoreboards and Functional Coverage Monitors to determine whether the test case has passed and/or reached its coverage goals.They work from the **bottom to the top** of the component hierarchy.

  1. ##### extract:
    - The extract phase is used to retrieve and process information from Scoreboards and Functional Coverage Monitors.
    - This may include the calculation of statistical information used by the report phase.

  2. ##### check:
    - This phase is used to check if the DUT behaved correctly and to find any error that may have occurred during the stimulus execution.

  3. ##### report:
    - The report phase is used to display the results of the simulation to the standard output or to write the results to file.  

  4. ##### final:
    - The final phase is used to complete any other outstanding actions that the Testbench has not already completed.
