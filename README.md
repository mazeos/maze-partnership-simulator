# Simulador del acuerdo — Maze

Calculadora del modelo de sociedad de Maze: se mueve la facturación del mes y muestra
cómo se reparte entre el socio y Maze.

- **Producción:** https://partnership.mazefunnels.io (rama `main`)
- **Pruebas:** https://partnership-test.mazefunnels.io (rama `develop`)

## Cómo reparte

1. A la facturación bruta se le resta la pauta publicitaria y las comisiones comerciales.
2. Sobre esa base neta se aplica el reparto, con dos mecanismos elegibles:
   - **Hasta cubrir el piso** — el neto va entero al socio hasta cubrir sus costos fijos.
     La venta siguiente compensa a Maze por sostener el riesgo. De ahí en más, 80/20.
   - **Por cantidad de ventas** — las primeras 3 ventas enteras al socio, la 4ª a Maze,
     de la 5ª en adelante 80/20.

La diferencia entre los dos importa: con supuestos típicos (ticket $3.000, pauta $2.500,
comisión 10% + $250, fijos $6.500), el mecanismo por cantidad de ventas deja al socio
corto hasta cerca de los $13.000 de facturación, mientras Maze ya cobra.

Todos los supuestos son editables en el panel derecho, así que la misma herramienta
sirve para cualquier negociación sin tocar el código.

## Estructura

App estática de un solo archivo (`index.html`), servida con nginx detrás de Traefik.
Deploy automático: push a `develop` → pruebas · merge a `main` vía PR → producción.

La interfaz habla en segunda persona a propósito: no lleva nombres propios, para que
pueda mostrarse a cualquier socio sin exponer con quién más se conversó.
