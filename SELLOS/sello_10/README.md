# Sello 10 — Regresión

**Pregunta de negocio:** ¿Qué variables predicen mejor las unidades vendidas?

**Modelo:** `unidades ~ precio_unitario + promocion_activa + clima + hora + sucursal`

## Contenido

- `Sello10_regresion.ipynb` — cuaderno completo (cargado y ejecutado):
  1. Preparación de datos y dummies (clima, sucursal, categoría).
  2. Regresión lineal múltiple (OLS) con `statsmodels`: coeficientes, p-values y R².
  3. Coeficientes estandarizados para ordenar la importancia de cada predictor.
  4. Interpretación de coeficientes en lenguaje de negocio.
  5. Validación entrenamiento/prueba con `scikit-learn`.
  6. Análisis de residuos.
  7. Chequeo de robustez con regresión Poisson (la variable es un conteo).
  8. Conclusión en lenguaje de negocio.

## Cómo ejecutar

Abre el cuaderno desde la raíz del repositorio:

```bash
jupyter lab sello_10_regresion/Sello10_regresion.ipynb
```

El cuaderno resuelve la ruta del dataset (`../cafe_cordillera_dataset.csv`) de forma automática.

## Requisitos

`pandas`, `numpy`, `scipy`, `matplotlib`, `seaborn`, `statsmodels`, `scikit-learn`. Instalación completa:

```bash
pip install pandas numpy scipy matplotlib seaborn statsmodels scikit-learn
```
