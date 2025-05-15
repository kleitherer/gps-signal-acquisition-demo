# gps-signal-acquisition-demo

# EE259 Principles of Sensing for Autonomy: PSET 1, Problem 2. #
This problem set simulates the foundational techniques used in GPS signal acquisition and pseudorange estimation. Starting with m-sequence generation, we build a basic CDMA-like receiver, then move toward realistic delay-Doppler matched filtering, and finally address range ambiguity. The complete system demonstrates how spreading codes, correlation, and frequency compensation enable robust localization in modern satellite navigation systems.

## Background 
Global Positioning System (GPS) is a space-based navigation system that provides accurate, continuous, and global 3D position and velocity information. It can serve an unlimited number of users and operates using a constellation of satellites that broadcast synchronized signals. A GPS receiver uses these signals to estimate its distance to each satellite and ultimately determine its position through trilateration.

GPS signals contain two main components:
    • Ranging signals: pseudorandom binary sequences (PRNs) used to estimate time-of-flight (TOF).
    • Navigation messages: containing satellite ephemeris and timing information.

The ranging signals are derived from maximum-length sequences (MLS), a type of m-sequence chosen for their sharp autocorrelation properties. Because MLS codes have very low cross-correlation between one another, GPS can operate under code-division multiple access (CDMA), where all satellites transmit on the same carrier frequency using distinct codes.

# Sections #

## Part A: ##
We generate an MLS code (a type of m-sequence) with good autocorrelation properties. This code mimics the behavior of the GPS Coarse/Acquisition (C/A) PRN codes, which allow for precise synchronization via a single sharp peak in the autocorrelation

## Part B: ##
We simulate a basic CDMA receiver setup. The MLS code is BPSK-modulated and transmitted through a static channel. At the receiver, we perform cross-correlation to identify the delay corresponding to the highest peak, which gives us an estimate of time-of-flight (TOF) and hence the pseudorange.

## Part C: ##
We implement a full delay-Doppler search to reflect how real GPS receivers acquire satellite signals in dynamic environments. By compensating for different Doppler shifts and searching over possible delays, we construct a 2D correlation matrix. This acts as a matched filter in both time and frequency, allowing us to extract TOF, Doppler shift, and ultimately a more robust pseudorange estimate.

## Part D: ##
Although we estimated a pseudorange of ~49.5 km in the previous section, this may not represent the true distance to the satellite due to range ambiguity. If the signal’s round-trip time exceeds the system’s pulse repetition interval, the receiver may alias the measurement—mistakenly interpreting an older pulse as a recent one. To resolve this, we compare with a second pseudorange measurement (from another satellite or receiver) and use modular arithmetic to find the correct unambiguous range.
