# Communication Systems

**Date:** 2026.4.16

---

## 1. Introduction

### 1.1 Basic Elements of a Digital Communication System
Information such as analog (audio or video) signals, or digital signals.

* **Transmitter side:** Information source $\rightarrow$ Source encoder (Bit sequence) $\rightarrow$ Channel encoder (Encoded bit sequence) $\rightarrow$ Digital modulator (Modulated signals)
* **Channel:** Wired or Wireless.
* **Receiver side:** Digital demodulator $\rightarrow$ Channel decoder (Detected bit sequence) $\rightarrow$ Source decoder (Decoded bit sequence) $\rightarrow$ Recovered information

**Purpose of Channel Encoder:**
To introduce redundancy so as to overcome the effects of noise and interference.

**Basic Elements of an Analog Communication System:**
Information source $\rightarrow$ Analog modulator (Analog signal $\rightarrow$ Modulated signals) $\rightarrow$ Channel (Wired or Wireless) $\rightarrow$ Analog demodulator $\rightarrow$ Recovered information

### 1.2 Analog and Digital Signals
Signals are electric current or voltage waveforms into which physical quantities such as sound and image are converted, and can be considered functions of time.

* **Analog signal:** a time-continuous waveform having continuous values.
* **Digital signal:** a discrete-time waveform having discrete values (a unit multiplied by an integer, the integer is expressed in a binary number).

### Advantages of Digital Modulation
1. High accuracy and adaptive control are possible.
2. To combine several signals and to send them together are possible.
3. Signals (Information) can be sent in packet form.
4. Band compression, forward error correction, and encryption techniques can be implemented.

**Conclusion:** Digital modulation overwhelms analog modulation.

---

## 2. Typical Channel (Linear Time-Invariant System)

### 2.1 Linear Time-Invariant System
A structure of the general system: Input signal $x(t) \rightarrow$ System $\rightarrow$ Output signal $y(t) = L[x(t)]$
The most important system for communications is the linear time-invariant system.

**Conditions for the linear time-invariant system:**
1. **Linear system:**
$$L[a_{1}x_{1}(t) + a_{2}x_{2}(t)] = a_{1}L[x_{1}(t)] + a_{2}L[x_{2}(t)]$$
($a_{1}, a_{2}$ arbitrary constants)
2. **Time-invariant system:**
$$y(t - \tau) = L[x(t - \tau)]$$
($\tau$ is an arbitrary real number.)

**Representation of the linear time-invariant system:**
Input signal $x(t)$ is expressed as:
$$x(t) = \int_{-\infty}^{\infty} x(\tau)\delta(t - \tau)d\tau$$
($\delta(t)$: delta function)

Using the condition for the linear system, output signal is given by:
$$y(t) = L[x(t)] = \int_{-\infty}^{\infty} x(\tau)L[\delta(t - \tau)]d\tau$$

The impulse response $h(t)$ is defined as $h(t) = L[\delta(t)]$.
Using the condition for the time-invariant system: 
$$h(t - \tau) = L[\delta(t - \tau)]$$

Therefore:
$$y(t) = \int_{-\infty}^{\infty} x(\tau)L[\delta(t - \tau)]d\tau = \int_{-\infty}^{\infty} x(\tau)h(t - \tau)d\tau$$
In the linear time-invariant system, the output $y(t)$ is a convolution between input $x(t)$ and impulse response $h(t)$.

In the frequency domain:
$$Y(f) = X(f)H(f) \quad \text{(Eq. 2-1)}$$
Where $Y(f)$, $X(f)$, and $H(f)$ are the Fourier transforms of $y(t)$, $x(t)$, and $h(t)$.

---

## 3. Characterization of Communication Signals

### 3.1 Representation of Bandpass Signals
**Narrowband bandpass signals and systems (channels):** Their bandwidth is much smaller than the carrier frequency ($f_{c} \gg B$).
Bandpass signals and systems (channels) are represented in terms of equivalent lowpass waveforms.

**Analytic signal $S_{+}(t)$:**
$$S_{+}(f) = 2u(f)S(f)$$
(where $u(f)$ is the step function)
$$s_{+}(t) = \left[\delta(t) + \frac{j}{\pi t}\right] \otimes s(t) = s(t) + j\hat{s}(t) \quad \text{(Eq. 3-1)}$$
($\hat{s}(t)$ is the Hilbert transform of $s(t)$)
$S_{+}(t)$ is a bandpass signal.

