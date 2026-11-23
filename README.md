# Chasqui — Red Ciudadana Autónoma Offline

> Nombre provisional del proyecto. Los chasquis eran los mensajeros del
> Tahuantinsuyo que llevaban los mensajes corriendo de posta en posta. Esta red
> hace lo mismo: cada celular y cada nodo es una posta.

**Autor y titular:** Nicolás Bergese — Córdoba, Argentina
**Inicio del repositorio:** 22 de noviembre de 2026
**Licencia:** [Apache 2.0](LICENSE) — ver [NOTICE](NOTICE)
**Estado:** Fase 1 — investigación y arquitectura. **Todavía no hay software funcionando.**

---

## Qué es

Una red de comunicación ciudadana que funcione cuando **no hay internet ni
telefonía móvil**: apagones, emergencias, cortes de red o lugares sin cobertura.

Teléfonos Android, celulares viejos reutilizados y, más adelante, routers
compatibles se convierten en **nodos** de una red descentralizada que transporta
mensajes cifrados de nodo en nodo, sin servidores, sin internet y sin operadoras.

## Cómo funcionaría (resumen)

1. **Identidad sin registro.** Cada teléfono genera su propio par de claves; la
   dirección del usuario se deriva de su clave pública.
2. **Teléfonos que transportan.** Si el destinatario no está al alcance, el mensaje
   se guarda y viaja con los teléfonos que se cruzan (almacenar–transportar–reenviar).
3. **Nodos fijos como buzones.** Celulares viejos enchufados (con UPS / solar) y,
   en una fase posterior, routers compatibles guardan y reenvían mensajes.
4. **Radio de largo alcance opcional.** Placas LoRa de 915 MHz conectadas al
   teléfono o al nodo fijo extienden el alcance a kilómetros.
5. **Prioridades.** SOS > texto > ubicación > audio > fotos comprimidas.

Detalle en [docs/ARQUITECTURA.md](docs/ARQUITECTURA.md).

## Principios

- **No inventar criptografía ni protocolos de red** si existe uno probado.
- **No afirmar compatibilidades no probadas.** Todo lo que diga "compatible"
  debe tener una prueba documentada en `pruebas/`.
- **No modificar routers reales** sin un procedimiento de recuperación probado.
- **Trazabilidad real:** el historial de Git es el registro de avances. No se
  simulan fechas ni trabajo previo.

## Documentación

| Documento | Contenido |
|---|---|
| [docs/INVESTIGACION.md](docs/INVESTIGACION.md) | Proyectos existentes, licencias, regulación, hardware |
| [docs/ARQUITECTURA.md](docs/ARQUITECTURA.md) | Arquitectura propuesta |
| [docs/HOJA_DE_RUTA.md](docs/HOJA_DE_RUTA.md) | Fases y criterios de avance |
| [docs/LIMITACIONES.md](docs/LIMITACIONES.md) | Limitaciones conocidas |
| [docs/decisiones/](docs/decisiones/) | Registro de decisiones técnicas (ADR) |
| [BITACORA.md](BITACORA.md) | Registro cronológico de avances |

## Autoría

La idea de esta red es de Nicolás Bergese, quien declara haberla concebido años
antes de la creación de este repositorio. El registro verificable comienza con
el primer commit de este repositorio.

El desarrollo se realiza con asistencia de herramientas de IA (Claude, de
Anthropic); los commits asistidos lo indican en su mensaje.

## Licencia

Copyright 2026 Nicolás Bergese. Distribuido bajo la Licencia Apache 2.0.
El autor conserva la autoría y el copyright; terceros pueden usar, modificar y
redistribuir el código manteniendo el aviso de autoría ([NOTICE](NOTICE)).
Ver [ADR-0001](docs/decisiones/ADR-0001-licencia.md).
