# RUSLE usando GEE
Google Colab para desarrollar un modelo RUSLE simple

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Saryace/rusle-ren237/blob/main/rusle_ren237.ipynb)

## ⚠️ Nota: este es un notebook de ejemplo con fines educativos, NO debe usarse como fuente definitiva para estudios técnicos, reportes oficiales o toma de decisiones sin validación adicional

Este notebook fue desarrollado como **material de clase** para el curso Conservación de Suelos y Gestión del Carbono, con el objetivo de mostrar cómo calcular los factores de la ecuación RUSLE (Erosividad R, Erodabilidad K, entre otros) utilizando datos públicos y Google Earth Engine.

---

### Fuentes de datos usadas en este ejemplo

| Variable | Fuente | Dataset / Asset (GEE) | Resolución | Notas |
|---|---|---|---|---|
| Área de interés (AOI) | [Inventario de Erosión CIREN](https://inventarioerosion.ciren.cl/) | `r13_168_rep_1ha`| Vectorial | Cuenca del Estero Cholqui; se disolvió el polígono a un solo contorno para reducir el tamaño del objeto |
| Precipitación | CHIRPS Daily | `UCSB-CHG/CHIRPS/DAILY` | ~5.5 km | Se sumó por año hidrológico (1 abr – 31 mar) |
| Carbono orgánico del suelo | OpenLandMap | `OpenLandMap/SOL/SOL_ORGANIC-CARBON_USDA-6A1C_M/v02` | 250 m | Banda `b0` (0 cm); unidad nativa "x5 g/kg" |
| Arena | OpenLandMap | `OpenLandMap/SOL/SOL_SAND-WFRACTION_USDA-3A1A1A_M/v02` | 250 m | Banda `b0` (0 cm); % directo |
| Arcilla | OpenLandMap | `OpenLandMap/SOL/SOL_CLAY-WFRACTION_USDA-3A1A1A_M/v02` | 250 m | Banda `b0` (0 cm); % directo |
| Limo | Calculado | `100 - arena - arcilla` | 250 m | OpenLandMap no publica limo como asset propio |

---

### Referencias

- Bonilla, C.A. y Vidal, K.L. (2011). Rainfall erosivity in Central Chile. *Journal of Hydrology*. http://dx.doi.org/10.1016/j.jhydrol.2011.09.022
- Núñez-Hidalgo, I., Pfeiffer, M., & Gaxiola, A. (2025). Long-term dynamics of soil water erosion in Chile: interactions between climate variability and land-cover change. CATENA, 259, 109377. https://doi.org/10.1016/j.catena.2025.109377
- CIREN — Inventario de Erosión de Suelos de Chile: https://inventarioerosion.ciren.cl/
