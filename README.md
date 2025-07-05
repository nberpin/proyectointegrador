---
title: 'LomoAccesible - Proyecto de Accesibilidad Educativa'
disqus: hackmd
---

# Aplicación LomoAccesible v.03

![downloads](https://img.shields.io/github/downloads/atom/atom/total.svg)
![build](https://img.shields.io/appveyor/ci/:user/:repo.svg)
![chat](https://img.shields.io/discord/:serverId.svg)

---

## 📘 Descripción general

**LomoAccesible** es una aplicación pensada para mejorar la accesibilidad de estudiantes con movilidad reducida en centros educativos. Permite conocer en tiempo real su localización prevista, asignar personal auxiliar y optimizar la atención educativa.

En esta **tercera iteración**, el proyecto evoluciona desde una idea funcional hacia una propuesta técnica más realista, incorporando lenguaje de programación, arquitectura, base de datos y estrategia de pruebas.

---

## 🆕 Mejoras implementadas en esta versión

- Selección justificada del lenguaje de programación.
- Aplicación del patrón arquitectónico MVC.
- Diseño del modelo de datos y base de datos relacional.
- Inclusión del enfoque de testing.
- Actualización del diagrama de clases UML.
- Comparación con versiones anteriores.
- Rúbricas de evaluación para profesorado, alumnado y autoevaluación.

---

## 💻 Lenguaje de programación

Se ha seleccionado **Python con Flask** como lenguaje y framework backend por las siguientes razones:

- Facilidad de aprendizaje y sintaxis limpia.
- Ligereza para proyectos educativos.
- Buena documentación y soporte para REST APIs.
- Compatible con ORM como SQLAlchemy.
- Uso extendido en contextos educativos y prototipos rápidos.

---

## 🏛️ Arquitectura propuesta: MVC

Se adopta el patrón **Modelo-Vista-Controlador (MVC)** para estructurar el proyecto:

- **Modelo**: entidades como Alumno, Horario, Aula, Auxiliar.
- **Vista**: interfaz web o aplicación para mostrar ubicación y asignaciones.
- **Controlador**: gestiona entradas del usuario, peticiones y respuestas.

Ventajas:

- Favorece la reutilización y el mantenimiento.
- Facilita el testing y el desarrollo por capas.
- Escalable a futuro si se necesita incorporar microservicios.

---

## 🧭 Diagrama de clases UML
![image](https://hackmd.io/_uploads/H1GZp-PHge.png)

## 🧭 Diagrama de casos de uso
![UseCase_LomoAccesible](https://hackmd.io/_uploads/S1wATWvBel.png)

## 🧭 Mockups con Figma
![image](https://hackmd.io/_uploads/B1BSRbDSgg.png)


🗃️ Esquema de base de datos (SQL)
![ERD_LomoAccesible](https://hackmd.io/_uploads/r1oLT-PHlg.png)

CREATE TABLE alumnos (
    id INTEGER PRIMARY KEY,
    nombre TEXT,
    nivel TEXT,
    movilidadReducida BOOLEAN
);

CREATE TABLE aulas (
    id INTEGER PRIMARY KEY,
    nombre TEXT,
    ubicacion TEXT
);

CREATE TABLE auxiliares (
    id INTEGER PRIMARY KEY,
    nombre TEXT,
    turno TEXT,
    disponible BOOLEAN
);

CREATE TABLE horarios (
    id INTEGER PRIMARY KEY,
    alumno_id INTEGER,
    aula_id INTEGER,
    dia TEXT,
    hora TEXT,
    FOREIGN KEY (alumno_id) REFERENCES alumnos(id),
    FOREIGN KEY (aula_id) REFERENCES aulas(id)
);

CREATE TABLE notificaciones (
    id INTEGER PRIMARY KEY,
    auxiliar_id INTEGER,
    mensaje TEXT,
    timestamp DATETIME,
    FOREIGN KEY (auxiliar_id) REFERENCES auxiliares(id)
);
🧪 Enfoque de pruebas
Se planifica la integración de distintos niveles de pruebas:

🔹 Pruebas unitarias
Validan métodos como getUbicacionActual() o esDisponible().

🔹 Pruebas de integración
Comprueban que los módulos interactúan correctamente (ej. horario + aula).

🔹 Pruebas funcionales
Simulan el uso completo desde la localización del alumno hasta la notificación al auxiliar.

🔹 Herramientas sugeridas:
unittest, pytest, Postman, Selenium (para pruebas funcionales web).
