---
title: "Nodo de CO2 para las aulas de la ETSI"
date: 2026-08-18
draft: true
summary: "Doce nodos LoRaWAN midiendo CO2 en las aulas grandes de la ETSI, con panel en tiempo real para que decanato no tenga que fiarse de nuestra palabra."

estado: "completado"
categoria: "LoRaWAN"
ubicacion: "ETSI"
metrica_valor: 12
metrica_unidad: "nodos"

stack: ["ESP32", "sensor MH-Z19 (CO2 NDIR)", "LoRaWAN", "The Things Network", "Node-RED", "Grafana"]
personas:
  - nombre: "Nombre Apellido"
    rol: "Firmware"
  - nombre: "Nombre Apellido"
    rol: "Backend y panel"
repositorio: "https://github.com/iotus-etsii/nodo-co2"

destacado: true
showDate: false
showAuthor: false
---

## Por qué

Después de la tercera clase de la tarde en la que alguien preguntaba si se podía abrir una
ventana "porque hay sueño", decidimos medirlo en vez de discutirlo. Doce nodos, cada uno con
un sensor NDIR (los que no se equivocan por culpa del alcohol de las manos, a diferencia de
los sensores de resistencia baratos), reportando cada cinco minutos por LoRaWAN.

**Nota del laboratorio**: durante las pruebas de calibración expusimos un nodo a una botella
de CO2 comprimido para verificar el rango alto de la escala. El nodo sobrevivió. El becario
que sujetaba la botella, también.

## Qué mide

- CO2 en ppm, cada 5 minutos.
- Temperatura y humedad relativa, de propina — el mismo sensor las da gratis.
- Batería del nodo, para saber cuál hay que cambiar antes de que deje de reportar.

## Estado

Los doce nodos están instalados y reportando desde marzo. El panel de Grafana es público
para cualquier miembro de la asociación — pregunta en el local si quieres el enlace.
