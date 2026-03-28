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

|Vid| < √2 VOV 





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

|Vid| > √2 VOV

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
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20190127.png)



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

# Differential Amplifier Design (Circuit 2)

## Given Parameters

Technology: TSMC 180 nm  
Supply Voltage VDD = +0.9 V  
Negative Supply VSS = −0.9 V  
Power Constraint P ≤ 2.2 mW  
Channel Length L = 540 nm  



## Design Objective

To design a CMOS differential amplifier satisfying:

- Tail current ISS ≈ 1.22 mA  
- Source node voltage Vp ≈ −0.7 V  
- All MOSFETs operating in saturation region  



## Current Calculation

From power constraint:

P = VDD × ISS  

ISS = P / VDD  

ISS = 2.2 mW / 1.8 V  

ISS ≈ 1.22 mA  



## Transistor Dimensions

### Input Differential Pair

M1:
W = 36 µm  
L = 540 nm  

M2:
W = 36 µm  
L = 540 nm  



### Tail Current Source

M5:
W = 228 µm  
L = 540 nm  



## Biasing Condition

Gate voltage of M5 is adjusted such that:

Vp ≈ −0.7 V  

This ensures proper biasing and saturation of M5.



## DC Operating Point Analysis

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20201112.png)


Expected results:



Tail current:
ISS ≈ 1.22 mA  

Current through each branch:
ID1 = ID2 ≈ 0.61 mA  

Node voltage:
Vp ≈ −0.7 V  

Output nodes:
Vout1 ≈ Vout2 (symmetrical under zero differential input)



## Condition for Linearity

|Vid| < √(2 × Vov)

Where Vov is the overdrive voltage of input transistors.



## Region of Operation

For proper operation:

- M1, M2 must be in saturation  
- M5 must be in saturation  

Saturation condition:

VDS ≥ VGS − Vth  



## Design Insight

- M5 controls the tail current ISS  
- Increasing W5 increases ISS  
- M1 and M2 control transconductance and gain  
- Proper bias ensures symmetrical operation  



## Final Design Summary

Channel Length for all MOSFETs:
L = 540 nm  

M1, M2:
W = 36 µm  

M5:
W = 228 µm  

Tail Current:
ISS ≈ 1.22 mA  

Source Voltage:
Vp ≈ −0.7 V  



## Conclusion

The differential amplifier is successfully designed to meet:

- Power constraint ≤ 2.2 mW  
- Tail current ≈ 1.22 mA  
- Proper biasing with Vp ≈ −0.7 V  

The circuit operates in saturation and provides balanced differential operation.

##  Input Common Mode Range (ICMR)

The input common-mode range is defined as the range of input voltage for which all transistors remain in saturation.

### Minimum Input Common Mode Voltage

For proper operation:
- NMOS transistors M1 and M2 must remain ON  
- Tail current source M5 must remain in saturation  

Condition:

VGS1 ≥ VT  

Using:

VGS1 = VICM − VS  

So,

VICM(min) = VS + VT  

Substituting:

VS = −0.7 V  
VT = 0.36 V  

VICM(min) = −0.7 + 0.36  

VICM(min) = −0.34 V  



### Maximum Input Common Mode Voltage

For proper operation:
- PMOS transistors M3 and M4 must remain in saturation  

Condition:

VSD ≥ VOVp  

Using:

VSD = VDD − VD  

At saturation boundary:

VSD = VSG − |VTP|  

Also:

VSG = VDD − VICM  

So,

VDD − VD = (VDD − VICM) − |VTP|  

Rearranging:

VICM(max) = VD + |VTP|  

Substiting:

VD ≈ 0 V  
|VTP| ≈ 0.39 V  

VICM(max) = 0 + 0.39  

VICM(max) = 0.39 V  



### Final Input Common Mode Range

−0.34 V ≤ VICM ≤ 0.39 V  



##  Output Common Mode Range (OCMR)

The output common-mode range is defined as the range of output voltage for which all transistors remain in saturation.

### Minimum Output Common Mode Voltage

For proper operation:
- NMOS transistors M1 and M2 must remain in saturation  

