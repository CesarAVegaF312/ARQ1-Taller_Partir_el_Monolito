# Entrega · Taller «Partir el monolito»

- **Grupo:**
- **Integrantes:**
- **Fecha de la sesión:**

> Cómo usar esta plantilla: completen cada sección y borren los textos entre `<!-- -->`. Donde dice
> «pegar», peguen el bloque correspondiente del Markdown exportado por la herramienta (sección 04).

---

## 1. Mapa de servicios y métricas

<!-- Pegar aquí las secciones «1. Mapa de servicios» y «2. Métricas» del Markdown exportado. -->

### Por qué estas fronteras

<!-- Una fila por servicio. La justificación debe citar una cifra de la herramienta y una restricción del caso.
     Ejemplo de justificación insuficiente: «porque es otro dominio».
     Ejemplo suficiente: «Catálogo va aparte porque concentra el 75 % del tráfico y en el Black Friday escala ×9,6;
     separarlo baja las unidades de cómputo del pico de 323 a N». -->

| Servicio | Justificación (cifra + restricción del caso) |
|---|---|
| | |
| | |

### Registro de movimientos durante el caos

<!-- Después de cada carta pudieron hacer un movimiento. Anoten cuál hicieron y por qué, o por qué no movieron nada. -->

| Carta | Movimiento | Por qué |
|---|---|---|
| 01 · Black Friday | | |
| 02 · Falla en Pagos | | |
| 05 · Transportadora lenta | | |
| 04 · Cambio de la DIAN | | |
| 03 · Cierre mensual | | |
| 06 · El equipo se triplica | | |

---

## 2. Lectura del caos

<!-- Pegar aquí la sección «3. Cartas de caos aplicadas» del Markdown exportado y completar la respuesta del grupo
     debajo de cada carta. La respuesta explica la causa del impacto, no lo repite. -->

### La carta que su diseño pierde

<!-- ¿Cuál es y por qué aceptan perderla? Un párrafo. -->

---

## 3. Saga

<!-- Pegar aquí la sección «4. Saga» del Markdown exportado. -->

### Preguntas

1. **¿Cuál es el paso pivote y por qué?**
2. **¿Qué pasa si falla un paso antes del pivote? ¿Y uno después?**
3. **¿Usarían orquestación o coreografía para este caso? ¿Por qué?** Consideren quién necesita saber en qué
   estado está un pedido (servicio al cliente, por ejemplo).
4. **Segundo caso de uso que analizaron:** nombre y una diferencia importante frente a «Crear pedido».

---

## 4. Outbox e idempotencia

<!-- Pegar aquí la sección «5. Outbox» del Markdown exportado. -->

1. **¿Por qué Outbox elimina los pedidos huérfanos?**
2. **¿Por qué con Outbox aparecen más duplicados que sin él?**
3. **¿Cómo haría su consumidor para ser idempotente?** Digan qué guarda, dónde y durante cuánto tiempo.

---

## 5. ADR

<!-- Pegar aquí el ADR del grupo, hecho con plantilla_adr.md. -->

---

## 6. Supuestos del modelo que cuestionan (opcional)

<!-- Si alguna fórmula de la herramienta les parece injusta con su diseño, argumenten aquí: qué supuesto cambiarían,
     con qué valor y cómo cambiaría el resultado. -->
