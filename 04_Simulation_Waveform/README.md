# Simulation Waveform

---
### Application code
```
#define testDATA 0xB3B2B1B0
int main() {
    sint32 i;
    init_platform();
    u32 rdDATA;
    xil_printf("BRAM\n\r");
    for (u64 i = 0; i < 32; i=i+4) {
        Xil_Out32(0x20000000+i, testDATA);}
    for (u64 i = 0; i < 32; i=i+4) {
        rdDATA = Xil_In32(0x20000000+i);
        //xil_printf(rdDATA == testDATA ? "PASS":"FAIL"); xil_printf("\n\r");}
    xil_printf("END\n\r");
}
```

---
### AXI Transaction
<img src="https://github.com/user-attachments/assets/18d34b95-06fe-4a52-ba8f-78d1ce0e0b2a" width=1200>


 
---
### Write Transaction

<img src="https://github.com/user-attachments/assets/d8f8f926-49c4-41b2-a9b0-6f9adbf9c5d1" width=800>


---
### Read Transaction

<img src="https://github.com/user-attachments/assets/0a0066c1-2f6f-4ac7-82ad-f40bfac33592" width=800>
