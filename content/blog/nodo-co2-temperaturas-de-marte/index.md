---
title: "Bitácora: por qué nuestro primer nodo LoRaWAN reportaba temperaturas de Marte"
date: 2026-04-03
draft: true
summary: "El nodo 7 del proyecto de CO2 llevaba una semana reportando -60°C. La aula no estaba tan mal ventilada."
showAuthor: false
---

{{< telemetry-label "Bitácora" "LoRaWAN" "ETSI" "Nodo 7" >}}

Semana tres del despliegue. Once nodos reportando temperaturas razonables, entre 19 y 24°C.
El nodo 7 reportando una media de -60°C, con picos ocasionales de -80°C. En Grafana parecía
que alguien había dejado una ventana abierta directamente al espacio exterior.

## Primera sospecha: el sensor

Cambiamos el sensor MH-Z19 del nodo 7 por uno nuevo. Mismo resultado. El sensor no era el
problema — o al menos no ese sensor en concreto.

## Segunda sospecha: el firmware

Revisamos la función de lectura de temperatura. Aquí está el fragmento sospechoso:

```c
int16_t raw_temp = read_sensor_temp();
float temp_celsius = raw_temp - 40; // offset del datasheet
```

El offset estaba bien. Lo que no estaba bien era `raw_temp`: el sensor devuelve la
temperatura como un `uint8_t` sin signo, no como un `int16_t`. Cuando la lectura pasaba de
`0x00` a `0xFF` por un problema de contacto en el cable de datos (soldadura floja, cómo no),
el valor se interpretaba como -1, y de ahí para abajo.

<!-- TODO: pendiente foto real del pin de datos resoldado — cuando exista,
     añadirla al bundle y usar el shortcode figure. -->
{{< telemetry-label "Foto" "Soldadura" "Nodo 7" "2mm de menos" >}}

## La solución

Resoldar el pin, cambiar `int16_t` por `uint8_t` en la lectura cruda, y añadir un rango
válido (`0-50°C`) que descarta cualquier lectura fuera de lo físicamente posible en un aula.
Si un aula de la ETSI llega algún día a -60°C, tenemos problemas mayores que un sensor.

**Nota del laboratorio**: el nodo 7 lleva desde entonces reportando temperaturas
terrestres. Se le echa de menos igualmente.
