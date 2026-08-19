# Infraestructura — Arquitectura de red

Proyecto de **redes y cableado estructurado** para una fábrica de **4 pisos** (Electrolux). Incluye diseño de red (Packet Tracer), planos físicos (SketchUp) y documentación técnica de cableado y subredes (Excel).

## Componentes

| Recurso | Formato | Contenido |
|---|---|---|
| `Red.pkt` | Packet Tracer | Topología lógica de la red (routers, switches, hosts) |
| `EXCEL EMPRESA.xlsx` | Excel | Documentación técnica completa del cableado (ver abajo) |
| Planos SketchUp (5) | `.skp` | Diseño físico por piso + planta general |

## Planos (release `planos-sketchup-v1`)

Los 5 planos SketchUp (~1 GB total) **no viven en git** (superan el límite de 100 MB por archivo de GitHub). Se distribuyen como assets de la release:

👉 https://github.com/estivenchaluisa27-ops/Infraestructura/releases/tag/planos-sketchup-v1

| Plano | Alcance |
|---|---|
| Fabrica.skp | Vista general de la fábrica |
| Piso 1.skp … Piso 4.skp | Detalle por piso |

Descargar: `gh release download planos-sketchup-v1` (o desde la UI de GitHub).

## Documentación Excel (hojas)

| Hoja | Contenido |
|---|---|
| TABLA GENERAL | Resumen de equipos y puntos por piso |
| PISO 1 | Núcleo operativo: monitoreo de seguridad, gestión comercial, atención a casos |
| PISO 2 | Centro de control con infraestructura crítica (DTC) |
| PISO 3 | Planta de producción |
| PISO 4 | Planta alta |
| DTC RACK 12 | Distribución del rack (12U): unidades de montaje de equipos |
| FÁBRICA | Área de planta productiva |
| SUCURSAL | Centro de ventas remoto |
| BACK BONE | Cableado vertical (backbone) entre pisos |
| SERVICIO INTERNET | Contratación de enlace / ISP |
| CONEXIONES SWITCHES | Puertos y conexiones entre switches por piso |
| SUBNETEO | Plan de subredes (VLSM) |

## Estructura de red

```
[Internet / SERVICIO INTERNET]
            │
            ▼
     Router principal
            │
      ┌─────┴─────┐
      ▼           ▼
 BACKBONE ──► Switches por piso (CONEXIONES SWITCHES)
      │
      ├──► PISO 1 (seguridad + comercial)
      ├──► PISO 2 (DTC: infraestructura crítica)
      ├──► PISO 3 (producción)
      └──► PISO 4
            │
            └──► SUCURSAL (enlace remoto)
```

El **DTC** (cuarto de telecomunicaciones) centraliza el backbone y el rack 12U donde se montan los equipos activos.

## Documentación relacionada

- [Índice](INDICE.md)
- [README](../README.md)