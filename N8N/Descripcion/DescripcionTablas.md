# Documentación Completa del Flujo n8n: "TablasAC"

## Introducción General

### Propósito del Flujo
El flujo **TablasAC** es un sistema de orquestación automatizado diseñado para:
- Extraer información de historias de usuario (HU) desde Azure DevOps Wiki
- Buscar y descargar archivos de prototipo/frames desde Google Drive
- Analizar imágenes con IA (Google Gemini 2.5 Flash)
- Generar matrices de decisión (tablas de verdad) basadas en criterios de aceptación
- Publicar los criterios de aceptación generados en Azure DevOps Wiki

### Contexto de Uso
Este flujo forma parte de un sistema más grande de generación automatizada de criterios de aceptación para pruebas de software (QA). 

### Stack Tecnológico
- **Orquestador**: n8n (Sistema de automatización de flujos)
- **Fuentes de Datos**: 
  - Azure DevOps Wiki (API REST)
  - Google Drive (API de Drive)
- **IA**: Google Gemini 2.5 Flash (análisis de imágenes)
- **Tipo de Integración**: REST APIs, webhooks, procesamiento de imágenes

---

## Arquitectura General del Flujo

### Vista de Alto Nivel

```
ENTRADA
  ↓
[Trigger Manual] 
  ↓
  ├─→ [Obtener HUs de Azure] ──→ [Parsear HUs] ──→ [Expandir por Frames] 
  │                                                       ↓
  │                                              [Buscar en Google Drive]
  │                                                       ↓
  │                                              [Descargar Archivos]
  │                                                       ↓
  │                                              [Combinar Datos]
  │                                                       ↓
  │                                              [Agrupar por HU]
  │                                                       ↓
  └─→ [Obtener Mapa de Navegación] ──→ [Procesar Mapa] ─┐
                                                          ↓
                                              [Fusionar Datos + Mapa]
                                                          ↓
                                         [Analizar Imagen con Gemini]
                                                          ↓
                                           [Formatear Documento Final]
                                                          ↓
                                       [Enviar a Azure DevOps Wiki]
                                                          ↓
                                                       SALIDA
```

### Estructura de Ejecución
- **Modo de Ejecución**: Trigger manual
- **Número de Nodos**: 13 nodos activos
- **Cantidad de Conexiones**: 13 conexiones principales
- **Bifurcaciones**: 2 (en el trigger inicial y en el merge)

---

## Diagrama de Conexiones

### Tabla de Rutas de Conexión

| Nodo Origen | Tipo de Conexión | Nodo Destino | Orden Ejecución |
|:---|:---:|:---|:---:|
| When clicking 'Execute workflow' | main[0] | HTTP HU1 | 1 |
| When clicking 'Execute workflow' | main[0] | HTTP Mapa | 1 |
| HTTP HU1 | main[0] | Code in JavaScript5 | 2 |
| Code in JavaScript5 | main[0] | Code in JavaScript6 | 3 |
| Code in JavaScript6 | main[0] | Search files and folders | 4 |
| Search files and folders | main[0] | Download file1 | 5 |
| Download file1 | main[0] | Code in JavaScript7 | 6 |
| Code in JavaScript7 | main[0] | Code in JavaScript8 | 7 |
| Code in JavaScript8 | main[0] | Merge1 (entrada 0) | 8 |
| HTTP Mapa | main[0] | Code in Criterios1 | 2 |
| Code in Criterios1 | main[0] | Merge1 (entrada 1) | 8 |
| Merge1 | main[0] | Analyze an image | 9 |
| Analyze an image | main[0] | Code in JavaScript1 | 10 |
| Code in JavaScript1 | main[0] | HTTP Azure enviar | 11 |

### Ejecución Paralela
- **Línea 1**: Trigger → HTTP HU1 → Parseo → Búsqueda de archivos → Descarga → Combinación
- **Línea 2**: Trigger → HTTP Mapa → Procesamiento de mapa
- Ambas líneas convergen en **Merge1** (sincronización)

---

## Descripción Detallada de Nodos

### 1. **When clicking 'Execute workflow'** (Trigger Manual)

#### Propósito
Punto de entrada manual del flujo. Permite ejecutar el flujo bajo demanda desde la interfaz de n8n.

#### Configuración
```json
{
  "id": "91de7945-94d7-47bd-a474-6ce9414980a0",
  "name": "When clicking 'Execute workflow'",
  "type": "n8n-nodes-base.manualTrigger",
  "typeVersion": 1,
  "position": [-1040, 32],
  "parameters": {}
}
```

#### Salida
- **Tipo**: Objeto vacío `{}`
- **Propósito**: Iniciar la ejecución del flujo
- **Parámetros de Entrada**: Ninguno (trigger manual)

#### Conexiones Salientes
- Rama 1: HTTP HU1 (obtener historias de usuario)
- Rama 2: HTTP Mapa (obtener mapa de navegación)

---

### 2. **HTTP HU1** (Nodo HTTP - Azure DevOps)

#### Propósito
Realizar una solicitud GET a Azure DevOps Wiki para obtener el contenido de la página con historias de usuario.

