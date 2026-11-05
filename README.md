# 🚗 Accidentes Fatales en EE. UU. 2022 — Dashboard en Power BI

> ¿**Dónde**, **cuándo**, **cómo** y **a quién** afectan más los accidentes de tránsito mortales en Estados Unidos?

![Dashboard principal](panel-general.png)

Proyecto de análisis y visualización de datos construido en **Power BI** con la base pública de la **NHTSA** (National Highway Traffic Safety Administration) sobre accidentes fatales ocurridos en 2022. Incluye modelado de datos, medidas en **DAX** y tres dashboards interactivos.

---

## 🎯 Objetivo

Identificar patrones en los accidentes fatales para entender qué factores (ubicación, tipo de vía, clima, perfil de las víctimas y causa) concentran más muertes, y presentar los hallazgos de forma clara para la toma de decisiones.

## ❓ Preguntas que responde

- ¿Qué estados concentran más muertes, en cifras absolutas y **por cada 100,000 habitantes**?
- ¿Cómo evolucionan las muertes **mes a mes** y en acumulado durante el año?
- ¿Ocurren más en zonas **rurales o urbanas**? ¿En qué tipo de vía?
- ¿Cuáles son las **principales causas** del accidente?
- ¿Qué papel juegan el **clima**, las **motocicletas**, los **adultos mayores (65+)** y el **sexo** de las víctimas?
- ¿Cuánto tarda en promedio la **reacción de emergencia** por estado?

## 🔎 Hallazgos principales

> ✏️ *Reemplaza con tus cifras reales de cada dashboard.*

1. **Las carreteras principales (highways), sobre todo en el sur del país, concentran la mayor cantidad de muertes.**
2. **[Estado X]** tiene el mayor número de decesos, pero **[Estado Y]** lidera en muertes por 100,000 habitantes.
3. **[X %]** de las muertes ocurre en zonas **[rurales/urbanas]**.
4. La causa más frecuente es **[causa]**, con **[N]** decesos.
5. Los meses con más muertes son **[meses]**; **[mes]** tuvo un cambio de **[±X %]** frente al mes anterior.
6. Las **motocicletas** representan **[X %]** de las muertes y los **adultos de 65+** **[X %]**.

## 🖼️ Vista del proyecto

| Panorama general | Rutas, zona y causas |
|---|---|
| ![Panorama](panel-general.png) | ![Rutas y causas](dashboard-decesos_estado.png) 



## 🗂️ Estructura del reporte

| Página | Contenido |
|---|---|
| **Análisis exploratorio** | Exploración inicial: estados, fechas, clima, tipo de calle y autobuses escolares |
| **Dashboard general** | KPIs de decesos, tendencia en el tiempo y comparativo por estado |
| **Dashboard rutas y causas** | Zona rural/urbana, rutas con más muertes y causas del accidente |
| **Dashboard perfil de víctimas** | Sexo, motocicletas, adultos mayores y muertes por 100,000 habitantes |
| **Indicadores mensuales** | Acumulado anual, cambio mes vs. mes y tiempo de reacción promedio |

## 🧱 Modelo de datos

Modelo en estrella con:

- **Hechos:** `Accidentes USA 2022`, `Personas Accidentes 2022`
- **Dimensiones:** `FECHA`, `Poblacion de Estados`, `Auxiliar Accidentes USA 2022`

![Modelo de datos](imagenes/modelo-datos.png)

## 🧮 Medidas DAX destacadas

> ✏️ *Pega aquí tu código real. Estos son ejemplos del estilo; ajústalos a tus nombres de columnas.*

```DAX
Decesos Totales = SUM ( 'Accidentes USA 2022'[Decesos] )

Muertes por 100000 habitantes =
DIVIDE ( [Decesos Totales], SUM ( 'Poblacion de Estados'[Poblacion] ) ) * 100000

Muertos hasta la fecha =
TOTALYTD ( [Decesos Totales], 'FECHA'[Fecha] )

Cambio MesVsMes Muertos % =
VAR MesActual = [Decesos Totales]
VAR MesPasado = CALCULATE ( [Decesos Totales], PREVIOUSMONTH ( 'FECHA'[Fecha] ) )
RETURN DIVIDE ( MesActual - MesPasado, MesPasado )
```

## 🛠️ Herramientas y habilidades

- **Power BI Desktop** — visualización y dashboards
- **Power Query** — limpieza y transformación
- **DAX** — medidas, inteligencia de tiempo, métricas per cápita
- **Modelado dimensional** — esquema en estrella, tabla de calendario
- **Storytelling con datos** — mensajes clave en cada dashboard

## 📁 Contenido del repositorio

```
├── nhtsa_accidentes_2022.pbix   # Reporte de Power BI
├── imagenes/                    # Capturas de los dashboards
└── README.md
```

## ▶️ Cómo abrirlo

1. Descarga `nhtsa_accidentes_2022.pbix`.
2. Ábrelo con [Power BI Desktop](https://powerbi.microsoft.com/desktop/) 
3. Explora las páginas y usa los filtros y segmentaciones.

## 📚 Fuente de datos

- NHTSA — *Fatality Analysis Reporting System (FARS)*, 2022: <https://www.nhtsa.gov/research-data/fatality-analysis-reporting-system-fars>
- Población por estado: *[agrega tu fuente, p. ej. U.S. Census Bureau]*

## 👤 Autor

**[Tu nombre]** — [LinkedIn](https://www.linkedin.com/in/tu-usuario) · [Correo](mailto:tu-correo@ejemplo.com)

⭐ Si te resultó útil, deja una estrella al repositorio.
