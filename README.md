# Charge_Pump_for_PLL
This repository presents the design of Charge Pump for PLL implemented using Synopsis Custom Compiler on 28nm CMOS Technology.

# Abstract
A high performance, ultra-low power scalable CMOS charge pump (CP) design for analog phase-locked loops (PLLs) fabricated in all-digital nanoscale IC processes. The compact CP circuit uses four minimally-sized transistor switches and a relatively small capacitor for transferring charge within the PLL to adjust the voltage controlled oscillator frequency in the PLL control loop. Unlike the state of the art designs, the proposed CP topology does not use current mirrors, nor does it suffer from traditional mismatch errors due to its unique structure. Additionally, this charge transfer-based CP has the ability to operate at very low supply voltages well below 1 V.  The fast switching action of the proposed CP allows for the use of a no-added delay D-flip flop-based phase-frequency detector resulting in a reduced PLL control loop delay and very low reference spurs in the overall PLL design. This proposed charge pump is based on 28nm CMOS logic process.

# Detailed Explanation
As with any PLL charge pump, there are three explicit switching modes of operation: (1) Idle, (2) Pump Up, and (3) Pump Down. The three following sub-sections describe each of these modes in detail for the proposed CP in the PLL control loop. 

(1) Idle Mode

The Idle mode is always characterized by the Up and Down error signals being low (i.e. Up = Down = logic 0). There are two different times in which the Idle mode occurs in the PLL control loop, each with a specific purpose: (1) during phase lock to hold the VC value constant (i.e. ΦFB equals ΦREF) and (2) for the recharging of the capacitor, CP, in between Pump Up and Pump Down modes (i.e., ΦFB does not equal ΦREF). At the start of the Idle mode, switches S1 and S2 are closed while S3 and S4 are open; meanwhile this action causes CP, to charge to VDD. After CP charges to the supply voltage, VDD, the capacitor CP holds its charge, QP, in an open loop fashion until the CP is instructed by the PFD to change modes to either Pump Up or Pump Down. VC, will not change during Idle mode and, therefore, retains the voltage value, VC0, it held at the moment prior to starting Idle mode.

<img width="452" alt="idle_mode" src="https://user-images.githubusercontent.com/77117825/155839193-8b268528-0f9d-46d5-b291-cde570fd4dae.png">

(2) Pump Up Mode 

In this case, the Pump Up mode is activated by a lagging phase difference between ΦFB and ΦREF; this causes the PFD to produce a logic 1 Up error signal for the duration of the phase difference between fFB and fREF. The CP responds by transitioning out of Idle mode with an opening of S2 and closing of S4 which allows the charge, QP, stored on CP to transfer to CL, thus raising the voltage on VC. The result for one Pump Up cycle is an increasing of ΦVCO and ΦFB in order to match ΦREF. At the end of every Pump Up cycle the CP returns to Idle mode to fully recharge CP. As the PLL approaches phase lock, partial Pump Up cycles take place incrementally raising VC which allows for accuracy in obtaining the desired frequency for the VCO.

<img width="430" alt="pump_up" src="https://user-images.githubusercontent.com/77117825/155841808-4b068610-9061-49d8-9a3a-35aedc1cbe9f.png">

(3) Pump Down Mode 

The Pump Down mode occurs when the phase error swings in the opposite direction and ΦFB leads vREF, causing the PFD to produce a logic 1 Down error signal for the duration of the difference between fFB and fREF. Similar to the Pump Up mode, the CP responds by moving out of the Idle mode, but instead opens S1 and closes S3 which allows the pulling of the stored charge, QP, away from CL, thus lowering the voltage on VC. This action decreases fVCO and, consequently, fFB, in the closed PLL control loop. At the end of every Pump Down cycle, the CP recharges CP in the Idle mode

<img width="430" alt="pump_down" src="https://user-images.githubusercontent.com/77117825/155841877-a647bb4f-6b7c-4d4f-bf8f-005766b8965c.png">

