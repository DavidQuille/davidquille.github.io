# Reporte de Escenarios Generados (S1)
> Generado el: 25/2/2026

### Nro. HU-34 - Título: Registrar información del tutor 

#### Criterios de aceptación HU-34

| Escenario | Descripción |
|---|---|
| **Registro exitoso de Datos Básicos** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil<br>**cuando** ingresa en el campo 'Nombre Completo': 'Daniela Castro', ingresa en el campo 'Número de WhatsApp': '593991234567', selecciona en el dropdown 'Facultad': 'FIS - Sistemas', selecciona en el dropdown 'Semestre Actual': '4° Semestre', ingresa en el campo 'Biografía Corta': 'Tengo 5 años de experiencia en desarrollo de software y disfruto enseñar algoritmos.', y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema redirige a '2 Disponibilidad' resaltado, el título 'Define tu Horario', el subtítulo 'Selecciona los bloques horarios en los que puedes dar clases', una cuadrícula con encabezados ('Lun' a 'Dom', '7:00' a '20:00') y el botón 'Siguiente Perfil Profesional'. |
| **Validación de campos obligatorios vacíos** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** deja los campos 'Nombre Completo', 'Número de WhatsApp', 'Facultad', 'Semestre Actual', y 'Biografía Corta' vacíos, y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema permanece en la pantalla, muestra el mensaje de error 'El nombre es obligatorio' debajo de 'Nombre Completo', el mensaje de error 'El número de WhatsApp es obligatorio' debajo de 'Número de WhatsApp', el mensaje de error 'Selecciona tu facultad' debajo del dropdown 'Facultad', el mensaje de error 'Selecciona tu semestre' debajo del dropdown 'Semestre Actual', y el mensaje de error 'La biografía es obligatoria' debajo de 'Biografía Corta'. |
| **Validación de Nombre Completo - Mínimo de caracteres** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** ingresa en el campo 'Nombre Completo': 'Jo', y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema permanece en la pantalla y muestra el mensaje en rojo 'Mínimo 3 caracteres' debajo de 'Nombre Completo'. |
| **Validación de Nombre Completo - Máximo de caracteres** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** ingresa en el campo 'Nombre Completo' 'Este es un nombre muy largo que definitivamente excede los sesenta caracteres para una prueba de longitud máxima' que excede los 60 caracteres <br>**entonces** el sistema limita el ingreso a 60 caracteres, muestra el contador '60/60' debajo del campo 'Nombre Completo', y no permite más digitación ni pegar texto. |
| **Validación de Nombre Completo - Caracteres no permitidos** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** intenta ingresar números o caracteres especiales (ej: 'Juan123$' o 'María@!') en el campo 'Nombre Completo', y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema bloquea el ingreso, y los caracteres no permitidos (números y especiales) no aparecen en la pantalla, permitiendo solo letras y espacios. |
| **Validación de Número de WhatsApp - Mínimo de dígitos** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** ingresa en el campo 'Número de WhatsApp' un número con menos de 10 dígitos (ej: '593991234'), y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema permanece en la pantalla y muestra el mensaje en rojo 'Ingresa un número válido (10-13 dígitos)' debajo del campo 'Número de WhatsApp'. |
| **Validación de Número de WhatsApp - Máximo de dígitos** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** ingresa en el campo 'Número de WhatsApp' un número con más de 13 dígitos (ej: '59399123456789'), y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema permanece en la pantalla y muestra el mensaje en rojo 'Ingresa un número válido (10-13 dígitos)' debajo del campo 'Número de WhatsApp'. |
| **Validación de Número de WhatsApp - Caracteres no numéricos** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** intenta ingresar letras o caracteres especiales (ej: '593abcd123' o '593-99123') en el campo 'Número de WhatsApp', y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema bloquea el ingreso, y las letras y caracteres especiales no aparecen en la pantalla, permitiendo solo números. |
| **Validación de Biografía Corta - Mínimo de caracteres** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil" <br>**cuando** ingresa en el campo 'Biografía Corta' un texto con menos de 20 caracteres (ej: 'Soy un tutor nuevo.'), y hace clic en el botón 'Siguiente Disponibilidad'<br>**entonces** el sistema permanece en la pantalla y muestra el mensaje en rojo 'Mínimo 20 caracteres' debajo de 'Biografía Corta'. |
| **Validación de Biografía Corta - Máximo de caracteres** | **Dado** que el tutor se encuentra en la interfaz de "Completa tu Perfil"<br>**cuando** ingresa en el campo 'Biografía Corta' 'Este es un texto de biografía muy extenso diseñado específicamente para superar el límite de trescientos caracteres y comprobar que el sistema bloquea correctamente cualquier intento de ingreso adicional una vez alcanzado el tope máximo permitido por el contador' que excede los 300 caracteres<br>**entonces** el sistema limita el ingreso a 300 caracteres, muestra el contador '300/300' debajo del campo 'Biografía Corta', y no permite más digitación ni pegar texto. |
---

