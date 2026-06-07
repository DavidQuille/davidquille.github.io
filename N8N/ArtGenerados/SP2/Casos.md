# Reporte de Scripts de Prueba Automatizados (S1)
> Generado el: 2026-02-27

## ID: CP-HU-34-R1
**Título:** Registro exitoso de Datos Básicos del Tutor
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Daniela Castro' en el campo 'Nombre Completo'.
 3. Ingresar '593991234567' en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema redirige al Paso 2.
 - Se visualiza paso '2 Disponibilidad' resaltado en la barra superior.
 - Se visualiza el título 'Define tu Horario'.
 - Se visualiza el subtítulo 'Selecciona los bloques horarios en los que puedes dar clases'.
 - Se visualiza una cuadrícula con encabezados ('Lun' a 'Dom', '7:00' a '20:00').
 - Se visualiza el botón 'Siguiente Perfil Profesional'.

---

## ID: CP-HU-34-R2
**Título:** Validación de campos obligatorios vacíos al registrar Datos Básicos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Dejar el campo 'Nombre Completo' vacío.
 3. Dejar el campo 'Número de WhatsApp' vacío.
 4. Dejar el dropdown 'Facultad' sin seleccionar.
 5. Dejar el dropdown 'Semestre Actual' sin seleccionar.
 6. Dejar el campo 'Biografía Corta' vacío.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema permanece en la pantalla "Completa tu Perfil".
 - Se muestra el mensaje de error exacto 'El nombre es obligatorio' en rojo debajo de 'Nombre Completo'.
 - Se muestra el mensaje de error exacto 'El número de WhatsApp es obligatorio' en rojo debajo de 'Número de WhatsApp'.
 - Se muestra el mensaje de error exacto 'Selecciona tu facultad' en rojo debajo del dropdown 'Facultad'.
 - Se muestra el mensaje de error exacto 'Selecciona tu semestre' en rojo debajo del dropdown 'Semestre Actual'.
 - Se muestra el mensaje de error exacto 'La biografía es obligatoria' en rojo debajo de 'Biografía Corta'.

---

## ID: CP-HU-34-R3
**Título:** Validación de 'Nombre Completo' con menos de 3 caracteres
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Jo' en el campo 'Nombre Completo'.
 3. Ingresar '593991234567' en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema permanece en la pantalla "Completa tu Perfil".
 - Se muestra el mensaje en rojo 'Mínimo 3 caracteres' debajo de 'Nombre Completo'.

---

## ID: CP-HU-34-R4
**Título:** Validación de 'Nombre Completo' con más de 60 caracteres
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Este es un nombre muy largo que definitivamente excede los sesenta caracteres para una prueba de longitud máxima' en el campo 'Nombre Completo'.
 3. Ingresar '593991234567' en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema limita el ingreso a 60 caracteres en el campo 'Nombre Completo'.
 - Se muestra el contador '60/60' debajo del campo 'Nombre Completo'.
 - No permite más digitación ni pegar texto en el campo 'Nombre Completo'.
 - El sistema permanece en la pantalla "Completa tu Perfil".

---

## ID: CP-HU-34-R5
**Título:** Validación de 'Nombre Completo' con caracteres no permitidos (números y especiales)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Intentar ingresar números o caracteres especiales (ej: 'Juan123$' o 'María@!') en el campo 'Nombre Completo'.
 3. Ingresar '593991234567' en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema bloquea el ingreso de caracteres no permitidos (números y especiales) en el campo 'Nombre Completo'.
 - Solo aparecen letras y espacios en la pantalla para el campo 'Nombre Completo'.
 - El sistema permanece en la pantalla "Completa tu Perfil".

---

## ID: CP-HU-34-R6
**Título:** Validación de 'Número de WhatsApp' con menos de 10 dígitos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Daniela Castro' en el campo 'Nombre Completo'.
 3. Ingresar '593991234' (un número con menos de 10 dígitos) en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema permanece en la pantalla "Completa tu Perfil".
 - Se muestra el mensaje en rojo 'Ingresa un número válido (10-13 dígitos)' debajo del campo 'Número de WhatsApp'.

---

