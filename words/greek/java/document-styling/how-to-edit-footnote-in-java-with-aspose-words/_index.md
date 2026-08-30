---
category: general
date: 2026-08-07
description: Πώς να επεξεργαστείτε υποσημείωση σε Java με το Aspose.Words – προσθέστε
  προσαρμοσμένη παύλα, αλλάξτε τη γραμμή υποσημείωσης και ορίστε την ευθυγράμμιση
  παραγράφου για άψογα έγγραφα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: el
lastmod: 2026-08-07
og_description: Πώς να επεξεργαστείτε τη υποσημείωση σε Java με το Aspose.Words. Μάθετε
  πώς να προσθέσετε ένα προσαρμοσμένο παύλο, να αλλάξετε τη γραμμή της υποσημείωσης
  και να ορίσετε την στοίχιση της παραγράφου σε λίγα μόνο βήματα.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Πώς να επεξεργαστείτε τη υποσημείωση σε Java – προσθήκη παύλας, αλλαγή γραμμής,
  ρύθμιση ευθυγράμμισης
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Πώς να επεξεργαστείτε το υποσημείωμα σε Java με το Aspose.Words
url: /el/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να επεξεργαστείτε υποσημείωση σε Java με Aspose.Words

Αν χρειάζεστε **πώς να επεξεργαστείτε υποσημείωση** σε ένα έγγραφο Word χρησιμοποιώντας Java, αυτός ο οδηγός δείχνει τη πλήρη ροή εργασίας. Θα μάθετε να προσθέτετε ένα προσαρμοσμένο παύλο, να αλλάζετε τη γραμμή της υποσημείωσης και να ορίζετε την ευθυγράμμιση παραγράφου ώστε ο διαχωριστής υποσημείωσης να φαίνεται επαγγελματικός.

Η επεξεργασία υποσημειώσεων είναι συχνή απαίτηση όταν ετοιμάζετε νομικά συμβόλαια, ακαδημαϊκές εργασίες ή διαφημιστικά φυλλάδια. Τα παρακάτω βήματα καλύπτουν όλα όσα χρειάζεστε—από τη φόρτωση του εγγράφου μέχρι την αποθήκευση του τελικού αρχείου—χωρίς να απαιτούν πρόσθετα εργαλεία.

## Προαπαιτούμενα

* Java 17 ή νεότερη εγκατεστημένη.
* Aspose.Words for Java (τελευταία έκδοση) προστιθέμενη στο classpath του έργου σας.
* Ένα αρχείο DOCX (`input.docx`) που περιέχει τουλάχιστον μία υποσημείωση.

Αυτά τα στοιχεία εγγυώνται ότι ο κώδικας εκτελείται χωρίς σφάλματα χρόνου εκτέλεσης.

## Πώς να επεξεργαστείτε το διαχωριστικό και τη γραμμή υποσημείωσης

Το διαχωριστικό υποσημείωσης είναι η παράγραφος που εμφανίζεται μεταξύ του κυρίως κειμένου και της λίστας υποσημειώσεων. Η αλλαγή της εμφάνισής του βελτιώνει την αναγνωσιμότητα και ταιριάζει με το εταιρικό branding.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Γιατί κάθε γραμμή έχει σημασία

1. **Φόρτωση του εγγράφου** – `new Document(...)` διαβάζει το αρχείο DOCX στη μνήμη, δίνοντάς σας πρόσβαση σε όλους τους κόμβους του.
2. **Ανάκτηση του διαχωριστικού** – `getFootnoteSeparator()` επιστρέφει την ειδική παράγραφο που το Aspose.Words θεωρεί ως τη γραμμή υποσημείωσης. Αυτό το αντικείμενο είναι το μοναδικό σημείο όπου μπορείτε να τροποποιήσετε με ασφάλεια το διαχωριστικό.
3. **Ορισμός ευθυγράμμισης παραγράφου** – `setAlignment(ParagraphAlignment.CENTER)` αλλάζει την ευθυγράμμιση της γραμμής. Η λέξη-κλειδί *set paragraph alignment* εφαρμόζεται απευθείας στο διαχωριστικό, εξασφαλίζοντας ένα κεντραρισμένο παύλο.
4. **Προσθήκη προσαρμοσμένου παύλου** – Καθαρίζοντας τα υπάρχοντα runs και προσθέτοντας ένα νέο `Run` με τον χαρακτήρα em‑dash (`—`), επιτυγχάνετε το *add custom dash* εφέ ενώ ταυτόχρονα *change footnote line* στο επιθυμητό στυλ.
5. **Αποθήκευση του εγγράφου** – `doc.save(...)` γράφει τις αλλαγές πίσω στο δίσκο, δημιουργώντας ένα αρχείο εξόδου που αντανακλά όλες τις τροποποιήσεις.

## Προσθήκη προσαρμοσμένου παύλου στο διαχωριστικό υποσημείωσης

