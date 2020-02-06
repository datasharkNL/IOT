Here's what my index.js looks like. You'll notice that I removed the wpi library and any calls to the blinkLED() function. The original program intends for an LED to blink when a message is sent or received by the Raspberry Pi. Since I didn't want to wire anything up, I removed this code from my index.js file. This solved my build errors, as mine was failing on the node-wiring-pi step (again, YMMV).

The final piece of the puzzle is to run without sudo, like this:

$ node index.js "HostName=XXX;DeviceId=XXX;SharedAccessKey=XXX"
You should then see something that looks like this

[Device] Using MQTT transport protocol
[Device] Sending message: {"messageId":1,"deviceId":"Raspberry Pi Node","temperature":29.63832366181949,"humidity":71.62597635438006}
[Device] Message sent to Azure IoT Hub
Just in case you need, here's my config.json as well:

{
  "simulatedData": true,
  "interval": 2000,
  "deviceId": "Raspberry Pi Node",
  "LEDPin": 5,
  "messageMax": 256,
  "credentialPath": "~/.iot-hub",
  "temperatureAlert": 30,
  "transport": "mqtt",
  "iotEdgeRootCertFilePath": null,
  "i2cOption": {
    "pin": 9,
    "i2cBusNo": 1,
    "i2cAddress": 119
  }
}
Let me know if you have any questions!