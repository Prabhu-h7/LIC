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

![Image description](PASTE_FILENAME_HERE)

The channel length of both MOS transistors was chosen as:

L = 360 nm

The initial width values for the NMOS and PMOS transistors were determined by design calculations. The values were later adjusted slightly by using a simulation tool.



### 4. DC Operating Point Analysis
![Image description](PASTE_FILENAME_HERE)

A DC operating point analysis was conducted by entering the following command:

This analysis will also aid in the determination of the steady-state values of the circuit. Node voltages and drain current will be among the values determined.



### 5. Bias Adjustment


During the simulation, the widths of the transistor were slightly adjusted until the desired operating conditions were met.

The desired operating conditions were:

- Drain current close to 250 µA
- Output voltage close to 0.8 V



###  6. Transient Analysis
![Image description](PASTE_FILENAME_HERE)
A small sinusoidal signal was applied to the input.

This analysis will show how the output signal changes with respect to time. 

### 7. AC Small Signal Analysis
![Image description](PASTE_FILENAME_HERE)

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
![Image description](PASTE_FILENAME_HERE)

After performing theoretical calculations and adjusting the values by means of simulation, the final dimensions of the transistor are as follows:


Wn = 30 µm
Wp = 128.5 µm
L = 360 nm

# DC Analysis
![Image description](PASTE_FILENAME_HERE)
The DC analysis is carried out to determine the **Quiescent Point of Operation (Q-point)** of the amplifier. Additionally, it helps us verify that the two MOSFETs are operating in the **Saturation Region**, which is essential for the amplification of the input signal. 

*Image description*

From the LT Spice operating point simulation:

Drain Current:

ID ≈ 250 µA

Output Voltage:

Vout ≈ 0.798 V

The output voltage obtained from the simulation is almost equal to the design output voltage of 0.8 V. This indicates that the biasing of the amplifier is appropriate and the design is working as expected. 

# Transient Analysis
![Image description](PASTE_FILENAME_HERE)
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
![Image description](PASTE_FILENAME_HERE)



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

At this point, the gain drops by 3 dB relative to the midband gain.



## Unity Boosts Bandwidth

One way to calculate unity gain bandwidth is:

BW × Av = UGB

15.34 × 15 MHz = UGB

230 MHz UGB

From the simulation plot, the UGB is around:

UGB ≈ 244 MHz

The small difference between the calculated and simulated values is due to the parasitic capacitance associated with the transistor.



# Result

The CMOS amplifier with the NMOS transistor and PMOS active load was successfully designed and simulated with the 180 nm CMOS technology of the TSMC.

The results obtained from the DC analysis showed that the drain current was close to 250 µA, while the output voltage was around 0.8 V. The results obtained showed that the transistor was biased correctly.

The results obtained from the transient analysis showed that the output signal was around 295 mV peak-to-peak with an input signal of 20 mV peak-to-peak. The results obtained showed that the voltage gain was around 14.77 V/V or 23.38 dB.

The results obtained from the AC analysis showed that the midband voltage gain was around 23.7 dB with a bandwidth of around 15 MHz. The calculated UGB was around 230 MHz, which is close to the simulated results.

From the simulation plot, it can be determined that the UGB is about:

UGB ≈ 244 MHz

The difference between the calculated values and the simulated values is attributed to the parasitic capacitance associated with the transistor.



# Inference
From the experiment, it is inferred that the CMOS amplifier with an NMOS transistor and PMOS active load is working properly.  
The DC analysis was performed to ensure the proper biasing of the circuit. In addition, it was ensured that the transistors were operating in the saturation region.  
The transient analysis was performed to ensure the amplification of the input signal.  
The AC analysis was performed to obtain the gain of the amplifier.  
Since the values obtained are close to the results obtained by the simulator, it is inferred that the design of the amplifier is correct and is working well.


# Circuit 02
*Image description*


# DC Analysis
## Design Calculations
### Drain Current
Based on the LTspice DC operating point:
ID ≈ 250 µA
The above equation implies that the simulation results match the required ID.





### Output DC Voltage
Based on the operating point:
Vout = Vdd/2 + Vds
= 0.6 + 0.3
= 0.9 V
*Image description*


# Transient Analysis Calculations


*Image description*
Based on the results obtained:
Maximum Output Voltage
Based on the results obtained:
Vmax = 913.7996 mV
Minimum Output Voltage
Based on the results obtained:
Vmin = 895.6754 mV

### Output Peak-to-Peak Voltage
Based on the results obtained:
Vout(pp) = Vmax − Vmin
= 913.7996 − 895.6754
= 18.1242 mV
= 18.12 mV