Ο κώδικας στην **Step 4** δείχνει την τεχνική *add custom dash*. Μπορείτε να αντικαταστήσετε το em‑dash με οποιαδήποτε συμβολοσειρά, όπως `"***"` ή `"---"`, ώστε να ταιριάζει με τη οπτική γλώσσα του εγγράφου σας.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Η χρήση προσαρμοσμένου παύλου είναι ιδιαίτερα χρήσιμη όταν η προεπιλεγμένη λεπτή γραμμή δεν πληροί τις οδηγίες branding.

## Αλλαγή στυλ γραμμής υποσημείωσης

Αν προτιμάτε μια στερεή γραμμή αντί για παύλο, μπορείτε να εισάγετε έναν Unicode χαρακτήρα γραμμής ή ένα επαναλαμβανόμενο underscore.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

Το βήμα *change footnote line* λειτουργεί με τον ίδιο τρόπο ανεξάρτητα από τον χαρακτήρα που επιλέγετε, επειδή η παράγραφος διαχωριστικού απλώς εμφανίζει το κείμενο που περιέχει.

## Ορισμός ευθυγράμμισης παραγράφου για το διαχωριστικό υποσημείωσης

Η λειτουργία *set paragraph alignment* δεν περιορίζεται στην κεντρική ευθυγράμμιση. Μπορείτε να ευθυγραμμίσετε αριστερά, δεξιά ή να κάνετε πλήρη στοίχιση ανάλογα με τις ανάγκες διάταξης.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Η στοίχιση του διαχωριστικού προς τα δεξιά μπορεί να είναι χρήσιμη για έγγραφα που χρησιμοποιούν υποσημειώσεις δεξιά‑ευθυγραμμισμένες, όπως δίγλωσσα δημοσιεύματα.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που ενσωματώνει όλες τις έννοιες—φόρτωση εγγράφου, επεξεργασία του διαχωριστικού υποσημείωσης, προσθήκη προσαρμοσμένου παύλου, αλλαγή στυλ γραμμής και ορισμός ευθυγράμμισης.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το αρχείο `output.docx` περιέχει ένα κεντραρισμένο em‑dash εκεί όπου υπήρχε η αρχική λεπτή γραμμή. Όλες οι υποσημειώσεις παραμένουν αμετάβλητες και η διάταξη του εγγράφου αντανακλά το νέο στυλ διαχωριστικού.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Δεν βρέθηκε το διαχωριστικό | Το έγγραφο δεν έχει υποσημειώσεις ή χρησιμοποιεί προσαρμοσμένο στυλ υποσημείωσης | Βεβαιωθείτε ότι το αρχικό DOCX περιέχει τουλάχιστον μία υποσημείωση πριν καλέσετε `getFootnoteSeparator()` |
| Το προσαρμοσμένο παύλο δεν εμφανίζεται | Η γραμματοσειρά δεν υποστηρίζει τον επιλεγμένο χαρακτήρα | Χρησιμοποιήστε έναν Unicode χαρακτήρα που υποστηρίζεται από την προεπιλεγμένη γραμματοσειρά του εγγράφου ή ενσωματώστε μια συμβατή γραμματοσειρά |
| Η ευθυγράμμιση δεν αλλάζει | Η μορφοποίηση της παραγράφου παρακάμπτεται αργότερα στον κώδικα | Εφαρμόστε την ευθυγράμμιση **μετά** από οποιεσδήποτε άλλες κλήσεις μορφοποίησης που μπορεί να την επαναφέρουν |

Η αντιμετώπιση αυτών των σημείων αποτρέπει σφάλματα χρόνου εκτέλεσης και εγγυάται ότι η *πώς να επεξεργαστείτε υποσημείωση* διαδικασία λειτουργεί αξιόπιστα.

## Επόμενα βήματα

Τώρα που γνωρίζετε **πώς να επεξεργαστείτε υποσημείωση** στοιχεία, μπορείτε να εξερευνήσετε σχετικές εργασίες:

* **Προσθήκη προσαρμοσμένου στυλ αναφοράς υποσημείωσης** – τροποποιήστε κόμβους `FootnoteReference` για να αλλάξετε την αρίθμηση ή τα σύμβολα.
* **Προγραμματιστική εισαγωγή νέων υποσημειώσεων** – χρησιμοποιήστε `DocumentBuilder.insertFootnote()` για δυναμικό περιεχόμενο.
* **Εφαρμογή υπό όρους μορφοποίησης** – αλλάξτε την εμφάνιση της υποσημείωσης βάσει του στυλ παραγράφου ή του μήκους του περιεχομένου.

Κάθε μία από αυτές τις επεκτάσεις βασίζεται στην ίδια επιφάνεια API που χρησιμοποιήσατε για *add custom dash*, *change footnote line* και *set paragraph alignment*.

---

*Καλό κώδικα! Αν ο οδηγός σας βοήθησε να κατακτήσετε την επεξεργασία υποσημειώσεων, σκεφτείτε να τον μοιραστείτε με την ομάδα σας ή να συνεισφέρετε με ένα pull request για να βελτιώσετε περαιτέρω το παράδειγμα.*

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω εκπαιδευτικές ενότητες καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}