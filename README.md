# infraredTransmitter Library
A simple library to transmit a simplified version of the IR remote protocol


The Library is intended to be used in time critical systems where the programmer can not afford to lock hardware resources. 
An example of such a system can be a realtime controller used in drones where basic commands signals need to be identified.

The Library is expected to be used with the related **infraredReceiver** library.

Since this library utilises the timer 1 of the arduino UNO the transmitter can only be attached to digital pin 9 and 10,
for this reason, Initialise the transmitter with argument 9 or 10.

## Initialising the Transmitter
```
infraredTransmitter myTransmitter(9);
myTransmitter.init(); //Performs hardware configurations
```

## Library Methods

**To set the signal type to be transmitted:**
```
myTransmitter.setSignalIdentity(2);
```
**To transmit the signal:**

Please note that the library can only toggle the output of the transmitter each time the __transmit__ method is called.
In order to meet the signal specifications the transmit method must be called once every 20 ms. In other words, the main loop of the program must run at at least 50 Hz.
```
myTransmitter.transmit(); // Should be called every loop
```
**To turn on the led:**

When it is desired to keep the led on all the time, the __alwaysOn__ method should be called. This method needs to be called only once. After this method is called the led will remain on as long as the microcontroller remains powered on.
```
myTransmitter.alwaysOn(); // Only needs to be called once
```
