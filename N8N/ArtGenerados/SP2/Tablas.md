# Reporte de Tablas
> Generado el: 25/2/2026
> **ÚLTIMA ACTUALIZACIÓN:** Correcciones post-verificación en prototipo 

---

### Nro. HU-34 - Título: Registrar información del tutor 

Descripción: Como tutor, quiero registrar información académica para generar confianza en los estudiantes.

#### Matriz de Decisión HU-34


| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 | R9 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿Campo 'Nombre Completo' está vacío? | N | S | N | N | N | N | N | N | N |
| C2 | ¿Campo 'Nombre Completo' < 3 caracteres? | N | N | S | N | N | N | N | N | N |
| C3 | ¿Campo 'Nombre Completo' > 60 caracteres? | N | N | N | S | N | N | N | N | N |
| C4 | ¿Números o especiales en 'Nombre Completo'? | N | N | N | N | S | N | N | N | N |
| C5 | ¿Campo 'Número de WhatsApp' está vacío? | N | S | N | N | N | N | N | N | N |
| C6 | ¿'Número de WhatsApp' tiene < 10 dígitos? | N | N | N | N | N | S | N | N | N |
| C7 | ¿'Número de WhatsApp' excede 13 dígitos? | N | N | N | N | N | N | S | N | N |
| C8 | ¿'Número de WhatsApp' contiene no-numéricos? | N | N | N | N | N | N | N | S | N |
| C9 | ¿Dropdown 'Facultad' sin seleccionar? | N | S | N | N | N | N | N | N | N |
| C10 | ¿Dropdown 'Semestre Actual' sin seleccionar? | N | S | N | N | N | N | N | N | N |
| C11 | ¿Campo 'Biografía Corta' está vacía? | N | S | N | N | N | N | N | N | N |
| C12 | ¿Campo 'Biografía Corta' < 20 caracteres? | N | N | N | N | N | N | N | N | S |
| C13 | Click botón 'Siguiente' (Disponibilidad) | S | S | S | S | S | S | S | S | S |
| | **ACCIONES** (Usar código corto) | | | | | | | | | |
| A1 | Avanzar a Paso 2 'Disponibilidad' | X | | | | | | | | |
| A2 | Mostrar Error: 'El nombre es obligatorio' | | X | | | | | | | |
| A3 | Mostrar Error: 'Mínimo 3 caracteres' | | | X | | | | | | |
| A4 | Bloquear: máximo 60 caracteres | | | | X | | | | | |
| A5 | Bloquear números/especiales en Nombre | | | | | X | | | | |
| A6 | Mostrar Error: 'El número de WhatsApp es obligatorio' | | X | | | | | | | |
| A7 | Mostrar Error: 'Ingresa un número válido (10-13 dígitos)' | | | | | | X | X | | |
| A8 | Bloquear no-numéricos en WhatsApp | | | | | | | | X | |
| A9 | Mostrar Error: 'Selecciona tu facultad' | | X | | | | | | | |
| A10 | Mostrar Error: 'Selecciona tu semestre' | | X | | | | | | | |
| A11 | Mostrar Error: 'La biografía es obligatoria' | | X | | | | | | | |
| A12 | Mostrar Error: 'Mínimo 20 caracteres' | | | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Avanzar a Paso 2 'Disponibilidad':** "Redirige al Paso 2. **VALIDACIÓN VISUAL:** Se visualiza paso '2 Disponibilidad' resaltado en la barra superior, título 'Define tu Horario', subtítulo 'Selecciona los bloques horarios en los que puedes dar clases', cuadrícula con encabezados ('Lun' a 'Dom', '7:00' a '20:00') y el botón 'Siguiente Perfil Profesional'."
* **A2 - Mostrar Error: 'El nombre es obligatorio':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje de error exacto 'El nombre es obligatorio' en rojo debajo de 'Nombre Completo'."
* **A3 - Mostrar Error: 'Mínimo 3 caracteres':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje en rojo 'Mínimo 3 caracteres' debajo de 'Nombre Completo'."
* **A4 - Bloquear: máximo 60 caracteres:** "Límite de ingreso. **VALIDACIÓN VISUAL:** Contador '60/60' visible. No permite más digitación ni pegar texto."
* **A5 - Bloquear números/especiales en Nombre:** "Bloqueo de teclado. **VALIDACIÓN VISUAL:** Caracteres no permitidos (0-9, especiales) no aparecen en pantalla. Solo letras y espacios."
* **A6 - Mostrar Error: 'El número de WhatsApp es obligatorio':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje en rojo 'El número de WhatsApp es obligatorio' debajo del campo."
* **A7 - Mostrar Error: 'Ingresa un número válido (10-13 dígitos)':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje en rojo 'Ingresa un número válido (10-13 dígitos)' debajo del campo."
* **A8 - Bloquear no-numéricos en WhatsApp:** "Bloqueo de teclado. **VALIDACIÓN VISUAL:** Letras y especiales no aparecen en pantalla. Solo números."
* **A9 - Mostrar Error: 'Selecciona tu facultad':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje en rojo 'Selecciona tu facultad' debajo del dropdown respectivo."
* **A10 - Mostrar Error: 'Selecciona tu semestre':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje en rojo 'Selecciona tu semestre' debajo del dropdown."
* **A11 - Mostrar Error: 'La biografía es obligatoria':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje en rojo 'La biografía es obligatoria' debajo de 'Biografía Corta'."
* **A12 - Mostrar Error: 'Mínimo 20 caracteres':** "Permanece en la pantalla. **VALIDACIÓN VISUAL:** Muestra el mensaje en rojo 'Mínimo 20 caracteres' debajo de 'Biografía Corta'."

### GLOSARIO TÉCNICO - REFERENCIAS PARA PRUEBAS

#### Facultades Disponibles

| Código | Nombre |
| :-- | :--- |
| FIS | FIS - Sistemas |
| FIEE | FIEE - Eléctrica y Electrónica |
| FC | FC - Ciencias |
| FICA | FICA - Civil y Ambiental |
| FIM | FIM - Mecánica |
| FIQA | FIQA - Química y Agroindustria |
| FIGP | FIGP - Geología y Petróleos |
| FCA | FCA - Ciencias Administrativas |
| ESFOT | ESFOT - Formación de Tecnólogos |

#### Semestres Disponibles

Pre-universitario, 1° Semestre, 2° Semestre, 3° Semestre, 4° Semestre, 5° Semestre, 6° Semestre, 7° Semestre, 8° Semestre, 9° Semestre

---

### Nro. HU-41 - Registrar mi disponibilidad

Descripción: Como tutor, quiero registrar mi disponibilidad para que los estudiantes conozcan cuándo pueden solicitar mis servicios.

#### Matriz de Decisión HU-41


| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 |
| :-- | :--- | :-: | :-: | :-: | :-: |
| C1 | ¿Se ha seleccionado al menos un bloque de hora? | N | S | S | S |
| C2 | Click botón 'Siguiente' (Perfil Profesional) sin selección | S | N | N | N |
| C3 | Click en bloque horario en la cuadrícula | N/A | S | S | S |
| C4 | ¿Contador dinámico visible en verde? | N/A | S | S | S |
| C5 | Click botón 'Siguiente' (Perfil Profesional) con selección | N | N | S | S |
| C6 | Click para deseleccionar un horario ya marcado | N/A | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | |
| A1 | Bloquear: Mostrar 'Selecciona al menos un horario...' | X | | | |
| A2 | Cambio visual bloque a azul y visto | | X | X | X |
| A3 | Mostrar contador dinámico (ej: '✓ 11 seleccionados') | | X | X | X |
| A4 | Avanzar a Paso 3 'Perfil Profesional' | | | X | X |
| A5 | Actualizar contador al deseleccionar | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Bloquear: Mostrar 'Selecciona al menos un horario...':** "Bloquea navegación. **VALIDACIÓN VISUAL:** Muestra el texto rojo 'Selecciona al menos un horario disponible' encima de la cuadrícula."
* **A2 - Cambio visual bloque a azul y visto:** "Interacción con celda. **VALIDACIÓN VISUAL:** El bloque horario seleccionado cambia de color blanco a azul oscuro y muestra un ícono '✓' blanco en el centro."
* **A3 - Mostrar contador dinámico (ej: '✓ 11 seleccionados'):** "Actualización UI. **VALIDACIÓN VISUAL:** Aparece texto verde centrado sobre la cuadrícula: '✓ [N] horarios seleccionados'."
* **A4 - Avanzar a Paso 3 'Perfil Profesional':** "Redirige al Paso 3. **VALIDACIÓN VISUAL:** Se visualiza paso '3 Perfil Profesional' resaltado. Título 'Detalles Profesionales', subtítulo 'Añade tu experiencia y materias para destacar'. Botón 'Finalizar Registro'."
* **A5 - Actualizar contador al deseleccionar:** "Actualización UI. **VALIDACIÓN VISUAL:** El bloque vuelve a ser blanco y el contador superior verde disminuye su número en tiempo real."

---

### Nro. HU-42 - Registrar información académica

Descripción: Como tutor, quiero registrar información académica para que los estudiantes se enteren cuáles son mis conocimientos.

#### Matriz de Decisión HU-42

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | Click en 'Finalizar Registro' con campos vacíos (Opcional) | S | S | N | N | N | N | N |
| C2 | Click en 'Guardar' (Modal Exp) con campos vacíos | N | N | S | N | N | N | N |
| C3 | ¿Formato en campo 'Fecha Inicio/Fin' es MM/AAAA? | N | N | N | S | N | N | N |
| C4 | ¿Se ingresan caracteres no-numéricos en Fecha? | N | N | N | N | S | N | N |
| C5 | ¿Campo de Fecha excede 7 caracteres (y no es 'Presente')? | N | N | N | N | N | S | N |
| C6 | Click en botón 'Agregar' materia | N | N | N | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | | | | |
| A1 | Registro exitoso (finaliza wizard) | X | | | | | | |
| A2 | Ignorar 'Guardar' sin mensajes de error | | X | | | | | |
| A3 | Validar y mantener formato de Fecha | | | X | | | | |
| A4 | Bloquear caracteres no-numéricos en Fecha | | | | | X | | |
| A5 | Mostrar Error: 'Máximo 7 caracteres' en Fecha | | | | | | X | |
| A6 | Crear etiqueta ('pill') con materia | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Registro exitoso (finaliza wizard):** "Concluye el proceso. **VALIDACIÓN VISUAL:** Finaliza el registro sin arrojar alertas, redirigiendo a la pantalla posterior o dashboard (dependiendo del flujo post-registro)."
* **A2 - Ignorar 'Guardar' sin mensajes de error:** "Fallo silencioso. **VALIDACIÓN VISUAL:** Al presionar 'Guardar' en el modal 'Nueva Experiencia' estando vacío, la acción se ignora y no aparece ningún mensaje de error; el modal permanece en pantalla."
* **A3 - Validar y mantener formato de Fecha:** "Ingreso correcto. **VALIDACIÓN VISUAL:** Muestra la fecha digitada con el slash incluido, ej: '03/2024'."
* **A4 - Bloquear caracteres no-numéricos en Fecha:** "Bloqueo de teclado. **VALIDACIÓN VISUAL:** Letras y signos (salvo '/') no se muestran al teclear. Para 'Fecha Fin', permite la palabra exacta 'Presente'."
* **A5 - Mostrar Error: 'Máximo 7 caracteres' en Fecha:** "Validación de límite. **VALIDACIÓN VISUAL:** Muestra el texto rojo 'Máximo 7 caracteres' debajo de las fechas si se excede el formato MM/AAAA (ej. 12/20255)."
* **A6 - Crear etiqueta ('pill') con materia:** "Actualización UI. **VALIDACIÓN VISUAL:** Se limpia el input text y aparece un elemento visual (etiqueta) color celeste claro con el texto de la materia y una 'x' a la derecha (Ej: 'matemática x')."


#### Restricciones Globales

| Campo | Mínimo | Máximo | Bloques | Notas |
| :-- | :-: | :-: | :-- | :-- |
| Nombre Completo | 3 | 60 | A-Z, a-z, espacios | Contador visible |
| Número WhatsApp | 10 | 13 | 0-9 | Exacto 10-13 |
| Biografía Corta | 20 | 300 | Sin restricción | Contador visible |
| Fecha (MM/AAAA) | 7 | 7 | 0-9, / | Salvo "Presente" en Fin |

---

### Nro. HU-07 - Título: Consultar mi disponibilidad

Descripción: Como tutor, quiero ver mi horario para revisar qué horas tengo libres para impartir tutorías.


#### Matriz de Decisión HU-07

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 |
| :-- | :--- | :-: | :-: |
| C1 | ¿Tutor accede a pantalla 'Gestionar Disponibilidad'? | S | S |
| C2 | Click en enlace 'Volver al Panel' | N | S |
| | **ACCIONES** (Usar código corto) | | |
| A1 | Mostrar cuadrícula de disponibilidad guardada (Sólo Lectura) | X | X |
| A2 | Ir a Pantalla 'T. Dashboard Tutor' | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar cuadrícula de disponibilidad guardada (Sólo Lectura):** "Pantalla carga correctamente. **VALIDACIÓN VISUAL:** - Cabecera: Texto 'Volver al Panel' (izquierda), logo 'Poli Tutorías' (derecha).
    - Título: 'Gestionar Disponibilidad'.
    - Descripción: 'Haz clic en los horarios que tienes disponibles para ofrecer tutorías.' (Nota: texto heredado, pero no interactivo).
    - SubDescripción: 'Tu horario se mostrará en la zona horaria local (GMT-5).'
    - Contador: Ej: '✓ 4 horarios seleccionados' (verde, con checkmark).
    - Tabla: Columnas ('HORA', 'Lun', 'Mar', 'Mié', 'Jue', 'Vie', 'Sáb', 'Dom'), filas '7:00' a '20:00'.
    - Horarios seleccionados: Ej 'Lun 12:00' en azul oscuro + checkmark blanco.
    - **Botones 'Cancelar' y 'Guardar Cambios' visibles pero INACTIVOS (no clickeables).**"
* **A2 - Ir a Pantalla 'T. Dashboard Tutor':** "Interacción de retroceso. **VALIDACIÓN VISUAL:** Redirige a la pantalla 'T. Dashboard Tutor' (hub central)."


**Notas Críticas:** - **SOLO LECTURA (READ-ONLY).** No permite editar horarios.
- **Ignorar botones 'Cancelar' y 'Guardar Cambios'** - no son interactivos.

---

### Nro. HU-32 - Título: Ver detalles de la oferta

Descripción: Como estudiante, quiero ver los detalles de una oferta para tomar una decisión informada.


#### Matriz de Decisión HU-32

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 |
| :-- | :--- | :-: | :-: |
| C1 | ¿Estudiante da click en una tarjeta de oferta? | S | N |
| C2 | Click en el botón de retroceso ('Volver') | N | S |
| | **ACCIONES** (Usar código corto) | | |
| A1 | Mostrar detalles textuales de la oferta | X | |
| A2 | Ir a Pantalla 'E. Home Estudiante' | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar detalles textuales de la oferta:** "Carga información de la oferta. **VALIDACIÓN VISUAL:** - Cabecera: Botón 'Volver' (izquierda), logo 'PoliTutorias' (derecha).
    - Sección Principal: Icono de libro + Título de la materia (Ej: 'Cálculo Vectorial').
    - Modalidad: 'Virtual y Presencial'.
    - Descripción: Párrafo descriptivo de la clase.
    - Categorías: Título 'Categorías', tags específicos (Ej: 'Matemática', 'Formación Básica').
    - Disponibilidad Semanal: Título 'Disponibilidad Semanal' listando días y horas.
    - Precio: Panel lateral con 'Precio por hora' = '$X'."
* **A2 - Ir a Pantalla 'E. Home Estudiante':** "Interacción de retroceso. **VALIDACIÓN VISUAL:** Redirige al listado principal de ofertas en 'E. Home Estudiante'."

**Notas Críticas:** - ⚠️ **SOLO mostrar detalles de oferta:** Título, modalidad, categoría, disponibilidad, precio.
- ⚠️ **DESCARTAR COMPLETAMENTE:** Sección "Sobre el Tutor", "Experiencia", "Contactar por WhatsApp".

---

### Nro. HU-05 - Título: Ver información sobre el tutor

Descripción: Como estudiante, quiero ver la información del tutor para saber qué conocimientos tiene.

**Pantalla:** E. Detalle Oferta

#### Matriz de Decisión HU-05

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 |
| :-- | :--- | :-: |
| C1 | ¿Se carga la pantalla de detalle para ver datos del tutor? | S |
| | **ACCIONES** (Usar código corto) | |
| A1 | Mostrar bloques de información del tutor | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar bloques de información del tutor:** "Visualización de perfil. **VALIDACIÓN VISUAL:** - Sección 'Sobre el Tutor': Imagen de perfil, Nombre (Ej: 'Juan Pérez'), Info Académica ('FIM - Mecánica', '9° Semestre'), Rating ('4.8 (15 reseñas)'), Descripción bibliográfica, y 'Materias que domina:' en formato tags.
    - Sección 'Experiencia': Entradas de historial con Rol, Institución/Lugar y Fechas (Ej: '2024 — Presente')."

**Notas Críticas:** - ⚠️ **SOLO "Sobre el Tutor" y "Experiencia".**
- ⚠️ **DESCARTAR COMPLETAMENTE:** Detalles de oferta, contactar por WhatsApp.

---

### Nro. HU-27 - Título: Filtrar ofertas por precio

Descripción: Como estudiante, quiero filtrar las ofertas por precio para encontrar opciones que se ajusten a mi presupuesto.

#### Matriz de Decisión HU-27

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 |
| :-- | :--- | :-: | :-: |
| C1 | ¿Se ajusta el slider a un rango con coincidencias? | S | N |
| C2 | ¿Se ajusta el slider a un rango sin coincidencias? | N | S |
| | **ACCIONES** (Usar código corto) | | |
| A1 | Actualizar ofertas según el rango monetario | X | |
| A2 | Mostrar Mensaje: 'No se encontraron ofertas' | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Actualizar ofertas según el rango monetario:** "Filtrado exitoso. **VALIDACIÓN VISUAL:** El listado se actualiza omitiendo elementos fuera del rango. El slider muestra los valores seleccionados (ej: '$5.00' a '$20.00')."
* **A2 - Mostrar Mensaje: 'No se encontraron ofertas':** "Filtrado sin resultados. **VALIDACIÓN VISUAL:** La lista se vacía y se muestra el mensaje exacto: 'No se encontraron ofertas. Intenta ajustar tus filtros de búsqueda.'"

**Notas Críticas:** - ⚠️ **SOLO desarrollar slider 'Precio'.** Rango $5.00 - $20.00.
- ⚠️ **DESCARTAR:** Lista de ofertas, otros filtros, ordenamiento.

---

### Nro. HU-26 - Título: Filtrar ofertas por modalidad

Descripción: Como estudiante, quiero filtrar las ofertas por modalidad para encontrar un tutor que se ajuste a mi preferencia.


#### Matriz de Decisión HU-26

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 |
| :-- | :--- | :-: | :-: | :-: | :-: |
| C1 | Click en botón filtro 'Todas' | S | N | N | N |
| C2 | Click en botón filtro 'Presencial' | N | S | N | N |
| C3 | Click en botón filtro 'Virtual' | N | N | S | N |
| C4 | Click en botón filtro 'Ambos' | N | N | N | S |
| | **ACCIONES** (Usar código corto) | | | | |
| A1 | Listar modalidad global (Todas) | X | | | |
| A2 | Listar modalidad Presencial + Ambos | | X | | |
| A3 | Listar modalidad Virtual + Ambos | | | X | |
| A4 | Listar únicamente modalidad Ambos | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Listar modalidad global (Todas):** "Estado por defecto. **VALIDACIÓN VISUAL:** Se muestran todas las ofertas sin restricción de modalidad. El botón 'Todas' aparece visualmente resaltado."
* **A2 - Listar modalidad Presencial + Ambos:** "Filtro aplicado. **VALIDACIÓN VISUAL:** Listado de ofertas se actualiza mostrando las que contengan etiqueta 'Presencial' y 'Virtual y Presencial'. Excluye ofertas únicamente 'Virtual'."
* **A3 - Listar modalidad Virtual + Ambos:** "Filtro aplicado. **VALIDACIÓN VISUAL:** Listado de ofertas se actualiza mostrando 'Virtual' y 'Virtual y Presencial'. Excluye ofertas únicamente 'Presencial'."
* **A4 - Listar únicamente modalidad Ambos:** "Filtro restrictivo. **VALIDACIÓN VISUAL:** Se muestran estrictamente ofertas que contengan ambas modalidades al mismo tiempo ('Virtual y Presencial')."

---

### Nro. HU-16 - Título: Filtrar ofertas por disponibilidad

Descripción: Como estudiante, quiero filtrar las ofertas por disponibilidad para encontrar tutores disponibles en mis horarios.

#### Matriz de Decisión HU-16

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 |
| :-- | :--- | :-: | :-: | :-: |
| C1 | ¿Se encuentra seleccionado algún día de la semana? | N | S | S |
| C2 | ¿Existen coincidencias de ofertas para ese día? | N/A | S | N |
| | **ACCIONES** (Usar código corto) | | | |
| A1 | Mostrar todas las ofertas (sin filtro de fecha) | X | | |
| A2 | Listar coincidencias por día(s) | | X | |
| A3 | Mostrar Mensaje: 'No se encontraron ofertas' | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar todas las ofertas (sin filtro de fecha):** "Estado inactivo. **VALIDACIÓN VISUAL:** Se muestran todas las ofertas de la base de datos sin restricciones de día."
* **A2 - Listar coincidencias por día(s):** "Filtro aplicado. **VALIDACIÓN VISUAL:** Botón del día seleccionado aparece resaltado. La lista muestra únicamente ofertas que incluyan ese día en su disponibilidad."
* **A3 - Mostrar Mensaje: 'No se encontraron ofertas':** "Día(s) sin coincidencias. **VALIDACIÓN VISUAL:** La lista se vacía y se muestra el mensaje exacto: 'No se encontraron ofertas. Intenta ajustar tus filtros de búsqueda.'"

**Notas Críticas:** - ⚠️ **SOLO desarrollar filtro 'Disponibilidad'.** Selector: Día de la semana.
- ⚠️ **DESCARTAR:** Otros filtros, lista de ofertas, ordenamiento.

---