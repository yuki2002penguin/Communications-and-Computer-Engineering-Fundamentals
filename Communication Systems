# Communication Systems

[cite_start]**Date:** 2026.4.16 [cite: 26]


---

## 1. Introduction

### 1.1 Basic Elements of a Digital Communication System
[cite_start]Information such as analog (audio or video) signals, or digital signals. [cite: 31, 32, 33]

* [cite_start]**Transmitter side:** Information source $\rightarrow$ Source encoder (Bit sequence) $\rightarrow$ Channel encoder (Encoded bit sequence) $\rightarrow$ Digital modulator (Modulated signals) [cite: 34, 35, 36, 37, 38, 41, 42, 43, 44]
* [cite_start]**Channel:** Wired or Wireless. [cite: 39, 54, 55]
* [cite_start]**Receiver side:** Digital demodulator $\rightarrow$ Channel decoder (Detected bit sequence) $\rightarrow$ Source decoder (Decoded bit sequence) $\rightarrow$ Recovered information [cite: 56, 57, 58, 59, 60, 61, 63, 64, 65, 66]

**Purpose of Channel Encoder:**
[cite_start]To introduce redundancy so as to overcome the effects of noise and interference. [cite: 45, 46, 47]

**Basic Elements of an Analog Communication System:**
[cite_start]Information source $\rightarrow$ Analog modulator (Analog signal $\rightarrow$ Modulated signals) $\rightarrow$ Channel (Wired or Wireless) $\rightarrow$ Analog demodulator $\rightarrow$ Recovered information [cite: 49, 50, 51, 52, 53, 54, 55, 56, 68, 70, 71, 72, 73, 74, 75]

### 1.2 Analog and Digital Signals
[cite_start]Signals are electric current or voltage waveforms into which physical quantities such as sound and image are converted, and can be considered functions of time. [cite: 80]

* [cite_start]**Analog signal:** a time-continuous waveform having continuous values. [cite: 81]
* [cite_start]**Digital signal:** a discrete-time waveform having discrete values (a unit multiplied by an integer, the integer is expressed in a binary number). [cite: 81]

### Advantages of Digital Modulation
1.  [cite_start]High accuracy and adaptive control are possible. [cite: 101]
2.  [cite_start]To combine several signals and to send them together are possible. [cite: 102, 103]
3.  [cite_start]Signals (Information) can be sent in packet form. [cite: 104]
4.  [cite_start]Band compression, forward error correction, and encryption techniques can be implemented. [cite: 105, 106]

[cite_start]**Conclusion:** Digital modulation overwhelms analog modulation. [cite: 108]

---

## 2. Typical Channel (Linear Time-Invariant System)

### 2.1 Linear Time-Invariant System
[cite_start]A structure of the general system: Input signal $x(t) \rightarrow$ System $\rightarrow$ Output signal $y(t) = L[x(t)]$ [cite: 114, 115, 116, 117]
[cite_start]The most important system for communications is the linear time-invariant system. [cite: 118]

**Conditions for the linear time-invariant system:**
1.  **Linear system:**
    $L[a_{1}x_{1}(t) + a_{2}x_{2}(t)] = a_{1}L[x_{1}(t)] + a_{2}L[x_{2}(t)]$ [cite: 121, 122]
    ($a_{1}, a_{2}$ arbitrary constants) [cite: 124]
2.  **Time-invariant system:**
    $y(t - \tau) = L[x(t - \tau)]$ ($\tau$ is an arbitrary real number.) [cite: 126, 127]

**Representation of the linear time-invariant system:**
Input signal $x(t)$ is expressed as:
[cite_start]$x(t) = \int_{-\infty}^{\infty} x(\tau)\delta(t - \tau)d\tau$ ($\delta(t)$: delta function) [cite: 130, 131, 132]

Using the condition for the linear system, output signal is given by:
[cite_start]$y(t) = L[x(t)] = \int_{-\infty}^{\infty} x(\tau)L[\delta(t - \tau)]d\tau$ [cite: 133, 134]

[cite_start]The impulse response $h(t)$ is defined as $h(t) = L[\delta(t)]$. [cite: 135]
[cite_start]Using the condition for the time-invariant system: $h(t - \tau) = L[\delta(t - \tau)]$ [cite: 137]

Therefore:
[cite_start]$y(t) = \int_{-\infty}^{\infty} x(\tau)L[\delta(t - \tau)]d\tau = \int_{-\infty}^{\infty} x(\tau)h(t - \tau)d\tau$ [cite: 138, 139]
[cite_start]In the linear time-invariant system, the output $y(t)$ is a convolution between input $x(t)$ and impulse response $h(t)$. [cite: 140]

In the frequency domain:
[cite_start]$Y(f) = X(f)H(f)$ (Eq. 2-1) [cite: 141]
[cite_start]Where $Y(f)$, $X(f)$, and $H(f)$ are the Fourier transforms of $y(t)$, $x(t)$, and $h(t)$. [cite: 142]

---

## 3. Characterization of Communication Signals

### 3.1 Representation of Bandpass Signals
[cite_start]**Narrowband bandpass signals and systems (channels):** Their bandwidth is much smaller than the carrier frequency ($f_{c} \gg B$). [cite: 149, 151]
[cite_start]Bandpass signals and systems (channels) are represented in terms of equivalent lowpass waveforms. [cite: 158]

**Analytic signal $S_{+}(t)$:**
[cite_start]$S_{+}(f) = 2u(f)S(f)$, where $u(f)$ is the step function. [cite: 167, 168]
[cite_start]$s_{+}(t) = [\delta(t) + \frac{j}{\pi t}] \otimes s(t) = s(t) + j\hat{s}(t)$ (Eq. 3-1) [cite: 178, 179]
($\hat{s}(t)[cite_start]$ is the Hilbert transform of $s(t)$) [cite: 178]
[cite_start]$S_{+}(t)$ is a bandpass signal. [cite: 182]

