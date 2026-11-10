---
name: gtm-research
description: Research de mercado y GTM en una sesión. Recoge webs de competidores, precios, changelogs, ofertas de empleo y reviews; saca las creencias que el sector da por sentadas y los dolores que nadie resuelve; ataca cada tesis (steelman + red-team) y entrega 3-4 hipótesis con criterio de descarte, preguntas para clientes, mensaje de posicionamiento y brief de UGC. Triggers: 'research de mercado', 'gtm research', 'entender un mercado', 'investiga el sector', 'hipótesis de GTM', 'qué no está resolviendo nadie', 'ángulos para atacar este mercado', 'antes de hablar con clientes', 'research para UGC/anuncios'.
version: 0.1.0
---

# GTM Research

Convierte material crudo de un mercado en 3-4 hipótesis de GTM que se pueden validar con clientes y convertir en anuncios.

La IA aquí es sparring partner, no resumidor. Cada fase obliga a pensar: qué cree todo el sector, dónde se equivoca, qué dolor nadie resuelve y dónde se rompe nuestra propia tesis.

## Reglas fijas (todas las fases)

1. **Cada afirmación lleva fuente.** URL, review o fragmento pegado por el usuario. Sin fuente, no entra.
2. **Dato ≠ inferencia.** Marca cada punto como `[DATO]` (lo dice una fuente) o `[INFERENCIA]` (lo deduces tú). Nunca presentes una inferencia como dato.
3. **Cero números inventados.** Ni cuotas de mercado, ni tamaños, ni porcentajes que no salgan de una fuente. Si hace falta un número y no lo hay, escribe `HUECO: falta X`.
4. **Huecos visibles.** Si falta material, se dice en el informe. No se rellena con conocimiento general.
5. **Idioma del mercado.** Si el mercado es España, prioriza fuentes en español y cita las frases literales tal cual las escribe el cliente.

## Fase 0. Brief

Pregunta al usuario lo que falte (en un solo mensaje, no en goteo):

- **Mercado:** sector + geografía + tamaño de cliente (ej. "CRM para pymes en España, 5-50 empleados").
- **Producto propio:** qué es y para quién. Entra como referencia, no como competidor.
- **ICP:** quién compra y quién usa.
- **Tesis inicial** (opcional): qué cree ya el usuario sobre el mercado.
- **Competidores:** lista del usuario. Si no la tiene, propón 5-7 y pide confirmación antes de seguir.

Crea la carpeta de salida: `research/<mercado-slug>-<AAAA-MM-DD>/` en el directorio de trabajo actual.

## Fase 1. Inputs (modo mixto)

Si están disponibles las skills `competitor-profiling` y `customer-research`, úsalas para esta fase. Si no, sigue este proceso:

**Automático (WebFetch / WebSearch), por cada competidor:**
- Home: propuesta de valor, a quién habla, CTA principal.
- Página de precios: planes, precio de entrada, qué limita cada plan, si hay free trial o freemium.
- Changelog / novedades / blog de producto: hacia dónde están invirtiendo.
- Ofertas de empleo (web de careers, LinkedIn Jobs vía búsqueda): qué equipos crecen dice qué apuestas tienen.

**Intentar y, si está bloqueado, pedir al usuario:**
- Reviews de G2, Capterra (incluido Capterra España), Trustpilot y Google. Prioriza las de 2-4 estrellas: ahí está el dolor real.
- Hilos de Reddit, foros y comunidades en el idioma del mercado.

**Lo que ya sabemos que pasa** (prueba de 2026-11):
- G2, Capterra, GetApp y Software Advice devuelven 403. Trustpilot (es.trustpilot.com con filtro `?stars=2&stars=3&stars=4`) sí se lee y es el mejor plan B. Las App Store también funcionan.
- Reddit no es accesible para WebFetch ni para WebSearch. Pide al usuario que pegue hilos o usa foros locales (Forocoches en España).
- Páginas de precios que solo cargan con JS: busca el JSON de precios que carga la página (Zoho lo expone) o prueba con `curl` (WebFetch falla en algunas webs con "Header overflow").
- Para ofertas de empleo, las APIs públicas de Greenhouse (`boards-api.greenhouse.io/v1/boards/<empresa>/jobs`) y Lever (`api.lever.co/v0/postings/<empresa>`) dan más que la página de careers. LinkedIn devuelve 429.
- Con 5 o más competidores, reparte la recogida en subagentes en paralelo (2-3 competidores por agente + 1 para reviews y foros) y pásales estas mismas reglas de fuente y huecos.

