---
category: general
date: 2026-09-11
description: Μάθετε πώς να αλλάζετε τη μορφοποίηση των υποσημειώσεων σε Java με το
  Aspose.Words. Αυτός ο οδηγός εξηγεί πώς να επεξεργαστείτε την υποσημείωση, να ενημερώσετε
  το στυλ της υποσημείωσης και να τροποποιήσετε το διαχωριστικό των υποσημειώσεων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: el
lastmod: 2026-09-11
og_description: Αλλάξτε τη μορφοποίηση των υποσημειώσεων σε Java με το Aspose.Words.
  Ακολουθήστε αυτόν τον πλήρη οδηγό για να επεξεργαστείτε την υποσημείωση, να ενημερώσετε
  το στυλ της υποσημείωσης και να τροποποιήσετε το διαχωριστικό υποσημειώσεων.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Αλλαγή μορφοποίησης υποσημειώσεων σε Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Πώς να αλλάξετε τη μορφοποίηση υποσημειώσεων σε έγγραφο Word χρησιμοποιώντας
  Java
url: /el/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αλλάξετε τη μορφοποίηση των υποσημειώσεων σε ένα έγγραφο Word χρησιμοποιώντας Java

Αν χρειάζεστε **αλλαγή μορφοποίησης υποσημειώσεων** σε ένα έγγραφο Word, αυτό το tutorial σας καθοδηγεί βήμα προς βήμα χρησιμοποιώντας το Aspose.Words for Java. Είτε δημιουργείτε μια αλυσίδα δημοσίευσης είτε απλώς χρειάζεστε **πώς να επεξεργαστείτε την εμφάνιση των υποσημειώσεων** προγραμματιστικά, η παρακάτω λύση καλύπτει τα πάντα, από τη φόρτωση του αρχείου μέχρι την αποθήκευση της ενημερωμένης έκδοσης.

Θα μάθετε πώς να **ενημερώσετε το στυλ των υποσημειώσεων**, να κάνετε το διαχωριστικό των υποσημειώσεων έντονο, και ακόμη **να τροποποιήσετε τις ιδιότητες του διαχωριστικού υποσημειώσεων** όπως το μέγεθος ή το χρώμα της γραμματοσειράς. Ο οδηγός υποθέτει ότι έχετε βασικές γνώσεις Java και μια ενεργή άδεια Aspose.Words for Java.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη εγκατεστημένη.
* Aspose.Words for Java (έκδοση 23.12 ή νεότερη) προστιθέμενη στο classpath του έργου σας.
* Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον μία υποσημείωση.
* Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) για τη μεταγλώττιση και εκτέλεση του κώδικα.

Αν δεν είστε σίγουροι πώς να προσθέσετε το Aspose.Words σε ένα έργο Maven, συμπεριλάβετε την ακόλουθη εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Αλλαγή μορφοποίησης υποσημειώσεων με το Aspose.Words for Java

Ο πυρήνας της λύσης είναι ένα σύντομο πρόγραμμα Java που φορτώνει ένα έγγραφο, προσπελαύνει την παράγραφο του διαχωριστικού υποσημειώσεων, αλλάζει τη μορφοποίησή του και αποθηκεύει το αποτέλεσμα. Ο κώδικας είναι πλήρως αυτόνομος, ώστε να μπορείτε να τον αντιγράψετε σε μια νέα κλάση και να τον εκτελέσετε αμέσως.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Γιατί κάθε βήμα είναι σημαντικό

* **Φόρτωση του εγγράφου** (`new Document`) δημιουργεί μια αναπαράσταση στη μνήμη που μπορεί να χειριστεί το Aspose.Words.  
* **Ανάκτηση του διαχωριστικού υποσημειώσεων** (`getFootnoteSeparator`) σας δίνει άμεση πρόσβαση στην παράγραφο που χωρίζει τις υποσημειώσεις από το κύριο κείμενο. Αυτό είναι το στοιχείο που πρέπει να στοχεύσετε όταν θέλετε να **αλλάξετε τη μορφοποίηση των υποσημειώσεων**.  
* **Μορφοποίηση του τμήματος κειμένου (run)** (`setBold`, `setItalic`, `setSize`, `setColor`) δείχνει πώς να **τροποποιήσετε τις ιδιότητες του διαχωριστικού υποσημειώσεων**. Μπορείτε να προσθέσετε οποιεσδήποτε επιπλέον ιδιότητες γραμματοσειράς εδώ, όπως υπογράμμιση ή επισήμανση, για πλήρη έλεγχο της εμφάνισης.  
* **Αποθήκευση του εγγράφου** γράφει τις αλλαγές πίσω στο δίσκο, δημιουργώντας ένα νέο αρχείο (`output.docx`) που αντικατοπτρίζει το ενημερωμένο στυλ υποσημειώσεων.

> **Συμβουλή:** Εάν το πηγαίο σας έγγραφο χρησιμοποιεί ένα προσαρμοσμένο διαχωριστικό υποσημειώσεων που περιέχει πολλαπλά τμήματα (π.χ., συνδυασμό συμβόλων), κάντε βρόχο μέσω `footnoteSeparator.getRuns()` και εφαρμόστε τις ίδιες ρυθμίσεις `Font` σε κάθε τμήμα για συνεπή στυλ.

## Πώς να επεξεργαστείτε το διαχωριστικό υποσημειώσεων προγραμματιστικά

