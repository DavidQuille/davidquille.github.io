# 📘 Pronts Agentes Playwright
## Guía para Creación, Análisis y Reparación de Pruebas

---

# 🛠️ Creación de casos en código (Generator)

Vas a generar las pruebas automatizadas basándote en el archivo `specs/SprintX/CasosHUxx.md`.

Por cada caso descrito, crearás un script independiente dentro de la carpeta:

```text
tests/SprintXX/HUxx/
```

Para una correcta construcción de las pruebas, ingresa a la URL que se encuentra dentro del propio archivo Markdown.

Además, es muy importante que verifiques que el código generado tenga estricta concordancia con el archivo `.md` y no omita ningún paso.

> **Nota para contexto:**  
> (agregan contexto si es necesario)

---

# 🔍 Análisis de casos en MD (Planner)

Analiza los casos de prueba del archivo `specs/SprintX/CasosHUx.md` y verifica que cubran el 100% de la funcionalidad.

Si identificas variables o flujos de prevención de errores que no se hayan tomado en cuenta, sugiere estos nuevos casos al final del documento manteniendo exactamente el mismo formato.

Para diferenciarlos, utiliza el prefijo **ADD** en lugar de **R**.

> **Importante:**  
> Para validar que estén todos los escenarios, ingresa a la URL que se encuentra dentro del propio archivo.

> **Nota para contexto:**  
> (agregan contexto si es necesario)

---

# 🔧 Creación de casos en código (Healer)

Vas a ejecutar y reparar las pruebas existentes basándote en los cambios que se dieron en la aplicación.

Primero, entra a la URL de la aplicación y revisa de forma general toda la página para entender su estructura y estado actual.

Después, basándote en la siguiente descripción de cambios, actualiza y repara el código de las pruebas que se encuentran en la carpeta:

```text
tests/Sprintx/HUx
```

Ejecuta las pruebas; si alguna falla debido a las nuevas actualizaciones (como cambios en botones, flujos o textos), corrige los localizadores o los pasos directamente en el código para que la prueba vuelva a pasar.

Verifica siempre que tus correcciones tengan total concordancia con los cambios reportados y no alteren el propósito original del caso de prueba.

> **Nota para contexto:**  
> (agrega aquí la descripción de los cambios de la app, por ejemplo: "Se cambió el botón de inicio de sesión y ahora sale un popup de confirmación").

---

## 📌 Consideraciones Generales

- Mantener concordancia entre los casos documentados y el código generado.
- No omitir pasos descritos en los archivos Markdown.
- Validar siempre los escenarios directamente en la URL proporcionada.
- Respetar el propósito original de cada caso de prueba.