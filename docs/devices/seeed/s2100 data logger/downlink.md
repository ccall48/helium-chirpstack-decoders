## S2100 Datalogger

### fPort: 3
Set the Data Uplink Interval<br />
0x80 0x00 0x00 duty_H duty_L

Example: Set the Node’s data interval is 10 minutes. Send the downlink command (HEX) via FPort=3:
80 00 00 00 0A

### Command List:<br />
0x80    Fixed field<br />
0x00    Fixed field<br />
0x00    Fixed field<br />
duty_L  Data interval low byte, you can set the data interval, unit: minute<br />
duty_H  Data interval high byte, you can set the data interval, unit: minute<br />

### Example Commands<br />
Set Uplink interval = 1 minute<br />
8000000001<br />
Set Uplink interval = 5 minutes<br />
8000000005<br />
Set Uplink interval = 10 minutes<br />
800000000A<br />
Set Uplink interval = 15 minutes<br />
800000000F<br />
Set Uplink interval = 20 minutes<br />
8000000014<br />
Set Uplink interval = 30 minutes<br />
800000001E<br />
Set Uplink interval = 60 minutes<br />
800000003C