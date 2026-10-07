---
category: general
date: 2026-10-07
description: πώς να μορφοποιήσετε τις υποσημειώσεις σε Java – μάθετε πώς να αλλάξετε
  το διαχωριστικό υποσημειώσεων, να επεξεργαστείτε τη μορφοποίηση του διαχωριστικού
  υποσημειώσεων και να αποθηκεύσετε το έγγραφο με μορφοποιημένες υποσημειώσεις.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style footnotes
- change footnote separator
- edit footnote separator
- format footnote separator
- access footnote separator
language: el
lastmod: 2026-10-07
og_description: πώς να μορφοποιήσετε τις υποσημειώσεις σε Java με το Aspose.Words.
  Αυτό το σεμινάριο σας δείχνει πώς να αλλάξετε το διαχωριστικό υποσημειώσεων, να
  επεξεργαστείτε τη μορφοποίηση του διαχωριστικού υποσημειώσεων και να δημιουργήσετε
  ένα τελειοποιημένο έγγραφο.
og_image_alt: Screenshot illustrating how to style footnotes in a Java Word processing
  example
og_title: πώς να μορφοποιήσετε τις υποσημειώσεις στη Java – πλήρης οδηγός προγραμματισμού
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  headline: how to style footnotes in Java using Aspose.Words
  type: TechArticle
- description: how to style footnotes in Java – learn to change footnote separator,
    edit footnote separator formatting, and save the document with styled footnotes.
  name: how to style footnotes in Java using Aspose.Words
  steps:
  - name: Load the source document.
    text: Load the source document.
  - name: Iterate through each footnote and **access footnote separator** runs.
    text: Iterate through each footnote and **access footnote separator** runs.
  - name: Apply the desired styling (bold, color, underline, etc.).
    text: Apply the desired styling (bold, color, underline, etc.).
  - name: Save the document with the updated footnote separator.
    text: Save the document with the updated footnote separator.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: πώς να μορφοποιήσετε τις υποσημειώσεις σε Java χρησιμοποιώντας το Aspose.Words
url: /el/java/document-styling/how-to-style-footnotes-in-java-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να μορφοποιήσετε υποσημειώσεις σε Java με Aspose.Words

Αν χρειάζεστε να μορφοποιήσετε υποσημειώσεις σε ένα έγγραφο Word χρησιμοποιώντας Java, αυτός ο οδηγός σας δείχνει **πώς να μορφοποιήσετε υποσημειώσεις** με το Aspose.Words. Θα μάθετε πώς να αλλάζετε το διαχωριστικό υποσημειώσεων, να επεξεργάζεστε τη μορφοποίηση του διαχωριστικού και να αποθηκεύετε το τροποποιημένο έγγραφο σε λίγα σαφή βήματα.

Η εργασία με υποσημειώσεις συχνά σημαίνει την προσαρμογή της γραμμής διαχωριστικού που εμφανίζεται μεταξύ του κυρίως κειμένου και της λίστας υποσημειώσεων. Στο τέλος αυτού του tutorial θα μπορείτε να **προσπελάσετε τα runs του διαχωριστικού υποσημειώσεων**, να εφαρμόζετε έντονη ή χρωματική μορφοποίηση και να ελέγχετε τη συνολική εμφάνιση των υποσημειώσεων χωρίς να βγείτε από το IDE σας.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη εγκατεστημένη.  
* Maven 3.6+ (ή Gradle) για τη διαχείριση εξαρτήσεων.  
* Ένα έγκυρο license του Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για αυτό το παράδειγμα).  
* Ένα πηγαίο έγγραφο Word που περιέχει τουλάχιστον μία υποσημείωση (π.χ., `Footnotes.docx`).

Αυτές οι απαιτήσεις διασφαλίζουν ότι ο κώδικας εκτελείται ομαλά σε σύγχρονα περιβάλλοντα Java και σας επιτρέπουν να εστιάσετε στην τεχνική **πώς να μορφοποιήσετε υποσημειώσεις** αντί για προβλήματα ρύθμισης.

## Πώς να μορφοποιήσετε υποσημειώσεις – γενική προσέγγιση

