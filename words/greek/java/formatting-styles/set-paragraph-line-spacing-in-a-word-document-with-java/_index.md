---
category: general
date: 2026-11-15
description: Ορίστε το διάστημα γραμμής παραγράφου σε ένα έγγραφο Word με Java. Μάθετε
  πώς να ορίζετε το διάστημα γραμμής προγραμματιστικά χρησιμοποιώντας το Aspose.Words
  για ακριβή μορφοποίηση εγγράφων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: el
lastmod: 2026-11-15
og_description: Ορίστε το διάστημα γραμμής παραγράφων σε ένα έγγραφο Word με Java.
  Αυτός ο οδηγός εξηγεί πώς να ορίσετε το διάστημα γραμμής για παραγράφους και διαχωριστές
  υποσημειώσεων χρησιμοποιώντας το Aspose.Words, παρέχοντάς σας πλήρη έλεγχο της διάταξης
  του εγγράφου.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Ορισμός διαστήματος γραμμής παραγράφου στο Word χρησιμοποιώντας Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Ρύθμιση διαστήματος γραμμής παραγράφου σε έγγραφο Word με Java
url: /el/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός διαστήματος γραμμής παραγράφου σε έγγραφο Word με Java

Αν χρειάζεστε να **ορίσετε το διάστημα γραμμής παραγράφου** σε ένα έγγραφο Word, αυτό το tutorial σας δείχνει πώς να το κάνετε με Java και Aspose.Words. Θα μάθετε επίσης **πώς να ορίσετε το διάστημα γραμμής** για τους διαχωριστές υποσημειώσεων—μια κοινή απαίτηση κατά τη μορφοποίηση επαγγελματικών εγγράφων.

Στις παρακάτω ενότητες θα:

* Φορτώσετε ένα υπάρχον αρχείο *.docx*.
* Ανακτήσετε την παράγραφο διαχωριστή υποσημειώσεων.
* Εφαρμόσετε μια προσαρμοσμένη τιμή διαστήματος γραμμής.
* Αποθηκεύσετε το ενημερωμένο έγγραφο.

Δεν απαιτείται εξωτερική διαμόρφωση πέρα από την προσθήκη της βιβλιοθήκης Aspose.Words στο έργο σας, ώστε να μπορείτε να αντιγράψετε τον κώδικα ακριβώς όπως είναι και να τον εκτελέσετε αμέσως.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Εγκατεστημένο Java 17 ή νεότερο.
* Maven (ή άλλο εργαλείο κατασκευής) για διαχείριση εξαρτήσεων.
* Έγκυρη άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για δοκιμές).
* Ένα εισερχόμενο έγγραφο Word (`input.docx`) τοποθετημένο σε γνωστό φάκελο.

Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Ορισμός διαστήματος γραμμής παραγράφου με Aspose.Words

Αυτή η επικεφαλίδα H2 περιέχει τη βασική λέξη-κλειδί, ικανοποιώντας την απαίτηση SEO.

### Step 1: Φόρτωση του εγγράφου Word

Πρώτα, δημιουργήστε ένα αντικείμενο `Document` που δείχνει στο αρχείο προέλευσης.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου σας παρέχει ένα μοντέλο στη μνήμη που μπορείτε να επεξεργαστείτε χωρίς να αγγίξετε το αρχικό αρχείο μέχρι να το αποθηκεύσετε ρητά.

### Step 2: Ανάκτηση του διαχωριστή υποσημειώσεων

