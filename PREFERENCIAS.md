# Preferencias y restricciones vigentes

Actualizado al cierre del 18/09/2026.

## Viaje

- Base: febrero de 2027, salida y regreso a Santiago (SCL). En la nueva revisión del 18/09/2026 el usuario confirmó flexibilidad aproximada de ±2 días: buscar salidas 30/01–03/02 y llegadas de regreso 26/02–02/03. Informar siempre la duración real; las alternativas de 27, 28 o 32 días no son equivalentes.
- Cinco destinos prioritarios: Estambul/Santa Sofía, Jordania/Petra, Delhi/Agra/Taj Mahal, Beijing/Gran Muralla y Tokio. Orden flexible; mínimo tres jornadas completas útiles por destino, contando llegadas y traslados reales.
- Prioridad al costo, con itinerario realizable. Se aceptan low-cost, billetes separados y cambios de aeropuerto si el ahorro compensa riesgos y traslados.
- **Toda escala debe tener al menos tres horas**; ampliar cuando los trámites concretos lo exijan. No asumir protección por compartir aerolínea o resultado de búsqueda. `self_transfer: null` significa desconocido.
- Evaluar ampliar escalas de aproximadamente 24 h a unas 48 h para visitar. Reportar el tiempo real, días consumidos, hotel, transporte y efecto sobre los cinco destinos.
- Debe cruzarse el Pacífico para la vuelta al mundo principal. Europa, cuando se incluye, va antes de Estambul (hacia el este).
- Económica y mochila/equipaje de mano; dimensiones y peso exactos pendientes. El filtro de cabina no acredita la franquicia final.
- No volver a incorporar automáticamente los antiguos destinos europeos, Egipto o las siete maravillas. El Cristo Redentor fue descartado.

## Viajeros y cotización

- Se solicitó presentar el escenario **“Viaje en pareja · Ignacio y Selene”**.
- El usuario confirmó **dos personas**, ambas con **pasaporte chileno y ESTA vigente**. No se necesitan números de documentos para esta investigación.
- No hay presupuesto máximo fijado: buscar lo más barato con un itinerario realizable, incluyendo el costo de los márgenes entre billetes separados.
- La interfaz usa la revisión de `work/revision-destinos-20260918/`, que consulta dos adultos conjuntamente. Los resultados históricos para un adulto se conservan separados. Google Vuelos confirmó visualmente que los importes incluyen impuestos y comisiones para dos adultos; falta precio final del vendedor y franquicia concreta.

## Interfaz y documentación

- **Texto mínimo:** el usuario indicó que no leerá explicaciones largas. Dejar precios, fechas, vuelos y diferencias clave visibles; cálculos, horarios y consejos en desplegables. Conservar avisos que afecten la comparación (U-Connect, tren estimado, regreso largo).

- Español, resultados concretos, documentación continua y autonomía en decisiones rutinarias.
- HTML local con buena presentación, fotos reales, banderas y nombres de ambos.
- Pestañas para reducir scroll; margen superior de 12 px al quedar sticky.
- Globo interactivo con ruta, escalas, ciudades seleccionables y flechas para indicar el sentido.
- 18/09/2026: el usuario pidió viajes realmente distintos (no variantes de un vuelo), incluir Europa (Roma, París, Barcelona, Londres y Madrid) comparando tren y avión, la Amazonía y un súper viaje, y eliminar la página de escenarios. Hecho: cuatro viajes y sin pestaña de escenarios.
- Separar siempre tarifas observadas, estimaciones y gastos desconocidos. Mantener fuentes y fecha/hora original de consulta.

## Autorización

- Se autoriza investigar, analizar y mantener archivos/interfaz.
- No comprar ni reservar vuelos, enviar mensajes, crear cuentas, activar servicios de pago o alertas automáticas sin instrucción adicional.
- Ante bloqueo, límite o CAPTCHA, detener ese método; no eludirlo.

## Estado actual

Ver «Opciones vigentes» abajo (se regenera desde el JSON con `python3 work/update_docs_viajes.py`).

## Opciones vigentes

<!-- viajes:start -->
**Cuatro viajes distintos (18/09/2026).** Pasajes observados para dos adultos; total con alojamiento, trenes y extras estimados (fuentes en `work/viajes-supuestos.json`).

| Viaje | Fechas | Días | Destinos | Pasajes para dos (observado) | Total estimado para dos |
|---|---|---:|---:|---:|---:|
| Clásico | 02/02–28/02 | 27 | 5 | 5.506 | 7.258–7.871 |
| Amazonía + Asia | 02/02–04/03 | 31 | 6 | 6.359 | 9.335–10.524 |
| Europa + Asia | 16/01–28/02 | 44 | 10 | 5.600 | 10.849–12.808 |
| Súper viaje | 16/01–05/03 | 49 | 12 | 7.047 | 13.639–16.201 |

Predeterminado: Clásico. Europa obliga a salir en enero y la Amazonía vuelve en marzo; solo el Clásico cabe en la ventana 30/01–02/03. Nada comprado ni reservado.
<!-- viajes:end -->
