# Proyecto Final Integrador — Café Cordillera

**TCNT0011 · Probabilidad y Estadística I · LEAD University**

Análisis integral del desempeño comercial de **Café Cordillera**, una cadena costarricense de cafeterías con sucursales en Cartago, Escazú, Heredia y San Pedro. El proyecto utiliza un único conjunto de datos para aplicar las diez técnicas principales del curso, desde estadística descriptiva hasta regresión múltiple, y convertir los resultados en decisiones de negocio reproducibles.

> **Pregunta de investigación:** ¿Qué decisiones de operación, surtido y promoción debe tomar la gerencia de Café Cordillera con base en la evidencia estadística de sus 11.983 transacciones registradas entre marzo y mayo de 2026?

## Información académica

| Campo | Detalle |
|---|---|
| Curso | TCNT0011 · Probabilidad y Estadística I |
| Universidad | LEAD University |
| Docente | Bernal Rojas Villalobos |
| Correo docente | bernal.rojas@ulead.ac.cr |
| Proyecto | Proyecto Final Integrador — Café Cordillera |
| Entrega | Viernes 21 de agosto de 2026, antes de las 11:59 p. m. |
| Valor | 50 puntos |
| Integrantes | Luciana Carabaguiaz, Diego Díaz, Julián Maroto y Santiago Volio |

## Objetivo

El objetivo es analizar el comportamiento comercial de Café Cordillera y responder preguntas relevantes para la gerencia mediante técnicas estadísticas aplicadas sobre el mismo dataset. El trabajo no está planteado como una colección de ejercicios independientes: cada análisis responde una pregunta de negocio y termina con una interpretación práctica.

El proyecto estudia principalmente:

- desempeño por sucursal, categoría y producto;
- comportamiento conjunto de compra;
- recurrencia de clientes;
- llegada de pedidos por hora;
- calidad y sesgo de los datos de satisfacción;
- estimación del ticket promedio;
- diferencias entre sucursales;
- impacto de las promociones;
- relación entre clima y mezcla de productos;
- predicción de unidades vendidas.

## Archivos del proyecto

```text
.
├── README.md
├── cafe_cordillera_dataset.csv
├── notebook proyecto final cafe cordillera.ipynb
├── REPORTE EJECUTIVO (versión reescrita).pdf
└── Pasted markdown.md
```

| Archivo | Descripción |
|---|---|
| `cafe_cordillera_dataset.csv` | Dataset original utilizado en todos los análisis. |
| `notebook proyecto final cafe cordillera.ipynb` | Cuaderno reproducible en Python con el setup, los diez sellos, cálculos, pruebas, modelos, visualizaciones e interpretaciones. |
| `REPORTE EJECUTIVO (versión reescrita).pdf` | Reporte ejecutivo dirigido a la gerencia con metodología, hallazgos, recomendaciones y limitaciones. |
| `Pasted markdown.md` | Material de referencia que contiene el HTML con las instrucciones originales del proyecto final, requisitos, entregables y rúbrica resumida. |
| `README.md` | Descripción general, instrucciones de ejecución y síntesis técnica del proyecto. |

## Dataset

El archivo `cafe_cordillera_dataset.csv` contiene **11.983 líneas de venta**, agrupadas en **7.731 pedidos** y correspondientes a **2.600 clientes**.

| Característica | Valor |
|---|---:|
| Filas | 11.983 |
| Columnas originales | 15 |
| Pedidos únicos | 7.731 |
| Clientes únicos | 2.600 |
| Sucursales | 4 |
| Productos | 13 |
| Categorías | 4 |
| Período | 2 de marzo al 31 de mayo de 2026 |
| Horario registrado | 6:00 a 19:00 |
| Calificaciones de satisfacción disponibles | 3.449 |
| Calificaciones de satisfacción faltantes | 71,22 % |

### Variables

