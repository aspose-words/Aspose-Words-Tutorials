---
"description": "Μάθετε πώς να χρησιμοποιείτε τις ετικέτες δομημένων εγγράφων (SDT) στο Aspose.Words για Java με αυτόν τον ολοκληρωμένο οδηγό. Δημιουργήστε, τροποποιήστε και συνδέστε SDT σε προσαρμοσμένα δεδομένα XML."
"linktitle": "Χρήση ετικετών δομημένων εγγράφων (SDT)"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Χρήση ετικετών δομημένων εγγράφων (SDT) στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση ετικετών δομημένων εγγράφων (SDT) στο Aspose.Words για Java


## Εισαγωγή στη χρήση ετικετών δομημένων εγγράφων (SDT) στο Aspose.Words για Java

Οι ετικέτες δομημένων εγγράφων (SDT) είναι μια ισχυρή λειτουργία στο Aspose.Words για Java που σας επιτρέπει να δημιουργείτε και να χειρίζεστε δομημένο περιεχόμενο μέσα στα έγγραφά σας. Σε αυτόν τον ολοκληρωμένο οδηγό, θα σας καθοδηγήσουμε στις διάφορες πτυχές της χρήσης των SDT στο Aspose.Words για Java. Είτε είστε αρχάριος είτε έμπειρος προγραμματιστής, θα βρείτε πολύτιμες πληροφορίες και πρακτικά παραδείγματα σε αυτό το άρθρο.

## Ξεκινώντας

Πριν εμβαθύνουμε στις λεπτομέρειες, ας ρυθμίσουμε το περιβάλλον μας και ας δημιουργήσουμε ένα βασικό SDT. Σε αυτήν την ενότητα, θα καλύψουμε τα ακόλουθα θέματα:

