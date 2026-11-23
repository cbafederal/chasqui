# Hoja de ruta

Cada fase se cierra solo cuando su criterio de avance está documentado con una
prueba real en `pruebas/`.

| Fase | Objetivo | Criterio de avance |
|---|---|---|
| **1** | Investigación, nombre, arquitectura y documentación pública | Pendientes de [INVESTIGACION.md §7](INVESTIGACION.md) resueltos; ADR-0002 aceptado o reemplazado |
| **2** | Prototipo Android: mensajes offline entre 2 teléfonos | Mensaje A→B sin internet, documentado |
| **3** | Multi-salto y almacenamiento temporal | A→B pasando por ≥2 intermediarios; entrega diferida de horas |
| **3b** | Nodo fijo con celular viejo + LoRa | Celular viejo enchufado actuando como buzón 24 h; enlace LoRa medido |
| **4** | Base offline de routers argentinos y detección | Detección correcta en los modelos que tengamos físicamente |
| **5** | Primer router convertido en nodo | Instalación **y recuperación** probadas en el mismo modelo |
| **6** | Pruebas de campo | Campamento: 4–5 celulares distribuidos, medición de saltos, latencia y alcance. Luego, un barrio piloto. |

## Etapas futuras (ideas registradas, sin fecha)

- **Drone "mula de datos"** (idea de Nicolás Bergese, registrada el 2026-11-22):
  un drone que recorre avenidas y calles llevando un nodo a bordo. Recoge y
  entrega mensajes al pasar cerca de celulares y nodos fijos, y conecta zonas
  aisladas entre sí. ⏳ Pendiente: regulación de ANAC para drones, autonomía y
  capacidad de carga.
- **Uso en campamentos y zonas rurales**: un nodo fijo con LoRa y antena
  elevada por campamento o establecimiento, y enlaces LoRa entre ellos.

## Prueba de campo de referencia: campamento

- 4–5 celulares viejos distribuidos, de ser posible en altura (árbol o palo), con power bank o panel.
- Opcional: 2 placas LoRa 915 MHz.
- Medir: alcance entre nodos, cantidad de saltos, tiempo de entrega y consumo de batería.
