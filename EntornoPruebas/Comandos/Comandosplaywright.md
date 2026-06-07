
# Instalación de Playwright y Agentes en Visual Studio Code

## 1. Instalar la Extensión de Playwright

1. Abre Visual Studio Code.
2. Ve a la sección de **Extensiones** (el ícono de cuadros en la barra lateral izquierda o presiona `Ctrl+Shift+X`).
3. En el buscador escribe **Playwright Test for VSCode**.
4. Selecciona la opción que dice Microsoft (la que tiene el visto azul verificado).
5. Haz clic en **Instalar**.

## 2. Instalar Playwright en tu Proyecto

1. En Visual Studio Code, abre la carpeta donde vas a crear tu proyecto.
2. Abre la terminal integrada del editor (ve al menú superior y selecciona **Terminal** > **New Terminal**).
3. Pega este comando y presiona Enter:
```bash
npm init playwright@latest

```


4. La terminal te hará unas preguntas rápidas para configurar el proyecto. Responde así:
* Elige tu lenguaje preferido (TypeScript o JavaScript).
* Presiona Enter para aceptar la carpeta por defecto donde se guardarán las pruebas (`tests`).
* Escribe **false** si te pregunta por GitHub Actions (para mantenerlo simple por ahora).
* Escribe **true** (o presiona Enter si es la opción por defecto) cuando te pregunte si deseas instalar los navegadores. Esto es obligatorio para que funcione.



---

## 3. Integración de Agentes de IA

Una vez que tienes tu entorno configurado, los agentes de IA entran para ayudarte directamente con la automatización de tus pruebas. Para inicializar estos agentes en tu proyecto, abre la terminal en Visual Studio Code y ejecuta:

```bash
npx playwright init-agents --loop=vscode
``` 

🎭 El planificador: explora la aplicación y genera un plan de prueba en Markdown.
🎭 El generador: transforma el plan Markdown en archivos de prueba de dramaturgo.
🎭 El sanador: ejecuta el conjunto de pruebas y repara automáticamente las pruebas fallidas.