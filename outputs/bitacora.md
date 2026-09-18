# Bitácora de investigación

Registro acumulativo. Cada actualización distinguirá precios nuevos, lectura de datos guardados, estimaciones, decisiones y asuntos pendientes. Los informes anteriores se conservan como referencia; una recomendación nueva se identifica explícitamente.

## 18/09/2026 — Comparación inicial ampliada

- Entorno original localizado y reutilizado; histórico copiado a `historical/`.
- Control SCL–IST satisfactorio. Dos lotes: 53 y 6 consultas; 495 filas de tarifas, no necesariamente únicas. Una consulta del lote reutilizó el control en caché.
- Se compararon ambos sentidos, fechas y aeropuertos alternativos. Se calcularon horarios con zonas y jornadas completas de visita.
- Candidatas A US$2.764; B US$2.888,75; C US$3.145. Precios mayoritariamente de Google Flights; Copa contrastada en su web.
- Multidestino visual US$2.132 para dos tramos, marcado como billetes separados, regreso vía Europa. No cumple circunnavegación ni demuestra ahorro de emisión conjunta.
- ZIPAIR devolvió error de sistema en su buscador. Pendiente validar sus tarifas directamente.
- Documentos: `comparacion-febrero-2027.md`, `resultados-febrero-2027.json`, `requisitos-y-equipaje.md`.

## 18/09/2026 — Auditoría específica de escalas, solicitada por el viajero

**Base tarifaria:** lectura de observaciones guardadas del mismo día; sin nuevas búsquedas de tarifas. **Investigación nueva:** condiciones oficiales de conexión y check-in.

- Registradas todas las escalas de A/B/C, diferenciando conexiones dentro de un resultado de enlaces entre reservas independientes.
- Detectados como puntos débiles: BKK 70 min, PTY 45 min, LIM 75 min en C y la llegada internacional → salida doméstica de ESB en C (90 min).
- Nueva variante **B2**, al mismo total observado US$2.888,75: DEL–BKK–PEK 17/02 16:05, Bangkok 2 h 05, llegada Beijing el 18; directo a Tokio el 22. Se validaron tres jornadas completas por destino y llegada SCL el 28.
- Nueva variante **B3**, mismo total aéreo observado: suma PTY 5 h 11; LAX 37 h 35 y llegada SCL 28/02 20:19. Provisión de gastos de conexión US$130–310, no cotización hotelera.
- Preferencia provisional actualizada: B2 para equilibrio; B3 si se prioriza una escala holgada en Panamá. A/B/C originales no se borraron.
- Confirmado: ZIPAIR no protege el vuelo sucesivo de otra aerolínea. HK Express ofrece protección condicionada a U-Connect, con cargo; falta comprobar inclusión. Air Arabia exige revisar sus condiciones documentales, además de la norma migratoria general.
- **Pendiente:** terminales de febrero, mínimos específicos THAI/Copa, producto Air Arabia, U-Connect, recuperación ante retrasos y confirmación directa del resto de tarifas.
- Entregables: `auditoria-escalas.md`, `auditoria-escalas.json`; cálculo reproducible: `work/audit_connections.py`.

## 18/09/2026 — Nueva regla explícita del viajero: mínimo 3 h y visitas de ~48 h

- Se establece mínimo de 180 min en **todas** las conexiones, sin excepciones por aerolínea o presunta emisión conjunta. Si los trámites exigen más, se amplía. No significa una conexión garantizada.
- Las recomendaciones A/B/C/B2/B3 quedan superadas. Se conservan los documentos con aviso visible.
- El optimizador ahora filtra conexiones internas con zonas horarias y rechaza cambios de aeropuerto en conexión. El mínimo predeterminado pasa a 3 h.
- Lote de 10 consultas: 9 lecturas de caché del mismo día y 1 nueva (NRT–SFO 25/02). No se presentaron como 10 tarifas recién consultadas.
- D: US$2.964, Beijing–Tokio directo, Los Ángeles 61 h 35, Panamá 5 h 11, regreso SCL 28/02 20:19.
- E: US$3.083, Beijing–Tokio y LAX–SCL directos, Los Ángeles 54 h 15, regreso 28/02 05:35.
- F: US$2.859; cumple márgenes pero añade largas esperas en HKG y noche en MEX; posible hotel consume parte del ahorro.
- D/E mantienen tres jornadas conservadoras por destino y añaden dos noches en Los Ángeles. Estimación aparte para LA: US$280–530; no se cotizaron hoteles ni entradas.
- Cambios nuevos: Pegasus directo a Amman y Air Astana vía Almaty (6 h 05). Verificados en fuentes oficiales política de equipaje Pegasus y exención Kazajistán para chileno; emisión y condiciones específicas siguen pendientes.
- Se mantuvieron como precios de itinerario las filas con escalas: no se afirmó que ese importe sea la suma de comprar todos los vuelos por separado.
- Entregables vigentes: `escalas-3h-y-visita-48h.md` y `.json`; código `work/build_stopovers.py`.


