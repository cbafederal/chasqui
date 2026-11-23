# ADR-0002 — Usar Reticulum + LXMF como base de red

- **Estado:** Propuesta (pendiente de verificación)
- **Fecha:** 2026-11-22

## Contexto
Hace falta transporte cifrado, multi-salto, sobre varios medios (BLE, Wi-Fi y
LoRa) y con almacenamiento y reenvío. Inventar un protocolo y criptografía
propios es riesgoso: hay antecedentes de fallas graves en apps mesh.

## Opciones
1. **Reticulum + LXMF**: cubre multi-medio, multi-salto, nodos de propagación y LoRa (RNode).
2. **Bramble/Briar**: Java nativo en Android, pero el modelo de contactos agregados en persona no sirve para llegar a desconocidos.
3. **Protocolo propio**: descartado por riesgo de seguridad y esfuerzo.

## Decisión propuesta
Opción 1, condicionada a verificar:
- [ ] La forma de integrarlo en Android (biblioteca o tomar Sideband como base).
- [ ] Las condiciones del manual de Reticulum sobre asistencia de IA.
- [ ] El rendimiento en celulares viejos.

## Consecuencias
- Interoperabilidad con la red Reticulum existente.
- Dependencia de un proyecto con un mantenedor principal.
