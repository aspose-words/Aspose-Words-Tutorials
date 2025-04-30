---
"description": "Δημιουργία εγγράφων Master με Aspose.Words για Java. Ένας οδηγός βήμα προς βήμα για την προσθήκη κειμένου, πινάκων, εικόνων και άλλων. Δημιουργήστε εκπληκτικά έγγραφα Word χωρίς κόπο."
"linktitle": "Προσθήκη περιεχομένου χρησιμοποιώντας το DocumentBuilder"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Προσθήκη περιεχομένου χρησιμοποιώντας το DocumentBuilder στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη περιεχομένου χρησιμοποιώντας το DocumentBuilder στο Aspose.Words για Java


## Εισαγωγή στην Προσθήκη Περιεχομένου χρησιμοποιώντας το DocumentBuilder στο Aspose.Words για Java

Σε αυτόν τον οδηγό βήμα προς βήμα, θα εξερευνήσουμε πώς να χρησιμοποιήσετε το Aspose.Words για το DocumentBuilder της Java για να προσθέσετε διάφορους τύπους περιεχομένου σε ένα έγγραφο του Word. Θα καλύψουμε την εισαγωγή κειμένου, πινάκων, οριζόντιων κανόνων, πεδίων φόρμας, HTML, υπερσυνδέσμων, πίνακα περιεχομένων, ενσωματωμένων και αιωρούμενων εικόνων, παραγράφων και άλλων. Ας ξεκινήσουμε!

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε ρυθμίσει τη βιβλιοθήκη Aspose.Words για Java στο έργο σας. Μπορείτε να την κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).

## Προσθήκη κειμένου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή μιας απλής παραγράφου κειμένου
builder.write("This is a simple text paragraph.");

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη πινάκων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ξεκινήστε έναν πίνακα
Table table = builder.startTable();

// Εισαγωγή κελιών και περιεχομένου
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Τερματίστε το τραπέζι
builder.endTable();

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη οριζόντιου κανόνα

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή οριζόντιου κανόνα
builder.insertHorizontalRule();

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη πεδίων φόρμας

### Πεδίο φόρμας εισαγωγής κειμένου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή πεδίου φόρμας εισαγωγής κειμένου
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

### Πεδίο φόρμας πλαισίου ελέγχου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή πεδίου φόρμας πλαισίου ελέγχου
builder.insertCheckBox("CheckBox", true, true, 0);

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

### Πεδίο φόρμας συνδυαστικού πλαισίου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ορισμός στοιχείων για το σύνθετο πλαίσιο
String[] items = { "Option 1", "Option 2", "Option 3" };

// Εισαγωγή πεδίου φόρμας συνδυαστικού πλαισίου
builder.insertComboBox("DropDown", items, 0);

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή περιεχομένου HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη υπερσυνδέσμων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή υπερσυνδέσμου
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", ψευδές);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη πίνακα περιεχομένων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή πίνακα περιεχομένων
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Προσθήκη περιεχομένου εγγράφου
// ...

// Ενημέρωση του πίνακα περιεχομένων
doc.updateFields();

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη εικόνων

### Ενσωματωμένη εικόνα

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή ενσωματωμένης εικόνας
builder.insertImage("path/to/your/image.png");

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

### Πλωτή εικόνα

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή αιωρούμενης εικόνας
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Προσθήκη παραγράφων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ορισμός μορφοποίησης παραγράφου
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Εισαγωγή παραγράφου
builder.writeln("This is a formatted paragraph.");

// Αποθήκευση του εγγράφου
doc.save("path/to/your/document.docx");
```

## Βήμα 10: Μετακίνηση του δρομέα

Μπορείτε να ελέγξετε τη θέση του κέρσορα μέσα στο έγγραφο χρησιμοποιώντας διάφορες μεθόδους, όπως `moveToParagraph`, `moveToCell`και πολλά άλλα. Ακολουθεί ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Μετακίνηση του κέρσορα σε μια συγκεκριμένη παράγραφο
builder.moveToParagraph(2, 0);

// Προσθήκη περιεχομένου στη νέα θέση του κέρσορα
builder.writeln("This is the 3rd paragraph.");
```

Αυτές είναι μερικές συνήθεις λειτουργίες που μπορείτε να εκτελέσετε χρησιμοποιώντας το Aspose.Words για το DocumentBuilder της Java. Εξερευνήστε την τεκμηρίωση της βιβλιοθήκης για πιο προηγμένες λειτουργίες και επιλογές προσαρμογής. Καλή δημιουργία εγγράφων!


