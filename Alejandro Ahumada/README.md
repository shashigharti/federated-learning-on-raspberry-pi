Project based on [this tutorial by Daniele Gadler](https://blog.openmined.org/federated-learning-of-a-rnn-on-raspberry-pis/).

# Tools needed/used
- Laptop (macOS)
- 2x Raspberry Pi Model 3B
- Local Network (Ethernet or WiFi)
- Wireless Keyboard (initial setup)
- Tv and HDMI cable (initial setup)
 
# Project phases
 - ## Initial setup
    - Installed a fresh copy of Raspbian on an empty card.
    - I connected the first RPi to a screen and wireless keybboard to do an initial setup:
        - connect it to WiFi
        - enable SSH
        - boot on CLI
    - Install Python, PyTorch and PySyft.
    - Clone card to the second RPi3B and give it an unique name.
 - ## Python
    - **Laptop:** Python 3.7 already installed on Anaconda env.
    - **Raspberry Pi:** I compiled and installed Python 3.6.7 with no problems following the tutorial steps.
 - ## Pytorch (v1.1.0)
    - **Laptop:** Installed via conda.
    - **Raspberry Pi:** I compiled and installed version 1.1.0.
    At the time of writing v1.2.0 had just been released, but had not been tested with latest PySyft release, so I chose to stick to v1.1.0.
        - I had some issues with Raspbian Buster GCC version, they've been summarized in the [troubleshooting guide](https://github.com/shashigharti/federated-learning-on-raspberry-pi/wiki/Troubleshooting).
 - ## PySyft (v0.1.23a1)
    - Had some issues that were solved by running the exact same version on PySyft on all devices as stated on [troubleshooting guide](https://github.com/shashigharti/federated-learning-on-raspberry-pi/wiki/Troubleshooting).     
# General workflow
- Mostly used Raspberry Pis on a headless setup (except initial setup).
- Access RPi3B via macOS SSH in terminal to launch worker servers and build tools.
- Used VS Code remote tools to edit code both on my laptop and the two RPi3B.