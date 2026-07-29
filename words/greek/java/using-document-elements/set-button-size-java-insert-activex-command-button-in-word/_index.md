---
category: general
date: 2026-07-29
description: 'Οδηγός Java για ορισμό μεγέθους κουμπιού: μάθετε πώς να εισάγετε κουμπί
  εντολών ActiveX σε έγγραφο Word χρησιμοποιώντας Java και Aspose.Words, καθώς και
  πώς να ρυθμίσετε το μέγεθος και να δημιουργήσετε κενό έγγραφο.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: el
lastmod: 2026-07-29
og_description: Ο οδηγός set button size java δείχνει πώς να εισάγετε ένα κουμπί εντολής
  ActiveX σε αρχείο Word χρησιμοποιώντας Java, να προσαρμόσετε το μέγεθός του και
  να αποθηκεύσετε το έγγραφο προγραμματιστικά.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Ορισμός μεγέθους κουμπιού σε Java – Προσθήκη κουμπιού εντολής ActiveX στο
  Word με Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: ορισμός μεγέθους κουμπιού java – Εισαγωγή κουμπιού εντολής ActiveX στο Word
url: /el/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Εισαγωγή κουμπιού εντολής ActiveX στο Word

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε το μέγεθος του κουμπιού java** όταν αυτοματοποιείτε έγγραφα Word; Ίσως δημιουργείτε ένα εργαλείο αναφοράς που χρειάζεται ένα κλικ‑βασισμένο κουμπί “Submit” μέσα στο αρχείο .docx. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — δημιουργία ενός κεντρικού εγγράφου Word, εισαγωγή ενός κουμπιού εντολής ActiveX και ρητή ρύθμιση του πλάτους και του ύψους — όλα με Java και Aspose.Words.

Θα απαντήσουμε επίσης στην επίμονη ερώτηση “πώς να εισάγετε activex” που εμφανίζεται σε πολλούς προγραμματιστές. Στο τέλος θα έχετε ένα εκτελέσιμο πρόγραμμα που παράγει ένα αρχείο Word με ένα τέλεια διαστασιοποιημένο κουμπί εντολής, έτοιμο για περαιτέρω προσαρμογές.

---

## Τι Θα Χρειαστείτε

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

