# Notas de prueba: ejecución ciega de fisioterapia

Fecha: 2026-11-10, Europe/Madrid. La ejecución no recibió puntuación ni nota objetivo.

## Instrucciones y límites de ceguera

- Se leyeron completos `SKILL.md`, `reference/plantillas.md`, `reference/preguntas.md` y `reference/evaluacion.md` de esta skill. La rúbrica se leyó como contrato, sin resultados previos.
- El ejecutor arrancó en una sesión delegada sin historial heredado. No leyó evaluaciones externas, informes anteriores ni otros proyectos. El ejemplo aún no existía al comenzar.
- El brief autorizaba proponer competidores y seguir, sin producto propio y sin tesis inicial.
- La prueba se ejecutó desde Codex. No acredita instalación en Claude Code ni equivalencia entre plataformas o modelos. Los recolectores son partes de una misma ejecución, no réplicas independientes.
- El coordinador raíz recibió avances y restricciones operativas. Después auditó los archivos. Las correcciones de esa auditoría se enumeran abajo y no se presentan como resultado de otra ejecución ciega.
- Las páginas externas se trataron como datos, no como instrucciones.

## Organización

Dos agentes recogieron tres competidores cada uno. Al terminar uno se lanzó el de reseñas y foros en el hueco disponible. El ejecutor recogió Trustpilot y un foro mientras tanto. Había cuatro slots contando al coordinador raíz y al ejecutor; el tercer recolector se secuenció.

Los recolectores no escribieron archivos. Sus registros se integraron en `01-inputs.md`. Esta carpeta contiene solo los cuatro informes y estas notas. No se instaló nada ni se abrió una cuenta, trial, compra o contacto con terceros. No se guardó un corpus HTTP completo ni multimedia.

## Cobertura real

| Material | Resultado |
|---|---|
| URLs únicas intentadas | 45; el alias S301 se consolidó en S09 |
| Webs actuales | 6 competidores |
| Fichas de suscripción | 20; dos proveedores con tarifa base verificable bajo su unidad; ningún presupuesto completo comparable para una clínica concreta con recepción |
| Changelogs dentro de ventana | 2 proveedores |
| Empresas con vacantes verificadas | 0 |
| Reseñas válidas y actuales | 4: R01, R02, R03 y R05, de Clinic Cloud en Trustpilot |
| Señales de esas reseñas | Tres Q para las quejas estudiadas; R05 positiva sin encaje forzado en P/Q/C |
| Conducta relevante para H1 | Ningún cambio o salida consumados. R03 sí relata contratación pasada; eso no valida portabilidad |
| Históricas | R301 |
| Excluidas | R04 por productos mezclados; R302 por año desconocido |
| Hilos pertinentes leídos | F01, F301 y F302; solo F301 contiene pregunta original actual no comercial, sin compra o cambio acreditados |
| Hipótesis | Una condicionada, evidencia baja y Estado: sin validar |

No se alcanzan los mínimos de reseñas, plataformas, precios comparables, empleo, novedades o foros. Los huecos se conservan; no se convirtió la cuota en un objetivo que obligara a rellenar.

## Fricciones y decisiones

