---
category: general
date: 2026-10-07
description: Μάθετε πώς να αποθηκεύετε docx με το DocumentBuilder, να εισάγετε έλεγχο
  απλού κειμένου και να προσθέτετε κείμενο μετά τον έλεγχο σε έναν ενιαίο οδηγό.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx with DocumentBuilder
- add text after control
- insert plain text control
language: el
lastmod: 2026-10-07
og_description: Αποθηκεύστε το docx με το DocumentBuilder, εισάγετε έλεγχο απλού κειμένου
  και προσθέστε κείμενο μετά τον έλεγχο χρησιμοποιώντας το Aspose.Words for Java σε
  αυτόν τον βήμα‑βήμα οδηγό.
og_image_alt: Screenshot showing a DOCX file created with DocumentBuilder after inserting
  a plain text control
og_title: Αποθήκευση docx με το DocumentBuilder – εισαγωγή ελέγχου απλού κειμένου
  και προσθήκη κειμένου μετά τον έλεγχο
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save docx with DocumentBuilder, insert plain text control,
    and add text after control in a single guide.
  headline: How to save docx with DocumentBuilder and add text after a control
  type: TechArticle
- description: Learn how to save docx with DocumentBuilder, insert plain text control,
    and add text after control in a single guide.
  name: How to save docx with DocumentBuilder and add text after a control
  steps:
  - name: Prerequisites
    text: '* Java 17 or newer installed. * Maven 3.6+ for dependency management. *
      Basic familiarity with Java syntax and object‑oriented programming.'
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for constructing Word documents
      programmatically. * `insertStructuredDocumentTag` creates a **plain text control**
      (also called an SDT) that appears as a content control in Word. * Setting `Title`
      and `PlaceholderName` provides metadata and a hint for the end‑u'
  - name: Expected output screenshot (alt text for accessibility)
    text: '*Alt text:* “Word document showing a plain text content control labeled
      CustomerName followed by the line ‘After the tag’.”'
  type: HowTo
tags:
- Aspose.Words
- Java
- DocumentBuilder
title: Πώς να αποθηκεύσετε ένα docx με το DocumentBuilder και να προσθέσετε κείμενο
  μετά από έναν έλεγχο
url: /el/java/document-manipulation/how-to-save-docx-with-documentbuilder-and-add-text-after-a-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε docx με DocumentBuilder και να προσθέσετε κείμενο μετά από έναν έλεγχο

Αν χρειάζεστε **να αποθηκεύσετε docx με DocumentBuilder**, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε. Θα δείτε πώς να **εισάγετε έλεγχο απλού κειμένου**, να ορίσετε τον τίτλο και το placeholder του, και στη συνέχεια **να προσθέσετε κείμενο μετά από τον έλεγχο** ώστε το τελικό έγγραφο να διαβάζεται φυσικά.

Στις παρακάτω ενότητες καλύπτουμε τα πάντα, από τη ρύθμιση του έργου μέχρι τη διαχείριση ειδικών περιπτώσεων, ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε ένα πλήρες, εκτελέσιμο παράδειγμα στο δικό σας έργο Java. Δεν απαιτούνται εξωτερικές αναφορές — μόνο ο κώδικας και οι εξηγήσεις που παρέχονται εδώ.

## Τι θα μάθετε

* Πώς να ρυθμίσετε το Aspose.Words for Java σε ένα έργο Maven.  
* Πώς να **εισάγετε έλεγχο απλού κειμένου** (μια Structured Document Tag) χρησιμοποιώντας το `DocumentBuilder`.  
* Πώς να **προσθέσετε κείμενο μετά από τον έλεγχο** ώστε το περιβάλλον περιεχόμενο να ρέει σωστά.  
* Πώς να **αποθηκεύσετε docx με DocumentBuilder** σε έναν επιλεγμένο φάκελο.  
* Συμβουλές για την προσαρμογή της εμφάνισης του ελέγχου, τη διαχείριση κενών placeholders και την επαναχρησιμοποίηση του builder για πολλαπλές ετικέτες.

### Προαπαιτούμενα

* Java 17 ή νεότερη εγκατεστημένη.  
* Maven 3.6+ για διαχείριση εξαρτήσεων.  
* Βασική εξοικείωση με τη σύνταξη της Java και τον αντικειμενοστραφή προγραμματισμό.

---

## Βήμα 1: Ρύθμιση του έργου Maven και προσθήκη του Aspose.Words

Πρώτα, δημιουργήστε ένα νέο έργο Maven (ή προσθέστε σε υπάρχον). Συμπεριλάβετε την εξάρτηση Aspose.Words for Java στο `pom.xml` σας:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version at the time of writing -->
    </dependency>