## 18 de septiembre de 2026 — Primera interfaz HTML

Se creó `index.html` con selector D/E/F, calendario, días útiles conservadores, detalle desplegable de cada vuelo, escalas y presupuesto con gastos de conexión opcionales. Se mantienen las fuentes y las fechas originales de consulta; no hubo una nueva cotización. El presupuesto distingue observados de estimaciones y excluye explícitamente los costos principales aún pendientes.

Generador: `work/build_html.py`; plantilla: `ui/template.html`. Verificados en Chrome los cambios de opción, horarios, totales, activación/desactivación de gastos y apertura del detalle de México. Comprobación visual de escritorio realizada. Diseño adaptable por CSS; no se ha verificado aún en un teléfono físico.


## 18 de septiembre de 2026 — Fotos y escenarios de pareja

La interfaz incorpora fotografías reales de Roma/Coliseo, París/Torre Eiffel, Londres/Big Ben, Madrid/Plaza Mayor, Barcelona/Sagrada Família y Estambul/Santa Sofía, con banderas y créditos/licencias de Wikimedia Commons en la página y `assets/photos/credits.json`. Se detuvo la obtención de otras imágenes tras respuestas HTTP 429; no se intentó eludir el límite. Las seis imágenes incorporadas se sirven desde archivos locales.

Los cinco escenarios europeos son inspiración opcional, con tres días propuestos y costos aún por cotizar; no modifican las rutas D/E/F ni los totales. Se pueden guardar o quitar mediante almacenamiento local del navegador. Cada alternativa presenta “Viaje en pareja · Ignacio y Selene”. Los precios consultados siguen siendo para un adulto; la referencia aérea para dos es solo multiplicación, sin confirmar disponibilidad de dos plazas, gastos compartidos ni requisitos de Selene.

Verificación en Chrome: renderizado de las cinco tarjetas con imágenes, banderas, selección y deselección de París; conservación de precios y calendario originales. Se regeneró index.html desde la plantilla y datos existentes.


## 18 de septiembre de 2026 — Globo interactivo y fotos de la ruta

Se incorporó un globo ortográfico giratorio con D3 7.9.0 local y tierra de Natural Earth (dominio público). Permite arrastre, flechas del teclado, zoom, giro opcional/pausa, selección de ciudades y vista de escenarios europeos. Los arcos se generan desde las piernas aéreas de la opción D/E/F activa, incluido el cruce del Pacífico. Son enlaces geográficos ilustrativos, no trazas reales ni cálculo de vuelo. Los puntos usan coordenadas aproximadas de aeropuertos; Amman y Delhi son accesos a Petra y Agra. Las escalas mantienen su duración y estado de protección desconocida.

Se añadieron fotografías de Petra, Taj Mahal, Gran Muralla, Tokio y Los Ángeles, de Unsplash con atribuciones y licencia en assets/photos/credits.json. Se usó una fuente alternativa accesible después del límite de Wikimedia anterior, sin nuevos intentos contra ese método bloqueado. Aparecen en las tarjetas del itinerario y en el detalle del globo. No se cambiaron vuelos, precios o fechas.

Verificaciones: sintaxis de globe.js, fotos JPEG locales válidas, cobertura de todos los aeropuertos y plantilla sin campos pendientes. En Chrome: globo renderizado, giro por arrastre, selección de Tokio con fotografía/horarios, vista europea, cambio a opción E sincronizado y fotos grandes del itinerario.

Fuentes de implementación: https://d3js.org/d3-geo/azimuthal y https://www.naturalearthdata.com/about/terms-of-use/ . Licencia fotográfica: https://unsplash.com/license .


