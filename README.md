# Proyecto Final Integrador — Café Cordillera

**TCNT0011 · Probabilidad y Estadística I · LEAD University**

Análisis integral del desempeño comercial de **Café Cordillera**, una cadena costarricense de cafeterías con sucursales en Cartago, Escazú, Heredia y San Pedro.

El proyecto utiliza un único conjunto de datos para aplicar las diez técnicas principales del curso, desde estadística descriptiva hasta regresión múltiple, con el objetivo de transformar los resultados estadísticos en información útil para la toma de decisiones gerenciales.

> **Pregunta de investigación:** ¿Qué decisiones de operación, surtido y promoción debe tomar la gerencia de Café Cordillera con base en la evidencia estadística de sus 11.983 transacciones registradas entre marzo y mayo de 2026?

---

## Información académica

| Campo | Detalle |
|---|---|
| Curso | TCNT0011 · Probabilidad y Estadística I |
| Universidad | LEAD University |
| Docente | Bernal Rojas Villalobos |
| Proyecto | Proyecto Final Integrador — Café Cordillera |
| Fecha de entrega | 21 de agosto de 2026 |
| Valor | 50 puntos |
| Integrantes | Luciana Carabaguiaz, Diego Díaz, Julián Maroto y Santiago Volio |

---

## Objetivo del proyecto

El objetivo principal es analizar el comportamiento comercial de Café Cordillera y responder preguntas relevantes para la gerencia mediante herramientas de probabilidad y estadística.

Todo el análisis se desarrolla sobre el mismo conjunto de datos. Cada técnica estadística responde a una pregunta concreta del negocio y termina con una interpretación práctica.

El proyecto analiza principalmente:

- desempeño por sucursal;
- desempeño por categoría y producto;
- comportamiento conjunto de compra;
- recurrencia de clientes;
- llegada de pedidos por hora;
- calidad de los datos de satisfacción;
- estimación del ticket promedio;
- diferencias entre sucursales;
- impacto de las promociones;
- relación entre clima y comportamiento de compra;
- predicción de unidades vendidas.

---

## Estructura del proyecto

La estructura del repositorio es la siguiente:

```text
main/
├── data/
│   └── cafe_cordillera_dataset.csv
│
├── instrucciones.html
├── notebook proyecto final cafe cordillera.ipynb
├── REPORTE EJECUTIVO.pdf
├── REPORTE EJECUTIVO.docx
└── README.md
```

### Descripción de los archivos

| Archivo | Descripción |
|---|---|
| `data/cafe_cordillera_dataset.csv` | Dataset original utilizado para todos los análisis estadísticos del proyecto. |
| `instrucciones.html` | Documento HTML con las instrucciones originales del Proyecto Final Integrador, incluyendo los diez sellos, requisitos mínimos, entregables, rúbrica y logística de entrega. |
| `notebook proyecto final cafe cordillera.ipynb` | Notebook de Python con los diez sellos, cálculos, pruebas estadísticas, modelos, gráficos e interpretaciones. |
| `REPORTE EJECUTIVO.pdf` | Versión final en PDF del reporte ejecutivo dirigido a la gerencia de Café Cordillera. |
| `REPORTE EJECUTIVO.docx` | Versión editable en Microsoft Word del reporte ejecutivo. |
| `README.md` | Documentación general del repositorio, incluyendo estructura, metodología, resultados e instrucciones de ejecución. |

---

## Instrucciones originales del proyecto

El archivo:

```text
instrucciones.html
```

contiene las instrucciones originales proporcionadas para el Proyecto Final Integrador.

Puede abrirse directamente en cualquier navegador web.

El documento incluye:

- descripción del caso Café Cordillera;
- estructura de los diez sellos;
- preguntas de negocio de cada fase;
- requisitos mínimos de cada análisis;
- entregables;
- rúbrica resumida;
- fecha y formato de entrega.

El HTML funciona como **documento de referencia con las instrucciones del proyecto**. Los análisis y resultados se encuentran desarrollados en el notebook y en el reporte ejecutivo.

