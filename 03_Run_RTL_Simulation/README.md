# Run RTL Simulation

---
## Vivado Simulation Flow

* Step 1. Association the elf files in Vivado2
* Step 2. Export the simulation for Vivado XSIM simualtor
* Step 3. Lunch the generated testbench script "tb.sh"
* Step 4. Open the dumped waveform file (*.wdb) with selected signals (tb_behav.wcfg)

---
## Launch the RTL simulation in command mode
* Run through all the steps in the Makefile
```
$ make sim
```

---
### Step 1. Associate ELF
```
$ cd ./vivado && vivado -mode tcl -project ./$(PRJ).xpr -source ../source/vivado_elf.tcl

## vivado_elf.tcl
remove_files main.elf
import_files -norecurse -force ./main.elf
set_property used_in_simulation 0 [get_files main.elf]
import_files -force -fileset sim_1 -norecurse ./main.elf

set_property SCOPED_TO_REF top [get_files -all -of_objects [get_fileset sources_1] {main.elf}]
set_property SCOPED_TO_CELLS { microblaze_0 } [get_files -all -of_objects [get_fileset sources_1] {main.elf}]

set_property SCOPED_TO_REF top [get_files -all -of_objects [get_fileset sim_1] {main.elf}]
set_property SCOPED_TO_CELLS { microblaze_0 } [get_files -all -of_objects [get_fileset sim_1] {main.elf}]
```

---
### Step 2. Exprt Simulaiton Files
```
$ cd ./vivado && vivado -mode tcl -project ./$(PRJ).xpr -source ../source/vivado_xsim.tcl
$ cd ./vivado/xsim && cp -f ../../source/xsim_cmd.tcl ./cmd.tcl

### vivado_xsim.tcl
export_simulation  -export_source_files -force -directory ./ -simulator xsim  -ip_user_files_dir "./proj.ip_user_files" -ipstatic_source_dir "./proj.ip_user_files/ipstatic" -use_ip_compiled_libs

```

---
### Step 3. Launch RTL Simulation
* Launch scripts: tb.sh
```
$ cd ./vivado/xsim && ./tb.sh

### tb.sh
# RUN_STEP: <elaborate>
elaborate()
{
  xelab --incr --debug typical --relax --mt auto  -L axi_bram_ctrl_v4_1_7 -L xil_defaultlib .....

#RUN_STEP: <simulate>
simulate()
{
  xsim  tb -key {Behavioral:sim_1:Functional:tb} -tclbatch cmd.tcl -protoinst "protoinst_files/bd_1e58.protoinst" -protoinst "protoinst_files/bd_acc6.protoinst" -protoinst "protoinst_files/bd_0696.protoinst" -protoinst "protoinst_files/bd_c637.protoinst" -protoinst "protoinst_files/top.protoinst" -log simulate.log
}

```


---
### Step 4. Open the dumped waveform

```
$ cd ./vivado && vivado -mode gui -project ./$(PRJ).xpr -source ../source/xsim_wave.tcl &

### xsim_wave.tcl
set_property target_simulator XSim [current_project]
open_wave_database {./xsim/tb.wdb}
open_wave_config  -quiet ./tb_behav.wcfg
```