## 18 de septiembre de 2026 — Pestañas y revisión de costos G

Se sustituyó la página extensa por seis pestañas accesibles con navegación de teclado, selector global de alternativa y una vista de destino a la vez junto al calendario. Se conserva el estado al cambiar pestañas y el globo se redimensiona al mostrarse. Las fotos, escenarios europeos, vuelos, fuentes y presupuesto permanecen disponibles.

Se evaluaron seis combinaciones compatibles con los vuelos documentados (dos Beijing–Tokio × tres LAX–SCL). Nueva opción G: Beijing–Tokio con HK Express vía Hong Kong por US$168 y regreso Copa vía Panamá por US$563. Total de pasajes US$2.864. Con provisión LA US$280–530, subtotal parcial US$3.144–3.394. Conserva 3 días completos conservadores por destino, escalas ≥3 h, 61 h 35 en LA y llegada SCL 28/02 20:19. No hubo búsquedas nuevas ni validación de vendedor.

D queda como equilibrio de tiempo (+US$100 por ahorrar 15 h 50); F mantiene el menor aéreo (US$2.859), pero si se incurre en la posible noche de México de US$60–130, G resulta US$55–125 menor con iguales gastos de LA. Se explicita que gastos desconocidos pueden cambiar la clasificación, que no es mínimo global y que dos pasajeros deben recotizarse.

Archivos nuevos: `work/optimize_ui_costs.py`, `outputs/costos-optimizados.json`, `outputs/costos-optimizados.md`, `ui/workspace.js`, `ui/workspace.css`. Comprobados en Chrome: pestañas excluyentes, globo al abrir su pestaña, selector global G→E→F, cambio de llegada a Tokio, destino individual y costos de México solo en F. Sintaxis JS y restricciones de la recombinación verificadas.


## Ajuste visual — margen de pestañas fijas

Se añadió un margen superior de 12 px a la barra de pestañas sticky, con fondo continuo para separar la navegación del borde superior al hacer scroll.


## Globo — sentido del recorrido

Se añadieron flechas sobre los arcos, orientadas desde el aeropuerto de salida al de llegada según la alternativa activa. Se recalculan con la proyección al girar o ampliar el globo y se ocultan en el hemisferio posterior. Los tramos intercontinentales largos muestran dos flechas; los cortos evitan sobrecargar los marcadores. La cabecera muestra la secuencia de destinos.


## Cierre de sesión — 18/09/2026

Se consolidaron README y preferencias, corrigiendo referencias antiguas a la fuente del HTML. Se preparó CIERRE_SESION.md con estado de entrega, ruta G completa, comparativa, límites de evidencia, pendientes, instrucciones de apertura/regeneración y prompt de continuación. outputs/cierre-sesion.json registra estado y huellas de los archivos principales. No hubo consultas nuevas, reservas ni compras al cierre. La carpeta no tiene Git inicializado; no hay commits de esta sesión. El servidor local puede dejar de estar disponible al terminar el proceso; index.html y assets/ permanecen guardados.

## Revisión posterior — destinos, dos viajeros y flexibilidad

El usuario pidió revisar los cinco destinos prioritarios y la opción de Terracota, buscando el menor costo con sentido común para billetes separados. Confirmó dos personas, ambas con pasaporte chileno y ESTA vigente; flexibilidad aproximada de ±2 días, sin presupuesto máximo. Se actualizaron preferencias: ventana de salida 30/01–03/02 y llegada 26/02–02/03.

Se conservaron los datos anteriores y se hicieron 49 consultas documentadas para dos adultos, más una consulta de control para un adulto, usando el entorno existente. Google Vuelos confirmó visualmente la base de precio para dos y la pieza de mano por pasajero. Una primera tanda se interrumpió por un error de formato con escalas nulas en vuelos directos; se corrigió y se continuó sin sobrescribir las observaciones guardadas. No hubo bloqueo ni CAPTCHA.

Resultados seleccionados: US$5.400 para dos, 2–28/02, doce vuelos físicos, condicionado a confirmar U-Connect en HK Express; US$5.601 sustituyendo Beijing–Tokio por directo, once vuelos; US$5.637, 2/02–2/03, diez vuelos, con Beijing–Tokio y LA–Santiago directos. Esta última deja 30 h 15 y una noche en LA entre billetes separados. La variante diurna con Xi’an llega el 2/03, cuesta US$6.079 de aéreo para dos y añade un tren todavía sin venta para febrero. Se comparó también regreso por Europa, US$5.783 de aéreo, y se exploró el orden inverso.

