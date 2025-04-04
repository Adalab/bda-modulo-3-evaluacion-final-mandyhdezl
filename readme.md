# Análisis de Datos del Programa de Lealtad de una Aerolínea

## Descripción de los Datos

El análisis se basa en dos conjuntos de datos:

1. **Customer Flight Analysis.csv**: Contiene información sobre la actividad de vuelo de los clientes, incluyendo número de vuelos reservados, distancia volada, puntos acumulados y redimidos, así como costos asociados a los puntos.
2. **Customer Loyalty History.csv**: Proporciona un perfil detallado de los clientes, incluyendo ubicación, nivel educativo, ingresos, estado civil y detalles de membresía en el programa de lealtad, como el tipo de tarjeta y valor del cliente.

---

## Fase 1: Exploración y Limpieza de Datos

### Exploración Inicial

Para comenzar, se realizó una exploración inicial de los datos utilizando la librería **pandas**, lo que permitió:

- Inspeccionar la estructura de los datos mediante `.info()` y `.describe()`.
- Identificar valores nulos y atípicos en columnas clave con `.isna().sum()` y visualización mediante **seaborn** con diagramas de caja (*boxplots*).
- Revisar la consistencia de los tipos de datos y realizar conversiones adecuadas (por ejemplo, transformar fechas con `pd.to_datetime`).

También se llevó a cabo la fusión de los dos conjuntos de datos usando `merge()`, asegurando que la combinación fuera eficiente y coherente.

### Limpieza de Datos

Se abordaron diversos problemas de calidad en los datos:

- **Valores nulos**: Se tomaron decisiones según el impacto en el análisis. En algunos casos, se imputaron valores usando estadísticas descriptivas (como la media para ingresos), mientras que en otros se eliminaron registros irrelevantes".
- **Duplicados**: Se identificaron y gestionaron duplicados en la columna *Loyalty Number*, dado que los clientes pueden aparecer varias veces debido a múltiples viajes.
- **Conversión de tipos de datos**: Se ajustaron formatos en fechas y valores numéricos para facilitar el análisis posterior.

---

## Fase 2: Visualización y Análisis de Preguntas Clave

Se utilizaron **matplotlib** y **seaborn** para generar visualizaciones que ayudaron a responder las preguntas de negocio.

### 1. Distribución de vuelos reservados por mes durante el año

- Se agruparon los datos por año y mes usando `groupby()` para obtener la cantidad de vuelos mensuales.
- Se emplearon gráficos de barras para identificar patrones estacionales en la demanda de vuelos.

### 2. Relación entre la distancia de los vuelos y los puntos acumulados

- Se analizó la correlación entre estas variables utilizando `.corr()`.
- Se graficó un *scatter plot* para visualizar la relación y se encontró una fuerte correlación positiva, lo que indica que a mayor distancia, más puntos se acumulan.

### 3. Distribución de los clientes por provincia o estado

- Se realizó un conteo de clientes por provincia utilizando `value_counts()`.
- Se utilizó un gráfico de barras para destacar las provincias con mayor cantidad de clientes, identificando que Ontario tiene la mayor proporción.

### 4. Comparación del salario promedio entre niveles educativos

- Se agruparon los datos por nivel educativo y se calculó el salario promedio.
- Se utilizó una visualización tipo *barplot* para mostrar las diferencias, evidenciando que el nivel "Doctor" tiene los ingresos más altos.

### 5. Proporción de clientes según tipo de tarjeta de fidelidad

- Se contó la cantidad de clientes únicos por tipo de tarjeta y se calculó su proporción en porcentaje.
- Un gráfico de barras mostró que la tarjeta *Star* es la más popular entre los clientes.

### 6. Distribución de clientes según estado civil y género

- Se utilizó `groupby()` para obtener la distribución de clientes combinando género y estado civil.
- Se encontró que los hombres y mujeres casados representan la mayor cantidad de clientes.

### 7. Análisis de cancelaciones

- Se identificó que el 65% de los datos en *Cancellation Year* y *Cancellation Month* eran nulos.
- Se evaluaron opciones: eliminar las columnas o reemplazar valores nulos con "Desconocido". Se optó por la segunda opción para conservar información relevante.

---

## Conclusiones

Este análisis permitió extraer información clave sobre el comportamiento de los clientes dentro del programa de lealtad de la aerolínea:

- **El mayor número de vuelos ocurrió en julio de 2018**, indicando un pico estacional en la actividad de los clientes.
- **Existe una fuerte correlación entre la distancia de vuelo y los puntos acumulados**, lo que confirma que los clientes ganan más puntos cuanto más lejos vuelan.
- **Ontario es la provincia con más clientes**, representando un mercado clave para la aerolínea.
- **El salario promedio más alto corresponde a clientes con doctorado**, lo que sugiere que este grupo puede tener un mayor poder adquisitivo.
- **La tarjeta de fidelidad *********Star********* tiene la mayor proporción de clientes**, lo que podría indicar que es la opción más accesible o popular entre los miembros del programa.
- **Los hombres y mujeres casados representan la mayor cantidad de clientes**, lo que podría tener implicaciones en estrategias de marketing y fidelización.

Este análisis proporciona información valiosa para mejorar la estrategia de retención de clientes y optimizar el programa de lealtad de la aerolínea.

