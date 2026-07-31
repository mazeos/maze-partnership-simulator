# Simulador del partnership — Maze × Clara

Calculadora del acuerdo de sociedad conversado el 14 de julio de 2026.
Se mueve la facturación del mes y muestra cómo se reparte entre Clara y Maze.

- **Producción:** https://partnership.mazefunnels.io (rama `main`)
- **Pruebas:** https://partnership-test.mazefunnels.io (rama `develop`)

## Cómo reparte

1. A la facturación bruta se le resta la pauta publicitaria y las comisiones comerciales.
2. Sobre esa base neta se aplica el reparto, con dos mecanismos elegibles:
   - **Hasta cubrir el piso** — el neto va entero a Clara hasta cubrir sus costos fijos.
     La venta siguiente compensa a Maze por sostener el riesgo. De ahí en más, 80/20.
   - **Por cantidad de ventas** — literal de lo conversado: las primeras 3 ventas enteras
     a Clara, la 4ª a Maze, de la 5ª en adelante 80/20.

La diferencia entre los dos importa: con los supuestos de la reunión (ticket $3.000,
pauta $2.500, comisión 10% + $250, fijos $6.500), el mecanismo por cantidad de ventas
deja a Clara corta hasta cerca de los $13.000 de facturación, mientras Maze ya cobra.

Todos los supuestos son editables en el panel derecho.

## Estructura

App estática de un solo archivo (`index.html`), servida con nginx detrás de Traefik.
Deploy automático: push a `develop` → pruebas · merge a `main` vía PR → producción.
