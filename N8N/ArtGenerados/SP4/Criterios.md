# Reporte de Escenarios Generados
> Generado el: 23/3/2026

### Nro. HU-39 - Título: Ver historial de tutorías impartidas

#### Criterios de aceptación HU-39

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización Inicial del Historial (<= 5 registros)** | **Dado** que el tutor ingresa a la opción 'Historial' y no tiene más de 5 tutorías impartidas registradas,<br> **cuando** el sistema carga la pantalla 'Historial de Tutorías Impartidas',<br> **entonces** se visualizan las tres métricas estáticas superiores (Tutorías completadas, Materias impartidas y Estudiantes que califican) y un listado de máximo 5 tarjetas. Cada tarjeta muestra los siguientes campos: iniciales del estudiante (en un círculo), título de la oferta de la tutoría, nombre del estudiante, y la fecha y hora de la sesión. Los controles de paginación están ocultos. |
| **Historial con Paginación Disponible (> 5 registros)** | **Dado** que el tutor tiene más de 5 tutorías registradas y accede a 'Historial',<br> **cuando** el sistema carga la pantalla 'Historial de Tutorías Impartidas',<br> **entonces** se visualiza el listado con las primeras 5 tarjetas (cada una detallando: iniciales, título de la oferta de la tutoría, nombre del estudiante, y fecha y hora de la sesión) y, en la parte inferior, los controles numéricos de paginación y flechas ('<', '1', '2', '>'). |
| **Navegación por Número de Página** | **Dado** que el tutor visualiza la primera página de su 'Historial de Tutorías Impartidas' con los controles de paginación visibles,<br> **cuando** hace clic en el número de página '2',<br> **entonces** el listado se actualiza para mostrar el siguiente bloque de tutorías (tarjetas 6 a 10) y el número '2' se resalta. |
| **Navegación por Flecha Siguiente** | **Dado** que el tutor visualiza la primera página de su 'Historial de Tutorías Impartidas',<br> **cuando** hace clic en la flecha de paginación '>',<br> **entonces** el listado avanza a la siguiente página de resultados y el número de la nueva página activa se resalta. |
| **Navegación por Flecha Anterior** | **Dado** que el tutor se encuentra visualizando la segunda página de su 'Historial de Tutorías Impartidas',<br> **cuando** hace clic en la flecha de paginación '<',<br> **entonces** el listado retrocede a la primera página de resultados y el número '1' se resalta. |
| **Abrir Detalle de Tutoría Impartida** | **Dado** que el tutor visualiza el listado de tarjetas en su 'Historial de Tutorías Impartidas',<br> **cuando** hace clic sobre el área general de una tarjeta individual,<br> **entonces** se despliega la ventana modal 'Detalle de la Tutoría' atenuando el fondo. El modal muestra la información del estudiante, título de la oferta de la tutoría, fecha, hora, modalidad, precio, lugar/enlace y mensaje. En la parte inferior únicamente se visualiza el botón 'Cerrar'. |
| **Cerrar Detalle de Tutoría Impartida** | **Dado** que el tutor se encuentra visualizando el modal 'Detalle de la Tutoría',<br> **cuando** hace clic en el botón 'Cerrar',<br> **entonces** la ventana modal desaparece y el usuario regresa a la vista principal del listado en la pantalla 'Historial de Tutorías Impartidas'. |

---

### Nro. HU-43 - Título: Registrar la tutoría completada