Η διαδικασία αποτελείται από τέσσερις λογικές φάσεις:

1. Φόρτωση του πηγαίου εγγράφου.  
2. Επανάληψη σε κάθε υποσημείωση και **πρόσβαση στα runs του διαχωριστικού υποσημειώσεων**.  
3. Εφαρμογή της επιθυμητής μορφοποίησης (έντονα, χρώμα, υπογράμμιση κ.λπ.).  
4. Αποθήκευση του εγγράφου με το ενημερωμένο διαχωριστικό υποσημειώσεων.

Κάθε φάση αντιστοιχεί άμεσα σε μια γραμμή κώδικα, καθιστώντας την υλοποίηση εύκολη στην παρακολούθηση και τροποποίηση.

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα νέο έργο Maven (ή προσθέστε στο υπάρχον) και συμπεριλάβετε την εξάρτηση Aspose.Words:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.10</version> <!-- Use the latest version -->
    </dependency>
</dependencies>
```

> **Συμβουλή:** Κρατήστε την έκδοση της βιβλιοθήκης ενημερωμένη· οι νεότερες εκδόσεις προσθέτουν διορθώσεις σφαλμάτων για τη διαχείριση υποσημειώσεων.

## Βήμα 2: Φόρτωση του πηγαίου εγγράφου που περιέχει υποσημειώσεις

```java
import com.aspose.words.*;

public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // Load the Word file that has footnotes.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
```

Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word. Η φόρτωσή του είναι η πρώτη συγκεκριμένη ενέργεια στο **πώς να μορφοποιήσετε υποσημειώσεις**.

## Βήμα 3: Επανάληψη σε κάθε υποσημείωση και **πρόσβαση στα runs του διαχωριστικού υποσημειώσεων**

```java
        // Iterate through all footnotes in the document.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // The separator is a Run that appears between the main text and the footnote list.
            Run separator = footnote.getSeparator();

            // Guard against unexpected null values (rare but possible with corrupted files).
            if (separator != null) {
                // Apply desired styling to the separator run.
                separator.getFont().setBold(true);          // change footnote separator to bold
                separator.getFont().setColor(Color.BLUE);   // optional: set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }
        }
```

Σε αυτό το τμήμα **προσπελάζουμε τα runs του διαχωριστικού υποσημειώσεων** μέσω του `footnote.getSeparator()`. Το αντικείμενο `Run` παρέχει πλήρη έλεγχο της μορφοποίησης του κειμένου, επιτρέποντάς σας να **αλλάξετε την εμφάνιση του διαχωριστικού υποσημειώσεων** με μια μόνο γραμμή κώδικα.

### Γιατί χρησιμοποιούμε το `Footnote.getSeparator()`

* Το `Footnote.getSeparator()` επιστρέφει το run που περιέχει τη γραμμή διαχωριστικού.  
* Είναι το μοναδικό σημείο εισόδου του API που σας επιτρέπει να **επεξεργαστείτε το διαχωριστικό υποσημειώσεων** άμεσα.  
* Η τροποποίηση των ιδιοτήτων `Font` του run ενημερώνει το οπτικό διαχωριστικό για όλες τις υποσημειώσεις που μοιράζονται το ίδιο στυλ.

## Βήμα 4: (Προαιρετικό) Μορφοποίηση του διαχωριστικού συνέχειας και της σημείωσης

Το Word διακρίνει τρεις τύπους διαχωριστικών:

| Τύπος                     | Μέθοδος API                                 | Τυπική χρήση |
|--------------------------|---------------------------------------------|--------------|
| Κύριο διαχωριστικό       | `Footnote.getSeparator()`                  | Διαχωρίζει το κύριο κείμενο από την πρώτη υποσημείωση |
| Διαχωριστικό συνέχειας   | `Footnote.getContinuationSeparator()`      | Διαχωρίζει τις επόμενες σελίδες υποσημειώσεων |
| Σημείωση συνέχειας       | `Footnote.getContinuationNotice()`         | Εμφανίζει το κείμενο “Continued…” σε μεταγενέστερες σελίδες |

Αν θέλετε επίσης να **μορφοποιήσετε το διαχωριστικό υποσημειώσεων** για σελίδες συνέχειας, προσθέστε τον παρακάτω κώδικα μέσα στον βρόχο:

```java
            // Continuation separator (optional)
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // Continuation notice (optional)
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
```

Αυτά τα αποσπάσματα δείχνουν πώς να **επεξεργαστείτε αντικείμενα διαχωριστικού υποσημειώσεων** πέρα από τη βασική γραμμή, δίνοντάς σας πλήρη έλεγχο της διάταξης των υποσημειώσεων.

## Βήμα 5: Αποθήκευση του τροποποιημένου εγγράφου

```java
        // Save the document with the styled footnote separators.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

