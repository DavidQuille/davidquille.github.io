# Reporte de Tablas
> Generado el: 10/2/2026

### Nro. HU-01 - Título: Publicar oferta de tutoría

Descripción: Como tutor, quiero publicar que domino una materia, para atraer estudiantes interesados

#### Matriz de Decisión HU-01

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 | R4 | R5 | R6 | R7 |
| :-- | :--- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| C1 | ¿'Título de la Oferta' lleno? | S | N | S | S | S | - | - |
| C2 | ¿'Precio por Hora ($)' lleno y entre $5 y $20? | S | S | N | S | S | - | - |
| C3 | ¿'Modalidad' seleccionada? | S | S | S | S | S | - | - |
| C4 | ¿'Categorías' seleccionadas (entre 1 y 5 ítems)? | S | S | S | N | S | - | - |
| C5 | ¿'Descripción de la Oferta' lleno? | S | S | S | S | N | - | - |
| C6 | Click en botón 'Cancelar' | N | N | N | N | N | S | N |
| C7 | Click en botón 'X' (cerrar modal) | N | N | N | N | N | N | S |
| C8 | Click en botón 'Publicar Oferta' | S | S | S | S | S | N | N |
| | **ACCIONES** (Usar código corto) | | | | | | | |
| A1 | Publicar Exitoso | X | | | | | | |
| A2 | Mostrar Error Título | | X | | | | | |
| A3 | Mostrar Error Precio | | | X | | | | |
| A4 | Mostrar Error Categorías | | | | X | | | |
| A5 | Mostrar Error Descripción | | | | | X | | |
| A6 | Navegar a Dashboard (por Cancelar) | | | | | | X | |
| A7 | Navegar a Dashboard (por Cerrar 'X') | | | | | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)
* **A1 - Publicar Exitoso:** Redirige a la pantalla 'T. Dashboard Tutor' (según mapa). **VALIDACIÓN VISUAL:** Se visualiza el mensaje de 'Oferta creada' La modal 'Nueva Oferta de Tutoría' se cierra.
* **A2 - Mostrar Error Título:** Permanece en la modal 'Nueva Oferta de Tutoría'. **VALIDACIÓN VISUAL:** El campo de entrada 'Título de la Oferta' muestra un borde rojo y el mensaje de error exacto: 'Escribe el título de la materia' debajo.
* **A3 - Mostrar Error Precio:** Permanece en la modal 'Nueva Oferta de Tutoría'. **VALIDACIÓN VISUAL:** El campo de entrada 'Precio por Hora ($)' muestra un borde rojo y el mensaje de error exacto: 'Ingresa un precio' debajo. Este mensaje se activa si el campo está vacío o el valor está fuera del rango de $5 a $20.
* **A4 - Mostrar Error Categorías:** Permanece en la modal 'Nueva Oferta de Tutoría'. **VALIDACIÓN VISUAL:** El campo de entrada 'Categorías' muestra un borde rojo y el mensaje de error exacto: 'Selecciona al menos una categoría' debajo.
* **A5 - Mostrar Error Descripción:** Permanece en la modal 'Nueva Oferta de Tutoría'. **VALIDACIÓN VISUAL:** El campo de entrada 'Descripción de la Oferta' muestra un borde rojo y el mensaje de error exacto: 'Agrega una descripción' debajo.
* **A6 - Navegar a Dashboard (por Cancelar):** Redirige a la pantalla 'T. Dashboard Tutor' (según mapa). **VALIDACIÓN VISUAL:** Se visualiza el perfil del tutor , y el botón '+ Nueva Oferta'. La modal 'Nueva Oferta de Tutoría' se cierra.
* **A7 - Navegar a Dashboard (por Cerrar 'X'):** Redirige a la pantalla 'T. Dashboard Tutor' (según mapa). **VALIDACIÓN VISUAL:** Se visualiza el perfil del tutor , y el botón '+ Nueva Oferta'. La modal 'Nueva Oferta de Tutoría' se cierra.