Μερικές φορές μπορεί να χρειαστεί να επεξεργαστείτε όχι μόνο το διαχωριστικό αλλά και το κείμενο της υποσημείωσης. Το ίδιο API μπορεί να χρησιμοποιηθεί για την πρόσβαση σε κάθε υποσημείωση, την προσαρμογή της μορφοποίησης της παραγράφου της ή την αλλαγή του στυλ αρίθμησης.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

Το παραπάνω απόσπασμα δείχνει **πώς να επεξεργαστείτε τα σώματα των υποσημειώσεων** μετά την **αλλαγή μορφοποίησης των υποσημειώσεων** για το διαχωριστικό. Με την επανάληψη πάνω από `doc.getFootnotes()`, εξασφαλίζετε ότι κάθε υποσημείωση κληρονομεί το ίδιο στυλ, κάτι που είναι απαραίτητο για ένα επαγγελματικό έγγραφο.

## Ενημέρωση στυλ υποσημειώσεων για συνεπή εμφάνιση εγγράφου

Αν προτιμάτε να εργάζεστε με στυλ αντί για μεμονωμένα τμήματα, το Aspose.Words σας επιτρέπει να δημιουργήσετε ή να τροποποιήσετε ένα αντικείμενο `Style` και στη συνέχεια να το εφαρμόσετε στις υποσημειώσεις και το διαχωριστικό. Αυτή η προσέγγιση είναι χρήσιμη όταν χρειάζεται να **ενημερώσετε το στυλ των υποσημειώσεων** σε πολλά έγγραφα.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Η χρήση ενός αφιερωμένου στυλ καθιστά τη μελλοντική συντήρηση πιο εύκολη — αλλάξτε το στυλ μία φορά και κάθε υποσημείωση και διαχωριστικό θα ενημερωθούν αυτόματα. Αυτή η τεχνική είναι ο προτεινόμενος τρόπος για **ενημέρωση του στυλ των υποσημειώσεων** σε μεγάλης κλίμακας ροές εργασίας δημοσίευσης.

## Τροποποίηση του διαχωριστικού υποσημειώσεων ώστε να ταιριάζει με το branding σας

Οι οδηγίες branding μερικές φορές απαιτούν το διαχωριστικό υποσημειώσεων να χρησιμοποιεί έναν συγκεκριμένο χαρακτήρα (π.χ., αστερίσκο) ή μια προσαρμοσμένη γραμμή. Το Aspose.Words επιτρέπει την πλήρη αντικατάσταση του προεπιλεγμένου περιεχομένου του διαχωριστικού.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

Ο παραπάνω κώδικας **τροποποιεί το διαχωριστικό υποσημειώσεων** καθαρίζοντας τυχόν υπάρχοντα τμήματα και εισάγοντας ένα νέο τμήμα με το επιθυμητό κείμενο και μορφοποίηση. Μπορείτε επίσης να χρησιμοποιήσετε χαρακτήρες Unicode όπως `\u2022` (κουκίδα) ή `\u2014` (παύλα) για να πετύχετε το ακριβές οπτικό αποτέλεσμα που απαιτεί το brand σας.

## Αναμενόμενο αποτέλεσμα

Μετά την εκτέλεση του προγράμματος:

* Το διαχωριστικό υποσημειώσεων στο `output.docx` εμφανίζεται **έντονο**, **πλάγιο**, 10 pt, και γκρι (ή οποιοδήποτε χρώμα έχετε ορίσει).  
* Όλες οι παράγραφοι υποσημειώσεων υιοθετούν το στυλ που ορίσατε, εξασφαλίζοντας ομοιόμορφη εμφάνιση σε όλο το έγγραφο.  
* Εάν αντικαταστήσατε το κείμενο του διαχωριστικού, η νέα προσαρμοσμένη γραμμή είναι ορατή ακριβώς εκεί που ήταν η αρχική γραμμή.

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word ή στο LibreOffice Writer για να επαληθεύσετε τις αλλαγές. Θα πρέπει να δείτε το ενημερωμένο διαχωριστικό ακριβώς πάνω από την πρώτη υποσημείωση, και το κείμενο της υποσημείωσης να αντανακλά τυχόν τροποποιήσεις στυλ που εφαρμόσατε.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| ``footnoteSeparator.getRuns().getCount() == 0`` προκαλεί εξαίρεση | Κάποια έγγραφα έχουν κενή παράγραφο διαχωριστικού. | Προσθέστε έναν έλεγχο ασφαλείας και δημιουργήστε ένα τμήμα εάν δεν υπάρχει (δείτε το παράδειγμα κώδικα). |
| Οι αλλαγές γραμματοσειράς δεν είναι ορατές | Το έγγραφο χρησιμοποιεί ένα θέμα που υπερισχύει της άμεσης μορφοποίησης. | Ορίστε `font.setThemeFont(null)` ή εφαρμόστε ένα προσαρμοσμένο στυλ αντί για άμεση μορφοποίηση. |
| Το αποθηκευμένο αρχείο δεν αντικατοπτρίζει τις αλλαγές | Το αρχικό αρχείο είναι ακόμη ανοιχτό στο Word, κλειδώνουν τη διαδρομή εξόδου. | Κλείστε τυχόν ανοιχτές παρουσίες του αρχείου πριν εκτελέσετε το πρόγραμμα, ή |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Επεξεργασία κειμένου με υποσημειώσεις και σημειώσεις τέλους](/words/english/net/working-with-footnote-and-endnote/)
- [Ορισμός θέσης υποσημείωσης και σημείωσης τέλους](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Πώς να εμφανίσετε πληροφορίες έκδοσης Aspose.Words σε Java: Ένας ολοκληρωμένος οδηγός](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}