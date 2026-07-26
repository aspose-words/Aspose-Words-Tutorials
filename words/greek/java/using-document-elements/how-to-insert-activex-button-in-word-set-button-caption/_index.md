---
category: general
date: 2026-07-26
description: Πώς να εισαγάγετε κουμπί ActiveX σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words – μάθετε πώς να ορίσετε τη λεζάντα, τη θέση και το μέγεθος του κουμπιού
  σε λίγες μόνο γραμμές.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: el
lastmod: 2026-07-26
og_description: Πώς να εισάγετε κουμπί ActiveX σε ένα έγγραφο Word με το Aspose.Words.
  Ακολουθήστε αυτόν τον βήμα‑βήμα οδηγό για να ορίσετε τη λεζάντα, τη θέση και το
  μέγεθος του κουμπιού.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Πώς να εισάγετε κουμπί ActiveX στο Word – Σύντομος οδηγός
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Πώς να εισαγάγετε κουμπί ActiveX στο Word – Ορίστε τη λεζάντα του κουμπιού
url: /el/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εισάγετε Κουμπί ActiveX στο Word – Ορισμός Ετικέτας Κουμπιού

Έχετε αναρωτηθεί ποτέ **πώς να εισάγετε ActiveX** ελέγχους σε ένα αρχείο Word χωρίς να ανοίξετε το UI; Δεν είστε ο μόνος. Σε πολλές επιχειρησιακές εφαρμογές χρειάζεστε ένα κλικ‑κουμπί που εκτελεί μια μακροεντολή, και η προγραμματιστική προσθήκη του εξοικονομεί ώρες. Αυτός ο οδηγός σας δείχνει ακριβώς **πώς να εισάγετε ActiveX** CommandButton χρησιμοποιώντας το Aspose.Words for Java, και—ναι—πώς να **ορίσετε την ετικέτα του κουμπιού** ώστε ο χρήστης να ξέρει τι να κάνει κλικ.

Θα περάσουμε από όλη τη διαδικασία: από τη ρύθμιση της βιβλιοθήκης, τη δημιουργία ενός νέου εγγράφου, την προσθήκη του κουμπιού, την προσαρμογή του μεγέθους και της θέσης του, την προσθήκη μιας φιλικής ετικέτας, και τέλος την αποθήκευση του αρχείου. Στο τέλος θα έχετε ένα εκτελέσιμο `.docx` που ανοίγει στο Word με ένα πλήρως λειτουργικό κουμπί ActiveX έτοιμο να εκκινήσει τη μακροεντολή σας.

---

## Τι Θα Μάθετε

- Εγκατάσταση και αναφορά του Aspose.Words σε ένα έργο Java.  
- Δημιουργία ενός νέου `Document` και `DocumentBuilder`.  
- **Insert ActiveX** CommandButton control με μία γραμμή κώδικα.  
- **Set button caption**, προσαρμογή της θέσης του και ορισμός των διαστάσεών του.  
- Αποθήκευση του εγγράφου και άνοιγμα του στο Word για να δείτε το αποτέλεσμα.

Δεν απαιτείται προηγούμενη εμπειρία με το ActiveX· αρκεί βασική γνώση της Java και ένα αντίγραφο του Aspose.Words.

---

## Προαπαιτούμενα

- Java 8 ή νεότερη εγκατεστημένη στο σύστημά σας.  
- Maven ή Gradle για διαχείριση εξαρτήσεων (θα δείξουμε το απόσπασμα Maven).  
- Αδειοδοτημένο ή δοκιμαστικό αντίγραφο του **Aspose.Words for Java** (η δωρεάν δοκιμή λειτουργεί καλά για αυτήν την επίδειξη).  
- Microsoft Word (οποιαδήποτε πρόσφατη έκδοση) για δοκιμή του παραγόμενου αρχείου.

---

## Βήμα 1: Ρύθμιση του Aspose.Words στο Έργο Σας

Πρώτα απ' όλα—προσθέστε την εξάρτηση Aspose.Words. Αν χρησιμοποιείτε Maven, τοποθετήστε αυτό στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Οι χρήστες του Gradle μπορούν να προσθέσουν:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Μετά από ένα γρήγορο `mvn clean install` (ή `gradle build`) η βιβλιοθήκη θα βρίσκεται στο classpath σας και είστε έτοιμοι να κωδικοποιήσετε.

---

## Βήμα 2: Δημιουργία Νέου Εγγράφου και Builder

Ένα `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` σας επιτρέπει να το επεξεργαστείτε. Σκεφτείτε το builder ως ένα στυλό που σχεδιάζει πάνω σε έναν φρέσκο καμβά.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Γιατί να ξεκινήσετε με ένα κενό έγγραφο; Σας εξασφαλίζει πλήρη έλεγχο σε κάθε στοιχείο που προσθέτετε και δεν υπάρχει κρυφή μορφοποίηση που να σας εκπλήσσει αργότερα.

---

## Βήμα 3: Εισαγωγή του Ελέγχου ActiveX CommandButton

Τώρα για το αστέρι της παράστασης. Το Aspose.Words εκθέτει τη μέθοδο `insertForms2OleControl` που μπορεί να τοποθετήσει οποιονδήποτε έλεγχο ActiveX καθορίζετε. Εδώ ζητάμε ένα **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Η μέθοδος επιστρέφει ένα αντικείμενο `Forms2OleControl`, δίνοντάς σας προγραμματιστική πρόσβαση στις ιδιότητες του κουμπιού. Εδώ το **how to insert activex** γίνεται μια εντολή μίας γραμμής—χωρίς να ασχοληθείτε με χαμηλού επιπέδου COM APIs.

