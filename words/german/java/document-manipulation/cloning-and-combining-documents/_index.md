---
"description": "Erfahren Sie, wie Sie Dokumente in Aspose.Words für Java klonen und kombinieren. Schritt-für-Schritt-Anleitung mit Quellcodebeispielen."
"linktitle": "Klonen und Kombinieren von Dokumenten"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Klonen und Kombinieren von Dokumenten in Aspose.Words für Java"
"url": "/de/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Klonen und Kombinieren von Dokumenten in Aspose.Words für Java


## Einführung in das Klonen und Kombinieren von Dokumenten in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie Dokumente mit Aspose.Words für Java klonen und kombinieren. Wir behandeln verschiedene Szenarien, darunter das Klonen eines Dokuments, das Einfügen von Dokumenten an Ersetzungspunkten, Lesezeichen und Serienbriefvorgänge.

## Schritt 1: Klonen eines Dokuments

Um ein Dokument in Aspose.Words für Java zu klonen, können Sie das `deepClone()` Methode. Hier ist ein einfaches Beispiel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Dieser Code erstellt einen vollständigen Klon des Originaldokuments und speichert ihn als neue Datei.

## Schritt 2: Dokumente an Ersetzungspunkten einfügen

Sie können Dokumente an bestimmten Stellen in ein anderes Dokument einfügen. So geht's:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

In diesem Beispiel verwenden wir eine `FindReplaceOptions` Objekt, um einen Callback-Handler für den Ersatz anzugeben. Das `InsertDocumentAtReplaceHandler` Die Klasse behandelt die Einfügelogik.

## Schritt 3: Dokumente an Lesezeichen einfügen

Um ein Dokument an einer bestimmten Stelle eines Lesezeichens in ein anderes Dokument einzufügen, können Sie den folgenden Code verwenden:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Hier finden wir das Lesezeichen nach Namen und verwenden die `insertDocument` Methode zum Einfügen des Inhalts der `subDoc` Dokument an der Lesezeichenposition.

## Schritt 4: Einfügen von Dokumenten während der Serienbrieffunktion

Sie können Dokumente während eines Seriendruckvorgangs in Aspose.Words für Java einfügen. So geht's:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

In diesem Beispiel setzen wir einen Callback für die Feldzusammenführung mit dem `InsertDocumentAtMailMergeHandler` Klasse, die das Einfügen des im Feld „Document_1“ angegebenen Dokuments handhabt.

## Abschluss

Das Klonen und Kombinieren von Dokumenten in Aspose.Words für Java kann mithilfe verschiedener Techniken erfolgen. Ob Sie ein Dokument klonen, Inhalte an Ersetzungspunkten, Lesezeichen oder während des Seriendrucks einfügen möchten – Aspose.Words bietet leistungsstarke Funktionen zur nahtlosen Bearbeitung von Dokumenten.

## Häufig gestellte Fragen

### Wie klone ich ein Dokument in Aspose.Words für Java?

Sie können ein Dokument in Aspose.Words für Java klonen, indem Sie `deepClone()` Methode. Hier ist ein Beispiel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Wie kann ich ein Dokument an einem Lesezeichen einfügen?

Um ein Dokument in einem Lesezeichen in Aspose.Words für Java einzufügen, können Sie das Lesezeichen nach Namen suchen und dann die `insertDocument` Methode zum Einfügen des Inhalts. Hier ist ein Beispiel:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Wie füge ich während der Serienbrieferstellung in Aspose.Words für Java Dokumente ein?

Sie können Dokumente während des Seriendrucks in Aspose.Words für Java einfügen, indem Sie einen Rückruf für die Feldzusammenführung einrichten und das einzufügende Dokument angeben. Hier ein Beispiel:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

In diesem Beispiel `InsertDocumentAtMailMergeHandler` Die Klasse verarbeitet die Einfügelogik für das „DocumentField“ während des Serienbriefbetriebs.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}