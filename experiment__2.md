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

This analysis will also aid in the determination of the steady-state values of the circuit. Node voltages and drain current will be among the values determined.



### 5. Bias Adjustment

During the simulation, the widths of the transistor were slightly adjusted until the desired operating conditions were met.

The desired operating conditions were:

- Drain current close to 250 µA
- Output voltage close to 0.8 V



###  6. Transient Analysis

A small sinusoidal signal was applied to the input.

This analysis will show how the output signal changes with respect to time. 

### 7. AC Small Signal Analysis

AC analysis was performed by setting the AC input magnitude to 1 V and using the command:
This analysis will yield the frequency response of the amplifier and will be useful in obtaining critical parameters of the amplifier such as the gain and bandwidth.


# Design Calculations

## Drain Current Selection

The design value of the drain current was chosen as:

ID = 250 µA

## Source Resistor Calculation

The voltage across the source resistor is assumed to be:


VRS = 0.2 V


The value of the source resistor is calculated as:


RS = VRS / ID
RS = 0.2 / (250 × 10⁻⁶)
RS = 800 Ω


## Output Voltage

For maximum signal swing, the output voltage is chosen from the middle range.

Vout = VDD/2 + IDRS
Vout = 0.6 + 0.2
Vout = 0.8 V


## Gate Voltage

For the NMOS transistor:


VGS ≈ 0.61 V


The source voltage is given by:


VS = IDRS
VS = 0.2 V


Therefore, the gate bias voltage is given by:


VB1 = VGS + VS
VB1 = 0.61 + 0.2
VB1 = 0.81 V


## Device Dimensions

After performing theoretical calculations and adjusting the values by means of simulation, the final dimensions of the transistor are as follows:


Wn = 30 µm
Wp = 128.5 µm
L = 360 nm

# DC Analysis
The DC analysis is carried out to determine the **Quiescent Point of Operation (Q-point)** of the amplifier. Additionally, it helps us verify that the two MOSFETs are operating in the **Saturation Region**, which is essential for the amplification of the input signal. 

*Image description*

From the LT Spice operating point simulation:

Drain Current:

ID ≈ 250 µA

Output Voltage:

Vout ≈ 0.798 V

The output voltage obtained from the simulation is almost equal to the design output voltage of 0.8 V. This indicates that the biasing of the amplifier is appropriate and the design is working as expected. 

# Transient Analysis
Image description

The transient analysis is conducted to observe the behavior of the amplifier while the input signal is varied. 

From the simulation waveform:

Maximum Output Voltage:

Vmax = 930.23 mV

Minimum Output Voltage:

Vmin = 634.74 mV

### Output Peak-to-Peak Voltage
Vout(pp) = Vmax - Vmin  

Vout(pp) = 930.23 - 634.74  

Vout(pp) = 295.49 mV

### Input Peak-to-Peak Voltage
Vin(pp) = 20 mV

### Voltage Gain
Av = Vout(pp) / Vin(pp)

Av = 295.49 / 20

Av ≈ 14.77 V/V

### Gain in Decibels
Gain(dB) = 20 * log10(Av)

Gain ≈ 23.38

# AC Analysis

*Image description*

AC analysis can be utilized in understanding how the gain of an amplifier is affected in terms of frequency.

From the AC plot, we can see that the gain is approximately:

Gain ≈ 23.7 dB

### Converting to Linear Gain

Av = 10^(23.7 / 20)

Av ≈ 15.34



## Bandwidth

The bandwidth at which the gain is reduced by 3 dB can be determined as:

BW ≈ 15 MHz

*Image description*


