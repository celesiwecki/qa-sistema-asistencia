# Proyecto de Testing QA: Sistema de Gestión de Asistencias

Este proyecto documenta el plan de pruebas y los escenarios de QA para el **Sistema de Gestión de Asistencias**, enfocado en la validación de módulos críticos, gestión de usuarios y control de accesos.

---

## 🎯 Objetivo
Asegurar la integridad, funcionalidad y seguridad de los módulos de autenticación y gestión de registros, garantizando una experiencia de usuario sin errores críticos.

---

## 🧪 Casos de Prueba (Test Cases)

| ID | Módulo | Descripción | Resultado Esperado |
| :--- | :--- | :--- | :--- |
| **TC-01** | Login | Autenticación con datos válidos | Acceso exitoso al panel principal |
| **TC-02** | Login | Autenticación con contraseña errónea | Mensaje de error: "Credenciales inválidas" |
| **TC-03** | Registro | Ingreso de nuevo alumno | Datos guardados correctamente en DB |
| **TC-04** | Registro | Duplicidad de DNI | Bloqueo de registro y aviso al usuario |
| **TC-05** | Roles | Acceso de Profesor a funciones de Admin | Acceso denegado / Menú restringido |

---

## 🐞 Reporte de Bugs (Ejemplo)

**ID:** BUG-01
**Título:** Error 500 al registrar apellido con caracteres especiales.
**Módulo:** Registro de Alumnos
**Severidad:** Alta
**Pasos para reproducir:**
1. Ir al formulario de registro.
2. Ingresar "Pérez#$" en el campo Apellido.
3. Presionar "Guardar".
**Resultado actual:** Pantalla blanca de error (Crash).
**Resultado esperado:** Validación de entrada y mensaje de error amigable.

---

## 🛠️ Herramientas utilizadas
* **Metodología:** Testing Manual, Pruebas de Caja Negra.
* **Documentación:** Markdown, GitHub.
* **Base de datos:** SQLite.
---

## 🔌 Testing de APIs (Postman)

Para asegurar el correcto funcionamiento del backend del Sistema de Asistencias, se diseñó una colección de pruebas en **Postman** enfocada en validar los endpoints principales de la aplicación.

### 📌 Endpoints Principales Evaluados

| Método | Endpoint | Descripción | Estado Esperado (Código HTTP) |
| :--- | :--- | :--- | :--- |
| **POST** | `/api/alumnos` | Registrar un nuevo alumno en la base de datos | `201 Created` |
| **GET**  | `/api/alumnos` | Obtener el listado completo de alumnos | `200 OK` |
| **POST** | `/api/asistencia` | Registrar la asistencia diaria de un alumno | `201 Created` |
| **GET**  | `/api/asistencia/{id}` | Consultar el historial de asistencias por alumno | `200 OK` |

---

### 🧪 Ejemplo de Validación (Prueba en Postman)

* **Prueba de Registro Exitoso (`POST /api/alumnos`):**
  * **Body enviado (JSON):**
    ```json
    {
      "nombre": "Carlos",
      "apellido": "Gómez",
      "dni": "35444888",
      "email": "carlos.gomez@email.com"
    }
    ```
  * **Validación de Postman (Test Script):** Se comprueba mediante scripts de JavaScript integrados que el código de respuesta sea `201` y que el tiempo de respuesta de la base de datos sea menor a `500ms`.