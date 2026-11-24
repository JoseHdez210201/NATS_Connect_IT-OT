# NATS_Connect_IT-OT

---

##IT vs OT

IT - Tecnologías de la información (oficina, toma de decisiones)
OT - Tecnología operativa (equipos de producción)

---

##NATS - Broker (mensajes)
Funciona como un radio, sintonizas el canal (señal) que deseas escuchar.

##UNS (Unified NameSpace): Organiza nombres, contexto y reglas compartidas

NATS + UNS = Datos reutilizables

##Arquitectura de NATS:

Equipo → Gateway (Normalización) → NATS (distribución) → App final (panel, alarma, analítica)

##Métafora:
Sistema nervioso digital

Sensores → Red + NATS → Aplicaciones

NATS: un publicador, varios consumidores

Gateway OT → NATS → Panel, Alarma, analítica

##Normalización: planta.línea.equipo.nombre

Ejemplo: mx.ensamble.remachadora.contador1

Ejemplo de mensaje:
{
	"temperatura_c":72,4,
	"nivel_pct":63,
	"bomba_activa": true
}

##Y MQTT?

Se puede usar en microcontroladores, baja demanda de recursos, conexiones punto a punto.

##NATS ventajas:
- Conexiones de uno (emisor) a muchos (suscriptores)
- Red de comunicación distribuida
- Persistencia de mensajes (opcional) con JetStream

---

##Tres ideas principales:
1. NATS: Distribuye mensajes
2. UNS: Organiza la información
3. Contrato: Da significado

"Un dato puede servir a muchos equipos sin que todos dependan entre sí".