## ID: CP-HU-34-R7
**Título:** Validación de 'Número de WhatsApp' con más de 13 dígitos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Daniela Castro' en el campo 'Nombre Completo'.
 3. Ingresar '59399123456789' (un número con más de 13 dígitos) en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema permanece en la pantalla "Completa tu Perfil".
 - Se muestra el mensaje en rojo 'Ingresa un número válido (10-13 dígitos)' debajo del campo 'Número de WhatsApp'.

---

## ID: CP-HU-34-R8
**Título:** Validación de 'Número de WhatsApp' con caracteres no numéricos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Daniela Castro' en el campo 'Nombre Completo'.
 3. Intentar ingresar letras o caracteres especiales (ej: '593abcd123' o '593-99123') en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema bloquea el ingreso de letras y caracteres especiales en el campo 'Número de WhatsApp'.
 - Solo aparecen números en la pantalla para el campo 'Número de WhatsApp'.
 - El sistema permanece en la pantalla "Completa tu Perfil".

---

## ID: CP-HU-34-R9
**Título:** Validación de 'Biografía Corta' con menos de 20 caracteres
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Daniela Castro' en el campo 'Nombre Completo'.
 3. Ingresar '593991234567' en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Soy un tutor nuevo.' (un texto con menos de 20 caracteres) en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema permanece en la pantalla "Completa tu Perfil".
 - Se muestra el mensaje en rojo 'Mínimo 20 caracteres' debajo de 'Biografía Corta'.

---

## ID: CP-HU-34-R10
**Título:** Validación de 'Biografía Corta' con más de 300 caracteres
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en la interfaz 'Completa tu Perfil'.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la interfaz "Completa tu Perfil".
 2. Ingresar 'Daniela Castro' en el campo 'Nombre Completo'.
 3. Ingresar '593991234567' en el campo 'Número de WhatsApp'.
 4. Seleccionar 'FIS - Sistemas' del dropdown 'Facultad'.
 5. Seleccionar '4° Semestre' del dropdown 'Semestre Actual'.
 6. Ingresar 'Este es un texto de biografía muy extenso diseñado específicamente para superar el límite de trescientos caracteres y comprobar que el sistema bloquea correctamente cualquier intento de ingreso adicional una vez alcanzado el tope máximo permitido por el contador. Este texto debe exceder los 300 caracteres para verificar el comportamiento de bloqueo y la visualización del contador de caracteres.' en el campo 'Biografía Corta'.
 7. Hacer clic en el botón 'Siguiente Disponibilidad'.

**Expected Results:**
 - El sistema limita el ingreso a 300 caracteres en el campo 'Biografía Corta'.
 - Se muestra el contador '300/300' debajo del campo 'Biografía Corta'.
 - No permite más digitación ni pegar texto en el campo 'Biografía Corta'.
 - El sistema permanece en la pantalla "Completa tu Perfil".

---

## ID: CP-HU-41-R1
**Título:** Verificar bloqueo de navegación al intentar avanzar sin seleccionar horarios
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El tutor ha iniciado sesión y se encuentra en la interfaz "Define tu Horario" (Paso 2 del proceso de registro).

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz "Define tu Horario" (Paso 2).
 3. Asegurarse de que no haya ningún bloque de horario seleccionado en la cuadrícula.
 4. Hacer clic en el botón 'Siguiente Perfil Profesional'.

**Expected Results:**
 - El sistema bloquea la navegación.
 - Se muestra el texto rojo 'Selecciona al menos un horario disponible' encima de la cuadrícula.

---

## ID: CP-HU-41-R2
**Título:** Verificar la selección visual y actualización del contador al hacer clic en un bloque horario
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El tutor ha iniciado sesión y se encuentra en la interfaz "Define tu Horario" (Paso 2 del proceso de registro).

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz "Define tu Horario" (Paso 2).
 3. Hacer clic en el bloque de horario 'Lun a 09:00' en la cuadrícula.

**Expected Results:**
 - El bloque horario 'Lun a 09:00' cambia visualmente de color blanco a azul oscuro.
 - Se muestra un ícono '✓' blanco en el centro del bloque seleccionado.
 - Aparece el texto verde centrado sobre la cuadrícula: '✓ 1 horario seleccionado'.