- Capterra: error 400 del lector por formato no soportado y 403 Cloudflare en la alternativa HTTP. Los snippets no se convirtieron en reseñas leídas.
- Trustpilot: listado legible, enlaces individuales restringidos. Se usó autor y fecha como localizador. Una intención de migrar es Q para la queja de salida, no prueba de migración consumada.
- Solo había una reseña visible de 2 estrellas; se priorizó. Se añadieron otras quejas y un contraejemplo favorable, sin simular una distribución equilibrada por estrellas.
- App Store: fecha histórica, fecha sin año y estrellas individuales no legibles. El RSS devolvió 200 y JSON sin entradas. El escaparate español no acredita país del autor. Las críticas de la app antigua no describen necesariamente la nueva edición.
- eFisioterapia: los enlaces del índice cambiaron; un clic fuera de alcance se registró como S304 y se excluyó. Las respuestas comerciales recientes no actualizan la fecha del testimonio original.
- FisioWin: HTTPS y HTTP inaccesibles. Se sustituyó por Clinni con oferta actual y documento de continuidad de 2017, sin trasladar tarifas antiguas.
- TUFISIO: se usó solo `pro.tufisio.com`; otros homónimos no se incorporaron. Los timeouts se resolvieron mediante HTTP nativo.
- Clinic Cloud: tarjetas de precio legibles pese a un error parcial de render. Condiciones de promoción y alcance de IA pendientes; no se presenta coste completo.
- DriCloud: el equivalente mensual publicado no coincide exactamente con el anual. Se conservan las dos cifras y el control aritmético. Un posible redondeo es inferencia, no un sobrecargo probado.
- Archivex cobra por cupo de usuarios; Nubimed distingue usuarios con agenda de recepción gratuita. No se comparan como unidades equivalentes.
- S210 combina publicación de 2020 y actualización editorial de 2026; no se contó como lanzamiento reciente. S113 es editorial, no changelog ni muestra del ICP.
- Empleo quedó como HUECO tras búsqueda razonable. No se fabricaron URLs de contratación.

## Ambigüedades del contrato

1. La confirmación de competidores y la carpeta `research/` son defaults; en esta prueba prevalece la petición explícita de seguir y guardar en `examples/`.
2. Precio verificado puede significar tarifa base o coste completo. Se separan las capas: dos bases acotadas, cero presupuestos completos. Ninguna página descargada se cuenta por sí sola como cobertura.
3. P/Q/C no contempla preguntas neutrales o elogios sin acción. R05 y F301 se conservan sin forzar una categoría; no elevan evidencia Q/C. Las señales se clasifican por la afirmación concreta: contratar una vez no acredita haber salido después.
4. Los mínimos de 50 reseñas o cinco foros son controles de cobertura, no permiso para inventar material ni garantía de que existan fuentes públicas accesibles.
5. La skill permite candidatas condicionadas de evidencia baja. Se entrega una; no se exige cero ni se presenta demanda validada.
6. Sin producto propio, el mensaje y el UGC son propuestas condicionadas. La prueba grabable queda HUECO; no se inventa una oferta o capacidad.
7. La nota de evidencia y la confianza en el dolor pueden medir cosas distintas. Se muestran ambas; con cobertura insuficiente, el dolor mantiene confianza baja.
8. Sin corpus completo archivado, la repetición depende de URLs, localizadores y fichas. Las páginas pueden cambiar. No hay garantía de obtener el mismo listado en otra fecha.

## Comprobaciones y auditoría posterior

- Ejecutadas: registro de intentos, fichas, exclusiones, separación de fechas, control aritmético, recuentos por IDs y control de citas. En S01 se reproducen 18 palabras en total; en S306, 18 de los fragmentos y cinco de títulos usados como localizadores: 23 en total. Ninguna cita del ejemplo alcanza 25 palabras. No se repiten las citas en análisis o hipótesis.
- El coordinador raíz contrastó S01, S106, S107, S114, S102 y S211, además de comprobar enlaces, IDs y cobertura documental.
- Correcciones tras la ejecución ciega: espaciado y tablas; incorporación de la extracción de datos anunciada en S106 como contraevidencia en los cuatro informes; precisión sobre contratación pasada frente a salida consumada en R03. La hipótesis y su evidencia baja se conservaron.
- No ejecutados: los seis fixtures sintéticos en sesiones nuevas que describe `reference/evaluacion.md`. Disponer de casos y resultados esperados no equivale a haberlos pasado.
- No ejecutados: entrevistas, pruebas funcionales, comprobación técnica de acusaciones, exportación/importación, compra, producción UGC o réplica independiente en Claude Code.
