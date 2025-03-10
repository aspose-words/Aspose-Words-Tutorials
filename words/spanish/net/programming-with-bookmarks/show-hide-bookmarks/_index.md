---
title: Mostrar Ocultar marcadores en un documento de Word
linktitle: Mostrar Ocultar marcadores en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda cómo mostrar u ocultar dinámicamente marcadores en un documento de Word usando Aspose.Words para .NET con nuestra guía paso a paso. Perfecto para desarrolladores.
weight: 10
url: /es/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mostrar Ocultar marcadores en un documento de Word

## Introducción

¿Alguna vez has necesitado ocultar o mostrar ciertas partes de tu documento de Word de forma dinámica? ¡Pues estás de suerte! Con Aspose.Words para .NET, puede administrar fácilmente la visibilidad del contenido marcado como favorito en sus documentos. Este tutorial lo guiará a través del proceso de mostrar y ocultar marcadores en un documento de Word usando Aspose.Words para .NET. Desglosaremos el código paso a paso, por lo que, ya seas un desarrollador experimentado o un novato, esta guía te resultará fácil de seguir.

## Requisitos previos

Antes de profundizar en el código, asegurémonos de que tiene todo lo que necesita:

1.  Aspose.Words para .NET: asegúrese de tener instalada la biblioteca Aspose.Words para .NET. Si no, puedes descargarlo.[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: un IDE como Visual Studio.
3. Conocimientos básicos de C#: será beneficiosa la familiaridad con la programación en C#.
4. Un documento de Word: un documento de Word de muestra con marcadores.

## Importar espacios de nombres

Antes de comenzar con el código, debe importar los espacios de nombres necesarios. Agregue lo siguiente al comienzo de su archivo C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Paso 1: cargue su documento

Lo primero es lo primero: debe cargar el documento de Word que contiene los marcadores. Así es como puedes hacerlo:

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Explicación

- dataDir: esta es la ruta del directorio donde se encuentra su documento de Word.
-  Documento doc: Esto inicializa una nueva instancia del`Document` class con su archivo especificado.

## Paso 2: mostrar u ocultar contenido marcado

A continuación, definiremos un método para mostrar u ocultar el contenido marcado. Aquí está el método completo:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD favorito}" = "verdadero" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Explicación

- Bookmark bm: recupera el marcador del documento.
- Generador de DocumentBuilder: ayuda a navegar y modificar el documento.
- Campo de campo: inserta un campo IF para verificar el estado del marcador.
- Nodo currentNode: atraviesa los nodos para encontrar el inicio y el final del campo.

## Paso 3: Ejecute la función Mostrar/Ocultar

 Ahora necesitas llamar al`ShowHideBookmarkedContent` método, pasando el documento, el nombre del marcador y la bandera de visibilidad:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Explicación

- doc: Su objeto de documento.
- "MyBookmark1": el nombre del marcador que desea mostrar/ocultar.
- falso: el indicador de visibilidad (verdadero para mostrar, falso para ocultar).

## Paso 4: guarde su documento

Finalmente, guarde el documento modificado:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Explicación

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": la ruta y el nombre del nuevo documento donde se guardarán los cambios.

## Conclusión

¡Y ahí lo tienes! Ha aprendido con éxito cómo mostrar y ocultar marcadores en un documento de Word usando Aspose.Words para .NET. Esta técnica puede resultar increíblemente útil para generar dinámicamente documentos con contenido condicional.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca de procesamiento de documentos que permite a los desarrolladores crear, modificar y convertir documentos de Word mediante programación.

### ¿Cómo obtengo Aspose.Words para .NET?
 Puede descargar Aspose.Words para .NET desde[aquí](https://releases.aspose.com/words/net/). También está disponible una prueba gratuita.

### ¿Puedo utilizar este método para otros tipos de marcadores?
Sí, este método se puede adaptar para gestionar la visibilidad de cualquier marcador en su documento de Word.

### ¿Qué pasa si mi documento no contiene el marcador especificado?
Si el marcador no existe, el método arrojará un error. Asegúrese de que el marcador exista antes de intentar mostrarlo/ocultarlo.

### ¿Cómo puedo obtener soporte si tengo problemas?
 Puede obtener apoyo de la comunidad Aspose[aquí](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