</dependencies>
```

> **Συμβουλή:** Το Aspose.Words είναι εμπορική βιβλιοθήκη, αλλά μια δωρεάν άδεια αξιολόγησης λειτουργεί για ανάπτυξη. Εγγραφείτε στην ιστοσελίδα του Aspose για να αποκτήσετε ένα αρχείο άδειας και φορτώστε το κατά την εκτέλεση για να αποφύγετε τα υδατογράμματα.

## Βήμα 2: Δημιουργία της κλάσης Java και εισαγωγή των απαιτούμενων τύπων

Δημιουργήστε μια κλάση με όνομα `DocxBuilderDemo`. Εισάγετε τις κλάσεις που χρειάζονται για εργασία με `DocumentBuilder`, `StructuredDocumentTag` και το enum εμφάνισης.

```java
package com.example.docx;

import com.aspose.words.*;

public class DocxBuilderDemo {

    public static void main(String[] args) throws Exception {
        // Initialize the license if you have one (optional)
        // License license = new License();
        // license.setLicense("Aspose.Words.Java.lic");

        // Step 3: Build the document and insert the plain text control
        buildDocument();
    }

    private static void buildDocument() throws Exception {
        // Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text Structured Document Tag (SDT) with default appearance
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);

        // Set the tag's title and placeholder text to guide the user
        sdt.setTitle("CustomerName");
        sdt.setPlaceholderName("Enter name");

        // Step 4: Add regular content after the SDT
        builder.writeln("After the tag");

