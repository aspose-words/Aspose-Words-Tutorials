---
title: Desenredar marcadores de fila en un documento de Word
linktitle: Desenredar marcadores de fila en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Desenrede los marcadores de filas enredados en sus documentos de Word con facilidad usando Aspose.Words para .NET. Esta guía lo guía a través del proceso para lograr una gestión de marcadores más limpia y segura.
weight: 10
url: /es/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Desenredar marcadores de fila en un documento de Word

## Introducción

¿Alguna vez se ha encontrado con una situación en la que al eliminar una fila en un documento de Word mediante un marcador se estropean otros marcadores en filas adyacentes? Esto puede resultar increíblemente frustrante, especialmente cuando se trata de tablas complejas. Afortunadamente, Aspose.Words para .NET ofrece una solución poderosa: desenredar los marcadores de filas. 

Esta guía lo guiará a través del proceso de desenredar los marcadores de filas en sus documentos de Word usando Aspose.Words para .NET. Dividiremos el código en pasos fáciles de entender y explicaremos el propósito de cada función, permitiéndole abordar esos molestos problemas de marcadores con confianza.

## Requisitos previos

Antes de sumergirte, necesitarás algunas cosas:

1.  Aspose.Words para .NET: esta biblioteca comercial proporciona funcionalidades para trabajar con documentos de Word mediante programación. 2. Puedes descargar una prueba gratuita desde[enlace de descarga](https://releases.aspose.com/words/net/) o comprar una licencia de[comprar](https://purchase.aspose.com/buy).
3. Entorno de desarrollo AC#: Visual Studio o cualquier otro IDE de C# funcionará perfectamente.
4. Un documento de Word con marcadores de fila: usaremos un documento de muestra llamado "Marcadores de columna de tabla.docx" con fines de demostración.

## Importar espacios de nombres

El primer paso consiste en importar los espacios de nombres necesarios a su proyecto C#. Estos espacios de nombres brindan acceso a las clases y funcionalidades que usaremos desde Aspose.Words para .NET:

```csharp
using Aspose.Words;
using System;
```

## Paso 1: cargue el documento de Word

 Comenzamos cargando el documento de Word que contiene los marcadores de filas enredadas. El`Document` La clase maneja la manipulación de documentos en Aspose.Words. A continuación se explica cómo cargar el documento:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Reemplace con la ubicación de su documento
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Recuerde reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real a su archivo "Columna de tabla bookmarks.docx".

## Paso 2: Desenredar los marcadores de fila

 ¡Aquí es donde ocurre la magia! El`Untangle` La función se encarga de desenredar los marcadores de fila. Analicemos su funcionalidad:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Obtener la fila principal del marcador y del final del marcador
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Compruebe si las filas son válidas y adyacentes
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Mover el final del marcador al último párrafo de la última celda de la fila superior
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Aquí hay una explicación paso a paso de lo que hace el código:

 Repetimos todos los marcadores del documento utilizando un`foreach` bucle.
Para cada marcador, recuperamos la fila principal tanto del inicio del marcador (`bookmark.BookmarkStart`) y el final del marcador (`bookmark.BookmarkEnd` ) usando el`GetAncestor` método.
Luego verificamos si se encuentran ambas filas (`row1 != null`y`row2 != null`) y si son filas adyacentes (`row1.NextSibling == row2`). Esto garantiza que solo modifiquemos los marcadores que abarcan filas adyacentes.
Si se cumplen las condiciones, movemos el nodo final del marcador al final del último párrafo en la última celda de la fila superior (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) desenredarlos efectivamente.

## Paso 3: eliminar fila por marcador

 Ahora que los marcadores están desenredados, podemos eliminar filas de forma segura usando sus nombres de marcadores. El`DeleteRowByBookmark` La función maneja esta tarea:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Aquí hay un desglose de esta función:

Tomamos el nombre del marcador (`bookmarkName`) como entrada.
 Recuperamos el objeto marcador correspondiente usando`doc.Range.Bookmarks[bookmarkName]`.
Luego comenzamos a usar la fila principal del marcador.`GetAncestor` (similar a la`Untangle` función).
Finalmente, verificamos si el marcador y la fila existen (`bookmark != null` y

## Paso 4: verificar el desenredado

 Mientras que el`Untangle` La función debe garantizar la seguridad de otros marcadores, siempre es una buena práctica verificarlo. Así es como podemos verificar si el proceso de desenredado no eliminó accidentalmente el final de otro marcador:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Este fragmento de código comprueba si el final del marcador denominado "ROW1" todavía existe después de eliminar la fila con el marcador "ROW2". Si es nulo, se genera una excepción, lo que indica un problema con el proceso de desenredado. 

## Paso 5: guarde el documento

 Finalmente, después de desenredar los marcadores y potencialmente eliminar filas, guarde el documento modificado usando el`Save` método:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Esto guarda el documento con los marcadores desenredados y las filas eliminadas con un nuevo nombre de archivo "WorkingWithBookmarks.UntangleRowBookmarks.docx". 

## Conclusión

 Siguiendo estos pasos y utilizando el`Untangle`función, puede desenredar eficazmente los marcadores de filas en sus documentos de Word con Aspose.Words para .NET. Esto garantiza que eliminar filas de marcadores no cause consecuencias no deseadas con otros marcadores en filas adyacentes. Recuerde reemplazar marcadores de posición como`"YOUR DOCUMENT DIRECTORY"` con sus rutas reales y nombres de archivos.

## Preguntas frecuentes

### ¿Aspose.Words para .NET es gratuito?

 Aspose.Words para .NET es una biblioteca comercial con una prueba gratuita disponible. Puedes descargarlo desde[enlace de descarga](https://releases.aspose.com/words/net/).

### ¿Puedo desenredar los marcadores de fila manualmente en Word?

Si bien es técnicamente posible, desenredar manualmente los marcadores en Word puede resultar tedioso y propenso a errores. Aspose.Words para .NET automatiza este proceso, ahorrándole tiempo y esfuerzo.

###  ¿Qué pasa si el`Untangle` function encounters an error?

El código incluye un controlador de excepciones que genera una excepción si el proceso de desenredado elimina accidentalmente el final de otro marcador. Puede personalizar este manejo de errores para adaptarlo a sus necesidades específicas.

### ¿Puedo usar este código para desenredar marcadores en filas no adyacentes?

Actualmente, el código se centra en desenredar los marcadores que se extienden por filas adyacentes. Modificar el código para manejar filas no adyacentes requeriría lógica adicional para identificar y manejar esos escenarios.

### ¿Existe alguna limitación para utilizar este enfoque?

Este enfoque supone que los marcadores están bien definidos dentro de las celdas de la tabla. Si los marcadores se colocan fuera de las celdas o en ubicaciones inesperadas, es posible que el proceso de desenredado no funcione según lo previsto.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