Condition:

VDS1 ≥ VOVn  

Using:

VDS1 = Vout − VS  

So,

Vout(min) − VS ≥ VOVn  

Vout(min) ≥ VS + VOVn  

Substituting:

VS = −0.7 V  
VOVn = 0.34 V  

Vout(min) = −0.7 + 0.34  

Vout(min) = −0.36 V  



### Maximum Output Common Mode Voltage

For proper operation:
- PMOS transistors M3 and M4 must remain in saturation  

Condition:

VSD ≥ VOVp  

Using:

VSD = VDD − Vout  

So,

VDD − Vout(max) ≥ VOVp  

Vout(max) ≤ VDD − VOVp  

Substituting:

VDD = 0.9 V  
VOVp ≈ 0.25 V  

Vout(max) = 0.9 − 0.25  

Vout(max) = 0.65 V  



### Final Output Common Mode Range

−0.36 V ≤ Vout ≤ 0.65 V  



## Differential Input Voltage Range (Linear Region)

The differential amplifier operates in the linear region as long as both transistors M1 and M2 remain ON and share the tail current.

The differential input voltage is defined as:

vid = vin1 − vin2  



### Condition for Linear Operation

- Both transistors must remain ON  
- Tail current must be shared between M1 and M2  
- One transistor should not turn OFF  



### Maximum Differential Input Voltage

At the boundary of linear operation:

vid(max) = 2 VOVn  

Substituting:

VOVn = 0.34 V  

vid(max) = 2 × 0.34  

vid(max) = 0.68 V  



### Final Differential Input Range

−0.68 V ≤ vid ≤ 0.68 V  

## 2.3 Transient Analysis and Linearity Observation


The linear behavior of the differential amplifier with PMOS active load is verified using transient analysis.



### Condition for Linearity

The amplifier operates linearly when:

|v_id| < √2 · V_OV

Using:

V_OV = 0.24 V  

So,

√2 · V_OV = 1.414 × 0.24 = 0.339 V ≈ 0.34 V



## Case 1: Linear Region

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20201327.png)


**Input applied:**

v_id = 100 mV < 0.34 V  

(Circuit 2)

### Observation

- Output waveform is sinusoidal  
- No distortion observed  
- Both NMOS transistors (M1, M2) operate in saturation  
- PMOS load transistors (M3, M4) remain in saturation  
- Amplifier behaves linearly  



## Case 2: Non-Linear Region

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20201705.png)


**Input applied:**

v_id = 600 mV > 0.34 V  



### Observation

- Output waveform shows distortion and clipping  
- One transistor (M1 or M2) enters cutoff  
- Current is steered completely to one branch  
- PMOS load still operates, but amplification becomes non-linear  



## Comparison Table

| Parameter | Case 1: Linear Region | Case 2: Non-Linear Region |
|----------|----------------------|--------------------------|
| Condition | v_id < √2 V_OV | v_id > √2 V_OV |
| Input (v_id) | 100 mV | 600 mV |
| Output waveform | Sinusoidal | Distorted / Clipped |
| Gain | Constant | Reduced / Non-linear |
| Transistor operation | All in saturation | One NMOS in cutoff |
| Current distribution | Shared between M1 & M2 | Current flows in one branch |



## Interpretation

In the linear region, the differential input is small and both NMOS transistors conduct simultaneously.  
The tail current is shared between the two branches, resulting in a proportional and undistorted output.

In the non-linear region, the differential input exceeds the limit (√2 V_OV), causing one transistor to carry almost the entire tail current while the other turns OFF. This leads to distortion and loss of linearity.



## Conclusion

The differential amplifier operates linearly only for small input signals:

|v_id| < √2 · V_OV ≈ 0.34 V  

When:

|v_id| > 0.34 V  

the circuit exhibits non-linear behavior due to current steering and transistor cutoff.
## Theoretical and Simulated Gain



The output waveform is amplified and inverted.



## Simulated Gain

### Input Signal Parameters

- Type: Sine wave  
- Frequency = 1 kHz  
- Amplitude = 50 mV (applied differentially)  
- DC Offset = 0 V  



