## Plato's Pizza – Análisis de ventas 2015

Análisis de un año de ventas de una pizzería (≈21.000 pedidos) desde la perspectiva
de un General Manager: decisiones de personal, carta, ticket medio y estacionalidad.

## Preguntas de negocio
1. ¿Cuándo se concentra la demanda y cómo ajustar las rotas de personal?
2. ¿Qué pizzas son estrellas y cuáles sobran en la carta?
3. ¿Cuál es el ticket medio y dónde hay margen de upselling?
4. ¿Hay estacionalidad que justifique acciones comerciales?

## Stack
SQL (BigQuery) · Power BI · GitHub

## Datos
[Maven Analytics – Pizza Place Sales](https://mavenanalytics.io/data-playground/pizza-place-sales)
4 tablas: orders, order_details, pizzas, pizza_types.
### Validación de datos
- 4 tablas cargadas en BigQuery; tipos de columna revisados tras la carga.
- Estructura: `orders` = 1 fila por pedido (≈21.000); `order_details` = 1 fila por línea de pedido (≈48.000), relación uno a muchos.
- Sin valores nulos en `order_details`.
- Integridad referencial: 0 líneas de pedido sin pizza válida en la carta.
- Periodo: año 2015 completo, 358 días con ventas (7 días sin actividad).
- Moneda: USD (pizzería ficticia de EE. UU.).
- Pedidos antes de las 11:00 residuales (9 en todo el año); se consideran fuera del horario operativo.

## Estado
🚧 En curso – exploración inicial en SQL.

## Conclusiones

### 1. Demanda y personal 
- **Días fuertes: jueves a sábado.** Viernes 70,8 pedidos/día, jueves 62,3, sábado 60,7.
  **Domingo, el más flojo** (50,5).
- **Horario operativo real: 11:00–23:00.**
- **Dos picos diarios:** comida de 12:00 a 14:00 (≈7 pedidos/hora de media) y tarde
  de 17:00 a 19:00 (≈6,5–6,7). Valle entre las 14:00 y las 16:00 (≈4,1).
- **Recomendación (criterio operativo):** reforzar plantilla de jueves a sábado en ambos
  picos, con entrada 30–60 min antes para preparación; dotación mínima el domingo.
  
### 2.Pizzas son estrellas y cuáles sobran en la carta


> **Limitación:** el dataset no incluye costes, así que el análisis se basa en unidades vendidas e ingresos, no en margen.


### Pizzas estrella
La venta está muy repartida: en unidades, ninguna pizza llega al 5 % del total.


**Top 5 por unidades:**
- classic_dlx: 2.453 (4,95 %)
- bbq_ckn: 2.432 (4,91 %)
- hawaiian: 2.422 (4,89 %)
- pepperoni: 2.418 (4,88 %)
- thai_ckn: 2.371 (4,78 %)


**Por ingresos**, lidera thai_ckn (5,31 %), seguida de bbq_ckn (5,23 %) y cali_ckn (5,01 %), que en unidades queda 6ª.


### Candidatas a salir: mediterraneo y spinach_supr
Las 10 pizzas con menos ventas son las mismas tanto en unidades como en ingresos. Dentro de ese grupo, dos destacan en ambas métricas:
- **mediterraneo:** 2ª con menos unidades (1,88 %) y 4ª con menos ingresos (1,88 %).
- **spinach_supr:** 4ª con menos unidades (1,92 %) y 3ª con menos ingresos (1,87 %).


Además, son las **únicas dos pizzas que usan aceitunas kalamata**. Retirarlas juntas permitiría eliminar ese ingrediente de las compras. Retirar solo una no generaría ese ahorro.


### Caso especial: brie_carre
Es la última en unidades (0,99 %) y en ingresos (1,42 %), pero **solo se ofrece en talla S** y a 23,65 $, casi el doble que el resto de pizzas S (9,75–12,75 $). Aun así, **dentro de las pizzas S ocupa el 9º puesto en ventas**, por encima de la media de su talla.


**Recomendación:** mantenerla y probar a ofrecerla en talla M durante un periodo para medir el impacto en unidades e ingresos.


### 4. Estacionalidad
- **Demanda estable durante el año:** entre 56 pedidos/día (diciembre) y 62,4 (julio),
  una variación de ≈10 %.
- Comparar totales mensuales lleva a error: por total, septiembre parecía el mes más flojo,
  pero por sus días de cierre. En media diaria, el más flojo es diciembre.
- **Implicación:** no se justifican grandes campañas estacionales; la variación relevante
  está dentro de la semana y del día (ver conclusión 1).

## Limitaciones
- Sin datos de costes: el análisis de carta se basa en ingresos, no en margen.
- En el cruce día × hora, la media de las horas de menor actividad puede estar inflada
  (solo cuenta los días con al menos un pedido en esa franja).
Ver el [registro de hipótesis](docs/hipotesis.md) para el detalle de las comprobaciones.
