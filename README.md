# Actividad-4-IMDB
Tarea Actividad 4 

# Benchmark de Modelos Preentrenados de Hugging Face para Análisis de Sentimiento

Este repositorio contiene la implementación, evaluación y análisis comparativo de modelos Transformer preentrenados de la plataforma **Hugging Face** para la tarea de clasificación binaria de sentimientos (Positivo / Negativo) en reseñas de cine utilizando el dataset de benchmark `IMDb`.

El proyecto evalúa la precisión diagnóstica frente a la latencia de inferencia en hardware GPU (NVIDIA Tesla T4) dentro de Google Colab.

---

## 📋 Tabla de Contenidos
- [Entorno de Ejecución](#-entorno-de-ejecución)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Pasos de Ejecución](#-pasos-de-ejecución)
- [Resultados Comparativos](#-resultados-comparativos)
- [Conclusiones y Recomendaciones](#-conclusiones-y-recomendaciones)

---

## ⚙️ Entorno de Ejecución

* **Entorno de Prototipado:** Google Colab
* **Acelerador de Hardware:** GPU NVIDIA Tesla T4 (VRAM: ~15 GB)
* **Versión de Python:** 3.10+
* **Ecosistema Principal:** PyTorch, Hugging Face `transformers`, `datasets`, `evaluate` y `scikit-learn`.

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
