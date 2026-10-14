---
category: general
date: 2026-10-13
description: Δημιουργήστε κουμπί πεδίου φόρμας στο Word χρησιμοποιώντας το Aspose.Words
  for Java. Μάθετε πώς να εισάγετε πεδία φόρμας τύπου κουμπί εντολής στο Word και
  να ορίσετε τη λεζάντα του κουμπιού εντολής σε λίγα εύκολα βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: el
lastmod: 2026-10-13
og_description: Δημιουργήστε κουμπί πεδίου φόρμας στο Word με το Aspose.Words για
  Java. Αυτό το σεμινάριο δείχνει πώς να εισάγετε πεδία κουμπιών εντολών στο Word
  και να ορίσετε γρήγορα τη λεζάντα του κουμπιού εντολής.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Δημιουργία κουμπιού πεδίου φόρμας στο Word – Οδηγός Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Δημιουργία κουμπιού πεδίου φόρμας στο Word με το Aspose.Words Java
url: /el/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κουμπιού πεδίου φόρμας στο Word με Aspose.Words Java

Αν χρειάζεστε **create form field button** σε ένα έγγραφο Word, αυτός ο οδηγός σας καθοδηγεί στη διαδικασία χρησιμοποιώντας το Aspose.Words for Java. Είτε δημιουργείτε ένα πρότυπο φόρμας συμπλήρωσης είτε προσθέτετε διαδραστικούς ελέγχους σε μια αναφορά, θα μάθετε πώς να **insert command button word** πεδία φόρμας και **set command button caption** με ελάχιστο κώδικα.

Ο οδηγός καλύπτει τα πάντα, από τη ρύθμιση του Maven μέχρι ένα πλήρως εκτελέσιμο παράδειγμα, ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε τον κώδικα, να τον εκτελέσετε και να δείτε ένα αρχείο `.docx` που περιέχει ένα κλικ-μενού κουμπί έτοιμο για περαιτέρω προσαρμογή.

## Προαπαιτούμενα

- Java 17 (ή νεότερη) εγκατεστημένη και ρυθμισμένη στο σύστημά σας.
- Maven 3.6+ για διαχείριση εξαρτήσεων.
- Ένα IDE ή κειμενογράφο της επιλογής σας (π.χ., IntelliJ IDEA, VS Code).
- Ένα έγκυρο άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για αξιολόγηση).

## Βήμα 1: Προσθήκη Aspose.Words στο Maven project σας

Δημιουργήστε ένα `pom.xml` (ή επεξεργαστείτε το υπάρχον) και συμπεριλάβετε την εξάρτηση Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Συμβουλή:** Διατηρήστε τον αριθμό έκδοσης ενημερωμένο. Οι νέες εκδόσεις προσθέτουν υποστήριξη για τις πιο πρόσφατες δυνατότητες του Word και βελτιώνουν την απόδοση.

## Βήμα 2: Αρχικοποίηση ενός κεντρικού εγγράφου και ενός `DocumentBuilder`

Η κλάση `DocumentBuilder` παρέχει μια ρευστή API για την επεξεργασία ενός εγγράφου Word. Σε αυτό το βήμα δημιουργούμε ένα κενό `Document` και συνδέουμε έναν builder σε αυτό.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Η δημιουργία του εγγράφου είναι η βάση για **create form field button** αντικείμενα αργότερα στον οδηγό.

## Βήμα 3: Εισαγωγή πεδίου φόρμας command button

