EXPERIMENT – 01
# Objective

To design and develop a PMOS Common Source amplifier using 180 nm CMOS technology with the specified voltage and power constraints, and to study the performance of the amplifier using DC analysis, transient analysis, and AC analysis with the LTspice simulation software.


# Specifications Given

Supply Voltage (VDD) = 1.2 V

Maximum allowable power consumption ≤ 0.4 mW

Load Capacitance (CL) = 0.5 pF

Channel Length (L) = 360 nm

Components Needed

PMOS transistor (TSMC 180 nm model)

Drain resistor

DC power supply

Signal source

Capacitor


# Theory

MOSFETs are an essential part of modern integrated circuits due to their small size, low power dissipation, high input resistance, and suitability for scaled VLSI technology. Based on the type of charge carriers, MOSFETs are classified into NMOS and PMOS transistors. These transistors can be further divided into three basic amplifier configurations: Common Source (CS), Source Follower (Common Drain), and Common Gate.
Of these three configurations, the Common Source amplifier is the most commonly used in analog circuit design. This is primarily because of its capability to offer high voltage gain and a 180° phase difference between the input and output signals.
For the PMOS transistor to properly amplify, it must work in the saturation region, where it acts as a voltage-controlled current source. To guarantee that the PMOS transistor is in the saturation region, certain biasing requirements must be met. These requirements for saturation are given by:

# Saturation Conditions of PMOS

For a PMOS transistor to work in the saturation region, the following conditions are required:
VSG > |VT|
VSD ≥ VSG − |VT|
Overdrive Voltage :
VOV = VSG − |VT|


# Procedure

Install and include the TSMC 180 nm technology library in LTspice.

Assemble the PMOS Common Source amplifier circuit by making the following connections:

Source to VDD

Drain to a load resistor (RD)

Gate to appropriate DC biasing and AC input signal

Body connection to source

Load capacitor connected at the output node

Assign the channel length (L) to 360 nm and enter an initial value for the width (W) of the transistor.

Perform DC operating point analysis.

Vary the width of the transistor until the required drain current and output voltage are obtained within the prescribed power limit.

Check that the transistor meets the saturation requirement.

Apply a sinusoidal input signal and execute transient analysis.

Carry out small-signal AC analysis using 1 V AC input signal.

Compare theoretical calculations with simulation data.


# Design Calculations.

1. Drain Current Calculation

Using the power equation:

P = VDD × ID

ID = P / VDD

ID = 0.4 mW / 1.2 V

ID = 0.333 mA

To stay well under the power constraint, select:

ID ≈ 250 µA

2. PMOS Width Calculation

The drain current in saturation is expressed as:

ID = (1/2) μp Cox (W/L) (VOV)²

The given parameters are:

μp = 0.0115689 m²/V·s
Cox = 0.0084207 F/m²
L = 360 nm = 360 × 10⁻⁹ m
VOV = 0.2094 V
ID = 250 µA = 250 × 10⁻⁶ A


# Substituting these parameters into the equation:

W ≈ 42 µm

3. Output Voltage

For maximum symmetrical swing:

VD ≈ VDD / 2

VD ≈ 0.6 V

4. Drain Resistance

RD = VD / ID

RD = 0.6 / (250 µA)

RD = 2.4 kΩ

5. Gate–Source Voltage

|VT| = 0.3906 V


# Choose:

VSG ≈ 0.6 V

Overdrive voltage:

VOV = 0.6 − 0.3906

VOV = 0.2094 V

6. Gate Voltage

VS = 1.2 V

VG = VS − VSG

VG = 1.2 − 0.6

VG = 0.6 V

7. Saturation Verification

VSD = VS − VD

VSD = 1.2 − 0.6

VSD = 0.6 V

Since VSD > VOV, the PMOS transistor operates in the saturation region.

# Final Calculated Values

ID ≈ 250 µA
VD ≈ 0.6 V
RD = 2.4 kΩ
VG = 0.6 V
VOV = 0.2094 V


