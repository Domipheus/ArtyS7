# Test of HDMI out at 720p60 on Arty S7 board

This uses souce from my Spartan6 TPU CPU/SoC to implement an HDMI/DVI-D test on the Arty S7 Spartan 7 board.

NOTE: I have tested on an Arty S7 Revision B board. If you have Rev E, you may need to use the Rev E constraint file instead.

Output is via the 4 differential pairs of 'High Speed' PMOD port JA. You can use an HDMI connector breakout to map the pins to an HDMI cable.

| Pin | HDMI Pin | Description |
| --- | --- | --- |
| 1 | 9 | TMDS0+ |
| 2 | 7 | TMDS0- |
| 3 | 4 | TMDS1+ |
| 4 | 6 | TMDS1- |
| 5 | 2,5,8,11,13,17,plug surround | GND of all HDMI connector signals |
| 6 | x | No Connection |
| 7 | 1 | TMDS2+ |
| 8 | 3 | TMDS2- |
| 9 | 10 | TMDSCLK+ |
| 10 | 12 | TMDSCLK- |
| 11 | x |No Connection |
| 12 | x |No Connection |

I have managed up to 1080p60 and 1440p30 with slightly out of spec timings on an HDMI monitor, using a 1m cable.