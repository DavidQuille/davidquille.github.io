# Reporte de Scripts de Prueba Automatizados (S1)
> Generado el: 2026-03-13

## ID: CP-HU-06-R1
**Título:** Verificación de botón "Solicitar Tutoría" inactivo al no seleccionar horarios
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta de una tutoría, sin ningún horario seleccionado en "Disponibilidad Semanal".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría.
 3. Asegurarse de que ningún chip de horario esté seleccionado en la sección "Disponibilidad Semanal".
 N. Verificar el estado del botón "Solicitar Tutoría".

**Expected Results:**
 - El usuario permanece en la pantalla "E. Detalle Oferta".
 - El botón "Solicitar Tutoría" se muestra en un estado visual deshabilitado, impidiendo la interacción del usuario para abrir el modal de solicitud.

---

## ID: CP-HU-06-R2
**Título:** Verificación de alerta por solicitud previa de horario
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta, con una solicitud activa previa para el horario "Miércoles 14:00".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría.
 3. Seleccionar el chip del horario "14:00" en la fila del "Miércoles" dentro de la sección "Disponibilidad Semanal".
 N. Observar el comportamiento del sistema.

**Expected Results:**
 - El botón "Solicitar Tutoría" no se habilita.
 - Se visualiza inmediatamente una alerta inferior con el texto exacto: "Horario ya solicitado. Ya tienes una solicitud activa para Miércoles 14:00."

---

## ID: CP-HU-06-R3
**Título:** Solicitud exitosa de tutoría con una sola modalidad y mensaje lleno
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta de una tutoría con una única modalidad configurada y con horarios disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría con una única modalidad configurada.
 3. Seleccionar el horario "Lunes 9 mar · 14:00" en la sección "Disponibilidad Semanal".
 4. Hacer clic en el botón "Solicitar Tutoría".
 5. En el modal "Solicitar Tutoría", ingresar "Requiero ayuda urgente con este tema para mi examen." en el campo "Mensaje para el tutor *".
 N. Hacer clic en el botón "Enviar Solicitud".

**Expected Results:**
 - Se superpone el modal "Solicitar Tutoría" mostrando la foto y nombre del tutor, el chip de "Horarios seleccionados", el campo de texto "Mensaje para el tutor *" con el contador "0/500", el botón "Cancelar" y el botón "Enviar Solicitud". No se visualiza selector de modalidad.
 - El modal se cierra.
 - Se visualiza en la pantalla principal una notificación de éxito con el texto exacto: "¡Solicitud enviada! 1 horario propuesto. El tutor revisará tu solicitud pronto."

---

## ID: CP-HU-06-R4
**Título:** Verificación de mensaje obligatorio en solicitud de tutoría (una modalidad)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta de una tutoría con una única modalidad configurada y con horarios disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría con una única modalidad configurada.
 3. Seleccionar el horario "Lunes 9 mar · 14:00" en la sección "Disponibilidad Semanal".
 4. Hacer clic en el botón "Solicitar Tutoría".
 5. En el modal "Solicitar Tutoría", dejar el campo de texto "Mensaje para el tutor *" completamente vacío.
 N. Hacer clic en el botón "Enviar Solicitud".

**Expected Results:**
 - Se superpone el modal "Solicitar Tutoría" mostrando la foto y nombre del tutor, el chip de "Horarios seleccionados", el campo de texto "Mensaje para el tutor *" con el contador "0/500", el botón "Cancelar" y el botón "Enviar Solicitud". No se visualiza selector de modalidad.
 - El sistema impide el envío.
 - El borde del campo de texto "Mensaje para el tutor *" cambia a color rojo.
 - Justo debajo del campo de texto se muestra el mensaje de error exacto: "El mensaje es obligatorio."

---

## ID: CP-HU-06-R5
**Título:** Verificación de modalidad obligatoria en solicitud de tutoría (dual modalidad)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta de una tutoría con modalidades "Virtual/Presencial" configuradas y con horarios disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría con modalidades "Virtual/Presencial" configuradas.
 3. Seleccionar el horario "Lunes 9 mar · 14:00" en la sección "Disponibilidad Semanal".
 4. Hacer clic en el botón "Solicitar Tutoría".
 5. En el modal "Solicitar Tutoría", dejar la sección "Modalidad *" sin seleccionar.
 6. Ingresar "Necesito repasar integrales." en el campo de texto "Mensaje para el tutor *".
 N. Hacer clic en el botón "Enviar Solicitud".

**Expected Results:**
 - Se superpone el modal "Solicitar Tutoría" mostrando la información del tutor, los "Horarios seleccionados", la sección obligatoria "Modalidad *" con los botones "Virtual" y "Presencial", el campo de texto "Mensaje para el tutor *" con el contador "0/500", el botón "Cancelar" y el botón "Enviar Solicitud".
 - El sistema impide el envío.
 - Justo debajo de los botones de selección "Virtual" y "Presencial" se muestra el mensaje de error exacto en color rojo: "Selecciona la modalidad".

---

## ID: CP-HU-06-R6
**Título:** Solicitud exitosa de tutoría con dual modalidad, modalidad y mensaje llenos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta de una tutoría con modalidades "Virtual/Presencial" configuradas y con horarios disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría con modalidades "Virtual/Presencial" configuradas.
 3. Seleccionar el horario "Lunes 9 mar · 14:00" en la sección "Disponibilidad Semanal".
 4. Hacer clic en el botón "Solicitar Tutoría".
 5. En el modal "Solicitar Tutoría", seleccionar el botón "Virtual" en la sección "Modalidad *".
 6. Ingresar "Necesito repasar integrales." en el campo de texto "Mensaje para el tutor *".
 N. Hacer clic en el botón "Enviar Solicitud".

**Expected Results:**
 - Se superpone el modal "Solicitar Tutoría" mostrando la información del tutor, los "Horarios seleccionados", la sección obligatoria "Modalidad *" con los botones "Virtual" y "Presencial", el campo de texto "Mensaje para el tutor *" con el contador "0/500", el botón "Cancelar" y el botón "Enviar Solicitud".
 - El modal se cierra.
 - Se visualiza una notificación de éxito con el texto exacto: "¡Solicitud enviada! 1 horario propuesto. El tutor revisará tu solicitud pronto."

---

## ID: CP-HU-06-R7
**Título:** Verificación de mensaje obligatorio en solicitud de tutoría (dual modalidad, modalidad seleccionada)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta de una tutoría con modalidades "Virtual/Presencial" configuradas y con horarios disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría con modalidades "Virtual/Presencial" configuradas.
 3. Seleccionar el horario "Lunes 9 mar · 14:00" en la sección "Disponibilidad Semanal".
 4. Hacer clic en el botón "Solicitar Tutoría".
 5. En el modal "Solicitar Tutoría", seleccionar el botón "Presencial" en la sección "Modalidad *".
 6. Dejar el campo de texto "Mensaje para el tutor *" completamente vacío.
 N. Hacer clic en el botón "Enviar Solicitud".

**Expected Results:**
 - Se superpone el modal "Solicitar Tutoría" mostrando la información del tutor, los "Horarios seleccionados", la sección obligatoria "Modalidad *" con los botones "Virtual" y "Presencial", el campo de texto "Mensaje para el tutor *" con el contador "0/500", el botón "Cancelar" y el botón "Enviar Solicitud".
 - El sistema impide el envío.
 - El borde del campo de texto "Mensaje para el tutor *" cambia a color rojo.
 - Justo debajo del campo de texto se muestra el mensaje de error exacto: "El mensaje es obligatorio."

---

## ID: CP-HU-06-R8
**Título:** Verificación de mensajes y modalidad obligatorios en solicitud de tutoría (dual modalidad)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla de Detalle de Oferta de una tutoría con modalidades "Virtual/Presencial" configuradas y con horarios disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría con modalidades "Virtual/Presencial" configuradas.
 3. Seleccionar el horario "Lunes 9 mar · 14:00" en la sección "Disponibilidad Semanal".
 4. Hacer clic en el botón "Solicitar Tutoría".
 5. En el modal "Solicitar Tutoría", dejar la sección "Modalidad *" sin seleccionar.
 6. Dejar el campo de texto "Mensaje para el tutor *" completamente vacío.
 N. Hacer clic en el botón "Enviar Solicitud".

**Expected Results:**
 - Se superpone el modal "Solicitar Tutoría" mostrando la información del tutor, los "Horarios seleccionados", la sección obligatoria "Modalidad *" con los botones "Virtual" y "Presencial", el campo de texto "Mensaje para el tutor *" con el contador "0/500", el botón "Cancelar" y el botón "Enviar Solicitud".
 - El sistema impide el envío.
 - Debajo de los botones de selección "Virtual" y "Presencial" se muestra el mensaje de error exacto en color rojo: "Selecciona la modalidad".
 - El borde del campo de texto "Mensaje para el tutor *" cambia a color rojo.
 - Debajo del campo de texto se muestra el mensaje de error exacto: "El mensaje es obligatorio."

