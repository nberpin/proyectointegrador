---
title: 'Project documentation template'
disqus: hackmd
---

Aplicación LomoAccesible v.02
===
![downloads](https://img.shields.io/github/downloads/atom/atom/total.svg)
![build](https://img.shields.io/appveyor/ci/:user/:repo.svg)
![chat](https://img.shields.io/discord/:serverId.svg)

## Tabla de contenidos

[TOC]

## Descripción general

**LomoAccesible** es una aplicación diseñada para facilitar la localización de estudiantes con movilidad reducida dentro de un centro educativo. A través del cruce de horarios, ubicaciones de aulas y disponibilidad del personal auxiliar, permite una respuesta rápida y eficaz en caso de necesidad.

La herramienta está orientada al uso por parte del personal de apoyo educativo, con el fin de mejorar la atención personalizada y optimizar la asistencia en los desplazamientos por el centro.

## Funcionalidades principales

- Consulta automática de horarios del alumnado.
- Localización prevista de cada estudiante según la franja horaria.
- Selección del auxiliar más adecuado en función de su cercanía y disponibilidad.
- Envío de notificaciones al personal auxiliar asignado.
- Registro de incidencias y asistencias prestadas.

## Datos requeridos

Para el correcto funcionamiento del sistema, se requieren las siguientes fuentes de datos estructuradas:

- 📋 **Listado de alumnado con necesidades motóricas**, incluyendo identificación, nivel educativo y posibles restricciones de movilidad.
- 🕒 **Horarios individuales** que indiquen la asignación de aulas por franja lectiva.
- 🧑‍🏫 **Listado de aulas**, con sus respectivas ubicaciones físicas en el centro (ej. edificio, planta, aula).
- 👩‍⚕️ **Listado de auxiliares**, con turnos, zonas asignadas y geolocalización si está disponible.
- 📌 (Opcional) Mapa del centro escolar con coordenadas físicas para integración con herramientas de localización.

## Funcionamiento del sistema

1. El sistema accede al horario de un alumno para saber en qué aula debería encontrarse.
2. Utiliza la ubicación física del aula para generar un mapa de posicionamiento estimado.
3. Si se registra una petición de asistencia:
   - Se muestra la posición esperada del alumno.
   - Se selecciona el auxiliar más cercano y disponible.
   - Se envía una notificación inmediata al auxiliar asignado.

El objetivo es actuar con agilidad y eficiencia, evitando esperas y mejorando la experiencia educativa del alumnado con movilidad reducida.

## Modelo de diseño

Se ha elegido el **modelo en cascada** por las siguientes razones:

- El proyecto tiene un alcance bien definido.
- Se trabaja con un equipo pequeño.
- No se esperan cambios significativos durante el desarrollo.
- La secuencia de etapas favorece una planificación clara y ordenada.

### Fases y temporalización estimada

- **Análisis de requisitos**: 3 días
- **Diseño de la aplicación**: 5 días
- **Desarrollo frontend**: 7 días
- **Desarrollo backend**: 7 días (en paralelo con frontend)
- **Pruebas y validación**: 3 días
- **Documentación y despliegue**: 2 días

![image](https://hackmd.io/_uploads/rJgOQZPSxe.png)

## Roles en el equipo

- 🎨 **Diseñador/a de interfaz** – 5 días
- 💻 **Programador/a frontend** – 7 días
- 🛠️ **Programador/a backend** – 7 días
- 🗂️ **Responsable de documentación y control de versiones**
- 🔄 Coordinación y seguimiento a través de **Trello** en formato Kanban.

### Herramienta de coordinación

Se ha configurado un tablero Trello con el método Kanban para gestionar las tareas del equipo:

![image](https://hackmd.io/_uploads/HJzVmZvSll.png)

## Control de versiones

Se utiliza **Git** como sistema de control de versiones, con el repositorio alojado en **GitHub**. La estructura recomendada es:

- Rama principal (`main`) protegida.
- Ramas de desarrollo por módulo (`frontend`, `backend`, `docs`).
- Commits con mensajes claros siguiendo el estilo convencional (`feat:`, `fix:`, `docs:`).
- Issues y pull requests para coordinar cambios entre miembros del equipo.

## Diagrama de clases (UML)

Se ha diseñado el siguiente **diagrama de clases** para modelar la lógica interna de la aplicación:

```plantuml
@startuml
class Alumno {
  - id: String
  - nombre: String
  - nivel: String
  - horario: List<Horario>
  + getUbicacionActual(): Aula
}

class Horario {
  - diaSemana: String
  - hora: String
  - aula: Aula
}

class Aula {
  - id: String
  - nombre: String
  - ubicacion: String
}

class Auxiliar {
  - id: String
  - nombre: String
  - disponibilidad: Boolean
  - zonaAsignada: String
  + esDisponible(): Boolean
}

class SistemaAsistencia {
  + localizarAlumno(idAlumno: String): Aula
  + asignarAuxiliar(aula: Aula): Auxiliar
  + notificar(auxiliar: Auxiliar, mensaje: String)
}

Alumno "1" -- "*" Horario
Horario "*" --> "1" Aula
SistemaAsistencia --> Alumno
SistemaAsistencia --> Auxiliar
SistemaAsistencia --> Aula
@enduml

