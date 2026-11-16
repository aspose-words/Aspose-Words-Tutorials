---
category: general
date: 2026-11-15
description: Επεξεργαστείτε το έγγραφο Word προγραμματιστικά για να εισάγετε ένα κουμπί
  εντολής. Μάθετε πώς να προσθέσετε κουμπί, να ορίσετε το όνομα του κουμπιού εντολής
  και να δημιουργήσετε κουμπί φόρμας στο Word σε λίγα λεπτά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: el
lastmod: 2026-11-15
og_description: Επεξεργαστείτε το έγγραφο Word προγραμματιστικά και εισάγετε ένα κουμπί
  εντολής. Αυτός ο οδηγός δείχνει πώς να προσθέσετε κουμπί, να ορίσετε το όνομα του
  κουμπιού εντολής και να δημιουργήσετε γρήγορα ένα κουμπί φόρμας στο Word.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Επεξεργασία εγγράφου Word προγραμματιστικά – προσθήκη κουμπιού εντολής
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Επεξεργασία εγγράφου Word προγραμματιστικά και προσθήκη κουμπιού εντολής
url: /el/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Επεξεργασία εγγράφου Word προγραμματιστικά και προσθήκη κουμπιού εντολής

Αν χρειάζεστε να **επεξεργαστείτε ένα έγγραφο Word προγραμματιστικά**, ο πιο γρήγορος τρόπος είναι να χρησιμοποιήσετε το Aspose.Words API. Αυτό το tutorial σας δείχνει ακριβώς **πώς να προσθέσετε κουμπιά** ελέγχου, να ρυθμίσετε τη λεζάντα τους και **να ορίσετε το όνομα του κουμπιού εντολής** ώστε το έγγραφο να λειτουργεί ως απλή φόρμα. Στο τέλος θα έχετε ένα πλήρως επεξεργάσιμο *.docx* που περιέχει ένα λειτουργικό κουμπί εντολής έτοιμο για επεξεργασία downstream.

Θα μάθετε πώς να **εισάγετε τη λέξη κουμπιού εντολής**, **δημιουργήσετε τη λέξη κουμπιού φόρμας**, και να διαχειριστείτε τις ιδιότητες του κουμπιού χωρίς να ανοίξετε το Word χειροκίνητα. Η μόνη προαπαιτούμενη προϋπόθεση είναι ένα βασικό περιβάλλον ανάπτυξης Java και η βιβλιοθήκη Aspose.Words for Java.

## Προαπαιτούμενα

