# Troubleshooting

## Problem: SBC could not reach VLAN 40 / MQTT broker

**Symptom:** the SBC could not ping the VLAN 40 gateway (`192.168.40.1`) or the MQTT broker (`192.168.40.10`). Because of this, the MQTT client written in Python could not be tested.

**Note:** the camera is connected to IoT port D0 of the SBC, so its communication is not verified with IP ping.

## Solution

The camera is the IoT device and the SBC works as an intermediary: the camera has no MQTT client of its own, so the SBC connects to the network and to the broker and publishes the data for it.

```
Camera → SBC → MQTT Broker → Laptop1
```

1. **Laptop1** subscribes to the topic `iot/temperature`.
2. The **SBC** publishes data on the topic `iot/temperature`.
3. The **MQTT broker** receives the data and forwards it to the subscriber.
4. **Laptop1** receives the data.

This demonstrates that an IoT device can send data over MQTT and that another device can receive it.

Screenshots of each step are in [`evidence/`](../evidence/).

## About red packets in Simulation mode

The packets passing between the switches in Packet Tracer's Simulation mode are a visual representation of network traffic and show that communication exists across the topology. Red indicators do not necessarily mean the network is failing; they are part of how Packet Tracer simulates traffic.
