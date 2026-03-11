# EXPERIMENT – 03  
## Virtual Lab  
### Characterization and Parameter Extraction of µA741 Operational Amplifier

## Aim

The aim of the experiment is to measure the parameters of the µA741 operational amplifier IC and compare them with the standard values given in the datasheet of the IC.



## Apparatus Required

The apparatus required for the experiment are:

- µA741 IC  
- Dual DC Power Supply  
- Digital Multimeter  
- Function Generator/A.F. Oscillator  
- CRO/DSO  
- Breadboard  
- Connecting wires  



## Function Generator

A function generator is a type of electronic test equipment used for generating various types of electrical waveforms or signals. These signals are required for the analysis of electronic circuits and devices.



# Measurement of Inverting Bias Current (IB₁)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p1.png?raw=true)


![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p2.png?raw=true)

IB₁ is the inverting bias current, i.e., the current flowing into the inverting input terminal of the operational amplifier IC.


## Procedure

1. The electronic components to be used need to be placed on the workstation.  
2. The circuit for measuring the inverting bias current has to be connected. The connections have to be made exactly as shown in the circuit diagram.  
3. The connections have to be verified using the **Check Connection** option.  
4. Once the connections have been verified, the output voltage has to be measured using the digital multimeter.

## Formula


IB₁ = Vo/Rf
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p3.png?raw=true)


## Given Values


Vo = 0.024 V  
Rf = 470 kΩ = 470000 Ω


## Calculation


IB₁ = 0.024/470000  
IB₁ = 5.106 x 10⁻⁸ A


Converting to nanoampere:


IB₁ ≈ 51 nA
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p4.png?raw=true)

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p5.png?raw=true)

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p6.png?raw=true)




# Measurement of Non-Inverting Bias Current (IB₂)

The non-inverting bias current is the current entering the non-inverting terminal of the operational amplifier.

## Procedure

1. The circuit for measuring the non-inverting bias current has to be connected exactly as shown in the diagram.  
2. The connections have to be carefully verified.  
3. The output voltage has to be measured using the digital multimeter.

## Formula


IB₂ = Vo/R₁


## Given Values


Vo = -0.020 V  
R₁ = 470 kΩ = 470000 Ω

## Calculation


IB₂ = -0.020 / 470000
IB₂ = -4.255 * 10^-8 A


Considering the magnitude:


IB₂ ≈ 42.6 nA

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p7.png?raw=true)

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p8.png?raw=true)

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p9.png?raw=true)


# Input Bias Current (IB)

Input bias current is the average value of the bias currents for the inverting input and the non-inverting input.

## Formula


IB = (IB1 + IB2)/2


## Calculation


IB = (51 + 42.6)/2
IB ≈ 46.8 nA




# Measurement of Input Offset Current (Iio)

Input offset current is the difference between the input bias currents for the two input terminals.

## Procedure

1. The circuit is connected as shown in the input offset current measurement circuit diagram.  
2. The connections to the circuit should be confirmed.  
3. The output voltage is measured using the digital multimeter.

## Formula


Iio = Vo / Rf


## Given Values

Vo = 0.003 V
Rf = 470 kΩ = 470000 Ω

## Calculation


Iio = 0.003 / 470000  
Iio = 6.38 × 10⁻⁹ A


Converted units:


Iio = 6.38 nA  
Iio = 0.00638 µA
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p10.png?raw=true)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p11.png?raw=true)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p12.png?raw=true)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p13.png?raw=true)




# Measurement of Input Offset Voltage (Vio)

Input offset voltage is the small voltage that needs to be applied between the input terminals so that the output voltage is zero.

## Procedure

1. The circuit is connected as in the diagram.  
2. The connections are properly ensured before the measurement.  
3. The output voltage is measured using the digital multimeter.

## Formula


Vio = Vo / (1 + Rf / Ri)


## Given Values


Vo = 0.106 V  
Rf = 100 kΩ  
Ri = 10 kΩ

## Calculation


Vio = 0.106 / (1 + 100k / 10k)
Vio = 0.106 / (1 + 10)
Vio = 0.106 / 101
Vio = 0.001048 V


Converted to millivolts:


Vio ≈ 1.048 mV

![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p14.png?raw=true)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p15.png?raw=true)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p16.png?raw=true)
![Image description](https://github.com/Prabhu-h7/LIC/blob/main/p17.png?raw=true)





# Measurement of Slew Rate (SR)

Slew rate is the maximum rate at which the output voltage of an op-amp changes with respect to time.

## Procedure

1. Connect the circuit for slew rate measurement as shown in the diagram.  
2. Apply an input signal using the function generator.  
3. Connect the input signal to Channel-1 of the CRO and the output signal to Channel-2.  
4. Gradually increase the frequency of the input signal until the output waveform becomes triangular.  
5. Record this frequency as the maximum frequency (**fmax**).

## Formula


SR = (2π fmax Vm) / 10⁶ V/µs


## Given Values


Vm = 3 V
fmax = 25 kHz = 25000 Hz


## Calculation


SR = (2π × 25000 × 3) / 10⁶
SR = 471000 / 10⁶
SR ≈ 0.471 V/µs

# Result
The parameters of the µA741 Operational Amplifier based on the experiment conducted above can be summarized as follows:
 **Inverting Bias Current (IB₁)**: 51 nA  
 **Non-Inverting Bias Current (IB₂)**: 42.6 nA  
 **Average Input Bias Current (IB)**: 46.8 nA  
 **Input Offset Current (Iio)**: 6.38 nA  
 **Input Offset Voltage (Vio)**: 1.048 mV  
 **Slew Rate (SR)**: 0.471 V/µs  

These parameters have approximate values similar to the standard parameters of the µA741 Operational Amplifier.


# Inference
In this experiment, important parameters of the µA741 Operational Amplifier have been determined.The results obtained in terms of input bias current, input offset 
current, input offset voltage, and slew rate are close to the values mentioned in the datasheet. As the experiment is conducted in a controlled environment, the effects of 
temperature variation and component tolerance are negligible.This experiment verifies the performance characteristics of the µA741 operational amplifier.  It proves that the µA741 
operational amplifier is useful in low-frequency analog applications.