Η αποθήκευση του αρχείου γράφει όλες τις αλλαγές μορφοποίησης στο δίσκο, ολοκληρώνοντας τη ροή εργασίας **πώς να μορφοποιήσετε υποσημειώσεις**.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα τμήματα παίρνουμε ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, να μεταγλωττίσετε και να εκτελέσετε:

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to style footnotes in a Word document using Aspose.Words for Java.
 * The example loads a document, makes the footnote separator bold and blue,
 * optionally styles continuation elements, and saves the result.
 */
public class FootnoteStyler {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");

        // 2. Iterate through each footnote.
        for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
            // 3a. Access and style the primary separator.
            Run separator = footnote.getSeparator();
            if (separator != null) {
                separator.getFont().setBold(true);          // change footnote separator
                separator.getFont().setColor(Color.BLUE);   // set a custom color
                separator.getFont().setUnderline(Underline.SINGLE);
            }

            // 3b. (Optional) Style continuation separator.
            Run contSeparator = footnote.getContinuationSeparator();
            if (contSeparator != null) {
                contSeparator.getFont().setItalic(true);
                contSeparator.getFont().setSize(9);
            }

            // 3c. (Optional) Style continuation notice.
            Run contNotice = footnote.getContinuationNotice();
            if (contNotice != null) {
                contNotice.getFont().setColor(Color.GRAY);
            }
        }

        // 4. Save the modified document.
        doc.save("YOUR_DIRECTORY/FootnotesStyled.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `FootnotesStyled.docx` στο Microsoft Word. Η γραμμή διαχωριστικού μεταξύ του κυρίου κειμένου και της λίστας υποσημειώσεων εμφανίζεται έντονη, μπλε και υπογραμμισμένη. Αν το έγγραφο περιέχει υποσημειώσεις που εκτείνονται σε πολλές σελίδες, το διαχωριστικό συνέχειας θα είναι πλάγιο και μικρότερο, ενώ η σημείωση συνέχειας θα εμφανίζεται σε γκρι.

## Συχνές ερωτήσεις και αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|----------|
| *Τι γίνεται αν μια υποσημείωση δεν έχει διαχωριστικό;* | Το `Footnote.getSeparator()` επιστρέφει `null`. Ο κώδικας ελέγχει για `null` πριν εφαρμόσει τη μορφοποίηση, αποτρέποντας `NullPointerException`. |
| *Μπορώ να εφαρμόσω διαφορετικό στυλ μόνο στην πρώτη υποσημείωση;* | Ναι. Προσθέστε έναν μετρητή μέσα στον βρόχο και εφαρμόστε υπό συνθήκη μορφοποίηση όταν `index == 0`. |
| *Λειτουργεί αυτό με αρχεία .doc;* | Το Aspose.Words υποστηρίζει τόσο `.doc` όσο και `.docx`. Φορτώστε το αντίστοιχο μονοπάτι και οι ίδιες κλήσεις API ισχύουν. |
| *Πώς επαναφέρω το αρχικό στυλ;* | Αποθηκεύστε το αρχικό `Font` |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to Change Cell Borders in Tables – Aspose.Words for Java](/words/english/java/document-conversion-and-export/formatting-tables-and-table-styles/)
- [How to Add Watermark – Document Conversion and Export with Aspose.Words for Java](/words/english/java/document-conversion-and-export/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}