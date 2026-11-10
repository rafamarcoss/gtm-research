# Evaluación de una ejecución

Esta rúbrica evalúa calidad del research, no valida una oportunidad comercial. Revisa los cuatro informes y sus fuentes. No premies el número de hipótesis: cero puede ser el resultado correcto.

## Rúbrica: 10 puntos

Cada criterio vale 0-2. Se admiten décimas justificadas con un ejemplo y un pendiente concreto.

| Criterio | 0 puntos | 1 punto | 2 puntos |
|---|---|---|---|
| Trazabilidad (2) | Afirmaciones sin origen o citas inventadas | Fuentes con fichas, fechas, exclusiones o recuentos incompletos | Registro de intentos, precios normalizados, reseñas por ID y conclusiones enlazadas; recuentos reproducibles |
| Pensamiento no obvio (2) | Resumen de funciones o frases genéricas | Inferencias específicas con poca contraevidencia | Tensiones del mercado, alternativas y señales contrarias; no convierte ausencia en exclusividad |
| Red-team honesto (2) | Todo pasa; solo defiende | Objeciones sin afectar veredictos | Contraevidencia cambia veredictos; tres ejes P/Q/C; cero aceptado; contraste omitido si no aplica; ninguna hipótesis validada |
| Accionable (2) | Recomendaciones sin forma de refutarlas | Preguntas o experimentos incompletos | Descarte, preguntas sobre pasado, prioridades y prueba UGC real o HUECO; con cero, plan concreto para obtener evidencia |
| Robustez y facilidad (2) | Se bloquea o rellena huecos | Avanza con ambigüedades o trabajo manual evitable | Maneja casos límite, mantiene salidas consistentes y límites visibles; registra fricciones y respeta confirmaciones ya autorizadas |

Una cita inventada, reseña excluida presentada como válida o hipótesis presentada como validada exige corregir antes de publicar, aunque la suma alcance 8.

## Casos límite reproducibles

Fixtures sintéticos de control, no evidencia del mercado ni reseñas publicadas. Reproduce cada caso en una sesión nueva: aporta el escenario, pide aplicar las fases afectadas y compara con el esperado. Registra fecha, agente/modelo si se conoce, resultado y desviaciones. Una revisión documental no equivale a ejecutar esa sesión.

| Caso y entrada de control | Resultado esperado | Fallo que detecta |
|---|---|---|
| Ninguna tesis sobrevive: T1 y T2 con contraevidencia y veredicto «se descarta» | Cuarto informe con 0 hipótesis, motivos por ID y material para reabrirlas. No rescatar descartes | Cuota artificial |
| Todas las reviews bloqueadas: S01 devuelve 403 y S02 JS/vacío; 0 fichas válidas | Registro de ambos intentos, alternativa y material concreto a pegar. Dolores HUECO y confianza baja; sin citas inventadas. Otras señales pueden sostener una candidata de evidencia baja | Relleno y bloqueo del flujo |
| Perfil mixto: R01 de Producto Agenda y R02 de Producto Nóminas, misma marca; estudio sobre Agenda | R02 excluida por otro producto; solo R01 puede contar. Si R01 está duplicada en otra plataforma, contar una vez | Contaminación y doble conteo |
| Precio: objetivo España/EUR; P01 USD sin mercado confirmado; S02 solo «Cargando» | P01 no verificada para comparar; S02 JS/vacío. Intentar JSON público/alternativa; si falla, HUECO. No comparar USD/EUR ni contar HTTP 200 como cobertura | Falsa normalización |
| Sin producto propio: brief neutral | Omitir contraste y anotarlo; no inventar empresa ni convertir un competidor en producto propio | Dependencia comercial |
| Solo proveedor: S01-S03 oficiales anuncian beneficios, sin Q/C | Señales P; evidencia baja aunque sean fuentes fiables. Nunca alta ni media. Estado: sin validar | Confundir propaganda con demanda |

Controles adicionales: más de 24 meses va a históricas; sin fecha no acredita actualidad; alta exige las condiciones de `SKILL.md`; con cobertura de reseñas insuficiente, confianza baja en dolores.

## Checklist para cualquier ejecución

- [ ] Brief: mercado, geografía, tamaño, comprador, usuarios y producto propio o ausencia.
- [ ] Competidores y elección justificados; respetar autorización para seguir sin confirmar otra vez.
- [ ] Corte, ventana de seis meses y umbral de históricas escritos.
- [ ] Cada URL intentada tiene fecha, estado y alternativa; vacío no cuenta como cobertura.
- [ ] Precios con plan, moneda, mercado, IVA, periodicidad, unidad, mínimo, promo, fecha y verificación; comparación compatible.
- [ ] Reseñas con ID, producto, plataforma, estrellas, fecha, país, título/cuerpo, cita, URL y validez con motivo.
- [ ] Históricas y excluidas separadas; duplicados identificados; producto propio fuera de dolores competitivos.
- [ ] Recuentos reconstruibles por IDs: una ficha por dolor y número de marcas.
- [ ] Conclusiones por IDs del corpus; datos e inferencias separados; umbrales experimentales como propuestas.
- [ ] Citas dentro del límite por cita y del total permitido por fuente; sin inventarlas ni atribuir un snippet a una reseña completa no leída.
- [ ] Sin crecimiento por vacantes/lanzamientos; sin vacío sectorial deducido de unas pocas páginas.
- [ ] Fuente, muestra y P/Q/C por evidencia; nota conforme al alcance. Solo P recibe baja.
- [ ] Menos de 50 reseñas válidas/actuales o una plataforma: confianza baja en dolores.
- [ ] Contraevidencia que descarta o condiciona cuando corresponde.
- [ ] Entre 0 y 4 hipótesis; todas con Estado: sin validar; menos de 3 explican huecos.
- [ ] Descarte, tres preguntas sobre pasado, mensaje condicionado y UGC real o HUECO; con cero, plan concreto de recogida.
- [ ] Cuatro archivos coherentes y enlaces válidos; notas de bloqueos/ambigüedades si es una prueba.
- [ ] Nota por criterio con justificación y pendientes; calidad metodológica no equivale a validación del mercado.

## Registro de revisión

| Ejecución y fecha | Trazabilidad /2 | Pensamiento /2 | Red-team /2 | Accionable /2 | Robustez /2 | Total /10 | Justificación y pendientes |
|---|---|---|---|---|---|---|---|
| Fisioterapia España, 2026-11-10; ejemplo tras auditoría | 1,8 | 1,6 | 1,8 | 1,8 | 1,6 | 8,6 | Fuentes por ID, cuatro candidatas y tres descartes. Quedan muestra parcial, precios completos y fixtures sin ejecutar. |

Ejemplo: [fisioterapia en España](../examples/fisioterapia-espana-2026-11/01-inputs.md). Sus [notas de prueba](../examples/fisioterapia-espana-2026-11/notas-prueba.md) distinguen controles ejecutados de límites pendientes.

La nota corresponde al ejemplo tras la auditoría descrita en sus notas. Es una revisión editorial de una ejecución, no un benchmark independiente ni una validación del mercado.