**Equivalent lowpass signal $s_{l}(t)$:**
$s_{l}(t)$ is complex-valued.
$$s_{l}(t) = i(t) + jq(t)$$
* $i(t)$: real part (In-phase component)
* $q(t)$: imaginary part (quadrature component)

**Relationship:**
$$s_{l}(t) = s_{+}(t)e^{-j2\pi f_{c}t} \quad \text{(Eq. 3-2)}$$
$$s(t) = Re\{s_{l}(t)e^{j2\pi f_{c}t}\} = i(t)\cos(2\pi f_{c}t) - q(t)\sin(2\pi f_{c}t) \quad \text{(Eq. 3-3)}$$
The Fourier transform of $s(t)$:
$$S(f) = \frac{1}{2}[S_{l}(f - f_{c}) + S_{l}^{*}(-f - f_{c})] \quad \text{(Eq. 3-4)}$$

### 3.2 Representation of Linear Bandpass Systems
$h(t)$: impulse response of a linear filter or system.
$H(f)$: Fourier transform of $h(t)$.
Since $h(t)$ is real, $H^{*}(-f) = H(f)$.
Let $H_{l}(f - f_{c}) = H(f)$ for $f > 0$, and $0$ for $f < 0$.
Then:
$$H(f) = H_{l}(f - f_{c}) + H_{l}^{*}(-f - f_{c})$$
$$h(t) = 2 Re[h_{l}(t)e^{j2\pi f_{c}t}] \quad \text{(Eq. 3-6)}$$

**Response of a Bandpass System to a Bandpass Signal:**
Time domain:
$$r(t) = \int_{-\infty}^{\infty} s(\tau)h(t - \tau)d\tau$$
Frequency domain:
$$R(f) = S(f)H(f)$$
$$R(f) = \frac{1}{2}[R_{l}(f - f_{c}) + R_{l}^{*}(-f - f_{c})]$$
Where $R_{l}(f) = S_{l}(f)H_{l}(f)$ (Eq. 3-7)
Time domain equivalence:
$$r_{l}(t) = \int_{-\infty}^{\infty} s_{l}(\tau)h_{l}(t - \tau)d\tau$$

**Conclusion:** We only have to deal with the transmission of equivalent lowpass signals through equivalent lowpass channels.

---

## 4. Modulation Scheme

### 4.1 Modulation Scheme General Form
$$S(t) = A(t)\cos[2\pi f_{c}t + \phi(t)] = Re[E(t)\exp(j 2\pi f_{c}t)]$$
$$E(t) = I(t) + jQ(t) = A(t)e^{j\Phi(t)}$$

* **Amplitude Modulation:** $g(t) \rightarrow A(t)$
* **Phase Modulation:** $g(t) \rightarrow \Phi(t)$
* **Frequency Modulation:** $g(t) \rightarrow \frac{1}{2\pi}\frac{d\phi(t)}{dt}$

### 4.2 Inphase and Quadrature Components
* $I(t) = A(t)\cos\theta(t)$ (In-phase Component)
* $Q(t) = A(t)\sin\theta(t)$ (Quadrature Component)

### 4.4 Classification of Digital Modulation Schemes
| Parameters | Scheme Name | Abbreviation |
| :--- | :--- | :--- |
| $A(t)$ | Amplitude Shift Keying | ASK |
| $f(t)$ | Frequency Shift Keying | FSK |
| $\Phi(t)$ | Phase Shift Keying | PSK |
| $A(t)$ and $\Phi(t)$ | Quadrature Amplitude Modulation | QAM |

### 4.5 Amplitude Modulation
**ASK (Amplitude Shift Keying):** $E(t) = I(t) = g(t)$, $g(t) \in \{A_{0}, A_{1}, ... A_{M-1}\}$
**OOK (On-Off Keying):** $A_{0} = 0$, $A_{1} = A$

### 4.6 Frequency Modulation
**FSK (Frequency Shift Keying):** Involves Voltage Controlled Oscillator (VCO).
**CPFSK:** Continuous Phase FSK.

### 4.7 Phase Modulation
**PSK (Phase Shift Keying):** $I(t) = A\cos\phi_{m}$, $Q(t) = A\sin\phi_{m}$
* **BPSK (Binary PSK)**
* **QPSK (Quaternary or Quadrature PSK)**

### 4.8 Multilevel QAM
Includes schemes like 16QAM and 16APSK.

---

