# Taller · Partir el monolito

Taller del **Módulo 4 — Arquitecturas: SOA, microservicios y REST** del *Diplomado en Diseño y
Arquitectura de Software*, Universidad de La Sabana. Modalidad virtual.

El taller trabaja sobre el caso **Inventarium Corp: elegir el estilo correcto con 6 ingenieros**.
En el taller del caso, los grupos eligieron un estilo arquitectónico y lo justificaron en papel. Aquí
lo van a someter a prueba: parten el sistema en servicios, ven en números lo que cuesta cada frontera,
aplican seis eventos de operación real y diseñan la saga que reemplaza a la transacción que dejó de existir.

> Un microservicio no se define por su tamaño sino por los datos de los que es dueño. Cuando la frontera
> parte un dato que un caso de uso necesita escribir de una sola vez, ese caso de uso se vuelve una
> transacción distribuida.

---

## Empiecen aquí

1. **Abran el taller en línea:** <https://cesaravegaf312.github.io/ARQ1-Taller_Partir_el_Monolito/partir_el_monolito.html>.
   Si prefieren trabajar sin conexión, descarguen el repositorio y abran [`partir_el_monolito.html`](partir_el_monolito.html)
   con doble clic: es un solo archivo, sin servidor ni instalación. Funciona en Chrome, Edge y Firefox.
2. **Escriban el nombre del grupo** en la esquina superior derecha. Aparece en la exportación.
3. **Trabajen en una sola copia por grupo.** Una persona comparte pantalla en la sala de grupo y las demás
   dictan. El estado se guarda en el navegador de esa persona: si cierra la pestaña, al volver sigue donde iba.
4. **Al final, exporten** (sección 04 de la página) y peguen el Markdown en la
   [plantilla de entrega](plantillas/plantilla_entrega.md).

---

## Objetivo

Que cada grupo pueda **defender con cifras** dónde traza las fronteras de un sistema y qué paga por
cada una, en vez de elegir microservicios o monolito por preferencia.

Al terminar, cada estudiante debe poder:

- Explicar por qué el dato, y no el tamaño del código, define el límite de un servicio.
- Calcular la disponibilidad compuesta de un caso de uso que atraviesa varios servicios síncronos.
- Identificar qué casos de uso exigen una saga y diseñarla: orden de los pasos, compensación o
  reintento por paso y ubicación del paso pivote.
- Explicar por qué el patrón Outbox elimina los pedidos huérfanos pero obliga a tener consumidores idempotentes.
- Relacionar el número de servicios con la capacidad real del equipo que los opera.

## Datos del caso que usa la herramienta

| Indicador | Valor (Exhibit 1 del caso) |
|---|---|
| Equipo | 6 personas: 5 desarrolladores y una arquitecta. Sin equipo de plataforma ni DevOps |
| Concurrencia normal | ~500 usuarios |
| Pico promocional | hasta 5.000 usuarios (10×), 3 o 4 veces al año, incluido el Black Friday |
| Latencia objetivo | p95 < 2 s en catálogo y checkout |
| Disponibilidad objetivo | 99,5 % mensual |
| Presupuesto | limitado, con prioridad en costo operativo bajo |

El caso completo está en [`caso/Caso_Inventarium_HBS.pdf`](caso/Caso_Inventarium_HBS.pdf).

---

## Formato de la sesión

- **Duración:** 2 horas, sincrónica por Teams.
- **Grupos:** de 3 a 4 personas, en salas de grupo.
- **Roles sugeridos dentro del grupo:** quien comparte pantalla y mueve tablas; quien lleva el registro de
  las decisiones para el ADR; quien defiende el diseño en la plenaria. Roten en cada ronda.

### Agenda

| Minuto | Ronda | Qué pasa |
|---|---|---|
| 0–10 | Encuadre | El docente proyecta la sección 00 (las restricciones). Votación rápida en el chat: «¿Inventarium debería usar microservicios? sí / no / depende». Se guarda el resultado para el cierre. |
| 10–40 | **Ronda 1 · Partir** (laboratorio 01) | 15 min con el diseño en **Vacío**: los grupos crean sus propios servicios. Después, 10 min comparando con los cuatro diseños de referencia. Los últimos 5 min vuelven a su diseño y lo ajustan. |
| 40–70 | **Ronda 2 · Caos** (laboratorio 02) | El docente anuncia las cartas una a una, cada 5 min. Todos los grupos la aplican a **su** diseño. Después de cada carta el grupo puede hacer **un solo movimiento**. |
| 70–100 | **Ronda 3 · Saga y Outbox** (laboratorio 03) | 20 min de saga sobre «Crear pedido» y un segundo caso de uso que elija el grupo. 10 min de Outbox. |
| 100–120 | Cierre | Dos grupos con diseños distintos presentan 5 min cada uno. Plenaria. Se repite la votación del inicio y se compara. Exportación. |

### Reglas del juego

- **Cada tabla tiene un solo dueño.** Si dos servicios necesitan el mismo dato, uno es dueño y el otro lo pide
  (o recibe una copia por eventos). No hay base de datos compartida.
- **Después de cada carta de caos, un movimiento:** mover una tabla, fusionar dos servicios o separar uno.
  El grupo anota en el registro qué movió y por qué. Ese registro alimenta el ADR.
