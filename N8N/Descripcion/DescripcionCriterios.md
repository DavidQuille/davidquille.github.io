# Documentación Completa del Flujo n8n: "CriteriosDT"

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

El flujo **CriteriosDT**  es un sistema avanzado de orquestación automatizado diseñado para:

- Extraer **historias de usuario (HU)** desde Azure DevOps Wiki
- Obtener **matrices de decisión** generadas previamente (tablas de verdad)
- Recopilar **criterios históricos** como ejemplos de entrenamiento para IA
- Descargar y procesar **frames/prototipados** desde Google Drive
- Analizar imágenes con IA (Google Gemini 2.5 Flash) para generar **Criterios de Aceptación en formato BDD**
- Publicar los criterios generados en Azure DevOps Wiki

### Contexto de Uso

Este flujo forma parte de un sistema de generación automatizada de criterios de aceptación que **evoluciona el enfoque TablasAC**:

- **TablasAC**: Genera matrices de decisión (tablas de verdad) basadas en lógica visual
- **CriteriosDT**: Toma esas matrices + ejemplos históricos + imágenes y **genera criterios BDD finales** con lenguaje natural refinado

### Diferencias Clave con TablasAC

| Aspecto | TablasAC | CriteriosDT |
|:---|:---|:---|
| **Entrada principal** | Imágenes de prototipos | Matrices de decisión + imágenes |
| **Contexto** | Observaciones técnicas | Criterios históricos (entrenamiento) |
| **Salida** | Matrices de decisión | Criterios de aceptación BDD |
| **Ramas iniciales** | 2 | 3 |
| **Modelo IA** | Gemini (análisis visual) | Gemini (traducción + enriquecimiento) |
| **Pasos en Glosario** | Validaciones visuales | Pasos detallados con valores reales |

### Stack Tecnológico

- **Orquestador**: n8n (Sistema de automatización de flujos)
- **Fuentes de Datos**: 
  - Azure DevOps Wiki (API REST) - 3 endpoints diferentes
  - Google Drive (API de Drive)
- **IA**: Google Gemini 2.5 Flash (traducción de criterios)
- **Tipo de Integración**: REST APIs, procesamiento de imágenes, lógica de decisión

---

## Arquitectura General del Flujo

### Vista de Alto Nivel

```
ENTRADA (Trigger Manual)
  │
  ├─→ [HTTP Criterios] ─→ [Parse Criterios] ─→ [Formatea Ejemplos]
  │                                                     │
  ├─→ [HTTP Tablas] ─→ [Extrae Matrices]             │
  │                                                     │
  └─→ [HTTP HU] ─→ [Extrae Frames] ─→ [Busca Drive] ─→ [Descarga] ─→ [Combina] ─→ [Agrupa]
                                                                                          │
                                                                                          │
Sincronización (Merge1) ────────────────────────────────────────────────────────────────┘
        │
  Fusión (Merge) ◄─────────────────────────────────────────────────────────────────────
        │
  [Analizar Imagen + Contexto con Gemini]
        │
  [Formatea Documento Final (BDD)]
        │
  [Enviar a Azure DevOps Wiki]
        │
      SALIDA
```

### Estructura de Ejecución

- **Modo de Ejecución**: Trigger manual
- **Número de Nodos**: 17 nodos activos
- **Cantidad de Conexiones**: 18 conexiones principales
- **Bifurcaciones**: 3 ramas iniciales (desde trigger)
- **Sincronizaciones**: 2 merges (Merge, Merge1)
- **Ejecución Paralela**: Ramas independientes hasta Merge1

---

## Diagrama de Conexiones

### Tabla Completa de Rutas

| Nodo Origen | Tipo | Nodo Destino | Rama | Orden |
|:---|:---:|:---|:---|:---:|
| When clicking 'Execute workflow' | main[0] | HTTP Criterios | A | 1 |
| When clicking 'Execute workflow' | main[0] | HTTP Tablas | B | 1 |
| When clicking 'Execute workflow' | main[0] | HTTP HU | C | 1 |
| HTTP Criterios | main[0] | Code in Criterios | A | 2 |
| Code in Criterios | main[0] | Code in JavaScript | A | 3 |
| Code in JavaScript | main[0] | Merge (entrada 1) | A | 8 |
| HTTP Tablas | main[0] | Code in JavaScript5 | B | 2 |
| Code in JavaScript5 | main[0] | Merge1 (entrada 0) | B | 6 |
| HTTP HU | main[0] | Code in JavaScript9 | C | 2 |
| Code in JavaScript9 | main[0] | Code in JavaScript6 | C | 3 |
| Code in JavaScript6 | main[0] | Search files and folders | C | 4 |
| Search files and folders | main[0] | Download file1 | C | 5 |
| Download file1 | main[0] | Code in JavaScript7 | C | 6 |
| Code in JavaScript7 | main[0] | Code in JavaScript8 | C | 7 |
| Code in JavaScript8 | main[0] | Merge1 (entrada 1) | C | 8 |
| Merge1 | main[0] | Merge (entrada 0) | - | 9 |
| Merge | main[0] | Analyze an image | - | 10 |
| Analyze an image | main[0] | Code in JavaScript1 | - | 11 |
| Code in JavaScript1 | main[0] | HTTP Azure enviar | - | 12 |

