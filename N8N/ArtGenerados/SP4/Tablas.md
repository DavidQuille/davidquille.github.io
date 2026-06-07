# Reporte de Tablas
> Generado el: 23/3/2026

### Nro. HU-39 - Título: Ver historial de tutorías impartidas

Descripción: Como tutor, quiero ver mi historial de tutorías impartidas para tener un registro de mi experiencia profesional

#### Matriz de Decisión HU-39

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Opción de menú "Historial" es clicada? | S | S | S | S | S |
| C2 | ¿Hay más de 5 tarjetas de tutoría disponibles en el historial? | N | S | S | S | - |
| C3 | ¿Un número de página en los controles de paginación (ej. '2') es clicado? | N | N | S | N | N |
| C4 | ¿Un control de flecha de paginación ('<' o '>') es clicado? | N | N | N | S | N |
| C5 | ¿Una tarjeta de tutoría individual es clicada? | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | |
| A1 | Ir a T. Historial | X | X | | | |
| A2 | Mostrar nueva página de tutorías | | | X | X | |
| A3 | Mostrar Modal Detalle Tutoría | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
* **A1 - Ir a T. Historial:** "Redirige a la pantalla 'T. Historial de Tutorías' (según mapa). **VALIDACIÓN VISUAL:** Se visualiza el logo 'Poli Tutorias' y el menú de navegación superior con las opciones 'Panel', 'Bandeja', 'Mi Agenda', 'Historial' (resaltada con un fondo oscuro y texto blanco, indicando la página actual), 'Reseñas', un icono de usuario con el texto 'J Juan' y el texto 'Salir'. El título principal 'Historial de Tutorías Impartidas' y el subtítulo 'Registro de todas tus sesiones pasadas' están presentes. Se muestran tres métricas estáticas en la parte superior: '9 Tutorías completadas' (acompañada de un ícono de check verde), '4 Materias impartidas' (acompañada de un ícono de libro) y '89% Estudiantes que califican' (acompañada de un ícono de estrella). Debajo, se carga un listado de tarjetas de tutorías, mostrando un máximo de 5 por vista. Cada tarjeta presenta las iniciales del estudiante en un círculo (ej. 'MV', 'AM', 'CR'), el nombre de la materia (ej. 'Cálculo Vectorial', 'Álgebra Lineal'), el nombre del estudiante (ej. 'Mateo Vargas', 'Andrés Morales', 'Camila Rodríguez'), y la fecha y hora de la sesión (ej. '22 de marzo de 2026 a las 09:00'). Los botones 'Completada' (con check verde) e 'Inasistencia' (con cruz roja) son visibles en cada tarjeta, pero no son funcionales para esta HU. Los controles de paginación ('<', '1' (resaltado), '2', '3', '4', '5', '6', '>') son visibles en la parte inferior de la pantalla si hay más de 5 tutorías."
* **A2 - Mostrar nueva página de tutorías:** "Permanece en la pantalla 'T. Historial de Tutorías'. **VALIDACIÓN VISUAL:** El listado de tarjetas de tutorías se actualiza para mostrar las 5 tutorías correspondientes a la página seleccionada. El número de página o el control de flecha de paginación correspondiente a la acción clicada se resalta, indicando la nueva página activa (ej. el número '2' se resalta si se hizo clic en '2')."
* **A3 - Mostrar Modal Detalle Tutoría:** "Despliega una ventana modal (correspondiente a la pantalla 'T. Historial (Detalle Tutoría sin Confirmar)' según el proceso) sobre la pantalla 'T. Historial de Tutorías'. **VALIDACIÓN VISUAL:** El modal se superpone a la pantalla principal, atenuándola ligeramente. Muestra la información detallada de la sesión seleccionada, incluyendo si la tutoría fue virtual o presencial, y cualquier otro dato relevante de la sesión. No se visualizan los botones 'Completada' ni 'Inasistencia' dentro de esta modal (según observaciones técnicas y descripción del proceso)."

---

### Nro. HU-43 - Título: Registrar la tutoría completada

Descripción: Como tutor, quiero registrar que la tutoría ha sido completada para mantener mi historial actualizado y recibir el pago

