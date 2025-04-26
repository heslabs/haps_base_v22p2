# Create Application Software

---
## Vitis Software Flow
* Step 1. Launch Vitis IDE and create project workspace
* Step 2. Create new application project
* Step 3. Create a new platform from hardware (XSA)
* Step 4. Create domain for your project: standalone
* Step 5. Explorer the C/C++ source code 
* Step 6. Build project and wait for build finished

---
### Step 1: Launch Vitis IDE and create project workspace
```
$ source ./setenv.sh
$ cd ./appsw && \rm -rf workspace && mkdir ./workspace
$ cd ./appsw/workspace && cp -f ../../export/$(TOP).xsa .
$ cd ./appsw/workspace && vitis --workspace . &
```


---
### Step 2: Create New Application Project

<img src="https://github.com/user-attachments/assets/4263a575-73f7-401c-b427-40b8a6be4217" width=500>\

<img src="https://github.com/user-attachments/assets/6b970697-963b-449d-8d37-625000257002" width=500>

---
### Step 3: Create a new platform from hardware (XSA)

* Select platform from prebuilt XSA file
* Browser the XSA file "top_wrapper.xsa" in workspace folder
  * XSA File: /appsw/workspace/top_wrapper.xsa
  * Platform name: top_wrapper
* Enter the project details
  * Application project name: main

---
<img src="https://github.com/user-attachments/assets/f578b841-9f0c-4054-87d6-f008de624e01" width=600>\

<img src="https://github.com/user-attachments/assets/b36276eb-fcc5-496f-9d02-fee1a92ea7b2" width=600>\

<img src="https://github.com/user-attachments/assets/bbab773a-847f-4b82-afa4-23218681ff87" width=600>\

<img src="https://github.com/user-attachments/assets/2f98f830-2f6c-49ce-af4c-ff25725e28a2" width=600> 

---
### Step 4: Create domain for your project

* Domain details
  * Name: standalone_microblaze_0
  * Display Name: standalone_microblaze_0
  * Operating System: standalone
  * Processor: microblaze_0
  * Architecture: 32-bit 
---
<img src="https://github.com/user-attachments/assets/f5d5afc5-54ea-4ea4-8c8a-5941e2f451ad" width=600>

---
### Select a template to create your project
* Select template: Memory Tests
<img src="https://github.com/user-attachments/assets/37b82c4d-93ca-45c2-9686-a52ed6c6d1d6" width=600>

---
### Step 5: Explorer the C/C++ source code 
* main_system
  * src: memorytest.c, memory_config_g.c

---
<img src="https://github.com/user-attachments/assets/396c2c0e-0f0d-4d29-95b5-281c3848f828" width=800>\
<img src="https://github.com/user-attachments/assets/bbf476e5-0d3d-4723-a652-94e346bee526" width=800>\
<img src="https://github.com/user-attachments/assets/3aa72ba4-8391-494f-b984-138c2fd6d4d0" width=800>\

---
### Step 6: Build project and wait for build finished

<img src="https://github.com/user-attachments/assets/e6766660-2253-4380-8857-ea0db1f42380" width=800>\

---
### platform.spr

<img src="https://github.com/user-attachments/assets/fd332116-486f-4df2-921a-5b10a6d1a8b1" width=850>

---
### microblaze -> bsp -> system.mss

<img src="https://github.com/user-attachments/assets/8a9c0619-c287-4fdb-8f0a-931bfcc0ce69" width=850>

---
### microblaze -> bsp -> system.mss -> mem_1

<img src="https://github.com/user-attachments/assets/5d5e3730-243a-4e42-a24a-4d0b8347651e" width=850>