#### Configuración
```json
{
  "id": "fd46a088-765b-452d-ac35-488b79cd8552",
  "name": "HTTP HU1",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [-432, -48],
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

#### Parámetros de Solicitud
| Parámetro | Valor |
|:---|:---|
| **Método HTTP** | GET |
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1490?includeContent=true&api-version=7.1` |
| **Autenticación** | HTTP Basic Auth (credencial: "Azure") |
| **Page ID** | 1490 |
| **Query Parameter** | `includeContent=true` (incluir contenido de la página) |
| **API Version** | 7.1 |

#### Respuesta Esperada
```json
{
  "id": 1490,
  "path": "/Historias de Usuario",
  "content": "# HU-1 - Título: Login...\n# HU-2 - Título: Registro...",
  "url": "...",
  "createdBy": "...",
  "createdDate": "...",
  "editedBy": "...",
  "editedDate": "..."
}
```

#### Datos Extraídos
- **Contenido Principal**: Campo `content` que contiene todas las historias de usuario en formato Markdown

---

### 3. **HTTP Mapa** (Nodo HTTP - Mapa de Navegación)

#### Propósito
Obtener el documento de mapeo de navegación (flujo de pantallas) desde Azure DevOps Wiki.

#### Configuración
```json
{
  "id": "9b325b4f-5c07-4f58-a6eb-17394f205092",
  "name": "HTTP Mapa",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [-416, 288],
  "parameters": {
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1422?includeContent=true&api-version=7.1",
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
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages/1422?includeContent=true&api-version=7.1` |
| **Autenticación** | HTTP Basic Auth |
| **Page ID** | 1422 |
| **Propósito** | Obtener contexto de navegación entre pantallas |

#### Datos Extraídos
- **Contenido**: Descripción del flujo de navegación con nodos, pantallas y transiciones

---

### 4. **Code in JavaScript5** (Parseo de Historias de Usuario)

#### Propósito
Parsear el contenido markdown de historias de usuario y extraer: ID, título, descripción, observaciones y frames/prototipos.

#### Ubicación en Flujo
Entrada: `items[0].json.content` (de HTTP HU1)

#### Código Principal

```javascript
// 1. Obtenemos el contenido
const content = items[0].json.content;

if (!content) {
  return [{ json: { error: "El nodo HTTP no trajo contenido." } }];
}

// 2. ESTRATEGIA FLEXIBLE: DIVIDIR POR CABECERAS DE HU
const splitRegex = /(?:\n|^)(?=(?:#{1,6}\s*|[\*_]*)\s*(?:Nro\.?)?s*HU\s*-?\s*\d+)/i;

const bloques = content.split(splitRegex);
const historias = [];

bloques.forEach(bloque => {
  const texto = bloque.trim();

  // A. INTENTAR EXTRAER EL ID Y TÍTULO
  const headerMatch = texto.match(/HU\s*-?\s*(\d+)[\s\S]*?Título\s*:?\s*([^\n\r]+)/i);

  if (headerMatch) {
    const idNum = headerMatch[1];
    const tituloLimpio = headerMatch[2].replace(/[\*_]/g, '').trim();

    // B. BUSCAR LA DESCRIPCIÓN (narrativa como/quiero/para)
    let descripcion = "Descripción no detectada";
    const narrativaMatch = texto.match(/(COMO\s+[\s\S]+?QUIERO\s+[\s\S]+?PARA\s+[\s\S]+?)(?=\.|\\||\n|$)/i);
    
    if (narrativaMatch) {
       descripcion = narrativaMatch[1].replace(/\|/g, '').trim(); 
    }

    // C. EXTRAER FRAMES
    const frames = [];
    const sectionFramesMatch = texto.match(/(?:Frame|Prototipo)[\s\S]*?(?=(?:Observaciones|Nota|###|$))/i);

    if (sectionFramesMatch) {
      const lineasFrames = sectionFramesMatch[0].split('\n');
      lineasFrames.forEach(linea => {
        if (linea.match(/^\s*[-*+v]\.\?\s*/i)) {
             const nombreLimpio = linea.replace(/^\s*[-*+vV\.0-9]*\s*/, '').trim();
             if (nombreLimpio.length > 0) {
                 frames.push(nombreLimpio);
             }
        }
      });
    }

    // D. OBSERVACIONES
    let observaciones = "Ninguna";
    const obsMatch = texto.match(/(?:Observaciones|Nota)[\s\S]*?:([\s\S]*)/i);
    if (obsMatch) {
      observaciones = obsMatch[1].trim();
    }

    historias.push({
      json: {
        id: `HU-${idNum}`,
        titulo: tituloLimpio,
        descripcion: descripcion,
        observaciones: observaciones,
        frames: frames
      }
    });
  }
});

return historias;
```

#### Salida Generada

```json
[
  {
    "json": {
      "id": "HU-1",
      "titulo": "Login de Usuario",
      "descripcion": "COMO usuario registrado QUIERO ingresar a mi cuenta PARA acceder al dashboard",
      "observaciones": "Incluir validación de email y contraseña",
      "frames": ["Pantalla Login", "Pantalla Dashboard"]
    }
  }
]
```

