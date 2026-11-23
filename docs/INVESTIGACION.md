# Investigación — Fase 1

Estado de cada dato:
- ✅ **Verificado**: confirmado contra la fuente indicada, con fecha.
- ⏳ **Pendiente**: conocimiento previo no verificado todavía. No usar como base de decisiones hasta verificarlo.

Última actualización: 2026-11-22.

---

## 1. Proyectos existentes

| Proyecto | Qué hace | Licencia | Estado |
|---|---|---|---|
| **Reticulum (RNS)** | Pila de red criptográfica sobre cualquier medio (Wi-Fi, LoRa, serie, TCP). Ruteo multi-salto y direcciones derivadas de claves. Implementación de referencia en Python. | Reticulum License (MIT + restricciones, ver §2) | ✅ licencia (manual 1.6.1) |
| **LXMF / Sideband** | Mensajería sobre Reticulum con almacenamiento y reenvío ("propagation nodes"). Sideband es el cliente para Android y escritorio. | ⏳ | ⏳ verificar soporte de imágenes y audio |
| **RNode** | Firmware que convierte placas LoRa en interfaces de radio para Reticulum. | ⏳ | ✅ placas soportadas (§4) |
| **Briar** | Mensajería para Android por Bluetooth y Wi-Fi, con contactos agregados en persona. | ⏳ GPLv3 | ⏳ |
| **LibreMesh** (AlterMundi, Córdoba) | Firmware basado en OpenWrt para redes mesh comunitarias. | ⏳ AGPLv3 | ⏳ |
| **Meshtastic** | Mensajería sobre LoRa con hardware dedicado. | ⏳ GPLv3 | ⏳ |
| **Knit** (getknit/knit) | Mensajero mesh para Android sobre Wi-Fi Aware y BLE, sin servidores. | ⏳ | ⏳ apareció en la búsqueda; revisar |
| **Bridgefy** | Mensajería mesh por Bluetooth, propietaria. Tuvo fallas criptográficas documentadas. | Propietaria | ⏳ referencias |

**Conclusión preliminar:** el problema de fondo (mensajes cifrados multi-salto
con almacenamiento y reenvío) ya está resuelto por Reticulum + LXMF. El aporte
original de Chasqui está en la capa de adopción (§6).

## 2. Licencias

### Reticulum License ✅
Fuente: https://markqvist.github.io/Reticulum/manual/license.html (consultado 2026-11-22).

Es una licencia permisiva estilo MIT con dos condiciones adicionales:
1. No se puede usar en sistemas que incluyan entre sus funciones dañar intencionalmente a personas.
2. No se puede usar, directa o indirectamente, para crear conjuntos de datos de entrenamiento de IA o modelos de lenguaje.

Implicancias:
- **No es compatible con GPL**: la GPL prohíbe agregar restricciones. Un proyecto GPL no puede incorporar Reticulum como parte de su código.
- **Sí es combinable con Apache 2.0.** Quien redistribuya Chasqui junto con Reticulum debe respetar también las condiciones de Reticulum.
- ⏳ El manual tiene una sección sobre el uso de asistencia de IA ("Assistance Versus Machine-Substitution"). Hay que leerla antes de contribuir código a Reticulum o integrarlo, porque este proyecto se desarrolla con asistencia de IA.

Decisión de licencia de Chasqui: ver [ADR-0001](decisiones/ADR-0001-licencia.md).

## 3. Regulación de radio en Argentina

- ✅ ENACOM lista **915–928 MHz** como banda de uso compartido sin autorización.
  Fuente: https://www.enacom.gob.ar/bandas-de-uso-compartido-sin-autorizacion_p680
  - En Argentina la banda **empieza en 915**, no en 902 como en EE.UU. Hay que configurar las placas dentro de 915–928 MHz.
- ✅ La Resolución ENACOM 4653/2019 fija una potencia media conducida máxima de **1 W** para sistemas de modulación digital de banda ancha en 915–928 MHz.
  Fuente: https://www.enacom.gob.ar/multimedia/normativas/2019/res4653.pdf
  - ⏳ Falta determinar en qué categoría cae LoRa (banda ancha u "otros sistemas") y cuál es su límite exacto.
- ⏳ Las bandas de radioaficionado requieren licencia. Hay que verificar las restricciones sobre cifrado en esas bandas. Por ahora no se usan.

## 4. Hardware LoRa compatible con RNode ✅

Fuente: https://reticulum.network/manual/hardware.html (consultado 2026-11-22).

Placas listadas, entre otras: Heltec LoRa32 v3, Heltec T114, LilyGO T3S3, placas RAK4631. Según https://www.reticulumnet.nl/en/hardware/ también se soportan Heltec V4, LilyGO T-Beam y T-Echo.

Al comprar:
- Elegir la versión **915 MHz**.
- Que incluya antena. **No transmitir nunca sin antena**, porque se daña la etapa de radio.

**Equipos evaluados:**
- **Seeed Wio Tracker L1 Pro** (nRF52840 + SX1262, GPS, batería de 2000 mAh, entrada solar, gabinete). Viene listo para Meshtastic y existe una variante para MeshCore. ⏳ Según un reporte de usuario en r/reticulum, **no está soportado por RNode** (https://www.reddit.com/r/reticulum/comments/1uq1orb/). No tiene Wi-Fi. No sirve como base de CHASQUI NODE. Es una buena referencia de diseño de producto: gabinete, solar y bajo consumo.

Velocidad orientativa de LoRa con RNode: de ~37 bps a ~11 kbps según la configuración (fuente: reticulumnet.nl). ⏳ medir en pruebas propias.

## 5. Android, Bluetooth, Wi-Fi Direct y routers ⏳

Puntos a verificar con documentación oficial y pruebas propias:
- Restricciones de ejecución en segundo plano (Doze, servicios en primer plano) por versión de Android.
- Alcance real de BLE y Wi-Fi Direct. Wi-Fi Direct necesita interacción del usuario en ciertas versiones.
- Wi-Fi Aware: disponible solo en algunos equipos.
- Nearby Connections depende de Google Play Services, que es propietario. Evitarlo si se busca independencia.
- Routers de proveedores de internet en Argentina (Telecom, Movistar, Claro, etc.): suelen estar bloqueados y son propiedad del proveedor. Se espera muy baja compatibilidad con OpenWrt.
- Requisitos de memoria y flash para correr Reticulum (Python) en OpenWrt. Alternativas: microcontroladores con firmware de transporte (por ejemplo RTNode) o celulares viejos.

## 6. Dónde puede estar lo novedoso

1. **Base offline de routers argentinos** con compatibilidad *probada*, no supuesta.
2. **Asistente guiado** de alta de nodos (celular viejo → nodo; router → nodo) con recuperación probada.
3. **Integración**: celulares, nodos fijos y LoRa en una sola experiencia simple.
4. **Distribución offline de la app** desde la propia app y desde los nodos (portal Wi-Fi con el APK).
5. **Despliegue comunitario local**: comercios, centros vecinales, defensa civil y campamentos.

## 7. Pendientes de investigación

- [ ] Leer la sección del manual de Reticulum sobre asistencia de IA.
- [ ] Verificar las licencias y capacidades actuales de Sideband, LXMF, RNode, Briar, LibreMesh y Meshtastic.
- [ ] Confirmar si existe una implementación de Reticulum para Android que se pueda usar como biblioteca, o si conviene usar Sideband como base.
- [ ] Límite de potencia aplicable a LoRa (ENACOM).
- [ ] Revisar Knit (Wi-Fi Aware + BLE) como referencia técnica.
