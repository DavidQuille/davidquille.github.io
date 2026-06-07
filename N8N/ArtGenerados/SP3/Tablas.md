# Reporte de Tablas
> Generado el: 10/3/2026

### Nro. HU-06 - Título: Enviar solicitud de tutoría

Descripción: Como estudiante, quiero enviar una solicitud para agendar una tutoría.

#### Matriz de Decisión HU-06

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Horario/s de la sección "Disponibilidad Semanal" seleccionado/s? | N | S | S | S | S | S | S | S |
| C2 | ¿El/los horario/s seleccionado/s tiene/n una solicitud activa previa por el estudiante? | N/A | S | N | N | N | N | N | N |
| C3 | ¿La oferta de tutoría tiene una sola modalidad? | N/A | N/A | S | S | N | N | N | N |
| C4 | ¿La oferta de tutoría tiene modalidad "Virtual/Presencial"? | N/A | N/A | N | N | S | S | S | S |
| C5 | ¿Se seleccionó una "Modalidad" en el modal "Solicitar Tutoría"? | N/A | N/A | N/A | N/A | N | S | S | N |
| C6 | ¿El campo de texto "Mensaje para el tutor *" está lleno? | N/A | N/A | S | N | S | S | N | N |
| | **ACCIONES** (Usar código corto) | | | | | | | | |
| A1 | Botón "Solicitar Tutoría" inactivo | X | | | | | | | |
| A2 | Mostrar alerta "Horario ya solicitado" | | X | | | | | | |
| A3 | Mostrar modal "Solicitar Tutoría (Una Modalidad)" | | | X | X | | | | |
| A4 | Mostrar modal "Solicitar Tutoría (Dual Modalidad)" | | | | | X | X | X | X |
| A5 | Mostrar error "Selecciona la modalidad" | | | | | X | | | X |
| A6 | Mostrar mensaje de confirmación de solicitud | | | X | | | X | | |
| A7 | Mostrar error "El mensaje es obligatorio" | | | | X | | | X | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
* **A1 - Botón "Solicitar Tutoría" inactivo:** Permanece en la pantalla "E. Detalle Oferta". **VALIDACIÓN VISUAL:** El botón "Solicitar Tutoría" se muestra en un estado visual deshabilitado, impidiendo la interacción del usuario para abrir el modal de solicitud.
* **A2 - Mostrar alerta "Horario ya solicitado":** Permanece en la pantalla "E. Detalle Oferta". **VALIDACIÓN VISUAL:** Se visualiza una alerta o mensaje con el texto exacto: "Horario ya solicitado. Ya tienes una solicitud activa para [Día] [Hora]."
* **A3 - Mostrar modal "Solicitar Tutoría (Una Modalidad)":** Se abre una ventana modal sobre la pantalla "E. Detalle Oferta". **VALIDACIÓN VISUAL:** El modal tiene como título "Solicitar Tutoría". En la parte superior muestra la foto y nombre del tutor. Incluye la sección "Horarios seleccionados" con chips de las horas. **No incluye selector de modalidad.** Presenta el campo de texto obligatorio "Mensaje para el tutor *" con un contador "0/500", y los botones "Cancelar" y "Enviar Solicitud".
* **A4 - Mostrar modal "Solicitar Tutoría (Dual Modalidad)":** Se abre una ventana modal sobre la pantalla "E. Detalle Oferta". **VALIDACIÓN VISUAL:** El modal tiene como título "Solicitar Tutoría". Muestra la información del tutor y los "Horarios seleccionados". En la sección "Modalidad *", se presentan los botones "Virtual" y "Presencial" (mutuamente excluyentes). Incluye el campo de texto "Mensaje para el tutor *" con el contador "0/500", y los botones "Cancelar" y "Enviar Solicitud".
* **A5 - Mostrar error "Selecciona la modalidad":** Permanece en el modal de solicitud. **VALIDACIÓN VISUAL:** Justo debajo de los botones de selección de "Virtual" y "Presencial", se muestra el mensaje de error exacto en color rojo: "Selecciona la modalidad".
* **A6 - Mostrar mensaje de confirmación de solicitud:** El modal se cierra y el usuario permanece en la pantalla "E. Detalle Oferta". **VALIDACIÓN VISUAL:** Se visualiza una notificación de éxito con el texto exacto: "¡Solicitud enviada! X horario(s) propuesto(s). El tutor revisará tu solicitud pronto." (Donde X es el número de horas seleccionadas).
* **A7 - Mostrar error "El mensaje es obligatorio":** Permanece en el modal de solicitud. **VALIDACIÓN VISUAL:** El borde del campo de texto cambia a color rojo y justo debajo del mismo se muestra el mensaje de error exacto: "El mensaje es obligatorio".
---

### Nro. HU-09 - Título: Ver solicitudes recibidas

Descripción: Como tutor, quiero ver las solicitudes de tutoría que he recibido para enterarme de los estudiantes que necesitan mi ayuda.