### Measured Peak-to-Peak Values

V_in(p-p) = 50 mV − (−50 mV) = 100 mV  

V_out(p-p) = 106 mV − (−75 mV) = 181 mV  



### Voltage Gain

A_v = V_out(p-p) / V_in(p-p)  

A_v = 181 / 100  

A_v = 1.81  



### Gain in dB

A_v(dB) = 20 log₁₀(1.81)  

A_v(dB) ≈ 5.15 dB  



## Theoretical Gain

### Assumptions (Based on Final Design)

- λ = 0.1 V⁻¹  
- I_D = 0.61 mA  
- V_OV = 0.297 V  



### Output Resistance

r_o = 1 / (λ I_D)  

r_o = 1 / (0.1 × 0.61 × 10⁻³)  

r_o ≈ 16.39 kΩ  



### Effective Output Resistance

r_o,eff = r_on || r_op  

r_o,eff = 16.39k || 16.39k  

r_o,eff ≈ 8.20 kΩ  



### Transconductance

g_m = 2I_D / V_OV  

g_m = (2 × 0.61 mA) / 0.297  

g_m = (1.22 mA) / 0.297  

g_m ≈ 4.11 mS  



### Total Output Resistance

R_out = r_o,eff  

R_out ≈ 8.20 kΩ  



### Differential Gain

A_d = g_m × R_out  

A_d = 4.11 mS × 8.20 kΩ  

A_d ≈ 33.7  



### Gain in dB

A_d(dB) = 20 log₁₀(33.7)  

A_d(dB) ≈ 30.55 dB  


## Reason for Difference Between Theoretical and Simulated Gain

A deviation is observed between the theoretical and simulated gain values due to practical non-idealities.



### Reasons for Deviation

#### 1. Channel Length Modulation

λ varies with bias in simulation:

r_o = 1 / (λ I_D)

This reduces gain.



#### 2. Finite Output Resistance of Active Load

R_out = r_on || r_op  

Any mismatch lowers effective gain.



#### 3. Mobility Degradation

Reduces transconductance:

g_m = 2I_D / V_OV  



#### 4. Variation in Overdrive Voltage (V_OV)

Operating point variations affect gain.



#### 5. Current Source Non-Ideality (M5)

- Finite output resistance  
- Slight current variation  



#### 6. Parasitic Capacitances

Reduce gain slightly in practical operation.



#### 7. Measurement Method

Minor inaccuracies due to waveform measurement.



## Conclusion

The difference between theoretical (~33.7) and simulated (~1.81) gain is expected.

This deviation arises due to:
- Non-ideal MOSFET behavior  
- Finite output resistances  
- Large-signal operation  

The circuit operation is successfully validated.




## AC Analysis

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20210250.png?raw=true)



In AC analysis, the frequency response of the differential amplifier is observed.

The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the frequency range between the lower cutoff frequency (f_L) and upper cutoff frequency (f_H), measured at the −3 dB points.



## Midband Gain

From AC simulation:

A_v = 5.2 dB  

The −3 dB gain is:

A_v(-3 dB) = 5.2 − 3  

A_v(-3 dB) = 2.2 dB  



## Cutoff Frequencies

Lower cutoff frequency:

f_L = 0 Hz  

Upper cutoff frequency:

f_H = 2.2 GHz  



## Bandwidth

Bandwidth is defined as:

BW = f_H − f_L  

BW = 2.2 − 0  

BW = 2.2 GHz  



##  Unity Gain Bandwidth (UGB)

Unity gain frequency:

f_0dB ≈ 4.8 GHz  

UGB is given by:

UGB = A_v × f_H  

Using linear gain:

A_v = 1.81  

UGB = 1.81 × 4.8 GHz  

UGB ≈ 8.69 GHz  



## Note

First-order theoretical analysis assumes ideal MOSFET operation in saturation and neglects higher-order effects such as:

- Channel length modulation  
- Mobility degradation  
- Finite output resistance of current sources  
- Parasitic capacitances  

These non-ideal effects are included in simulation, leading to differences between theoretical and simulated results.



## Comparison of Results