- Δημιουργία νέου εγγράφου
- Προσθήκη ετικέτας δομημένου εγγράφου
- Αποθήκευση του εγγράφου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Δημιουργήστε μια ετικέτα δομημένου εγγράφου τύπου CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Αποθήκευση του εγγράφου
doc.save("WorkingWithSDT.docx");
```

## Έλεγχος της τρέχουσας κατάστασης ενός SDT πλαισίου ελέγχου

Μόλις προσθέσετε ένα πλαίσιο ελέγχου SDT στο έγγραφό σας, ίσως θελήσετε να ελέγξετε την τρέχουσα κατάστασή του μέσω προγραμματισμού. Αυτό μπορεί να είναι χρήσιμο όταν χρειάζεται να επικυρώσετε την εισαγωγή δεδομένων χρήστη ή να εκτελέσετε συγκεκριμένες ενέργειες με βάση την κατάσταση του πλαισίου ελέγχου.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Το πλαίσιο ελέγχου είναι επιλεγμένο
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Τροποποίηση στοιχείων ελέγχου περιεχομένου

Σε αυτήν την ενότητα, θα εξερευνήσουμε τον τρόπο τροποποίησης των στοιχείων ελέγχου περιεχομένου μέσα στο έγγραφό σας. Θα καλύψουμε τρεις τύπους στοιχείων ελέγχου περιεχομένου: Απλό κείμενο, Αναπτυσσόμενη λίστα και Εικόνα.

### Τροποποίηση ελέγχου περιεχομένου απλού κειμένου

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Διαγραφή του υπάρχοντος περιεχομένου
    sdtPlainText.removeAllChildren();

    // Προσθήκη νέου κειμένου
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Τροποποίηση ελέγχου περιεχομένου αναπτυσσόμενης λίστας

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Επιλέξτε το δεύτερο στοιχείο από τη λίστα
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Τροποποίηση ελέγχου περιεχομένου εικόνας

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Αντικαταστήστε την εικόνα με μια νέα
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Δημιουργία στοιχείου ελέγχου περιεχομένου ComboBox

Ένα στοιχείο ελέγχου περιεχομένου ComboBox επιτρέπει στους χρήστες να επιλέγουν από μια προκαθορισμένη λίστα επιλογών. Ας δημιουργήσουμε μία στο έγγραφό μας.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Εργασία με έλεγχο περιεχομένου εμπλουτισμένου κειμένου

Τα στοιχεία ελέγχου εμπλουτισμένου κειμένου είναι ιδανικά για την προσθήκη μορφοποιημένου κειμένου στα έγγραφά σας. Ας δημιουργήσουμε ένα και ας ορίσουμε το περιεχόμενό του.

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## Ορισμός στυλ ελέγχου περιεχομένου

Μπορείτε να εφαρμόσετε στυλ σε στοιχεία ελέγχου περιεχομένου για να βελτιώσετε την οπτική εμφάνιση του εγγράφου σας. Ας δούμε πώς να ορίσετε το στυλ ενός στοιχείου ελέγχου περιεχομένου.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Εφαρμογή προσαρμοσμένου στυλ
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Σύνδεση ενός SDT με προσαρμοσμένα δεδομένα XML

Σε ορισμένα σενάρια, ίσως χρειαστεί να συνδέσετε ένα SDT με προσαρμοσμένα δεδομένα XML για τη δημιουργία δυναμικού περιεχομένου. Ας εξερευνήσουμε πώς να το πετύχετε αυτό.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Δημιουργία πίνακα με επαναλαμβανόμενες ενότητες που αντιστοιχίζονται σε προσαρμοσμένα δεδομένα XML

Οι πίνακες με επαναλαμβανόμενες ενότητες μπορούν να είναι εξαιρετικά χρήσιμοι για την παρουσίαση δομημένων δεδομένων. Ας δημιουργήσουμε έναν τέτοιο πίνακα και ας τον αντιστοιχίσουμε σε προσαρμοσμένα δεδομένα XML.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## Εργασία με ετικέτες δομημένων εγγράφων πολλαπλών ενοτήτων

Οι ετικέτες δομημένων εγγράφων μπορούν να εκτείνονται σε πολλές ενότητες σε ένα έγγραφο. Σε αυτήν την ενότητα, θα εξερευνήσουμε πώς να εργαστείτε με SDT πολλαπλών ενοτήτων.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Σύναψη

Οι ετικέτες δομημένων εγγράφων στο Aspose.Words για Java παρέχουν έναν ευέλικτο τρόπο διαχείρισης και μορφοποίησης περιεχομένου στα έγγραφά σας. Είτε χρειάζεται να δημιουργήσετε πρότυπα, φόρμες είτε δυναμικά έγγραφα, τα SDT προσφέρουν την ευελιξία και τον έλεγχο που χρειάζεστε. Ακολουθώντας τα παραδείγματα και τις οδηγίες που παρέχονται σε αυτό το άρθρο, μπορείτε να αξιοποιήσετε τη δύναμη των SDT για να βελτιώσετε τις εργασίες επεξεργασίας εγγράφων σας.

## Συχνές ερωτήσεις

### Ποιος είναι ο σκοπός των ετικετών δομημένων εγγράφων (SDT);

Οι ετικέτες δομημένων εγγράφων (SDT) εξυπηρετούν τον σκοπό της οργάνωσης και της μορφοποίησης περιεχομένου μέσα σε έγγραφα, διευκολύνοντας τη δημιουργία προτύπων, φορμών και δομημένων εγγράφων.

### Πώς μπορώ να ελέγξω την τρέχουσα κατάσταση ενός Checkbox SDT;

Μπορείτε να ελέγξετε την τρέχουσα κατάσταση ενός SDT με πλαίσιο ελέγχου χρησιμοποιώντας το `setChecked` μέθοδος, όπως παρουσιάζεται στο άρθρο.

### Μπορώ να εφαρμόσω στυλ σε στοιχεία ελέγχου περιεχομένου;

Ναι, μπορείτε να εφαρμόσετε στυλ στα Στοιχεία ελέγχου περιεχομένου για να προσαρμόσετε την εμφάνισή τους στο έγγραφο.

### Είναι δυνατή η σύνδεση ενός SDT με προσαρμοσμένα δεδομένα XML;

Ναι, μπορείτε να συνδέσετε ένα SDT με προσαρμοσμένα δεδομένα XML, επιτρέποντας τη δυναμική δημιουργία περιεχομένου και την αντιστοίχιση δεδομένων.

### Τι είναι οι Επαναλαμβανόμενες Ενότητες στα SDT;

Οι Επαναλαμβανόμενες Ενότητες σε SDT σάς επιτρέπουν να δημιουργείτε πίνακες με δυναμικά δεδομένα, όπου οι γραμμές μπορούν να επαναληφθούν με βάση τα αντιστοιχισμένα δεδομένα XML.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}