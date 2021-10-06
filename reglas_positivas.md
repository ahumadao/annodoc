---
layout: entry
title: Reglas Positivas
---

En esta página se describirán las reglas positivas para el proceso de anotación de metástasis a distancia (M), es decir, aquello que efectivamente debe ser etiquetado por los anotadores. 

## Contenido

* [Todas las menciones en la misma frase](#todas-las-menciones-en-la-misma-frase)
* [Abreviaturas y siglas](#abreviaturas-y-siglas)
* [Anotar antecedentes familiares o personales](#anotar-antecedentes-familiares-o-personales)
* [Anotar la conclusión del examen](#anotar-la-conclusión-del-examen)
* [Anotar de manera dependiente al diagnóstico](#anotar-de-manera-dependiente-al-diagnostico)
* [Anotar menciones negadas](#anotar-menciones-negadas)
* [Anotar menciones inciertas](#anotar-menciones-inciertas)


## Todas las menciones en la misma frase

Se deberá anotar de manera separada, todas las menciones o sinónimos distintos utilizados para referirse a una metástasis a distancia en una misma frase:

Ejemplo: 

~~~ ann
Cambios postquirúrgicos de histerectomía total y doble anexectomía, no se reconocen masas ni focos hipermetabólicos en lecho quirúrgico.
T1 M0 84 89 masas
T2 M0 94 115 focos hipermetabólicos
A1 menciónincierta[-] T1
A2 menciónincierta[-] T2
~~~

## Abreviaturas y siglas

Una mención puede ser una abreviatura o una sigla de un hallazgo de metástasis a distancia. 

## Anotar antecedentes familiares o personales

Se debe anotar las menciones incluso cuando no se refieren directamente al paciente del reporte o examen, o al momento actual, por ejemplo, menciones de metástasis enumeradas en historia clínica o antecedentes familiares.

## Anotar la conclusión del examen

Todas las menciones de metástasis deben ser anotadas, incluso las que estén presentes en la conclusión del examen que se está revisando. 

Ejemplo:
~~~ ann
Estudio PET/CT con F18-PSMA sin evidencia de recurrencia locorregional ni a distancia de cáncer de próstata tratado.
T1 M0 45 85 masas
A1 menciónincierta[-] T1
~~~

## Anotar de manera dependiente al diagnóstico

La mención M1 o M0 de metástasis a distancia dependerá del tipo de cáncer diagnosticado. Por lo tanto, para catalogar una mención se deberá tener en cuenta la clasificación TNM de tumores malignos mencionada anteriormente y la parte del cuerpo involucrada. 

## Anotar menciones negadas

Anotar, incluso si la mención está en una expresión negada, por ejemplo, en el caso de que se mencione un sinónimo de metástasis para dejar claro que no hay metástasis a distancia. 

Ejemplo: 

~~~ ann
No se reconocen focos hipermetabólicos en esqueleto visible. 
T1 Negación 0 16 No se reconocen
T2 M0 16 38 focos hipermetabólicos
A1 menciónincierta[-] T2

~~~
## Anotar menciones inciertas

En casos en que el médico, *explícitamente*, declare una duda o incertidumbre y no pueda determinar el carácter metastásico de la lesión encontrada, se deberá asignar el atributo de Mención incierta positiva[+], en caso contrario, mantener negativo [-]

Ejemplo: 

~~~ ann
Se observan 2 focos con discreto hipermetabolismo, de carácter indeterminado.
T1 M1 14 49 focos con discreto hipermetabolismo
T2 Incertidumbre 54 76 carácter indeterminado
A1 menciónincierta[+] T1
~~~

En el ejemplo, como hay un contexto de incertidumbre que rodea a la mención de metátasis a distancia, se le agrega el atributo mencióninterna[+]. 

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
