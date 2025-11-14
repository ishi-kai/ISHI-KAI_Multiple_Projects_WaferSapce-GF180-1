#  ISHI-KAI's Multiple Users Project
We, [ISHI-KAI](https://ishi-kai.org/), are a community that promotes open source PDK & EDA.  
This time, we brought together 14 novice semiconductor designers (most of whom were new to semiconductor design), each of whom created an analog circuit, such as an Inverter or OPAMP, ADC, PLL, BGR, CS, made using xschem & klayout with P-Cells .  
All schematics and layouts are released under an open source license.  
  
In addition, pads for probing were added to all circuits, taking into account that only bare dies are received.  
Since ISHI-KAI has university professors and semiconductor companies as collaborators, we are able to borrow probers through the generosity of professors and companies.Therefore, we plan to run analog circuits by probing.  

- ![all_members_layout_using](/images/chip_image_members.png)


## Project List
- [SAR-ADC](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_WaferSapce-GF180-1#SAR-ADC)
- [LDO](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_WaferSapce-GF180-1#LDO)
- [PLL](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_WaferSapce-GF180-1#PLL)
- [BGR](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_WaferSapce-GF180-1#BGR)
- [CS](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_WaferSapce-GF180-1#CS)
- [Inverter](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_WaferSapce-GF180-1#Inverter)
- [OPAMP](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_WaferSapce-GF180-1#OPAMP)


## Members (14 Members)
- [Prof.Tsuchiya](https://github.com/atuchiya)
- [3zki](https://github.com/3zki)
- ajisai
- [bols-blue](https://github.com/bols-blue)
- [gitefu](https://github.com/Gitefu)
- [homelith](https://github.com/homelith)
- [ice458](https://github.com/ice458)
- [noritsuna](https://github.com/noritsuna)
- [ponzu840w](https://github.com/mulwak)
- [yamada3](https://github.com/keropiyo)
- [Maple0705](https://github.com/maple0705)
- [Gitefu](https://github.com/Gitefu)
- [Kinako](https://github.com/kinako71)
- [Tseng](https://github.com/tsengs0)


## Files
### [GDS](/gds/)

- [Layout File](/gds/ISHI-KAI_WS_RUN1.zip)
    - It is compressed because it exceeded 100MB.
- [Frame File](/gds/frame_ISHI-KAI.gds)
- [Member's Project](/gds/member_project/)

- ![KLayout](/images/chip_image_klayout.png)


### Schematic
Please refer to the links below.  

- [SAR-ADC](https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/submit_version)
- [LDO](https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/noritsuna/ldo)
- [PLL](https://github.com/atuchiya/DC23-LTC2/tree/japan-test/PLL/)
- [BGR](https://github.com/atuchiya/DC23-LTC2/tree/japan-test/BGR/)
- [CS](https://github.com/atuchiya/DC23-LTC2/tree/japan-test/CS)
- [Inverter](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1)
- [OPAMP](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1)



## Precheck Log
- [precheck log](/precheck_log/RUN_2025-11-14_00-07-09/)
- ![precheck log](/images/precheck_2nd_OK.png)


# [SAR-ADC](https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/submit_version)
## Specification
- Base Spec
    - 6bit SAR-ADC
- Clock(Resolution)
    - 8MHz
- Process
    - Global Fundories 180nm
- Size
    - x00um x x00um
- Work Voltage (VDD)
    - 3.3V


## Submission files
- [GDSII for tapeout](https://github.com/ishi-kai/Chipathon2023_ADC/blob/main/submit_version/klayout/SAR_TOP.gds)
- [Schematic file for LVS](https://github.com/ishi-kai/Chipathon2023_ADC/blob/main/submit_version/xschem/sar_adc_lvs.sch)

  - Layout and the contributor of each subblock/subsystem
  ![Parts Layout](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/layout.jpg)

  - Block Diagrams
  ![Block Figs](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/PnR.png)

  - Interface and Area
  ![Pins Layout](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/layout_pin_placement.png)  

---

## Descriptoin of each design file
| File | Purpose/Function | Remark |
| --- | --- | --- |
|SW_CDAC.sch|switch component for each CDAC bit which is based on the https://github.com/ishi-kai/Chipathon2023_ADC/blob/main/transmission-gate/sw.sch|The only difference from the base sw.sch is the NMOS connected to the Vout port|
|SW_CDAC.sym|symbol file made from the Sw_CDAC.sch||
|user_proj_sarlogic.sym|symbol file used for the simulation of [user_proj_sarlogic_pex_extracted.spice](https://github.com/ishi-kai/Chipathon2023_ADC/blob/main/maple0705/SAR_Logic/klayout/user_proj_sarlogic_pex_extracted.spice)||
|user_proj_sarlogic.sch|blackbox module for making the symbol file of user_proj_sarlogic||
|tran_sar_logic.sch|schematic file for the unit-level verification of SAR logic||
|tran_sar_adc.sch|Testbench for the integration of the overall SAR A/D converter as shown in the figure below||

![SAR-ADC Spec](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/sar_adc_operating_waveform.png) 

---

### Miscellaneous:  
  - Top-level schematic of the A/D converter integrating all subblocks 
    - https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/maple0705/SAR_Logic/caravel/openlane
    - ![SAR_TOP_LVS](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/SAR_TOP_LVS.png)  
  - Design of the MIM capacitor array  
    - https://github.com/ishi-kai/Chipathon2023_ADC/tree/cdac_tseng/cdac/mim_cap_array_8x8
    - ![CDAC](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/advanced_mimcap_array8x8_15step.png)  
  - Design of the latch components
    - https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/latch  
    - https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/inverter
    - ![LATCH](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/LATCH.png)  
    - ![Inv](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/Inv.png)  
  - Design of the comparator
    - https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/gitefu/comp_20240331
    - ![Comparator](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version/images/comp_20240331.png)  
  - Unused/Tentative design material
      - LDO: https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/noritsuna/ldo
      - ![LDO](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/submit_version//images/ldo.png)  




# [LDO](https://github.com/ishi-kai/Chipathon2023_ADC/tree/main/noritsuna/ldo)

- ![Curcuit](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/noritsuna/ldo/images/curcuit_ldo.jpg)  
- ![Layout](https://github.com/ishi-kai/Chipathon2023_ADC/raw/main/noritsuna/ldo/images/layout_ldo.jpg)  

## Specification
    - Process
        - Global Fundories 180nm
    - Size
        - 700um x 550um
    - In Voltage (VDD)
        - 3.3V
        - Layer4&5(Right Side)
        - Layer2&4&5(Left Side)
    - GND (VSS)
        - Layer1
    - Out Voltage (Vout)
        - 3.2V
        - Layer4&5
    - Out Ampere (Vout)
        - 4mA
        - Layer4&5

## Other Parts
- [Power Source (Band Gap Reference)](https://github.com/atuchiya/DC23-LTC2/tree/japan-test/BGR)
    - Made by Akira Tsuchiya at Chipathon2023's Japan Team
- [Current Source](https://github.com/keropiyo/Chipathon2023)
    - Made by Miho Yamada at Chipathon2023's Japan Team
- [Waffle Type P-Fet Array (as Current Mirror)](https://github.com/akiles-esta-usado/DC23-LTC2/tree/add-ic-makefile/LDO/xschem/waffle_1984)
    - Made by Akiles Esta Usado at Chipathon2023's Chili Team



# [PLL](https://github.com/atuchiya/DC23-LTC2/tree/japan-test/PLL/)
Analog PLL testbench

* input : 8MHz
* output : 48/40MHz
* VDD : 3.3V

# Files
* pll_bench - PLL and its benchmark
* pfd, pfd2 - PFD 
* cp - Charge pump
* lf, lf2 - Loop filter
* ctrlsel - Vctrl selector
  * tmg -Transmission gate
* vco - VCO
  * inv_bias - Special inverter for the ring oscillator
* fdiv - Buffer and Clock divider
* sw - Output switch

- [PLL Benchmark](/images/pll_bench.png)
- [PLL Layout](/images/pll_layout.png)


# [BGR](https://github.com/atuchiya/DC23-LTC2/tree/japan-test/BGR/)
## Specification
BGR : diode + current mirror  

- core schematic file: bgr_diode.sch
- symbol file: bgr_diode.sym
- test bench file: tbdc_bgr_diode.sch
- pin list: vdd (3.3 V supply), vss (ground), vout (voltage output)
- output voltage (target) : 1.2 V


## Layout
- GDSII file: bgr_diode.gds
- Netlist for LVS: bgr_diode.cdl
- pin list: vdd (3.3 V supply), vss (ground), vout (voltage output)
- size: 108 um x 200 um

![image](https://github.com/atuchiya/DC23-LTC2/assets/49263791/6c8e2316-a329-44d8-8517-f05f2b79a016)


# [CS](https://github.com/atuchiya/DC23-LTC2/tree/japan-test/CS)
## Specification
Current source : Vth referenced current source + current mirror  

- core schematic file: cs_vthref.sch
- symbol file: cs_vthref.sym
- test bench file: tbdc_cs_vthref.sch
- pin list: vdd (3.3 V supply), vss (ground), vb (bias voltage for pMOS current mirror)
- current: 20 uA


## Layout
- GDSII file: cs_vthref.gds
- Netlist for LVS: cs_vthref.cdl
- pin list: vdd (3.3 V supply), vss (ground), vb (bias voltage for pMOS current mirror)
- size: 39 um x 49 um

![image](https://github.com/atuchiya/DC23-LTC2/assets/49263791/741bb0b8-ffda-4fc8-b15a-b7af3cdb1eaa)




# [OPAMP](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1)
## [3zki](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/3zki/)
I designed a rail-to-rail opamp.

I am assuming Vdd=5.0V and Vb=2.5V.

(Note July 24, 2025)

This design has taken from "CMOS Circuit Design, Layout, and Simulation" (Figure 24.48) by R. Jacob Baker.

We applied for GFMPW-1 (free shuttle), but were not accepted, so no documents or measurements were created.

Also, look into "Low Voltage Cascode Current Mirror"

- ![3zki_opamp_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/3zki_opamp_xschem.jpg)
- ![3zki_opamp_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/3zki_opamp_layout.jpg)


## [gitefu](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/Gitefu/)
I am a graduate school student majoring in processor research, and I am involved in robot building with a group called [tofunology](https://tofunology.github.io/site/).

One day, through an event, I learned about the organization [ISHI-KAI](https://ishi-kai.org/) and decided to participate in a project where each member creates an analog circuit to be integrated onto a single chip.

However, I had little knowledge of analog circuits. 
This was my first time making an operational amplifier, and being a beginner, I faced many challenges. However, with a lot of support from [ISHI-KAI](https://ishi-kai.org/)  members, I was able to complete it.

Through this project, I've gained a solid understanding of the fundamentals of analog circuits and the process of creating chips. I feel extremely pleased with the experience


### About My Circuit
This is the operational amplifier on a chip I made for the first time.This operational amplifier was created with reference to following website.  
Akira Tsuchiya「GF180でオペアンプ設計してみよう」[https://note.com/akira_tsuchiya/n/n710ed2d0e428](https://note.com/akira_tsuchiya/n/n710ed2d0e428) (Published:2023/09/19 23:24)

### Contact
X : [@tnk_make](https://twitter.com/tnk_make)

### TestBench
[op_tb.sch](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/gitefu/op_tb.sch)  
- ![gitefu_opamp_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/gitefu_opamp_xschem.jpg)
- ![gitefu_opamp_xschem_PEX](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/gitefu_opamp_xschem_PEX.jpg)

### Last Layout
[op_20231204.gds](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/gitefu/op_20231204.gds)  

### Flatten Layout
[op_20231204_flat.gds](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/gitefu/op_20231204_flat.gds)  
- ![gitefu_opamp_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/gitefu_opamp_layout.jpg)


## [ice458](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/ice458/)
I designed a dynamic comparator.

### [xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/ice458/dynamic_comparator/xschem/)
At first I was designing a 4-bit asynchronous SAR ADC, but in the middle of the project, I realized that I could not use 3.3V transistors and that I did not have time for layout, so I decided to make only a comparator.

- ![ice458_adc_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/ice458_adc_xschem.jpg)

### [klayout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/ice458/dynamic_comparator/klayout/)
This is the layout of the comparator.

- ![ice458_adc_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/ice458_adc_layout.jpg)


## [noritsuna](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/noritsuna/)
I designed my first semiconductor and built an inverter&opamp circuit.  

### [opamp/xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/noritsuna/opamp/xschem/)
Here you will find the schematic for the opamp and the test bench for PEX.  

- ![noritsuna_opamp_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/noritsuna_opamp_xschem.jpg)
- ![noritsuna_opamp_xschem_PEX](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/noritsuna_opamp_xschem_PEX.jpg)

### [opamp/klayout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/noritsuna/opamp/klayout/)
Here is the layout for the opamp.  
- ![noritsuna_opamp_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/noritsuna_opamp_layout.jpg)


## [yamada3](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/yamada3/)
I was able to build an operational amplifier for the first time!
Thanks to the "mokumoku-kai" of ISHI-KAI, which was held every day until midnight, I was able to do it with everyone's help. Thank you very much.
I am glad that I did not give up and worked on it.

- ![yamada3_opamp_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/yamada3_opamp_xschem.jpg)
- ![yamada3_opamp_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/yamada3_opamp_layout.jpg)



# [Inverter](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1)
## [ajisai](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/ajisai/)
I designed my first semiconductor and built an inverter circuit.  

- ![ajisai_inverter_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/ajisai_inverter_xschem.jpg)
- ![ajisai_inverter_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/ajisai_inverter_layout.jpg)


## [bols-blue](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/bols-blue/)
I designed my first semiconductor and built an inverter circuit.  

- ![bols-blue_inverter_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/bols-blue_inverter_xschem.jpg)
- ![bols-blue_inverter_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/bols-blue_inverter_layout.jpg)

## [homelith](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/homelith/)
This is the first time I designed my semiconductor, building a simple inverter circuit.

Although my PMOS design is relatively smaller than expected by counterpart NMOS, I dare submit on current composition for measure real performance of un-balanced design.

This attempt tells me a important understanding of principles of semiconductor design and I would like to express my gratitude to this project.

- ![homelith_inverter_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/homelith_inverter_xschem.jpg)
- ![homelith_inverter_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/homelith_inverter_layout.jpg)


## [noritsuna](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/noritsuna/)
I designed my first semiconductor and built an inverter&opamp circuit.  

### [inverter/xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/noritsuna/inverter/xschem/)
Here you will find the schematic for the inverter and the test bench for PEX.  
- ![noritsuna_inverter_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/noritsuna_inverter_xschem.jpg)
- ![noritsuna_inverter_xschem_PEX](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/noritsuna_inverter_xschem_PEX.jpg)

### [inverter/klayout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/noritsuna/inverter/klayout/)
Here is the layout for the inverter.  
- ![noritsuna_inverter_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/noritsuna_inverter_layout.jpg)


## [ponzu840w](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/member_project/ponzu840w/)
I am an electronics undergraduate student working on analog circuit design.  
In this shuttle I designed a simple inverter. This work has helped me to understand the IC design flow with open source CAD tools.  

- ![ponzu840w_inverter_xschem](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/ponzu840w_inverter_xschem.jpg)
- ![ponzu840w_inverter_layout](https://github.com/ishi-kai/ISHI-KAI_Multiple_Projects_OpenGFMPW-1/raw/main/images/ponzu840w_inverter_layout.jpg)




[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) 