---

## ID: CP-HU-41-R3
**Título:** Verificar avance al Paso 3 'Perfil Profesional' con al menos un horario seleccionado
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El tutor ha iniciado sesión y se encuentra en la interfaz "Define tu Horario" (Paso 2 del proceso de registro).

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz "Define tu Horario" (Paso 2).
 3. Hacer clic en el bloque de horario 'Mar a las 10:00' en la cuadrícula para seleccionarlo.
 4. Verificar que se muestra el texto verde '✓ 1 horario seleccionado'.
 5. Hacer clic en el botón 'Siguiente Perfil Profesional'.

**Expected Results:**
 - El sistema redirige a la pantalla del Paso 3.
 - Se visualiza el paso '3 Perfil Profesional' resaltado.
 - Se muestra el título 'Detalles Profesionales'.
 - Se muestra el subtítulo 'Añade tu experiencia y materias para destacar'.
 - Se visualiza el botón 'Finalizar Registro'.

---

## ID: CP-HU-41-R4
**Título:** Verificar la deselección de un bloque horario y la actualización del contador
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El tutor ha iniciado sesión y se encuentra en la interfaz "Define tu Horario" (Paso 2 del proceso de registro), con al menos dos bloques de horario seleccionados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz "Define tu Horario" (Paso 2).
 3. Seleccionar los bloques de horario 'Mié de 11:00' y 'Mié de 12:00' en la cuadrícula.
 4. Verificar que se muestra el texto verde '✓ 2 horarios seleccionados'.
 5. Hacer clic nuevamente en el bloque horario 'Mié de 11:00' para deseleccionarlo.

**Expected Results:**
 - El bloque horario 'Mié de 11:00' vuelve a ser de color blanco.
 - El ícono '✓' blanco desaparece del bloque deseleccionado.
 - El contador superior verde disminuye su número en tiempo real, mostrando '✓ 1 horario seleccionado'.

---

## ID: CP-HU-41-ADD-01
**Título:** Verificar la navegabilidad hacia atrás al Paso 1 'Datos Básicos'
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** El tutor ha iniciado sesión y se encuentra en la interfaz "Define tu Horario" (Paso 2 del proceso de registro).

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz "Define tu Horario" (Paso 2).
 3. Hacer clic en el botón inferior izquierdo '← Atrás Datos Básicos'.

**Expected Results:**
 - El sistema redirige a la pantalla del Paso 1 'Datos Básicos'.
 - Toda la información previamente ingresada por el usuario en los campos del Paso 1 se conserva intacta.

---

---

## ID: CP-HU-42-R1
**Título:** Finalización Exitosa del Registro de Perfil de Tutor
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la interfaz de "Detalles Profesionales" (Paso 3 del wizard), con todos los campos obligatorios del perfil debidamente llenados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz de "Detalles Profesionales" (Paso 3 del wizard).
 3. Asegurarse de que todos los campos obligatorios del perfil (ej. Nombre Completo, Biografía Corta, Número WhatsApp) estén debidamente llenados.
 4. (Opcional) Dejar vacíos los campos de "Nueva Experiencia" o "Materias", si son considerados opcionales.
 5. Hacer clic en el botón 'Finalizar Registro'.

**Expected Results:**
 - El sistema finaliza el proceso de registro sin arrojar alertas.
 - El sistema redirige a una pantalla posterior o dashboard (dependiendo del flujo post-registro).
 - Se muestra una pantalla con el mensaje "¡Perfil creado! Ahora puedes publicar tus ofertas de tutorías."

## ID: CP-HU-42-R2
**Título:** Ignorar Acción de 'Guardar' al Dejar Campos de Experiencia Vacíos en Modal
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la interfaz de "Detalles Profesionales".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz de "Detalles Profesionales".
 3. Hacer clic en el botón '+ Añadir Experiencia' para abrir el modal 'Nueva Experiencia'.
 4. Dejar todos los campos del modal 'Nueva Experiencia' (ej. Puesto, Institución, Fechas) vacíos.
 5. Hacer clic en el botón 'Guardar' dentro del modal 'Nueva Experiencia'.

