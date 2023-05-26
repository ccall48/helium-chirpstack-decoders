## SenseCAP S2100

### Example Uplink Decoder
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

Please submit pull request to main repository to report/repair any bad links or to provide additional documentation or node reviews.