#### Matriz de Decisión HU-43

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Tarjeta de tutoría en pantalla 'Historial de Tutorías Impartidas' en estado "sin confirmar"? | S | S | S | N | N |
| C2 | ¿Tarjeta de tutoría en pantalla 'Historial de Tutorías Impartidas' en estado "Completada"? | N | N | N | S | S |
| C3 | ¿Clic en botón 'Completada' en la tarjeta de la pantalla 'Historial de Tutorías Impartidas'? | S | N | N | N | N |
| C4 | ¿Clic en el área general de la tarjeta de la pantalla 'Historial de Tutorías Impartidas'? | N | S | S | S | S |
| C5 | ¿Clic en botón 'Completada' dentro del modal de "Detalle Tutoría sin Confirmar"? | N | N | S | N | N |
| C6 | ¿Clic en botón 'Cerrar' dentro del modal de "Detalle Tutoría Completada (SR)"? | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | |
| A1 | Actualizar Tarjeta a Estado Completada (Directo) | X | | | | |
| A2 | Abrir Modal "Detalle Tutoría sin Confirmar" | | X | | | |
| A3 | Actualizar Tarjeta a Estado Completada (Desde Modal) | | | X | | |
| A4 | Abrir Modal "Detalle Tutoría Completada (SR)" | | | | X | |
| A5 | Cerrar Modal "Detalle Tutoría Completada (SR)" | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
* **A1 - Actualizar Tarjeta a Estado Completada (Directo):** Permanece en la misma pantalla `Historial de Tutorías Impartidas`. **VALIDACIÓN VISUAL:** La tarjeta de la tutoría específica en el listado de la pantalla 'Historial de Tutorías Impartidas' se actualiza. Los botones 'Completada' (verde) e 'Inasistencia' (rojo) **desaparecen**. En su lugar, la tarjeta muestra una etiqueta verde con el texto 'Completada' y un icono de cheque (según la descripción del estado 'T.completado' y visible en tarjetas sin botones en la imagen `T. Historial.png`).
* **A2 - Abrir Modal "Detalle Tutoría sin Confirmar":** Permanece en la pantalla `Historial de Tutorías Impartidas`. **VALIDACIÓN VISUAL:** Se despliega una ventana modal (referida en la descripción como `T. Historial (Detalle Tutoría sin Confirmar)`). El modal contendrá un título genérico 'Detalle de la Tutoría', información de la tutoría (ej. 'Cálculo Vectorial', 'Mateo Vargas', '22 de marzo de 2026 a las 09:00' – datos de la primera tarjeta en `T. Historial.png`), y los botones 'Completada' (verde) e 'Inasistencia' (rojo) en la parte inferior, tal como se describe para el flujo de acción desde el detalle.
* **A3 - Actualizar Tarjeta a Estado Completada (Desde Modal):** La ventana modal (referida en la descripción como `T. Historial (Detalle Tutoría sin Confirmar)`) se cierra automáticamente (según la `Descripción del Proceso`). Permanece en la misma pantalla `Historial de Tutorías Impartidas`. **VALIDACIÓN VISUAL:** La ventana modal desaparece. La tarjeta de la tutoría específica en el listado de la pantalla 'Historial de Tutorías Impartidas' se actualiza. Los botones 'Completada' e 'Inasistencia' **desaparecen**. En su lugar, la tarjeta muestra una etiqueta verde con el texto 'Completada' y un icono de cheque (según la descripción del estado 'T.completado' y visible en tarjetas sin botones en la imagen `T. Historial.png`).
* **A4 - Abrir Modal "Detalle Tutoría Completada (SR)":** Permanece en la pantalla `Historial de Tutorías Impartidas`. **VALIDACIÓN VISUAL:** Se despliega una ventana modal (referida en la descripción como `T.completadoSR`). El modal contendrá un título genérico 'Detalle de la Tutoría', información de la tutoría (ej. 'Cálculo Vectorial', 'Andrés Morales', '15 de marzo de 2026 a las 10:00' – datos de la última tarjeta en `T. Historial.png`). En la parte inferior izquierda se visualiza el texto estático "Estado: [Icono de cheque] Completada". Los botones de acción ('Completada' e 'Inasistencia') **no están disponibles**. El único botón habilitado es 'Cerrar'.
* **A5 - Cerrar Modal "Detalle Tutoría Completada (SR)":** La ventana modal (referida en la descripción como `T.completadoSR`) se cierra. Permanece en la misma pantalla `Historial de Tutorías Impartidas`. **VALIDACIÓN VISUAL:** La ventana modal desaparece. La pantalla 'Historial de Tutorías Impartidas' se mantiene visible con la tarjeta de la tutoría en el estado 'Completada' (etiqueta verde con texto 'Completada' y icono de cheque).

---

### Nro. HU-48 - Título: Registrar inasistencia del estudiante

Descripción: Como tutor, quiero registrar la inasistencia de un estudiante para proteger mi tiempo y evitar pérdidas económicas.

#### Matriz de Decisión HU-48

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Clic en botón 'Inasistencia' en la tarjeta de `T. Historial`? | S | N | N | N | N | N | N |
| C2 | ¿Clic en área general de tarjeta en estado "Sin confirmar"? | N | S | N | N | N | N | N |
| C3 | ¿Clic en botón 'Inasistencia' dentro del modal de detalle? | N | N | S | N | N | N | N |
| C4 | ¿Clic en 'Cancelar' en el modal `Confirmar Inasistencia`? | N | N | N | S | N | N | N |
| C5 | ¿Clic en 'Sí, reportar inasistencia' en modal de confirmación? | N | N | N | N | S | N | N |
| C6 | ¿Clic en área general de tarjeta con estado "Inasistencia"? | N | N | N | N | N | S | N |
| C7 | ¿Clic en 'Cerrar' en cualquier modal de Detalle de Tutoría? | N | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | |
| A1 | Mostrar Modal 'Confirmar Inasistencia' (T.IM) | X | | X | | | | |
| A2 | Desplegar Modal 'Detalle Tutoría sin Confirmar' | | X | | | | | |
| A3 | Cerrar Modal de Confirmación (Regresar a vista previa) | | | | X | | | |
| A4 | Actualizar Tarjeta a estado 'Inasistencia' | | | | | X | | |
| A5 | Desplegar Modal 'Detalle Tutoría con Inasistencia' (SR) | | | | | | X | |
| A6 | Cerrar Modal Detalle y volver a 'T. Historial' | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar Modal 'Confirmar Inasistencia' (T.IM):** Se superpone una ventana de advertencia sobre la interfaz actual. 
**VALIDACIÓN VISUAL:** Se visualiza un modal con el título "Confirmar Inasistencia", un ícono de advertencia rojo, y el texto explicativo "¿Estás seguro? Esta acción marcará la tutoría como inasistencia del estudiante. Esta acción no se puede deshacer.". En la parte inferior, contiene los botones "Cancelar" (borde gris) y "Sí, reportar inasistencia" (borde y texto rojo).

