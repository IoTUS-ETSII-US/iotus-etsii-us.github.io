---
title: "Cerradura NFC para el local de la asociación (y su registro de quién entra y a qué hora)"
date: 2026-08-25
draft: true
summary: "Sustituir la llave que siempre tiene alguien por una tarjeta NFC y un registro de accesos, para dejar de preguntar en el grupo quién tiene la llave hoy."

estado: "idea"
categoria: "Control de acceso"
ubicacion: "Local IoTUS, ETSI"
metrica_valor: 1
metrica_unidad: "puerta"

stack: ["ESP32", "lector RC522 (RFID/NFC)", "cerradura eléctrica 12V", "Node-RED", "SQLite"]
personas:
  - nombre: "Nombre Apellido"
    rol: "Propuesta y hardware"

destacado: false
showDate: false
showAuthor: false
---

## Por qué

El local de la asociación tiene una llave física. Esa llave tiene, según quién cuente la
historia, entre dos y cinco copias en circulación. Ninguna está donde debería en el momento
en que hace falta.

**Nota del laboratorio**: este proyecto todavía es una idea con esquema en una pizarra, no
hardware soldado. Lo dejamos aquí igualmente — enseñar el "en construcción" es parte del
trato.

## Qué haría

- Lector NFC en la puerta, tarjetas del carné universitario o llavero propio.
- Registro de aperturas con fecha y hora, consultable por la junta.
- Botón físico de emergencia para cuando el NFC decida no cooperar (siempre hay un día así).

## Estado

En fase de diseño. Si te interesa el control de acceso o quieres prestar un lector RC522
que tengas cogiendo polvo, pásate por el local.