British Airways mostró SCL–LHR–IST del 2/02 como un itinerario para dos en su propia web, Economy Basic, $1.685,80 total, coincidente con US$1.686 redondeado en Google. No se ingresaron datos de pasajeros. Las demás tarifas requieren validación final con vendedor; misma aerolínea o resultado de buscador no se toma como prueba de protección. Las sumas, secuencia temporal, número de vuelos, fechas de regreso y márgenes internos ≥3 h se verificaron en el generador.

La revisión incluye Año Nuevo chino 6/02, cierre del Taj los viernes, Ramadán tentativo desde 8/02, exención china unilateral aún limitada a 2026 y alternativa vigente de tránsito 240 h, así como el aviso oficial actual sobre interrupciones regionales en Jordania. Wadi Rum es la adición terrestre preferida; Xi’an queda opcional por tiempo y costo.

Archivos: `outputs/revision-destinos-febrero-2027.md` y `.json`; datos crudos en `work/revision-destinos-20260918/`; consulta en `work/revision_destinos.py` y generador `work/build_revision_destinos.py`. El HTML no se regeneró: README y cierre advierten que G/D/E/F siguen siendo el snapshot anterior. No hubo compras, reservas, alertas ni mensajes a terceros.


## 18/09/2026 · HTML actualizado con las consultas para dos

A solicitud del usuario, la interfaz pasó a `revision-destinos-febrero-2027.json`: cinco alternativas, valores para ambos viajeros y referencia por persona sin redondear centavos. Predeterminada «Menos vuelos» (US$5.637, 10 vuelos, regreso 2/03). Se actualizaron todas las superficies: comparación, gastos estimados, vuelos, calendario hasta marzo, estancias y globo. Xi’an y el tren solo aparecen en Terracota; el regreso por Europa omite LA. Se preservan las seis pestañas, fotografías, escenarios guardables, controles del globo y sticky de 12 px. La provisión actual de LA es de una noche, US$200–350 por pareja. Fuentes anteriores guardadas en `historical/interfaz-antes-revision-dos/`. No se consultaron nuevas tarifas ni se reservó nada.

Validación: el generador comprobó sumas para dos adultos, duración de cada itinerario con zonas horarias, escalas mínimas de 3 h y una noche real en LA. En Chrome se recorrieron las cinco alternativas y se comprobaron subtotales, fecha de regreso, presencia de marzo, eliminación de LA en Europa, Xi’an/tren en itinerario y globo, desglose del LATAM del 1/03 al 2/03 y el interruptor de gastos de LA. Se revisaron las pestañas de Europa y Documentación y los enlaces locales. Sin errores ni advertencias de JavaScript observados. Se dejó abierta la comparación de costos con «Menos vuelos».


## 18/09/2026 · Menos texto en la interfaz

Por petición explícita del usuario, se redujo la lectura de todas las pestañas: tarjetas breves, una explicación de la alternativa seleccionada y detalles desplegables para costos, horarios, consejos y requisitos. Se mantienen visibles los importes para dos, fechas, número de vuelos, margen en LA y las condiciones que cambian el costo. Europa conserva fotos y selección de intereses con menos texto. La vista inicial de Costos pasó de 729 a 291 palabras según `body.innerText` en el mismo navegador (aproximadamente 60 % menos). Se verificaron apertura de tabla y desglose, cálculo de Terracota al quitar/reponer LA, consejos del itinerario, globo y documentación. Sin errores de JavaScript observados. Tarifas y fechas originales sin cambios.


## 18/09/2026 · Cierre para otro agente: verificar y mejorar costos

El usuario cerrará la sesión y pedirá una revisión independiente de tarifas y ahorro. Se rehízo `CIERRE_SESION.md` como traspaso vigente para dos adultos, con archivos de entrada, referencia de cinco alternativas, prioridades de búsqueda, verificación de vendedores, gastos de margen, restricciones y prompt de continuación. El cierre anterior y su generador se archivaron en `historical/cierre-antes-traspaso-20260918T055717Z/`.

