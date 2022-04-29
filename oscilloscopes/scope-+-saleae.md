# Scope + Saleae

### Understanding the cause

Your **Scope** is great for **“what’s it look like?”**

Your **Saleae** is great for **“what’s the history?”**

### Searching for clues

Your **Scope** is great for **“is the I2C bus running?**”

Your **Saleae** is great for **“where’s my problem in these 10,000 transactions?”**

### Understanding the context

Your **Scope** is great for **“does that signal ever droop during our zero crossings?”**

Your **Saleae** is great for **“what’s the situation before, during, and after my failure? — on these 3 rails, 4 GPIOs, and two SPI buses?”**

### Validating the design

Your **Scope** is great for **“Is my rail too noisy?”**

Your **Saleae** is great for **“Are all 6 of my rails coming up and down in the right sequence?”**

### Extending the capabilities

Your **Scope** is great for **“how can I write Python to capture waveforms?”**

Your **Saleae** is great for **“how can I write Python to decode my proprietary BMS protocol?”**\


### Why the differences?

Scopes take individual “snapshots” of signals, typically up to 4, based on a trigger.  They’re great for seeing what’s happening right now, on up to few signals, especially when those signals continually repeat.  Scopes don’t require you to fire up your computer, so often they are the most convenient tool for the job.  Because they don’t need to record for long periods, that can be be very high bandwidth — critical for signal integrity, eye diagrams, etc. &#x20;

\
Saleae’s logic analyzers can also give you a live view of “what’s going on” — but they really shine when you need to recording lots of signals over fairly long time periods.   Once set up, you could plug in your DUT’s USB cord, type some things into the console,  and then unplug your DUT, maybe 60 seconds later — and have a record of everything that happened during that time —  perhaps several power rails, pwm signals, protocol busses, and GPIOs. &#x20;
