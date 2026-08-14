---
category: general
date: 2026-08-14
description: Δημιουργήστε κουμπί ActiveX σε αρχείο docx με Java και Aspose.Words.
  Μάθετε πώς να προσθέσετε ένα κουμπί φόρμας στο Word προγραμματιστικά και να αποθηκεύσετε
  το έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: el
lastmod: 2026-08-14
og_description: Δημιουργήστε κουμπί ActiveX σε αρχείο docx με Java χρησιμοποιώντας
  το Aspose.Words. Αυτός ο οδηγός σας δείχνει πώς να προσθέσετε ένα κουμπί φόρμας
  στο Word, να το διαμορφώσετε και να αποθηκεύσετε το αρχείο.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Δημιουργία κουμπιού ActiveX docx σε Java – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Δημιουργία κουμπιού ActiveX σε docx με Java – πλήρης οδηγός προγραμματισμού
url: /el/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κουμπιού ActiveX σε αρχείο docx με Java – πλήρης οδηγός προγραμματισμού

Αν χρειάζεστε **να δημιουργήσετε κουμπί ActiveX σε docx** με Java, αυτός ο οδηγός σας καθοδηγεί βήμα‑βήμα σε όλη τη διαδικασία. Θα δείτε πώς να προσθέσετε ένα κουμπί φόρμας στο Word, να ρυθμίσετε τις ιδιότητές του και να παραγάγετε ένα έτοιμο προς χρήση .docx αρχείο.

Η εργασία με ελέγχους ActiveX είναι συχνή απαίτηση όταν αυτοματοποιούμε κληροδοτημένες φόρμες Word. Σε αυτό το tutorial θα μάθετε πώς να **προσθέσετε κουμπί φόρμας σε έγγραφα Word** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words for Java, ώστε να ενσωματώνετε διαδραστικούς ελέγχους χωρίς χειροκίνητη επεξεργασία.

## Τι θα χρειαστείτε

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη (ο κώδικας μπορεί να μεταγλωττιστεί και με παλαιότερες εκδόσεις, αλλά συνιστάται η Java 17).
* Aspose.Words for Java 23.10 ή νεότερη – κατεβάστε το JAR από την ιστοσελίδα της Aspose ή προσθέστε την εξάρτηση Maven.
* Ένα IDE (IntelliJ IDEA, Eclipse ή VS Code) ή έναν απλό επεξεργαστή κειμένου και εργαλεία γραμμής εντολών για τη δημιουργία.
* Βασικές γνώσεις σύνταξης Java και αντικειμενοστραφούς προγραμματισμού.

## Πώς να δημιουργήσετε κουμπί ActiveX σε docx με Aspose.Words

Τα παρακάτω βήματα παρουσιάζουν τη σωστή ακολουθία για τη **δημιουργία αντικειμένων κουμπιού ActiveX σε docx** και την ενσωμάτωσή τους σε έγγραφο Word.

