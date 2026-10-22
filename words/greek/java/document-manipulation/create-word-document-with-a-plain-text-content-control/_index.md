---
category: general
date: 2026-10-04
description: Δημιουργήστε έγγραφο Word χρησιμοποιώντας Java που περιλαμβάνει έναν
  έλεγχο περιεχομένου απλού κειμένου και ένα σύμβολο κράτησης θέσης. Μάθετε πώς να
  προσθέσετε σύμβολο κράτησης θέσης στην ετικέτα και πώς να εισάγετε sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: el
lastmod: 2026-10-04
og_description: Δημιουργήστε έγγραφο Word με έναν έλεγχο περιεχομένου απλού κειμένου
  και ένα σύμβολο κράτησης θέσης. Αυτό το σεμινάριο δείχνει πώς να προσθέσετε σύμβολο
  κράτησης θέσης σε ετικέτα και πώς να εισάγετε sdt χρησιμοποιώντας το Aspose.Words
  για Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Δημιουργήστε έγγραφο Word με έλεγχο περιεχομένου – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Δημιουργία εγγράφου Word με έλεγχο περιεχομένου απλού κειμένου
url: /el/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word με έλεγχο περιεχομένου απλού κειμένου

Αν χρειάζεστε **δημιουργήσετε έγγραφο Word** που περιέχει μια περιοχή επεξεργάσιμη από τον χρήστη, ένας έλεγχος περιεχομένου απλού κειμένου είναι η πιο αξιόπιστη προσέγγιση. Αυτό το tutorial δείχνει ακριβώς πώς να εισάγετε ένα Structured Document Tag (SDT), να ορίσετε ένα placeholder και να αποθηκεύσετε το αποτέλεσμα ως **docx με placeholder**. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα Java που λειτουργεί με Aspose.Words for Java 23.8.

Ο οδηγός καλύπτει όλες τις προαπαιτήσεις, εξηγεί γιατί κάθε κλήση API είναι σημαντική και παρέχει συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως πολύγλωσσα placeholders ή ενσωματωμένες ετικέτες. Στο τέλος, μπορείτε να δημιουργήσετε ένα αρχείο Word που ζητά από τους χρήστες να «Enter text…» απευθείας μέσα στο έγγραφο.

## Προαπαιτήσεις

* Java 17 (ή νεότερη) εγκατεστημένη και ρυθμισμένη στο PATH σας.  
* Maven 3.8+ για διαχείριση εξαρτήσεων.  
* Άδεια Aspose.Words for Java (η δοκιμαστική έκδοση λειτουργεί για δοκιμές).  
* Ένα IDE ανάπτυξης (IntelliJ IDEA, Eclipse ή VS Code).

Προσθέστε το Aspose.Words στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Δημιουργία εγγράφου Word με έλεγχο περιεχομένου απλού κειμένου

Η κύρια ροή εργασίας αποτελείται από τέσσερα λογικά βήματα. Κάθε βήμα είναι ενσωματωμένο σε μια με σαφή όνομα μέθοδο, ώστε να μπορείτε να επαναχρησιμοποιήσετε τη λογική σε μεγαλύτερα έργα.

### Βήμα 1: Αρχικοποίηση του εγγράφου και του builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Γιατί είναι σημαντικό:** `Document` αντιπροσωπεύει το αρχείο Word στη μνήμη. `DocumentBuilder` είναι το fluent API που σας επιτρέπει να εισάγετε παραγράφους, πίνακες και SDTs. Ξεκινώντας με ένα κενό έγγραφο εξασφαλίζει ότι το placeholder εμφανίζεται στην αρχή, κάτι που είναι χρήσιμο για πρότυπα.

### Βήμα 2: Εισαγωγή Structured Document Tag (SDT) απλού κειμένου

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Γιατί είναι σημαντικό:** `StructuredDocumentTagType.PLAIN_TEXT` δημιουργεί έναν έλεγχο περιεχομένου που αποδέχεται μόνο απλούς χαρακτήρες, αποτρέποντας τυχαία μορφοποίηση. Η κλήση `setPlaceholderName` γεμίζει το γκρι κείμενο υπόδειξης που βλέπουν οι χρήστες πριν πληκτρολογήσουν — αυτή είναι η λειτουργία **add placeholder to tag** που κάνει το έγγραφο να μοιάζει με φόρμα.

### Βήμα 3: Προσθήκη κανονικού περιεχομένου μετά το SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Γιατί είναι σημαντικό:** Η προσθήκη περιεχομένου μετά τον έλεγχο επαληθεύει ότι το SDT δεν καταναλώνει όλη τη ροή του εγγράφου. Επίσης δείχνει πώς να συνδυάσετε δομημένες ετικέτες με συνηθισμένες παραγράφους, μια κοινή απαίτηση κατά τη δημιουργία προτύπων.