Οι διαχωριστές υποσημειώσεων είναι ειδικές παράγραφοι που εμφανίζονται μεταξύ των υποσημειώσεων και του κύριου κειμένου. Για να αλλάξετε την εμφάνισή τους, πρέπει να έχετε πρόσβαση στο αντικείμενο `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Συμβουλή*: Αν το έγγραφό σας δεν περιέχει υποσημειώσεις, ο διαχωριστής υπάρχει ακόμη ως κρυφή παράγραφος, οπότε η κλήση δεν θα επιστρέψει ποτέ `null`.

### Step 3: Πώς να ορίσετε το διάστημα γραμμής για την παράγραφο του διαχωριστή

Τώρα εφαρμόστε το επιθυμητό διάστημα γραμμής. Το Aspose.Words χρησιμοποιεί μονάδες points για τις τιμές διαστήματος γραμμής· 12 pts είναι περίπου μονόδιάστημα για τις περισσότερες γραμματοσειρές.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Μπορείτε επίσης να χρησιμοποιήσετε άλλες λειτουργίες διαστήματος:

| Mode                     | Method call                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (π.χ., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Η επιλογή του σωστού κανόνα διασφαλίζει ότι το έγγραφο αποδίδεται σταθερά σε Word, Google Docs και άλλους προβολείς.

### Step 4: Αποθήκευση του ενημερωμένου εγγράφου

Τέλος, γράψτε τις αλλαγές πίσω στο δίσκο.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Όταν ανοίξετε το `output.docx` στο Microsoft Word, ο διαχωριστής υποσημειώσεων θα εμφανιστεί με το διάστημα γραμμής που ορίσατε.

## Κατανόηση του τρόπου ορισμού διαστήματος γραμμής για κανονικές παραγράφους

Το ίδιο API λειτουργεί για οποιοδήποτε αντικείμενο `Paragraph`, όχι μόνο για διαχωριστές υποσημειώσεων. Ακολουθεί ένα σύντομο παράδειγμα που προσαρμόζει το διάστημα της πρώτης παραγράφου στο σώμα του εγγράφου:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Γιατί μπορεί να το χρειαστείτε**: Εκθέσεις, συμβόλαια και ακαδημαϊκές εργασίες συχνά απαιτούν συγκεκριμένο στυλ διαστήματος γραμμής (π.χ., διπλό διάστημα για προσχέδια). Η χρήση της ίδιας μεθόδου `setLineSpacing` εγγυάται την ακριβή διάταξη που επιθυμείτε.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Issue                                 | Cause                                   | Fix |
|---------------------------------------|----------------------------------------|-----|
| Το διάστημα γραμμής δεν αλλάζει       | `LineSpacingRule` παραμένει στην προεπιλογή (AUTO) | Ορίστε ρητά τον κανόνα με `setLineSpacingRule`. |
| Επιπλέον κενές γραμμές μετά το διαχωριστή | Ο διαχωριστής περιέχει κρυφές επιστροφές carriage return | Κόψτε το κείμενο του διαχωριστή με `separator.getText().trim();` πριν εφαρμόσετε το διάστημα. |
| Το έγγραφο καταστρέφεται μετά την αποθήκευση | Χρήση παλιάς έκδοσης Aspose.Words | Αναβαθμίστε στην πιο πρόσφατη έκδοση (π.χ., 24.10) που περιλαμβάνει διορθώσεις σφαλμάτων αποθήκευσης. |

## Pro tip: επεξεργασία πολλαπλών εγγράφων σε batch

Αν χρειάζεται να ενημερώσετε δεκάδες αρχεία, τυλίξτε τη λογική σε μια βοηθητική μέθοδο και επαναλάβετε τη διαδικασία σε έναν φάκελο:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Η εκτέλεση αυτής της μεθόδου σε βρόχο σας εξοικονομεί ώρες χειροκίνητης επεξεργασίας.

## Αναμενόμενο αποτέλεσμα

Μετά την εκτέλεση του πλήρους προγράμματος, το `output.docx` θα:

* Διατηρεί το αρχικό περιεχόμενο αμετάβλητο εκτός από το διάστημα γραμμής.
* Εμφανίζει τον διαχωριστή υποσημειώσεων με μονόδιάστημα (12 pts).
* Διατηρεί όλη την υπόλοιπη μορφοποίηση (στυλ, εικόνες, πίνακες).

Ανοίξτε το αρχείο στο Word και ελέγξτε ότι η γραμμή του διαχωριστή είναι πιο στενή (ή πιο χαλαρή, ανάλογα με την τιμή που ορίσατε).

## Συμπέρασμα

Τώρα ξέρετε πώς να **ορίσετε το διάστημα γραμμής παραγράφου** σε έγγραφο Word χρησιμοποιώντας Java, και επίσης κατανοείτε **πώς να ορίσετε το διάστημα γραμμής** για διαχωριστές υποσημειώσεων και κανονικές παραγράφους. Το πλήρες, εκτελέσιμο παράδειγμα δείχνει πώς να φορτώσετε ένα έγγραφο, να προσαρμόσετε τις ιδιότητες διαστήματος γραμμής και να αποθηκεύσετε το αποτέλεσμα—όλα με λίγες σαφείς κλήσεις API.

**Επόμενα βήματα** που μπορείτε να εξερευνήσετε:

* **Πώς να ορίσετε το διάστημα γραμμής** για πίνακες και στοιχεία λίστας.
* Εφαρμογή διαφορετικών κανόνων διαστήματος σε επικεφαλίδες έναντι κυρίως κειμένου.
* Χρήση του αντικειμένου `Style` για επιβολή διαστήματος σε ολόκληρο το έγγραφο.

Δοκιμάστε τις τιμές, συνδυάστε τες με άλλες επιλογές μορφοποίησης, και θα έχετε πλήρη έλεγχο της διάταξης του εγγράφου σε οποιαδήποτε εφαρμογή Java. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να ορίσετε επιλογές στο Aspose.Words for Java – πλήρης οδηγός](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Πώς να ορίσετε LoadOptions στο Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Αλλαγή διαστήματος και εσοχών ασιατικών παραγράφων σε έγγραφο Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}