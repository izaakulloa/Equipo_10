# CONTRIBUTIONS.md — Proyecto Integrador: Clasificación Supervisada

**Equipo:** Alex Astudillo, Martina Bedwell, Sebastián Quintolén, Valentina Quiroz, Izaak Ulloa

Este documento detalla las tareas principales, productos elaborados y revisiones cruzadas realizadas por cada integrante del equipo, según los roles definidos en la propuesta inicial del proyecto.

---

## Alex Astudillo

**Rol:** Formulación, datos y coordinación

**Tareas principales:**
•⁠  ⁠Formulación del problema de negocio y justificación para Ingeniería
  Industrial.
•⁠  ⁠Búsqueda y verificación de la fuente del dataset (UCI, licencia CC
  BY 4.0, DOI).
•⁠  ⁠Diseño del experimento de partición aleatoria vs. temporal (AUC
  0.775 vs. 0.714).
•⁠  ⁠Consolidación del ⁠ informe.Rmd ⁠ bajo la estructura de 14 secciones.
•⁠  ⁠Redacción de ⁠ DATASET_README.md ⁠, ⁠ README.md ⁠ y ⁠ CONTRIBUTIONS.md ⁠.

**Productos elaborados:**
•⁠  ⁠⁠ DATASET_README.md ⁠, ⁠ README.md ⁠, ⁠ CONTRIBUTIONS.md ⁠.
•⁠  ⁠⁠ informe.Rmd ⁠ consolidado (Secciones 1, 2, 4.3, 5 y 13).

**Revisión cruzada realizada:**
•⁠ Valentina Quiroz: apoyo en el código de KNN.
•⁠ Martina Bedwell: apoyo en la partición 80/20, planteando el argumento del drift de prevalencia como justificación.
•⁠ Izaak Ulloa: revisión del código de Random Forest.
•⁠ Sebastián Quintolen: apoyo en clasificación y selección del umbral, buscando el contenido del curso aplicable.


---

## Martina Bedwell

**Rol**: Preparación y modelos probabilísticos

**Tareas principales**:
•⁠  ⁠Implementación y análisis del baseline y regresión logística (Sección 7.1)
•⁠  ⁠Evaluación e interpretación del desempeño de la regresión logística dentro del esquema de validación cruzada
•⁠  ⁠Apoyo en la revisión de la partición estratificada 80/20 y coherencia del pipeline de modelamiento

**Productos elaborados:**
•⁠  ⁠chunks "baseline" y "logit-cv" en informe.Rmd

**Revisión cruzada realizada:**
•⁠  ⁠Revisé el código de: Alex Astudillo
•⁠  ⁠Comentarios/correcciones aportadas: Formulación del problema de negocio y definición de la decisión predictiva

•⁠  ⁠Revisé el código de: Sebastián Quintolén
•⁠  ⁠Comentarios/correcciones aportadas: Comparación de modelos, diagnóstico de calibración y selección del umbral operacional

•⁠  ⁠Revisé el código de: Izaak Ulloa
•⁠  ⁠Comentarios/correcciones aportadas: Revisión de los resultados y chunks correspondientes a Árbol de clasificación, Random Forest y Gradient Boosting

---

## Valentina Quiroz

**Rol:** Modelos geométricos y locales

**Tareas principales:**
•⁠  ⁠Realización del kNN, SVM lineal y SVM con kernel RBF (Sección 7.2 - 7.3)
•⁠  ⁠Ajuste de grillas de hiperparámetros, tales como k, C y sigma.

**Productos elaborados:**
•⁠  ⁠chunks “knn-cv”, “svm”, “svm-ker” y sus correspondientes partes en el informe.

**Revisión cruzada realizada:**
•⁠  ⁠Izaak Ulloa: Revisión del código de arbol de clasificación
•⁠  ⁠Sebastian Quintolen: Apoyo en la comparación formal de la calibracion
•⁠  ⁠Martina Bedwell: Apoyo en la creación de los chunks “baseline”, “logit-cv”, “partición”.
•⁠  ⁠Alex Astudillo: Apoyo en la consolidación final del informe y en la coordinación de migración del codigo.


## Izaak Ulloa

**Rol:** Arboles y Ensambles

**Tareas principales:**
•⁠  ⁠Árbol de clasificación, Random Forest y Gradient Boosting

**Productos elaborados:**
•⁠  ⁠Árbol de decisión, r-forest y gboosting en "informe.rmd"

**Revisión cruzada realizada:**
•⁠  ⁠Revisé el código de: Alex Astudillo
•⁠  ⁠Comentarios/correcciones aportadas: Sugerir eliminar la variable "duration", ya que ésta puede sesgar la predicción.

•⁠  ⁠Revisé el código de: Martina Bedwell
•⁠  ⁠Comentarios/correcciones aportadas: Revisión de la preparación de las variables.

•⁠  ⁠Revisé el código de: Valentina Quiroz
•⁠  ⁠Comentarios/correcciones aportadas: Revisión del ajuste de grillas.

•⁠  ⁠Revisé el código de: Sebastián Quintolén
•⁠  ⁠Comentarios/correcciones aportadas: Revisión del índice de Youden.

---

## Sebastián Quintolén

**Rol:** Evaluación y decisión

**Tareas principales:**
•⁠  ⁠Comparación formal de validación cruzada, calibración y selección de umbral
•⁠  ⁠Análisis de sensibilidad de costos, sistema final congelado y auditoría de subgrupo

**Productos elaborados:**
•⁠  ⁠chunks "comp-c", "calibracion-sin-test", "youden", "sistema-congelado", "auditoria-mes"

**Revisión cruzada realizada:**
•⁠  ⁠Revisé el código de: Alex Astudillo
•⁠  ⁠Comentarios/correcciones aportadas: Investigación de fuente, licencia y DOI del dataset

•⁠  ⁠Revisé el código de: Martina Bedwell
•⁠  ⁠Comentarios/correcciones aportadas: Baseline y regresión logística

•⁠  ⁠Revisé el código de: Valentina Quiroz
•⁠  ⁠Comentarios/correcciones aportadas: Ajuste de grillas de hiperparámetros (k, C, sigma) y paralelización

•⁠ Revisé el código de: Izaak Ulloa
•⁠ Comentarios/correcciones aportadas: Árbol de clasificación, Random Forest y Gradient Boosting

---

## Declaración firmada

Declaramos que la información presentada en este documento refleja fielmente la contribución individual de cada integrante al proyecto, y que todos los integrantes revisaron y pueden explicar el pipeline completo, no solo la parte de su rol asignado.

| Integrante | Firma / confirmación |
|---|---|
| Alex Astudillo | **CONFIRMO** |
| Martina Bedwell | **CONFIRMO** |
| Sebastián Quintolén | **CONFIRMO** |
| Valentina Quiroz | **CONFIRMO** |
| Izaak Ulloa | **CONFIRMO** |

*Fecha: 09-08-2026*
