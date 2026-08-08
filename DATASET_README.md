# Dataset: Bank Marketing (UCI Machine Learning Repository)

## Fuente

- **Repositorio:** UCI Machine Learning Repository — dataset "Bank Marketing" (ID 222)
- **URL permanente:** https://archive.ics.uci.edu/dataset/222/bank+marketing
- **DOI:** [10.24432/C5K306](https://doi.org/10.24432/C5K306)
- **Autores:** S. Moro (ISCTE — University Institute of Lisbon), P. Cortez (Universidade do Minho), P. Rita (ISCTE — University Institute of Lisbon)
- **Fecha de donación al repositorio:** 13 de febrero de 2012
- **Fecha de acceso por el equipo:** *[PENDIENTE — completar con la fecha real de descarga]*
- **Copia de trabajo del equipo:** *[PENDIENTE — pegar aquí el link a la carpeta `datos/` de este repositorio]*, subida únicamente para trazabilidad y reproducibilidad. La fuente original y autoritativa sigue siendo UCI.

## Licencia

**Creative Commons Attribution 4.0 International (CC BY 4.0).**

Permite compartir y adaptar el dataset para cualquier propósito (incluyendo uso académico y comercial), siempre que se dé el crédito correspondiente a los autores originales y a UCI Machine Learning Repository.

Texto completo de la licencia: https://creativecommons.org/licenses/by/4.0/

### Alternativa descartada: mirrors de Kaggle

Se evaluaron copias del dataset alojadas en Kaggle (ej. `prakharrathi25/banking-dataset-marketing-targets`) y se descartaron como fuente principal porque:
- Tienen licencias etiquetadas de forma inconsistente y a veces contradictoria (un mirror aparece marcado como "CC0: Dominio Público", lo cual contradice la licencia real CC BY 4.0).
- No cuentan con DOI ni versionado estable.
- Existe riesgo de modificaciones no documentadas (columnas eliminadas o renombradas, reparticiones train/test propias del mirror).

## Citación académica

> Moro, S., Rita, P., & Cortez, P. (2014). *Bank Marketing* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5K306

> Moro, S., Cortez, P., & Rita, P. (2014). A Data-Driven Approach to Predict the Success of Bank Telemarketing. *Decision Support Systems*, 62, 22–31. https://doi.org/10.1016/j.dss.2014.03.001

## Unidad de observación

Cada fila representa **un contacto telefónico** realizado a un cliente en el marco de una campaña de marketing directo de una institución bancaria retail portuguesa, ofreciendo un producto de depósito a plazo.

## Población y período

- **Población:** clientes contactados telefónicamente por un banco retail portugués (identidad de la institución no divulgada, por privacidad).
- **Período cubierto por este archivo:** mayo de 2008 a noviembre de 2010.
- **Nota:** el trabajo académico original (Moro, Cortez & Rita, 2014) utilizó una ventana más amplia de datos (mayo 2008 – junio 2013, 52.944 contactos). El archivo público `bank-additional-full.csv` es "muy cercano" a esos datos, pero no idéntico, por restricciones de privacidad.
- **Tamaño:** 41.188 observaciones (41.176 tras eliminar duplicados) × 21 columnas.
- **Prevalencia del target:** 11.3% "yes" / 88.7% "no" (fuertemente desbalanceado).

## Variable objetivo (target)

| Variable | Tipo | Descripción |
|---|---|---|
| `y` | Binaria | ¿El cliente contrató un depósito a plazo tras el contacto? Valores: `"yes"` / `"no"`. Clase positiva: `"yes"`. |

## Diccionario completo de variables

### Datos del cliente

| Variable | Tipo | Descripción |
|---|---|---|
| `age` | Numérica | Edad del cliente, en años. |
| `job` | Categórica | Tipo de ocupación (12 categorías: admin., blue-collar, entrepreneur, housemaid, management, retired, self-employed, services, student, technician, unemployed, unknown). |
| `marital` | Categórica | Estado civil (divorced, married, single, unknown). |
| `education` | Categórica | Nivel educativo (basic.4y, basic.6y, basic.9y, high.school, illiterate, professional.course, university.degree, unknown). |
| `default` | Categórica | ¿Tiene crédito en mora? (no, yes, unknown). |
| `housing` | Categórica | ¿Tiene crédito hipotecario? (no, yes, unknown). |
| `loan` | Categórica | ¿Tiene préstamo personal? (no, yes, unknown). |

### Datos del último contacto de la campaña actual

| Variable | Tipo | Descripción |
|---|---|---|
| `contact` | Categórica | Tipo de contacto (cellular, telephone). |
| `month` | Categórica | Mes del último contacto (jan a dec). |
| `day_of_week` | Categórica | Día de la semana del último contacto (mon a fri). |
| `duration` | Numérica | Duración del último contacto, en segundos. **Excluida del modelamiento por Data Leakage:** solo se conoce después de finalizada la llamada. |

### Otros atributos de campaña

| Variable | Tipo | Descripción |
|---|---|---|
| `campaign` | Numérica (entera) | Cantidad de contactos realizados durante esta campaña para este cliente (incluye el contacto actual). |
| `pdays` | Numérica (entera) | Días transcurridos desde el último contacto de una campaña anterior. `999` significa que el cliente no había sido contactado antes. |
| `previous` | Numérica (entera) | Cantidad de contactos realizados antes de esta campaña para este cliente. |
| `poutcome` | Categórica | Resultado de la campaña de marketing anterior (failure, nonexistent, success). |

### Indicadores socioeconómicos (contexto agregado, no específicos del cliente)

| Variable | Tipo | Descripción |
|---|---|---|
| `emp.var.rate` | Numérica | Tasa de variación del empleo — indicador trimestral. |
| `cons.price.idx` | Numérica | Índice de precios al consumidor — indicador mensual. |
| `cons.conf.idx` | Numérica | Índice de confianza del consumidor — indicador mensual. |
| `euribor3m` | Numérica | Tasa Euribor a 3 meses — indicador diario. |
| `nr.employed` | Numérica | Número de empleados — indicador trimestral (a nivel país). |

Fuente de los indicadores socioeconómicos: Banco de Portugal (https://www.bportugal.pt/estatisticasweb).

## Valores faltantes

El dataset no tiene valores `NA` en el sentido convencional. Las variables categóricas usan la categoría `"unknown"` para representar información no declarada, y `pdays` usa el código `999` para "nunca contactado antes" (ambos se documentan y tratan explícitamente en el análisis, no se tratan como NA de R).

## Criterios de inclusión/exclusión aplicados por el equipo

- Se utilizan todas las observaciones del archivo `bank-additional-full.csv`.
- Se eliminan 12 filas exactamente duplicadas (limpieza de datos).
- Se excluye la variable `duration` del modelamiento predictivo por Data Leakage (ver `informe.Rmd`, sección "Instante predictivo").

## Restricciones de uso

Ninguna restricción especial más allá de la atribución exigida por CC BY 4.0. El dataset es de uso público para investigación y fines educativos.

## Limitaciones de representatividad

- Corresponde a una única institución bancaria, en un único país (Portugal), durante un período específico (2008–2010) que incluye efectos de la crisis financiera global — la generalización a otros bancos, países o períodos económicos distintos no está garantizada.
- Se detectó *drift* temporal en la prevalencia de la variable objetivo a lo largo del período de recolección (ver `informe.Rmd`, sección "Partición de datos").
