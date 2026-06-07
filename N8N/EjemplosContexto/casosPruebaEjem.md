
---

# Historias de Usuario - Proyecto PoliTutorías

## Nro. HU03 - Título: Publicar oferta

#### Criterios de aceptación HU03

| **Escenario** | **Descripción** |
| --- | --- |
| **Publicación Exitosa de Tutoría** | <br>**Dado** que el tutor está en la interfaz de Publicación de Tutorías , **cuando** selecciona los campos de Carrera, Materia, Modalidad, Indicaciones, Precio, Descripción y sube una imagen , **entonces** el sistema crea la tutoría y muestra el mensaje "La publicación ha sido creada exitosamente" con un botón para ir a sus ofertas.
| **Bloqueo por Publicación Duplicada** | <br>**Dado** que el tutor ya tiene una oferta publicada con la misma Carrera y Materia , **cuando** intenta crear otra igual , **entonces** el sistema no la publica y muestra el mensaje "Ya existe una oferta para esta Carrera y Materia".
| **Bloqueo por Precio Negativo** | <br>**Dado** que el tutor está en la interfaz , **cuando** ingresa un precio negativo (ej: -5.00) , **entonces** el sistema no publica la tutoría y muestra "El Precio debe ser un valor numérico positivo".
| **Bloqueo por Descripción Demasiado Corta** | <br>**Dado** que el tutor está en la interfaz , **cuando** ingresa una descripción de menos de 50 caracteres , **entonces** el sistema muestra "La descripción debe contener un mínimo de 50 y un máximo de 500 caracteres".
| **Bloqueo de Selección de Materia** | <br>**Dado** que el tutor está en la interfaz , **cuando** no selecciona nada en el campo Carrera , **entonces** el combo box de Materia debe estar deshabilitado.
| **Bloqueo Campo Obligatorio** | <br>**Dado** que el tutor está en la interfaz , **cuando** no llena los campos obligatorios y hace clic en "Guardar" , **entonces** se muestra el mensaje "Por favor llena los campos obligatorios".
| **Bloqueo por Indicaciones Cortas** | <br>**Dado** que el tutor está en la interfaz , **cuando** ingresa indicaciones de menos de 20 caracteres , **entonces** el sistema muestra "Las indicaciones deben contener un mínimo de 20 y un máximo de 100 caracteres".
| **Abandono de Formulario** | <br>**Dado** que el tutor está llenando el formulario , **cuando** hace clic en "Cancelar" , **entonces** el sistema pregunta "¿Estás seguro de cancelar la publicación de la oferta?" con opciones de Si y No.


---

## Nro. HU04 - Título: Ver mis tutorías ofertadas

#### Criterios de aceptación HU04

| **Escenario** | **Descripción** |
| --- | --- |
| **Visualización de Tarjeta** | <br>**Dado** que el tutor tiene ofertas registradas , **cuando** accede a “Mis Ofertas” , **entonces** la lista muestra una tarjeta con materia, carrera, descripción, precio, fecha y modalidad.
| **Estado Inicial sin Ofertas** | <br>**Dado** que el tutor no ha registrado publicaciones , **cuando** revisa la lista , **entonces** la lista está vacía y muestra “Aún no has publicado ninguna oferta”.
| **Límite de paginación** | <br>**Dado** que el tutor tiene 12 ofertas , **cuando** accede a la sección , **entonces** la página muestra 10 ofertas y la paginación indica Página 1 de 2.
| **Ingreso a Publicar** | <br>**Dado** que el tutor está en “Mis Ofertas” , **cuando** hace clic en “Publicar Oferta” , **entonces** es redirigido a la sección de publicación.


---

## Nro. HU013 - Título: Ver ofertas de tutorías

#### Criterios de aceptación HU13