* **A2 - Desplegar Modal 'Detalle Tutoría sin Confirmar':** Se abre una ventana modal sobre la pantalla `T. Historial`. 
**VALIDACIÓN VISUAL:** Muestra el título "Detalle de la Tutoría" y la información completa de la sesión (Materia, Estudiante, Fecha, Hora, Modalidad, Precio, Lugar/Enlace y Mensaje del estudiante). En la parte inferior, se visualizan los botones interactivos "Completada" (borde verde), "Inasistencia" (borde rojo) y el botón de texto "Cerrar".

* **A3 - Cerrar Modal de Confirmación (Regresar a vista previa):** La ventana de advertencia `T.IM` se cierra sin realizar cambios. 
**VALIDACIÓN VISUAL:** El modal de advertencia desaparece. El usuario regresa exactamente a la interfaz previa desde donde originó la acción (ya sea la vista general del listado `T. Historial` o el modal abierto de `Detalle de la Tutoría`).

* **A4 - Actualizar Tarjeta a estado 'Inasistencia':** Se registra la acción en el sistema, cerrando los modales abiertos y actualizando la UI principal. 
**VALIDACIÓN VISUAL:** Al regresar al listado `T. Historial`, la tarjeta de la sesión correspondiente se actualiza. Los botones interactivos de acción desaparecen y, en su lugar, la tarjeta muestra una etiqueta estática con contorno rojo, ícono de "X" y el texto "Inasistencia" (estado `T.HistorialIN`).

* **A5 - Desplegar Modal 'Detalle Tutoría con Inasistencia' (SR):** Se abre una ventana modal de solo lectura sobre la pantalla actual. 
**VALIDACIÓN VISUAL:** Muestra la información de la sesión original. Los botones de acción ("Completada" e "Inasistencia") no se visualizan. En la esquina inferior izquierda se muestra el texto estático "Estado: [Ícono X rojo] Inasistencia". El único control interactivo disponible es el botón "Cerrar".

* **A6 - Cerrar Modal Detalle y volver a 'T. Historial':** Cierra el modal de detalle activo. 
**VALIDACIÓN VISUAL:** La ventana modal desaparece y el sistema muestra nuevamente la vista principal del listado en la pantalla `T. Historial`, sin ninguna alteración en el estado previo de las tarjetas.

---

### Nro. HU-40 - Título: Ver historial de tutorías recibidas

Descripción: Como estudiante, quiero ver mi historial de tutorías recibidas para recordar tutores anteriores y revisar mi progreso

#### Matriz de Decisión HU-40

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Opción "Historial" del menú superior clickeada? | S | N | N | N | N | N | N |
| C2 | ¿Tarjeta de tutoría con estado "Completada" clickeada? | N | S | N | N | N | N | N |
| C3 | ¿Botón "Cerrar" del modal "Detalle de tutoría" clickeado? | N | N | S | N | N | N | N |
| C4 | ¿Tarjeta de tutoría con mensaje "El tutor reportó inasistencia para esta sesión" clickeada? | N | N | N | S | N | N | N |
| C5 | ¿Número de página ('2', '3', '4', '5') de la paginación clickeado? | N | N | N | N | S | N | N |
| C6 | ¿Control de paginación '>' clickeado? | N | N | N | N | N | S | N |
| C7 | ¿Control de paginación '<' clickeado? | N | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | |
| A1 | Mostrar Pantalla E. Historial | X | | | | | | |
| A2 | Mostrar Modal Detalle Tutoría Completada | | X | | | | | |
| A3 | Ocultar Modal Detalle Tutoría | | | X | | | | |
| A4 | Mostrar Modal Detalle Tutoría Inasistencia | | | | X | | | |
| A5 | Actualizar Listado de Tutorías | | | | | X | X | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
*   **A1 - Mostrar Pantalla E. Historial:** Redirige a la pantalla "E. Historial de Tutorías" (según mapa). **VALIDACIÓN VISUAL:** Se visualiza el logo "Poli Tutorías" en la esquina superior izquierda. La barra de navegación superior muestra las opciones "Explorar", "Mis Solicitudes", "Agenda", "Historial" (resaltada), "Patricio" con icono de perfil y "Salir". El título principal de la pantalla es "Historial de Tutorías" con el subtítulo "Tutorías que has recibido y calificado". Se muestra un listado de tarjetas de tutorías. Las tarjetas de tutorías con estado "Completada" muestran un label verde "Completada". Las tarjetas de tutorías con estado "Inasistencia" muestran un recuadro rojo con el texto "El tutor reportó inasistencia para esta sesión". Los controles de paginación "<", "1", "2", "3", "4", "5", ">" se muestran en la parte inferior. *Se descartan los elementos "Ordenar:" y "Estado:" según Observaciones Técnicas.*
*   **A2 - Mostrar Modal Detalle Tutoría Completada:** Muestra un modal superpuesto a la pantalla "E. Historial". **VALIDACIÓN VISUAL:** Se visualiza un modal con los detalles de la tutoría, incluyendo campos como "Materia:", "Tutor:", "Fecha:", "Hora:", "Duración:". El "Estado:" se muestra como "Completada". En la parte inferior del modal se visualiza un botón "Cerrar". *No se visualiza el botón "Calificar" ni estrellas de calificación, según Observaciones Técnicas.*
*   **A3 - Ocultar Modal Detalle Tutoría:** Oculta el modal de detalle de tutoría. **VALIDACIÓN VISUAL:** La pantalla "E. Historial" vuelve a ser completamente visible, mostrando el listado de tarjetas de tutorías y los controles de paginación, sin ningún modal superpuesto.
*   **A4 - Mostrar Modal Detalle Tutoría Inasistencia:** Muestra un modal superpuesto a la pantalla "E. Historial". **VALIDACIÓN VISUAL:** Se visualiza un modal con los detalles de la tutoría, incluyendo campos como "Materia:", "Tutor:", "Fecha:", "Hora:", "Duración:". El "Estado:" se muestra como "Inasistencia". En la parte inferior del modal se visualiza un botón "Cerrar".
*   **A5 - Actualizar Listado de Tutorías:** Permanece en la pantalla "E. Historial". **VALIDACIÓN VISUAL:** El listado de tarjetas de tutorías se actualiza para mostrar los registros correspondientes a la página seleccionada. El número de página actualmente activa se resalta con un fondo oscuro (ej. "1" o "2").

