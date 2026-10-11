# MQTT

| Item | Value |
|---|---|
| Broker | Server-PT, `192.168.40.10` (VLAN 40) |
| Port | TCP `1883` (no username / password) |
| Publisher | SBC (data from the camera on IoT port D0) |
| Subscriber | Laptop1 |
| Topic | `iot/temperature` |

Flow: Camera → SBC → Broker → Laptop1.

## Broker setup

1. Add a **Server-PT** with IP `192.168.40.10`.
2. On the server open **Programming → Global Script Project → MQTT Broker (Python)** and run the ready-made broker script.
3. The broker listens on TCP port `1883` and handles the MQTT packets `CONNECT`, `CONNACK`, `PUBLISH` and `SUBSCRIBE`.
4. Connect the SBC and Laptop1 to `192.168.40.10:1883` (no authentication).
5. Subscribe Laptop1 to `iot/temperature` and publish to it from the SBC.
6. Check that the messages published by the SBC arrive at Laptop1.

> The broker is the example script that ships with Packet Tracer; its code was **not modified**.

> ⚠️ Use one exact topic string everywhere (code, Laptop1 subscription, docs). MQTT topics are case-sensitive.