#### Criterios de aceptación HU-43

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Registro de Tutoría Completada desde Tarjeta** | **Dado** que el tutor visualiza una tutoría "sin confirmar" en el listado de 'Historial de Tutorías Impartidas',<br>**cuando** hace clic directamente en el botón 'Completada' (con borde verde) ubicado en la tarjeta,<br>**entonces** la tarjeta se actualiza en tiempo real. Los botones de acción desaparecen y la tarjeta muestra únicamente una etiqueta verde estática con el ícono check y el texto 'Completada', lo cual incrementa en uno la métrica de "Tutorías completadas". |
| **Apertura de Detalle de Tutoría sin Confirmar** | **Dado** que el tutor visualiza una tutoría "sin confirmar" en el listado principal,<br>**cuando** hace clic sobre el área general de dicha tarjeta,<br>**entonces** se despliega el modal 'Detalle de la Tutoría'. En su parte inferior se visualiza el botón interactivo 'Completada' (borde verde) junto al botón 'Cerrar'. |
| **Registro de Tutoría Completada desde Modal** | **Dado** que el tutor se encuentra visualizando el modal 'Detalle de la Tutoría' con los botones de acción habilitados,<br>**cuando** hace clic en el botón 'Completada' dentro del modal,<br>**entonces** la ventana modal se cierra automáticamente. Al regresar al listado principal, la tarjeta correspondiente se actualiza visualmente al estado 'Completada' (mostrando solo la etiqueta verde estática) e incrementa en uno la métrica de "Tutorías completadas". |
| **Visualización de Detalle de Tutoría Completada (Solo Lectura)** | **Dado** que el tutor hace clic en el área general de una tarjeta que ya está en estado 'Completada' (y el estudiante aún no ha calificado),<br>**cuando** se abre el modal 'Detalle de la Tutoría',<br>**entonces** la vista es de modo lectura. En la esquina inferior izquierda se visualiza el texto estático "Estado: [Icono] Completada" y en la esquina inferior derecha únicamente está habilitado el botón 'Cerrar'. |
| **Cierre de Detalle de Tutoría Completada** | **Dado** que el tutor se encuentra visualizando el modal 'Detalle de la Tutoría' en modo lectura,<br>**cuando** hace clic en el botón 'Cerrar',<br>**entonces** la ventana modal se cierra y el sistema regresa a la pantalla 'Historial de Tutorías Impartidas'. |
| **Visualización de Detalle de Tutoría Confirmada (Integración HU-10)** | **Dado** que el tutor hace clic en una tarjeta 'Completada' que ya fue calificada por el estudiante,<br>**cuando** se abre el modal 'Detalle de la Tutoría',<br>**entonces** la vista es de lectura y muestra, en su parte inferior, una sección adicional con la puntuación en estrellas otorgada y el comentario exacto redactado por el estudiante. Solo el botón 'Cerrar' está habilitado. |

---

### Nro. HU-48 - Título: Registrar inasistencia del estudiante

#### Criterios de aceptación HU-48

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Mostrar Modal de Confirmación desde Tarjeta** | **Dado** que el tutor visualiza una tutoría "sin confirmar" en su 'Historial de Tutorías Impartidas',<br> **cuando** hace clic en el botón 'Inasistencia' (con borde rojo) de la tarjeta,<br> **entonces** se superpone la ventana modal de advertencia "Confirmar Inasistencia" con el texto: "¿Estás seguro? Esta acción marcará la tutoría como inasistencia del estudiante. Esta acción no se puede deshacer.", y los botones "Cancelar" y "Sí, reportar inasistencia". |
| **Mostrar Modal de Confirmación desde Detalle** | **Dado** que el tutor se encuentra dentro del modal 'Detalle de la Tutoría' de una sesión pendiente,<br> **cuando** hace clic en el botón rojo 'Inasistencia' dentro de este modal,<br> **entonces** se superpone el modal de advertencia "Confirmar Inasistencia" bloqueando la vista anterior, mostrando el mensaje de confirmación y los botones "Cancelar" y "Sí, reportar inasistencia". |
| **Cancelar Confirmación de Inasistencia** | **Dado** que el tutor visualiza el modal de advertencia "Confirmar Inasistencia",<br> **cuando** hace clic en el botón 'Cancelar',<br> **entonces** el modal de advertencia desaparece sin aplicar cambios. El sistema devuelve al tutor exactamente a la interfaz que estaba debajo (el modal de detalle). |
| **Reportar Inasistencia Exitosamente** | **Dado** que el tutor visualiza el modal de advertencia "Confirmar Inasistencia",<br> **cuando** hace clic en el botón rojo 'Sí, reportar inasistencia',<br> **entonces** todos los modales abiertos se cierran. En el listado principal de 'Historial de Tutorías Impartidas', la tarjeta se actualiza visualmente mostrando una etiqueta estática con contorno rojo, ícono de "X" y el texto "Inasistencia". Los botones de acción desaparecen. |
| **Ver Detalles de Tutoría con Inasistencia (Solo lectura)** | **Dado** que el tutor hace clic sobre una tarjeta que ya se encuentra en estado 'Inasistencia',<br> **cuando** se despliega el modal 'Detalle de la Tutoría',<br> **entonces** la información se presenta en modo lectura. En la parte inferior se muestra estáticamente "Estado: [Ícono X rojo] Inasistencia". Solo el botón "Cerrar" está habilitado. |
| **Cerrar Detalle de Tutoría con Inasistencia** | **Dado** que el tutor se encuentra visualizando el modal 'Detalle de la Tutoría' de una sesión con inasistencia,<br> **cuando** hace clic en el botón 'Cerrar',<br> **entonces** el modal se cierra y el sistema regresa a la pantalla 'Historial de Tutorías Impartidas'. |