### Nro. HU-41 - Título: Registrar mi disponibilidad

#### Criterios de aceptación HU-341
| Escenario | Descripción |
|---|---|
| **Bloqueo sin selección de horario** | **Dado** que el tutor se encuentra en la interfaz de "Define tu Horario" <br>**cuando** no ha seleccionado ningún bloque de horario en la cuadrícula y hace clic en el botón 'Siguiente Perfil Profesional'<br>**entonces** el sistema bloquea la navegación y muestra el texto rojo 'Selecciona al menos un horario disponible' encima de la cuadrícula. |
| **Selección de bloques horarios** | **Dado** que el tutor se encuentra en la interfaz de "Define tu Horario" <br>**cuando** hace clic en un bloque de horario en la cuadrícula Lun a  09:00 <br>**entonces** el bloque horario seleccionado cambia visualmente de color blanco a azul oscuro y muestra un ícono '✓' blanco en el centro, y aparece el texto verde centrado sobre la cuadrícula: '✓ 1 horario seleccionado'. |
| **Avance a Perfil Profesional con horario seleccionado** | **Dado** que el tutor se encuentra en la interfaz de "Define tu Horario" y ha seleccionado al menos un bloque de horario Mar a las  10:00<br>**cuando** hace clic en el botón 'Siguiente Perfil Profesional'<br>**entonces** el sistema redirige  '3 Perfil Profesional' resaltado, el título 'Detalles Profesionales', el subtítulo 'Añade tu experiencia y materias para destacar', y el botón 'Finalizar Registro'. |
| **Deselección de bloques horarios** | **Dado** que el tutor se encuentra en la interfaz de "Define tu Horario" y tiene bloques de horario previamente seleccionados ej: 'Mié de 11:00' y 'Mié de 12:00', mostrando '✓ 2 horarios seleccionados')<br>**cuando** vuelve a hacer clic en un bloque horario ya marcado (ej: 'Miércoles 11:00')<br>**entonces** el bloque horario vuelve a ser blanco, el ícono '✓' desaparece, y el contador superior verde disminuye su número en tiempo real (ej: mostrando '✓ 1 horario seleccionado'). |
| **Navegabilidad hacia atrás: Del Paso 2 al 1** | **Dado** que el tutor se encuentra en la interfaz de "Define tu Horario" <br>**cuando** hace clic en el botón inferior izquierdo de '← Atrás Datos Básicos' o en el paso '1 Datos Básicos' del menú superior<br>**entonces** el sistema redirige a la pantalla del Paso 1, conservando intacta toda la información previamente ingresada por el usuario en los campos. | 


---
### Nro. HU-42 - Título: Registrar información académica

