# Microblaze MCU FPGA Design Example

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
### Application SW Test Flow

* Copy the application source from workspace
  ```
  $ cd ./appsw/memorytests
  $ cp -rf ../workspace/main/src .
  ```
  
* Modify the application code in command mode \
  ```$ vim ./appsw/memorytests/src/memorytest.c```
  
* Build the Vitis project and generate elf file in command mode \
  ```$ make app-cmd```
  
* Launch the RTL simulaiton and view the dumped waveform \
  ```$ make sim```
  
* Copy the simulation waveform (*.wdb) into SW test case
  ```
  $ cd ./vivado && ln -s ../appsw/$(APP)/tb.wdb .
  $ cd ./vivado && cp -f ../appsw/$(APP)/tb_behav.wcfg .
  ```
  
* Launch waveform viewer for SW test case
  ```
  $ cd ./vivado && vivado -mode gui -project ./$(PRJ).xpr -source ../appsw/$(APP)/xsim_wave.tcl &
  ### xsim_wave.tcl
  set_property target_simulator XSim [current_project]
  open_wave_database {./tb.wdb}
  open_wave_config  -quiet ./tb_behav.wcfg
  ```