---

## Βήμα 4: Θέση, Μέγεθος και Ορισμός Ετικέτας Κουμπιού

Ένα κουμπί που αιωρείται στη μέση της σελίδας δεν είναι πολύ χρήσιμο. Θα θέλετε να το τοποθετήσετε εκεί που οι χρήστες το αναμένουν, να του δώσετε λογικό μέγεθος, και—το πιο σημαντικό—**να ορίσετε την ετικέτα του κουμπιού** ώστε να ξέρουν τι κάνει το κλικ.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Γιατί αυτά τα νούμερα;** Το Word χρησιμοποιεί μονάδες σημείων (1 pt ≈ 1/72 inch). `100 pt` ≈ 1.4 ίντσες από τα αριστερά, `150 pt` ≈ 2.1 ίντσες από την κορυφή—περίπου το κέντρο μιας τυπικής σελίδας A4. Προσαρμόστε τα ανάλογα με τη διάταξή σας.

Ο ορισμός της ετικέτας είναι κρίσιμος· χωρίς αυτήν το κουμπί φαίνεται ως κενό ορθογώνιο. Η μέθοδος `setCaption` δέχεται οποιαδήποτε συμβολοσειρά, ώστε να μπορείτε να το τοπικοποιήσετε αργότερα αν χρειαστεί.

---

## Βήμα 5: Αποθήκευση του Εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιονδήποτε φάκελο θέλετε· απλώς βεβαιωθείτε ότι η διαδρομή υπάρχει.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Όταν ανοίξετε το `ActiveXButton.docx` στο Word, θα δείτε ένα ωραία τοποθετημένο κουμπί με την ετικέτα **«Click Me.»** Αν κάνετε διπλό κλικ, το Word θα σας ζητήσει να ενεργοποιήσετε τις μακροεντολές (επειδή οι έλεγχοι ActiveX θεωρούνται ενεργοποιημένοι με μακροεντολές). Από εκεί μπορείτε να συνδέσετε μια ρουτίνα VBA στο γεγονός `Click` του κουμπιού.

---

## Περιπτώσεις Άκρων & Συμβουλές που Μπορεί να Χάσετε

- **Macro‑Enabled Format**: Το Word απενεργοποιεί τους ελέγχους ActiveX σε απλά αρχεία `.docx` εκτός εάν ο χρήστης ενεργοποιήσει τις μακροεντολές. Αν χρειάζεστε το κουμπί να λειτουργεί αμέσως, σκεφτείτε να αποθηκεύσετε ως `.docm` (macro‑enabled) χρησιμοποιώντας `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibility**: Οι παλαιότερες εκδόσεις του Word (πριν το 2007) χρησιμοποιούν το δυαδικό format `.doc`. Το Aspose.Words μπορεί να αποθηκεύσει σε αυτό το format, αλλά οι ιδιότητες του ελέγχου μπορεί να εμφανιστούν ελαφρώς διαφορετικά.
- **Security Settings**: Ορισμένα εταιρικά περιβάλλοντα κλειδώνουν το ActiveX. Αν το κουμπί σας δεν εμφανίζεται, ελέγξτε το Trust Center του Word → ActiveX Settings.
- **Multiple Buttons**: Θέλετε περισσότερα από ένα; Απλώς επαναλάβετε την κλήση `insertForms2OleControl` και προσαρμόστε τις τιμές `Left`/`Top` κάθε κουμπιού. Κρατήστε υπόψη τα επιστρεφόμενα αντικείμενα ώστε να μπορείτε να ορίσετε ξεχωριστές ετικέτες.
- **Styling the Caption**: Η ετικέτα κληρονομεί την προεπιλεγμένη γραμματοσειρά. Για να την αλλάξετε, θα πρέπει να επεξεργαστείτε το υποκείμενο XML ή να εφαρμόσετε ένα στυλ Word μετά την εισαγωγή—πέρα από το εύρος αυτού του γρήγορου οδηγού, αλλά εφικτό με το API `ParagraphFormat` του Aspose.Words.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται η πλήρης, έτοιμη για εκτέλεση κλάση Java. Αντιγράψτε‑και‑επικολλήστε την στο IDE σας, προσαρμόστε τη διαδρομή εξόδου και πατήστε **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Αναμενόμενο αποτέλεσμα**: Μετά την εκτέλεση, η κονσόλα εμφανίζει τη θέση αποθήκευσης. Ανοίγοντας το παραγόμενο αρχείο στο Word εμφανίζεται ένα κουμπί τοποθετημένο περίπου στο κέντρο της σελίδας, με ετικέτα “Click Me”. Κάνοντας κλικ θα ενεργοποιηθεί το τυπικό γεγονός κλικ του ActiveX (θα χρειαστεί να συνδέσετε μια μακροεντολή VBA για να ανταποκριθεί).

---

## Συμπέρασμα

Τώρα ξέρετε **πώς να εισάγετε ActiveX** ελέγχους CommandButton σε ένα έγγραφο Word προγραμματιστικά με το Aspose.Words, και έχετε δει ακριβώς πώς να **ορίσετε την ετικέτα του κουμπιού**, τη θέση και το μέγεθος του ελέγχου. Αυτή η προσέγγιση εξαλείφει την χειροκίνητη εργασία UI, ενσωματώνεται καθαρά σε αυτόματους δημιουργούς αναφορών, και σας δίνει πλήρη έλεγχο πάνω στο

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή Σχημάτων σε Έγγραφα Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Εισαγωγή Ενσωματωμένης Εικόνας σε Έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Εισαγωγή Εικόνας στην Κεφαλίδα Εγγράφου Word | Aspose.Words για .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}