---

### Nro. HU-10 - Título: Dejar reseña a tutor

Descripción: Como estudiante, quiero dejar una reseña a un tutor para compartir mi experiencia con otros estudiantes

#### Matriz de Decisión HU-10

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Estudiante hace clic en botón oscuro "Calificar" (en 'E.Hcomp' o en 'E. Historial (Detalle Tutoría Completada)')? | S | N | N | N | N | N |
| C2 | ¿Estudiante selecciona de 1 a 5 estrellas en 'E. Historial (Calificar Tutoría)' modal? | N | S | S | N | S/N | N |
| C3 | ¿Estudiante ingresa texto en campo 'Deja un comentario (opcional):' en 'E. Historial (Calificar Tutoría)' modal? | N | S | N | S | S/N | N |
| C4 | ¿Estudiante hace clic en botón 'Enviar Reseña' en 'E. Historial (Calificar Tutoría)' modal? | N | S | S | N | N | N |
| C5 | ¿Estudiante hace clic en botón 'Cancelar' en 'E. Historial (Calificar Tutoría)' modal? | N | N | N | N | S | N |
| C6 | ¿Estudiante hace clic sobre área general de la tarjeta 'E. calificaComp'? | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | |
| A1 | Mostrar modal 'E. Historial (Calificar Tutoría)' | X | | | | | |
| A2 | Botón 'Enviar Reseña' está habilitado | | X | X | | | |
| A3 | Botón 'Enviar Reseña' está deshabilitado | X | | | X | | |
| A4 | Cerrar modal 'E. Historial (Calificar Tutoría)' | | X | X | | X | |
| A5 | Mostrar mensaje temporal de éxito | | X | X | | | |
| A6 | Actualizar tarjeta de sesión en listado principal a 'E. calificaComp' | | X | X | | | |
| A7 | Mostrar modal 'E. Historial (Detalle Tutoría Calificada)' | | | | | | X |
| A8 | Regresar a pantalla/modal anterior | | X | X | X | X | |
| A9 | Botón 'Cerrar' habilitado en 'E. Historial (Detalle Tutoría Calificada)' modal | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

*   **A1 - Mostrar modal 'E. Historial (Calificar Tutoría)':**
    *   **ACCIÓN DE FLUJO:** El sistema despliega el modal "Calificar Tutoría" sobre la pantalla actual (ya sea 'E. Historial' o 'E. Historial (Detalle Tutoría Completada)').
    *   **VALIDACIÓN VISUAL DETALLADA:** Se visualiza un modal centrado con el título "Calificar Tutoría". Contiene el texto "Califica tu experiencia con el tutor:", un conjunto de 5 estrellas (inicialmente sin selección), el texto "Deja un comentario (opcional):", un campo de texto (textarea), y dos botones en la parte inferior: "Enviar Reseña" y "Cancelar". El botón "Enviar Reseña" se muestra deshabilitado (gris claro). (Referencia `E. Historial (Calificar Tutoría).png`).
    *   **CONTEXTO MAPA:** Representado por `M9: Modal Dejar Reseña`.

*   **A2 - Botón 'Enviar Reseña' está habilitado:**
    *   **ACCIÓN DE FLUJO:** El botón 'Enviar Reseña' cambia su estado.
    *   **VALIDACIÓN VISUAL DETALLADA:** El botón "Enviar Reseña" dentro del modal "Calificar Tutoría" se visualiza habilitado (cambia de gris claro a un color más oscuro, indicando que es cliqueable).

*   **A3 - Botón 'Enviar Reseña' está deshabilitado:**
    *   **ACCIÓN DE FLUJO:** El botón 'Enviar Reseña' mantiene o cambia su estado.
    *   **VALIDACIÓN VISUAL DETALLADA:** El botón "Enviar Reseña" dentro del modal "Calificar Tutoría" se visualiza deshabilitado (en gris claro).

*   **A4 - Cerrar modal 'E. Historial (Calificar Tutoría)':**
    *   **ACCIÓN DE FLUJO:** El modal de calificación es removido de la vista.
    *   **VALIDACIÓN VISUAL DETALLADA:** El modal con el título "Calificar Tutoría" desaparece de la pantalla.
    *   **CONTEXTO MAPA:** Implícito en la transición de `M9` de vuelta a `N19` (`E. Historial de Tutorías`).

*   **A5 - Mostrar mensaje temporal de éxito:**
    *   **ACCIÓN DE FLUJO:** El sistema despliega una notificación de confirmación.
    *   **VALIDACIÓN VISUAL DETALLADA:** Un mensaje de confirmación temporal (ej. toast o snackbar) aparece en la interfaz con el texto exacto: "Reseña enviada. Gracias por calificar tu tutoría.".

*   **A6 - Actualizar tarjeta de sesión en listado principal a 'E. calificaComp':**
    *   **ACCIÓN DE FLUJO:** El sistema refresca la representación de la tutoría en el historial del estudiante.
    *   **VALIDACIÓN VISUAL DETALLADA:** La tarjeta de la tutoría correspondiente en la pantalla 'E. Historial' se actualiza automáticamente. El botón oscuro "Calificar" desaparece. En su lugar, se muestran las estrellas seleccionadas por el estudiante y el comentario ingresado (si lo hubo). La etiqueta de estado verde "Completada" permanece visible. (Referencia `E.calificaComp.png`).