---

## ID: CP-HU-06-ADD01
**Título:** Verificación de bloqueo por límite máximo de caracteres en mensaje de solicitud
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en el modal "Solicitar Tutoría" (ya sea de una o dual modalidad).

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla de "Detalle de Oferta" de una tutoría.
 3. Seleccionar al menos un horario en la sección "Disponibilidad Semanal".
 4. Hacer clic en el botón "Solicitar Tutoría" para abrir el modal.
 5. En el modal "Solicitar Tutoría", ingresar "A" repetido 501 veces sin espacios en el campo de texto "Mensaje para el tutor *".
 N. Intentar ingresar un carácter adicional.

**Expected Results:**
 - El sistema bloquea el ingreso adicional de texto.
 - El contador inferior muestra exactamente "500/500".
 - No se permite sobrepasar el límite visual ni funcionalmente al teclear.

---

## ID: CP-HU-09-R1
**Título:** Visualización Inicial de Solicitudes Pendientes con Datos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y existen solicitudes de tutoría en estado "Pendiente" dirigidas a él.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción "Bandeja" en la barra de navegación superior.

**Expected Results:**
 - El sistema carga la pantalla principal de la Bandeja de Entrada.
 - Se visualiza la barra de navegación superior con los botones "Panel", "Bandeja" (activo), "Mi Agenda", el nombre de usuario y el botón "Salir".
 - Se visualiza el título "Bandeja de Entrada" y el subtítulo "Solicitudes de tutoría recibidas".
 - El indicador global de pendientes en la esquina superior derecha se muestra con un número (ej. '3 pendientes').
 - La pestaña 'Pendientes (X)' (ej. 'Pendientes (3)') se muestra activa (fondo oscuro, texto blanco).
 - Las pestañas "Expiradas (Y)" (ej. 'Expiradas (14)') y "Respondidas (Z)" se muestran inactivas.
 - Se visualizan las cabeceras de la tabla: "ESTUDIANTE", "MATERIA", "FECHA/HORA", "MENSAJE", "ESTADO".
 - Se muestra una lista de hasta 10 solicitudes pendientes en filas colapsadas (con paginación si excede).
 - Cada fila contiene: avatar/iniciales, nombre del estudiante, materia, fecha y hora, un fragmento del mensaje.
 - Cada fila muestra el tag de estado 'Pendiente' (texto naranja, fondo claro).
 - Cada fila presenta un ícono de flecha hacia abajo a la derecha.

---

## ID: CP-HU-09-R2
**Título:** Visualización Inicial de Solicitudes Pendientes sin Datos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y NO existen solicitudes de tutoría en estado "Pendiente" dirigidas a él.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción "Bandeja" en la barra de navegación superior.

**Expected Results:**
 - El sistema carga la pantalla principal de la Bandeja de Entrada.
 - Se visualiza la barra de navegación superior con los botones "Panel", "Bandeja" (activo), "Mi Agenda", el nombre de usuario y el botón "Salir".
 - Se visualiza el título "Bandeja de Entrada" y el subtítulo "Solicitudes de tutoría recibidas".
 - El indicador global de pendientes en la esquina superior derecha muestra '0 pendientes'.
 - La pestaña 'Pendientes (0)' se muestra activa (fondo oscuro, texto blanco).
 - Las cabeceras de la tabla se ocultan.
 - En el área central de la pantalla se visualiza el texto exacto: "No hay solicitudes pendientes.".

---

## ID: CP-HU-09-R3
**Título:** Visualización Inicial de Solicitudes Expiradas con Datos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y existen solicitudes de tutoría en estado "Expirada".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada" (haciendo clic en "Bandeja" en la barra superior).
 3. Hacer clic en la pestaña 'Expiradas (Y)' (ej. 'Expiradas (14)').

**Expected Results:**
 - Permanece en la pantalla "T. Bandeja de Entrada".
 - La pestaña 'Expiradas (Y)' (ej. 'Expiradas (14)') se muestra activa (fondo oscuro, texto blanco).
 - Las pestañas "Pendientes (X)" y "Respondidas (Z)" se muestran inactivas.
 - Se visualizan las cabeceras de la tabla: "ESTUDIANTE", "MATERIA", "FECHA/HORA", "MENSAJE", "ESTADO".
 - Se muestra una lista de solicitudes expiradas en filas colapsadas.
 - Cada fila contiene: avatar/iniciales, nombre del estudiante, materia, fecha y hora, un fragmento del mensaje.
 - Cada fila muestra el tag de estado 'Expirada' (texto rojo).
 - Las filas de solicitudes expiradas NO presentan ícono de flecha hacia abajo a la derecha.

---

## ID: CP-HU-09-R4
**Título:** Visualización Inicial de Solicitudes Expiradas sin Datos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y NO existen solicitudes de tutoría en estado "Expirada".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada" (haciendo clic en "Bandeja" en la barra superior).
 3. Hacer clic en la pestaña 'Expiradas (0)'.

**Expected Results:**
 - Permanece en la pantalla "T. Bandeja de Entrada".
 - La pestaña 'Expiradas (0)' se muestra activa (fondo oscuro, texto blanco).
 - Las cabeceras de la tabla se ocultan.
 - En el área central de la pantalla se visualiza el texto exacto: "No hay solicitudes expiradas.".

---

## ID: CP-HU-09-R5
**Título:** Cambio de Pestaña: De Expiradas a Pendientes
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado, en la pantalla "T. Bandeja de Entrada", con la pestaña 'Expiradas' actualmente activa, y existen solicitudes "Pendiente".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada" (haciendo clic en "Bandeja" en la barra superior).
 3. Hacer clic en la pestaña 'Expiradas (Y)' (ej. 'Expiradas (14)') para activarla.
 4. Hacer clic en la pestaña 'Pendientes (X)' (ej. 'Pendientes (3)').

**Expected Results:**
 - La interfaz actualiza su vista.
 - La pestaña 'Pendientes (X)' (ej. 'Pendientes (3)') se muestra activa (fondo oscuro, texto blanco).
 - Las pestañas "Expiradas (Y)" y "Respondidas (Z)" se muestran inactivas.
 - Se visualizan las cabeceras de la tabla: "ESTUDIANTE", "MATERIA", "FECHA/HORA", "MENSAJE", "ESTADO".
 - Se muestra una lista de solicitudes en estado 'Pendiente' en filas colapsadas.
 - Cada fila contiene: avatar/iniciales, nombre del estudiante, materia, fecha y hora, un fragmento del mensaje.
 - Cada fila muestra el tag de estado 'Pendiente' (texto naranja, fondo claro).
 - Cada fila presenta un ícono de flecha hacia abajo a la derecha.

---

## ID: CP-HU-09-R6
**Título:** Desplegar una Fila de Solicitud Pendiente
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado, en la pantalla "T. Bandeja de Entrada", con la pestaña 'Pendientes' activa y al menos una solicitud "Pendiente" visible (ej. 'Valeria Sánchez').

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada" (haciendo clic en "Bandeja" en la barra superior).
 3. Asegurarse de que la pestaña 'Pendientes (X)' esté activa y que se visualicen solicitudes.
 4. Hacer clic en el ícono de flecha hacia abajo de una fila de solicitud pendiente (ej. la correspondiente a 'Valeria Sánchez').

**Expected Results:**
 - La fila de la solicitud seleccionada se expande verticalmente.
 - Debajo de la información base, aparecen los detalles adicionales: un ícono con la modalidad (ej. "Virtual") y su texto.
 - Se visualiza el precio por hora (ej. "$10/h").
 - Se visualiza un recuadro con el título "MENSAJE DEL ESTUDIANTE" que contiene el texto completo del mensaje.
 - Se visualizan los botones "Aceptar" (fondo oscuro) y "Rechazar" (fondo blanco) en la fila expandida.
 - El ícono de flecha de la fila seleccionada cambia apuntando hacia arriba.

---

## ID: CP-HU-09-R7
**Título:** Colapsar una Fila de Solicitud Pendiente Desplegada
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado, en la pantalla "T. Bandeja de Entrada", con la pestaña 'Pendientes' activa y una fila de solicitud pendiente (ej. 'Valeria Sánchez') está actualmente expandida.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada" (haciendo clic en "Bandeja" en la barra superior).
 3. Asegurarse de que la pestaña 'Pendientes (X)' esté activa.
 4. Desplegar una fila de solicitud pendiente (ej. la de 'Valeria Sánchez') haciendo clic en su ícono de flecha hacia abajo.
 5. Hacer clic en el ícono de flecha hacia arriba de la fila de la solicitud expandida (ej. la de 'Valeria Sánchez').

