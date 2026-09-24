---
category: general
date: 2026-09-24
description: Ορίστε τη θέση του κουμπιού σε ένα έγγραφο Word χρησιμοποιώντας Java
  και Aspose.Words. Μάθετε πώς να εισάγετε κουμπί, να προσθέσετε έλεγχο ActiveX και
  να δημιουργήσετε έγγραφο Word σε στυλ Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: el
lastmod: 2026-09-24
og_description: Ορίστε τη θέση του κουμπιού σε ένα έγγραφο Word χρησιμοποιώντας Java.
  Αυτός ο οδηγός δείχνει πώς να εισάγετε κουμπί, να προσθέσετε έλεγχο ActiveX και
  να δημιουργήσετε έγγραφο Word με Java χρησιμοποιώντας το Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Ορισμός θέσης κουμπιού σε έγγραφο Word με Java – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Πώς να ορίσετε τη θέση του κουμπιού σε ένα έγγραφο Word με τη Java
url: /el/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε τη θέση του κουμπιού σε ένα έγγραφο Word με Java

Αν χρειάζεστε να **ορίσετε τη θέση του κουμπιού** μέσα σε ένα αρχείο Word, αυτός ο οδηγός σας παρουσιάζει μια πλήρη, εκτελέσιμη λύση. Είτε δημιουργείτε ένα πρότυπο που απαιτεί αλληλεπίδραση χρήστη είτε αυτοματοποιείτε μια φόρμα, θα μάθετε ακριβώς **πώς να εισάγετε ένα κουμπί** χρησιμοποιώντας το Aspose.Words for Java και να ελέγχετε την τοποθέτησή του.

Το σεμινάριο καλύπτει όλα όσα χρειάζεστε για να **προσθέσετε έλεγχο ActiveX** σε ένα έγγραφο Word, εξηγεί πώς να **προσθέσετε κουμπί σε Word**, και δείχνει τη πλήρη διαδικασία για **δημιουργία εγγράφου Word με Java**. Δεν απαιτούνται εξωτερικές αναφορές—απλώς αντιγράψτε, εκτελέστε και επαληθεύστε το αποτέλεσμα.

## Προαπαιτούμενα

* Εγκατεστημένο Java 17 (ή οποιοδήποτε runtime Java 8+).
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* Άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για αξιολόγηση).
* Βασική κατανόηση της σύνταξης της Java.

> **Συμβουλή:** Κρατήστε τα JAR του Aspose.Words σε φάκελο `libs/` και προσθέστε τα στο classpath του έργου σας για να αποφύγετε συγκρούσεις εκδόσεων.

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα απλό έργο Maven (ή χρησιμοποιήστε Gradle) και προσθέστε την εξάρτηση Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Η εκτέλεση του `mvn clean compile` κατεβάζει τη βιβλιοθήκη και προετοιμάζει τη διαδρομή κατασκευής.

## Βήμα 2: Δημιουργία νέου εγγράφου Word

Η πρώτη ενέργεια είναι η **δημιουργία εγγράφου Word με Java**. Δημιουργείτε ένα αντικείμενο `Document` και ένα `DocumentBuilder` που σας επιτρέπει να επεξεργαστείτε το αρχείο.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρέχει μια ευέλικτη API για την εισαγωγή περιεχομένου.

## Βήμα 3: Πώς να εισάγετε κουμπί – προσθήκη ελέγχου ActiveX

Το Aspose.Words εκθέτει την κλάση `Forms2OleControl` για την εισαγωγή παλαιών ελέγχων ActiveX όπως ένα CommandButton. Αυτό το βήμα δείχνει τον ακριβή τρόπο **πώς να εισάγετε ένα κουμπί** στο έγγραφο.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Η μέθοδος `insertForms2OleControl` επιστρέφει ένα αντικείμενο `Forms2OleControl` που μπορείτε να διαμορφώσετε. Αυτό αποτελεί τον πυρήνα της διαδικασίας **προσθήκης ελέγχου ActiveX**.

## Βήμα 4: Ορισμός θέσης κουμπιού

Τώρα πραγματικά **ορίζουμε τη θέση του κουμπιού**. Οι μέθοδοι `setLeft` και `setTop` του ελέγχου δέχονται τιμές σε σημεία (1 pt = 1/72 in). Για να ευθυγραμμίσετε το κουμπί με τυπικές συντεταγμένες οθόνης, μπορείτε να μετατρέψετε εικονοστοιχεία (pixels) σε σημεία (1 px ≈ 0.75 pt). Στο παράδειγμα τοποθετούμε το κουμπί 100 px από την αριστερή άκρη και 150 px από την άνω άκρη.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Επειδή η λογική **ορισμού θέσης κουμπιού** είναι ενσωματωμένη εδώ, μπορείτε να επαναχρησιμοποιήσετε αυτές τις γραμμές όποτε χρειαστεί να μετακινήσετε έναν έλεγχο. Προσαρμόστε τους αριθμούς ώστε να ταιριάζουν στις απαιτήσεις της διάταξής σας.

## Βήμα 5: Ορισμός μεγέθους και λεζάντας

Ένα κουμπί χωρίς ετικέτα είναι συγκεχυμένο. Χρησιμοποιήστε `setWidth`, `setHeight` και `setCaption` για να του δώσετε μια ορατή εμφάνιση.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

Το μέγεθος εκφράζεται επίσης σε σημεία, έτσι μετατρέπουμε από εικονοστοιχεία για συνέπεια.

