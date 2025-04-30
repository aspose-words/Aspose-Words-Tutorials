---
"description": "Leer hoe je documenten kunt klonen en combineren in Aspose.Words voor Java. Stapsgewijze handleiding met broncodevoorbeelden."
"linktitle": "Documenten klonen en combineren"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Documenten klonen en combineren in Aspose.Words voor Java"
"url": "/nl/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Documenten klonen en combineren in Aspose.Words voor Java


## Inleiding tot het klonen en combineren van documenten in Aspose.Words voor Java

In deze tutorial laten we zien hoe je documenten kunt klonen en combineren met Aspose.Words voor Java. We behandelen verschillende scenario's, waaronder het klonen van een document, het invoegen van documenten op vervangingspunten, bladwijzers en tijdens samenvoegbewerkingen.

## Stap 1: Een document klonen

Om een document in Aspose.Words voor Java te klonen, kunt u de `deepClone()` methode. Hier is een eenvoudig voorbeeld:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Deze code maakt een diepe kloon van het originele document en slaat dit op als een nieuw bestand.

## Stap 2: Documenten invoegen op vervangingspunten

Je kunt documenten op specifieke vervangingspunten in een ander document invoegen. Zo doe je dat:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

In dit voorbeeld gebruiken we een `FindReplaceOptions` object om een callback-handler voor de vervanging op te geven. `InsertDocumentAtReplaceHandler` klasse behandelt de invoeglogica.

## Stap 3: Documenten invoegen bij bladwijzers

Om een document bij een specifieke bladwijzer in een ander document in te voegen, kunt u de volgende code gebruiken:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Hier zoeken we de bladwijzer op naam en gebruiken de `insertDocument` methode om de inhoud van de `subDoc` document op de bladwijzerlocatie.

## Stap 4: Documenten invoegen tijdens het samenvoegen

U kunt documenten invoegen tijdens een samenvoegbewerking in Aspose.Words voor Java. Zo werkt het:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

In dit voorbeeld stellen we een callback voor het samenvoegen van velden in met behulp van de `InsertDocumentAtMailMergeHandler` klasse die de invoeging van het document, zoals gespecificeerd in het veld "Document_1", afhandelt.

## Conclusie

Het klonen en combineren van documenten in Aspose.Words voor Java kan met verschillende technieken worden gedaan. Of u nu een document wilt klonen, inhoud wilt invoegen op vervangingspunten, bladwijzers of tijdens een samenvoeging, Aspose.Words biedt krachtige functies om documenten naadloos te bewerken.

## Veelgestelde vragen

### Hoe kloon ik een document in Aspose.Words voor Java?

U kunt een document in Aspose.Words voor Java klonen met behulp van de `deepClone()` methode. Hier is een voorbeeld:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Hoe kan ik een document aan een bladwijzer toevoegen?

Om een document in een bladwijzer in Aspose.Words voor Java in te voegen, kunt u de bladwijzer op naam zoeken en vervolgens de `insertDocument` Methode om de inhoud in te voegen. Hier is een voorbeeld:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Hoe voeg ik documenten in tijdens een samenvoeging in Aspose.Words voor Java?

U kunt documenten invoegen tijdens het samenvoegen in Aspose.Words voor Java door een callback voor het samenvoegen van velden in te stellen en het in te voegen document op te geven. Hier is een voorbeeld:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

In dit voorbeeld is de `InsertDocumentAtMailMergeHandler` klasse verwerkt de invoeglogica voor het "DocumentField" tijdens het samenvoegen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}