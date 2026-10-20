---
category: general
date: 2026-07-16
description: Ορίστε το μέγεθος του κουμπιού προγραμματιστικά σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words for Java. Μάθετε πώς να εισάγετε κουμπί ActiveX, να ορίσετε τη θέση
  του κουμπιού και άλλα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: el
lastmod: 2026-07-16
og_description: Ορίστε το μέγεθος του κουμπιού σε ένα έγγραφο Word χρησιμοποιώντας
  Java. Αυτός ο οδηγός βήμα‑βήμα δείχνει πώς να εισαγάγετε κουμπί ActiveX, να ορίσετε
  τη θέση του κουμπιού και να προσθέσετε το κουμπί προγραμματιστικά.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Ορισμός μεγέθους κουμπιού στο Word με Java – Πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Ορισμός μεγέθους κουμπιού στο Word με Java – Πλήρης οδηγός Aspose.Words
url: /el/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός Μεγέθους Κουμπιού σε Word με Java – Πλήρης Οδηγός Aspose.Words

Αναρωτηθήκατε ποτέ πώς να **set button size** μέσα σε ένα αρχείο Word χωρίς να ανοίξετε το UI; Δεν είστε ο μόνος. Όταν χρειάζεται να δημιουργήσετε ένα έγγραφο με συμπληρωμένες φόρμες άμεσα—π.χ., ένα πακέτο ενσωμάτωσης με κουμπί “Submit”—η προγραμματιστική προσέγγιση εξοικονομεί ώρες χειροκίνητης εργασίας.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα τις ακριβείς ενέργειες για **insert ActiveX button**, να προσαρμόσουμε τις διαστάσεις του, να το τοποθετήσουμε σωστά και, τέλος, να αποθηκεύσουμε το αρχείο. Στο τέλος θα μπορείτε να **programmatically add button** ελέγχους σε οποιοδήποτε έγγραφο Word χρησιμοποιώντας το Aspose.Words for Java.

## Προαπαιτούμενα – Τι Χρειάζεστε Πριν Ξεκινήσετε

- **Java Development Kit (JDK) 8+** – ο κώδικας εκτελείται σε οποιοδήποτε πρόσφατο JDK.
- **Aspose.Words for Java** library (download the latest JAR from the official site).  
- Ένα **IDE** της επιλογής σας—IntelliJ IDEA, Eclipse, ή ακόμη και ένας απλός επεξεργαστής κειμένου λειτουργεί.
- Βασική εξοικείωση με τη σύνταξη της Java· δεν απαιτείται βαθιά γνώση αυτοματοποίησης του Word.

> *Pro tip:* Κρατήστε το JAR του Aspose.Words στο classpath του έργου σας, διαφορετικά θα αντιμετωπίσετε `ClassNotFoundException` τη στιγμή που θα προσπαθήσετε να εισάγετε `com.aspose.words.*`.

## Βήμα 1: Δημιουργία Νέου Εγγράφου Word

Το πρώτο που κάνουμε είναι να δημιουργήσουμε ένα κενό έγγραφο και ένα `DocumentBuilder`. Σκεφτείτε το builder ως ένα στυλό που μας επιτρέπει να σχεδιάζουμε οτιδήποτε μέσα στο αρχείο.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` είναι η κύρια μηχανή που μας επιτρέπει να εισάγουμε παραγράφους, πίνακες και—ναι—ελέγχους ActiveX.

## Βήμα 2: Εισαγωγή ActiveX Button – Η Στιγμή “Insert ActiveX Button”

Τώρα πραγματικά **insert activex button** στο έγγραφο. Το Aspose.Words εκθέτει μια βολική μέθοδο `insertForms2OleControl` που επιστρέφει ένα αντικείμενο `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *What’s happening under the hood?* `Forms2OleControlType.COMMAND_BUTTON` λέει στο Word ότι θέλουμε ένα κλασικό CommandButton, το ίδιο είδος που θα σύρνατε από την καρτέλα Developer στο UI.

## Βήμα 3: Ορισμός Μεγέθους και Θέσης Κουμπιού – Η Κεντρική Λογική “Set Button Size”

Εδώ όπου το κύριο keyword λάμπει. Θα **set button size** και επίσης **set button location** ώστε ο έλεγχος να εμφανίζεται ακριβώς εκεί που θέλουμε στη σελίδα.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Why you should care:** Τα points είναι η φυσική μονάδα μέτρησης στο Word (1 point = 1/72 ίντσα). Με την τροποποίηση των `setLeft`, `setTop`, `setWidth` και `setHeight` αποκτάτε έλεγχο pixel‑perfect—χωρίς το “φαίνεται σωστό στην οθόνη μου αλλά όχι στον εκτυπωτή”.
> *Common pitfall:* Η παράλειψη του ορισμού είτε του πλάτους είτε του ύψους θα αφήσει το κουμπί στο προεπιλεγμένο μέγεθος, το οποίο μπορεί να είναι πολύ μικρό για κλικ. Πάντα ορίζετε και τα δύο.

## Βήμα 4: Αποθήκευση Εγγράφου – Η “Create Word Document Button” Ολοκληρώθηκε

