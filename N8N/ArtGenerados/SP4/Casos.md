# Reporte de Scripts de Prueba Automatizados (S1)
> Generado el: 2026-03-26

## ID: CP-HU-39-R1
**Título:** Visualización inicial del Historial de Tutorías con menos de 5 registros
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema con 3 tutorías impartidas registradas (menos de 5).

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción de menú 'Historial' en la barra de navegación superior.

**Expected Results:**
 - El sistema redirige a la pantalla 'Historial de Tutorías Impartidas'.
 - Se visualiza el logo 'Poli Tutorias' y el menú de navegación superior con las opciones 'Panel', 'Bandeja', 'Mi Agenda', 'Historial' (resaltada con un fondo oscuro y texto blanco, indicando la página actual), 'Reseñas', un icono de usuario con el texto 'J Juan' y el texto 'Salir'.
 - El título principal 'Historial de Tutorías Impartidas' y el subtítulo 'Registro de todas tus sesiones pasadas' están presentes.
 - Se muestran tres métricas estáticas en la parte superior: '9 Tutorías completadas' (acompañada de un ícono de check verde), '4 Materias impartidas' (acompañada de un ícono de libro) y '89% Estudiantes que califican' (acompañada de un ícono de estrella).
 - Se visualiza un listado de máximo 5 tarjetas de tutorías, correspondiente a las 3 tutorías registradas.
 - Cada tarjeta presenta las iniciales del estudiante en un círculo, el título de la oferta de la tutoría, el nombre del estudiante, y la fecha y hora de la sesión.
 - Los controles de paginación ('<', '1', '2', '>') están ocultos en la parte inferior de la pantalla.

## ID: CP-HU-39-R2
**Título:** Visualización inicial del Historial de Tutorías con más de 5 registros (con paginación)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema con 12 tutorías impartidas registradas (más de 5).

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción de menú 'Historial' en la barra de navegación superior.

**Expected Results:**
 - El sistema redirige a la pantalla 'Historial de Tutorías Impartidas'.
 - Se visualiza el logo 'Poli Tutorias' y el menú de navegación superior con las opciones 'Panel', 'Bandeja', 'Mi Agenda', 'Historial' (resaltada con un fondo oscuro y texto blanco, indicando la página actual), 'Reseñas', un icono de usuario con el texto 'J Juan' y el texto 'Salir'.
 - El título principal 'Historial de Tutorías Impartidas' y el subtítulo 'Registro de todas tus sesiones pasadas' están presentes.
 - Se muestran tres métricas estáticas en la parte superior: '9 Tutorías completadas' (acompañada de un ícono de check verde), '4 Materias impartidas' (acompañada de un ícono de libro) y '89% Estudiantes que califican' (acompañada de un ícono de estrella).
 - Se visualiza un listado con las primeras 5 tarjetas de tutorías, cada una detallando: iniciales del estudiante (en un círculo), título de la oferta de la tutoría, nombre del estudiante, y fecha y hora de la sesión.
 - En la parte inferior de la pantalla, los controles numéricos de paginación y flechas ('<', '1' (resaltado), '2', '3', '4', '5', '6', '>') son visibles, indicando la disponibilidad de más páginas.

## ID: CP-HU-39-R3
**Título:** Navegación por número de página en el Historial de Tutorías
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema con 12 tutorías impartidas registradas, visualizando la primera página de su 'Historial de Tutorías Impartidas' con los controles de paginación visibles.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción de menú 'Historial' en la barra de navegación superior.
 3. Asegurarse de que el listado de tutorías muestra las primeras 5 tarjetas y los controles de paginación están visibles.
 4. Hacer clic en el número de página '2' de los controles de paginación.

**Expected Results:**
 - El sistema permanece en la pantalla 'Historial de Tutorías Impartidas'.
 - El listado de tarjetas de tutorías se actualiza para mostrar el siguiente bloque de tutorías (tarjetas 6 a 10).
 - El número '2' en los controles de paginación se resalta, indicando que es la nueva página activa.

## ID: CP-HU-39-R4-Siguiente
**Título:** Navegación por flecha 'Siguiente' (>) en el Historial de Tutorías
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema con 12 tutorías impartidas registradas, visualizando la primera página de su 'Historial de Tutorías Impartidas' con los controles de paginación visibles.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción de menú 'Historial' en la barra de navegación superior.
 3. Asegurarse de que el listado de tutorías muestra las primeras 5 tarjetas y los controles de paginación están visibles.
 4. Hacer clic en la flecha de paginación '>' (Siguiente).

**Expected Results:**
 - El sistema permanece en la pantalla 'Historial de Tutorías Impartidas'.
 - El listado de tarjetas de tutorías se actualiza para mostrar la siguiente página de resultados (tarjetas 6 a 10).
 - El número de la nueva página activa (ej. '2') se resalta en los controles de paginación.

## ID: CP-HU-39-R4-Anterior
**Título:** Navegación por flecha 'Anterior' (<) en el Historial de Tutorías
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema con 12 tutorías impartidas registradas, visualizando la segunda página de su 'Historial de Tutorías Impartidas'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción de menú 'Historial' en la barra de navegación superior.
 3. Asegurarse de que el listado de tutorías muestra las primeras 5 tarjetas y los controles de paginación están visibles.
 4. Hacer clic en el número de página '2' para navegar a la segunda página.
 5. Hacer clic en la flecha de paginación '<' (Anterior).

**Expected Results:**
 - El sistema permanece en la pantalla 'Historial de Tutorías Impartidas'.
 - El listado de tarjetas de tutorías se actualiza para mostrar la primera página de resultados (tarjetas 1 a 5).
 - El número '1' en los controles de paginación se resalta, indicando que es la nueva página activa.

## ID: CP-HU-39-R5-Abrir
**Título:** Abrir modal de detalle al hacer clic en una tarjeta de tutoría impartida
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema, visualizando el listado de tarjetas en su 'Historial de Tutorías Impartidas' con al menos una tarjeta visible.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción de menú 'Historial' en la barra de navegación superior.
 3. Asegurarse de que al menos una tarjeta de tutoría es visible en el listado.
 4. Hacer clic sobre el área general de una tarjeta individual de tutoría (ej. la primera tarjeta del listado).

**Expected Results:**
 - Se despliega una ventana modal 'Detalle de la Tutoría' sobre la pantalla 'Historial de Tutorías Impartidas'.
 - El modal se superpone a la pantalla principal, atenuándola ligeramente.
 - Muestra la información detallada de la sesión seleccionada, incluyendo la información del estudiante, título de la oferta de la tutoría, fecha, hora, modalidad, precio, lugar/enlace y mensaje.
 - No se visualizan los botones 'Completada' ni 'Inasistencia' dentro de esta modal.
 - En la parte inferior del modal, únicamente se visualiza el botón 'Cerrar'.

## ID: CP-HU-39-R5-Cerrar
**Título:** Cerrar modal de detalle de tutoría impartida
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema, con el modal 'Detalle de la Tutoría' abierto sobre la pantalla 'Historial de Tutorías Impartidas'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Hacer clic en la opción de menú 'Historial' en la barra de navegación superior.
 3. Hacer clic sobre el área general de una tarjeta individual de tutoría (ej. la primera tarjeta del listado) para abrir el modal de detalle.
 4. Asegurarse de que el modal 'Detalle de la Tutoría' se ha desplegado correctamente.
 5. Hacer clic en el botón 'Cerrar' dentro del modal.

**Expected Results:**
 - La ventana modal 'Detalle de la Tutoría' desaparece.
 - El usuario regresa a la vista principal del listado en la pantalla 'Historial de Tutorías Impartidas', manteniendo el estado previo de la paginación y el listado.

---

## ID: CP-HU-43-R1
**Título:** Actualizar estado de tutoría a 'Completada' directamente desde la tarjeta.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado. Existe al menos una tutoría en estado "sin confirmar" en la pantalla 'Historial de Tutorías Impartidas'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Historial de Tutorías Impartidas'.
 3. Localizar una tarjeta de tutoría específica que se encuentre en estado "sin confirmar".
 4. Hacer clic en el botón 'Completada' (con borde verde) ubicado directamente en la tarjeta de la tutoría.