#### Transformaciones Realizadas
- **División**: Separa bloques por expresión regular que busca encabezados "HU-XXX"
- **Extracción de ID**: Regex para obtener número de HU
- **Extracción de Título**: Busca después de palabra "Título:"
- **Extracción de Descripción**: Busca narrativa Como/Quiero/Para
- **Extracción de Frames**: Identifica items de lista bajo secciones de frames
- **Validación**: Filtra frames vacíos o inválidos

---

### 5. **Code in JavaScript6** (Expansión por Frames)

#### Propósito
Convertir cada HU con múltiples frames en múltiples items, uno por frame. Esto permite buscar y descargar una imagen por cada frame.

#### Entrada
```json
[
  {
    "json": {
      "id": "HU-1",
      "titulo": "Login",
      "descripcion": "...",
      "observaciones": "...",
      "frames": ["Pantalla Login", "Pantalla Dashboard"]
    }
  }
]
```

#### Código

```javascript
const itemsProcesados = [];

for (const item of items) {
  const json = item.json;
  
  // Filtramos para asegurarnos de que solo pasen textos sin estar vacíos
  const frames = (json.frames || []).filter(f => f && f.trim() !== "");

  if (frames.length > 0) {
    frames.forEach(frameNombre => {
      itemsProcesados.push({
        json: {
          id_hu: json.id,
          titulo_hu: json.titulo,
          descripcion: json.descripcion,
          observaciones: json.observaciones,
          nombre_imagen_buscar: frameNombre // Nombre del frame
        }
      });
    });
  } else {
    itemsProcesados.push({
      json: {
        id_hu: json.id,
        titulo_hu: json.titulo,
        descripcion: json.descripcion,
        observaciones: json.observaciones,
        nombre_imagen_buscar: "Sin Frames"
      }
    });
  }
}

return itemsProcesados;
```

#### Salida Generada

```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "titulo_hu": "Login",
      "descripcion": "...",
      "observaciones": "...",
      "nombre_imagen_buscar": "Pantalla Login"
    }
  },
  {
    "json": {
      "id_hu": "HU-1",
      "titulo_hu": "Login",
      "descripcion": "...",
      "observaciones": "...",
      "nombre_imagen_buscar": "Pantalla Dashboard"
    }
  }
]
```

#### Impacto
- **Entrada**: 1 HU con 2 frames
- **Salida**: 2 items (uno por frame)
- **Beneficio**: Permite búsqueda individual de archivos en Google Drive

---

### 6. **Search files and folders** (Búsqueda en Google Drive)

#### Propósito
Buscar archivos PNG en Google Drive que coincidan con el nombre del frame.

