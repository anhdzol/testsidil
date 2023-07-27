---
output:
  html_document: default
---
# PRESENTACIÓN DEL SIDIL

>*Aplicación de la analítica de datos para la generación de estrategias inteligentes de selección de empresas para la inspección laboral*


PRUEBA VER [Fuentes de informacion que vienen del IMSS](#fuentes_IMSS)

Las inspecciones laborales son el instrumento más importante que utilizan los gobiernos para verificar y garantizar que las empresas adopten las medidas necesarias para cumplir con las normativas en materia de condiciones laborales y de seguridad y salud en el trabajo. No obstante, el efecto de dichas inspecciones depende de diversos factores, siendo un factor fundamental el de los mecanismos de selección de los centros de trabajo a inspeccionar.

Realizar inspecciones en todo el universo de empresas no resulta viable debido a las limitaciones presupuestales y de recursos humanos que tienen las instituciones públicas. Al día de hoy la selección de las empresas que se van a inspeccionar se basa en un mecanismo aleatorio sobre una preselección de centros de trabajo que cumplen con ciertas características o que cuentan con determinados atributos de tamaña, rama de actividad, región, etc. Dichas características de selección no sólo son un conjunto limitado de atributos observables, sino que además no toman en consideración en ninguna medida el riesgo de incumplimiento laboral de las empresas. 

En ese marco, este componente busca apoyar a la Secretaría de Trabajo y Previsión Social (STPS) en la generación de herramientas y mecanismos que permitan seleccionar centros de trabajo en función de un enfoque basado en el **análisis de los factores de riesgo** de que cada una de las empresas incumplan determinada normatividad en materia laboral. Suponemos que este enfoque resultará en una mayor eficiencia de la inspección. Para ello se requirió el desarrollo de métodos de análisis que permitieran la priorización en función del riesgo, basándose en que la STPS dispone de grandes volúmenes de datos derivados de la inspección laboral y de otras bases de datos, propias o de terceros, de enorme utilidad. Ha sido necesario, de la misma manera, relacionar estos registros administrativos de la autoridad inspectiva con otras fuentes de información estadística y registros de otras instituciones públicas para enriquecer el universo de empresas y contar así con más información que permita establecer factores de riesgo.
 
Así, el Sistema de Inteligencia de Datos para la Inspección Laboral (SIDIL) que aquí se presenta es una herramienta tecnológica que explota diversas fuentes de información para generar una predicción de incumplimiento a la normativa laboral en los centros de trabajo (CT) susceptibles de ser inspeccionados por la Secretaría del Trabajo y Previsión Social del Gobierno de México. El SIDIL permite a la STPS aplicar estrategias inteligentes de inspección laboral a partir de la generación de subconjuntos de empresas y CT con base en criterios preestablecidos que reflejan su perfil de riesgo de incumplimiento de los derechos laborales. A tal efecto, como se explica más adelante, el SIDIL explota más de un millón de inspecciones registradas y más de 35 millones de estimaciones puntuales a diferentes niveles de agregación, para predecir el riesgo en un universo siempre dinámico de CT registrados en el Directorio Nacional de Empresas (DNE), independientemente de que éstos tengan o no antecedentes de inspección.

El SIDIL fue desarrollado por American Institutes for Research (AIR) en colaboración con la STPS y en el marco del proyecto de Cumplimiento con el Derecho Laboral en el Sector de Autopartes (CALLE, por sus siglas en inglés). AIR busca apoyar a la STPS y otras autoridades competentes en materia laboral en el desarrollo de procesos y herramientas que permitan el incremento en la eficiencia y eficacia de las funciones relativas a la aplicación de la ley laboral en el sector de autopartes de México, así como en el fortalecimiento de la implementación de la Reforma Constitucional en materia de Justicia Laboral (realizada en 2017) y la Reforma de la Ley Federal del Trabajo (del 1 de mayo 2019). 
 
El SIDIL responde a la necesidad de hacer un uso eficiente y eficaz de los recursos públicos a través de la focalización de los universos de las inspecciones y al propósito de realizar una mejor cobertura de los diferentes tipos de riesgos laborales, a la no repetición de inspecciones y a la priorización de CT con mayor probabilidad de incumplimiento, entre otros aspectos relativos a la eficiencia y eficacia de las inspecciones laborales.

En los primeros meses de este proyecto el equipo se abocó al entendimiento, descripción y explotación de los registros administrativos del proceso de inspección y sanción. Dicho trabajó concluyó de manera preliminar en un documento de hallazgos, cuyos principales resultados fueron presentados a la STPS.


[[pendiente definir sobre: 

[DOCUMENTO DE HALLAZGOS](https://msair.sharepoint.com/:w:/r/sites/Impaq_Projects/Mexico/CALLE/Ongoing%20Tasks/Data%20Intelligence/Data%20Analysis/2022-01%20An%C3%A1lisis%20SIAPI_SIPAS%20-%20Hallazgos.docx?d=wf74a0d86ad244c92a86c8a88e3af6f1e&csf=1&web=1&e=GcTmkv)
]]

En cuanto a los temas técnicos, abordar el reto de seleccionar empresas de alto riesgo mediante el uso de la analítica de datos resulta adecuado para los algoritmos de aprendizaje automático, ya que se cuenta con una masa crítica de información para procesar.  A lo largo de este proyecto el equipo de AIR se avocó al análisis de datos, la incorporación de fuentes de información, su relacionamiento, la definición de indicadores, la generación y entrenamiento de modelos matemáticos para la predicción de riesgo y el desarrollo de un poderoso sistema de información, que se presenta a detalle a lo largo de este documento.


## Alineación con la Misión y Programas de Gobierno

En el Programa Sectorial de Trabajo y Previsión Social, en el “Objetivo prioritario 4. Dignificar el trabajo y estimular la productividad mediante la vigilancia al cumplimiento de la normativa laboral”2 se menciona: “La nueva visión de la inspección pretende hacerla más efectiva y lograr mejores resultados reduciendo los procedimientos burocráticos, impulsando reformas integrales para mejorar el marco legal, coordinando y dirigiendo las inspecciones de trabajo con nuevos enfoques, estrategias e instrumentos con una visión de lucha frontal contra la corrupción (...) con el fin de coadyuvar a la mejora de las condiciones del mercado laboral mexicano con un especial interés en materia de Salud y Seguridad en el trabajo y combate a la subcontratación y al subregistro en el IMSS”. En particular, en el análisis del estado actual se menciona: “el uso de bases de datos anticuadas y la falta de mecanismos de coordinación institucional ocasionó que la inspección federal se llevará a cabo en un universo reducido de empresas que eran constantemente visitadas, en muchos casos en materias de escasa relevancia, generando actos de molestia que no resultaron en una mejora de las condiciones laborales del país”.

Así, en la Estrategia prioritaria “4.1.- Impulsar acciones para favorecer la protección social de las personas trabajadoras ante el futuro del trabajo con perspectiva de igualdad y no discriminación”, se menciona, entre otras acciones: Coordinar la elaboración de estudios, diagnósticos, encuestas y otros documentos de carácter analítico que permitan conocer el estado de segmentos específicos de las personas trabajadoras en materia de seguridad social, con especial énfasis en grupos históricamente discriminados.

En la Estrategia prioritaria “4.4.- Reestructurar la inspección laboral con énfasis en la simplificación normativa, la capacitación, el uso de nuevas tecnologías y la lucha frontal contra la corrupción”, para garantizar el cumplimiento de la normativa laboral vigente con una perspectiva de no discriminación e inclusión, se mencionan las acciones tendientes a 

* Coordinar y dirigir las inspecciones de trabajo con nuevos enfoques, estrategias e instrumentos con el fin de contribuir al trabajo digno o decente, con perspectiva de género, inclusión y no discriminación
* Implementar	mecanismos eficaces para optimizar y consolidar el proceso de inspección como herramienta eficaz para proteger los derechos de las personas trabajadoras.
*	Fortalecer los mecanismos de inspección a través de la vinculación con otros entes gubernamentales, para el intercambio de información con el objeto de vigilar el marco normativo en materia de subcontratación y subregistro.


Por su parte la Estrategia Digital Nacional (EDN) centra su razón de ser en la necesidad de orientar el uso y el desarrollo de las TIC al bienestar del pueblo mexicano con una visión humanista del uso de las tecnologías y guardando estrictamente los principios de austeridad republicana, transparencia, privilegiando lo público y el uso o desarrollo nacional de tecnologías de acceso abierto [...] Visión: Un país digitalizado y un gobierno austero, honesto y transparente, con autonomía e independencia tecnológicas, centrado en las necesidades ciudadanas, principalmente de los más pobres.

Entre sus Líneas de acción figuran:
*	Definir elementos técnicos y normativos clave para la contratación o desarrollo de soluciones tecnológicas propias, de acceso abierto.
*	Fomentar el desarrollo de sistemas de información gubernamentales propios y de acceso abierto que se compartan entre Instituciones.
* Priorizar el uso de Software Libre y estándares abiertos.
* Promover el intercambio de información entre Instituciones para la simplificación de trámites y servicios a la ciudadanía.
* Impulsar la integración de bases de datos institucionales que concentren, compartan y estandaricen la información de los sistemas gubernamentales.
* Promover el uso y aprovechamiento de las bases de datos institucionales.


En cuanto a la inspección laboral, según el marco normativo vigente la STPS tiene entre sus facultades la vigilancia y cumplimiento de la normatividad laboral como se marca en los artículos 540 al 550 de la Ley Federal del Trabajo (LFT), así como el artículo 40 fracción I de la Ley Orgánica de la Administración Pública Federal. Para ejercer estas funciones, la STPS ha implementado el procedimiento de “Inspección del Trabajo”, que lleva a cabo a través de la Dirección General de Inspección Federal del Trabajo supervisando a las Delegaciones Federales del Trabajo, como los responsables operativos. 
Cabe señalar que el proceso de inspección incluye la vigilancia de las normas de trabajo constitucionales, las contenidas en la LFT, sus reglamentos, convenios internacionales, Normas Oficiales Mexicanas (NOMs), y las disposiciones dictadas por la STPS. Otra de las funciones que lleva a cabo la Secretaría, es el Procedimiento Administrativo Sancionador, que determina la existencia de elementos jurídicos para sancionar al centro de trabajo por actos violatorios a la legislación laboral.
Es entonces en ese marco, tanto sustantivo en términos de la inspección laboral, como en materia de tecnologías y desarrollo de sistemas de información, que se enmarca este proyecto a las prioridades del Gobierno de México.



## Justificación de la viabilidad del proyecto
La determinación de estrategias inteligentes de inspección basadas en el análisis de datos requiere un volumen suficiente de datos y una serie de herramientas que, en función de determinados criterios de análisis, permitan su procesamiento. La Inspección Federal del Trabajo y más en general la Secretaría del Trabajo (STPS), dispone de una gran cantidad de datos: datos históricos de la inspección, directorio de empresas y centros de trabajo, reportes de accidentes, información de la evolución de sueldos y salarios en los contratos colectivos, entre otros. Así, se cuenta con la información que recopila y almacena el organismo de inspección de trabajo, que en general son datos relacionados con sus objetos de inspección y sus actividades: datos de las empresas como el número de empleados, la antigüedad de la empresa, la rama de actividad, el número de inspecciones previas, el resultado de dichas inspecciones y las notificaciones de accidentes. Asimismo, se cuenta con un importante acervo de información generada por el área de estadística e investigación de la STPS referida a accidentes y contratos colectivos. Además, el número de datos aumenta progresivamente al añadirse nuevas inspecciones y al registrarse más y más nuevos contratos.

Por otro lado, la gran institución en materia de seguridad social de los trabajadores, que es el Instituto Mexicano del Seguro Social (IMSS), dispone de enormes acervos de información de empleados, empleadores, accidentes laborales, etc., que, anonimizados y agrupados, están disponibles (evitando todo problema de confidencialidad de la información) en el marco de la cooperación entre estas instituciones del Estado Mexicano, siendo una realidad que esa información ya fluye como parte del intercambio entre la STPS y el IMSS. 

Del mismo modo, es de resaltar la importante labor que ha desarrollado por décadas el Instituto Nacional de Estadística y Geografía (INEGI), a través de los censos económicos, encuestas de ocupación y empleo, los directorios de unidades económicas y otros instrumentos fundamentales para el análisis estadístico y el desarrollo de las políticas públicas en la materia en México. La información generada por el INEGI, de la misma manera, está disponible públicamente en tabulados y, a través de acuerdos interinstitucionales, se puede contar con la misma a nivel de los microdatos.

A estos acervos se podría en un futuro sumar los de otras instituciones públicas como la Secretaría de Economía, la Secretaría de Hacienda, la Secretaría de Gobernación, con las cuales será menester realizar análisis de la información de la que disponen y de las posibilidades de establecer acuerdos y convenios para su intercambio.


## Objetivos del SIDIL

### General
El SIDIL tiene como objetivo sistematizar la explotación de fuentes de información internas y externas a la STPS para establecer una herramienta tecnológica que permita a la Secretaría del Trabajo y Previsión Social del Gobierno de México aplicar estrategias de inspección laboral a partir de la generación de subconjuntos de empresas y centros de trabajo con base en criterios preestablecidos que reflejen su perfil de riesgo de incumplimiento de los derechos laborales.


### Específicos

* Establecer y reflejar criterios de identificación de riesgos de violaciones laborales que pueden ser medidos con la información actualmente disponible a la STPS.
* Recuperar de encuestas y registros administrativos datos que permitan construir indicadores de utilidad para la medición del riesgo de incumplimiento laboral.
* Generar estructuras de información que reflejen indicadores de riesgo asociados a los criterios establecidos.
* Establecer los coeficientes que fungen como ponderadores de riesgo para conformar una matriz de factores de riesgo que pueda ser asociada al universo de los CT.
* Asociar factores de riesgo a los centros de trabajo que están registrados en el DNE para informar los CT con mayor probabilidad de riesgo.
* Generar interfaces comprensivas que permitan incorporar, actualizar y consultar los diferentes productos de información relativa a los factores de riesgo.
* Exportar subconjuntos del universo de centros de trabajo que cumplan con criterios de selección flexibles asociados a los factores de riesgo.

## Propuesta de solución

Buscando fortalecer el objetivo de que desde la inspección laboral se vigile y promueva el cumplimiento de las condiciones laborales de los trabajadores mexicanos en apego al marco regulatorio, se buscó desarrollar una herramienta que permitiera generar estrategias cada vez más inteligentes de inspección, así como analizar su impacto e incidencia en dichas condiciones. En este componente se trabajaron elementos que corresponden al proceso de análisis e inteligencia de datos previos a la inspección: desde la recopilación y procesamiento de fuentes internas y externas de información para la conformación de un repositorio estructurado, el análisis de criterios para establecer riesgo de violaciones laborales de los patrones y la consulta de estos indicadores para la generación de estrategias inteligentes para la inspección laboral basadas en análisis de riesgos de incumplimiento. 

Para abordar el reto de seleccionar empresas de alto riesgo mediante el uso de la analítica de datos debieron desarrollarse herramientas y actividades para la elaboración de criterios de detección de violaciones y desviaciones de las normas laborales, con la formalización de indicadores que de estos criterios, la gestión y procesamiento de información y el desarrollo y la puesta en funcionamiento de herramientas tecnológicas que permitan el almacenamiento de los datos, su explotación y consulta.




PRUEBA INSERCION IMAGEN COMO CHUNK DE R


```r
knitr::include_graphics("images-1/01/Ilustracion1.png")
```

![plot of chunk unnamed-chunk-1](/images-1/01/Ilustracion1.png)


PRUEBA INSERCION IMAGEN SIN CHUNK R


![Ilustración 1: ](images-1/01/Ilustracion1.png)


En el esquema anterior se puede observar los componentes básicos de la solución planteada, que tienen que ver con:

* La concentración y procesamiento de la información estadística y los estudios especializados que permiten el análisis de las redes y cadenas productivas, del contexto laboral y su caracterización en materia de actividad económica, ocupación, empleo, evolución de los sueldos y salarios, etc.
* La limpieza, enriquecimiento y relacionamiento de información que se pudo integrar en bases de datos para su análisis. Esta información, como ya se mencionó, proviene tanto de fuentes internas como externas, a través de convenios de colaboración.
* La determinación de los criterios de análisis que buscaron identificar las principales violaciones y que reflejen las prioridades en materia de política pública que deben guiar la inspección del trabajo.
* El desarrollo de las herramientas que, a partir del establecimiento de los criterios mencionados y su descomposición en indicadores, permitieron llevar a cabo análisis basados en algoritmos de analítica, minería de datos y aprendizaje de máquina.


## Alcance

El SIDIL tiene como alcance:

* Desarrollar una matriz de criterios sustantivos para la identificación de las principales violaciones laborales por parte de los patrones, desagregados en los indicadores necesarios y factibles para su evaluación en las empresas y centros a partir de las fuentes de información que se disponen.
* A partir de un diagnóstico pormenorizado contar con la identificación de los acervos de información susceptibles de incorporarse, así como las necesidades de procesamiento que son necesarias para integrar estos datos al cálculo de los indicadores generados.
* La implementación de un repositorio de información y un ambiente de analítica de datos con las bases de datos procesadas y listas para su incorporación.
* Una serie de interfaces y servicios de información que permitan la consulta del repositorio de datos a través de los indicadores y criterios definidos para la generación de estrategias inteligentes para la inspección.
*	La transferencia del conocimiento y de las herramientas necesarias para asegurar la sostenibilidad del proyecto en el mediano plazo.

