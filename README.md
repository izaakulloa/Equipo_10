# Proyecto Integrador: Clasificación Supervisada — Bank Marketing

**Estadística Aplicada, Ingeniería Industrial, Universidad de Santiago de Chile**

**Equipo:** Alex, Martina, Valentina, Sebastián e Izaak
**Profesor:** Luis Rojo-González, Ph.D.
**Ayudantes:** Carla Jaramillo, Benjamín Quezada

## Descripción del proyecto

Este proyecto formula y resuelve un problema de clasificación binaria aplicado a Ingeniería Industrial: **predecir si un cliente de un banco aceptará un depósito a plazo**, a partir de información disponible antes de contactarlo telefónicamente.

El problema se enmarca como una decisión de **asignación eficiente de un recurso escaso** (el tiempo de los agentes de un call center) bajo una función de costos asimétrica entre falsos positivos (llamadas sin resultado) y falsos negativos (ventas potenciales perdidas) — un caso aplicado de optimización de procesos y toma de decisiones bajo incertidumbre.

Se comparan ocho familias de modelos de clasificación (baseline, regresión logística, KNN, SVM lineal, SVM con kernel RBF, árbol de clasificación, Random Forest y Gradient Boosting), evaluados bajo un protocolo riguroso de validación cruzada, calibración de probabilidades, selección de umbral de decisión y auditoría de subgrupos.

## Dataset

**Bank Marketing**, UCI Machine Learning Repository (ID 222), licencia CC BY 4.0.
Ver [`DATASET_README.md`](./DATASET_README.md) para la ficha completa (fuente, licencia, diccionario de variables, período, población y limitaciones).

## Resultado principal

- **Modelo seleccionado:** Gradient Boosting
- **Umbral de decisión:** índice de Youden (0.4874), seleccionado en validación
- **Desempeño en test (sistema congelado, evaluado una sola vez):** AUC ≈ 0.78, Sensibilidad ≈ 62%, frente a un baseline con Sensibilidad 0%
- Detalle completo de la comparación de los 8 modelos, calibración, selección de umbral y auditoría de subgrupo en [`informe.html`](./informe.html) / [`informe.Rmd`](./informe.Rmd)

## Estructura del repositorio

```
equipo_clasificacion/
├── README.md                  Este archivo
├── DATASET_README.md          Ficha completa del dataset
├── propuesta_problema.pdf     Propuesta inicial (problema, dataset, justificación)
├── informe.Rmd                Informe técnico completo (código + análisis)
├── informe.html               Informe técnico compilado (generado desde informe.Rmd)
├── presentacion.pdf           Presentación para la defensa oral
├── CONTRIBUTIONS.md           Registro de contribuciones y revisión cruzada del equipo
├── codigo/                    Scripts y notebooks de trabajo/exploración
├── figuras/                   Gráficos exportados
├── resultados/                Tablas de resultados exportadas
└── datos/                     Copia del dataset (o enlace_descarga.txt con el link a UCI)
```

## Cómo reproducir el análisis

1. Clonar o descargar este repositorio.
2. Colocar el archivo `bank-additional-full.csv` en la misma carpeta que `informe.Rmd` (ver [`DATASET_README.md`](./DATASET_README.md) para el link de descarga original).
3. Abrir `informe.Rmd` en RStudio.
4. Instalar los paquetes necesarios (el propio documento instala automáticamente los que falten al ejecutarse, vía `install.packages()` condicional).
5. Ejecutar **Knit → Knit to HTML** desde una sesión de R recién iniciada (Session → Restart R), para garantizar reproducibilidad completa de principio a fin.

**Nota de reproducibilidad:** se observó una pequeña variabilidad en resultados de SVM con kernel RBF entre distintas versiones de R (4.5.x vs. 4.6.x), atribuible a cambios en el algoritmo interno de muestreo aleatorio. El código maneja este caso explícitamente y no afecta la validez de las conclusiones; ver nota correspondiente en `informe.Rmd` y `sessionInfo()` al final del documento.

## Metodología (resumen)

- **Partición:** aleatoria estratificada 80/20 (train/test), con justificación explícita frente a la alternativa de partición temporal (ver sección correspondiente en `informe.Rmd`).
- **Balanceo de clases:** down-sampling aplicado únicamente dentro de cada fold de validación cruzada (`sampling = "down"` en `caret::trainControl`), nunca antes de la partición.
- **Preprocesamiento:** centrado y escalado recalculados dentro de cada fold (sin fuga de información hacia la validación).
- **Selección de modelo:** por ROC-AUC en validación cruzada, con análisis de incertidumbre entre folds.
- **Umbral de decisión:** comparación entre índice de Youden y umbral basado en costos, con análisis de sensibilidad a los supuestos de costo.
- **Test:** abierto una única vez, sobre el sistema ya congelado (algoritmo + hiperparámetros + umbral).

## Declaración de uso de IA

Ver declaración completa en `informe.Rmd` (sección correspondiente) y evidencia de uso en `CONTRIBUTIONS.md`.

## Licencia del código

Código desarrollado por el equipo para fines educativos, en el marco del curso Estadística Aplicada (Ingeniería Industrial, USACH). El dataset utilizado mantiene su licencia original CC BY 4.0 (ver `DATASET_README.md`).
