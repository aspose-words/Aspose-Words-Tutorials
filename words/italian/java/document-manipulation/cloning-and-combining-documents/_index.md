---
"description": "Scopri come clonare e combinare documenti in Aspose.Words per Java. Guida passo passo con esempi di codice sorgente."
"linktitle": "Clonazione e combinazione di documenti"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Clonazione e combinazione di documenti in Aspose.Words per Java"
"url": "/it/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Clonazione e combinazione di documenti in Aspose.Words per Java


## Introduzione alla clonazione e alla combinazione di documenti in Aspose.Words per Java

In questo tutorial esploreremo come clonare e combinare documenti utilizzando Aspose.Words per Java. Analizzeremo diversi scenari, tra cui la clonazione di un documento, l'inserimento di documenti in corrispondenza di punti di sostituzione, segnalibri e durante le operazioni di stampa unione.

## Fase 1: Clonazione di un documento

Per clonare un documento in Aspose.Words per Java, puoi utilizzare `deepClone()` metodo. Ecco un semplice esempio:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Questo codice creerà un clone profondo del documento originale e lo salverà come un nuovo file.

## Fase 2: Inserimento di documenti nei punti di sostituzione

È possibile inserire documenti in punti di sostituzione specifici in un altro documento. Ecco come fare:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

In questo esempio utilizziamo un `FindReplaceOptions` oggetto per specificare un gestore di callback per la sostituzione. L' `InsertDocumentAtReplaceHandler` la classe gestisce la logica di inserimento.

## Passaggio 3: inserimento di documenti nei segnalibri

Per inserire un documento in un segnalibro specifico di un altro documento, puoi utilizzare il seguente codice:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Qui troviamo il segnalibro per nome e utilizziamo il `insertDocument` metodo per inserire il contenuto del `subDoc` documento nella posizione del segnalibro.

## Fase 4: Inserimento di documenti durante la stampa unione

È possibile inserire documenti durante un'operazione di stampa unione in Aspose.Words per Java. Ecco come:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

In questo esempio, impostiamo un callback di unione dei campi utilizzando `InsertDocumentAtMailMergeHandler` classe per gestire l'inserimento del documento specificato dal campo "Document_1".

## Conclusione

La clonazione e la combinazione di documenti in Aspose.Words per Java possono essere eseguite utilizzando diverse tecniche. Che si tratti di clonare un documento, inserire contenuti in punti di sostituzione, segnalibri o durante la stampa unione, Aspose.Words offre potenti funzionalità per gestire i documenti in modo fluido.

## Domande frequenti

### Come faccio a clonare un documento in Aspose.Words per Java?

È possibile clonare un documento in Aspose.Words per Java utilizzando `deepClone()` metodo. Ecco un esempio:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Come posso inserire un documento in un segnalibro?

Per inserire un documento in un segnalibro in Aspose.Words per Java, puoi trovare il segnalibro per nome e quindi utilizzare `insertDocument` Metodo per inserire il contenuto. Ecco un esempio:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Come posso inserire documenti durante la stampa unione in Aspose.Words per Java?

È possibile inserire documenti durante la stampa unione in Aspose.Words per Java impostando una callback per l'unione dei campi e specificando il documento da inserire. Ecco un esempio:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

In questo esempio, il `InsertDocumentAtMailMergeHandler` La classe gestisce la logica di inserimento per "DocumentField" durante la stampa unione.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}