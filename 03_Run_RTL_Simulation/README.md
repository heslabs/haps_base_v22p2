# Run RTL Simulation

---
## Vivado Simulation Flow

* Association the elf files in Vivado
* Export the simulation for Vivado XSIM simualtor
* Lunch the generated testbench script "tb.sh"
* Open the dumped waveform file (*.wdb) with selected signals (tb_behav.wcfg)

---
### Associate ELF
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
### Exprt Simulaiton Files
```
$ cd ./vivado && vivado -mode tcl -project ./$(PRJ).xpr -source ../source/vivado_xsim.tcl
$ cd ./vivado/xsim && cp -f ../../source/xsim_cmd.tcl ./cmd.tcl

### vivado_xsim.tcl
export_simulation  -export_source_files -force -directory ./ -simulator xsim  -ip_user_files_dir "./proj.ip_user_files" -ipstatic_source_dir "./proj.ip_user_files/ipstatic" -use_ip_compiled_libs

```

---
### Launch Simulation
* Launch scripts: tb.sh
```
$ cd ./vivado/xsim && ./tb.sh
```


---
### Open the dumped waveform

```
$ cd ./vivado && vivado -mode gui -project ./$(PRJ).xpr -source ../source/xsim_wave.tcl &

### xsim_wave.tcl
set_property target_simulator XSim [current_project]
open_wave_database {./xsim/tb.wdb}
open_wave_config  -quiet ./tb_behav.wcfg
```

