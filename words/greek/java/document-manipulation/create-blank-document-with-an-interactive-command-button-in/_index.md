---
category: general
date: 2026-09-18
description: Δημιουργήστε κενό έγγραφο σε Java και προσθέστε ένα κουμπί ActiveX. Μάθετε
  πώς να εισάγετε κουμπί εντολής, να δημιουργήσετε μια διαδραστική φόρμα και να αποθηκεύσετε
  ένα έγγραφο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: el
lastmod: 2026-09-18
og_description: Δημιουργήστε κενό έγγραφο σε Java και ενσωματώστε ένα κουμπί εντολής
  ActiveX. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να δημιουργήσετε μια διαδραστική
  φόρμα και να αποθηκεύσετε το αρχείο Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Δημιουργήστε κενό έγγραφο με διαδραστικό κουμπί εντολής στο Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Δημιουργία κενού εγγράφου με διαδραστικό κουμπί εντολής στο Word χρησιμοποιώντας
  Java
url: /el/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου με διαδραστικό κουμπί εντολής στο Word χρησιμοποιώντας Java

Αν χρειάζεστε **να δημιουργήσετε κενό έγγραφο** που περιέχει ένα κλικ-με δυνατό κουμπί, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for Java. Θα μάθετε πώς να δημιουργήσετε μια διαδραστική φόρμα, να προσθέσετε ένα ActiveX κουμπί και, τέλος, να αποθηκεύσετε το αρχείο Word—όλα σε λίγα σύντομα βήματα.

Η ενσωμάτωση ενός κουμπιού εντολής μετατρέπει ένα στατικό .docx σε μια λειτουργική φόρμα που οι τελικοί χρήστες μπορούν να αλληλεπιδράσουν απευθείας μέσα στο Microsoft Word. Αυτό το tutorial καλύπτει επίσης **πώς να εισάγετε κουμπί εντολής**, αντιμετωπίζει κοινά προβλήματα και επεκτείνει τη λύση για πιο σύνθετες φόρμες.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη (ο κώδικας μεταγλωττίζεται με JDK 17+)
* Aspose.Words for Java 23.9 ή νεότερη – η βιβλιοθήκη παρέχει `Document`, `DocumentBuilder` και `Forms2OleControl`.
* Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) που μπορεί να προσθέσει την εξάρτηση Aspose.Words.
* Βασικές γνώσεις της σύνταξης Java και των εννοιών εγγράφων Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Βήμα 1: Δημιουργία κενής εγγράφου

Η πρώτη ενέργεια είναι η δημιουργία ενός νέου αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα κενό αρχείο Word έτοιμο για περιεχόμενο.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Η δημιουργία ενός κενής εγγράφου σας δίνει έναν καθαρό καμβά, κάτι που είναι απαραίτητο όταν θέλετε **να δημιουργήσετε έγγραφο word** προγραμματιστικά χωρίς κάποιο προϋπάρχον πρότυπο.

## Βήμα 2: Αρχικοποίηση του DocumentBuilder

`DocumentBuilder` είναι η κύρια κλάση για την προσθήκη κειμένου, πινάκων και στοιχείων φόρμας. Λειτουργεί πάνω στο `Document` που μόλις δημιουργήσατε.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder διατηρεί το τρέχον σημείο εισαγωγής, ώστε οι επόμενες εντολές να επηρεάζουν τη σωστή θέση στο αρχείο.

## Βήμα 3: Εισαγωγή ελέγχου κουμπιού Forms2Ole

Το Aspose.Words εκθέτει την κλάση `Forms2OleControl` για ελέγχους ActiveX. Για **να προσθέσετε activex κουμπί**, ζητάτε έναν τύπο `COMMANDBUTTON` από τον builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Η μέθοδος `insertForms2OleControl` εισάγει το στοιχείο στην τρέχουσα θέση του κέρσορα του builder. Επειδή το στοιχείο είναι αντικείμενο ActiveX, λειτουργεί μόνο στην έκδοση desktop του Microsoft Word, όχι στο Word Online.

## Βήμα 4: Διαμόρφωση εμφάνισης και θέσης του κουμπιού

Μπορείτε να ορίσετε τη λεζάντα, το μέγεθος και τη θέση του κουμπιού χρησιμοποιώντας τις μεθόδους setter του ελέγχου. Οι τιμές θέσης μετρώνται σε points (1 point = 1/72 ίντσα).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Γιατί να διαμορφώσετε αυτές τις ιδιότητες;* Η ρύθμιση των `Top` και `Left` εξασφαλίζει ότι το κουμπί εμφανίζεται εκεί που το περιμένετε στη σελίδα, ενώ το `Caption` ορίζει την ετικέτα που βλέπουν οι χρήστες. Αν παραλείψετε το πλάτος/ύψος, το Word θα ορίσει προεπιλεγμένες διαστάσεις, οι οποίες μπορεί να μην ταιριάζουν με το σχέδιό σας.

### Συμβουλή
Αν σκοπεύετε να προσθέσετε πολλαπλά στοιχεία, καλέστε `builder.moveToDocumentEnd()` πριν από κάθε εισαγωγή για να αποφύγετε την επικάλυψη αντικειμένων.

## Βήμα 5: Αποθήκευση του εγγράφου με το ενσωματωμένο κουμπί εντολής

