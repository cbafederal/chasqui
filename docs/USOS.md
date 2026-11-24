# Usos previstos

## Principio: no es una herramienta de rastreo
Chasqui **no se diseña para rastrear personas ni objetos** (decisión de
Nicolás Bergese, 2026-11-22). La ubicación solo se comparte cuando el usuario la
envía a propósito, en un mensaje o en un SOS. Nunca se envía de forma automática
ni continua.

## Primer uso cotidiano: Modo Ruta / Modo Campamento (prioridad, 2026-11-24)
- Grupo creado con un QR (por ejemplo, los integrantes de una salida en moto).
- Chat del grupo y mensajes directos sin señal.
- Botones rápidos: "Estoy bien", "Me detuve", "Necesito ayuda" y SOS.
- "Enviar mi ubicación" solo cuando el usuario lo toca, nunca de forma automática.
- Hardware opcional: una placa LoRa por moto o por carpa, conectada al celular por Bluetooth.
- **Audio como función central** (2026-11-24): notas de voz y reproducción automática al llegar.
  ⏳ Verificar si los audios y llamadas de Sideband (LXST) funcionan sobre LoRa o solo sobre Wi-Fi.
- **Intercomunicador de moto** como complemento: el intercomunicador se conecta al celular como
  auricular Bluetooth, así que la app reproduce y graba por él. ⏳ Probar que el botón del
  intercomunicador dispare la grabación, modelo por modelo. Pensado para usar sin mirar la pantalla.
- **Extender el alcance del intercomunicador con LoRa** (idea de Nicolás Bergese, 2026-11-24):
  cuando el grupo supera el alcance propio del intercomunicador, los audios viajan por LoRa
  como "handy diferido". Se acepta la demora.
- **Voz → texto → voz** (idea de Nicolás Bergese, 2026-11-24): el emisor habla, el celular lo
  pasa a texto **sin internet**, viaja como texto (de bytes a pocos KB, ideal para LoRa) y el
  celular del receptor lo **lee en voz alta** por el intercomunicador. Modos: solo texto
  leído, solo audio, o ambos.
  ⏳ Evaluar reconocimiento de voz offline en español (motor de Android sin conexión, Vosk,
  Whisper) con ruido de viento y casco. ⏳ Lectura en voz alta (TTS) offline de Android.
- **Reloj inteligente**: ⏳ con Wear OS se puede hacer una app compañera (botón SOS, "Estoy bien",
  enviar ubicación con el GPS del reloj). Garmin tiene una plataforma limitada (Connect IQ) y los
  relojes económicos con sistema cerrado probablemente no sirvan. Se mantiene el principio: la
  ubicación se envía solo a pedido.

## Usos
- **Emergencias y apagones**: comunicación vecinal, SOS, coordinación con bomberos voluntarios y defensa civil.
- **Campamentos**: mensajes entre carpas, grupos y campamentos vecinos.
- **Viajes en moto, 4x4 o bici** por rutas sin señal: mensajes entre los integrantes del grupo, y SOS a un nodo en el próximo pueblo o puesto.
- **Campos y zonas rurales**: comunicación entre la casa, los puestos y los vecinos, y avisos de incendio o tormenta.
- **Trekking y montaña**: grupos separados en distintos tramos de un sendero, refugios con nodo fijo.
- **Eventos masivos** (recitales, peregrinaciones, maratones), donde la red celular se satura.
- **Escuelas rurales y parajes sin cobertura**: mensajería comunitaria y avisos.
- **Clubes de pesca, náutica y vuelo libre**: comunicación en zonas sin antenas.
- **Educación**: enseñar redes, radio y criptografía con hardware barato.
