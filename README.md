# Clasificación de señales técnicas de compra en el S&P 500 mediante imágenes de velas japonesas y aprendizaje automático

Trabajo de Fin de Grado — Ingeniería Informática  
Universitat Autònoma de Barcelona  
Autor: Aaron Lozano Amores  
Curso académico: 2025–2026

---

## Descripción general

Este proyecto estudia si distintos modelos de aprendizaje automático pueden clasificar señales técnicas de compra en activos del S&P 500 utilizando imágenes de velas japonesas.

El objetivo no es predecir directamente el comportamiento futuro del mercado, sino analizar si los modelos son capaces de reconocer visualmente patrones asociados a señales técnicas de compra.

Para ello, las series históricas de precios OHLC se transforman en ventanas temporales y posteriormente en imágenes RGB de velas japonesas de 30×30 píxeles. Cada imagen se etiqueta mediante reglas basadas en tres indicadores técnicos:

- RSI
- MACD
- Bandas de Bollinger

Posteriormente se comparan modelos clásicos de machine learning, una red neuronal convolucional y un sistema de votación por mayoría.

---

## Objetivos del proyecto

- Descargar y preparar datos históricos OHLC de activos del S&P 500.
- Generar etiquetas de señal de compra / no compra mediante RSI, MACD y Bandas de Bollinger.
- Transformar series temporales financieras en imágenes de velas japonesas.
- Entrenar y comparar modelos clásicos de machine learning, una CNN y un sistema Hard Voting.
- Evaluar el rendimiento mediante métricas de clasificación y matrices de confusión.
- Analizar falsos positivos y realizar una evaluación bursaria simplificada de las señales generadas.

---

## Metodología

El proyecto sigue el siguiente flujo de trabajo:

1. Descarga de datos históricos OHLC.
2. Limpieza y preparación del conjunto de datos.
3. Cálculo de indicadores técnicos.
4. Generación de etiquetas de compra / no compra.
5. Construcción de ventanas temporales.
6. División en conjuntos de entrenamiento, validación y prueba.
7. Generación de imágenes de velas japonesas de 30×30 píxeles.
8. Entrenamiento de modelos de machine learning.
9. Evaluación de resultados y análisis de errores.

---

## Conjunto de datos

Los datos se obtuvieron de Yahoo Finance mediante la librería `yfinance`.

- Activos analizados: 250 tickers del S&P 500
- Periodo temporal: datos diarios entre 2015 y 2026
- Variables utilizadas: Open, High, Low y Close
- Dataset final: 23.400 imágenes de velas japonesas
- Imágenes por indicador: 7.800
- Tamaño de imagen: 30×30 píxeles
- Formato: RGB

El dataset completo y las imágenes generadas no se incluyen en este repositorio porque pueden regenerarse ejecutando el notebook. Se pueden incluir algunos ejemplos o salidas representativas únicamente con fines ilustrativos.

---

## Indicadores técnicos utilizados

### RSI

Se genera una señal de compra cuando:

```text
RSI < 30