### Βήμα 4: Αποθήκευση του παραγόμενου αρχείου

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Γιατί είναι σημαντικό:** Η μέθοδος `save` γράφει το μοντέλο στη μνήμη σε ένα φυσικό αρχείο **docx with placeholder**. Το παραγόμενο αρχείο μπορεί να ανοιχτεί στο Microsoft Word, LibreOffice ή σε οποιαδήποτε βιβλιοθήκη που υποστηρίζει τη μορφή OpenXML.

## Πλήρης κώδικας πηγής

Συνδυάζοντας τα κομμάτια παίρνετε ένα αυτόνομο πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος δημιουργεί το `SdtDemo.docx`. Το άνοιγμα του αρχείου στο Word εμφανίζει:

* Ένα γκρι placeholder «Enter text…» μέσα σε έλεγχο περιεχομένου απλού κειμένου με ετικέτα **MyTag**.  
* Η γραμμή **After SDT** αμέσως κάτω από τον έλεγχο.

Το placeholder εξαφανίζεται μόλις ο χρήστης πληκτρολογήσει, διατηρώντας την αρχική μορφοποίηση.

## Κοινές παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Συνιστώμενη αλλαγή |
|----------|--------------------|
| **Multilingual placeholder** | Χρησιμοποιήστε χαρακτήρες Unicode στη `setPlaceholderName`, π.χ., `sdt.setPlaceholderName("Введите текст…");`. |
| **Nested content controls** | Εισάγετε ένα δεύτερο SDT μέσα στο πρώτο καλώντας `builder.moveTo(sdt.getParagraph());` πριν από το δεύτερο `insertStructuredDocumentTag`. |
| **Read‑only control** | Καλέστε `sdt.setLockContentControl(true);` για να αποτρέψετε τους χρήστες από τη διαγραφή της ετικέτας. |
| **Rich‑text instead of plain text** | Αντικαταστήστε το `StructuredDocumentTagType.PLAIN_TEXT` με `StructuredDocumentTagType.RICH_TEXT`. |
| **Saving to a stream** | Χρησιμοποιήστε `doc.save(OutputStream, SaveFormat.DOCX);` όταν χρειάζεται να στείλετε το αρχείο μέσω HTTP. |

## Συμβουλές επαγγελματιών

* **Reuse tag IDs** – Εάν δημιουργείτε πολλά έγγραφα από το ίδιο πρότυπο, διατηρήστε το όνομα ετικέτας (`"MyTag"`) συνεπές ώστε η επεξεργασία downstream (π.χ., mail‑merge) να το εντοπίζει αξιόπιστα.  
* **Performance** – Για μεγάλα πρότυπα, δημιουργήστε το `DocumentBuilder` μία φορά και επαναχρησιμοποιήστε το· η εισαγωγή πολλών SDT σε βρόχο είναι πιο γρήγορη από το να δημιουργείτε ξανά το builder σε κάθε επανάληψη.  
* **Testing** – Μετά τη δημιουργία του DOCX, επαληθεύστε προγραμματιστικά ότι το placeholder υπάρχει με τη μέθοδο `doc.getRange().getStructuredDocumentTags().getCount()`.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create word document** που περιέχει έναν **plain text content control** με προσαρμοσμένο placeholder, παράγοντας αποτελεσματικά ένα **docx with placeholder** έτοιμο για είσοδο χρήστη. Το παράδειγμα δείχνει ολόκληρο τον κύκλο από την αρχικοποίηση του εγγράφου, **how to insert sdt**, **add placeholder to tag**, την προσθήκη κανονικού περιεχομένου και τέλος την αποθήκευση του αρχείου.

### Επόμενα βήματα

* Εξερευνήστε **how to insert sdt** μέσα σε πίνακες για διατάξεις τύπου φόρμας.  
* Συνδυάστε αυτήν την τεχνική με συγχώνευση **docx with placeholder** για να δημιουργήσετε αυτοματοποιημένους δημιουργούς αναφορών.  
* Πειραματιστείτε με άλλους τύπους ελέγχων (`RICH_TEXT`, `CHECKBOX`) για να δημιουργήσετε πιο πλούσιες φόρμες Word.

Νιώστε ελεύθεροι να προσαρμόσετε τον κώδικα για τη δική σας μηχανή προτύπων και να μοιραστείτε τα αποτελέσματά σας στα σχόλια!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να δημιουργήσετε έγγραφα PDF με Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}