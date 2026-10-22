---
category: general
date: 2026-07-20
description: Πώς να προσθέσετε κουμπί σε έγγραφο Word χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να εισάγετε ένα κουμπί Forms2OleControl με το DocumentBuilder σε λίγα
  λεπτά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: el
lastmod: 2026-07-20
og_description: Πώς να προσθέσετε ένα κουμπί σε έγγραφο Word με το Aspose.Words. Ακολουθήστε
  αυτόν τον πρακτικό οδηγό για να ενσωματώσετε ένα CommandButton Forms2OleControl
  χρησιμοποιώντας Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Πώς να προσθέσετε κουμπί σε έγγραφο Word – Πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Πώς να προσθέσετε κουμπί σε έγγραφο Word – Οδηγός βήμα‑προς‑βήμα
url: /el/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Προσθέσετε Κουμπί σε Έγγραφο Word – Πλήρες Tutorial Aspose.Words

Έχετε αναρωτηθεί ποτέ **πώς να προσθέσετε κουμπί σε έγγραφο Word** χωρίς να ανοίξετε το UI και να κάνετε κλικ; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές χρειάζονται να ενσωματώνουν προγραμματιστικά διαδραστικούς ελέγχους — σκεφτείτε ένα κουμπί “Submit” σε ένα πρότυπο που αργότερα θα συμπληρωθεί από τον τελικό χρήστη. Τα καλά νέα; Με το Aspose.Words for Java μπορείτε να το κάνετε σε λίγες γραμμές.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για την εισαγωγή ενός `Forms2OleControl` τύπου **CommandButton** χρησιμοποιώντας το `DocumentBuilder`. Στο τέλος θα έχετε ένα έτοιμο `.docx` αρχείο που εμφανίζει ένα κλικ‑με δυνατό κουμπί με την ετικέτα “Click Me”. Καμία μυστήριο, μόνο καθαρός κώδικας και η λογική πίσω από κάθε γραμμή.

## Τι Θα Μάθετε

- Πώς να δημιουργήσετε ένα νέο έγγραφο Word από το μηδέν.
- Πώς να χρησιμοποιήσετε **DocumentBuilder** για να τοποθετήσετε ένα **Forms2OleControl**.
- Γιατί πρέπει να ορίσετε τη λεζάντα του κουμπιού και το μέγεθος όπως το κάνουμε.
- Πώς να αποθηκεύσετε και να επαληθεύσετε το αποτέλεσμα.
- Κοινά προβλήματα (π.χ., ελλιπείς βιβλιοθήκες, μη υποστηριζόμενοι τύποι ελέγχου) και πώς να τα αποφύγετε.

**Prerequisites** – Χρειάζεστε Java 8+ (ή νεότερη) και τη βιβλιοθήκη Aspose.Words for Java (έκδοση 23.12 ή νεότερη). Ένα IDE όπως IntelliJ IDEA ή Eclipse θα κάνει τη διαδικασία πιο ομαλή, αλλά οποιοσδήποτε επεξεργαστής κειμένου λειτουργεί.

---

## Βήμα 1: Ρυθμίστε το Έργο σας και Εισάγετε τις Εξαρτήσεις

Πριν τρέξει οποιοσδήποτε κώδικας, το Maven (ή Gradle) πρέπει να ξέρει από πού να κατεβάσει το Aspose.Words. Προσθέστε αυτό το απόσπασμα στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Χρησιμοποιήστε την πιο πρόσφατη έκδοση· οι παλαιότερες εκδόσεις μπορεί να μην περιλαμβάνουν το API `Forms2OleControl`.

Μόλις η εξάρτηση λυθεί, είστε έτοιμοι να γράψετε κώδικα Java.

---