**Expected Results:**
 - La fila de la solicitud seleccionada se contrae.
 - Se ocultan los detalles de modalidad, precio, el mensaje completo y los botones de acción ("Aceptar", "Rechazar").
 - La fila vuelve a su estado de resumen inicial, mostrando únicamente la información básica.
 - El ícono de flecha de la fila vuelve a apuntar hacia abajo.

---

## ID: CP-HU-09-R8
**Título:** Desplegar una Fila de Solicitud Expirada
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado, en la pantalla "T. Bandeja de Entrada", con la pestaña 'Expiradas' activa y al menos una solicitud expirada visible.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada" (haciendo clic en "Bandeja" en la barra superior).
 3. Hacer clic en la pestaña 'Expiradas (Y)' (ej. 'Expiradas (14)') para activarla y visualizar solicitudes.
 4. Hacer clic en cualquier parte de una fila de solicitud expirada (ej. la fila correspondiente a 'Juan Pérez').

**Expected Results:**
 - La fila de la solicitud seleccionada se expande verticalmente.
 - Se muestran detalles adicionales: un ícono con la modalidad (ej. "Presencial") y su texto.
 - Se visualiza el precio por hora (ej. "$8/h").
 - Se visualiza un recuadro con el título "MENSAJE DEL ESTUDIANTE" conteniendo el texto completo del mensaje.
 - El ícono de flecha de la fila seleccionada apunta hacia arriba.
 - No se visualizan botones de acción ("Aceptar", "Rechazar") en la fila expandida.
 - *Observación:* Existe una aparente inconsistencia en la documentación: Los criterios de aceptación indican que las filas expiradas "NO presentan ícono de flecha hacia abajo" inicialmente, mientras que el glosario de A9 y A10 describe la funcionalidad de flechas para desplegar/colapsar. Este caso de prueba asume que la fila es expandible mediante clic en la fila, y que el ícono de flecha aparece y cambia de estado tras la expansión.

---

## ID: CP-HU-09-R9
**Título:** Colapsar una Fila de Solicitud Expirada Desplegada
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado, en la pantalla "T. Bandeja de Entrada", con la pestaña 'Expiradas' activa y una fila de solicitud expirada está actualmente expandida.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada" (haciendo clic en "Bandeja" en la barra superior).
 3. Hacer clic en la pestaña 'Expiradas (Y)' (ej. 'Expiradas (14)') para activarla y visualizar solicitudes.
 4. Desplegar una fila de solicitud expirada (ej. la de 'Juan Pérez') haciendo clic en la fila.
 5. Hacer clic en el ícono de flecha hacia arriba de la fila de la solicitud expandida (ej. la de 'Juan Pérez').

**Expected Results:**
 - La fila de la solicitud seleccionada se contrae.
 - Se ocultan los detalles de modalidad, precio y el mensaje completo.
 - La fila vuelve a su estado de resumen inicial, mostrando únicamente la información básica.
 - El ícono de flecha de la fila vuelve a apuntar hacia abajo (o desaparece si la implementación inicial no lo muestra).
 - *Observación:* Se mantiene la observación sobre la inconsistencia de la documentación respecto a la presencia de íconos de flecha en filas expiradas en su estado colapsado inicial, asumiendo aquí que el ícono es interactivo una vez la fila está desplegada.

---

## ID: CP-HU-08-R1
**Título:** Confirmar Tutoría Virtual exitosamente con enlace válido.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Virtual' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Virtual'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. En el modal "Confirmar Tutoría", ingresar "https://zoom.us/j/123456789" en el campo de texto "Enlace de la reunión *".
 6. Hacer clic en el botón "Confirmar".

**Expected Results:**
 - La ventana modal se cierra.
 - El sistema procesa la aceptación, cambiando internamente el estado a "Aceptada".
 - Se regresa a la pantalla "T. Bandeja de Entrada".
 - La solicitud recién aceptada desaparece de la lista de la pestaña "Pendientes".
 - El contador numérico de la pestaña "Pendientes" se reduce en uno.
 - El contador de la pestaña "Respondidas" se incrementa en uno.

---

## ID: CP-HU-08-R2
**Título:** Intentar confirmar Tutoría Virtual sin ingresar el enlace de reunión obligatorio.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Virtual' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Virtual'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. En el modal "Confirmar Tutoría", dejar el campo de texto "Enlace de la reunión *" completamente vacío.
 6. Hacer clic en el botón "Confirmar".

**Expected Results:**
 - El sistema impide la confirmación y el modal "Confirmar Tutoría" permanece abierto en pantalla.
 - Debajo del campo de texto de enlace, se muestra el mensaje de error exacto en rojo: "El enlace de reunión es obligatorio.".

---

## ID: CP-HU-08-R3
**Título:** Intentar confirmar Tutoría Virtual con un enlace de reunión URL inválida.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Virtual' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Virtual'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. En el modal "Confirmar Tutoría", ingresar "zoom.us/j/1234" en el campo de texto "Enlace de la reunión *".
 6. Hacer clic en el botón "Confirmar".

**Expected Results:**
 - El sistema impide la confirmación y el modal "Confirmar Tutoría" permanece abierto en pantalla.
 - Debajo del campo de texto de enlace, se muestra el mensaje de error exacto en rojo: "Ingresa una URL válida (debe comenzar con https:// o http://).".

---

## ID: CP-HU-08-R4
**Título:** Cancelar la confirmación de una Tutoría Virtual.
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Virtual' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Virtual'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. Hacer clic en el botón "Cancelar" situado en la parte inferior izquierda del modal "Confirmar Tutoría".

**Expected Results:**
 - La ventana modal "Confirmar Tutoría" se cierra inmediatamente.
 - Se descarta la información ingresada en el modal.
 - La pantalla base de "T. Bandeja de Entrada" permanece inalterada.
 - La solicitud original se mantiene en estado "Pendiente" y su fila completamente desplegada.
 - No hay alteraciones en los contadores numéricos de las pestañas.

---

## ID: CP-HU-08-R5
**Título:** Confirmar Tutoría Presencial exitosamente con lugar de encuentro válido.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Presencial' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Presencial'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. En el modal "Confirmar Tutoría", ingresar "Edificio H, Aula 205, Campus Principal" en el campo de texto "Lugar de encuentro *".
 6. Hacer clic en el botón "Confirmar".

**Expected Results:**
 - La ventana modal se cierra.
 - El sistema procesa la aceptación, cambiando internamente el estado a "Aceptada".
 - Se regresa a la pantalla "T. Bandeja de Entrada".
 - La solicitud recién aceptada desaparece de la lista de la pestaña "Pendientes".
 - El contador numérico de la pestaña "Pendientes" se reduce en uno.
 - El contador de la pestaña "Respondidas" se incrementa en uno.

---

## ID: CP-HU-08-R6
**Título:** Intentar confirmar Tutoría Presencial sin ingresar el lugar de encuentro obligatorio.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Presencial' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Presencial'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. En el modal "Confirmar Tutoría", dejar el campo de texto "Lugar de encuentro *" completamente vacío.
 6. Hacer clic en el botón "Confirmar".

**Expected Results:**
 - El sistema impide la confirmación y el modal "Confirmar Tutoría" permanece abierto en pantalla.
 - Debajo del campo de texto de lugar, se muestra el mensaje de error exacto en rojo: "El lugar de encuentro es obligatorio.".

---

## ID: CP-HU-08-R7
**Título:** Intentar confirmar Tutoría Presencial con un lugar de encuentro de menos de 10 caracteres.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Presencial' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Presencial'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. En el modal "Confirmar Tutoría", ingresar "Aula 1" en el campo de texto "Lugar de encuentro *".
 6. Hacer clic en el botón "Confirmar".

**Expected Results:**
 - El sistema impide la confirmación y el modal "Confirmar Tutoría" permanece abierto en pantalla.
 - Debajo del campo de texto de lugar, se muestra el mensaje de error exacto en rojo: "Mínimo 10 caracteres para el lugar.".

---

## ID: CP-HU-08-R8
**Título:** Cancelar la confirmación de una Tutoría Presencial.
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Presencial' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Presencial'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. Hacer clic en el botón "Cancelar" situado en la parte inferior izquierda del modal "Confirmar Tutoría".

**Expected Results:**
 - La ventana modal "Confirmar Tutoría" se cierra inmediatamente.
 - Se descarta la información ingresada en el modal.
 - La pantalla base de "T. Bandeja de Entrada" permanece inalterada.
 - La solicitud original se mantiene en estado "Pendiente" y su fila completamente desplegada.
 - No hay alteraciones en los contadores numéricos de las pestañas.

