# haps_mbmcu_v22p2

---
### Build the application software for RTL simulation flow
The design and verfication for RTL simulaiton are as below

1. Create design based on prebuit reference (top.tcl)
2. Export the hardware in Vivado (top_wrapper.xsa)
3. Create new application project in Vitis
4. Select the xsa file from hardware export for platform
5. Enter the platform name: "main", this will be used in tcl command later
6. Create C/C++ program from the template
7. Modify the application C/C++ codes
8. Build the Vitis project and geenrate the exectuable binary (main.elf)
9. Association the elf files in Vivado
10. Export the simulation for Vivado XSIM simualtor
11. Launch the generated testbench script "tb.sh"
12. Open the dumped waveform file (*.wdb) with selected signals (tv_behav.wcfg)

   
