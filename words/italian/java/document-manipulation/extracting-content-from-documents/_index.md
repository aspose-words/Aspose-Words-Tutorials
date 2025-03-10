---
title: Estrazione di contenuto da documenti in Aspose.Words per Java
linktitle: Estrazione di contenuti dai documenti
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come estrarre facilmente contenuti dai documenti utilizzando Aspose.Words per Java. La nostra guida passo passo e gli esempi di codice semplificano il processo.
weight: 13
url: /it/java/document-manipulation/extracting-content-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Estrazione di contenuto da documenti in Aspose.Words per Java


## Introduzione all'estrazione di contenuti da documenti in Aspose.Words per Java

Nel mondo dell'elaborazione dei documenti, estrarre contenuti dai documenti è un requisito comune. Che tu debba estrarre testo, tabelle, immagini o elementi specifici del documento, Aspose.Words for Java fornisce potenti strumenti per rendere questo compito un gioco da ragazzi. In questa guida completa, ti guideremo attraverso il processo di estrazione di contenuti dai documenti utilizzando Aspose.Words for Java. 

## Prerequisiti

Prima di addentrarci nel processo di estrazione, assicurati di avere i seguenti prerequisiti:

1.  Aspose.Words per Java: dovresti avere Aspose.Words per Java installato e configurato nel tuo ambiente di sviluppo Java. Puoi scaricarlo da[Qui](https://releases.aspose.com/words/java/).

2. Un documento da cui estrarre il contenuto: per questa guida, utilizzeremo un documento di esempio denominato "Estrai contenuto.docx". Assicurati di avere un documento simile pronto per l'estrazione.

## Estrazione di contenuto tra nodi a livello di blocco

```java
// Esempio di codice Java per l'estrazione di contenuti tra nodi a livello di blocco
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getLastSection().getChild(NodeType.PARAGRAPH, 2, true);
Table endTable = (Table) doc.getLastSection().getChild(NodeType.TABLE, 0, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endTable, true);
Collections.reverse(extractedNodes);
while (extractedNodes.size() > 0) {
    endTable.getParentNode().insertAfter((Node) extractedNodes.get(0), endTable);
    extractedNodes.remove(0);
}
doc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBlockLevelNodes.docx");
```

## Estrazione del contenuto tra i segnalibri

```java
//Esempio di codice Java per l'estrazione di contenuti tra i segnalibri
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("Bookmark1");
BookmarkStart bookmarkStart = bookmark.getBookmarkStart();
BookmarkEnd bookmarkEnd = bookmark.getBookmarkEnd();
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.IncludingBookmark.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(bookmarkStart, bookmarkEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenBookmark.WithoutBookmark.docx");
```

## Estrazione del contenuto tra intervalli di commenti

```java
// Esempio di codice Java per l'estrazione di contenuto tra intervalli di commenti
Document doc = new Document("Your Directory Path" + "Extract content.docx");
CommentRangeStart commentStart = (CommentRangeStart) doc.getChild(NodeType.COMMENT_RANGE_START, 0, true);
CommentRangeEnd commentEnd = (CommentRangeEnd) doc.getChild(NodeType.COMMENT_RANGE_END, 0, true);
ArrayList<Node> extractedNodesInclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesInclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.IncludingComment.docx");
ArrayList<Node> extractedNodesExclusive = ExtractContentHelper.extractContent(commentStart, commentEnd, false);
dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodesExclusive);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenCommentRange.WithoutComment.docx");
```

## Estrazione del contenuto tra i paragrafi

```java
// Esempio di codice Java per l'estrazione del contenuto tra i paragrafi
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Estrazione del contenuto tra stili di paragrafo

```java
// Esempio di codice Java per l'estrazione di contenuto tra stili di paragrafo
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Estrazione del contenuto tra le esecuzioni

```java
// Esempio di codice Java per l'estrazione di contenuto tra le esecuzioni
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Estrazione di contenuto tramite DocumentVisitor

```java
// Esempio di codice Java per l'estrazione di contenuti tramite DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Estrazione del contenuto tramite campo

```java
// Esempio di codice Java per l'estrazione di contenuto tramite Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Estrazione del sommario

```java
// Esempio di codice Java per l'estrazione del sommario
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
for (Field field : doc.getRange().getFields()) {
    if (field.getType() == FieldType.FIELD_HYPERLINK) {
        FieldHyperlink hyperlink = (FieldHyperlink) field;
        if (hyperlink.getSubAddress() != null && hyperlink.getSubAddress().startsWith("_Toc")) {
            Paragraph tocItem = (Paragraph) field.getStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(tocItem.toString().trim());
            System.out.println("------------------");
            Bookmark bm = doc.getRange().getBookmarks().get(hyperlink.getSubAddress());
            Paragraph pointer = (Paragraph) bm.getBookmarkStart().getAncestor(NodeType.PARAGRAPH);
            System.out.println(pointer.toString());
        }
    }
}
```

## Estrazione solo testo

```java
// Esempio di codice Java per l'estrazione del solo testo
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Estrazione di contenuti in base agli stili

```java
// Esempio di codice Java per l'estrazione di contenuti in base agli stili
Document doc = new Document("Your Directory Path" + "Styles.docx");
final String PARA_STYLE = "Heading 1";
final String RUN_STYLE = "Intense Emphasis";
ArrayList<Paragraph> paragraphs = paragraphsByStyleName(doc, PARA_STYLE);
System.out.println("Paragraphs with \"{paraStyle}\" styles ({paragraphs.Count}):");
for (Paragraph paragraph : paragraphs)
    System.out.println(paragraph.toString(SaveFormat.TEXT));
ArrayList<Run> runs = runsByStyleName(doc, RUN_STYLE);
System.out.println("\nRuns with \"{runStyle}\" styles ({runs.Count}):");
for (Run run : runs)
    System.out.println(run.getRange().getText());
}

public ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}

public ArrayList<Run> runsByStyleName(Document doc, String styleName) {
    ArrayList<Run> runsWithStyle = new ArrayList<Run>();
    NodeCollection runs = doc.getChildNodes(NodeType.RUN, true);
    for (Run run : (Iterable<Run>) runs) {
        if (run.getFont().getStyle().getName().equals(styleName))
            runsWithStyle.add(run);
    }
    return runsWithStyle;
}
```

## Estrazione e stampa del testo

```java
// Esempio di codice Java per l'estrazione e la stampa del testo
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Estrazione delle immagini nei file

```java
// Esempio di codice Java per l'estrazione di immagini in file
Document doc = new Document("Your Directory Path" + "Images.docx");
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
int imageIndex = 0;
for (Shape shape : (Iterable<Shape>) shapes) {
    if (shape.hasImage()) {
        String imageFileName = MessageFormat.format("Image.ExportImages.{0}_{1}",
                imageIndex, FileFormatUtil.imageTypeToExtension(shape.getImageData().getImageType()));
        shape.getImageData().save("Your Directory Path" + imageFileName);
        imageIndex++;
    }
}
```

## Conclusione

Congratulazioni! Hai imparato come estrarre contenuti dai documenti usando Aspose.Words per Java. Questa guida ha trattato varie tecniche di estrazione, tra cui contenuti tra nodi a livello di blocco, segnalibri, intervalli di commenti, paragrafi e altro. Ora sei equipaggiato per gestire in modo efficiente l'estrazione di contenuti di documenti nelle tue applicazioni Java.

## Domande frequenti

### Come posso estrarre il contenuto da sezioni specifiche del documento?

Per estrarre il contenuto da sezioni specifiche del documento, è possibile identificare i punti di inizio e fine delle sezioni e utilizzare i metodi Aspose.Words per Java appropriati per estrarre il contenuto tra di essi.

### Posso estrarre contenuti da documenti protetti da password?

Sì, Aspose.Words per Java fornisce funzionalità per estrarre contenuti da documenti protetti da password. Puoi fornire la password quando apri il documento usando`Document` costruttore di classe.

### Come posso estrarre il contenuto e salvarlo in formati diversi, ad esempio testo normale o HTML?

 Puoi estrarre il contenuto da un documento e salvarlo in diversi formati usando Aspose.Words per Java. Dopo aver estratto il contenuto, puoi usare`Document` metodi di classe per salvarlo in formati come testo normale, HTML o altri.

### Esiste un modo per estrarre contenuti da elementi specifici di un documento, come tabelle o immagini?

Sì, puoi estrarre il contenuto da elementi specifici del documento, come tabelle o immagini, utilizzando Aspose.Words per Java. Identifica gli elementi che vuoi estrarre, quindi utilizza i metodi appropriati per estrarne il contenuto.

### Come posso automatizzare il processo di estrazione dei contenuti nella mia applicazione Java?

Per automatizzare il processo di estrazione dei contenuti nella tua applicazione Java, puoi creare codice personalizzato basato sulle tecniche descritte in questa guida. Puoi anche implementare la logica per scorrere più documenti ed estrarre i contenuti in base alle necessità.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
