# Create Application Software

---
## Vitis Software Flow
1. Launch Vitis IDE and create project workspace
2. Create New Application Project
3. Create a new platform from hardware (XSA)
4. Create domain for your project: standalone
5. Build project and wait for build finished

---
### Launch Vitis IDE and create project workspace
```
$ source ./setenv.sh
$ cd ./appsw && \rm -rf workspace && mkdir ./workspace
$ cd ./appsw/workspace && cp -f ../../export/$(TOP).xsa .
$ cd ./appsw/workspace && vitis --workspace . &
```


---
### Create New Application Project

<img src="https://github.com/user-attachments/assets/4263a575-73f7-401c-b427-40b8a6be4217" width=500>\

<img src="https://github.com/user-attachments/assets/6b970697-963b-449d-8d37-625000257002" width=500>

---
### Create a new platform from hardware (XSA)

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
### Create domain for your project

* Domain details
  * Name: standalone_microblaze_0
  * Display Name: standalone_microblaze_0
  * Operating System: standalone
  * Processor: microblaze_0
  * Architecture: 64-bit
  
<img src="https://github.com/user-attachments/assets/bd0914ec-9112-4f38-b198-e8695fed9e51" width=600>

---
### Select a template to create your project
* Select template: Memory Tests
<img src="https://github.com/user-attachments/assets/37b82c4d-93ca-45c2-9686-a52ed6c6d1d6" width=600>

---
### Vitis IDE - Explorer
* main_system
  * src: memorytest.c, memory_config_g.c

---
<img src="https://github.com/user-attachments/assets/396c2c0e-0f0d-4d29-95b5-281c3848f828" width=800>\
<img src="https://github.com/user-attachments/assets/bbf476e5-0d3d-4723-a652-94e346bee526" width=800>\
<img src="https://github.com/user-attachments/assets/3aa72ba4-8391-494f-b984-138c2fd6d4d0" width=800>\

---
### Build project and wait for build finished

<img src="https://github.com/user-attachments/assets/e6766660-2253-4380-8857-ea0db1f42380" width=800>\