*   **A7 - Mostrar modal 'E. Historial (Detalle Tutoría Calificada)':**
    *   **ACCIÓN DE FLUJO:** El sistema despliega un modal de solo lectura para la tutoría calificada.
    *   **VALIDACIÓN VISUAL DETALLADA:** Se despliega un modal centrado con el título "Detalle de la Tutoría". Contiene la información general de la sesión y, en la parte inferior, una sección "Tu Reseña" con las estrellas otorgadas y el comentario redactado. Solo se visualiza un botón "Cerrar" en la parte inferior. Esta vista es de solo lectura. (Referencia `E. Historial (Detalle Tutoría Calificada).png`).

*   **A8 - Regresar a la pantalla o modal anterior:**
    *   **ACCIÓN DE FLUJO:** El usuario es redirigido a la vista previa.
    *   **VALIDACIÓN VISUAL DETALLADA (Caso R2, R3 - Envío exitoso):** La pantalla 'E. Historial' se visualiza nuevamente.
    *   **VALIDACIÓN VISUAL DETALLADA (Caso R4 - Intento de envío inválido):** El modal 'E. Historial (Calificar Tutoría)' permanece abierto y visible en la pantalla.
    *   **VALIDACIÓN VISUAL DETALLADA (Caso R5 - Cancelación):** Se regresa a la pantalla 'E. Historial' o al modal 'E. Historial (Detalle Tutoría Completada)', dependiendo de la vista desde la cual se invocó el modal de calificación.

*   **A9 - Botón 'Cerrar' habilitado en 'E. Historial (Detalle Tutoría Calificada)' modal:**
    *   **ACCIÓN DE FLUJO:** El botón de cierre en el modal de detalle de tutoría calificada está interactuable.
    *   **VALIDACIÓN VISUAL DETALLADA:** El botón con el texto "Cerrar" en la parte inferior del modal "Detalle de la Tutoría" (para tutorías calificadas) se visualiza habilitado y es cliqueable.

**Nota de Proceso conjunto: Visualización de tutoría calificada por el estudiante (Integración T. Historial)** * **Condición de visualización:** La pantalla `T. Historial (Detalle Tutoría Confirmada)`, correspondiente a la vista del tutor, se mostrará **única y exclusivamente** después de que el estudiante haya realizado y enviado la calificación de una tutoría en estado "Completada". * Mientras el estudiante no envíe su reseña, el tutor únicamente visualizará su tarjeta con la etiqueta de estado "Completada" normal. * Una vez que el sistema registre la calificación y el comentario del estudiante, la tarjeta en el historial del tutor se actualizará automáticamente en la base de datos. Al hacer clic sobre ella, el tutor podrá acceder al detalle completo de la retroalimentación mediante el modal `T. Historial (Detalle Tutoría Confirmada)`. (Este flujo influye a la HU43)

---

### Nro. HU-24 - Título: Cancelar tutoría agendada por tutor

Descripción: Como tutor, quiero cancelar una tutoría agendada para informar al estudiante sobre un imprevisto.

#### Matriz de Decisión HU-24

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Clic en el botón rojo 'Cancelar Tutoría' en `T. Mi Agenda (Detalle Tutoría)`? | S | N | N | N | N | N | N |
| C2 | ¿Selección de un motivo predefinido (ej. "Imprevisto personal")? | N | S | N | N | N | N | N |
| C3 | ¿Selección del radio button "Otro"? | N | N | S | S | S | N | N |
| C4 | ¿Ingresa texto en "Comentario adicional (opcional)" (si C3 es S)? | N/A | N/A | S | N | N/A| N/A | N/A |
| C5 | ¿Clic en el botón 'Volver' en el modal de cancelación? | N | N | N | N | S | N | N |
| C6 | ¿Clic en el botón 'Sí, cancelar tutoría'? | N | S | S | S | N | N | N |
| C7 | ¿Estudiante hace clic en tarjeta cancelada en su pantalla `E. Historial`? | N | N | N | N | N | S | N |
| C8 | ¿Estudiante hace clic en 'Cerrar' en el modal `E.HCancelT`? | N | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | |
| A1 | Desplegar modal 'Cancelar Tutoría' | X | | | | | | |
| A2 | Mostrar campo de texto 'Comentario adicional (opcional)' | | | X | X | X | | |
| A3 | Procesar cancelación (Motivo predefinido) y actualizar vistas | | X | | | | | |
| A4 | Procesar cancelación (Motivo "Otro" con texto) y actualizar vistas | | | X | | | | |
| A5 | Procesar cancelación (Motivo "Otro" sin texto) y actualizar vistas | | | | X | | | |
| A6 | Cerrar modal y regresar a 'Detalles de la Sesión' (Tutor) | | | | | X | | |
| A7 | Desplegar modal `E.HCancelT` ("Detalle de la Tutoría" Cancelada) | | | | | | X | |
| A8 | Cerrar modal `E.HCancelT` y regresar a `E. Historial` (Estudiante) | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Desplegar modal 'Cancelar Tutoría':** Se superpone un segundo modal de advertencia en la pantalla del tutor. 
**VALIDACIÓN VISUAL:** Se visualiza un modal con el título "Cancelar Tutoría", la advertencia en rojo "¿Cancelar esta tutoría? El estudiante será notificado...", y la lista de radio buttons para el "Motivo de la cancelación". Los botones inferiores son "Volver" y "Sí, cancelar tutoría".

* **A2 - Mostrar campo de texto 'Comentario adicional (opcional)':** El modal actual del tutor se expande dinámicamente. 
**VALIDACIÓN VISUAL:** Al seleccionar "Otro", aparece inmediatamente un campo de texto con la etiqueta "Comentario adicional (opcional)" y límite de caracteres.