---

## Ruta del dataset

El dataset se encuentra dentro de la carpeta:

```text
data/
```

Por lo tanto, desde la raíz del proyecto (`main`) la ruta relativa es:

```text
data/cafe_cordillera_dataset.csv
```

En Python puede cargarse de la siguiente manera:

```python
import pandas as pd

DATA_PATH = "data/cafe_cordillera_dataset.csv"

df = pd.read_csv(DATA_PATH, parse_dates=["fecha"])
```

Durante el análisis también se crea la variable `monto`:

```python
df["monto"] = df["precio_unitario"] * df["unidades"]
```

---

## Dataset

El archivo:

```text
data/cafe_cordillera_dataset.csv
```

contiene **11.983 líneas de venta**, agrupadas en **7.731 pedidos** realizados por **2.600 clientes distintos**.

### Dimensiones principales

| Característica | Valor |
|---|---:|
| Líneas de venta | 11.983 |
| Pedidos únicos | 7.731 |
| Clientes únicos | 2.600 |
| Sucursales | 4 |
| Período analizado | 2 de marzo al 31 de mayo de 2026 |
| Horario registrado | 6:00 a 19:00 |
| Calificaciones de satisfacción disponibles | 3.449 |
| Calificaciones de satisfacción faltantes | 71,22 % |

Las cuatro sucursales analizadas son:

- Cartago
- Escazú
- Heredia
- San Pedro

---

## Variables del dataset

El dataset original contiene las siguientes variables:

| Variable | Descripción |
|---|---|
| `id_transaccion` | Identificador único de cada línea de venta. |
| `id_pedido` | Identificador del pedido al que pertenece la transacción. |
| `id_cliente` | Identificador del cliente. |
| `fecha` | Fecha de la transacción. |
| `hora` | Hora de la transacción. |
| `sucursal` | Sucursal donde se realizó la compra. |
| `producto` | Producto vendido. |
| `categoria` | Categoría del producto. |
| `precio_unitario` | Precio unitario del producto en colones costarricenses. |
| `unidades` | Cantidad de unidades vendidas. |
| `medio_pago` | Medio utilizado para realizar el pago. |
| `clima` | Condición climática registrada. |
| `promocion_activa` | Indica si existía una promoción activa. |
| `promocion_tipo` | Tipo de promoción utilizada. |
| `calificacion_satisfaccion` | Calificación de satisfacción del cliente cuando está disponible. |

Durante el análisis también se crea:

```python
df["monto"] = df["precio_unitario"] * df["unidades"]
```

Esta variable representa el monto correspondiente a cada línea de venta.

Para calcular el **ticket de un pedido**, se agrupan todas las líneas pertenecientes al mismo `id_pedido`.

---

## Tecnologías utilizadas

El proyecto fue desarrollado principalmente en **Python 3** utilizando un notebook de Jupyter.

Puede ejecutarse en:

- Google Colab;
- Jupyter Notebook;
- JupyterLab;
- Visual Studio Code con soporte para notebooks.

### Librerías principales

```text
numpy
pandas
matplotlib
seaborn
scipy
statsmodels
scikit-learn
```

Para instalar las dependencias en un entorno local:

```bash
pip install numpy pandas matplotlib seaborn scipy statsmodels scikit-learn
```

---

## Cómo ejecutar el proyecto

### 1. Clonar o descargar el repositorio

La carpeta principal debe conservar la siguiente estructura:

```text
main/
├── data/
│   └── cafe_cordillera_dataset.csv
├── instrucciones.html
├── notebook proyecto final cafe cordillera.ipynb
├── REPORTE EJECUTIVO.pdf
├── REPORTE EJECUTIVO.docx
└── README.md
```

### 2. Verificar la ubicación del dataset

El archivo debe encontrarse en:

```text
main/data/cafe_cordillera_dataset.csv
```

Si el notebook se ejecuta desde la carpeta `main`, la ruta relativa es:

```python
DATA_PATH = "data/cafe_cordillera_dataset.csv"
```

### 3. Abrir el notebook

Abrir:

```text
notebook proyecto final cafe cordillera.ipynb
```

utilizando Jupyter Notebook, JupyterLab, Visual Studio Code o Google Colab.

### 4. Cargar el dataset

El setup puede utilizar:

```python
import os
import pandas as pd

DATA_PATH = "data/cafe_cordillera_dataset.csv"

if not os.path.exists(DATA_PATH):
    raise FileNotFoundError(
        "No se encontró el archivo data/cafe_cordillera_dataset.csv."
    )

df = pd.read_csv(DATA_PATH, parse_dates=["fecha"])

df["monto"] = df["precio_unitario"] * df["unidades"]
```

### 5. Ejecutar las celdas en orden

El notebook debe ejecutarse desde el inicio hasta el final.

El bloque de setup:

1. importa las librerías;
2. carga el dataset;
3. convierte `fecha` al formato correspondiente;
4. crea la variable `monto`;
5. deja disponible el DataFrame `df`.

Los diez sellos reutilizan posteriormente el mismo DataFrame.

---

# Metodología

El proyecto está organizado alrededor de **diez sellos**, correspondientes a las principales herramientas estadísticas estudiadas durante el curso.

| Sello | Técnica | Pregunta de negocio |
|---:|---|---|
| 1 | Descriptiva y visualización | ¿Qué se vende, dónde y cuánto factura Café Cordillera? |
| 2 | Probabilidad condicional | ¿Comprar bebida caliente aumenta la probabilidad de comprar postre? |
| 3 | Teorema de Bayes | Si un cliente compró postre en su primera visita, ¿qué tan probable es que vuelva? |
| 4 | Distribuciones | ¿Cuántos pedidos puede esperar una sucursal en una hora determinada? |
| 5 | Muestreo y sesgos | ¿La calificación de satisfacción representa a todos los clientes? |
| 6 | Intervalos de confianza | ¿Cuál es el ticket promedio y con qué margen de error? |
| 7 | Prueba de hipótesis | ¿Una sucursal vende realmente más que otra? |
| 8 | A/B Testing | ¿La promoción activa aumenta las unidades vendidas? |
| 9 | Correlación vs. causalidad | ¿El clima causa cambios en el comportamiento de compra? |
| 10 | Regresión | ¿Qué variables predicen mejor las unidades vendidas? |

---

# Sello 1 — Estadística descriptiva y visualización

## Pregunta de negocio

**¿Qué se vende, dónde y cuánto factura Café Cordillera?**

Se analizan:

- media;
- mediana;
- desviación estándar;
- precio unitario;
- unidades;
- sucursal;
- categoría;
- producto.

También se utilizan visualizaciones para analizar la facturación por sucursal, categoría y producto.

## Principales resultados

La sucursal con mayor facturación es:

```text
Escazú: ₡7.295.509
```

Cartago registra:

```text
₡6.616.884
```

La diferencia entre ambas es cercana al **10,3 %**.

La categoría con mayor facturación es:

```text
Bebida fría: ₡11.855.048
```

El producto con mayor facturación es:

```text
Frappe: ₡4.733.463
```

Los tres primeros productos del ranking pertenecen a la categoría de bebidas frías.

Escazú presenta además:

- el precio unitario promedio más alto;
- la menor cantidad media de unidades por transacción.

Este comportamiento refleja un perfil de compra orientado hacia productos de mayor precio.

---

# Sello 2 — Probabilidad condicional

## Pregunta de negocio

**¿Comprar una bebida caliente aumenta la probabilidad de comprar postre en el mismo pedido?**

El análisis se realiza a nivel de `id_pedido`.

Primero se calcula:

\[
P(\text{postre})
\]

y posteriormente:

\[
P(\text{postre}\mid\text{bebida caliente})
\]

## Resultados

La probabilidad general de que un pedido incluya postre es:

\[
P(\text{postre})=20,88\%
\]

