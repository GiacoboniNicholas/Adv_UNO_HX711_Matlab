# Adv_UNO_HX711_Matlab
Get data from the HX711 load cell amplifier and import into MATLAB workspace 
with Arduino Uno and Mega2560.

This manual explains how to register a custom library and get started with
the HX711 load cell ampliﬁer in MATLAB environment. You need to have
already installed the MATLAB Support Package for ARDUINO Hardware.
It does require basic knowledge about MATLAB and his functionality, furthermore 
it assumes your load cell works properly and the connection is
correct. This particular library has been tested with Arduino UNO and
MEGA2560, if you are using Arduino DUE you can use this one ().

## Overview
An add-on library is a collection of MATLAB and C++ code that provides a user
easy access to features on the Arduino hardware or attached shields. 
The HX711 add-on library just develops the two wire comunication protocol
between Matlab workspace and HX711 itself through ARDUINO, thus you can built
your own commands to calibrate your load cell and acquire weight. 

The HX711 is a precision 24-bit analog to digital converter (ADC) designed for 
weigh scales and industrial control applications to interface directly with a 
bridge sensor. All you have to do is to specify the name of the digital pins in
according to phisical connection. 

## Limitations
• This library has been tested with ARDUINO UNO and MEGA2560 under windows environment. 
  It does not work with ARDUINO DUE and it might not work with other board.
  
• You can make static or dynamic measurements with high precision even with low cost 
  components, but in the second case do not exceed the sampling rate of 10 [Hz] because 
  you may have some comunication error (0 or NaN).
