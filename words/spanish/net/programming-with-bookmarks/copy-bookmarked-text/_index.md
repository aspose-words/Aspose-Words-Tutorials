---
"description": "Copie fácilmente texto marcado entre documentos de Word con Aspose.Words para .NET. Aprenda cómo con esta guía paso a paso."
"linktitle": "Copiar texto marcado en un documento de Word"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Copiar texto marcado en un documento de Word"
"url": "/es/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Copiar texto marcado en un documento de Word

## Introducción

¿Alguna vez has tenido que copiar secciones específicas de un documento de Word a otro? ¡Tienes suerte! En este tutorial, te explicaremos cómo copiar texto marcado de un documento de Word a otro usando Aspose.Words para .NET. Tanto si creas un informe dinámico como si automatizas la generación de documentos, esta guía te simplificará el proceso.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

- Biblioteca Aspose.Words para .NET: puede descargarla desde [aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: Visual Studio o cualquier otro entorno de desarrollo .NET.
- Conocimientos básicos de C#: Familiaridad con la programación en C# y el marco .NET.

## Importar espacios de nombres

Para comenzar, asegúrese de tener los espacios de nombres necesarios importados en su proyecto:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Paso 1: Cargar el documento fuente

Lo primero es lo primero: debes cargar el documento de origen que contiene el texto marcado que deseas copiar.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Aquí, `dataDir` es la ruta al directorio de su documento, y `Bookmarks.docx` Es el documento fuente.

## Paso 2: Identificar el marcador

A continuación, identifique el marcador que desea copiar del documento de origen.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Reemplazar `"MyBookmark1"` con el nombre real de tu marcador.

## Paso 3: Crear el documento de destino

Ahora, crea un nuevo documento donde se copiará el texto marcado.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Paso 4: Importar contenido marcado

Para garantizar que se conserven los estilos y el formato, utilice `NodeImporter` para importar el contenido marcado del documento de origen al documento de destino.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Paso 5: Definir el método AppendBookmarkedText

Aquí es donde ocurre la magia. Define un método para gestionar la copia del texto marcado:

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

¡Listo! Has copiado correctamente el texto marcado de un documento de Word a otro con Aspose.Words para .NET. Este método es eficaz para automatizar la manipulación de documentos, optimizando y optimizando tu flujo de trabajo.

## Preguntas frecuentes

### ¿Puedo copiar varios marcadores a la vez?
Sí, puedes iterar a través de múltiples marcadores y usar el mismo método para copiar cada uno.

### ¿Qué pasa si no se encuentra el marcador?
El `Range.Bookmarks` la propiedad volverá `null`, así que asegúrese de manejar este caso para evitar excepciones.

### ¿Puedo conservar el formato del marcador original?
¡Por supuesto! Usando `ImportFormatMode.KeepSourceFormatting` garantiza que se conserve el formato original.

### ¿Existe un límite para el tamaño del texto marcado?
No hay un límite específico, pero el rendimiento puede variar con documentos extremadamente grandes.

### ¿Puedo copiar texto entre diferentes formatos de documentos de Word?
Sí, Aspose.Words admite varios formatos de Word y el método funciona en todos estos formatos.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}