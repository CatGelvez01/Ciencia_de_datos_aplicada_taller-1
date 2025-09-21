ENTREGA TALLER N°1 - ANALITICA DE DATOS
Ana C. Gelvez 

READ ME - REPO

**Dimensiones técnicas del Dataset**
La industria hotelera es un sector consolidado en la mayoría de los contextos, sin embargo, siempre existe espacio para la mejora y la innovación.
En este estudio se aborda el contexto hotelero a partir de los datos proporcionados por el cliente “Hotel”, con el objetivo de identificar estrategias que impacten aspectos clave como las cancelaciones, la ocupación y los factores que pueden influir en la estadía de los huéspedes.

**Descripción del Dataset**
El cliente “Hotel” facilitó un dataset en formato CSV compuesto por 32 columnas (atributos) y más de 50.000 registros, acompañado de un Data Dictionary que facilita la comprensión de los términos y tipos de datos.

**Evaluación inicial de la calidad del Dataset**
Para validar la pertinencia del dataset frente a los objetivos del caso de estudio, se evaluaron las siguientes dimensiones:

- Completitud: amplia cantidad de registros, suficiente para análisis robustos.
- Consistencia: coherencia entre los atributos y los tipos de datos.
- Conformidad: los datos cumplen en gran medida con las reglas y estándares definidos en el Data Dictionary.
- Relevancia: las variables disponibles son adecuadas para los objetivos del estudio.
- Precisión: la terminología utilizada en el dataset coincide con la del Data Dictionary y el contexto del negocio.
- Procesabilidad: presenta algunos retos, principalmente por valores faltantes en ciertos atributos y violaciones de integridad (formatos no estandarizados).
- Disponibilidad: acceso completo a los datos en almacenamiento local.
- Temporalidad: los registros corresponden a los años 2015 y 2016.
- Credibilidad: los datos provienen directamente del cliente.

**Tipología de datos**
El dataset contiene variables de distintos tipos:
- Booleanas
- Numéricas (enteros y continuas)
- Texto plano (categóricas)
- Fechas
De acuerdo con la evaluación inicial, el dataset posee características favorables para el desarrollo del estudio, aunque se identifican desafíos relacionados con valores faltantes y estandarización.

**Objetivo del análisis**

El propósito del análisis es identificar atributos relevantes que permitan diseñar estrategias para incrementar la duración de la estadía y reducir la tasa de cancelaciones.
Para un primer acercamiento, se seleccionaron cinco variables clave:

- Hotel
- Is_canceled
- Stays_in_weekend_nights
- Stays_in_week_nights
- Adults

Estas variables cumplen con criterios de consistencia y completitud, y se consideran factores críticos para alcanzar los objetivos del caso de estudio.

**Estrategia de análisis** 

La estrategia consiste en analizar los atributos seleccionados para identificar posibles relaciones entre ellos. Para este propósito, se eligió aplicar pruebas de A/B testing, dado que resultan apropiadas en este escenario. Por otra parte, en el caso de las variables cuantitativas (stays_in_weekend_nights, stays_in_week_nights y adults), se emplearán pruebas estadísticas que permitan comprender mejor sus dependencias y correlaciones. Asimismo, para las relaciones entre variables categóricas y cuantitativas se utilizarán pruebas de hipótesis adecuadas con el fin de validar las relaciones planteadas.
En el código se va a encontrar en los comentarios las hipótesis para cada relación entre variables, además la mayoría de los escenarios se van a manejar con valores típicos de un 0.05, como una aproximación estándar del caso. 

Estas relaciones se analizan con el propósito de identificar conexiones entre los usuarios, la ubicación, el tiempo y la cancelación dentro del dataset del cliente. Las variables seleccionadas buscan principalmente comprender cómo el tipo de día influye en la cancelación, así como la relación con el tipo de hotel. De esta manera, se pretende caracterizar el comportamiento del usuario más frecuente en el dataset y, a partir de ello, diseñar estrategias que reduzcan las cancelaciones y mejoren la ocupación hotelera.

**Generación de resultados**

***Adultos y Cancelaciones (t-test)***
- Prueba aplicada: T-test independiente
- Resultado: Hipótesis nula rechazada, existe diferencia significativa en el número de adultos entre reservas canceladas y no canceladas.
- Visualización: Boxplot + Stripplot muestran que las reservas con más adultos presentan un patrón diferente de cancelaciones.
- Conclusión: El número de adultos en la reserva influye significativamente en la probabilidad de cancelación.