#### Configuración
```json
{
  "id": "6a920068-e11b-47eb-bbc1-e4a6f91baf5d",
  "name": "Search files and folders",
  "type": "n8n-nodes-base.googleDrive",
  "typeVersion": 3,
  "position": [240, -48],
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
        "cachedResultName": "SP3",
        "cachedResultUrl": "https://drive.google.com/drive/folders/1t3gWETWX0yH6O34BAHkShNogIEADJe3d"
      }
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

#### Parámetros de Búsqueda
| Parámetro | Valor |
|:---|:---|
| **Recurso** | Carpeta/Archivo (fileFolder) |
| **Método de Búsqueda** | Query (consulta avanzada) |
| **Query String** | `name = '{{ $json.nombre_imagen_buscar }}.png' and trashed = false` |
| **Carpeta Target** | ID: `1t3gWETWX0yH6O34BAHkShNogIEADJe3d` (SP3) |
| **Return All** | true (retorna todos los resultados) |
| **Autenticación** | OAuth2 de Google Drive |

#### Lógica de Búsqueda
- **Patrón**: Busca archivos cuyo nombre sea exactamente `{nombre_imagen_buscar}.png`
- **Scope**: Solo dentro de carpeta SP3 específica
- **Filtro**: Excluye archivos en papelera

#### Respuesta Esperada
```json
[
  {
    "json": {
      "kind": "drive#file",
      "id": "1a2b3c4d5e6f7g8h9i0j",
      "name": "Pantalla Login.png",
      "mimeType": "image/png",
      "webViewLink": "https://drive.google.com/file/d/...",
      ...
    }
  }
]
```

---

### 7. **Download file1** (Descargar Archivo)

#### Propósito
Descargar el archivo PNG encontrado desde Google Drive como contenido binario.

#### Configuración
```json
{
  "id": "6f7c327e-db0e-4c7d-8e1f-8cf5a0040701",
  "name": "Download file1",
  "type": "n8n-nodes-base.googleDrive",
  "typeVersion": 3,
  "position": [432, -48],
  "parameters": {
    "operation": "download",
    "fileId": {
      "__rl": true,
      "value": "={{ $json.id }}",
      "mode": "id"
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
| **File ID** | `={{ $json.id }}` (dinámico del nodo anterior) |

#### Datos de Salida
```json
{
  "json": {
    "kind": "drive#file",
    "id": "1a2b3c4d5e6f7g8h9i0j",
    "name": "Pantalla Login.png",
    ...
  },
  "binary": {
    "data": {
      "data": [255, 216, 255, ...],  // Bytes de la imagen PNG
      "type": "image/png",
      "filename": "Pantalla Login.png"
    }
  }
}
```

---

### 8. **Code in JavaScript7** (Combinación de Datos con Metadatos)

#### Propósito
Combinar los datos de HU con la información de archivo descargado y los datos de imagen binarios.

#### Entrada
- **items[0-N]** (de Download file1): Items con metadatos del archivo y contenido binario

#### Código

```javascript
const datosTexto = $('Code in JavaScript6').all();

const itemsFinales = [];

// Mapa de agrupación por nombre de imagen
const mapaHUs = new Map();

datosTexto.forEach(item => {
  const data = item.json;
  if (data.nombre_imagen_buscar) {
    const nombreLimpio = data.nombre_imagen_buscar.trim();
    if (!mapaHUs.has(nombreLimpio)) {
      mapaHUs.set(nombreLimpio, []);
    }
    mapaHUs.get(nombreLimpio).push(data);
  }
});

// Control de duplicados
const imagenesProcesadas = new Set();

// Recorremos las imágenes descargadas
for (const itemImagen of items) {
  const driveData = itemImagen.json; 
  const binaryData = itemImagen.binary;

  const nombreArchivoSinExt = driveData.name.replace(/\.[^/.]+$/, "").trim();

  // Filtro anti-repetición
  if (imagenesProcesadas.has(nombreArchivoSinExt)) {
    continue; 
  }

  const listaHUsCoincidentes = mapaHUs.get(nombreArchivoSinExt);

  if (listaHUsCoincidentes && listaHUsCoincidentes.length > 0) {
    
    imagenesProcesadas.add(nombreArchivoSinExt);

    for (const huData of listaHUsCoincidentes) {
      itemsFinales.push({
        json: {
          id_hu: huData.id_hu,
          titulo: huData.titulo_hu,
          descripcion: huData.descripcion,
          observaciones: huData.observaciones,
          
          archivo_nombre_original: driveData.name,
          archivo_id: driveData.id
        },
        binary: binaryData
      });
    }
  }
}

return itemsFinales;
```

#### Salida
```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "titulo": "Login",
      "descripcion": "...",
      "observaciones": "...",
      "archivo_nombre_original": "Pantalla Login.png",
      "archivo_id": "1a2b3c4d5e6f7g8h9i0j"
    },
    "binary": {
      "data": { /* contenido binario PNG */ }
    }
  }
]
```

---

### 9. **Code in JavaScript8** (Agrupamiento por Historia de Usuario)

#### Propósito
Agrupar todos los items de un mismo HU (que pueden tener múltiples frames/imágenes) en un solo item con arrays de frames.

#### Entrada
Items individuales del nodo JavaScript7

#### Código

```javascript
const grupos = {};

for (const item of items) {
  const json = item.json;
  
  const binaryKey = Object.keys(item.binary)[0]; 
  const binary = item.binary[binaryKey];
  
  const idHu = json.id_hu;

  if (!grupos[idHu]) {
    grupos[idHu] = {
      json: {
        id_hu: idHu,
        titulo: json.titulo,
        descripcion: json.descripcion,
        observaciones: json.observaciones,
        frames_info: [] 
      },
      binary: {}
    };
  }

  grupos[idHu].json.frames_info.push({
    nombre: json.archivo_nombre_original, 
    archivo_id: json.archivo_id        
  });

  const indice = Object.keys(grupos[idHu].binary).length;
  
  grupos[idHu].binary[`data_${indice}`] = binary;
}

return Object.values(grupos);
```

#### Salida Esperada
```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "titulo": "Login",
      "descripcion": "...",
      "observaciones": "...",
      "frames_info": [
        {
          "nombre": "Pantalla Login.png",
          "archivo_id": "id123"
        },
        {
          "nombre": "Pantalla Dashboard.png",
          "archivo_id": "id456"
        }
      ]
    },
    "binary": {
      "data_0": { /* PNG binario 1 */ },
      "data_1": { /* PNG binario 2 */ }
    }
  }
]
```

---

### 10. **Code in Criterios1** (Procesamiento del Mapa)

#### Propósito
Procesar el contenido del mapa de navegación para extraer la información clave y consolidarla.

#### Entrada
```json
{
  "json": {
    "content": "... contenido del mapa ..."
  }
}
```

#### Código

```javascript
const content = items[0].json.content || "";

// Limpieza: Quitamos asteriscos y saltos HTML
const textoLimpio = content
  .replace(/\*\*/g, "") 
  .replace(/<br\s*\/?>/gi, "\n")
  .trim();

// Extracción de datos
const razonMatch = textoLimpio.match(/Razon:\s*([\s\S]*?)(?=(?:Total de Nodos|Pantallas|###|$))/i);
const nodosMatch = textoLimpio.match(/Total de Nodos:\s*(\d+)/i);
const pantallasMatch = textoLimpio.match(/Pantallas:\s*(\d+)/i);

const razon = razonMatch ? razonMatch[1].trim() : "No especificada";
const nodos = nodosMatch ? nodosMatch[1] : "N/A";
const pantallas = pantallasMatch ? pantallasMatch[1] : "N/A";

const bloqueFinal = `
=== CONTEXTO DEL MAPA DE NAVEGACIÓN ===
> Resumen de actualización:
- Motivo: ${razon}
- Métricas: ${nodos} nodos y ${pantallas} pantallas involucradas.

> Detalle Completo:
${textoLimpio}
`.trim();

return [{
  json: {
    mapa_consolidado: bloqueFinal 
  }
}];
```

#### Salida
```json
[
  {
    "json": {
      "mapa_consolidado": "=== CONTEXTO DEL MAPA DE NAVEGACIÓN ===\n> Resumen... "
    }
  }
]
```

---

### 11. **Merge1** (Fusión de Dos Streams)

#### Propósito
Combinar los datos de las dos ramas paralelas:
- **Entrada 0**: Datos de HUs agrupadas con imágenes (de JavaScript8)
- **Entrada 1**: Datos del mapa consolidado (de Criterios1)

#### Configuración
```json
{
  "id": "c98b5c0f-68cb-48cf-ad1f-51345d54f1d0",
  "name": "Merge1",
  "type": "n8n-nodes-base.merge",
  "typeVersion": 3.2,
  "position": [1504, 160],
  "parameters": {
    "mode": "combine",
    "combineBy": "combineAll",
    "options": {}
  }
}
```

#### Parámetros
| Parámetro | Valor |
|:---|:---|
| **Modo** | combine |
| **Combinar Por** | combineAll |

#### Comportamiento
- **Entrada 0** (index 0): Arrays de HUs con imágenes
- **Entrada 1** (index 1): Objeto con mapa consolidado
- **Salida**: Todos los items combinados (múltiples items HU + 1 item de mapa)

#### Salida
```json
[
  {
    "json": {
      "id_hu": "HU-1",
      "titulo": "Login",
      "descripcion": "...",
      "frames_info": [...],
      "mapa_consolidado": undefined  // No viene aquí
    }
  },
  {
    "json": {
      "mapa_consolidado": "=== CONTEXTO DEL MAPA ===..."
    }
  }
]
```

---

### 12. **Analyze an image** (Análisis con Google Gemini 2.5 Flash)

#### Propósito
Utilizar IA (Google Gemini) para analizar las imágenes y generar matrices de decisión (tablas de verdad) con criterios de aceptación.

#### Configuración
```json
{
  "id": "57cf65de-6f26-4387-a874-72f77afc8d06",
  "name": "Analyze an image",
  "type": "@n8n/n8n-nodes-langchain.googleGemini",
  "typeVersion": 1,
  "position": [1792, 160],
  "parameters": {
    "resource": "image",
    "operation": "analyze",
    "modelId": {
      "__rl": true,
      "value": "models/gemini-2.5-flash",
      "mode": "list",
      "cachedResultName": "models/gemini-2.5-flash"
    },
    "text": "{{ PROMPT EXTENSO }}",
    "inputType": "binary",
    "binaryPropertyName": "data_0",
    "options": {}
  },
  "credentials": {
    "googlePalmApi": {
      "id": "i6AlcEi2Rvcd9bIu",
      "name": "Google Gemini(PaLM) Api account 2"
    }
  }
}
```

#### Parámetros Clave
| Parámetro | Valor |
|:---|:---|
| **Recurso** | image |
| **Operación** | analyze |
| **Modelo** | gemini-2.5-flash |
| **Entrada Binaria** | data_0 (la primera imagen binaria) |
| **Autenticación** | Google Gemini API |

#### Prompt Enviado

El prompt es extenso e incluye:

1. **Contexto**: Rol de QA Analyst especializado en diseño de pruebas
2. **Objetivo**: Crear matriz de decisiones (tabla de verdad) basada en visual + observaciones
3. **Fuentes de Verdad** (Jerarquía):
   - Info Visual (elementos en pantalla)
   - Observaciones Técnicas
   - Contexto Mapa (guía de navegación)

4. **Reglas de Estructura**:
   - Nomenclatura idéntica a elementos visuales
   - Cobertura 2^n (combinaciones lógicas)
   - Glosario con validaciones visuales detalladas

5. **Reglas de Negocio**: 
   - USER-01 a USER-N (sobre usuarios)
   - SOL-01 a SOL-08 (sobre solicitudes)
   - CAL-01 a CAL-03 (sobre calendario)
   - FAC-01 (sobre facultades)
   - OFERTA-01 (sobre ofertas)

6. **Formato de Salida**: Markdown con estructura específica

#### Variables Inyectadas en el Prompt
```javascript
{
  "id_hu": "HU-1",
  "titulo": "Login de Usuario",
  "descripcion": "...",
  "observaciones": "...",
  "frames_info": [{nombre: "...", archivo_id: "..."}],
  "mapa_consolidado": "..."
}
```

#### Respuesta Esperada

```markdown
### Nro. HU-1 - Título: Login de Usuario

Descripción: ...

#### Matriz de Decisión HU-1

| ID | Condición | R1 | R2 |
| :-- | :--- | :-: | :-: |
| C1 | ¿"Usuario" lleno? | S | N |
| C2 | ¿"Contraseña" lleno? | S | N |
| | **ACCIONES** | | |
| A1 | Enviar formulario | X | |
| A2 | Mostrar error | | X |

### GLOSARIO DE ACCIONES

* **A1 - Enviar formulario:** "...detalles visuales..."
* **A2 - Mostrar error:** "...detalles visuales..."
```

---

### 13. **Code in JavaScript1** (Formateo del Documento Final)

#### Propósito
Tomar las respuestas de Gemini y formatearlas en un documento Markdown completo listo para publicar en Azure DevOps Wiki.

#### Código

```javascript
// 1. Recolectamos el texto con extracción robusta
const listaEscenarios = items.map(item => {
  const json = item.json;

  // CASO A: Estructura de Gemini
  if (json.content && json.content.parts && json.content.parts[0] && json.content.parts[0].text) {
    return json.content.parts[0].text;
  }

  // CASO B: Estructura simple
  return json.text || json.output || json.content;
})
.filter(texto => texto)
.map(texto => {
  // Conversión segura a String
  return String(texto).trim(); 
});

// 2. Unimos todo con separador Markdown
const contenidoUnido = listaEscenarios.join('\n\n---\n\n');

// 3. Creamos el documento con encabezado y fecha
const fecha = new Date().toLocaleDateString('es-ES');
const documentoFinal = `# Reporte de Tablas\n> Generado el: ${fecha}\n\n${contenidoUnido}`;

// 4. Salida para Azure DevOps
return [{
  json: {
    contenido_wiki: documentoFinal,
    page_path: "CriteriosS1", 
  }
}];
```

#### Salida
```json
[
  {
    "json": {
      "contenido_wiki": "# Reporte de Tablas\n> Generado el: 6/6/2026\n\n### Nro. HU-1...",
      "page_path": "CriteriosS1"
    }
  }
]
```

#### Transformaciones
- **Integración**: Combina múltiples respuestas de Gemini
- **Formateo**: Añade encabezado y fecha
- **Validación**: Asegura que el contenido sea String válido

---

### 14. **HTTP Azure enviar** (Publicación Final)

#### Propósito
Enviar el documento formateado a Azure DevOps Wiki mediante una solicitud PUT.

#### Configuración
```json
{
  "id": "64edc94b-e32b-49ec-b8ed-262a22d3d1c3",
  "name": "HTTP Azure enviar",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.3,
  "position": [2272, 160],
  "parameters": {
    "method": "PUT",
    "url": "https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages?path=/Testing(IA)/Sprint3/TablasS3&api-version=7.1",
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
| **URL** | `https://dev.azure.com/DTIC-2025-B/PoliTutoriasAI/_apis/wiki/wikis/PoliTutoriasAI.wiki/pages?path=/Testing(IA)/Sprint3/TablasS3&api-version=7.1` |
| **Autenticación** | HTTP Basic Auth |
| **Content-Type** | application/json |
| **Body** | JSON con propiedad `content` |

#### Cuerpo de Solicitud
```json
{
  "content": "# Reporte de Tablas\n> Generado el: 6/6/2026\n\n### Nro. HU-1..."
}
```

#### Respuesta Esperada
```json
{
  "id": 12345,
  "path": "/Testing(IA)/Sprint3/TablasS3",
  "url": "...",
  "createdBy": "...",
  "createdDate": "...",
  "editedBy": "...",
  "editedDate": "...",
  "content": "# Reporte de Tablas..."
}
```

---

## Análisis de Propiedades y Configuraciones

### Credenciales Utilizadas

#### 1. Azure DevOps (HTTP Basic Auth)
- **ID de Credencial**: `J1QlSdi95FPXq84s`
- **Nombre**: "Azure"
- **Tipo**: HTTP Basic Authentication
- **Uso**: Autenticación en APIs de Azure DevOps (wikis, páginas)
- **Nodos que la usan**: HTTP HU1, HTTP Mapa, HTTP Azure enviar

#### 2. Google Drive OAuth2
- **ID de Credencial**: `KRo0vEZn7fvpO3D1`
- **Nombre**: "Google Drive account"
- **Tipo**: OAuth2
- **Alcance**: Acceso a archivos en Google Drive
- **Uso**: Búsqueda y descarga de imágenes
- **Nodos que la usan**: Search files and folders, Download file1

#### 3. Google Gemini API
- **ID de Credencial**: `i6AlcEi2Rvcd9bIu`
- **Nombre**: "Google Gemini(PaLM) Api account 2"
- **Tipo**: API Key
- **Modelo**: gemini-2.5-flash
- **Uso**: Análisis de imágenes y generación de criterios
- **Nodos que la usan**: Analyze an image

### Variables Globales y Templating

#### Inyección Dinámica

El flujo utiliza expresiones n8n para inyectar valores dinámicamente:

```javascript
// Ejemplo 1: Obtener propiedad JSON del item actual
{{ $json.id_hu }}

// Ejemplo 2: Referenciar nodo específico
{{ $json.nombre_imagen_buscar }}.png

// Ejemplo 3: Acceder a salidas de nodo anterior
$('Code in JavaScript6').all()
```

#### Contexto de Ejecución

En cada nodo:
- `items`: Array de items procesados del nodo anterior
- `item`: Item actual
- `$json`: Acceso a propiedades JSON del item
- `$binary`: Acceso a propiedades binarias del item

---

## Flujo de Datos

### Ruta Completa de una Historia de Usuario

```
1. TRIGGER (Usuario hace clic)
   ↓
2. HTTP HU1
   - GET: Página 1490 de Azure Wiki
   - Respuesta: { content: "# HU-1...\n# HU-2..." }
   ↓
3. Code in JavaScript5
   - Parse: Extrae HU-1, HU-2, etc.
   - Salida: Array de historias con frames
   ↓
4. Code in JavaScript6
   - Expande: HU-1 con 2 frames → 2 items
   - Salida: [
       {id_hu: "HU-1", nombre_imagen_buscar: "Frame1"},
       {id_hu: "HU-1", nombre_imagen_buscar: "Frame2"}
     ]
   ↓
5. Search files and folders
   - Query: name = "Frame1.png" en carpeta SP3
   - Respuesta: [{id: "123", name: "Frame1.png"}]
   ↓
6. Download file1
   - Download: Archivo con id "123"
   - Respuesta: {json: {...}, binary: {data: [255, 216, ...]}}
   ↓
7. Code in JavaScript7
   - Combina: Datos HU + metadatos archivo + binario
   - Salida: {json: {..., archivo_id: "123"}, binary: {...}}
   ↓
8. Code in JavaScript8
   - Agrupa: Todos los frames de HU-1 en un item
   - Salida: {json: {id_hu: "HU-1", frames_info: [...]}, binary: {...}}
   ↓
9. MERGE (Sincroniza dos ramas)
   ↓
10. Analyze an image
    - POST: Imagen + prompt a Gemini
    - Respuesta: "### Nro. HU-1\n#### Matriz..."
    ↓
11. Code in JavaScript1
    - Formatea: Crea documento final
    - Salida: {contenido_wiki: "# Reporte...", page_path: "..."}
    ↓
12. HTTP Azure enviar
    - PUT: Documento a página Azure Wiki
    - Respuesta: {id: 12345, path: "...", content: "..."}
    ↓
FIN
```

### Ruta del Mapa (Rama Paralela)

```
1. TRIGGER
   ↓
2. HTTP Mapa
   - GET: Página 1422 de Azure Wiki
   - Respuesta: { content: "Razon: ...\nTotal de Nodos: 5..." }
   ↓
3. Code in Criterios1
   - Parse: Extrae razon, nodos, pantallas
   - Formatea: Crea bloque consolidado
   - Salida: {mapa_consolidado: "=== CONTEXTO..."}
   ↓
4. MERGE (Sincroniza con rama HU)
   ↓
[Continúa en paso 10 de la rama HU]
```

---

## Transformaciones de Datos

### T1: HTML Markdown → Objeto Estructurado

**Entrada**:
```
# HU-1 - Título: Login
COMO usuario QUIERO ingresar PARA acceder
Frames:
* Pantalla Login
* Pantalla Dashboard
Observaciones: Validar correo
```

**Proceso**: Regex y parsing en JavaScript5

**Salida**:
```json
{
  "id": "HU-1",
  "titulo": "Login",
  "descripcion": "COMO usuario QUIERO ingresar PARA acceder",
  "frames": ["Pantalla Login", "Pantalla Dashboard"],
  "observaciones": "Validar correo"
}
```

---

### T2: Array HU → Array Item (Expansión)

**Entrada**:
```json
[{"id": "HU-1", "frames": ["Frame1", "Frame2"]}]
```

**Proceso**: Bucle sobre frames en JavaScript6

**Salida**:
```json
[
  {"id_hu": "HU-1", "nombre_imagen_buscar": "Frame1"},
  {"id_hu": "HU-1", "nombre_imagen_buscar": "Frame2"}
]
```

---

### T3: Metadata Google Drive + Binario

**Entrada**:
```json
{
  "json": {"id": "123", "name": "Frame1.png"},
  "binary": {"data": [255, 216, ...]}
}
```

**Proceso**: Combinación en JavaScript7

**Salida**:
```json
{
  "json": {
    "id_hu": "HU-1",
    "archivo_nombre_original": "Frame1.png",
    "archivo_id": "123"
  },
  "binary": {"data": [255, 216, ...]}
}
```

---

### T4: Items Dispersos → Item Consolidado

**Entrada**:
```json
[
  {"json": {"id_hu": "HU-1", "frames_info": [...]}, "binary": {"data_0": {...}}},
  {"json": {"id_hu": "HU-1", "frames_info": [...]}, "binary": {"data_1": {...}}}
]
```

**Proceso**: Agrupamiento en JavaScript8

**Salida**:
```json
{
  "json": {
    "id_hu": "HU-1",
    "frames_info": [{...}, {...}]
  },
  "binary": {"data_0": {...}, "data_1": {...}}
}
```

---

### T5: Imagen + Prompt → Markdown Criterios

**Entrada**:
- Imagen PNG (binario)
- Prompt: "Crear matriz de decisión..."

**Proceso**: API Gemini en "Analyze an image"

**Salida**:
```markdown
### Nro. HU-1 - Título: Login

#### Matriz de Decisión HU-1

| ID | Condición | R1 | R2 |
| :-- | :--- | :-: | :-: |
| C1 | ¿Usuario lleno? | S | N |

### GLOSARIO DE ACCIONES

* **A1:** "Detalle visual..."
```

---

### T6: Markdown → Documento Wiki

**Entrada**:
```
"### Nro. HU-1...\n### Nro. HU-2..."
```

**Proceso**: Formateo en JavaScript1

**Salida**:
```
"# Reporte de Tablas\n> Generado el: 6/6/2026\n\n### Nro. HU-1...\n### Nro. HU-2..."
```

---

## Autenticaciones y Credenciales

### Flujo de Autenticación

```
┌─────────────────────────────────────┐
│  Usuario hace clic (Trigger)        │
└────────────┬────────────────────────┘
             │
    ┌────────┴───────┐
    │                │
    ▼                ▼
[Azure OAuth]   [Google OAuth]
    │                │
    ├─── HTTP HU1 ───┤
    │                │
    ├─ HTTP Mapa ────┤
    │                │
    └─ HTTP Enviar ──┤
                     │
                ┌────┴─────────┐
                │              │
                ▼              ▼
          [Drive Search]  [Gemini API]
          [Drive Download]

```

### Flujo de Autorización

1. **Azure DevOps**:
   - Tipo: Basic Auth (usuario:contraseña)
   - Scope: Wiki pages, read/write
   - Endpoints: Pages API 7.1

2. **Google Drive**:
   - Tipo: OAuth2
   - Scope: drive.readonly (búsqueda y descarga)
   - Endpoints: Files API

3. **Google Gemini**:
   - Tipo: API Key
   - Scope: Vision API (análisis de imágenes)
   - Modelo: gemini-2.5-flash

---

## Salida Final

### Estructura del Documento Publicado

```markdown
# Reporte de Tablas
> Generado el: 6/6/2026

---

### Nro. HU-1 - Título: Login de Usuario

Descripción: COMO usuario registrado QUIERO ingresar a mi cuenta PARA acceder al dashboard

#### Matriz de Decisión HU-1

| ID | Condición | R1 | R2 | R3 | R4 |
| :-- | :--- | :-: | :-: | :-: | :-: |
| C1 | ¿Email lleno? | S | S | N | N |
| C2 | ¿Contraseña llena? | S | N | S | N |
| | **ACCIONES** | | | | |
| A1 | Enviar solicitud | X | | | |
| A2 | Error: Email requerido | | X | X | X |
| A3 | Error: Contraseña requerida | | X | X | X |

### GLOSARIO DE ACCIONES

* **A1 - Enviar solicitud:** "El sistema valida el email y contraseña (según regla USER-01), redirige a la pantalla de Dashboard. **VALIDACIÓN VISUAL:** Se visualiza el título 'Bienvenido', el gráfico de solicitudes activas, y el botón 'Cerrar Sesión' como indica la Info Visual."

* **A2 - Error: Email requerido:** "Permanece en la pantalla de Login. **VALIDACIÓN VISUAL:** Muestra el mensaje de error exacto: 'El correo corporativo es obligatorio' en color rojo (#FF0000), bajo el campo Email."

* **A3 - Error: Contraseña requerida:** "Permanece en la pantalla de Login. **VALIDACIÓN VISUAL:** Muestra el mensaje de error: 'La contraseña es requerida' en color rojo, bajo el campo Contraseña."

---

### Nro. HU-2 - Título: Registro de Usuario

[Estructura similar para HU-2, HU-3, etc.]
```

### Publicación en Azure

**Ubicación**: `/Testing(IA)/Sprint3/TablasS3`

**Método**: PUT a Azure DevOps Wiki API

**Payload**:
```json
{
  "content": "# Reporte de Tablas\n> Generado el: 6/6/2026\n\n..."
}
```

**Respuesta**:
```json
{
  "id": 12345,
  "path": "/Testing(IA)/Sprint3/TablasS3",
  "url": "https://dev.azure.com/...",
  "version": 2,
  "content": "# Reporte de Tablas...",
  "createdBy": "system",
  "createdDate": "2026-06-06T...",
  "editedBy": "n8n-automation",
  "editedDate": "2026-06-06T..."
}
```

---

## Consideraciones de Rendimiento y Escalabilidad

### Limites y Restricciones

1. **Google Drive**: Búsqueda limitada a una carpeta específica
2. **Gemini**: Procesamiento de una imagen por HU (data_0)
3. **Azure**: API rate limits en wiki pages
4. **n8n**: Timeout por ejecución (~100s por defecto)

### Optimizaciones Posibles

1. Batch processing de múltiples HUs
2. Caché de búsquedas en Drive
3. Procesamiento paralelo de imágenes
4. Validación previa de archivos

---

## Conclusión

El flujo **TablasAC** es un sistema robusto de orquestación que:

1. **Integra** múltiples fuentes de datos (Azure, Google)
2. **Transforma** datos semi-estructurados en matrices lógicas
3. **Enriquece** con análisis de IA (Gemini)
4. **Publica** resultados automatizados

**Propósito**: Automatizar la generación de criterios de aceptación precisos y validados visualmente para pruebas de software (QA), eliminando errores manuales y asegurando coherencia entre especificaciones visuales y lógica de validación.

---

**Documento Generado**: 6 de junio de 2026
**Versión del Flujo**: g1VrC1yfZnfe2UDP (TablasAC)