### Ejecución Paralela Detallada

```
PARALELA 1 (Rama A - Criterios):
  Trigger → HTTP Criterios → Code in Criterios → Code in JavaScript → Merge[1]

PARALELA 2 (Rama B - Tablas):
  Trigger → HTTP Tablas → Code in JavaScript5 → Merge1[0]

PARALELA 3 (Rama C - HU + Imágenes):
  Trigger → HTTP HU → Code in JavaScript9 → Code in JavaScript6 → 
    Search Drive → Download → Code in JavaScript7 → Code in JavaScript8 → Merge1[1]

SINCRONIZACIÓN:
  Merge1[0,1] → Merge[0]

FUSIÓN FINAL:
  Merge → Analyze → Code in JavaScript1 → HTTP Azure enviar
```

---

## Descripción Detallada de Nodos

### 1. **When clicking 'Execute workflow'** (Trigger Manual)

#### Propósito
Punto de entrada manual que inicia las tres ramas paralelas del flujo.

#### Configuración
```json
{
  "id": "55481586-6b03-42e3-b9dd-0dc66c5ee10f",
  "name": "When clicking 'Execute workflow'",
  "type": "n8n-nodes-base.manualTrigger",
  "typeVersion": 1,
  "position": [-2048, 1008],
  "parameters": {}
}
```

#### Salida
- **Tipo**: Objeto vacío `{}`
- **Propósito**: Sincronizador de tres ramas paralelas
- **Parámetros**: Ninguno

#### Conexiones Salientes (3)
- Rama A: HTTP Criterios
- Rama B: HTTP Tablas
- Rama C: HTTP HU

---

### 2. **HTTP Criterios** (Rama A - Criterios Históricos)

#### Propósito
Obtener criterios históricos/ejemplos de Azure DevOps Wiki para crear contexto de entrenamiento para Gemini.

#### Configuración
```json
{
  "id": "25a7da3c-a8ea-47a8-a9d3-2d53b4a76fc0",
  "name": "HTTP Criterios",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [-1584, 1616],
  "parameters": {
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutorias/_apis/wiki/wikis/PoliTutorias.wiki/pages/1060?includeContent=true&api-version=7.1",
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

#### Parámetros de Solicitud
| Parámetro | Valor |
|:---|:---|
| **Método HTTP** | GET |
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutorias/_apis/wiki/wikis/PoliTutorias.wiki/pages/1060?includeContent=true&api-version=7.1` |
| **Autenticación** | HTTP Basic Auth |
| **Page ID** | 1060 (Criterios históricos) |
| **Propósito** | Obtener ejemplos de criterios previos exitosos |

#### Datos Extraídos
- **Contenido**: Criterios de aceptación históricos formateados con estructura: HU, Título, Criterios

---

### 3. **Code in Criterios** (Parser de Criterios Históricos)

#### Propósito
Parsear criterios históricos y extraer: ID HU, Título, Tipo, Contenido de criterios. Estos servirán como ejemplos para el entrenamiento de Gemini.

#### Ubicación en Flujo
Entrada: `items[0].json.content` (de HTTP Criterios)

#### Código Principal