**Expected Results:**
 - La acción de guardar se ignora silenciosamente.
 - No aparece ningún mensaje de error.
 - El modal 'Nueva Experiencia' permanece en pantalla.

## ID: CP-HU-42-R3
**Título:** Validar y Mantener Formato de Fecha MM/AAAA en Campos de Experiencia
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la interfaz de "Detalles Profesionales", con el modal 'Nueva Experiencia' abierto.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz de "Detalles Profesionales".
 3. Abrir el modal 'Nueva Experiencia' (haciendo clic en '+ Añadir Experiencia' si no está abierto).
 4. Ingresar la fecha '03/2024' en el campo 'Fecha Inicio'.
 5. Mover el foco al campo 'Fecha Fin'.

**Expected Results:**
 - El sistema valida y mantiene el formato de la fecha.
 - El campo 'Fecha Inicio' muestra la fecha digitada con el slash incluido, ej: '03/2024'.

## ID: CP-HU-42-R4
**Título:** Bloquear Ingreso de Caracteres No-Numéricos en Campos de Fecha
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la interfaz de "Detalles Profesionales", con el modal 'Nueva Experiencia' abierto.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz de "Detalles Profesionales".
 3. Abrir el modal 'Nueva Experiencia' (haciendo clic en '+ Añadir Experiencia' si no está abierto).
 4. Intentar ingresar los caracteres 'Hola' en el campo 'Fecha Inicio'.
 5. Intentar ingresar 'Presentes' (con 's' al final) en el campo 'Fecha Fin'.
 6. Intentar ingresar '12-2024' en el campo 'Fecha Fin'.

**Expected Results:**
 - El sistema bloquea el ingreso de caracteres no-numéricos y signos (salvo '/').
 - Las letras y signos no se muestran al teclear en el campo 'Fecha Inicio'.
 - En el campo 'Fecha Fin', solo se permite la palabra exacta 'Presente', y no permite 'Presentes'.
 - El campo 'Fecha Fin' no permite el ingreso de '-'.

## ID: CP-HU-42-R5
**Título:** Mostrar Error por Exceso de Caracteres en Campos de Fecha (Máximo 7)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la interfaz de "Detalles Profesionales", con el modal 'Nueva Experiencia' abierto.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz de "Detalles Profesionales".
 3. Abrir el modal 'Nueva Experiencia' (haciendo clic en '+ Añadir Experiencia' si no está abierto).
 4. Ingresar la fecha '12/20255' en el campo 'Fecha Inicio'.
 5. Mover el foco al campo 'Fecha Fin' o intentar continuar.

**Expected Results:**
 - El sistema detecta que la fecha excede los 7 caracteres del formato MM/AAAA.
 - Se muestra el mensaje de error en rojo 'Máximo 7 caracteres' debajo del campo de fecha.

## ID: CP-HU-42-R6
**Título:** Añadir Materia como Etiqueta ('Pill')
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la interfaz de "Detalles Profesionales", en la sección para añadir materias.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz de "Detalles Profesionales".
 3. Localizar la sección para añadir materias.
 4. Ingresar 'Cálculo' en el campo de texto 'Escribe una Materia(Ej. Cálculo, Física...)'.
 5. Hacer clic en el botón '+ Agregar'.

**Expected Results:**
 - El campo de texto 'Escribe una Materia(Ej. Cálculo, Física...)' se limpia.
 - Aparece un elemento visual (etiqueta o 'pill') de color celeste claro con el texto 'Cálculo'.
 - La etiqueta incluye una 'x' a la derecha que permite eliminar la materia.

## ID: CP-HU-42-R7
**Título:** Navegación hacia Atrás del Paso 3 ('Detalles Profesionales') al Paso 2 ('Disponibilidad')
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la interfaz de "Detalles Profesionales" (Paso 3 del wizard), con bloques horarios seleccionados previamente en el Paso 2.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la interfaz de "Detalles Profesionales" (Paso 3 del wizard).
 3. Asegurarse de que se han seleccionado previamente bloques horarios en la pantalla "Disponibilidad" (Paso 2).
 4. Hacer clic en el botón inferior izquierdo de '← Atrás Disponibilidad' o en el paso '2 Disponibilidad' del menú superior.

