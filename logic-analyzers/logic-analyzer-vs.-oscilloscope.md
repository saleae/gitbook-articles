# Logic Analyzer vs. Oscilloscope

## Logic Analyzer vs. Oscilloscope

In the real world, electrical signals are analog (including digital ones!). An [oscilloscope](../oscilloscopes/what-is-an-oscilloscope.md#what-is-an-oscilloscope) allows you to view analog voltages and how they change over time. Oscilloscopes are best used for evaluating signal integrity and measuring analog circuit performance.

On the other hand, [Logic analyzers](what-is-a-logic-analyzer.md#what-is-a-logic-analyzer) represent signals in their digital form: a logic 0 or logic 1. This is similar to an oscilloscope with a 1-bit resolution. However, most logic analyzers have many more channels than oscilloscopes (8, 16, or even over 100 channels). Logic analyzers are great tools for viewing digital waveforms, debugging digital communication (e.g. Serial, I2C), and characterizing digital systems with many lines (e.g. FPGAs).

### Uses

Choosing the right tool for the job can be a crucial step when debugging circuits. At its core, an oscilloscope is useful for measuring and visualizing analog signals with 1-4 channels. A logic analyzer is best for digital systems with more than 4 channels.

An oscilloscope can help you visualize analog waveforms and measure various characteristics, such as amplitude, ringing, transient signals, phase, and unwanted pulses. Even when debugging digital systems, you can easily measure signal integrity with an oscilloscope.

![Example of an oscilloscope displaying a sine wave and overshoot on two channels](../.gitbook/assets/oscilloscope\_display\_example.png)

However, if you need to monitor and debug the output of a digital system or capture digital communication, such as serial and I2C, a logic analyzer is often the better tool. Logic analyzers generally offer more channels than an oscilloscope and can display data in state mode, where one of the channels acts as a clock.

![Example of a logic analyzer displaying digital signals on six channels](../.gitbook/assets/logic\_analyzer\_display\_example.png)

### Differences

The differences between oscilloscopes and logic analyzers can be summarized in the following table:

| Oscilloscope                                                            | Logic Analyzer                                                     |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Measure and display analog signals on a few channels                    | Measure and display digital signals on many channels               |
| Repeatedly store and display small snapshots                            | Record data before displaying                                      |
| Displays signals in real time                                           | Allows users to navigate potentially long recordings               |
| Measure amplitude and timing of a waveform                              | Measure time between data capture points                           |
| Offers real-time features, like fast Fourier transform (FFT)            | Offers features unique to digital systems, like protocol analyzers |
| Simple threshold or pulse-width triggers used to show a steady waveform | Complex triggering system used to capture and filter data          |

### How Do Oscilloscopes Work?

The following diagram shows the basic functional blocks that can be found in a digital storage oscilloscope (DSO). Note that some blocks have been left out for the sake of simplicity.

![Block diagram of an oscilloscope](<../.gitbook/assets/oscilloscope\_block\_diagram (1).png>)

**Probe:** The part that attaches to your circuit. Most probes have two tips, as an oscilloscope measures the voltage (electric potential difference) between two points.

**Amplifier/Attenuator:** Oscilloscopes often contain circuitry to amplify or attenuate electrical signals so they can be effectively displayed to the user. This circuitry can be in the probe or inside the oscilloscope chassis.

**Trigger Select:** Many oscilloscopes will let you chose between an internal signal or an external signal (on a separate probe) to trigger the sweep that displays the captured waveform.

**Control Logic:** Internal logic or software that allows you to configure how signals are captured and displayed.

**ADC:** Analog-to-Digital Converter. The ADC is in charge of sampling the electrical signal at regular intervals and converting the voltage to digital information that is stored in memory. ADCs for oscilloscopes often have 8, 12, or 16 bits of resolution.

**Memory:** Sampled data from the ADC is stored to memory. This information is used to reconstruct a close approximation of the electrical signal--a waveform--on the display.

**Time Base:** Used to control the horizontal (time) axis on the display. Triggering information can be used to adjust the time base so that a periodic signal, like a sine wave, appears stable in the display.

**Display:** On modern, digital oscilloscopes, the waveform is generated from information in the time base and data in memory. Most often, waveforms are shown with voltage as the Y-axis and time as the X-axis.

### How Do Logic Analyzers Work?

The following diagram shows the basic functional blocks found in most logic analyzers. Like in the oscilloscope example, the blocks have been simplified.

![Block diagram of a logic analyzer](../.gitbook/assets/logic\_analyzer\_block\_diagram.png)

**Probes:** If you are using a logic analyzer, you might need to fit many probes into a tight space. As a result, probes are often simple: a piece of wire with a clip and little or no circuitry. Some probes can have dozens of channels packed into a single, high-density connector that requires a specialized mounting point on your test system.

**Clock Select:** Some logic analyzers will allow you to choose which clock is used to sample the signals. An internal clock will sample at regular intervals (timing mode), or an input channel may be used as a clock source (state mode).

**Comparator:** Unlike an oscilloscope, the logic analyzer compares each input signal to a user-defined voltage threshold. If the voltage is higher than the threshold, it is stored as a logic high (1). Otherwise, it is stored as a logic low (0). Because logic analyzers do not require ADCs, they often have many more channels than oscilloscopes.

**Trigger Logic:** Logic analyzers frequently have more triggering features than oscilloscopes. Any or all of the probed channels can be used to trigger the start of a capture, and some advanced logic analyzers will let you construct a series of if-then-else statements to create complex triggers.

**Trigger Select:** Some logic analyzers will allow you to select between triggering from the captured channels or a separate "trigger" input. This specialized input can be used for synchronizing to other test equipment, such as an oscilloscope.

**Memory:** Much like many modern oscilloscopes, logic analyzers store the captured series of logic 1s and 0s in memory. Memory can be inside the logic analyzer's chassis or on a computer (as is the case for USB logic analyzers).

**Display:** Waveforms depicting the captured digital signals are drawn on a display for the user. Similar to oscilloscopes, the Y-axis for each waveform is voltage. However, the voltage is a 1-bit value: logic high just shows the voltage was over a threshold and logic low shows the voltage was under it. The X-axis is time.

### Mixed Signal Oscilloscope

Sometimes, you might find yourself in need of both a logic analyzer and an oscilloscope. Many electrical engineers will have both machines on their workbench. However, the combination of logic analyzer and oscilloscope can be found in a piece of equipment called the _Mixed Signal Oscilloscope_ (MSO).

![Example of a Mixed Signal Oscilloscope](../.gitbook/assets/Hmo3524.jpg)

&#x20;_Image credits: "_ 350 MHz Mixed Signal Oscilloscope HMO3524 by HAMEG Instruments_" by Hameg_ _is licensed under_ [_CC BY SA 3.0_](https://creativecommons.org/licenses/by-sa/3.0/deed.en)_​_

MSOs can capture and display analog as well as digital signals. They often have several oscilloscope channels along with dozens of digital inputs. Additionally, they can be configured with complex triggers based on both analog and digital characteristics.