### Βήμα 1: Ρύθμιση του έργου και εισαγωγή του Aspose.Words

Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` αν χρησιμοποιείτε Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Ή, αν προτιμάτε Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Αφού η εξάρτηση λυθεί, εισάγετε τις απαιτούμενες κλάσεις στο αρχείο πηγαίου κώδικα Java:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Αυτές οι εισαγωγές σας δίνουν πρόσβαση στις κλάσεις `Document`, `DocumentBuilder` και στο API `Forms2OleControl` που χρησιμοποιείται για την εισαγωγή ελέγχων ActiveX.

### Βήμα 2: Δημιουργία νέου κενού εγγράφου

Δημιουργήστε ένα αντικείμενο `Document`, το οποίο αντιπροσωπεύει ένα άδειο αρχείο Word έτοιμο να λάβει περιεχόμενο.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Η δημιουργία του εγγράφου πρώτα εξασφαλίζει ότι ο επόμενος builder λειτουργεί πάνω σε καθαρό καμβά.

### Βήμα 3: Αρχικοποίηση του DocumentBuilder

`DocumentBuilder` παρέχει μια ρευστή διεπαφή για την εισαγωγή κειμένου, εικόνων και ελέγχων. Συνδέστε το με το έγγραφο που μόλις δημιουργήσατε.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Ο builder παρακολουθεί τη θέση του κέρσορα μέσα στο έγγραφο, ώστε η επόμενη εισαγωγή να γίνει ακριβώς εκεί που το χρειάζεστε.

### Βήμα 4: Εισαγωγή ελέγχου ActiveX CommandButton

Χρησιμοποιήστε τη μέθοδο `insertForms2OleControl` για να ενσωματώσετε ένα ActiveX `CommandButton`. Αυτή η μέθοδος επιστρέφει ένα αντικείμενο `Forms2OleControl` που μπορείτε να ρυθμίσετε περαιτέρω.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Σε αυτό το σημείο το αρχείο .docx περιέχει έναν χώρο κράτησης για το κουμπί, αλλά δεν έχει ακόμη οπτική λεζάντα ή μέγεθος.

### Βήμα 5: Ρύθμιση των ιδιοτήτων του κουμπιού

Ορίστε το όνομα, τη λεζάντα και τα χαρακτηριστικά διάταξης του ελέγχου. Αυτές οι τιμές καθορίζουν πώς θα εμφανίζεται το κουμπί στο Word και πώς θα το αναφέρετε αργότερα μέσω VBA ή σεναρίων αυτοματισμού.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Συμβουλή:** Το Word μετρά τις θέσεις σε points (1 pt ≈ 1/72 in). Προσαρμόστε τα `setTop` και `setLeft` ώστε το κουμπί να ευθυγραμμίζεται με το περιβάλλον περιεχόμενο.

### Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Χρησιμοποιήστε την επέκταση `.docx` για να διατηρήσετε το αρχείο στη σύγχρονη μορφή Office Open XML.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Όταν ανοίξετε το παραγόμενο αρχείο στο Microsoft Word, θα δείτε ένα κουμπί **Submit** τοποθετημένο στις συντεταγμένες που καθορίσατε. Η κλικ στο κουμπί στο Word δεν θα προκαλέσει καμία ενέργεια εκτός αν συνδέσετε κώδικα VBA, αλλά ο έλεγχος είναι πλήρως λειτουργικός για ροές εργασίας βασισμένες σε φόρμες.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Χρειάζομαι ειδική έκδοση του Word;** | Οι έλεγχοι ActiveX υποστηρίζονται στην επιτραπέζια έκδοση του Microsoft Word για Windows. Δεν είναι διαθέσιμοι στο Word για Mac ή στο Word Online. |
| **Μπορώ να το χρησιμοποιήσω με αρχεία `.doc`;** | Ναι. Αποθηκεύστε το έγγραφο με επέκταση `.doc` (`document.save("ActiveXButton.doc")`). Το ίδιο API λειτουργεί και για την παλαιότερη δυαδική μορφή. |
| **Τι γίνεται αν το κουμπί δεν εμφανίζεται;** | Βεβαιωθείτε ότι **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** επιτρέπει ελέγχους ActiveX. Επίσης, ελέγξτε ότι το έγγραφο δεν είναι ανοιγμένο σε “Protected View”. |
| **Μπορώ να προσθέσω άλλους ελέγχους ActiveX;** | Απόλυτα. Αντικαταστήστε το `Forms2OleControlType.COMMAND_BUTTON` με `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` κ.λπ. |
| **Υπάρχει όριο μεγέθους;** | Το μέγεθος του ελέγχου περιορίζεται μόνο από τη διάταξη της σελίδας. Πολύ μεγάλες διαστάσεις μπορεί να προκαλέσουν υπερχείλιση διάταξης. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται μια πλήρης κλάση Java που μπορείτε να αντιγράψετε, να μεταγλωττίσετε και να εκτελέσετε. Περιλαμβάνει όλες τις εισαγωγές, τη μέθοδο `main` και ενσωματωμένα σχόλια για σαφήνεια.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Μετά την εκτέλεση του προγράμματος, το `ActiveXButton.docx` εμφανίζεται στον τρέχοντα φάκελο εργασίας. Ανοίγοντάς το στο Microsoft Word, θα δείτε ένα κλικ‑με δυνατό **Submit** κουμπί τοποθετημένο κοντά στην πάνω‑αριστερή γωνία της πρώτης σελίδας.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε αντικείμενα κουμπιού ActiveX σε docx** με Java χρησιμοποιώντας το Aspose.Words, και έχετε δει πώς να **προσθέσετε κουμπί φόρμας σε έγγραφα Word** προγραμματιστικά. Τα βήματα — ρύθμιση του έργου, δημιουργία εγγράφου, εισαγωγή του ελέγχου, ρύθμιση των ιδιοτήτων του και αποθήκευση — καλύπτουν ολόκληρη τη ροή εργασίας από την αρχή μέχρι το τέλος.

Επόμενα, μπορείτε να εξερευνήσετε:

* Προσθήκη μακροεντολών VBA που ανταποκρίνονται στο κλικ του κουμπιού.
* Ενσωμάτωση άλλων ελέγχων ActiveX όπως πλαίσια ελέγχου ή λίστες.
* Αυτοματοποίηση της δημιουργίας πολυ‑σελιδών φορμών με πολλαπλά διαδραστικά στοιχεία.

Μη διστάσετε να πειραματιστείτε με μεγέθη, θέσεις και λεζάντες ώστε να ταιριάζουν στις συγκεκριμένες απαιτήσεις του σχεδίου φόρμας σας. Καλό κώδικα!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}