# Charge_Pump_for_PLL
This repository presents the design of Charge Pump for PLL implemented using Synopsis Custom Compiler on 28nm CMOS Technology.

# Table of Contents

- [Abstract](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#abstract)
- [Detailed Explanation](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#detailed-explanation)
- [Reference Circuit](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#reference-circuit)
- [Tools Used](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#tools-used)
- [Simulation in Synopsys](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#simulation-in-synopsys)
- [Idle Mode](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#idle-mode)
- [Pump Up Mode](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#pump-up-mode)
- [Pump Down Mode](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#pump-down-mode)
- [Netlist](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#netlist)
- [Author](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#author)
- [Acknowledgement](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#acknowledgement)
- [References](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/blob/main/README.md#references)
# Abstract
A high performance, ultra-low power scalable CMOS charge pump (CP) design for analog phase-locked loops (PLLs) fabricated in all-digital nanoscale IC processes. The compact CP circuit uses four minimally-sized transistor switches and a relatively small capacitor for transferring charge within the PLL to adjust the voltage controlled oscillator frequency in the PLL control loop. Unlike the state of the art designs, the proposed CP topology does not use current mirrors, nor does it suffer from traditional mismatch errors due to its unique structure. Additionally, this charge transfer-based CP has the ability to operate at very low supply voltages well below 1 V.  The fast switching action of the proposed CP allows for the use of a no-added delay D-flip flop-based phase-frequency detector resulting in a reduced PLL control loop delay and very low reference spurs in the overall PLL design. This proposed charge pump is based on 28nm CMOS logic process.

# Detailed Explanation
As with any PLL charge pump, there are three explicit switching modes of operation: (1) Idle, (2) Pump Up, and (3) Pump Down. The three following sub-sections describe each of these modes in detail for the proposed CP in the PLL control loop. 

(1) Idle Mode

The Idle mode is always characterized by the Up and Down error signals being low (i.e. Up = Down = logic 0). There are two different times in which the Idle mode occurs in the PLL control loop, each with a specific purpose: (1) during phase lock to hold the VC value constant (i.e. ??FB equals ??REF) and (2) for the recharging of the capacitor, CP, in between Pump Up and Pump Down modes (i.e., ??FB does not equal ??REF). At the start of the Idle mode, switches S1 and S2 are closed while S3 and S4 are open; meanwhile this action causes CP, to charge to VDD. After CP charges to the supply voltage, VDD, the capacitor CP holds its charge, QP, in an open loop fashion until the CP is instructed by the PFD to change modes to either Pump Up or Pump Down. VC, will not change during Idle mode and, therefore, retains the voltage value, VC0, it held at the moment prior to starting Idle mode.

<p align="center"><img width="452" alt="idle_mode" src="https://user-images.githubusercontent.com/77117825/155839193-8b268528-0f9d-46d5-b291-cde570fd4dae.png"></p>

(2) Pump Up Mode 

In this case, the Pump Up mode is activated by a lagging phase difference between ??FB and ??REF; this causes the PFD to produce a logic 1 Up error signal for the duration of the phase difference between fFB and fREF. The CP responds by transitioning out of Idle mode with an opening of S2 and closing of S4 which allows the charge, QP, stored on CP to transfer to CL, thus raising the voltage on VC. The result for one Pump Up cycle is an increasing of ??VCO and ??FB in order to match ??REF. At the end of every Pump Up cycle the CP returns to Idle mode to fully recharge CP. As the PLL approaches phase lock, partial Pump Up cycles take place incrementally raising VC which allows for accuracy in obtaining the desired frequency for the VCO.

<p align="center"><img width="430" alt="pump_up" src="https://user-images.githubusercontent.com/77117825/155841808-4b068610-9061-49d8-9a3a-35aedc1cbe9f.png"></p>

(3) Pump Down Mode 

The Pump Down mode occurs when the phase error swings in the opposite direction and ??FB leads vREF, causing the PFD to produce a logic 1 Down error signal for the duration of the difference between fFB and fREF. Similar to the Pump Up mode, the CP responds by moving out of the Idle mode, but instead opens S1 and closes S3 which allows the pulling of the stored charge, QP, away from CL, thus lowering the voltage on VC. This action decreases fVCO and, consequently, fFB, in the closed PLL control loop. At the end of every Pump Down cycle, the CP recharges CP in the Idle mode

<p align="center"><img width="430" alt="pump_down" src="https://user-images.githubusercontent.com/77117825/155841877-a647bb4f-6b7c-4d4f-bf8f-005766b8965c.png"></p>

# Reference Circuit 

![reference_ckt](https://user-images.githubusercontent.com/77117825/155841900-8564bc7b-d8fb-4d29-9589-762a755c08a0.jpeg)

# Tools Used 

> Synopsys Custom Compiler: ???The Synopsys Custom Compiler??? design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.


> Synopsys Primewave: ???PrimeWave??? Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.


> Synopsys 28nm PDK: ???The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.

# Simulation in Synopsys 

> Schematic 

<p align="center"><img width="1119" alt="Synopsys_circuit" src="https://user-images.githubusercontent.com/77117825/155841991-5d99dd63-958e-4754-a272-2b560a898b0f.png"></p>

> Symbol 

<p align="center"><img width="301" alt="Symbol" src="https://user-images.githubusercontent.com/77117825/155842003-d2b34152-2a86-4d84-8ad3-9bb5f695fc6e.png"></p>

# Idle Mode 

> Schematic 

<p align="center"><img width="806" alt="idle_mode_circuit" src="https://user-images.githubusercontent.com/77117825/155842017-707ebbd2-2f23-47f2-b969-6cb4088b97ac.png"></p>

> Waveform 

<p align="center"><img width="1431" alt="idle_mode_waveform" src="https://user-images.githubusercontent.com/77117825/155842030-d8dff107-5ac7-47df-a8fa-889091e3a1d0.png"></p>

# Pump Up Mode 

> Schematic 

<p align="center"><img width="759" alt="pump_up_mode_ckt" src="https://user-images.githubusercontent.com/77117825/155842057-7f04a238-52d0-41f4-9d4a-b99c2de3292c.png"></p>

> Waveform 

<p align="center"><img width="1431" alt="pump_up_wave" src="https://user-images.githubusercontent.com/77117825/155842065-2beed6da-4a29-48a2-9c5b-618314bec5b3.png"></p>

# Pump Down Mode

> Schematic 

<p align="center"><img width="728" alt="pump_down_ckt" src="https://user-images.githubusercontent.com/77117825/155842073-0084b350-795d-4d01-b2d7-7ceba0e41de5.png"></p>

> Waveform 

<p align="center"><img width="1427" alt="pump_down_wave" src="https://user-images.githubusercontent.com/77117825/155842081-8d255639-b3ae-45b8-94a0-54901e575c44.png"></p>

# Netlist 

Refer to the netlist of the idle mode here:[idle_mode](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/files/8146526/idle_mode_text.txt)

Refer to the netlist of the pump up mode here:[pump up mode](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/files/8146536/pump._up.txt)

Refer to the netlist of the pump down mode here:[pump down mode](https://github.com/tanmaycv-09/Charge_Pump_for_PLL/files/8146541/pump_down.txt)

# Author 

Tanmay Chakravorty, B.E. ECE, Thapar Institute of engineering & Technology, Patiala-147004.

# Acknowledgement

1. [CLoud Based Analog IC Design Hackathon](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/)
2. [Synopsys India](https://www.synopsys.com/)
3. [VLSI System Design (VSD) Corp.Pvt.Ltd India
4. Kunal Ghosh, Co-founder, VSD Corp.Pvt.Ltd.- [kunalghosh@gmail.com](kunalghosh@gmail.com)
5. Chinmay Panda, IIT Hyderabad
6. Sameer Durgoji, NIT Karnataka 

# References 

1. S. M. Schober and J. Choma Jr., A charge transfer- based high performance, ultra-low power CMOS charge pump for PLLs, Analog Integr. Circ. Sig. Process. (2016) 561???570
2. B. Razavi, Phase-locked loops.


