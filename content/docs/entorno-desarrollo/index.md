---
title: "Preparar el entorno de desarrollo"
date: 2026-02-10
draft: true
summary: "Lo mínimo para clonar el repo de un proyecto de IoTUS y tenerlo corriendo en tu máquina."
showTableOfContents: true
---

*(Contenido de ejemplo — pendiente de que la junta confirme el flujo real de cada
proyecto. La estructura sirve de plantilla para el resto de guías internas.)*

## Requisitos

- Git.
- El toolchain específico del proyecto (se indica en el `README` de cada repositorio:
  PlatformIO para firmware, Node para paneles web, Python para scripts de datos...).
- Cuenta en el GitHub de la organización — pídesela a la junta si no la tienes.

## Pasos generales

1. Clona el repositorio del proyecto al que te sumes.
2. Lee el `README.md` — cada proyecto documenta su propio setup, porque no todos usan el
   mismo stack.
3. Si vas a tocar hardware, coordina con quien lleve el proyecto antes de flashear nada:
   varias placas comparten banco de pruebas en el local.

## Convenciones comunes

- Commits en español, mensaje corto y en imperativo ("añade sensor de humedad", no
  "añadido").
- Ramas por feature, PR antes de tocar `main`.
- Si un proyecto tiene datos de sensores reales, nunca subas credenciales de MQTT/API al
  repositorio — usa variables de entorno.