**Expected Results:**
 - La tarjeta de la tutoría específica en el listado de la pantalla 'Historial de Tutorías Impartidas' se actualiza en tiempo real.
 - Los botones 'Completada' (verde) e 'Inasistencia' (rojo) desaparecen de la tarjeta.
 - En su lugar, la tarjeta muestra únicamente una etiqueta verde estática con el ícono check y el texto 'Completada'.
 - La métrica de "Tutorías completadas" del tutor se incrementa en uno.

## ID: CP-HU-43-R2
**Título:** Abrir modal 'Detalle de la Tutoría' para tutoría "sin confirmar" al hacer clic en el área general de la tarjeta.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado. Existe al menos una tutoría en estado "sin confirmar" en la pantalla 'Historial de Tutorías Impartidas'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Historial de Tutorías Impartidas'.
 3. Localizar una tarjeta de tutoría específica que se encuentre en estado "sin confirmar".
 4. Hacer clic en el área general de la tarjeta de la tutoría (fuera de los botones de acción).

**Expected Results:**
 - Se despliega una ventana modal con el título genérico 'Detalle de la Tutoría'.
 - El modal contiene la información de la tutoría (ej. 'Cálculo Vectorial', 'Mateo Vargas', '22 de marzo de 2026 a las 09:00').
 - En su parte inferior se visualiza el botón interactivo 'Completada' (borde verde) junto al botón 'Cerrar'. (No se visualiza el botón 'Inasistencia').

## ID: CP-HU-43-R3
**Título:** Registrar tutoría como 'Completada' desde el modal 'Detalle de la Tutoría' (para tutoría sin confirmar).
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado. Existe al menos una tutoría en estado "sin confirmar" en la pantalla 'Historial de Tutorías Impartidas'. El modal 'Detalle de la Tutoría' está abierto.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Historial de Tutorías Impartidas'.
 3. Localizar una tarjeta de tutoría específica que se encuentre en estado "sin confirmar".
 4. Hacer clic en el área general de la tarjeta para abrir el modal 'Detalle de la Tutoría'.
 5. Dentro del modal 'Detalle de la Tutoría', hacer clic en el botón 'Completada'.

**Expected Results:**
 - La ventana modal 'Detalle de la Tutoría' se cierra automáticamente.
 - El sistema permanece en la pantalla 'Historial de Tutorías Impartidas'.
 - La tarjeta de la tutoría correspondiente en el listado se actualiza visualmente al estado 'Completada'.
 - Los botones 'Completada' e 'Inasistencia' desaparecen de la tarjeta.
 - En su lugar, la tarjeta muestra una etiqueta verde estática con el icono check y el texto 'Completada'.
 - La métrica de "Tutorías completadas" del tutor se incrementa en uno.

## ID: CP-HU-43-R4
**Título:** Abrir modal 'Detalle de la Tutoría' en modo lectura para tutoría ya 'Completada' (sin calificación del estudiante).
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado. Existe al menos una tutoría en estado 'Completada' (y que el estudiante aún no ha calificado) en la pantalla 'Historial de Tutorías Impartidas'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Historial de Tutorías Impartidas'.
 3. Localizar una tarjeta de tutoría específica que se encuentre en estado 'Completada' (con etiqueta verde y sin botones de acción).
 4. Hacer clic en el área general de dicha tarjeta.

**Expected Results:**
 - Se despliega una ventana modal con el título genérico 'Detalle de la Tutoría'.
 - El modal muestra la información de la tutoría (ej. 'Cálculo Vectorial', 'Andrés Morales', '15 de marzo de 2026 a las 10:00').
 - La vista del modal es de modo lectura.
 - En la esquina inferior izquierda se visualiza el texto estático "Estado: [Icono de cheque] Completada".
 - Los botones de acción ('Completada' e 'Inasistencia') no están disponibles.
 - Únicamente el botón 'Cerrar' está habilitado en la parte inferior derecha del modal.

## ID: CP-HU-43-R5
**Título:** Cerrar modal 'Detalle de la Tutoría' (modo lectura) de una tutoría 'Completada'.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado. El modal 'Detalle de la Tutoría' para una tutoría en estado 'Completada' (modo lectura) está abierto.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Historial de Tutorías Impartidas'.
 3. Localizar una tarjeta de tutoría específica que se encuentre en estado 'Completada'.
 4. Hacer clic en el área general de la tarjeta para abrir el modal 'Detalle de la Tutoría' en modo lectura.
 5. Dentro del modal 'Detalle de la Tutoría', hacer clic en el botón 'Cerrar'.

**Expected Results:**
 - La ventana modal 'Detalle de la Tutoría' se cierra.
 - El sistema regresa a la pantalla 'Historial de Tutorías Impartidas'.
 - La pantalla 'Historial de Tutorías Impartidas' se mantiene visible con la tarjeta de la tutoría en el estado 'Completada' (etiqueta verde con texto 'Completada' y icono de cheque).

## ID: CP-HU-43-ADD-01
**Título:** Abrir modal 'Detalle de la Tutoría' en modo lectura para tutoría 'Completada' y calificada por el estudiante.
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado. Existe al menos una tutoría en estado 'Completada' que ya fue calificada por el estudiante en la pantalla 'Historial de Tutorías Impartidas'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Historial de Tutorías Impartidas'.
 3. Localizar una tarjeta de tutoría específica que se encuentre en estado 'Completada' y que ya haya sido calificada por el estudiante.
 4. Hacer clic en el área general de dicha tarjeta.

**Expected Results:**
 - Se despliega una ventana modal con el título 'Detalle de la Tutoría' sobre la pantalla 'Historial de Tutorías Impartidas'.
 - La vista del modal es de modo lectura.
 - En su parte inferior, se muestra una sección adicional con la puntuación en estrellas otorgada y el comentario exacto redactado por el estudiante.
 - Únicamente el botón 'Cerrar' está habilitado.

---

## ID: CP-HU-48-R1
**Título:** Reportar Inasistencia desde Tarjeta de Historial
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado, en la sección 'Historial de Tutorías Impartidas'. Debe existir al menos una tutoría con estado "sin confirmar".

**Steps:**
 1. Iniciar sesión como Tutor en la plataforma.
 2. Navegar a la sección 'Historial de Tutorías Impartidas'.
 3. Identificar una tarjeta de tutoría con el estado "sin confirmar".
 4. Hacer clic en el botón 'Inasistencia' (con borde rojo) ubicado en la tarjeta de la tutoría.

**Expected Results:**
 - Se superpone la ventana modal de advertencia.
 - El modal se visualiza con el título "Confirmar Inasistencia" y un ícono de advertencia rojo.
 - Se muestra el texto explicativo: "¿Estás seguro? Esta acción marcará la tutoría como inasistencia del estudiante. Esta acción no se puede deshacer."
 - En la parte inferior, se visualizan los botones "Cancelar" (borde gris) y "Sí, reportar inasistencia" (borde y texto rojo).

## ID: CP-HU-48-R2
**Título:** Visualizar Detalle de Tutoría sin Confirmar
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado, en la sección 'Historial de Tutorías Impartidas'. Debe existir al menos una tutoría con estado "sin confirmar".

**Steps:**
 1. Iniciar sesión como Tutor en la plataforma.
 2. Navegar a la sección 'Historial de Tutorías Impartidas'.
 3. Identificar una tarjeta de tutoría con el estado "sin confirmar".
 4. Hacer clic en el área general de la tarjeta de tutoría en estado "sin confirmar".

**Expected Results:**
 - Se despliega una ventana modal sobre la pantalla 'Historial de Tutorías Impartidas'.
 - El modal muestra el título "Detalle de la Tutoría".
 - Se visualiza la información completa de la sesión (título de la oferta de la tutoría, Estudiante, Fecha, Hora, Modalidad, Precio, Lugar/Enlace y Mensaje del estudiante).
 - En la parte inferior, se visualizan los botones interactivos "Completada" (borde verde), "Inasistencia" (borde rojo) y el botón de texto "Cerrar".

## ID: CP-HU-48-R3
**Título:** Reportar Inasistencia desde Modal de Detalle
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado, en el modal 'Detalle de la Tutoría' de una sesión pendiente de confirmar.

**Steps:**
 1. Iniciar sesión como Tutor en la plataforma.
 2. Navegar a la sección 'Historial de Tutorías Impartidas'.
 3. Identificar una tarjeta de tutoría con el estado "sin confirmar" y hacer clic para abrir el modal 'Detalle de la Tutoría'.
 4. Hacer clic en el botón rojo 'Inasistencia' dentro del modal 'Detalle de la Tutoría'.

