# ACD Proyecto Final: Análisis de Precios y Características en Falabella Perú

## Integrantes del Grupo
- Frisancho Gálvez, Gabriel Nicolás
- Cueva Loayza, Dayron Saiyuk
- 
- 

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
├── data/
│   ├── dataset_inicial.csv      # Dataset crudo obtenido del web scraping
│   └── dataset_final.csv        # Dataset procesado y listo para análisis
├── docs/
│   ├── Diccionario de Datos Inicial.pdf
│   └── Diccionario de Datos Final.pdf
├── notebooks/
│   └── 01_limpieza_preprocesamiento.ipynb # Notebook de limpieza
├── README.md                    # Documentación principal
└── requirements.txt             # Dependencias del proyecto

## Instalación y Reproducibilidad

Para replicar este análisis en tu entorno local, sigue estos pasos en git bash:

1. **Clona este repositorio:**
git clone https://github.com/dayroncueva-ops/ACD_Proyecto_2026.git
cd ACD_Proyecto_2026

2. **Instala las dependencias necesarias:**
pip install -r requirements.txt

3. **Ejecuta el Jupyter Notebook:**
jupyter notebook

Abre el archivo ubicado en notebooks/01_limpieza_preprocesamiento.ipynb y ejecuta las celdas en orden.
A
## Pipeline de Datos
El flujo de trabajo implementado en este proyecto consta de las siguientes etapas, desarrolladas en el notebook `01_limpieza_preprocesamiento.ipynb`:

1. **Ingesta y estructuración:** Carga del dataset original (`falabella_productos.csv`) y eliminación de registros duplicados exactos. Se estandarizaron los nombres de las columnas con minúsculas y sin espacios ni caracteres especiales para facilitar su manipulación.
2. **Limpieza y conversión de tipos:** Eliminación de símbolos monetarios en las variables de precios y conversión de tipos de datos de texto a numéricos. Se calculó la variable `descuento` a partir de la diferencia entre el precio original y el precio final.
3. **Tratamiento de valores nulos:** Diagnóstico de nulos (solo 5.29% en `precio_original`). Se aplicó una duplicación, si el precio original estaba vacío, se puso el valor del precio actual. El dataset final quedó con 0% de valores nulos.
4. **Tratamiento de outliers:** Detección de errores extremos de parseo web (productos con precios mayores a S/70,000) y su eliminación para no sesgar las estadísticas. Se aplicó el criterio del Rango Intercuartílico (IQR) para el diagnóstico de valores atípicos en las variables numéricas.
5. **Análisis exploratorio (EDA):** Generación de gráficos univariados (histogramas, boxplots) y bivariados (scatterplots) para entender la distribución de precios, la relación entre descuentos y precios y el comportamiento de las reseñas.
6. **Almacenamiento:** Exportación del dataset depurado (`dataset_final_limpio.csv`) con 1830 registros listos para la siguiente fase de análisis y modelado.

## Diccionario de Datos

## Requisitos y Dependencias
