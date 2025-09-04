# Michel_Spectrum_OPTICS

This document describes the simulations performed to recover the Michel Spectrum.  
The noise data is simulated using Gaussian distributions, as observed in real WCD data.  

## Data_Processing  

This module extracts information from each pulse.  
Each dataset is first grouped into **3-hour files**, and then combined into **24-hour files**.  
Afterwards, pulse characteristics are extracted. Each of the functions contained in this file is described below.

### `pulses`  
Returns a **DataFrame** with the information of the 32 ADC bins and the time difference between pulses.  

### `Peak_Position`  
Returns the highest bin value within the 32 ADC bins of a pulse.  

### `ACAP`  
Returns the mean value between the peak and the following three consecutive bins.  

### `SPC_16`  
Returns the difference between the peak and the bin located **16 ns** later.  

### `SPC_24`  
Returns the difference between the peak and the bin located **24 ns** later.  

### `SPC_32`  
Returns the difference between the peak and the bin located **32 ns** later.  

### `Charge_Histogram`  
Returns a histogram of the deposited energy per pulse.  

### `charge`  
Returns the **total deposited energy** in a pulse by summing the 32 ADC bin values.  

## Feature_Extraction  

This module compares the resulting data after applying each algorithm.  
The functions contained in this file are described below.

### `Mean_Pulse`  
Returns the mean pulse for a given dataset.  

### `Individual_Pulse`  
Extracts the 32 ADC bin values for a single pulse.  

### `Graph_Mean_Pulse`  
Creates a histogram from the information extracted in `Mean_Pulse`.  

### `Error_Michel`  
Calculates the error between the theoretical time difference associated with the Michel spectrum and the time difference obtained from fitting real data.  

### `diff_df`  
Returns a **DataFrame** with the information required to build a histogram, given a mask on the time differences.  

### `Integrated_Charge_Histogram_Comparison`  
Returns a graph comparing the results of each charge histogram after applying different cleaning algorithms.  

## Simulations  

This module recreates Python simulations of the data collected by the Water Cherenkov Tank.  
The data can be modified by adding more or less noise.  
