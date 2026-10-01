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
_Pendiente._
Ver el [registro de hipótesis](docs/hipotesis.md) para el detalle de las comprobaciones.