#### Criterios de aceptación HU-42
| Escenario | Descripción |
|---|---|
| **Ignorar Guardar Experiencia Vacía** | **Dado** que el tutor se encuentra en la interfaz de "Detalles Profesionales"  y ha abierto el modal de 'Nueva Experiencia' (al hacer clic en '+ Añadir Experiencia')<br>**cuando** deja todos los campos del modal 'Nueva Experiencia' (ej. Puesto, Institución, Fechas) vacíos y hace clic en el botón 'Guardar' dentro del modal<br>**entonces** la acción de guardar se ignora silenciosamente, no aparece ningún mensaje de error, y el modal 'Nueva Experiencia' permanece en pantalla. |
| **Validar Formato de Fecha MM/AAAA** | **Dado** que el tutor se encuentra en la interfaz de "Detalles Profesionales" en el campo "Nueva Experiencia" y está ingresando fechas en un campo de 'Fecha Inicio' o 'Fecha Fin'<br>**cuando** ingresa una fecha en el formato MM/AAAA (ej: '03/2024')<br>**entonces** el sistema valida y mantiene el formato de la fecha (ej: '03/2024'). |
| **Bloquear Caracteres No-Numéricos en Fecha** | **Dado** que el tutor se encuentra en la interfaz de "Detalles Profesionales"y está ingresando fechas en un campo de experiencia (ej: 'Fecha Inicio' o 'Fecha Fin')<br>**cuando** intenta ingresar Hola en los campos de fecha  o intenta ingresar algo distinto a 'Presente' en 'Fecha Fin'<br>**entonces** el sistema bloquea el ingreso, y las letras y signos no se muestran, permitiendo solo números. En el campo 'Fecha Fin', permite la palabra exacta 'Presente'. |
| **Validar Máximo Caracteres en Fecha** | **Dado** que el tutor se encuentra en la interfaz de "Detalles Profesionales"  y está ingresando una fecha en un campo de experiencia (ej: 'Fecha Inicio' o 'Fecha Fin')<br>**cuando** ingresa la fecha '12/20255' que excede los 7 caracteres del formato MM/AAAA <br>**entonces** el sistema muestra el mensaje de error en rojo 'Máximo 7 caracteres' debajo del campo de fecha. |
| **Añadir Materia como Etiqueta** | **Dado** que el tutor se encuentra en la interfaz de "Detalles Profesionales"  y está en la sección para añadir materias<br>**cuando** ingresa 'Cálculo' en el campo 'Escribe una Materia(Ej. Cálculo, Física...)' y hace clic en el botón '+ Agregar'<br>**entonces** el sistema limpia el campo de texto y crea un elemento visual (etiqueta o 'pill') de color celeste claro con el texto de la materia (ej: 'Cálculo') y una 'x' a la derecha que permite eliminar. |
| **Finalización Exitosa del Registro** | **Dado** que el tutor se encuentra en la interfaz de "Detalles Profesionales"  y ha completado los pasos anteriores<br>**cuando** hace clic en el botón 'Finalizar Registro' (habiendo llenado o dejado vacíos los campos opcionales)<br>**entonces** el sistema finaliza el proceso sin errores y muestra una pantalla con el mensaje "¡Perfil creado! Ahora puedes publicar tus ofertas de tutorías."  | 
| **Navegabilidad hacia atrás: Del Paso 3 al 2** | **Dado** que el tutor se encuentra en la interfaz de "Detalles Profesionales" <br>**cuando** hace clic en el botón inferior izquierdo de '← Atrás Disponibilidad' o en el paso '2 Disponibilidad' del menú superior<br>**entonces** el sistema redirige a la pantalla del Paso 2, conservando intactos todos los bloques horarios previamente seleccionados en la cuadrícula. |

---

### Nro. HU-07 - Título: Consultar mi disponibilidad

#### Criterios de aceptación HU-07

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización de Horario Registrado** | **Dado** que el tutor tiene disponibilidad registrada previamente en el sistema, <br> **cuando** accede a la interfaz 'Gestionar Disponibilidad', <br> **entonces** la pantalla carga correctamente mostrando en la cabecera el texto 'Volver al Panel' a la izquierda y el logo 'Poli Tutorías' a la derecha. El título 'Gestionar Disponibilidad', la descripción 'Haz clic en los horarios que tienes disponibles para ofrecer tutorías.' y la sub-descripción 'Tu horario se mostrará en la zona horaria local (GMT-5).' son visibles. Se muestra el contador '✓ 4 horarios seleccionados' en color verde. La cuadrícula de horarios desde las 7:00 hasta las 20:00 con las columnas 'HORA', 'Lun', 'Mar', 'Mié', 'Jue', 'Vie', 'Sáb', 'Dom' presenta los bloques 'Lun 12:00', 'Mar 12:00', 'Lun 19:00' y 'Mar 19:00' resaltados con un checkmark blanco sobre fondo oscuro, indicando su selección. Los botones 'Cancelar' y 'Guardar Cambios' están visibles pero deshabilitados. |
| **Navegación a Panel de Control** | **Dado** que el tutor se encuentra en la interfaz 'Gestionar Disponibilidad', <br> **cuando** hace clic en el enlace 'Volver al Panel', <br> **entonces** es redirigido a la pantalla del Dashboard Tutor. |