| Variable | Descripción |
|---|---|
| `id_transaccion` | Identificador de la línea de venta. |
| `id_pedido` | Identificador del pedido al que pertenece la línea. |
| `id_cliente` | Identificador del cliente. |
| `fecha` | Fecha de la transacción. |
| `hora` | Hora registrada, de 6 a 19. |
| `sucursal` | Sucursal: Cartago, Escazu, Heredia o San Pedro. |
| `producto` | Producto vendido. |
| `categoria` | `bebida_caliente`, `bebida_fria`, `postre` o `snack`. |
| `precio_unitario` | Precio unitario del producto en colones. |
| `unidades` | Cantidad vendida en la línea, entre 1 y 4 unidades. |
| `medio_pago` | `efectivo`, `sinpe_movil` o `tarjeta`. |
| `clima` | `lluvioso`, `nublado` o `soleado`. |
| `promocion_activa` | Indicador binario: `1` cuando hay promoción y `0` cuando no. |
| `promocion_tipo` | `2x1_bebidas`, `combo_postre` o `descuento_10`; queda vacío cuando no hay promoción. |
| `calificacion_satisfaccion` | Calificación de 1 a 5; contiene una proporción alta de datos faltantes. |

Durante el análisis se crea además:

```python
df["monto"] = df["precio_unitario"] * df["unidades"]
```

`monto` representa el valor de una línea de venta. Para el análisis del **ticket**, el notebook agrupa por `id_pedido` y suma las líneas de cada pedido.

## Tecnologías

El análisis fue desarrollado en **Python 3** y está preparado para ejecutarse en **Google Colab** o en un entorno local de Jupyter.

Principales librerías utilizadas:

```text
numpy
pandas
matplotlib
seaborn
scipy
statsmodels
scikit-learn
```

Instalación local:

```bash
pip install numpy pandas matplotlib seaborn scipy statsmodels scikit-learn
```

## Cómo ejecutar el proyecto

1. Descargue o clone los archivos del proyecto.
2. Mantenga `cafe_cordillera_dataset.csv` en la misma carpeta que el notebook, o ajuste la ruta del dataset en el setup.
3. Abra `notebook proyecto final cafe cordillera.ipynb` en Jupyter Notebook, JupyterLab o Google Colab.
4. En Colab, suba el CSV al panel de archivos o monte Google Drive.
5. Ejecute las celdas en orden desde el inicio.
6. El bloque de setup carga el dataset una sola vez, convierte `fecha`, crea `monto` y deja disponible el `DataFrame` `df` para los diez sellos.

El notebook busca automáticamente el dataset en estas ubicaciones:

```python
"cafe_cordillera_dataset.csv"
"../cafe_cordillera_dataset.csv"
"/content/cafe_cordillera_dataset.csv"
"/content/drive/MyDrive/cafe_cordillera_dataset.csv"
```

Cuando el archivo no está en ninguna de esas rutas, se debe ajustar `DATA_PATH` o subir el CSV al entorno.

## Metodología: los diez sellos

Cada sello aplica una herramienta del curso a una pregunta concreta de negocio.

| Sello | Técnica | Pregunta de negocio | Método principal |
|---:|---|---|---|
| 1 | Descriptiva y visualización | ¿Qué se vende, dónde y cuánto factura Café Cordillera? | Medias, medianas, desviaciones estándar, agregaciones y gráficos. |
| 2 | Probabilidad condicional | ¿Comprar bebida caliente aumenta la probabilidad de comprar postre en el mismo pedido? | Probabilidades marginales y condicionales, tabla de contingencia. |
| 3 | Teorema de Bayes | Si un cliente compró postre en su primera visita, ¿qué tan probable es que vuelva? | Definición de eventos, probabilidades base y fórmula de Bayes. |
| 4 | Distribuciones | ¿Cuántos clientes puede esperar una sucursal en una hora dada? | Conteo de pedidos por sucursal-fecha-hora, Poisson y bondad de ajuste. |
| 5 | Muestreo y sesgos | ¿La calificación de satisfacción representa a todos los clientes? | Análisis de faltantes, comparaciones de respuesta y pruebas de independencia. |
| 6 | Intervalos de confianza | ¿Cuál es el ticket promedio real y con qué margen de error? | IC del 95 % con t de Student y verificación mediante bootstrap. |
| 7 | Prueba de hipótesis | ¿Una sucursal vende de verdad más que otra, o es azar? | ANOVA de una vía, OLS con variables indicadoras y t-test de confirmación. |
| 8 | A/B Testing | ¿La promoción activa realmente aumenta las ventas? | Comparación tratamiento-control, t de Welch, tamaño del efecto y validación. |
| 9 | Correlación vs. causalidad | ¿El clima causa que se venda más bebida caliente? | Chi-cuadrado, V de Cramér y análisis de variables confusoras. |
| 10 | Regresión | ¿Qué variables predicen mejor las unidades vendidas? | Regresión lineal múltiple, coeficientes estandarizados, validación y Poisson de robustez. |