Τέλος, γράφουμε το αρχείο στο δίσκο. Το όνομα υποδηλώνει ότι **creating a Word document button** μέσα σε ένα .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Όταν ανοίξετε το `CommandButtonDemo.docx` στο Microsoft Word, θα δείτε ένα κουμπί **Submit** τοποθετημένο 100 pt από την αριστερή άκρη και 150 pt από την κορυφή, με μέγεθος 80 × 30 pt. Κάνοντας κλικ σε αυτό στο UI θα ενεργοποιήσει τη προεπιλεγμένη συμπεριφορά ActiveX (που μπορείτε αργότερα να συνδέσετε με VBA αν χρειαστεί).

### Αναμενόμενη Στιγμιότυπο Εξόδου

![Έγγραφο Word που εμφανίζει το εισαχθέν κουμπί με το ορισμένο μέγεθος κουμπιού](https://example.com/images/set-button-size.png "Στιγμιότυπο οθόνης ενός αρχείου Word όπου το μέγεθος του κουμπιού έχει οριστεί χρησιμοποιώντας Aspose.Words for Java")

*Alt text:* ορισμός μεγέθους κουμπιού σε έγγραφο Word χρησιμοποιώντας Java

## Βήμα 5 (Προαιρετικό): Προσθήκη Περισσότερων Ελέγχων ή Στυλιζάρισμα του Κουμπιού

Αν χρειάζεστε να **programmatically add button** ελέγχους πέρα από ένα μόνο κουμπί Submit, απλώς επαναλάβετε το μπλοκ εισαγωγής με νέα ονόματα και λεζάντες. Μπορείτε επίσης να προσαρμόσετε τη γραμματοσειρά, το χρώμα φόντου ή ακόμη και να συνδέσετε μακροεντολές VBA αργότερα.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tip:* Διατηρήστε όλες τις διαστάσεις του κουμπιού συνεπείς για επαγγελματική εμφάνιση. Ένας γρήγορος τρόπος είναι να αποθηκεύετε το πλάτος/ύψος σε σταθερές.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### “Μπορώ να ορίσω το μέγεθος του κουμπιού χρησιμοποιώντας εκατοστά αντί για points;”

Το API του Word δέχεται μόνο points, αλλά μπορείτε να μετατρέψετε τα εκατοστά σε points (`points = cm * 28.3465`). Γράψτε μια μικρή βοηθητική μέθοδο αν προτιμάτε μετρικές μονάδες.

### “Τι γίνεται αν χρειάζεται το κουμπί να εμφανίζεται σε συγκεκριμένη σελίδα;”

Μετά την εισαγωγή του κουμπιού, μπορείτε να μετακινήσετε τον κέρσορα σε μια συγκεκριμένη σελίδα χρησιμοποιώντας `builder.moveToPage(pageNumber)`. Εισάγετε τον έλεγχο αμέσως μετά τη μετακίνηση, στη συνέχεια ορίστε τη θέση του όπως φαίνεται παραπάνω.

### “Λειτουργεί αυτό με αρχεία .doc (Word 97‑2003);”

Ναι—το Aspose.Words διαχειρίζεται αυτόματα παλαιότερες μορφές. Απλώς αλλάξτε την επέκταση του αρχείου στο `doc.save("Demo.doc")`.

## Πλήρες, Εκτελέσιμο Παράδειγμα

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια κλάση Java και να το εκτελέσετε αμέσως (υπό την προϋπόθεση ότι το JAR του Aspose.Words βρίσκεται στο classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο `CommandButtonDemo.docx`, και θα δείτε δύο κουμπιά με σωστό μέγεθος, έτοιμα για αλληλεπίδραση.

## Συμπέρασμα – Κατακτήσατε τον Ορισμό Μεγέθους Κουμπιού σε Word

Μόλις περάσαμε από μια πλήρη, ολοκληρωμένη λύση για **set button size** και **set button location** χρησιμοποιώντας το Aspose.Words for Java. Ακολουθώντας τα βήματα μπορείτε να **insert activex button**, **programmatically add button** ελέγχους, και τελικά **create word document button** στοιχεία που λειτουργούν ακριβώς όπως χρειάζεστε.

Τι ακολουθεί; Δοκιμάστε να ενσωματώσετε το κουμπί μέσα σε κελί πίνακα, ή να συνδέσετε μια μακροεντολή VBA που επικυρώνει τα πεδία φόρμας πριν από την υποβολή. Το ίδιο μοτίβο λειτουργεί για άλλους ελέγχους ActiveX όπως τα check boxes ή τα combo boxes—απλώς αντικαταστήστε το `Forms2OleControlType.COMMAND_BUTTON` με την κατάλληλη τιμή enum.

Αν αντιμετωπίσετε οποιοδήποτε πρόβλημα, αφήστε ένα σχόλιο παρακάτω. Καλή προγραμματιστική, και απολαύστε τη δύναμη της αυτοματοποιημένης δημιουργίας εγγράφων Word!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα επεξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να ορίσετε LoadOptions στο Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Πώς να αφαιρέσετε υποσέλιδα από έγγραφα Word χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java: Πλήρης Οδηγός Επεξεργασίας Εγγράφων Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}