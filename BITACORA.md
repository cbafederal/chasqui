# Bitácora de avances

Registro cronológico real. Cada entrada corresponde a trabajo hecho en esa fecha.

## 2026-11-22 — Inicio del repositorio (Fase 1)

- Creación del repositorio público `cbafederal/chasqui`.
- Nombre provisional: **Chasqui — Red Ciudadana Autónoma Offline**.
- Licencia Apache 2.0 con NOTICE a nombre de Nicolás Bergese ([ADR-0001](docs/decisiones/ADR-0001-licencia.md)).
- Investigación inicial verificada:
  - Licencia de Reticulum: MIT con restricciones, incompatible con GPL.
  - ENACOM: 915–928 MHz de uso compartido sin autorización.
  - Placas LoRa compatibles con RNode.
- Arquitectura propuesta: Reticulum + LXMF como base ([ADR-0002](docs/decisiones/ADR-0002-base-reticulum.md), pendiente de verificación).
- Decisión: celulares viejos como primeros nodos fijos ([ADR-0003](docs/decisiones/ADR-0003-nodos-fijos.md)).
- Definida la prueba de campo de referencia: campamento con 4–5 celulares.

- Idea registrada para una etapa futura: drone como "mula de datos" que recorre calles distribuyendo mensajes ([HOJA_DE_RUTA](docs/HOJA_DE_RUTA.md)).

**Próximo:** resolver los pendientes de [INVESTIGACION.md §7](docs/INVESTIGACION.md) y conseguir 2 placas LoRa de 915 MHz.
