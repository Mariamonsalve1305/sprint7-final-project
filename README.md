# 📊 Análisis de Comportamiento de Clientes — ConnectaTel LATAM

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es evaluar y comprender de forma integral el **comportamiento de consumo de los clientes** de la empresa de telecomunicaciones ConnectaTel en Latinoamérica dentro del periodo registrado **hasta el año 2024**.

A través de un enfoque programático, el análisis busca:
* Construir un **perfil estadístico** detallado de los usuarios.
* Detectar **comportamientos atípicos** y anomalías en el uso de los servicios.
* Estructurar **segmentos de clientes** basados en patrones reales de consumo.
* Proporcionar insights accionables para **diseñar estrategias de retención de clientes** (reducción de *churn*) y proponer **mejoras en la oferta comercial** de los planes de la empresa.

---

## 💾 Datasets Utilizados
El análisis se realiza mediante la integración y el procesamiento de tres conjuntos de datos principales:

1. **`plans.csv`**: Contiene las especificaciones comerciales de las tarifas vigentes (`Basico` y `Premium`). Incluye variables como precio base mensual, minutos/GB/mensajes incluidos y los costes adicionales por unidad extra.
2. **`users.csv`**: Base de datos de los usuarios registrados. Almacena información sobre edad, ciudad de residencia, fecha de registro, tipo de plan y fecha de cancelación (`churn_date`).
3. **`usage.csv`**: Detalle transaccional de la utilización real del servicio. Registra cada evento identificando si es una llamada o mensaje de texto, su fecha y sus métricas asociadas (duración en minutos o longitud del mensaje).

---

## 🛠️ Etapas del Análisis Realizadas

### 1. Carga y Exploración Inicial
* Importación del stack analítico esencial de Python (`pandas`, `numpy`, `matplotlib`, `seaborn`).
* Auditoría estructural preliminar usando métodos de inspección dimensional (`.shape`, `.head()`, `.info()`) para validar la correcta lectura en memoria de los tipos de datos primarios.

### 2. Identificación y Diagnóstico de Calidad de Datos
* **Análisis de Ausencias Legítimas vs. Anomalías (MAR/MCAR):** Se determinó matemáticamente que los valores nulos en `duration` y `length` corresponden a la naturaleza del servicio transaccionado (los mensajes no tienen duración en minutos y las llamadas no poseen longitud de caracteres).
* **Detección de Datos Inválidos (*Sentinels*):** Localización de registros erróneos en variables clave como valores de edad fuera de rango biológico (ej. `-999` en la columna `age`) que sesgan la media y desviación estándar de los perfiles de usuario.
* **Inconsistencias Categóricas:** Identificación de caracteres de ruido (como `?`) en campos de ubicación geográfica (`city`).

### 3. Limpieza, Imputación y Transformación *(Siguientes pasos)*
* Tratamiento y corrección de los tipos de datos (conversión de formatos `string`/`object` a tipos temporales `datetime` para columnas de fechas).
* Reemplazo estratégico o imputación de valores centinela (`-999`) basándose en medidas de tendencia central no sesgadas.

### 4. Análisis Estadístico y Segmentación *(Etapas de conclusión)*
* Agregación de consumos mensuales por usuario.
* Cálculo de ingresos generados por excesos de consumo.
* Modelado de comportamiento y visualización gráfica de patrones de abandono del cliente.

---

## 🚀 Cómo Ejecutar el Notebook

Este entorno está configurado para ejecutarse de manera óptima utilizando **Google Colab** o un servidor **Jupyter Notebook** local.

### Opción Recomendada: Google Colab
1. Ve a [Google Colab](https://colab.research.google.com/).
2. Selecciona la pestaña **Subir / Upload** y selecciona el archivo `.ipynb` de este repositorio.
3. Para asegurar que el notebook acceda a los archivos `.csv` correspondientes, debes estructurar un directorio con el nombre `datasets` en la raíz de almacenamiento temporal de tu sesión de Colab.

---