* **A3 - Procesar cancelación (Motivo predefinido) y actualizar vistas:** El sistema ejecuta la cancelación usando una opción estándar. 
**VALIDACIÓN VISUAL (TUTOR):** Se cierra el modal, muestra el mensaje de éxito "Tutoría cancelada. La sesión ha sido cancelada." y la tarjeta desaparece de `T. Mi Agenda`.
**VALIDACIÓN VISUAL (ESTUDIANTE):** En `E. Historial`, se genera la tarjeta `E. cancelM` con la etiqueta gris "Cancelada". En su parte inferior indica: "Cancelada por el tutor", seguido exactamente del motivo predefinido seleccionado (ej. "Conflicto de horarios con otra tutoría").

* **A4 - Procesar cancelación (Motivo "Otro" con texto) y actualizar vistas:** El sistema ejecuta la cancelación concatenando el texto ingresado. 
**VALIDACIÓN VISUAL (TUTOR):** Idéntico a A3.
**VALIDACIÓN VISUAL (ESTUDIANTE):** En `E. Historial`, la tarjeta `E. cancelM` indica en su parte inferior: "Cancelada por el tutor", seguido de la palabra "Otro" y a continuación el texto exacto redactado por el tutor en el campo opcional.

* **A5 - Procesar cancelación (Motivo "Otro" sin texto) y actualizar vistas:** El sistema ejecuta la cancelación registrando solo la opción principal. 
**VALIDACIÓN VISUAL (TUTOR):** Idéntico a A3.
**VALIDACIÓN VISUAL (ESTUDIANTE):** En `E. Historial`, la tarjeta `E. cancelM` indica en su parte inferior: "Cancelada por el tutor", seguido **únicamente** de la palabra "Otro" (sin espacios en blanco ni caracteres adicionales).

* **A6 - Cerrar modal y regresar a 'Detalles de la Sesión' (Tutor):** La acción se aborta a petición del tutor. 
**VALIDACIÓN VISUAL:** El modal "Cancelar Tutoría" desaparece. Se visualiza nuevamente el modal "Detalles de la Sesión" sin haber realizado cambios en el agendamiento.

* **A7 - Desplegar modal `E.HCancelT` ("Detalle de la Tutoría" Cancelada):** Se abre una ventana de consulta en la interfaz del estudiante. 
**VALIDACIÓN VISUAL:** Se despliega el modal `E.HCancelT` en modo solo lectura. Se visualiza la etiqueta "Cancelada" y un recuadro gris "MOTIVO DE CANCELACIÓN". Este recuadro renderizará exactamente la cadena de texto definida en A3, A4 o A5, confirmando "Cancelada por el tutor ([Nombre del Tutor])". El único botón disponible es "Cerrar".

* **A8 - Cerrar modal `E.HCancelT` y regresar a `E. Historial` (Estudiante):** Se cierra la ventana de lectura. 
**VALIDACIÓN VISUAL:** El modal desaparece, dejando al estudiante en la lista de `E. Historial`.


**Condición del Sistema (Actualización del Historial del Estudiante)**
Como resultado directo de este proceso de cancelación iniciado por el tutor, el sistema debe generar y actualizar automáticamente el registro correspondiente en el historial del estudiante afectado (pantalla `E. Historial`), reflejando los siguientes estados visuales:
* **Vista en el listado principal:** Se mostrará una tarjeta de sesión inactiva con la etiqueta gris de "Cancelada". En la parte inferior de esta tarjeta, se debe indicar explícitamente el texto "Cancelada por el tutor", seguido del motivo exacto que el tutor seleccionó o redactó al momento de cancelar la reserva.
* **Vista de Detalle (E.HCancelT):** Si el estudiante hace clic sobre esta tarjeta desde su historial, el sistema desplegará la ventana modal `E.HCancelT` ("Detalle de la Tutoría"). Esta vista será de solo lectura y, en su sección inferior, mostrará el estado "Cancelada" acompañado de un bloque informativo titulado "MOTIVO DE CANCELACIÓN". Este bloque detallará la razón de la cancelación y confirmará la autoría de la acción con el texto: "Cancelada por el tutor ([Nombre del Tutor])". El único control disponible en esta interfaz será el botón "Cerrar".



---

### Nro. HU-14 - Título: Cancelar tutoría agendada por estudiante

Descripción: Como estudiante, quiero cancelar una tutoría agendada para avisar al tutor que no podré asistir.

#### Matriz de Decisión HU-14

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 |
| :-- | :------------------------------------------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Clic en tarjeta de "Tutorías Agendadas" en la pestaña `Agenda`? | S | N | N | N | N | N | N |
| C2 | ¿Clic en el botón rojo 'Cancelar Tutoría' dentro del modal de detalle? | N | S | N | N | N | N | N |
| C3 | ¿Selección del radio button con la opción "Otro"? | N | N | S | N | N | N | N |
| C4 | ¿Clic en el botón 'Volver' en el modal de cancelación? | N | N | N | S | N | N | N |
| C5 | ¿Clic en el botón rojo 'Sí, cancelar tutoría' en el modal de cancelación? | N | N | N | N | S | N | N |
| C6 | ¿Clic en tarjeta de tutoría cancelada (`E. cancelM`) en la pestaña `Historial`? | N | N | N | N | N | S | N |
| C7 | ¿Clic en el botón 'Cerrar' dentro del modal `E. cancelDeta`? | N | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | |
| A1 | Desplegar Modal 'Detalle Tutoría Confirmada' | X | | | | | | |
| A2 | Desplegar Modal 'Cancelar Tutoría' | | X | | | | | |
| A3 | Mostrar campo de texto 'Comentario adicional (opcional)' | | | X | | | | |
| A4 | Cerrar Modal de Cancelación (Regresar a Detalle) | | | | X | | | |
| A5 | Procesar cancelación y actualizar 'Agenda' e 'Historial' | | | | | X | | |
| A6 | Desplegar Modal 'Detalle de la Tutoría' (Cancelada SR) | | | | | | X | |
| A7 | Cerrar Modal Detalle y volver a 'E. Historial' | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Desplegar Modal 'Detalle Tutoría Confirmada':** Se abre una ventana modal sobre la pantalla `E. Agenda`. 
**VALIDACIÓN VISUAL:** Se visualiza el modal con el título "Detalles de la Sesión", incluyendo la información del tutor, enlace/lugar de reunión, materia, fecha, hora, tarifa y el mensaje original del estudiante. En la parte inferior se muestra un botón interactivo rojo con el texto "Cancelar Tutoría" junto con el botón "Cerrar".

