# Estructura del proyecto Playwright

Generado: 2026-05-31

Este archivo lista la estructura principal del workspace y archivos/carpetas relevantes.

```
GuiaPruebaHappy_Presentadores.md
GuiaPruebaHappy.md
package.json
# package.json: dependencias y scripts de ejecución (`npm test`, `playwright test`) (configura scripts, versión de Playwright y reporters según tu entorno)
playwright.config.ts
# Config: ajustes de Playwright (projects, timeouts, reporters) (configurado por el autor; debes ajustar `use.baseURL`, `projects`, `retries` y `outputDir` a tu entorno)
seed.spec.ts
# Seed: script de pruebas iniciales / casos de ejemplo que ejecutan flujo base (asegúrate de configurar endpoints y datos que crea este script)
playwright-report/
	index.html
	data/
		bf756fe78b610580e72c13af5c0772d5367d90bf.md
	trace/
		codeMirrorModule.C3UTv-Ge.css
		defaultSettingsView.ConWv5KN.css
		index.BxQ34UMZ.js
		index.C4Y3Aw8n.css
		index.html
		manifest.webmanifest
		snapshot.html
		sw.bundle.js
		uiMode.Btcz36p_.css
		uiMode.BWTwXl41.js
		uiMode.html
		xtermModule.DYP7pi_n.css
		tests/
		# tests/: Scripts Playwright automatizados y utilidades para E2E
			auth.ts
			# auth.ts: helpers para autenticación (login, tokens y manejo de sesión)
			# (configuración necesaria: selectores de formulario, endpoint de autenticación, manejo de MFA si aplica)
			config.ts
			# config.ts: configuración de entorno para tests (URLs, timeouts, fixtures)
			# (configura `baseUrl`, `defaultTimeout`, y variables de entorno usadas por los tests)
			credentials.ts
			# credentials.ts: datos de prueba / credenciales usadas en los scripts
			# (reemplaza con cuentas de prueba; no subir credenciales reales al repositorio)
			example.spec.ts
			# example.spec.ts: prueba de ejemplo / plantilla para nuevos tests
			seed.spec.ts
			# seed.spec.ts: pruebas de seed y preparación de datos antes de suites
			# (configura datos iniciales, usuarios y permisos necesarios para ejecutar las suites)
	Sprint2/
		CasosHU05.md
		CasosHU07.md
		CasosHU16.md
		CasosHU26.md
		CasosHU27.md
		CasosHU32.md
		CasosHU34.md
		CasosHU41.md
		CasosHU42.md
	Sprint3/
		CasosHU06.md
		CasosHU08.md
		CasosHU09.md
		CasosHU11.md
		CasosHU15.md
		CasosHu23.md
		CasosHU33.md
	Sprint4/
		CasosHU10.md
		CasosHU22.md
		CasosHu34.md
		CasosHU40.md
		CasosHU43.md
		CasosHU48.md
test-results/
tests/
	# tests/: Scripts Playwright automatizados y utilidades para E2E
	auth.ts
	# auth.ts: helpers para autenticación (login, tokens y manejo de sesión)
	config.ts
	# config.ts: configuración de entorno para tests (URLs, timeouts, fixtures)
	credentials.ts
	# credentials.ts: datos de prueba / credenciales usadas en los scripts
	example.spec.ts
	# example.spec.ts: prueba de ejemplo / plantilla para nuevos tests
	seed.spec.ts
	# seed.spec.ts: pruebas de seed y preparación de datos antes de suites
	Sprint1/
		HU01/
			cp-hu01-r1-oferta-exitosa.spec.ts
			cp-hu01-r10-truncado-descripcion.spec.ts
			cp-hu01-r11-bloqueo-titulo-corto.spec.ts
			cp-hu01-r12-bloqueo-descripcion-corta.spec.ts
			cp-hu01-r2-bloqueo-titulo-vacio.spec.ts
			cp-hu01-r3-bloqueo-precio-invalido.spec.ts
			cp-hu01-r4-bloqueo-categorias-vacio.spec.ts
			cp-hu01-r5-bloqueo-descripcion-vacio.spec.ts
			cp-hu01-r6-cancelar-con-boton.spec.ts
			cp-hu01-r7-cancelar-con-x.spec.ts
			cp-hu01-r8-truncado-titulo.spec.ts
			cp-hu01-r9-bloqueo-limite-categorias.spec.ts
		HU02/
			cp-hu02-r1-dashboard-con-ofertas.spec.ts
			cp-hu02-r2-modal-creacion-oferta.spec.ts
			cp-hu02-r3-dashboard-sin-ofertas.spec.ts
		HU03/
			...
		HU17/
			...
	Sprint2/
		HU05/
			...
		HU07/
			...
		HU16/
			...
		HU26/
		HU27/
		HU32/
		HU34/
		HU41/
		HU42/
	Sprint3/
		HU06/
		HU08/
		HU09/
		HU11/
		HU15/
		HU23/
		HU33/
	Sprint4/
		HU10/
		HU22/
		HU34/
		HU40/
		HU43/
		HU48/
```



