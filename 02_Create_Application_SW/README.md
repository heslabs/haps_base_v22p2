# Create Application Software

---
### Launch Vitis IDE and create project workspace
```
$ source ./setenv.sh
$ cd ./appsw && \rm -rf workspace && mkdir ./workspace
$ cd ./appsw/workspace && cp -f ../../export/$(TOP).xsa .
$ cd ./appsw/workspace && vitis --workspace . &
```


---
#### Create New Application Project

<img src="https://github.com/user-attachments/assets/4263a575-73f7-401c-b427-40b8a6be4217" width=500>\

<img src="https://github.com/user-attachments/assets/6b970697-963b-449d-8d37-625000257002" width=500>

---
#### Select a platform to create the project

* Create a new platform from hardware (XSA)
* Browser the XSA file "top_wrapper.xsa" in workspace folder
  * XSA File: /appsw/workspace/top_wrapper.xsa
  * Platform name: top_wrapper
* Enter the project details
  * Application project name: main

---
<img src="https://github.com/user-attachments/assets/f578b841-9f0c-4054-87d6-f008de624e01" width=500>\

<img src="https://github.com/user-attachments/assets/b36276eb-fcc5-496f-9d02-fee1a92ea7b2" width=500>\

<img src="https://github.com/user-attachments/assets/bbab773a-847f-4b82-afa4-23218681ff87" width=500>\

<img src="https://github.com/user-attachments/assets/2f98f830-2f6c-49ce-af4c-ff25725e28a2" width=500> 

