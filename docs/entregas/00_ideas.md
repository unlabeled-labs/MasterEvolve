# Ideas

## Índice
1. [Buscador y agregador de precios y ofertas locales](#1-buscador-y-agregador-de-precios-y-ofertas-locales-ahorrando)
2. [Reparto de una cartera de inversión](#2-reparto-de-una-cartera-de-inversión)
3. [Planificador de transporte público](#3-planificador-de-transporte-público)
4. [Gestión de stock según ventas](#4-gestión-de-stock-según-ventas)
5. [Diario de comidas](#5-diario-de-comidas-manjare)
6. [Recomendador de rutas o actividades](#6-recomendador-de-rutas-o-actividades)


## 1 Buscador y agregador de precios y ofertas locales (ahorrando)
Ahorrando es una aplicación que ayuda a gastar menos en la compra. El usuario sube la foto de sus tickets y la app guarda qué productos compra y a qué precio en cada establecimiento. Con esa información compara su cesta habitual entre supermercados y tiendas locales de su zona, le avisa de ofertas cercanas y le resume cuánto gasta y dónde. No compra por él ni ofrece precios en tiempo real.

Está pensada para quien hace la compra del hogar y quiere ahorrar sin dedicar tiempo a comparar tienda por tienda. Hoy probablemente lo haga a ojo, mirando folletos o las webs de cada establecimiento. Como segundo perfil, un pequeño comercio local podría publicar sus ofertas para llegar a clientes de su zona.

Resulta útil cada semana al planificar la compra, al decidir en qué tienda comprar y al seguir cómo evoluciona el gasto del mes o el precio de un producto habitual. Su valor está en partir de lo que el usuario compra realmente, no de un catálogo genérico de ofertas, y en ahorrarle la comparación manual. Su límite principal es que los tickets se leen con errores y que un mismo producto aparece con nombres distintos en cada tienda, por lo que la app debe mostrar cuándo una comparación no es fiable.


## 2 Reparto de una cartera de inversión
Propone cómo repartir un dinero entre varios activos según el riesgo que acepte el usuario. Muestra además cómo habría funcionado esa cartera en el pasado.
Y va actualizando las recomendaciones en función del flujo del mercado. 


## 3 Planificador de transporte público
Estima la probabilidad de retraso y cuanto retraso de autobuses y trenes en un trayecto. Ayuda a elegir la ruta y el margen de salida.


## 4 Gestión de stock según ventas
Analiza las ventas de una tienda, clasifica los productos por rotación y propone qué reponer, mantener o reducir. Incluye una previsión de ventas semanal

## 5 Diario de comidas (Manjare)
Manjare es una aplicación que convierte un objetivo nutricional en un menú. El usuario indica su peso, altura, sexo y alérgenos, y la app le propone unos límites de calorías y nutrientes como proteínas, hierro o vitamina C, que puede aceptar o ajustar. A partir de ahí le recomienda ingredientes, productos y recetas, y le arma un menú semanal o mensual que se actualiza cuando añade o quita ingredientes. También puntúa un producto según contenga o no el nutriente que busca o quiere evitar. No da diagnósticos médicos ni sustituye a un nutricionista.

Está pensada para quien ya tiene un objetivo nutricional, propio o recomendado por un dietista, y no sabe traducirlo en qué comprar y qué cocinar. El usuario principal es esa persona que quiere el menú, aunque la app también podría ofrecer un perfil de nutricionista para validar las recomendaciones y seguir a sus pacientes.

Manjare es útil al planificar la semana o el mes, al decidir qué producto comprar y al comprobar día a día si se está cumpliendo el objetivo. Su valor está en ahorrar al usuario el cálculo de nutrientes y la búsqueda de recetas, y en convertir una recomendación abstracta en una lista de la compra y un menú concretos. Tiene un límite claro: si faltan datos nutricionales de un producto, el menú podría quedarse corto en algún nutriente sin que se note, por lo que la app debe avisar de esa incertidumbre.


## 6 Recomendado de rutas y actividades

* Descripción: Sistema para buscar planes, experiencias  ocio a daptados al presupuesto
* Fuentes:
    * Ubicación: OpenStreetMap
    * Precios: Foursquare Places API
    * Usuarios similares: Formulario inicial de gustos

* MVP: En una zona concreta curuzar datos de OpenScreetMap con listado de precios y un filtrado por presupesto y categoria

* Escalabilidad: Cambio a la API de Google Maps en un plan de pago para obtener mayor cobertura de opiniones si el volumen de usuarios justifica el coste.
