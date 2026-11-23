# ADR-0001 — Licencia del proyecto

- **Estado:** Aceptada
- **Fecha:** 2026-11-22
- **Decide:** Nicolás Bergese

## Contexto
El proyecto es público y abierto, y debe dejar trazable la autoría. La base
técnica candidata, Reticulum, usa una licencia estilo MIT con restricciones
adicionales (no usarlo para dañar a personas ni para entrenar IA). Esas
restricciones la hacen incompatible con GPL ([INVESTIGACION.md §2](../INVESTIGACION.md)).

## Opciones
1. **Apache 2.0**: permisiva, exige conservar el copyright y el NOTICE, e incluye concesión de patentes. Se puede combinar con Reticulum.
2. **GPLv3 / AGPLv3**: obliga a que los derivados sigan abiertos, pero impide integrar Reticulum como biblioteca.

## Decisión
**Apache 2.0.**

## Consecuencias
- El autor conserva la autoría y el copyright. Toda copia debe mantener el aviso de [NOTICE](../../NOTICE).
- Terceros pueden usar, modificar y redistribuir el código, incluso en productos cerrados.
- Las distribuciones que incluyan Reticulum deben respetar además su licencia.