---

### Nro. HU-40 - Título: Ver historial de tutorías recibidas

#### Criterios de aceptación HU-40

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización Inicial del Historial (Integración HU-43 y HU-48)** | **Dado** que el estudiante ingresa a la pestaña "Historial",<br> **cuando** el sistema carga la pantalla principal 'Historial de Tutorías',<br> **entonces** se listan únicamente las tarjetas en estado "Completada" (etiqueta verde) e "Inasistencia" (con recuadro rojo: "El tutor reportó inasistencia para esta sesión."). |
| **Navegación a Página Específica** | **Dado** que el estudiante visualiza la primera página de su 'Historial de Tutorías' con paginación,<br> **cuando** hace clic en el número de página '2',<br> **entonces** el listado se actualiza para mostrar los registros de la página 2 y el número se resalta con fondo oscuro. |
| **Navegación a Siguiente Página** | **Dado** que el estudiante se encuentra en la primera página de su 'Historial de Tutorías',<br> **cuando** hace clic en el control de paginación '>',<br> **entonces** el listado avanza a la siguiente página y el número activo se resalta. |
| **Navegación a Página Anterior** | **Dado** que el estudiante se encuentra en la segunda página de su 'Historial de Tutorías',<br> **cuando** hace clic en el control de paginación '<',<br> **entonces** el listado retrocede a la página anterior y el número activo se resalta. |
| **Ver Detalles de Tutoría Completada (Integración HU-43)** | **Dado** que el estudiante hace clic sobre el área general de una tarjeta "Completada",<br> **cuando** se abre el modal 'Detalle de la Tutoría',<br> **entonces** se muestran los datos de la sesión y una etiqueta inferior de "Estado: Completada". En la parte inferior únicamente se visualiza el botón "Cerrar". |
| **Ver Detalles de Tutoría con Inasistencia (Integración HU-48)** | **Dado** que el estudiante hace clic sobre una tarjeta con el recuadro rojo de Inasistencia,<br> **cuando** se abre el modal 'Detalle de la Tutoría',<br> **entonces** muestra los datos de la sesión y en la parte inferior la etiqueta "Estado: Inasistencia". Solo el botón "Cerrar" está habilitado. |
| **Cerrar Modal de Detalle de Tutoría** | **Dado** que el estudiante visualiza cualquier modal 'Detalle de la Tutoría' desde su historial,<br> **cuando** hace clic en el botón 'Cerrar',<br> **entonces** la ventana modal desaparece y regresa a la vista del listado de 'Historial de Tutorías'. |

---

### Nro. HU-10 - Título: Dejar reseña a tutor