---

## ID: CP-HU-08-Extra-01
**Título:** Verificar el límite máximo de 100 caracteres en el campo "Lugar de encuentro".
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "T. Bandeja de Entrada". Una solicitud de tutoría pendiente con modalidad 'Presencial' está visible y sus detalles desplegados.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla "T. Bandeja de Entrada".
 3. Desplegar los detalles de una solicitud pendiente con modalidad 'Presencial'.
 4. Hacer clic en el botón "Aceptar" en la fila de la solicitud desplegada.
 5. En el modal "Confirmar Tutoría", intentar ingresar 101 caracteres (ej. la letra "B" repetida 101 veces sin espacios) en el campo de texto "Lugar de encuentro *".

**Expected Results:**
 - El sistema bloquea el ingreso adicional de texto después del caracter 100.
 - El campo de texto "Lugar de encuentro *" muestra exactamente 100 caracteres.
 - El contador inferior del campo "Lugar de encuentro *" muestra exactamente "100/100".
 - No se permite sobrepasar este límite visual ni funcionalmente.

---

## ID: CP-HU-23-R1
**Título:** Rechazo de solicitud de tutoría con motivo predefinido exitoso
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El Tutor se encuentra logueado y en la pantalla de Bandeja de Entrada con solicitudes pendientes.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Bandeja de Entrada'.
 3. Desplegar los detalles de una solicitud de tutoría pendiente (ej. la de "Valeria Sánchez").
 4. Hacer clic en el botón "Rechazar" (fondo blanco).
 5. Hacer clic en el radio button "Conflicto de horarios con otra tutoría".
 6. Hacer clic en el botón "Confirmar Rechazo".

**Expected Results:**
 - El modal "Rechazar solicitud de tutoría" desaparece.
 - Se visualiza una alerta inferior azul con el texto exacto: "Solicitud rechazada".
 - En la pestaña "Pendientes", la solicitud del estudiante (ej. "Valeria Sánchez") ya no aparece.
 - El contador numérico de la pestaña "Pendientes" se reduce en 1.
 - En la pestaña "Respondidas", la solicitud del estudiante (ej. "Valeria Sánchez") ahora es visible y su contador se incrementa.

## ID: CP-HU-23-R2
**Título:** Rechazo de solicitud de tutoría con motivo 'Otro' sin comentario (exitoso)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El Tutor se encuentra logueado y en la pantalla de Bandeja de Entrada con solicitudes pendientes.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Bandeja de Entrada'.
 3. Desplegar los detalles de una solicitud de tutoría pendiente (ej. la de "Valeria Sánchez").
 4. Hacer clic en el botón "Rechazar" (fondo blanco).
 5. Hacer clic en el radio button "Otro".
 6. Dejar el campo de texto "Comentario adicional (opcional)" completamente vacío.
 7. Hacer clic en el botón "Confirmar Rechazo".

**Expected Results:**
 - El modal "Rechazar solicitud de tutoría" desaparece.
 - Se visualiza una alerta inferior azul con el texto exacto: "Solicitud rechazada".
 - En la pestaña "Pendientes", la solicitud del estudiante (ej. "Valeria Sánchez") ya no aparece.
 - El contador numérico de la pestaña "Pendientes" se reduce en 1.
 - En la pestaña "Respondidas", la solicitud del estudiante (ej. "Valeria Sánchez") ahora es visible y su contador se incrementa.

## ID: CP-HU-23-R3
**Título:** Rechazo de solicitud de tutoría con motivo 'Otro' y comentario (exitoso)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El Tutor se encuentra logueado y en la pantalla de Bandeja de Entrada con solicitudes pendientes.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Bandeja de Entrada'.
 3. Desplegar los detalles de una solicitud de tutoría pendiente (ej. la de "Valeria Sánchez").
 4. Hacer clic en el botón "Rechazar" (fondo blanco).
 5. Hacer clic en el radio button "Otro".
 6. Ingresar en el campo "Comentario adicional (opcional)" el texto: "No podré atender esta semana debido a un cruce de horarios.".
 7. Hacer clic en el botón "Confirmar Rechazo".

**Expected Results:**
 - El sistema procesa el rechazo guardando el texto ingresado en el comentario.
 - El modal "Rechazar solicitud de tutoría" desaparece.
 - Se visualiza una alerta inferior azul con el texto exacto: "Solicitud rechazada".
 - En la pestaña "Pendientes", la solicitud del estudiante (ej. "Valeria Sánchez") ya no aparece.
 - El contador numérico de la pestaña "Pendientes" se reduce en 1.
 - En la pestaña "Respondidas", la solicitud del estudiante (ej. "Valeria Sánchez") ahora es visible y su contador se incrementa.

## ID: CP-HU-23-R4
**Título:** Cancelar rechazo con motivo predefinido seleccionado
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** El Tutor se encuentra logueado y en la pantalla de Bandeja de Entrada con solicitudes pendientes.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Bandeja de Entrada'.
 3. Desplegar los detalles de una solicitud de tutoría pendiente (ej. la de "Valeria Sánchez").
 4. Hacer clic en el botón "Rechazar" (fondo blanco).
 5. Hacer clic en el radio button "Imprevisto personal".
 6. Hacer clic en el botón "Cancelar" ubicado en la parte inferior izquierda del modal.

**Expected Results:**
 - El sistema interrumpe la acción de rechazo.
 - La ventana modal "Rechazar solicitud de tutoría" se cierra inmediatamente.
 - La pantalla 'T. Bandeja de Entrada (Solicitud Pendiente Desplegada)' permanece inalterada.
 - La solicitud (ej. "Valeria Sánchez") continúa visible en la pestaña "Pendientes" y su fila sigue desplegada.
 - Los contadores numéricos de las pestañas ("Pendientes", "Expiradas", "Respondidas") no sufren alteraciones.

## ID: CP-HU-23-R5
**Título:** Cancelar rechazo con motivo 'Otro' seleccionado sin comentario
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** El Tutor se encuentra logueado y en la pantalla de Bandeja de Entrada con solicitudes pendientes.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Bandeja de Entrada'.
 3. Desplegar los detalles de una solicitud de tutoría pendiente (ej. la de "Valeria Sánchez").
 4. Hacer clic en el botón "Rechazar" (fondo blanco).
 5. Hacer clic en el radio button "Otro".
 6. Dejar el campo de texto "Comentario adicional (opcional)" vacío.
 7. Hacer clic en el botón "Cancelar".

**Expected Results:**
 - El sistema interrumpe la acción de rechazo.
 - La ventana modal expandida "Rechazar solicitud de tutoría" se cierra inmediatamente.
 - La pantalla 'T. Bandeja de Entrada (Solicitud Pendiente Desplegada)' permanece inalterada.
 - La solicitud (ej. "Valeria Sánchez") continúa visible en la pestaña "Pendientes" y su fila sigue desplegada.
 - Los contadores numéricos de las pestañas no sufren alteraciones.

## ID: CP-HU-23-R6
**Título:** Cancelar rechazo con motivo 'Otro' seleccionado con comentario
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** El Tutor se encuentra logueado y en la pantalla de Bandeja de Entrada con solicitudes pendientes.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Bandeja de Entrada'.
 3. Desplegar los detalles de una solicitud de tutoría pendiente (ej. la de "Valeria Sánchez").
 4. Hacer clic en el botón "Rechazar" (fondo blanco).
 5. Hacer clic en el radio button "Otro".
 6. Ingresar en el campo de texto "Comentario adicional (opcional)" el texto: "Revisar agenda".
 7. Hacer clic en el botón "Cancelar".

**Expected Results:**
 - El sistema interrumpe la acción de rechazo y descarta el texto escrito en el comentario.
 - La ventana modal "Rechazar solicitud de tutoría" se cierra inmediatamente.
 - La pantalla 'T. Bandeja de Entrada (Solicitud Pendiente Desplegada)' permanece inalterada.
 - La solicitud (ej. "Valeria Sánchez") continúa visible en la pestaña "Pendientes" y su fila sigue desplegada.
 - Los contadores numéricos de las pestañas no sufren alteraciones.

## ID: CP-HU-23-R7
**Título:** Bloqueo de ingreso de caracteres en comentario adicional al exceder el límite
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** El Tutor se encuentra logueado y en la pantalla de Bandeja de Entrada con solicitudes pendientes. El modal 'Rechazar solicitud de tutoría' está abierto y el radio button "Otro" ha sido seleccionado, mostrando el campo "Comentario adicional (opcional)".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Bandeja de Entrada'.
 3. Desplegar los detalles de una solicitud de tutoría pendiente (ej. la de "Valeria Sánchez").
 4. Hacer clic en el botón "Rechazar" (fondo blanco).
 5. Hacer clic en el radio button "Otro".
 6. Ingresar en el campo de texto "Comentario adicional (opcional)" el texto: "C" repetido 301 veces sin espacios.