- **Java Development Kit (JDK) 8 ή νεότερο** – ο κώδικας μεταγλωττίζεται με οποιοδήποτε πρόσφατο JDK.  
- **Aspose.Words for Java** (η πιο πρόσφατη έκδοση μέχρι τον Ιούλιο 2026). Κατεβάστε το JAR από την [Aspose website](https://products.aspose.com/words/java) ή μέσω Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Ένα IDE ή απλός επεξεργαστής κειμένου — IntelliJ IDEA, Eclipse ή VS Code αρκούν.  
- Έναν φάκελο όπου θέλετε να αποθηκευτεί το **CommandButton.docx**.

Αυτό είναι όλο. Χωρίς πρόσθετες βιβλιοθήκες Office interop, χωρίς κόλπα COM, μόνο καθαρή Java.

---

## Υλοποίηση Βήμα‑Βήμα

Θα χωρίσουμε τη λύση σε πέντε λογικά βήματα. Κάθε βήμα έχει τη δική του επικεφαλίδα H2· ένα από αυτά περιέχει τη **κύρια λέξη‑κλειδί** για SEO.

### 1. Ρύθμιση του Project και Εισαγωγή Aspose.Words

Πρώτα, δημιουργήστε ένα νέο Maven (ή Gradle) project και προσθέστε την εξάρτηση Aspose.Words όπως φαίνεται παραπάνω. Στη συνέχεια, εισάγετε τις απαιτούμενες κλάσεις στο αρχείο Java:

```java
import com.aspose.words.*;
```

> **Pro tip:** Αν χρησιμοποιείτε IDE, αφήστε το να κάνει αυτό‑ματη εισαγωγή των κλάσεων. Εξοικονομεί πολύ χρόνο και αποτρέπει τυπογραφικά λάθη.

### 2. java create blank word Document

Τώρα δημιουργούμε πραγματικά **java create blank word** έγγραφο. Αυτό είναι το θεμέλιο πάνω στο οποίο θα εισάγουμε αργότερα το **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη. Σε αυτό το σημείο το αρχείο δεν έχει σελίδες, κείμενο — μόνο ένα καθαρό καμβά.

### 3. Αρχικοποίηση DocumentBuilder και Εισαγωγή του ActiveX Control

Το `DocumentBuilder` είναι ένας βοηθός που μας επιτρέπει να προσθέτουμε περιεχόμενο, παραγράφους, πίνακες και, ναι, ελέγχους ActiveX. Εδώ απαντάμε στο **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

Το `Forms2OleControl` είναι το wrapper της Aspose γύρω από ένα αντικείμενο OLE. Καθορίζοντας `COMMANDBUTTON` λέμε στο Word να ενσωματώσει ένα κλασικό κουμπί εντολής ActiveX.

### 4. How to Set Button Size Java – Προσαρμογή Πλάτους και Ύψους

Τώρα έρχεται η καρδιά του tutorial: **how to set button size java**. Ο έλεγχος εκθέτει πολλές ιδιότητες διάταξης — `Left`, `Top`, `Width`, και `Height`. Ορίζοντάς τες απευθείας ελέγχετε την εμφάνιση του κουμπιού στη σελίδα.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Γιατί αυτά τα νούμερα; Στο Word, ένα point ισούται με 1/72 της ίντσας. Έτσι, πλάτος `120` points μεταφράζεται σε περίπου 1,67 ίντσες — αρκετά μεγάλο για μια ευανάγνωστη ετικέτα, αλλά όχι υπερβολικό. Προσαρμόστε τις τιμές ώστε να ταιριάζουν στο layout σας· οι ίδιες ιδιότητες απαντούν επίσης στο ερώτημα **how to set button** που μπορεί να έχετε.

> **Σημείωση:** Αν χρειάζεστε διαφορετικό τύπο κουμπιού (π.χ. ένα checkbox), αντικαταστήστε το `Forms2OleControlType.COMMANDBUTTON` με την κατάλληλη τιμή enum.

### 5. Αποθήκευση του Εγγράφου

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Αντικαταστήστε το `YOUR_DIRECTORY` με απόλυτη ή σχετική διαδρομή στο σύστημά σας. Μετά την εκτέλεση του προγράμματος, ανοίξτε το παραγόμενο αρχείο στο Microsoft Word. Θα δείτε ένα κουμπί με την ετικέτα “Click Me” τοποθετημένο 100 pts από τα αριστερά και 200 pts από το πάνω μέρος, με ακριβείς διαστάσεις όπως ορίσαμε.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται η πλήρης, έτοιμη‑για‑εκτέλεση κλάση Java. Αντιγράψτε‑και‑επικολλήστε την στο `CommandButtonActiveX.java`, προσαρμόστε τη διαδρομή εξόδου και πατήστε **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `CommandButton.docx` στο Word εμφανίζει μία σελίδα με ένα κλικ‑βασισμένο κουμπί “Click Me” τοποθετημένο περίπου στο μέσο της σελίδας. Οι διαστάσεις του κουμπιού ταιριάζουν με τις τιμές που ορίσατε, επιβεβαιώνοντας ότι **set button size java** λειτουργεί όπως προβλέπεται.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν το κουμπί δεν εμφανίζεται στο Word;

- **Ελέγξτε την έκδοση του Word.** Τα ActiveX controls απαιτούν την επιτραπέζια έκδοση του Word· το Word Online τα αφαιρεί.  
- **Βεβαιωθείτε ότι έχει εφαρμοστεί η άδεια Aspose.Words** (αν χρησιμοποιείτε πληρωμένη έκδοση). Μια μη αδειοδοτημένη έκδοση αξιολόγησης μπορεί να προσθέσει υδατογράφημα αλλά εξακολουθεί να εμφανίζει τον έλεγχο.

### Μπορώ να αλλάξω τη γραμματοσειρά ή το χρώμα του κουμπιού;

Ναι. Μετά την εισαγωγή του ελέγχου, μπορείτε να προσπελάσετε το υποκείμενο αντικείμενο OLE και να τροποποιήσετε τις ιδιότητες VBA. Αυτό είναι πιο προχωρημένο θέμα — ρίξτε μια ματιά στο `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` για κόκκινη λεζάντα, για παράδειγμα.

### Πώς διαχειρίζομαι το γεγονός κλικ του κουμπιού;

Τα κουμπιά εντολής ActiveX πυροδοτούν ένα VBA `Click` event. Για να λειτουργήσει το κουμπί, πρέπει να ενσωματώσετε μια μακροεντολή στο ίδιο έγγραφο. Η Aspose.Words μπορεί να προσθέσει ένα macro module μέσω του API `Document.getMacros()`, αλλά ο κώδικας της μακροεντολής πρέπει να γραφτεί σε VBA.

### Τι γίνεται με διαφορετικούς τύπους κουμπιών;

Η Aspose.Words υποστηρίζει πολλές τιμές `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, κ.λπ. Απλώς αλλάξτε την σταθερά enum στην κλήση `insertForms2OleControl` για να πειραματιστείτε.

---

## Pro Tips για Κώδικα Έτοιμο για Παραγωγή

1. **Χρησιμοποιήστε σταθερές για τις τιμές διάταξης** – διευκολύνει μελλοντικές προσαρμογές.  
2. **Τυλίξτε τη διαδρομή αποθήκευσης σε αντικείμενο `Path`** για να αποφύγετε διαχωριστές ειδικά για κάθε πλατφόρμα.  
3. **Κλείστε το Document** (ή χρησιμοποιήστε try‑with‑resources) αν επεξεργάζεστε πολλά αρχεία σε βρόχο.  
4. **Επικυρώστε τον φάκελο εξόδου** πριν καλέσετε `save` για να αποφύγετε `FileNotFoundException`.

---

## Συμπέρασμα

Μάθατε πώς να **set button size java** δημιουργώντας ένα κενό αρχείο Word, εισάγοντας ένα κουμπί εντολής ActiveX και ρυθμίζοντας ακριβώς τις διαστάσεις του — όλα με λίγες γραμμές κώδικα Java. Αυτό καλύπτει το βασικό μέρος του **how to insert activex**, **how to set button**, **java create blank word**, και **insert command button word** σε ένα ενιαίο, αυτόνομο παράδειγμα.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να προσαρμόσετε την ετικέτα του κουμπιού, να προσθέσετε μια μακροεντολή που να ανταποκρίνεται στα κλικ, ή να ενσωματώσετε πολλαπλούς ελέγχους στην ίδια σελίδα. Μπορείτε επίσης να εξερευνήσετε τη μετατροπή του παραγόμενου .docx σε PDF με Aspose.Words, διατηρώντας το κουμπί ως στατική εικόνα.

Πειραματιστείτε ελεύθερα, και αν συναντήσετε κάποιο πρόβλημα, αφήστε ένα σχόλιο παρακάτω. Καλό coding!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}