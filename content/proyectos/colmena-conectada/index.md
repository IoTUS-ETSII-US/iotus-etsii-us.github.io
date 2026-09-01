---
title: "Colmena conectada"
date: 2026-07-02
draft: false
summary: "Peso, temperatura y humedad de tres colmenas experimentales, para saber si están bien sin tener que abrirlas y arriesgarse a que opinen lo contrario."

estado: "en-curso"
categoria: "Sensórica ambiental"
ubicacion: "Finca experimental, ETSIA"
metrica_valor: 3
metrica_unidad: "colmenas"

stack: ["Arduino Nano 33 IoT", "célula de carga + HX711", "DHT22", "LoRa punto a punto", "InfluxDB"]
personas:
  - nombre: "Nombre Apellido"
    rol: "Hardware y calibración"
  - nombre: "Nombre Apellido"
    rol: "Colaboración con ETSIA"
repositorio: "https://github.com/iotus-etsii/colmena-conectada"

destacado: true
showDate: false
showAuthor: false
---

## Por qué

Un apicultor sabe si una colmena va bien por el peso: gana peso cuando hay buena cosecha,
lo pierde en invierno. El problema es pesar una colmena sin abrirla ni molestar a sesenta
mil animales con aguijón (que te lo clavan con mas gusto que la universídad la  27ª matricula de ADDA  o FFI). La solución fue una célula de carga bajo cada colmena y un nodo
que reporta cada hora.

**Nota del laboratorio**: la primera versión del firmware confundía "cae la temperatura por
la noche" con "la colmena ha desaparecido" y mandaba una alerta a las tres de la madrugada.
El sensor no tenía la culpa. El código, sí.

## Qué mide

- Peso total de la colmena, en gramos, con resolución suficiente para ver el efecto de una
  sola abeja aterrizando (en teoría; en la práctica el ruido de fondo lo tapa).
- Temperatura y humedad interior y exterior, para comparar.
- Actividad de vuelo, estimada por vibración — todavía en fase de calibración.

## Estado

Se murío el que teníamos como jefe de proyectos (era alergico a las abejas).

La abeja maya nos llevó a la haya por violación masiva de la privacidad de las abejas, así que yo diriá que lo hicimos muy bien.
