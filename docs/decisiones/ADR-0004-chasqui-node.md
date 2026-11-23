# ADR-0004 — CHASQUI NODE: dispositivo físico comercial

- **Estado:** Propuesta (investigación pendiente; no modifica la arquitectura vigente)
- **Fecha:** 2026-11-22
- **Propone:** Nicolás Bergese

## Idea
Un dispositivo propio, **CHASQUI NODE**, basado en una placa Heltec LoRa 32 con
antena, batería recargable y carcasa compacta, que venga con firmware Chasqui
preinstalado. Al encenderlo:
1. Levanta su propia red Wi-Fi con una página de bienvenida.
2. Desde esa página se descarga la APK oficial y se configura el equipo.
3. Una vez configurado, funciona como nodo permanente de la red mesh LoRa y
   retransmite mensajes cifrados sin internet.

Está pensado para fabricación y venta masiva, con instalación simple, bajo
costo y funcionamiento autónomo. Es la versión producto del nodo fijo de
[ADR-0003](ADR-0003-nodos-fijos.md).

## Antecedente
RTNode-HeltecV4 (https://github.com/GrayHatGuy/RTNode-HeltecV4): firmware de
nodo de transporte Reticulum autónomo para Heltec V3/V4, configurable por portal
web. Muestra que la idea es viable.

## Puntos a investigar antes de diseñar
- [ ] **Placa**: V4 (16 MB flash, 2 MB PSRAM, hasta 28 dBm) frente a V3 (8 MB, sin PSRAM).
- [ ] **APK en el equipo**: la flash es insuficiente para una APK grande. Opciones: microSD o una app Chasqui liviana.
- [ ] **Almacenamiento y reenvío en microcontrolador**: capacidad real de guardar mensajes con 2 MB de PSRAM.
- [ ] **Autonomía**: ~50–80 mA solo LoRa y ~150–200 mA con Wi-Fi (fuente: reticulumnet.nl). Evaluar Wi-Fi a demanda (botón), batería 18650 y panel solar.
- [ ] **Homologación ENACOM** obligatoria para comercializar equipos de radio: costos, plazos y requisitos.
- [ ] **Licencias**: licencia del firmware RNode y de RTNode. Si son GPL, el firmware del nodo será un componente GPL separado.
- [ ] **Seguridad**: Wi-Fi abierto como superficie de ataque, firma del firmware, actualización segura.
- [ ] **Costos de fabricación**: placa, batería, antena, carcasa y homologación, por volumen.

## Orden
Esta fase arranca después de validar la red con celulares y Sideband (Fases 2–3).
