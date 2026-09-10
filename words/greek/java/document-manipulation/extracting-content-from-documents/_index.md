---
date: 2026-01-01
description: Μάθετε πώς να εξάγετε κείμενο χρησιμοποιώντας το Aspose.Words για Java.
  Αυτός ο οδηγός βήμα‑προς‑βήμα παρουσιάζει πολλαπλές τεχνικές εξαγωγής με έτοιμα
  παραδείγματα κώδικα.
linktitle: Extracting Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Πώς να εξάγετε κείμενο χρησιμοποιώντας το Aspose.Words για Java
url: /el/java/document-manipulation/extracting-content-from-documents/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εξάγετε Κείμενο Χρησιμοποιώντας το Aspose.Words για Java

## Πώς να Εξάγετε Κείμενο Χρησιμοποιώντας το Aspose.Words για Java

Στον κόσμο της επεξεργασίας εγγράφων, η **εξαγωγή κειμένου με το Aspose.Words** αποτελεί συχνή ερώτηση για προγραμματιστές Java. Είτε χρειάζεστε απλό κείμενο, πίνακες, εικόνες ή συγκεκριμένα στοιχεία όπως σελιδοδείκτες ή σχόλια, το Aspose.Words για Java προσφέρει ένα πλούσιο API που κάνει τη δουλειά απλή. Σε αυτόν τον οδηγό θα περάσουμε από δεκάδες σενάρια εξαγωγής, θα εξηγήσουμε γιατί κάθε προσέγγιση είναι σημαντική και θα παρέχουμε έτοιμα παραδείγματα κώδικα που μπορείτε να ενσωματώσετε στο πρόγραμμά σας.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη χρειάζομαι;** Aspose.Words για Java (κατεβάστε από την επίσημη ιστοσελίδα).  
- **Μπορώ να εξάγω μόνο απλό κείμενο;** Ναι – χρησιμοποιήστε `Document.getText()` ή `DocumentBuilder` με πεδία.  
- **Μπορεί να γίνει εξαγωγή μεταξύ σελιδοδεικτών;** Απόλυτα, χρησιμοποιήστε `BookmarkStart`/`BookmarkEnd` με `ExtractContentHelper`.  
- **Χρειάζεται άδεια για παραγωγική χρήση;** Απαιτείται εμπορική άδεια για χρήση εκτός δοκιμής.  
- **Ποιες εκδόσεις Java υποστηρίζονται;** Java 8 και νεότερες είναι πλήρως συμβατές.

## Προαπαιτούμενα

1. **Aspose.Words για Java** – εγκαταστήστε τη βιβλιοθήκη και προσθέστε την στο έργο σας. Μπορείτε να τη κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).  
2. **Ένα δείγμα εγγράφου** – για τα παραδείγματα θα χρησιμοποιήσουμε ένα αρχείο με όνομα `Extract content.docx`. Τοποθετήστε το σε φάκελο που μπορείτε να αναφέρετε από τον κώδικά σας.

## Εξαγωγή Περιεχομένου μεταξύ Κόμβων Επιπέδου Block

```java
// Java code sample for extracting content between block-level nodes
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

## Εξαγωγή Περιεχομένου μεταξύ Σελιδοδεικτών

```java
// Java code sample for extracting content between bookmarks
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

## Εξαγωγή Περιεχομένου μεταξύ Περιοχών Σχολίων

