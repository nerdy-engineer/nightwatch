
# Sonar
- Distance range: 15cm - 18m
- Measurement rate: 18m @ 9Hz, 6m @ 28Hz
- Multiple reflection detection


## Modes:

- Simple
  - Distance
    - Pulse Time of flight: (0.89ms, 6"/15.2cm)-(106.6ms, 60'/1800cm)
  - Velocity (Doppler shift)
    - Resolution of 1ft/sec requires a sample history of 28ms limiting minimum distance measurements to approx. 18'
    - Resolution of 3ft/sec requires a sample history of 9.36ms limiting minimum distance measurements to approx. 5'3"
- Frequency Response
  - Distance
  - Velocity (Doppler shift using multiple frequencies)
  - Material absorbtion at multiple frequencies
- Low-Baudrate Comms (QAM? FSK?)
  - Could possibly transmit 2+ bits in parallel using multiple frequencies
    - Signal buffer size = 2 * 1/40000 = 50uS
    - Sample Rate > 80kHz
    - Max word-rate: 20,000
    - Max bit rate @ 4 bits per word: 80,000bps = 1000 Bps
  - **Could possibly transmit 16 bits at once using QAM-16**
    - Signal buffer size =  3 * 1/40000 = 75uS
    - Sample Rate > 80kHz
    - Max word-rate: 13,333
    - Max bit rate @ 16 bits per word: 213,328bps = 26,666 Bps



## Interface:
- Trigger in
- Trigger out (Modes: synchronized & sequential)
  - Default: Sequential
- 


### Return Data:
- Distanced
- Velocities
- Frequency/Frequencies used
- Sample age (milliseconds)




## Hardware:
- 3.3v Power in
- 3.3v Logic level, 5v tolerant



### Transmitter:
- Boost Power Supply (3.3v -> 12v-30v)
  - Use Digital Potentiometer to adjust the output voltage (SPI? I2C?)
- Transformer to boost the ultrasonic output signal to the output voltage level (ac couple through a transformer, into the ultrasonic transducer)
- Output voltage level at the transducer should be somewhere close to 150Vp-p
- Signal will come from the processor via a DAC


### Receiver:
- Time-variable gain (controlled via DAC from the processor)
  - Gain range: 4.5V/V <= Gain <= 8845V/V
  - Variable gain amplifier AD8330 needs an input signal amplitude between +/-6.3mV and +/-2V
  - Use fixed gain of 20 before feeding into the AD8330
- Possibly multiple receivers for phased array detection...?
- 

### Processor:
- \>=2 ADCs (8-bit+)
  - Sample rate: 100000Hz
- \>=2 DACs
- CAN
- I2C
- SPI
- UART