#### Criterios de aceptación HU-10

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Apertura de Modal de Calificación desde Tarjeta (Integración HU-40)** | **Dado** que el estudiante visualiza una tutoría "Completada" en su pantalla 'Historial de Tutorías',<br> **cuando** hace clic en el botón oscuro 'Calificar' directamente en la tarjeta,<br> **entonces** se despliega la ventana modal "Califica tu tutoría" con 5 estrellas vacías, el campo opcional de comentario ("0/300") y el botón "Enviar Reseña" deshabilitado (gris). |
| **Apertura de Detalle de Tutoría Completada (Integración HU-40)** | **Dado** que el estudiante hace clic sobre el área general de una tarjeta "Completada",<br> **cuando** se abre el modal 'Detalle de la Tutoría',<br> **entonces** se muestran los datos de la sesión y, en la parte inferior junto al botón "Cerrar", se visualiza el botón oscuro interactivo "Calificar". |
| **Apertura de Modal de Calificación desde Detalle** | **Dado** que el estudiante se encuentra dentro del modal 'Detalle de la Tutoría' de una sesión completada,<br> **cuando** hace clic en el botón 'Calificar',<br> **entonces** se superpone el modal "Califica tu tutoría" bloqueando la vista anterior, con las 5 estrellas vacías, el campo de comentario opcional y el botón "Enviar Reseña" deshabilitado. |
| **Botón Enviar Reseña Deshabilitado sin Estrellas** | **Dado** que el estudiante se encuentra en el modal "Califica tu tutoría",<br> **cuando** ingresa texto en el campo opcional de comentario pero no selecciona ninguna estrella,<br> **entonces** el botón "Enviar Reseña" permanece deshabilitado. |
| **Habilitación de Botón de Envío** | **Dado** que el estudiante se encuentra en el modal "Califica tu tutoría",<br> **cuando** hace clic para seleccionar de 1 a 5 estrellas,<br> **entonces** el botón "Enviar Reseña" cambia visualmente a estado habilitado e interactuable. |
| **Validación Límite de Caracteres en Comentario** | **Dado** que el estudiante ingresa texto en el campo opcional de comentario,<br> **cuando** alcanza los 300 caracteres permitidos,<br> **entonces** el sistema restringe el ingreso de texto adicional, indicando en el contador "300/300". |
| **Envío de Reseña con Comentario (Integración HU-43)** | **Dado** que el estudiante está en el modal "Califica tu tutoría" con estrellas seleccionadas y un comentario ingresado,<br> **cuando** hace clic en el botón "Enviar Reseña",<br> **entonces** el modal se cierra, se muestra el mensaje temporal exacto: "Reseña enviada. Gracias por calificar tu tutoría." y la tarjeta en el historial se actualiza mostrando la sección "TU CALIFICACIÓN" con las estrellas y el texto. El botón "Calificar" desaparece. |
| **Envío de Reseña sin Comentario (Integración HU-43)** | **Dado** que el estudiante está en el modal "Califica tu tutoría" con estrellas seleccionadas pero deja el campo de comentario vacío,<br> **cuando** hace clic en "Enviar Reseña",<br> **entonces** el sistema procesa el envío correctamente, mostrando el mensaje temporal exacto: "Reseña enviada. Gracias por calificar tu tutoría." y actualizando la tarjeta solo con la representación de las estrellas. |
| **Cancelación de Reseña** | **Dado** que el estudiante visualiza el modal "Califica tu tutoría",<br> **cuando** hace clic en el botón "Cancelar",<br> **entonces** el modal se cierra sin guardar información, regresando al estudiante a la vista exacta donde se encontraba (tarjeta o detalle). |
| **Visualización de Detalle de Tutoría Calificada** | **Dado** que el estudiante hace clic sobre una tarjeta que ya fue calificada en su 'Historial de Tutorías',<br> **cuando** se abre el modal 'Detalle de la Tutoría',<br> **entonces** el modal muestra la información estática y una sección inferior "Tu Reseña" con las estrellas y el texto exacto ingresado. Solo el botón "Cerrar" está habilitado. |
| **Cerrar Detalle de Tutoría Calificada** | **Dado** que el estudiante visualiza el modal 'Detalle de la Tutoría' de una sesión calificada,<br> **cuando** hace clic en el botón 'Cerrar',<br> **entonces** el modal se cierra y el usuario regresa al listado principal. |

---

### Nro. HU-24 - Título: Cancelar tutoría agendada por tutor

