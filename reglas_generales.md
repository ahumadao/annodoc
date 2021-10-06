---
layout: entry
title: Reglas Generales
---

En esta página se describirán las reglas generales para el proceso de anotación de metástasis a distancia (M)

## Table of contents

* [Mención mínima](#mención-mínima)
* [Uso de recursos de conocimiento externos](#uso-de-recursos-de-conocimiento-externos)
* [Unicidad del anotador](#unicidad-del-anotador)
* [Anotación basada en documentos individuales](#anotación-basada-en-documentos-individuales)
* [Menciones ambiguas](#menciones-ambiguas)
* [Revisión de las reglas de anotación](#revisión-de-las-reglas-de-anotación)
* [Exhaustividad de las menciones](#exhaustividad-de-las-menciones)
* [Límite de menciones](#límite-de-menciones)
* [Límite de sentencias](#límite-de-sentencias)
* [Perfil del anotador](#perfil-del-anotador)

## Mención Mínima

Una entidad debe reconocerse como la parte más corta que define un hallazgo o mención de metástasis y que permite aportar ejemplos generalizables para el entrenamiento del algoritmo. Se puede definir también como un *sinónimo* en el texto correspondiente a un hallazgo  de lesión relacionada a una metástasis a distancia. 

Se anotarán como [M1-](#mención-mínima) con mención incierta negativa,  [M0-](#mención-mínima) según indique presencia o ausencia de Metástasis a Distancia. 

En caso de que la mención del hallazgo no sea concluyente, tenga carácter inespecífico, indeterminado o indefinido, se etiquetará como [M1+](#mención-mínima)

Ejemplos: 

~~~ ann
Cuello: Los distintos compartimentos cervicales son de amplitud conservada, no se identifica masas ni adenopatías hipermetabólicas
T1 M0 93 98 masas
T2 M0 102 130 adenopatías hipermetabólicas
A1 menciónincierta[-] T1
A2 menciónincierta[-] T2
~~~

~~~ ann
Musculoesquelético: El extenso compromiso hipermetabólico medular y óseo difuso, tanto del esqueleto axial como del esqueleto apendicular, presenta leve disminución en intensidad y extensión. Sin embargo, persisten incontables focos hipermetabólicos en practicamente todo el esqueleto axial y apendicular visible, con SUV máximo 8,3 a nivel de L5.
T1 M1 31 57 compromiso hipermetabólico
T2 M1 227 249 focos hipermetabólicos
A1 menciónincierta[-] T1 
A2 menciónincierta[-] T2
~~~

~~~ ann
Focos óseos discretamente captantes en esternón y acetábulo  izquierdo, de carácter indeterminado.Por su localización no es descartable compromiso secundario.
T1 M1 0 35 focos
A1 menciónincierta[+] T1 
~~~

No se debe añadir la parte del cuerpo ni las características o adjetivos de aquella, por ejemplo, en este caso no se anotan los *“compartimientos cervicales”* ni que *“son de amplitud conservada”*.

## Uso de recursos de conocimiento externos

En caso de duda del anotador, sobre si corresponde o no a una mención a la categoría de metástasis a distancia, dado por la ubicación o parte del cuerpo afectada, referirse al manual de la Clasificación TNM de Tumores Malignos.

Link al [Libro de la Clasificación TNM de Tumores Malignos (8va edición, 2016)](https://drive.google.com/file/d/1OAgYj1EUuTKrI_W4bsaKYvdbKSXHuSuU/view?usp=sharing)  

El proceso de anotación no tiene como propósito anotar todas las palabras asociadas a la notación TNM de tumores incluidas en el reporte de imagenología, sino que solo aquellas que hacen mención a la clasificación M de metástasis a distancia. 


## Unicidad del anotador

Cada instancia de documento debe ser anotada por un único anotador.

## Anotación basada en documentos individuales

Todas las anotaciones de una instancia de documento deben realizarse de manera aislada sin tener en cuenta otros casos clínicos.

## Menciones ambiguas

No anotar menciones para las que no esté claro si corresponde anotarlas (incluso tras consultar algún recurso externo). 

En caso de que esto suceda, consultar en el siguiente [Formulario de Google](https://forms.gle/b2AfGJ97toecB5hb9), ingresando la información solicitada.

## Revisión de las reglas de anotación

Si se detectan casos especiales de tipos de menciones que podrían ser de interés o estar relacionadas y las guías no especifican su anotación, se deben reportar estos casos junto con ejemplos para refinar las reglas de anotación y una explicación mínima para que cualquier anotador pueda entender el razonamiento en un caso concreto.

En caso de que esto suceda, ingresar al [Formulario de Google](https://forms.gle/b2AfGJ97toecB5hb9) para ingresar la revisión.  


## Exhaustividad de las menciones

Las menciones de metástasis afirmativas o negadas deben anotarse cada vez que aparezcan. Una entidad negativa, por ejemplo, que se menciona múltiples veces, debe anotarse múltiples veces.

En el caso del examen PET-CT suele mencionarse en múltiples oportunidades el descarte de lesiones malignas, todas las menciones deben ser etiquetadas.

## Límite de menciones

La mención debe incluir el hallazgo de metástasis a distancia o su descarte y se podrá incluir dentro de la anotación, información no relevante con el objetivo de no romper la cadena siempre y cuando la distancia entre las partes relevantes de la mención sea igual o menor a 5 tokens.

En caso de que la distancia sea mayor a 5 tokens, las palabras relevantes de la mención deberán considerarse menciones individuales.

Ejemplos: 

En el primer ejemplo se observa una mención entre las palabras clave *masa* e *hipermetabólica*. La distancia entre estas palabras es de 5 tokens, por lo que es factible anotar como una mención única.


~~~ ann
Se observa masa en músculo esquelético conservado, hipermetabólica.
T1 M1 11 66 masa, en músculo esquelético conservado, de características hipermetabólicas
A1 menciónincierta[-] T1
~~~
En cambio, en este ejemplo similar al anterior, la distancia entre las mismas palabras es de 7 tokens, por lo que se anotan separadas en 2 menciones distintas. 
~~~ ann
Se observa masa, en músculo esquelético conservado, de características hipermetabólicas
T1 M1 11 15 masa
T2 M1 71 87 hipermetabólicas
A1 menciónincierta[-] T1
A2 menciónincierta[-] T2
~~~

Otro ejemplo de un hallazgo dividido en dos menciones distintas: 

~~~ ann
No se identifican adenopatías axilares, supraclaviculares, hiliomediastínicas ni mamarias internas hipercaptantes.
T1 M0 18 29 adenopatías
T2 M0 99 113 hipercaptantes
A1 menciónincierta[-] T1
A2 menciónincierta[-] T2
~~~

## Límite de sentencias

Las menciones de entidades de metástasis a distancia no pueden atravesar oraciones múltiples. Es decir, una mención no puede atravesar:

- Un punto y seguido
- Un punto y aparte
- Un bullet-point

Esta regla, en algunos casos produce que no se anote información relevante. No obstante, su aplicación simplifica y acelera la anotación y facilita el tratamiento computacional posterior.

## Perfil del anotador

Para la correcta aplicación de esta guía en una tarea de anotación, sería deseable que el anotador dispusiera de las siguientes capacidades:

- Conocimiento de la clasificación TNM de tumores malignos. 
- Conocimiento de las bases biológicas del comportamiento del tumor o biología del cáncer y específicamente de la metástasis.
- Conocimiento en anatomía humana.
- Conocimiento de los términos, abreviaturas y siglas médicas.
- Habilidades en la búsqueda de información científica.

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
