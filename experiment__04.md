# Experiment__04 
 
Differential Amplifier Analysis  

## Aim  

The aim of this experiment is to design and simulate three different MOSFET differential amplifier circuits using the LT Spice software. DC analysis, transient analysis, and AC analysis are carried out in order to compare the gain and bandwidth of the differential amplifiers and the power consumption of the differential amplifiers.  

## Introduction  

Differential Amplifier is a basic and very important circuit in analog electronics. It is used for the amplification of the difference between two signals and is completely unaffected by the common signal present in the two voltage signals. Hence, the differential amplifier is very useful in the reduction of noise in the signal.

MOSFET differential amplifiers are often employed in the development of various electronic circuits such as operational amplifiers and comparators. They provide good gain and better performance. In this experiment, three different differential amplifier circuits are created and tested using the LT Spice software.

## Theory  

A differential amplifier is an amplifier used for producing an output based on the difference between two input signals. The formula for this is:

vid = vin1 - vin2  

The circuit consists of two MOSFETs connected in series. The MOSFETs are connected at the source end and biased by a constant current source. The drain end is connected to the load.  

If vin1 > vin2, then M1 will conduct more current.  
If vin2 > vin1, then M2 will conduct more current.  

For small input signals, both MOSFETs operate in saturation. The output is linear.  

The gain of the differential amplifier is given by:

Av = gm × Rout  

where gm is transconductance and Rout is output resistance.  

Transconductance is given by:

gm = 2ID / Vov  

For high input signals, one MOSFET is in cutoff. The circuit becomes nonlinear for:

vid > 2Vov  

The gain in the circuit varies for different types of loads. The gain is highest for a current mirror. The gain is highest for an active load and medium for a resistor.



# Circuit 1: Differential Amplifier with Resistive Load  

## Working  

This circuit uses two NMOS transistors with resistors at the drain.

When input is applied:

vid = vin1 − vin2  

Current is shared between the two transistors.

If vin1 increases, M1 current increases.  
If vin2 increases, M2 current increases.  

Voltage drop across RD gives the output.

For small input → linear output  
For large input → distortion  

## Design Calculations  

### Given Values  

Technology = TSMC 180 nm  
VDD = +0.9 V  
VSS = −0.9 V  
Power ≤ 2.2 mW  
Ln = 540 nm  
Vin,CM = 0 V  
Vo,CM = 0 V  
Vp = −0.7 V  
CL = 10 pF  
VT ≈ 0.36 V  

### Power Calculation  

P = (VDD − VSS) × ISS  

Total voltage:

VDD − VSS = 1.8 V  

1.8 × ISS ≤ 2.2 × 10⁻³  

ISS ≤ 1.22 mA  

Choose:

ISS = 1.22 mA  

Power = 2.2 mW  

### Drain Current  

ID1 = ID2 = ISS / 2  

ID = 0.61 mA  

### Load Resistance  

Vout = VDD − ID RD  

0 = 0.9 − ID RD  

RD = 0.9 / ID  

RD ≈ 1.475 kΩ  

### Bias Point  

VG = 0 V  
VS = −0.7 V  

VGS = 0 − (−0.7) = 0.7 V  

VOV = VGS − VT  

VOV = 0.34 V  

VDS = 0 − (−0.7) = 0.7 V  

Condition:

VDS > VOV  

0.7 > 0.34 → Saturation satisfied
### Width Calculation  

ID = (1/2) μnCox (W/L) (VOV)²  

W = (2 ID L) / (μnCox (VOV)²)  

After calculation:

W ≈ 24.1 µm  

After simulation adjustment:

W ≈ 32 µm (approx)  

Reason: practical effects like channel length modulation and mobility changes.

## DC Analysis  
  
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/d.a%20dc%20circuit.png)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/d.a__dc%20op%20pt.png)


The DC operating point shows correct biasing.  
Output and source voltages match expected values.  
Transistors are in saturation.

## Input Common Mode Range  

Minimum:

VICM(min) = VS + VT  

VICM(min) = −0.7 + 0.36 = −0.34 V  

Maximum:

VICM(max) = VD + VT  

VICM(max) = 0 + 0.36 = 0.36 V  

Final:

−0.34 V ≤ VICM ≤ 0.36 V  

## Output Common Mode Range  

Maximum:

VOCM(max) = VDD = 0.9 V  

Minimum:

VOCM(min) = VS + VOV  

VOCM(min) = −0.7 + 0.34 = −0.36 V  

Final:

−0.36 V ≤ VOCM ≤ 0.9 V  

## Linear Input Range  

|vid| ≤ 2VOV  

|vid| ≤ 0.68 V  

## Transient Analysis  

### Case 1 (Linear)

vid = 100 mV  

Output is sinusoidal  
No distortion  
Both transistors in saturation  

### Case 2 (Non-linear)

vid = 600 mV  

Output is distorted  
Clipping occurs  
One transistor turns OFF  

## Conclusion from Transient  

Small input → linear behavior  
Large input → distortion  

## Gain Calculation  

Input:

Vin(pp) = 100 mV  

Output:

Vout(pp) ≈ 550 mV  

Av ≈ 5.5  

Gain(dB) ≈ 14.8 dB  

## Theoretical Gain  

ro = 1 / (λ ID) ≈ 16.39 kΩ  

ro_eff ≈ 8.2 kΩ  

gm = 2ID / VOV ≈ 3.59 mS  

Rout = RD || ro  

Rout ≈ 1.25 kΩ  

Ad = gm × Rout  

Ad ≈ 4.49  

Gain ≈ 13.05 dB  

## Reason for Difference  

Difference happens because:

Channel length modulation  
Finite output resistance  
Mobility reduction  
Variation in VOV  
Parasitic capacitances  
Measurement errors  

## AC Analysis  

Midband gain:

Av ≈ 10 dB  

−3 dB level:

≈ 7 dB  

Lower cutoff:

fL = 0  

Upper cutoff:

fH ≈ 4.5 MHz  

Bandwidth:

BW ≈ 4.5 MHz  

## Unity Gain Bandwidth  

UGB = Av × BW  

UGB ≈ 5.5 × 4.5  

UGB ≈ 24.75 MHz  

## Comparison  

Voltage Gain:

Theoretical ≈ 4.49  
Simulated ≈ 5.5  

Gain(dB):

Theoretical ≈ 13.05 dB  
Simulated ≈ 14.8 dB  

## Inference  

The differential amplifier with resistive load is designed successfully.

Power limit is satisfied:

P ≤ 2.2 mW  

Current splits equally:

ID1 = ID2 ≈ 0.61 mA  

Biasing is proper and both transistors work in saturation.

Simulation and theory values are close.

Gain is around 5.5 V/V  
Bandwidth ≈ few MHz  

Small signal gives good amplification.  
Large signal causes distortion.

The circuit works correctly and meets the design requirements.