#### Matriz de Decisión HU-09

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 | R9 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Ingreso a la pantalla "T. Bandeja de Entrada"?     | S | S | N | N | N | N | N | N | N |
| C2 | ¿Click en tab "Pendientes (X)"?                     | N | N | N | N | S | N | N | N | N |
| C3 | ¿Click en tab "Expiradas (Y)"?                      | N | N | S | S | N | N | N | N | N |
| C4 | ¿Click en "Fila de Solicitud"?                      | N | N | N | N | N | S | S | S | S |
| C5 | ¿"Fila de Solicitud" actualmente desplegada?        | N | N | N | N | N | N | S | N | S |
| C6 | ¿Tab activo es "Pendientes (X)"?                    | S | S | N | N | S | S | S | N | N |
| C7 | ¿Tab activo es "Expiradas (Y)"?                     | N | N | S | S | N | N | N | S | S |
| C8 | ¿Hay solicitudes en la vista del tab activo?        | S | N | S | N | S | S | S | S | S |
| | **ACCIONES** (Usar código corto)                      | | | | | | | | | |
| A1 | Cargar Pantalla T. Bandeja de Entrada (Pendientes Activo) | X | X | | | X | | | | |
| A2 | Mostrar Solicitudes Pendientes (Lista Colapsada)    | X | | | | X | | | | |
| A3 | Mostrar mensaje "No hay solicitudes pendientes."    | | X | | | | | | | |
| A4 | Cargar Pantalla T. Bandeja de Entrada (Expiradas Activo) | | | X | X | | | | | |
| A5 | Mostrar Solicitudes Expiradas (Lista Colapsada)     | | | X | | | | | | | |
| A6 | Mostrar mensaje "No hay solicitudes expiradas."     | | | | X | | | | | |
| A7 | Desplegar Fila de Solicitud (Pendientes)            | | | | | | X | | | |
| A8 | Colapsar Fila de Solicitud (Pendientes)             | | | | | | | X | | |
| A9 | Desplegar Fila de Solicitud (Expiradas)             | | | | | | | | X | |
| A10 | Colapsar Fila de Solicitud (Expiradas)             | | | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
* **A1 - Cargar Pantalla T. Bandeja de Entrada (Pendientes Activo):** Redirige a la pantalla "T. Bandeja de Entrada". **VALIDACIÓN VISUAL:** Se visualiza la barra de navegación superior con los botones "Panel", "Bandeja" (activo), "Mi Agenda", el nombre de usuario y el botón "Salir". Se visualiza el título "Bandeja de Entrada", el subtítulo "Solicitudes de tutoría recibidas" y el indicador global de pendientes en la esquina superior derecha. La pestaña "Pendientes (X)" se muestra activa (fondo oscuro, texto blanco). Las pestañas "Expiradas (Y)" y "Respondidas (Z)" se muestran inactivas.
* **A2 - Mostrar Solicitudes Pendientes (Lista Colapsada):** **VALIDACIÓN VISUAL:** Se visualizan las cabeceras de la tabla "ESTUDIANTE", "MATERIA", "FECHA/HORA", "MENSAJE", "ESTADO". Se muestra una lista de hasta 10 solicitudes (con paginación si excede) en filas. Cada fila contiene: avatar/iniciales, nombre del estudiante, materia, fecha y hora, un fragmento del mensaje y el tag de estado "Pendiente" (texto naranja, fondo claro). Cada fila presenta un ícono de flecha hacia abajo a la derecha.
* **A3 - Mostrar mensaje "No hay solicitudes pendientes.":** **VALIDACIÓN VISUAL:** Se ocultan las cabeceras de la tabla y en el área principal de contenido se visualiza el texto exacto: "No hay solicitudes pendientes.".
* **A4 - Cargar Pantalla T. Bandeja de Entrada (Expiradas Activo):** Permanece en la pantalla "T. Bandeja de Entrada". **VALIDACIÓN VISUAL:** La pestaña "Expiradas (Y)" se muestra activa (fondo oscuro, texto blanco). Las pestañas "Pendientes (X)" y "Respondidas (Z)" se muestran inactivas.
* **A5 - Mostrar Solicitudes Expiradas (Lista Colapsada):** **VALIDACIÓN VISUAL:** Se visualizan las cabeceras de la tabla. Se muestra una lista de hasta 10 solicitudes (con paginación si excede) en filas. Cada fila contiene: avatar/iniciales, nombre del estudiante, materia, fecha y hora, un fragmento del mensaje y el tag de estado "Expirada" (texto rojo). Cada fila presenta un ícono de flecha hacia abajo a la derecha.
* **A6 - Mostrar mensaje "No hay solicitudes expiradas.":** **VALIDACIÓN VISUAL:** Se ocultan las cabeceras de la tabla y en el área principal de contenido se visualiza el texto exacto: "No hay solicitudes expiradas.".
* **A7 - Desplegar Fila de Solicitud (Pendientes):** La fila seleccionada se expande. **VALIDACIÓN VISUAL:** Se muestran detalles adicionales debajo de la información base: un ícono con la modalidad (ej. "Virtual"), el precio por hora (ej. "$10/h"), y un recuadro con el título "MENSAJE DEL ESTUDIANTE" que contiene el texto completo. **Se visualizan los botones "Aceptar" (fondo oscuro) y "Rechazar" (fondo blanco).** El ícono de flecha de la fila cambia apuntando hacia arriba.
* **A8 - Colapsar Fila de Solicitud (Pendientes):** La fila seleccionada se contrae. **VALIDACIÓN VISUAL:** Se ocultan los detalles de modalidad, precio, mensaje completo y los botones de acción. Se vuelve a mostrar únicamente el resumen de la fila.
* **A9 - Desplegar Fila de Solicitud (Expiradas):** La fila seleccionada se expande. **VALIDACIÓN VISUAL:** Se muestran detalles adicionales: modalidad (ej. "Presencial"), precio (ej. "$8/h"), y un recuadro con el título "MENSAJE DEL ESTUDIANTE" conteniendo el texto completo. El ícono de flecha apunta hacia arriba. **No se visualizan botones de acción.**
* **A10 - Colapsar Fila de Solicitud (Expiradas):** La fila seleccionada se contrae. **VALIDACIÓN VISUAL:** Se ocultan los detalles de modalidad, precio y mensaje completo. Se vuelve a mostrar únicamente el resumen de la fila.

---

### Nro. HU-08 - Título: Aceptar solicitud de tutoría

Descripción: Como tutor, quiero aceptar una solicitud para confirmar el agendamiento de la tutoría.

