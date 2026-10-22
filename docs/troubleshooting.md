# Notes

## How the data flows

The camera is the IoT device and the SBC works as an intermediary: the camera has no MQTT client of its own, so the SBC connects to the network (over Wi-Fi, through AP3-EXTERIOR) and to the broker and publishes the data for it.

```
Camera → SBC2 → MQTT Broker → Laptop1
```

1. **Laptop1** subscribes to the topic `iot/camara`.
2. **SBC2** publishes `estado=activa` on the topic `iot/camara` with its MQTT client.
3. The **MQTT broker** receives the data and forwards it to the subscriber.
4. **Laptop1** receives the data.

This demonstrates that an IoT device can send data over MQTT and that another device can receive it.

Screenshots of each step are in [`evidence/`](../evidence/).

## About red packets in Simulation mode

The packets passing between the switches in Packet Tracer's Simulation mode are a visual representation of network traffic and show that communication exists across the topology. Red indicators do not necessarily mean the network is failing; they are part of how Packet Tracer simulates traffic.
