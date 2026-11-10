# Plantillas de salida

Usa estas fichas con `SKILL.md`. Los campos sin datos llevan `HUECO`. Las propuestas de experimentos llevan `[INFERENCIA]`; sus umbrales son decisiones de diseño, no estadísticas del mercado.

Salida habitual: `research/<mercado-slug>-<AAAA-MM-DD>/`. Si el usuario indica otro destino, úsalo.

IDs únicos por ejecución: `S01` para fuentes, `P01` para precios, `R01` para reseñas y `F01` para hilos. Las fichas citan Sxx y las conclusiones citan fichas. Registra también las URL fallidas.

## 01-inputs.md

```markdown
# Inputs: <mercado>
Fecha de corte y consulta: <AAAA-MM-DD>
Mercado / geografía / tamaño: …
ICP: compra …; usa …
Producto propio: <producto o «no hay; research neutral»>
Tesis inicial: <tesis o «no aportada»>
Competidores elegidos y motivo: …
Ventana de novedades: <inicio> a <corte>
Reseñas históricas: anteriores a <corte menos 24 meses>

## Registro de fuentes
| ID | Competidor / alcance | URL | Fecha de consulta | Estado | Qué se obtuvo / qué se hizo en su lugar |
|---|---|---|---|---|---|
| S01 | … | … | … | OK / 403 / JS/vacío / moneda incorrecta / otro producto / inaccesible | … |

## Competidores
### <Competidor>
- [DATO] Home y propuesta literal: «…» (Sxx).
- [DATO] Producto, destinatario y CTA: … (Sxx).
- Precios: Pxx o HUECO.
- [DATO] Trial/freemium y límites verificados: … (Sxx).
- [DATO] Novedades fechadas dentro de la ventana: … (Sxx), o HUECO.
- [DATO] Vacantes, perfil y fecha: … (Sxx), o HUECO. No acredita crecimiento del equipo.

## Fichas de precio
### P01
| Campo | Valor |
|---|---|
| Competidor y producto/edición | … |
| Plan | … |
| Precio publicado | … / HUECO |
| Moneda | … |
| Mercado aplicable | … / HUECO |
| IVA / impuestos | incluido / excluido / HUECO |
| Periodicidad de facturación y compromiso | mensual / anual / … |
| Unidad | por plan / por asiento / por clínica / … |
| Mínimo de asientos / clínicas / permanencia | … / HUECO |
| Promoción y condiciones | ninguna explícita / … / HUECO |
| Límites y extras relevantes | … / HUECO |
| Fecha de consulta | … |
| Fuente y URL | Sxx; … |
| Verificado para comparar | sí / no; motivo y campos pendientes |

No compares unidades, monedas o periodicidades distintas. Si calculas un equivalente, muestra la fórmula y conserva el compromiso de pago. Un precio parcial puede registrarse, pero no cuenta como verificado mientras falten condiciones necesarias para compararlo.

## Fichas de reseña
### R01
| Campo | Valor |
|---|---|
| Competidor | … |
| Producto / edición identificable | … / HUECO |
| Plataforma | … |
| Estrellas | … / HUECO |
| Fecha de publicación y actualización | … / HUECO |
| País visible | … / HUECO |
| Rol / tamaño de clínica / relación con el ICP | confirmado con … / parcial / no consta |
| Fragmento tomado de | título / cuerpo |
| Frase literal | «…» (máximo 25 palabras; respeta además el límite total por fuente) |
| URL de la reseña / localizador estable | …; autor visible y fecha si no hay enlace individual |
| Fuente y fecha de consulta | Sxx; … |
| Señal | P / Q / C; motivo |
| Válida o excluida | válida / excluida; motivo |
| Actual o histórica | actual / histórica / fecha desconocida |
| Duplicados vinculados | ninguno detectado / Rxx (no contar dos veces) |

Una fecha desconocida no acredita actualidad. Sin producto identificable, excluye del recuento de ese producto hasta resolver el hueco. Una ficha localizada acredita un testimonio, no demuestra sus acusaciones.

### Índice de válidas y actuales
| ID | Competidor | Producto | Plataforma | Fecha | País | Señal | Relación con el ICP |
|---|---|---|---|---|---|---|---|

### Históricas (más de 24 meses; fuera del recuento actual)
| ID | Competidor | Fecha | Fuente | Por qué conservarla / qué exige verificar hoy |
|---|---|---|---|---|

### Excluidas
| ID | Competidor | Fuente | Motivo: otro producto / duplicado / sin producto / sin actualidad / no habla del producto |
|---|---|---|---|

## Foros y comunidades
### F01
- URL, fuente Sxx y fecha de consulta: …
- Fecha de publicación / actualización: … / HUECO.
- [DATO] Contexto, producto e ICP verificables: … / HUECO.
- Frase literal: «…».
- Señal P / Q / C y motivo: …
- Relación con Rxx si se republica el testimonio: …

## Sesgos y huecos
- Plataformas, estrellas, países, fechas e ICP sin verificar: …
- Material concreto a pegar si es inaccesible: URL, filtro y campos.

## Checklist de cobertura
| Input | Mínimo | Conseguido | Estado |
|---|---|---|---|
| Webs de competidores | 5 | … | OK / HUECO |
| Precios verificados | 5 competidores | … | … |
| Changelogs dentro de la ventana | 3 | … | … |
| Empleo con vacantes verificadas | 3 empresas | … | … |
| Reviews válidas y actuales | 50 | …; excluidas: …; históricas: … | … |
| Plataformas con reviews válidas y actuales | 2 | … | … |
| Hilos de foros | 5 | … | … |

Confianza en dolores: baja si hay menos de 50 reseñas válidas y actuales o una sola plataforma. Descargar una página no equivale a cubrir el input.
```