***Cancelaciones y Tipo de Hotel (Chi-cuadrado)***
- Prueba aplicada: Chi-cuadrado de independencia
- Resultado: Hipótesis nula rechazada, existe relación significativa entre cancelaciones y tipo de hotel. Cancelaciones más frecuentes en City Hotels que en Resorts.
- Visualización: Heatmap de contingencia confirma la asociación.
- Conclusión: El tipo de hotel tiene un impacto directo en la tasa de cancelaciones, siendo los hoteles de ciudad más vulnerables.

***Noches de fin de semana y Tipo de Hotel (Correlación de Pearson)***
- Prueba aplicada: Correlación de Pearson
- Resultado: Correlación positiva y significativa, los Resorts concentran más noches de fin de semana en comparación con los City Hotels.
- Visualización: Scatterplot con anotación de correlación y Barplot comparativo City vs Resort.
- Conclusión: La cantidad de noches de fin de semana está asociada con el tipo de hotel, reflejando diferentes patrones de comportamiento.

***Cancelaciones y Noches de fin de semana (Chi-cuadrado)***
- Prueba aplicada: Chi-cuadrado de independencia
- Resultado: Hipótesis nula rechazada, existe relación significativa entre el número de noches de fin de semana y la cancelación. Entre más noches de fin de semana en la reserva, mayor es la probabilidad de cancelación.
- Visualización: Tabla de contingencia inicial para observar la distribución, Bar chart muestra el incremento de cancelaciones según noches, y Heatmap refuerza la tendencia entre mayor cantidad de noches y aumento de cancelaciones.
- Conclusión: El número de noches de fin de semana es un predictor importante del riesgo de cancelación.

**Visualizaciones clave**
- Heatmaps → dependencias categóricas (Chi-cuadrado).
- Boxplot + Stripplot → diferencias de medias (t-test).
- Scatterplot con Pearson → correlaciones lineales.
- Barplots → tendencias de cancelación y noches de estancia.

**Estrategias e insights**
El cliente ofrece un servicio amplio en el diseño de experiencias dentro de la industria hotelera, lo que implica la presencia de múltiples factores que influyen en el comportamiento de los huéspedes al momento de realizar una reserva. Asimismo, resulta clave comprender el valor agregado que el servicio brinda como un todo a los potenciales clientes.
A partir de los datos proporcionados, fue posible realizar varias aproximaciones con los atributos más significativos. Entre ellos destaca el número de adultos, que constituyen el segmento más representativo del dataset en comparación con niños y bebés. De igual forma, se analizó el tipo de hotel, considerando dos categorías principales que ayudan a entender las experiencias que los huéspedes buscan. Tal como se mencionó en una de las hipótesis anteriores, la propuesta de valor de un Resort, en términos de servicio y experiencia, difiere de la de un City Hotel, lo que puede reflejar las intenciones de los huéspedes tanto al reservar como al cancelar.
A continuación, se presentan estrategias orientadas a reforzar las reservas y reducir las cancelaciones de acuerdo con el tipo de hotel.

***Segmentar estrategias por tipo de hotel:***
Hoteles City: políticas enfocadas en reducción de cancelaciones.
Resorts: reforzar campañas vacacionales de fin de semana.

Un factor clave del análisis fue el tipo de día de la semana, con el objetivo de relacionarlo con el comportamiento del huésped. Este enfoque permite profundizar en el planteamiento sobre el tipo de experiencia que el cliente busca al momento de reservar o cancelar, y al mismo tiempo refuerza la percepción del hotel como un espacio de descanso.
Por otro lado, los resultados de las hipótesis muestran que los grupos grandes de huéspedes tienden a cancelar menos las reservas, y que las estancias prolongadas durante los días laborales de la semana también presentan una menor probabilidad de cancelación.

***Optimizar políticas según número de adultos y noches:***
Ajustar condiciones de reserva en grupos numerosos.
Incluir incentivos para reducir cancelaciones en estancias de fin de semana prolongadas.

***Campañas diferenciadas:***
Promociones de escapadas en Resorts.
Ofertas flexibles en City Hotels para estadías cortas.

