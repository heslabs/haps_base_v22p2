# Configure and Program HAPS FPGA
 

---
### Step 1: Select HAPS System

```
$ export CONFPRO_HOME=/home/eda/Confpro-SX_1.1.10
$(CONFPRO_HOME)/guibin/Confpro-SX-GuiRun.sh
/home/eda/Confpro-SX_1.1.10/guibin/Confpro-SX-GuiRun.sh
```

---

<img src="https://github.com/user-attachments/assets/a32cca22-9007-4ce4-8f42-c9275288065f" width=650>
 
### Step 2: Configure HAPS

#### Load HAPS-SX configuration file: c2cmbz.csprj

<img src="https://github.com/user-attachments/assets/7b156d7e-5f71-4cd4-b54f-ed7e119f25dc" width=650>

---
#### FPGA bitstream (c2cmbz.bit) is specified in the configuration file (c2cmbz.csprj)

```
### c2cmbz.csprj
        {
            "configurable": true,
            "max falut current": "0",
            "max falut voltage": "0",
            "max voltage": "0",
            "max warning voltage": "0",
            "min falut voltage": "0",
            "min voltage": "0",
            "min warning voltage": "0",
            "pmu channel id": "0xba000018",
            "pmu channel name": "JX24_VCCO",
            "power on": false,
            "pwm on": false,
            "voltage": "0",
            "write NVM": false
        }
    ],
    "program file name": "c2cmbz.bit"
```

#### Step-by-Step configuration
* https://github.com/heslabs/mpc2c_mcu_v22p2/blob/main/05_Program_FPGA/config-haps.md


---
### Step 3: Download FPGA Bitstream 

### Select FPGA bitstream file (c2cmbz.bit) and program the FPGA

<img src="https://github.com/user-attachments/assets/f06e5de9-b67e-4b43-bdb0-e6c7c93b174b" width=650>
 
