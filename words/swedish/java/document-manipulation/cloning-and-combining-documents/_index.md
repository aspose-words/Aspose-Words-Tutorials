---
"description": "Lär dig hur du klonar och kombinerar dokument i Aspose.Words för Java. Steg-för-steg-guide med exempel på källkod."
"linktitle": "Kloning och kombination av dokument"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Kloning och kombination av dokument i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kloning och kombination av dokument i Aspose.Words för Java


## Introduktion till kloning och kombination av dokument i Aspose.Words för Java

den här handledningen utforskar vi hur man klonar och kombinerar dokument med Aspose.Words för Java. Vi går igenom olika scenarier, inklusive kloning av ett dokument, infogning av dokument vid ersättningspunkter, bokmärken och under dokumentkopplingar.

## Steg 1: Klona ett dokument

För att klona ett dokument i Aspose.Words för Java kan du använda `deepClone()` metod. Här är ett enkelt exempel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Den här koden skapar en djup klon av originaldokumentet och sparar det som en ny fil.

## Steg 2: Infoga dokument vid ersättningspunkter

Du kan infoga dokument vid specifika ersättningspunkter i ett annat dokument. Så här gör du:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

I det här exemplet använder vi en `FindReplaceOptions` objekt för att ange en återanropshanterare för ersättningen. `InsertDocumentAtReplaceHandler` klassen hanterar insättningslogiken.

## Steg 3: Infoga dokument i bokmärken

För att infoga ett dokument vid ett specifikt bokmärke i ett annat dokument kan du använda följande kod:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Här hittar vi bokmärket efter namn och använder `insertDocument` metod för att infoga innehållet i `subDoc` dokumentet på bokmärkesplatsen.

## Steg 4: Infoga dokument under dokumentkoppling

Du kan infoga dokument under en dokumentkoppling i Aspose.Words för Java. Så här gör du:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

I det här exemplet ställer vi in en återanropsfunktion för fältsammanslagning med hjälp av `InsertDocumentAtMailMergeHandler` klass för att hantera infogningen av dokumentet som anges i fältet "Dokument_1".

## Slutsats

Kloning och kombination av dokument i Aspose.Words för Java kan göras med olika tekniker. Oavsett om du behöver klona ett dokument, infoga innehåll vid ersättningspunkter, bokmärken eller under dokumentkoppling, erbjuder Aspose.Words kraftfulla funktioner för att manipulera dokument sömlöst.

## Vanliga frågor

### Hur klonar jag ett dokument i Aspose.Words för Java?

Du kan klona ett dokument i Aspose.Words för Java med hjälp av `deepClone()` metod. Här är ett exempel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Hur kan jag infoga ett dokument i ett bokmärke?

För att infoga ett dokument i ett bokmärke i Aspose.Words för Java kan du söka efter bokmärket efter namn och sedan använda `insertDocument` metod för att infoga innehållet. Här är ett exempel:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Hur infogar jag dokument under dokumentkoppling i Aspose.Words för Java?

Du kan infoga dokument under dokumentkoppling i Aspose.Words för Java genom att ställa in en återanropsfunktion för fältkoppling och ange vilket dokument som ska infogas. Här är ett exempel:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

I det här exemplet, `InsertDocumentAtMailMergeHandler` Klassen hanterar infogningslogiken för "DocumentField" under dokumentkoppling.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}