| **Escenario** | **Descripción** |
| --- | --- |
| **Visualización de Tarjetas** | <br>**Dado** que el estudiante está en "Encuentra tu Tutoría" con ofertas disponibles , **cuando** revisa la lista , **entonces** se muestra la tarjeta con toda la información de la oferta y su imagen.
| **Estado Inicial sin Ofertas** | <br>**Dado** que no existen ofertas publicadas , **cuando** el estudiante revisa la lista , **entonces** se muestra el mensaje "Aún no hay ofertas disponibles".

---

## Nro. HU14 - Título: Buscar ofertas por materia

#### Criterios de aceptación HU14

| **Escenario** | **Descripción** |
| --- | --- |
| **Búsqueda Exitosa** | <br>**Dado** que existen ofertas publicadas , **cuando** el estudiante ingresa una materia (ej: "Cálculo") y busca , **entonces** la lista se filtra y muestra las ofertas coincidentes.
| **Búsqueda Vacía** | <br>**Dado** que el estudiante está en la sección , **cuando** deja el campo vacío y busca , **entonces** la lista no cambia y muestra "Por favor ingresa el nombre de una materia o el de un tutor".
| **Caracteres Especiales** | <br>**Dado** que el estudiante está en la sección , **cuando** ingresa caracteres especiales (ej: "#") , **entonces** el sistema muestra "No se permiten caracteres especiales".

 

---

## Nro. HU19 - Título: Ver detalles de la oferta

#### Criterios de aceptación HU19

| **Escenario** | **Descripción** |
| --- | --- |
| **Navegación al Detalle** | <br>**Dado** que el estudiante está en la sección de búsqueda , **cuando** hace clic en una tarjeta de tutoría , **entonces** es redirigido a la ventana de Detalle de la Tutoría.
| **Ver Detalle Completo** | <br>**Dado** que el estudiante está en la interfaz de detalle , **cuando** revisa la información , **entonces** se muestra: materia, carrera, nombre del tutor, foto, descripción, lugar, precio y contacto.

---

## Nro. HU01 - Título: Seleccionar horas disponibles

#### Criterios de aceptación HU01

| **Escenario** | **Descripción** |
| --- | --- |
| **Seleccionar Disponibilidad** | <br>**Dado** que el tutor está en "Mi Horario" , **cuando** hace clic en bloques de tiempo , **entonces** el bloque cambia de color con la palabra "Disponible".
| **Marcado y Desmarcado** | <br>**Dado** que el tutor tiene bloques seleccionados , **cuando** vuelve a hacer clic sobre ellos , **entonces** vuelven a blanco y se quita la palabra "Disponible".
| **Guardar Horario** | <br>**Dado** que el tutor seleccionó bloques , **cuando** hace clic en "Guardar" , **entonces** el sistema guarda la disponibilidad y muestra un modal de éxito.
| **Bloqueo al Guardar** | <br>**Dado** que el tutor no ha seleccionado ningún bloque , **cuando** hace clic en "Guardar" , **entonces** el sistema muestra "Por favor seleccionar un horario".



---

## Nro. HU02 - Título: Ver mi horario

#### Criterios de aceptación HU02

| **Escenario** | **Descripción** |
| --- | --- |
| **Visualización de Horario** | <br>**Dado** que el tutor guardó su disponibilidad previamente , **cuando** accede a "Mi Horario" , **entonces** los bloques guardados deben aparecer resaltados y como "Disponible".


---

## Nro. HU24 - Título: Enviar solicitud de tutoría

#### Criterios de aceptación HU24

