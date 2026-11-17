# ADR-001: Fronteras de servicio de la plataforma Inventarium v1

- **Estado:** propuesto | aceptado | reemplazado por ADR-___
- **Fecha:**
- **Decisores:** (integrantes del grupo)

> Un ADR registra **una** decisión: el contexto que la obligó, lo que se decidió, lo que se descartó y lo que
> cuesta. Debe caber en una página. Quien lo lea dentro de un año tiene que entender por qué se hizo así
> sin haber estado en la sala.

---

## Contexto

<!-- Las fuerzas que empujan la decisión, con cifras del caso. Máximo 6 viñetas.
     Ejemplo: «Equipo de 6 personas sin DevOps: cada servicio adicional es un pipeline, una base de datos y una
     guardia más». -->

-
-
-

## Decisión

<!-- En una o dos frases, en voz activa. Ejemplo: «Partimos Inventarium en N desplegables: …».
     Luego, la tabla de fronteras. -->

| Servicio / módulo | Tablas de las que es dueño | Se despliega aparte |
|---|---|---|
| | | sí / no |
| | | sí / no |

**Comunicación entre servicios:** <!-- qué va síncrono y qué por eventos -->

## Alternativas consideradas

<!-- Al menos dos. Para cada una, el costo concreto que la descartó, con una cifra de la herramienta. -->

### Alternativa A:

- **Qué ofrecía:**
- **Por qué se descartó:**

### Alternativa B:

- **Qué ofrecía:**
- **Por qué se descartó:**

## Consecuencias

### Positivas

-

### Negativas (lo que aceptamos perder)

<!-- Incluyan al menos una carta de caos que este diseño pierde. -->

-

### Riesgos y cómo los mitigamos

| Riesgo | Mitigación |
|---|---|
| | |

## Cuándo revisar esta decisión

<!-- Una condición observable que haría reabrir el ADR. Ejemplo: «Cuando el equipo supere 12 personas» o
     «Si el catálogo supera N peticiones por segundo fuera de campañas». -->