## Σύναψη

Σε αυτόν τον ολοκληρωμένο οδηγό, εξερευνήσαμε τις δυνατότητες του Aspose.Words για το DocumentBuilder της Java για την προσθήκη διαφόρων τύπων περιεχομένου σε έγγραφα του Word. Καλύψαμε κείμενο, πίνακες, οριζόντιους κανόνες, πεδία φόρμας, HTML, υπερσυνδέσμους, πίνακα περιεχομένων, εικόνες, παραγράφους και κίνηση του κέρσορα.

## Συχνές ερωτήσεις

### Ε: Τι είναι το Aspose.Words για Java;

Α: Το Aspose.Words για Java είναι μια βιβλιοθήκη Java που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν και να χειρίζονται έγγραφα του Microsoft Word μέσω προγραμματισμού. Παρέχει ένα ευρύ φάσμα λειτουργιών για τη δημιουργία εγγράφων, τη μορφοποίηση και την εισαγωγή περιεχομένου.

### Ε: Πώς μπορώ να προσθέσω έναν πίνακα περιεχομένων στο έγγραφό μου;

Α: Για να προσθέσετε έναν πίνακα περιεχομένων, χρησιμοποιήστε το `DocumentBuilder` για να εισαγάγετε ένα πεδίο πίνακα περιεχομένων στο έγγραφό σας. Βεβαιωθείτε ότι έχετε ενημερώσει τα πεδία στο έγγραφο μετά την προσθήκη περιεχομένου για να συμπληρώσετε τον πίνακα περιεχομένων. Ακολουθεί ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή πεδίου πίνακα περιεχομένων
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Προσθήκη περιεχομένου εγγράφου
// ...

// Ενημέρωση του πίνακα περιεχομένων
doc.updateFields();
```

### Ε: Πώς μπορώ να εισάγω εικόνες σε ένα έγγραφο χρησιμοποιώντας το Aspose.Words για Java;

Α: Μπορείτε να εισαγάγετε εικόνες, τόσο ενσωματωμένες όσο και αιωρούμενες, χρησιμοποιώντας το `DocumentBuilder`Ακολουθούν παραδείγματα και των δύο:

#### Ενσωματωμένη εικόνα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή ενσωματωμένης εικόνας
builder.insertImage("path/to/your/image.png");
```

#### Πλωτή εικόνα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή αιωρούμενης εικόνας
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Ε: Μπορώ να μορφοποιήσω κείμενο και παραγράφους κατά την προσθήκη περιεχομένου;

Α: Ναι, μπορείτε να μορφοποιήσετε κείμενο και παραγράφους χρησιμοποιώντας το `DocumentBuilder`Μπορείτε να ορίσετε ιδιότητες γραμματοσειράς, στοίχιση παραγράφων, εσοχή και πολλά άλλα. Ακολουθεί ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ορισμός γραμματοσειράς και μορφοποίησης παραγράφου
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Εισαγωγή μορφοποιημένης παραγράφου
builder.writeln("This is a formatted paragraph.");
```

### Ε: Πώς μπορώ να μετακινήσω τον κέρσορα σε μια συγκεκριμένη θέση μέσα στο έγγραφο;

Α: Μπορείτε να ελέγξετε τη θέση του δρομέα χρησιμοποιώντας μεθόδους όπως `moveToParagraph`, `moveToCell`και πολλά άλλα. Ακολουθεί ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Μετακίνηση του κέρσορα σε μια συγκεκριμένη παράγραφο
builder.moveToParagraph(2, 0);

// Προσθήκη περιεχομένου στη νέα θέση του κέρσορα
builder.writeln("This is the 3rd paragraph.");
```

Αυτές είναι μερικές συνήθεις ερωτήσεις και απαντήσεις που θα σας βοηθήσουν να ξεκινήσετε με το Aspose.Words για το DocumentBuilder της Java. Εάν έχετε περισσότερες ερωτήσεις ή χρειάζεστε περαιτέρω βοήθεια, ανατρέξτε στο [τεκμηρίωση της βιβλιοθήκης](https://reference.aspose.com/words/java/) ή ζητήστε βοήθεια από την κοινότητα Aspose.Words και τους πόρους υποστήριξης.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}