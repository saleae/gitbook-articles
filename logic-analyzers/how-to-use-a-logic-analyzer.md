# How to Use a Logic Analyzer

## How to Use a Logic Analyzer

### When to Use a Logic Analyzer

An [oscilloscope](../oscilloscopes/what-is-an-oscilloscope.md#what-is-an-oscilloscope) and a logic analyzer allow you to see how a signal's voltage changes over time. However, a logic analyzer is the better tool in a number of situations:

* You want to observe many digital signals  at the same time
* You want to look at digital signals the same way a system sees them
* You need to trigger your data capture on a complex series of digital 1s and 0s

Generally, you should consider using a logic analyzer when you are working with a digital system with more lines than can be measured by an oscilloscope.

&lt;Photo of LA connected to circuit with lots of probes?&gt;

In the rest of this tutorial, we will look at the five main steps normally taken to capture and analyze data using a logic analyzer:

1. Connect probes to the system under test
2. Set your sampling mode
3. Configure the trigger conditions
4. Acquire signal data
5. Display and analyze waveforms

### Terminology

A few definitions might help you on your journey with logic analyzers:

**Channel:** A single signal line on the system under test. Logic analyzers are capable of monitoring anywhere from 4 to over 100 channels at the same time.

**Threshold:** A voltage level set by logic analyzer or by the user. Voltages detected by the probe below the threshold are assigned a logic "0," and voltages above the threshold are assigned a logic "1."

**Sample:** Data that is captured by the logic analyzer at a particular moment in time. The logic analyzer simultaneously compares the voltages detected on all probes to the threshold, translates them to logic 1s and 0s, and stores that data in memory.

**Sample Rate:** How often the logic analyzer captures data. The maximum sample rate for a logic analyzer is often given as megahertz \(MHz\) or mega-samples per second \(Msps\); both of which equate to taking one set of samples \(across all channels\) one million times per second.

**Memory Depth:** The amount of computer memory available to store the samples. The maximum memory depth for most logic analyzers is often presented as thousands or millions of samples per channel.

**Trigger:** The condition or conditions necessary that cause the logic analyzer to begin sampling and recording data. For example, a rising or falling voltage on a particular channel or a particular pattern of 1s and 0s across multiple channels can be used as triggers.

### Probe Setup

Most logic analyzers come with a special wire harness that contains a number of probes. To begin, connect the wire harness to the logic analyzer.

Next, ensure that the system or device you wish to test is off! We don't want to accidentally short something out in our circuit with a probe. Find the "ground" or "common" probe and attach it to the ground or common in your system. Ground will be used as a reference voltage when sampling signal lines. 

Note that for some logic analyzers, you will only need to attach one ground probe for the whole wire harness. With other analyzers, you will need to attach one ground probe for each signal probe.

Finally, find the signal lines in your circuit that you wish to monitor. These could be GPIO lines or a communication bus, such as UART, SPI, or I2C. Attach one probe to each signal line. The logic analyzer will measure the difference between the reference voltage and signal voltage on each line.

&lt;image of annotated schematic showing where to connect probes. I2C?&gt;

Most logic analyzers have clip-on probes that you can attach to headers, plated-through hole \(PTH\) parts, or even some larger surface-mount devices \(SMD\). If you are working with small SMD parts with no exposed leads, you can solder thin wire to an exposed printed circuit board \(PCB\) trace to give you access to the signal.

&lt;photo of clipped probe&gt;

Some high-density or high-speed systems may require a specialized connector. Test PCBs can be made with these connectors, which mate to a wire harness connector from the logic analyzer. During development, this technique can save time from having to wire up dozens of probes to the circuit. 

&lt;photo of high-density connector on circuit&gt;

### Sampling Modes

Most logic analyzers have two methods of capturing and displaying data: timing mode and state mode. You will need to select the mode best suited for your application.

In timing mode, also known as "asynchronous mode," data is captured at precise intervals according to the logic analyzer's internal clock. The sample rate can often be set by the user. For example, if you set the sample rate to 1 khz, the logic analyzer will capture data 1000 times per second \(in other words, sample the probed lines once every millisecond\).

In the image below, we can see how a logic analyzer \(with 1 channel\) will sample a sinewave at precise intervals. The voltage at each sample is compared to the threshold. A digital signal is reconstructed from the captured 1s and 0s to show a waveform to the user.

&lt;image if sampling sine wave&gt;

State mode, also called "synchronous mode," requires one of the channels to tell the logic analyzer when to sample the other channels. If your system under test requires a clock line, this mode can be helpful for viewing data as your system might see it.

In the example below, we have 4 D flip-flops. Each has a "data in" line \(labeled D0-D3\), a "data out" line \(labeled Q0-Q3\), and a clock line \(CLK\). On each rising edge of the clock signal, the logic level at the "data in" pin is latched and replicated on the "data out" pin.

If we attach 4 logic analyzer probes to the "data in" pins \(D0-D3\) and a 5th probe to the CLK line, we can use state mode to see what the data should look like at the outputs. Note that state mode data is often presented in list format.

&lt;image of sampling 4 D flip flops&gt;

### Configure Trigger

Before you begin sampling, you will need to configure your trigger conditions. How else will the logic analyzer know to start sampling data?

**No trigger:** With no trigger, the logic analyzer will begin sampling and recording data as soon as you press the "Start" or "Run" button.

**Edge Trigger:** You can set the logic analyzer to watch for a rising or falling edge on a single channel, which will begin the recording process.

**Pattern Trigger:** If you are capturing multiple channels, you can set the logic analyzer to start the capturing process when it sees a pattern of 1s and 0s across several channels. Pattern triggers can be useful if you are looking for start-of-frame transmissions on parallel buses.

**Complex Trigger:** Some advanced logic analyzers will let you set a series of if-then-else statements to create a trigger. These types of triggers can be helpful to look for transmissions to a particular address on a bus, for example.

### Acquire

For most logic analyzers, you push a button named "start" or "run." With no trigger set, the analyzer will begin sampling and storing data until memory is full.

If you configured a trigger, the analyzer will begin capturing data, but older samples will be thrown out to make room for new samples. When the trigger condition is met, the logic analyzer will continue capturing data until its memory is full. Some logic analyzers retain and display a portion of the data prior to the trigger point. Information shown before the trigger is known as "negative time."

&lt;captured data with trigger and negative time&gt;

### Display and Analyze

Most logic analyzers will display data as waveforms with time in the x-axis and voltage in the y-axis. This type of display is useful for seeing correlation among multiple signals in the time domain.

&lt;diagram of several digital signals&gt;

Some logic analyzers come with the ability to decode various communication protocols, such as UART, SPI, I2C, etc. Decoders might show the data as a waveform but will also present the data as decimal, hexadecimal, ASCII, and so on. Decoding protocols can be extremely helpful in troubleshooting problems on these communication buses.

&lt;diagram of decoded ascii&gt;

Advanced logic analyzers can even be equipped with decoders capable of analyzing machine language and converting it to assembly code. This type of analysis would require software unique to each type of processor or instruction set.

Using a logic analyzer is very similar to using an oscilloscope. However, if you need to debug a digital system with multiple signal lines or decode digital communication, a logic analyzer might be the better option.

