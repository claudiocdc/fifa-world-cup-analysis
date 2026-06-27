# Análisis Histórico de los Mundiales de Fútbol (1930–2022)

Proyecto de portafolio de análisis de datos sobre la historia de la Copa del Mundo de la FIFA.
Mi objetivo es practicar el ciclo completo de un análisis: limpieza de datos, exploración,
creación de métricas y visualización, siempre conectando los números con preguntas de negocio.

##  Objetivo
Explorar y limpiar datos históricos de los Mundiales para responder preguntas como:
¿qué torneo llenó más los estadios? ¿qué selección ha sido la más dominante?

##  Herramientas
- **Python** (pandas) para limpieza y análisis
- **Google Colab** como entorno de trabajo
- *(Próximamente)* Power BI para el dashboard final

##  Datos
Dataset clásico de la FIFA World Cup (Kaggle): ediciones, partidos y jugadores.

##  Alcance de los datos
- **Resumen por edición** (campeones, asistencia, goles): actualizado hasta **2022**.
- **Detalle de partidos y jugadores**: disponible hasta **2014** (limitación del dataset original).
- Las ediciones 2018 y 2022 se añadieron manualmente desde fuentes oficiales (FIFA / Wikipedia).

##  Hallazgos
- **El Mundial que más llenó los estadios fue USA 1994.** Tiene el récord de asistencia
  total de la historia, y al calcular la asistencia media por partido sigue siendo el número uno:
  es el más taquillero lo mires por donde lo mires.
- **Brasil es la selección con más títulos (5).** Le siguen Italia y Alemania con 4 cada una,
  y Argentina con 3 (incluyendo su victoria en 2022).
- **Lección de limpieza de datos:** en los datos originales, "Germany FR" (Alemania Occidental)
  y "Germany" aparecían como países distintos, lo que hacía que Alemania pareciera tener solo 3
  títulos. Al unificarlos, su recuento real subió a 4. 

##  Estructura del repositorio
- `01_Limpieza_Fifa_WorldCup.ipynb` — limpieza de datos y primeras métricas
- `WorldCups.csv` — resumen por edición (actualizado a 2022)
- `WorldCupMatches.csv` — detalle de partidos (hasta 2014)
- `WorldCupPlayers.csv` — detalle de jugadores (hasta 2014)

##  Próximos pasos
- Análisis exploratorio de la tabla de partidos
- Dashboard interactivo en Power BI
