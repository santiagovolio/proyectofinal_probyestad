# Sello 9 — Correlación vs. causalidad

**Pregunta de negocio:** ¿El clima "causa" que se venda más bebida caliente?

## Contenido

- `Sello9_correlacion_vs_causalidad.ipynb` — cuaderno completo (cargado y ejecutado):
  1. Tabla de contingencia `clima × categoria` (conteos y proporciones).
  2. Prueba chi-cuadrado de independencia y Cramér's V.
  3. Proporción de bebida caliente y unidades promedio por clima.
  4. Variables confusoras (hora del día, promociones, sucursal, música) verificadas en los datos.
  5. Conclusión en lenguaje de negocio.

## Cómo ejecutar

Abre el cuaderno desde la raíz del repositorio:

```bash
jupyter lab sello_9_correlacion_causalidad/Sello9_correlacion_vs_causalidad.ipynb
```

El cuaderno resuelve la ruta del dataset (`../cafe_cordillera_dataset.csv`) de forma automática.

## Requisitos

`pandas`, `numpy`, `scipy`, `matplotlib`, `seaborn`. Instalación completa:

```bash
pip install pandas numpy scipy matplotlib seaborn statsmodels scikit-learn
```