## Resultados principales

### 1. Perfil de ventas

- **Facturación total del período:** ₡27.323.791.
- **Sucursal con mayor facturación:** Escazú, con ₡7.295.509.
- **Categoría con mayor facturación:** bebida fría, con ₡11.855.048.
- **Producto estrella:** Frappe, con ₡4.733.463 facturados.
- Escazú presenta el precio unitario medio más alto y, al mismo tiempo, la menor cantidad media de unidades por línea de venta entre las cuatro sucursales.

### 2. Probabilidad condicional: bebida caliente + postre

A nivel de pedido:

\[
P(\text{postre}) = 20,88\%
\]

\[
P(\text{postre}\mid\text{bebida caliente}) = 19,80\%
\]

La diferencia es de aproximadamente **−1,07 puntos porcentuales**. El comportamiento observado no respalda un combo de bebida caliente y postre como asociación natural de compra.

### 3. Bayes y recurrencia

Se define:

- **A:** cliente recurrente, es decir, realizó más de un pedido.
- **B:** la primera compra del cliente incluyó al menos un postre.

Resultados:

\[
P(A)=43,12\%
\]

\[
P(A\mid B)=59,77\%
\]

Conocer que la primera compra incluyó un postre eleva la probabilidad estimada de recurrencia en **16,65 puntos porcentuales**. Este resultado funciona como una **señal de segmentación**, no como prueba de que el postre cause la recurrencia.

### 4. Distribución de pedidos por hora

Las llegadas se modelan con una **distribución de Poisson por sucursal y franja horaria**. Al separar las horas, el índice medio de dispersión es aproximadamente **0,989**, cercano a 1.

El patrón de demanda es bimodal:

- pico matutino: **7:00–9:00**;
- pico vespertino: **16:00–18:00**;
- valles marcados alrededor de **11:00** y **15:00**.

Ejemplo operativo: en Escazú a las 17:00 se obtiene \(\lambda = 2,077\), y el percentil 95 corresponde a **5 pedidos**.

### 5. Muestreo y sesgo de satisfacción

De las 11.983 líneas de venta, **8.534 no tienen calificación**, equivalente a **71,22 %** de datos faltantes.

La media observada de satisfacción es **3,752**, pero no debe interpretarse como la satisfacción de toda la clientela. Las variables observables analizadas no muestran una relación estadísticamente significativa con la propensión a responder al nivel \(\alpha=0,05\), pero esto no descarta sesgo de autoselección relacionado con la satisfacción no observada.

El análisis de sensibilidad muestra que, cuando los no respondientes se suponen medio punto por debajo, la media global bajaría a **3,396**; con una diferencia de un punto, bajaría a **3,040**.

### 6. Intervalo de confianza del ticket

Sobre los 7.731 pedidos:

- **ticket promedio:** ₡3.534,3;
- **desviación estándar:** ₡2.302,5;
- **IC 95 %:** [₡3.483,0; ₡3.585,6];
- **margen de error:** ± ₡51,3.

El bootstrap de 5.000 remuestreos produce un intervalo muy cercano al paramétrico, lo que respalda la estabilidad de la estimación.

### 7. Diferencias entre sucursales

El ANOVA de una vía contrasta la igualdad del monto promedio por línea de venta entre las cuatro sucursales:

\[
F=18,101,\qquad p\approx1,03\times10^{-11}
\]

La igualdad de medias se rechaza al nivel \(\alpha=0,05\). Escazú presenta la diferencia más clara: alrededor de **₡2.425** por línea frente a **₡2.220** en Heredia.

Aun así, el modelo basado solo en sucursal tiene **R² = 0,0045**, por lo que la sucursal explica menos del 1 % de la variación total del monto. La diferencia es estadísticamente clara, pero de relevancia práctica limitada frente a otros factores.

### 8. Impacto de las promociones

| Grupo | Unidades promedio | n |
|---|---:|---:|
| Sin promoción | 1,267 | 8.033 |
| Con promoción | 1,765 | 3.950 |

La promoción aumenta las unidades observadas en aproximadamente **39,3 %**.

Resultados de la comparación:

- **t de Welch:** 34,61;
- **p-value:** extremadamente inferior a 0,001;
- **d de Cohen:** 0,702;
- **efecto estimado:** aproximadamente +0,498 unidades por línea.

