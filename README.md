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
- 4 tablas cargadas en BigQuery; esquemas revisados tras la carga.
- Sin valores nulos en `order_details`.
- Integridad referencial: todas las líneas de pedido tienen una pizza válida en la carta (0 huérfanas).
- Periodo: año 2015, 358 días con ventas (7 días sin actividad: 24 y 25 Sept , 5, 12, 19 y 26 Oct, 25 Diciembre ).
- Moneda: USD.

## Estado
🚧 En curso – exploración inicial en SQL.

## Conclusiones
_Pendiente._
