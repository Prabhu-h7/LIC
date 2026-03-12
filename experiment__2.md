# CMOS Amplifier Using NMOS with PMOS Active Load

## Aim

The aim of this experiment is to design and study a CMOS amplifier circuit. For the circuit, an NMOS transistor acts as the active device in the circuit, whereas a PMOS transistor acts as an active load.  

The circuit of the amplifier is designed with the following parameters:  
- VDD = 1.2 V  
- ID = 250 µA  
- CL = 0.5 pF  
- L = 360 nm  

To understand the operation of the amplifier circuit, three different analyses are done:  
- DC analysis  
- Transient analysis  
- AC analysis  

## Components Required

The components used in the circuit are:  
*NMOS transistor  
*PMOS transistor  
*Source resistor  
*DC voltage source  
*Input voltage source  
*Load Capacitor  

## Theory

MOSFET transistors are very important devices in modern electronic circuits. MOSFET transistors are commonly used in both analog and digital devices due to their low power consumption and small sizes.

The combination of NMOS and PMOS transistors is used in the CMOS technology. This combination helps reduce the power consumption of the devices while maintaining good performance.

In the experiment, a CMOS amplifier is designed. The NMOS transistor is used as the main device for amplification. The NMOS transistor is responsible for converting the small changes in the voltage signal into corresponding changes in the current.

Instead of using a regular resistor as a load device, a PMOS transistor is used as an active load. The use of an active load helps increase the voltage gain of the amplifier.

A resistor is used as a degeneration resistor and is connected in series with the source terminal of the NMOS transistor. The degeneration resistor is used for stabilizing the operating point and for minimizing distortion in the amplified signal.

The advantages of the amplifier are as follows:

- High voltage gain  
- High bias stability  
- High input impedance  
- Low signal distortion

 For the amplifier circuit to work properly, both NMOS and PMOS transistors have to be in the saturation region. At this point, the MOSFET acts as a controlled current source.

 ## Saturation Conditions

For an NMOS transistor to be in the saturation region, the following conditions need to be met:

- VGS > VT  
- VDS ≥ VOV  

where

- VOV = VGS - VT  

For a PMOS transistor, the conditions are:

- VSG > |VT|  
- VSD ≥ VOV  

where

- VOV = VSG - |VT|

This enables LT Spice to simulate the operation of these MOSFET devices based on the technology that was chosen.






## Procedure

### 1. Adding the Technology Model

The TSMC 180 nm device model was added in LTspice using the library command:
This enables LT Spice to simulate the operation of these MOSFET devices based on the technology that was chosen.



### 2. Building the Circuit

The CMOS amplifier circuit was now created in LT Spice.

- The **PMOS transistor** is connected to the supply voltage, *VDD*, and acts as the load.  
- The NMOS transistor acts as the main amplifying device and is connected with a source resistor.  
- The output voltage is taken from the drain node of the NMOS transistor.  

Appropriate bias voltages are applied to the gate terminals of these transistors. A load capacitor is connected at the output node, simulating the load capacitance.



### 3. Choosing Device Parameters

The channel length of both MOS transistors was chosen as:

L = 360 nm

The initial width values for the NMOS and PMOS transistors were determined by design calculations. The values were later adjusted slightly by using a simulation tool.



### 4. DC Operating Point Analysis

A DC operating point analysis was conducted by entering the following command:


