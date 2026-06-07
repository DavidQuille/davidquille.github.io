# Reporte de Scripts de Prueba Automatizados (S1)
> Generado el: 2026-02-12

## ID: CP-HU-01-R1
**Título:** Publicación exitosa de una oferta de tutoría
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas".
 3. Hacer clic en el botón "+ Nueva Oferta" para abrir la modal 'Nueva Oferta de Tutoría'.
 4. Ingresar en el campo 'Título de la Oferta': 'Cálculo Vectorial'.
 5. Ingresar en el campo 'Precio por Hora ($)': '10'.
 6. Seleccionar en el campo 'Modalidad': 'Presencial'.
 7. Seleccionar en el campo 'Categorías': 'Matemáticas'.
 8. Ingresar en el campo 'Descripción de la Oferta': 'Se enseñará cálculo vectorial, incluyendo integrales de línea y superficie.'.
 9. Hacer clic en el botón 'Publicar Oferta'.

**Expected Results:**
 - El sistema publica la oferta.
 - La modal 'Nueva Oferta de Tutoría' se cierra.
 - Se visualiza el perfil del tutor en el Dashboard con un mensaje de 'Oferta creada'.

---

## ID: CP-HU-01-R2
**Título:** Bloqueo por título de oferta vacío
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas".
 3. Hacer clic en el botón "+ Nueva Oferta" para abrir la modal 'Nueva Oferta de Tutoría'.
 4. Dejar el campo 'Título de la Oferta' vacío.
 5. Ingresar en el campo 'Precio por Hora ($)': '10'.
 6. Seleccionar en el campo 'Modalidad': 'Presencial'.
 7. Seleccionar en el campo 'Categorías': 'Matemáticas'.
 8. Ingresar en el campo 'Descripción de la Oferta': 'Clases de matemáticas avanzadas para universitarios.'.
 9. Hacer clic en el botón 'Publicar Oferta'.

**Expected Results:**
 - La modal 'Nueva Oferta de Tutoría' permanece abierta.
 - El campo 'Título de la Oferta' muestra un borde rojo.
 - Se muestra el mensaje de error exacto: 'Escribe el título de la materia' debajo del campo 'Título de la Oferta'.

---

## ID: CP-HU-01-R3
**Título:** Bloqueo por precio por hora inválido (fuera de rango o vacío)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas".
 3. Hacer clic en el botón "+ Nueva Oferta" para abrir la modal 'Nueva Oferta de Tutoría'.
 4. Ingresar en el campo 'Título de la Oferta': 'Física I'.
 5. Ingresar en el campo 'Precio por Hora ($)': '3' (valor fuera del rango $5-$20).
 6. Seleccionar en el campo 'Modalidad': 'Presencial'.
 7. Seleccionar en el campo 'Categorías': 'Ciencias Exactas'.
 8. Ingresar en el campo 'Descripción de la Oferta': 'Tutorías personalizadas de Física I para estudiantes universitarios.'.
 9. Hacer clic en el botón 'Publicar Oferta'.

**Expected Results:**
 - La modal 'Nueva Oferta de Tutoría' permanece abierta.
 - El campo 'Precio por Hora ($)' muestra un borde rojo.
 - Se muestra el mensaje de error exacto: 'Ingresa un precio' debajo del campo 'Precio por Hora ($)'.

---

## ID: CP-HU-01-R4
**Título:** Bloqueo por categorías de oferta vacías
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas".
 3. Hacer clic en el botón "+ Nueva Oferta" para abrir la modal 'Nueva Oferta de Tutoría'.
 4. Ingresar en el campo 'Título de la Oferta': 'Programación en Python'.
 5. Ingresar en el campo 'Precio por Hora ($)': '15'.
 6. Seleccionar en el campo 'Modalidad': 'Presencial'.
 7. Dejar el campo 'Categorías' vacío.
 8. Ingresar en el campo 'Descripción de la Oferta': 'Clases de Python desde cero hasta nivel intermedio.'.
 9. Hacer clic en el botón 'Publicar Oferta'.

**Expected Results:**
 - La modal 'Nueva Oferta de Tutoría' permanece abierta.
 - El campo 'Categorías' muestra un borde rojo.
 - Se muestra el mensaje de error exacto: 'Selecciona al menos una categoría' debajo del campo 'Categorías'.

---

## ID: CP-HU-01-R5
**Título:** Bloqueo por descripción de oferta vacía
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas".
 3. Hacer clic en el botón "+ Nueva Oferta" para abrir la modal 'Nueva Oferta de Tutoría'.
 4. Ingresar en el campo 'Título de la Oferta': 'Álgebra Lineal'.
 5. Ingresar en el campo 'Precio por Hora ($)': '12'.
 6. Seleccionar en el campo 'Modalidad': 'Presencial'.
 7. Seleccionar en el campo 'Categorías': 'Matemáticas'.
 8. Dejar el campo 'Descripción de la Oferta' vacío.
 9. Hacer clic en el botón 'Publicar Oferta'.

**Expected Results:**
 - La modal 'Nueva Oferta de Tutoría' permanece abierta.
 - El campo 'Descripción de la Oferta' muestra un borde rojo.
 - Se muestra el mensaje de error exacto: 'Agrega una descripción' debajo del campo 'Descripción de la Oferta'.

---

## ID: CP-HU-01-R6
**Título:** Cancelar la publicación de oferta con el botón 'Cancelar'
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas".
 3. Hacer clic en el botón "+ Nueva Oferta" para abrir la modal 'Nueva Oferta de Tutoría'.
 4. Ingresar en el campo 'Título de la Oferta': 'Prueba de Cancelación'.
 5. Hacer clic en el botón 'Cancelar'.

**Expected Results:**
 - La modal 'Nueva Oferta de Tutoría' se cierra.
 - El sistema redirige al perfil del tutor en el Dashboard.
 - Se muestra el botón '+ Nueva Oferta' en el Dashboard.

---

## ID: CP-HU-01-R7
**Título:** Cancelar la publicación de oferta con el botón 'X' (cerrar modal)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas".
 3. Hacer clic en el botón "+ Nueva Oferta" para abrir la modal 'Nueva Oferta de Tutoría'.
 4. Ingresar en el campo 'Título de la Oferta': 'Prueba de Cierre con X'.
 5. Hacer clic en el botón 'X' para cerrar la modal.

**Expected Results:**
 - La modal 'Nueva Oferta de Tutoría' se cierra.
 - El sistema redirige al perfil del tutor en el Dashboard.
 - Se muestra el botón '+ Nueva Oferta' en el Dashboard.


---
## ID: CP-HU-01-R8

**Título:** Truncado automático por límite máximo en Título (80 caracteres)

**Prioridad:** Media

**Tipo:** Funcional / UI

**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

  

**Steps:**

 1. Iniciar sesión como Tutor.

 2. Navegar a la sección "Mis Ofertas" y abrir la modal.

 3. Intentar escribir o pegar en el campo 'Título de la Oferta' el texto: 'Curso completo de Cálculo Vectorial y Ecuaciones Diferenciales para Ingeniería de Software' (90 caracteres).

 4. Observar el comportamiento del campo y el contador.

  

**Expected Results:**

 - El sistema trunca el texto automáticamente a los 80 caracteres.

 - No se permite ingresar caracteres adicionales más allá del límite.

 - El contador visual debajo del campo muestra "80/80".

  

---

  

## ID: CP-HU-01-R9

**Título:** Bloqueo por límite máximo de categorías (Máx. 5)

**Prioridad:** Media

**Tipo:** Funcional

**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

  

**Steps:**

 1. Iniciar sesión como Tutor.

 2. Navegar a la sección "Mis Ofertas" y abrir la modal.

 3. Seleccionar 5 categorías: 'Matemática', 'Física', 'Química', 'Álgebra' y 'Cálculo'.

 4. Intentar seleccionar una sexta categoría (ej. 'Estadística').

  

**Expected Results:**

 - El sistema no permite marcar la sexta categoría.

 - La selección se mantiene en 5 elementos.

 - El contador visual de categorías permanece en "5/5".

  

---

  

## ID: CP-HU-01-R10

**Título:** Truncado automático por límite máximo en Descripción (250 caracteres)

**Prioridad:** Media

**Tipo:** Funcional / UI

**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

  

**Steps:**

 1. Iniciar sesión como Tutor.

 2. Navegar a la sección "Mis Ofertas" y abrir la modal.

 3. Intentar pegar en el campo 'Descripción de la Oferta' el texto: 'En este curso intensivo aprenderás a dominar las integrales dobles y triples, así como el análisis vectorial completo. Incluye resolución de exámenes pasados, talleres prácticos semanales y acceso a grabaciones de las clases para repaso constante previo al examen.' (263 caracteres).

 4. Observar el comportamiento del campo y el contador.

  

**Expected Results:**

 - El sistema trunca el texto en el carácter 250 (terminando en "...constante pre").

 - El contador visual muestra "250/250".

 - No se permiten más entradas de teclado en ese campo.

  

---

  

## ID: CP-HU-01-R11

**Título:** Bloqueo por Título de oferta demasiado corto (menor a 3 caracteres)

**Prioridad:** Alta

**Tipo:** Funcional

**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

  

**Steps:**

 1. Iniciar sesión como Tutor.

 2. Navegar a la sección "Mis Ofertas" y abrir la modal.

 3. Ingresar en el campo 'Título de la Oferta': 'Fe'(2 caracteres).

 4. Completar los campos: Precio '10', Modalidad 'Presencial', Categoría 'Matemáticas' y una descripción válida.

 5. Hacer clic en el botón 'Publicar Oferta'.

  

**Expected Results:**

 - La modal permanece abierta.

 - El campo 'Título de la Oferta' muestra un borde rojo.

 - El contador indica '2/80'.

 - Aparece el mensaje de error: 'Mínimo 3 caracteres' debajo del campo.

  

---

  

## ID: CP-HU-01-R12

**Título:** Bloqueo por Descripción de oferta demasiado corta (menor a 20 caracteres)

**Prioridad:** Alta

**Tipo:** Funcional

**Pre-condiciones:** Usuario Tutor logueado y en la interfaz 'Nueva Oferta de Tutoría'.

  

**Steps:**

 1. Iniciar sesión como Tutor.

 2. Navegar a la sección "Mis Ofertas" y abrir la modal.

 3. Ingresar un Título válido (ej. 'Cálculo Vectorial').

 4. Ingresar en el campo 'Descripción de la Oferta': 'Clases rápidas.' (15 caracteres).

 5. Completar los demás campos con datos válidos.

 6. Hacer clic en el botón 'Publicar Oferta'.

  

**Expected Results:**

 - La modal permanece abierta.

 - El campo 'Descripción de la Oferta' muestra un borde rojo.

 - El contador indica '15/250'.

 - Aparece el mensaje de error: 'Mínimo 20 caracteres' debajo del campo.

---

## ID: CP-HU-02-R1
**Título:** Visualización del Dashboard de Tutor con ofertas publicadas
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema con al menos una oferta de tutoría publicada previamente.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas de Tutorías" (o la página de inicio por defecto del tutor, donde se carga el dashboard).

**Expected Results:**
 - La página "T. Inicio Tutor (Oferta Creada)" se carga correctamente.
 - Se visualiza el logo/texto "Poli Tutorías" en la parte superior izquierda.
 - Se visualiza el botón/texto "Cerrar Sesión" en la parte superior derecha.
 - Se visualiza el título principal de la sección: "Mis Ofertas de Tutorías".
 - Se visualiza el botón "+ Nueva Oferta" en la esquina superior derecha del área de contenido.
 - Se visualiza una tarjeta de oferta con el título "Cálculo en una Variable".
 - Dentro de la tarjeta de oferta "Cálculo en una Variable" se visualiza: Ícono "Presencial", descripción "Me enfoco en ejercicios de MRU.", etiquetas de categoría ("Matemática", "Formación Básica", "Preparación de Exámenes", "Resolución de Ejercicios", "Laboratorios") y el precio "$10/h".

---

## ID: CP-HU-02-R2
**Título:** Redirección al modal de creación de oferta desde el dashboard con ofertas
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema, con al menos una oferta de tutoría publicada, y en la sección "Mis Ofertas de Tutorías".

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas de Tutorías".
 3. Hacer clic en el botón "+ Nueva Oferta".

**Expected Results:**
 - Se visualiza un modal superpuesto a la pantalla actual para la creación de una nueva oferta de tutoría.

---

## ID: CP-HU-02-R3
**Título:** Visualización del Dashboard de Tutor sin ofertas publicadas (Estado Vacío)
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Tutor logueado en el sistema sin ofertas de tutoría publicadas previamente.

**Steps:**
 1. Iniciar sesión como Tutor.
 2. Navegar a la sección "Mis Ofertas de Tutorías" (o la página de inicio por defecto del tutor, donde se carga el dashboard).

**Expected Results:**
 - La página "T. Inicio Tutor (Sin Ofertas)" se carga correctamente.
 - **Cabecera:** Se visualiza el logo "Poli Tutorías" en la parte superior izquierda y el botón "Cerrar Sesión" en la parte superior derecha.
 - **Área Central:** Se visualiza el título "Mis Ofertas de Tutorías" y el botón "+ Nueva Oferta".
 - **Contenedor de Estado Vacío:**
     - Se visualiza el ícono de un libro abierto.
     - Se visualiza el mensaje central: "No tienes ofertas activas".
     - Se visualiza el subtexto: "Publica tu primera oferta para que los estudiantes te encuentren".
     - Se visualiza el botón central: "+ Crear mi primera oferta".

