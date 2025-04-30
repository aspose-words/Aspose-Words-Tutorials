---
"description": "Μάθετε πώς να ενώνετε και να προσθέτετε έγγραφα χωρίς κόπο χρησιμοποιώντας το Aspose.Words για Java. Διατηρήστε τη μορφοποίηση, διαχειριστείτε κεφαλίδες, υποσέλιδα και πολλά άλλα."
"linktitle": "Σύνδεση και Προσάρτηση Εγγράφων"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Ένωση και προσάρτηση εγγράφων στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ένωση και προσάρτηση εγγράφων στο Aspose.Words για Java


## Εισαγωγή στην ένωση και προσάρτηση εγγράφων στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να ενώνουμε και να προσαρτάμε έγγραφα χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για Java. Θα μάθετε πώς να συγχωνεύετε απρόσκοπτα πολλά έγγραφα διατηρώντας παράλληλα τη μορφοποίηση και τη δομή.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε ρυθμίσει το Aspose.Words για το Java API στο έργο Java σας.

## Επιλογές ένωσης εγγράφων

### Απλή Προσθήκη

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Προσθήκη με επιλογές μορφοποίησης εισαγωγής

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Προσθήκη σε κενό έγγραφο

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Προσθήκη με μετατροπή αριθμού σελίδας

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Μετατροπή NUMPAGES πεδίων
dstDoc.updatePageLayout(); // Ενημέρωση διάταξης σελίδας για σωστή αρίθμηση
```

## Χειρισμός διαφορετικών ρυθμίσεων σελίδας

Κατά την προσθήκη εγγράφων με διαφορετικές ρυθμίσεις σελίδας:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Βεβαιωθείτε ότι οι ρυθμίσεις διαμόρφωσης σελίδας ταιριάζουν με το έγγραφο προορισμού
```

## Ένωση εγγράφων με διαφορετικά στυλ

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Έξυπνη Συμπεριφορά Στυλ

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Εισαγωγή εγγράφων με το DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Διατήρηση αρίθμησης πηγών

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Χειρισμός πλαισίων κειμένου

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Διαχείριση κεφαλίδων και υποσέλιδων

### Σύνδεση κεφαλίδων και υποσέλιδων

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Αποσύνδεση κεφαλίδων και υποσέλιδων

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Σύναψη

Το Aspose.Words για Java παρέχει ευέλικτα και ισχυρά εργαλεία για την ένωση και την προσάρτηση εγγράφων, είτε χρειάζεται να διατηρήσετε τη μορφοποίηση, να χειριστείτε διαφορετικές ρυθμίσεις σελίδας είτε να διαχειριστείτε κεφαλίδες και υποσέλιδα. Πειραματιστείτε με αυτές τις τεχνικές για να καλύψετε τις συγκεκριμένες ανάγκες επεξεργασίας εγγράφων σας.

## Συχνές ερωτήσεις

### Πώς μπορώ να ενώσω έγγραφα με διαφορετικά στυλ απρόσκοπτα;

Για να ενώσετε έγγραφα με διαφορετικά στυλ, χρησιμοποιήστε `ImportFormatMode.USE_DESTINATION_STYLES` κατά την προσθήκη.

### Μπορώ να διατηρήσω την αρίθμηση σελίδων κατά την προσάρτηση εγγράφων;

Ναι, μπορείτε να διατηρήσετε την αρίθμηση σελίδων χρησιμοποιώντας το `convertNumPageFieldsToPageRef` μέθοδος και ενημέρωση της διάταξης σελίδας.

### Τι είναι η Έξυπνη Συμπεριφορά Στυλ;

Η Έξυπνη Συμπεριφορά Στυλ βοηθά στη διατήρηση σταθερών στυλ κατά την προσάρτηση εγγράφων. Χρησιμοποιήστε την με `ImportFormatOptions` για καλύτερα αποτελέσματα.

### Πώς μπορώ να χειριστώ πλαίσια κειμένου κατά την προσθήκη εγγράφων;

Σειρά `importFormatOptions.setIgnoreTextBoxes(false)` για να συμπεριλάβετε πλαίσια κειμένου κατά την προσθήκη.

### Τι γίνεται αν θέλω να συνδέσω/αποσυνδέσω κεφαλίδες και υποσέλιδα μεταξύ εγγράφων;

Μπορείτε να συνδέσετε κεφαλίδες και υποσέλιδα με `linkToPrevious(true)` ή να τα αποσυνδέσετε με `linkToPrevious(false)` όπως απαιτείται.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}