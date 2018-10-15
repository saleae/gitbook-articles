# How to Use a Logic Analyzer

## How to Use a Logic Analyzer

### When to Use a Logic Analyzer

What happens when you need to troubleshoot a circuit with many different signals working simultaneously? An oscilloscope is one possible tool, but a logic analyzer might be a better tool for the job.

&lt;photo of logic analyzer connected to a circuit. Maybe?&gt;

A logic analyzer and an [oscilloscope](oscilloscopes/what-is-an-oscilloscope.md) accomplish a similar purpose: both allow you to see how a signal's voltage changes over time. However, a logic analyzer is the better tool in a number of situations:

* You want to observe many digital signals  at the same time
* You want to look at digital signals the same way a system sees them
* You need to trigger your data capture on a complex series of digital 1s and 0s

Generally, you should consider using a logic analyzer when you are working with a digital system with more lines than can be measured by an oscilloscope.

In the rest of this tutorial, we will look at the five main steps normally taken to capture and analyze data using a logic analyzer:

1. Connect probes to the system under test
2. Set your sampling mode
3. Configure the trigger conditions
4. Acquire signal data
5. Display and analyze waveforms

### Terminology

Threshold:

Sample:

Sample Rate:

Memory Depth:

Trigger:

### Probe Setup

Connect wire harness to logic analyzer.

Where to attach a probe in a circuit:

 - Make sure circuit is off!

 - Attach ground probe to ground \(common\) on circuit

 - Attach signal probe\(s\) to the line or lines you want to monitor. Logic analyzer will measure and display the voltage difference between ground and the signal.

&lt;image of annotated schematic showing where to connect probes. I2C?&gt;

How to connect probes:

 - Clip-on probe: connect to DIP, SOIC. Solder wire \(30 AWG\) to trace, via, or lead for smaller parts.

&lt;photo of clipped probe&gt;

 - High-density, multi-channel probe with mating connector attached to board.

&lt;photo of high-density connector on circuit&gt;

### Sampling Modes

Timing Mode

&lt;image if sampling sine wave&gt;

State Mode

&lt;image of sampling 4 D flip flops&gt;

### Configure Trigger

No trigger

Edge Trigger

Pattern Trigger

Complex Trigger

### Acquire

Run LA \(usually a button that says "start" or "run"\). Signals are sampled. If no trigger, will capture data until memory is full.

With trigger, earlier data samples are thrown out to make room for new samples. When trigger condition is met, the logic analyzer will continue to capture data until its memory is full. Some logic analyzers will retain and display a portion of the data prior to the trigger point. This is known as "negative time."

### Display and Analyze

Most will display as waveforms with time in the x-axis and voltage in the y-axis. Useful for seeing correlation among multiple signals in the time domain.

&lt;diagram of several digital signals&gt;

Some logic analyzers come with the ability to decode various communication protocols, such as UART, SPI, I2C, and so on. Decoding such protocols can be extremely helpful in troubleshooting problems on these communication buses.

Advanced logic analyzers can even be equipped with decoders capable of analyzing machine language and converting it to assembly code. This type of analysis would require software unique to each type of processor or instruction set.

Using a logic analyzer is very similar to using an oscilloscope. However, if you need to debug a digital system with multiple signal lines, a logic analyzer might be option.

