# gtm-research

Skill para Claude Code que convierte material crudo de un mercado en 3-4 hipótesis de go-to-market listas para validar con clientes y convertir en anuncios.

No resume el mercado. Le obliga a Claude a pensar: qué cree todo el sector sin cuestionarlo, qué dolor se repite en las reviews y nadie resuelve, y dónde se rompe tu propia tesis.

## Qué hace

| Fase | Qué pasa | Archivo |
|---|---|---|
| 0. Brief | Te pide mercado, producto, ICP, tesis inicial y competidores | — |
| 1. Inputs | Lee webs, precios, changelogs y ofertas de empleo de cada competidor. Intenta sacar reviews y foros; si están bloqueados, te dice exactamente qué pegar | `01-inputs.md` |
| 2. Análisis | Consenso del sector, 7 creencias que todos dan por sentadas, dolores repetidos con recuento y frases literales, ángulos vacíos | `02-analisis.md` |
| 3. Red-team | Steelman de cada tesis, dónde se rompe, contraste con tu propio producto y nota de evidencia | `03-red-team.md` |
| 4. Hipótesis | 3-4 hipótesis con evidencia, criterio de descarte, 3 preguntas para clientes, mensaje de posicionamiento y brief de UGC | `04-hipotesis.md` |

Todo se guarda en `research/<mercado>-<fecha>/`.

## Reglas que sigue siempre

- Cada afirmación lleva fuente.
- Separa `[DATO]` de `[INFERENCIA]`.
- No inventa números. Si falta algo, escribe `HUECO`.
- Las preguntas para clientes son sobre comportamiento pasado ("¿qué hiciste la última vez que…?"), no sobre opiniones futuras.

## Instalación

```bash
git clone https://github.com/rafamarcoss/gtm-research ~/.claude/skills/gtm-research
```

Reinicia Claude Code y la skill aparece en la lista.

## Uso

Pide algo como:

> Haz un gtm research de software de reservas para clínicas de fisioterapia en España. Competidores: …

O escribe `/gtm-research`.

## Limitaciones conocidas

Probada en un research de CRM para pymes en España (6 competidores, 75 reviews, 4 hipótesis). Lo que encontramos:

- G2, Capterra, GetApp y Software Advice bloquean el acceso automático (403). Trustpilot sí funciona y es el plan B.
- Reddit no es accesible desde las herramientas web de Claude. Toca pegar los hilos a mano.
- Las páginas de precios que cargan con JavaScript a veces no se leen. La skill sabe buscar el JSON de precios o tirar de `curl`.
- Si las reviews salen solo de Trustpilot, los dolores tiran a soporte y facturación. La skill lo avisa en el informe.
- Las hipótesis son eso: hipótesis. La skill te prepara para las llamadas con clientes, no las sustituye.

## Licencia

MIT
