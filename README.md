# NATS Connect IT–OT

## Descripción

Este documento resume cómo NATS puede facilitar la comunicación entre los sistemas de Tecnología Operativa (OT) y Tecnología de la Información (IT). También presenta el papel del **Unified Namespace (UNS)** y de los contratos de datos para hacer que la información sea reutilizable.

## IT vs. OT

| Área | Descripción | Ejemplos |
|---|---|---|
| **IT (Tecnologías de la Información)** | Sistemas orientados a la gestión de información y la toma de decisiones. | Aplicaciones de oficina, paneles y analítica |
| **OT (Tecnología Operativa)** | Sistemas y equipos que supervisan o controlan procesos físicos. | Máquinas, sensores y equipos de producción |

## ¿Qué es NATS?

NATS es un *broker* de mensajes: permite que los sistemas publiquen información y que otros sistemas se suscriban para recibirla.

Una forma sencilla de imaginarlo es como una radio: el publicador transmite en un canal y uno o varios consumidores se suscriben a ese canal.

## ¿Qué es un UNS?

**UNS** (*Unified Namespace* o espacio de nombres unificado) es una estructura compartida para organizar nombres, contexto y reglas de los datos.

> **NATS distribuye los mensajes; el UNS organiza la información.**  
> Juntos, ayudan a que los datos puedan reutilizarse entre aplicaciones.

## Arquitectura de referencia

```text
Equipo → Gateway (normalización) → NATS (distribución) → Aplicaciones
```

Las aplicaciones pueden incluir paneles, alarmas o sistemas de analítica.

### Flujo de datos

```text
Sensores → Red + NATS → Aplicaciones
```

Un gateway OT puede publicar datos en NATS y permitir que varios consumidores los reciban:

```text
Gateway OT → NATS → Panel
                   → Alarma
                   → Analítica
```

Este modelo permite que un publicador envíe información a varios consumidores sin establecer una conexión independiente con cada uno.

## Convención para nombres

Una estructura posible para los nombres es:

```text
planta.línea.equipo.nombre
```

Ejemplo:

```text
mx.ensamble.remachadora.contador1
```

La convención debería ser coherente y compartida entre los sistemas que producen y consumen los datos.

## Ejemplo de mensaje

```json
{
  "temperatura_c": 72.4,
  "nivel_pct": 63,
  "bomba_activa": true
}
```

> **Nota:** En JSON, los decimales se escriben con punto (`72.4`), no con coma.

## NATS y MQTT

MQTT puede ser una opción adecuada para dispositivos con recursos limitados, como microcontroladores, y para ciertos escenarios de comunicación punto a punto. La elección entre NATS y MQTT depende de los requisitos de arquitectura, dispositivos y comunicación.

## Ventajas de NATS

- Permite distribuir mensajes de un emisor a varios suscriptores.
- Facilita arquitecturas de comunicación distribuida.
- Puede ofrecer persistencia de mensajes mediante **JetStream**.

## Conceptos clave

1. **NATS** distribuye los mensajes.
2. **UNS** organiza la información y su contexto.
3. **El contrato de datos** define el significado y la estructura de los datos.

> «Un dato puede servir a muchos equipos sin que todos dependan entre sí».