## Archivos de configuración clave



- **`playwright.config.ts`**: se configuraron `use.baseURL`, `projects` (navegadores/viewport), `timeout`, `retries` y `reporter` para adaptar las ejecuciones a los entornos de prueba.

ejemplo de configuración:

```
import { defineConfig, devices } from '@playwright/test';

/**
 * Read environment variables from file.
 * https://github.com/motdotla/dotenv
 */
// import dotenv from 'dotenv';
// import path from 'path';
// dotenv.config({ path: path.resolve(__dirname, '.env') });

/**
 * See https://playwright.dev/docs/test-configuration.
 */
export default defineConfig({
  testDir: './tests',
  /* Run tests in files in parallel */
  fullyParallel: true,
  /* Fail the build on CI if you accidentally left test.only in the source code. */
  forbidOnly: !!process.env.CI,
  /* Retry on CI only */
  retries: process.env.CI ? 2 : 0,
  /* Opt out of parallel tests on CI. */
  workers: process.env.CI ? 1 : undefined,
  /* Reporter to use. See https://playwright.dev/docs/test-reporters */
  reporter: 'html',
  /* Shared settings for all the projects below. See https://playwright.dev/docs/api/class-testoptions. */
  use: {
    /* Base URL to use in actions like `await page.goto('')`. */
    // baseURL: 'http://localhost:3000',

    /* Collect trace when retrying the failed test. See https://playwright.dev/docs/trace-viewer */
    trace: 'on-first-retry',
  },

  /* Configure projects for major browsers */
  projects: [
    {
      name: 'chromium',
      use: { ...devices['Desktop Chrome'] },
    },

    {
      name: 'firefox',
      use: { ...devices['Desktop Firefox'] },
    },

    {
      name: 'webkit',
      use: { ...devices['Desktop Safari'] },
    },

    /* Test against mobile viewports. */
    // {
    //   name: 'Mobile Chrome',
    //   use: { ...devices['Pixel 5'] },
    // },
    // {
    //   name: 'Mobile Safari',
    //   use: { ...devices['iPhone 12'] },
    // },

    /* Test against branded browsers. */
    // {
    //   name: 'Microsoft Edge',
    //   use: { ...devices['Desktop Edge'], channel: 'msedge' },
    // },
    // {
    //   name: 'Google Chrome',
    //   use: { ...devices['Desktop Chrome'], channel: 'chrome' },
    // },
  ],

  /* Run your local dev server before starting the tests */
  // webServer: {
  //   command: 'npm run start',
  //   url: 'http://localhost:3000',
  //   reuseExistingServer: !process.env.CI,
  // },
});

```


- **`package.json`**:  scripts (`test`, `test:headed`, `report`) y dependencias (versión de Playwright, reporteros, utilidades) para ejecutar las pruebas de forma reproducible.
- **`config.ts`**: variables de entorno como `BASE_URL`, `TIMEOUT` y otras constantes de entorno para separar configuración del código.
- **`credentials.ts`**: cuentas de prueba (usuarios tutor/admin) y sus roles/permissions; documenta que estas credenciales son de prueba y no deben ser usadas en producción.
- **`auth.ts`**: helpers de login y manejo de sesión; documenta los selectores y flujos (login, logout, tokens) que configuraste.
- **`seed.spec.ts`**: Se tienen datos iniciales y escenarios base para que las pruebas puedan correr en cualquier entorno replicable.


## Estructura de carpetas para casos de prueba
- **`tests/`**: carpeta raíz de pruebas.
- **`tests/SprintX/HUYY/`**: subcarpetas organizadas por sprint e historia de usuario (HU) para mantener la trazabilidad.
- **`tests/SprintX/HUYY/cp-huYY-rZ-nombre-corto.spec.ts`**: archivos de prueba específicos para cada regla (rZ) de la historia de usuario (HUYY), siguiendo un formato de nombre consistente para fácil identificación. 
