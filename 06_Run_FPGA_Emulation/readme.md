# Running FPGA Emilation

## Download embedded software and launch emulation
Download your application software for Microblaze MCU and launch the FPGA emulaiton at runtime. Note that the prerequisites
are the FPGA bitstream was successfully programmed and the Microblaze MCU in the HW design works funcitonal.

1. Prepare you application software "apps.elf"
2. Launch Xilinx system command line tool with tcl script \
```$ xsct ../scripts/xsct_uartcmd.tcl $(HAPS_IP)```
3. Check the results in "uart.log" 

---
## xsct_uartcmd.tcl
```
connect -xvc-url [lindex $argv 0]
after 1000

## Program FPGA
## targets -set -filter {name =~ "xcvu19p*"}
## fpga ./$::env(XSA).bit

## list available targest
targets
## 1  xcvu19p
## 2  MicroBlaze Debug Module at USER2
## 3  MicroBlaze #0 (Running)

## Select target:  Microblaze Debug Moduel (MDM)
targets -set -filter {name =~ "MicroBlaze Debug Module *"}
## Set output file name
set fp [open ./uart.log w]
## start uart terminal
readjtaguart -handle $fp
after 1000

## Select target: Microblaze
targets -set -filter {name =~ "MicroBlaze #*"}
after 1000

## Download ELF program
puts "## apps.elf"
#set APPS $::env(APPS)
dow ./apps.elf
after 1000

# jtagterminal
## start microblaze
rst -processor
after 500
con
## Read test result
## puts "Test done. Press any key to continue ..."
## set rsp [gets stdin]