- Java 17 ή νεότερη (ο κώδικας λειτουργεί επίσης με Java 8+)
- Aspose.Words for Java (λήψη από [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Ένα υπάρχον έγγραφο Word (`input.docx`) που θέλετε να τροποποιήσετε
- Εξοικείωση με Maven ή Gradle για την προσθήκη της εξάρτησης Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Βήμα 1: Φόρτωση του εγγράφου Word

Η πρώτη ενέργεια όταν **επεξεργάζεστε ένα έγγραφο Word προγραμματιστικά** είναι να φορτώσετε το αρχείο προέλευσης σε ένα αντικείμενο `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη, επιτρέποντάς σας να χειριστείτε το περιεχόμενό του.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου δημιουργεί μια δομή τύπου DOM που το Aspose.Words μπορεί να διασχίσει και να τροποποιήσει. Η παράλειψη αυτού του βήματος θα σας αφήσει χωρίς στόχο για την εισαγωγή του κουμπιού.

## Βήμα 2: Δημιουργία ενός `DocumentBuilder` για την επεξεργασία του εγγράφου

Ένας `DocumentBuilder` λειτουργεί σαν κέρσορας μέσα στο αρχείο Word. Σας επιτρέπει να εισάγετε κείμενο, εικόνες και στοιχεία φόρμας στην τρέχουσα θέση.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Συμβουλή:** Εάν χρειάζεστε το κουμπί σε μια συγκεκριμένη παράγραφο, μετακινήστε πρώτα τον builder με `builder.moveToParagraph(index, true);`.

## Βήμα 3: Εισαγωγή ενός Forms2OleControl (κουμπί εντολής)

Τώρα απαντάμε στο κεντρικό ερώτημα **πώς να προσθέσετε κουμπί** σε ένα αρχείο Word. Η μέθοδος `insertForms2OleControl()` δημιουργεί ένα κληροδοτημένο κουμπί εντολής *Forms2.0*, το οποίο είναι ο πιο συμβατός έλεγχος σε όλες τις εκδόσεις του Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Ακραία περίπτωση:** Ο έλεγχος Forms2.0 είναι ορατός μόνο στη *Λειτουργία Σχεδίασης* του Word. Εάν χρειάζεστε ένα νεότερο κουμπί ActiveX, σκεφτείτε το `insertOleControl()` αντί αυτού, αλλά ο κληροδοτημένος έλεγχος λειτουργεί για τις περισσότερες περιπτώσεις αυτοματοποίησης.

## Βήμα 4: Διαμόρφωση των ιδιοτήτων του κουμπιού

Μετά την εισαγωγή του ελέγχου, μπορείτε να **ορίσετε το όνομα του κουμπιού εντολής** και να **εισάγετε τη λέξη κουμπιού εντολής** (λεζάντα) ώστε να είναι φιλικό προς το χρήστη.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Γιατί αυτές οι ιδιότητες;**  
> - `setName` δίνει στο κουμπί ένα αναγνωριστικό που μπορεί να αναφερθεί από VBA ή εξωτερικά εργαλεία.  
> - `setCaption` είναι η ορατή ετικέτα, ουσιαστικά **δημιουργώντας τη λέξη κουμπιού φόρμας** που κάνουν κλικ οι τελικοί χρήστες.

Μπορείτε επίσης να προσαρμόσετε το μέγεθος, τη θέση ή να προσθέσετε μια μακροεντολή προσπερνώντας το υποκείμενο αντικείμενο OLE, αλλά αυτά τα θέματα υπερβαίνουν το πεδίο αυτού του γρήγορου οδηγού.

## Βήμα 5: Αποθήκευση του τροποποιημένου εγγράφου

Τέλος, αποθηκεύστε τις αλλαγές σε ένα νέο αρχείο. Αυτό το βήμα **δημιουργεί τη λέξη κουμπιού φόρμας** στο αρχείο εξόδου.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Αποτέλεσμα:** Ανοίγοντας το `output.docx` στο Microsoft Word, θα δείτε ένα κουμπί με την ετικέτα “Submit”. Όταν μεταβείτε στο Word στη *Λειτουργία Σχεδίασης* (Developer → Design Mode), μπορείτε να κάνετε διπλό‑κλικ στο κουμπί για να επισυνάψετε μια μακροεντολή ή απλώς να το χρησιμοποιήσετε ως placeholder σε μια φόρμα.

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το αποθηκευμένο αρχείο:

- Το σημείο εισαγωγής του κέρσορα αντικαθίσταται από ένα κουμπί.
- Το κουμπί εμφανίζει τη λεζάντα **Submit**.
- Το εσωτερικό όνομα του κουμπιού είναι **cmdSubmit**, το οποίο μπορείτε να αναφέρετε σε VBA ή εξωτερικά σενάρια αυτοματοποίησης.

## Συχνές ερωτήσεις και παραλλαγές

### Πώς να προσθέσετε κουμπί σε μια συγκεκριμένη παράγραφο;

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Πώς να εισάγετε ένα κουμπί μέσα σε κελί πίνακα;

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Τι κάνω αν χρειάζομαι μεγαλύτερο κουμπί;

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Πώς να **εισάγετε τη λέξη κουμπιού εντολής** χρησιμοποιώντας διαφορετική γλώσσα (π.χ., C#);

Η ίδια λογική ισχύει· αντικαταστήστε τη σύνταξη Java με ισοδύναμα C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Επαγγελματικές συμβουλές και παγίδες

- **Pro tip:** Πάντα καλέστε `builder.moveToDocumentEnd()` πριν εισάγετε ένα κουμπί αν θέλετε να βρίσκεται στο πολύ τέλος του εγγράφου.  
- **Προσοχή:** Η αποθήκευση στο ίδιο αρχείο που ανοίξατε μπορεί να καταστρέψει το έγγραφο εάν προκύψει εξαίρεση. Χρησιμοποιήστε ξεχωριστό μονοπάτι εξόδου όπως φαίνεται.  
- **Συμβατότητα:** Το κληροδοτημένο κουμπί Forms2.0 λειτουργεί σε Word 2007‑2021. Για Word στο web, σκεφτείτε τη χρήση ελέγχων περιεχομένου αντί αυτού.  
- **Απόδοση:** Η φόρτωση πολύ μεγάλων εγγράφων (>100 MB) μπορεί να καταναλώσει σημαντική μνήμη. Χρησιμοποιήστε `Document.load(InputStream, LoadOptions)` με `LoadOptions.setLoadFormat(LoadFormat.DOCX)` για περιορισμό της χρήσης πόρων.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα Java. Αντιγράψτε το σε μια κλάση με όνομα `WordButtonDemo.java`, προσαρμόστε τις διαδρομές αρχείων και εκτελέστε `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Εκτελέστε το πρόγραμμα και ανοίξτε το `output.docx` για να επαληθεύσετε ότι το κουμπί εμφανίζεται όπως αναμένεται.

## Συμπέρασμα

Τώρα ξέρετε πώς να **επεξεργαστείτε ένα έγγραφο Word προγραμματιστικά** για να **εισάγετε τη λέξη κουμπιού εντολής**, **δημιουργήσετε τη λέξη κουμπιού φόρμας**, και **ορίσετε το όνομα του κουμπιού εντολής** χρησιμοποιώντας το Aspose.Words for Java. Αυτή η προσέγγιση εξαλείφει την χειροκίνητη επεξεργασία, επιτρέπει την επεξεργασία πολλαπλών φορμών και ενσωματώνεται άψογα σε αυτοματοποιημένες ροές εργασίας.

Επόμενα, μπορείτε να εξερευνήσετε:

- Προσθήκη μακροεντολών VBA στο κουμπί (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Χρήση **ελέγχων περιεχομένου** για πιο πλούσιες εμπειρίες φόρμας (`builder.insertCheckBox()` κ.λπ.)  
- Αυτοματοποίηση μαζικής εισαγωγής σε πολλαπλά έγγραφα με βρόχο  

Νιώστε ελεύθεροι να πειραματιστείτε με το μέγεθος, τη θέση και τη διαχείριση συμβάντων του κουμπιού ώστε να ταιριάζει στο συγκεκριμένο σενάριό σας. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}