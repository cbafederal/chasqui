# ADR-0003 — Celulares viejos como primeros nodos fijos

- **Estado:** Aceptada
- **Fecha:** 2026-11-22
- **Decide:** Nicolás Bergese

## Contexto
Flashear routers tiene riesgo de dejarlos inutilizables, la compatibilidad es
baja y los routers de los proveedores de internet no son del usuario. Un
celular Android viejo ya tiene batería, Wi-Fi y Bluetooth, y no hay que
modificarle nada.

## Decisión
Los primeros nodos fijos serán **celulares Android viejos en "modo nodo"**,
enchufados, con respaldo UPS o solar y, opcionalmente, una placa LoRa. Los
routers OpenWrt pasan a la Fase 5 y solo se usarán modelos con instalación y
recuperación probadas.

## Consecuencias
- Prueba de campo posible desde temprano (campamento).
- Hay que gestionar las baterías degradadas de los equipos viejos (⏳ evaluar riesgo de hinchazón con carga permanente).
