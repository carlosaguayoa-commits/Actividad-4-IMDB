# Benchmark de Modelos Preentrenados de Hugging Face para Análisis de Sentimiento

[![Open In Colab](https.colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/carlosaguayoa-commits/Actividad-4-IMDB/blob/main/Evaluaci%C3%B3n_de_Modelos_Preentrenados_de_Hugging_Face.ipynb)

Este repositorio contiene la implementación, evaluación y análisis comparativo de tres modelos Transformer preentrenados de la plataforma **Hugging Face** para la clasificación binaria de sentimientos (Positivo / Negativo) en reseñas de cine utilizando el dataset `IMDb`.

---

## 📋 Tabla de Contenidos
- [Entorno de Ejecución](#-entorno-de-ejecución)
- [Pasos de Ejecución](#-pasos-de-ejecución)
- [Resultados Comparativos](#-resultados-comparativos)
- [Conclusiones y Recomendaciones](#-conclusiones-y-recomendaciones)

---

## ⚙️ Entorno de Ejecución

* **Entorno de Prototipado:** Google Colab
* **Acelerador de Hardware:** GPU NVIDIA Tesla T4 (VRAM: ~15 GB)
* **Versión de Python:** 3.10+
* **Ecosistema:** PyTorch, Hugging Face `transformers`, `datasets`, `evaluate`, `scikit-learn` y `pandas`.

---

## 🚀 Pasos de Ejecución

1. Haz clic en el botón superior **Open in Colab** o abre el archivo [`Evaluación_de_Modelos_Preentrenados_de_Hugging_Face.ipynb`](./Evaluación_de_Modelos_Preentrenados_de_Hugging_Face.ipynb) en este repositorio.
2. Dentro de Google Colab, activa la GPU en el menú: **Entorno de ejecución > Cambiar tipo de entorno de ejecución > GPU T4 > Guardar**.
3. Selecciona **Entorno de ejecución > Ejecutar todas** (`Ctrl + F9`) para correr todo el análisis.

---

## 📊 Resultados Comparativos

Resumen de métricas y latencia obtenidas sobre la muestra de evaluación en GPU Tesla T4:

| Modelo | Hugging Face ID | Accuracy | Precision | Recall | F1-Score | Latencia Total (s) | Latencia/Muestra (ms) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **DistilBERT (Ligero)** | `distilbert-base-uncased-finetuned-sst-2-english` | 0.8900 | 0.9099 | 0.8618 | 0.8852 | 8.22 | **16.44** |
| **BERT Base (Estándar)** | `textattack/bert-base-uncased-SST-2` | 0.9000 | 0.8952 | 0.9024 | 0.8988 | 13.99 | 27.99 |
| **RoBERTa Large (Alta Capacidad)** | `siebert/sentiment-roberta-large-english` | **0.9440** | **0.9431** | **0.9431** | **0.9431** | 42.32 | 84.63 |

---

## 💡 Conclusiones y Recomendaciones

### Modelo Elegido: DistilBERT (`distilbert-base-uncased-finetuned-sst-2-english`)
A pesar de que **RoBERTa Large** nos da los mejores valores cuantitativos (F1 = 0.9431), **DistilBERT** representa la opción arquitectónica óptima en un entorno productivo real de uso masivo debido a:
* **Eficiencia en costo-beneficio:** Ofrece una precisión diagnóstica bastante sólida (89.0% Accuracy / 88.52% F1) procesando hasta **60 peticiones por segundo por GPU T4** (16.44 ms por muestra).
* **Escalabilidad y Menor Costo:** Su baja exigencia computacional permite realizar múltiples réplicas en un mismo entorno GPU o incluso realizar un despliegue eficiente en CPUs mediante marcos de inferencia, haciéndolo más escalable y económico.
* *Nota:* Si el caso de uso no fuera para análisis en tiempo real y la velocidad de respuesta no fuera una prioridad, la elección sería RoBERTa Large.