Por tipo de promoción:

| Promoción | Unidades promedio |
|---|---:|
| 2x1 en bebidas | 1,779 |
| Combo postre | 1,765 |
| Descuento del 10 % | 1,751 |
| Sin promoción | 1,267 |

La diferencia importante está entre **promocionar y no promocionar**. Los tres mecanismos promocionales presentan resultados muy cercanos, por lo que conviene evaluar también su costo operativo antes de escoger uno.

La asignación de promociones no fue aleatoria, por lo que este análisis debe interpretarse como **cuasiexperimental**.

### 9. Clima, asociación y causalidad

La composición de ventas cambia según el clima. La bebida caliente representa aproximadamente:

- **41,9 %** de las transacciones en días lluviosos;
- **31,3 %** en días nublados;
- **29,9 %** en días soleados.

La asociación entre clima y categoría es estadísticamente detectable:

\[
\chi^2=183,40,\qquad gl=6,\qquad p=6,42\times10^{-37}
\]

Sin embargo, **V de Cramér = 0,0875**, lo que indica una asociación débil. Además, el volumen total de unidades cambia poco entre climas.

Variables como la hora del día, la estacionalidad y el perfil de cada sucursal pueden actuar como confusoras. Por ello, los datos permiten hablar de **asociación**, no de causalidad.

### 10. Regresión

El modelo lineal múltiple utiliza las unidades como variable dependiente y combina precio, promoción, hora, clima, sucursal y categoría como predictores.

Resultados globales:

- **R² del modelo:** 0,110;
- **R² de validación:** 0,101;
- **promoción activa:** \(\beta \approx 0,496\), p < 0,001;
- **precio unitario:** efecto no distinguible de cero al 5 %;
- **hora:** efecto no distinguible de cero al 5 %;
- **clima:** coeficientes no distinguibles de cero al 5 % dentro del modelo.

La promoción es, con amplia diferencia, el predictor de mayor peso entre las variables incluidas. El modelo explica cerca del 11 % de la variabilidad, por lo que resulta más apropiado como **guía direccional** que como pronóstico puntual.

Como verificación de robustez, se ajusta además una regresión de Poisson para tratar `unidades` como variable de conteo; el orden general de importancia de los predictores se conserva.

## Síntesis de decisiones para la gerencia

| Evidencia | Implicación |
|---|---|
| La promoción presenta el efecto más grande y consistente del análisis. | Mantener la estrategia promocional y simplificar el mecanismo según costo y facilidad operativa. |
| La demanda tiene picos claros por hora. | Dimensionar personal y preparación por franja horaria, no por un promedio diario. |
| La satisfacción tiene 71,22 % de datos faltantes. | Rediseñar la captura con muestreo activo y selección aleatoria de clientes por turno. |
| Escazú se separa estadísticamente del resto. | Auditar su mezcla de producto, clientela y operación para identificar prácticas replicables. |
| El postre en la primera visita se asocia con mayor recurrencia. | Utilizarlo como señal para segmentación y seguimiento, sin atribuir causalidad. |
| El clima cambia la mezcla de categorías, pero no explica claramente el volumen. | Usarlo para preparación de surtido, no como palanca causal de demanda. |

## Limitaciones

1. **Ventana temporal corta:** el dataset cubre únicamente marzo–mayo de 2026 y no permite separar completamente estacionalidad de patrones estructurales.
2. **Promociones no aleatorias:** la activación fue decidida por la cadena, de modo que pueden existir factores de confusión en la comparación tratamiento-control.
3. **Poder explicativo limitado:** el modelo lineal explica cerca del 11 % de la variación de unidades; quedan variables relevantes fuera del dataset.
4. **Ausencia de costos y márgenes:** el análisis estudia facturación y volumen, no rentabilidad. Una promoción puede aumentar unidades y al mismo tiempo reducir margen.
5. **Datos incompletos de satisfacción:** la alta no respuesta impide tratar la media observada como representativa de toda la clientela.

## Requisitos originales del proyecto final

Las instrucciones académicas establecen que el reporte debe integrar los **diez sellos** sobre el mismo caso. Para que cada sello cuente como completo debe incluir:

- respuesta a la pregunta de negocio;
- cálculo reproducible;
- al menos un gráfico o tabla;
- conclusión de 2 a 4 líneas en lenguaje de negocio;
- interpretación contextual, no únicamente código o resultados numéricos.

