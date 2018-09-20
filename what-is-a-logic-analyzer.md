# What Is a Logic Analyzer?

## What Is a Logic Analyzer?

A logic analyzer is an instrument for capturing, displaying, and measuring multiple electronic signals simultaneously in a digital circuit. Logic analyzers are capable of showing the relationship and timing among many different signals in a digital system and are often capable of analyzing digital communication protocols, such as I2C, SPI, and Serial. As a result, a logic analyzer is the best tool for debugging digital circuits and digital communication systems.

Based on: [https://paper.dropbox.com/doc/Logic-Analyzer-Basics--AMVXGzmE7xq2lyCHyjqyvKdGAg-OGLGmM84YXGnl5XxUFIme](https://paper.dropbox.com/doc/Logic-Analyzer-Basics--AMVXGzmE7xq2lyCHyjqyvKdGAg-OGLGmM84YXGnl5XxUFIme)

### Filling a Need

Digital logic and ICs in the 60s, need to view several channels at once. Oscilloscopes around since 1930s, channels are expensive. first LA in 197?

Differences between LA and oscilloscope

### What Makes a Logic Analyzer Unique

* Record one or more digital signals simultaneously
  * Potentially start recording based on a trigger
  * Potentially record analog signals at the same time \(mixed-signal oscilloscope\)
* Display the signals
  * On-device or computer application
  * Store-and-display vs. real-time display
  * Navigate \(zoom, pan, etc.\)
  * %%%gif of navigating through signals%%%
* Measure the signals
  * Pulse width
  * %%%screenshot of pulse width%%%
  * Frequency, period, duty cycle
  * %%%screenshot of freq/period/duty cycle%%%
  * Time between events \(e.g. setup and hold time\)
  * %%%screenshot of measuring setup and hold%%%
* Search for a pattern
  * Search within previously recorded data
  * %%%screenshot of searching for pattern%%%
  * Start recording when pattern is seen \(trigger\)
* Interpret signals \(protocol analyzer\)
  * List examples of protocols supported by Saleae analyzer
  * %%%screenshot of analyzed Serial data%%%

### Form Factors

Portable logic analyzer (instrument chassis)
Modular logic analyzer (modules that plug into a mainframe)
PC-based logic analyzer (standalone units that plug into a computer via USB, Ethernet, etc.)

### How a Logic Analyzer Works

Input is digitized: thresholds for TTL, CMOS, user-defined. 0 for low, 1 for high.

Sync (state) vs async (timing) clocking

All channels are sampled simultaneously and stored in memory

When trigger condition is met, contents in memory are displayed. Triggers can be user pushing button, single channel transition, several channel states, pattern in one or more channels.

Various tools can help the user browse through the data, search for patters, and analyze protocols.

### Why Would You Need a Logic Analyzer?

What kinds of problems can LAs help you solve?

Measure the time between events.

Debug protocols such as UART, SPI, I2C, etc.

Test and characterize firmware (toggle GPIO at the beginning and end of events)--interrupts, sleep, power

Reverse engineer undocumented digital hardware
