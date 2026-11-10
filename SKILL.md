---
name: gtm-research
description: Research de mercado y GTM en una sesión. Recoge webs de competidores, precios, changelogs, ofertas de empleo y reviews con ficha verificable; saca las creencias que el sector da por sentadas y los dolores que nadie resuelve; ataca cada tesis (steelman + red-team) y entrega de 0 a 4 hipótesis con criterio de descarte, preguntas para clientes, mensaje de posicionamiento y brief de UGC. Triggers: 'research de mercado', 'gtm research', 'entender un mercado', 'investiga el sector', 'hipótesis de GTM', 'qué no está resolviendo nadie', 'ángulos para atacar este mercado', 'antes de hablar con clientes', 'research para UGC/anuncios'.
version: 0.2.0
---

# GTM Research

Convierte material crudo de un mercado en hipótesis de GTM que se pueden validar con clientes y convertir en anuncios. Pueden salir de 0 a 4: el número lo decide la evidencia, no una cuota.

La IA aquí es sparring partner, no resumidor. Cada fase obliga a pensar: qué cree todo el sector, dónde se equivoca, qué dolor nadie resuelve y dónde se rompe nuestra propia tesis.

## Reglas fijas (todas las fases)

1. **Cada afirmación lleva fuente.** URL con fecha de consulta, ID de ficha (`R07`, `P03`) o fragmento pegado por el usuario. Sin fuente, no entra.
2. **Dato ≠ inferencia.** Marca cada punto como `[DATO]` (lo dice una fuente) o `[INFERENCIA]` (lo deduces tú). Nunca presentes una inferencia como dato.
3. **Cero números inventados.** Ni cuotas de mercado, ni tamaños, ni porcentajes que no salgan de una fuente. Si hace falta un número y no lo hay, escribe `HUECO: falta X`.
4. **Huecos visibles.** Si falta material, se dice en el informe. No se rellena con conocimiento general.
5. **Idioma del mercado.** Si el mercado es España, prioriza fuentes en español y cita las frases literales tal cual las escribe el cliente.
6. **Una carga HTTP no es cobertura.** Una página que devuelve 200 pero con "Cargando", otra moneda u otro producto cuenta como HUECO, no como dato.
7. **Nada sale validado.** Toda hipótesis lleva `Estado: sin validar` hasta que haya entrevistas o datos de conducta del ICP.

## Fase 0. Brief

Pregunta al usuario lo que falte (en un solo mensaje, no en goteo):

- **Mercado:** sector + geografía + tamaño de cliente (ej. "software de reservas y gestión para clínicas de fisioterapia en España, 1-10 fisios").
- **Producto propio** (opcional): qué es y para quién. Entra como referencia, no como competidor. Si no hay, el research es neutral y se omite el contraste de la fase 3 (anótalo).
- **ICP:** quién compra y quién usa.
- **Tesis inicial** (opcional): qué cree ya el usuario sobre el mercado.
- **Competidores:** lista del usuario. Si no la tiene, propón 5-7 y pide confirmación. Si no hay nadie a quien preguntar, elige, escribe por qué y sigue.

Crea la carpeta de salida: `research/<mercado-slug>-<AAAA-MM-DD>/` en el directorio de trabajo actual.

## Fase 1. Inputs (modo mixto)

Si están disponibles las skills `competitor-profiling` y `customer-research`, puedes usarlas, pero el resultado tiene que acabar en las fichas de abajo. Con 5 o más competidores, reparte la recogida en subagentes en paralelo (2-3 competidores por agente + 1 para reviews y foros) y pásales estas reglas y las plantillas.

**Por cada competidor (WebFetch / WebSearch):**
- Home: propuesta de valor (frase literal), a quién habla, CTA principal.
- Precios: una **ficha de precio** por plan (plantilla en `reference/plantillas.md`): moneda, mercado, IVA, periodicidad, unidad (por asiento o por plan), mínimo de asientos, promoción, fecha de consulta y si está verificado. Solo se comparan precios con la misma moneda, periodicidad y unidad.
- Changelog / novedades: en qué están invirtiendo en los últimos 6 meses.
- Ofertas de empleo: qué perfiles buscan. Una foto de vacantes es una señal de apuesta, no prueba de que un equipo crezca.

**Reviews: ficha por reseña.** Cada reseña tiene ID (`R01`, `R02`…), competidor, producto o edición concreta, plataforma, estrellas, fecha, país, si la frase es del título o del cuerpo, frase literal (máximo 25 palabras) y URL. Prioriza 2-4 estrellas.
- **Excluye** con motivo escrito: reseñas de otro producto de la misma marca (perfiles de empresa que mezclan productos), duplicados de la misma persona en otra plataforma y reseñas que no hablan del producto.
- **Marca como histórica** toda reseña de más de 24 meses. Cuenta aparte.
- Solo las fichas válidas y actuales cuentan para los recuentos de la fase 2.

**Foros y comunidades:** hilos en el idioma del mercado, con URL, fecha y una cita literal.

**Registro de fuentes:** cada URL intentada va a una tabla con fecha, estado (`OK`, `403`, `JS/vacío`, `moneda incorrecta`, `otro producto`, `inaccesible`) y qué se hizo en su lugar.

Estrategias de acceso (verifica el resultado en cada sesión):
- Los directorios de reseñas pueden bloquear el acceso. Prueba otra plataforma y registra el resultado de cada URL; no des por hecho que un filtro funciona.
- Si un foro no se puede leer, prueba una comunidad del mercado o pide un hilo concreto al usuario.
- Páginas de precios con JS: busca el JSON público que carga la página o prueba `curl`. Una página en español puede mostrar otra moneda: comprueba siempre el mercado.
- Empleo: las APIs públicas de Greenhouse (`boards-api.greenhouse.io/v1/boards/<empresa>/jobs`) y Lever (`api.lever.co/v0/postings/<empresa>`) pueden servir de alternativa. Verifica el identificador del portal; un resultado vacío no demuestra ausencia de contratación.