**Expected Results:**
 - Se superpone el modal de advertencia "Confirmar Inasistencia" bloqueando la vista del modal de detalle anterior.
 - El modal se visualiza con el título "Confirmar Inasistencia" y un ícono de advertencia rojo.
 - Se muestra el texto de confirmación: "¿Estás seguro? Esta acción marcará la tutoría como inasistencia del estudiante. Esta acción no se puede deshacer."
 - Contiene los botones "Cancelar" (borde gris) y "Sí, reportar inasistencia" (borde y texto rojo).

## ID: CP-HU-48-R4
**Título:** Cancelar la Confirmación de Inasistencia
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado, visualizando el modal de advertencia "Confirmar Inasistencia" abierto desde el modal de detalle.

**Steps:**
 1. Iniciar sesión como Tutor en la plataforma.
 2. Navegar a la sección 'Historial de Tutorías Impartidas'.
 3. Identificar una tarjeta de tutoría "sin confirmar" y abrir el modal 'Confirmar Inasistencia' desde el modal de detalle.
 4. Hacer clic en el botón 'Cancelar' en el modal "Confirmar Inasistencia".

**Expected Results:**
 - El modal de advertencia "Confirmar Inasistencia" desaparece sin aplicar cambios.
 - El sistema devuelve al tutor exactamente a la interfaz que estaba debajo (el modal 'Detalle de la Tutoría').

## ID: CP-HU-48-R5
**Título:** Reportar Inasistencia Exitosamente
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado, visualizando el modal de advertencia "Confirmar Inasistencia".

**Steps:**
 1. Iniciar sesión como Tutor en la plataforma.
 2. Navegar a la sección 'Historial de Tutorías Impartidas'.
 3. Identificar una tarjeta de tutoría "sin confirmar" y abrir el modal 'Confirmar Inasistencia' (ya sea desde la tarjeta o desde el modal de detalle).
 4. Hacer clic en el botón rojo 'Sí, reportar inasistencia'.

**Expected Results:**
 - Todos los modales abiertos se cierran.
 - Al regresar al listado 'Historial de Tutorías Impartidas', la tarjeta de la sesión correspondiente se actualiza visualmente.
 - La tarjeta actualizada muestra una etiqueta estática con contorno rojo, ícono de "X" y el texto "Inasistencia".
 - Los botones interactivos de acción ("Completada", "Inasistencia") en la tarjeta desaparecen.

## ID: CP-HU-48-R6
**Título:** Ver Detalles de Tutoría con Inasistencia (Solo lectura)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado, en la sección 'Historial de Tutorías Impartidas'. Debe existir al menos una tutoría en estado 'Inasistencia'.

**Steps:**
 1. Iniciar sesión como Tutor en la plataforma.
 2. Navegar a la sección 'Historial de Tutorías Impartidas'.
 3. Identificar una tarjeta de tutoría que ya se encuentre en estado 'Inasistencia'.
 4. Hacer clic en el área general de la tarjeta de tutoría en estado 'Inasistencia'.

**Expected Results:**
 - Se abre una ventana modal 'Detalle de la Tutoría'.
 - La información de la sesión original se presenta en modo lectura.
 - Los botones de acción ("Completada" e "Inasistencia") no se visualizan.
 - En la esquina inferior izquierda del modal se muestra el texto estático "Estado: [Ícono X rojo] Inasistencia".
 - El único control interactivo disponible es el botón "Cerrar".

## ID: CP-HU-48-R7
**Título:** Cerrar Modal de Detalle de Tutoría con Inasistencia
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado, visualizando el modal 'Detalle de la Tutoría' de una sesión con inasistencia.

**Steps:**
 1. Iniciar sesión como Tutor en la plataforma.
 2. Navegar a la sección 'Historial de Tutorías Impartidas'.
 3. Identificar una tarjeta de tutoría en estado 'Inasistencia' y hacer clic para abrir el modal 'Detalle de la Tutoría'.
 4. Hacer clic en el botón 'Cerrar' dentro del modal.

**Expected Results:**
 - La ventana modal 'Detalle de la Tutoría' desaparece.
 - El sistema muestra nuevamente la vista principal del listado en la pantalla 'Historial de Tutorías Impartidas'.
 - No hay ninguna alteración en el estado previo de las tarjetas en el listado.

---

## ID: CP-HU-40-R1
**Título:** Visualización inicial de la pantalla "Historial de Tutorías"
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado en el sistema.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Hacer clic en la opción "Historial" del menú superior de navegación.

**Expected Results:**
 - El sistema redirige a la pantalla "Historial de Tutorías".
 - Se visualiza el logo "Poli Tutorías" en la esquina superior izquierda.
 - La barra de navegación superior muestra las opciones "Explorar", "Mis Solicitudes", "Agenda", "Historial" (resaltada), "Patricio" con icono de perfil y "Salir".
 - El título principal de la pantalla es "Historial de Tutorías" con el subtítulo "Tutorías que has recibido y calificado".
 - Se muestra un listado de tarjetas de tutorías, listando únicamente las tarjetas en estado "Completada" (etiqueta verde) e "Inasistencia" (con recuadro rojo: "El tutor reportó inasistencia para esta sesión.").
 - Los controles de paginación "<", "1", "2", "3", "4", "5", ">" se muestran en la parte inferior.

## ID: CP-HU-40-R2
**Título:** Ver detalles de una tutoría con estado "Completada"
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla "Historial de Tutorías", con tarjetas de tutorías "Completadas" visibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla "Historial de Tutorías".
 3. Hacer clic en el área general de una tarjeta de tutoría con estado "Completada".

**Expected Results:**
 - Se muestra un modal superpuesto a la pantalla "Historial de Tutorías".
 - Se visualiza un modal con los detalles de la tutoría, incluyendo campos como título de la oferta de la tutoría, "Tutor:", "Fecha:", "Hora:", "Duración:".
 - El "Estado:" se muestra como "Completada".
 - En la parte inferior del modal se visualiza únicamente el botón "Cerrar".
 - No se visualiza el botón "Calificar" ni estrellas de calificación (si el modal es en modo lectura y ya se calificó).

## ID: CP-HU-40-R3
**Título:** Cerrar el modal de detalle de tutoría
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y visualizando el modal "Detalle de la Tutoría" desde la pantalla "Historial de Tutorías".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla "Historial de Tutorías".
 3. Hacer clic en una tarjeta de tutoría (Completada o Inasistencia) para abrir el modal de detalle.
 4. Hacer clic en el botón "Cerrar" dentro del modal "Detalle de la Tutoría".

**Expected Results:**
 - La ventana modal desaparece.
 - La pantalla "Historial de Tutorías" vuelve a ser completamente visible, mostrando el listado de tarjetas de tutorías y los controles de paginación, sin ningún modal superpuesto.

## ID: CP-HU-40-R4
**Título:** Ver detalles de una tutoría con estado "Inasistencia"
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla "Historial de Tutorías", con tarjetas de tutorías con estado "Inasistencia" visibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla "Historial de Tutorías".
 3. Hacer clic en una tarjeta de tutoría que muestre el recuadro rojo con el texto "El tutor reportó inasistencia para esta sesión".

**Expected Results:**
 - Se muestra un modal superpuesto a la pantalla "Historial de Tutorías".
 - Se visualiza un modal con los detalles de la tutoría, incluyendo campos como título de la oferta de la tutoría, "Tutor:", "Fecha:", "Hora:", "Duración:".
 - El "Estado:" se muestra como "Inasistencia".
 - En la parte inferior del modal se visualiza únicamente el botón "Cerrar".

## ID: CP-HU-40-R5
**Título:** Navegar a una página específica del historial de tutorías
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla "Historial de Tutorías", con múltiples páginas de resultados disponibles en la paginación.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla "Historial de Tutorías".
 3. Hacer clic en el número de página '2' (o cualquier número de página disponible diferente de la actual) de los controles de paginación.

**Expected Results:**
 - El listado de tarjetas de tutorías se actualiza para mostrar los registros correspondientes a la página seleccionada (página 2).
 - El número de página '2' se resalta con un fondo oscuro, indicando que es la página activa.
 - Permanece en la pantalla "Historial de Tutorías".

