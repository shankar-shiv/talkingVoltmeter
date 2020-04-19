A fun little talking Voltmeter project from the great AVR Programming. 

![cover photo](https://link)

This project uses DPCM. Differential Pulse-Code Modulation (DPCM), which is an audio compression method developed for compressing speech. 

In order to reproduce it, download the AVRDUDE toolchain and set the path accordingly.

``` bash
make program
make clean
```

Timer0 : used to create the fast PWM output. Timer 0 is set at a fixed frequency of around 31.25 kHz, as before, so what we hear is the changes in average voltage due to the duty cycle changing over time.

Timer2 : CTC mode and counts up until a fixed value and then triggers and interrupt. I’ve set the frequency of Timer 2’s cycle to be around 8 kHz to match the sample rate of the audio input files. (You can play with this to speed up or slow down sample playback.) Each time Timer 2’s ISR is called, it loads a new sample value into Timer 0’s output compare register. Timer 2's Interrupt Service Routine loads a new sample into Timer 0’s PWM register. 

I feel that this project has taught me a lot by creating a real prototype. Thanks !