Τέλος, γράψτε το έγγραφο στο δίσκο. Η επέκταση του αρχείου πρέπει να είναι `.docx` (ή `.doc` για παλαιότερες εκδόσεις Word) ώστε να διατηρηθεί ο έλεγχος ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Όταν ανοίξετε το `CommandButton.docx` στο Microsoft Word, θα δείτε ένα κουμπί με την ετικέτα **Click Me**. Κάνοντας κλικ θα ενεργοποιηθεί η προεπιλεγμένη ενέργεια ActiveX (που, από προεπιλογή, δεν κάνει τίποτα). Μπορείτε αργότερα να συνδέσετε ένα macro ή σενάριο VBA για να ορίσετε προσαρμοσμένη συμπεριφορά.

## Πώς να εισάγετε κουμπί εντολής σε υπάρχουσα φόρμα (προαιρετικό)

Αν έχετε ήδη μια φόρμα με πεδία κειμένου και θέλετε **να δημιουργήσετε διαδραστική φόρμα** που περιλαμβάνει κουμπί, ακολουθήστε τα παρακάτω επιπλέον βήματα:

1. Φορτώστε το υπάρχον έγγραφο: `Document doc = new Document("ExistingForm.docx");`
2. Μετακινήστε τον builder στην επιθυμητή θέση: `builder.moveToParagraph(5, 0); // 6ο παράγραφος, πρώτο κόμβος`
3. Εισάγετε το κουμπί όπως στο Βήμα 3.
4. Προσαρμόστε τα `Top`/`Left` του κουμπιού βάσει της διάταξης της παραγράφου.

Αυτή η προσέγγιση σας επιτρέπει να εμπλουτίσετε οποιοδήποτε προϋπάρχον πρότυπο Word με ένα κουμπί ActiveX χωρίς να χρειάζεται να ξαναδημιουργήσετε ολόκληρο το αρχείο.

## Ακραίες περιπτώσεις και αντιμετώπιση προβλημάτων

| Κατάσταση | Τι να ελέγξετε | Προτεινόμενη διόρθωση |
|-----------|---------------|-----------------|
| Το κουμπί δεν εμφανίζεται στο Word | Βεβαιωθείτε ότι ανοίξατε το αρχείο στην έκδοση desktop του Word (το Word Online αφαιρεί το ActiveX). | Ανοίξτε το αρχείο σε Word 2016+ desktop. |
| Η λεζάντα κόβεται | Επαληθεύστε ότι το πλάτος του κουμπιού είναι αρκετό για το κείμενο. | Αυξήστε το `setWidth` μέχρι να χωρά η λεζάντα. |
| Η αποθήκευση ρίχνει `IOException` | Επιβεβαιώστε ότι ο φάκελος εξόδου υπάρχει και έχετε δικαιώματα εγγραφής. | Δημιουργήστε το φάκελο ή τρέξτε το πρόγραμμα με αυξημένα δικαιώματα. |
| Πολλά κουμπιά επικαλύπτονται | Ο κέρσορας του builder μπορεί να μην έχει μετακινηθεί μετά την προηγούμενη εισαγωγή. | Καλέστε `builder.moveToDocumentEnd()` πριν την εισαγωγή κάθε νέου ελέγχου. |

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα πλήρες, αυτόνομο πρόγραμμα Java που μπορείτε να αντιγράψετε, να μεταγλωττίσετε και να τρέξετε. Δείχνει **δημιουργία κενής εγγράφου**, **προσθήκη activex κουμπιού** και **αποθήκευση word εγγράφου** σε μία ροή.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενη έξοδος**

```
Document created: CommandButton.docx
```

Ανοίγοντας το `CommandButton.docx` θα δείτε μια μοναδική σελίδα με ένα κουμπί με την ετικέτα **Click Me** τοποθετημένο 100 pt από τις άνω και αριστερές άκρες.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κενό έγγραφο**, να ενσωματώσετε ένα **ActiveX κουμπί** και να μετατρέψετε ένα απλό αρχείο Word σε **διαδραστική φόρμα**. Με την εξοικείωση με το **πώς να εισάγετε κουμπί εντολής**, μπορείτε να επεκτείνετε αυτό το μοτίβο για να προσθέσετε πλαίσια ελέγχου, λίστες επιλογής ή ακόμη και προσαρμοσμένη λογική VBA.

Στη συνέχεια, εξερευνήστε τα παρακάτω συναφή θέματα:

* **Δημιουργία διαδραστικής φόρμας** με πεδία κειμένου (`builder.insertField`)  
* **Προσθήκη activex κουμπιού** που εκτελεί μακροεντολή VBA (`builder.insertOleObject`)  
* **Δημιουργία εγγράφου word** από πρότυπο χρησιμοποιώντας `Document(docTemplatePath)`  
* Μετατροπή του παραγόμενου .docx σε PDF διατηρώντας το κουμπί (σημείωση: το PDF θα εμφανίζει το κουμπί ως στατική εικόνα).

Μη διστάσετε να πειραματιστείτε με το μέγεθος, τη θέση και τη λεζάντα του κουμπιού ώστε να ταιριάζει στο UI design σας. Καλή προγραμματιστική διασκέδαση!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Δημιουργία έργου Vba σε έγγραφο Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Δημιουργία νέου εγγράφου Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}