# Charge_Pump_for_PLL
This repository presents the design of Charge Pump for PLL implemented using Synopsis Custom Compiler on 28nm CMOS Technology.

# Abstract
A high performance, ultra-low power scalable CMOS charge pump (CP) design for analog phase-locked loops (PLLs) fabricated in all-digital nanoscale IC processes. The compact CP circuit uses four minimally-sized transistor switches and a relatively small capacitor for transferring charge within the PLL to adjust the voltage controlled oscillator frequency in the PLL control loop. Unlike the state of the art designs, the proposed CP topology does not use current mirrors, nor does it suffer from traditional mismatch errors due to its unique structure. Additionally, this charge transfer-based CP has the ability to operate at very low supply voltages well below 1 V.  The fast switching action of the proposed CP allows for the use of a no-added delay D-flip flop-based phase-frequency detector resulting in a reduced PLL control loop delay and very low reference spurs in the overall PLL design. This proposed charge pump is based on 28nm CMOS logic process.

# Detailed Explanation
As with any PLL charge pump, there are three explicit switching modes of operation: (1) Idle, (2) Pump Up, and (3) Pump Down. The three following sub-sections describe each of these modes in detail for the proposed CP in the PLL control loop. 

(1) Idle Mode
The Idle mode is always characterized by the Up and Down error signals being low (i.e. Up = Down = logic 0). There are two different times in which the Idle mode occurs in the PLL control loop, each with a specific purpose: (1) during phase lock to hold the VC value constant (i.e. /FB equals /REF) and (2) for the recharging of the capacitor, CP, in between Pump Up and Pump Down modes (i.e., /FB does not equal /REF).

<img width="452" alt="idle_mode" src="https://user-images.githubusercontent.com/77117825/155839193-8b268528-0f9d-46d5-b291-cde570fd4dae.png">

