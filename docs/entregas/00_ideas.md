# Ideas

## Índice
1. [Buscador y agregador de precios y ofertas locales](#1-buscador-y-agregador-de-precios-y-ofertas-locales)
2. [Reparto de una cartera de inversión](#2-reparto-de-una-cartera-de-inversión)
3. [Planificador de transporte público](#3-planificador-de-transporte-público)
4. [Gestión de stock según ventas](#4-gestión-de-stock-según-ventas)
5. [Diario de comidas](#5-diario-de-comidas)
6. [Recomendador de rutas o actividades](#6-recomendador-de-rutas-o-actividades)


## 1 Buscador y agregador de precios y ofertas locales
Un sistema que te permita hacer un seguimiento en lo que gastas en la cesta de la compra y localizar ofertas o buenos precios en supermercados y tiendas locales.
Funcionaría escaneando los tickets de compra y agregando los datos por establecimiento y localización.
Dependiendo del grado de precisión se podría ampliar para su uso en tiendas online.


## 2 Reparto de una cartera de inversión
Propone cómo repartir un dinero entre varios activos según el riesgo que acepte el usuario. Muestra además cómo habría funcionado esa cartera en el pasado.
Y va actualizando las recomendaciones en función del flujo del mercado. 


## 3 Planificador de transporte público
Estima la probabilidad de retraso y cuanto retraso de autobuses y trenes en un trayecto. Ayuda a elegir la ruta y el margen de salida.


## 4 Gestión de stock según ventas
Analiza las ventas de una tienda, clasifica los productos por rotación y propone qué reponer, mantener o reducir. Incluye una previsión de ventas semanal

## 5 Diario de comidas
Una aplicación o sistema que te permita sacar una foto de comidas o productos y analizar su valor alimenticio.
Dependiendo de la ruta puede servir para comparar productos entre sí y cuanto podría ser su consumo diario recomendado o incluso organizar raciones diarias y base a unos parámetros recomendados. Ej: el dietista te recomienda tomar más hierro por lo que la herramienta te ayuda a localizar ingredientes y recetas para incluirlas en la dieta con facilidad así como organizarte un menú diario.
Ruta dos, te permite sacar fotos de las comidas para analizar su contenido nutricional directamente, aunque veo ciertos problemas con este acercamiento ya que una foto no aporta mucha información.


# Recomendado de rutas y actividades

* Descripción: Sistema para buscar planes, experiencias  ocio a daptados al presupuesto
* Fuentes:
    * Ubicación: OpenStreetMap
    * Precios: Foursquare Places API
    * Usuarios similares: Formulario inicial de gustos

* MVP: En una zona concreta curuzar datos de OpenScreetMap con listado de precios y un filtrado por presupesto y categoria

* Escalabilidad: Cambio a la API de Google Maps en un plan de pago para obtener mayor cobertura de opiniones si el volumen de usuarios justifica el coste.
