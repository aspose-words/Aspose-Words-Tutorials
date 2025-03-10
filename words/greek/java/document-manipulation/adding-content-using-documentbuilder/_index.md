---
title: Προσθήκη περιεχομένου χρησιμοποιώντας το DocumentBuilder στο Aspose.Words για Java
linktitle: Προσθήκη περιεχομένου χρησιμοποιώντας το DocumentBuilder
second_title: Aspose.Words Java Document Processing API
description: Δημιουργία Κύριου Εγγράφου με Aspose.Words για Java. Ένας οδηγός βήμα προς βήμα για την προσθήκη κειμένου, πινάκων, εικόνων και άλλων. Δημιουργήστε εκπληκτικά έγγραφα Word χωρίς κόπο.
weight: 26
url: /el/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη περιεχομένου χρησιμοποιώντας το DocumentBuilder στο Aspose.Words για Java


## Εισαγωγή στην προσθήκη περιεχομένου με χρήση του DocumentBuilder στο Aspose.Words για Java

Σε αυτόν τον οδηγό βήμα προς βήμα, θα εξερευνήσουμε πώς να χρησιμοποιήσετε το Aspose.Words για το DocumentBuilder της Java για να προσθέσετε διάφορους τύπους περιεχομένου σε ένα έγγραφο του Word. Θα καλύψουμε την εισαγωγή κειμένου, πινάκων, οριζόντιων κανόνων, πεδίων φόρμας, HTML, υπερσυνδέσμων, πίνακα περιεχομένων, ενσωματωμένων και αιωρούμενων εικόνων, παραγράφων και πολλά άλλα. Ας ξεκινήσουμε!

## Προαπαιτούμενα

 Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε ρυθμίσει τη βιβλιοθήκη Aspose.Words for Java στο έργο σας. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.aspose.com/words/java/).

## Προσθήκη κειμένου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε μια απλή παράγραφο κειμένου
builder.write("This is a simple text paragraph.");

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Προσθήκη πινάκων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Ξεκινήστε ένα τραπέζι
Table table = builder.startTable();

// Εισαγάγετε κελιά και περιεχόμενο
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Τελειώστε το τραπέζι
builder.endTable();

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Προσθήκη οριζόντιου κανόνα

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε έναν οριζόντιο κανόνα
builder.insertHorizontalRule();

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Προσθήκη πεδίων φόρμας

### Πεδίο φόρμας εισαγωγής κειμένου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε ένα πεδίο φόρμας εισαγωγής κειμένου
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

### Πεδίο φόρμας πλαισίου ελέγχου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε ένα πεδίο φόρμας πλαισίου ελέγχου
builder.insertCheckBox("CheckBox", true, true, 0);

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

### Πεδίο φόρμας σύνθετου πλαισίου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ορίστε στοιχεία για το σύνθετο πλαίσιο
String[] items = { "Option 1", "Option 2", "Option 3" };

// Εισαγάγετε ένα πεδίο φόρμας σύνθετου πλαισίου
builder.insertComboBox("DropDown", items, 0);

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Προσθήκη HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε περιεχόμενο HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Προσθήκη υπερσυνδέσμων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε έναν υπερσύνδεσμο
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Προσθήκη πίνακα περιεχομένων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε έναν πίνακα περιεχομένων
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Προσθήκη περιεχομένου εγγράφου
// ...

// Ενημερώστε τον πίνακα περιεχομένων
doc.updateFields();

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Προσθήκη εικόνων

### Ενσωματωμένη εικόνα

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε μια ενσωματωμένη εικόνα
builder.insertImage("path/to/your/image.png");

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

### Πλωτή εικόνα

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε μια αιωρούμενη εικόνα
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Αποθηκεύστε το έγγραφο
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

// Εισαγάγετε μια παράγραφο
builder.writeln("This is a formatted paragraph.");

// Αποθηκεύστε το έγγραφο
doc.save("path/to/your/document.docx");
```

## Βήμα 10: Μετακίνηση του δρομέα

 Μπορείτε να ελέγξετε τη θέση του δρομέα μέσα στο έγγραφο χρησιμοποιώντας διάφορες μεθόδους όπως`moveToParagraph`, `moveToCell`και άλλα. Εδώ είναι ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Μετακινήστε τον κέρσορα σε μια συγκεκριμένη παράγραφο
builder.moveToParagraph(2, 0);

// Προσθέστε περιεχόμενο στη νέα θέση του δρομέα
builder.writeln("This is the 3rd paragraph.");
```

