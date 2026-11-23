# GeoHub | Kamila Guerrero — Geóloga

**Directorio interactivo y suite de herramientas web para Geología, Geografía, Minería, SIG y Monitoreo de Emergencias en Chile.**

Desarrollado como una aplicación web ligera (*Single-Page / Multi-Module*), sin necesidad de backend ni instalaciones complejas, diseñada para trabajo técnico de gabinete y terreno.

![Estado](https://img.shields.io/badge/estado-activo-success)
![Stack](https://img.shields.io/badge/stack-HTML5%20%7C%20TailwindCSS%20%7C%20JavaScript-3892D0)
![GIS](https://img.shields.io/badge/GIS-Leaflet%20%7C%20Esri%20%7C%20Proj4js-647855)

---

## Tabla de Contenidos
- [Características Principales del Panel](#características-principales-del-panel)
- [Módulos Incluidos](#módulos-incluidos)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Tecnologías y APIs Utilizadas](#tecnologías-y-apis-utilizadas)
- [Instalación y Uso](#instalación-y-uso)
- [Autora](#autora)

---

## Características Principales del Panel (`index.html`)

* **Organización Visual Personalizable:** Arrastra y suelta (*Drag & Drop* con SortableJS) cualquier tarjeta para reordenar tus herramientas según prioridad y cambia el color temático por disciplina.
* **Vista Previa Integrada:** Abre cualquier módulo directamente dentro de un visor modal sin abandonar el panel principal, o ábrelo en una pestaña independiente.
* **Buscador y Vistas:** Filtrado instantáneo por disciplina (Geología, Minería, SIG, Alertas) con alternancia entre vista cuadrícula y vista lista.
* **Modo Oscuro / Claro:** Interfaz optimizada para lectura prolongada en gabinete o visibilidad en terreno.
* **Persistencia Local:** Guarda automáticamente el orden, colores y nuevas herramientas personalizadas en `localStorage`.

---

## Módulos Incluidos

### 1. Monitor Unificado de Alertas por Región y Comuna (`modulos/alertas_regionales.html`)
Consolidador multi-organismo de emergencias y amenazas naturales en las 16 regiones y comunas de Chile[cite: 1, 2]:
* **Organismos integrados:** DMC (Meteorología), Armada / DIRECTEMAR, SENAPRED, SERNAGEOMIN (RNVV / Remociones), CONAF y SHOA[cite: 1, 2].
* **Mapa Interactivo (Leaflet + Esri):** Polígonos regionales coloreados según nivel de alerta (Roja, Amarilla, Aviso/ATP, Normal) con capas base Esri (Oscuro, Topográfico, Satelital y Vectorial).
* **Datos en Tiempo Real:** Sincronización meteorológica por región vía **Open-Meteo** (temperatura, viento, precipitación e isoterma 0°C) y sismicidad reciente ($M \ge 3.0$ en las últimas 48 h) vía **USGS**[cite: 2].
* **Despacho Rápido:** Generador de boletín consolidado listo para compartir por **WhatsApp**, copiar al portapapeles o exportar en `.TXT` y `.CSV`[cite: 2].

### 2. Conversor Geodésico Universal (`modulos/conversor_sig.html`)
Herramienta de geodesia y sistemas de información geográfica para conversión bidireccional simultánea[cite: 1, 6]:
* **Formatos soportados:** Grados Decimales (DD), Grados Minutos Segundos (DMS), Grados Minutos Decimales (DDM), Coordenadas UTM (Este/Norte), Cuadrícula Militar MGRS y Web Mercator (`EPSG:3857`)[cite: 1, 6].
* **Soporte Multi-Datum:** Transformaciones geodésicas mediante `Proj4js` entre **WGS84 / SIRGAS**, **PSAD56** y **SAD69**[cite: 1, 6].
* **Integración directa:** Enlace directo de verificación espacial en Google Maps[cite: 6].

### 3. Calculadora de Rumbo y Buzamiento (`modulos/calculadora_buzamiento.html`)
Conversión automática para mediciones estructurales en terreno[cite: 1, 3]:
* Transforma rumbo azimutal ($0^\circ - 360^\circ$), manteo y cuadrante hacia donde buza entre **Notación Cuadrante** (ej. `N45°E / 30°SE`), **Regla de la Mano Derecha (RHR)** y **Dip Direction / Dip**[cite: 3].

### 4. Libreta Digital de Terreno (`modulos/libreta_terreno.html`)
Registro estructurado de estaciones geológicas y muestreo en campaña[cite: 1, 7]:
* Almacena código de estación, litología/mena, datos estructurales y observaciones de alteración hidrotermal o mineralización con guardado automático en el navegador[cite: 7].

### 5. Clasificador Petrográfico QAPF (`modulos/clasificador_qapf.html`)
Normalizador modal para clasificación de rocas ígneas plutónicas y volcánicas[cite: 1, 4]:
* Calcula los porcentajes normalizados de **Cuarzo (Q)**, **Feldespato Alcalino (A)** y **Plagioclasa (P)** entregando la clasificación petrográfica correspondiente (Granito/Riolita, Granodiorita/Dacita, Tonalita, Diorita/Andesita, etc.)[cite: 4].

### 6. Columna Estratigráfica Rápida (`modulos/columna_estratigrafica.html`)
Generador visual de perfiles litológicos de base a techo[cite: 1, 5]:
* Permite construir secuencias sedimentarias y volcánicas asignando litología, espesor en metros y código de color estratigráfico[cite: 5].

---

## Estructura del Proyecto

```text
geohub/
├── index.html                            # Panel principal y gestor de módulos
├── README.md                             # Documentación del repositorio
└── modulos/
    ├── alertas_regionales.html           # Monitor de alertas por región y comuna (Esri/Leaflet)
    ├── conversor_sig.html                # Conversor geodésico multi-datum (Proj4js/MGRS)
    ├── calculadora_buzamiento.html       # Calculadora estructural (Cuadrante / RHR / DipDir)
    ├── libreta_terreno.html              # Registro digital de estaciones de campo
    ├── clasificador_qapf.html            # Normalizador QAP para rocas ígneas
    └── columna_estratigrafica.html       # Generador visual de columnas litológicas