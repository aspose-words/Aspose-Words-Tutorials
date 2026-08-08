---
category: general
date: 2026-08-07
description: Δημιουργήστε κενό έγγραφο Word χρησιμοποιώντας το Aspose.Words for Java
  – μάθετε πώς να ορίσετε κείμενο κράτησης θέσης, να προσθέσετε έλεγχο απλού κειμένου
  και να αποθηκεύσετε το έγγραφο ως docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- add placeholder to tag
- add plain text control
language: el
lastmod: 2026-08-07
og_description: Δημιουργήστε κενό έγγραφο Word σε Java με το Aspose.Words. Αυτό το
  σεμινάριο δείχνει πώς να ορίσετε κείμενο κράτησης θέσης, να προσθέσετε έλεγχο απλού
  κειμένου και να αποθηκεύσετε το έγγραφο ως docx για αυτοματοποιημένες ροές εργασίας.
og_image_alt: Screenshot of a blank Word document created with Aspose.Words in Java
og_title: Δημιουργία κενού εγγράφου Word σε Java – Εγχειρίδιο Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank word document using Aspose.Words for Java – learn to set
    placeholder text, add plain text control, and save document as docx.
  headline: Create blank word document in Java with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Structured Document Tag
- Document Generation
title: Δημιουργία κενής εγγράφου Word σε Java με το Aspose.Words
url: /el/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word σε Java με Aspose.Words

Αν χρειάζεστε να **δημιουργήσετε κενό έγγραφο Word** προγραμματιστικά, το Aspose.Words for Java το καθιστά απλό. Αυτός ο οδηγός σας καθοδηγεί στη δημιουργία ενός κενού εγγράφου Word, στην προσθήκη ενός ελέγχου απλού κειμένου, **ορισμός κειμένου placeholder**, και τελικά **αποθήκευση εγγράφου ως docx** για επεξεργασία downstream.

Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που καλύπτει κάθε βήμα από τη ρύθμιση του έργου μέχρι το τελικό αρχείο στο δίσκο. Δεν απαιτούνται εξωτερικές αναφορές, ώστε να μπορείτε να αντιγράψετε τον κώδικα απευθείας στο IDE σας και να τον εκτελέσετε. Στο τέλος αυτού του tutorial θα μπορείτε να **προσθέσετε placeholder σε ετικέτα**, να διαχειριστείτε τον τίτλο του ελέγχου, και να δημιουργήσετε ένα επαγγελματικό αρχείο Word χωρίς χειροκίνητη επεξεργασία.

## Προαπαιτούμενα

- Java Development Kit 8 ή νεότερο εγκατεστημένο.
- Maven ή Gradle για διαχείριση εξαρτήσεων (τα παραδείγματα χρησιμοποιούν Maven).
- IDE όπως IntelliJ IDEA, Eclipse ή VS Code.
- Ένας φάκελος με δυνατότητα εγγραφής στον υπολογιστή σας όπου θα αποθηκευτεί το παραγόμενο **docx** αρχείο.

> **Pro tip:** Αν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση Aspose.Words for Java στο `pom.xml`. Η βιβλιοθήκη είναι πλήρως αδειοδοτημένη, αλλά μια δωρεάν έκδοση αξιολόγησης λειτουργεί για εκπαιδευτικούς σκοπούς.