## Βήμα 2: Δημιουργήστε ένα Νέο Έγγραφο και Αποκτήστε ένα DocumentBuilder

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το πακέτο `.docx`, ενώ το `DocumentBuilder` είναι το πινέλο που χρησιμοποιείτε για να “ζωγραφίσετε” περιεχόμενο σε αυτό. Σκεφτείτε το `DocumentBuilder` ως το “κέρσορα” που ξέρει πού πρέπει να τοποθετηθεί το επόμενο στοιχείο.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** Η αρχικοποίηση ενός νέου `Document` σας δίνει έναν καθαρό καμβά. Ο builder αυτόματα δείχνει στην πρώτη παράγραφο, έτσι δεν χρειάζεται να διαχειριστείτε ενότητες ή σελίδες χειροκίνητα.

---

## Βήμα 3: Εισαγωγή ενός Forms2OleControl Τύπου CommandButton

Τώρα έρχεται το αστέρι της παράστασης: `insertForms2OleControl`. Αυτή η μέθοδος δημιουργεί έναν έλεγχο OLE (Object Linking and Embedding) που το Word αντιμετωπίζει ως στοιχείο φόρμας. Θα περάσουμε τρία ορίσματα:

1. `Forms2OleControlType.COMMANDBUTTON` – λέει στο Word ότι θέλουμε ένα κουμπί.  
2. `100` – πλάτος σε points (≈1.39 ίντσες).  
3. `30` – ύψος σε points (≈0.42 ίντσες).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**How it works:** Στο παρασκήνιο το Aspose.Words δημιουργεί το κατάλληλο XML στο τμήμα `word/document.xml`, αναφέροντας το OLE αντικείμενο. Οι διαστάσεις που δίνετε γίνονται σεβαστές από τη μηχανή διάταξης του Word, έτσι το κουμπί εμφανίζεται ακριβώς εκεί που βρίσκεται ο κέρσορας του builder.

---

## Βήμα 4: Ορισμός της Λεζάντας (Κειμένου) στο Κουμπί

Ένα κουμπί χωρίς ετικέτα είναι συγκεχυμένο—σκεφτείτε ένα σιωπηλό κουμπί ανελκυστήρα. Η μέθοδος `setCaption` ορίζει το ορατό κείμενο:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Μπορείτε να αλλάξετε τη λεζάντα σε οτιδήποτε: “Submit”, “Approve”, ή ακόμη και σε μια τοπική συμβολοσειρά. Η λεζάντα αποθηκεύεται στις ιδιότητες του OLE αντικειμένου, έτσι το Word θα την αποδώσει εγγενώς.

---

## Βήμα 5: Αποθήκευση του Εγγράφου και Επαλήθευση του Αποτελέσματος

Τέλος, γράψτε το αρχείο στο δίσκο. Επιλέξτε έναν φάκελο στον οποίο έχετε δικαίωμα εγγραφής· διαφορετικά θα αντιμετωπίσετε `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Ανοίξτε το `button-demo.docx` στο Microsoft Word. Θα πρέπει να δείτε ένα κουμπί με την ετικέτα **Click Me** τοποθετημένο στην κορυφή του εγγράφου. Κάνοντας κλικ σε αυτό στο Word θα ενεργοποιηθεί η προεπιλεγμένη συμπεριφορά OLE (συνήθως ένα μήνυμα placeholder, εκτός αν συνδέσετε μια μακροεντολή).

## Συνηθισμένες Καταστάσεις Άκρων και Πώς να τις Διαχειριστείτε

| Κατάσταση | Γιατί Συμβαίνει | Διόρθωση |
|-----------|----------------|----------|
| **Missing `Forms2OleControl` type** | Οι παλαιότερες εκδόσεις του Aspose.Words δεν εκθέτουν αυτό το enum. | Αναβαθμίστε στην έκδοση 23.12+ ή νεότερη. |
| **Button appears as a picture** | Οι ρυθμίσεις ασφαλείας του Word εμποδίζουν τα OLE controls. | Ενεργοποιήστε την επιλογή “Trust access to the VBA project object model” στο Trust Center, ή χρησιμοποιήστε ένα αρχείο `.docm` με ενεργοποιημένα μακροεντολές. |
| **Incorrect size** | Συγχυση μεταξύ points και pixels. | Θυμηθείτε ότι 1 point = 1/72 inch. Προσαρμόστε τους αριθμούς αναλόγως. |
| **Saving throws `FileNotFoundException`** | Η διαδρομή δεν υπάρχει. | Βεβαιωθείτε ότι ο φάκελος (`output/`) δημιουργείται πριν από το `doc.save`. Χρησιμοποιήστε `new File("output").mkdirs();`. |

## Επέκταση του Παραδείγματος: Προσθήκη Πολλαπλών Κουμπιών ή Άλλων Ελέγχων

Αν χρειάζεστε περισσότερα από ένα κουμπί, απλώς μετακινήστε τον κέρσορα του builder με `builder.moveTo` ή `builder.writeln()` πριν καλέσετε ξανά το `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Μπορείτε επίσης να εισάγετε ένα **CheckBox**, **ComboBox**, ή **ListBox** αντικαθιστώντας το `Forms2OleControlType.COMMANDBUTTON` με την κατάλληλη τιμή enum (`CHECKBOX`, `COMBOBOX`, κ.λπ.). Οι ίδιοι παράμετροι πλάτους/ύψους ισχύουν.