## ID: CP-HU-40-R6
**Título:** Navegar a la siguiente página del historial de tutorías
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla "Historial de Tutorías", con una página siguiente disponible en la paginación (no en la última página).

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla "Historial de Tutorías" y asegurarse de estar en la primera página (o una página intermedia).
 3. Hacer clic en el control de paginación '>'.

**Expected Results:**
 - El listado de tarjetas de tutorías se actualiza para mostrar los registros de la siguiente página.
 - El número de la página activa (ej. '2') se resalta con un fondo oscuro.
 - Permanece en la pantalla "Historial de Tutorías".

## ID: CP-HU-40-R7
**Título:** Navegar a la página anterior del historial de tutorías
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla "Historial de Tutorías", con una página anterior disponible en la paginación (no en la primera página).

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla "Historial de Tutorías" y asegurarse de estar en la segunda página (o una página posterior a la primera).
 3. Hacer clic en el control de paginación '<'.

**Expected Results:**
 - El listado de tarjetas de tutorías se actualiza para mostrar los registros de la página anterior.
 - El número de la página activa (ej. '1') se resalta con un fondo oscuro.
 - Permanece en la pantalla "Historial de Tutorías".

## ID: CP-HU-40-EXTRA-01
**Título:** Verificación de ausencia de elementos "Ordenar" y "Estado" en la pantalla de historial
**Prioridad:** Baja
**Tipo:** Funcional / UI
**Pre-condiciones:** Estudiante logueado y en la pantalla "Historial de Tutorías".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla "Historial de Tutorías".
 3. Observar los elementos presentes en la interfaz de la pantalla.

**Expected Results:**
 - No se visualiza ningún control o label con el texto "Ordenar:".
 - No se visualiza ningún control o label con el texto "Estado:".

---

## ID: CP-HU-10-01
**Título:** Apertura de Modal de Calificación desde Tarjeta de Historial
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada" visible.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic en el botón oscuro "Calificar" directamente en la tarjeta de la tutoría.

**Expected Results:**
 - El sistema despliega el modal "Califica tu tutoría" sobre la pantalla actual.
 - Se visualiza un modal centrado con el título "Califica tu tutoría".
 - Contiene el texto "Califica tu experiencia con el tutor:", un conjunto de 5 estrellas (inicialmente sin selección), el texto "Deja un comentario (opcional):", un campo de texto (textarea), y dos botones en la parte inferior: "Enviar Reseña" y "Cancelar".
 - El botón "Enviar Reseña" se muestra deshabilitado (gris claro).

## ID: CP-HU-10-02
**Título:** Envío Exitoso de Reseña con Comentario y Calificación
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada". Modal "Califica tu tutoría" abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic en el botón oscuro "Calificar" en la tarjeta.
 5. Seleccionar 4 estrellas en el conjunto de calificación.
 6. Ingresar texto en el campo "Deja un comentario (opcional):", por ejemplo: "Excelente tutor, muy claro en sus explicaciones y dispuesto a ayudar.".
 7. Hacer clic en el botón "Enviar Reseña".

**Expected Results:**
 - El botón "Enviar Reseña" se visualiza habilitado después de seleccionar las estrellas.
 - El modal "Califica tu tutoría" se cierra.
 - Se muestra el mensaje temporal exacto: "Reseña enviada. Gracias por calificar tu tutoría.".
 - La tarjeta de la tutoría correspondiente en la pantalla 'Historial de Tutorías' se actualiza: el botón oscuro "Calificar" desaparece.
 - En su lugar, se muestran las 4 estrellas seleccionadas por el estudiante y el comentario ingresado "Excelente tutor, muy claro en sus explicaciones y dispuesto a ayudar.".
 - La etiqueta de estado verde "Completada" permanece visible.
 - La pantalla 'Historial de Tutorías' se visualiza nuevamente.

## ID: CP-HU-10-03
**Título:** Envío Exitoso de Reseña sin Comentario, solo Calificación
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada". Modal "Califica tu tutoría" abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic en el botón oscuro "Calificar" en la tarjeta.
 5. Seleccionar 5 estrellas en el conjunto de calificación.
 6. Dejar el campo "Deja un comentario (opcional):" vacío.
 7. Hacer clic en el botón "Enviar Reseña".

**Expected Results:**
 - El botón "Enviar Reseña" se visualiza habilitado después de seleccionar las estrellas.
 - El modal "Califica tu tutoría" se cierra.
 - Se muestra el mensaje temporal exacto: "Reseña enviada. Gracias por calificar tu tutoría.".
 - La tarjeta de la tutoría correspondiente en la pantalla 'Historial de Tutorías' se actualiza: el botón oscuro "Calificar" desaparece.
 - En su lugar, se muestran las 5 estrellas seleccionadas por el estudiante.
 - La etiqueta de estado verde "Completada" permanece visible.
 - La pantalla 'Historial de Tutorías' se visualiza nuevamente.

## ID: CP-HU-10-04
**Título:** Botón 'Enviar Reseña' Deshabilitado sin Selección de Estrellas
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada". Modal "Califica tu tutoría" abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic en el botón oscuro "Calificar" en la tarjeta.
 5. Dejar las 5 estrellas sin seleccionar.
 6. Ingresar texto en el campo "Deja un comentario (opcional):", por ejemplo: "Quiero dejar un comentario sin calificar la tutoría.".

**Expected Results:**
 - El botón "Enviar Reseña" dentro del modal "Califica tu tutoría" se visualiza deshabilitado (en gris claro).
 - El modal 'Califica tu tutoría' permanece abierto y visible en la pantalla.

## ID: CP-HU-10-05
**Título:** Cancelación de Reseña
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada". Modal "Califica tu tutoría" abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic en el botón oscuro "Calificar" en la tarjeta.
 5. Seleccionar 3 estrellas.
 6. Ingresar texto en el campo "Deja un comentario (opcional):", por ejemplo: "Este es un comentario de prueba para cancelar.".
 7. Hacer clic en el botón "Cancelar".

**Expected Results:**
 - El modal con el título "Califica tu tutoría" desaparece de la pantalla.
 - El modal se cierra sin guardar información.
 - El estudiante regresa a la vista exacta donde se encontraba (la pantalla 'Historial de Tutorías').
 - La tarjeta de la tutoría permanece en su estado original "Completada" y el botón oscuro "Calificar" sigue visible.

## ID: CP-HU-10-06
**Título:** Visualización de Detalle de Tutoría Calificada
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría que ya ha sido calificada (mostrando estrellas/comentario).

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría que ya fue calificada (indicada por las estrellas y posible comentario visible).
 4. Hacer clic sobre el área general de la tarjeta de la tutoría calificada.

**Expected Results:**
 - Se despliega un modal centrado con el título "Detalle de la Tutoría".
 - El modal muestra la información general de la sesión.
 - En la parte inferior, se visualiza una sección "Tu Reseña" con las estrellas otorgadas y el comentario redactado previamente.
 - Solo se visualiza un botón "Cerrar" en la parte inferior del modal.
 - El botón "Cerrar" se visualiza habilitado y es cliqueable.
 - Esta vista es de solo lectura.

## ID: CP-HU-10-07
**Título:** Habilitación del Botón 'Enviar Reseña' al Seleccionar Estrellas
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada". Modal "Califica tu tutoría" abierto, con el botón "Enviar Reseña" deshabilitado.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic en el botón oscuro "Calificar" en la tarjeta. (El botón "Enviar Reseña" está deshabilitado por defecto).
 5. Hacer clic para seleccionar 1 estrella (o cualquier número entre 1 y 5).

**Expected Results:**
 - El botón "Enviar Reseña" cambia visualmente a estado habilitado e interactuable (cambia de gris claro a un color más oscuro).

## ID: CP-HU-10-08
**Título:** Validación del Límite de Caracteres en el Campo de Comentario (300 caracteres)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada". Modal "Califica tu tutoría" abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic en el botón oscuro "Calificar" en la tarjeta.
 5. Ingresar un texto de 300 caracteres exactos en el campo "Deja un comentario (opcional):".
 6. Intentar ingresar un carácter adicional.

**Expected Results:**
 - El contador de caracteres en el campo de comentario muestra "300/300".
 - El sistema restringe el ingreso de texto adicional, no permitiendo escribir más allá de los 300 caracteres.

