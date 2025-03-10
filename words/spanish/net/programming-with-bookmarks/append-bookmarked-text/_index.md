---
title: Añadir texto marcado como favorito en un documento de Word
linktitle: Añadir texto marcado como favorito en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a agregar texto marcado en un documento de Word con Aspose.Words para .NET con esta guía paso a paso. Perfecta para desarrolladores.
weight: 10
url: /es/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Añadir texto marcado como favorito en un documento de Word

## Introducción

¡Hola! ¿Alguna vez intentaste agregar texto de una sección marcada en un documento de Word y te resultó complicado? ¡Estás de suerte! Este tutorial te guiará a través del proceso usando Aspose.Words para .NET. Lo dividiremos en pasos simples para que puedas seguirlo fácilmente. ¡Vamos a sumergirnos y agregar ese texto marcado como un profesional!

## Prerrequisitos

Antes de comenzar, asegurémonos de que tienes todo lo que necesitas:

-  Aspose.Words para .NET: Asegúrate de tenerlo instalado. Si no es así, puedes[Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: cualquier entorno de desarrollo .NET como Visual Studio.
- Conocimientos básicos de C#: comprender los conceptos básicos de programación de C# será útil.
- Documento de Word con marcadores: un documento de Word con marcadores configurados, que usaremos para agregar texto.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Esto garantizará que tengamos todas las herramientas que necesitamos a nuestro alcance.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Dividamos el ejemplo en pasos detallados.

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

Ahora, localicemos los párrafos donde comienza y termina el marcador. Esto es crucial, ya que debemos manejar el texto dentro de estos límites.

```csharp
// Este es el párrafo que contiene el comienzo del marcador.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Este es el párrafo que contiene el final del marcador.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Paso 3: Validar los párrafos principales

Necesitamos asegurarnos de que los párrafos de inicio y fin tengan el mismo padre. Este es un escenario simple para que las cosas sean más sencillas.

```csharp
// Limitémonos a un escenario razonablemente simple.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Paso 4: Identificar el nodo que se va a detener

A continuación, debemos determinar el nodo en el que dejaremos de copiar texto. Este será el nodo que se encuentra inmediatamente después del párrafo final.

```csharp
// Queremos copiar todos los párrafos desde el párrafo inicial hasta (e incluyendo) el párrafo final,
// Por lo tanto, el nodo en el que nos detenemos es uno después del párrafo final.
Node endNode = endPara.NextSibling;
```

## Paso 5: Anexar texto marcado al documento de destino

Por último, recorramos los nodos desde el párrafo inicial hasta el nodo después del párrafo final y agreguémoslos al documento de destino.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Esto crea una copia del nodo actual y lo importa (lo hace válido) en el contexto.
    // del documento de destino. Importar significa ajustar correctamente los estilos y los identificadores de lista.
    Node newNode = importer.ImportNode(curNode, true);

    // Añade el nodo importado al documento de destino.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Guarde el documento de destino con el texto adjunto.
dstDoc.Save("appended_document.docx");
```

## Conclusión

¡Y ya está! Has añadido texto de una sección marcada en un documento de Word con éxito usando Aspose.Words para .NET. Esta poderosa herramienta hace que la manipulación de documentos sea muy sencilla y ahora tienes un truco más bajo la manga. ¡Que disfrutes codificando!

## Preguntas frecuentes

### ¿Puedo añadir texto de varios marcadores a la vez?
Sí, puedes repetir el proceso para cada marcador y añadir el texto correspondiente.

### ¿Qué pasa si los párrafos inicial y final tienen padres diferentes?
En el ejemplo actual se supone que tienen el mismo padre. Para padres diferentes, se requiere un manejo más complejo.

### ¿Puedo conservar el formato original del texto adjunto?
 ¡Por supuesto!`ImportFormatMode.KeepSourceFormatting` garantiza que se conserve el formato original.

### ¿Es posible añadir texto a una posición específica en el documento de destino?
Sí, puede agregar el texto a cualquier posición navegando hasta el nodo deseado en el documento de destino.

### ¿Qué pasa si necesito agregar texto de un marcador a una nueva sección?
Puede crear una nueva sección en el documento de destino y agregar el texto allí.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
