# App de Citas Médicas

## 1. Descripción General

El sistema es una aplicación móvil/web para que los pacientes puedan gestionar sus citas médicas con diferentes especialidades.

- El paciente debe autenticarse con número de identificación y clave, o bien registrarse si no tiene cuenta.
- Una vez dentro, podrá:
  - Solicitar citas médicas en un rango horario (7:00 am a 8:00 pm).
  - Escoger entre mínimo 5 especialidades (ej: Medicina General, Pediatría, Cardiología, Dermatología, Odontología).
  - Consultar, cancelar (con justificación) o reprogramar citas.
  - Recibir notificación por correo con la información de la cita.

## 2. Requerimientos

### 2.1 Requerimientos Funcionales

- **Autenticación de paciente**
  - RF1: El paciente debe iniciar sesión con cédula y clave.
  - RF2: Si no tiene cuenta, debe registrarse proporcionando: Nombre, apellido, fecha de nacimiento, barrio, teléfono, número de identificación, clave.
- **Gestión de citas**
  - RF3: El sistema debe permitir agendar citas de 40 minutos.
  - RF4: Las citas solo podrán reservarse en el horario de 7:00 am a 8:00 pm.
  - RF5: El paciente puede solicitar varias citas, pero no repetir la misma especialidad.
  - RF6: El paciente puede cancelar una cita, proporcionando una justificación.
  - RF7: El paciente puede reprogramar una cita si no puede asistir.
  - RF8: El sistema debe enviar un correo al paciente con la información de la cita programada, reprogramada o cancelada.
- **Especialidades**
  - RF9: El sistema debe manejar mínimo 5 especialidades con médicos asignados.

### 2.2 Requerimientos No Funcionales

- RNF1: La app debe estar disponible 24/7.
- RNF2: La interfaz debe ser intuitiva y fácil de usar.
- RNF3: El sistema debe garantizar la seguridad de datos personales mediante cifrado de contraseñas.
- RNF4: El sistema debe ser escalable para soportar múltiples pacientes y citas simultáneamente.
- RNF5: El tiempo de respuesta del sistema no debe superar los 3 segundos en operaciones críticas.
- RNF6: El sistema debe enviar confirmaciones y notificaciones en menos de 1 minuto tras la acción del usuario.

## 3. Entradas y Salidas

**Entradas:**
- Datos de registro (nombre, apellido, fecha de nacimiento, barrio, teléfono, número de identificación, clave).
- Credenciales de acceso (cédula y clave).
- Selección de especialidad, fecha y hora para la cita.
- Justificación en caso de cancelación.
- Nueva fecha y hora en caso de reprogramación.

**Salidas:**
- Mensajes de validación (error en login, registro exitoso, horario no disponible, etc.).
- Confirmación de cita.
- Correo electrónico con información de la cita.
- Actualización en el perfil del paciente sobre sus citas.

## 4. Diagrama de Clases (UML)

A continuación se presenta el diagrama de clases del sistema (unificado):

![Diagrama de Clases](diagrama_clases.png)

**Clases principales:**
- **Sistema**: validateLogin(), registerPatient(), scheduleAppointment(), sendNotification()
- **Paciente**: patientId, name, surname, birthDate, neighborhood, phone, idNumber, password; register(), authenticate(), requestAppointment(), cancelAppointment(), rescheduleAppointment()
- **Cita**: appointmentId, date, time, specialty, state, justification; assign(), cancel(), reschedule()
- **Especialidad**: specialtyId, specialtyName; listDoctors()
- **Medico**: doctorId, name, surname, specialty; assignAppointment()
- **Notificacion**: notificationId, sendDate, destinationEmail, message; sendEmail()

## 5. Diagramas Adicionales

- **Diagrama de Casos de Uso:** Registrarse, iniciar sesión, solicitar cita, cancelar cita, reprogramar, recibir notificación.
- **Diagrama de Secuencia:** Flujo desde que el paciente solicita una cita hasta que recibe el correo.

---

**Nota:** El diagrama de clases mostrado integra todos los componentes descritos en los requerimientos y casos de uso del sistema, facilitando la comprensión y desarrollo de la aplicación en tu repositorio.