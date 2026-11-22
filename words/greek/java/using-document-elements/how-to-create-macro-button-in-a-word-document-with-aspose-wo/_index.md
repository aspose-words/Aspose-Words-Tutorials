---
category: general
date: 2026-11-22
description: Δημιουργήστε κουμπί μακροεντολής σε ένα έγγραφο Word χρησιμοποιώντας
  Java. Μάθετε πώς να εισάγετε κουμπί εντολής, να ορίσετε το κείμενο του κουμπιού
  και να συνδέσετε τη μακροεντολή με το κουμπί για διαδραστικά έγγραφα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: el
lastmod: 2026-11-22
og_description: Δημιουργήστε κουμπί μακροεντολής σε έγγραφο Word χρησιμοποιώντας Java.
  Αυτό το σεμινάριο δείχνει πώς να εισαγάγετε κουμπί εντολής, να ορίσετε το κείμενο
  του κουμπιού και να συνδέσετε τη μακροεντολή με το κουμπί για πλήρη διαδραστικότητα.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Δημιουργήστε ένα κουμπί μακροεντολής σε έγγραφο Word με Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Πώς να δημιουργήσετε κουμπί μακροεντολής σε ένα έγγραφο Word με το Aspose.Words
  για Java
url: /el/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κουμπί macro σε έγγραφο Word με Aspose.Words for Java

Αν χρειάζεστε **να δημιουργήσετε κουμπί macro** σε αρχείο Word, αυτός ο οδηγός σας καθοδηγεί βήμα‑βήμα στις ακριβείς ενέργειες που απαιτούνται. Θα μάθετε πώς να **εισάγετε κουμπί εντολής**, **ορίσετε το κείμενο του κουμπιού** και **συνδέσετε macro στο κουμπί** ώστε το έγγραφο να γίνει πλήρως διαδραστικό.

Οι προγραμματιστές συχνά ενσωματώνουν ελέγχους OLE για να ενεργοποιήσουν VBA macros από μέσα σε ένα έγγραφο. Αυτό το tutorial καλύπτει ολόκληρη τη ροή εργασίας, από τη ρύθμιση του έργου μέχρι ένα εκτελέσιμο παράδειγμα Java που προσθέτει ένα **διαδραστικό κουμπί** σε αρχείο .docx. Δεν απαιτούνται εξωτερικά σενάρια—όλα εκτελούνται μέσα στη διαδικασία Java.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* JDK 17 ή νεότερο εγκατεστημένο.  
* Maven 3.8+ (ή Gradle) για διαχείριση εξαρτήσεων.  
* Aspose.Words for Java 23.9 ή νεότερο – η βιβλιοθήκη παρέχει το `DocumentBuilder` και τα API ελέγχου OLE.  
* Βασική εξοικείωση με Java και VBA macros.

Αν λείπει κάποιο από τα παραπάνω, εγκαταστήστε το πρώτα· το υπόλοιπο tutorial υποθέτει ότι είναι διαθέσιμο.

## Πώς να δημιουργήσετε κουμπί macro με Aspose.Words for Java

Ο πυρήνας της λύσης αποτελείται από τέσσερις ενέργειες:

1. **Εισαγωγή κουμπιού εντολής** OLE control στο έγγραφο.  
2. **Ορισμός κειμένου κουμπιού** (caption) που βλέπει ο χρήστης.  
3. **Σύνδεση macro στο κουμπί** ώστε το κλικ να εκτελεί τη ζητούμενη VBA ρουτίνα.  
4. **Αποθήκευση του εγγράφου** με το ενσωματωμένο macro.

Κάθε ενέργεια εξηγείται στην αντίστοιχη ενότητα παρακάτω.

### Βήμα 1: Εισαγωγή κουμπιού εντολής στο έγγραφο

`DocumentBuilder.insertForms2OleControl` δημιουργεί έναν έλεγχο OLE του συγκεκριμένου τύπου. Η σταθερά `Forms2OleControlType.COMMAND_BUTTON` λέει στο Aspose.Words να δημιουργήσει ένα κουμπί εντολής που μπορεί να φιλοξενήσει macro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Γιατί είναι σημαντικό:** Ο έλεγχος OLE λειτουργεί ως δοχείο για το macro. Χωρίς την εισαγωγή του, δεν υπάρχει οπτικό στοιχείο για κλικ από τον χρήστη.

### Βήμα 2: Ορισμός κειμένου κουμπιού (caption)

Η λεζάντα είναι η ορατή ετικέτα του κουμπιού. Χρησιμοποιήστε `setCaption` για να ορίσετε τι βλέπει ο χρήστης.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Γιατί είναι σημαντικό:** Καθαρό κείμενο κουμπιού βελτιώνει τη χρηστικότητα. Η μέθοδος `setCaption` ενημερώνει την ιδιότητα `Caption` του ελέγχου OLE, την οποία το Word αποδίδει ως ετικέτα του κουμπιού.

### Βήμα 3: Σύνδεση macro στο κουμπί

Ένα macro προσδιορίζεται από το όνομά του, π.χ. `MyMacro`. Η μέθοδος `setOnClick` αποθηκεύει αυτό το όνομα στον χειριστή συμβάντος `OnClick` του κουμπιού.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Γιατί είναι σημαντικό:** Η σύνδεση macro δημιουργεί τη διαδραστική συμπεριφορά. Όταν ο χρήστης κάνει κλικ στο κουμπί στο Word, εκτελείται η σχετική VBA ρουτίνα.

### Βήμα 4: Προσθήκη διαδραστικού κουμπιού σε έγγραφο Word

