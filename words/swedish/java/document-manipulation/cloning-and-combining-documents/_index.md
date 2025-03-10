---
title: Klona och kombinera dokument i Aspose.Words för Java
linktitle: Klona och kombinera dokument
second_title: Aspose.Words Java Document Processing API
description: Lär dig att klona och kombinera dokument i Aspose.Words för Java. Steg-för-steg-guide med exempel på källkod.
weight: 27
url: /sv/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Klona och kombinera dokument i Aspose.Words för Java


## Introduktion till kloning och kombination av dokument i Aspose.Words för Java

I den här handledningen kommer vi att utforska hur man klona och kombinera dokument med Aspose.Words för Java. Vi kommer att täcka olika scenarier, inklusive kloning av ett dokument, infogning av dokument vid ersättningspunkter, bokmärken och under kopplingsoperationer.

## Steg 1: Klona ett dokument

 För att klona ett dokument i Aspose.Words för Java kan du använda`deepClone()` metod. Här är ett enkelt exempel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Denna kod kommer att skapa en djup klon av originaldokumentet och spara den som en ny fil.

## Steg 2: Infoga dokument vid ersättningspunkter

Du kan infoga dokument på specifika ersättningspunkter i ett annat dokument. Så här kan du göra det:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

 I det här exemplet använder vi a`FindReplaceOptions` objekt för att ange en återuppringningshanterare för ersättningen. De`InsertDocumentAtReplaceHandler` klass hanterar insättningslogiken.

## Steg 3: Infoga dokument vid bokmärken

För att infoga ett dokument vid ett specifikt bokmärke i ett annat dokument kan du använda följande kod:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

 Här hittar vi bokmärket efter namn och använder`insertDocument` metod för att infoga innehållet i`subDoc` dokument på bokmärkesplatsen.

## Steg 4: Infoga dokument under sammanfogning

Du kan infoga dokument under en kopplingsoperation i Aspose.Words för Java. Så här gör du:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

 I det här exemplet ställer vi in ett fältsammanfogande återuppringning med hjälp av`InsertDocumentAtMailMergeHandler` klass för att hantera infogningen av dokumentet som anges i fältet "Dokument_1".

## Slutsats

Kloning och kombination av dokument i Aspose.Words för Java kan utföras med olika tekniker. Oavsett om du behöver klona ett dokument, infoga innehåll vid ersättningspunkter, bokmärken eller under sammanslagning, erbjuder Aspose.Words kraftfulla funktioner för att manipulera dokument sömlöst.

## FAQ's

### Hur klona jag ett dokument i Aspose.Words för Java?

 Du kan klona ett dokument i Aspose.Words för Java med hjälp av`deepClone()` metod. Här är ett exempel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Hur kan jag infoga ett dokument vid ett bokmärke?

 För att infoga ett dokument vid ett bokmärke i Aspose.Words för Java kan du hitta bokmärket efter namn och sedan använda`insertDocument` sätt att infoga innehållet. Här är ett exempel:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Hur infogar jag dokument under sammanslagningen i Aspose.Words för Java?

Du kan infoga dokument under sammanslagningen i Aspose.Words för Java genom att ställa in ett fält som sammanfogar återuppringning och ange dokumentet som ska infogas. Här är ett exempel:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

 I det här exemplet är`InsertDocumentAtMailMergeHandler`klass hanterar infogningslogiken för "DocumentField" under sammanslagningen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