## 02-analisis.md

```markdown
# Análisis: <mercado>
Corpus: 01-inputs.md. No incorporar fuentes nuevas en esta fase.

## Consenso
- [DATO] Mensaje observado en <marcas>: … (Sxx, Syy).
- [INFERENCIA] Qué sugiere, limitado a la muestra: …
- Comparación de precios: Pxx / Pyy; condiciones coincidentes o HUECO.

## Hasta 7 creencias con base documental
### 1. <creencia; no confundir mensaje del proveedor con creencia del comprador>
- [INFERENCIA] Base: Sxx / Rxx / Pxx.
- Sería falsa si: …
- Señales contrarias: IDs … / HUECO.

## Dolores repetidos
| Dolor | IDs válidos y actuales | Menciones únicas | Nº de marcas | Marcas | Contraejemplo / solución observada | Frases o remisión a fichas |
|---|---|---|---|---|---|---|

Una ficha cuenta una vez por dolor. No incluir históricas, excluidas ni producto propio. No hay porcentajes sin denominador. Sin fichas, escribir HUECO. Usar 2-3 fragmentos solo si existen y el límite total por fuente lo permite.

## Apuestas observadas
- [DATO] Cambio, vacante o packaging: … (Sxx / Pxx, fecha).
- [INFERENCIA] Apuesta que podría indicar: …
- Crecimiento o liderazgo: métrica, periodo y fuente verificable / HUECO.

## Ángulos no observados en la muestra
- [INFERENCIA] Mensaje no encontrado en <páginas>: … (IDs).
- Objeción y cobertura pendiente para hablar del sector completo: …

## Huecos y confianza
- …
```

## 03-red-team.md

```markdown
# Red-team: <mercado>
Producto propio: <producto o «no hay; se omite el contraste»>.

## T1. <tesis candidata>
- [INFERENCIA] Steelman con IDs: …
- Dónde se rompe, contraevidencia con IDs y reacción de un competidor: …
- Contraste con producto propio: … / no aplica; investigación neutral.

| Evidencia ID | Qué respalda y qué no | Fuente: fiable / dudosa | Muestra: actual del ICP / parcial / no | Señal P / Q / C y motivo |
|---|---|---|---|---|

- Nota: alta / media / baja. Fichas actuales Q/C, marcas e ICP que lo justifican: …
- Confianza en el dolor: …; mantener baja con cobertura insuficiente aunque haya varios testimonios.
- Veredicto: pasa / pasa condicionada a … / se descarta; motivo.

## Balance
- Revisadas: …; pasan: …; condicionadas: …; descartadas: …
- Candidatas para fase 4: … (máximo 4; cero es válido).
```

`P`: lo dice el proveedor. `Q`: queja del cliente. `C`: el cliente relata una acción concreta. Una intención no es C; una acción relatada no equivale a una transacción auditada.

Nota según `SKILL.md`: alta exige Q/C en al menos 3 fichas válidas y actuales, 2 marcas y muestra del ICP; media exige al menos 2 fichas Q/C; baja si solo hay P, una ficha o inferencia. No recuperar históricas o excluidas para subir la nota. Ninguna nota valida por sí sola la hipótesis.

## 04-hipotesis.md (1-4 hipótesis)

```markdown
# Hipótesis de GTM: <mercado>
Resultado: … hipótesis. Si son menos de 3: motivo y material que falta.

## H1. <frase específica y falsable; vinculada a Txx>
Estado: sin validar

**Evidencia y alcance**
| ID | Afirmación respaldada | Señal P/Q/C | Fuente | Muestra | Nota y límite |
|---|---|---|---|---|---|

**Criterio de descarte**
- [INFERENCIA] Se descarta si …; experimento, población, plazo y umbral propuestos. El umbral es una decisión de prueba, no un dato del mercado.

**3 preguntas para clientes**
1. ¿Qué hiciste la última vez que …?
2. …
3. …

**Mensaje de posicionamiento si se valida**
«…»

**Ángulo de anuncio + mini-brief UGC (condicionado a validación)**
- Hook: «…»
- Dolor: … / HUECO.
- Prueba real grabable, fuente y permisos pendientes: … / HUECO.
- CTA: …
- Formato: …
- Quién lo graba: …

## Orden de validación y huecos
- Primero H… porque … (IDs); material pendiente: …
```

## 04-hipotesis.md (0 hipótesis)

```markdown
# Hipótesis de GTM: <mercado>
Resultado: 0 hipótesis.
Estado: sin validar

## Por qué no pasa ninguna
| Tesis | Veredicto | Evidencia / contraevidencia por ID | Supuesto sin demostrar |
|---|---|---|---|

No rescatar descartes ni preparar anuncios con pruebas inventadas.

## Qué material permitiría reabrirlas
| Hueco | Material concreto y de quién obtenerlo | Qué decisión permitiría tomar |
|---|---|---|

## Siguiente paso
- Orden de recogida o entrevistas y preguntas sobre el último caso real.
- No hay mensaje, anuncio o UGC validado que entregar.
```
