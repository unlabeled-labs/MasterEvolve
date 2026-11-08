# Ideas

## Índice
- [1 Composición del equipo](#1-composición-del-equipo)
- [2 Ideas](#2-ideas)
    - [2.1 Buscador y agregador de precios y ofertas locales (Ahorrando)](#21-buscador-y-agregador-de-precios-y-ofertas-locales-ahorrando)
    - [2.2 Reparto de una cartera de inversión (Repartia)](#22-reparto-de-una-cartera-de-inversión-repartia)
    - [2.3 Planificador de transporte público (Puntual)](#23-planificador-de-transporte-público-puntual)
    - [2.4 Gestión de stock según ventas (Stockea)](#24-gestión-de-stock-según-ventas-stockea)
    - [2.5 Diario de comidas (Manjare)](#25-diario-de-comidas-manjare)
    - [2.6 Recomendador de rutas y actividades (Planea)](#26-recomendador-de-rutas-y-actividades-planea)

## 1 Composición del equipo
Repositorio común: [unlabeled-labs/MasterEvolve](https://github.com/unlabeled-labs/MasterEvolve)

| Integrante | Usuario de GitHub |
| --- | --- |
| Juan José Casamitjana Benítez | [JuanJoCasamitjana](https://github.com/JuanJoCasamitjana) |
| Brayan Silvestre Valero | [Brai266](https://github.com/Brai266) |
| José Tomás Pérez Martínez | [JoseTomasPM](https://github.com/JoseTomasPM) |
| Javier Giral Sanchez | [PointedHammer](https://github.com/PointedHammer) |

Excepción al trabajo por parejas: el equipo está formado por cuatro integrantes. Motivo de la excepción: [POR COMPLETAR].

## 2 Ideas

### 2.1 Buscador y agregador de precios y ofertas locales (Ahorrando)
Ahorrando es una aplicación que ayuda a gastar menos en la compra. El usuario sube la foto de sus tickets y la app guarda qué productos compra y a qué precio en cada establecimiento. Con esa información compara su cesta habitual entre supermercados y tiendas locales de su zona, le avisa de ofertas cercanas y le resume cuánto gasta y dónde. No compra por él ni ofrece precios en tiempo real.

Está pensada para quien hace la compra del hogar y quiere ahorrar sin dedicar tiempo a comparar tienda por tienda. Hoy probablemente lo haga a ojo, mirando folletos o las webs de cada establecimiento. Como segundo perfil, un pequeño comercio local podría publicar sus ofertas para llegar a clientes de su zona.

Los datos salen de dos fuentes. La principal son los tickets que suben los usuarios: la app lee la foto y extrae el establecimiento, la fecha, los productos y sus precios, y los guarda sin conservar datos de pago. Como los tickets suelen traer solo el nombre abreviado del producto y no su código de barras, la app empareja los productos de distintas tiendas por nombre y categoría. La segunda fuente son las ofertas que publican los propios comercios locales. Al principio no habrá tickets de otras personas, así que el proyecto partirá de los del equipo y de voluntarios, y las comparaciones solo serán fiables en las zonas y productos con datos suficientes. Las webs de las cadenas quedan como posible ampliación, y solo si sus condiciones de uso lo permiten.

Resulta útil cada semana al planificar la compra, al decidir en qué tienda comprar y al seguir cómo evoluciona el gasto del mes o el precio de un producto habitual. Su valor está en partir de lo que el usuario compra realmente, no de un catálogo genérico de ofertas, y en ahorrarle la comparación manual. Su límite principal es que los tickets se leen con errores y que un mismo producto aparece con nombres distintos en cada tienda, por lo que la app debe mostrar cuándo una comparación no es fiable.


### 2.2 Reparto de una cartera de inversión (Repartia)
Problema: quien empieza a invertir no sabe cómo repartir su dinero entre activos ni qué riesgo asume con cada reparto. 

Decisión del usuario: una persona que ahorra una cantidad fija al mes y quiere decidir qué porcentaje destina a cada una de 4 o 5 categorías amplias (por ejemplo renta variable global, renta fija, oro y liquidez), sabiendo cuánta pérdida podría soportar en un año malo. No elige acciones concretas ni decide cuándo comprar o vender. Hoy lo resuelve copiando repartos de artículos o foros, usando la recomendación de su banco o dejándolo todo en una cuenta de ahorro.

Resultado que recibe: para su horizonte de inversión y su tolerancia a la pérdida, un reparto propuesto, el rango de resultados que podría tener a 1, 5 y 10 años (con su incertidumbre) y la comparación con repartir a partes iguales. No es asesoramiento financiero y no promete rentabilidades.

Enfoque: Descargar series de precios y calcular rentabilidades. Estimar riesgo y volatilidad, con intervalos de confianza. Predecir la volatilidad con GARCH y XGBoost frente a una media móvil. Optimizar el reparto con Markowitz, simular escenarios con Monte Carlo y compararlo con un reparto equitativo. 

Origen de los datos: precios históricos diarios de yfinance (Yahoo Finance) de un conjunto pequeño de fondos cotizados (ETF) que representen cada categoría, con 10 o más años de historia. Una fila es un activo en un día, con su precio de cierre ajustado. Hay que revisar las condiciones de uso de Yahoo Finance, pensadas para uso personal, y tener preparada una fuente alternativa (por ejemplo Stooq) por si cambian el acceso.

MVP: con 4 o 5 ETF, el usuario indica su tolerancia a la pérdida y ve el reparto propuesto, su riesgo y la simulación frente al reparto equitativo.

Se deja fuera: acciones individuales, impuestos y comisiones, aportaciones periódicas con reequilibrado automático, criptomoneda y cualquier recomendación personalizada de producto financiero.

Duda principal y cómo se comprobaría: que un reparto optimizado con datos pasados no sea mejor que el equitativo cuando se aplica a datos nuevos. Se comprobaría con una evaluación por ventanas (optimizar con los años anteriores, medir en el año siguiente y repetir) y se mostraría el resultado aunque el reparto equitativo gane. Riesgo ético: no presentar los resultados pasados como una predicción.

**Verificación de datos (8 de noviembre de 2026).** Acceso confirmado: la consulta diaria de SPY al servicio de gráficos de Yahoo Finance, el que utiliza yfinance, respondió con precios y metadatos. No se ha probado la librería yfinance en sí. Limitaciones: yfinance no es oficial y depende de que Yahoo mantenga ese servicio; las condiciones de uso de Yahoo no se han podido comprobar (la página de términos consultada devolvió un error 404), así que queda pendiente confirmar si permiten este uso y qué se puede publicar. Requisitos: no subir al repositorio los datos descargados, solo el script de descarga con las fechas y los tickers, y tener identificada una fuente alternativa por si el acceso falla.

### 2.3 Planificador de transporte público (Puntual)
Problema: quien debe llegar a una hora no sabe qué ruta de tren o autobús es más fiable. Los horarios teóricos no muestran los retrasos habituales.

Usuario: quien se desplaza con un horario fijo (estudiante o trabajador que llega a una hora a clase u oficina) y tiene dos o tres rutas posibles. Hoy mira el horario oficial o una aplicación de rutas, que le dice cuándo debería pasar el transporte pero no con qué frecuencia llega tarde, y acaba saliendo con un margen de seguridad a ojo. Una consulta típica: "Debo llegar a las 9:00, ¿qué ruta tiene menos riesgo de llegar tarde y cuándo debo salir?".

Enfoque: Construir un histórico de puntualidad por línea, franja horaria y día. Clasificar la probabilidad de retraso, con clases desbalanceadas, y compararla con una referencia basada en la media por línea. Comparar dos o tres rutas y recomendar el margen de salida.

Origen de datos: dos tipos de fuente que hay que combinar. Los horarios teóricos salen de ficheros GTFS publicados por los operadores o por el Punto de Acceso Nacional de transporte (nap.transportes.gob.es). Los retrasos reales salen de los feeds GTFS-Realtime del operador (por ejemplo los de Renfe Cercanías o los de la EMT o el consorcio de la ciudad elegida), que dan el estado en el momento de la consulta pero no guardan histórico. Por eso el histórico habrá que construirlo guardando una consulta cada pocos minutos durante varias semanas, y eso condiciona el tamaño y el plazo del proyecto. Falta por confirmar la ciudad y el operador, y si su feed en tiempo real es abierto y de uso libre (algunos piden registro o clave).

MVP: una ciudad, una o dos líneas con dos rutas alternativas entre el mismo origen y destino, con 3 o 4 semanas de datos recogidos por el propio equipo. El usuario indica la hora de llegada y ve la probabilidad de retraso de cada ruta y la hora de salida recomendada.

Se deja fuera: planificación de viajes de cualquier origen a cualquier destino, alertas en vivo, otras ciudades, transbordos complejos y predicción por incidencias (obras, huelgas, meteorología).

Duda principal y cómo se comprobaría: si el feed en tiempo real es estable y trae retrasos suficientes para que haya algo que predecir. Esta semana se guardaría una consulta cada pocos minutos durante 2 o 3 días y se mediría cuántos viajes tienen retraso registrado, cuántos huecos hay en los datos y si la proporción de retrasos permite entrenar (si hay muy pocos retrasos, el modelo no mejorará la media por línea). Esa prueba decide también si la ciudad elegida sirve.

**Verificación de datos (8 de noviembre de 2026).** Confirmado: Renfe publica un GTFS estático descargable (por ejemplo, el de alta velocidad y larga distancia, un zip que responde correctamente) y un feed GTFS-Realtime de actualizaciones de viaje (gtfsrt.renfe.com/trip_updates, en formato binario y JSON) que responde sin clave de acceso. En una consulta devolvió 299 viajes, 121 de ellos con retraso mayor que cero, expresado en segundos por viaje y parada. Limitaciones: el feed solo da el estado actual, sin histórico, por lo que hay que consultarlo periódicamente y guardar los resultados; no se ha comprobado qué servicios cubre (Cercanías, media distancia, etc.) ni que sus identificadores de viaje coincidan con los del GTFS estático que se elija; no se ha localizado su licencia o condiciones de reutilización; y la web del Punto de Acceso Nacional (NAP) no se ha podido verificar. Requisitos: elegir un servicio concreto, comprobar ese cruce de identificadores y consultar las condiciones de uso antes de publicar nada.

### 2.4 Gestión de stock según ventas (Stockea)
Problema: quien gestiona una tienda no sabe qué productos reponer, cuáles reducir y cuáles inmovilizan dinero. Decide por intuición o revisando hojas de ventas a mano. Limpiar las transacciones, incluidas cancelaciones y devoluciones.

Enfoque: Clasificar los productos por rotación (alta, media, baja). Predecir las ventas de la semana o mes siguiente y compararlas con una referencia sencilla, como repetir la semana anterior. Mostrar una lista de productos a reponer, mantener o reducir.

Obtención de datos: Online Retail II, de UCI, con transacciones reales de un comercio electrónico entre diciembre de 2009 y diciembre de 2011. Una fila es una línea de factura (producto, cantidad, fecha, precio y cliente); las facturas que empiezan por "C" son cancelaciones. Es una fuente válida de ventas reales, pero no contiene existencias ni plazos de reposición, así que con ella solo se puede prever la demanda, no decidir cuánto pedir.

Alcance de la recomendación: la lista indica qué productos tienen una demanda prevista alta, estable o en descenso, y se presenta como una señal para que alguien de la tienda revise, no como una orden de compra. Para recomendar cantidades harían falta el stock actual, el plazo del proveedor y el coste de cada producto. El producto se plantearía con un responsable de una tienda real (o de un comercio conocido de los integrantes) que revise una muestra de las recomendaciones y diga si las tomaría.

MVP: los 50 productos más vendidos, agrupados por semana, con la previsión de la semana siguiente frente a repetir la semana anterior y una lista de tres columnas (reponer, mantener, reducir) con el motivo de cada una.

Se deja fuera: cantidades a pedir, stock de seguridad, costes y márgenes, estacionalidad por país y productos con muy pocas ventas.

Duda principal y cómo se comprobaría: si la previsión mejora de verdad a la referencia sencilla, y si las recomendaciones tienen sentido para quien gestiona una tienda. Se comprobaría reservando las últimas semanas como prueba (la previsión nunca ve esos datos) y comparando el error con el de repetir la semana anterior, y después enseñando 15 o 20 recomendaciones a una persona de una tienda para que las valore. Hay que avisar de que los datos son de venta online mayorista y pueden no representar a una tienda física.

**Verificación de datos (8 de noviembre de 2026).** Acceso confirmado: la descarga del conjunto Online Retail II desde el repositorio de UCI (zip de unos 45,6 MB con un fichero online_retail_II.xlsx) y su ficha indican 1.067.371 registros. La licencia que figura en la página es Creative Commons Attribution 4.0 (CC BY 4.0), por lo que se puede usar y transformar citando al autor (Daqing Chen) y el DOI 10.24432/C5CG6D. Limitaciones: no se ha abierto el fichero ni revisado su calidad; según la ficha, procede de una empresa del Reino Unido sin tienda física y con muchos clientes mayoristas, vende sobre todo artículos de regalo, y no incluye existencias ni plazos de reposición.

### 2.5 Diario de comidas (Manjare)
Manjare es una aplicación que ayuda a comprobar si los productos que alguien compra y come cumplen un objetivo nutricional que ya tiene. El usuario introduce el objetivo (por ejemplo, un mínimo de proteínas o hierro al día, o un máximo de azúcar), que le ha dado un dietista o que fija él mismo, y los alérgenos que debe evitar. Después identifica los productos que consume, por código de barras o foto de la etiqueta, e indica la cantidad. La app suma lo que aportan al día o a la semana, lo compara con su objetivo y señala qué falta, qué sobra y qué productos contienen un alérgeno o no se pueden evaluar. No calcula las necesidades del usuario a partir de su peso o altura, no monta menús ni recetas, no da diagnósticos médicos ni sustituye a un nutricionista.

Está pensada para quien ya tiene un objetivo nutricional, propio o recomendado por un dietista, y no sabe si lo que compra y come lo cumple. Hoy probablemente lo compruebe leyendo etiquetas una a una, con una hoja de cálculo o con una app de recuento de calorías que no avisa de alérgenos ni de datos que faltan. Como segundo perfil, un nutricionista podría definir el objetivo de su paciente y revisar el resultado, pero no es necesario para la primera versión.

Los datos salen de dos fuentes. La información nutricional y los alérgenos de los productos proceden de Open Food Facts, una base de datos abierta y colaborativa con más de 4 millones de productos, que se consulta por código de barras. Es colaborativa, por lo que habrá productos que no aparezcan o que tengan campos vacíos o erróneos, sobre todo en alérgenos; en esos casos el usuario puede completar el producto a mano o con la foto de la etiqueta, y la app lo marca como dato introducido por el usuario. La segunda fuente es el propio usuario, que aporta su objetivo, sus alérgenos y las cantidades consumidas. Las fórmulas de necesidades nutricionales y los menús completos quedan para una fase posterior, cuando el cálculo con objetivos dados funcione.

Resulta útil al comprar, cuando el usuario escanea un producto para saber si encaja con su objetivo y si contiene un alérgeno, y al revisar el día o la semana para ver si se está cumpliendo. Su valor está en ahorrarle sumar nutrientes a mano y en avisar de cuándo la suma no es fiable. Su límite principal es que, si faltan datos nutricionales o de alérgenos de un producto, el total podría quedarse corto sin que se note, por lo que la app debe mostrar siempre qué productos están incompletos y no declarar un producto como seguro cuando no tiene datos de alérgenos.

La primera versión se limitaría a que el usuario defina un objetivo con 3 o 4 nutrientes y sus alérgenos, escanee o busque entre 20 y 30 productos y vea el total comparado con el objetivo, los productos con datos incompletos y las alertas de alérgenos. Quedan fuera por ahora calcular las necesidades a partir del peso, la altura y el sexo, las recetas y los menús semanales o mensuales, la sustitución automática de productos y el perfil de nutricionista.

La principal duda es cuántos productos reales tienen datos suficientes en Open Food Facts. Para comprobarlo se tomaría una muestra de unos 100 productos de la compra habitual del equipo, se mediría qué porcentaje tiene completos los nutrientes del objetivo y el campo de alérgenos, y se contrastaría un subconjunto con la etiqueta física, con atención especial a los alérgenos. Si la proporción de datos completos fuera baja, la app se limitaría a las categorías con buena cobertura.

**Verificación de datos (8 de noviembre de 2026).** Acceso confirmado: la API de Open Food Facts responde sin clave y devuelve, para un código de barras, nutrientes, alérgenos y un indicador de completitud. En una muestra de los 100 productos más escaneados de su catálogo en español (362.848 productos), tenían proteínas 98, azúcares 97 y energía 98, pero solo 27 tenían hierro y 16 vitamina C, y 76 tenían alérgenos informados. Como la muestra son productos populares, la completitud real probablemente es menor. Además, un campo de alérgenos vacío no distingue entre "no contiene" y "no informado", por lo que no debe interpretarse como seguro. Condiciones: la base está bajo licencia Open Database License (ODbL) según sus términos de uso, que obliga a atribuir la fuente y compartir en las mismas condiciones las bases derivadas; conviene identificar la aplicación en las peticiones. Se debe revisar aparte la licencia de las imágenes de las etiquetas antes de usarlas.

### 2.6 Recomendador de rutas y actividades (Planea)

Problema: quien quiere salir a hacer un plan (una ruta, un museo, una actividad al aire libre) dentro de un presupuesto tiene que buscar en varias webs y mapas, y casi nunca encuentra el precio junto a la ubicación.

Descripción: sistema que, dado un presupuesto, una zona y unas categorías de interés, propone planes de ocio cercanos con su precio aproximado y cómo llegar. No reserva ni vende entradas.

Usuario: personas o grupos que planifican un plan de fin de semana o de visita a una ciudad con un límite de gasto (estudiantes, familias, turistas). Hoy lo resuelven con buscadores y mapas, que muestran lugares pero rara vez el coste, o con guías y webs de turismo. Un perfil secundario sería el ayuntamiento u oficina de turismo, que podría publicar actividades gratuitas o de bajo coste.

Fuentes:
* Ubicación y categoría: OpenStreetMap (descarga por zona con Overpass o Geofabrik, licencia ODbL). Algunos lugares incluyen la etiqueta fee (de pago o no), pero en una prueba ninguno traía la etiqueta charge con el precio.
* Precios: es la parte más débil. Las opciones son portales de datos abiertos del ayuntamiento o la comunidad (por ejemplo datos.gob.es o el portal municipal de la zona elegida) y las webs oficiales de museos, instalaciones y parques. Habrá que confirmar si publican los precios en un formato reutilizable y, si no, el equipo los recogerá a mano para una muestra pequeña y citará la fecha de consulta.
* Gustos del usuario: un formulario inicial de preferencias (categorías, tipo de plan, esfuerzo físico); no hay datos de otros usuarios al principio, por lo que no habrá recomendación por usuarios similares hasta tener uso real.

MVP: una ciudad o comarca, 3 o 4 categorías (por ejemplo museos, rutas a pie, parques e instalaciones deportivas) y unos 50 lugares con precio verificado. El usuario indica presupuesto y categoría y ve la lista filtrada en un mapa, con precio, fecha del dato y distancia.

Se deja fuera: valoraciones y opiniones, reservas, planificación de itinerarios completos con varias paradas, transporte y otras ciudades.

Duda principal y cómo se comprobaría: cuántos lugares tienen un precio utilizable. Se comprobaría descargando de OpenStreetMap los lugares de la zona elegida, contando qué proporción trae precio, cuántos se pueden completar desde el portal abierto o la web oficial y cuántos quedan sin dato. Si la cobertura es baja, el producto se reduciría a la categoría que sí tenga precios.

Escalabilidad: cambio a la API de Google Maps en un plan de pago para obtener mayor cobertura de opiniones si el volumen de usuarios justifica el coste.

**Verificación de datos (8 de noviembre de 2026).** Acceso confirmado a OpenStreetMap mediante la API Overpass: en un radio de 5 km del centro de Madrid devolvió 86 museos, 42 con la etiqueta que indica si son de pago y ninguno con el precio. Por tanto, los precios no pueden salir de OpenStreetMap y siguen siendo una hipótesis a resolver con portales abiertos o webs oficiales, que no se han probado. Madrid es solo un ejemplo: la zona del proyecto no está elegida. Condiciones: los datos están bajo licencia ODbL, que exige atribuir (© colaboradores de OpenStreetMap) y compartir en las mismas condiciones las bases derivadas; la API pública tiene límites de uso, así que para más volumen conviene un extracto por zona.

