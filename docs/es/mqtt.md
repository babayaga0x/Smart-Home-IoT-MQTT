# MQTT

| Ítem | Valor |
|---|---|
| Broker | Server-PT, `192.168.40.10` (VLAN 40) |
| Puerto | TCP `1883` (sin usuario / contraseña) |
| Publicador | SBC (datos de la cámara en el puerto IoT D0) |
| Suscriptor | Laptop1 |
| Topic | `iot/temperature` |

Flujo: Cámara → SBC → Broker → Laptop1.

## Configuración del broker

1. Agregar un **Server-PT** con IP `192.168.40.10`.
2. En el servidor abrir **Programming → Global Script Project → MQTT Broker (Python)** y ejecutar el script del broker ya incluido.
3. El broker escucha en el puerto TCP `1883` y procesa los paquetes MQTT `CONNECT`, `CONNACK`, `PUBLISH` y `SUBSCRIBE`.
4. Conectar la SBC y Laptop1 a `192.168.40.10:1883` (sin autenticación).
5. Suscribir Laptop1 a `iot/temperature` y publicar en ese topic desde la SBC.
6. Verificar que los mensajes publicados por la SBC llegan a Laptop1.

> El broker es el script de ejemplo que trae Packet Tracer; su código **no fue modificado**.

> ⚠️ Usar exactamente la misma cadena de topic en todos lados (código, suscripción de Laptop1, documentación). Los topics MQTT distinguen mayúsculas y minúsculas.