# circuit

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/3.jpeg?raw=true)




























# DC Analysis
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/1.jpeg?raw=true)

DC analysis is performed to find the operating point (Q-point) of the PMOS transistor. The DC analysis is performed to ensure that the PMOS transistor is operating in the saturation region. This is required for linear amplification with minimal distortion. The DC analysis is also performed to ensure that the circuit components are properly biased and to check the circuit component stability.

Initial Simulation Results

After the DC operating point analysis, the results obtained were:

ID ≈ 149 µA
Vout ≈ 0.359 V

The simulation results were lower than the theoretical values obtained. This difference is due to the practical effects of the devices, such as short-channel effects and carrier mobility reduction, which are not considered in the simulation.

Modified Design (Width Increased to 72 µm)

In order to obtain the desired operating point, the width of the transistor was increased to 72 µm. After re-running the DC analysis, the results were:

ID ≈ 247 µA
Vout ≈ 0.59 V

The results are much closer to the theoretical design requirements, ensuring that the PMOS transistor is properly biased and is operating in the saturation region.


# Transient Analysis
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/2.jpeg?raw=true)

The transient analysis is carried out to analyze the time-domain behavior of the amplifier. This helps in analyzing the signal amplification, phase reversal, distortion, and overall dynamic behavior of the circuit. By performing this analysis, we can check whether the output signal is amplified and phase-reversed correctly with respect to the input signal.

Gain Calculation
Theoretical Gain

The transconductance value is calculated as:

gm = 2ID / VOV

gm = 2(250 µA) / 0.2094

gm ≈ 2.39 mS

Voltage gain:

Av = gm × RD

Av = 2.39 mS × 2.4 kΩ

Av ≈ 5.736

Gain in decibels:

Gain (dB) = 20 log10(Av)

Gain ≈ 15.16 dB

Simulated Gain

From transient simulation:

Input peak-to-peak voltage = 20 mV
Output peak-to-peak voltage = 136.05 mV

Voltage gain:

Av = 136.05 / 20

Av ≈ 6.80

Gain in decibels:

Gain (dB) = 20 log10(6.80)

Gain ≈ 16.65 dB

The slight difference between the theoretical and simulated gain values is primarily because of the channel length modulation, absence of output resistance, and short-channel effects in practical CMOS transistors.


# AC Analysis
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/4.jpeg?raw=true)

AC analysis is performed to find the frequency response, mid-band gain, bandwidth, and unity gain bandwidth of the amplifier.

Mid-Band Gain

From the AC frequency response graph:

Gain ≈ 16.912 dB

This is equivalent to:

Av ≈ 6.8 V/V

Bandwidth

The theoretical bandwidth is expressed as:

BW = 1 / (2π RD CL)

BW = 1 / (2π × 2.4 kΩ × 0.5 pF)

BW ≈ 132.63 MHz

From simulation:

Bandwidth ≈ 131.8 MHz

The simulated result is almost the same as the theoretical value.

Unity Gain Bandwidth (UGB)

UGB = Av × BW

UGB = 6.8 × 131.8 MHz

UGB ≈ 896 MHz

From simulation:

Observed UGB ≈ 913 MHz


# Result

The PMOS Common Source amplifier design and simulation were accomplished successfully.

DC analysis validated correct saturation biasing.

Transient analysis revealed amplified output with phase reversal.

AC analysis revealed a mid-band gain of approximately 6.8 V/V and a bandwidth near the theoretical value.

Therefore, the amplifier design satisfies the specified design requirements.


# Inference

The fact that the theoretical and simulation values match validates the design methodology.

Appropriate saturation biasing is necessary for linear amplification.

Transient analysis confirms the time-domain signal integrity.

AC analysis confirms the gain and bandwidth specifications.

Therefore, the PMOS Common Source amplifier circuit is valid for low-power CMOS analog circuit designs.