**Expected Results:**
 - El sistema redirige a la pantalla del Paso 2 ('Disponibilidad').
 - Todos los bloques horarios previamente seleccionados en la cuadrícula de la pantalla "Disponibilidad" se conservan intactos.

---

## ID: CP-HU-07-R1
**Título:** Verificar la visualización correcta de la disponibilidad registrada del tutor en modo solo lectura.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El tutor ha iniciado sesión con credenciales válidas y tiene disponibilidad horaria registrada previamente en el sistema.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección 'Gestionar Disponibilidad' (por ejemplo, haciendo clic en el enlace o menú correspondiente desde el Dashboard Tutor).

**Expected Results:**
 - La pantalla 'Gestionar Disponibilidad' carga correctamente.
 - **VALIDACIÓN VISUAL:** En la cabecera, se visualiza el texto 'Volver al Panel' a la izquierda y el logo 'Poli Tutorías' a la derecha.
 - El título 'Gestionar Disponibilidad' es visible.
 - La descripción 'Haz clic en los horarios que tienes disponibles para ofrecer tutorías.' es visible.
 - La sub-descripción 'Tu horario se mostrará en la zona horaria local (GMT-5).' es visible.
 - Se muestra el contador '✓ 4 horarios seleccionados' en color verde.
 - La cuadrícula de horarios presenta las columnas 'HORA', 'Lun', 'Mar', 'Mié', 'Jue', 'Vie', 'Sáb', 'Dom' y filas desde las 7:00 hasta las 20:00.
 - Los bloques 'Lun 12:00', 'Mar 12:00', 'Lun 19:00' y 'Mar 19:00' están resaltados con un checkmark blanco sobre fondo oscuro, indicando su selección.
 - Los botones 'Cancelar' y 'Guardar Cambios' están visibles pero deshabilitados (no clickeables).
 - No se permite la interacción (selección/deselección) de los horarios de la cuadrícula, confirmando el modo de solo lectura.

---

## ID: CP-HU-07-R2
**Título:** Verificar la navegación correcta al Dashboard Tutor al hacer clic en el enlace 'Volver al Panel'.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El tutor ha iniciado sesión con credenciales válidas y se encuentra actualmente en la pantalla 'Gestionar Disponibilidad'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección 'Gestionar Disponibilidad' (por ejemplo, haciendo clic en el enlace o menú correspondiente desde el Dashboard Tutor).
 3. Hacer clic en el enlace 'Volver al Panel' ubicado en la cabecera de la pantalla 'Gestionar Disponibilidad'.

**Expected Results:**
 - El sistema redirige a la pantalla 'T. Dashboard Tutor'.
 - **VALIDACIÓN VISUAL:** La pantalla del 'T. Dashboard Tutor' (hub central) se carga completamente, mostrando sus elementos característicos.

---

## ID: CP-HU-32-R1
**Título:** Verificar la visualización de los detalles de una oferta al hacer clic en su tarjeta.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'E. Home Estudiante' (sección de búsqueda de tutorías) con ofertas visibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla principal de "E. Home Estudiante".
 3. Localizar una tarjeta de oferta (ej: la oferta de "Cálculo Vectorial").
 4. Hacer clic en la tarjeta de oferta "Cálculo Vectorial".

**Expected Results:**
 - El sistema carga la información detallada de la oferta.
 - En la cabecera, se visualiza el botón 'Volver' a la izquierda y el logo 'PoliTutorias' a la derecha.
 - La sección principal muestra el icono de libro junto al título de la materia 'Cálculo Vectorial'.
 - Se muestra la modalidad 'Virtual y Presencial'.
 - Se visualiza un párrafo descriptivo de la clase.
 - Se muestra el título 'Categorías' con los tags 'Matemática' y 'Formación Básica'.
 - Se visualiza el título 'Disponibilidad Semanal' listando Lunes de 14:00 a 15:00, Miércoles de 14:00 a 15:00 y Viernes de 09:00 a 10:00.
 - En el panel lateral, se visualiza el 'Precio por hora' de $10.
 - La sección "Sobre el Tutor" NO se muestra.
 - La sección "Experiencia" NO se muestra.
 - La sección "Contactar por WhatsApp" NO se muestra.

