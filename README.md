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

##  Limpieza
- Eliminé ~3.700 filas vacías de la tabla de partidos.
- Corregí nombres de equipos corruptos (un prefijo `rn">` que arrastraba el dataset original).
 - **Selecciones sucesoras:** algunas naciones aparecen divididas por cambios históricos
  (URSS/Rusia, Yugoslavia/Serbia, Checoslovaquia/Chequia). Al no afectar a los resultados principales, se dejaron **separadas**
  y se documenta aquí la decisión. Sí se unificaron los casos claros de una misma entidad mal
  etiquetada: Alemania (FRG/GER) e Irán ("IR Iran"/"Iran").
- Convertí a su tipo correcto columnas numéricas mal interpretadas (asistencia y año).
- Detecté y eliminé **filas duplicadas** que inflaban los conteos. Lo descubrí al validar el máximo
  goleador: salían 19 goles cuando Klose marcó 16. Investigando, encontré duplicados en el fichero
  original **multiplicados por un cruce de tablas (merge)**, y los limpié en el origen con
  `drop_duplicates()`, verificando el resultado comparando el número de filas antes y después.
 

##  Hallazgos
- **El Mundial que más llenó los estadios fue USA 1994.** Tiene el récord de asistencia
  total de la historia (y eso que se jugaron menos partidos que sus posteriores mundiales: 24 vs 32), y al calcular la asistencia media por partido sigue siendo el número uno:
  es el más taquillero lo mires por donde lo mires. La asistencia media por partido verifica que fue probablemente por la capacidad de los estadios.
- **Brasil es la selección con más títulos (5).** Le siguen Alemania e Italia (18) y Argentina (16) (incluyendo su victoria en 2022).
- **Lección de limpieza de datos:** en los datos originales, "Germany FR" (Alemania Occidental)
  y "Germany" aparecían como países distintos, lo que hacía que Alemania pareciera tener solo 3
  títulos. Al unificarlos, su recuento real subió a 4.
- **Brasil es la única selección que ha jugado las 20 ediciones (1930–2014).**
  Le siguen Italia (18) y Argentina (16). Lo calculé combinando las apariciones
  como local y visitante (partidos) y contando los años únicos de cada país.
- **Alemania es la máxima goleadora de la historia de los Mundiales**, por delante de Brasil.
  Curiosamente, este dato solo aparece tras unificar "Germany FR" y "Germany", que el dataset
  contaba como países distintos, un recordatorio de que la limpieza de datos es importante.
- **El partido más goleador de la historia fue Austria 7–5 Suiza (1954): 12 goles**, todos en los
  90 minutos reglamentarios y 9 de ellos antes del descanso.
- **Los dorsales no se usaron en los Mundiales hasta 1954.** Antes, los jugadores no llevaban
  número: todos los registros con dorsal "0" corresponden exclusivamente a las ediciones de
  1930, 1934, 1938 y 1950. Lo confirmé cruzando la tabla de jugadores con la de partidos para obtener el año.
- **Excluyendo ese "0", el número más usado de la historia es el 1**, el dorsal del portero,
  por ser el más fijo de cada equipo en casi todos los partidos.
- **El dorsal 9 es el más goleador de la historia de los Mundiales** (256 goles), confirmando
  que es el número clásico del delantero centro. Para contarlo con precisión, extraje cada gol
  del texto de la columna de eventos (no solo los partidos en los que se marcó).
- **Argentina y Alemania son las selecciones más tarjeteras de la historia** (123 tarjetas cada una,
  hasta 2014). Alemania solo llega a lo más alto tras unificar sus siglas FRG y GER
- **El fútbol se ha vuelto menos goleador con los años.** Hay una correlación negativa fuerte
  (-0,75) entre el año y los goles por partido: el pico fue 1954 (~5,4 goles por partido) y desde
  entonces ha ido cayendo hasta el ~2,5 actual.
  Esto no significa que los años sean la causa sino sino que refleja la evolución táctica del juego. (correlación ≠ causalidad).
- **"Los goleadores son los más sucios": una ilusión estadística** (hasta 2014). La correlación bruta
  entre goles y tarjetas por selección era fuerte (0,84), pero al normalizar por partidos jugados cae a
  -0,30. La relación aparente la causaba la causaba el número de partidos disputados: los equipos que llegan lejos acumulan más de todo.
  
##  Estructura del repositorio
- `01_Limpieza_Fifa_WorldCup.ipynb` — limpieza de datos y primeras métricas
- `WorldCups.csv` — resumen por edición (actualizado a 2022)
- `WorldCupMatches.csv` — detalle de partidos (hasta 2014)
- `WorldCupPlayers.csv` — detalle de jugadores (hasta 2014)

## Validación
Los hallazgos principales se han contrastado con fuentes oficiales (FIFA, Wikipedia, Guinness)
y son consistentes con los registros históricos, respetando el alcance de cada dato:
el resumen por edición llega hasta 2022; el detalle de partidos y jugadores, hasta 2014.


