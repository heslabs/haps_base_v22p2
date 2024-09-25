# haps_mbmcu_v22p2

Build the application software for RTL simulation flow. Folow the steps to launch the RTL simualtion with application software running on Microblaze MCU

---  
### Vivado HW Development Flow

* Create design based on prebuit reference (top.tcl) \
  ```$ make new```
* Add your custom IP into the referecne and validate it
* Export the hardware in Vivado (top_wrapper.xsa) \
  ```$ make exp```

---  
### Vitis SW Development Flow

* Create new application project in Vitis \
  ```$ make app-new```
* Select the xsa file from hardware export for platform   
* Enter the platform name: "main", this will be used in tcl command later  
* Create C/C++ program from the template
* Modify the application C/C++ codes
* Build the Vitis project and geenrate the exectuable binary (main.elf)

--- 
### Vivado Simulation Flow
* Association the elf files in Vivado
* Export the simulation for Vivado XSIM simualtor
* Lunch the generated testbench script "tb.sh"
* Open the dumped waveform file (*.wdb) with selected signals (tb_behav.wcfg)

---
### Application test case

* Copy the application source from workspace
     ```
     $ cd ./appsw/memorytests
     $ cp -rf ../workspace/main/src .
     ```
* Modify the application code in command mode
    ```
    $ vim ./appsw/memorytests/src/memorytest.c
    ```
* Build the Vitis project and generate elf file in command mode \
  ```$ make app-cmd```
* Launch the RTL simulaiton and view the dumped waveform \
  ```$ make sim```
   
