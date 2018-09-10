# What Is a Logic Analyzer, and What Is It Used For?

## What Is a Logic Analyzer, and What Is It Used For?

A logic analyzer is an instrument for capturing, displaying, and measuring multiple electronic signals simultaneously in a digital circuit. Logic analyzers are capable of showing the relationship and timing among many different signals in a digital system and are often capable of analyzing digital communication protocols, such as I2C, SPI, and Serial. As a result, a logic analyzer is the best tool for debugging digital circuits and digital communication systems.

Based on: [https://paper.dropbox.com/doc/Logic-Analyzer-Basics--AMVXGzmE7xq2lyCHyjqyvKdGAg-OGLGmM84YXGnl5XxUFIme](https://paper.dropbox.com/doc/Logic-Analyzer-Basics--AMVXGzmE7xq2lyCHyjqyvKdGAg-OGLGmM84YXGnl5XxUFIme)

#### History

This is a *test* of my ***ability*** and mad skillllllzzzzz.

Trying to measure signals from ICs using oscilloscopes in the 1960s

%%%photo of old oscope%%%

In October of 1973, the HP 5000A Logic Analyzer was released

Features and better displays were added, but logic analyzers remained large test equipment

%%%photo of old logic analyzer%%%

Smaller, more powerful ICs and fast communication over USB allowed for computer-connected logic analyzers

%%%photo of Saleae logic analyzer%%%

**Operation**

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

#### Common Uses

* See that's going on
  * If a digital circuit is not working as expected, a logic analyzer is often the first tool used to debug potential problems. 
  * %%%screenshot of no signals%%%
* Fix timing problems
  * A logic analyzer can be used to measure the timing relationship between many different digital signals.
  * %%%screenshot of measuring timing between signals%%%
* Debug protocols
  * Electrical signals may initially appear acceptable, even when viewed on an oscilloscope.
  * A logic analyzer can help find issues in the communication protocol.
  * %%%screenshot of protocol analyzer%%%
* Reverse engineer
  * Discover how undocumented digital hardware operates
  * %%%PCB with weird connector%%%
* Bit-bang
  * Writing firmware to directly manipulate GPIO pins to implement a protocol
  * %%%Code snippet of bit-banging example%%%
* Optimize power & performance
  * Toggle GPIO pins in specific sections of code to measure how long that particular section takes to run
  * %%%Code snippet with GPIO toggling%%%
* Debug interrupts & race conditions
  * Toggle GPIO pins at the entrance and exit of critical sections to investigate potential race conditions
  * %%%Code snippet with GPIO toggling in interrupt%%%
* Debug firmware \(w/o breakpoints\)
  * Toggle GPIO pins to output debugging information
  * %%%Code snippet showing variable output to GPIO%%%
* Data-log firmware
  * Record events for long periods of time to keep a record of events in the system
  * %%%Sketch ???%%%
* Debug analog-firmware interaction
  * If an logic analyzer supports recording analog voltages, debugging microcontroller-analog interactions is possible.
  * %%%Screenshot of audio output%%%
* Debug microcontroller peripherals
  * Examine register flags to debug microcontroller peripherals
  * %%%Code snippet outputting register to GPIO%%%
* Debug peripheral ICs
  * Examine communication between microcontroller and connected peripheral IC \(sensors, crypto IC, IO expander, etc.\)
  * %%%Screenshot of I2C with register flag setting%%%
* Debug power quality and sequencing
  * With analog inputs on the logic analyzer, monitor the power supplies on system power up or power down
  * Examine power rails before and after regulation along with reset lines
  * %%%Screenshot of voltage sag when powering up microcontroller%%%