| **Escenario** | **Descripción** |
| --- | --- |
| **Selección y Cálculo** | <br>**Dado** que el estudiante está en el detalle , **cuando** selecciona bloques de tiempo , **entonces** el componente "Tu Elección" y el "Total" se actualizan automáticamente.
| **Bloqueo sin Fecha/Hora** | <br>**Dado** que no se ha seleccionado fecha ni hora , **cuando** intenta solicitar , **entonces** se muestra "Por favor, selecciona una fecha y hora".
| **Método de Pago** | <br>**Dado** que se seleccionaron las horas , **cuando** no selecciona método de pago y solicita , **entonces** se muestra “Por favor selecciona un método de pago”.
| **Botón Solicitar** | <br>**Dado** que completó la selección , **cuando** hace clic en "Solicitar" , **entonces** se muestra el modal "Planifica tu tutoría" con el resumen y formulario para el tutor.
| **Enviar Solicitud** | <br>**Dado** que está en el modal de planificación , **cuando** ingresa mensaje y datos de contacto y envía , **entonces** se muestra un modal de éxito con el mensaje "La tutoría se ha solicitado exitosamente".
| **Bloqueo Mensaje Largo** | <br>**Dado** que está en el modal , **cuando** el mensaje excede los 150 caracteres , **entonces** se muestra “Solo se permiten 150 caracteres en el mensaje".
| **Campos Obligatorios** | <br>**Dado** que está en el modal , **cuando** deja Correo o Teléfono vacíos , **entonces** se muestra el mensaje "Este campo es obligatorio".

---

## Nro. HU26 - Título: Consultar lista de solicitudes enviadas

#### Criterios de aceptación HU26

| **Escenario** | **Descripción** |
| --- | --- |
| **Visualización** | <br>**Dado** que el estudiante envió una solicitud previa , **cuando** revisa "Mis Solicitudes" , **entonces** la tabla muestra materia, tutor, horario, costo, modalidad y estado "Pendiente".
| **Sin Solicitudes** | <br>**Dado** que no ha enviado solicitudes , **cuando** revisa la sección , **entonces** se muestra el mensaje "No hay solicitudes disponibles".

---

## Nro. HU45 - Título: Cancelar una solicitud enviada

#### Criterios de aceptación HU45

| **Escenario** | **Descripción** |
| --- | --- |
| **Navegación a Cancelar** | <br>**Dado** que tiene una solicitud "Pendiente" , **cuando** hace clic en "Cancelar" , **entonces** se abre un modal con motivos obligatorios y campo de mensaje opcional.
| **Cancelación Exitosa** | <br>**Dado** que está en el modal , **cuando** elige un motivo y confirma , **entonces** se muestra el modal de "Solicitud Cancelada".
| **Bloqueo sin Motivo** | <br>**Dado** que está en el modal , **cuando** no selecciona un motivo y confirma , **entonces** se muestra el mensaje "Por favor elije un motivo".

---

## Nro. HU05 - Título: Consultar solicitudes recibidas

#### Criterios de aceptación HU05

| **Escenario** | **Descripción** |
| --- | --- |
| **Ver Solicitud** | <br>**Dado** que el tutor tiene solicitudes , **cuando** revisa la tabla , **entonces** ve nombre del estudiante, materia, fecha, horario y estado "Pendiente".
| **Estado Conflicto** | <br>**Dado** que tiene dos solicitudes en el mismo horario , **cuando** revisa la tabla , **entonces** el estado de ambas debe mostrarse como "Conflicto".
| **Estado Expirado** | <br>**Dado** que pasó la fecha de la tutoría , **cuando** revisa la tabla , **entonces** el estado se muestra como "Expirado".
| **Detalle de Solicitud** | <br>**Dado** que está en la sección de solicitudes , **cuando** hace clic en “Ver Detalles” , **entonces** es redirigido a la vista de detalle con toda la información y el mensaje del estudiante.


---

## Nro. HU06 - Título: Confirmar una solicitud de tutoría

#### Criterios de aceptación HU06

| **Escenario** | **Descripción** |
| --- | --- |
| **Confirmar solicitud** | <br>**Dado** que el tutor está en "Detalle de la Solicitud" , **cuando** hace clic en “Confirmar” , **entonces** se muestra el mensaje "Tutoría Confirmada" con el resumen completo y datos de contacto del estudiante.


