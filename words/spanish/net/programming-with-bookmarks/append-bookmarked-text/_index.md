---
"description": "Aprenda a añadir texto marcado a un documento de Word con Aspose.Words para .NET con esta guía paso a paso. Ideal para desarrolladores."
"linktitle": "Añadir texto marcado en un documento de Word"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Añadir texto marcado en un documento de Word"
"url": "/es/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Añadir texto marcado en un documento de Word

## Introducción

¡Hola! ¿Alguna vez has intentado añadir texto de una sección marcada en un documento de Word y te ha resultado complicado? ¡Estás de suerte! Este tutorial te guiará por el proceso usando Aspose.Words para .NET. Lo dividiremos en pasos sencillos para que puedas seguirlo fácilmente. ¡Adelante, añade ese texto marcado como un profesional!

## Prerrequisitos

Antes de comenzar, asegurémonos de que tienes todo lo que necesitas:

- Aspose.Words para .NET: Asegúrate de tenerlo instalado. Si no, puedes... [Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: cualquier entorno de desarrollo .NET como Visual Studio.
- Conocimientos básicos de C#: comprender los conceptos básicos de programación de C# será de ayuda.
- Documento de Word con marcadores: un documento de Word con marcadores configurados, que usaremos para agregar texto.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios. Esto nos asegurará tener todas las herramientas necesarias a mano.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Desglosemos el ejemplo en pasos detallados.

## Paso 1: Cargar el documento e inicializar las variables

Muy bien, comencemos cargando nuestro documento de Word e inicializando las variables que necesitaremos.

```csharp
// Cargue los documentos de origen y destino.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicializar el importador de documentos.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Encuentra el marcador en el documento fuente.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Paso 2: Identificar los párrafos inicial y final

Ahora, localicemos los párrafos donde comienza y termina el marcador. Esto es crucial, ya que necesitamos gestionar el texto dentro de estos límites.

```csharp
// Este es el párrafo que contiene el comienzo del marcador.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Este es el párrafo que contiene el final del marcador.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Paso 3: Validar los padres del párrafo

Necesitamos asegurarnos de que los párrafos inicial y final tengan el mismo padre. Este es un escenario simple para simplificar las cosas.

```csharp
// Limitémonos a un escenario razonablemente simple.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Paso 4: Identificar el nodo que se va a detener

A continuación, debemos determinar el nodo donde dejaremos de copiar texto. Este será el nodo inmediatamente después del último párrafo.

```csharp
// Queremos copiar todos los párrafos desde el párrafo inicial hasta (e incluyendo) el párrafo final,
// Por lo tanto, el nodo en el que nos detenemos es uno después del párrafo final.
Node endNode = endPara.NextSibling;
```

## Paso 5: Anexar texto marcado al documento de destino

Por último, recorramos los nodos desde el párrafo inicial hasta el nodo después del párrafo final y adjúntelos al documento de destino.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Esto crea una copia del nodo actual y lo importa (lo hace válido) en el contexto
    // del documento de destino. Importar implica ajustar correctamente los estilos y los identificadores de lista.
    Node newNode = importer.ImportNode(curNode, true);

    // Añade el nodo importado al documento de destino.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Guarde el documento de destino con el texto adjunto.
dstDoc.Save("appended_document.docx");
```

## Conclusión

¡Y listo! Has añadido texto de una sección marcada en un documento de Word con Aspose.Words para .NET. Esta potente herramienta facilita la manipulación de documentos, y ahora tienes un as bajo la manga. ¡Que disfrutes programando!

## Preguntas frecuentes

### ¿Puedo agregar texto de varios marcadores a la vez?
Sí, puedes repetir el proceso para cada marcador y agregar el texto correspondiente.

### ¿Qué pasa si los párrafos inicial y final tienen padres diferentes?
El ejemplo actual asume que tienen el mismo padre. Para padres diferentes, se requiere un manejo más complejo.

### ¿Puedo conservar el formato original del texto adjunto?
¡Por supuesto! El `ImportFormatMode.KeepSourceFormatting` garantiza que se conserve el formato original.

### ¿Es posible agregar texto a una posición específica en el documento de destino?
Sí, puede agregar el texto a cualquier posición navegando hasta el nodo deseado en el documento de destino.

### ¿Qué pasa si necesito agregar texto de un marcador a una nueva sección?
Puede crear una nueva sección en el documento de destino y agregar el texto allí.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}