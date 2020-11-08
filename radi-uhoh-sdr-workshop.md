# Radi-uhoh: What is this SDR Thing and How do I Use It?
Josh Conway

Repo with slides: https://gitlab.com/crankylinuxuser/remoticon2020

# Basics of SDR
10's of thousands of radio protocols
SDR allows switching protocls like switching software
Not monolithic
## What is SDR not good for?
- Your wallet
- Protocls with hard timing constraints
- Nearby LOUD FM broadcast stations
- Potentially easy to break the law

## Basics behind radio signals

Modulation
- Analog modulation (amplitude, frequency, and phase modulation)
- Digital modulation (amplitude, frequency, and phase shift keying)

4QAM - quadrature amplitude modulation, or HD radio
Four quadrants, encoding amplitude, phase, etc. High data compression

# Hardware
## RTL-SDR
- Cheap, easy to obtain
- 24MHz-1766MHz
- 2.4MHz bandwidth
- Sometimes dubious build quality
- Janky included antennas

## ADALM-PLUTO
- $100-$150
- Dual core Arm with Linux that you can flash software to
- 70MHz-6GHz
- 20MHz window
- Can run programs on device
- Send and receive
- USB2 limits overall bandwidth
- 5mW transmit (which can be good since you can barely get in trouble)

## HackRF
- $300
- 1MHz-6GHz
- Sweep mode- 8GHz/second
- Cannot do transmit/receive at the same time
- 8 bit signal capture, which is limiting

## KerberosSDR
- $150
- Coherent Quad RTL-SDR
- 24MHz-1.7GHz
- Also is 8 bit like the HackRF
- Toolchain is bare bones- less software or niceties

## BLadeRF A(4/9)
- $480
- 2 TX, 2 RX
- 47MHz-6GHz @ 61 MHz bandwidth
- Known clock jitter issue
- GPSDO recommended- uses GPS to correc the clock signal but costs extra

# Antennas

Default antennas for most hardware not considered good enough

Log periodic antennas - can be made on PCBs and cover frequency from the lognest to the shortest "tines"
Similar to a Yagi antenna but you get a wider response while also being directional like the Yagi antennas.

Vivaldi antennas- can be made with PCBs as well and has a "horn" design
Extremely directional. Mostly used for ground pentrating radar

Helical antennas - great for space where circular polarization makes it easier then thinking about "horizontal" and "vertical" polarization.

# Computers
Dedicated USB3
More CPU the better
More RAM the better
Good graphics card for OpenCL
If over ethernet, 1G or 10G

# Software
## Operating systems
Rasbian, Kali, Pentoo

## Reading Signals
GQRX - gets you frequency and waterfall plots, lots of decoders

SDR# - Good option for Windows, lots of decdoers

SDRAngel - Also lets you act as a transmitter. Sort of like a TV broadcasting tool Also supports video

ShinySDR - web server streaming data to your endpoint if your SDR isn't present with you (e.g. an attic install)

# Reverse Engineering

URH - Universal Radio Hacker: capture data from SDR, save it, and then analyze it with their tool. They have an audo-detect feature which is very interesting

SigDigger- another auto-detect and analysis tool

Inspectum - another auto-detect and analysis tool

# Transmitters

RPITX - turn an RPi into a transmitter
Realtime TX on a GPIO pin
Do not transmit on an antenna without a band-pass filter!

# Advanced Tools:
- GnuRadio Companion: GUI that lets you connect different plugins that builds you a radio in software
Has a Python package associated with it
- RedHawk - similar to GnuRadio Companion but lets you have multiple transmitters and receivers

# Non-SDR Tools
- NodeRED - drag and drop programmer with function blocks. Lets you connect tools to process and share data

# SDR PRojects
Airplane Detector, Virtual Radar Server - aircraft have radio transmitters that emit their name and their location/heading
Ship Plotter is similar, but for ships and boats
Home power sniffer called the Itron data recorder
- Uses the smart meters installed by utilities

LocalRadio - RTL-SDR software to listen in on nearby radio, like emergency vehicles and emergency alerts

DIY Radio Astronomy - PICTOR

Salamandra - Spy Microphone Detector. Has a speaker where it emits test tones, and then looks for correlations in devices transmitting. 

# Sigidwiki (Signal Identification Wiki)

Recommended IQ, images, etc. wiki dataset that lets you figure out what you're looking at

# Cognitive Radio

Only briefly brought this up but it's effectively machine learning for radios- definitely want to look into this

# Utility meters

Working on decoders for radio water meters

Water pumps and other utility equipment have these radio transmitters

Could be used to detect if someone were on vacation, fingerprinting, etc.

# Hardware Analysis

SDR to listen to harmonics that can signal the failure points of a solar panel

# TEMPEST

Demosntrated a GNUradio "attack" to pick up the LCD screen's radio emissions from the monitor next to him