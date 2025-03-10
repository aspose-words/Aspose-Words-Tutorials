---
title: Copiar texto marcado en un documento de Word
linktitle: Copiar texto marcado en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Copie texto marcado entre documentos de Word sin esfuerzo con Aspose.Words para .NET. Aprenda cómo hacerlo con esta guía paso a paso.
weight: 10
url: /es/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Copiar texto marcado en un documento de Word

## Introducción

¿Alguna vez ha tenido que copiar secciones específicas de un documento de Word a otro? ¡Pues está de suerte! En este tutorial, le explicaremos cómo copiar texto marcado de un documento de Word a otro utilizando Aspose.Words para .NET. Ya sea que esté creando un informe dinámico o automatizando la generación de documentos, esta guía le simplificará el proceso.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Biblioteca Aspose.Words para .NET: puede descargarla desde[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: Visual Studio o cualquier otro entorno de desarrollo .NET.
- Conocimientos básicos de C#: Familiaridad con la programación en C# y el marco .NET.

## Importar espacios de nombres

Para comenzar, asegúrese de tener los espacios de nombres necesarios importados en su proyecto:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Paso 1: Cargue el documento fuente

Lo primero es lo primero: debes cargar el documento fuente que contiene el texto marcado que deseas copiar.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Aquí,`dataDir` es la ruta al directorio de su documento, y`Bookmarks.docx` Es el documento fuente.

## Paso 2: Identificar el marcador

A continuación, identifique el marcador que desea copiar del documento fuente.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Reemplazar`"MyBookmark1"` con el nombre real de tu marcador.

## Paso 3: Crear el documento de destino

Ahora, crea un nuevo documento donde se copiará el texto marcado.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Paso 4: Importar contenido marcado

 Para garantizar que se conserven los estilos y el formato, utilice`NodeImporter` para importar el contenido marcado del documento de origen al documento de destino.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Paso 5: Definir el método AppendBookmarkedText

Aquí es donde ocurre la magia. Defina un método para gestionar la copia del texto marcado:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Paso 6: Guardar el documento de destino

Por último, guarde el documento de destino para verificar el contenido copiado.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Conclusión

¡Y eso es todo! Has copiado con éxito el texto marcado de un documento de Word a otro usando Aspose.Words para .NET. Este método es eficaz para automatizar las tareas de manipulación de documentos, lo que hace que tu flujo de trabajo sea más eficiente y optimizado.

## Preguntas frecuentes

### ¿Puedo copiar varios marcadores a la vez?
Sí, puedes iterar a través de varios marcadores y utilizar el mismo método para copiar cada uno.

### ¿Qué pasa si no se encuentra el marcador?
 El`Range.Bookmarks` La propiedad regresará`null`, así que asegúrese de manejar este caso para evitar excepciones.

### ¿Puedo conservar el formato del marcador original?
 ¡Por supuesto! Utilizando`ImportFormatMode.KeepSourceFormatting` garantiza que se conserve el formato original.

### ¿Existe un límite para el tamaño del texto marcado?
No hay un límite específico, pero el rendimiento puede variar con documentos extremadamente grandes.

### ¿Puedo copiar texto entre diferentes formatos de documentos de Word?
Sí, Aspose.Words admite varios formatos de Word y el método funciona en todos estos formatos.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