```xml
<!-- Maven dependency for Aspose.Words -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

## Βήμα 1: Ρύθμιση Aspose.Words για Java

Δημιουργήστε ένα νέο έργο Maven (ή προσθέστε την εξάρτηση σε υπάρχον έργο). Μετά το τέλος της κατασκευής, οι κλάσεις `com.aspose.words.*` γίνονται διαθέσιμες στο classpath.

```bash
mvn archetype:generate -DgroupId=com.example -DartifactId=WordDemo -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
cd WordDemo
# Add the dependency shown above to pom.xml, then:
mvn compile
```

> **Why this matters:** Η αρχικοποίηση της βιβλιοθήκης νωρίς εξασφαλίζει ότι όλες οι επόμενες κλήσεις API—όπως η δημιουργία κενής εγγράφου Word—επιλύονται χωρίς σφάλματα χρόνου εκτέλεσης.

## Βήμα 2: Δημιουργία κενού εγγράφου Word και αρχικοποίηση DocumentBuilder

Η πρώτη λειτουργική γραμμή κώδικα είναι η δημιουργία ενός κενών αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα **κενό έγγραφο Word** στη μνήμη. Στη συνέχεια, συνδέεται ένα `DocumentBuilder` με το έγγραφο για να απλοποιήσει την εισαγωγή περιεχομένου.

```java
import com.aspose.words.*;

public class SDTDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- creates a blank word document
        // Step 2.2: Obtain a DocumentBuilder for editing
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Επεξήγηση:**  
- `new Document()` δημιουργεί ένα **κενό έγγραφο Word** στη μνήμη με προεπιλεγμένες ρυθμίσεις (σελίδα A4, χωρίς ενότητες).  
- `DocumentBuilder` παρέχει ένα fluent API για εισαγωγή κειμένου, πινάκων και ελέγχων περιεχομένου χωρίς χειροκίνητη διαχείριση δομών κόμβων χαμηλού επιπέδου.

## Βήμα 3: Προσθήκη ελέγχου απλού κειμένου (Structured Document Tag)

Ένας **plain‑text control** είναι ένας τύπος Structured Document Tag (SDT) που επιτρέπει στους τελικούς χρήστες να εισάγουν ελεύθερο κείμενο. Η προσθήκη αυτού του ελέγχου αποτελεί τον πυρήνα της λειτουργίας **add plain text control**.

```java
        // Step 3: Insert a plain‑text Structured Document Tag (SDT)
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, false);
```

**Γιατί να χρησιμοποιήσετε ένα plain‑text SDT;**  
- Εμφανίζεται ως ένα γκρι-σκιασμένο πλαίσιο στο Word, υποδεικνύοντας πού πρέπει να πληκτρολογήσει ο χρήστης.  
- Μπορεί να συνδεθεί με XML αργότερα, επιτρέποντας τη δημιουργία εγγράφων βάσει δεδομένων.

## Βήμα 4: Ορισμός κειμένου placeholder για το Structured Document Tag

Το placeholder καθοδηγεί τους χρήστες σχετικά με το τι πρέπει να πληκτρολογήσουν. Εδώ **ορίζουμε κείμενο placeholder** και δίνουμε επίσης στην ετικέτα έναν περιγραφικό τίτλο.

```java
        // Step 4.1: Assign a title – useful for programmatic lookup later
        sdt.setTitle("CustomerName");
        // Step 4.2: Define the placeholder that appears inside the control
        sdt.setPlaceholderName("Enter name here");   // <-- set placeholder text
```

**Τι κάνει το placeholder:**  
Όταν το έγγραφο ανοίξει στο Microsoft Word, το γκρι πλαίσιο εμφανίζει το κείμενο “Enter name here”. Το κείμενο εξαφανίζεται μόλις ο χρήστης αρχίσει να πληκτρολογεί, παρέχοντας μια σαφή υπόδειξη χωρίς να είναι ενσωματωμένη μια στατική τιμή.

## Βήμα 5: Γράψτε το περιβάλλον κείμενο και επιδείξτε τη ροή

Για να επιδείξουμε ότι το SDT ενσωματώνεται άψογα με το κανονικό περιεχόμενο, προσθέτουμε μια απλή πρόταση μετά τον έλεγχο.

```java
        // Step 5: Write regular text after the SDT
        builder.writeln(" – after the SDT");
```

Η έξοδος θα μοιάζει με:

> **[Πλαίσιο απλού κειμένου] – after the SDT**