```javascript
// Validación de seguridad
if (!items[0].json.content) {
  return [{ json: { error: "No hay contenido. Verifica la URL de la API." } }];
}

const content = items[0].json.content;

// ESTRATEGIA: BLOQUES MAESTROS
// Estructura: "### Nro. HU03 - Título: Publicar oferta"
const masterRegex = /(?:###|##)\s*Nro\.\s*HU(\d+)\s*-\s*Título:\s*([^\n\r]+)([\s\S]*?)(?=(?:###|##)\s*Nro\.\s*HU|$)/gi;

let match;
const resultados = [];

while ((match = masterRegex.exec(content)) !== null) {
  const huNumero = match[1];
  const huTitulo = match[2].trim();
  const huCuerpo = match[3];

  // BUSCAR CRITERIOS dentro del cuerpo de ESTA HU
  const criteriaRegex = /(?:#+\s*)?Criterios de aceptación\s*HU\d+([\s\S]*?)(?=(?:#+\s*)?Tareas|Nro\.\s*HU|(?:#+\s*)?Resumen|$)/i;
  
  const criteriaMatch = criteriaRegex.exec(huCuerpo);

  if (criteriaMatch) {
    let tablaRaw = criteriaMatch[1];

    // LIMPIEZA DE TEXTO
    let textoLimpio = tablaRaw
      .replace(/Tareas\s*HU\d+/i, '')
      .replace(/Resumen\s*de\s*Story\s*Points/i, '')
      .replace(/\|\?\s*:?-+:?\s*\|\s*:?-+:?\s*\|?/g, '') 
      .replace(/\*\*/g, '')
      .replace(/<br\s*\/?>/gi, ' ')
      .replace(/\|/g, ' - ')
      .replace(/Escenario\s*-\s*Descripción/gi, '')
      .replace(/\s+/g, ' ')
      .trim();

    if (textoLimpio.length > 5) {
      resultados.push({
        json: {
          id: `HU-${huNumero}`,
          titulo: huTitulo,
          tipo: 'Entrenamiento',
          contenido_criterios: textoLimpio    
        }
      });
    }
  }
}

if (resultados.length === 0) {
    return [{ json: { warning: "No se encontraron HUs con el formato esperado." } }];
}

return resultados;
```

#### Salida Generada

```json
[
  {
    "json": {
      "id": "HU-1",
      "titulo": "Solicitar Tutoría",
      "tipo": "Entrenamiento",
      "contenido_criterios": "Escenario 1: Estudiante sin solicitudes previas... Escenario 2: Estudiante con solicitud expirada..."
    }
  },
  {
    "json": {
      "id": "HU-2",
      "titulo": "Cancelar Solicitud",
      "tipo": "Entrenamiento",
      "contenido_criterios": "..."
    }
  }
]
```

#### Transformaciones Realizadas
- **Búsqueda de bloques**: Regex para localizar encabezados "Nro. HU-XXX"
- **Extracción de criterios**: Identifica sección "Criterios de aceptación"
- **Limpieza**: Elimina formatos Markdown y HTML
- **Validación**: Filtra bloques vacíos o inválidos

---

### 4. **Code in JavaScript** (Formatea Ejemplos de Entrenamiento)

#### Propósito
Convertir criterios históricos en bloques de contexto para inyectar en el prompt de Gemini como ejemplos maestros.

#### Entrada
```json
[
  {
    "json": {
      "id": "HU-1",
      "titulo": "Solicitar Tutoría",
      "contenido_criterios": "..."
    }
  }
]
```

#### Código

```javascript
if (items.length === 0) {
    return [{ json: { contexto_entrenamiento: "No hay ejemplos históricos." } }];
}

const listaEjemplos = items.map(item => {
    const datos = item.json;
    
    return `### EJEMPLO DE REFERENCIA (${datos.id})
TÍTULO: ${datos.titulo}
--------------------------------------------------
CRITERIOS:
${datos.contenido_criterios}`;
});

// Separador fuerte entre bloques
const separador = '\n\n\n--------------------------------------------------------------------------------\n\n\n';

const textoFinal = listaEjemplos.join(separador);

return [{
    json: {
        contexto_entrenamiento: textoFinal
    }
}];
```

#### Salida Generada

```
### EJEMPLO DE REFERENCIA (HU-1)
TÍTULO: Solicitar Tutoría
--------------------------------------------------
CRITERIOS:
Escenario 1: Estudiante sin solicitudes previas...
Escenario 2: Estudiante con solicitud expirada...


--------------------------------------------------------------------------------


### EJEMPLO DE REFERENCIA (HU-2)
TÍTULO: Cancelar Solicitud
--------------------------------------------------
CRITERIOS:
...
```

#### Propósito en Flujo
Proporciona **contexto de entrenamiento** a Gemini con ejemplos de criterios bien formados para que replique el estilo y estructura.

---

### 5. **HTTP Tablas** (Rama B - Matrices de Decisión)

#### Propósito
Obtener las matrices de decisión generadas previamente (del flujo TablasAC) que servirán como lógica base para los criterios.

#### Configuración
```json
{
  "id": "487d9138-a67a-4c2e-85fb-0e7d81adfbfc",
  "name": "HTTP Tablas",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [-1584, 736],
  "parameters": {
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1494?includeContent=true&api-version=7.1",
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

#### Parámetros de Solicitud
| Parámetro | Valor |
|:---|:---|
| **Método HTTP** | GET |
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1494?includeContent=true&api-version=7.1` |
| **Page ID** | 1494 (Matrices de decisión) |
| **Propósito** | Obtener tablas de verdad generadas |

#### Datos Esperados
```json
{
  "content": "### Nro. HU-1 - Título: Solicitar Tutoría\n#### Matriz de Decisión HU-1\n| ID | Condición | R1 | R2 |...\n### GLOSARIO DE ACCIONES..."
}
```