---

## Nro. HU36 - Título: Rechazar solicitud de tutoría por tutor

#### Criterios de aceptación HU36

| **Escenario** | **Descripción** |
| --- | --- |
| **Rechazar solicitud** | <br>**Dado** que el tutor está en "Detalle de la Solicitud" , **cuando** hace clic en "Rechazar" , **entonces** se muestra un modal de rechazo con motivos obligatorios y mensaje opcional.
| **Rechazo Exitoso** | <br>**Dado** que está en el modal de rechazo , **cuando** selecciona motivo y confirma , **entonces** se muestra el modal de "Solicitud Cancelada".
| **Bloqueo sin Motivo** | <br>**Dado** que está en el modal , **cuando** no elige motivo y confirma , **entonces** se muestra "Por favor elije un motivo".



---

## Nro. HU07 - Título: Consultar agenda de tutorías

#### Criterios de aceptación HU07

| **Escenario** | **Descripción** |
| --- | --- |
| **Ver Calendario** | <br>**Dado** que el tutor aceptó una solicitud , **cuando** presiona en "Agendadas" , **entonces** se muestra un horario semanal con el bloque correspondiente en color verde.
| **Detalle desde Agenda** | <br>**Dado** que ve el bloque verde en la agenda , **cuando** presiona sobre él , **entonces** se muestra el modal "Detalle de la tutoría" con datos del estudiante y botón para cancelar.


---

## Nro. HU09 - Título: Consultar historial de tutorías por tutor

#### Criterios de aceptación HU09

| **Escenario** | **Descripción** |
| --- | --- |
| **Historial con Reseña** | <br>**Dado** que el tutor está en "Historial" y recibió una reseña , **cuando** revisa la tabla , **entonces** se muestra el estado "Finalizada", las estrellas obtenidas y la opción "Ver Detalles".
| **Detalles de Reseña** | <br>**Dado** que selecciona una tutoría con reseña , **cuando** hace clic en "Ver Detalles" , **entonces** se muestra el nombre del estudiante, calificación y el comentario escrito.
| **Resumen de Actividad** | <br>**Dado** que el tutor ha impartido tutorías , **cuando** revisa la sección de métricas , **entonces** se muestran tarjetas con Ingresos Totales, Horas Totales y Tasa de Cumplimiento.


---

## Nro. HU27 - Título: Consultar historial de tutorías por estudiante

#### Criterios de aceptación HU27

| **Escenario** | **Descripción** |
| --- | --- |
| **Ver Historial** | <br>**Dado** que el estudiante recibió tutorías , **cuando** revisa "Historial" , **entonces** se muestra el resumen de actividad y la tabla con los estados correspondientes.
| **Detalles tras Calificar** | <br>**Dado** que el estudiante ya calificó una tutoría , **cuando** vuelve a revisar esa entrada , **entonces** se muestran sus estrellas y la opción "Ver Detalles".
| **Volver a Reservar** | <br>**Dado** que la tutoría fue finalizada y calificada , **cuando** hace clic en el botón "Volver a reservar" , **entonces** es redirigido al detalle de esa tutoría.


---

## Nro. HU28 - Título: Publicar reseña sobre el tutor

#### Criterios de aceptación HU28

| **Escenario** | **Descripción** |
| --- | --- |
| **Botón de Reseña** | <br>**Dado** que tiene una tutoría "Finalizada" sin reseña , **cuando** revisa su historial , **entonces** aparece habilitado el botón "Escribir Reseña".
| **Formulario de Reseña** | <br>**Dado** que hace clic en el botón , **cuando** se abre el modal , **entonces** se muestra la identificación del tutor, las estrellas para calificar y el campo de comentario opcional.
| **Envío Exitoso** | <br>**Dado** que seleccionó estrellas y presionó enviar , **entonces** se muestra el mensaje "Reseña enviada exitosamente".

 |

---