Cuando el pedido contiene una bebida caliente:

\[
P(\text{postre}\mid\text{bebida caliente})=19,80\%
\]

La diferencia es aproximadamente:

\[
-1,07
\]

puntos porcentuales.

## Interpretación

El comportamiento observado no presenta una asociación positiva entre comprar una bebida caliente y agregar un postre.

Los datos históricos no respaldan por sí solos la creación de un combo bebida caliente + postre.

---

# Sello 3 — Teorema de Bayes

## Pregunta de negocio

**Si un cliente compró postre en su primera visita, ¿qué tan probable es que vuelva?**

Se definen los eventos:

- **A:** el cliente es recurrente;
- **B:** la primera compra del cliente incluyó al menos un postre.

Un cliente recurrente se define como aquel que realizó más de un pedido durante el período.

## Probabilidades

\[
P(A)=43,12\%
\]

\[
P(B)=16,73\%
\]

\[
P(B\mid A)=23,19\%
\]

Aplicando Bayes:

\[
P(A\mid B)
=
\frac{P(B\mid A)P(A)}{P(B)}
\]

\[
P(A\mid B)
=
\frac{0,2319\times0,4312}{0,1673}
\]

\[
P(A\mid B)=59,77\%
\]

## Interpretación

La probabilidad general de recurrencia es de **43,12 %**.

Cuando se conoce que el cliente compró un postre en su primera visita, la probabilidad aumenta hasta **59,77 %**.

El incremento corresponde a **16,65 puntos porcentuales**.

Este resultado identifica al postre como una posible **señal de fidelización**, pero no demuestra que comprar un postre cause que el cliente vuelva.

---

# Sello 4 — Distribuciones de probabilidad

## Pregunta de negocio

**¿Cuántos pedidos puede esperar una sucursal en una hora determinada?**

Para este análisis se cuentan los pedidos por:

- sucursal;
- fecha;
- hora.

También se incorporan las horas en las que no hubo pedidos para evitar sobreestimar la tasa de llegada.

## Distribución utilizada

Se utiliza una **distribución de Poisson**.

La elección se analiza mediante el índice de dispersión:

\[
\frac{\text{Varianza}}{\text{Media}}
\]

Al calcularlo dentro de cada combinación de sucursal y hora, el promedio es aproximadamente:

\[
0,989
\]

## Patrón horario

El comportamiento muestra dos períodos principales de demanda.

### Pico matutino

```text
7:00 – 9:00
```

### Pico vespertino

```text
16:00 – 18:00
```

Los períodos de menor actividad aparecen alrededor de:

```text
11:00
15:00
```

## Ejemplo operativo

Para Escazú a las 17:00:

\[
\lambda=2,077
\]

El percentil 95 corresponde aproximadamente a:

```text
5 pedidos
```

Este valor puede utilizarse como referencia para dimensionar la capacidad operativa de esa franja.

---

# Sello 5 — Muestreo y sesgos

## Pregunta de negocio

**¿La calificación de satisfacción disponible representa correctamente a todos los clientes?**

La variable analizada es:

```text
calificacion_satisfaccion
```

## Datos faltantes

De las **11.983** líneas de venta:

```text
8.534
```

no contienen una calificación.

Esto representa:

\[
71,22\%
\]

de datos faltantes.

Únicamente:

```text
3.449 registros
```

contienen una respuesta.

## Media observada

La calificación media entre quienes respondieron es:

\[
3,752
\]

Esta cifra no debe considerarse automáticamente como la satisfacción promedio de toda la clientela.

## Análisis de sesgo

Se compara la tasa de respuesta según:

- hora;
- sucursal;
- clima;
- promoción;
- categoría;
- día de la semana;
- medio de pago.

Ninguna de estas variables muestra una relación estadísticamente significativa con la respuesta al nivel:

\[
\alpha=0,05
\]

Esto no elimina el posible **sesgo de no respuesta o autoselección**, debido a que la satisfacción de quienes no respondieron es desconocida.