---

### 6. **Code in JavaScript5** (Extrae Matrices de Decisión)

#### Propósito
Parsear matrices de decisión y glosarios de la página de tablas para extraer la lógica y las acciones.

#### Código Principal

```javascript
// Validación
if (!items[0].json.content) {
  return [{ json: { error: "El nodo HTTP no trajo contenido." } }];
}

const content = items[0].json.content;

// Dividir por cabeceras HU
const splitRegex = /(?:\n|^)(?=(?:#{1,6}\s*|[\*_]*)\s*(?:Nro\.?)?s*HU\s*-?\s*\d+)/i;
const bloques = content.split(splitRegex);
const historias = [];

bloques.forEach(bloque => {
  const texto = bloque.trim();

  // Extraer ID y TÍTULO
  const headerMatch = texto.match(/HU\s*-?\s*(\d+)[\s\S]*?Título\s*:?\s*([^\n\r]+)/i);

  if (headerMatch) {
    const idNum = headerMatch[1];
    const tituloLimpio = headerMatch[2].replace(/[\*_]/g, '').trim();

    // Extraer DESCRIPCIÓN
    let descripcion = "Descripción no detectada";
    const descMatch = texto.match(/Descripción\s*:?\s*([\s\S]*?)(?=\s*####?\s*(?:PASO|Matriz))/i);
    
    if (descMatch) {
        descripcion = descMatch[1].trim();
    }

    // Extraer MATRICES (múltiples si hay varios PASOS)
    const regexMatriz = /(?:####?\s*(?:PASO|Matriz))[\s\S]*?(?=(?:###\s*GLOSARIO|$))/gi;
    let matricesExtraidas = [];
    let matchM;
    while ((matchM = regexMatriz.exec(texto)) !== null) {
        matricesExtraidas.push(matchM[0].trim());
    }
    let matriz = matricesExtraidas.length > 0 ? matricesExtraidas.join("\n\n") : "Matriz no detectada";

    // Extraer GLOSARIOS
    const regexGlosario = /(?:###\s*GLOSARIO)[\s\S]*?(?=(?:####?\s*(?:PASO|Matriz)|$))/gi;
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

#### Salida Esperada

```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "titulo": "Solicitar Tutoría",
      "descripcion": "COMO estudiante QUIERO solicitar una tutoría...",
      "tabla_decision_generada": "#### PASO 1\n| ID | Condición | R1 | R2 |...",
      "glosario_acciones": "### GLOSARIO DE ACCIONES\n* **A1:** Enviar solicitud..."
    }
  }
]
```

---

### 7. **HTTP HU** (Rama C - Historias de Usuario)

#### Propósito
Obtener las historias de usuario con descripción y referencias a frames/prototipos.

#### Configuración
```json
{
  "id": "636284ab-acda-4fb5-8457-cd2c68e3cb5d",
  "name": "HTTP HU",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [-1712, 1072],
  "parameters": {
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1490?includeContent=true&api-version=7.1",
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
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1490?includeContent=true&api-version=7.1` |
| **Page ID** | 1490 (Historias de usuario) |

---

### 8. **Code in JavaScript9** (Extrae Frames de HU)

#### Propósito
Parsear historias de usuario para extraer referencias a frames/prototipos.

#### Código

```javascript
const content = items[0].json.content;

if (!content) {
  return [{ json: { error: "El nodo HTTP no trajo contenido." } }];
}

// Dividir por cabeceras HU
const splitRegex = /(?:\n|^)(?=(?:#{1,6}\s*|[\*_]*)\s*(?:Nro\.?)?s*HU\s*-?\s*\d+)/i;
const bloques = content.split(splitRegex);
const output = [];

bloques.forEach(bloque => {
  const texto = bloque.trim();

  // Extraer ID
  const headerMatch = texto.match(/HU\s*-?\s*(\d+)/i);

  if (headerMatch) {
    const idNum = `HU-${headerMatch[1]}`;
    
    // Buscar sección de Frames
    const sectionFramesMatch = texto.match(/(?:Frame|Prototipo)[\s\S]*?(?=(?:Observaciones|Nota|###|$))/i);

    if (sectionFramesMatch) {
      const lineasFrames = sectionFramesMatch[0].split('\n');
      
      lineasFrames.forEach(linea => {
        // Detecta líneas con viñetas
        if (linea.match(/^\s*[-*+v]\.\?\s*/i)) {
          const nombreLimpio = linea.replace(/^\s*[-*+vV\.0-9]*\s*/, '').trim();
          
          if (nombreLimpio.length > 0 && nombreLimpio.toLowerCase() !== "empty") {
            // Crear item por cada frame
            output.push({
              json: {
                id_hu: idNum,
                nombre_frame: nombreLimpio,
                busqueda_drive: nombreLimpio 
              }
            });
          }
        }
      });
    }
  }
});

if (output.length === 0) {
    return [{ json: { warning: "No se detectaron frames." } }];
}

return output;
```

#### Salida
```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "nombre_frame": "Pantalla Solicitud Tutoría",
      "busqueda_drive": "Pantalla Solicitud Tutoría"
    }
  }
]
```

---

### 9. **Code in JavaScript6** (Limpia y Prepara Búsqueda)

#### Propósito
Validar y preparar los nombres de frames para la búsqueda en Google Drive.

#### Código

```javascript
const itemsProcesados = [];

for (const item of items) {
  const data = item.json;
  
  if (data.nombre_frame && data.nombre_frame.trim() !== "") {
    itemsProcesados.push({
      json: {
        id_hu: data.id_hu,
        nombre_imagen_buscar: data.nombre_frame.trim()
      }
    });
  }
}

if (itemsProcesados.length === 0) {
    return [{ json: { warning: "No se encontraron frames en la entrada." } }];
}

return itemsProcesados;
```

---

### 10. **Search files and folders** (Google Drive)

#### Propósito
Buscar archivos PNG en Google Drive con nombres que coincidan con los frames.

#### Configuración
```json
{
  "id": "74b19df8-51e7-469d-9385-cac379b9d720",
  "name": "Search files and folders",
  "type": "n8n-nodes-base.googleDrive",
  "typeVersion": 3,
  "parameters": {
    "resource": "fileFolder",
    "searchMethod": "query",
    "queryString": "=name = '{{ $json.nombre_imagen_buscar }}.png' and trashed = false",
    "returnAll": true,
    "filter": {
      "folderId": {
        "__rl": true,
        "value": "1t3gWETWX0yH6O34BAHkShNogIEADJe3d",
        "mode": "list",
        "cachedResultName": "SP3"
      }
    },
    "options": {}
  }
}
```

---

### 11-13. **Download file1**, **Code in JavaScript7**, **Code in JavaScript8**

Estos nodos funcionan idénticamente a los del flujo TablasAC:
- Descargan archivos de Drive
- Combinan metadatos con datos binarios
- Agrupan imágenes por HU

Ver documentación TablasAC para detalles completos.

---

### 14. **Merge1** (Sincronización de Ramas B y C)

#### Propósito
Combinar datos de matrices de decisión (rama B) con datos de HU + imágenes (rama C).

#### Configuración
```json
{
  "id": "841b3216-7a8c-4a11-adeb-8ab4122a3560",
  "name": "Merge1",
  "type": "n8n-nodes-base.merge",
  "typeVersion": 3.2,
  "position": [144, 880],
  "parameters": {
    "mode": "combine",
    "fieldsToMatchString": "=id_hu",
    "options": {}
  }
}
```

#### Parámetros Clave
| Parámetro | Valor |
|:---|:---|
| **Modo** | combine |
| **Campos a coincidir** | id_hu |

#### Comportamiento
- **Entrada 0**: Items de Code in JavaScript5 (matrices + glosarios)
- **Entrada 1**: Items de Code in JavaScript8 (HU + imágenes)
- **Salida**: Items fusionados con ambos datasets

#### Salida Esperada
```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "titulo": "Solicitar Tutoría",
      "descripcion": "...",
      "tabla_decision_generada": "...",
      "glosario_acciones": "...",
      "frames_info": [{...}]
    },
    "binary": {"data_0": {...}}
  }
]
```

---

### 15. **Merge** (Fusión de Tres Ramas)

#### Propósito
Combinar todos los datos: contexto histórico + matrices + imágenes + HU.

#### Configuración
```json
{
  "id": "3aee4985-ace9-442d-bb3f-311d5a0e57b5",
  "name": "Merge",
  "type": "n8n-nodes-base.merge",
  "typeVersion": 3.2,
  "position": [704, 1024],
  "parameters": {
    "mode": "combine",
    "combineBy": "combineAll",
    "options": {}
  }
}
```

#### Entradas
- **[0]**: Merge1 (matrices + HU + imágenes)
- **[1]**: Code in JavaScript (contexto de entrenamiento)

#### Salida
```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "titulo": "...",
      "tabla_decision_generada": "...",
      "glosario_acciones": "...",
      "frames_info": [...]
    },
    "binary": {...}
  },
  {
    "json": {
      "contexto_entrenamiento": "### EJEMPLO DE REFERENCIA (HU-1)..."
    }
  }
]
```

---

### 16. **Analyze an image** (Google Gemini 2.5 Flash)

#### Propósito
Analizar imagen de prototipo + matriz de decisión + glosario + contexto histórico para generar **Criterios de Aceptación en formato BDD**.

#### Configuración Extendida

```json
{
  "id": "add4d752-711b-4aab-99dc-66e84471ffaf",
  "name": "Analyze an image",
  "type": "@n8n/n8n-nodes-langchain.googleGemini",
  "typeVersion": 1,
  "parameters": {
    "resource": "image",
    "operation": "analyze",
    "modelId": "models/gemini-2.5-flash",
    "text": "{{ PROMPT EXTENSO }}",
    "inputType": "binary",
    "binaryPropertyName": "data_0",
    "options": {}
  }
}
```

#### Prompt Principal (Secciones)

**SECCIÓN 1: CONTEXTO DE MAESTRÍA**
```
SECCIÓN 1: MIS EJEMPLOS MAESTROS (GUÍA DE ESTILO OBLIGATORIA)
Úsalos como GUÍA DE ESTILO.