## ID: CP-HU-10-09
**Título:** Apertura de Modal de Calificación desde Detalle de Tutoría Completada
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría en estado "Completada".

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría con la etiqueta de estado "Completada".
 4. Hacer clic sobre el área general de la tarjeta para abrir el modal 'Detalle de la Tutoría'.
 5. Hacer clic en el botón oscuro interactivo "Calificar" dentro del modal 'Detalle de la Tutoría'.

**Expected Results:**
 - Se superpone el modal "Califica tu tutoría" bloqueando la vista anterior ('Detalle de la Tutoría').
 - El modal contiene las 5 estrellas vacías, el campo de comentario opcional y el botón "Enviar Reseña" deshabilitado (gris claro).

## ID: CP-HU-10-10
**Título:** Cerrar Modal de Detalle de Tutoría Calificada
**Prioridad:** Baja
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías', con al menos una tutoría calificada. Modal 'Detalle de la Tutoría' abierto.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Localizar una tarjeta de tutoría que ya fue calificada.
 4. Hacer clic sobre el área general de la tarjeta para abrir el modal 'Detalle de la Tutoría'.
 5. Hacer clic en el botón "Cerrar" en la parte inferior del modal.

**Expected Results:**
 - El modal 'Detalle de la Tutoría' desaparece de la pantalla.
 - El usuario regresa al listado principal de 'Historial de Tutorías'.

---

## ID: CP-HU-24-R1
**Título:** Despliegue del Modal 'Cancelar Tutoría'
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla 'Mi Agenda'. El modal 'Detalles de la Sesión' está visible.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Mi Agenda'.
 3. Hacer clic sobre una tarjeta de tutoría agendada (tarjeta naranja) en el panel lateral derecho para desplegar el modal 'Detalles de la Sesión'.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría' en el modal 'Detalles de la Sesión'.
 5. El modal 'Cancelar Tutoría' es desplegado.

**Expected Results:**
 - Se superpone el modal 'Cancelar Tutoría'.
 - Se visualiza un modal con el título "Cancelar Tutoría".
 - Se visualiza la advertencia en rojo: "¿Cancelar esta tutoría? El estudiante será notificado de la cancelación. Esta acción no se puede deshacer.".
 - Se visualiza una lista de radio buttons para el "Motivo de la cancelación" ('Imprevisto personal', 'Conflicto de horarios con otra tutoría', 'Otras opciones de tutorías', 'Otro').
 - Se visualizan los botones inferiores "Volver" y "Sí, cancelar tutoría".

## ID: CP-HU-24-R2
**Título:** Cancelación de Tutoría con Motivo Predefinido (Tutor)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla 'Mi Agenda'. El modal 'Cancelar Tutoría' está visible.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Mi Agenda'.
 3. Hacer clic sobre una tarjeta de tutoría agendada (tarjeta naranja) en el panel lateral derecho para desplegar el modal 'Detalles de la Sesión'.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría' en el modal 'Detalles de la Sesión'.
 5. Seleccionar el radio button con un motivo predefinido, por ejemplo, "Conflicto de horarios con otra tutoría".
 6. Hacer clic en el botón 'Sí, cancelar tutoría'.

**Expected Results:**
 - El modal "Cancelar Tutoría" se cierra.
 - Se muestra el mensaje exacto: "Tutoría cancelada La sesión ha sido cancelada."
 - La tarjeta de la tutoría cancelada desaparece de la pantalla 'Mi Agenda'.
 - En la pantalla 'Historial de Tutorías' del estudiante afectado, se genera una tarjeta gris de "Cancelada".
 - En la parte inferior de la tarjeta del estudiante, se indica "Cancelada por el tutor", seguido exactamente de "Conflicto de horarios con otra tutoría".

## ID: CP-HU-24-R3
**Título:** Cancelación de Tutoría con Motivo "Otro" y Comentario Adicional (Tutor)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla 'Mi Agenda'. El modal 'Cancelar Tutoría' está visible.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Mi Agenda'.
 3. Hacer clic sobre una tarjeta de tutoría agendada (tarjeta naranja) en el panel lateral derecho para desplegar el modal 'Detalles de la Sesión'.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría' en el modal 'Detalles de la Sesión'.
 5. Seleccionar el radio button "Otro".
 6. Ingresar el texto "Tuve una emergencia familiar inesperada" en el campo 'Comentario adicional (opcional)'.
 7. Hacer clic en el botón 'Sí, cancelar tutoría'.

**Expected Results:**
 - El campo de texto 'Comentario adicional (opcional)' aparece dinámicamente debajo del radio button "Otro" después del Paso 5.
 - El modal "Cancelar Tutoría" se cierra.
 - Se muestra el mensaje exacto: "Tutoría cancelada La sesión ha sido cancelada."
 - La tarjeta de la tutoría cancelada desaparece de la pantalla 'Mi Agenda'.
 - En la pantalla 'Historial de Tutorías' del estudiante afectado, se genera una tarjeta gris de "Cancelada".
 - En la parte inferior de la tarjeta del estudiante, se indica "Cancelada por el tutor", seguido de la palabra "Otro" y a continuación el texto exacto redactado por el tutor: "Tuve una emergencia familiar inesperada".

## ID: CP-HU-24-R4
**Título:** Cancelación de Tutoría con Motivo "Otro" sin Comentario Adicional (Tutor)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla 'Mi Agenda'. El modal 'Cancelar Tutoría' está visible.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Mi Agenda'.
 3. Hacer clic sobre una tarjeta de tutoría agendada (tarjeta naranja) en el panel lateral derecho para desplegar el modal 'Detalles de la Sesión'.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría' en el modal 'Detalles de la Sesión'.
 5. Seleccionar el radio button "Otro".
 6. Dejar el campo 'Comentario adicional (opcional)' vacío.
 7. Hacer clic en el botón 'Sí, cancelar tutoría'.

**Expected Results:**
 - El campo de texto 'Comentario adicional (opcional)' aparece dinámicamente debajo del radio button "Otro" después del Paso 5.
 - El modal "Cancelar Tutoría" se cierra.
 - Se muestra el mensaje exacto: "Tutoría cancelada La sesión ha sido cancelada."
 - La tarjeta de la tutoría cancelada desaparece de la pantalla 'Mi Agenda'.
 - En la pantalla 'Historial de Tutorías' del estudiante afectado, se genera una tarjeta gris de "Cancelada".
 - En la parte inferior de la tarjeta del estudiante, se indica "Cancelada por el tutor", seguido únicamente de la palabra "Otro".

## ID: CP-HU-24-R5
**Título:** Abortar la Cancelación de Tutoría desde el Modal (Tutor)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla 'Mi Agenda'. El modal 'Cancelar Tutoría' está visible.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Mi Agenda'.
 3. Hacer clic sobre una tarjeta de tutoría agendada (tarjeta naranja) en el panel lateral derecho para desplegar el modal 'Detalles de la Sesión'.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría' en el modal 'Detalles de la Sesión'.
 5. Hacer clic en el botón 'Volver' en el modal 'Cancelar Tutoría'.

**Expected Results:**
 - El modal 'Cancelar Tutoría' desaparece.
 - Se visualiza nuevamente el modal 'Detalles de la Sesión'.
 - La tutoría no ha sido cancelada ni se han aplicado cambios en el agendamiento.

## ID: CP-HU-24-R6
**Título:** Visualización del Detalle de Tutoría Cancelada por Estudiante
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías'. Existe al menos una tutoría previamente cancelada por un tutor y visible como tarjeta gris en 'Historial de Tutorías'.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Hacer clic en la tarjeta gris de una tutoría previamente cancelada.
 4. El modal 'Detalle de la Tutoría' es desplegado.

**Expected Results:**
 - Se despliega el modal "Detalle de la Tutoría".
 - La vista del modal es de solo lectura.
 - Se visualiza la etiqueta "Cancelada" en el modal.
 - Se visualiza un recuadro gris "MOTIVO DE CANCELACIÓN" que detalla la razón de la cancelación (ej. "Conflicto de horarios con otra tutoría").
 - Debajo del motivo, confirma la autoría con un texto gris que dice: "Cancelada por el tutor ([Nombre del Tutor])".
 - El único botón disponible en esta interfaz es "Cerrar".

## ID: CP-HU-24-R7
**Título:** Cerrar Modal de Detalle de Tutoría Cancelada (Estudiante)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y en la pantalla 'Historial de Tutorías'. El modal "Detalle de la Tutoría" (Cancelada) está visible.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Hacer clic en la tarjeta gris de una tutoría previamente cancelada para abrir el modal 'Detalle de la Tutoría'.
 4. Hacer clic en el botón 'Cerrar' en el modal 'Detalle de la Tutoría'.