## ID: CP-HU-32-R2
**Título:** Verificar el regreso a la lista principal de ofertas desde la pantalla de detalles.
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de "Detalles de la Oferta" para una tutoría.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla principal de "E. Home Estudiante".
 3. Hacer clic en una tarjeta de oferta (ej: la oferta de "Cálculo Vectorial") para visualizar sus detalles.
 4. Hacer clic en el botón 'Volver' ubicado en la cabecera superior izquierda.

**Expected Results:**
 - El sistema redirige a la pantalla principal de listado de ofertas ('E. Home Estudiante').
 - Se visualiza el listado de tarjetas de oferta.

---

## ID: CP-HU-05-R1
**Título:** Visualización detallada del perfil del tutor en la pantalla de oferta
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y existe al menos una oferta de tutoría publicada.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla principal 'Inicio' o donde se listan las ofertas de tutoría.
 3. Seleccionar y hacer clic en una tarjeta de oferta de tutoría para acceder a la pantalla de 'Detalle de la Oferta'.
 4. Observar las secciones de información del tutor presentadas en la pantalla.

**Expected Results:**
 - Se carga la pantalla de 'Detalle de la Oferta'.
 - Se visualizan claramente las secciones 'Sobre el Tutor' y 'Experiencia'.
 - En la sección 'Sobre el Tutor', se muestra:
     - Una imagen de perfil del tutor.
     - El nombre del tutor (ej: 'Juan Pérez').
     - La información académica del tutor (ej: 'FIM - Mecánica ☁️ 9° Semestre').
     - El rating del tutor (ej: '4.8 (15 reseñas)').
     - Una descripción bibliográfica del tutor (ej: 'Soy un apasionado por la mecánica y las matemáticas aplicadas...').
     - Las materias que domina el tutor, listadas como tags (ej: 'Cálculo Vectorial', 'Física I', 'Estática', 'Dinámica', 'Termodinámica').
 - En la sección 'Experiencia', se muestran:
     - Entradas de historial con el Rol, Institución/Lugar y Fechas (ej: 'Ayudante de Cátedra - Estática, EPN, Facultad de Mecánica, 2024 — Presente').
     - Entradas de historial adicionales (ej: 'Tutor Particular - Cálculo y Física, Independiente, 2023 — Presente').
 - No se visualizan detalles específicos de la oferta (ej: precio, modalidad, indicaciones de la reunión) ni opciones directas para contactar por WhatsApp en esta vista del perfil del tutor, solo su información personal y académica.

---

## ID: CP-HU-27-R1
**Título:** Filtrar ofertas por precio con rango con coincidencias
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante está logueado y se encuentra en la interfaz "Encuentra tu Tutoría" con ofertas disponibles, incluyendo algunas en el rango de $5.00 a $20.00.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Localizar el slider de "Precio".
 4. Ajustar el slider de "Precio" para seleccionar el rango de '$5.00' a '$20.00' y liberar el control para aplicar el filtro.

**Expected Results:**
 - El listado de ofertas se actualiza.
 - **VALIDACIÓN VISUAL:** El listado se actualiza mostrando solo las ofertas que están dentro del rango de precio seleccionado y omitiendo elementos fuera del rango.
 - El slider refleja los valores de '$5.00' a '$20.00'.
 - No se muestra ningún mensaje de error o indicación de falta de resultados.

---

## ID: CP-HU-27-R2
**Título:** Filtrar ofertas por precio con rango sin coincidencias
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante está logueado y se encuentra en la interfaz "Encuentra tu Tutoría" con ofertas disponibles, pero ninguna de ellas se encuentra dentro del rango de $1 a $4.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Localizar el slider de "Precio".
 4. Ajustar el slider de "Precio" para seleccionar el rango de '$1' a '$4' y liberar el control para aplicar el filtro.

**Expected Results:**
 - La lista de ofertas se vacía.
 - **VALIDACIÓN VISUAL:** La lista de ofertas se vacía.
 - Se muestra el mensaje exacto: 'No se encontraron ofertas. Intenta ajustar tus filtros de búsqueda.'.
 - El slider mantiene los valores de '$1' a '$4' seleccionados.

---