## Análisis de sensibilidad

Media observada:

\[
3,752
\]

Si quienes no respondieron hubieran otorgado en promedio medio punto menos:

\[
3,396
\]

Si hubieran otorgado un punto menos:

\[
3,040
\]

## Recomendación

Implementar un sistema de **muestreo activo**, seleccionando aleatoriamente una cantidad fija de clientes por turno para solicitar una evaluación.

---

# Sello 6 — Intervalos de confianza

## Pregunta de negocio

**¿Cuál es el ticket promedio de Café Cordillera y con qué margen de error puede estimarse?**

El ticket se calcula agrupando todas las líneas correspondientes al mismo `id_pedido`.

## Resultados globales

Número de pedidos:

\[
n=7.731
\]

Ticket promedio:

\[
₡3.534,3
\]

Desviación estándar:

\[
₡2.302,5
\]

Intervalo de confianza del 95 %:

\[
[₡3.483,0;\ ₡3.585,6]
\]

Margen de error:

\[
\pm ₡51,3
\]

## Interpretación

Bajo condiciones comparables, el análisis estima que el ticket promedio de la cadena se encuentra aproximadamente entre:

```text
₡3.483 y ₡3.586
```

con un nivel de confianza del 95 %.

También se utiliza bootstrap con **5.000 remuestreos** como comprobación adicional.

---

# Sello 7 — Prueba de hipótesis

## Pregunta de negocio

**¿Una sucursal vende realmente más que las demás o las diferencias pueden atribuirse al azar?**

Se plantea:

### Hipótesis nula

\[
H_0:
\mu_{Cartago}
=
\mu_{Escazú}
=
\mu_{Heredia}
=
\mu_{SanPedro}
\]

### Hipótesis alternativa

\[
H_1:
\text{al menos una media es diferente}
\]

Se utiliza un **ANOVA de una vía** debido a que existen cuatro grupos independientes.

## Resultado

\[
F=18,101
\]

\[
p=1,03\times10^{-11}
\]

Con:

\[
\alpha=0,05
\]

se rechaza la hipótesis nula.

## Escazú

El análisis posterior identifica a Escazú como la principal fuente de diferencia.

Comparando Escazú con Heredia:

\[
t=6,241
\]

\[
p=4,64\times10^{-10}
\]

La diferencia observada es aproximadamente:

```text
₡205,44 por transacción
```

Sin embargo:

\[
R^2=0,0045
\]

La sucursal explica menos del 1 % de la variabilidad total del monto.

## Interpretación

Las diferencias entre sucursales son estadísticamente detectables, pero la sucursal por sí sola explica una proporción muy pequeña de la variación total de los tickets.

---

# Sello 8 — A/B Testing

## Pregunta de negocio

**¿La promoción activa realmente aumenta las ventas?**

Se comparan dos grupos.

### Grupo de control

```text
promocion_activa = 0
```

### Grupo de tratamiento

```text
promocion_activa = 1
```

La variable de resultado utilizada es:

```text
unidades
```

## Resultados

### Sin promoción

```text
n = 8.033
media = 1,267 unidades
```

### Con promoción

```text
n = 3.950
media = 1,765 unidades
```

El incremento relativo es aproximadamente:

\[
39,3\%
\]

La prueba t de Welch produce:

\[
t=34,61
\]

El tamaño del efecto es:

\[
d=0,702
\]

## Tipos de promoción

| Tipo de promoción | Unidades promedio | n |
|---|---:|---:|
| 2x1 en bebidas | 1,779 | 1.264 |
| Combo postre | 1,765 | 1.194 |
| Descuento del 10 % | 1,751 | 1.492 |
| Sin promoción | 1,267 | 8.033 |

## Interpretación

La principal diferencia se encuentra entre **tener una promoción activa** y **no tener promoción**.

Las tres promociones muestran resultados muy similares.

La asignación histórica de promociones no fue aleatoria, por lo que el análisis debe interpretarse como **cuasiexperimental**.

