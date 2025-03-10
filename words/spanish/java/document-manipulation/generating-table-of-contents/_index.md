---
title: Generación de una tabla de contenidos en Aspose.Words para Java
linktitle: Generando tabla de contenidos
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a generar y personalizar una tabla de contenido (TOC) con Aspose.Words para Java. Cree documentos organizados y profesionales sin esfuerzo.
weight: 21
url: /es/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generación de una tabla de contenidos en Aspose.Words para Java


## Introducción a la generación de tablas de contenido en Aspose.Words para Java

En este tutorial, le explicaremos el proceso de generación de una tabla de contenido (TOC) con Aspose.Words para Java. La TOC es una función fundamental para crear documentos organizados. Explicaremos cómo personalizar la apariencia y el diseño de la TOC.

## Prerrequisitos

Antes de comenzar, asegúrese de tener Aspose.Words para Java instalado y configurado en su proyecto Java.

## Paso 1: Crear un nuevo documento

Primero, vamos a crear un nuevo documento con el que trabajar.

```java
Document doc = new Document();
```

## Paso 2: Personalizar los estilos de la tabla de contenidos

Para personalizar la apariencia de la tabla de contenidos, puede modificar los estilos asociados a ella. En este ejemplo, pondremos en negrita las entradas de la tabla de contenidos de primer nivel.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Paso 3: Agrega contenido a tu documento

Puedes agregar tu contenido al documento. Este contenido se utilizará para generar la tabla de contenidos.

## Paso 4: Generar la tabla de contenidos

Para generar la tabla de contenidos, inserte un campo de tabla de contenidos en la ubicación deseada en el documento. Este campo se completará automáticamente en función de los títulos y estilos del documento.

```java
// Inserte un campo TOC en la ubicación deseada en su documento.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Paso 5: Guardar el documento

Por último, guarde el documento con la tabla de contenidos.

```java
doc.save("your_output_path_here");
```

## Personalización de tabulaciones en la tabla de contenidos

También puedes personalizar las tabulaciones en la tabla de contenidos para controlar el diseño de los números de página. Aquí te mostramos cómo cambiar las tabulaciones:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Obtenga la primera pestaña utilizada en este párrafo, que alinea los números de página.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Retire la pestaña vieja.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Insertar una nueva pestaña en una posición modificada (por ejemplo, 50 unidades a la izquierda).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Ahora tiene una tabla de contenido personalizada en su documento con tabulaciones ajustadas para la alineación del número de página.


## Conclusión

En este tutorial, hemos explorado cómo generar una tabla de contenido (TOC) utilizando Aspose.Words para Java, una potente biblioteca para trabajar con documentos de Word. Una tabla de contenido bien estructurada es esencial para organizar y navegar por documentos extensos, y Aspose.Words proporciona las herramientas para crear y personalizar tablas de contenido sin esfuerzo.

## Preguntas frecuentes

### ¿Cómo cambio el formato de las entradas de la tabla de contenidos?

 Puede modificar los estilos asociados con los niveles de TOC utilizando`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, donde X es el nivel de TOC.

### ¿Cómo puedo agregar más niveles a mi TOC?

Para incluir más niveles en su TOC, puede modificar el campo TOC y especificar la cantidad deseada de niveles.

### ¿Puedo cambiar las posiciones de tabulación para entradas específicas de la tabla de contenidos?

Sí, como se muestra en el ejemplo de código anterior, puede cambiar las posiciones de tabulación para entradas de TOC específicas iterando a través de los párrafos y modificando las tabulaciones en consecuencia.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