Cuando algo esté bloqueado, pide exactamente qué pegar: "Abre <URL>, filtra por 2-3 estrellas y pega 20-30 reviews aquí". No sigas a la fase 2 esperando material que no va a llegar: marca el hueco y avanza.

**Checklist de cobertura** (al final de `01-inputs.md`):

| Input | Mínimo | Conseguido | Estado |
|---|---|---|---|
| Webs de competidores | 5 | n | OK / HUECO |
| Páginas de precios | 5 | n | |
| Changelogs | 3 | n | |
| Ofertas de empleo | 3 empresas | n | |
| Reviews | 50 | n | |
| Hilos de foros/Reddit | 5 | n | |

Si las reviews no llegan a 50, avisa de que la fase 2 tendrá confianza baja en la parte de dolores.

Guarda todo en `01-inputs.md` siguiendo `reference/plantillas.md`.

## Fase 2. Análisis

Lee `reference/preguntas.md` y responde cada bloque usando solo el material de la fase 1.

1. **Consenso:** qué dicen todos los competidores igual (mensaje, precio, features, a quién apuntan).
2. **7 creencias que el sector da por sentadas.** Para cada una: de dónde sale, qué tendría que pasar para que fuera falsa y si hay alguna señal en el material de que ya está pasando.
3. **Dolores repetidos sin resolver.** Agrupa los dolores de las reviews, cuenta menciones (una review cuenta una vez por dolor, sin contar las del producto propio) y pega 2-3 frases literales por dolor. Marca cuáles no resuelve bien ningún competidor y anota el sesgo de la fuente (Trustpilot tira a quejas de soporte y facturación).
4. **Lo que saben los ganadores.** Qué hacen los que más crecen (por changelog, empleo, precios) que el cliente nunca diría en una encuesta.
5. **Ángulos que nadie usa.** Dónde está vacío el mensaje del sector.

Guarda en `02-analisis.md`.

## Fase 3. Red-team

Saca 4-6 tesis candidatas de la fase 2 (más la tesis inicial del usuario, si la dio). Para cada una:

1. **Steelman:** defiéndela como lo haría un inversor convencido, con la mejor evidencia del material.
2. **Dónde se rompe:** atácala. Qué supuesto falla, qué dato la contradice, qué haría un competidor para neutralizarla.
3. **Contraste con el producto propio:** busca en sus reviews y su web si tiene el mismo problema o si el mensaje choca con su modelo (ej. prometer "sin sorpresas" y cobrar IA por créditos). Si choca, la tesis pasa como condicionada o se descarta.
4. **Nota de evidencia:** `alta` (varias fuentes independientes), `media` (una fuente sólida o varias débiles) o `baja` (sobre todo inferencia).
5. **Veredicto:** pasa / pasa condicionada (di a qué) / se descarta, con una línea de motivo.

Guarda en `03-red-team.md`.

## Fase 4. Hipótesis

Quédate con las 3-4 tesis que pasaron el red-team. Para cada una, rellena la plantilla de `reference/plantillas.md`:

- **Hipótesis:** una frase, específica y falsable.
- **Evidencia:** puntos con fuente y nota de evidencia.
- **Criterio de descarte:** qué respuesta o dato concreto la mataría.
- **3 preguntas para clientes:** abiertas, sobre comportamiento pasado, no sobre opiniones futuras ("¿Qué hiciste la última vez que…?", no "¿Usarías…?").
- **Mensaje de posicionamiento:** una frase de propuesta de valor si se valida.
- **Ángulo de anuncio + mini-brief UGC:** hook (primera frase), dolor, prueba, CTA, formato (talking head, pantalla grabada, reacción, antes/después) y perfil de quien lo graba.

Cierra `04-hipotesis.md` con un orden recomendado de validación (cuál primero y por qué) y los huecos de material que más afectan a la confianza.

## Al terminar

Resume al usuario en el chat, en corto:
- Las 3-4 hipótesis en una línea cada una, con su nota de evidencia.
- Los huecos más importantes.
- Las rutas de los 4 archivos.

No pegues los informes enteros en el chat.