**Expected Results:**
 - El sistema bloquea el ingreso adicional de texto después del caracter número 300.
 - El contador inferior muestra exactamente "300/300".
 - No se permite sobrepasar el límite de 300 caracteres visualmente ni funcionalmente en el campo.

---

## ID: CP-HU-33-R1
**Título:** Verificar visualización del filtro "Todas" en Mis Solicitudes
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra autenticado y navega a la pantalla principal de "Mis Solicitudes". Existen solicitudes en varios estados (Pendiente, Aceptada, Rechazada, Expirada).

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Hacer clic en la pestaña superior "Todas (X)" (donde X es el contador total de solicitudes).

**Expected Results:**
 - La pestaña "Todas (X)" se muestra activa (fondo azul oscuro con texto blanco).
 - Se visualiza una lista de tarjetas que combina visualmente solicitudes en estado Pendiente, Aceptada, Rechazada y Expirada.
 - Cada tarjeta muestra de forma obligatoria el avatar, materia, tutor, fecha/hora, modalidad, precio y su respectiva etiqueta de estado en la esquina superior derecha.

---

## ID: CP-HU-33-R2
**Título:** Verificar visualización del filtro "Pendientes" en Mis Solicitudes
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la pantalla de "Mis Solicitudes". Existen solicitudes en estado Pendiente.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Hacer clic en la pestaña "Pendientes (X)" (donde X es el contador de solicitudes pendientes).

**Expected Results:**
 - La pestaña "Pendientes (X)" se muestra activa (fondo oscuro, texto blanco).
 - El sistema filtra la lista principal y renderiza únicamente las tarjetas correspondientes a solicitudes en curso.
 - En todas las tarjetas visibles, la etiqueta de estado es "Pendiente" (texto naranja con ícono de reloj, fondo naranja claro).

---

## ID: CP-HU-33-R3
**Título:** Verificar visualización del filtro "Aceptadas" en Mis Solicitudes
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la pantalla de "Mis Solicitudes". Existen solicitudes en estado Aceptada.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Hacer clic en la pestaña "Aceptadas (X)" (donde X es el contador de solicitudes aceptadas).

**Expected Results:**
 - La pestaña "Aceptadas (X)" se muestra activa (fondo oscuro, texto blanco).
 - El sistema filtra la lista principal y renderiza únicamente las tarjetas correspondientes a solicitudes aceptadas.
 - En todas las tarjetas visibles, la etiqueta de estado es "Aceptada" (texto negro con ícono de check, fondo gris claro).

---

## ID: CP-HU-33-R4
**Título:** Verificar visualización del filtro "Rechazadas" en Mis Solicitudes
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la pantalla de "Mis Solicitudes". Existen solicitudes en estado Rechazada.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Hacer clic en la pestaña "Rechazadas (X)" (donde X es el contador de solicitudes rechazadas).

**Expected Results:**
 - La pestaña "Rechazadas (X)" se muestra activa (fondo oscuro, texto blanco).
 - El sistema filtra la lista principal y renderiza únicamente las tarjetas correspondientes a solicitudes rechazadas.
 - En todas las tarjetas visibles, la etiqueta de estado es "Rechazada" (texto gris oscuro con ícono de cruz, fondo gris claro).

---

## ID: CP-HU-33-R5
**Título:** Verificar visualización del filtro "Expiradas" en Mis Solicitudes
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la pantalla de "Mis Solicitudes". Existen solicitudes en estado Expirada.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Hacer clic en la pestaña "Expiradas (X)" (donde X es el contador de solicitudes expiradas).

**Expected Results:**
 - La pestaña "Expiradas (X)" se muestra activa (fondo oscuro, texto blanco).
 - El sistema filtra la lista principal y renderiza únicamente las tarjetas que superaron la regla de tiempo.
 - Visualmente, todas las tarjetas mostradas presentan una franja lateral izquierda color rojo y en la esquina superior derecha contienen el tag "Expirada" (texto rojo, ícono de reloj, fondo rojo claro).

---

## ID: CP-HU-33-R6
**Título:** Verificar despliegue del modal "Detalle de la Solicitud" para una solicitud Pendiente
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la vista de "Mis Solicitudes" y visualiza en su lista una tarjeta con el tag de estado "Pendiente".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Asegurarse de que existe al menos una tarjeta de solicitud con la etiqueta "Pendiente".
 4. Hacer clic sobre cualquier parte de una tarjeta de solicitud con estado "Pendiente".

**Expected Results:**
 - El sistema superpone en la pantalla el modal "Detalle de la Solicitud".
 - El modal despliega el resumen del tutor, el bloque informativo de la tutoría, y el recuadro "TU MENSAJE" con el texto original enviado.
 - En la parte inferior del modal, se muestra únicamente el botón "Cerrar".
 - El botón "Cancelar Solicitud" no se visualiza o se encuentra inactivo para esta versión.

---

## ID: CP-HU-33-R7
**Título:** Verificar despliegue del modal "Detalle de la Solicitud" para una solicitud Aceptada
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la vista de "Mis Solicitudes" y visualiza en su lista una tarjeta con el tag de estado "Aceptada".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Asegurarse de que existe al menos una tarjeta de solicitud con la etiqueta "Aceptada".
 4. Hacer clic sobre cualquier parte de una tarjeta de solicitud con estado "Aceptada".

**Expected Results:**
 - El sistema superpone en la pantalla el modal "Detalle de la Solicitud".
 - En el bloque del tutor del modal, se visualiza la etiqueta "Aceptada".
 - El modal incluye recuadros adicionales con la confirmación del "LUGAR" o "ENLACE", seguido de "TU MENSAJE".
 - En la parte inferior del modal, se visualizan los botones "Cancelar Tutoría" (texto rojo) y "Cerrar".

---

## ID: CP-HU-33-R8
**Título:** Verificar despliegue del modal "Detalle de la Solicitud" para una solicitud Rechazada
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la vista de "Mis Solicitudes" y visualiza en su lista una tarjeta con el tag de estado "Rechazada".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Asegurarse de que existe al menos una tarjeta de solicitud con la etiqueta "Rechazada".
 4. Hacer clic sobre cualquier parte de una tarjeta de solicitud con estado "Rechazada".

**Expected Results:**
 - El sistema superpone en la pantalla el modal "Detalle de la Solicitud".
 - En el bloque del tutor del modal, se visualiza la etiqueta "Rechazada".
 - El modal incluye el recuadro "TU MENSAJE" y, debajo de este, un recuadro gris llamado "MOTIVO DE RECHAZO" con la explicación del tutor.
 - En la parte inferior del modal, se visualiza únicamente el botón "Cerrar".

---

## ID: CP-HU-33-R9
**Título:** Verificar despliegue del modal "Detalle de la Solicitud" para una solicitud Expirada
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra en la vista de "Mis Solicitudes" y visualiza en su lista una tarjeta con el tag de estado "Expirada".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Asegurarse de que existe al menos una tarjeta de solicitud con la etiqueta "Expirada".
 4. Hacer clic sobre cualquier parte de una tarjeta de solicitud con estado "Expirada".

**Expected Results:**
 - El sistema superpone el modal "Detalle de la Solicitud".
 - En la cabecera del modal se visualiza el tag "Expirada" (rojo).
 - El modal opera en modo solo lectura, mostrando la información base de la tutoría solicitada.
 - En la parte inferior del modal, únicamente se muestra el botón "Cerrar".

---

## ID: CP-HU-33-R10
**Título:** Verificar visualización de controles de paginación con más de 5 solicitudes
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante se encuentra autenticado y navega a la pantalla principal de "Mis Solicitudes". En la pestaña "Todas" (o cualquier otra pestaña) existen más de 5 registros asociados (ej: "Todas (16)").

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Mis Solicitudes'.
 3. Asegurarse de que la pestaña "Todas" (o la pestaña activa) muestre un contador de solicitudes mayor a 5.
 4. Observar la parte inferior de la lista de tarjetas después de la carga inicial.

**Expected Results:**
 - La aplicación carga y renderiza la lista inicial de las primeras 5 tarjetas.
 - Justo debajo de la última tarjeta visible, se visualiza una barra de paginación numérica (ej. `< 1 2 3 4 >`).
 - El control de paginación está compuesto por flechas de navegación y números de página.
 - El número de la página activa se muestra resaltado dentro de un recuadro oscuro.

---