**Expected Results:**
 - El modal 'Detalle de la Tutoría' desaparece.
 - El estudiante regresa a la pantalla principal de su 'Historial de Tutorías'.

## ID: CP-HU-24-ADD-01
**Título:** Verificación del Contenido Inicial del Modal 'Detalles de la Sesión' (Tutor)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla 'Mi Agenda'. Existe una tutoría agendada.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Mi Agenda'.
 3. Hacer clic sobre una tarjeta de tutoría agendada (tarjeta naranja) en el panel lateral derecho.
 4. El modal 'Detalles de la Sesión' es desplegado.

**Expected Results:**
 - Se despliega el modal 'Detalles de la Sesión'.
 - El modal muestra los datos del estudiante, lugar/enlace, título de la oferta de la tutoría, fecha, hora, tarifa y mensaje.
 - En la parte inferior del modal se muestra el botón rojo 'Cancelar Tutoría'.
 - En la parte inferior del modal se muestra el botón 'Cerrar'.

## ID: CP-HU-24-ADD-02
**Título:** Validación del Límite de Caracteres en 'Comentario adicional (opcional)' (Tutor)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado y en la pantalla 'Mi Agenda'. El modal 'Cancelar Tutoría' está visible y el radio button "Otro" ha sido seleccionado.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la pantalla 'Mi Agenda'.
 3. Hacer clic sobre una tarjeta de tutoría agendada (tarjeta naranja) en el panel lateral derecho para desplegar el modal 'Detalles de la Sesión'.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría' en el modal 'Detalles de la Sesión'.
 5. Seleccionar el radio button "Otro".
 6. Ingresar texto en el campo 'Comentario adicional (opcional)' hasta alcanzar su límite máximo de caracteres.
 7. Intentar ingresar caracteres adicionales.

**Expected Results:**
 - El campo de texto 'Comentario adicional (opcional)' aparece dinámicamente debajo del radio button "Otro" después del Paso 5.
 - El sistema bloquea el ingreso de caracteres adicionales en el campo una vez alcanzado el límite máximo.
 - El texto ingresado hasta el límite máximo de caracteres permanece visible en el campo.

---

## ID: CP-HU-14-R1
**Título:** Visualizar detalles de una tutoría agendada
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y con al menos una tutoría agendada en la pantalla 'Tutorías Agendadas'.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.

**Expected Results:**
 - Se despliega el modal 'Detalles de la Sesión'.
 - Se visualiza el modal con el título "Detalles de la Sesión", incluyendo la información del tutor, enlace/lugar de reunión, título de la oferta de la tutoría, fecha, hora, tarifa y el mensaje original del estudiante.
 - En la parte inferior se muestra un botón interactivo rojo con el texto "Cancelar Tutoría" junto con el botón "Cerrar".

## ID: CP-HU-14-R2
**Título:** Desplegar modal de cancelación de tutoría
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y visualizando el modal 'Detalles de la Sesión' de una tutoría agendada.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría' dentro del modal de detalle.

**Expected Results:**
 - Se superpone el modal de advertencia 'Cancelar Tutoría'.
 - Se visualiza el modal con el título "Cancelar Tutoría" y un recuadro rojo de advertencia con el texto: "¿Cancelar esta tutoría? El tutor será notificado...".
 - Se muestra una lista de radio buttons para el "Motivo de la cancelación" con las opciones: "Cambio de planes", "Encontré otro tutor", "Problema de horario", "Otro".
 - En la parte inferior se muestran los botones "Volver" y el botón rojo interactivo "Sí, cancelar tutoría".

## ID: CP-HU-14-R3-01
**Título:** Visualizar campo 'Comentario adicional (opcional)' al seleccionar 'Otro'
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y visualizando el modal 'Cancelar Tutoría'.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría'.
 5. Seleccionar el radio button con la opción "Otro".

**Expected Results:**
 - El modal actual se expande dinámicamente.
 - Aparece inmediatamente debajo el campo de texto con la etiqueta "Comentario adicional (opcional)".
 - Se visualiza un contador de caracteres "0/300" junto al campo de texto.

## ID: CP-HU-14-R3-02
**Título:** Restringir ingreso de texto en 'Comentario adicional' a 300 caracteres
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado, visualizando el modal 'Cancelar Tutoría' y con la opción "Otro" seleccionada.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría'.
 5. Seleccionar el radio button con la opción "Otro".
 6. Ingresar un texto de 301 caracteres o más en el campo 'Comentario adicional (opcional)'.
 7. Hacer clic en el botón 'Sí, cancelar tutoría'. (Este paso es para forzar la validación, aunque la restricción suele ser en input).

**Expected Results:**
 - El campo de texto 'Comentario adicional (opcional)' restringe la entrada a un máximo de 300 caracteres.
 - El contador de caracteres se actualiza y muestra "300/300".
 - El sistema permite continuar con la cancelación utilizando los 300 caracteres ingresados (si el flujo lo permite o si la validación es del campo de texto solamente, el botón de "cancelar" debería estar habilitado).

## ID: CP-HU-14-R4
**Título:** Abortar cancelación y regresar a detalles de sesión
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y visualizando el modal 'Cancelar Tutoría'.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría'.
 5. Hacer clic en el botón 'Volver' en el modal de cancelación.

**Expected Results:**
 - El modal "Cancelar Tutoría" se cierra.
 - La acción de cancelación se aborta sin aplicar cambios en el sistema.
 - El usuario es devuelto al modal inferior "Detalles de la Sesión".
 - La cita se mantiene visible en la pantalla 'Tutorías Agendadas'.

## ID: CP-HU-14-R5-01
**Título:** Cancelación exitosa de tutoría con motivo predefinido
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y visualizando el modal 'Cancelar Tutoría'.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría'.
 5. Seleccionar una opción predefinida para el "Motivo de la cancelación" (ej: "Cambio de planes").
 6. Hacer clic en el botón rojo 'Sí, cancelar tutoría'.

**Expected Results:**
 - Los modales se cierran.
 - Se muestra una notificación temporal (toast/snackbar) en la pantalla con el texto exacto: "Tutoría cancelada La sesión ha sido cancelada correctamente."
 - La tarjeta de la sesión desaparece inmediatamente de la pantalla 'Tutorías Agendadas'.
 - Al navegar a la pantalla 'Historial de Tutorías', la sesión aparece reflejada con una etiqueta gris de "Cancelada", y un recuadro inferior indicando "Cancelada por ti" junto con el motivo seleccionado "Cambio de planes".

## ID: CP-HU-14-R5-02
**Título:** Cancelación exitosa de tutoría con motivo 'Otro' y comentario
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado, visualizando el modal 'Cancelar Tutoría', con la opción "Otro" seleccionada y un comentario válido ingresado.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría'.
 5. Seleccionar el radio button con la opción "Otro".
 6. Ingresar un comentario válido en el campo 'Comentario adicional (opcional)' (ej: "Surgió una emergencia personal").
 7. Hacer clic en el botón rojo 'Sí, cancelar tutoría'.

**Expected Results:**
 - Los modales se cierran.
 - Se muestra una notificación temporal (toast/snackbar) en la pantalla con el texto exacto: "Tutoría cancelada La sesión ha sido cancelada correctamente."
 - La tarjeta de la sesión desaparece inmediatamente de la pantalla 'Tutorías Agendadas'.
 - Al navegar a la pantalla 'Historial de Tutorías', la sesión aparece reflejada con una etiqueta gris de "Cancelada", y un recuadro inferior indicando "Cancelada por ti", seguido de la palabra "Otro" y el texto redactado por el estudiante.

## ID: CP-HU-14-R5-03
**Título:** Cancelación exitosa de tutoría con motivo 'Otro' sin comentario
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado, visualizando el modal 'Cancelar Tutoría', y con la opción "Otro" seleccionada pero el campo de comentario vacío.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pestaña 'Agenda'.
 3. Hacer clic sobre la tarjeta de una tutoría agendada.
 4. Hacer clic en el botón rojo 'Cancelar Tutoría'.
 5. Seleccionar el radio button con la opción "Otro".
 6. Dejar el campo 'Comentario adicional (opcional)' vacío.
 7. Hacer clic en el botón rojo 'Sí, cancelar tutoría'.