{{ $json.contexto_entrenamiento }}
```

**SECCIÓN 2: REGLAS DE TRADUCCIÓN**

1. **Construcción del "Dado"**:
   - Identifica el actor de la DESCRIPCIÓN
   - Flujo normal: "Dado que el [Actor] se encuentra en la interfaz de [Título]..."
   - Lista vacía: "Dado que el [Actor] ingresa a [Título] pero NO tiene registros previos..."
   - Edición: "Dado que el [Actor] ya tiene un registro previo..."

2. **Lógica del "Cuando"**:
   - Lee condiciones (C) de columnas de MATRIZ
   - **CONSULTA FRAMES**: Usa nombres exactos de Info Visual
   - Para "S": `[Verbo] en [Nombre Exacto Visual]: [Valor Real/Ejemplo]`
   - Para "N": `deja el campo [Nombre Visual] vacío`

3. **Lógica del "Entonces"**:
   - Identifica Acción (A) de GLOSARIO
   - Limpia referencias internas (elimina "(según Info Visual)", etc.)
   - Verifica mensajes/textos exactos de Info Visual

4. **Formato HTML**:
   - Usa `<br>` para separar Dado/Cuando/Entonces
   - NO uses Enter dentro de celdas

**SECCIÓN 3: ENTRADA DE DATOS**
```
ID: {{ $json.id_hu }}
Título: {{ $json.titulo }}
Descripción: {{ $json.descripcion }}

