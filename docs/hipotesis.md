# Registro de hipótesis

Hipótesis planteadas durante la exploración y cómo se comprobaron.

| # | Hipótesis | Por qué lo pensaba | Cómo lo comprobé | Resultado |
|---|---|---|---|---|
| H1 | Los 7 días sin ventas son la semana de Navidad | Cierre habitual en restauración | Días de 2015 sin pedidos (`GENERATE_DATE_ARRAY` + `NOT IN`) | ❌ Rechazada: días sueltos en septiembre, octubre y el 25 de diciembre |
| H2 | El local abre a las 9:00 | Aparecen pedidos a esa hora | Total de pedidos por hora en el año | ❌ Rechazada: solo 9 pedidos antes de las 11:00 en todo el año (1 a las 9h, 8 a las 10h). Horario operativo real desde las 11:00 |
| H3 | La facturación diaria (2.284 $) es baja | Experiencia como GM | No comprobable sin datos de costes ni referencias del sector | ⚪ Opinión, no conclusión |
| H4 | Diciembre es el mes más flojo por las fiestas | Cambio de hábitos en Navidad | Comparar diciembre semana a semana | ⏳ Pendiente |
