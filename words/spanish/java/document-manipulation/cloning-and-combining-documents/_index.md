---
"description": "Aprenda a clonar y combinar documentos en Aspose.Words para Java. Guía paso a paso con ejemplos de código fuente."
"linktitle": "Clonación y combinación de documentos"
"second_title": "API de procesamiento de documentos Java de Aspose.Words"
"title": "Clonación y combinación de documentos en Aspose.Words para Java"
"url": "/es/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Clonación y combinación de documentos en Aspose.Words para Java


## Introducción a la clonación y combinación de documentos en Aspose.Words para Java

En este tutorial, exploraremos cómo clonar y combinar documentos con Aspose.Words para Java. Cubriremos diversos escenarios, como la clonación de documentos, la inserción de documentos en puntos de reemplazo, marcadores y durante las operaciones de combinación de correspondencia.

## Paso 1: Clonar un documento

Para clonar un documento en Aspose.Words para Java, puede utilizar el `deepClone()` Método. He aquí un ejemplo sencillo:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Este código creará un clon profundo del documento original y lo guardará como un archivo nuevo.

## Paso 2: Inserción de documentos en puntos de reemplazo

Puedes insertar documentos en puntos de reemplazo específicos de otro documento. Así es como se hace:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

En este ejemplo, utilizamos un `FindReplaceOptions` objeto para especificar un controlador de devolución de llamada para el reemplazo. El `InsertDocumentAtReplaceHandler` La clase maneja la lógica de inserción.

## Paso 3: Insertar documentos en marcadores

Para insertar un documento en un marcador específico en otro documento, puede utilizar el siguiente código:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Aquí, buscamos el marcador por nombre y usamos el `insertDocument` método para insertar el contenido del `subDoc` documento en la ubicación del marcador.

## Paso 4: Inserción de documentos durante la combinación de correspondencia

Puedes insertar documentos durante una operación de combinación de correspondencia en Aspose.Words para Java. A continuación te explicamos cómo:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

En este ejemplo, establecemos una devolución de llamada de fusión de campos utilizando el `InsertDocumentAtMailMergeHandler` clase para manejar la inserción del documento especificado por el campo "Documento_1".

## Conclusión

La clonación y combinación de documentos en Aspose.Words para Java se puede realizar mediante diversas técnicas. Ya sea para clonar un documento, insertar contenido en puntos de reemplazo, marcadores o durante la combinación de correspondencia, Aspose.Words ofrece potentes funciones para manipular documentos sin problemas.

## Preguntas frecuentes

### ¿Cómo clono un documento en Aspose.Words para Java?

Puede clonar un documento en Aspose.Words para Java usando el `deepClone()` Método. Aquí tienes un ejemplo:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### ¿Cómo puedo insertar un documento en un marcador?

Para insertar un documento en un marcador en Aspose.Words para Java, puede buscar el marcador por nombre y luego usar el `insertDocument` Método para insertar el contenido. Ejemplo:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### ¿Cómo inserto documentos durante la combinación de correspondencia en Aspose.Words para Java?

Puede insertar documentos durante la combinación de correspondencia en Aspose.Words para Java configurando una llamada de combinación de campos y especificando el documento que se insertará. A continuación, se muestra un ejemplo:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

En este ejemplo, el `InsertDocumentAtMailMergeHandler` La clase maneja la lógica de inserción del "DocumentField" durante la combinación de correspondencia.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}