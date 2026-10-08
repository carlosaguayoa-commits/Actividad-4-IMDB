# Actividad-4-IMDB
Tarea Actividad 4 

# Benchmark de Modelos Preentrenados de Hugging Face para Análisis de Sentimiento

Este repositorio contiene la implementación, evaluación y análisis comparativo de modelos Transformer preentrenados de la plataforma **Hugging Face** para la tarea de clasificación binaria de sentimientos (Positivo / Negativo) en reseñas de cine utilizando el dataset de benchmark `IMDb`.

---

## 📋 Tabla de Contenidos
- [Entorno de Ejecución](#-entorno-de-ejecución)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Pasos de Ejecución](#-pasos-de-ejecución)
- [Resultados Comparativos](#-resultados-comparativos)
- [Conclusiones y Recomendaciones](#-conclusiones-y-recomendaciones)

---

## ⚙️ Entorno de Ejecución
## 🚀 Pasos de Ejecución (Google Colab)

Para ejecutar y reproducir los resultados de este proyecto no necesitas instalar nada localmente. Todo el proceso se realiza en la nube a través de Google Colab con aceleración GPU:

1. **Abrir el Notebook:**
   Haz clic en el archivo [`Evaluación_de_Modelos_Preentrenados_de_Hugging_Face.ipynb`](./Evaluación_de_Modelos_Preentrenados_de_Hugging_Face.ipynb) dentro de este repositorio.

2. **Cargar en Google Colab:**
   En la parte superior de la vista del notebook en GitHub, haz clic en el botón **"Open in Colab"** (o descarga el archivo `.ipynb` y súbelo a [colab.research.google.com](https://colab.research.google.com/)).

3. **Activar la GPU T4:**
   Dentro de Colab, ve al menú superior:
   > **Entorno de ejecución** > **Cambiar tipo de entorno de ejecución** > Selecciona **GPU T4** > Guardar.

4. **Ejecutar el Cuaderno:**
   Ve a **Entorno de ejecución** > **Ejecutar todas** (o presiona `Ctrl + F9`). Las celdas instalarán automáticamente las dependencias, cargarán el dataset y evaluarán los tres modelos.

---

## 📁 Estructura del Proyecto

```text
.
├── README.md                   # Documentación técnica general
├── requirements.txt            # Dependencias del proyecto
├── notebooks/                  # Cuaderno reproducible en Colab
│   └── 01_huggingface_sentiment_benchmark.ipynb
├── src/                        # Scripts de Python organizados
│   ├── ingest_data.py
│   └── evaluate_models.py
├── data/                       # Muestras exportadas
│   ├── eval_dataset_sample.csv
│   └── eval_dataset_sample.jsonl
└── results/                    # Resultados tabulares exportados
    └── model_comparison_results.csv
