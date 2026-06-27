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

 ##  Llimpieza
- Eliminé ~3.700 filas vacías de la tabla de partidos.
- Corregí nombres de equipos corruptos (un prefijo `rn">` que arrastraba el dataset original).
- Unifiqué "Germany FR" y "Germany" como un mismo país para que saliese correctamente los recuentos.
- Convertí a su tipo correcto columnas numéricas mal interpretadas (asistencia y año).

##  Hallazgos
- **El Mundial que más llenó los estadios fue USA 1994.** Tiene el récord de asistencia
  total de la historia, y al calcular la asistencia media por partido sigue siendo el número uno:
  es el más taquillero lo mires por donde lo mires.
- **Brasil es la selección con más títulos (5).** Le siguen Italia y Alemania con 4 cada una,
  y Argentina con 3 (incluyendo su victoria en 2022).
- **Lección de limpieza de datos:** en los datos originales, "Germany FR" (Alemania Occidental)
  y "Germany" aparecían como países distintos, lo que hacía que Alemania pareciera tener solo 3
  títulos. Al unificarlos, su recuento real subió a 4.
- **Brasil es la única selección que ha jugado las 20 ediciones (1930–2014).**
  Le siguen Italia (18) y Argentina (16). Lo calculé combinando las apariciones
  como local y visitante (partidos) y contando los años únicos de cada país.

##  Estructura del repositorio
- `01_Limpieza_Fifa_WorldCup.ipynb` — limpieza de datos y primeras métricas
- `WorldCups.csv` — resumen por edición (actualizado a 2022)
- `WorldCupMatches.csv` — detalle de partidos (hasta 2014)
- `WorldCupPlayers.csv` — detalle de jugadores (hasta 2014)

##  Próximos pasos
- Más preguntas sobre los partidos (goles por selección, partidos más goleadores, anfitrión vs. resultado...).
- Análisis de la tabla de jugadores (`WorldCupPlayers.csv`).
- Construcción de un dashboard interactivo en Power BI.
