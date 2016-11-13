## Node.js Eddystone and iBeacon Farol beacon implementation

### Run

```bash
docker run --net=host --rm -e BEACON="beacon-spec" menvia/farol-node-beacon
```

Where ```beacon-spec``` can be an ```eddystone``` or ```ibeacon```.

#### Eddystone

Based on [node-eddystone-beacon](https://github.com/don/node-eddystone-beacon), e.g.:

```js
var eddystoneBeacon = require('eddystone-beacon');
var options = {
  name: 'Eddy',      // set device name when advertising (Linux only)
  txPowerLevel: -22, // override TX Power Level, default value is -21,
  tlmCount: 2,       // 2 TLM frames
  tlmPeriod: 10      // every 10 advertisements
};
var url = 'https://google.com/';
eddystoneBeacon.advertiseUrl(url, [options]);

```

#### iBeacon

Based on [node-bleacon](https://github.com/sandeepmistry/node-bleacon), e.g.:

```js
var Bleacon = require('bleacon');
var uuid = 'e2c56db5dffb48d2b060d0f5a71096e0';
var major = 6; // 0 - 65535
var minor = 9; // 0 - 65535
var measuredPower = -59; // -128 - 127 (measured RSSI at 1 meter)
Bleacon.startAdvertising(uuid, major, minor, measuredPower);

```

