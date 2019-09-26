# Test of HDMI out at 720p60 on Arty S7 board

This uses souce from my Spartan6 TPU CPU/SoC to implement an HDMI/DVI-D test on the Arty S7 Spartan 7 board.

NOTE: I have tested on an Arty S7 Revision B board. If you have Rev E, you may need to use the Rev E constraint file instead.

Output is via the 4 differential pairs of 'High Speed' PMOD port JA. You can use an HDMI connector breakout to map the pins to an HDMI cable.

| Pin | HDMI Pin | Description |
| --- | --- | --- |
| 1 | 4 | TMDS1+ |
| 2 | 6 | TMDS1- |
| 3 | 7 | TMDS0+ |
| 4 | 9 | TMDS0- |
| 5 | 2,5,8,11,13,17,plug surround | GND of all HDMI connector signals |
| 6 | x | No Connection |
| 7 | 1 | TMDS2+ |
| 8 | 3 | TMDS2- |
| 9 | 10 | TMDSCLK+ |
| 10 | 12 | TMDSCLK- |
| 11 | x |No Connection |
| 12 | x |No Connection |

I have managed up to 1080p60 and 1440p30 with slightly out of spec timings on an HDMI monitor, using a 1m cable.
Tested configurations below:


# 1080p60
```
150MHz pixel clock
vga_gen generic values:
hRez       : natural := 1920;	
hStartSync : natural := 1920+88;
hEndSync   : natural := 1920+88+44;
hMaxCount  : natural := 1920+88+44+148;
hsyncActive : std_logic := '0';
vRez       : natural := 1080;
vStartSync : natural := 1080+4;
vEndSync   : natural := 1080+4+5;
vMaxCount  : natural := 1080+4+5+36;
vsyncActive : std_logic := '1'
```

# 1440p30
```
150MHz pixel clock
vga_gen generic values:
hRez       : natural := 2560 ;    
hStartSync : natural := 2680 ;
hEndSync   : natural := 2944 ;
hMaxCount  : natural := 3328 ;
hsyncActive : std_logic := '0';
vRez       : natural := 1440;
vStartSync : natural := 1443 ;
vEndSync   : natural := 1448 ;
vMaxCount  : natural := 1468;
vsyncActive : std_logic := '1'
```

# 800x480x60hz (many 5" HDMI Raspberry Pi screens)
```
33.33MHz pixel clock
vga_gen generic values:
hRez       : natural := 800;    
hStartSync : natural := 800+40;
hEndSync   : natural := 800+40+128;
hMaxCount  : natural := 800+40+128+88;
hsyncActive : std_logic := '0';
vRez       : natural := 480;
vStartSync : natural := 480+8;
vEndSync   : natural := 480+8+2;
vMaxCount  : natural := 480+8+2+35;
vsyncActive : std_logic := '1'
```

# 720p60
```
75MHz pixel clock
vga_gen generic values:
hRez       : natural := 1280;    
hStartSync : natural := 1280+72;
hEndSync   : natural := 1280+72+80;
hMaxCount  : natural := 1280+72+80+216;
hsyncActive : std_logic := '0';
vRez       : natural := 720;
vStartSync : natural := 720+3;
vEndSync   : natural := 720+3+5;
vMaxCount  : natural := 720+3+5+22;
vsyncActive : std_logic := '1';
```