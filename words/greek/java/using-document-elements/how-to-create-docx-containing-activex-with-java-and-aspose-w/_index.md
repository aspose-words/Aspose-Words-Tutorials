---
category: general
date: 2026-09-27
description: Δημιουργήστε docx που περιέχει ActiveX σε Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να εισάγετε ένα κουμπί εντολής ActiveX βήμα‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: el
lastmod: 2026-09-27
og_description: Δημιουργήστε docx που περιέχει ActiveX σε Java με το Aspose.Words.
  Ακολουθήστε αυτόν τον οδηγό για να εισαγάγετε ένα κουμπί εντολής ActiveX και να
  αποθηκεύσετε το έγγραφο.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Δημιουργία docx που περιέχει ActiveX σε Java – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Πώς να δημιουργήσετε docx που περιέχει ActiveX με Java και Aspose.Words
url: /el/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε docx που περιέχει ActiveX με Java και Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε docx που περιέχει ActiveX**, αυτός ο οδηγός σας παρουσιάζει μια πλήρη λύση. Θα μάθετε πώς να **εισάγετε κουμπί εντολής ActiveX** σε ένα αρχείο Word χρησιμοποιώντας το Aspose.Words for Java, και στη συνέχεια να αποθηκεύσετε το αποτέλεσμα ως .docx που μπορεί να ανοιχθεί στο Microsoft Word.

Η δημιουργία ενός εγγράφου Word προγραμματιστικά σας εξοικονομεί το χειροκίνητο επεξεργαστικό έργο και εγγυάται τη συνέπεια σε αναφορές, συμβόλαια ή πρότυπα φορμών. Τα παρακάτω βήματα καλύπτουν όλα, από τη ρύθμιση του έργου μέχρι την αντιμετώπιση κοινών προβλημάτων, ώστε να μπορείτε να ενσωματώσετε την τεχνική σε οποιαδήποτε εφαρμογή Java.

## Προαπαιτούμενα

* Java Development Kit (JDK) 8 ή νεότερο εγκατεστημένο.
* Maven 3.6+ (ή άλλο εργαλείο κατασκευής που προτιμάτε).
* Αρχείο άδειας χρήσης Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για δοκιμές).
* Microsoft Word εγκατεστημένο στον προορισμό μηχάνημα εάν θέλετε να επαληθεύσετε οπτικά το ActiveX control.

Αυτά τα στοιχεία απαιτούνται επειδή το Aspose.Words παρέχει το API που δημιουργεί το έγγραφο, ενώ το Word χρειάζεται για την απόδοση του ActiveX control.

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα νέο έργο Maven ή προσθέστε την εξάρτηση Aspose.Words σε ένα υπάρχον `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Συμβουλή:** Διατηρήστε την έκδοση του Aspose.Words συγχρονισμένη με τις επίσημες σημειώσεις έκδοσης για να επωφεληθείτε από διορθώσεις σφαλμάτων και νέες δυνατότητες ActiveX.

## Βήμα 2: Γράψτε τον κώδικα Java που δημιουργεί το έγγραφο

Δημιουργήστε μια κλάση με όνομα `ActiveXDocxCreator`. Ο παρακάτω κώδικας περιλαμβάνει όλες τις απαιτούμενες εισαγωγές, μια μέθοδο `main` και λεπτομερή σχόλια που εξηγούν κάθε λειτουργία.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Γιατί κάθε γραμμή είναι σημαντική

* `Document` είναι το δοχείο για όλο το περιεχόμενο του Word. Η δημιουργία μιας νέας στιγμής σας δίνει έναν καθαρό καμβά.
* `DocumentBuilder` παρέχει ένα ευέλικτο API για την εισαγωγή στοιχείων· παρακολουθεί αυτόματα το σημείο εισαγωγής.
* `insertForms2OleControl()` δημιουργεί έναν γενικό placeholder ελέγχου OLE. Το Aspose.Words το αντιμετωπίζει ως κοντέινερ ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` λέει στο Word ότι το placeholder πρέπει να αποδοθεί ως CommandButton.
* `setCaption("Click Me")` ορίζει το κείμενο που εμφανίζεται στο κουμπί.
* `setLeft` και `setTop` τοποθετούν το κουμπί σε σχέση με τα περιθώρια της σελίδας. Προσαρμόστε αυτές τις τιμές ώστε να ταιριάζουν στη διάταξή σας.
* `setWidth` και `setHeight` είναι προαιρετικά αλλά βελτιώνουν την εμφάνιση του κουμπιού, ειδικά όταν το προεπιλεγμένο μέγεθος είναι πολύ μικρό.
* `doc.save` γράφει τη δομή στη μνήμη σε ένα φυσικό αρχείο .docx που μπορεί να ανοίξει το Word.

