# gtm-research

Skill para Claude Code que convierte fuentes de un mercado en **0 a 4 hipótesis de go-to-market**. Cada hipótesis lleva evidencia, criterio de descarte y preguntas para clientes. Todas salen con `Estado: sin validar`.

Puede entregar cero. Si ninguna tesis resiste el red-team, explica por qué y qué material falta.

## Qué hace

| Fase | Trabajo | Archivo |
|---|---|---|
| 0. Brief | Mercado, comprador, usuarios, competidores y producto propio opcional | — |
| 1. Inputs | Webs, fichas de precios y reseñas, novedades, empleo, foros y registro de accesos fallidos | `01-inputs.md` |
| 2. Análisis | Consenso, hasta 7 creencias con base documental, dolores por IDs y marcas, apuestas observadas | `02-analisis.md` |
| 3. Red-team | Defensa, objeciones, fuente, muestra, tipo de señal y veredicto | `03-red-team.md` |
| 4. Hipótesis | De 0 a 4, con descarte, preguntas sobre pasado y brief UGC condicionado | `04-hipotesis.md` |

Salida habitual: `research/<mercado>-<fecha>/`. Puede usarse otro destino si lo indica el usuario.

## Reglas

- Cada afirmación remite a una fuente con fecha o a una ficha con ID.
- Separa `[DATO]` de `[INFERENCIA]`. Si falta material, escribe `HUECO`.
- Las reseñas de otro producto y los duplicados se excluyen con motivo. Las de más de 24 meses se cuentan aparte.
- Los precios se comparan con moneda, mercado, periodicidad y unidad compatibles.
- Distingue `P`: lo dice el proveedor; `Q`: queja del cliente; `C`: acción relatada por el cliente. Muchas señales P siguen teniendo evidencia baja.
- No deduce crecimiento de una lista de vacantes ni de un lanzamiento.
- Sin producto propio, el research es neutral y omite ese contraste.

## Instalación

```bash
git clone https://github.com/rafamarcoss/gtm-research ~/.claude/skills/gtm-research
```

Reinicia Claude Code y comprueba que aparece la skill. Necesita herramientas de búsqueda web y lectura de páginas; para la recogida paralela, un entorno con subagentes. Sin acceso a una fuente, registra el hueco.

## Uso

> Investiga software de reservas y gestión para clínicas de fisioterapia en España, de 1 a 10 fisios. Compra el dueño y usan el equipo y la recepción. No tengo producto propio. Propón competidores y sigue.

También puedes invocarla con `/gtm-research`.

## Ejemplo y evaluación

El [ejemplo de fisioterapia en España](examples/fisioterapia-espana-2026-11/) conserva los cuatro informes y las notas de una ejecución desde Codex. Permite revisar fuentes, huecos, exclusiones y decisiones. No acredita instalación ni resultados idénticos en Claude Code.

La [rúbrica de evaluación](reference/evaluacion.md) puntúa trazabilidad, pensamiento no obvio, red-team, utilidad y robustez. Incluye seis casos límite y una checklist para revisar otras ejecuciones.

## Límites

- Los directorios de reseñas pueden bloquear el acceso. Los filtros y alternativas se comprueban por sesión.
- Una página descargada puede no contener el precio o mostrar otra moneda.
- Menos de 50 reseñas válidas y actuales, o una sola plataforma, implica confianza baja en dolores.
- La publicidad de un proveedor no demuestra que el comprador tenga el problema o pague por resolverlo.
- La investigación prepara la validación con clientes. No la sustituye.

## Licencia

MIT