---

## ID: CP-HU-03-R1
**Título:** Verificación de la visualización inicial de ofertas en la Página 1
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante está logueado en el sistema y existen al menos 13 ofertas de tutorías publicadas para ser visualizadas.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Encuentra tu Tutoría' (Home Estudiante).

**Expected Results:**
 - Se visualiza la pantalla 'Encuentra tu Tutoría'.
 - Se visualiza '13 resultados' en la cabecera.
 - Se muestran 10 tarjetas de oferta.
 - La primera tarjeta de oferta muestra el título 'Cálculo Vectorial', el precio '$10/h', la modalidad 'Virtual/Presencial' con su icono, las etiquetas 'Matemática' y 'Formación Básica', el tutor 'Juan Pérez' con su foto, y la calificación '4.8 (15)'.
 - Los controles de paginación muestran '< 1 2 >' al pie de página.
 - El botón '1' de paginación se muestra activo (con fondo sólido).
 - El botón '2' de paginación se muestra inactivo (con fondo blanco/borde).

---

## ID: CP-HU-03-R2
**Título:** Verificación de la navegación a la Página 2 de ofertas mediante paginación
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante está logueado, en la pantalla 'Encuentra tu Tutoría', visualizando las ofertas de la Página 1, y existen al menos 13 ofertas de tutorías publicadas.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la pantalla 'Encuentra tu Tutoría' (Home Estudiante), visualizando la Página 1 de ofertas.
 3. Hacer clic en el botón de paginación número '2'.

**Expected Results:**
 - La lista de ofertas se actualiza.
 - Se muestran las tarjetas de oferta correspondientes a los resultados 11 al 13 (diferentes a las de la página 1).
 - En los controles de paginación, el botón '1' pasa a estar inactivo.
 - En los controles de paginación, el botón '2' se activa.
 - Los botones de navegación '<' y '>' se mantienen visibles.

---

---

## ID: CP-HU-17-R1
**Título:** Búsqueda exitosa de tutorías por materia o tutor
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante debe estar logueado y en la interfaz "Encuentra tu Tutoría" con ofertas disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Ingresar el término 'Cálculo' en el campo de texto 'Buscar por materia, tutor...'.
 4. Hacer clic en el botón con el icono de lupa (o presionar Enter).

**Expected Results:**
 - El contador superior derecho se actualiza a "X resultados" (siendo X la cantidad de coincidencias).
 - El grid de resultados se actualiza, mostrando exclusivamente las tarjetas que contienen el término 'Cálculo' en el Título de la materia o en el Nombre del Tutor.
 - Las tarjetas resultantes mantienen la estructura completa: Título, Precio, Modalidad, Descripción, Etiquetas, Horario, Tutor y Rating.

---

## ID: CP-HU-17-R2
**Título:** Búsqueda de tutorías sin coincidencias
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante debe estar logueado y en la interfaz "Encuentra tu Tutoría" con ofertas disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Ingresar el término 'Astronomía' en el campo de texto 'Buscar por materia, tutor...'.
 4. Hacer clic en el botón con el icono de lupa (o presionar Enter).

**Expected Results:**
 - El contador superior derecho indica "0 resultados".
 - El grid de tarjetas se oculta.
 - En el área central se visualiza un círculo de fondo gris claro conteniendo el ícono de una lupa (azul/gris).
 - Se visualiza el mensaje principal en negrita: "**No se encontraron ofertas**".
 - Se visualiza el subtexto explicativo: "**Intenta ajustar tus filtros de búsqueda**".
 - No se visualizan tarjetas de oferta ni botones adicionales de acción (como "Limpiar filtros").

---

## ID: CP-HU-17-R3
**Título:** Búsqueda con campo de texto vacío
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** El estudiante debe estar logueado y en la interfaz "Encuentra tu Tutoría" con ofertas disponibles.

**Steps:**
 1. Iniciar sesión como Estudiante.
 2. Navegar a la interfaz "Encuentra tu Tutoría".
 3. Asegurarse de que el campo de texto 'Buscar por materia, tutor...' esté vacío.
 4. Hacer clic en el botón con el icono de lupa (o presionar Enter).

**Expected Results:**
 - La lista muestra todas las ofertas disponibles.
 - El contador superior derecho indica "13 resultados".
 - Las tarjetas se visualizan ordenadas según el criterio por defecto.