Cuando algo esté bloqueado, pide exactamente qué pegar: "Abre <URL>, filtra por 2-3 estrellas y pega 20-30 reviews aquí". No esperes material que no va a llegar: marca el hueco y avanza.

**Checklist de cobertura** (al final de `01-inputs.md`):

| Input | Mínimo | Conseguido | Estado |
|---|---|---|---|
| Webs de competidores | 5 | n | OK / HUECO |
| Fichas de precio verificadas | 5 competidores | n | |
| Changelogs | 3 | n | |
| Ofertas de empleo | 3 empresas | n | |
| Reviews válidas y actuales | 50 | n (excluidas: n, históricas: n) | |
| Plataformas de reviews distintas | 2 | n | |
| Hilos de foros | 5 | n | |

Si las reviews válidas y actuales no llegan a 50, o salen de una sola plataforma, avisa de que los dolores tendrán confianza baja.

Guarda todo en `01-inputs.md` siguiendo `reference/plantillas.md`.

## Fase 2. Análisis

Lee `reference/preguntas.md` y responde cada bloque usando solo el material de la fase 1.

1. **Consenso:** qué dicen todos los competidores igual (mensaje, precio, features, a quién apuntan).
2. **Hasta 7 creencias que el sector da por sentadas.** Solo las que tengan base en el material. Para cada una: de dónde sale, qué tendría que pasar para que fuera falsa y si hay alguna señal de que ya está pasando.
3. **Dolores repetidos sin resolver.** Agrupa los dolores de las fichas válidas y actuales. Cuenta menciones (una ficha cuenta una vez por dolor) y cuántas marcas distintas lo tienen. Lista los IDs de ficha de cada dolor y pega 2-3 frases literales. No cuentes las del producto propio. Anota el sesgo de cada plataforma (Trustpilot tira a quejas de soporte y facturación).
4. **Apuestas observadas.** Qué apuestan los competidores según changelog, empleo y precios. Habla de crecimiento o liderazgo solo si hay una métrica verificable con fuente.
5. **Ángulos que nadie usa.** Dónde está vacío el mensaje del sector.

Guarda en `02-analisis.md`.

## Fase 3. Red-team

Saca las tesis candidatas que dé el material (normalmente 4-6, más la tesis inicial del usuario si la dio). Para cada una:

1. **Steelman:** defiéndela como lo haría un inversor convencido, con la mejor evidencia del material.
2. **Dónde se rompe:** atácala. Qué supuesto falla, qué dato la contradice, qué haría un competidor para neutralizarla.
3. **Contraste con el producto propio** (si lo hay): busca en sus reviews y su web si tiene el mismo problema o si el mensaje choca con su modelo (ej. prometer "sin sorpresas" y cobrar IA por créditos). Si choca, la tesis pasa condicionada o se descarta.
4. **Evidencia en 3 ejes:**
   - **Fuente:** fiable (web oficial, reseña con ficha válida) o dudosa (terceros con interés, resúmenes de buscador).
   - **Muestra:** actual y del ICP / parcial / no.
   - **Tipo de señal:** `P` lo dice el proveedor; `Q` se queja el cliente; `C` el cliente actuó (cambió, pagó, se fue, contrató a alguien).
5. **Nota de evidencia:**
   - `alta`: señales `Q` o `C` en 3 o más fichas válidas y actuales, de 2 o más marcas, con muestra del ICP.
   - `media`: señales `Q` o `C` en 2 o más fichas, aunque la muestra sea parcial.
   - `baja`: solo señales `P`, una sola ficha o sobre todo inferencia.
   Muchas fuentes `P` no suben la nota: que varias marcas anuncien algo no prueba que el comprador lo pague.
6. **Veredicto:** pasa / pasa condicionada (di a qué) / se descarta, con una línea de motivo.

Guarda en `03-red-team.md`.

## Fase 4. Hipótesis

Quédate solo con las tesis que pasaron el red-team, hasta un máximo de 4. **Cero, una o dos es un resultado válido.** Si quedan menos de 3, escribe por qué y qué material haría falta para tener más. No rescates tesis descartadas para llegar a un número.

Para cada una, rellena la plantilla de `reference/plantillas.md`:

- **Hipótesis:** una frase, específica y falsable.
- **Estado:** sin validar.
- **Evidencia:** puntos con fuente o ID de ficha, tipo de señal y nota.
- **Criterio de descarte:** qué respuesta o dato concreto la mataría.
- **3 preguntas para clientes:** abiertas, sobre comportamiento pasado, no sobre opiniones futuras ("¿Qué hiciste la última vez que…?", no "¿Usarías…?").
- **Mensaje de posicionamiento:** una frase de propuesta de valor si se valida.
- **Ángulo de anuncio + mini-brief UGC:** hook (primera frase), dolor, prueba, CTA, formato (talking head, pantalla grabada, reacción, antes/después) y perfil de quien lo graba. La prueba tiene que ser algo real que se pueda grabar; si hace falta un dato que no existe, márcalo como HUECO.

Cierra `04-hipotesis.md` con un orden recomendado de validación (cuál primero y por qué) y los huecos de material que más afectan a la confianza.

## Al terminar

Resume al usuario en el chat, en corto:
- Las hipótesis (de 0 a 4) en una línea cada una, con su nota de evidencia.
- Los huecos más importantes.
- Las rutas de los 4 archivos.

No pegues los informes enteros en el chat. Para revisar si una ejecución está bien hecha, usa `reference/evaluacion.md`.
