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

***IMPORTANT: if you are not familiar with custom Arduino Addons I suggest to download 
my basic Addons for HX711 here:
https://it.mathworks.com/matlabcentral/fileexchange/66641-custom-arduino-library-for-hx711
which contains a more complete User's Manual. Once you get confident with the basic one 
you can use this library which is more complete and offers several functionality such as 
PowerUp and PowerDown function, a more stable serial comunication and so on...

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

## Caution
Here I sum up some tips you should follow in order to avoid wasting time and solve every
problem quickly. Please don’t ask for help in comment section if you are not going to 
check the following recommendations.

• I suggest to test your load cell with an usual library in Arduino IDE environment. 
  You can ﬁnd a very good one at https://github.com/bogde/HX711. 
  After the calibration phase take note of the scale factor so you can compare it 
  with the one you get from MATLAB.
• Make sure that the connection between ARDUINO and HX711 is correct and particularly 
  the connection between the load cell and HX711 must be stable and strong 
  (I personally recommend a soldered connection, it also reduces noise eﬀect if it’s 
  well executed, instead of other temporary connection).
• The correct functioning of the load cell depends on the installation of the strain 
  gauges, I warn you that on the market there are load cell with a low quality installation 
  technique and even a wrong bridge connection between strain gauges. If the calibration 
  phase is done properly you should be able to make measurements with at least 0.001 [kg] of
  precision with a 0÷10 [kg] load cell. In the best case the error is below 0.0001 [kg]. 

## How to Start
In this part you will learn how to use a Custom Arduino Libraries and then how to get data 
from HX711 with just one command. 

### Register Custom Library
The current folder contains two ﬁles named HX711.m and HX711.h. The ﬁrst one is the MATLAB 
Add-On Class that inherits from arduino LibraryBase class a variety of properties and methods. 
The C++ Header File is a class that includes librarybase.h and the code segments executed on the
Arduino device.

First you should extract content from .zip ﬁle and paste it in your own personal folder (C:\work). 
In order to register the HX711 custom library you have to add the path of the folder to Matlab search path. 
You can do that with the following command:
```c++
1 addpath ( ’C : \ work ’ );
```
The structure in the work folder is the following: +arduinoioaddons which contains several subfolders, 
one of these is +advancedHX711 folder. You can have other +NameLibrary subfolder in +arduinoioaddons folder. 
The folder structure is really important so if you have some questions look here:
https://it.mathworks.com/help/supportpkg/arduinoio/ug/create-custom-folder-structure.html. 
Make sure the basicHX711/basic HX711 library is available with listArduinoLibraries command.
```c++  
2 listArduinoLibraries  
```  

### Upload Arduino Server
Now you have to initialize the connection between Matlab and Arduino. You can do that in two ways. 
The ﬁrst one consists of using the following command, which requires as argument the Arduino Board 
you’re currently using and the name of serial port (UNO and COM6 in the example).
```c++  
3 a= arduino (’com6’,’Uno’,’libraries’,’advancedHX711/advanced_HX711’);
```  
The second way consists of using the hardware setup procedure which is initialized by the following command:
```c++  
3 arduinosetup
```
Now you can start creating the objects of the classes: 
```c++  
4 a= arduino (’com6’,’Uno’) // If you ’ve used Hardware Setup ;
5 LoadCell = addon (a,’advancedHX711/advanced_HX711’,’Pins’,{’D2’,’D3’})
``` 
The default gain is 128, if you wish you can use 64 for channel A and 32 for channel B with an additional parameter:
```c++  
5 LoadCell = addon (a,’advancedHX711/advanced_HX711’,’Pins’,{’D2’,’D3’},’Gain’,64)
``` 
  
  
  
  
  