#### Criterios de aceptación HU-24

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Despliegue de Detalles de la Sesión (Tutor)** | **Dado** que el tutor se encuentra en su pantalla 'Mi Agenda',<br> **cuando** hace clic sobre una cita agendada (tarjeta naranja) en el panel lateral derecho,<br> **entonces** se despliega el modal 'Detalles de la Sesión' mostrando los datos del estudiante, lugar/enlace, título de la oferta de la tutoría, fecha, hora, tarifa y mensaje. En la parte inferior se muestra el botón rojo 'Cancelar Tutoría' y el botón 'Cerrar'. |
| **Despliegue Modal de Cancelación** | **Dado** que el tutor se encuentra visualizando el modal 'Detalles de la Sesión',<br> **cuando** hace clic en el botón rojo 'Cancelar Tutoría',<br> **entonces** se superpone el modal 'Cancelar Tutoría' mostrando la advertencia roja: "¿Cancelar esta tutoría? El estudiante será notificado de la cancelación. Esta acción no se puede deshacer.", una lista de radio buttons ('Imprevisto personal', 'Conflicto de horarios con otra tutoría', 'Otras opciones de tutorías', 'Otro') y los botones inferiores 'Volver' y 'Sí, cancelar tutoría'. |
| **Aparición de Campo 'Otro' y Validación** | **Dado** que el tutor visualiza el modal 'Cancelar Tutoría',<br> **cuando** selecciona el radio button de la opción 'Otro',<br> **entonces** se despliega dinámicamente e inmediatamente debajo un campo de texto con la etiqueta 'Comentario adicional (opcional)'. Si el tutor ingresa texto hasta el límite máximo de caracteres, el sistema bloquea el ingreso de caracteres adicionales en el campo. |
| **Abortar Cancelación** | **Dado** que el tutor visualiza el modal 'Cancelar Tutoría',<br> **cuando** hace clic en el botón 'Volver',<br> **entonces** el modal de advertencia se cierra sin aplicar cambios, regresando al tutor al modal previo 'Detalles de la Sesión'. |
| **Cancelación por Motivo Predefinido (Integración HU-40)** | **Dado** que el tutor selecciona una opción predefinida en el modal 'Cancelar Tutoría',<br> **cuando** hace clic en 'Sí, cancelar tutoría',<br> **entonces** la sesión desaparece de su pantalla 'Mi Agenda' y se muestra el mensaje exacto: "Tutoría cancelada La sesión ha sido cancelada." Simultáneamente, en el 'Historial de Tutorías' del estudiante afectado, se genera una tarjeta gris de "Cancelada" que en su recuadro inferior indica "Cancelada por el tutor", seguido de la opción predefinida seleccionada. |
| **Cancelación por Motivo "Otro" con Texto (Integración HU-40)** | **Dado** que el tutor selecciona 'Otro' y redacta un texto en el campo opcional,<br> **cuando** hace clic en 'Sí, cancelar tutoría',<br> **entonces** la sesión se cancela mostrando el mensaje exacto: "Tutoría cancelada La sesión ha sido cancelada." Simultáneamente, en el 'Historial de Tutorías' del estudiante, se genera una tarjeta gris de "Cancelada" que en su recuadro inferior indica "Cancelada por el tutor", seguido de la palabra "Otro" y el texto exacto redactado. |
| **Cancelación por Motivo "Otro" sin Texto (Integración HU-40)** | **Dado** que el tutor selecciona 'Otro' y deja el campo opcional vacío,<br> **cuando** hace clic en 'Sí, cancelar tutoría',<br> **entonces** la sesión se cancela mostrando el mensaje exacto: "Tutoría cancelada La sesión ha sido cancelada." Simultáneamente, en el 'Historial de Tutorías' del estudiante, se genera una tarjeta gris de "Cancelada" que en su recuadro inferior indica únicamente "Cancelada por el tutor", seguido de la palabra "Otro". |
| **Visualización de Tutoría Cancelada por Estudiante (Integración HU-40)** | **Dado** que el estudiante afectado hace clic en la tarjeta gris cancelada en su 'Historial de Tutorías',<br> **cuando** se abre el modal 'Detalle de la Tutoría',<br> **entonces** la vista es de solo lectura. Presenta una etiqueta gris de "Cancelada" y un recuadro inferior titulado "MOTIVO DE CANCELACIÓN" que detalla la razón. Debajo del motivo, confirma la autoría con un texto gris que dice: "Cancelada por el tutor ([Nombre del Tutor])". Solo está habilitado el botón "Cerrar". |
| **Cerrar Detalle de Tutoría Cancelada (Estudiante)** | **Dado** que el estudiante visualiza el modal 'Detalle de la Tutoría' de una cita cancelada,<br> **cuando** hace clic en el botón 'Cerrar',<br> **entonces** el modal desaparece y regresa a la pantalla principal de su 'Historial de Tutorías'. |

