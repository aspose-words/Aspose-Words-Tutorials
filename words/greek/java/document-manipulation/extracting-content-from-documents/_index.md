---
title: Εξαγωγή περιεχομένου από έγγραφα στο Aspose.Words για Java
linktitle: Εξαγωγή περιεχομένου από έγγραφα
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να εξάγετε περιεχόμενο από έγγραφα με ευκολία χρησιμοποιώντας το Aspose.Words για Java. Ο οδηγός βήμα προς βήμα και τα δείγματα κώδικα απλοποιούν τη διαδικασία.
weight: 13
url: /el/java/document-manipulation/extracting-content-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή περιεχομένου από έγγραφα στο Aspose.Words για Java


## Εισαγωγή στην εξαγωγή περιεχομένου από έγγραφα στο Aspose.Words για Java

Στον κόσμο της επεξεργασίας εγγράφων, η εξαγωγή περιεχομένου από έγγραφα είναι μια κοινή απαίτηση. Είτε θέλετε να εξαγάγετε κείμενο, πίνακες, εικόνες ή συγκεκριμένα στοιχεία εγγράφου, το Aspose.Words για Java παρέχει ισχυρά εργαλεία για να κάνετε αυτή την εργασία παιχνιδάκι. Σε αυτόν τον περιεκτικό οδηγό, θα σας καθοδηγήσουμε στη διαδικασία εξαγωγής περιεχομένου από έγγραφα χρησιμοποιώντας το Aspose.Words για Java. 

## Προαπαιτούμενα

Πριν ξεκινήσουμε τη διαδικασία εξαγωγής, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

1.  Aspose.Words για Java: Θα πρέπει να έχετε εγκατεστημένο και ρυθμισμένο το Aspose.Words για Java στο περιβάλλον ανάπτυξης Java. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.aspose.com/words/java/).

2. Έγγραφο για εξαγωγή περιεχομένου από: Για αυτόν τον οδηγό, θα χρησιμοποιήσουμε ένα δείγμα εγγράφου με το όνομα "Εξαγωγή περιεχομένου.docx". Βεβαιωθείτε ότι έχετε ένα παρόμοιο έγγραφο έτοιμο για εξαγωγή.

## Εξαγωγή περιεχομένου μεταξύ κόμβων σε επίπεδο μπλοκ

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου μεταξύ κόμβων σε επίπεδο μπλοκ
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

## Εξαγωγή περιεχομένου μεταξύ σελιδοδεικτών

```java
//Δείγμα κώδικα Java για εξαγωγή περιεχομένου μεταξύ σελιδοδεικτών
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

## Εξαγωγή περιεχομένου μεταξύ εύρους σχολίων

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου μεταξύ περιοχών σχολίων
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

## Εξαγωγή περιεχομένου μεταξύ παραγράφων

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου μεταξύ παραγράφων
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Εξαγωγή περιεχομένου μεταξύ στυλ παραγράφων

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου μεταξύ στυλ παραγράφων
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Εξαγωγή περιεχομένου μεταξύ εκτελέσεων

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου μεταξύ των εκτελέσεων
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Εξαγωγή περιεχομένου με χρήση του DocumentVisitor

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου χρησιμοποιώντας DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Εξαγωγή περιεχομένου με χρήση πεδίου

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου χρησιμοποιώντας το Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Εξαγωγή πίνακα περιεχομένων

```java
// Δείγμα κώδικα Java για εξαγωγή πίνακα περιεχομένων
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

## Εξαγωγή μόνο κειμένου

```java
// Δείγμα κώδικα Java μόνο για εξαγωγή κειμένου
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Εξαγωγή περιεχομένου με βάση στυλ

```java
// Δείγμα κώδικα Java για εξαγωγή περιεχομένου βάσει στυλ
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

## Εξαγωγή και εκτύπωση κειμένου

```java
// Δείγμα κώδικα Java για εξαγωγή και εκτύπωση κειμένου
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Εξαγωγή εικόνων σε αρχεία

```java
// Δείγμα κώδικα Java για εξαγωγή εικόνων σε αρχεία
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

## Σύναψη

Συγχαρητήρια! Έχετε μάθει πώς να εξάγετε περιεχόμενο από έγγραφα χρησιμοποιώντας το Aspose.Words για Java. Αυτός ο οδηγός κάλυψε διάφορες τεχνικές εξαγωγής, συμπεριλαμβανομένου περιεχομένου μεταξύ κόμβων σε επίπεδο μπλοκ, σελιδοδεικτών, εύρους σχολίων, παραγράφων και πολλά άλλα. Τώρα είστε εξοπλισμένοι για να χειρίζεστε αποτελεσματικά την εξαγωγή περιεχομένου εγγράφων στις εφαρμογές σας Java.

## Συχνές ερωτήσεις

### Πώς μπορώ να εξαγάγω περιεχόμενο από συγκεκριμένες ενότητες εγγράφων;

Για να εξαγάγετε περιεχόμενο από συγκεκριμένες ενότητες εγγράφων, μπορείτε να προσδιορίσετε τα σημεία έναρξης και τέλους των ενοτήτων και να χρησιμοποιήσετε τις κατάλληλες μεθόδους Aspose.Words για Java για να εξαγάγετε περιεχόμενο μεταξύ τους.

### Μπορώ να εξαγάγω περιεχόμενο από έγγραφα που προστατεύονται με κωδικό πρόσβασης;

Ναι, το Aspose.Words για Java παρέχει λειτουργικότητα για εξαγωγή περιεχομένου από έγγραφα που προστατεύονται με κωδικό πρόσβασης. Μπορείτε να δώσετε τον κωδικό πρόσβασης κατά το άνοιγμα του εγγράφου χρησιμοποιώντας το`Document` κατασκευαστής τάξης.

### Πώς μπορώ να εξαγάγω περιεχόμενο και να το αποθηκεύσω σε διαφορετικές μορφές, όπως απλό κείμενο ή HTML;

 Μπορείτε να εξαγάγετε περιεχόμενο από ένα έγγραφο και να το αποθηκεύσετε σε διαφορετικές μορφές χρησιμοποιώντας το Aspose.Words για Java. Μετά την εξαγωγή του περιεχομένου, μπορείτε να χρησιμοποιήσετε το`Document` μεθόδους κλάσης για να το αποθηκεύσετε σε μορφές όπως απλό κείμενο, HTML ή άλλες.

### Υπάρχει τρόπος εξαγωγής περιεχομένου από συγκεκριμένα στοιχεία εγγράφου, όπως πίνακες ή εικόνες;

Ναι, μπορείτε να εξαγάγετε περιεχόμενο από συγκεκριμένα στοιχεία εγγράφου, όπως πίνακες ή εικόνες, χρησιμοποιώντας το Aspose.Words για Java. Προσδιορίστε τα στοιχεία που θέλετε να εξαγάγετε και, στη συνέχεια, χρησιμοποιήστε τις κατάλληλες μεθόδους για να εξαγάγετε το περιεχόμενό τους.

### Πώς μπορώ να αυτοματοποιήσω τη διαδικασία εξαγωγής περιεχομένου στην εφαρμογή Java;

Για να αυτοματοποιήσετε τη διαδικασία εξαγωγής περιεχομένου στην εφαρμογή Java, μπορείτε να δημιουργήσετε προσαρμοσμένο κώδικα με βάση τις τεχνικές που περιγράφονται σε αυτόν τον οδηγό. Μπορείτε επίσης να εφαρμόσετε τη λογική για επανάληψη μέσω πολλών εγγράφων και να εξαγάγετε περιεχόμενο όπως απαιτείται.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
