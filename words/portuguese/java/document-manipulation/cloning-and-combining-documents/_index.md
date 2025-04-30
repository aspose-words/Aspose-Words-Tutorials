---
"description": "Aprenda a clonar e combinar documentos no Aspose.Words para Java. Guia passo a passo com exemplos de código-fonte."
"linktitle": "Clonagem e combinação de documentos"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Clonando e combinando documentos no Aspose.Words para Java"
"url": "/pt/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Clonando e combinando documentos no Aspose.Words para Java


## Introdução à clonagem e combinação de documentos no Aspose.Words para Java

Neste tutorial, exploraremos como clonar e combinar documentos usando o Aspose.Words para Java. Abordaremos vários cenários, incluindo clonagem de documentos, inserção de documentos em pontos de substituição, marcadores e durante operações de mala direta.

## Etapa 1: Clonando um documento

Para clonar um documento no Aspose.Words para Java, você pode usar o `deepClone()` método. Aqui está um exemplo simples:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Este código criará um clone profundo do documento original e o salvará como um novo arquivo.

## Etapa 2: Inserindo documentos em pontos de substituição

Você pode inserir documentos em pontos de substituição específicos em outro documento. Veja como fazer isso:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Neste exemplo, usamos um `FindReplaceOptions` objeto para especificar um manipulador de retorno de chamada para a substituição. O `InsertDocumentAtReplaceHandler` A classe manipula a lógica de inserção.

## Etapa 3: Inserindo documentos nos favoritos

Para inserir um documento em um marcador específico em outro documento, você pode usar o seguinte código:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Aqui, encontramos o marcador pelo nome e usamos o `insertDocument` método para inserir o conteúdo do `subDoc` documento no local do marcador.

## Etapa 4: Inserindo documentos durante a mala direta

Você pode inserir documentos durante uma operação de mala direta no Aspose.Words para Java. Veja como:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

Neste exemplo, definimos um retorno de chamada de mesclagem de campo usando o `InsertDocumentAtMailMergeHandler` classe para manipular a inserção do documento especificado pelo campo "Document_1".

## Conclusão

A clonagem e a combinação de documentos no Aspose.Words para Java podem ser realizadas por meio de diversas técnicas. Seja para clonar um documento, inserir conteúdo em pontos de substituição, favoritos ou durante mala direta, o Aspose.Words oferece recursos poderosos para manipular documentos com facilidade.

## Perguntas frequentes

### Como clonar um documento no Aspose.Words para Java?

Você pode clonar um documento no Aspose.Words para Java usando o `deepClone()` método. Aqui está um exemplo:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Como posso inserir um documento em um marcador?

Para inserir um documento em um marcador no Aspose.Words para Java, você pode encontrar o marcador pelo nome e então usar o `insertDocument` método para inserir o conteúdo. Aqui está um exemplo:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Como faço para inserir documentos durante a mala direta no Aspose.Words para Java?

Você pode inserir documentos durante a mala direta no Aspose.Words para Java definindo um retorno de chamada para mesclagem de campos e especificando o documento a ser inserido. Veja um exemplo:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

Neste exemplo, o `InsertDocumentAtMailMergeHandler` a classe manipula a lógica de inserção do "DocumentField" durante a mala direta.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}