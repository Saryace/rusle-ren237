# RUSLE usando GEE
Google Colab para desarrollar un modelo RUSLE simple

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Saryace/rusle-ren237/blob/main/rusle_ren237.ipynb)

## ⚠️ Nota: este es un notebook de ejemplo con fines educativos

Este notebook fue desarrollado como **material de clase** para el curso AGP3141, con el objetivo de mostrar cómo calcular los factores de la ecuación RUSLE (Erosividad R, Erodabilidad K, entre otros) usando datos públicos y Google Earth Engine.

**No debe usarse como fuente definitiva para estudios técnicos, reportes oficiales o toma de decisiones sin validación adicional.** Los valores obtenidos son aproximaciones basadas en datasets globales de resolución media (250 m – 5.5 km), y deben contrastarse con datos locales/medidos en campo cuando el objetivo sea un análisis real de erosión.

---

### Fuentes de datos usadas en este ejemplo

| Variable | Fuente | Dataset / Asset (GEE) | Resolución | Notas |
|---|---|---|---|---|
| Área de interés (AOI) | [Inventario de Erosión CIREN](https://inventarioerosion.ciren.cl/) | `r13_168_rep_1ha` (WFS) | Vectorial | Cuenca del Estero Cholqui; se disolvió el polígono a un solo contorno para reducir el tamaño del objeto |
| Precipitación | CHIRPS Daily | `UCSB-CHG/CHIRPS/DAILY` | ~5.5 km | Se sumó por año hidrológico (1 abr – 31 mar) |
| Carbono orgánico del suelo | OpenLandMap | `OpenLandMap/SOL/SOL_ORGANIC-CARBON_USDA-6A1C_M/v02` | 250 m | Banda `b0` (0 cm); unidad nativa "x5 g/kg" |
| Arena | OpenLandMap | `OpenLandMap/SOL/SOL_SAND-WFRACTION_USDA-3A1A1A_M/v02` | 250 m | Banda `b0` (0 cm); % directo |
| Arcilla | OpenLandMap | `OpenLandMap/SOL/SOL_CLAY-WFRACTION_USDA-3A1A1A_M/v02` | 250 m | Banda `b0` (0 cm); % directo |
| Limo | Calculado | `100 - arena - arcilla` | 250 m | OpenLandMap no publica limo como asset propio |

---

### Referencias

- Williams, J.R. (1995). Ecuación de erodabilidad del suelo, implementada en el modelo EPIC.
- Arnold, J.G., Kiniry, J.R., Srinivasan, R., Williams, J.R., Haney, E.B., Neitsch, S.L. (2012). *Input/Output Documentation, SWAT 2012*.
- Bonilla, C.A. y Vidal, K.L. (2011). Rainfall erosivity in Central Chile. *Journal of Hydrology*.
- CIREN — Inventario de Erosión de Suelos de Chile: https://inventarioerosion.ciren.cl/