| Parameter | Theoretical | Simulated |
|----------|------------|----------|
| Voltage Gain (A_v) | 33.7 V/V | 1.81 V/V |
| Gain (dB) | 30.55 dB | 5.15 dB |

The deviation between theoretical and simulated gain is mainly due to simplified first-order assumptions and the presence of non-ideal MOSFET effects.



## Inference

The MOS differential amplifier with PMOS active load and NMOS current source was successfully designed and analyzed while satisfying the given design constraints:

- Power consumption ≤ 1.8 mW  
- V_DD = 0.9 V  
- V_SS = −0.9 V  
- V_ocm = 0 V  



### Current Distribution

The tail current is:

I_tail = 1.22 mA  

Under balanced conditions:

I_D1 = I_D2 = 0.61 mA  



### Biasing Condition

All transistors (M1, M2, M3, M4, M5) are maintained in saturation.

The tail node voltage:

V_S ≈ −0.7 V  


## Gain Observation

Theoretical and simulated results show a significant deviation:

- Theoretical gain ≈ 33.7 V/V (30.55 dB)  
- Simulated gain ≈ 1.81 V/V (5.15 dB)  



## Reasons for Gain Reduction

This difference arises due to non-ideal effects:

- NMOS current source (M5) has finite output resistance  
- PMOS active load (M3, M4) is not ideal  
- Channel length modulation reduces output resistance  
- Mobility degradation reduces transconductance  



## Frequency Response Observation

From AC analysis:

- The amplifier shows a flat midband gain  
- Gain rolls off at higher frequencies  
- This is due to parasitic capacitances and load capacitance  

These introduce a dominant pole and limit bandwidth.



## Linearity Behavior

The differential amplifier provides linear amplification for small signals.

For large input signals:

- Current steering occurs  
- One transistor turns OFF  
- Distortion and non-linearity appear  



## Final Conclusion

The designed differential amplifier demonstrates:

- Correct biasing  
- Proper saturation operation  
- Expected frequency response  

However, the results highlight the significant impact of non-ideal MOSFET behavior on gain when using active loads and current sources.















## Circuit 3: CMOS Differential Amplifier with PMOS Active Load (Bias-Controlled Load)





## Working Principle

The circuit consists of two matched NMOS transistors (M1 and M2) forming a differential pair, with their sources connected together and biased by a constant tail current source (M5). The drains of M1 and M2 are connected to PMOS transistors (M3 and M4), which act as active loads.

The gates of the PMOS transistors are connected to a bias voltage Vb2, ensuring they operate as current sources.

When a differential input is applied:

v_id = v_in1 − v_in2

the tail current ISS is steered between M1 and M2:

- If v_in1 > v_in2 → M1 carries more current  
- If v_in2 > v_in1 → M2 carries more current  

The PMOS load converts current variation into output voltage, providing high gain.



## Design Calculations

### GIVEN PARAMETERS

- Technology: TSMC 180nm  
- VDD = +0.9 V  
- VSS = −0.9 V  
- Power ≤ 2.2 mW  
- L (M1, M2) = **540 nm**  
- Vin,CM = 0 V  
- Vo,CM = 0 V  
- Vp = −0.7 V  
- CL = 10 pF  
- VT ≈ 0.36 V
- ![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20224308.png?raw=true)



## Power Constraint

P = (VDD − VSS) × ISS  

= 1.8 × ISS  

Given:

P ≤ 2.2 mW  

ISS ≤ 2.2 / 1.8  

 ISS ≤ 1.22 mA  

Choose:

 ISS = **1.22 mA**

Power:

P = 1.8 × 1.22  

 P = **2.196 mW** 



