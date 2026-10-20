---
date: 2026-01-01
description: Μάθετε πώς να δημιουργείτε πεδία φόρμας και να προσθέτετε κείμενο, πίνακες,
  εικόνες, υπερσυνδέσμους και άλλα χρησιμοποιώντας το Aspose.Words for Java DocumentBuilder.
  Ένας οδηγός βήμα‑βήμα για προγραμματιστές.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας
  το DocumentBuilder στο Aspose.Words για Java
url: /el/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Περιεχομένου χρησιμοποιώντας το DocumentBuilder στο Aspose.Words for Java

## Εισαγωγή στην Προσθήκη Περιεχομένου χρησιμοποιώντας το DocumentBuilder στο Aspose.Words for Java

Σε αυτόν τον οδηγό βήμα‑βήμα, θα **δημιουργήσετε πεδία φόρμας** και θα προσθέσετε μια ποικιλία περιεχομένου—κείμενο, πίνακες, οριζόντιες γραμμές, HTML, υπερσυνδέσμους, εικόνες και πολλά άλλα—σε ένα έγγραφο Word με το Aspose.Words for Java. Είτε δημιουργείτε μια αναφορά, ένα πρότυπο σύμβασης ή μια διαδραστική φόρμα, η κλάση `DocumentBuilder` σας παρέχει λεπτομερή έλεγχο σε κάθε στοιχείο. Ας ξεκινήσουμε!

## Γρήγορες Απαντήσεις
- **Πώς δημιουργώ πεδία φόρμας;** Χρησιμοποιήστε `insertTextInput`, `insertCheckBox` ή `insertComboBox` σε ένα `DocumentBuilder`.
- **Ποια μέθοδος προσθέτει απλό κείμενο;** Καλέστε `builder.write("Your text")` ή `builder.writeln("Your text")`.
- **Μπορώ να εισάγω οριζόντια γραμμή;** Ναι—`builder.insertHorizontalRule()` προσθέτει μια γραμμή διαχωρισμού.
- **Πώς ενσωματώνω HTML;** Χρησιμοποιήστε `builder.insertHtml("<p>HTML content</p>")`.
- **Πώς προσθέτω ενσωματωμένη εικόνα;** `builder.insertImage("path/to/image.png")` τοποθετεί την εικόνα μέσα στη ροή κειμένου.

## Τι είναι το DocumentBuilder και γιατί να το χρησιμοποιήσετε για τη δημιουργία πεδίων φόρμας;

`DocumentBuilder` είναι το ευέλικτο API του Aspose.Words για τη δημιουργία και επεξεργασία εγγράφων Word προγραμματιστικά. Απομονώνει τη χαμηλού επιπέδου δομή OpenXML, επιτρέποντάς σας να εστιάσετε στο *τι* θέλετε να προσθέσετε—όπως **πεδία φόρμας**—αντί στο *πώς* φαίνεται το XML. Αυτό το καθιστά ιδανικό για τη δημιουργία δυναμικών φορμών, συμβάσεων ή οποιουδήποτε εγγράφου που απαιτεί αλληλεπίδραση χρήστη.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε εγκαταστήσει τη βιβλιοθήκη Aspose.Words for Java στο έργο σας. Μπορείτε να τη κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).

## Προσθήκη Κειμένου (πώς να προσθέσετε κείμενο)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη Πινάκων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη Οριζόντιας Γραμμής (προσθήκη οριζόντιας γραμμής)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη Πεδίων Φόρμας (δημιουργία πεδίων φόρμας)

### Πεδίο Κειμενικής Εισόδου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Πεδίο Πλαισίου Ελέγχου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Πεδίο Συνδυαστικού Πλαισίου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη HTML (εισαγωγή html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη Υπερσυνδέσμων (πώς να προσθέσετε υπερσύνδεσμο)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη Πίνακα Περιεχομένων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη Εικόνων

### Ενσωματωμένη Εικόνα (εισαγωγή ενσωματωμένης εικόνας)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Αιωρούμενη Εικόνα

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Προσθήκη Παραγράφων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
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

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Μετακίνηση του Δείκτη (Βήμα 10)

