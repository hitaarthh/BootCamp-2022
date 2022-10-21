<div>
<img src="https://img.shields.io/badge/Domain:-Wireless Security%20-black">
<img src="https://img.shields.io/badge/Date-10%20August%202022-green[700]" align="right">

<div align="center"><h1>IQ Signals</h1></div>
</div>

- Quadrature signals, also called IQ signals, IQ data or IQ samples, are often used in RF applications. They form the basis of complex RF signal modulation and demodulation, both in hardware and in software, as well as in complex signal analysis. This post looks at the concept of IQ signals and how they are used.

- A pair of periodic signals are said to be in “quadrature” when they differ in phase by 90 degrees. The “in-phase” or reference signal is referred to as “I,” and the signal that is shifted by 90 degrees (the signal in quadrature) is called “Q.” What does this mean and why do we care? Let’s break it down by starting with some basics.

## Basics of RF Modulation:

<div align="center">
    <img width="400" src="https://www.tek.com/-/media/sites/default/files/u811871/whats20iq20image201.png?w=662">
</div>

The signal can be described as a function of time by the following equation:

            V(t) = A * sin (2 * π * f * t + Ф)

            where:
                     A: is the peak amplitude

                     f: is the frequency

                     t: is time

                     Ф: is the phase shift

- Information is “carried” by an RF carrier through the process of modulation. The information signal (voice, data, etc.) is used to alter the properties of the RF signal (see also: RF signal generators). A simple example is Amplitude Modulation, or AM.

- For AM, the information signal is used to alter, or modulate the amplitude of the carrier. Mathematically, it can be represented by changing the constant “A” in the previous equation into some time-varying signal (the information signal):

            V(t) = A(t) * sin (2 * π * f * t + Ф)


- The information signal, also known as the baseband signal, varies much more slowly with time than the RF signal does. Therefore, to see the effect of the modulation, you need to observe the envelope of the RF signal over a longer time scale as shown below.

<div align="center">
   <img width="400" src="https://www.tek.com/-/media/sites/default/files/u811871/what20iq20image202.png">
</div>

- In this case, the A(t) signal is a sinusoid. The figure shows how the amplitude of the RF signal follows the sinusoidal A(t) baseband signal.

- You can expand on this by recognizing that other properties of the RF carrier can be altered, or modulated, by a baseband signal vs. time. If the frequency is modulated by a baseband signal, you have Frequency Modulation (FM). Similarly, if the phase is modulated you then have Phase Modulation (PM). Thus:

     - A(t) is when the amplitude is varied vs. time
     - f(t) is when the frequency is varied vs. time
     - Ф(t) is when the phase is varied vs. time.