Αυτές είναι μερικές κοινές λειτουργίες που μπορείτε να εκτελέσετε χρησιμοποιώντας το Aspose.Words για το DocumentBuilder της Java. Εξερευνήστε την τεκμηρίωση της βιβλιοθήκης για πιο προηγμένες δυνατότητες και επιλογές προσαρμογής. Καλή δημιουργία εγγράφου!


## Σύναψη

Σε αυτόν τον περιεκτικό οδηγό, έχουμε εξερευνήσει τις δυνατότητες του Aspose.Words για το DocumentBuilder της Java για την προσθήκη διαφόρων τύπων περιεχομένου σε έγγραφα του Word. Καλύψαμε κείμενο, πίνακες, οριζόντιους κανόνες, πεδία φόρμας, HTML, υπερσυνδέσμους, πίνακα περιεχομένων, εικόνες, παραγράφους και κίνηση του δρομέα.

## Συχνές ερωτήσεις

### Ε: Τι είναι το Aspose.Words για Java;

Α: Το Aspose.Words για Java είναι μια βιβλιοθήκη Java που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν και να χειρίζονται έγγραφα του Microsoft Word μέσω προγραμματισμού. Παρέχει ένα ευρύ φάσμα δυνατοτήτων για τη δημιουργία εγγράφων, τη μορφοποίηση και την εισαγωγή περιεχομένου.

### Ε: Πώς μπορώ να προσθέσω έναν πίνακα περιεχομένων στο έγγραφό μου;

Α: Για να προσθέσετε έναν πίνακα περιεχομένων, χρησιμοποιήστε το`DocumentBuilder` για να εισαγάγετε ένα πεδίο πίνακα περιεχομένων στο έγγραφό σας. Βεβαιωθείτε ότι έχετε ενημερώσει τα πεδία στο έγγραφο αφού προσθέσετε περιεχόμενο για να συμπληρώσετε τον πίνακα περιεχομένων. Εδώ είναι ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε ένα πεδίο πίνακα περιεχομένων
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Προσθήκη περιεχομένου εγγράφου
// ...

// Ενημερώστε τον πίνακα περιεχομένων
doc.updateFields();
```

### Ε: Πώς μπορώ να εισάγω εικόνες σε ένα έγγραφο χρησιμοποιώντας το Aspose.Words για Java;

 Α: Μπορείτε να εισαγάγετε εικόνες, τόσο ενσωματωμένες όσο και κινούμενες, χρησιμοποιώντας το`DocumentBuilder`. Ακολουθούν παραδείγματα και των δύο:

#### Ενσωματωμένη εικόνα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε μια ενσωματωμένη εικόνα
builder.insertImage("path/to/your/image.png");
```

#### Κυμαινόμενη εικόνα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε μια αιωρούμενη εικόνα
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Ε: Μπορώ να μορφοποιήσω κείμενο και παραγράφους κατά την προσθήκη περιεχομένου;

 Α: Ναι, μπορείτε να μορφοποιήσετε κείμενο και παραγράφους χρησιμοποιώντας το`DocumentBuilder`. Μπορείτε να ορίσετε ιδιότητες γραμματοσειράς, στοίχιση παραγράφου, εσοχή και πολλά άλλα. Εδώ είναι ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ορισμός μορφοποίησης γραμματοσειράς και παραγράφου
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

// Εισαγάγετε μια μορφοποιημένη παράγραφο
builder.writeln("This is a formatted paragraph.");
```

### Ε: Πώς μπορώ να μετακινήσω τον κέρσορα σε μια συγκεκριμένη θέση μέσα στο έγγραφο;

 Α: Μπορείτε να ελέγξετε τη θέση του δρομέα χρησιμοποιώντας μεθόδους όπως`moveToParagraph`, `moveToCell`και άλλα. Εδώ είναι ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Μετακινήστε τον κέρσορα σε μια συγκεκριμένη παράγραφο
builder.moveToParagraph(2, 0);

// Προσθέστε περιεχόμενο στη νέα θέση του δρομέα
builder.writeln("This is the 3rd paragraph.");
```

Αυτές είναι μερικές συνήθεις ερωτήσεις και απαντήσεις που θα σας βοηθήσουν να ξεκινήσετε με το Aspose.Words για το DocumentBuilder της Java. Εάν έχετε περισσότερες ερωτήσεις ή χρειάζεστε περαιτέρω βοήθεια, ανατρέξτε στο[τεκμηρίωση της βιβλιοθήκης](https://reference.aspose.com/words/java/) ή ζητήστε βοήθεια από την κοινότητα Aspose.Words και πόρους υποστήριξης.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
