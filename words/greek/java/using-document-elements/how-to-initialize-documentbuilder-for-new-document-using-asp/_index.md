---
category: general
date: 2026-10-04
description: Μάθετε πώς να αρχικοποιήσετε το DocumentBuilder για νέο έγγραφο και να
  προσθέσετε ένα κουμπί ActiveX με το Aspose.Words σε Java. Οδηγός βήμα‑προς‑βήμα
  με πλήρες κώδικα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: el
lastmod: 2026-10-04
og_description: Αρχικοποιήστε το DocumentBuilder για νέο έγγραφο και ενσωματώστε ένα
  κουμπί εντολής ActiveX χρησιμοποιώντας το Aspose.Words Java API. Ακολουθήστε αυτόν
  τον σύντομο οδηγό.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Αρχικοποίηση του DocumentBuilder για νέο έγγραφο – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Πώς να αρχικοποιήσετε το DocumentBuilder για νέο έγγραφο χρησιμοποιώντας το
  Aspose.Words
url: /el/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αρχικοποιήσετε το DocumentBuilder για νέο έγγραφο χρησιμοποιώντας το Aspose.Words

Αν χρειάζεστε να **initialize DocumentBuilder for new document** σε ένα έργο Java, αυτό το tutorial σας δείχνει τα ακριβή βήματα. Θα δείτε πώς να δημιουργήσετε ένα κενό αρχείο Word, να προσθέσετε ένα κουμπί ActiveX command button και να αποθηκεύσετε το αποτέλεσμα — όλα με ένα ενιαίο, αυτόνομο δείγμα κώδικα.

Η εργασία με έγγραφα Word προγραμματιστικά συχνά σημαίνει διαχείριση λεπτομερειών χαμηλού επιπέδου όπως τα στοιχεία φόρμας. Στο τέλος αυτού του οδηγού θα μπορείτε να ενσωματώσετε ένα κουμπί ActiveX χωρίς να αφήσετε το IDE σας, κάτι που είναι χρήσιμο για τη δημιουργία προτύπων, αυτοματοποιημένων αναφορών ή διαδραστικών φορμών.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη έκδοση εγκατεστημένη  
* Maven 3.8+ (ή Gradle αν προτιμάτε)  
* Άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για δοκιμές)  
* Βασική εξοικείωση με τη σύνταξη της Java  

Αν είστε νέοι στο Aspose.Words, η βιβλιοθήκη παρέχει ένα υψηλού επιπέδου API για δημιουργία, επεξεργασία και αποθήκευση εγγράφων Word. Η κλάση `DocumentBuilder` είναι το κύριο σημείο εισόδου για την κατασκευή του περιεχομένου του εγγράφου.

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα νέο έργο Maven (ή προσθέστε σε υπάρχον) και συμπεριλάβετε την εξάρτηση Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Συμβουλή:** Διατηρήστε την έκδοση της βιβλιοθήκης ενημερωμένη· οι νεότερες εκδόσεις προσθέτουν υποστήριξη για επιπλέον στοιχεία φόρμας και βελτιώνουν την απόδοση.

## Βήμα 2: Αρχικοποίηση του `DocumentBuilder` για νέο έγγραφο

Ο πυρήνας του tutorial είναι η λειτουργία **initialize DocumentBuilder for new document**. Πρώτα δημιουργείτε μια κενή παρουσία `Document`, στη συνέχεια τη περνάτε στον κατασκευαστή του `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό:* Η αρχικοποίηση του `DocumentBuilder` συνδέει τον builder με ένα συγκεκριμένο αντικείμενο `Document`, επιτρέποντάς σας να προσθέτετε παραγράφους, πίνακες ή στοιχεία φόρμας απευθείας σε αυτό το έγγραφο. Χωρίς αυτό το βήμα, ο builder δεν θα είχε στόχο για εργασία.

## Βήμα 3: Εισαγωγή ελέγχου κουμπιού ActiveX command button

Το Aspose.Words εκθέτει την κλάση `Forms2OleControl` για την ενσωμάτωση παλαιών ελέγχων ActiveX. Ο παρακάτω κώδικας προσθέτει ένα **Forms2OleControl command button** στη τρέχουσα θέση του δρομέα.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Τι είναι ένα κουμπί ActiveX command button;

Ένα κουμπί ActiveX command button είναι ένα παλαιό στοιχείο UI που μπορεί να εκτελεί μακροεντολές ή να ενεργοποιεί γεγονότα όταν ο χρήστης το κάνει κλικ μέσα σε ένα έγγραφο Word. Αν και οι σύγχρονες εκδόσεις του Office προτιμούν τα Content Controls, πολλά εταιρικά πρότυπα εξακολουθούν να βασίζονται στο ActiveX για συμβατότητα με παλαιότερες εκδόσεις.

## Βήμα 4: Αποθήκευση του εγγράφου

Αφού εισάγετε το στοιχείο, απλώς καλείτε τη μέθοδο `save`. Το αρχείο θα περιέχει το κουμπί ActiveX και μπορεί να ανοίξει στο Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Όταν ανοίξετε το `ActiveXButton.docx` στο Word, θα δείτε ένα κουμπί με την ετικέτα **Click Me**. Το κλικ στο κουμπί δεν θα κάνει τίποτα εκτός αν συνδέσετε μια μακροεντολή, αλλά το ίδιο το στοιχείο λειτουργεί πλήρως.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο `src/main/java/com/example/ActiveXButtonDemo.java`. Περιλαμβάνει όλες τις εισαγωγές και τη διαχείριση σφαλμάτων που χρειάζονται για μια γρήγορη δοκιμή.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
Document saved to output/ActiveXButton.docx
```

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word 2016 ή νεότερο· θα πρέπει να δείτε ένα κουμπί με την ετικέτα *Click Me* τοποθετημένο στην κορυφή της πρώτης σελίδας.

