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
   Entre a: https://colab.research.google.com/drive/1aME9hAoU2fhHT3obQIpf0jYKwx_cWTob?authuser=1#scrollTo=DVWM_UJ2ympR

2. **Activar la GPU T4:**
   Dentro de Colab, ve al menú superior:
   > **Entorno de ejecución** > **Cambiar tipo de entorno de ejecución** > Selecciona **GPU T4** > Guardar.

3. **Ejecutar el Cuaderno:**
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


## Resultados Comparativos



---

## 💡 Conclusiones y Recomendaciones

Modelo elegido: DistilBERT
Elegí este modelo ya que a pesar de que RoBERTa Largen nos da los mejores valores cuantitativos, DistilBERT representa la opción arquitectónica óptima en un entorno productivo real de uso masivo, esto porque: 
•	Eficiencia en el costo - beneficio: Ofrece una precisión diagnóstica bastante sólida procesando hasta 60 peticiones por segundo por GPU T4, 16.44 ms por muestra. 
•	Escalabilidad: su baja capacidad computacional permite realizar múltiples réplicas en un mismo entorno GPU o incluso realizar un despliegue eficiente en CPUs mediante marcos de inferencia. Lo hace más escalable y a un costo más barato.
•	Si el caso no fuera para un análisis en tiempo real donde la velocidad de respuesta no es una prioridad, me inclinaría más por RoBERTa.
Umbrales:
•	Umbral de confianza: se recomienda establecer un nivel de confianza mínimo de probabilidad de softmax de 0.75 = 75%. Las predicciones que oscilen entre un 50 y 74% deberían pasar a una revisión humana.
•	Latencia: máximo 50 ms por petición.
Riesgos:
•	Sesgo de idioma: al estar los textos en ingles podría haber sesgos al pasarse a otro idioma o que estén sesgados por alguna región o modismos en específico. Su impacto puede ser alto.
•	Límite en la longitud del contexto (tokens 512): Textos muy extensos que superen los 512 tokens que se delimitaron, por lo que se podría perder conclusiones importantes al final del texto en algunos casos. Se podría mitigar dividiendo el documento en párrafos. Eso tiene un impacto medio, ya que la gran parte de las reseñas se puede inferir su sentimiento en menos de esa cantidad de token. 
•	Negaciones complejas o sarcasmo: dobles negativos o sarcasmos que no sean identificados, sin embargo, se pueden mitigar con un fine tuning etiquetando datos en específico. Su impacto se considera medio. 


