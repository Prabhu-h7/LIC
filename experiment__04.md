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

## Input Common Mode Range (ICMR)

The input common-mode range is the range of input voltage for which all the transistors in the circuit remain in saturation and the amplifier works properly.

### Minimum Input Common Mode Voltage

For correct operation, the NMOS transistors must stay ON and in saturation.

Condition:

VGS ≥ VT  

We know:

VGS = VICM − VS  

So,

VICM(min) = VS + VT  

Substituting values:

VS = −0.7 V  
VT = 0.36 V  

VICM(min) = −0.7 + 0.36  

VICM(min) = −0.34 V  

### Maximum Input Common Mode Voltage

For the maximum input voltage, the transistors should still remain in saturation.

Condition:

VDS ≥ VOV  

We know:

VD = 0 V  
VS = −0.7 V  

So,

VDS = VD − VS = 0 − (−0.7) = 0.7 V  

Now,

VICM(max) = VD + VT  

Substituting:

VICM(max) = 0 + 0.36  

VICM(max) = 0.36 V  

### Final ICMR

−0.34 V ≤ VICM ≤ 0.36 V  



## Output Common Mode Range (OCMR)

The output common-mode range is the range of output voltage for which the circuit operates correctly and all transistors remain in saturation.

### Maximum Output Voltage

The maximum output voltage is limited by the supply voltage.

VOCM(max) = VDD  

VOCM(max) = 0.9 V  

### Minimum Output Voltage

To keep the transistor in saturation:

VDS ≥ VOV  

At the boundary:

VD − VS = VOV  

So,

VD = VS + VOV  

Since output is taken at drain:

VOCM(min) = VS + VOV  

Substituting values:

VS = −0.7 V  
VOV = 0.34 V  

VOCM(min) = −0.7 + 0.34  

VOCM(min) = −0.36 V  

### Final OCMR

−0.36 V ≤ VOCM ≤ 0.9 V  


## Transient Analysis and Linearity

We use transient analysis to check whether the differential amplifier is working linearly or not.

### Condition for Linearity

|Vid| < 2VOV  

2VOV = 2 × 0.34 = 0.68 V  



### Case 1: Linear Region
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20180618.png)


Input:

Vid = 100 mV < 0.68 V  

Observation:

Output waveform is smooth and sinusoidal  
No distortion is seen  
Both MOSFETs are in saturation  
Amplifier behaves properly (linear)  



### Case 2: Near Non-Linear Region
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20180841.png?raw=true)


Input:

Vid = 600 mV (close to 0.68 V limit)  

Observation:

Output waveform shows slight distortion  
Clipping starts appearing  
One transistor begins moving towards cutoff  
Gain is no longer perfectly constant  



### Explanation

When input is small, both transistors share current equally.  
So output is clean and proportional.

When input increases, current shifts more to one side.  
Because of this, distortion starts appearing.



### Conclusion

The amplifier works linearly only for small inputs.

|Vid| < 2VOV  

As input approaches or crosses this limit, the circuit becomes non-linear.



## Simulated Gain

Input signal:

Type: Sine wave  
Frequency = 1 kHz  
Amplitude = 50 mV  
DC Offset = 0 V  

Measured values:

Vin(pp) = 100 mV  

Vout(pp) ≈ 550 mV  

Voltage Gain:

Av = Vout / Vin  

Av ≈ 5.5  

Gain in dB:

Av(dB) ≈ 20 log(5.5) ≈ 14.8 dB  



## Theoretical Gain

Assume:

λ = 0.1 V⁻¹  

### Output Resistance

ro = 1 / (λ ID)  

ID = 0.61 mA  

ro ≈ 16.39 kΩ  

Effective output resistance:

ro_eff ≈ 8.2 kΩ  



### Transconductance

gm = 2ID / VOV  

gm ≈ 3.59 mS  



### Total Output Resistance

Rout = RD || ro_eff  

RD ≈ 1.475 kΩ  

Rout ≈ 1.25 kΩ  



### Differential Gain

Ad = gm × Rout  

Ad ≈ 4.49  

Gain in dB:

Ad(dB) ≈ 13.05 dB  



## Why Theoretical and Simulated Gain Are Different



There is always a small difference between calculated and simulated results.

### Reasons

Channel length modulation changes output resistance  

MOSFETs have finite output resistance  

Mobility degradation reduces gm  

Small variations in VOV change operating point  

Parasitic capacitances affect response  

Measurement from waveform may not be perfectly accurate  



##  Conclusion

The amplifier shows linear behavior only for small signals.

Theoretical gain assumes ideal conditions.  
Simulation includes real effects.

So, some difference between both values is expected and completely normal.


## AC Analysis
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/ac%20d.a.png)



In AC analysis, the frequency response of the differential amplifier is studied using a Bode plot.

The midband gain is taken from the flat portion of the gain curve.  
The bandwidth is defined between the lower cutoff frequency (fL) and upper cutoff frequency (fH) at −3 dB points.



### Midband Gain

From AC simulation:

Av ≈ 14.8 dB  

The −3 dB gain is:

Av(-3 dB) = 14.8 − 3  

Av(-3 dB) ≈ 11.8 dB  



### Cutoff Frequencies

Lower cutoff frequency:

fL ≈ 0 Hz  

Upper cutoff frequency:

fH ≈ 4.819 MHz  


### Bandwidth

BW = fH − fL  

BW ≈ 4.819 MHz  



## Unity Gain Bandwidth (UGB)

Since the 0 dB crossing is not clearly visible, UGB is estimated using:

UGB = Av × BW  

Av ≈ 5.5  

UGB ≈ 5.5 × 4.819 MHz  

UGB ≈ 26.5 MHz  



## Comparison of Results

Parameter            Theoretical        Simulated  
Voltage Gain (Av)    ≈ 4.49 V/V         ≈ 5.5 V/V  
Gain (dB)            ≈ 13.05 dB         ≈ 14.8 dB  



## Reason for Difference

The difference between theoretical and simulated results is due to practical effects.

Channel length modulation changes output resistance  

Finite output resistance affects gain  

Mobility degradation reduces transconductance  

Parasitic capacitances affect high-frequency response  

Operating point variations slightly change VOV  



## Inference

The MOS differential amplifier with resistive load is successfully designed and analyzed.

### Design Constraints

Power consumption ≤ 2.2 mW  
VDD = 0.9 V  
VSS = −0.9 V  
VOCM = 0 V  


### Biasing Details

The tail current is chosen as:

Itail ≈ 1.22 mA  

So that:

ID1 = ID2 ≈ 0.61 mA  

The source voltage is adjusted to:

VS ≈ −0.7 V  

This ensures both MOSFETs operate in saturation.



### Performance Summary

Theoretical gain ≈ 4.49 V/V (13.05 dB)  
Simulated gain ≈ 5.5 V/V (14.8 dB)  

Bandwidth ≈ 4.819 MHz  

Unity Gain Bandwidth ≈ 26.5 MHz  



### Frequency Response Observation

The amplifier shows a flat gain in midband region.  

At higher frequencies, gain decreases due to parasitic capacitances.  

This introduces a dominant pole and limits bandwidth.



### Conclusion

The differential amplifier works correctly under given constraints.

It provides:

Good linear amplification for small signals  

Expected gain close to theoretical value  

Proper frequency response  

When input increases beyond linear range, distortion appears.  

Overall, the circuit satisfies the design requirements and performs as expected.


## Circuit 2 :