## Πώς Αυτό Εντάσσεται σε Μεγαλύτερες Ροές Εργασίας Αυτοματοποίησης Word

- **Template Generation:** Δημιουργία προτύπου σύμβασης που περιλαμβάνει ένα κουμπί “Approve” για επακόλουθη έγκριση.  
- **Reporting:** Δημιουργία ημερήσιας αναφοράς με κουμπί “Refresh Data” που ενεργοποιεί μια μακροεντολή.  
- **Form Distribution:** Αποστολή ερωτηματολογίου με προσυμπληρωμένους διαδραστικούς ελέγχους.

Όλα αυτά τα σενάρια ωφελούνται από την προσέγγιση **Word automation** που παρουσιάσαμε. Ενσωματώνοντας ελέγχους προγραμματιστικά, εξαλείφετε την ανάγκη χειροκίνητης επεξεργασίας και μειώνετε τα ανθρώπινα λάθη.

## Πλήρης Κώδικας Πηγής (Έτοιμος για Αντιγραφή‑Επικόλληση)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Expected output:** Όταν ανοίξετε το `output/button-demo.docx` στο Microsoft Word, θα δείτε δύο κουμπιά—“Click Me” και “Submit”—στοιχισμένα κάθετα στην κορυφή του αρχείου.

## Συμπέρασμα

Απαντήσαμε στο **πώς να προσθέσετε κουμπί σε έγγραφο Word** χρησιμοποιώντας το Aspose.Words for Java, βήμα‑βήμα. Ξεκινώντας από ένα κενό `Document`, αξιοποιήσαμε το **DocumentBuilder** για να εισάγουμε ένα `Forms2OleControl` τύπου **CommandButton**, θέσαμε μια φιλική λεζάντα και αποθηκεύσαμε το αποτέλεσμα. Η προσέγγιση κλιμακώνεται σε πολλαπλούς ελέγχους και ενσωματώνεται άψογα σε ευρύτερες **Word automation** αλυσίδες.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να αντικαταστήσετε το κουμπί με ένα **CheckBox**, ή συνδέστε μια μακροεντολή που θα αντιδρά όταν ο χρήστης κάνει κλικ στο κουμπί σε ένα αρχείο `.docm`. Το ίδιο μοτίβο ισχύει—απλώς αλλάξτε το enum και προσαρμόστε τη λεζάντα.

Αν αντιμετωπίσετε δυσκολίες, ελέγξτε ξανά την έκδοση της βιβλιοθήκης και τα δικαιώματα του φακέλου εξόδου. Μη διστάσετε να αφήσετε ένα σχόλιο παρακάτω με ερωτήσεις ή να μοιραστείτε τη δική σας περίπτωση χρήσης. Καλή κωδικοποίηση!

## Τι Θα Μάθετε Στη Σύντομη Επόμενη

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}