```java
// Java code sample for extracting content between comment ranges
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

## Εξαγωγή Περιεχομένου μεταξύ Παραγράφων

```java
// Java code sample for extracting content between paragraphs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph startPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 6, true);
Paragraph endPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 10, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara, endPara, true);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphs.docx");
```

## Εξαγωγή Περιεχομένου μεταξύ Στυλ Παραγράφων

```java
// Java code sample for extracting content between paragraph styles
Document doc = new Document("Your Directory Path" + "Extract content.docx");
ArrayList<Paragraph> parasStyleHeading1 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 1");
ArrayList<Paragraph> parasStyleHeading3 = ExtractContentHelper.paragraphsByStyleName(doc, "Heading 3");
Node startPara1 = parasStyleHeading1.get(0);
Node endPara1 = parasStyleHeading3.get(0);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startPara1, endPara1, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentBetweenParagraphStyles.docx");
```

## Εξαγωγή Περιεχομένου μεταξύ Run

```java
// Java code sample for extracting content between runs
Document doc = new Document("Your Directory Path" + "Extract content.docx");
Paragraph para = (Paragraph) doc.getChild(NodeType.PARAGRAPH, 7, true);
Run startRun = para.getRuns().get(1);
Run endRun = para.getRuns().get(4);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startRun, endRun, true);
Node node = (Node) extractedNodes.get(0);
System.out.println(node.toString());
```

## Εξαγωγή Περιεχομένου χρησιμοποιώντας DocumentVisitor

```java
// Java code sample for extracting content using DocumentVisitor
Document doc = new Document("Your Directory Path" + "Absolute position tab.docx");
MyDocToTxtWriter myConverter = new MyDocToTxtWriter();
doc.accept(myConverter);
System.out.println(myConverter.getText());
```

## Εξαγωγή Περιεχομένου χρησιμοποιώντας Field

```java
// Java code sample for extracting content using Field
Document doc = new Document("Your Directory Path" + "Extract content.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
builder.moveToMergeField("Fullname", false, false);
FieldStart startField = (FieldStart) builder.getCurrentNode();
Paragraph endPara = (Paragraph) doc.getFirstSection().getChild(NodeType.PARAGRAPH, 5, true);
ArrayList<Node> extractedNodes = ExtractContentHelper.extractContent(startField, endPara, false);
Document dstDoc = ExtractContentHelper.generateDocument(doc, extractedNodes);
dstDoc.save("Your Directory Path" + "ExtractContent.ExtractContentUsingField.docx");
```

## Εξαγωγή Πίνακα Περιεχομένων

```java
// Java code sample for extracting table of contents
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

## Εξαγωγή Μόνο Κειμένου

```java
// Java code sample for extracting text only
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertField("MERGEFIELD Field");
System.out.println("GetText() Result: " + doc.getText());
System.out.println("ToString() Result: " + doc.toString());
```

## Εξαγωγή Περιεχομένου βάσει Στυλ

```java
// Java code sample for extracting content based on styles
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

## Εξαγωγή και Εκτύπωση Κειμένου

```java
// Java code sample for extracting and printing text
Document doc = new Document("Your Directory Path" + "Tables.docx");
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);
System.out.println("Contents of the table: ");
System.out.println(table.getRange().getText());
System.out.println("\nContents of the row: ");
System.out.println(table.getRows().get(1).getRange().getText());
System.out.println("\nContents of the cell: ");
System.out.println(table.getLastRow().getLastCell().getRange().getText());
```

## Εξαγωγή Εικόνων σε Αρχεία

```java
// Java code sample for extracting images to files
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

## Συμπέρασμα

Συγχαρητήρια! Διαθέτετε πλέον ένα ολοκληρωμένο σύνολο εργαλείων για **την εξαγωγή κειμένου με το Aspose.Words** σε Java. Από κόμβους επιπέδου block μέχρι σελιδοδείκτες, σχόλια, στυλ και ακόμη εικόνες, το API σας δίνει λεπτομερή έλεγχο πάνω σε ό,τι εξάγετε από ένα έγγραφο. Χρησιμοποιήστε αυτά τα αποσπάσματα ως βάση, προσαρμόστε τα στις δικές σας δομές αρχείων και αυτοματοποιήστε τη διαδικασία εξαγωγής σε μεγάλα σύνολα εγγράφων.

## Συχνές Ερωτήσεις

**Ε: Πώς εξάγω περιεχόμενο από έγγραφο προστατευμένο με κωδικό;**  
Α: Φορτώστε το έγγραφο με τον κατασκευαστή κωδικού: `new Document(path, new LoadOptions("password"))`, στη συνέχεια εκτελέστε οποιαδήποτε από τις μεθόδους εξαγωγής που παρουσιάστηκαν παραπάνω.

**Ε: Μπορώ να εξάγω περιεχόμενο από πολλαπλά έγγραφα σε μία εκτέλεση;**  
Α: Ναι. Διατρέξτε μια λίστα διαδρομών αρχείων, δημιουργήστε ένα `Document` για το καθένα και εφαρμόστε την ίδια λογική εξαγωγής μέσα στον βρόχο.

**Ε: Υπάρχει τρόπος να εξάγω μόνο το ορατό κείμενο (αγνοώντας κρυφά ή κώδικες πεδίων);**  
Α: Χρησιμοποιήστε `doc.getText()` για απλό ορατό κείμενο. Για μεγαλύτερο έλεγχο, επαναλάβετε τους κόμβους και φιλτράρετε κατά `NodeType.RUN` και `Run.getFont().getHidden()`.

**Ε: Σε ποιες μορφές μπορώ να αποθηκεύσω το εξαγόμενο περιεχόμενο;**  
Α: Μετά την εξαγωγή, μπορείτε να αποθηκεύσετε ένα `Document` ως DOCX, PDF, HTML, TXT ή οποιαδήποτε μορφή υποστηρίζεται από το Aspose.Words μέσω `doc.save("output.pdf")`.

**Ε: Υποστηρίζει το Aspose.Words την εξαγωγή περιεχομένου από μεγάλα (εκατοντάδες MB) αρχεία;**  
Α: Ναι, αλλά σκεφτείτε τη χρήση `LoadOptions` με `LoadFormat` και `MemoryOptimization` για μείωση της κατανάλωσης μνήμης.

---

**Τελευταία Ενημέρωση:** 2026-01-01  
**Δοκιμασμένο Με:** Aspose.Words για Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}