        // Step 5: Save the resulting document – this is where we **save docx with DocumentBuilder**
        String outputPath = "output/SDT.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Γιατί λειτουργεί αυτό

* `DocumentBuilder` είναι το κύριο API για την προγραμματική δημιουργία εγγράφων Word.  
* `insertStructuredDocumentTag` δημιουργεί έναν **έλεγχο απλού κειμένου** (επίσης γνωστό ως SDT) που εμφανίζεται ως έλεγχος περιεχομένου στο Word.  
* Ο ορισμός του `Title` και του `PlaceholderName` παρέχει μεταδεδομένα και υπόδειξη για τον τελικό χρήστη.  
* `writeln` προσθέτει μια νέα παράγραφο **μετά τον έλεγχο**, ικανοποιώντας την απαίτηση **προσθήκη κειμένου μετά από τον έλεγχο**.  
* Τέλος, το `doc.save` **αποθηκεύει docx με DocumentBuilder** στο σύστημα αρχείων.

## Βήμα 3: Εκτέλεση του παραδείγματος και επαλήθευση του αποτελέσματος

1. Συγκεντρώστε το έργο με `mvn clean compile`.  
2. Εκτελέστε την κλάση `DocxBuilderDemo` (`mvn exec:java -Dexec.mainClass="com.example.docx.DocxBuilderDemo"`).  
3. Ανοίξτε το `output/SDT.docx` στο Microsoft Word ή στο LibreOffice.

Θα πρέπει να δείτε ένα έγγραφο που περιέχει:

* Έναν έλεγχο περιεχομένου με τίτλο **CustomerName** και το placeholder “Enter name”.  
* Το κείμενο **After the tag** στην επόμενη γραμμή.

### Αναμενόμενη εικόνα εξόδου (alt text για προσβασιμότητα)

*Alt text:* “Έγγραφο Word που εμφανίζει έναν έλεγχο απλού κειμένου με ετικέτα CustomerName, ακολουθούμενο από τη γραμμή ‘After the tag’.”

## Βήμα 4: Προσαρμογή της εμφάνισης του ελέγχου (προαιρετικό)

Αν θέλετε ο έλεγχος να φαίνεται διαφορετικά — π.χ., με πλαίσιο ή σκιασμένο φόντο — χρησιμοποιήστε το enum `SdtAppearanceTags`:

```java
// Insert a plain‑text control with a bounding box appearance
StructuredDocumentTag sdtBox = builder.insertStructuredDocumentTag(
        StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.BOUNDING_BOX);
sdtBox.setTitle("OrderNumber");
sdtBox.setPlaceholderName("Enter order #");
```

Μπορείτε να επαναλάβετε το μοτίβο **προσθήκη κειμένου μετά από τον έλεγχο** για κάθε ετικέτα που εισάγετε:

```java
builder.writeln("First line after first tag");
builder.writeln("Second line after second tag");
```

## Βήμα 5: Διαχείριση πολλαπλών ελέγχων και επαναχρησιμοποίηση του builder

Κατά τη δημιουργία φορμών, συχνά χρειάζεστε πολλούς ελέγχους. Η ίδια παρουσία `DocumentBuilder` μπορεί να εισάγει πολλές ετικέτες διαδοχικά:

```java
String[] titles = {"FirstName", "LastName", "Email"};
for (String title : titles) {
    StructuredDocumentTag tag = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);
    tag.setTitle(title);
    tag.setPlaceholderName("Enter " + title.toLowerCase());
    builder.writeln(" "); // Add a space so the next tag starts on a new line
}
builder.writeln("All fields added above.");
```

Ο βρόχος δείχνει πώς να **αποθηκεύσετε docx με DocumentBuilder** μετά από μια σειρά λειτουργιών **προσθήκη κειμένου μετά από τον έλεγχο**, διατηρώντας τον κώδικα σύντομο.

## Περιπτώσεις άκρων και αντιμετώπιση προβλημάτων

| Κατάσταση | Σε τι να προσέξετε | Προτεινόμενη διόρθωση |
|-----------|-------------------|-----------------------|
| **Απουσία φακέλου εξόδου** | `doc.save` ρίχνει `FileNotFoundException` | Βεβαιωθείτε ότι ο φάκελος υπάρχει (`new File("output").mkdirs();`) πριν καλέσετε το `save`. |
| **Ο έλεγχος εμφανίζεται κενός στο Word** | Το placeholder δεν εμφανίζεται | Επιβεβαιώστε ότι έχετε ορίσει `setPlaceholderName` **μετά** την εισαγωγή της ετικέτας. |
| **Η άδεια δεν φορτώθηκε** | Εμφανίζεται υδατογράφημα “Aspose.Words Evaluation” | Φορτώστε ένα έγκυρο αρχείο άδειας όπως φαίνεται στο Βήμα 2. |
| **Κατεστραμμένοι χαρακτήρες Unicode** | Το κείμενο εκτός ASCII εμφανίζεται ως � | Αποθηκεύστε το έγγραφο με `SaveFormat.DOCX` (προεπιλογή) και βεβαιωθείτε ότι τα αρχεία πηγαίου κώδικα είναι κωδικοποιημένα σε UTF‑8. |

## Πλήρες λειτουργικό παράδειγμα (έτοιμο για αντιγραφή-επικόλληση)

```java
package com.example.docx;

import com.aspose.words.*;

import java.io.File;

public class DocxBuilderDemo {

    public static void main(String[] args) throws Exception {
        // Optional: load license to remove evaluation watermark
        // License license = new License();
        // license.setLicense("Aspose.Words.Java.lic");

        // Ensure the output folder exists
        File outDir = new File("output");
        if (!outDir.exists()) outDir.mkdirs();

        // Build the document
        buildDocument(outDir.getAbsolutePath() + "/SDT.docx");
    }

    private static void buildDocument(String outputPath) throws Exception {
        // 1️⃣ Create a new document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a plain‑text Structured Document Tag (SDT)
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);
        sdt.setTitle("CustomerName");
        sdt.setPlaceholderName("Enter name");

        // 3️⃣ Add regular content after the SDT – this satisfies **add text after control**
        builder.writeln("After the tag");

        // 4️⃣ Save the resulting document – this is the core **save docx with DocumentBuilder** step
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Η εκτέλεση αυτής της κλάσης παράγει το ίδιο αρχείο `SDT.docx` που περιγράφηκε παραπάνω.

---

## Συμπέρασμα

Τώρα ξέρετε πώς να **αποθηκεύσετε docx με DocumentBuilder**, **να εισάγετε έλεγχο απλού κειμένου** και **να προσθέσετε κείμενο μετά από τον έλεγχο** χρησιμοποιώντας το Aspose.Words for Java. Το πλήρες δείγμα κώδικα δείχνει τη ρύθμιση του έργου, τη δημιουργία ελέγχου, την εισαγωγή περιεχομένου και την αποθήκευση του αρχείου σε μια ενιαία, αυτόνομη ροή εργασίας.

Από εδώ μπορείτε:

* Πειραματιστείτε με άλλες τιμές `StructuredDocumentTagType` (π.χ., `RICH_TEXT` ή `DATE`).  
* Συνδυάστε πολλαπλούς ελέγχους για να δημιουργήσετε σύνθετες φόρμες.  
* Εφαρμόστε προσαρμοσμένο στυλ στις γειτονικές παραγράφους για πιο επαγγελματική εμφάνιση.

Αισθανθείτε ελεύθεροι να προσαρμόσετε το μοτίβο στις δικές σας ανάγκες δημιουργίας εγγράφων και να μοιραστείτε τα αποτελέσματά σας στα σχόλια ή στο GitHub. Καλό κώδικο!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Αποθήκευση docx ως pdf με Java – Πλήρης Οδηγός Βήμα‑βήμα](/words/english/java/document-conversion-and-export/save-docx-as-pdf-with-java-complete-step-by-step-guide/)
- [Αποθήκευση docx ως markdown σε Java – Πλήρης Οδηγός Βήμα‑βήμα](/words/english/java/document-conversion-and-export/save-docx-as-markdown-in-java-complete-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}