- **La casilla «Pasos diferibles por eventos»** se puede activar en cualquier momento, pero quien la activa
  debe explicar en el ADR qué consistencia pierde a cambio.
- **No se discute la fórmula durante la ronda.** Si el grupo no está de acuerdo con un supuesto del modelo,
  lo anota y lo argumenta en el ADR. Esa discusión también se evalúa.

---

## Entregable

Uno por grupo, en el aula virtual, en el plazo que indique el docente.

1. **[`plantilla_entrega.md`](plantillas/plantilla_entrega.md)** completa, con el Markdown exportado de la
   herramienta pegado en la sección indicada y las respuestas a las preguntas de las cartas aplicadas.
2. **Un ADR** con la decisión de fronteras del grupo, usando [`plantilla_adr.md`](plantillas/plantilla_adr.md).

Se pueden entregar en un solo archivo `.md` o exportados a PDF.

### Rúbrica (5,0)

| Criterio | Puntos | Qué se espera |
|---|--:|---|
| Mapa de servicios justificado | 1,5 | Cada frontera se justifica con una cifra de la herramienta y una restricción del caso. No basta «porque es otro dominio». |
| Lectura del caos | 1,0 | Las respuestas a las cartas explican la **causa** del impacto (proceso compartido, hilos, dueño de la regla), no solo el síntoma. |
| Diseño de la saga | 1,0 | Orden de pasos y recuperación por paso coherentes, con el paso pivote identificado y una explicación de qué pasa si falla antes y después de él. |
| Outbox e idempotencia | 0,5 | Explican por qué desaparecen los huérfanos y por qué siguen apareciendo duplicados. |
| ADR | 1,0 | Decisión concreta, al menos dos alternativas descartadas con su costo, y consecuencias, incluidas las negativas. Si cuestionan un supuesto del modelo, lo argumentan. |

---

## Cómo calcula la herramienta

Cada laboratorio tiene una sección plegable **«Cómo se calcula»** con las fórmulas. En resumen:

- **Disponibilidad compuesta** = disponibilidad por servicio ^ servicios síncronos tocados.
- **Latencia p95 estimada** = base del caso + 6 ms por paso + 35 ms por llamada remota + terceros
  (pasarela 600 ms, transportadora 350 ms).
- **Saga** = el caso escribe en tablas de dos o más servicios.
- **Carga operativa** = servicios ÷ personas. Hasta 0,5 es sostenible; hasta 1, tenso; más de 1, inviable sin
  un equipo de plataforma.
- **Black Friday**: réplicas por servicio = ⌈2 × factor de carga⌉, con 2 réplicas de base; unidades de
  cómputo = réplicas × (1 + tablas del servicio).

Son modelos simples hechos para comparar diseños entre sí, no para predecir producción.

## Relación con el resto del módulo

- Presentación **02 · Microservicios**: «La aritmética que casi nadie hace antes de migrar», «El dato es el
  límite real», «Saga», «Outbox» y «Prerrequisitos organizacionales». Cada sección tiene aquí su laboratorio.
- **Taller de cohesión y acoplamiento**: es la misma idea un nivel más arriba. Una frontera de servicio con baja
  cohesión obliga a escribir en varios servicios a la vez, y eso es acoplamiento por la red.
- **Caso Inventarium**: este taller usa el mismo caso. La decisión que tomaron en papel ahora se puede medir.

## Archivos

```text
ARQ1-Taller_Partir_el_Monolito/
 ├─ README.md                    # esta guía
 ├─ partir_el_monolito.html      # herramienta interactiva (un solo archivo)
 ├─ caso/
 │   └─ Caso_Inventarium_HBS.pdf # el caso completo
 └─ plantillas/
     ├─ plantilla_entrega.md     # documento de entrega del grupo
     └─ plantilla_adr.md         # registro de decisión arquitectónica
```

## Referencias

- Fowler, M. (2015). *MonolithFirst*. martinfowler.com. <https://martinfowler.com/bliki/MonolithFirst.html>
- Garcia-Molina, H., & Salem, K. (1987). Sagas. *ACM SIGMOD Record, 16*(3), 249–259.
  <https://doi.org/10.1145/38714.38742>
- Kleppmann, M. (2017). *Designing data-intensive applications*. O'Reilly Media.
- Newman, S. (2021). *Building microservices: Designing fine-grained systems* (2.ª ed.). O'Reilly Media.
- Nygard, M. T. (2018). *Release it! Design and deploy production-ready software* (2.ª ed.). Pragmatic Bookshelf.
- Richardson, C. (2018). *Microservices patterns*. Manning. <https://microservices.io/patterns/>

---

*Inventarium Corp es una organización simulada con fines pedagógicos.*

---

## Créditos y uso académico

**Autor:** César Augusto Vega Fernández
**Programa:** Diplomado en Diseño y Arquitectura de Software, Universidad de La Sabana
**Año:** 2026

Material académico diseñado por el profesor **César Augusto Vega Fernández** para el módulo de
estilos y patrones arquitectónicos. Su propósito es exclusivamente educativo.

### Licencia de uso

Este material se distribuye bajo la licencia
[Creative Commons Atribución-NoComercial-CompartirIgual 4.0 Internacional (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.es).
