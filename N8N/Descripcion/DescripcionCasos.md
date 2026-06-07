# Documentación Completa del Flujo n8n: "CasosDC"

## Índice
1. [Introducción General](#introducción-general)
2. [Arquitectura General del Flujo](#arquitectura-general-del-flujo)
3. [Diagrama de Conexiones](#diagrama-de-conexiones)
4. [Descripción Detallada de Nodos](#descripción-detallada-de-nodos)
5. [Análisis de Propiedades y Configuraciones](#análisis-de-propiedades-y-configuraciones)
6. [Flujo de Datos](#flujo-de-datos)
7. [Transformaciones de Datos](#transformaciones-de-datos)
8. [Autenticaciones y Credenciales](#autenticaciones-y-credenciales)
9. [Salida Final](#salida-final)

---

## Introducción General

### Propósito del Flujo

El flujo **CasosDC** (Casos Decision Cases) es un sistema de orquestación automatizado diseñado para:

- Obtener **matrices de decisión** desde Azure DevOps Wiki
- Recopilar **criterios de aceptación** formateados en BDD
- Descargar **ejemplos históricos** de test cases desde Google Drive (CSV)
- Transformar lógica dura + narrativa + ejemplos en **Casos de Prueba detallados**
- Generar scripts de prueba con **Steps y Expected Results** estructurados
- Publicar la documentación de pruebas en Azure DevOps Wiki

### Contexto de Uso

Este flujo es la **culminación del pipeline QA automatizado**:

1. **TablasAC**: Genera matrices de decisión (tablas de verdad)
2. **CriteriosDT**: Traduce matrices a criterios BDD
3. **CasosDC**: Convierte criterios BDD a casos de prueba ejecutables

### Diferencia Clave con Flujos Anteriores

| Aspecto | CriteriosDT | CasosDC |
|:---|:---|:---|
| **Entrada** | Matriz + Imagen | Matriz + Criterios + Ejemplos históricos |
| **Procesamiento** | Traducción BDD | Generación de test cases |
| **Salida** | Criterios en tablas | Cases con Steps/Expected Results |
| **Formato** | Markdown tabular | Markdown estructurado para ejecutables |
| **LLM Model** | Gemini (Vision + Text) | Gemini (Text only) |
| **Ejemplos** | Contexto histórico | CSV descargado de Drive |

### Stack Tecnológico

- **Orquestador**: n8n (Sistema de automatización de flujos)
- **Fuentes de Datos**: 
  - Azure DevOps Wiki (API REST) - 2 endpoints
  - Google Drive (API de Drive) - descarga CSV
- **IA**: Google Gemini Chat Model (generación de casos)
- **Tipo de Integración**: REST APIs, procesamiento de archivos, LLM chain

---

## Arquitectura General del Flujo

### Vista de Alto Nivel

```
ENTRADA (Trigger Manual)
  │
  ├─→ [HTTP Tablas] ─→ [Parse Matrices]
  │                           │
  ├─→ [HTTP CriteriosF] ─→ [Parse Criterios]
  │                           │
  └─→ [Download CSV] ─→ [Extract] ─→ [Contexto]
                                           │
                    Sincronización (Merge1) │
                            │              │
                        [Merge] ◄──────────┘
                            │
                    [Gemini Chat: Generador de Casos]
                            │
                    [Formateo Final]
                            │
                    [Publicación Azure]
                            │
                          SALIDA
```

### Estructura de Ejecución

- **Modo de Ejecución**: Trigger manual
- **Número de Nodos**: 12 nodos activos
- **Cantidad de Conexiones**: 13 conexiones principales
- **Bifurcaciones**: 3 ramas iniciales (desde trigger)
- **Sincronizaciones**: 2 merges (Merge1, Merge)
- **LLM Integration**: Chain LLM con Google Gemini Chat Model

---

## Diagrama de Conexiones

### Tabla Completa de Rutas

| Nodo Origen | Tipo | Nodo Destino | Rama | Orden |
|:---|:---:|:---|:---|:---:|
| When clicking 'Execute workflow' | main[0] | HTTP Tablas | A | 1 |
| When clicking 'Execute workflow' | main[0] | HTTP CriteriosF | B | 1 |
| When clicking 'Execute workflow' | main[0] | Download file | C | 1 |
| HTTP Tablas | main[0] | Code in JavaScript5 | A | 2 |
| HTTP CriteriosF | main[0] | Code in CriteriosF | B | 2 |
| Download file | main[0] | Extract from File | C | 2 |
| Code in JavaScript5 | main[0] | Merge1 (entrada 0) | A | 3 |
| Code in CriteriosF | main[0] | Merge1 (entrada 1) | B | 3 |
| Extract from File | main[0] | Code in Casos | C | 3 |
| Code in Casos | main[0] | Merge (entrada 1) | C | 4 |
| Merge1 | main[0] | Merge (entrada 0) | - | 5 |
| Merge | main[0] | Basic LLM Chain Casos | - | 6 |
| Basic LLM Chain Casos | main[0] | Code in JavaScript4 | - | 7 |
| Code in JavaScript4 | main[0] | HTTP Azure enviar2 | - | 8 |
| Google Gemini Chat Model1 | ai_languageModel | Basic LLM Chain Casos | - | 6 |

### Ejecución Paralela

```
PARALELA 1 (Rama A - Matrices):
  Trigger → HTTP Tablas → Code in JavaScript5 → Merge1[0]

PARALELA 2 (Rama B - Criterios):
  Trigger → HTTP CriteriosF → Code in CriteriosF → Merge1[1]

PARALELA 3 (Rama C - Ejemplos CSV):
  Trigger → Download file → Extract → Code in Casos → Merge[1]

SINCRONIZACIÓN:
  Merge1[0,1] → Merge[0]
  
GENERACIÓN:
  Merge → Basic LLM Chain Casos (con Gemini Chat Model)
  
PUBLICACIÓN:
  Basic LLM Chain → Code in JavaScript4 → HTTP Azure enviar2
```

---

## Descripción Detallada de Nodos

### 1. **When clicking 'Execute workflow'** (Trigger Manual)

#### Propósito
Punto de entrada manual que inicia las tres ramas paralelas del flujo.

#### Configuración
```json
{
  "id": "4c472b60-56b8-40c1-a092-5900a6e84f83",
  "name": "When clicking 'Execute workflow'",
  "type": "n8n-nodes-base.manualTrigger",
  "typeVersion": 1,
  "position": [-784, 32],
  "parameters": {}
}
```

#### Salida
- **Tipo**: Objeto vacío `{}`
- **Propósito**: Iniciar 3 ramas paralelas
- **Parámetros**: Ninguno

#### Conexiones Salientes (3)
- Rama A: HTTP Tablas
- Rama B: HTTP CriteriosF
- Rama C: Download file

---

### 2. **HTTP Tablas** (Rama A - Matrices de Decisión)

#### Propósito
Obtener las matrices de decisión generadas (del flujo TablasAC) que contienen la lógica de prueba.

#### Configuración
```json
{
  "id": "db9f8f86-a47e-46a0-bd5c-46dc4e996d92",
  "name": "HTTP Tablas",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [-320, -128],
  "parameters": {
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1665?includeContent=true&api-version=7.1",
    "authentication": "genericCredentialType",
    "genericAuthType": "httpBasicAuth",
    "options": {}
  },
  "credentials": {
    "httpBasicAuth": {
      "id": "J1QlSdi95FPXq84s",
      "name": "Azure"
    }
  }
}
```

#### Parámetros
| Parámetro | Valor |
|:---|:---|
| **Método HTTP** | GET |
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1665?includeContent=true&api-version=7.1` |
| **Page ID** | 1665 (Matrices/Tablas) |
| **Autenticación** | HTTP Basic Auth |

#### Datos Esperados
```json
{
  "content": "### Nro. HU-01 - Título: Solicitar Tutoría\n#### Matriz de Decisión HU-01\n| ID | Condición | R1 | R2 |..."
}
```

---

### 3. **Code in JavaScript5** (Parser de Matrices)

#### Propósito
Parsear matrices de decisión para extraer: ID HU, título, descripción, tabla y glosario.

#### Ubicación en Flujo
Entrada: `items[0].json.content` (de HTTP Tablas)

#### Código Principal

```javascript
const content = items[0].json.content;

if (!content) {
  return [{ json: { error: "El nodo HTTP no trajo contenido." } }];
}

// Dividir por cabeceras HU
const splitRegex = /(?:\r?\n|^)(?=(?:#{1,6}\s*|[\*_]*)\s*(?:Nro\.?)?s*HU\s*-?\s*\d+)/i;
const bloques = content.split(splitRegex);
const historias = [];

bloques.forEach(bloque => {
  const texto = bloque.trim();

  // Extraer ID y TÍTULO
  const idMatch = texto.match(/HU\s*-?\s*(\d+)/i);

  if (idMatch) {
    const idNum = idMatch[1];
    
    // Limpiar título
    const firstLine = texto.split(/\r?\n/)[0];
    const tituloLimpio = firstLine
        .replace(/#{1,6}/g, '')
        .replace(/\*/g, '')
        .replace(/Nro\.?/i, '')
        .replace(new RegExp(`HU\\s*-?\\s*${idNum}`, 'i'), '')
        .replace(/-\s*Título\s*:/i, '')
        .replace(/Título\s*:/i, '')
        .replace(/^[-\s:|]+/, '')
        .trim();

    // Extraer DESCRIPCIÓN
    let descripcion = "Descripción no detectada";
    const regexDesc = /Descripción\s*:?\s*([\s\S]*?)(?=\r?\n[ \t]*(?:#{1,6}|\*\*)?[ \t]*(?:PASO\s+\d+|Matriz\s+de))/i;
    const descMatch = texto.match(regexDesc);
    
    if (descMatch) {
        descripcion = descMatch[1].trim();
    }

    // Extraer MATRICES
    const regexMatriz = /(?:^|\r?\n)[ \t]*(?:#{1,6}|\*\*)?[ \t]*(?:PASO\s+\d+|Matriz\s+de)[\s\S]*?(?=(?:\r?\n[ \t]*(?:#{1,6}|\*\*)?[ \t]*GLOSARIO)|$)/gi;
    let matricesExtraidas = [];
    let matchM;
    while ((matchM = regexMatriz.exec(texto)) !== null) {
        matricesExtraidas.push(matchM[0].trim());
    }
    let matriz = matricesExtraidas.length > 0 ? matricesExtraidas.join("\n\n") : "Matriz no detectada";

    // Extraer GLOSARIOS
    const regexGlosario = /(?:^|\r?\n)[ \t]*(?:#{1,6}|\*\*)?[ \t]*GLOSARIO[\s\S]*?(?=(?:\r?\n[ \t]*(?:#{1,6}|\*\*)?[ \t]*(?:PASO\s+\d+|Matriz\s+de))|$)/gi;
    let glosariosExtraidos = [];
    let matchG;
    while ((matchG = regexGlosario.exec(texto)) !== null) {
        glosariosExtraidos.push(matchG[0].trim());
    }
    let glosario = glosariosExtraidos.length > 0 ? glosariosExtraidos.join("\n\n") : "Glosario no detectado";

    historias.push({
      json: {
        id_hu: `HU-${idNum}`,
        titulo: tituloLimpio,
        descripcion: descripcion,
        tabla_decision_generada: matriz, 
        glosario_acciones: glosario      
      }
    });
  }
});

if (historias.length === 0) {
    return [{ 
        json: { 
            warning: "No se detectaron historias con el formato esperado.",
            texto_inicio: content.substring(0, 500) 
        } 
    }];
}

return historias;
```

#### Salida
```json
[
  {
    "json": {
      "id_hu": "HU-01",
      "titulo": "Solicitar Tutoría",
      "descripcion": "COMO estudiante QUIERO solicitar...",
      "tabla_decision_generada": "#### PASO 1\n| ID | Condición | R1 | R2 |...",
      "glosario_acciones": "### GLOSARIO...\n* **A1:** Enviar solicitud..."
    }
  }
]
```

---

### 4. **HTTP CriteriosF** (Rama B - Criterios de Aceptación)

#### Propósito
Obtener criterios de aceptación en formato BDD (del flujo CriteriosDT).

#### Configuración
```json
{
  "id": "d56a3ed5-50cc-43e8-8078-3f732b632996",
  "name": "HTTP CriteriosF",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [-336, 128],
  "parameters": {
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1667?includeContent=true&api-version=7.1",
    "authentication": "genericCredentialType",
    "genericAuthType": "httpBasicAuth",
    "options": {}
  },
  "credentials": {
    "httpBasicAuth": {
      "id": "J1QlSdi95FPXq84s",
      "name": "Azure"
    }
  }
}
```

#### Parámetros
| Parámetro | Valor |
|:---|:---|
| **Método HTTP** | GET |
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1667?includeContent=true&api-version=7.1` |
| **Page ID** | 1667 (Criterios formateados) |

---

### 5. **Code in CriteriosF** (Parser de Criterios)

#### Propósito
Extraer criterios de aceptación en formato BDD y prepararlos para inyección en LLM.

#### Código

```javascript
const content = items[0].json.content;

if (!content) {
  return [{ json: { error: "No se pudo leer el contenido de la Wiki." } }];
}

// Capturar bloques de HU con criterios
const regex = /###\s*Nro\.\s*HU-?(\d+)\s*-\s*Título:\s*([^\n\r]+)([\s\S]*?)(?=\n\s*---\s*\n|$)/gi;

let match;
const paquetes = [];

while ((match = regex.exec(content)) !== null) {
  const idRaw = match[1];
  const tituloRaw = match[2].trim();
  const cuerpoRaw = match[3];
  
  const idHuFormatted = `HU-${idRaw}`;

  const bloqueCompleto = `### Nro. ${idHuFormatted} - Título: ${tituloRaw}\n${cuerpoRaw}`;

  if (cuerpoRaw.length > 20) {
    paquetes.push({
      json: {
        id_hu: idHuFormatted,
        titulo: tituloRaw,
        input_para_llm: bloqueCompleto.trim()
      }
    });
  }
}

if (paquetes.length === 0) {
    return [{ json: { warning: "No se encontraron bloques con el formato '### Nro. HU-...'" } }];
}

return paquetes;
```

#### Salida
```json
[
  {
    "json": {
      "id_hu": "HU-01",
      "titulo": "Solicitar Tutoría",
      "input_para_llm": "### Nro. HU-01 - Título: Solicitar Tutoría\n#### Criterios de aceptación HU-01\n| **Escenario** |..."
    }
  }
]
```

---

### 6. **Download file** (Rama C - Ejemplos Históricos)

#### Propósito
Descargar archivo CSV con ejemplos históricos de test cases desde Google Drive.

#### Configuración
```json
{
  "id": "79649116-db02-4ca9-8a7b-65abe8810209",
  "name": "Download file",
  "type": "n8n-nodes-base.googleDrive",
  "typeVersion": 3,
  "position": [-352, 368],
  "parameters": {
    "operation": "download",
    "fileId": {
      "__rl": true,
      "value": "1W0hPHn5xXDOkAvoCCUEFH_p3G4KoGFI1",
      "mode": "list",
      "cachedResultName": "Casos1.csv",
      "cachedResultUrl": "https://drive.google.com/file/d/1W0hPHn5xXDOkAvoCCUEFH_p3G4KoGFI1/view?usp=drivesdk"
    },
    "options": {}
  },
  "credentials": {
    "googleDriveOAuth2Api": {
      "id": "KRo0vEZn7fvpO3D1",
      "name": "Google Drive account"
    }
  }
}
```

#### Parámetros
| Parámetro | Valor |
|:---|:---|
| **Operación** | download |
| **File ID** | 1W0hPHn5xXDOkAvoCCUEFH_p3G4KoGFI1 |
| **Nombre del Archivo** | Casos1.csv |
| **Propósito** | Descarga ejemplos de test cases históricos |

#### Datos Descargados
```csv
ID,Título,Pre-condiciones,Steps,Expected Results
CP-HU01-R1,Solicitud exitosa,Usuario logueado,1. Navegar a Solicitar...,El sistema envía...
CP-HU01-R2,Campo vacío,Usuario logueado,1. Navegar a Solicitar...,Se muestra error...
...
```

---

### 7. **Extract from File** (Extractor CSV)

#### Propósito
Convertir archivo CSV descargado en array de objetos JSON.

#### Configuración
```json
{
  "id": "7c637ea6-7d86-46c6-8eff-cac1ff653d35",
  "name": "Extract from File",
  "type": "n8n-nodes-base.extractFromFile",
  "typeVersion": 1.1,
  "position": [-64, 368],
  "parameters": {
    "options": {
      "delimiter": ";",
      "headerRow": false
    }
  }
}
```

#### Parámetros
| Parámetro | Valor |
|:---|:---|
| **Delimitador** | ; (punto y coma) |
| **Fila de Encabezado** | false |

#### Salida
```json
[
  {
    "json": {
      "column_1": "CP-HU01-R1",
      "column_2": "Solicitud exitosa",
      "column_3": "Usuario logueado",
      "column_4": "1. Navegar a Solicitar...",
      "column_5": "El sistema envía..."
    }
  }
]
```

---

### 8. **Code in Casos** (Formatea Ejemplos)

#### Propósito
Convertir array CSV en bloque de texto formateado para usar como contexto en LLM.

#### Código

```javascript
const todasLasFilas = items.map(item => item.json);

const textoContexto = JSON.stringify(todasLasFilas);

return [{
    json: {
        contexto_entrenamiento: textoContexto
    }
}];
```

#### Salida
```json
{
  "json": {
    "contexto_entrenamiento": "[{\"column_1\":\"CP-HU01-R1\",\"column_2\":\"Solicitud exitosa\",...}]"
  }
}
```

---

### 9. **Merge1** (Sincronización Ramas A y B)

#### Propósito
Combinar matrices y criterios por `id_hu`.

#### Configuración
```json
{
  "id": "216ba528-1dd2-4345-9312-678baeae8ac5",
  "name": "Merge1",
  "type": "n8n-nodes-base.merge",
  "typeVersion": 3.2,
  "position": [432, -32],
  "parameters": {
    "mode": "combine",
    "fieldsToMatchString": "=id_hu",
    "options": {}
  }
}
```

#### Comportamiento
- **Entrada 0**: Matrices (Code in JavaScript5)
- **Entrada 1**: Criterios (Code in CriteriosF)
- **Modo**: Combina items que coincidan por `id_hu`

#### Salida Esperada
```json
[
  {
    "json": {
      "id_hu": "HU-01",
      "titulo": "Solicitar Tutoría",
      "descripcion": "...",
      "tabla_decision_generada": "...",
      "glosario_acciones": "...",
      "input_para_llm": "### Nro. HU-01..."
    }
  }
]
```

---

### 10. **Merge** (Fusión de Tres Ramas)

#### Propósito
Combinar todas las fuentes: matrices+criterios + ejemplos históricos.

#### Configuración
```json
{
  "id": "239c1bdb-308e-4808-9590-1474e516601b",
  "name": "Merge",
  "type": "n8n-nodes-base.merge",
  "typeVersion": 3.2,
  "position": [832, 96],
  "parameters": {
    "mode": "combine",
    "combineBy": "combineAll",
    "options": {}
  }
}
```

#### Entradas
- **[0]**: Merge1 (matrices + criterios)
- **[1]**: Code in Casos (contexto histórico)

#### Salida
```json
[
  {
    "json": {
      "id_hu": "HU-01",
      "titulo": "Solicitar Tutoría",
      "tabla_decision_generada": "...",
      "glosario_acciones": "...",
      "input_para_llm": "..."
    }
  },
  {
    "json": {
      "contexto_entrenamiento": "[...]"
    }
  }
]
```

---

### 11. **Basic LLM Chain Casos** (Generador Principal)

#### Propósito
Usar Google Gemini Chat para transformar matrices + criterios + ejemplos en casos de prueba estructurados.

#### Tipo de Nodo
`@n8n/n8n-nodes-langchain.chainLlm`

#### Configuración
```json
{
  "id": "ff1bda01-a3ae-4c1f-92bb-ef6efce18887",
  "name": "Basic LLM Chain Casos",
  "type": "@n8n/n8n-nodes-langchain.chainLlm",
  "typeVersion": 1.7,
  "position": [1136, -16],
  "parameters": {
    "promptType": "define",
    "text": "=Actúa como un QA Lead Senior, meticuloso y experto en documentación técnica.\n\nOBJETIVO PRINCIPAL:\nTransformar la **MATRIZ DE DECISIONES** (Lógica Dura) y los **CRITERIOS ASOCIADOS** (Detalle Narrativo) en un PLAN DE PRUEBAS DETALLADO.\n\n...[PROMPT EXTENSO]...",
    "batching": {}
  }
}
```

#### Prompt Principal (Secciones)

**SECCIÓN 1: LÓGICA DE GENERACIÓN**

Genera un Caso de Prueba independiente por cada Regla (R1, R2, R3...) de la matriz.

1. **Construcción de STEPS**:
   - **Inicio**: Pasos de navegación previos (login, etc.)
   - **Interacción**: Traduce condiciones de tabla en acciones
   - **Cierre**: Último clic en botón principal

2. **Construcción de EXPECTED RESULTS**:
   - **Estado**: Pantalla que carga o modal que se cierra
   - **Detalle Visual**: Texto exacto del criterio asociado
   - **Mensajes**: Literales del criterio
   - **Estado de elementos**: Botones habilitados/deshabilitados

3. **Guía de Estilo**:
   - Usa ejemplos históricos como referencia
   - Mantén tono profesional
   - Estructura Markdown consistente

**SECCIÓN 2: FORMATO DE SALIDA (ESTRICTO)**

```markdown
## ID: CP-{{ $json.id_hu }}-[Número Regla]
**Título:** [Título descriptivo único para este caso]
**Prioridad:** [Alta/Media/Baja]
**Tipo:** Funcional
**Pre-condiciones:** [Estado previo necesario]

**Steps:**
 1. [Paso de navegación/login implícito]
 2. [Paso derivado del input 1 de la matriz]
 3. [Paso derivado del input 2...]
 ...
 N. Hacer clic en el botón [Nombre del botón]

**Expected Results:**
 - [Resultado principal: ej. El sistema redirige a la pantalla Dashboard]
 - [Validación visual detallada extraída de Criterios]
 - [Mensaje exacto: ej. Se muestra el toast "Datos guardados correctamente"]
 - [Estado de elementos: ej. El botón 'Guardar' se deshabilita]
```

**SECCIÓN 3: ENTRADA DE DATOS**

```
TABLA DE DECISIONES (Lógica):
{{ $json.tabla_decision_generada }}
{{ $json.glosario_acciones }}

CRITERIOS (Detalle Visual y Narrativo):
{{ $json.input_para_llm }}

EJEMPLOS GUÍA (Estilo):
{{ $json.contexto_entrenamiento }}
```

#### Modelo de IA
- **Tipo**: Google Gemini Chat Model
- **No es visión**: Solo procesa texto
- **Conexión**: Referencia a nodo "Google Gemini Chat Model1"

---

### 12. **Google Gemini Chat Model1** (Modelo IA)

#### Propósito
Proveedor del modelo de lenguaje para el LLM Chain.

#### Configuración
```json
{
  "id": "5ad6322b-be43-4927-90ae-fccbf0d637ee",
  "name": "Google Gemini Chat Model1",
  "type": "@n8n/n8n-nodes-langchain.lmChatGoogleGemini",
  "typeVersion": 1,
  "position": [1168, 336],
  "parameters": {
    "options": {}
  },
  "credentials": {
    "googlePalmApi": {
      "id": "qy2on0OQFKvp9WNd",
      "name": "Google Gemini(PaLM) Api account"
    }
  }
}
```

#### Parámetros
| Parámetro | Valor |
|:---|:---|
| **Tipo de Nodo** | Language Model (LLM Chat) |
| **Proveedor** | Google Gemini |
| **Credencial** | Google Gemini(PaLM) Api account |
| **Modelo** | gemini (por defecto) |

---

### 13. **Code in JavaScript4** (Formateo Final)

#### Propósito
Compilar casos de prueba generados en documento Markdown para publicación.

#### Código

```javascript
const scriptsGenerados = items.map(item => item.json.text || item.json.output);

const contenidoUnido = scriptsGenerados.join('\n\n---\n\n');

const fecha = new Date().toISOString().split('T')[0];
const documentoFinal = `# Reporte de Scripts de Prueba Automatizados (S1)\n> Generado el: ${fecha}\n\n${contenidoUnido}`;

return [{
    json: {
        contenido_wiki: documentoFinal
    }
}];
```

#### Salida
```json
{
  "json": {
    "contenido_wiki": "# Reporte de Scripts de Prueba Automatizados (S1)\n> Generado el: 2026-06-06\n\n## ID: CP-HU-01-R1\n**Título:** Solicitud exitosa..."
  }
}
```

---

### 14. **HTTP Azure enviar2** (Publicación Final)

#### Propósito
Enviar documento de casos de prueba a Azure DevOps Wiki mediante PUT.

#### Configuración
```json
{
  "id": "168254a4-ba3b-4bb4-98a6-fd31cf1553a6",
  "name": "HTTP Azure enviar2",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [1760, -16],
  "parameters": {
    "method": "PUT",
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages?path=/Testing(IA)/Sprint4/CasosS4&api-version=7.1",
    "authentication": "genericCredentialType",
    "genericAuthType": "httpBasicAuth",
    "sendHeaders": true,
    "headerParameters": {
      "parameters": [
        {
          "name": "Content-Type",
          "value": "application/json"
        }
      ]
    },
    "sendBody": true,
    "bodyParameters": {
      "parameters": [
        {
          "name": "content",
          "value": "={{ $json.contenido_wiki }}"
        }
      ]
    },
    "options": {}
  },
  "credentials": {
    "httpBasicAuth": {
      "id": "J1QlSdi95FPXq84s",
      "name": "Azure"
    }
  }
}
```

#### Parámetros de Solicitud
| Parámetro | Valor |
|:---|:---|
| **Método HTTP** | PUT |
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages?path=/Testing(IA)/Sprint4/CasosS4&api-version=7.1` |
| **Path de Página** | /Testing(IA)/Sprint4/CasosS4 |
| **Cuerpo** | JSON con propiedad `content` |

---

## Análisis de Propiedades y Configuraciones

### URLs de Azure Utilizadas

| Nodo | Endpoint | Page ID | Propósito |
|:---|:---|:---:|:---|
| HTTP Tablas | PoliTutoriasAI.wiki | 1665 | Matrices de decisión |
| HTTP CriteriosF | PoliTutoriasAI.wiki | 1667 | Criterios BDD |
| HTTP Azure enviar2 | PoliTutoriasAI.wiki | - (path) | Publicación de casos |

### Credenciales Utilizadas

#### 1. Azure DevOps (HTTP Basic Auth)
- **ID**: J1QlSdi95FPXq84s
- **Nombre**: "Azure"
- **Nodos**: HTTP Tablas, HTTP CriteriosF, HTTP Azure enviar2
- **Permisos**: Read Wiki, Write Wiki

#### 2. Google Drive OAuth2
- **ID**: KRo0vEZn7fvpO3D1
- **Nombre**: "Google Drive account"
- **Nodos**: Download file
- **Permisos**: Drive file read

#### 3. Google Gemini API
- **ID**: qy2on0OQFKvp9WNd
- **Nombre**: "Google Gemini(PaLM) Api account"
- **Nodos**: Google Gemini Chat Model1
- **Modelo**: Gemini (chat text)

---

## Flujo de Datos

### Ruta Completa de Ejecución

```
TRIGGER
  │
  ├─ [Rama A] HTTP Tablas
  │    ↓
  │    Code in JavaScript5
  │    ↓
  │    Matriz + Glosario → Merge1[0]
  │
  ├─ [Rama B] HTTP CriteriosF
  │    ↓
  │    Code in CriteriosF
  │    ↓
  │    Criterios BDD → Merge1[1]
  │
  └─ [Rama C] Download CSV
       ↓
       Extract from File
       ↓
       Code in Casos
       ↓
       Contexto Histórico → Merge[1]

SINCRONIZACIÓN
  Merge1[0,1] → Fusión (Matriz + Criterios)
  ↓
  Merge[0] ← Contexto Histórico
  ↓
  [Basic LLM Chain: Genera Casos]
       ↑
       │ (usa)
       │
  [Google Gemini Chat Model]
  ↓
  [Code in JavaScript4: Formatea]
  ↓
  [HTTP Azure enviar2: Publica]
  ↓
  FIN
```

### Flujo Específico de una HU

```
HU-01 Solicitar Tutoría
  ├─ Rama A: Tabla de Decisión
  │    R1: Usuario logueado + Campos llenos → Enviar
  │    R2: Usuario logueado + Campo vacío → Error
  │    R3: Usuario no logueado → Redirect login
  │    ...
  │
  ├─ Rama B: Criterios BDD
  │    R1: Dado... cuando... entonces "Se redirige a Dashboard"
  │    R2: Dado... cuando... entonces "Muestra error campo requerido"
  │    R3: Dado... cuando... entonces "Redirige a login"
  │    ...
  │
  └─ Rama C: Ejemplos Históricos CSV
       CP-HU01-R1: Solicitud exitosa [Steps] [Expected Results]
       CP-HU01-R2: Campo vacío [Steps] [Expected Results]
       CP-HU01-R3: No logueado [Steps] [Expected Results]

GEMINI COMBINA:
  - Lógica de matriz (R1, R2, R3)
  - Narrativa de criterios (el "entonces" con detalles)
  - Estilo de ejemplos históricos

SALIDA:
  CP-HU-01-R1: Solicitud exitosa
    Steps:
      1. Iniciar sesión como estudiante
      2. Navegar a "Solicitar Tutoría"
      3. Ingresar "Juan Pérez" en Tutor
      4. Seleccionar "Ingeniería de Software" en Carrera
      5. Hacer clic en "Enviar"
    
    Expected Results:
      - Se redirige a "Mis Solicitudes"
      - Se visualiza la tarjeta de solicitud recién creada
      - Muestra toast "Solicitud enviada correctamente" en verde
      - El botón "Ver Detalles" está habilitado

  CP-HU-01-R2: Campo Tutor vacío
    Steps:
      1. Iniciar sesión como estudiante
      2. Navegar a "Solicitar Tutoría"
      3. Dejar campo "Tutor" vacío
      4. Hacer clic en "Enviar"
    
    Expected Results:
      - Permanece en "Solicitar Tutoría"
      - Muestra error "Campo 'Tutor' es obligatorio" en rojo
      - El formulario conserva otros valores ingresados
```

---

## Transformaciones de Datos

### T1: Matrices Markdown → Objetos Estructurados

**Entrada**: Markdown con tablas y glosarios
**Proceso**: Regex en Code in JavaScript5
**Salida**: JSON con tabla_decision_generada y glosario_acciones

### T2: Criterios BDD → Objetos Estructurados

**Entrada**: Criterios en tabla BDD
**Proceso**: Regex en Code in CriteriosF
**Salida**: JSON con input_para_llm (criterios completos)

### T3: CSV Histórico → Contexto de Entrenamiento

**Entrada**: Archivo CSV descargado
**Proceso**: Extract + JSON stringify
**Salida**: Texto con ejemplos formateados

### T4: Fusión Multinivel

**Entrada**: 3 streams independientes
**Proceso**: Merge1 (por id_hu) + Merge (combineAll)
**Salida**: Item consolidado con matriz + criterios + histórico

### T5: Generación de Casos (Núcleo del Valor)

**Entrada**:
- Matriz (lógica combinatorial)
- Criterios BDD (detalle visual + narrativa)
- Ejemplos históricos (formato y estilo)

**Proceso**: 
- Gemini Lee matriz (R1, R2, R3...)
- Para cada R, consulta criterios asociados
- Usa ejemplos como guía de estilo
- Genera Steps detallados
- Genera Expected Results exactos

**Salida**:
```markdown
## ID: CP-HU-01-R1
**Título:** Solicitud exitosa con todos los campos completos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado en pantalla principal

**Steps:**
 1. Navegar a "Solicitar Tutoría"
 2. Ingresar "Juan Pérez" en "Tutor"
 3. Seleccionar "Ingeniería de Software" en "Carrera"
 4. Hacer clic en "Enviar"

**Expected Results:**
 - Se redirige a "Mis Solicitudes"
 - Se visualiza tarjeta con solicitud creada
 - Toast "Solicitud enviada correctamente" en verde
 - Botón "Ver Detalles" habilitado
```

---

## Ventajas del Enfoque CasosDC

### Frente a Procesos Manuales
1. **100% Automatizado**: Sin intervención humana
2. **Consistencia**: Sigue estructura + estilo histórico
3. **Velocidad**: Genera decenas de casos en segundos
4. **Cobertura**: Un caso por cada regla + extras inferidos

### Frente a Otros Flujos QA
| Aspecto | Tablas AC | Criterios DT | Casos DC |
|:---|:---|:---|:---|
| **Salida** | Matriz | Criterios BDD | Casos ejecutables |
| **Nivel de Detalle** | Lógica | Narrativa | Procedural |
| **Uso Directo** | Diseño de prueba | Documentación | Ejecución de prueba |
| **Reutilizable** | Criterios DT | Casos DC | Scripts (Cypress, etc.) |

---

## Salida Final

### Estructura del Documento Publicado

```markdown
# Reporte de Scripts de Prueba Automatizados (S1)
> Generado el: 2026-06-06

---

## ID: CP-HU-01-R1
**Título:** Solicitud exitosa con datos completos
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado en pantalla principal

**Steps:**
 1. Navegar a sección "Solicitar Tutoría"
 2. Ingresar "Juan Pérez" en el campo "Tutor"
 3. Seleccionar "Ingeniería de Software" en dropdown "Carrera"
 4. Ingresar "15" en campo "Precio por hora"
 5. Hacer clic en el botón "Enviar Solicitud"

**Expected Results:**
 - El sistema valida datos según regla SOL-02
 - Se redirige a la pantalla "Mis Solicitudes"
 - Se visualiza tarjeta con solicitud recién creada
 - Se muestra toast "Solicitud enviada correctamente" en color verde
 - El estado de la solicitud es "Pendiente"
 - El botón "Cancelar" está habilitado

---

## ID: CP-HU-01-R2
**Título:** Rechazo por campo Tutor vacío
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado en pantalla "Solicitar Tutoría"

**Steps:**
 1. Dejar el campo "Tutor" vacío
 2. Ingresar "Ingeniería de Software" en "Carrera"
 3. Ingresar "15" en "Precio por hora"
 4. Hacer clic en "Enviar Solicitud"

**Expected Results:**
 - Permanece en la pantalla "Solicitar Tutoría"
 - Se muestra mensaje de error: "El campo 'Tutor' es obligatorio" en color rojo
 - El mensaje se posiciona bajo el campo "Tutor"
 - Los otros campos conservan los valores ingresados
 - El botón "Enviar" sigue habilitado

---

## ID: CP-HU-01-R3
**Título:** Rechazo por precio negativo
**Prioridad:** Media
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado en pantalla "Solicitar Tutoría"

**Steps:**
 1. Ingresar "Juan Pérez" en "Tutor"
 2. Seleccionar "Ingeniería de Software" en "Carrera"
 3. Ingresar "-5" en "Precio por hora"
 4. Hacer clic en "Enviar Solicitud"

**Expected Results:**
 - Permanece en la pantalla "Solicitar Tutoría"
 - Se muestra validación: "El precio debe ser un valor positivo" en rojo
 - El campo "Precio por hora" se resalta con borde rojo
 - Los datos no se guardan

---

## ID: CP-HU-01-R4
**Título:** Validación de anticipación mínima (SOL-02)
**Prioridad:** Alta
**Tipo:** Funcional
**Pre-condiciones:** Estudiante logueado; faltan < 12 horas para tutoría

**Steps:**
 1. Navegar a "Solicitar Tutoría"
 2. Completar todos los campos con datos válidos
 3. Seleccionar fecha/hora que está a menos de 12 horas
 4. Hacer clic en "Enviar"

**Expected Results:**
 - Permanece en "Solicitar Tutoría"
 - Muestra error: "Debe haber mínimo 12 horas de anticipación para solicitar tutoría"
 - La fecha/hora problemática se resalta
 - Los datos no se guardan

---

[Más casos para HU-01...]

---

## ID: CP-HU-02-R1
**Título:** Cancelación exitosa en estado Pendiente
...

```

### Publicación en Azure

**Ubicación**: `/Testing(IA)/Sprint4/CasosS4`

**Contenido**: Documento completo con todos los casos de prueba

**Método**: PUT a Wiki API

---

## Comparativa: Flujos TablasAC → CriteriosDT → CasosDC

| Fase | Entrada | Salida | Propósito |
|:---|:---|:---|:---|
| **TablasAC** | Imágenes | Matrices de decisión | Extraer lógica |
| **CriteriosDT** | Matrices | Criterios BDD | Documentar requisitos |
| **CasosDC** | Criterios + Ejemplos | Casos de prueba | Ejecutar pruebas |

### Pipeline Completo

```
Prototipos (PNG)
    ↓ [TablasAC]
Matrices de Decisión
    ↓ [CriteriosDT]
Criterios de Aceptación (BDD)
    ↓ [CasosDC]
Casos de Prueba Ejecutables
    ↓ [Manual/Automation]
Test Execution → Results
```

---

## Conclusión

El flujo **CasosDC** es la etapa final del pipeline automatizado de QA que:

1. **Consolida** lógica (matrices) + narrativa (criterios) + experiencia (histórico)
2. **Genera** casos de prueba profesionales y estructura con el formato de industria estándar
3. **Optimiza** cobertura: Un caso por regla + casos adicionales derivados de criterios
4. **Documenta** pasos y validaciones con precisión procedural
5. **Automatiza** lo que manualmente tomaría horas de un QA Senior

**Salida Final**: Repositorio de casos de prueba listos para ejecución manual, integración con herramientas de automatización (Cypress, Selenium, etc.), o auditoría de cobertura de pruebas.

---

**Documento Generado**: 6 de junio de 2026
**Versión del Flujo**: aXLPWUYLuaplvpET (CasosDC)
**Modelo IA Utilizado**: Google Gemini Chat Model
**Estadísticas**: 12 nodos, 13 conexiones, 3 ramas paralelas