### Input Peak-to-Peak Voltage

The input signal used in the circuit is as follows:

SINE(0.91 10m 1k)

Input amplitude = 10 mV

Vin pp = 2 x 10 mV = 20 mV


### Voltage Gain

Av = Vout pp / Vin pp

Av = 18.1242 / 20

Av = 0.906


### Gain in Decibels

Gain(dB) = 20 log10(Av)

Gain = 20 log10(0.906)

Gain = -0.86


# AC Analysis Calculations

*Image description*

From the AC magnitude analysis plot, we can conclude that:

Gain = -0.86 dB


### Linear Gain Conversion

Av = 10^(Gain/20)

Av = 10^(-0.86/20)

Av = 0.906 V/V

## Unity Gain Bandwidth

Unity gain bandwidth is not applicable to the circuit since the **midband gain is less than 1 (0 dB)**. Hence, the gain never crosses **0 dB** on the frequency response curve.

---

## Bandwidth

*Image description*

The bandwidth is calculated by using the −3 dB cutoff frequency.

Midband Gain = −0.86 dB

−3 dB Level = −0.86 dB − 3 dB

−3 dB Level ≈ −3.86 dB

The −3.86 dB level on the AC response curve is observed at:

BW ≈ 179.19 MHz


# Result

The CMOS amplifier circuit was simulated using the LT spice software with the technology used as TSMC 180 nm. The DC analysis was performed to ensure the circuit is working with the drain current of around 250 µA and the output voltage around 0.905 V.

The output signal was found to be around 18 mV peak-to-peak with an input of 20 mV peak-to-peak. Hence, the voltage gain is around 0.96 V/V or −0.86 dB by using the transient analysis. The AC analysis also showed nearly the same results with a stable frequency response.

# Inference
From the results, we can observe that the circuit gives small signal amplification along with stable biasing.

It can be noted that the values of the gain calculated through transient analysis and AC analysis are almost the same, thus verifying that the circuit is operating correctly.

It can be noted that the circuit gives basic amplification along with moderate gain.


# Circuit 03
*Image description*

# DC Analysis
## Design Calculations
### Drain Current
ID ≈ 250 µA


### Output DC Voltage
Vout = Vdd/2 + Vds
Vout = 0.6 + 0.3
Vout = 0.9 V
From the LTspice DC operating point:
*Image description*


# Transient Analysis Calculations
*Image description*
From the transient waveform:
Maximum Output Voltage
Vmax ≈ 1.00 V
Minimum Output Voltage
Vmin ≈ 0.73 V

### Output Peak-to-Peak Voltage

Vout(pp) = Vmax - Vmin  
Vout(pp) = 1.00 - 0.73  
Vout(pp) = 0.27  
Vout(pp) = 270 mV  


### Input Peak-to-Peak Voltage  


Input Signal  
SINE(0.91 5m 1k)  
Input Signal Amplitude  
Input Signal = 5 mV  
Vin(pp) = 2 * 5 mV  
Vin(pp) = 10 mV  


### Voltage Gain  

Av = Vout(pp) / Vin(pp)  
Av = 270 mV / 10 mV  
Av = 27 V/V  


### Gain in Decibels  

Gain(dB) = 20 


# AC Analysis Calculations

From the AC magnitude plot, the **midband gain** is approximately:

*Image description*

Gain ≈ 27.7 dB

### Linear Gain

Av = 10^(Gain/20)

Av = 10^(27.7/20)

Av ≈ 24.8 V/V



## Bandwidth

*Image description*

Bandwidth is obtained from the −3 dB cutoff point.

Midband gain ≈ 27.7 dB

−3 dB level = 27.7 − 3

−3 dB level ≈ 24.7 dB

From the AC response graph:

BW ≈ 19.15 MHz


# Result

The CMOS amplifier using NMOS with PMOS active load was successfully designed and simulated.

DC analysis showed a drain current of about 250 µA and an output voltage of around 0.903 V.

From transient analysis, the output peak-to-peak voltage was about 270 mV for an input peak-to-peak voltage of 10 mV, giving a voltage gain of about 27 V/V (≈ 28.6 dB).

AC analysis showed a midband gain of around 27.7 dB with a bandwidth close to 19.15 MHz.

# Inference

This experiment shows that a CMOS amplifier can achieve high voltage gain when it is properly biased.

The results obtained from **DC, transient, and AC analysis** are consistent with each other, which confirms that the amplifier is working correctly.

The circuit provides good amplification along with reasonable frequency performance.



