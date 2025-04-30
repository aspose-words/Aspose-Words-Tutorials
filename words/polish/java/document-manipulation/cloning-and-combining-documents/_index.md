---
"description": "Dowiedz się, jak klonować i łączyć dokumenty w Aspose.Words dla Java. Przewodnik krok po kroku z przykładami kodu źródłowego."
"linktitle": "Klonowanie i łączenie dokumentów"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Klonowanie i łączenie dokumentów w Aspose.Words dla Java"
"url": "/pl/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Klonowanie i łączenie dokumentów w Aspose.Words dla Java


## Wprowadzenie do klonowania i łączenia dokumentów w Aspose.Words dla Java

tym samouczku pokażemy, jak klonować i łączyć dokumenty za pomocą Aspose.Words for Java. Omówimy różne scenariusze, w tym klonowanie dokumentu, wstawianie dokumentów w punktach zastępowania, zakładkach i podczas operacji korespondencji seryjnej.

## Krok 1: Klonowanie dokumentu

Aby sklonować dokument w Aspose.Words dla Java, możesz użyć `deepClone()` metoda. Oto prosty przykład:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Ten kod utworzy głęboką kopię oryginalnego dokumentu i zapisze ją jako nowy plik.

## Krok 2: Wstawianie dokumentów w punktach wymiany

Możesz wstawiać dokumenty w określonych punktach zastępowania w innym dokumencie. Oto jak możesz to zrobić:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

W tym przykładzie używamy `FindReplaceOptions` obiekt, aby określić obsługę wywołania zwrotnego dla zastąpienia. `InsertDocumentAtReplaceHandler` Klasa obsługuje logikę wstawiania.

## Krok 3: Wstawianie dokumentów do zakładek

Aby wstawić dokument do określonej zakładki w innym dokumencie, możesz użyć następującego kodu:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Tutaj znajdujemy zakładkę według nazwy i używamy `insertDocument` metoda wstawiania zawartości `subDoc` dokument w miejscu zakładki.

## Krok 4: Wstawianie dokumentów podczas korespondencji seryjnej

Możesz wstawiać dokumenty podczas operacji korespondencji seryjnej w Aspose.Words dla Java. Oto jak:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

W tym przykładzie ustawiamy wywołanie zwrotne scalania pól za pomocą `InsertDocumentAtMailMergeHandler` Klasa obsługująca wstawianie dokumentu określonego w polu "Document_1".

## Wniosek

Klonowanie i łączenie dokumentów w Aspose.Words for Java można wykonać za pomocą różnych technik. Niezależnie od tego, czy musisz sklonować dokument, wstawić zawartość w punktach zastępowania, zakładkach lub podczas scalania korespondencji, Aspose.Words zapewnia potężne funkcje do bezproblemowego manipulowania dokumentami.

## Najczęściej zadawane pytania

### Jak sklonować dokument w Aspose.Words dla Java?

Możesz sklonować dokument w Aspose.Words dla Java za pomocą `deepClone()` metoda. Oto przykład:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Jak mogę wstawić dokument do zakładki?

Aby wstawić dokument do zakładki w Aspose.Words for Java, możesz wyszukać zakładkę według nazwy, a następnie użyć `insertDocument` metoda wstawiania treści. Oto przykład:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Jak wstawiać dokumenty podczas korespondencji seryjnej w Aspose.Words dla Java?

Możesz wstawiać dokumenty podczas korespondencji seryjnej w Aspose.Words for Java, ustawiając wywołanie zwrotne scalania pól i określając dokument, który ma zostać wstawiony. Oto przykład:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

W tym przykładzie `InsertDocumentAtMailMergeHandler` Klasa obsługuje logikę wstawiania dla „DocumentField” podczas korespondencji seryjnej.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}