**Equivalent lowpass signal $s_{l}(t)$:**
[cite_start]$s_{l}(t)$ is complex-valued. [cite: 183, 184]
[cite_start]$s_{l}(t) = i(t) + jq(t)$ [cite: 185]
[cite_start]$i(t)$: real part (In-phase component) [cite: 186, 206]
[cite_start]$q(t)$: imaginary part (quadrature component) [cite: 186, 212]

**Relationship:**
[cite_start]$s_{l}(t) = s_{+}(t)e^{-j2\pi f_{c}t}$ (Eq. 3-2) [cite: 191]
[cite_start]$s(t) = Re\{s_{l}(t)e^{j2\pi f_{c}t}\} = i(t)\cos(2\pi f_{c}t) - q(t)\sin(2\pi f_{c}t)$ (Eq. 3-3) [cite: 199, 200, 203, 204]
The Fourier transform of $s(t)$:
[cite_start]$S(f) = \frac{1}{2}[S_{l}(f - f_{c}) + S_{l}^{*}(-f - f_{c})]$ (Eq. 3-4) [cite: 228, 231]

### 3.2 Representation of Linear Bandpass Systems
$h(t)$: impulse response of a linear filter or system. [cite_start]$H(f)$: Fourier transform of $h(t)$. [cite: 242]
[cite_start]Since $h(t)$ is real, $H^{*}(-f) = H(f)$. [cite: 243, 244]
Let $H_{l}(f - f_{c}) = H(f)$ for $f > 0$, and $0$ for $f < 0$. [cite: 245, 247]
Then $H(f) = H_{l}(f - f_{c}) + H_{l}^{*}(-f - f_{c})$ [cite: 251]
[cite_start]$h(t) = 2 Re[h_{l}(t)e^{j2\pi f_{c}t}]$ (Eq. 3-6) [cite: 253, 256]

**Response of a Bandpass System to a Bandpass Signal:**
[cite_start]Time domain: $r(t) = \int_{-\infty}^{\infty} s(\tau)h(t - \tau)d\tau$ [cite: 262]
[cite_start]Frequency domain: $R(f) = S(f)H(f)$ [cite: 262]
[cite_start]$R(f) = \frac{1}{2}[R_{l}(f - f_{c}) + R_{l}^{*}(-f - f_{c})]$ [cite: 281]
[cite_start]Where $R_{l}(f) = S_{l}(f)H_{l}(f)$ (Eq. 3-7) [cite: 282, 283]
[cite_start]Time domain equivalence: $r_{l}(t) = \int_{-\infty}^{\infty} s_{l}(\tau)h_{l}(t - \tau)d\tau$ [cite: 284]

[cite_start]**Conclusion:** We only have to deal with the transmission of equivalent lowpass signals through equivalent lowpass channels. [cite: 285]

---

## 4. Modulation Scheme

### 4.1 Modulation Scheme General Form
[cite_start]$S(t) = A(t)\cos[2\pi f_{c}t + \phi(t)] = Re[E(t)\exp(j 2\pi f_{c}t)]$ [cite: 17, 21]
[cite_start]$E(t) = I(t) + jQ(t) = A(t)e^{j\Phi(t)}$ [cite: 17, 21]

* **Amplitude Modulation:** $g(t) \rightarrow A(t)$ [cite: 17]
* [cite_start]**Phase Modulation:** $g(t) \rightarrow \Phi(t)$ [cite: 17]
* [cite_start]**Frequency Modulation:** $g(t) \rightarrow \frac{1}{2\pi}\frac{d\phi(t)}{dt}$ [cite: 17]

### 4.2 Inphase and Quadrature Components
[cite_start]$I(t) = A(t)\cos\theta(t)$ (In-phase Component) [cite: 17]
[cite_start]$Q(t) = A(t)\sin\theta(t)$ (Quadrature Component) [cite: 17]

### 4.4 Classification of Digital Modulation Schemes
| Parameters | Scheme Name | Abbreviation |
| :--- | :--- | :--- |
| $A(t)$ | Amplitude Shift Keying | [cite_start]ASK [cite: 18] |
| $f(t)$ | Frequency Shift Keying | [cite_start]FSK [cite: 18] |
| $\Phi(t)$ | Phase Shift Keying | [cite_start]PSK [cite: 18] |
| $A(t)$ and $\Phi(t)$ | Quadrature Amplitude Modulation | [cite_start]QAM [cite: 18] |

### 4.5 Amplitude Modulation
[cite_start]**ASK (Amplitude Shift Keying):** $E(t) = I(t) = g(t)$, $g(t) \in \{A_{0}, A_{1}, ... A_{M-1}\}$ [cite: 19]
[cite_start]**OOK (On-Off Keying):** $A_{0} = 0$, $A_{1} = A$ [cite: 19]

### 4.6 Frequency Modulation
[cite_start]**FSK (Frequency Shift Keying):** Involves Voltage Controlled Oscillator (VCO). [cite: 19]
[cite_start]**CPFSK:** Continuous Phase FSK. [cite: 19]

### 4.7 Phase Modulation
[cite_start]**PSK (Phase Shift Keying):** $I(t) = A\cos\phi_{m}$, $Q(t) = A\sin\phi_{m}$ [cite: 19]
* **BPSK (Binary PSK)** [cite: 20]
* [cite_start]**QPSK (Quaternary or Quadrature PSK)** [cite: 20]

### 4.8 Multilevel QAM
[cite_start]Includes schemes like 16QAM and 16APSK. [cite: 20, 23]