---

# Sello 9 — Correlación y causalidad

## Pregunta de negocio

**¿El clima causa que se venda más bebida caliente?**

Se estudia la relación entre:

```text
clima
```

y:

```text
categoria
```

## Bebidas calientes según clima

En días lluviosos representan aproximadamente:

\[
41,9\%
\]

de las transacciones.

En días nublados:

\[
31,3\%
\]

En días soleados:

\[
29,9\%
\]

## Prueba chi-cuadrado

\[
\chi^2=183,40
\]

\[
gl=6
\]

\[
p=6,42\times10^{-37}
\]

Existe una asociación estadística entre clima y categoría.

Sin embargo:

\[
V\ de\ Cramér=0,0875
\]

La asociación tiene una intensidad débil.

## Variables confusoras

Entre los posibles factores que pueden explicar parte de la relación se encuentran:

- hora del día;
- estacionalidad;
- mes;
- perfil de cada sucursal;
- composición de la clientela.

## Interpretación

Los datos muestran una **asociación** entre clima y mezcla de productos.

No permiten establecer que el clima sea directamente la causa de los cambios observados.

El clima puede ayudar a anticipar la mezcla de productos que debe prepararse, pero no debe interpretarse como una causa comprobada del volumen total vendido.

---

# Sello 10 — Regresión

## Pregunta de negocio

**¿Qué variables predicen mejor las unidades vendidas?**

La variable dependiente es:

```text
unidades
```

Entre los predictores utilizados se encuentran:

- precio unitario;
- promoción activa;
- hora;
- clima;
- sucursal;
- categoría.

## Modelo

Se utiliza una regresión lineal múltiple.

Resultado global:

\[
R^2\approx0,110
\]

En validación:

\[
R^2\approx0,101
\]

## Principales coeficientes

### Promoción activa

\[
\beta\approx0,496
\]

\[
p<0,001
\]

Manteniendo constantes las demás variables, una promoción activa se asocia con aproximadamente:

```text
0,5 unidades adicionales por transacción
```

### Precio unitario

\[
\beta\approx-0,0000232
\]

\[
p=0,282
\]

El precio no presenta un efecto estadísticamente distinguible de cero dentro del rango observado.

### Hora

\[
p=0,548
\]

No muestra un efecto estadísticamente significativo dentro del modelo.

### Clima

Los coeficientes asociados con el clima tampoco son estadísticamente significativos dentro del modelo multivariable.

## Interpretación

La variable de mayor importancia entre las disponibles es:

```text
promoción activa
```

El modelo explica aproximadamente el:

\[
11\%
\]

de la variabilidad en las unidades.

Esto implica que aproximadamente el:

\[
89\%
\]

de la variación depende de factores que no están capturados por las variables incluidas.

Por esa razón, el modelo debe interpretarse principalmente como una herramienta de **dirección e interpretación**, no como un sistema de pronóstico exacto.

También se utiliza una regresión de Poisson como análisis de robustez debido a que `unidades` es una variable de conteo.

---

# Hallazgos principales

El análisis completo permite destacar cinco hallazgos principales:

1. **Las promociones presentan el efecto más fuerte y consistente sobre las unidades vendidas.**

2. **Escazú presenta un comportamiento comercial estadísticamente diferente**, aunque la sucursal explica una fracción muy pequeña de la variabilidad total.

3. **Las bebidas frías concentran la mayor facturación**, con el Frappe como producto estrella.

4. **Comprar postre durante la primera visita se asocia con una mayor probabilidad de recurrencia**, aunque no se puede establecer una relación causal.

5. **La encuesta de satisfacción presenta una debilidad importante**, debido a que el 71,22 % de los registros no contienen una calificación.

---

# Recomendaciones para la gerencia

## 1. Mantener las promociones

Las promociones presentan la evidencia estadística más fuerte del análisis.

Como los tres mecanismos muestran resultados muy similares, puede priorizarse aquel que tenga:

- menor costo;
- menor complejidad;
- mejor margen;
- mayor facilidad operativa.

---

## 2. Ajustar el personal según la hora

La demanda no se distribuye uniformemente durante el día.

Los principales picos se encuentran entre:

```text
7:00 – 9:00
16:00 – 18:00
```

La planificación de personal debería considerar estas franjas y no solamente un promedio diario.

---

## 3. Rediseñar la medición de satisfacción

Con:

\[
71,22\%
\]

de datos faltantes, la calificación promedio observada no puede utilizarse como representación segura de toda la clientela.

Se recomienda implementar un muestreo activo y aleatorio por turno.

---

## 4. Analizar la operación de Escazú

Escazú presenta:

- mayor precio unitario promedio;
- ticket superior;
- menor número promedio de unidades;
- diferencias estadísticamente detectables frente a las demás sucursales.

Conviene investigar elementos relacionados con:

- mezcla de productos;
- perfil de clientes;
- estrategia comercial;
- operación.

---

# Limitaciones

## Ventana temporal limitada

El dataset cubre únicamente:

```text
marzo – mayo de 2026
```

Tres meses no permiten observar completamente la estacionalidad anual.

---

## Promociones no asignadas aleatoriamente

La empresa decidió cuándo activar cada promoción.

Por lo tanto, pueden existir factores adicionales asociados con los períodos promocionales.

---

## Poder explicativo limitado

La regresión explica aproximadamente:

\[
11\%
\]

de la variación en unidades.

Variables que no aparecen en el dataset podrían incluir:

- cantidad de personas en el local;
- personal disponible;
- tiempos de espera;
- inventario;
- margen por producto;
- eventos especiales;
- características individuales de los clientes.

---

## Ausencia de costos

El dataset contiene información de ventas, pero no información de costos o márgenes.

Por esta razón, no puede determinarse directamente cuál estrategia maximiza la rentabilidad.

Una promoción puede aumentar las unidades vendidas y simultáneamente reducir el margen.

---

## Datos incompletos de satisfacción

El:

\[
71,22\%
\]

de los registros carece de una calificación de satisfacción.

Esto limita cualquier conclusión general sobre esta variable.

---

# Requisitos originales del proyecto

Los requisitos completos pueden consultarse directamente en:

```text
instrucciones.html
```

El proyecto establece que los diez sellos deben formar parte de un único análisis.

Cada sello debe incluir como mínimo:

- una pregunta de negocio;
- un cálculo reproducible;
- al menos un gráfico o tabla;
- interpretación del resultado;
- conclusión en lenguaje de negocio.

---

# Checklist de los diez sellos

## Sello 1 — Descriptiva y visualización

- Media, mediana y desviación estándar de `precio_unitario`.
- Media, mediana y desviación estándar de `unidades`.
- Análisis por sucursal.
- Análisis por categoría.
- Al menos dos gráficos.
- Identificación del producto estrella.
- Identificación de la categoría estrella.

## Sello 2 — Probabilidad condicional

- Calcular \(P(postre)\).
- Calcular \(P(postre\mid bebida\ caliente)\).
- Trabajar a nivel de `id_pedido`.
- Mostrar tabla de contingencia o cálculo.
- Interpretar si conviene un combo.

## Sello 3 — Bayes

- Definir evento A.
- Definir evento B.
- Mostrar la fórmula de Bayes.
- Mostrar cada término.
- Comparar la probabilidad inicial con la posterior.

## Sello 4 — Distribuciones

- Contar pedidos por hora y fecha.
- Seleccionar Poisson o Binomial.
- Justificar la distribución elegida.
- Comparar la teoría con los datos observados.
- Incluir visualización.

## Sello 5 — Muestreo y sesgos

- Calcular porcentaje de datos faltantes.
- Comparar quienes respondieron y quienes no.
- Analizar variables observables.
- Identificar el posible sesgo.
- Explicar el riesgo de ignorarlo.

## Sello 6 — Intervalos de confianza