MATRIZ DE DECISIÓN:
{{ $json.tabla_decision_generada }}

GLOSARIO DE ACCIONES:
{{ $json.glosario_acciones }}

INFO VISUAL (FRAMES):
{{ JSON.stringify($json.frames_info) }}
```

**SECCIÓN 4: SALIDA ESPERADA**
```markdown
### Nro. {{ $json.id_hu }} - Título: {{ $json.titulo }}

#### Criterios de aceptación {{ $json.id_hu }}

| **Escenario** | **Descripción** |
| :--- | :--- |
| **[Nombre Corto R1]** | **Dado** [Contexto]... <br> **cuando** [Detalle Visual]... <br> **entonces** [Resultado]... |
| **[Nombre Corto R2]** | ... |
```

#### Diferencia Clave con TablasAC

| Aspecto | TablasAC | CriteriosDT |
|:---|:---|:---|
| **Entrada de Prompt** | Solo imagen + observaciones | Imagen + Matriz + Glosario + Contexto |
| **Salida** | Matriz de decisión | Criterios BDD formato tabla |
| **Enfoque** | Validación visual | Traducción + enriquecimiento |
| **Ejemplos** | Ninguno | Ejemplos maestros históricos |

#### Respuesta Esperada

```markdown
### Nro. HU-1 - Título: Solicitar Tutoría

#### Criterios de aceptación HU-1

| **Escenario** | **Descripción** |
| :--- | :--- |
| **Solicitud exitosa con todos los campos completos** | **Dado** que el estudiante se encuentra en la pantalla "Solicitar Tutoría"... <br> **cuando** ingresa en el campo "Tutor": "Juan Pérez", selecciona en "Carrera": "Ingeniería de Software", y hace clic en el botón "Enviar"... <br> **entonces** el sistema valida los datos según regla SOL-02, redirige a la pantalla "Mis Solicitudes", y muestra el mensaje "Solicitud enviada correctamente" en color verde. |

