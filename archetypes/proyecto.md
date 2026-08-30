---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
draft: true
summary: ""

# Ciclo de vida del proyecto
estado: "en-curso" # idea | en-curso | completado

# Campos de la etiqueta de telemetría:
# "PROYECTO · <categoria> · <ubicacion> · <metrica_valor> <metrica_unidad>"
categoria: ""         # p.ej. "LoRaWAN" — tecnología/dominio principal
ubicacion: "ETSI"      # contexto/lugar
metrica_valor: 0       # p.ej. 12
metrica_unidad: ""     # p.ej. "nodos", "sensores"

# Datos ampliados, para el cuerpo del artículo (no forman parte de la etiqueta)
stack: []              # lista completa hardware+software
personas:
  - nombre: ""
    rol: ""
repositorio: ""         # URL de GitHub/GitLab, opcional

destacado: false        # si aparece en "proyectos destacados" de la home

showDate: false
showAuthor: false
---
