# Problemas y soluciones

## Problema: la SBC no llegaba a la VLAN 40 / broker MQTT

**Síntoma:** la SBC no podía hacer ping al gateway de la VLAN 40 (`192.168.40.1`) ni al broker MQTT (`192.168.40.10`). Por este motivo no se pudo comprobar correctamente la conexión del cliente MQTT mediante Python.

**Nota:** la cámara está conectada al puerto IoT D0 de la SBC, por lo que su comunicación no se verifica mediante ping IP.

## Solución

La cámara es el dispositivo IoT y la SBC funciona como intermediaria: la cámara no tiene un cliente MQTT propio, así que la SBC se conecta a la red y al broker y publica los datos en su nombre.

```
Cámara → SBC → Broker MQTT → Laptop1
```

1. **Laptop1** se suscribe al topic `iot/temperature`.
2. La **SBC** publica datos en el topic `iot/temperature`.
3. El **broker MQTT** recibe los datos y los reenvía al suscriptor.
4. **Laptop1** recibe los datos.

Así se demuestra que un dispositivo IoT puede enviar datos a través de MQTT y que otro dispositivo puede recibirlos.

Las capturas de cada paso están en [`evidence/`](../../evidence/).

## Sobre los paquetes en rojo en modo Simulación

Los paquetes que se ven pasando entre los switches en el modo Simulación de Packet Tracer son una representación visual del tráfico de red y muestran que existe comunicación dentro de la topología. Los indicadores en rojo no significan necesariamente que la red esté fallando; forman parte de cómo Packet Tracer simula el tráfico.
