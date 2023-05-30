## SenseCAP S2100

![SenseCAP S2100!](https://media-cdn.seeedstudio.com/media/catalog/product/cache/bb49d3ec4ee05b6f018e93f896b8a25d/f/i/first_page_all-22.jpg)

SenseCAP S2100 Data Logger can connect to MODBUS-RTU RS485/Analog/GPIO sensors and transmit data from sensors to the LoRaWAN network. Benefits from LoRa and IP66 design, this device features stability and reliability and can cover a long transmission range while keeping ultra-low power consumption, ideal for outdoor use. It is specifically optimized for OTA with built-in Bluetooth, which enables quick setup and update. It can be battery-powered or connected to a 12V external power supply. When the 12V power supply is connected, the replaceable built-in battery is set to be used as the backup power supply. What's more, with the help of S2110 converter, S2100 Data Logger is able to connect to Grove Sensor, it is an ideal solution for developing, fast prototyping, and small deployment for DIY Industrial level LoRaWAN Sensors.

[SenseCAP S2100](https://www.seeedstudio.com/SenseCAP-S2100-LoRaWAN-Data-Logger-p-5361.html)

## Example Payload Codec
Cayenne compatible: Yes/No/Unknown

### Example Uplink Codec
```js
function decodeUplink(input) {
    let data = buf2Hex(input.bytes);
    let numMeasure = data.substring(0, 6);
    let metrics = data.substring(data.lastIndexOf(39));
    let decoded = {};

    switch (numMeasure) {
        case '311001':
            // TODO: one measurement
            break;
        case '311202':
            // TODO: two measurements
            break;
        case '301202':
            // TODO: three or four measurements
            decoded.ambient = hex2int(data.substring(6, 14)) / 10000;
            decoded.compressor = hex2int(data.substring(14, 22)) / 1000;
            decoded.defrost = hex2int(data.substring(28, 36)) / 1000;
            break;
        case '301203':
            // TODO: five or six measurements
            break;
        default:
            break;
    }

    if (metrics.length === 20) {
        decoded.battery = hex2int(metrics.substring(2, 4));
        decoded.upInterval = hex2int(metrics.substring(12, 16));
    }
    return {data: decoded};
}

function buf2Hex(buffer) {
    return [...new Uint8Array(buffer)]
        .map (b => b.toString(16).padStart (2, '0'))
        .join ('');
}

function hex2int(hex) {
    return parseInt(hex, 16);
}
```
### Example Downlink Codec
#### Set the Data Uplink Interval<br />
0x80 0x00 0x00 duty_H duty_L

Example: Set the Node’s data interval is 10 minutes.<br />
Send the downlink command (HEX) via FPort=3:<br />
`80 00 00 00 0A`

#### Command List
```
0x80    Fixed field
0x00    Fixed field
0x00    Fixed field
duty_L  Data interval low byte, you can set the data interval, unit: minute
duty_H  Data interval high byte, you can set the data interval, unit: minute
```

#### Change Uplink Interval
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

Please submit pull request to main repository to report/repair any bad links or to provide additional documentation or node reviews.