---

### Nro. HU-14 - Título: Cancelar tutoría agendada por estudiante

#### Criterios de aceptación HU-14

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización Detalle de Sesión Agendada (Estudiante)** | **Dado** que el estudiante se encuentra en la pantalla 'Tutorías Agendadas' (pestaña Agenda),<br> **cuando** hace clic sobre una tarjeta de tutoría próxima,<br> **entonces** se despliega el modal 'Detalles de la Sesión' mostrando la información de la reserva, y un botón rojo inferior con el texto 'Cancelar Tutoría' junto al botón 'Cerrar'. |
| **Despliegue Modal de Cancelación** | **Dado** que el estudiante visualiza el modal 'Detalles de la Sesión',<br> **cuando** hace clic en el botón rojo 'Cancelar Tutoría',<br> **entonces** se superpone el modal de advertencia 'Cancelar Tutoría' con el texto: "¿Cancelar esta tutoría? El tutor será notificado...", y los radio buttons de motivo ('Cambio de planes', 'Encontré otro tutor', 'Problema de horario', 'Otro'). |
| **Aparición Campo 'Comentario adicional' y Validación** | **Dado** que el estudiante visualiza el modal 'Cancelar Tutoría',<br> **cuando** selecciona la opción 'Otro',<br> **entonces** aparece inmediatamente el campo de texto 'Comentario adicional (opcional)' con un contador "0/300". Si el texto alcanza los 300 caracteres permitidos, el sistema restringe el ingreso de texto adicional marcando "300/300". |
| **Retorno a Detalle de Sesión (Abortar)** | **Dado** que el estudiante se encuentra en el modal de confirmación 'Cancelar Tutoría',<br> **cuando** hace clic en el botón 'Volver',<br> **entonces** el modal se cierra sin aplicar cambios, regresando a la vista del modal 'Detalles de la Sesión' y manteniendo la cita en 'Tutorías Agendadas'. |
| **Cancelación Exitosa de Tutoría (Motivo Predefinido e Integración HU-40)** | **Dado** que el estudiante selecciona una opción predefinida en el modal 'Cancelar Tutoría',<br> **cuando** hace clic en el botón rojo 'Sí, cancelar tutoría',<br> **entonces** los modales se cierran y se muestra la notificación temporal exacta: "Tutoría cancelada La sesión ha sido cancelada correctamente." La cita desaparece de 'Tutorías Agendadas' y pasa automáticamente a 'Historial de Tutorías' como una tarjeta gris con el recuadro "Cancelada por ti" junto al motivo seleccionado. |
| **Cancelación Exitosa de Tutoría (Otro con comentario e Integración HU-40)** | **Dado** que el estudiante selecciona 'Otro' e ingresa un comentario válido,<br> **cuando** confirma la cancelación,<br> **entonces** se cierra, se muestra el mensaje exacto "Tutoría cancelada La sesión ha sido cancelada correctamente.", y la tarjeta en 'Historial de Tutorías' reflejará en su recuadro inferior "Cancelada por ti", seguido de la palabra "Otro" y el texto redactado por el estudiante. |
| **Cancelación Exitosa de Tutoría (Otro sin comentario e Integración HU-40)** | **Dado** que el estudiante selecciona 'Otro' pero deja el campo opcional vacío,<br> **cuando** confirma la cancelación,<br> **entonces** se cierra, se muestra el mensaje exacto "Tutoría cancelada La sesión ha sido cancelada correctamente.", y la tarjeta en 'Historial de Tutorías' reflejará en su recuadro inferior únicamente "Cancelada por ti", seguido de la palabra "Otro". |
| **Visualización Detalle de Cancelación Propia (Integración HU-40)** | **Dado** que el estudiante hace clic sobre su tarjeta cancelada en la pantalla 'Historial de Tutorías',<br> **cuando** se abre el modal 'Detalle de la Tutoría',<br> **entonces** se muestra la sesión en modo lectura con la etiqueta "Cancelada". El recuadro inferior "MOTIVO DE CANCELACIÓN" detalla la razón registrada y debajo un texto gris indicando "Cancelada por ti". Solo el botón "Cerrar" está habilitado. |
| **Cierre Detalle de Tutoría Cancelada** | **Dado** que el estudiante visualiza el modal 'Detalle de la Tutoría' de su cita cancelada,<br> **cuando** hace clic en el botón 'Cerrar',<br> **entonces** el modal desaparece, regresando a la vista principal del listado en su 'Historial de Tutorías'. |

