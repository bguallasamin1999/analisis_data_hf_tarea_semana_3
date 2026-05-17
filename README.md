# Auditoría y Trazabilidad de IA Generativa con R

## Descripción del proyecto

Este proyecto tiene como finalidad implementar una auditoría básica para evaluar el uso de la Inteligencia Artificial Generativa mediante el análisis de conversaciones reales obtenidas desde el dataset `lmsys/lmsys-chat-1m` de Hugging Face.

El sistema fue desarrollado en lenguaje R y permite descargar una muestra de interacciones, procesar los mensajes, extraer prompts y respuestas, clasificar los prompts según su nivel de riesgo y generar reportes que apoyen la trazabilidad, supervisión y gobernanza del uso de IA generativa.

La auditoría clasifica cada interacción en tres niveles de riesgo:

- **BAJO:** Prompts sin señales críticas o sensibles.
- **MEDIO:** Prompts relacionados con código, tareas, ensayos, exámenes, artículos o actividades académicas que requieren supervisión.
- **ALTO:** Prompts que pueden estar relacionados con datos personales, credenciales, malware, phishing, deepfakes, manipulación o intentos de uso indebido.

Además, el sistema asigna un estado de control a cada prompt:

- **PERMITIDO:** El prompt no presenta señales de alto riesgo.
- **BLOQUEADO:** El prompt contiene patrones asociados a posibles riesgos críticos.

---

## Objetivo general

Implementar un proceso de auditoría y trazabilidad de interacciones con IA generativa utilizando R, con el propósito de identificar, clasificar y analizar prompts según su nivel de riesgo.

---

## Objetivos específicos

- Descargar datos reales desde Hugging Face mediante la API del Dataset Server.
- Procesar conversaciones del dataset `lmsys/lmsys-chat-1m`.
- Extraer prompts y respuestas desde las interacciones registradas.
- Clasificar los prompts en niveles de riesgo bajo, medio y alto.
- Detectar prompts que deben ser bloqueados automáticamente.
- Generar gráficos de análisis de riesgos.
- Exportar resultados en archivos CSV.
- Crear un reporte ejecutivo con los principales hallazgos de la auditoría.

---

## Fuente de datos

El proyecto utiliza el dataset:

```text
lmsys/lmsys-chat-1m
```

Este dataset contiene conversaciones con distintos modelos de lenguaje, lo cual permite analizar interacciones similares a las realizadas en herramientas de IA generativa.

La muestra utilizada en esta práctica fue de:

```text
100 registros
```

---

## Tecnologías utilizadas

- R
- RStudio
- Hugging Face Dataset Server
- tidyverse
- dplyr
- ggplot2
- readr
- httr
- jsonlite
- stringr
- tidyr
- lubridate

---

## Estructura del proyecto

```text
Laboratorio_HuggingFace_LMSYS/
│
├── data/
│   └── datos_originales_lmsys.csv
│
├── graficos/
│   ├── grafico_riesgos.png
│   ├── grafico_modelos.png
│   ├── grafico_estado_prompts.png
│   └── grafico_departamento.png
│
├── resultados/
│   ├── auditoria_ia_generativa_lmsys.csv
│   ├── prompts_bloqueados.csv
│   ├── riesgo_alto.csv
│   ├── riesgo_por_modelo.csv
│   ├── riesgo_por_usuario.csv
│   ├── riesgo_por_departamento.csv
│   └── tabla_riesgos.csv
│
└── reportes/
    └── reporte_ejecutivo.txt
```

---

## Proceso de auditoría

El proceso implementado sigue las siguientes etapas:

1. Limpieza del entorno de trabajo.
2. Instalación y carga de librerías.
3. Creación de carpetas del proyecto.
4. Configuración del dataset de Hugging Face.
5. Descarga de datos desde la API.
6. Procesamiento de conversaciones.
7. Extracción de prompts y respuestas.
8. Clasificación de riesgos.
9. Bloqueo automático de prompts críticos.
10. Generación de gráficos.
11. Exportación de resultados.
12. Creación de reporte ejecutivo.

---

## Clasificación de riesgos

El sistema utiliza reglas basadas en palabras clave para clasificar cada prompt.

### Riesgo alto

Se consideran de alto riesgo los prompts que contienen términos asociados a:

- Datos personales
- Información privada
- Contraseñas
- API keys
- Tokens
- Credenciales
- Malware
- Virus
- Phishing
- Deepfake
- Identidad falsa
- Propaganda política
- Hackeo
- Explotación de vulnerabilidades

### Riesgo medio

Se consideran de riesgo medio los prompts relacionados con:

- Tesis
- Ensayos
- Código
- Programación
- Artículos
- Contratos
- Exámenes
- Tareas
- Prompts
- Modelos
- Datasets
- Investigación académica

### Riesgo bajo

Se consideran de riesgo bajo los prompts que no contienen patrones sensibles o críticos.

---

## Resultados obtenidos

En la auditoría se analizaron 100 interacciones del dataset LMSYS Chat 1M.

Los resultados principales fueron:

```text
Riesgo alto: 4 registros
Riesgo medio: 31 registros
Riesgo bajo: 65 registros
```

La mayoría de los prompts fueron clasificados como riesgo bajo, lo que indica que gran parte de las interacciones no contienen elementos críticos. Sin embargo, se identificaron prompts de riesgo medio y alto que requieren revisión, supervisión o bloqueo.

---

## Gráficos generados

El proyecto genera gráficos para facilitar el análisis visual de la auditoría:

- Clasificación general de riesgos.
- Riesgos detectados por modelo de IA.
- Estado de prompts permitidos y bloqueados.
- Riesgos detectados por departamento.

Estos gráficos permiten observar la distribución de los niveles de riesgo y apoyar la toma de decisiones.

---

## Archivos exportados

El sistema genera archivos CSV con los resultados de la auditoría:

```text
auditoria_ia_generativa_lmsys.csv
prompts_bloqueados.csv
riesgo_alto.csv
riesgo_por_modelo.csv
riesgo_por_usuario.csv
riesgo_por_departamento.csv
tabla_riesgos.csv
```

Estos archivos pueden ser utilizados para análisis posteriores en herramientas como Excel, Power BI, Superset o Metabase.

---

## Conclusiones

La práctica demuestra que es posible implementar un proceso de auditoría de IA generativa utilizando R y datasets reales. A través de reglas de clasificación, el sistema permite identificar prompts de riesgo bajo, medio y alto, así como bloquear automáticamente solicitudes potencialmente críticas.

La trazabilidad generada mediante usuario, fecha, modelo, departamento, fuente e identificador de auditoría permite dar seguimiento a cada interacción. Esto contribuye al fortalecimiento de la gobernanza de IA, especialmente en entornos académicos, empresariales e institucionales.

---

## Recomendaciones

Se recomienda ampliar las reglas de clasificación de riesgo incorporando más palabras clave, patrones semánticos y validaciones contextuales. También sería útil integrar modelos de clasificación más avanzados para reducir falsos positivos y mejorar la precisión del análisis.

Además, se recomienda complementar el bloqueo automático con revisión humana, especialmente para prompts clasificados como riesgo alto, ya que algunas solicitudes pueden requerir interpretación contextual antes de tomar una decisión definitiva.

---

## Autor

Proyecto desarrollado como práctica académica para la materia relacionada con Inteligencia Artificial, Big Data, Transformación Digital y Gobernanza de IA.

```text
Auditoría y trazabilidad de IA generativa con R
Dataset: lmsys/lmsys-chat-1m
Fuente: Hugging Face
```