## Συνηθισμένες παραλλαγές και περιπτώσεις άκρων

| Σενάριο | Προσαρμογή |
|----------|------------|
| **Add the button to a specific paragraph** | Μετακινήστε τον δρομέα του builder με `builder.moveToParagraph(index, NodeType.PARAGRAPH);` πριν καλέσετε το `insertForms2OleControl`. |
| **Set button size** | Χρησιμοποιήστε `commandButton.setWidth(100);` και `commandButton.setHeight(30);` για να ορίσετε τις διαστάσεις σε points. |
| **Add a macro to the button** | Μετά την αποθήκευση του εγγράφου, ανοίξτε το στο Word, ενεργοποιήστε την καρτέλα Developer και συνδέστε χειροκίνητα μια μακροεντολή VBA στο κουμπί (τα στοιχεία ActiveX δεν μπορούν να προγραμματιστούν απευθείας από το Aspose.Words). |
| **Target .doc (binary) format** | Αλλάξτε `doc.save(outputPath, SaveFormat.DOC);` για να παραγάγετε ένα παλαιό αρχείο Word 97‑2003. |
| **Run on Android** | Χρησιμοποιήστε το Aspose.Words for Android μέσω του Java API του· ο ίδιος κώδικας λειτουργεί εφόσον η βιβλιοθήκη περιλαμβάνεται στο APK. |

## Συμβουλές αντιμετώπισης προβλημάτων

* **`java.lang.NoClassDefFoundError`** – Βεβαιωθείτε ότι το JAR του Aspose.Words βρίσκεται στο classpath. Το Maven το προσθέτει αυτόματα· για χειροκίνητες κατασκευές, τοποθετήστε το JAR στο `libs/` και προσθέστε το στις βιβλιοθήκες του IDE σας.  
* **Button does not appear in Word** – Ελέγξτε ότι η επιλογή *Show legacy forms* είναι ενεργοποιημένη στο Trust Center του Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **License exception** – Αν εκτελέσετε τον κώδικα χωρίς έγκυρη άδεια, το Aspose.Words θα προσθέσει υδατογράφημα. Καταχωρήστε μια δωρεάν δοκιμή ή αγοράστε άδεια για να το αφαιρέσετε.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **initialize DocumentBuilder for new document**, να εισάγετε ένα κουμπί ActiveX command button και να αποθηκεύσετε το αποτέλεσμα με το Aspose.Words for Java. Αυτό το μοτίβο σας επιτρέπει να δημιουργείτε διαδραστικά πρότυπα Word προγραμματιστικά, κάτι που είναι ιδιαίτερα χρήσιμο για αυτοματοποιημένες αναφορές ή ροές εργασίας βασισμένες σε φόρμες.

Από εδώ μπορείτε να εξερευνήσετε πρόσθετα στοιχεία φόρμας (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, κ.λπ.), να συνδυάσετε το κουμπί με προσαρμοσμένες μακροεντολές VBA ή να δημιουργήσετε πλήρη έγγραφα που περιλαμβάνουν πίνακες, εικόνες και στυλ — όλα χρησιμοποιώντας την ίδια ροή εργασίας του `DocumentBuilder`.

---

*Έτοιμοι να δημιουργήσετε πιο σύνθετη αυτοματοποίηση Word; Δείτε τους οδηγούς μας για **insert table with DocumentBuilder**, **apply styles programmatically**, και **export to PDF with Aspose.Words**.*

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας το DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Πώς να αποθηκεύσετε ένα έγγραφο ως PDF με το Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Προσθήκη υδατογραφήματος σε έγγραφο χρησιμοποιώντας το Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}