- Calcular el ticket.
- IC del 95 % global.
- IC del 95 % por sucursal.
- Explicar el método utilizado.
- Interpretar el intervalo en lenguaje de negocio.

## Sello 7 — Prueba de hipótesis

- Definir \(H_0\).
- Definir \(H_1\).
- Elegir una prueba apropiada.
- Reportar estadístico.
- Reportar p-value.
- Definir \(\alpha\).
- Tomar una decisión estadística.
- Interpretar el resultado.

## Sello 8 — A/B Testing

- Comparar promoción activa contra ausencia de promoción.
- Definir control y tratamiento.
- Aplicar una prueba de hipótesis.
- Calcular tamaño del efecto.
- Interpretar los resultados.
- Proponer una recomendación.

## Sello 9 — Correlación vs. causalidad

- Analizar la relación entre clima y categoría o ventas.
- Medir la asociación.
- Identificar variables confusoras.
- Diferenciar correlación de causalidad.
- Explicar qué puede afirmarse.
- Explicar qué no puede afirmarse.

## Sello 10 — Regresión

- Utilizar `unidades` o monto como variable dependiente.
- Incorporar al menos tres predictores.
- Reportar coeficientes.
- Reportar R².
- Interpretar al menos dos coeficientes.
- Evaluar el desempeño del modelo.

---

# Entregables

Las instrucciones completas de entrega pueden consultarse en:

```text
instrucciones.html
```

El proyecto contiene dos entregables principales: el reporte ejecutivo y el cuaderno de cálculo.

## Reporte ejecutivo

El reporte resume las diez fases del análisis mediante:

- metodología;
- análisis estadístico;
- hallazgos principales;
- gráficos y tablas;
- interpretación en contexto de negocio;
- recomendaciones para la gerencia;
- limitaciones;
- conclusiones.

El reporte se encuentra disponible en dos formatos:

```text
REPORTE EJECUTIVO.pdf
REPORTE EJECUTIVO.docx
```

`REPORTE EJECUTIVO.pdf` corresponde a la versión final del documento.

`REPORTE EJECUTIVO.docx` corresponde a la versión editable en Microsoft Word.

## Cuaderno de cálculo

Todos los cálculos, pruebas estadísticas y modelos utilizados en el proyecto se encuentran en:

```text
notebook proyecto final cafe cordillera.ipynb
```

El notebook permite reproducir los análisis utilizando el dataset ubicado en:

```text
data/cafe_cordillera_dataset.csv
```

---

# Rúbrica resumida

| Criterio | Nivel excelente esperado |
|---|---|
| Análisis estadístico | Riguroso y bien fundamentado |
| Interpretación | Precisa y relacionada con el contexto real |
| Herramientas | Uso correcto de las herramientas estadísticas |
| Visualización | Clara y correctamente etiquetada |
| Conclusiones y decisión | Claras y orientadas al negocio |
| Presentación y documentación | Profesional y completa |

La versión original de la rúbrica puede consultarse en:

```text
instrucciones.html
```

---

# Reproducibilidad

El notebook está diseñado para que los análisis se ejecuten en orden a partir del mismo dataset.

El nivel de significancia utilizado, salvo indicación contraria, es:

\[
\alpha=0,05
\]

Los intervalos de confianza se reportan generalmente al:

\[
95\%
\]

Para reproducir correctamente los resultados:

1. conservar el dataset original sin modificaciones manuales;
2. mantener el archivo dentro de:

```text
data/cafe_cordillera_dataset.csv
```

3. ejecutar el notebook desde la raíz del proyecto;
4. ejecutar primero el setup;
5. ejecutar las celdas de arriba hacia abajo;
6. utilizar la unidad de análisis correspondiente para cada sello.

---

# Autores

- Luciana Carabaguiaz
- Diego Díaz
- Julián Maroto
- Santiago Volio

---

## Proyecto académico

**LEAD University**  
**TCNT0011 · Probabilidad y Estadística I**  
**Proyecto Final Integrador — Café Cordillera**  
**2026**