## ID: CP-HU-46-R1
**Título:** Verificar la visualización de la lista de solicitudes Respondidas con un total de 10 o menos registros.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Bandeja de Entrada". Existe un historial de solicitudes procesadas (aceptadas y/o rechazadas) con un total de 10 o menos.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Bandeja de Entrada".
 3. Hacer clic en la pestaña "Respondidas (X)" (donde X es un número menor o igual a 10, por ejemplo, "Respondidas (8)").

**Expected Results:**
 - La pantalla permanece en la vista principal de "T. Bandeja de Entrada".
 - La pestaña "Respondidas (X)" se muestra activa (fondo oscuro, texto blanco).
 - Se visualiza una lista continua de hasta 10 tarjetas que combinan las solicitudes previamente aceptadas y rechazadas.
 - Cada fila en la lista cuenta con su respectiva etiqueta visual de estado en la columna derecha ("Aceptada" o "Rechazada").

---

## ID: CP-HU-46-R2
**Título:** Verificar el despliegue del modal "Detalle de la Solicitud" al hacer clic en una tarjeta con estado "Aceptada".
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Bandeja de Entrada" con la pestaña "Respondidas" activa. La lista visible contiene al menos una tarjeta de solicitud con la etiqueta "Aceptada".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Bandeja de Entrada".
 3. Hacer clic en la pestaña "Respondidas (X)".
 4. Hacer clic sobre una tarjeta de solicitud en la lista que tenga la etiqueta "Aceptada".

**Expected Results:**
 - Se superpone el modal "Detalle de la Solicitud" sobre la pantalla actual.
 - El modal tiene el título "Detalle de la Solicitud" con ícono de "X" para cerrar.
 - Se muestra un recuadro superior con el avatar, nombre del estudiante, rol "Estudiante" y la etiqueta ovalada "Aceptada".
 - Incluye recuadros separados detallando la confirmación de la tutoría (ej. "LUGAR" con su ubicación o enlace), la información base de la materia con fecha, hora y precio por hora (ej. "$10/h").
 - Incluye el recuadro "MENSAJE DEL ESTUDIANTE" con borde lateral naranja.
 - En la parte inferior derecha, se encuentra únicamente el botón "Cerrar" (sin borde, color de texto azul oscuro).

---

## ID: CP-HU-46-R3
**Título:** Verificar el despliegue del modal "Detalle de la Solicitud" al hacer clic en una tarjeta con estado "Rechazada".
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Bandeja de Entrada" con la pestaña "Respondidas" activa. La lista visible contiene al menos una tarjeta de solicitud con la etiqueta "Rechazada".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Bandeja de Entrada".
 3. Hacer clic en la pestaña "Respondidas (X)".
 4. Hacer clic sobre una tarjeta de solicitud en la lista que tenga la etiqueta "Rechazada".

**Expected Results:**
 - Se superpone el modal "Detalle de la Solicitud" sobre la pantalla actual.
 - El modal tiene el título "Detalle de la Solicitud" con ícono de "X" para cerrar.
 - Se muestra el recuadro superior con la información del estudiante y la etiqueta ovalada "Rechazada".
 - Incluye el recuadro de la materia, fecha, hora y precio.
 - No incluye bloque de confirmación (lugar/enlace).
 - Muestra el "MENSAJE DEL ESTUDIANTE".
 - Directamente debajo de este, un recuadro gris claro titulado "MOTIVO DE RECHAZO" que detalla la razón seleccionada por el tutor (ej. "Otro").
 - En la parte inferior derecha, se encuentra únicamente el botón "Cerrar".

---

## ID: CP-HU-46-R4
**Título:** Verificar la visualización de la lista de solicitudes Respondidas con más de 10 registros y controles de paginación.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Bandeja de Entrada". Existe un historial de solicitudes procesadas (aceptadas y/o rechazadas) con un total superior a 10 (ej. 12).

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Bandeja de Entrada".
 3. Hacer clic en la pestaña "Respondidas (X)" (donde X es un número mayor a 10, por ejemplo, "Respondidas (12)").

**Expected Results:**
 - La pantalla permanece en la vista principal de "T. Bandeja de Entrada".
 - La pestaña "Respondidas (X)" se muestra activa (fondo oscuro, texto blanco).
 - Se visualiza una lista de hasta 10 tarjetas que combinan las solicitudes previamente aceptadas y rechazadas.
 - Cada fila en la lista cuenta con su respectiva etiqueta visual de estado en la columna derecha ("Aceptada" o "Rechazada").
 - Justo debajo de la última tarjeta de la lista en la pantalla principal, se visualizan los controles numéricos estándar de paginación para permitir al tutor navegar hacia páginas anteriores o siguientes.

---

## ID: CP-HU-47-R1
**Título:** Verificar filtrado y visualización de solicitudes aceptadas.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla "Mis Solicitudes". El sistema registra en la base de datos tutorías que los tutores ya confirmaron.

**Steps:**
 1. Iniciar sesión como estudiante.
 2. Navegar a la sección "Mis Solicitudes".
 3. Hacer clic en la pestaña "Aceptadas (X)".

**Expected Results:**
 - La interfaz responde marcando la pestaña "Aceptadas (X)" como estado activo (fondo oscuro, texto blanco).
 - La lista de tarjetas central se actualiza y muestra exclusivamente aquellas solicitudes confirmadas.
 - Visualmente, todas las tarjetas renderizadas incluyen en su esquina superior derecha el tag "Aceptada" (ícono de check, fondo gris claro).
 - Se visualiza una lista de hasta 5 tarjetas.

---

## ID: CP-HU-47-R2
**Título:** Verificar filtrado y visualización de solicitudes rechazadas.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla "Mis Solicitudes". El sistema registra en la base de datos tutorías que los tutores declinaron.

**Steps:**
 1. Iniciar sesión como estudiante.
 2. Navegar a la sección "Mis Solicitudes".
 3. Hacer clic en la pestaña "Rechazadas (X)".

**Expected Results:**
 - La interfaz responde marcando la pestaña "Rechazadas (X)" como estado activo (fondo oscuro, texto blanco).
 - La lista de tarjetas central se actualiza y muestra exclusivamente aquellas solicitudes declinadas.
 - Visualmente, todas las tarjetas renderizadas incluyen en su esquina superior derecha el tag "Rechazada" (ícono de cruz, fondo gris claro).
 - Justo debajo de la información base de la tutoría, se inyecta una línea de texto cursiva en color gris con el formato "Motivo de rechazo: [Texto del motivo]".
 - Se visualiza una lista de hasta 5 tarjetas.

---

## ID: CP-HU-47-R3
**Título:** Verificar visualización del modal de detalle para solicitud aceptada.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla "Mis Solicitudes". Se visualiza al menos una tarjeta de tutoría que contiene el tag de estado "Aceptada".

**Steps:**
 1. Iniciar sesión como estudiante.
 2. Navegar a la sección "Mis Solicitudes".
 3. Hacer clic en cualquier parte interactiva de una tarjeta de solicitud que contenga la etiqueta "Aceptada".

**Expected Results:**
 - El sistema interrumpe la vista actual superponiendo el modal "Detalle de la Solicitud".
 - La interfaz del modal incluye la cabecera con el tag "Aceptada".
 - El modal presenta un bloque superior con la confirmación acordada (recuadro "LUGAR" o "ENLACE" según la modalidad).
 - El modal presenta los datos de fecha/hora, materia y el campo original "TU MENSAJE".
 - En la barra inferior del modal se renderiza únicamente el botón "Cerrar".
 - No se visualiza la opción "Cancelar Tutoría".

---

## ID: CP-HU-47-R4
**Título:** Verificar visualización del modal de detalle para solicitud rechazada.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla "Mis Solicitudes". Se visualiza al menos una tarjeta de tutoría que contiene el tag de estado "Rechazada".

**Steps:**
 1. Iniciar sesión como estudiante.
 2. Navegar a la sección "Mis Solicitudes".
 3. Hacer clic en cualquier parte interactiva de una tarjeta de solicitud que contenga la etiqueta "Rechazada".

**Expected Results:**
 - El sistema superpone el modal "Detalle de la Solicitud".
 - La interfaz del modal incluye la cabecera con el tag "Rechazada".
 - El modal presenta los datos de la materia/fecha y el campo original "TU MENSAJE".
 - El modal presenta un bloque adicional inferior con fondo gris titulado "MOTIVO DE RECHAZO" conteniendo la justificación del tutor (ej. "Falta de tiempo").
 - La barra inferior del modal presenta únicamente el botón "Cerrar".

---

## ID: CP-HU-47-R5
**Título:** Verificar la visualización de controles de paginación cuando hay más de 5 solicitudes.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla "Mis Solicitudes". Una de las pestañas de estado (ej. "Todas", "Aceptadas", "Rechazadas") tiene un volumen de datos que excede el límite de tarjetas por vista (5 registros).

