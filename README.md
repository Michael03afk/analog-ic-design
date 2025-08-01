#  MEMS Microphone Interface IC Design

A complete analog front-end (AFE) design for MEMS microphones, focusing on clean signal amplification, filtering, and buffering—ideal for embedded systems, audio sensing, and IoT applications.

---

## 📌 Overview

This design includes:

- ✅ Thevenin equivalent model of MEMS microphone
- ✅ Op-amp based preamplifier
- ✅ High-pass filter for noise/DC rejection
- ✅ Buffer stage for impedance isolation
- ✅ Simulations using Ngspice (.tran and .ac analysis)

---

##  Thevenin Equivalent Modeling

### SPL to Pressure Conversion

Using the formula:

```math
Pressure(Pa) 
 = 10^{\frac{60 - 94}{20}} \text{ Pa} = 19.95* 10^-3 Pa
```
### Output Voltage Model

```math
Vout(peak) = 2×19.95×10^−3 ×10{frac{-44}{20}} ≈0.178mV pk
```

### Symbolic Model
<img width="1280" height="666" alt="mic" src="https://github.com/user-attachments/assets/2b865430-d933-4ddb-bfa2-753f1a957b15" />


## 🎛️ Op-Amp Amplifier Stage

The op-amp amplifier stage in your MEMS microphone interface is essential for boosting the tiny audio signal coming from the MEMS mic (typically in microvolts to millivolts) to a level that can be further processed by filters, buffers, or an ADC.

Using SparkFun’s standard mic preamp design:

Rin = 5 kΩ

Rfb = 300 kΩ

Gain = 60

𝑉out = 60 × 0.178 mV = 10.68 mV pk 

ckt:--
<img width="1920" height="1080" alt="opamp_plot" src="https://github.com/user-attachments/assets/115af2b1-f9d2-4b4d-b837-15e4b0538fd5" />

## 🎚️ High-Pass Filter
To block DC and low-frequency rumble:

R = 5 kΩ
C = 4.7 µF
Cutoff Frequency(fc)
```math
 fc = 1/2πRC 
 ≈6.77Hz
```
 img:--
 <img width="1920" height="1020" alt="HighPassFilter" src="https://github.com/user-attachments/assets/7a53acfc-81b4-43c5-b14c-8c763eada597" />


## 🔌Buffer Stage

The buffer op-amp, also known as a voltage follower or unity-gain amplifier, plays a crucial role in analog signal chains

✅ Purpose of Buffer Op-Amp
-> Impedance Matching
-> Signal Isolation
-> Preserving Gain and Signal Integrity
 #### Inshort
⚙️ In MEMS Interface IC Project
After amplification and filtering, you’ve used a buffer before output. Here’s why that’s important:

Role	Description
Prevents loading	Without a buffer, the filter's capacitor and resistor might interact with the ADC input impedance, shifting the cutoff frequency.
Ensures stable signal	Provides a clean, stable signal to the next stage, especially important if your system includes long traces or ADCs with switching inputs.
Acts like an ideal wire	Transmits the voltage faithfully, but with the ability to source or sink current — unlike a real wire.
 
ckt :-

<img width="1920" height="1020" alt="opamp_model" src="https://github.com/user-attachments/assets/66e3fa45-8a0e-4fd5-a3f9-3394c368778c" />

## 📊 ckts , plots & waveforms

OP_AMP model


<img width="547" height="555" alt="opamp_sym" src="https://github.com/user-attachments/assets/3e8f0021-d827-4967-be5f-7681f9daa588" />

PLOTS & WAVEFORM :-


<img width="1920" height="1080" alt="plot" src="https://github.com/user-attachments/assets/6a59726e-4b0d-4199-85f5-8298d77dd050" /> 

### RESULTS
Simulations were performed using Ngspice:

AC analysis: Verified gain across frequency

Transient analysis: Observed time-domain waveform flow

Filter behavior: Confirmed 6.77 Hz cutoff

Buffer: Validated signal stability


### 📌 Summary
The Analog Front End (AFE) for a MEMS microphone involves:

Accurate modeling of sensor output

Clean amplification

Effective noise filtering

Output buffering

This analog interface ensures high-fidelity, low-noise, and ready-to-digitize signals from MEMS microphones.


### 👤 Contributors
Abhishek Mishra

B.Tech, Electronics & Instrumentation Engineering

SIC :- 23BEIH62




 