## Circuit 3: CMOS Differential Amplifier with PMOS Active Load

 ![Image description](https://github.com/Prabhu-h7/LIC/blob/main/Screenshot%202026-03-28%20231038.png)


## Power Constraint Verification

The total power consumed by the circuit is given by:

P = (VDD − VSS) × ISS  

Substituting supply values:

VDD − VSS = 0.9 − (−0.9) = 1.8 V  

So,

P = 1.8 × ISS  

Given constraint:

P ≤ 2.2 mW  

Therefore,

ISS ≤ 2.2 / 1.8  

ISS ≤ 1.22 mA  

For design:

 ISS = 1.22 mA  

Power dissipation:

P = 1.8 × 1.22 = 2.196 mW  

 Condition satisfied


## Current Distribution in Differential Pair

For zero differential input:

Vin1 = Vin2  

The tail current splits equally:

ID1 = ID2 = ISS / 2  

Substituting:

ID1 = ID2 = 1.22 / 2  

ID1 = ID2 = 0.61 mA  



## Drain-Source Voltage Evaluation

Output common-mode voltage:

VOCM = 0 V  

Thus:

VD = 0 V  

Given tail node voltage:

VP = −0.7 V  

Drain-source voltage becomes:

VDS = VD − VS  

VDS = 0 − (−0.7)  

VDS = 0.7 V  



## Gate-Source and Overdrive Voltage

Gate voltage:

VG = 0 V  

Source voltage:

VS = −0.7 V  

Therefore:

VGS = VG − VS  

VGS = 0 − (−0.7)  

 VGS = 0.7 V  
Overdrive voltage:

VOV = VGS − VTH  

VOV = 0.7 − 0.36  

 VOV ≈ 0.34 V  

(Design adjusted value: ≈ 0.297 V)


##  Region of Operation Check

Condition for saturation:

VDS > VOV  

Substitute:

0.7 > 0.297  

 NMOS transistors operate in saturation



##  Tail Current Source (M5)

Voltages:

VS = −0.9 V  
VD = −0.7 V  

Thus:

VDS5 = VD − VS  

VDS5 = −0.7 − (−0.9)  

 VDS5 = 0.2 V  

To ensure saturation:

VOV5 ≈ 0.2 V  

Then:

VGS5 = VTH + VOV5  

VGS5 = 0.36 + 0.2  

VGS5 = 0.56 V  

Gate voltage:

VG5 = VS + VGS5  

VG5 = −0.9 + 0.56  

 VG5 = −0.34 V  

 M5 operates at saturation boundary



##  PMOS Active Load (M3, M4)

Source voltage:

VS = 0.9 V  

Drain voltage:

VD = 0 V  

Thus:

VSD = 0.9 V  

For saturation:

VSD ≥ VSG − |VTP|  

Choosing:

VG ≈ −0.36 V  

Then:

VSG = 0.9 − (−0.36) = 1.26 V  

VOVp = 1.26 − 0.39  

 VOVp ≈ 0.87 V  

 PMOS operates in saturation


##  Width Calculation of Tail Transistor (M5)

Using:

W = (2ID L) / (μnCox × VOV²)

Substitute:

ID = 1.22 mA  
L = 540 nm  
VOV = 0.2 V  

W5 = (2 × 1.22×10⁻³ × 540×10⁻⁹) / (2.306×10⁻⁴ × (0.2)²)

 W5 ≈ 139 µm  



##  Width of NMOS Pair (M1, M2)

ID = 0.61 mA  
L = 540 nm  
VOV = 0.297 V  

W = (2 × 0.61×10⁻³ × 540×10⁻⁹) / (2.306×10⁻⁴ × (0.297)²)

W1 = W2 ≈ 31.6 µm  



## 3.10 Width of PMOS Load (M3, M4)

ID = 0.61 mA  
L = 540 nm  
VOVp = 0.87 V  

W = (2 × 0.61×10⁻³ × 540×10⁻⁹) / (9.98×10⁻⁵ × (0.87)²)

 W3 = W4 ≈ 8.7 µm  



## Final Design Summary

| Transistor | Width |
|----------|--------|
| M1, M2 | 31.6 µm |
| M3, M4 | 8.7 µm |
| M5 | 139 µm |



## Conclusion

The differential amplifier is designed using:

- ISS = 1.22 mA  
- Power = 2.196 mW (within limit)  
- Channel length = 540 nm  

All MOSFETs are biased in saturation, ensuring proper operation. The circuit achieves balanced current distribution and efficient amplification using PMOS active loads.