**Steps:**
 1. Iniciar sesión como estudiante.
 2. Navegar a la sección "Mis Solicitudes".
 3. Asegurarse de que la pestaña activa (ej. "Todas") contenga más de 5 solicitudes.
 4. Observar la parte inferior de la lista de tarjetas.

**Expected Results:**
 - El sistema inserta en el DOM, inmediatamente debajo del último elemento de la lista, la barra de paginación numérica (ej. `< 1 2 3 4 >`).
 - La página actual en visualización resalta con un fondo azul oscuro sólido.
 - La lista de tarjetas en la pantalla principal muestra un máximo de 5 solicitudes.

---

## ID: CP-HU-15-R1
**Título:** Verificar navegación a la vista principal "Mi Agenda"
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor autenticado y logueado en la plataforma PoliTutorias.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Ubicar el cursor y hacer clic sobre el enlace "Mi Agenda" en la barra de navegación global superior.

**Expected Results:**
 - El sistema enruta y carga la vista principal de la agenda ('T. Mi Agenda').
 - Se visualiza el título "Mi Agenda" y el subtítulo "Calendario de sesiones confirmadas".
 - El enlace "Mi Agenda" en el menú superior queda marcado con un resaltado amarillo indicando la ubicación activa.
 - La vista se divide en dos columnas: la izquierda muestra el calendario mensual con indicadores textuales en los días agendados, y la columna derecha (panel lateral) muestra el resumen "ESTE MES".
 - En la barra de navegación superior se muestran los enlaces 'Panel', 'Bandeja', 'Mi Agenda' (resaltado con fondo amarillo), 'Henry' (con ícono de usuario 'H' en círculo naranja), y 'Salir'.
 - El calendario muestra el mes 'Marzo 2026', flechas de navegación '<' y '>', los encabezados de los días de la semana 'DOM' a 'SÁB', y la cuadrícula de días del mes (del 1 al 31), incluyendo días con sesiones confirmadas (ej: '4: 15:00 Cálculo...', '6: 09:00 Cálculo..., 09:00 Física I, +2 más', '7: 11:00 Álgebra...', '8: 09:00 Cálculo..., 11:00 Física I, +2 más', '15: 10:00 Cálculo...').
 - El día '9' está resaltado con un círculo morado y el día '15' con un fondo amarillo.
 - El panel lateral derecho muestra el encabezado '15 de Marzo', '1 sesión confirmada', y la tarjeta '10:00 — Cálculo Vectorial', 'Andrés Morales', 'Toca para ver detalles →'.
 - La sección 'ESTE MES' muestra 'Sesiones confirmadas 11' (y flecha de expandir/contraer), listando sesiones como '11:00 — Álgebra Lineal', 'Andrés Morales', divisores de día (ej. 'Dom 8' con '4' sesiones) y sus respectivas sesiones, y 'Dom 15' con '1' sesión y su sesión.

---

## ID: CP-HU-15-R2
**Título:** Verificar actualización del panel lateral al seleccionar un día en el calendario
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Mi Agenda", observando el calendario mensual con datos cargados, donde se evidencian días específicos que contienen etiquetas de sesiones confirmadas.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la vista principal "Mi Agenda".
 2. Posicionar el cursor y hacer clic sobre el cuadro numérico correspondiente a un día específico en el calendario que contenga sesiones confirmadas (ej., el día '8').

**Expected Results:**
 - El panel lateral derecho actualiza su cabecera para mostrar la fecha específica seleccionada (ej. '8 de Marzo') y el número de sesiones confirmadas para ese día (ej. '4 sesiones confirmadas').
 - El bloque de tarjetas "ESTE MES" se desplaza hacia abajo.
 - En la parte superior del panel se renderizan las tarjetas de sesiones confirmadas **exclusivamente para el día seleccionado** (ej. si se clickea el día '8', se muestran las tarjetas: '09:00 — Cálculo Vectorial', 'Sebastián Ríos', '11:00 — Física I', 'Isabella Mora', '14:00 — Álgebra Lineal', 'Lucas Herrera', '16:00 — Estática', 'Camila Flores').
 - La sección 'ESTE MES' y su listado de sesiones por mes se mantiene visible debajo, si está expandida.

---

## ID: CP-HU-15-R3
**Título:** Verificar visualización del modal "Detalle Tutoría" para una tutoría Virtual Pendiente
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Mi Agenda", habiendo seleccionado un día en el calendario cuyo panel lateral visualiza la tarjeta resumen de una tutoría confirmada con modalidad "Virtual" y estado "Pendiente".

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la vista principal "Mi Agenda".
 2. Seleccionar un día en el calendario que tenga una tutoría Virtual y Pendiente (ej. el día '15' que muestra '10:00 — Cálculo Vectorial').
 3. Hacer clic sobre la tarjeta resumen de la sesión "10:00 — Cálculo Vectorial" en el panel lateral derecho.

**Expected Results:**
 - El sistema bloquea la vista de fondo y abre un modal (según mapa M7) sobre la pantalla 'T. Mi Agenda'.
 - El modal tiene el título '10:00 — Cálculo Vectorial' y subtítulo 'Andrés Morales'.
 - Dentro del modal se visualizan los campos: 'Modalidad: Virtual', 'Estado: Pendiente', 'Fecha: 15 de Marzo, 2026'.
 - Se visualiza un bloque titulado 'ENLACE' que presenta la URL 'meet.google.com/abc-xyz-pqr' en color azul.
 - Se visualizan los campos 'Estudiante:' y un campo de texto multi-línea 'Mensaje:'.
 - La botonera inferior del modal despliega los botones 'Cancelar tutoría' (a la izquierda) y 'Cerrar' (a la derecha).

---

## ID: CP-HU-15-R4
**Título:** Verificar visualización del modal "Detalle Tutoría" para una tutoría Presencial Pendiente
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Mi Agenda", habiendo seleccionado un día en el calendario cuyo panel lateral visualiza la tarjeta resumen de una tutoría confirmada con modalidad "Presencial" y estado "Pendiente".

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la vista principal "Mi Agenda".
 2. Seleccionar un día en el calendario que tenga una tutoría Presencial y Pendiente (ej. el día '15' que muestra '10:00 — Cálculo Vectorial').
 3. Hacer clic sobre la tarjeta resumen de la sesión "10:00 — Cálculo Vectorial" en el panel lateral derecho.

**Expected Results:**
 - El sistema bloquea la vista de fondo y abre un modal (según mapa M7) sobre la pantalla 'T. Mi Agenda'.
 - El modal tiene el título '10:00 — Cálculo Vectorial' y subtítulo 'Andrés Morales'.
 - Dentro del modal se visualizan los campos: 'Modalidad: Presencial', 'Estado: Pendiente', 'Fecha: 15 de Marzo, 2026'.
 - Se visualiza un bloque titulado 'LUGAR' (acompañado de un ícono de ubicación) que expone la dirección física 'Carrera 43 # 12-34, Bogotá'.
 - Se visualizan los campos 'Estudiante:' y un campo de texto multi-línea 'Mensaje:'.
 - La botonera inferior del modal despliega los botones 'Cancelar tutoría' (a la izquierda) y 'Cerrar' (a la derecha).

---

## ID: CP-HU-15-R5
**Título:** Verificar visualización del modal "Detalle Tutoría" para una tutoría Completada
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Mi Agenda", habiendo seleccionado un día en el calendario cuyo panel lateral visualiza la tarjeta resumen de una tutoría confirmada con estado "Completada".

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la vista principal "Mi Agenda".
 2. Seleccionar un día en el calendario que contenga una tutoría con estado "Completada".
 3. Hacer clic sobre la tarjeta resumen de la sesión con estado "Completada" en el panel lateral derecho.

**Expected Results:**
 - El sistema bloquea la vista de fondo y abre un modal (según mapa M7) sobre la pantalla 'T. Mi Agenda'.
 - El modal muestra un mensaje superior indicando: 'Tutoría completada. Esta tutoría ya se realizó. Solo puedes ver los detalles.'
 - Únicamente el botón 'Cerrar' se visualiza en la parte inferior del modal.

---

## ID: CP-HU-15-R6
**Título:** Verificar el cierre del modal de detalle de tutoría Completada
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Mi Agenda", con el modal "Detalle Tutoría" de una tutoría "Completada" abierto.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la vista principal "Mi Agenda".
 2. Seleccionar un día en el calendario que contenga una tutoría con estado "Completada" y hacer clic en su tarjeta resumen para abrir el modal.
 3. Hacer clic en el botón "Cerrar" en la parte inferior del modal de detalle de tutoría completada.

**Expected Results:**
 - El modal de detalle de tutoría completada se cierra y desaparece de la vista.
 - Se regresa a la pantalla 'T. Mi Agenda' con la vista de calendario mensual.
 - El panel lateral derecho muestra el estado previo (ej. el resumen de sesiones del día o del mes) antes de la apertura del modal.