* **A2 - Desplegar Modal 'Cancelar Tutoría':** Se superpone un segundo modal de advertencia. 
**VALIDACIÓN VISUAL:** Se visualiza un modal con el título "Cancelar Tutoría", un recuadro rojo de advertencia ("¿Cancelar esta tutoría? El tutor será notificado..."), y una lista de radio buttons para el "Motivo de la cancelación" (Cambio de planes, Encontré otro tutor, Problema de horario, Otro). En la parte inferior se muestran los botones "Volver" y el botón rojo interactivo "Sí, cancelar tutoría".

* **A3 - Mostrar campo de texto 'Comentario adicional (opcional)':** El modal actual se expande dinámicamente. 
**VALIDACIÓN VISUAL:** Al seleccionar la opción "Otro", aparece inmediatamente debajo un campo de texto con la etiqueta "Comentario adicional (opcional)" que incluye un contador de caracteres con límite de 300. 

* **A4 - Cerrar Modal de Cancelación (Regresar a Detalle):** La acción se aborta y la alerta desaparece. 
**VALIDACIÓN VISUAL:** El modal "Cancelar Tutoría" se cierra, devolviendo al usuario al modal inferior "Detalles de la Sesión" sin haber realizado ningún cambio en el sistema.

* **A5 - Procesar cancelación y actualizar 'Agenda' e 'Historial':** El sistema ejecuta la cancelación, cierra los modales y actualiza las vistas correspondientes. 
**VALIDACIÓN VISUAL:** 1. Se cierra el modal y se muestra una notificación temporal (toast/snackbar) en la pantalla con el texto exacto: "Tutoría cancelada La sesión ha sido cancelada correctamente."
  2. La tarjeta de la sesión desaparece inmediatamente de la pestaña `E. Agenda`.
  3. Al navegar a la pestaña `E. Historial`, la sesión aparece reflejada con el estilo visual `E. cancelM` (etiqueta gris de "Cancelada", y un recuadro inferior indicando "Cancelada por ti" junto con el motivo seleccionado).

* **A6 - Desplegar Modal 'Detalle de la Tutoría' (Cancelada SR):** Se abre una ventana modal de consulta sobre la pantalla `E. Historial`. 
**VALIDACIÓN VISUAL:** Se despliega el modal `E. cancelDeta` mostrando la información original en modo de solo lectura. En la sección inferior, se visualiza la etiqueta "Cancelada" y un recuadro gris titulado "MOTIVO DE CANCELACIÓN" con el detalle. El único botón habilitado es "Cerrar".

* **A7 - Cerrar Modal Detalle y volver a 'E. Historial':** La ventana modal de lectura se cierra. 
**VALIDACIÓN VISUAL:** El modal `E. cancelDeta` desaparece de la vista, dejando al usuario en la pantalla principal del listado en `E. Historial`.

---

### Nro. HU-22 - Título: Ver reseñas sobre el tutor

Descripción: Como estudiante, quiero ver las reseñas sobre un tutor para tomar una decisión informada antes de agendar

#### Matriz de Decisión HU-22

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 |
| :-- | :--- | :-: | :-: |
| C1 | ¿Click en botón 'Ver más reseñas'? | S | N |
| | **ACCIONES** (Usar código corto) | | |
| A1 | Cargar más reseñas | X | |
| A2 | Mantener vista actual de reseñas | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
* **A1 - Cargar más reseñas:** "Permanece en la pantalla 'E. Detalle Oferta y Reseñas' (según mapa) y carga reseñas adicionales. **VALIDACIÓN VISUAL DETALLADA:** Se mantiene visible la sección 'Reseñas de Estudiantes'. La lista de reseñas individuales se expande, mostrando comentarios adicionales. Cada nueva reseña mostrada incluye: Iniciales/Avatar del estudiante, Fecha de la reseña, Calificación otorgada en estrellas, Nombre de la materia sobre la cual se dio la tutoría, y el Comentario o retroalimentación escrita. El texto 'Mostrando X de Y reseñas' (donde X es un número mayor al inicial de 3, y Y el total de 8) se actualiza para reflejar la cantidad de reseñas ahora visibles. El botón 'Ver más reseñas' permanece visible (si aún quedan reseñas por cargar) o desaparece (si todas las reseñas ya están visibles)."
* **A2 - Mantener vista actual de reseñas:** "Permanece en la pantalla 'E. Detalle Oferta y Reseñas' (según mapa) sin cargar nuevas reseñas. **VALIDACIÓN VISUAL DETALLADA:** Se visualiza el encabezado 'Reseñas de Estudiantes'. Se visualiza el resumen de calificaciones, incluyendo la calificación promedio '4.6' con su representación en estrellas (5 estrellas llenas y 1 media estrella), y el texto '8 reseñas'. Se visualizan las barras de desglose de estrellas: '5 estrellas 63%', '4 estrellas 38%', '3 estrellas 0%', '2 estrellas 0%', '1 estrella 0%'. Se visualizan las tres tarjetas de métricas del tutor: '9 Tutorías completadas', '4 Materias impartidas', y '89% Estudiantes que califican'. Se visualiza el texto 'Mostrando 3 de 8 reseñas'. Se visualizan las 3 reseñas individuales mostradas por defecto, que son:
    *   `SO` Sofía Mendoza, con 5 estrellas, "Tutoría: Álgebra Lineal", "Juan es el mejor tutor que he tenido. Explica de forma muy clara y directa.", con fecha '28 feb 2026'.
    *   `AN` Andrés Morales, con 5 estrellas, "Tutoría: Estática", "Juan explica los problemas paso a paso. Muy recomendado para Estática.", con fecha '25 feb 2026'.
    *   `VA` Valeria Sánchez, con 3.5 estrellas, "Tutoría: Física I", "Muy buena clase, aunque empezamos un poco tarde. Los ejercicios fueron muy útiles.", con fecha '18 feb 2026'.
    El botón 'Ver más reseñas' es visible en la parte inferior de la lista de reseñas."

