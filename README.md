# 📡 Análisis de uso de clientes – ConnectaTel

Proyecto 6 del curso de Análisis de Datos de TripleTen (Sprint 7: *Análisis estadístico para detectar patrones y outliers*).

## 🎯 Objetivo del proyecto

ConnectaTel es una empresa de telecomunicaciones con operaciones en México y Colombia. El objetivo es entender **cómo usan realmente sus clientes los servicios móviles** (llamadas y mensajes) para:

- identificar patrones de uso y segmentos de clientes,
- detectar comportamientos atípicos (outliers) o errores de registro,
- analizar cómo varía el uso según la edad y el tipo de plan,
- proponer mejoras a la oferta de planes.

## 🗃️ Datasets utilizados

| Archivo | Contenido |
|---|---|
| `plans.csv` | Planes disponibles (Básico y Premium): precio, minutos, mensajes y GB incluidos, costo por extra. |
| `users_latam.csv` | 4,000 clientes: edad, ciudad, fecha de registro, plan y fecha de cancelación. |
| `usage.csv` | 40,000 registros de uso en 2024: llamadas (duración) y mensajes (longitud). |

> Los datasets pertenecen a la plataforma de TripleTen y no se incluyen en este repositorio. El notebook conserva las salidas de cada celda para poder revisar el análisis sin ejecutarlo.

## 📂 Estructura del repositorio

```
telecom-analysis/
├── notebooks/
│   └── connectatel_analysis.ipynb   # Notebook con el análisis completo
└── README.md
```

## 🛠️ Etapas del análisis

1. **Carga y exploración** de los tres datasets (`head()`, `shape`, `info()`).
2. **Problemas de calidad**: nulos, sentinels (`-999` en edad, `?` en ciudad) y fechas fuera de rango (registros en 2026).
3. **Limpieza**: imputación de la edad con la mediana, sentinels a nulos, fechas imposibles a nulas y verificación de nulos MAR en `duration` y `length`.
4. **Resumen por usuario**: cantidad de mensajes, llamadas y minutos de llamada por cliente.
5. **Distribuciones y outliers**: histogramas por plan, boxplots y límites con el método IQR.
6. **Segmentación**: grupos por nivel de uso (Bajo / Medio / Alto) y por edad (Joven / Adulto / Adulto Mayor).
7. **Insight ejecutivo** con conclusiones y recomendaciones para el negocio.

## 🧠 Hallazgos principales

- El 74% de los clientes tiene un **uso medio**, el 19% **bajo** y el 7% **alto**.
- La **edad no cambia el consumo**: todos los grupos usan en promedio ~5.5 mensajes, ~4.5 llamadas y ~23 minutos.
- Los clientes **Premium pagan más del doble que los Básico por un uso prácticamente igual**, y ambos planes consumen muy por debajo de lo incluido.
- Recomendaciones: revisar el plan Premium, crear un plan para clientes de alto uso y otro económico para los de bajo uso, y mejorar la captura de datos.

## ▶ Cómo ejecutar el notebook

**Opción 1 – Google Colab**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/katerinemoronb/telecom-analysis/blob/main/notebooks/connectatel_analysis.ipynb)

**Opción 2 – Jupyter local**

1. Clona o descarga este repositorio.
2. Instala las librerías: `pip install pandas numpy matplotlib seaborn`
3. Coloca los archivos `plans.csv`, `users_latam.csv` y `usage.csv` en una carpeta y ajusta las rutas de `pd.read_csv()` en el Paso 1.
4. Abre `notebooks/connectatel_analysis.ipynb` y ejecuta las celdas en orden.

## 🧰 Herramientas

Python · pandas · NumPy · matplotlib · seaborn · Jupyter Notebook
