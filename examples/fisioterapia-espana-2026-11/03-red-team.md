# Red-team: software de reservas y gestión para fisioterapia en España
Fecha de corte: 2026-11-10. Corpus: [01-inputs.md](01-inputs.md).
Producto propio: no hay; contraste omitido. Investigación neutral.

## T1. Reversibilidad comprobada al contratar puede pesar en la elección
- [INFERENCIA] Steelman: una clínica acumula historia, citas y bonos; S107 diferencia precisamente esos módulos al importar. R03 describe un obstáculo de salida. Una prueba de exportación/reconstrucción durante la evaluación podría reducir un riesgo concreto, frente a una promesa genérica de importación gratuita.
- [INFERENCIA] Dónde se rompe: R03 no demuestra el fallo técnico ni que sea clínica de fisioterapia de 1-10 profesionales. La queja puede referirse a un formato o procedimiento mal entendido. S102 ya ofrece entorno de prueba de migración, S106 anuncia extracción de datos y S211 revisión/reversión: el problema puede estar suficientemente resuelto. Importación y exportación no son lo mismo.
- [INFERENCIA] Reacción posible: un competidor publica un ejemplo de exportación, documenta qué módulos conserva y acompaña una prueba; no hay barrera competitiva demostrada.
- Contraste con producto propio: no aplica.

| Evidencia | Respalda / no respalda | Fuente | Muestra | Señal |
|---|---|---|---|---|
| R03/S01 | Queja e intención de cambiar; no salida consumada ni fallo auditado | Fiable como testimonio localizado | Actual, ICP parcial | Q para la queja; contratación pasada relatada no prueba salida |
| S107/P108-P110 | Coste/viabilidad por módulos de importación; no demanda ni exportación futura | Oficial fiable para oferta | Actual, oferta sectorial; comprador no observado | P |
| S102 | Comprobación de traspaso ya prometida; contraevidencia a vacío general | Oficial | Actual, oferta multiespecialidad | P |
| S106 | Extracción de datos anunciada; formato y reconstrucción no verificados | Oficial | Actual, oferta; no comprador observado | P |
| S211 | Revisión/reversión e importación asistida ya descritas | Oficial | Actual, muestra de compradores HUECO | P |

- Nota: baja. Una ficha Q actual, una marca, relación parcial con ICP; ninguna C de cambio o salida consumados.
- Confianza en dolor: baja por cobertura insuficiente.
- Veredicto: pasa condicionada a comprobar incidencia en propietarios del ICP y auditar una exportación real o sintética reproducible. Es pregunta comercial refutable, no oportunidad demostrada.

## T2. Ofrecer migración gratuita es un espacio sin cubrir
- [INFERENCIA] Steelman: R03 y los costes por módulos de S107 pueden hacer atractiva una entrada previsible.
- [INFERENCIA] Dónde se rompe: Clinic Cloud, Nubimed y Clinni ya anuncian gratuidad; DriCloud añade modalidad gratuita y alternativas asistidas. Archivex explicita alcance y coste. Una promesa absoluta se contradice con el corpus (S101,S102,S107,S211,S212).
- [INFERENCIA] Reacción posible: los competidores ajustan alcance comercial o explican su proceso actual.
- Contraste propio: no aplica.

| Evidencia | Alcance | Fuente | Muestra | Señal |
|---|---|---|---|---|
| R03 | Queja de salida, no ausencia de importadores gratuitos | Fiable como testimonio | Actual/ICP parcial | Q |
| S101,S102,S107,S211,S212 | Oferta de migración ya existente, con alcances distintos | Oficiales | Actual; oferta, no compradores | P |

- Nota: baja; una Q que no prueba la tesis.
- Confianza en dolor: baja.
- Veredicto: se descarta; oferta existente y confusión entre salir e importar. No se rescata como diferenciación.

## T3. La agenda móvil es una función que nadie resuelve
- [INFERENCIA] Steelman: R01 describe una fricción móvil; entre cabina y recepción es razonable investigar uso en varios dispositivos, pero este contexto no se acredita para su autora.
- [INFERENCIA] Dónde se rompe: R01 es una clínica de especialidad/tamaño desconocidos. S209 publica cambios móviles y S114 ajustes de app; R301/R302 no son evidencia actual de la nueva edición Archivex. No se ha probado ningún producto.
- [INFERENCIA] Reacción posible: demostración en dispositivo del cliente, ajustes de interfaz o formación.
- Contraste propio: no aplica.

| Evidencia | Alcance | Fuente | Muestra | Señal |
|---|---|---|---|---|
| R01 | Queja móvil localizada; no prevalencia ni disposición a pagar | Fiable como testimonio | Actual/ICP parcial | Q |
| S209,S114 | Inversión publicada en interfaces; no resolución auditada | Oficiales | Actual; oferta | P |
| R301,R302 | Solo control de exclusión: histórica/sin año, app distinta | Testimonios localizados | No actual comparable | No se usan como Q actual |

- Nota: baja; una Q actual y cero C de cambio o salida consumados.
- Confianza en dolor: baja.
- Veredicto: se descarta en su forma de vacío competitivo. Entrevistar sobre el último uso móvil puede ser útil, pero no justifica segunda hipótesis diferenciadora.

## T4. Añadir reservas que crucen fisio, sala y aparato crea una ventaja nueva
- [INFERENCIA] Steelman: fisioterapia sí necesita coordinar recursos; la especificidad está documentada en las páginas de producto, no en una queja de comprador (S203,S209).
- [INFERENCIA] Dónde se rompe: TUFISIO ya publica Booking 2.0 y DriCloud ya anuncia salas/camillas. F301 pregunta por programas, sin relatar colisiones o costes. No hay conducta de compra asociada.
- [INFERENCIA] Reacción posible: demostrar la función existente. No es necesario inferir desarrollo nuevo.
- Contraste propio: no aplica.

| Evidencia | Alcance | Fuente | Muestra | Señal |
|---|---|---|---|---|
| S203,S209 | Función/oferta actual y lanzamiento concreto | Oficiales | Actual; oferta sectorial, no compradores | P |
| F301 | Pregunta de elección, no dolor de recursos | Foro localizado | Actual, fisio ES, tamaño HUECO | HUECO; ni Q ni C |

- Nota: baja; solo P e inferencia.
- Confianza en dolor: baja/HUECO.
- Veredicto: se descarta como ventaja nueva y por falta de dolor observado.

## Balance
- Revisadas: 4. Pasan sin condición: 0. Condicionadas: 1 (T1). Descartadas: 3 (T2-T4).
- Fase 4: solo T1, máximo permitido: 4 sin buscar una cuota.
- Ninguna tesis está validada. Muchas fuentes oficiales no elevan la nota. El testimonio positivo R05 se mantiene como contraejemplo; no se transforma en C.