---

### Nro. HU-22 - Título: Ver reseñas sobre el tutor

#### Criterios de aceptación HU-22

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Vista Inicial de Reseñas (Integración HU-10)** | **Dado** que el estudiante se desplaza a la sección 'Reseñas de Estudiantes' dentro de la pantalla de detalle de oferta del tutor,<br> **cuando** el sistema carga la sección,<br> **entonces** visualiza el consolidado general de calificaciones, el gráfico de barras porcentuales, las tres métricas del tutor, y un listado de un máximo de 3 reseñas individuales (con avatar, nombre, fecha, estrellas, título de la oferta de la tutoría a la cual asistió el estudiante y comentario). |
| **Carga de Reseñas Adicionales (Integración HU-10)** | **Dado** que el estudiante se encuentra en la sección 'Reseñas de Estudiantes' y existen más de 3 reseñas en total para ese tutor,<br> **cuando** hace clic en el botón inferior 'Ver más reseñas',<br> **entonces** la lista se expande cargando comentarios adicionales hacia abajo, y el texto contador (ej. "Mostrando 3 de 8 reseñas") se actualiza dinámicamente. El botón permanece visible si hay más reseñas por mostrar o desaparece si se alcanzó el total. |

---

### Nro. HU-19 - Título: Ver reseñas recibidas

#### Criterios de aceptación HU-19

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización de Reseñas sin Paginación (Integración HU-10)** | **Dado** que el tutor ingresa a la pestaña superior 'Reseñas' y tiene 5 o menos calificaciones totales,<br> **cuando** el sistema carga la pantalla 'Bandeja de Reseñas',<br> **entonces** se visualiza el recuadro estático "Resumen de Calificaciones" a la izquierda. En el área derecha se listan todas las tarjetas de reseñas. Los controles numéricos de paginación están ocultos en la parte inferior. |
| **Visualización de Primera Página con Paginación (Integración HU-10)** | **Dado** que el tutor tiene más de 5 reseñas registradas y accede a 'Reseñas',<br> **cuando** el sistema carga la pantalla 'Bandeja de Reseñas',<br> **entonces** se listan únicamente las primeras 5 tarjetas de reseñas en el panel derecho. En la parte inferior aparece el control de paginación numérica y de flechas, con el número '1' resaltado visualmente indicando la página activa. |
| **Navegación Directa a Segunda Página** | **Dado** que el tutor se encuentra visualizando la primera página de su 'Bandeja de Reseñas' con los controles de paginación activos,<br> **cuando** hace clic en el número de página '2',<br> **entonces** el bloque de "Reseñas detalladas" se actualiza mostrando el siguiente grupo de tarjetas correspondientes a la segunda página, y el número '2' se resalta de color oscuro en el control de paginación. |
| **Navegación a Segunda Página con Botón Siguiente** | **Dado** que el tutor se encuentra en la primera página de su 'Bandeja de Reseñas',<br> **cuando** hace clic en el botón de flecha '>',<br> **entonces** el bloque de "Reseñas detalladas" avanza a la siguiente página mostrando las nuevas tarjetas, y el número '2' se resalta en el control de paginación. |
| **Navegación a Primera Página con Botón Anterior** | **Dado** que el tutor se encuentra visualizando la segunda página de su 'Bandeja de Reseñas',<br> **cuando** hace clic en el botón de flecha '<',<br> **entonces** el bloque de "Reseñas detalladas" retrocede a la primera página mostrando las tarjetas iniciales, y el número '1' se resalta en el control de paginación. |