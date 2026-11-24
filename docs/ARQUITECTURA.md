# Arquitectura (propuesta — Fase 1)

> Documento vivo. Las piezas marcadas ⏳ dependen de verificaciones pendientes
> en [INVESTIGACION.md](INVESTIGACION.md).

## Vista general

```
 [Celular A] ~~BLE/Wi-Fi~~ [Celular B] ~~~~ [Nodo fijo] ===LoRa 915=== [Nodo fijo] ~~~~ [Celular C]
   usuario      transporta      (celular viejo +         (enlace km)        (buzón)        destinatario
                                 UPS/solar, buzón)
```

## Capas

| Capa | Responsabilidad | Base propuesta |
|---|---|---|
| **Transporte y ruteo** | Cifrado, direcciones, multi-salto | Reticulum (⏳ [ADR-0002](decisiones/ADR-0002-base-reticulum.md)) |
| **Mensajería** | Almacenar y reenviar, buzones, confirmaciones | LXMF (⏳) |
| **App Chasqui (Android)** | Interfaz simple, SOS, prioridades, compartir la app sin internet | Desarrollo propio |
| **Nodo fijo** | Buzón permanente, portal de descarga del APK | Celular viejo en "modo nodo" ([ADR-0003](decisiones/ADR-0003-nodos-fijos.md)) |
| **Radio de largo alcance** | Enlaces de kilómetros | Placas RNode LoRa 915 MHz |
| **Routers** (fase 5) | Nodos fijos de alta disponibilidad | OpenWrt, solo en modelos probados |
| **Base de routers** (fase 4) | Detección y compatibilidad offline | Desarrollo propio |

## Tipos de mensaje y prioridad

| Prioridad | Tipo | Tamaño orientativo |
|---|---|---|
| 1 | SOS + ubicación | < 1 KB |
| 2 | Texto | < 2 KB |
| 3 | Ubicación | < 1 KB |
| 4 | Nota de voz comprimida | pocos KB por segundo de audio (⏳ medir) |
| 5 | Foto comprimida | 30–100 KB máx. (⏳ definir límite) |
| — | Video | No soportado |

Reglas de convivencia de la red (a definir con pruebas):
- Vencimiento de mensajes (propuesta: 72 h).
- Cupo de almacenamiento por nodo.
- No retransmitir multimedia por LoRa salvo configuración explícita.

## Distribución de la app sin internet

1. La app comparte su propio APK por Bluetooth o Wi-Fi (Quick Share).
2. Los nodos fijos ofrecen una red Wi-Fi abierta con un portal para descargar el APK.
3. Distribución previa con internet: GitHub Releases, F-Droid (⏳) y QR en lugares públicos.

**Propagación "viral" con consentimiento** (pedido de Nicolás Bergese, 2026-11-24):
cada app instalada **anuncia automáticamente** que puede compartir el APK y lo
ofrece a los dispositivos cercanos. La instalación **siempre la confirma el
usuario**: Android no permite instalar apps sin aceptación, y hacerlo sería
comportamiento de malware.
- El APK se firma con la clave del proyecto. Antes de ofrecer o instalar una
  copia recibida, la app verifica la firma, para que no circulen versiones
  falsas o modificadas.
- Las versiones más nuevas se propagan del mismo modo y reemplazan a las viejas.

## Energía

Ningún nodo fijo se considera desplegado sin respaldo de energía (batería, UPS o panel solar).

## Seguridad (a desarrollar)

- No se implementa criptografía propia.
- Modelo de amenazas: ⏳ documento pendiente (`docs/AMENAZAS.md`).
- Metadatos: quién habla con quién puede filtrarse aunque el contenido esté cifrado. Hay que evaluar cómo lo maneja Reticulum.
