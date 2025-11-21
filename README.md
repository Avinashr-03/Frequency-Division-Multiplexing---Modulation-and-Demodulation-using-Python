# Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python

__Aim__:

To generate an FDM signal by multiplexing multiple baseband message signals on different carrier frequencies, transmit (sum) them, optionally add channel noise, then recover each message by bandpass filtering and coherent demodulation in Python (Google Colab). Observe time & frequency domain signals and measure recovery quality.


__Apparatus Required__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)


__Theory__:

FDM places different message signals in separate, non-overlapping frequency bands by modulating each message onto a distinct carrier frequency. The multiplexed signal is the sum of all modulated channels. At the receiver, bandpass filters (or tuned filters) isolate each channel; then each isolated carrier is demodulated (coherently multiplied by a synchronized carrier) and low-pass filtered to recover the original baseband.

__Procedure__:

1 — Imports and parameters

2 — Create message signals and carriers

3 — Modulate each message (standard AM DSB-SC) and form FDM signal

4 — Frequency domain (spectrum) of FDM signal

5 — (Optional) Add AWGN noise to FDM signal

6 — Receiver: isolate each channel with bandpass filter

7 — Demodulate each isolated channel (coherent) and low-pass filter to recover baseband
__PROGRAM__:
```asm
clc;
clear;
close;
Pt = 1000;
G = 40;
lambda = 0.05;
sigma = 10;
pi4 = (4*%pi)^3;
R = linspace(1e3, 200e3, 500);
Pr_R = (Pt .* G^2 .* lambda^2 .* sigma) ./ (pi4 .* R.^4);
subplot(3,1,1);
Pr_R_dB = 10 .* log10(Pr_R);
plot(R/1000, Pr_R_dB);
Pt_values = linspace(100, 10000, 500);
R_fixed = 50e3;
Pr_Pt = (Pt_values .* G^2 .* lambda^2 .* sigma) ./ (pi4 .* R_fixed.^4);
subplot(3,1,2);
plot(Pt_values, Pr_Pt);
G_values = linspace(5, 60, 500);
Pt_fixed = 3000;
Pr_G = (Pt_fixed .* G_values.^2 .* lambda^2 .* sigma) ./ (pi4 .* R_fixed.^4);
subplot(3,1,3);
plot(G_values, Pr_G);
```

__Output_:
<img width="1715" height="1010" alt="Screenshot 2025-11-20 234632" src="https://github.com/user-attachments/assets/b1dd8d0b-0d4d-45d0-9092-623180aa659b" />

![WhatsApp Image 2025-11-20 at 23 07 06_0b1a1678](https://github.com/user-attachments/assets/874b1d92-770b-4e31-9a82-27bf53b22a38)

__Result__:
Thus, the maximum range of a radar system calculated using the Radar Range Equation is successfully verified using Scilab programming.