Μπορείτε να ελέγξετε τη θέση του δείκτη μέσα στο έγγραφο χρησιμοποιώντας μεθόδους όπως `moveToParagraph`, `moveToCell`, κ.λπ.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Αυτές είναι μερικές κοινές λειτουργίες που μπορείτε να εκτελέσετε χρησιμοποιώντας το `DocumentBuilder` του Aspose.Words for Java. Εξερευνήστε την τεκμηρίωση της βιβλιοθήκης για πιο προχωρημένα χαρακτηριστικά και επιλογές προσαρμογής. Καλή δημιουργία εγγράφων!

## Συμπέρασμα

Σε αυτόν τον ολοκληρωμένο οδηγό, δείξαμε πώς να **δημιουργήσετε πεδία φόρμας** και να προσθέσετε διάφορους τύπους περιεχομένου—κείμενο, πίνακες, οριζόντιες γραμμές, HTML, υπερσυνδέσμους, πίνακα περιεχομένων, εικόνες, μορφοποιημένες παραγράφους και πλοήγηση του δείκτη—χρησιμοποιώντας το `DocumentBuilder` του Aspose.Words for Java. Τώρα έχετε μια σταθερή βάση για τη δημιουργία δυναμικών, διαδραστικών εγγράφων Word προγραμματιστικά.

## Συχνές Ερωτήσεις

### Ε: Τι είναι το Aspose.Words for Java;

Α: Το Aspose.Words for Java είναι μια βιβλιοθήκη Java που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν και να διαχειρίζονται έγγραφα Microsoft Word προγραμματιστικά. Παρέχει ένα ευρύ φάσμα λειτουργιών για δημιουργία εγγράφων, μορφοποίηση και εισαγωγή περιεχομένου.

### Ε: Πώς μπορώ να προσθέσω πίνακα περιεχομένων στο έγγραφό μου;

Α: Για να προσθέσετε πίνακα περιεχομένων, χρησιμοποιήστε το `DocumentBuilder` για να εισάγετε ένα πεδίο TOC και, στη συνέχεια, καλέστε `doc.updateFields()` μετά την προσθήκη του περιεχομένου σας.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Ε: Πώς εισάγω εικόνες σε ένα έγγραφο χρησιμοποιώντας το Aspose.Words for Java;

Α: Μπορείτε να εισάγετε εικόνες, τόσο ενσωματωμένες όσο και αιωρούμενες, χρησιμοποιώντας το `DocumentBuilder`.

#### Ενσωματωμένη Εικόνα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Αιωρούμενη Εικόνα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Ε: Μπορώ να μορφοποιήσω κείμενο και παραγράφους κατά την προσθήκη περιεχομένου;

Α: Ναι, μπορείτε να μορφοποιήσετε κείμενο και παραγράφους χρησιμοποιώντας το `DocumentBuilder`. Ορίστε ιδιότητες γραμματοσειράς, στοίχιση παραγράφου, εσοχές και άλλα πριν γράψετε το περιεχόμενο.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
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

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Ε: Πώς μπορώ να μετακινήσω τον δείκτη σε συγκεκριμένη θέση μέσα στο έγγραφο;

Α: Χρησιμοποιήστε μεθόδους όπως `moveToParagraph`, `moveToCell`, κ.λπ., για να τοποθετήσετε τον δείκτη πριν την εισαγωγή νέου περιεχομένου.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Αυτές οι απαντήσεις καλύπτουν τα πιο συνηθισμένα σενάρια κατά τη χρήση του `DocumentBuilder` του Aspose.Words for Java. Για πιο λεπτομερείς πληροφορίες, ανατρέξτε στην [τεκμηρίωση της βιβλιοθήκης](https://reference.aspose.com/words/java/) ή ενταχθείτε στην κοινότητα Aspose.Words για υποστήριξη.

---

**Τελευταία Ενημέρωση:** 2026-01-01  
**Δοκιμασμένο Με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}