---

## ID: CP-HU-15-R7
**Título:** Verificar el cierre del modal de detalle de tutoría (virtual/presencial pendiente)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Mi Agenda", con el modal "Detalle Tutoría" de una tutoría "Virtual Pendiente" o "Presencial Pendiente" abierto.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la vista principal "Mi Agenda".
 2. Seleccionar un día en el calendario que contenga una tutoría Virtual o Presencial Pendiente y hacer clic en su tarjeta resumen para abrir el modal.
 3. Hacer clic en el botón "Cerrar" en la esquina inferior derecha del modal de detalle de tutoría.

**Expected Results:**
 - La acción de cerrado se ejecuta, el modal desaparece de la vista.
 - La pantalla principal de Mi Agenda recupera el foco.
 - Se conserva el día previamente seleccionado en el calendario y la vista del panel derecho intacta.
 - Se regresa a la pantalla 'T. Mi Agenda' con la vista de calendario mensual y el panel lateral derecho mostrando el estado previo antes de la apertura del modal.

---

## ID: CP-HU-15-R8
**Título:** Verificar el inicio del flujo de cancelación de tutoría desde el modal de detalle
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla "Mi Agenda", con el modal "Detalle Tutoría" de una tutoría "Virtual Pendiente" o "Presencial Pendiente" abierto, y el botón "Cancelar tutoría" visible.

**Steps:**
 1. Iniciar sesión como Tutor y navegar a la vista principal "Mi Agenda".
 2. Seleccionar un día en el calendario que contenga una tutoría Virtual o Presencial Pendiente y hacer clic en su tarjeta resumen para abrir el modal.
 3. Hacer clic en el botón "Cancelar tutoría" en la parte inferior izquierda del modal de detalle de tutoría.

**Expected Results:**
 - Se cierra el modal de detalle de tutoría actual.
 - El sistema inicia el flujo de cancelación de la tutoría, levantando una alerta destructiva o un nuevo modal exigiendo la selección de un motivo justificado.
 - Una vez completado este flujo de selección de motivo, se regresa a la pantalla 'T. Mi Agenda'.
 - La pantalla principal de Mi Agenda recupera el foco.

---

## ID: CP-HU-11-01
**Título:** Visualización de la pantalla 'Tutorías Agendadas' al navegar desde el menú
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado en el sistema y con registros de tutorías futuras confirmadas.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Hacer clic en el enlace de navegación "Agenda" en el menú superior.

**Expected Results:**
 - El sistema enruta la vista y carga la pantalla de Tutorías Agendadas.
 - Se visualiza la barra de navegación superior con el 'Poli Tutorías' logo y los textos 'Explorar', 'Mis Solicitudes', 'Agenda' (subrayado).
 - A la derecha, se muestra 'P Patricio' y 'Salir'.
 - El contenido principal incluye el título 'Tutorías Agendadas' y el subtítulo 'Lista cronológica de tus sesiones confirmadas'.
 - Se organiza la sección titulada "PRÓXIMAS (3)" que contiene tres tarjetas de tutorías futuras con su fecha, horario, materia y tutor resaltados.
 - Cada tarjeta de 'PRÓXIMAS' incluye: un bloque de calendario con el mes (ej. 'MAR') y el día (ej. '15'), el título de la materia (ej. 'Cálculo Vectorial'), la hora (ej. '10:00'), un mini avatar seguido del nombre del tutor (ej. 'Juan Pérez'), y la fecha completa (ej. 'Domingo, 15 de marzo de 2026').
 - Se muestra la sección 'ANTERIORES (7)' con tres tarjetas de tutoría visibles en un tono gris claro.
 - Cada tarjeta de 'ANTERIORES' incluye: un bloque de calendario con el mes (ej. 'MAR') y el día (ej. '8'), el título de la materia (ej. 'Programación Básica'), la hora (ej. '09:00'), un mini avatar seguido del nombre del tutor (ej. 'María López'), la fecha completa (ej. 'Domingo, 8 de marzo de 2026'), y una etiqueta 'COMPLETADA' en el lado derecho.
 - Debajo de las tarjetas de 'ANTERIORES', se encuentra un botón con el texto 'Ver todas las anteriores (4 más)' y un icono de flecha hacia abajo.

---

## ID: CP-HU-11-02
**Título:** Visualización del modal de detalle para tutoría virtual próxima
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla 'Tutorías Agendadas', con una tutoría virtual próxima en la sección "PRÓXIMAS".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'E. Agenda' (Tutorías Agendadas).
 3. Localizar una tarjeta de tutoría configurada bajo la modalidad "Virtual" en la sección "PRÓXIMAS" (Ej: 'Cálculo Vectorial').
 4. Hacer clic en la tarjeta de tutoría 'Cálculo Vectorial'.

**Expected Results:**
 - El sistema reacciona levantando la superposición del modal "Detalles de la Sesión".
 - El modal se despliega con el título 'Cálculo Vectorial'.
 - Dentro del modal se muestran los detalles: Fecha 'Domingo, 15 de marzo de 2026', Hora '10:00', Tarifa '$20.000 COP/hora', Modalidad 'Virtual'.
 - Se renderiza el bloque "ENLACE" mostrando el hipervínculo en color azul 'meet.google.com/abc-xyz-123'.
 - Se muestra la sección con el título 'Mensaje' y el texto 'Necesito refuerzo en integrales triples y series de Fourier.'.
 - En la esquina inferior derecha del modal, se presenta únicamente el botón "Cerrar". No se visualiza la opción para cancelar.

---

## ID: CP-HU-11-03
**Título:** Visualización del modal de detalle para tutoría presencial próxima
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla 'Tutorías Agendadas', con una tutoría presencial próxima en la sección "PRÓXIMAS".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'E. Agenda' (Tutorías Agendadas).
 3. Localizar una tarjeta de tutoría configurada bajo la modalidad "Presencial" en la sección "PRÓXIMAS" (Ej: 'Química Orgánica').
 4. Hacer clic en la tarjeta de tutoría 'Química Orgánica'.

**Expected Results:**
 - El sistema reacciona levantando la superposición del modal "Detalles de la Sesión".
 - El modal se despliega con el título 'Química Orgánica'.
 - Dentro del modal se muestran los detalles: Fecha 'Jueves, 2 de abril de 2026', Hora '11:00', Tarifa '$20.000 COP/hora', Modalidad 'Presencial'.
 - Se renderiza el bloque específico "LUGAR" acompañado de un ícono de ubicación o mapa, detallando la dirección 'Laboratorio de Química, Edificio B, Piso 2'.
 - Se muestra la sección con el título 'Mensaje' y el texto 'Necesito repasar los mecanismos de reacción para SN1 y SN2.'.
 - En la botonera de la parte inferior del modal, se presenta únicamente el botón "Cerrar".

---

## ID: CP-HU-11-04
**Título:** Cierre del modal de detalle de tutoría al hacer clic en el botón 'Cerrar'
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla 'Tutorías Agendadas', con el modal "Detalles de la Sesión" de una tutoría próxima abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'E. Agenda' (Tutorías Agendadas).
 3. Hacer clic en una tarjeta de tutoría 'PRÓXIMA' (Ej: 'Cálculo Vectorial') para abrir el modal de detalle.
 4. Hacer clic en el botón "Cerrar" en la parte inferior del modal "Detalles de la Sesión".

**Expected Results:**
 - El sistema captura la orden de salida y destruye el modal.
 - El modal desaparece de la vista.
 - La pantalla 'E. Agenda' se muestra completamente, con todos sus elementos visibles nuevamente.
 - La lista de tutorías "PRÓXIMAS" se mantiene en la misma posición de scroll o vista en la que se encontraba originalmente antes del clic.

---

## ID: CP-HU-11-05
**Título:** Cierre del modal de detalle de tutoría al hacer clic en el ícono 'X'
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante autenticado y en la pantalla 'Tutorías Agendadas', con el modal "Detalles de la Sesión" de una tutoría próxima abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'E. Agenda' (Tutorías Agendadas).
 3. Hacer clic en una tarjeta de tutoría 'PRÓXIMA' (Ej: 'Química Orgánica') para abrir el modal de detalle.
 4. Hacer clic en el ícono de "X" ubicado en la cabecera del modal "Detalles de la Sesión".

**Expected Results:**
 - El sistema captura la orden de salida y destruye el modal.
 - El modal desaparece de la vista.
 - La pantalla 'E. Agenda' se muestra completamente, con todos sus elementos visibles nuevamente.
 - La lista de tutorías "PRÓXIMAS" se mantiene en la misma posición de scroll o vista en la que se encontraba originalmente antes del clic.

---