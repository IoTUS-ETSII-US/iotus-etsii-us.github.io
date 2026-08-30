---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}   # fecha y hora del evento — pasado/futuro se deriva de esto
draft: true
summary: ""

lugar: ""             # p.ej. "Aula 1.3, ETSI"
tipo: ""               # p.ej. "Taller", "Charla", "Hackathon" — segmento de telemetría
plazas: 0              # 0 = sin límite/no especificado
inscripcion_url: ""
inscripcion_estado: "abierta" # abierta | cerrada | agotado | no-requiere
modalidad: "presencial"        # presencial | online | hibrido

showDate: true
showAuthor: false
---
