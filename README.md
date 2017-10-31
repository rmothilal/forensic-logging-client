# forensic-logging-client
A client library used to connect to the forensic-logging-sidecar

## Installation
You must have setup connection to the @mojaloop npm repo on JFrog in order to install.
`npm install @mojaloop/forensic-logging-client`

## Usage
To use the forensic logging client, you only need to require it in the file where you want to use the sidecar.

```
'use strict'

const Client = require('@mojaloop/forensic-logging-client')

function connectAndWrite(message) {
  const sidecar = Client.create({
      host: localhost,
      port: 5678,
      connectTimeout: 30000,
      reconnectInterval: 5000
    })
  }

  sidecar.connect().then(() => {
    sidecar.write(message)
  }).catch(err =>{

  })
}
```

## API

### create(settings)
Creates a new sidecar client.

- `settings` {Object}
  - `host` {String} The hostname or IP address of the Sidecar Client server. Defaults to 'localhost'.
  - `port` {Number} The port for the Sidecar. Defaults to 5678.
  - `connectTimeout` {Number} The time, in milliseconds, to timeout a connection attempt to the Sidecar. Defaults to 30000.
  - `reconnectInterval` {Number} The time, in milliseconds, between connection attempts to the Sidecar. Defaults to 5000.
  
### sidecarClient.connect()
Connects to the sidecar, returns a promise.
The promise will be rejected with an error if it can't connect to the sidecar.

### sidecarClient.write(message)
Writes a message to the sidecar, returns nothing.

- `message` {String} The message to send to the Sidecar.

This method will throw an error if the sidecar has yet to be connected to.
