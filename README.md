# SI7011 — Aprendizaje Profundo

**Universidad EAFIT**  
**Maestría en Ciencia de Datos y Analítica**  
**Estudiante:** Carlos José Muñoz Cabrera

## Descripción

Este repositorio reúne los trabajos desarrollados durante el curso **SI7011 — Aprendizaje Profundo**, incluyendo los tres eventos evaluativos. Los ejercicios abarcan el entrenamiento de redes neuronales, el aprendizaje por transferencia en visión por computador y la adaptación de modelos de lenguaje mediante *fine-tuning* eficiente en parámetros.

Cada evento contiene un notebook con implementaciones, resultados experimentales, visualizaciones y análisis, además del PDF de la evaluación teórica.

## Estructura del repositorio

```text
si7011-Munoz/
├── README.md
├── .gitignore
├── event_1/
│   ├── Eventoevaluativo1_CarlosMunoz.pdf
│   └── sesion_02_6_integrador_covertype.ipynb
├── event_2/
│   ├── EventoEvaluativo2_CarlosMunoz.pdf
│   └── sesion_03_6_integrador_eurosat.ipynb
└── event_3/
    ├── EventoEvaluativo3_CarlosMunoz.pdf
    └── sesion_06_6_integrador_estilo_llm.ipynb
```

## Eventos evaluativos

### Evento 1 — Entrenamiento de redes neuronales con Covertype

**Objetivo:** Implementar y evaluar estrategias de entrenamiento para clasificación multiclase a partir de variables cartográficas.

**Actividades desarrolladas:**
- Partición estratificada y escalado sin fuga de información.
- Diseño de una red neuronal multicapa (*MLP*) con inicialización He y Batch Normalization.
- Optimización con AdamW y programación de la tasa de aprendizaje.
- Comparación de corridas y métricas (pérdida, accuracy y F1 macro) en MLflow.
- Evaluación en prueba e inferencia sobre datos crudos mediante `predict_raw`.

**Archivos:**
- [Notebook — Covertype](event_1/sesion_02_6_integrador_covertype.ipynb)
- [Evaluación teórica — Evento 1](event_1/Eventoevaluativo1_CarlosMunoz.pdf)

### Evento 2 — Transfer Learning con EuroSAT

**Objetivo:** Evaluar si las representaciones preentrenadas en ImageNet resultan útiles para clasificar imágenes satelitales del conjunto EuroSAT.

**Actividades desarrolladas:**
- Partición estratificada y aumento de datos mediante transformaciones geométricas.
- Entrenamiento de una CNN desde cero como línea base.
- Fine-tuning de ResNet-18 preentrenada en ImageNet, con tasas de aprendizaje diferenciadas.
- Experimento sobre el comportamiento de Batch Normalization.
- Registro de corridas en MLflow, análisis de matriz de confusión y predicción sobre imágenes crudas.

**Resultado destacado:** La ResNet-18 ajustada alcanzó una **accuracy de validación del 97,5 %**, frente al **92,1 %** de la CNN desde cero. No se atribuye toda la diferencia exclusivamente al preentrenamiento, porque también cambian arquitectura y optimización.

**Archivos:**
- [Notebook — EuroSAT](event_2/sesion_03_6_integrador_eurosat.ipynb)
- [Evaluación teórica — Evento 2](event_2/EventoEvaluativo2_CarlosMunoz.pdf)

### Evento 3 — Adaptación de modelos de lenguaje mediante LoRA

**Objetivo:** Comparar el uso de instrucciones en un prompt frente al ajuste supervisado para generar respuestas con un estilo inspirado en el castellano de *Don Quijote*.

**Actividades desarrolladas:**
- Preparación de conversaciones en formato *prompt/completion*.
- Uso del modelo Qwen2.5-0.5B-Instruct y entrenamiento SFT con LoRA.
- Cálculo de la pérdida solo sobre los tokens de respuesta (`completion_only_loss=True`).
- Comparación de modelo base, instrucciones de estilo y adaptación LoRA.
- Evaluación mediante NLL, perplejidad e indicadores de estilo.
- Experimento adicional cambiando el rango de LoRA de 16 a 4.
- Función `responder_raw` para inferencia con validación de entradas y carga del adaptador.

**Resultados destacados:**

| Estrategia | NLL en test |
|---|---:|
| Modelo base | 2.593 |
| Modelo base + prompt de estilo | 2.506 |
| Modelo ajustado con LoRA (r = 16) | 1.945 |
| Modelo ajustado con LoRA (r = 4) | 1.9482 |

En este conjunto de evaluación, LoRA redujo la pérdida frente al uso exclusivo de instrucciones de estilo. El rango menor produjo una diferencia pequeña en NLL.

**Archivos:**
- [Notebook — Adaptación de LLM](event_3/sesion_06_6_integrador_estilo_llm.ipynb)
- [Evaluación teórica — Evento 3](event_3/EventoEvaluativo3_CarlosMunoz.pdf)

## Herramientas y tecnologías

- **Python y Jupyter Notebook:** implementación y documentación de experimentos.
- **PyTorch:** entrenamiento y evaluación de redes neuronales.
- **scikit-learn:** preprocesamiento y métricas.
- **Torchvision:** modelos y transformaciones para imágenes.
- **MLflow:** seguimiento de experimentos, métricas y artefactos.
- **Hugging Face Transformers, PEFT y TRL:** modelos de lenguaje, LoRA y SFT.

## Ejecución y reproducibilidad

Los notebooks incluyen el código desarrollado y las salidas guardadas de su ejecución. Para reproducir los experimentos:

1. Abrir el notebook de interés en un entorno compatible con Python y Jupyter.
2. Instalar las dependencias indicadas en el propio notebook.
3. Configurar el acceso a los conjuntos de datos y a los modelos preentrenados.
4. Ejecutar las celdas en el orden previsto.
5. Revisar las métricas, visualizaciones y análisis.

Algunos entrenamientos requieren una GPU y acceso a recursos externos. Las cifras reportadas corresponden a las ejecuciones documentadas en los notebooks.

## Organización de los entregables

Cada carpeta contiene un **PDF de la evaluación teórica (Parte A)** y un **notebook práctico (Parte B)** con los TODO implementados, las salidas de ejecución y las respuestas a las preguntas de análisis.

---

**Universidad EAFIT · Maestría en Ciencia de Datos y Analítica · SI7011 — Aprendizaje Profundo**
