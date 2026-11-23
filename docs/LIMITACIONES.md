# Limitaciones conocidas

Se actualiza a medida que avanzan las pruebas. Nada de lo que figura acá está
resuelto todavía.

1. **Energía**: en un apagón, todo nodo fijo sin batería deja de funcionar.
2. **Densidad**: con radios de corto alcance (BLE y Wi-Fi), la red necesita muchos dispositivos cerca para que los mensajes avancen.
3. **Android**: las restricciones de segundo plano pueden cortar la retransmisión cuando la app no está abierta (⏳ medir por versión).
4. **Routers**: la mayoría de los routers domésticos en Argentina vienen del proveedor de internet, están bloqueados y no son del usuario. Se espera que la base de compatibles sea chica.
5. **Velocidad LoRa**: de bps a pocos kbps. Sirve para texto y ubicación; las fotos tardan minutos.
6. **Almacenamiento ajeno**: cada mensaje en tránsito ocupa espacio y batería de terceros. Hay que poner límites.
7. **Dependencia externa**: la base propuesta (Reticulum) tiene licencia con restricciones propias y un único mantenedor principal (⏳ evaluar riesgo).
8. **Sin pruebas reales todavía**: ninguna funcionalidad está probada a la fecha.