Se corrigió `work/close_session.py`: ahora verifica el JSON actual contra los datos del HTML y genera un inventario con hashes sin sobrescribir el traspaso. Se actualizaron las referencias de continuidad y se señaló que cambiar fechas/rutas exige adaptar los calendarios y textos específicos del generador, no solo los precios del JSON. Sin búsquedas nuevas, reservas, compras ni modificaciones del itinerario en este cierre.


## 18/09/2026 · Herramientas GitHub para búsqueda y equipaje

A petición del usuario se revisaron repositorios y APIs para mejorar las búsquedas de vuelos y la información de equipaje. Resultado en `outputs/herramientas-busqueda-github.md`. Hallazgos: `fast-flights` 3.1.0 y `fli` 0.10.0 ya instalados ofrecen filtros no usados (autotransferencia, escala máxima, multi-city), calendario de precios y opciones de compra por vendedor; el cliente directo de `fli` devolvió 0 resultados en este entorno y la página de compra de Google carga los vendedores por XHR, así que la verificación de vendedor sigue requiriendo navegador. Con cuenta del usuario: Amadeus (2.000 llamadas/mes, `includedCheckedBags`/`includedCabinBags`), SerpApi (250/mes, `extensions` y `booking_token`), SearchApi (100 gratis, integrada en fast-flights). Kiwi Tequila es solo por invitación desde 2024. No existe un dataset abierto fiable de franquicias de equipaje. No se instaló ni contrató nada.

Estado de la auditoría de tarifas interrumpida: el lote `work/revision-destinos-20260918/fase-3-verificacion-results.json` (20 consultas para dos adultos, 06:05–06:06 UTC) quedó guardado; JSON vigente, informe y HTML no se modificaron.


## 18/09/2026 · Segunda pasada: tarifas verificadas, vendedores y cambio a Cathay

Se recotizaron para dos adultos los 13 bloques usados y 7 rutas nuevas (`fase-3-verificacion-results.json`, 06:05–06:06 UTC): sin cambios relevantes. Partir Santiago–Estambul por Madrid no ahorra; Haneda–Los Ángeles y el 1/02 tampoco. En Chrome se leyó la página de compra de Google (2 adultos) de 12 itinerarios: todos con la aerolínea como vendedor único o principal y con pieza de mano incluida (`vendedores-google-20260918.json`). BA Basic Economy US$1.686 (maleta US$120 por pasajero), Pegasus Saver US$311 con maleta, Cathay US$442 con maleta, Thai US$700 con maleta, Zipair/Copa/Air Arabia/LATAM con maleta de pago. HK Express US$335 incluye CN¥86 de tarjeta; su web indica que U-Connect se añade con cargo, importe no publicado.

Decisión: la opción predeterminada pasa a `cathay_febrero` (US$5.506 para dos, 27 días, Cathay PEK–HKG–HND en un solo billete, US$94 menos que el directo). Se añade `cathay_marzo` (US$5.542, regreso 2/03) y se retiran como tarjetas `menos_vuelos_marzo` y `directo_febrero`, conservadas en `retired_variants` con la variante vía Lima. Terracota y Europa se recalculan con Cathay (US$6.078 y US$5.686). Informe y JSON regenerados por `work/build_revision_20260918b.py`; HTML por `build_html.py`; versión anterior en `historical/revision-antes-cathay-20260918T062324Z/`. Enlaces de compra por itinerario generados con `fli` (`booking-links-20260918.json`). Nada comprado, reservado ni contratado.


## 18/09/2026 · Cuándo comprar y publicación en GitHub Pages

A pregunta del usuario se registró la recomendación de compra (ahora o en las próximas semanas; no después de mediados de noviembre) con las señales de precio de Google leídas el 18/09 (Cathay, Thai y Air Arabia «bajo»; el resto «típico») y datos públicos sobre ventanas de compra de Google Flights. Se añadió como desplegable «Cuándo comprar» en la pestaña Costos, en el informe y en el JSON (`purchase_timing`). Se creó `work/publish_pages.sh` y la carpeta `site/` (copia pública: HTML, fotos, D3, informes enlazados y preferencias, con `noindex`), publicada en el repositorio público `ignacioaraya1995/vacations-2027` con GitHub Pages: https://ignacioaraya1995.github.io/vacations-2027/. No hubo consultas de tarifas nuevas ni reservas.


## 18/09/2026 · Optimización de cadena y sistema de verificación de precios