**Expected Results:**
 - Los modales se cierran.
 - Se muestra una notificación temporal (toast/snackbar) en la pantalla con el texto exacto: "Tutoría cancelada La sesión ha sido cancelada correctamente."
 - La tarjeta de la sesión desaparece inmediatamente de la pantalla 'Tutorías Agendadas'.
 - Al navegar a la pantalla 'Historial de Tutorías', la sesión aparece reflejada con una etiqueta gris de "Cancelada", y un recuadro inferior indicando únicamente "Cancelada por ti", seguido de la palabra "Otro", sin comentario adicional.

## ID: CP-HU-14-R6
**Título:** Visualizar detalles de una tutoría cancelada por el estudiante
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y con al menos una tutoría cancelada por él mismo visible en la pantalla 'Historial de Tutorías'.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Hacer clic sobre una tarjeta de tutoría cancelada.

**Expected Results:**
 - Se abre una ventana modal 'Detalle de la Tutoría'.
 - El modal muestra la información original de la sesión en modo de solo lectura.
 - En la sección inferior, se visualiza la etiqueta "Cancelada" y un recuadro gris titulado "MOTIVO DE CANCELACIÓN" con el detalle de la razón.
 - Debajo del motivo de cancelación, se muestra un texto gris indicando "Cancelada por ti".
 - El único botón habilitado es "Cerrar".

## ID: CP-HU-14-R7
**Título:** Cerrar modal de detalle de tutoría cancelada
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado y visualizando el modal 'Detalle de la Tutoría' de una cita cancelada.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Historial de Tutorías'.
 3. Hacer clic sobre una tarjeta de tutoría cancelada.
 4. Hacer clic en el botón 'Cerrar' dentro del modal 'Detalle de la Tutoría'.

**Expected Results:**
 - El modal 'Detalle de la Tutoría' desaparece de la vista.
 - El usuario regresa a la pantalla principal del listado en su 'Historial de Tutorías'.

---

## ID: CP-HU-22-R1-01
**Título:** Verificar carga de reseñas adicionales (no todas) al hacer clic en 'Ver más reseñas'.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado, en la sección 'Reseñas de Estudiantes' de la pantalla detalle de oferta del tutor que tiene un total de 8 reseñas, de las cuales 3 son visibles inicialmente y el botón 'Ver más reseñas' está presente.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla detalle de oferta del tutor para un tutor que tenga 8 reseñas en total.
 3. Desplazarse a la sección 'Reseñas de Estudiantes'.
 4. Verificar que se visualiza el texto "Mostrando 3 de 8 reseñas" en la parte inferior de la lista de reseñas.
 5. Hacer clic en el botón 'Ver más reseñas'.

**Expected Results:**
 - La pantalla detalle de oferta del tutor permanece visible.
 - La sección 'Reseñas de Estudiantes' se mantiene visible.
 - La lista de reseñas individuales se expande, mostrando comentarios adicionales hacia abajo (ej. se cargan 3 reseñas más, totalizando 6 reseñas visibles).
 - El texto contador se actualiza dinámicamente, por ejemplo, a "Mostrando 6 de 8 reseñas".
 - Cada nueva reseña mostrada incluye: Iniciales/Avatar del estudiante, Fecha de la reseña, Calificación otorgada en estrellas, título de la oferta de la tutoría a la cual asistió el estudiante, y el Comentario o retroalimentación escrita.
 - El botón 'Ver más reseñas' permanece visible en la parte inferior de la lista, ya que aún quedan reseñas por cargar (ej. 2 reseñas pendientes).

## ID: CP-HU-22-R1-02
**Título:** Verificar carga de todas las reseñas restantes y desaparición del botón 'Ver más reseñas'.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado, en la sección 'Reseñas de Estudiantes' de la pantalla detalle de oferta del tutor que tiene un total de 8 reseñas, de las cuales 6 son visibles y el botón 'Ver más reseñas' está presente.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla detalle de oferta del tutor para un tutor que tenga 8 reseñas en total.
 3. Asegurarse de que la sección 'Reseñas de Estudiantes' muestre 6 de 8 reseñas (puede ser un estado posterior a una carga previa o preconfigurado).
 4. Verificar que se visualiza el texto "Mostrando 6 de 8 reseñas" y que el botón 'Ver más reseñas' es visible.
 5. Hacer clic en el botón 'Ver más reseñas'.

**Expected Results:**
 - La pantalla detalle de oferta del tutor permanece visible.
 - La sección 'Reseñas de Estudiantes' se mantiene visible.
 - La lista de reseñas individuales se expande, mostrando los comentarios adicionales restantes (ej. las últimas 2 reseñas, totalizando 8 reseñas visibles).
 - El texto contador se actualiza dinámicamente a "Mostrando 8 de 8 reseñas".
 - Las nuevas reseñas mostradas incluyen: Iniciales/Avatar del estudiante, Fecha de la reseña, Calificación otorgada en estrellas, título de la oferta de la tutoría a la cual asistió el estudiante, y el Comentario o retroalimentación escrita.
 - El botón 'Ver más reseñas' desaparece de la parte inferior de la lista, ya que todas las reseñas han sido cargadas.

## ID: CP-HU-22-R2-01
**Título:** Verificar la vista inicial de la sección 'Reseñas de Estudiantes' sin interacción adicional.
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado, en la pantalla detalle de oferta del tutor con al menos 3 reseñas disponibles (ej. 8 reseñas en total).

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla detalle de oferta del tutor de un tutor que tenga reseñas disponibles (ej. 8 reseñas en total).
 3. Desplazarse a la sección 'Reseñas de Estudiantes'.
 4. (No realizar ninguna acción adicional en la sección de reseñas).

**Expected Results:**
 - La pantalla detalle de oferta del tutor permanece visible.
 - Se visualiza el encabezado 'Reseñas de Estudiantes'.
 - Se visualiza el resumen de calificaciones, incluyendo la calificación promedio '4.6' con su representación en estrellas (5 estrellas llenas y 1 media estrella), y el texto '8 reseñas'.
 - Se visualizan las barras de desglose de estrellas: '5 estrellas 63%', '4 estrellas 38%', '3 estrellas 0%', '2 estrellas 0%', '1 estrella 0%'.
 - Se visualizan las tres tarjetas de métricas del tutor: '9 Tutorías completadas', '4 Materias impartidas', y '89% Estudiantes que califican'.
 - Se visualiza el texto 'Mostrando 3 de 8 reseñas'.
 - Se visualizan las 3 reseñas individuales mostradas por defecto, que son:
     - `SO` Sofía Mendoza, con 5 estrellas, "Tutoría: Álgebra Lineal", "Juan es el mejor tutor que he tenido. Explica de forma muy clara y directa.", con fecha '28 feb 2026'.
     - `AN` Andrés Morales, con 5 estrellas, "Tutoría: Estática", "Juan explica los problemas paso a paso. Muy recomendado para Estática.", con fecha '25 feb 2026'.
     - `VA` Valeria Sánchez, con 3.5 estrellas, "Tutoría: Física I", "Muy buena clase, aunque empezamos un poco tarde. Los ejercicios fueron muy útiles.", con fecha '18 feb 2026'.
 - El botón 'Ver más reseñas' es visible en la parte inferior de la lista de reseñas.

---

## ID: CP-HU-19-R1
**Título:** Visualización de la Bandeja de Reseñas sin Paginación
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El usuario 'Juan' (Tutor) está logueado en el sistema y tiene un total de 5 o menos reseñas registradas en su perfil.

**Steps:**
 1. Iniciar sesión en el sistema como Tutor (usuario 'Juan').
 2. Navegar a la pestaña superior 'Reseñas' en la cabecera.

**Expected Results:**
 - El sistema permanece en la pantalla 'Bandeja de Reseñas'.
 - La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'.
 - Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'.
 - El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio (ej. '4.6'), un contador 'X reseñas' (donde X es el número total de reseñas <= 5, por ejemplo '5 reseñas'), y el gráfico de barras con la distribución porcentual de estrellas.
 - La sección 'Reseñas detalladas' muestra el texto 'Mostrando 1–X de X reseñas' (donde X es el número total de reseñas <= 5, por ejemplo 'Mostrando 1–5 de 5 reseñas').
 - Se listan las tarjetas de reseñas individuales (máximo 5).
 - El control de paginación numérica ('<', '1', '2', '>') NO se visualiza.