## ID: CP-HU-26-R1
**Título:** Filtrar ofertas por modalidad 'Todas'
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la interfaz de "Encuentra tu Tutoría" con ofertas disponibles de distintas modalidades.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Hacer clic en el botón filtro 'Todas' en la sección 'Modalidad'.

**Expected Results:**
 - El listado de ofertas se actualiza.
 - Se muestran todas las ofertas sin restricción de modalidad.
 - El botón 'Todas' aparece visualmente resaltado.

## ID: CP-HU-26-R2
**Título:** Filtrar ofertas por modalidad 'Presencial'
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la interfaz de "Encuentra tu Tutoría" con ofertas disponibles de distintas modalidades.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Hacer clic en el botón filtro 'Presencial' en la sección 'Modalidad'.

**Expected Results:**
 - El listado de ofertas se actualiza.
 - Se muestran las ofertas que tienen las modalidades 'Presencial' y 'Ambos'.
 - Se excluyen las ofertas únicamente 'Virtual'.

## ID: CP-HU-26-R3
**Título:** Filtrar ofertas por modalidad 'Virtual'
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la interfaz de "Encuentra tu Tutoría" con ofertas disponibles de distintas modalidades.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Hacer clic en el botón filtro 'Virtual' en la sección 'Modalidad'.

**Expected Results:**
 - El listado de ofertas se actualiza.
 - Se muestran las ofertas que tienen las modalidades 'Virtual' y 'Ambos'.
 - Se excluyen las ofertas únicamente 'Presencial'.

## ID: CP-HU-26-R4
**Título:** Filtrar ofertas por modalidad 'Ambos'
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la interfaz de "Encuentra tu Tutoría" con ofertas disponibles con modalidad 'Ambos'.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría'.
 3. Hacer clic en el botón filtro 'Ambos' en la sección 'Modalidad'.

**Expected Results:**
 - El listado de ofertas se actualiza.
 - Se muestran únicamente las ofertas que tienen la modalidad 'Ambos'.

---

## ID: CP-HU-16-R1
**Título:** Visualización inicial de ofertas sin filtro de día aplicado
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Estudiante logueado y en la interfaz "Encuentra tu Tutoría".

**Steps:**
 1. Iniciar sesión en el sistema como Estudiante.
 2. Navegar a la interfaz de "Encuentra tu Tutoría".
 3. Asegurarse de que ningún día de la semana se encuentre seleccionado en la sección "Disponibilidad".

**Expected Results:**
 - El sistema carga la interfaz "Encuentra tu Tutoría".
 - Se muestran todas las ofertas de la base de datos sin restricciones de día, tal como se define en el criterio "Visualización Inicial sin Filtro".

---

## ID: CP-HU-16-R2
**Título:** Filtrar ofertas exitosamente por un día de la semana con coincidencias
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Estudiante logueado y en la interfaz "Encuentra tu Tutoría". Existen ofertas de tutoría disponibles para el día 'Mar'.

**Steps:**
 1. Iniciar sesión en el sistema como Estudiante.
 2. Navegar a la interfaz de "Encuentra tu Tutoría".
 3. Hacer clic en el botón 'Mar' en la sección "Disponibilidad".

**Expected Results:**
 - El botón 'Mar' aparece resaltado.
 - La lista de ofertas se filtra mostrando únicamente las que tienen disponibilidad el día 'Mar', tal como se define en el criterio "Filtrado Exitoso por Día".

---

## ID: CP-HU-16-R3
**Título:** Filtrar ofertas por un día sin coincidencias y mostrar mensaje
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Estudiante logueado y en la interfaz "Encuentra tu Tutoría". NO existen ofertas de tutoría disponibles para el día 'Dom'.

**Steps:**
 1. Iniciar sesión en el sistema como Estudiante.
 2. Navegar a la interfaz de "Encuentra tu Tutoría".
 3. Hacer clic en el botón 'Dom' en la sección "Disponibilidad".

**Expected Results:**
 - La lista de ofertas se vacía.
 - Se muestra el mensaje "No se encontraron ofertas. Intenta ajustar tus filtros de búsqueda", tal como se define en el criterio "Sin Ofertas para el Día Seleccionado".

---