Το Aspose.Words εκθέτει την κλάση `Forms2OleControl` για ελέγχους φόρμας OLE. Για **insert command button word** πεδία φόρμας, καλέστε `insertForms2OleControl` με την τιμή enum `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Η μέθοδος επιστρέφει ένα αντικείμενο `Forms2OleControl` που μπορούμε να διαμορφώσουμε πριν από την αποθήκευση.

## Βήμα 4: Ορισμός μεγέθους και θέσης του κουμπιού

Ένα command button χρειάζεται ρητές διαστάσεις και θέση στη σελίδα. Προσαρμόστε το πλάτος, το ύψος και τις συντεταγμένες ώστε να ταιριάζουν με τη διάταξή σας.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Η λεπτομερής ρύθμιση αυτών των τιμών εξασφαλίζει ότι το κουμπί εμφανίζεται ακριβώς όπου το θέλετε στο τελικό έγγραφο.

## Βήμα 5: **Set command button caption**

Το ορατό κείμενο στο κουμπί ελέγχεται από τη μέθοδο `setCaption`. Εδώ **set command button caption** για να καθοδηγήσετε τον χρήστη.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Μπορείτε να αντικαταστήσετε το `"Click Me"` με οποιαδήποτε ετικέτα ταιριάζει με την πρόθεση της φόρμας σας, όπως `"Submit"` ή `"Approve"`.

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Το παραγόμενο αρχείο περιέχει το διαδραστικό κουμπί και μπορεί να ανοιχθεί στο Microsoft Word ή στο LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `CommandButtonDemo.docx`. Ανοίγοντάς το στο Word εμφανίζεται ένα κουμπί με την ετικέτα **Click Me** τοποθετημένο 50 pts από αριστερά και 100 pts από την κορυφή της σελίδας.

### Αναμενόμενο αποτέλεσμα

- Ένα αρχείο `.docx` με όνομα `CommandButtonDemo.docx`.
- Το έγγραφο περιέχει μία σελίδα με ένα πεδίο φόρμας command button.
- Το κουμπί εμφανίζει την ετικέτα που ορίσατε (π.χ., **Click Me**).

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Πώς να προσαρμόσετε |
|-----------|--------------------|
| **Πολλαπλά κουμπιά** | Καλέστε το `insertForms2OleControl` επανειλημμένα, προσαρμόζοντας τα `setLeft`/`setTop` για κάθε νέο κουμπί. |
| **Διαφορετική ετικέτα ανά κουμπί** | Χρησιμοποιήστε το `setCaption` με μια μοναδική συμβολοσειρά μετά από κάθε εισαγωγή. |
| **Κουμπί μέσα σε κελί πίνακα** | Μετακινήστε τον κέρσορα στο επιθυμητό κελί με `builder.moveTo(cell.getFirstParagraph())` πριν την εισαγωγή του ελέγχου. |
| **Παλαιές μορφές Word (.doc)** | Αποθηκεύστε χρησιμοποιώντας `doc.save("Demo.doc", SaveFormat.DOC);` – το command button διατηρείται. |
| **Φόρμες μόνο για ανάγνωση** | Μετά την εισαγωγή, ορίστε `commandButton.setEnabled(false);` για να αποτρέψετε την αλληλεπίδραση του χρήστη. |

## Συμβουλές για μια αξιόπιστη υλοποίηση

- **Επικύρωση διαστάσεων**: Πολύ μεγάλα πλάτη μπορεί να προκαλέσουν υπερχείλιση του κουμπιού πέρα από το περιθώριο της σελίδας.
- **Επιβολή άδειας**: Χωρίς έγκυρη άδεια, το Aspose.Words προσθέτει υδατογράφημα στο παραγόμενο έγγραφο. Εφαρμόστε την άδειά σας νωρίς με `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Δοκιμή**: Ανοίξτε το παραγόμενο αρχείο στο Word και ενεργοποιήστε το **Design Mode** (Developer → Design Mode) για να δείτε τις ιδιότητες του κουμπιού.

## Ανασκόπηση πλήρους κώδικα

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Αντιγράψτε τον κώδικα σε ένα αρχείο με όνομα `InsertCommandButtonDemo.java`, μεταγλωττίστε με Maven (`mvn compile`) και εκτελέστε (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Το παραγόμενο έγγραφο θα εμφανιστεί στο ριζικό φάκελο του έργου σας.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create form field button** σε Word χρησιμοποιώντας το Aspose.Words for Java, πώς να **insert command button word** πεδία φόρμας και πώς να **set command button caption** προγραμματιστικά. Αυτό το ολοκληρωμένο παράδειγμα σας παρέχει μια ισχυρή βάση για τη δημιουργία πιο πλούσιων, διαδραστικών εγγράφων Word — είτε χρειάζεστε ένα μόνο κουμπί υποβολής είτε μια πλήρη σειρά ελέγχων φόρμας.

### Τι θα ακολουθήσει;

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Προσθήκη πεδίου φόρμας Combo Box σε έγγραφο Word με Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Προσθήκη πεδίου φόρμας Check Box σε έγγραφο Word με Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}