## ID: CP-HU-19-R2
**Título:** Visualización de la Primera Página de Reseñas con Paginación Activa
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El usuario 'Juan' (Tutor) está logueado en el sistema y tiene un total de más de 5 reseñas registradas (ej. 8 reseñas) en su perfil.

**Steps:**
 1. Iniciar sesión en el sistema como Tutor (usuario 'Juan').
 2. Navegar a la pestaña superior 'Reseñas' en la cabecera.

**Expected Results:**
 - El sistema permanece en la pantalla 'Bandeja de Reseñas'.
 - La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'.
 - Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'.
 - El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio '4.6', el texto '8 reseñas', y el gráfico de barras con la distribución porcentual de estrellas.
 - La sección 'Reseñas detalladas' muestra el texto 'Mostrando 1–5 de 8 reseñas'.
 - Se listan las 5 tarjetas de reseñas de la página 1, incluyendo: 'SO Sofía Mendoza' (5 estrellas, 'Tutoría: Álgebra Lineal', 'Juan es el mejor tutor que he tenido. Explica de forma muy clara y directa.', '1 de marzo de 2026'), 'AN Andrés Morales' (5 estrellas, 'Tutoría: Estática', 'Juan explica los problemas paso a paso. Muy recomendado para Estática.', '26 de febrero de 2026'), 'VA Valeria Sánchez' (3.5 estrellas, 'Tutoría: Física I', 'Muy buena clase, aunque empezamos un poco tarde. Los ejercicios fueron muy útiles.', '19 de febrero de 2026'), 'AN Andrés Morales' (5 estrellas, 'Tutoría: Cálculo Vectorial', 'Excelente clase, Juan explica muy bien y tiene mucha paciencia. Logré entender todo para mi examen.', '16 de febrero de 2026'), e 'IS Isabella Mora' (3.5 estrellas, 'Tutoría: Cálculo Vectorial', 'Muy buen tutor. Me ayudó a entender integrales de línea.', '16 de enero de 2026').
 - Se visualiza el control de paginación numérica: el botón '<' está deshabilitado, el botón '1' está resaltado (con fondo oscuro), el botón '2' está activo, y el botón '>' está activo.

## ID: CP-HU-19-R3
**Título:** Navegación Directa a la Segunda Página de Reseñas
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El usuario 'Juan' (Tutor) está logueado en el sistema, tiene más de 5 reseñas registradas (ej. 8 reseñas) y se encuentra visualizando la primera página de su 'Bandeja de Reseñas' con los controles de paginación activos.

**Steps:**
 1. Iniciar sesión en el sistema como Tutor (usuario 'Juan').
 2. Navegar a la pestaña superior 'Reseñas' en la cabecera (asegurándose de estar en la primera página).
 3. Hacer clic en el número de página '2' en el control de paginación.

**Expected Results:**
 - El sistema permanece en la pantalla 'Bandeja de Reseñas'.
 - La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'.
 - Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'.
 - El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio '4.6', el texto '8 reseñas', y el gráfico de barras con la distribución porcentual de estrellas.
 - La sección 'Reseñas detalladas' muestra el texto 'Mostrando 6–8 de 8 reseñas'.
 - Se listan las 3 tarjetas de reseñas de la página 2 (contenido simulado, ya que no visible en la imagen: e.g., 'JU Juan Pérez', 'Tutoría: Álgebra', 'Excelente', '15 de enero de 2026'; 'MA María García', 'Tutoría: Cálculo', 'Muy bueno', '10 de enero de 2026'; 'PE Pedro Lopez', 'Tutoría: Física', 'Mejorable', '5 de enero de 2026').
 - Se visualiza el control de paginación numérica: el botón '<' está activo, el botón '1' está activo, el botón '2' está resaltado (con fondo oscuro), y el botón '>' está deshabilitado.

## ID: CP-HU-19-R4
**Título:** Navegación a la Segunda Página de Reseñas Usando el Botón 'Siguiente' (>)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El usuario 'Juan' (Tutor) está logueado en el sistema, tiene más de 5 reseñas registradas (ej. 8 reseñas) y se encuentra en la primera página de su 'Bandeja de Reseñas' con los controles de paginación activos.

**Steps:**
 1. Iniciar sesión en el sistema como Tutor (usuario 'Juan').
 2. Navegar a la pestaña superior 'Reseñas' en la cabecera (asegurándose de estar en la primera página).
 3. Hacer clic en el botón de flecha '>' (Siguiente) en el control de paginación.

**Expected Results:**
 - El sistema permanece en la pantalla 'Bandeja de Reseñas'.
 - La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'.
 - Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'.
 - El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio '4.6', el texto '8 reseñas', y el gráfico de barras con la distribución porcentual de estrellas.
 - La sección 'Reseñas detalladas' muestra el texto 'Mostrando 6–8 de 8 reseñas'.
 - Se listan las 3 tarjetas de reseñas de la página 2 (contenido simulado: e.g., 'JU Juan Pérez', 'Tutoría: Álgebra', 'Excelente', '15 de enero de 2026'; 'MA María García', 'Tutoría: Cálculo', 'Muy bueno', '10 de enero de 2026'; 'PE Pedro Lopez', 'Tutoría: Física', 'Mejorable', '5 de enero de 2026').
 - Se visualiza el control de paginación numérica: el botón '<' está activo, el botón '1' está activo, el botón '2' está resaltado (con fondo oscuro), y el botón '>' está deshabilitado.

## ID: CP-HU-19-R5
**Título:** Navegación a la Primera Página de Reseñas Usando el Botón 'Anterior' (<)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El usuario 'Juan' (Tutor) está logueado en el sistema, tiene más de 5 reseñas registradas (ej. 8 reseñas) y se encuentra visualizando la segunda página de su 'Bandeja de Reseñas' con los controles de paginación activos.

**Steps:**
 1. Iniciar sesión en el sistema como Tutor (usuario 'Juan').
 2. Navegar a la pestaña superior 'Reseñas' en la cabecera.
 3. Asegurar que la pantalla muestre la segunda página de reseñas (esto implica haber navegado previamente a la página 2, ya sea directamente o con el botón '>').
 4. Hacer clic en el botón de flecha '<' (Anterior) en el control de paginación.

**Expected Results:**
 - El sistema permanece en la pantalla 'Bandeja de Reseñas'.
 - La cabecera superior se mantiene con los elementos 'Poli Tutorías', 'Panel', 'Bandeja', 'Mi Agenda', 'Historial', 'Reseñas' (resaltado), 'Juan' y 'Salir'.
 - Se visualiza el título 'Bandeja de Reseñas' y el subtítulo 'Lo que los estudiantes dicen sobre tus tutorías'.
 - El cuadro 'Resumen de Calificaciones' se muestra con la calificación promedio '4.6', el texto '8 reseñas', y el gráfico de barras con la distribución porcentual de estrellas.
 - La sección 'Reseñas detalladas' muestra el texto 'Mostrando 1–5 de 8 reseñas'.
 - Se listan las 5 tarjetas de reseñas de la página 1, incluyendo: 'SO Sofía Mendoza' (5 estrellas, 'Tutoría: Álgebra Lineal', 'Juan es el mejor tutor que he tenido. Explica de forma muy clara y directa.', '1 de marzo de 2026'), 'AN Andrés Morales' (5 estrellas, 'Tutoría: Estática', 'Juan explica los problemas paso a paso. Muy recomendado para Estática.', '26 de febrero de 2026'), 'VA Valeria Sánchez' (3.5 estrellas, 'Tutoría: Física I', 'Muy buena clase, aunque empezamos un poco tarde. Los ejercicios fueron muy útiles.', '19 de febrero de 2026'), 'AN Andrés Morales' (5 estrellas, 'Tutoría: Cálculo Vectorial', 'Excelente clase, Juan explica muy bien y tiene mucha paciencia. Logré entender todo para mi examen.', '16 de febrero de 2026'), e 'IS Isabella Mora' (3.5 estrellas, 'Tutoría: Cálculo Vectorial', 'Muy buen tutor. Me ayudó a entender integrales de línea.', '16 de enero de 2026').
 - Se visualiza el control de paginación numérica: el botón '<' está deshabilitado, el botón '1' está resaltado (con fondo oscuro), el botón '2' está activo, y el botón '>' está activo.