| **Solicitud rechazada por campo vacío** | **Dado** que el estudiante se encuentra en la pantalla "Solicitar Tutoría"... <br> **cuando** deja el campo "Tutor" vacío y hace clic en "Enviar"... <br> **entonces** permanece en la pantalla de solicitud y muestra el mensaje "El campo 'Tutor' es obligatorio" en color rojo bajo el campo. |
```

---

### 17. **Code in JavaScript1** (Formateo Final para Wiki)

#### Propósito
Compilar respuestas de Gemini en un documento Markdown completo listo para publicar.

#### Código

```javascript
const listaEscenarios = items.map(item => {
  const json = item.json;

  // CASO A: Estructura Gemini estándar
  if (json.content && json.content.parts && json.content.parts[0] && json.content.parts[0].text) {
    return json.content.parts[0].text;
  }

  // CASO B: Estructura simple
  return json.text || json.output || json.content;
})
.filter(texto => texto)
.map(texto => {
  return String(texto).trim(); 
});

// Unir con separador
const contenidoUnido = listaEscenarios.join('\n\n---\n\n');

// Crear documento final
const fecha = new Date().toLocaleDateString('es-ES');
const documentoFinal = `# Reporte de Escenarios Generados (S1)\n> Generado el: ${fecha}\n\n${contenidoUnido}`;

return [{
  json: {
    contenido_wiki: documentoFinal,
    page_path: "CriteriosS1", 
  }
}];
```

#### Salida
```json
{
  "json": {
    "contenido_wiki": "# Reporte de Escenarios Generados (S1)\n> Generado el: 6/6/2026\n\n### Nro. HU-1...",
    "page_path": "CriteriosS1"
  }
}
```

---

### 18. **HTTP Azure enviar** (Publicación Final)

Idéntico al flujo TablasAC. Envía el documento a Azure DevOps Wiki mediante PUT.

---

## Análisis de Propiedades y Configuraciones

### URLs de Azure Utilizadas

| Nodo | Endpoint | Page ID | Propósito |
|:---|:---|:---:|:---|
| HTTP Criterios | PoliTutorias.wiki | 1060 | Criterios históricos |
| HTTP Tablas | PoliTutoriasAI.wiki | 1494 | Matrices de decisión |
| HTTP HU | PoliTutoriasAI.wiki | 1490 | Historias de usuario |
| HTTP Azure enviar | PoliTutoriasAI.wiki | - (path based) | Publicación final |

### Credenciales Utilizadas

#### 1. Azure DevOps (HTTP Basic Auth)
- **ID**: J1QlSdi95FPXq84s
- **Nombre**: "Azure"
- **Nodos**: HTTP Criterios, HTTP Tablas, HTTP HU, HTTP Azure enviar

#### 2. Google Drive OAuth2
- **ID**: KRo0vEZn7fvpO3D1
- **Nombre**: "Google Drive account"
- **Nodos**: Search files and folders, Download file1

#### 3. Google Gemini API
- **ID**: i6AlcEi2Rvcd9bIu
- **Nombre**: "Google Gemini(PaLM) Api account 2"
- **Nodos**: Analyze an image
- **Modelo**: gemini-2.5-flash

---

## Flujo de Datos

### Ruta Completa de Ejecución

```
TRIGGER
  ├─ [Rama A] HTTP Criterios
  │    ↓
  │    Code in Criterios
  │    ↓
  │    Code in JavaScript
  │    ↓
  │    Contexto Histórico → Merge[1]
  │
  ├─ [Rama B] HTTP Tablas
  │    ↓
  │    Code in JavaScript5
  │    ↓
  │    Matriz + Glosario → Merge1[0]
  │
  └─ [Rama C] HTTP HU
       ↓
       Code in JavaScript9
       ↓
       Code in JavaScript6
       ↓
       Search Drive → Download
       ↓
       Code in JavaScript7
       ↓
       Code in JavaScript8
       ↓
       HU + Imágenes → Merge1[1]

SINCRONIZACIÓN
  Merge1[0,1] → Fusión (Matriz + HU + Imágenes)
  ↓
  Merge[0] ← Contexto Histórico [Rama A]
  ↓
  [Análisis Gemini: Imagen + Matriz + Glosario + Contexto]
  ↓
  [Generación de Criterios BDD]
  ↓
  [Formateo de Documento]
  ↓
  [Publicación en Azure]
  ↓
  FIN
