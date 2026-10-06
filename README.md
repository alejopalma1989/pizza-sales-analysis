# Plato's Pizza – Análisis de ventas 2015

Análisis de un año de ventas de una pizzería (≈21.000 pedidos) desde la perspectiva
de un General Manager: decisiones de personal, carta, ticket medio y estacionalidad.

## Preguntas de negocio
1. ¿Cuándo se concentra la demanda y cómo ajustar los turnos de personal?
2. ¿Qué pizzas son estrellas y cuáles sobran en la carta?
3. ¿Cuál es el ticket medio y dónde hay margen de upselling?
4. ¿Hay estacionalidad que justifique acciones comerciales?

## Stack
SQL (BigQuery) · Power BI · GitHub

## Datos
[Maven Analytics – Pizza Place Sales](https://mavenanalytics.io/data-playground/pizza-place-sales)
4 tablas: orders, order_details, pizzas, pizza_types.

## Estado
🚧 En curso
- SQL: preguntas 1, 2 y 4 completadas · pregunta 3 en curso
- Pendiente: dashboard en Power BI

## Conclusiones

### 1. ¿Cuándo se concentra la demanda y cómo ajustar los turnos de personal?
- **Días fuertes:** jueves a sábado. Viernes 70,8 pedidos/día, jueves 62,3, sábado 60,7. Domingo, el más flojo (50,5).
- **Horario operativo real:** 11:00–23:00.
- **Dos picos diarios:** comida de 12:00 a 14:00 (≈7 pedidos/hora de media) y tarde de 17:00 a 19:00 (≈6,5–6,7). Valle entre las 14:00 y las 16:00 (≈4,1).
- **Recomendación (criterio operativo):** reforzar plantilla de jueves a sábado en ambos picos, con entrada 30–60 min antes para preparación; dotación mínima el domingo.

### 2. ¿Qué pizzas son estrellas y cuáles sobran en la carta?

> **Limitación:** el dataset no incluye costes, así que el análisis se basa en unidades vendidas e ingresos, no en margen.

#### Pizzas estrella
La venta está muy repartida: en unidades, ninguna pizza llega al 5 % del total.

**Top 5 por unidades:**
- classic_dlx: 2.453 (4,95 %)
- bbq_ckn: 2.432 (4,91 %)
- hawaiian: 2.422 (4,89 %)
- pepperoni: 2.418 (4,88 %)
- thai_ckn: 2.371 (4,78 %)

**Por ingresos**, lidera thai_ckn (5,31 %), seguida de bbq_ckn (5,23 %) y cali_ckn (5,01 %), que en unidades queda 6ª.

#### Candidatas a salir: mediterraneo y spinach_supr
Las 10 pizzas con menos ventas son las mismas tanto en unidades como en ingresos. Dentro de ese grupo, dos destacan en ambas métricas:
- **mediterraneo:** 2ª con menos unidades (1,88 %) y 4ª con menos ingresos (1,88 %).
- **spinach_supr:** 4ª con menos unidades (1,92 %) y 3ª con menos ingresos (1,87 %).

Además, son las **únicas dos pizzas que usan aceitunas kalamata**. Retirarlas juntas permitiría eliminar ese ingrediente de las compras; retirar solo una no generaría ese ahorro.

#### Caso especial: brie_carre
Es la última en unidades (0,99 %) y en ingresos (1,42 %), pero **solo se ofrece en talla S** y a 23,65 USD, casi el doble que el resto de pizzas S (9,75–12,75 USD). Aun así, **dentro de las pizzas S ocupa el 9º puesto en ventas**, por encima de la media de su talla.

**Recomendación:** mantenerla y probar a ofrecerla en talla M durante un periodo para medir el impacto en unidades e ingresos.

### Pregunta 3: ¿Cuál es el ticket medio y dónde hay margen de upselling?

El ticket medio global es de **$38,3** y apenas varía entre días: hay una diferencia de alrededor del 3% entre el día con menor ticket medio (domingo, $37,81) y el día con mayor ticket medio (sábado, $39,01).

Durante el día, los datos muestran una diferencia de \~15–20% en el ticket medio, que es mayor durante las comidas ($40–44 entre las 12 y las 14 h) que en el resto del día, incluida la cena (\~$36,5). Esto descartó mi hipótesis inicial de que el ticket medio sería más alto en las cenas, momento en el que familias y amigos se reúnen.

El siguiente paso fue averiguar por qué el ticket medio era más alto en las comidas. Las hipótesis eran dos: o se piden más pizzas por pedido, o se piden pizzas de mayor precio.

- **Precio por pizza:** estable a lo largo del día (en torno a $16,5).
- **Pizzas por pedido:** varía según el turno. En las comidas alcanza 2,69 pizzas por pedido a las 12 h y 2,45 a las 14 h; en el resto del día ronda las 2,2.

Por tanto, **la diferencia de ticket se explica por el número de pizzas por pedido, no por el precio de las pizzas.**

**Margen de upselling:** está en las cenas. Para aprovecharlo, habría que centrarse en aumentar el número de pizzas por pedido, ya que el precio por pizza es estable. Pasar de 2,2 a 2,4 pizzas por pedido elevaría el ticket medio de la cena en unos $3 (si se mantiene el precio medio por pizza).

### 4. ¿Hay estacionalidad que justifique acciones comerciales?
- **Demanda estable durante el año:** entre 56 pedidos/día (diciembre) y 62,4 (julio), una variación de ≈10 %.
- **Comparar totales mensuales lleva a error:** por total, septiembre parecía el mes más flojo, pero por sus días de cierre. En media diaria, el más flojo es diciembre.
- **Implicación:** no se justifican grandes campañas estacionales; la variación relevante está dentro de la semana y del día (ver conclusión 1).
