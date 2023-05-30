## Vega SI-11 Pulsecounter

![Vega SI-11!](https://en.iotvega.com/content/ru/si/si11/3.jpg)

## Description
Vega SI-11 pulse counter is designed for counting of pulses incoming to 4 independent inputs, further accumulating and transmitting of this information via the LoRaWAN® protocol to the gateway through wireless communication within 860-1000 MHz frequency plan.

[Vega SI-11](https://en.iotvega.com/product/si11)

#### Example Payload Codec
Cayenne compatible: *No*

```js
/****************************************************************************************
v1.4 cory callcott -> cory@callref.com.au
construct byte packet decoder for 24bytes sent from vega-si11 device
*****************************************************************************************/
function decodeUplink(input) {
    let bytes = input.bytes;
    let decoded = {}
    /*
    Convert bytes to get raw values and pulses from pulse counter
    */
    decoded.pktType  = bytes[0];
    decoded.battery  = bytes[1];
    decoded.values   = bytes[2];
    decoded.readTime = bytes[6] << 24 | bytes[5] << 16 | bytes[4] << 8 | bytes[3];
    decoded.ambient  = bytes[7];
    /*
    Pulses can be setup as 4 x pulse counters or as secuity guards.
    Adjust to suit desired application.
    */
    decoded.pulse_1 = ((bytes[11]<<24|bytes[10]<<16|bytes[9]<<8|bytes[8]) * 5) / 1000;
    decoded.pulse_2 = ((bytes[15]<<24|bytes[14]<<16|bytes[13]<<8|bytes[12]) * 5) / 1000;
    decoded.pulse_3 = ((bytes[19]<<24|bytes[18]<<16|bytes[17]<<8|bytes[16]) * 5) / 1000;
    decoded.pulse_4 = ((bytes[23]<<24|bytes[22]<<16|bytes[21]<<8|bytes[20]) * 5) / 1000;

    return {data: decoded};
}

/*****************************************
* downlink function not set or tested
******************************************/
function encodeDownlink(input) {
  	let port = input.fPort;
  	let bytes = input.bytes;
	return {data: bytes, fPort: port};
}
```
Please submit pull request to main repository to report/repair any bad links or to provide additional documentation or node reviews.