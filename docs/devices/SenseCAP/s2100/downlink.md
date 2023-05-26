## S2100 Datalogger

### Set the Data Uplink Interval<br />
0x80 0x00 0x00 duty_H duty_L

Example: Set the Node’s data interval is 10 minutes.<br />
Send the downlink command (HEX) via FPort=3:<br />
`80 00 00 00 0A`

### Command List
0x80    Fixed field<br />
0x00    Fixed field<br />
0x00    Fixed field<br />
duty_L  Data interval low byte, you can set the data interval, unit: minute<br />
duty_H  Data interval high byte, you can set the data interval, unit: minute<br />

### Change Uplink Interval
Set Uplink interval = 1 minute<br />
`8000000001`<p />
Set Uplink interval = 5 minutes<br />
`8000000005`<p />
Set Uplink interval = 10 minutes<br />
`800000000A`<p />
Set Uplink interval = 15 minutes<br />
`800000000F`<p />
Set Uplink interval = 20 minutes<br />
`8000000014`<p />
Set Uplink interval = 30 minutes<br />
`800000001E`<p />
Set Uplink interval = 60 minutes<br />
`800000003C`