```

### Tiempos de Ejecución Estimados

| Fase | Tiempo Estimado |
|:---|:---|
| Descarga de datos (3 HTTP) | 2-3s (paralela) |
| Parsing y transformación | 1-2s |
| Búsqueda y descarga de Drive | 3-5s |
| Análisis Gemini | 10-15s |
| Publicación Azure | 2-3s |
| **TOTAL** | **15-25 segundos** |

---

## Transformaciones de Datos

### T1: Criterios Markdown → Contexto Histórico

**Entrada**: Criterios en Markdown sin procesar
**Proceso**: Parse + Limpieza en Code in Criterios
**Salida**: Array de ejemplos con ID, título, criterios limpios

### T2: Matrices Markdown → Objetos Estructurados

**Entrada**: Matrices + Glosarios en Markdown
**Proceso**: Regex en Code in JavaScript5
**Salida**: 
```json
{
  "tabla_decision_generada": "#### PASO 1...",
  "glosario_acciones": "### GLOSARIO..."
}
```

### T3: Fusión Multinivel

**Entrada**: Tres streams (histórico, matrices, HU+imágenes)
**Proceso**: Merge1 (por id_hu) + Merge (combineAll)
**Salida**: Item consolidado con todos los datos

### T4: Traducción BDD (Núcleo del Valor)

**Entrada**:
- Matriz de decisión (lógica)
- Glosario (textos de acciones)
- Imágenes (validación visual)
- Contexto histórico (ejemplos de estilo)

**Proceso**: Gemini analiza y traduce
**Salida**:
```markdown
| Escenario | Descripción |
|:---|:---|
| R1 | **Dado**... <br> **cuando**... <br> **entonces**... |
```

---

## Reglas de Negocio Inyectadas

El prompt de Gemini incluye 14 reglas de negocio:

- **USER-01**: Usuarios con rol dual (Estudiante/Tutor)
- **SOL-01 a SOL-08**: Políticas de solicitud de tutoría (anticipación mínima, cancelación, etc.)
- **CAL-01 a CAL-03**: Lógica de calendario y disponibilidad
- **FAC-01**: Asociación tutor-facultad
- **OFERTA-01**: Bloqueo dinámico de solicitudes

Estas reglas se integran en los criterios generados para asegurar validez de negocio.

---

## Salida Final

### Estructura del Documento Publicado

```markdown
# Reporte de Escenarios Generados (S1)
> Generado el: 6/6/2026

---

### Nro. HU-1 - Título: Solicitar Tutoría

#### Criterios de aceptación HU-1

| **Escenario** | **Descripción** |
| :--- | :--- |
| **R1: Solicitud exitosa** | **Dado** que el estudiante se encuentra en la pantalla "Solicitar Tutoría"... <br> **cuando** ingresa "Juan Pérez" en "Tutor", selecciona "Ingeniería de Software" en "Carrera"... <br> **entonces** el sistema valida según SOL-02, redirige a "Mis Solicitudes", y muestra "Solicitud enviada correctamente" en verde. |
| **R2: Campo tutor vacío** | **Dado** que el estudiante está en la pantalla de solicitud... <br> **cuando** deja "Tutor" vacío y hace clic "Enviar"... <br> **entonces** permanece en la pantalla y muestra error "Campo 'Tutor' obligatorio" en rojo. |
| **R3: Validación SOL-02** | **Dado** que faltan menos de 12 horas para la tutoría... <br> **cuando** intenta enviar la solicitud... <br> **entonces** el sistema rechaza y muestra "Debe haber mínimo 12 horas de anticipación". |

---

### Nro. HU-2 - Título: Cancelar Solicitud

[Estructura similar...]
```

### Publicación en Azure

**Ubicación**: `/Testing(IA)/Sprint3/CasosS3`

**Método**: PUT

**Payload**:
```json
{
  "content": "# Reporte de Escenarios...\n\n### Nro. HU-1..."
}
```

---

## Ventajas Arquitectónicas del CriteriosDT

### Frente a TablasAC
1. **Contexto Histórico**: Aprende de criterios previos
2. **Traducción Refinada**: Convierte lógica en lenguaje natural BDD
3. **Validación Multinivel**: Matriz + Imagen + Glosario + Histórico
4. **Salida Directa**: Criterios finales (no requiere paso adicional)

### Frente a Procesos Manuales
1. **100% Automatizado**: Sin intervención humana
2. **Consistencia**: Sigue patrones históricos
3. **Velocidad**: 15-25 segundos por ejecución
4. **Trazabilidad**: Auditoría completa en Azure

---

## Conclusión

El flujo **CriteriosDT** es la culminación de un pipeline automatizado sofisticado que:

1. **Recopila** múltiples fuentes de verdad (histórico, lógica, visual)
2. **Orquesta** ejecución paralela de tres ramas independientes
3. **Traduce** lógica matemática en criterios BDD legibles
4. **Enriquece** con contexto histórico y reglas de negocio
5. **Publica** documentación consistente y validada

**Propósito Final**: Generar Criterios de Aceptación profesionales y validados que sirvan como especificación ejecutable para pruebas de software (QA), aprovechando IA para traducción, validación visual, y aseguración de consistencia.

---

**Documento Generado**: 6 de junio de 2026
**Versión del Flujo**: 0w8DMTrztgb9vgpw (CriteriosDT)
**Modelo IA Utilizado**: Google Gemini 2.5 Flash