## Βήμα 3: Επαλήθευση του παραγόμενου εγγράφου

Ανοίξτε το `output/ActiveXCommandButton.docx` στο Microsoft Word:

1. Το έγγραφο θα πρέπει να εμφανίζει μια μόνο σελίδα με ένα κουμπί με την ετικέτα **Click Me** τοποθετημένο κοντά στην επάνω‑αριστερή γωνία.
2. Εάν το κουμπί δεν εμφανίζεται, ελέγξτε ότι **οι έλεγχοι ActiveX είναι ενεργοποιημένοι** στο Trust Center του Word (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. Το κουμπί λειτουργεί μόνο σε εκδόσεις του Word για Windows που υποστηρίζουν ActiveX. Σε macOS ή σε web‑based Word, ο έλεγχος θα εμφανιστεί ως στατική εικόνα.

## Βήμα 4: Διαχείριση κοινών περιπτώσεων άκρων

| Situation | Reason | Recommended action |
|-----------|--------|--------------------|
| Το κουμπί λείπει μετά το άνοιγμα του αρχείου | Οι ρυθμίσεις ασφαλείας του Word εμποδίζουν το ActiveX | Ενεργοποιήστε “Run all controls without restrictions” για αξιόπιστες τοποθεσίες. |
| Το παραγόμενο .docx δεν μπορεί να ανοιχτεί | Ασύμβατη έκδοση Aspose.Words | Αναβαθμίστε στην τελευταία έκδοση του Aspose.Words· οι παλαιότερες εκδόσεις ενδέχεται να μην ενσωματώνουν σωστά τα απαιτούμενα τμήματα OLE. |
| Χρειάζεστε το κουμπί να εκτελεί μια μακροεντολή | Το ActiveX μόνο του δεν περιέχει κώδικα μακροεντολής | Συνδυάστε το ActiveX control με μια μακροεντολή VBA που διαχειρίζεται το συμβάν `Click`. Χρησιμοποιήστε τη μέθοδο `DocumentBuilder.insertOleObject` για να ενσωματώσετε ένα πρότυπο ενεργοποιημένο για μακροεντολές. |
| Η διάταξη είναι λανθασμένη σε διαφορετικά μεγέθη σελίδας | Οι συντεταγμένες είναι απόλυτα σημεία | Χρησιμοποιήστε `builder.getPageSetup().setPageWidth` και `setPageHeight` για να τυποποιήσετε το μέγεθος της σελίδας πριν τοποθετήσετε το control. |

## Βήμα 5: Επέκταση της λύσης

Μπορείτε να εισάγετε άλλα ActiveX controls αλλάζοντας το enum `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Το Aspose.Words υποστηρίζει επίσης την εισαγωγή **ActiveX πλαισίων κειμένου**, **πλαισίων λίστας** και **πλαισίων συνδυασμού**. Οι ίδιες μέθοδοι τοποθέτησης (`setLeft`, `setTop`, `setWidth`, `setHeight`) ισχύουν.

Εάν χρειάζεται να τοποθετήσετε πολλαπλά controls, καλέστε επανειλημμένα το `builder.insertForms2OleControl()` και προσαρμόστε τις συντεταγμένες κάθε control ανάλογα.

## Πλήρες αρχείο πηγαίου κώδικα

Παρακάτω βρίσκεται ολόκληρο το αρχείο `ActiveXDocxCreator.java` έτοιμο για αντιγραφή‑και‑επικόλληση:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Η εκτέλεση αυτού του προγράμματος δημιουργεί ένα **docx που περιέχει ActiveX** το οποίο μπορείτε να διανείμετε σε τελικούς χρήστες που χρειάζονται διαδραστικές φόρμες.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε docx που περιέχει ActiveX** χρησιμοποιώντας Java και Aspose.Words, και πώς να **εισάγετε κουμπί εντολής ActiveX** προγραμματιστικά. Ο οδηγός κάλυψε τη ρύθμιση του έργου, τον πλήρη κώδικα, τα βήματα επαλήθευσης και τις στρατηγικές αντιμετώπισης τυπικών προβλημάτων.

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη VBA μακροεντολών για την απόκριση στο κλικ του κουμπιού.
* Ενσωμάτωση άλλων ActiveX controls όπως πλαίσια ελέγχου ή πλαίσια συνδυασμού.
* Αυτοματοποίηση της δημιουργίας πολυ‑σελιδών φορμών με δυναμικά δεδομένα.

Δοκιμάστε διαφορετικές συντεταγμένες, μεγέθη και τύπους ελέγχων για να ταιριάξουν με τη συγκεκριμένη διάταξη του εγγράφου σας. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Χρήση OLE Objects και ActiveX Controls στο Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}