### Checklist por sello

#### Sello 1 — Descriptiva y visualización

- Media, mediana y desviación estándar de `precio_unitario` y `unidades`, por sucursal y categoría.
- Al menos dos gráficos.
- Identificación del producto y categoría estrella a partir de los datos.

#### Sello 2 — Probabilidad condicional

- Cálculo de \(P(postre)\).
- Cálculo de \(P(postre\mid bebida\ caliente)\) dentro del mismo `id_pedido`.
- Tabla de contingencia o desarrollo paso a paso.
- Conclusión sobre la conveniencia de un combo bebida + postre.

#### Sello 3 — Teorema de Bayes

- Definición explícita de los eventos A y B.
- Fórmula de Bayes con cada término mostrado.
- Comparación de la probabilidad antes y después de conocer la evidencia.

#### Sello 4 — Distribuciones

- Conteo de pedidos por fecha y hora.
- Ajuste de Poisson o Binomial con justificación.
- Comparación de la distribución teórica con los datos observados mediante gráfico.

#### Sello 5 — Muestreo y sesgos

- Porcentaje de datos faltantes en `calificacion_satisfaccion`.
- Comparación de quienes respondieron y quienes no por variables observables.
- Identificación del tipo de sesgo y del riesgo de ignorarlo.

#### Sello 6 — Intervalos de confianza

- IC del 95 % del ticket global y por sucursal.
- Explicación del método seleccionado.
- Traducción del intervalo a lenguaje gerencial.

#### Sello 7 — Prueba de hipótesis

- Planteamiento explícito de \(H_0\) y \(H_1\).
- Elección y justificación de t-test o ANOVA.
- Estadístico, p-value, nivel de significancia y decisión.

#### Sello 8 — A/B Testing

- Comparación de `promocion_activa = 1` contra `promocion_activa = 0`.
- Prueba de hipótesis para la diferencia.
- Tamaño del efecto.
- Recomendación sobre mantener o no la promoción.

#### Sello 9 — Correlación vs. causalidad

- Relación entre `clima` y `categoria` o ventas.
- Al menos una variable confusora explicada.
- Separación explícita entre lo que los datos permiten afirmar y lo que no permiten concluir causalmente.

#### Sello 10 — Regresión

- `unidades` o monto como variable dependiente.
- Al menos tres predictores entre precio, promoción, clima, hora y sucursal.
- Coeficientes y R².
- Interpretación de al menos dos coeficientes en lenguaje de negocio.

## Entregables

Las instrucciones del proyecto solicitan:

| Entregable | Formato | Contenido |
|---|---|---|
| Reporte ejecutivo | PDF o Word; entrega final indicada en PDF | Narrativa integrada de los diez sellos, hallazgos, gráficos clave y recomendación de negocio. |
| Cuaderno de trabajo | `.ipynb`, enlace de Colab, Excel o R según la herramienta usada | Cálculos, pruebas, modelos y resultados reproducibles. |

Para este proyecto, el cuaderno se desarrolló en **Python/Jupyter** y el reporte ejecutivo se encuentra en **PDF**.

## Rúbrica resumida

| Criterio | Nivel excelente esperado |
|---|---|
| Análisis estadístico | Riguroso y bien fundamentado. |
| Interpretación | Precisa y conectada con el contexto real del negocio. |
| Herramientas | Uso correcto de Python y de las técnicas estadísticas. |
| Visualización | Clara, pertinente y bien etiquetada. |
| Conclusiones y decisión | Claras, justificadas y orientadas al negocio. |
| Presentación y documentación | Profesional, ordenada y completa. |

## Reproducibilidad

El notebook está diseñado para ejecutarse en orden y reproducir los resultados del reporte desde la carga del CSV hasta el modelo final. El nivel de significancia general utilizado es:

\[
\alpha=0,05
\]

y, salvo indicación contraria, los intervalos se presentan al **95 % de confianza**.

Para obtener los mismos resultados:

- no modifique manualmente el CSV antes de cargarlo;
- ejecute el setup antes de cualquier sello;
- ejecute las celdas de arriba hacia abajo;
- conserve la misma unidad de análisis requerida en cada fase: línea de venta, pedido o cliente según corresponda.

## Autores

- Luciana Carabaguiaz
- Diego Díaz
- Julián Maroto
- Santiago Volio

---

**Proyecto académico — LEAD University · Probabilidad y Estadística I · 2026**
