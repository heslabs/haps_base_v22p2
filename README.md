# HAPS FPGA Design Example

* Hardware features
    * FPGA reference design for PS+PL on HAPS system architecture architecture
    * AXI-C2C interface between PS (Cortex-A53) and PL on HAPS
    * DDR controller and 16GB DRAM on HAPS
    * Microbloaze MCU with virtual UART port for simulation and emulaiton 
* Software features
    * Vitis software flow for building Microblaze baremetal software
    * Embedded software reference for running on Microblaze MCU
    * Running MCU software on both simuation abd FPGA emulation 

---
| # | Training Module | Page | Description |
|:-:|:-|:-|:-|
| 1 | Vivado HW Development Flow | [Page](https://github.com/heslabs/haps_mcu_v22p2/tree/main/01_Create_HW_Design) | Create RTL hardware design using Vivado |
| 2 | Vitis SW Development Flow | [Page](https://github.com/heslabs/haps_mcu_v22p2/tree/main/02_Create_Application_SW) | Build MCU baremetal software using Vitis |
| 3 | Vivado Simulation Flow | [Page](https://github.com/heslabs/haps_mcu_v22p2/tree/main/03_Run_RTL_Simulation) | Running Verilog simulation using Vivado |
| 4 | Application SW Test Flow | [Page](https://github.com/heslabs/haps_mcu_v22p2/tree/main/04_Run_Software_Application) | Running application software in RTL simulation |
| 5 | Configure and Program FPGA | [Page](https://github.com/heslabs/haps_mcu_v22p2/tree/main/05_Program_FPGA) | Configure HAPS and Program FPGA using Confpro-SX GUI |
| 6 | Running FPGA Emulation | [Page](https://github.com/heslabs/haps_mcu_v22p2/tree/main/06_Run_FPGA_Emulation) | Running application software in FPGA emulation |

---
### Learning Prerequisites
* Verilog design and simluation 
* FPGA design and implementaiton methodology
* AMBA-based SoC architecture and UART peripherals
* Embedded software programming

---
### FPGA Hardware and Software Design Flow
1. Create HDL Design using Vivado
   * Create Block Diagram Design using Vivado
   * Configure MicroBlaze Processor
   * Build Hardware Design
2. Create Application Software Using Vitis
   * Create Platform Project from the XSA
   * Create a new Application Project on Platform
   * Associate ELF and Generate Bitstream (Optional)
3. Connecting FPGA Hardware  
   * Connecting HAPS Hardware using Confpro
   * Connecting HAPS Hardware using Vivado
   * Connecting HAPS Hardware using XSCT
4. Launch Application Software 
   * Launch Application Software using Vitis
   * Launch Application Software using XSCT




---
### FPGA Prototyping Platform - Lab setup

<img src="https://github.com/user-attachments/assets/a6ae9ef1-3186-4321-974c-7e695fa983c7" width=850>


---
### Remote access to HAPS-Zynq module
```
<local> $ sshpass -p demo!@# ssh zynq@59.124.169.195 -X
<zynq@cx5> $ sshpass -p xilinx ssh xilinx@192.168.50.4 -X
```

---
### HAPS-SX and Daughter card

<img src="https://github.com/user-attachments/assets/23fcf5dd-3bff-45a7-8453-76a189d734e6" width=850>


---
### AMBA-based SoC Architecture

<img src="https://github.com/user-attachments/assets/c8baf5aa-a481-4689-8ffa-03971eac20e4" width=850>

---
### Leverage Cortex-A53 CPU subsystem in AMD-Xilinx ZynqMPSoC 
<img src="https://github.com/user-attachments/assets/285e3d75-bbee-47f5-a2d2-3137a261021c" width=850>

---  
### 1. Vivado HW Development Flow

* Create design based on prebuit reference (top.tcl) \
  ```$ make new```
* Add your custom IP into the referecne and validate it
* Export the hardware in Vivado (top_wrapper.xsa) \
  ```$ make exp```

---  
### 2. Vitis SW Development Flow

* Create new application project in Vitis \
  ```$ make app-new```
* Select the xsa file from hardware export for platform   
* Enter the platform name: "main", this will be used in tcl command later  
* Create C/C++ program from the template
* Modify the application C/C++ codes
* Build the Vitis project and geenrate the exectuable binary (main.elf)

--- 
### 3. Vivado Simulation Flow
* Association the elf files in Vivado
* Export the simulation for Vivado XSIM simualtor
* Lunch the generated testbench script "tb.sh"
* Open the dumped waveform file (*.wdb) with selected signals (tb_behav.wcfg)

---
### 4. Application SW Test Flow

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

---
### 5. Config HAPS and Program FPGA

Launch Confpro-SX GUI tools
```
$ export CONFPRO_HOME=/home/eda/Confpro-SX_1.1.10
$(CONFPRO_HOME)/guibin/Confpro-SX-GuiRun.sh
/home/eda/Confpro-SX_1.1.10/guibin/Confpro-SX-GuiRun.sh (/bin/Confpro-SX)
```

---
### 6. Run FPGA Emulation Flow

* Download embedded software and launch emulation
* Download your application software for Microblaze MCU and launch the FPGA emulaiton at runtime. Note that the prerequisites are the FPGA bitstream was successfully programmed and the Microblaze MCU in the HW design works funcitonal.
* Prepare you application software "apps.elf"
* Launch Xilinx system command line tool with tcl script
* Check the results in "uart.log"

```
$ xsct ../scripts/xsct_uartcmd.tcl $(HAPS_IP)
```