Barrido de 20 consultas para dos adultos (`fase-4-barrido-results.json`, 13:21 UTC): fechas vecinas de cada bloque, IST en lugar de SAW, PEK–NRT y órdenes alternativos (Estambul–Delhi desde US$510; Amán–Pekín sin tarifas legibles). Nuevo `work/optimize_combination.py`: combina las 89 consultas con las reglas del viaje (tres jornadas por destino, escalas 3–12 h, LA 24–48 h con una noche, ventana de fechas). Mínimo realizable US$5.467–5.477 (Aegean IST–ATH–AMM el 7/02, verificado en Google a US$278 para dos, un vendedor, pieza de mano incluida). Ahorro de US$29–39 frente a `cathay_febrero` a cambio de 8 h 35 más de viaje o de un día menos en Tokio: no se adopta; queda en `retired_variants`.

Nuevo `work/price_watch.py`: recotiza los vuelos exactos de las cinco opciones, guarda instantáneas en `work/price-watch/` y reescribe `outputs/precios-vigilancia.md`. Dos ejecuciones (13:26 y 13:31 UTC): variaciones de −US$2 a −US$5; la tarifa Qatar–Iberia del regreso por Europa ya no aparece (más barato válido US$2.673, +US$548). El HTML muestra «Verificación de precios» y enlaces «Ver vendedores y equipaje» por vuelo. Plantilla launchd creada, no instalada. Sitio de GitHub Pages actualizado.


## 18/09/2026 · Cuatro viajes distintos, Europa con tren o avión, Amazonía y sin escenarios

A pedido del usuario (las cinco tarjetas eran el mismo viaje con un vuelo distinto) se rehicieron las opciones como viajes realmente distintos: Clásico (5 destinos, 2/02–28/02), Amazonía + Asia (Lima y Tambopata al volver, hasta el 4/03), Europa + Asia (Londres, París, Barcelona, Madrid y Roma desde el 16/01) y Súper viaje (Europa, Asia con Xi’an y Amazonía, 16/01–5/03). La cadena de Asia verificada es la misma en los cuatro. Se eliminó la página de escenarios europeos (pestaña, script y `localStorage`) y el globo ya no tiene la vista de ideas.

Búsquedas: 46 nuevas para dos adultos (fases 5–7). Entrar a Europa por Londres el 16/01 con Avianca cuesta US$1.424 para dos (US$2.154 el 13–15/01), así que Europa suma solo US$94 de pasajes frente al Clásico; el costo real está en 17 noches de hotel europeo. En Chrome se verificaron vendedor y equipaje de Avianca, Iberia MAD–FCO (Basic con pieza de mano), Pegasus FCO–SAW (Saver con pieza de mano), AJet (cobra la pieza de mano), LATAM LAX–LIM, LIM–PEM y LIM–SCL. No hay billete único LAX–Amazonía visible: se agrega una noche en Lima entre billetes.

Corrección: el decodificador mapea códigos IATA antiguos (VF = AJet, no Fly Armenia; W4 = Wizz Air Malta, no LC Perú; LL = LEVEL). El optimizador había descartado AJet por ese nombre. Con AJet el mínimo del Clásico baja US$70, pero AJet cobra la pieza de mano: no es un ahorro confirmado.

Supuestos con fuente en `work/viajes-supuestos.json`: trenes (seat61, Eurostar, Trainline), alojamiento (promedios 3★ de Booking.com, rango +30 %), lodge en Tambopata (US$1.106–1.646 para dos), ETA del Reino Unido (£20 por persona) y ETIAS (sin fecha). Tren vs avión: tren en Londres–París y Barcelona–Madrid; París–Barcelona en tren si se compra al abrir la venta (unas 3 h más lento que el avión); Madrid–Roma y Roma–Estambul en avión. Foto nueva: río Tambopata (Tim Buss, CC BY 2.0).

Código: `work/build_viajes.py` genera viajes, estancias, calendario (enero a marzo) y costos; `work/build_html.py` solo valida y embebe; `ui/app.js` renderiza todo desde datos; `work/booking_links.py` crea enlaces de compra; `work/update_docs_viajes.py` refresca las tablas de README, PREFERENCIAS y CIERRE. Versión anterior en `historical/antes-viajes-distintos-20260918T134557Z/`. Vigilancia de precios ejecutada sobre los cuatro viajes. Nada comprado ni reservado.
