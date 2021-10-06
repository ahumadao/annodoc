---
layout: entry
title: Reglas Negativas
---

En esta página se describirán las reglas positivas para el proceso de anotación de metástasis a distancia (M), es decir, aquello que efectivamente debe ser etiquetado por los anotadores. 

## Contenido

* [Lesiones no metastásicas](#lesiones-no-metastásicas)
* [Sitios anatómicos](#sitios-anatómicos)
* [Menciones implícitas de entidades](#menciones-implícitas-de-entidades)

## Lesiones no metastásicas

No anotar textos relacionados a otro tipo de lesiones de carácter no metastásico, como la descripción del tumor primario en el documento u otro tipo de lesiones, por ejemplo, inflamatorias, benignas, de conservación de estructuras anatómicas, etc. 

Ejemplo: 

~~~ ann
Cambios postquirúrgicos de histerectomía total y doble anexectomía, no se reconocen masas ni focos hipermetabólicos en lecho quirúrgico.
T1 M0 84 89 masas
T2 M0 94 115 focos hipermetabólicos
A1 menciónincierta[-] T1
A2 menciónincierta[-] T2
~~~

## Sitios anatómicos

No serán anotados los sitios anatómicos para este proyecto, solo la mención de metástasis a distancia. La excepción a esta regla corresponde a sitios anatómicos que estén presentes al interior de una frase que indique un hallazgo de metástasis a distancia (ver regla general de [Límite de menciones](http://127.0.0.1:4000/annodoc/reglas_generales#l%C3%ADmite-de-menciones) como ejemplo).

Ejemplo:
~~~ ann
Se observa un extenso compromiso hipermetabólico medular
T1 M1 22 48 
A1 menciónincierta[-] T1
~~~
~~~ ann
Se observa un extenso compromiso medular hipermetabólico
T1 M1 22 56 
A1 menciónincierta[-] T1
~~~

En el primer ejemplo, no se etiqueta la palabra *medular*. En el segundo ejemplo se etiqueta, como excepción, porque está al interior de dos palabras clave -*compromiso* e *hipermetabólico*- que hacen referencia a una mención de M1, según regla de [Límite de menciones](http://127.0.0.1:4000/annodoc/reglas_generales#l%C3%ADmite-de-menciones).

## Menciones implícitas de entidades

No se debe realizar ningún tipo de inferencia clínica para decidir si una evidencia textual representa indirectamente una entidad clínica. Asimismo, las anáforas no deben anotarse.

La mención debe corresponder a una descripción textual de un sinónimo de metástasis a distancia.





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