---

### Nro. HU-19 - Título: Ver reseñas recibidas

Descripción: Como tutor, quiero ver las reseñas que he recibido para conocer la opinión de mis estudiantes sobre mi servicio

#### Matriz de Decisión HU-19

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Número total de reseñas mayor a 5? | N | S | S | S | S |
| C2 | ¿Página actual es la primera? | N/A | S | S | S | N |
| C3 | ¿Página actual es la última? | N/A | N | N | N | S |
| C4 | ¿Click en '2'? | N/A | N | S | N | N |
| C5 | ¿Click en '>'? | N/A | N | N | S | N |
| C6 | ¿Click en '<'? | N/A | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | |
| A1 | Mostrar Reseñas sin Paginación | X | | | | |
| A2 | Mostrar Reseñas en Página 1 con Paginación Activa | | X | | | X |
| A3 | Mostrar Reseñas en Página 2 | | | X | X | |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
*   **A1 - Mostrar Reseñas sin Paginación:** "Permanece en la pantalla 'Bandeja de Reseñas'. **VALIDACIÓN VISUAL:** La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'. Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'. El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio (ej. '4.6'), un contador 'X reseñas' (donde X es el número total de reseñas <= 5), y el gráfico de barras con la distribución porcentual de estrellas. La sección 'Reseñas detalladas' muestra el texto 'Mostrando 1–X de X reseñas' (donde X es el número total de reseñas <= 5). Se listan las tarjetas de reseñas individuales (máximo 5). **El control de paginación numérica ('<', '1', '2', '>') NO se visualiza.**"
*   **A2 - Mostrar Reseñas en Página 1 con Paginación Activa:** "Permanece en la pantalla 'Bandeja de Reseñas'. **VALIDACIÓN VISUAL:** La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'. Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'. El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio '4.6', el texto '8 reseñas', y el gráfico de barras con la distribución porcentual de estrellas. La sección 'Reseñas detalladas' muestra el texto 'Mostrando 1–5 de 8 reseñas'. Se listan las 5 tarjetas de reseñas de la página 1, incluyendo: 'SO Sofía Mendoza' (5 estrellas, 'Tutoría: Álgebra Lineal', 'Juan es el mejor tutor que he tenido. Explica de forma muy clara y directa.', '1 de marzo de 2026'), 'AN Andrés Morales' (5 estrellas, 'Tutoría: Estática', 'Juan explica los problemas paso a paso. Muy recomendado para Estática.', '26 de febrero de 2026'), 'VA Valeria Sánchez' (3.5 estrellas, 'Tutoría: Física I', 'Muy buena clase, aunque empezamos un poco tarde. Los ejercicios fueron muy útiles.', '19 de febrero de 2026'), 'AN Andrés Morales' (5 estrellas, 'Tutoría: Cálculo Vectorial', 'Excelente clase, Juan explica muy bien y tiene mucha paciencia. Logré entender todo para mi examen.', '16 de febrero de 2026'), e 'IS Isabella Mora' (3.5 estrellas, 'Tutoría: Cálculo Vectorial', 'Muy buen tutor. Me ayudó a entender integrales de línea.', '16 de enero de 2026'). Se visualiza el control de paginación numérica: el botón '<' está deshabilitado, el botón '1' está resaltado (con fondo oscuro), el botón '2' está activo, y el botón '>' está activo."
*   **A3 - Mostrar Reseñas en Página 2:** "Permanece en la pantalla 'Bandeja de Reseñas'. **VALIDACIÓN VISUAL:** La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'. Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'. El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio '4.6', el texto '8 reseñas', y el gráfico de barras con la distribución porcentual de estrellas. La sección 'Reseñas detalladas' muestra el texto 'Mostrando 6–8 de 8 reseñas'. Se listan las 3 tarjetas de reseñas de la página 2 (contenido simulado, ya que no visible en la imagen: e.g., 'JU Juan Pérez', 'Tutoría: Álgebra', 'Excelente', '15 de enero de 2026'; 'MA María García', 'Tutoría: Cálculo', 'Muy bueno', '10 de enero de 2026'; 'PE Pedro Lopez', 'Tutoría: Física', 'Mejorable', '5 de enero de 2026'). Se visualiza el control de paginación numérica: el botón '<' está activo, el botón '1' está activo, el botón '2' está resaltado (con fondo oscuro), y el botón '>' está deshabilitado."