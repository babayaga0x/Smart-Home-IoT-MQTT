# Notas

## Cómo fluyen los datos

La cámara es el dispositivo IoT y la SBC funciona como intermediaria: la cámara no tiene un cliente MQTT propio, así que la SBC se conecta a la red (por Wi-Fi, mediante AP3-EXTERIOR) y al broker y publica los datos en su nombre.

```
Cámara → SBC2 → Broker MQTT → Laptop1
```

1. **Laptop1** se suscribe al topic `iot/camara`.
2. La **SBC2** publica `estado=activa` en el topic `iot/camara` con su cliente MQTT.
3. El **broker MQTT** recibe los datos y los reenvía al suscriptor.
4. **Laptop1** recibe los datos.

Así se demuestra que un dispositivo IoT puede enviar datos a través de MQTT y que otro dispositivo puede recibirlos.

Las capturas de cada paso están en [`evidence/`](../../evidence/).

## Sobre los paquetes en rojo en modo Simulación

Los paquetes que se ven pasando entre los switches en el modo Simulación de Packet Tracer son una representación visual del tráfico de red y muestran que existe comunicación dentro de la topología. Los indicadores en rojo no significan necesariamente que la red esté fallando; forman parte de cómo Packet Tracer simula el tráfico.