Αφού διαμορφώσετε τον έλεγχο OLE, ίσως θέλετε να τον τοποθετήσετε, να αλλάξετε το μέγεθός του ή να προσθέσετε κείμενο γύρω του. Ο `DocumentBuilder` συνεχίζει να λειτουργεί στο έγγραφο, ώστε να μπορείτε να εισάγετε παραγράφους πριν ή μετά το κουμπί.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Γιατί είναι σημαντικό:** Η αποθήκευση ως `.docm` διατηρεί τον κώδικα macro. Αν αποθηκεύσετε ως `.docx`, η αναφορά στο macro χάνεται.

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα Java, με εισαγωγές, διαχείριση εξαιρέσεων και σχόλια που εξηγούν κάθε βήμα. Αντιγράψτε τον κώδικα σε ένα έργο Maven με την εξάρτηση Aspose.Words και εκτελέστε το.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος δημιουργεί το `MacroButtonDemo.docm`. Ανοίγοντας το αρχείο στο Microsoft Word εμφανίζεται:

* Μια παράγραφος που γράφει *«Πατήστε το κουμπί για να εκτελέσετε το macro:”*.
* Ένα κουμπί με την ετικέτα **Run Report** ακριβώς κάτω από την παράγραφο.
* Όταν κάνετε κλικ στο κουμπί, το Word προσπαθεί να εκτελέσει το macro `MyMacro`. (Πρέπει να προσθέσετε τον πραγματικό κώδικα VBA στο έγγραφο χειροκίνητα ή μέσω άλλου βήματος αυτοματοποίησης.)

Αν το macro δεν υπάρχει, το Word εμφανίζει προειδοποίηση ασφαλείας, που είναι η τυπική συμπεριφορά για έγγραφα με ενεργοποιημένα macros.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|-------------------------------|
| **Διαφορετική λεζάντα κουμπιού** | Αλλάξτε τη συμβολοσειρά που περνάτε στο `setCaption`. |
| **Πολλαπλά κουμπιά** | Καλέστε επανειλημμένα το `insertForms2OleControl`, καθένα με το δικό του `setCaption` και `setOnClick`. |
| **Προσαρμοσμένα ονόματα macro** | Αντικαταστήστε το `"MyMacro"` με οποιοδήποτε έγκυρο όνομα διαδικασίας VBA, π.χ. `"ExportToExcel"`. |
| **Περιορισμοί μεγέθους κουμπιού** | Προσαρμόστε τις τιμές `setWidth` και `setHeight`; το Word τηρεί τα σημεία που παρέχετε. |
| **Ενσωμάτωση macro προγραμματιστικά** | Χρησιμοποιήστε `Document.getBuiltInDocumentProperties().add("Macros", …)` ή ξεχωριστό βήμα εισαγωγής VBA· το Aspose.Words δεν γράφει κώδικα VBA αυτόματα. |

**Pro tip:** Δοκιμάστε πάντα το παραγόμενο `.docm` σε μηχάνημα με ρυθμίσεις ασφαλείας macro στο *Enable all macros* για ανάπτυξη. Σε παραγωγή, υπογράψτε το macro με πιστοποιητικό εμπιστοσύνης για να αποφύγετε προειδοποιήσεις ασφαλείας.

## Λίστα ελέγχου αντιμετώπισης προβλημάτων

* **Το κουμπί δεν εμφανίζεται** – Βεβαιωθείτε ότι το έγγραφο αποθηκεύεται ως `.docm` και ανοίγεται σε έκδοση Word που υποστηρίζει ελέγχους OLE.  
* **Το macro δεν εκτελείται** – Ελέγξτε ότι το όνομα του macro ταιριάζει ακριβώς, συμπεριλαμβανομένου του κεφαλαίου, και ότι το macro υπάρχει στο VBA project του εγγράφου.  
* **Η λεζάντα του κουμπιού περικόπτεται** – Αυξήστε το πλάτος του κουμπιού με `setWidth` ώστε να χωράει το κείμενο.  
* **Απρόσμενη μετατόπιση διάταξης** – Χρησιμοποιήστε `builder.moveTo` για ακριβή τοποθέτηση του κέρσορα πριν την εισαγωγή του ελέγχου.  

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κουμπί macro** σε έγγραφο Word χρησιμοποιώντας Java, **να εισάγετε κουμπί εντολής**, **να ορίσετε το κείμενο του κουμπιού** και **να συνδέσετε macro στο κουμπί** για πλήρη διαδραστικότητα. Το πλήρες παράδειγμα δείχνει κάθε απαιτούμενη κλήση API, εξηγεί γιατί κάθε βήμα είναι σημαντικό και παρέχει οδηγίες για κοινές παραλλαγές.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* **Προσθήκη διαδραστικού κουμπιού** σε υπάρχοντα πρότυπα αντί για νέο έγγραφο.  
* **Προγραμματιστική ένεση κώδικα VBA** χρησιμοποιώντας το Open XML SDK ή ένα δευτερεύον εργαλείο αυτοματοποίησης.  
* **Συνδυασμός πολλαπλών ελέγχων OLE** (checkboxes, list boxes) για δημιουργία πλούσιων φορμών.

Πειραματιστείτε με διαφορετικές λεζάντες, ονόματα macro και μεγέθη κουμπιών ώστε να ταιριάζουν στην περίπτωσή σας. Καλή προγραμματιστική δουλειά!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές υλοποιήσεις στα δικά σας έργα.

- [How to insert command button in a Word document using Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [How to set button position in a Word document with Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}