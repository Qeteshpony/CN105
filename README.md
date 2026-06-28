# Mitsubishi CN105 compatible heatpump controller for ESPHome and Home Assistant

[![CI](https://github.com/Qeteshpony/CN105/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/Qeteshpony/CN105/actions/workflows/ci.yml)

![3D Render](https://qeteshpony.github.io/CN105/3D/CN105-3D_top.png)

[Hardware Documentation](https://qeteshpony.github.io/CN105)

## Hardware fabrication

I ordered these boards from JLCPCB (Not a sponsor) and had only the smd components on the top side assembled. You then still need an ESP32-C6-WROOM-1 module (gets soldered on the bottom) and a Gaptec LME78_03-1.0 DC/DC Regulator. Also some header pins and a cable with a JST PAP-V-S PA 2.0 5 pin connector which goes into the CN105 port on the heatpumps main board. 

### Some details about the hardware

I decided to use the DC/DC regulator and pull power from the 12V pin of the heatpump since the 5V pin can't handle much current and I didn't want to risk damaging the heatpump. The 5V pin is just used for the pullups on the logic level converter since the heatpumps CN105 connector uses 5V logic which the ESP can't handle properly. 

LEDs 1 and 2 are connected to GPIO 23 and 22 and can be used freely by your software. 

LEDs 3 and 4 show activity on TX and RX and can be left out if you don't want the module to blink all the time... 

## Software

Mine are running with ESPHome and the external component found at [github.com/echavet/MitsubishiCN105ESPHome](https://github.com/echavet/MitsubishiCN105ESPHome)

Since this board uses the ESP32-C5 it can use WiFi as well as Thread to communicate with Home Assistant. 

Keep in mind that cheap serial adapters might not deliver enough power to successfully flash the ESP. I had to feed external power while flashing it. In that case only connect GND, RX and TX of the UART0 header to your serial adapter and feed anything between 6 and 36 volts (That's what the LME78 can handle) into the 12V pin of the boards CN105 header. 
When using ESPHome this is also just needed once. Updates can then be installed OTA. 