## Βήμα 6: Αποθήκευση του εγγράφου – ολοκλήρωση της ροής δημιουργίας εγγράφου Word με Java

Τέλος, αποθηκεύστε το αρχείο στο δίσκο. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική με τη ρίζα του έργου.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `CommandButtonDemo.docx` μέσα στο φάκελο `output`. Το άνοιγμα του αρχείου στο Microsoft Word εμφανίζει ένα κλικ‑κουμπί τοποθετημένο ακριβώς εκεί που το ορίσατε.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο `.docx` με όνομα **CommandButtonDemo.docx**.
* Μέσα στο έγγραφο, ένα **CommandButton** με ετικέτα “Click Me” εμφανίζεται 100 px από το αριστερό περιθώριο και 150 px από το άνω περιθώριο.
* Το κουμπί ανταποκρίνεται σε κλικ όταν το έγγραφο ανοίγει στο Word (θα εμφανίσει ένα προεπιλεγμένο μήνυμα ActiveX εκτός εάν προσθέσετε προσαρμοσμένο κώδικα VBA).

## Βήμα 7: Κοινές παραλλαγές και ειδικές περιπτώσεις

### Προσθήκη πολλαπλών κουμπιών

Αν χρειάζεται να **προσθέσετε κουμπί σε Word** περισσότερες από μία φορές, επαναλάβετε τα βήματα 3‑5 με ένα νέο αντικείμενο `Forms2OleControl` κάθε φορά. Θυμηθείτε να προσαρμόσετε την τιμή `setTop` ώστε τα κουμπιά να μην επικαλύπτονται.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Λειτουργία χωρίς άδεια

Το Aspose.Words προσθέτει υδατογράφημα όταν χρησιμοποιείται χωρίς άδεια. Για κώδικα παραγωγής, αγοράστε μια άδεια και εφαρμόστε την στην αρχή της `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Συμβατότητα με παλαιότερες εκδόσεις του Office

Οι έλεγχοι ActiveX υποστηρίζονται στη μορφή `.doc` (Word 97‑2003). Για να δημιουργήσετε ένα παλαιό αρχείο, αλλάξτε τη μορφή αποθήκευσης:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Πλήρης κώδικας (εκτελέσιμος)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Αποθηκεύστε το αρχείο ως `src/main/java/CommandButtonDemo.java`, εκτελέστε `mvn exec:java -Dexec.mainClass=CommandButtonDemo` και ανοίξτε το παραγόμενο έγγραφο για να δείτε το αποτέλεσμα.

## Συχνές ερωτήσεις

**Ε: Λειτουργεί αυτό με OpenJDK;**  
Α: Ναι. Το Aspose.Words είναι καθαρά Java και λειτουργεί σε οποιαδήποτε υλοποίηση JDK 8+, συμπεριλαμβανομένου του OpenJDK.

**Ε: Μπορώ να αλλάξω τη γραμματοσειρά ή το χρώμα του κουμπιού;**  
Α: Η εμφάνιση του κουμπιού ActiveX ελέγχεται από την εφαρμογή‑ξενιστή (Word). Μπορείτε να προσθέσετε κώδικα VBA για να τροποποιήσετε τις ιδιότητες κατά την εκτέλεση, αλλά η στατική εμφάνιση περιορίζεται στο προεπιλεγμένο στυλ.

**Ε: Τι γίνεται αν χρειαστεί να τοποθετήσω το κουμπί μέσα σε κελί πίνακα;**  
Α: Μετακινήστε τον κέρσορα του `DocumentBuilder` στο κελί πριν καλέσετε το `insertForms2OleControl`. Ο έλεγχος θα κληρονομήσει τη διάταξη του κελιού και μπορείτε ακόμη να χρησιμοποιήσετε `setLeft`/`setTop` για ακριβή ρύθμιση.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **ορίσετε τη θέση του κουμπιού** σε ένα έγγραφο Word χρησιμοποιώντας Java, πώς να **εισάγετε κουμπί**, πώς να **προσθέσετε έλεγχο ActiveX**, και πώς να **προσθέσετε κουμπί σε Word** ακολουθώντας τις βέλτιστες πρακτικές για έργα **δημιουργίας εγγράφου Word με Java**. Το πλήρες παράδειγμα παρουσιάζει ολόκληρη τη ροή εργασίας—από τη ρύθμιση του έργου έως ένα αποθηκευμένο αρχείο `.docx` που περιέχει ένα λειτουργικό CommandButton.

### Επόμενα βήματα

* Εξερευνήστε άλλες τιμές `Forms2OleControl.ControlType` (π.χ., `CHECKBOX`, `TEXTBOX`) για να δημιουργήσετε πιο πλούσιες φόρμες.
* Συνδυάστε το κουμπί με μακροεντολές VBA για προσαρμοσμένο χειρισμό κλικ.
* Χρησιμοποιήστε τη λειτουργία συγχώνευσης αλληλογραφίας του Aspose.Words για να δημιουργήσετε εξατομικευμένα έγγραφα που ήδη περιέχουν διαδραστικούς ελέγχους.

Καλή προγραμματιστική δουλειά και απολαύστε την αυτοματοποίηση εγγράφων Word με Java!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Προσθήκη πεδίου φόρμας Combo Box σε έγγραφο Word με Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Πώς να φορτώσετε έγγραφα Word με Aspose.Words Java: Ολοκληρωμένος οδηγός](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}