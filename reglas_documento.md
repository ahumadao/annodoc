---
layout: entry
title: Reglas Anotación a nivel de documento
---

En esta página se describirán las reglas para la anotación a nivel de documento del proceso de etiquetado de metástasis a distancia (M).

## Contenido

* [Introducción](#introducción)
* [Anotación](#anotación)
* [Anotar antecedentes familiares o personales](#anotar-antecedentes-familiares-o-personales)
* [Anotar la conclusión del examen](#anotar-la-conclusión-del-examen)
* [Anotar de manera dependiente al diagnóstico](#anotar-de-manera-dependiente-al-diagnostico)
* [Anotar menciones negadas](#anotar-menciones-negadas)
* [Anotar menciones inciertas](#anotar-menciones-inciertas)


## Introducción

Además de realizar la anotación a nivel de entidades al interior de cada uno de los reportes de imagenología mencionados, se realizará un etiquetado a nivel de documento. 

Esto permitirá obtener la clase a la que pertenece cada documento, que será útil para el entrenamiento de modelos de clasificación de texto. 

Ejemplo: 

~~~ ann
Cambios postquirúrgicos de histerectomía total y doble anexectomía, no se reconocen masas ni focos hipermetabólicos en lecho quirúrgico.
T1 M0 84 89 masas
T2 M0 94 115 focos hipermetabólicos
A1 menciónincierta[-] T1
A2 menciónincierta[-] T2
~~~

## Anotación

Para anotar a nivel de documento, deberán ingresar a la vista de anotación e ingresar a la sección de "Document Metadata", con un ícono de 3 etiquetas. 

Luego hacer click en el menú desplegable y seleccionar "Metástasis-Documento" y presionar el signo más para agregar esa metadata al texto. 

Se mostrarán 3 opciones: 
- M0: Yes / No
- M1: Yes / No
- Metástasis incierta : Yes / No

Se deberá escoger solo una de las opciones como "Yes" de la siguiente manera.

## Selección de la clasificación del documento

1. Deberá identificar la sección de la conclusión del examen y observar si efectivamente la clase del texto aparece explícita en aquel segmento. 
2. Si sale explícita para M1 o M0, seleccionar "Yes" en la que corresponda. 
3. Si no aparece de forma explícita, se seguirá el siguiente algoritmo:
- - Si hubiere al menos 1 mención catalogada como M1[-], el documento completo se clasifica como M1. 
- - Si no hubiere meniones catalogadas como M1[-] y hubiera al menos 1 mención catalogada como M1[+], el documento completo se clasifica como Metástasis incierta. 
- - Si no hubiere ninguna mención de M1, ya sea [-] o [+], el documento completo se clasifica como M0[-]. 

------------------------------------------------------------------------------

[Markdown]: http://daringfireball.net/projects/markdown/
[Stanford dependency]: http://nlp.stanford.edu/software/stanford-dependencies.shtml
[CoNLL-X]: http://ilk.uvt.nl/conll/#dataformat
[CoNLL-U]: http://universaldependencies.github.io/docs/format.html
[.ann standoff]: http://brat.nlplab.org/standoff.html
[SVG]: http://en.wikipedia.org/wiki/Scalable_Vector_Graphics
[Jekyll]: http://jekyllrb.com/
[brat]: http://brat.nlplab.org
[Liquid]: http://wiki.shopify.com/Liquid
[Git]: http://git-scm.com
[GitHub]: http://github.com
[Annodoc repository]: https://github.com/spyysalo/annodoc
[CSS]: http://en.wikipedia.org/wiki/Cascading_Style_Sheets
[YAML]: http://yaml.org/
