# Ideas

## Índice
1. [Buscador y agregador de precios y ofertas locales](#1-buscador-y-agregador-de-precios-y-ofertas-locales-ahorrando)
2. [Reparto de una cartera de inversión](#2-reparto-de-una-cartera-de-inversión)
3. [Planificador de transporte público](#3-planificador-de-transporte-público)
4. [Gestión de stock según ventas](#4-gestión-de-stock-según-ventas)
5. [Diario de comidas](#5-diario-de-comidas-manjare)
6. [Recomendador de rutas o actividades](#6-recomendador-de-rutas-y-actividades)


## 1 Buscador y agregador de precios y ofertas locales (ahorrando)
Ahorrando es una aplicación que ayuda a gastar menos en la compra. El usuario sube la foto de sus tickets y la app guarda qué productos compra y a qué precio en cada establecimiento. Con esa información compara su cesta habitual entre supermercados y tiendas locales de su zona, le avisa de ofertas cercanas y le resume cuánto gasta y dónde. No compra por él ni ofrece precios en tiempo real.

Está pensada para quien hace la compra del hogar y quiere ahorrar sin dedicar tiempo a comparar tienda por tienda. Hoy probablemente lo haga a ojo, mirando folletos o las webs de cada establecimiento. Como segundo perfil, un pequeño comercio local podría publicar sus ofertas para llegar a clientes de su zona.

Los datos salen de dos fuentes. La principal son los tickets que suben los usuarios: la app lee la foto y extrae el establecimiento, la fecha, los productos y sus precios, y los guarda sin conservar datos de pago. Como los tickets suelen traer solo el nombre abreviado del producto y no su código de barras, la app empareja los productos de distintas tiendas por nombre y categoría. La segunda fuente son las ofertas que publican los propios comercios locales. Al principio no habrá tickets de otras personas, así que el proyecto partirá de los del equipo y de voluntarios, y las comparaciones solo serán fiables en las zonas y productos con datos suficientes. Las webs de las cadenas quedan como posible ampliación, y solo si sus condiciones de uso lo permiten.

Resulta útil cada semana al planificar la compra, al decidir en qué tienda comprar y al seguir cómo evoluciona el gasto del mes o el precio de un producto habitual. Su valor está en partir de lo que el usuario compra realmente, no de un catálogo genérico de ofertas, y en ahorrarle la comparación manual. Su límite principal es que los tickets se leen con errores y que un mismo producto aparece con nombres distintos en cada tienda, por lo que la app debe mostrar cuándo una comparación no es fiable.


## 2 Reparto de una cartera de inversión
Problema: quien empieza a invertir no sabe cómo repartir su dinero entre activos ni qué riesgo asume con cada reparto. 

Enfoque: Descargar series de precios y calcular rentabilidades. Estimar riesgo y volatilidad, con intervalos de confianza. Predecir la volatilidad con GARCH y XGBoost frente a una media móvil. Optimizar el reparto con Markowitz, simular escenarios con Monte Carlo y compararlo con un reparto equitativo. 

Origen de los datos: precios históricos de yfinance (Yahoo Finance)


## 3 Planificador de transporte público
Problema: quien debe llegar a una hora no sabe qué ruta de tren o autobús es más fiable. Los horarios teóricos no muestran los retrasos habituales.

Enfoque: Construir un histórico de puntualidad por línea, franja horaria y día. Clasificar la probabilidad de retraso, con clases desbalanceadas, y compararla con una referencia basada en la media por línea. Comparar dos o tres rutas y recomendar el margen de salida.

Origen de datos: revisar datos de autobuses, trenes y metro en vivo.


## 4 Gestión de stock según ventas
Problema: quien gestiona una tienda no sabe qué productos reponer, cuáles reducir y cuáles inmovilizan dinero. Decide por intuición o revisando hojas de ventas a mano. Limpiar las transacciones, incluidas cancelaciones y devoluciones.

Enfoque: Clasificar los productos por rotación (alta, media, baja). Predecir las ventas de la semana o mes siguiente y compararlas con una referencia sencilla, como repetir la semana anterior. Mostrar una lista de productos a reponer, mantener o reducir.

Obtención de datos: Online Retail II, de UCI, con transacciones reales de un comercio electrónico entre diciembre de 2009 y diciembre de 2011.


## 5 Diario de comidas (Manjare)
Manjare es una aplicación que convierte un objetivo nutricional en un menú. El usuario indica su peso, altura, sexo y alérgenos, y la app le propone unos límites de calorías y nutrientes como proteínas, hierro o vitamina C, que puede aceptar o ajustar. A partir de ahí le recomienda ingredientes, productos y recetas, y le arma un menú semanal o mensual que se actualiza cuando añade o quita ingredientes. También puntúa un producto según contenga o no el nutriente que busca o quiere evitar. No da diagnósticos médicos ni sustituye a un nutricionista.

Está pensada para quien ya tiene un objetivo nutricional, propio o recomendado por un dietista, y no sabe traducirlo en qué comprar y qué cocinar. El usuario principal es esa persona que quiere el menú, aunque la app también podría ofrecer un perfil de nutricionista para validar las recomendaciones y seguir a sus pacientes.

Los datos salen de tres fuentes. La información nutricional de los productos procede de una base de datos abierta y colaborativa, Open Food Facts, que reúne más de 4 millones de productos, que se consulta por código de barras; cuando un producto no aparece o está incompleto, el usuario puede introducirlo a mano con el formulario libre o con la foto de la etiqueta. Los datos de cada persona (peso, altura, sexo y alérgenos) los aporta ella misma, y con ellos la app calcula los límites recomendados a partir de fórmulas y pautas públicas de ingesta, cuya referencia se citará en el proyecto. Las recetas y los ingredientes básicos saldrán de un conjunto abierto o propio, todavía por decidir.

Manjare es útil al planificar la semana o el mes, al decidir qué producto comprar y al comprobar día a día si se está cumpliendo el objetivo. Su valor está en ahorrar al usuario el cálculo de nutrientes y la búsqueda de recetas, y en convertir una recomendación abstracta en una lista de la compra y un menú concretos. Tiene un límite claro: si faltan datos nutricionales de un producto, el menú podría quedarse corto en algún nutriente sin que se note, por lo que la app debe avisar de esa incertidumbre.


## 6 Recomendador de rutas y actividades

* Descripción: Sistema para buscar planes, experiencias  ocio a daptados al presupuesto
* Fuentes:
    * Ubicación: OpenStreetMap
    * Precios: Fuentes de datos Instiucionales y Portales de datos Abiertos
    * Usuarios similares: Formulario inicial de gustos

* MVP: En una zona concreta curuzar datos de OpenScreetMap con listado de precios y un filtrado por presupesto y categoria

* Escalabilidad: Cambio a la API de Google Maps en un plan de pago para obtener mayor cobertura de opiniones si el volumen de usuarios justifica el coste.
