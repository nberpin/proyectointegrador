---
title: 'Project documentation template'
disqus: hackmd
---
Aplicación LomoAccesible
===
![downloads](https://img.shields.io/github/downloads/atom/atom/total.svg)
![build](https://img.shields.io/appveyor/ci/:user/:repo.svg)
![chat](https://img.shields.io/discord/:serverId.svg)

## Table of Contents

[TOC]

## Descripción

Esta aplicación permite ubicar en todo momento a los alumnos con problemas motóricos, utilizando sus horarios y la asignación de aulas. Facilita que el personal auxiliar pueda localizar rápidamente dónde se encuentra un alumno en cada hora lectiva y así enviar al auxiliar más adecuado desde una lista previamente definida.

Datos necesarios
---

Para su funcionamiento, la aplicación necesita las siguientes fuentes de datos:

📋 Listado de alumnado con necesidades motóricas, con su identificación y nivel educativo.

🕒 Horario de cada alumno, que indique en qué aula debería encontrarse en cada hora.

🧑‍🏫 Listado de aulas y su ubicación física dentro del centro.

👩‍⚕️ Listado de auxiliares disponibles, junto con sus turnos, disponibilidad y localización actual (si está geolocalizada o asignada a zonas).


Funcionamiento
---

* Consulta automática del horario del alumno para determinar en qué aula debe estar en cada franja horaria.

* Cruce con la ubicación física de las aulas para generar un mapa actualizado de localización esperada de cada estudiante.

* En caso de incidencia o petición de asistencia, la aplicación:

* Muestra en pantalla la localización prevista del alumno.

* Sugiere el auxiliar más próximo y disponible.

* Lanza una notificación o aviso interno al auxiliar asignado.

Este sistema permite actuar con agilidad ante cualquier necesidad de desplazamiento o asistencia en el entorno educativo, y reduce la carga organizativa del equipo docente.




## Modelo de diseño
Elejimos un modelo de diseño en cascada ya que es un proyecto corto con un equipo pequeño y no se esperan muchos cambios sobre la idea inicial. 
Las fases y la temporalización podrían ser como sigue: 

![image](https://hackmd.io/_uploads/rJgOQZPSxe.png)

Roles 
---
Seremos un pequeño equipo:
Diseño de la aplicación: 5 días, a cargo del diseñador.

Programación Frontend: 7 días, a cargo del programador frontend.

Programación Backend: 7 días, en paralelo con el frontend, a cargo del programador backend.

Para poder coordinarnos usaremos Trello que hemos configurado con un esquema Kanban
![image](https://hackmd.io/_uploads/HJzVmZvSll.png)
