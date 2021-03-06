# JavaScript SDK

The Losant JavaScript SDK is a library for Node.js compatible compute modules. The library is open source and <a href="https://github.com/Losant/losant-sdk-js" target="_blank">available on GitHub</a>.

Below is a basic example demonstrating how to connect, send [state](/devices/state), and subscribe to [commands](/devices/commands).

```JavaScript
var Device = require('losant-sdk-js').Device;

// Construct gateway.
var device = new Device({
  id: 'my-device-id',
  key: 'my-app-access-key',
  secret: 'my-app-access-secret'
});

// Connect to Losant.
device.connect();

// Listen for commands.
device.on('command', function(command) {
  console.log('Command received.');
  console.log(command.name);
  console.log(command.payload);
});

// Send temperature once every second.
setInterval(function() {
  device.sendState({ temperature: readAnalogIn() });
}, 1000);
```

Please refer to the <a href="https://github.com/Losant/losant-sdk-js" target="_blank">repository</a> for detailed documentation and examples.
