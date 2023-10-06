# Cosmic Emu

![Emu](emu2.png)

## Description

The Cosmic Emu produces predictions for the matter power spectrum based on eight cosmological parameters and redshift. These predictions, based on Gaussian process emulation, approximate the power spectra that would be obtained from large dark matter simulations. Details as follows:
* The simulation and design details are provide in [_The Mira-Titan Universe: Precision Predictions for Dark Energy Surveys_](https://iopscience.iop.org/article/10.3847/0004-637X/820/2/108/pdf). 
* The emulator construction and performance details for the first power spectrum emulator based on a subset of 36 cosmological models, available in the `Deprecated-2017-Mira-Titan-II` folder, is described in [_The Mira-Titan Universe II. Matter Power Spectrum Emulation_](https://iopscience.iop.org/article/10.3847/1538-4357/aa86a9/pdf).
* The updated final power spectrum emulator based on the full simulation suite, available in the `Current-2022-Mira-Titan-IV` folder, is described in [_The Mira-Titan Universe IV. High Precision Power Spectrum Emulation_](https://arxiv.org/abs/2207.12345). 

We recommend using the current 2022 emulator rather than the deprecated 2017 version. Note that prior to July 2022, the only Cosmic Emu version available on this site was the 2017 Mira-Titan II version.

## Getting Started

The Cosmic Emu requires the GNU Scientific Library (GSL). The makefile for both spectrum emulators includes lines to point to your installation of the GSL. The Cosmic Emu can produce predictions for the dark matter spectrum (P_cb) and the dark matter plus neutrino spectrum (P_tot). For each spectrum emulator, there are two files in addition to the makefile: emu.c and params.h. Simply type "make" at the command line to compile. The resulting program, emu.exe, is intended to be a demonstration of how to use the emu() and emuInit() functions. This program looks for a file called "xstar.dat" which should have nine space-delimited numbers on each line:

omega_m   omega_b   sigma_8   h   n_s   w_0   w_a   omega_nu   z

Running "emu.exe" will produce a prediction, in its own file, for each line in xstar.dat (e.g. if xstar.dat has 10 lines of inputs, the code will produce 10 output files, each with a prediction for the corresponding line). 

The ranges for the parameters are

Lower | Parameter | Upper
------|-----------|------
0.12  | omega_m   | 0.155
0.0215| omega_b   | 0.0235
0.7   | sigma_8   | 0.9
0.55  | h         | 0.85
0.85  | n_s       | 1.05
-1.3  | w_0       | -0.7
0.3   | (-w_0-w_a)^(1/4) | 1.29
0.0   | omega_nu  | 0.01
0.0   | z         | 2.02
 
The code will not produce a spectrum for parameters outside these ranges. Note that the range for w_a depends on w_0.

## Copyright and License

Triad National Security, LLC owns the copyright for this code. Please see LICENSE for copyright details.