#### Matriz de Decisión HU-08

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Botón "Aceptar" clickeado en fila de solicitud desplegada? | S | S | S | S | S | S | S | S |
| C2 | ¿Modalidad de la solicitud es "Virtual"? | S | S | S | S | N | N | N | N |
| C3 | ¿Campo "Enlace de la reunión *" lleno en el modal? | S | N | S | N/A | N/A | N/A | N/A | N/A |
| C4 | ¿Campo "Enlace de la reunión *" es URL válida (https:// o http://)? | S | N/A | N | N/A | N/A | N/A | N/A | N/A |
| C5 | ¿Campo "Lugar de encuentro *" lleno en el modal? | N/A | N/A | N/A | N/A | S | N | S | N/A |
| C6 | ¿Campo "Lugar de encuentro *" tiene al menos 10 caracteres? | N/A | N/A | N/A | N/A | S | N/A | N | N/A |
| C7 | ¿Botón "Confirmar" clickeado en el modal? | S | S | S | N | S | S | S | N |
| C8 | ¿Botón "Cancelar" clickeado en el modal? | N | N | N | S | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | | |
| A1 | Desplegar Modal Confirmar Tutoría (Virtual) | X | X | X | X | | | | |
| A2 | Desplegar Modal Confirmar Tutoría (Presencial) | | | | | X | X | X | X |
| A3 | Mostrar Error Enlace Obligatorio | | X | | | | | | |
| A4 | Mostrar Error Enlace URL Inválida | | | X | | | | | |
| A5 | Mostrar Error Lugar Obligatorio | | | | | | X | | |
| A6 | Mostrar Error Lugar Minimo Caracteres | | | | | | | X | |
| A7 | Cerrar Modal y Volver a Bandeja | | | | X | | | | X |
| A8 | Confirmación Exitosa | X | | | | X | | | |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
* **A1 - Desplegar Modal Confirmar Tutoría (Virtual):** Se despliega la ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** El modal tiene el título "Confirmar Tutoría". Muestra un recuadro informativo con la materia, estudiante, fecha/hora y "Modalidad elegida: Virtual". Se muestra el campo de texto obligatorio "Enlace de la reunión \*" con el texto de ayuda "Zoom, Teams, Meet u otra plataforma" y el placeholder "https://zoom.us/j/...". En la parte inferior, los botones "Cancelar" y "Confirmar".
* **A2 - Desplegar Modal Confirmar Tutoría (Presencial):** Se despliega la ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** El modal tiene el título "Confirmar Tutoría". Muestra un recuadro informativo con la materia, estudiante, fecha/hora y "Modalidad elegida: Presencial". Se muestra el campo de texto obligatorio "Lugar de encuentro \*" con el texto de ayuda "Indica dónde se realizará la tutoría presencial", el placeholder "Ej. Biblioteca Central, Aula 301...", la nota "Mínimo 10 caracteres" y un contador "0/100". En la parte inferior, los botones "Cancelar" y "Confirmar".
* **A3 - Mostrar Error Enlace Obligatorio:** Permanece en el modal. **VALIDACIÓN VISUAL:** Debajo del campo de texto de enlace, se muestra el mensaje de error: "El enlace de reunión es obligatorio.".
* **A4 - Mostrar Error Enlace URL Inválida:** Permanece en el modal. **VALIDACIÓN VISUAL:** Debajo del campo de texto de enlace, se muestra el mensaje de error: "Ingresa una URL válida (debe comenzar con https:// o http://).".
* **A5 - Mostrar Error Lugar Obligatorio:** Permanece en el modal. **VALIDACIÓN VISUAL:** Debajo del campo de texto de lugar, se muestra el mensaje de error: "El lugar de encuentro es obligatorio.".
* **A6 - Mostrar Error Lugar Minimo Caracteres:** Permanece en el modal. **VALIDACIÓN VISUAL:** Debajo del campo de texto de lugar, se muestra el mensaje de error: "Mínimo 10 caracteres para el lugar.".
* **A7 - Cerrar Modal y Volver a Bandeja:** El modal se cierra sin procesar cambios. **VALIDACIÓN VISUAL:** Se regresa a la pantalla "T. Bandeja de Entrada", manteniendo desplegada la solicitud original. No hay alteraciones en los contadores numéricos de las pestañas ni en el estado de la solicitud.
* **A8 - Confirmación Exitosa:** El modal se cierra y el sistema procesa la aceptación. **VALIDACIÓN VISUAL:** Se regresa a la pantalla "T. Bandeja de Entrada". La solicitud recién aceptada desaparece de la lista de la pestaña "Pendientes". El contador numérico de la pestaña "Pendientes" se reduce en uno (ej. de 3 a 2), y el contador de la pestaña "Respondidas" se incrementa en uno. El estado interno de la tutoría pasa a "Aceptada" y se sincroniza en "T. Mi Agenda".

---

### Nro. HU-23 - Título: Rechazar solicitud de tutoría

Descripción: Como tutor, quiero rechazar una solicitud para descartar las tutorías que no me convienen impartir

#### Matriz de Decisión HU-23

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Radio button "Imprevisto personal" o "Conflicto de horarios" o "No es mi área de especialidad" seleccionado? | S | N | N | S | N | N |
| C2 | ¿Radio button "Otro" seleccionado? | N | S | S | N | S | S |
| C3 | ¿Campo de texto "Comentario adicional (opcional)" lleno (cuando C2 es S)? | - | N | S | - | N | S |
| C4 | ¿Botón "Confirmar rechazo" clickeado? | S | S | S | N | N | N |
| C5 | ¿Botón "Cancelar" clickeado? | N | N | N | S | S | S |
| | **ACCIONES** (Usar código corto) | | | | | | |
| A1 | Mostrar Modal 'Rechazar solicitud de tutoría' | X | X | X | X | X | X |
| A2 | Mostrar campo "Comentario adicional (opcional)" | | X | X | | X | X |
| A3 | Habilitar botón "Confirmar rechazo" | X | X | X | X | X | X |
| A4 | Cerrar Modal 'Rechazar solicitud de tutoría' | X | X | X | X | X | X |
| A5 | Mover solicitud a la pestaña "Respondidas" y actualizar contadores | X | X | X | | | |
| A6 | Permanecer en la pantalla 'T. Bandeja de Entrada (Solicitud Pendiente Desplegada)' con la solicitud desplegada | | | | X | X | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

*   **A1 - Mostrar Modal 'Rechazar solicitud de tutoría':** Muestra una ventana modal superpuesta. **VALIDACIÓN VISUAL:** Título "Rechazar solicitud de tutoría", texto "Selecciona el motivo de rechazo", cuatro radio buttons: "Imprevisto personal", "Conflicto de horarios", "No es mi área de especialidad", "Otro". Los radio buttons no están seleccionados inicialmente. Botón "Confirmar rechazo" (deshabilitado) y botón "Cancelar" (habilitado).
*   **A2 - Mostrar campo "Comentario adicional (opcional)":** El modal se expande mostrando un nuevo campo de texto. **VALIDACIÓN VISUAL:** Campo de texto con label "Comentario adicional (opcional)", placeholder "Ingresa tu comentario aquí..." y contador de caracteres "0/300" debajo del campo.
*   **A3 - Habilitar botón "Confirmar rechazo":** El botón para confirmar el rechazo se vuelve interactivo. **VALIDACIÓN VISUAL:** El botón "Confirmar rechazo" cambia su estilo (ej. color o opacidad) para indicar que está habilitado y es clickeable.
*   **A4 - Cerrar Modal 'Rechazar solicitud de tutoría':** La ventana modal desaparece. **VALIDACIÓN VISUAL:** El modal "Rechazar solicitud de tutoría" ya no es visible. La pantalla `T. Bandeja de Entrada (Solicitud Pendiente Desplegada)` es visible con el título "Bandeja de Entrada", subtítulo "Solicitudes de tutoría recibidas" y las pestañas "Pendientes", "Expiradas", "Respondidas".
*   **A5 - Mover solicitud a la pestaña "Respondidas" y actualizar contadores:** La solicitud procesada se archiva y el estado de los contadores de solicitudes se actualiza. **VALIDACIÓN VISUAL:** En la pestaña "Pendientes", la solicitud del estudiante (ej. "Valeria Sánchez") ya no aparece y su contador (ej. "Pendientes (2)") se decrementa. En la pestaña "Respondidas", la solicitud del estudiante (ej. "Valeria Sánchez") ahora es visible y su contador (ej. "Respondidas (13)") se incrementa.
*   **A6 - Permanecer en la pantalla 'T. Bandeja de Entrada (Solicitud Pendiente Desplegada)' con la solicitud desplegada:** La interfaz vuelve al estado anterior a la apertura del modal. **VALIDACIÓN VISUAL:** La pantalla `T. Bandeja de Entrada (Solicitud Pendiente Desplegada)` está visible con el título "Bandeja de Entrada", subtítulo "Solicitudes de tutoría recibidas" y las pestañas "Pendientes (3)", "Expiradas (14)", "Respondidas (12)". La solicitud del estudiante (ej. "Valeria Sánchez") sigue visible en la pestaña "Pendientes" y su detalle está desplegado.

---

### Nro. HU-33 - Título: Ver solicitudes de tutoría enviadas

Descripción: Como estudiante, quiero ver las solicitudes que he enviado para saber qué servicios he solicitado.

#### Matriz de Decisión HU-33

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 | R9 | R10 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Click en la pestaña "Todas"? | S | N | N | N | N | N | N | N | N | N |
| C2 | ¿Click en la pestaña "Pendientes"? | N | S | N | N | N | N | N | N | N | N |
| C3 | ¿Click en la pestaña "Aceptadas"? | N | N | S | N | N | N | N | N | N | N |
| C4 | ¿Click en la pestaña "Rechazadas"? | N | N | N | S | N | N | N | N | N | N |
| C5 | ¿Click en la pestaña "Expiradas"? | N | N | N | N | S | N | N | N | N | N |
| C6 | ¿Click en una tarjeta de solicitud en la lista? | N | N | N | N | N | S | S | S | S | N |
| C7 | ¿Estado de la solicitud clickeada? | - | - | - | - | - | Pend. | Acep. | Rech. | Exp. | - |
| C8 | ¿Cantidad total de solicitudes en la pestaña activa es > 5? | N | N | N | N | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | | | | |
| A1 | Mostrar vista filtrada "Todas" | X | | | | | | | | | |
| A2 | Mostrar vista filtrada "Pendientes" | | X | | | | | | | | |
| A3 | Mostrar vista filtrada "Aceptadas" | | | X | | | | | | | |
| A4 | Mostrar vista filtrada "Rechazadas" | | | | X | | | | | | |
| A5 | Mostrar vista filtrada "Expiradas" | | | | | X | | | | | |
| A6 | Desplegar Modal "Detalle de la Solicitud" (Pendiente) | | | | | | X | | | | |
| A7 | Desplegar Modal "Detalle de la Solicitud" (Aceptada) | | | | | | | X | | | |
| A8 | Desplegar Modal "Detalle de la Solicitud" (Rechazada) | | | | | | | | X | | |
| A9 | Desplegar Modal "Detalle de la Solicitud" (Expirada) | | | | | | | | | X | |
| A10| Mostrar controles de paginación en la parte inferior | | | | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar vista filtrada "Todas":** Permanece en la pantalla "Mis Solicitudes". **VALIDACIÓN VISUAL:** La pestaña "Todas (X)" se muestra activa (fondo azul oscuro con texto blanco). Se visualiza una lista de hasta 5 tarjetas que combinan todos los estados de las solicitudes. Cada tarjeta muestra avatar, materia, tutor, fecha/hora, modalidad, precio y su respectiva etiqueta de estado en la esquina superior derecha.
* **A2 - Mostrar vista filtrada "Pendientes":** Permanece en la pantalla. **VALIDACIÓN VISUAL:** La pestaña "Pendientes (X)" se muestra activa. Se listan hasta 5 tarjetas filtradas. En las tarjetas, la etiqueta de estado es "Pendiente" (texto naranja con ícono de reloj, fondo naranja claro).
* **A3 - Mostrar vista filtrada "Aceptadas":** Permanece en la pantalla. **VALIDACIÓN VISUAL:** La pestaña "Aceptadas (X)" se muestra activa. Se listan hasta 5 tarjetas filtradas. La etiqueta de estado es "Aceptada" (texto negro con ícono de check, fondo gris claro).
* **A4 - Mostrar vista filtrada "Rechazadas":** Permanece en la pantalla. **VALIDACIÓN VISUAL:** La pestaña "Rechazadas (X)" se muestra activa. Se listan hasta 5 tarjetas filtradas. La etiqueta de estado es "Rechazada" (texto gris oscuro con ícono de cruz, fondo gris claro).
* **A5 - Mostrar vista filtrada "Expiradas":** Permanece en la pantalla. **VALIDACIÓN VISUAL:** La pestaña "Expiradas (X)" se muestra activa. Se listan hasta 5 tarjetas filtradas. La tarjeta presenta una franja lateral izquierda color rojo y la etiqueta de estado es "Expirada" (texto rojo con ícono de reloj, fondo rojo claro).
* **A6 - Desplegar Modal "Detalle de la Solicitud" (Pendiente):** Se abre una ventana modal sobre la pantalla actual (NO redirige). **VALIDACIÓN VISUAL:** Modal con título "Detalle de la Solicitud". Muestra resumen de la tutoría y el recuadro "TU MENSAJE". En la parte inferior, se visualiza el botón "Cancelar Solicitud" (el cual se encuentra inactivo para esta versión) y el botón "Cerrar".
* **A7 - Desplegar Modal "Detalle de la Solicitud" (Aceptada):** Se abre una ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** Modal con título "Detalle de la Solicitud". En el bloque del tutor se visualiza la etiqueta "Aceptada". Incluye recuadros adicionales con la confirmación del "LUGAR" o "ENLACE", seguido de "TU MENSAJE". En la parte inferior, botones "Cancelar Tutoría" (texto rojo) y "Cerrar".
* **A8 - Desplegar Modal "Detalle de la Solicitud" (Rechazada):** Se abre una ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** Modal con título "Detalle de la Solicitud". En el bloque del tutor se visualiza la etiqueta "Rechazada". Incluye el recuadro "TU MENSAJE" y, debajo de este, un recuadro gris llamado "MOTIVO DE RECHAZO" con la explicación del tutor. Únicamente incluye el botón "Cerrar".
* **A9 - Desplegar Modal "Detalle de la Solicitud" (Expirada):** Se abre una ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** Modal de solo lectura con la información original de la solicitud. En el bloque del tutor se visualiza la etiqueta "Expirada". Únicamente incluye el botón "Cerrar".
* **A10 - Mostrar controles de paginación en la parte inferior:** La acción se activa si hay más de 5 registros en la pestaña seleccionada. **VALIDACIÓN VISUAL:** Justo debajo de la última tarjeta de la lista, se visualiza una barra de paginación numérica (ej. `< 1 2 3 4 >`) que permite al estudiante navegar entre las diferentes páginas de su historial.

---

### Nro. HU-46 - Título: Ver solicitudes respondidas del tutor

Descripción: Como tutor, quiero ver las solicitudes respondidas para llevar un control de las solicitudes que respondí.

#### Matriz de Decisión HU-46

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: |
| C1 | ¿Click en la pestaña "Respondidas (X)" en la bandeja de entrada? | S | N | N | S |
| C2 | ¿Click en una tarjeta de solicitud con etiqueta "Aceptada"? | N | S | N | N |
| C3 | ¿Click en una tarjeta de solicitud con etiqueta "Rechazada"? | N | N | S | N |
| C4 | ¿Cantidad total de solicitudes en la pestaña activa es > 10? | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | |
| A1 | Mostrar vista filtrada "Respondidas" (Lista) | X | | | X |
| A2 | Desplegar Modal "Detalle de la Solicitud" (Aceptada) | | X | | |
| A3 | Desplegar Modal "Detalle de la Solicitud" (Rechazada) | | | X | |
| A4 | Mostrar controles de paginación en la parte inferior | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar vista filtrada "Respondidas" (Lista):** Permanece en la pantalla "T. Bandeja de Entrada". **VALIDACIÓN VISUAL:** La pestaña "Respondidas (X)" se muestra activa (fondo oscuro, texto blanco). Se visualiza una lista de hasta 10 tarjetas que combinan las solicitudes previamente aceptadas y rechazadas. Cada fila en la lista cuenta con su respectiva etiqueta visual de estado en la columna derecha ("Aceptada" o "Rechazada").
* **A2 - Desplegar Modal "Detalle de la Solicitud" (Aceptada):** Se abre una ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** El modal tiene el título "Detalle de la Solicitud" con ícono de "X" para cerrar. Muestra un recuadro superior con el avatar, nombre del estudiante, rol "Estudiante" y la etiqueta ovalada "Aceptada". Incluye recuadros separados detallando la confirmación de la tutoría (ej. "LUGAR" con su ubicación o enlace), la información base de la materia con fecha, hora y precio por hora (ej. "$10/h"), y el recuadro "MENSAJE DEL ESTUDIANTE" con borde lateral naranja. En la parte inferior derecha, se encuentra únicamente el botón "Cerrar" (sin borde, color de texto azul oscuro).
* **A3 - Desplegar Modal "Detalle de la Solicitud" (Rechazada):** Se abre una ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** El modal tiene el título "Detalle de la Solicitud" con ícono de "X" para cerrar. Muestra el recuadro superior con la información del estudiante y la etiqueta ovalada "Rechazada". Incluye el recuadro de la materia, fecha, hora y precio. No incluye bloque de confirmación (lugar/enlace). Muestra el "MENSAJE DEL ESTUDIANTE" y, directamente debajo de este, un recuadro gris claro titulado "MOTIVO DE RECHAZO" que detalla la razón seleccionada por el tutor (ej. "Otro"). En la parte inferior derecha, se encuentra únicamente el botón "Cerrar".
* **A4 - Mostrar controles de paginación en la parte inferior:** La acción se activa si hay más de 10 registros en el historial de respondidas. **VALIDACIÓN VISUAL:** Justo debajo de la última tarjeta de la lista en la pantalla principal, se visualizan los controles numéricos de paginación para permitir al tutor navegar hacia páginas anteriores o siguientes.

---

### Nro. HU-47 - Título: Ver solicitudes respondidas del estudiante

Descripción: Como estudiante, quiero ver las solicitudes a las que el tutor ya ha dado respuesta (aceptadas o rechazadas) para llevar un control de mi agendamiento.

#### Matriz de Decisión HU-47

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Click en la pestaña "Aceptadas (X)"? | S | N | N | N | N |
| C2 | ¿Click en la pestaña "Rechazadas (X)"? | N | S | N | N | N |
| C3 | ¿Click en una tarjeta de solicitud con etiqueta "Aceptada"? | N | N | S | N | N |
| C4 | ¿Click en una tarjeta de solicitud con etiqueta "Rechazada"? | N | N | N | S | N |
| C5 | ¿Cantidad total de solicitudes en la pestaña activa es > 5? | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | |
| A1 | Mostrar vista filtrada "Aceptadas" (Lista) | X | | | | |
| A2 | Mostrar vista filtrada "Rechazadas" (Lista) | | X | | | |
| A3 | Desplegar Modal "Detalle de la Solicitud" (Aceptada) | | | X | | |
| A4 | Desplegar Modal "Detalle de la Solicitud" (Rechazada) | | | | X | |
| A5 | Mostrar controles de paginación en la parte inferior | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar vista filtrada "Aceptadas" (Lista):** Permanece en la pantalla "Mis Solicitudes". **VALIDACIÓN VISUAL:** La pestaña "Aceptadas (X)" se muestra activa (fondo oscuro, texto blanco). Se visualiza una lista de hasta 5 tarjetas. Cada tarjeta muestra la información del tutor y la tutoría, y en la esquina superior derecha presenta la etiqueta de estado "Aceptada" (texto oscuro con ícono de check, fondo gris claro).
* **A2 - Mostrar vista filtrada "Rechazadas" (Lista):** Permanece en la pantalla "Mis Solicitudes". **VALIDACIÓN VISUAL:** La pestaña "Rechazadas (X)" se muestra activa (fondo oscuro, texto blanco). Se visualiza una lista de hasta 5 tarjetas. Cada tarjeta muestra la información de la tutoría, en la esquina superior derecha presenta la etiqueta de estado "Rechazada" (texto oscuro con ícono de cruz, fondo gris claro), y debajo de los detalles de la tutoría se previsualiza en texto cursivo gris el "Motivo de rechazo: [Razón]".
* **A3 - Desplegar Modal "Detalle de la Solicitud" (Aceptada):** Se abre una ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** El modal tiene el título "Detalle de la Solicitud" con un ícono "X" para cerrar. Muestra un recuadro superior con el avatar, nombre del tutor y la etiqueta "Aceptada". Incluye un recuadro detallando la confirmación de la tutoría (ej. "LUGAR" y el texto "Laboratorio de Química, Edificio B, Piso 2" o "ENLACE" si fuera virtual), un recuadro con la información de la materia, fecha, hora y precio (ej. "$10/h"), y el recuadro "TU MENSAJE" con borde lateral naranja. En la parte inferior, se visualizan dos botones: "Cancelar Tutoría" (texto rojo, acompañado de ícono de papelera) y "Cerrar".
* **A4 - Desplegar Modal "Detalle de la Solicitud" (Rechazada):** Se abre una ventana modal sobre la pantalla actual. **VALIDACIÓN VISUAL:** El modal tiene el título "Detalle de la Solicitud" con un ícono "X" para cerrar. Muestra un recuadro superior con el avatar, nombre del tutor y la etiqueta "Rechazada". Incluye el recuadro con la información de la materia, fecha, hora y precio. Muestra el recuadro "TU MENSAJE" y, directamente debajo de este, un recuadro gris claro titulado "MOTIVO DE RECHAZO" que detalla la razón seleccionada por el tutor (ej. "Falta de tiempo"). En la parte inferior, se encuentra únicamente el botón "Cerrar".
* **A5 - Mostrar controles de paginación en la parte inferior:** La acción se activa si hay más de 5 registros en la pestaña seleccionada. **VALIDACIÓN VISUAL:** Justo debajo de la última tarjeta de la lista en la pantalla principal, se visualizan los controles numéricos de paginación (ej. `< 1 2 3 4 >`) resaltando el número de la página actual en azul oscuro para permitir al estudiante navegar por el historial.
---

### Nro. HU-15 - Título: Ver tutorías agendadas del tutor

Descripción: Como tutor, quiero ver mis tutorías agendadas para recordar cuando tengo que impartir las tutorías

#### Matriz de Decisión HU-15

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Navegación al enlace "Mi Agenda" en la barra superior? | S | N | N | N | N | N | N | N |
| C2 | ¿Número de día en el calendario (con sesiones confirmadas) clickeado? | N | S | N | N | N | N | N | N |
| C3 | ¿Tarjeta de sesión en el panel lateral clickeada? | N | N | S | S | S | N | N | N |
| C4 | ¿Tutoría seleccionada es "Virtual" y estado "Pendiente"? | N | N | S | N | N | N | N | N |
| C5 | ¿Tutoría seleccionada es "Presencial" y estado "Pendiente"? | N | N | N | S | N | N | N | N |
| C6 | ¿Tutoría seleccionada tiene estado "Completada"? | N | N | N | N | S | N | N | N |
| C7 | ¿Botón "Cerrar" en modal de detalle de tutoría completada clickeado? | N | N | N | N | N | S | N | N |
| C8 | ¿Botón "Cerrar" en modal de detalle de tutoría (virtual/presencial pendiente) clickeado? | N | N | N | N | N | N | S | N |
| C9 | ¿Botón "Cancelar tutoría" en modal de detalle de tutoría (virtual/presencial pendiente) clickeado? | N | N | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | | |
| A1 | Mostrar vista principal "Mi Agenda" | X | - | - | - | - | X | X | X |
| A2 | Actualizar panel lateral derecho | - | X | - | - | - | - | - | - |
| A3 | Abrir modal "Detalle Tutoría" Virtual Pendiente | - | - | X | - | - | - | - | - |
| A4 | Abrir modal "Detalle Tutoría" Presencial Pendiente | - | - | - | X | - | - | - | - |
| A5 | Abrir modal "Detalle Tutoría" Completada | - | - | - | - | X | - | - | - |
| A6 | Cerrar modal de tutoría completada | - | - | - | - | - | X | - | - |
| A7 | Cerrar modal de tutoría (virtual/presencial pendiente) | - | - | - | - | - | N | X | N |
| A8 | Iniciar flujo de cancelación de tutoría | - | - | - | - | - | N | N | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

*   **A1 - Mostrar vista principal "Mi Agenda":** Redirige (o permanece en) la pantalla 'T. Mi Agenda' (según mapa N16). **VALIDACIÓN VISUAL:** Se visualiza el título 'Mi Agenda' y subtítulo 'Calendario de sesiones confirmadas'. En la barra de navegación superior se muestran los enlaces 'Panel', 'Bandeja', 'Mi Agenda' (resaltado con fondo amarillo), 'Henry' (con ícono de usuario 'H' en círculo naranja), y 'Salir'. El calendario muestra el mes 'Marzo 2026', flechas de navegación '<' y '>', los encabezados de los días de la semana 'DOM' a 'SÁB', y la cuadrícula de días del mes (del 1 al 31), incluyendo días con sesiones confirmadas (ej: '4: 15:00 Cálculo...', '6: 09:00 Cálculo..., 09:00 Física I, +2 más', '7: 11:00 Álgebra...', '8: 09:00 Cálculo..., 11:00 Física I, +2 más', '15: 10:00 Cálculo...'). El día '9' está resaltado con un círculo morado y el día '15' con un fondo amarillo. El panel lateral derecho muestra el encabezado '15 de Marzo', '1 sesión confirmada', y la tarjeta '10:00 — Cálculo Vectorial', 'Andrés Morales', 'Toca para ver detalles →'. También la sección 'ESTE MES' con 'Sesiones confirmadas 11' (y flecha de expandir/contraer), listando sesiones como '11:00 — Álgebra Lineal', 'Andrés Morales', divisores de día (ej. 'Dom 8' con '4' sesiones) y sus respectivas sesiones, y 'Dom 15' con '1' sesión y su sesión.

*   **A2 - Actualizar panel lateral derecho:** Permanece en la pantalla 'T. Mi Agenda'. **VALIDACIÓN VISUAL:** El panel lateral derecho actualiza su encabezado para mostrar la fecha del día clickeado (ej. '8 de Marzo') y el número de sesiones confirmadas para ese día (ej. '4 sesiones confirmadas'). A continuación, se listan las tarjetas de sesiones confirmadas **exclusivamente para el día seleccionado** (ej. si se clickea el día '8', se muestran las tarjetas: '09:00 — Cálculo Vectorial', 'Sebastián Ríos', '11:00 — Física I', 'Isabella Mora', '14:00 — Álgebra Lineal', 'Lucas Herrera', '16:00 — Estática', 'Camila Flores'). La sección 'ESTE MES' y su listado de sesiones por mes se mantiene visible debajo, si está expandida.

*   **A3 - Abrir modal "Detalle Tutoría" Virtual Pendiente:** Abre un modal (según mapa M7) sobre la pantalla 'T. Mi Agenda'. **VALIDACIÓN VISUAL:** El modal tiene el título '10:00 — Cálculo Vectorial', subtítulo 'Andrés Morales'. Dentro del modal se visualizan los campos: 'Modalidad: Virtual', 'Estado: Pendiente', 'Fecha: 15 de Marzo, 2026', 'ENLACE: meet.google.com/abc-xyz-pqr', 'Estudiante:', y un campo de texto multi-línea 'Mensaje:'. En la parte inferior se muestran los botones 'Cancelar tutoría' (a la izquierda) y 'Cerrar' (a la derecha).

*   **A4 - Abrir modal "Detalle Tutoría" Presencial Pendiente:** Abre un modal (según mapa M7) sobre la pantalla 'T. Mi Agenda'. **VALIDACIÓN VISUAL:** El modal tiene el título '10:00 — Cálculo Vectorial', subtítulo 'Andrés Morales'. Dentro del modal se visualizan los campos: 'Modalidad: Presencial', 'Estado: Pendiente', 'Fecha: 15 de Marzo, 2026', 'LUGAR: Carrera 43 # 12-34, Bogotá', 'Estudiante:', y un campo de texto multi-línea 'Mensaje:'. En la parte inferior se muestran los botones 'Cancelar tutoría' (a la izquierda) y 'Cerrar' (a la derecha).

*   **A5 - Abrir modal "Detalle Tutoría" Completada:** Abre un modal (según mapa M7) sobre la pantalla 'T. Mi Agenda'. **VALIDACIÓN VISUAL:** El modal muestra un mensaje superior indicando: 'Tutoría completada. Esta tutoría ya se realizó. Solo puedes ver los detalles.' y únicamente el botón 'Cerrar' en la parte inferior.

*   **A6 - Cerrar modal de tutoría completada:** Cierra el modal de detalle de tutoría completada. **VALIDACIÓN VISUAL:** Se regresa a la pantalla 'T. Mi Agenda' con la vista de calendario mensual y el panel lateral derecho mostrando el estado previo (ej. el resumen de sesiones del día o del mes) antes de la apertura del modal.

*   **A7 - Cerrar modal de tutoría (virtual/presencial pendiente):** Cierra el modal de detalle de tutoría virtual o presencial pendiente. **VALIDACIÓN VISUAL:** Se regresa a la pantalla 'T. Mi Agenda' con la vista de calendario mensual y el panel lateral derecho mostrando el estado previo (ej. el resumen de sesiones del día o del mes) antes de la apertura del modal.

*   **A8 - Iniciar flujo de cancelación de tutoría:** Inicia el proceso de cancelación de la tutoría. **VALIDACIÓN VISUAL:** Se cierra el modal actual y (según descripción) "levanta una alerta destructiva exigiendo la selección de un motivo", que indica la apertura de un nuevo modal o un cambio de vista para gestionar la cancelación con motivo justificado. Una vez completado este flujo, se regresa a la pantalla 'T. Mi Agenda'.

---

### Nro. HU-11 - Título: Ver tutorías agendadas del estudiante

Descripción: Como estudiante, quiero ver mis tutorías agendadas para recordar cuando tengo que asistir las tutorías

#### Matriz de Decisión HU-11

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 |
| :-- | :--- | :-: | :-: | :-: | :-: |
| C1 | ¿Usuario navega a 'Agenda' desde el menú superior? | S | N | N | N |
| C2 | ¿Tarjeta de tutoría 'PRÓXIMA' clickeada en 'E. Agenda'? | N | S | S | N |
| C3 | ¿La tutoría clickeada es de modalidad 'Virtual'? | - | S | N | - |
| C4 | ¿Botón 'Cerrar' clickeado en el modal de detalle de tutoría? | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | |
| A1 | Mostrar 'E. Agenda' | X | | | X |
| A2 | Mostrar Modal 'E. Agenda (Detalle Tutoría Próxima)' (Virtual) | | X | | |
| A3 | Mostrar Modal 'E. Agenda (Detalle Tutoría Próxima)P' (Presencial) | | | X | |
| A4 | Cerrar Modal de detalle de tutoría | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

*   **A1 - Mostrar 'E. Agenda':** Redirige a la pantalla 'E. Agenda' (según mapa). **VALIDACIÓN VISUAL:** Se visualiza la barra de navegación superior con el 'Poli Tutorías' logo y los textos 'Explorar', 'Mis Solicitudes', 'Agenda' (subrayado). A la derecha, se muestra 'P Patricio' y 'Salir'. El contenido principal incluye el título 'Tutorías Agendadas' y el subtítulo 'Lista cronológica de tus sesiones confirmadas'. Se muestran dos secciones principales:
    *   **Sección 'PRÓXIMAS (3)':** Contiene tres tarjetas de tutoría. Cada tarjeta incluye: un bloque de calendario con el mes (ej. 'MAR') y el día (ej. '15'), el título de la materia (ej. 'Cálculo Vectorial'), la hora (ej. '10:00'), un mini avatar seguido del nombre del tutor (ej. 'Juan Pérez'), y la fecha completa (ej. 'Domingo, 15 de marzo de 2026').
    *   **Sección 'ANTERIORES (7)':** Contiene tres tarjetas de tutoría visibles en un tono gris claro. Cada tarjeta incluye: un bloque de calendario con el mes (ej. 'MAR') y el día (ej. '8'), el título de la materia (ej. 'Programación Básica'), la hora (ej. '09:00'), un mini avatar seguido del nombre del tutor (ej. 'María López'), la fecha completa (ej. 'Domingo, 8 de marzo de 2026'), y una etiqueta 'COMPLETADA' en el lado derecho. Debajo de estas tarjetas, se encuentra un botón con el texto 'Ver todas las anteriores (4 más)' y un icono de flecha hacia abajo.

*   **A2 - Mostrar Modal 'E. Agenda (Detalle Tutoría Próxima)' (Virtual):** Permanece en la misma pantalla 'E. Agenda' con un modal superpuesto. **VALIDACIÓN VISUAL:** Se despliega un modal titulado 'Cálculo Vectorial'. Dentro del modal se muestran los siguientes detalles: Fecha 'Domingo, 15 de marzo de 2026', Hora '10:00', Tarifa '$20.000 COP/hora', Modalidad 'Virtual'. Una sección con el título 'ENLACE' y el texto 'meet.google.com/abc-xyz-123'. Una sección con el título 'Mensaje' y el texto 'Necesito refuerzo en integrales triples y series de Fourier.'. En la parte inferior del modal, se visualizan dos botones: 'Cancelar Tutoría' (en color rojo) y 'Cerrar'.

*   **A3 - Mostrar Modal 'E. Agenda (Detalle Tutoría Próxima)P' (Presencial):** Permanece en la misma pantalla 'E. Agenda' con un modal superpuesto. **VALIDACIÓN VISUAL:** Se despliega un modal titulado 'Química Orgánica'. Dentro del modal se muestran los siguientes detalles: Fecha 'Jueves, 2 de abril de 2026', Hora '11:00', Tarifa '$20.000 COP/hora', Modalidad 'Presencial'. Una sección con el título 'LUGAR' y el texto 'Laboratorio de Química, Edificio B, Piso 2'. Una sección con el título 'Mensaje' y el texto 'Necesito repasar los mecanismos de reacción para SN1 y SN2.'. En la parte inferior del modal, se visualizan dos botones: 'Cancelar Tutoría' (en color rojo) y 'Cerrar'.

*   **A4 - Cerrar Modal de detalle de tutoría:** Cierra el modal de detalle de tutoría (A2 o A3). **VALIDACIÓN VISUAL:** El modal desaparece de la vista. La pantalla 'E. Agenda' se muestra completamente, con todos los elementos descritos en la acción A1 visible de nuevo.