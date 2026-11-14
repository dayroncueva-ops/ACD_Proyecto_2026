# ACD Proyecto Final: Análisis de Precios y Características en Falabella Perú

## Integrantes del Grupo
- Frisancho Gálvez, Gabriel Nicolás
- Cueva Loayza, Dayron Saiyuk
- Maguiña Quispe, Paul Ricardo 

## Contexto y Objetivos
Este proyecto busca analizar si las características comerciales de los productos de Falabella determinan el precio final del producto. Para ello, se realizó un web scraping inicial y un profundo proceso de limpieza, preprocesamiento y análisis exploratorio de datos (EDA) sobre un dataset de productos de tecnología (celulares y accesorios).

**Objetivo General:**
Determinar qué variables (marca, vendedor, descuentos, reseñas) influyen en el precio final de los productos en la plataforma de Falabella Perú.

**Objetivos Específicos:**
- Limpiar y estandarizar los datos extraídos mediante web scraping.
- Tratar valores nulos y atípicos bajo reglas de negocio justificadas.
- Generar variables derivadas (Feature Engineering) que aporten valor al análisis.
- Identificar patrones de consumo, segmentación de precios y comportamiento de las reseñas.

## Estructura del Repositorio
```text
├── data/
│   ├── dataset_inicial.csv           # Dataset limpio (salida del Notebook 1)
│   └── dataset_feature_engineering.csv # Dataset final procesado (salida del Notebook 2)
├── docs/
│   ├── Diccionario de Datos Inicial.pdf
│   └── Diccionario de Datos Final.pdf
├── notebooks/
│   ├── 01_limpieza_preprocesamiento.ipynb # Limpieza y tratamiento de datos
│   └── 02_feature_engineering_analisis_y_visualizacion.ipynb # FE y Análisis
├── README.md                    # Documentación principal
└── requirements.txt             # Dependencias del proyecto
```

## Instalación y Reproducibilidad

Para replicar este análisis en tu entorno local, sigue estos pasos en git bash:

1. **Clona este repositorio:**
git clone https://github.com/dayroncueva-ops/ACD_Proyecto_2026.git
cd ACD_Proyecto_2026

2. **Instala las dependencias necesarias:**
pip install -r requirements.txt

3. **Ejecuta el Jupyter Notebook:**
jupyter notebook

Ejecuta los notebooks en orden para reproducir el pipeline completo.

## Pipeline de Datos
El flujo de trabajo implementado se divide en dos etapas principales:

**Etapa 1: Limpieza y Preprocesamiento (`01_limpieza_preprocesamiento_corregido (2).ipynb`)**
1. **Ingesta:** Carga del dataset original y eliminación de duplicados exactos.
2. **Conversión de tipos:** Estandarización de nombres y conversión de variables monetarias (strings a float).
3. **Tratamiento de nulos:** Imputación de `precio_original` bajo regla de negocio (si está vacío, se iguala al `precio` actual). Resultado: 0% de nulos.
4. **Outliers:** Eliminación de errores de parseo web (precios > S/ 70,000) y diagnóstico con criterio IQR.

**Etapa 2: Feature Engineering y Análisis (`02_feature_engineering_analisis_y_visualizacion.ipynb`)**
5. **Generación de variables:** Creación de `ahorro` (diferencia en soles), segmentación por gamas (`segmento_precio_num`), e indicadores de reseñas.
6. **Transformación y Escalado:** Codificación (One-Hot Encoding) de marcas y descuentos, transformación logarítmica para reducir asimetría y escalado (MinMax y Standard).
7. **Análisis y Visualización:** Exploración de relaciones, detección de anomalías y segmentación de patrones de consumo.

## Insights Estratégicos
A partir del análisis exploratorio, se destacan los siguientes hallazgos:
- **Brand Premium:** Apple concentra su oferta en la cúspide del mercado, mientras que Xiaomi domina el volumen económico.
- **Elasticidad de descuentos:** La plataforma usa rebajas agresivas (>40%) para liquidar accesorios, pero la gama premium es inelástica (descuentos mínimos) para proteger su valor.
- **Calidad percibida:** La gama económica tiene alta variabilidad en sus reseñas (quejas), mientras que la gama Premium muestra una consistencia casi perfecta en sus calificaciones.
- **Concentración de oferta:** El catálogo está dominado por vendedores terceros del Marketplace (liderados por *Cellbytez Store*), superando al propio *retail* tradicional.

## Diccionario de Datos
El dataset final cuenta con **1830 registros** y variables clave como:
- `precio`: Precio final de venta en Soles.
- `precio_original`: Precio antes del descuento.
- `descuento`: Porcentaje de descuento calculado.
- `ahorro`: Diferencia absoluta en soles entre precio original y final.
- `segmento_precio_num`: Categorización de la gama (0: Económico, 1: Intermedio, 2: Gama Alta, 3: Premium).
- `calificacion_con_resenas`: Puntuación aislada de productos con opiniones reales.

## Requisitos y Dependencias
El proyecto utiliza las siguientes librerías principales de Python (detalladas en `requirements.txt`):
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `jupyter`