---

### Nro. HU-32 - Título: Ver detalles de la oferta

#### Criterios de aceptación HU-32

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización de Detalles de Oferta** | **Dado** que el estudiante está en la sección de búsqueda de tutorías <br> **cuando** hace clic en una tarjeta de oferta <br> **entonces** se carga la información detallada de la oferta, mostrando en la cabecera el botón 'Volver' a la izquierda y el logo 'PoliTutorias' a la derecha. La sección principal muestra el icono de libro junto al título de la materia 'Cálculo Vectorial', la modalidad 'Virtual y Presencial', una descripción de la clase, las 'Categorías' con los tags 'Matemática' y 'Formación Básica', y la 'Disponibilidad Semanal' con los horarios para Lunes de 14:00 a 15:00, Miércoles de 14:00 a 15:00 y Viernes de 09:00 a 10:00. En el panel lateral, se visualiza el 'Precio por hora' de $10. |
| **Regreso a la Lista de Ofertas** | **Dado** que el estudiante está visualizando los detalles de una oferta de tutoría <br> **cuando** hace clic en el botón 'Volver' en la cabecera superior izquierda <br> **entonces** es redirigido a la pantalla principal de listado de ofertas. |

---

### Nro. HU-05 - Título: Ver información sobre el tutor

#### Criterios de aceptación HU-05

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización de Perfil del Tutor** | **Dado** que el estudiante está en la interfaz de Detalle de la Oferta <br> **cuando** revisa la información del tutor <br> **entonces** se muestran las secciones 'Sobre el Tutor' y 'Experiencia'.<br>En la sección 'Sobre el Tutor', se visualiza la imagen de perfil del tutor, su nombre (ej: 'Juan Pérez'), su información académica (ej: 'FIM - Mecánica ☁️ 9° Semestre', su descripción bibliográfica (ej: 'Soy un apasionado por la mecánica y las matemáticas aplicadas...') y las materias que domina listadas como tags (ej: 'Cálculo Vectorial', 'Física I', 'Estática', 'Dinámica', 'Termodinámica').<br>En la sección 'Experiencia', se muestran las entradas de historial con el rol, institución/lugar y fechas (ej: 'Ayudante de Cátedra - Estática, EPN, Facultad de Mecánica, 2024 — Presente' y 'Tutor Particular - Cálculo y Física, Independiente, 2023 — Presente'). |

---

### Nro. HU-27 - Título: Filtrar ofertas por precio

#### Criterios de aceptación HU-27

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Filtrado Exitoso por Precio** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" con ofertas disponibles, <br> **cuando** ajusta el slider de "Precio" a un rango (ej: de '$5.00' a '$20.00') que contiene ofertas, <br> **entonces** el listado de ofertas se actualiza mostrando solo las que están dentro del rango de precio seleccionado y el slider refleja los valores de '$5.00' a '$20.00'. |
| **Filtrado Sin Coincidencias** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" con ofertas disponibles, <br> **cuando** ajusta el slider de "Precio" a un rango (ej: de '$1' a '$4') que no contiene ofertas, <br> **entonces** la lista de ofertas se vacía y se muestra el mensaje 'No se encontraron ofertas. Intenta ajustar tus filtros de búsqueda.'. |
| **Visualización de Etiqueta de Precio** | **Dado** que el estudiante ha filtrado las ofertas por un rango de precio (ej: '$8 - $16')<br>**cuando** visualiza la parte superior del listado de ofertas<br>**entonces** el sistema muestra una etiqueta verde claro con el texto del rango y una 'x' (ej: '$8 - $16 x'), junto con el botón 'Limpiar todos'. | 
| **Remoción de Filtro de Precio** | **Dado** que el estudiante tiene activo el filtro de precio y visualiza la etiqueta correspondiente (ej: '$8 - $16 x')<br>**cuando** hace clic en la 'x' de la etiqueta o en el botón 'Limpiar todos'<br>**entonces** el filtro de precio se elimina, la etiqueta desaparece y el listado se actualiza mostrando las ofertas sin este filtro. |

---

### Nro. HU-26 - Título: Filtrar ofertas por modalidad

#### Criterios de aceptación HU-26

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Filtrar por Todas las Modalidades** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" y existen ofertas disponibles <br> **cuando** hace clic en el botón filtro 'Todas' en la sección 'Modalidad' <br> **entonces** el listado de ofertas se muestra sin restricción de modalidad y el botón 'Todas' aparece visualmente resaltado. |
| **Filtrar por Modalidad Presencial** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" y existen ofertas disponibles con diferentes modalidades <br> **cuando** hace clic en el botón filtro 'Presencial' en la sección 'Modalidad' <br> **entonces** el listado de ofertas se actualiza mostrando aquellas que tienen las modalidades 'Presencial' y 'Ambos', y excluye las ofertas únicamente 'Virtual'. |
| **Filtrar por Modalidad Virtual** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" y existen ofertas disponibles con diferentes modalidades <br> **cuando** hace clic en el botón filtro 'Virtual' en la sección 'Modalidad' <br> **entonces** el listado de ofertas se actualiza mostrando aquellas que tienen las modalidades 'Virtual' y 'Ambos', y excluye las ofertas únicamente 'Presencial'. |
| **Filtrar por Modalidad Ambos** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" y existen ofertas disponibles con modalidad 'Ambos' <br> **cuando** hace clic en el botón filtro 'Ambos' en la sección 'Modalidad' <br> **entonces** el listado de ofertas se actualiza mostrando únicamente las ofertas que tienen la modalidad 'Ambos'. |
| **Visualización de Etiqueta de Modalidad** | **Dado** que el estudiante ha filtrado las ofertas por una modalidad (ej: 'Virtual')<br>**cuando** visualiza la parte superior del listado de ofertas<br>**entonces** el sistema muestra una etiqueta morada claro con el texto de la modalidad y una 'x' (ej: 'Virtual x'), junto con el botón 'Limpiar todos'. |
 | **Remoción de Filtro de Modalidad** | **Dado** que el estudiante tiene activo el filtro de modalidad y visualiza la etiqueta correspondiente (ej: 'Virtual x')<br>**cuando** hace clic en la 'x' de la etiqueta o en el botón 'Limpiar todos'<br>**entonces** el filtro de modalidad se elimina, la etiqueta desaparece y el listado se actualiza mostrando las ofertas sin este filtro. |

---

### Nro. HU-16 - Título: Filtrar ofertas por disponibilidad

#### Criterios de aceptación HU-16

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Visualización Inicial sin Filtro** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría"<br>**cuando** no selecciona ningún día de la semana en la sección "Disponibilidad"<br>**entonces** el sistema muestra todas las ofertas de la base de datos sin restricciones de día. |
| **Filtrado Exitoso por Día** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" con ofertas disponibles para el día seleccionado<br>**cuando** selecciona el día 'Mar' en la sección "Disponibilidad"<br>**entonces** el botón 'Mar' aparece resaltado y la lista de ofertas se filtra mostrando únicamente las que tienen disponibilidad ese día. |
| **Sin Ofertas para el Día Seleccionado** | **Dado** que el estudiante se encuentra en la interfaz de "Encuentra tu Tutoría" pero no existen ofertas disponibles para el día seleccionado<br>**cuando** selecciona el día 'Dom' en la sección "Disponibilidad"<br>**entonces** la lista de ofertas se vacía y se muestra el mensaje "No se encontraron ofertas. Intenta ajustar tus filtros de búsqueda". |
| **Visualización de Etiqueta de Disponibilidad** | **Dado** que el estudiante ha filtrado las ofertas seleccionando un día de disponibilidad (ej: 'Mié')<br>**cuando** visualiza la parte superior del listado de ofertas<br>**entonces** el sistema muestra una etiqueta naranja claro con el texto del día y una 'x' (ej: 'Mié x'), junto con el botón 'Limpiar todos'. | 
| **Remoción de Filtro de Disponibilidad** | **Dado** que el estudiante tiene activo el filtro de disponibilidad y visualiza la etiqueta correspondiente (ej: 'Mié x')<br>**cuando** hace clic en la 'x' de la etiqueta o en el botón 'Limpiar todos'<br>**entonces** el filtro de disponibilidad se elimina, la etiqueta desaparece y el listado se actualiza mostrando las ofertas sin este filtro. |