Αυτό δείχνει ότι η **προσθήκη placeholder σε ετικέτα** δεν επηρεάζει το επόμενο περιεχόμενο του εγγράφου.

## Βήμα 6: Αποθήκευση εγγράφου ως docx

Τέλος, αποθηκεύουμε το έγγραφο στη μνήμη στο δίσκο. Το βήμα **save document as docx** είναι κρίσιμο για downstream κατανάλωση (π.χ., συνημμένο email, περαιτέρω επεξεργασία).

```java
        // Step 6: Save the file – you can change the path to suit your environment
        String outputPath = "YOUR_DIRECTORY/SDTDemo.docx";
        doc.save(outputPath);                       // <-- save document as docx
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Σημαντικές σημειώσεις:**

- Η μέθοδος `save` επιλέγει αυτόματα τη μορφή DOCX επειδή η επέκταση του αρχείου είναι `.docx`.  
- Αν χρειάζεται να μεταφέρετε το αρχείο (π.χ., σε web εφαρμογή), χρησιμοποιήστε `doc.save(OutputStream, SaveFormat.DOCX)` αντί αυτού.  
- Βεβαιωθείτε ότι ο φάκελος προορισμού υπάρχει· διαφορετικά, το `doc.save` θα ρίξει `IOException`.

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `SDTDemo.docx` στο Microsoft Word ή στο LibreOffice Writer. Θα δείτε:

1. Έναν **plain‑text control** με το placeholder “Enter name here”.  
2. Το κείμενο “ – after the SDT” αμέσως μετά τον έλεγχο.  

Το έγγραφο είναι διαφορετικά κενό, επιβεβαιώνοντας ότι έχετε δημιουργήσει επιτυχώς **κενό έγγραφο Word**, **προσθέσει έλεγχο απλού κειμένου**, **ορίσει κείμενο placeholder**, και **αποθηκεύσει το έγγραφο ως docx** σε μια ενιαία ροή εργασίας.

## Προχωρημένες παραλλαγές και περιπτώσεις άκρων

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|----------------------|
| **Multiple SDTs** | Καλέστε `builder.insertStructuredDocumentTag` επανειλημμένα, αναθέτοντας μοναδικούς τίτλους σε κάθε ετικέτα. |
| **Repeatable section** | Χρησιμοποιήστε `StructuredDocumentTagType.REPEAT_SECTION` αντί για `PLAIN_TEXT`. |
| **Binding to XML** | Μετά τη δημιουργία του SDT, καλέστε `sdt.setXmlMapping(xmlPart, "/Root/Customer/Name", true)`. |
| **Saving to a stream** | Αντικαταστήστε `doc.save(outputPath)` με `try (FileOutputStream out = new FileOutputStream("out.docx")) { doc.save(out, SaveFormat.DOCX); }`. |
| **Changing placeholder style** | Ανακτήστε τον υποκείμενο κόμβο `Run` μέσω `sdt.getPlaceholder()` και εφαρμόστε μορφοποίηση `Font`. |

> **Pro tip:** Όταν δημιουργείτε πολλά έγγραφα σε παρτίδα, επαναχρησιμοποιήστε μια μόνο παρουσία `DocumentBuilder` και καλέστε `doc.clone()` για κάθε επανάληψη ώστε να αποφύγετε το κόστος επαναλαμβανόμενης δημιουργίας των εσωτερικών αντικειμένων της βιβλιοθήκης.

## Πλήρης κώδικας πηγής (εκτελέσιμος)

```java
import com.aspose.words.*;

public class SDTDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a plain‑text Structured Document Tag (SDT)
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, false);

        // Step 4: Assign a title and placeholder text to the SDT
        sdt.setTitle("CustomerName");
        sdt.setPlaceholderName("Enter name here");        // set placeholder text

        // Step 5


## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να δημιουργήσετε αρχείο απλού κειμένου με Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-text-files/)
- [Δημιουργία Κενής Εγγράφου Word με Σχήμα Ορθογωνίου με Σκιά – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}