---

### Nro. HU-02 - Título: Ver mis ofertas (Dashboard)

Descripción: Como tutor, quiero ver un listado de las ofertas de tutoría que he publicado para saber que tutorías estoy ofreciendo

#### Matriz de Decisión HU-02

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 |
| :-- | :--- | :---: | :---: | :---: |
| C1 | ¿Existen ofertas creadas por el tutor? | S | S | N |
| C2 | ¿Clic en el botón "+ Nueva Oferta" o "Crear mi primera oferta"? | N | S | N |
| | **ACCIONES** | | | |
| A1 | Ver Dashboard con Ofertas | X | | |
| A2 | Ir a Modal Crear Oferta | | X | |
| A3 | Ver Dashboard Estado Vacío (Sin Ofertas) | | | X |


### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Ver Dashboard con Ofertas:** Permanece en la pantalla "T. Inicio Tutor (Oferta Creada)". **VALIDACIÓN VISUAL:**
    * Se visualiza el logo/texto "Poli Tutorías" en la parte superior izquierda.
    * Se visualiza el botón/texto "Cerrar Sesión" en la parte superior derecha.
    * Se visualiza el título principal de la sección: "Mis Ofertas de Tutorías".
    * Se visualiza el botón "+ Nueva Oferta" en la esquina superior derecha del área de contenido.
    * Se visualiza una tarjeta de oferta con el título "Cálculo en una Variable".
    * **Dentro de la tarjeta se visualiza:** Ícono "Presencial", descripción "Me enfoco en ejercicios de MRU.", etiquetas de categoría (Matemática, Formación Básica, Preparación de Exámenes, Resolución de Ejercicios, Laboratorios) y precio "$10/h".
    * **NOTA:** No se incluye ni funcionaliza el ícono de eliminación/basurero.

* **A2 - Ir a Modal Crear Oferta:** Redirige a la pantalla "Modal: T. Crear Oferta". **VALIDACIÓN VISUAL:**
    * Se visualiza un modal superpuesto a la pantalla actual para la creación de una nueva oferta de tutoría.

* **A3 - Ver Dashboard Estado Vacío (Sin Ofertas):** Permanece en la pantalla "T. Inicio Tutor (Sin Ofertas)". **VALIDACIÓN VISUAL:**
    * **Cabecera:** Se visualiza logo "Poli Tutorías" (izquierda) y "Cerrar Sesión" (derecha).
    * **Área Central:** Se visualiza el título "Mis Ofertas de Tutorías" y el botón "+ Nueva Oferta".
    * **Contenedor de Estado Vacío:** * Se visualiza ícono de un libro abierto.
        * Se visualiza el mensaje central: "No tienes ofertas activas".
        * Se visualiza el subtexto: "Publica tu primera oferta para que los estudiantes te encuentren".
        * Se visualiza el botón central: "+ Crear mi primera oferta".

---

### Nro. HU-03 - Título: Ver ofertas de tutorías

Descripción: Como estudiante, quiero revisar la oferta de tutorías, para encontrar la que mejor se adapte a mis necesidades

#### Matriz de Decisión HU-03

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 |
| :-- | :--- | :-: | :-: |
| C1 | ¿Pantalla 'E. Home Estudiante' cargada por defecto? | S | S |
| C2 | ¿Clic en botón de paginación número '2'? | N | S |
| | **ACCIONES** | | |
| A1 | Visualizar Ofertas Página 1 (Estado Inicial) | X | |
| A2 | Visualizar Ofertas Página 2 (Refresco de Lista) | | X |


### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Visualizar Ofertas Página 1 (Estado Inicial):** Se muestra la primera carga de resultados. **VALIDACIÓN VISUAL:**
    * **Cabecera:** Se visualiza "13 resultados" alineado a la derecha. (Sin barra de búsqueda ni filtros).
    * **Grid de Datos:** Se visualizan exactamente 10 tarjetas de oferta.
    * **Verificación de Datos (Tarjeta Ejemplo "Cálculo Vectorial"):**
        * **Título:** "Cálculo Vectorial".
        * **Precio:** "$10/h" (esquina superior derecha).
        * **Modalidad:** Ícono + "Virtual/Presencial".
        * **Etiquetas:** "Matemática", "Formación Básica".
        * **Tutor:** Foto circular + "Juan Pérez".
        * **Rating:** Estrella + "4.8 (15)".
    * **Controles de Paginación:**
        * Se visualizan los controles `< 1 2 >` al pie de página.
        * El botón **'1'** tiene fondo sólido (Activo).
        * El botón **'2'** tiene fondo blanco/borde (Inactivo).

* **A2 - Visualizar Ofertas Página 2 (Refresco de Lista):** La lista se actualiza tras el clic. **VALIDACIÓN VISUAL:**
    * **Refresco de Grid:** Se visualizan nuevas tarjetas de oferta (diferentes a las de la página 1) correspondientes a los resultados restantes (11 al 13).
    * **Cambio de Estado en Paginación:**
        * El botón **'1'** pasa a tener fondo blanco/borde (Inactivo).
        * El botón **'2'** pasa a tener fondo sólido (Activo).
        * Los botones de navegación `<` y `>` se mantienen visibles.

---

### Nro. HU-17 - Título: Buscar tutoría por materia

Descripción: Como estudiante, quiero buscar una tutoría por el nombre de la materia para encontrar resultados específicos rápidamente


#### Matriz de Decisión HU-17

| ID | Condición (Nombre Exacto de Info Visual) / Acción | R1 | R2 | R3 |
| :-- | :--- | :-: | :-: | :-: |
| C1 | ¿Campo de texto 'Buscar por materia, tutor...' lleno? | S | S | N |
| C2 | ¿El texto ingresado produce coincidencias con ofertas existentes? | S | N | - |
| | **ACCIONES** | | | |
| A1 | Mostrar Ofertas Filtradas | X | | |
| A2 | Mostrar Pantalla "No se encontraron ofertas" | | X | |
| A3 | Mostrar Todas las Ofertas (Default) | | | X |

### GLOSARIO DE ACCIONES (Definición Exacta y Completa)

* **A1 - Mostrar Ofertas Filtradas:** Se actualiza el grid de resultados en la pantalla 'E. Home Estudiante'. **VALIDACIÓN VISUAL:**
    * **Contador:** El texto superior derecho se actualiza a "X resultados" (siendo X la cantidad de coincidencias).
    * **Grid:** Se visualizan exclusivamente las tarjetas que contienen el término buscado en el Título o en el Nombre del Tutor.
    * **Integridad de Tarjeta:** Las tarjetas resultantes mantienen la estructura completa: Título, Precio, Modalidad, Descripción, Etiquetas, Horario, Tutor y Rating.

* **A2 - Mostrar Pantalla "No se encontraron ofertas":** Se oculta el grid de tarjetas y se muestra el estado vacío. **VALIDACIÓN VISUAL:**
    * **Contador:** El texto superior derecho indica "0 resultados".
    * **Área Central (Estado Vacío):**
        * Se visualiza un círculo de fondo gris claro conteniendo el **ícono de una lupa** (azul/gris).
        * Se visualiza el mensaje principal en negrita: "**No se encontraron ofertas**".
        * Se visualiza el subtexto explicativo: "**Intenta ajustar tus filtros de búsqueda**".
    * **Restricción:** No se visualizan tarjetas de oferta ni botones adicionales de acción (como "Limpiar filtros").

* **A3 - Mostrar Todas las Ofertas (Default):** Estado inicial o cuando se borra el texto de búsqueda. **VALIDACIÓN VISUAL:**
    * **Contador:** Muestra el total de ofertas disponibles (Ej. "13 resultados").
    * **Grid:** Se visualizan todas las tarjetas disponibles ordenadas según el criterio por defecto.