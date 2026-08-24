---
category: general
date: 2026-08-23
description: Αποθηκεύστε το Word ως markdown σε Java ενώ εξάγετε πίνακες ως HTML.
  Μάθετε πώς να μετατρέπετε docx σε markdown, να εξάγετε πίνακες Word σε HTML και
  να ενσωματώνετε πίνακες HTML χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as markdown
- convert docx to markdown
- export word tables html
- convert word tables html
- export tables as html
language: el
lastmod: 2026-08-23
og_description: Αποθηκεύστε το Word ως markdown σε Java και εξάγετε πίνακες ως HTML.
  Αυτός ο οδηγός δείχνει πώς να μετατρέψετε docx σε markdown, να εξάγετε πίνακες Word
  σε HTML και να ενσωματώσετε πίνακες HTML σε markdown.
og_image_alt: Screenshot of Java code exporting Word tables as HTML in a markdown
  file
og_title: Αποθήκευση Word ως markdown με πίνακες HTML – Οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Save Word as markdown in Java while exporting tables as HTML. Learn
    to convert docx to markdown, export word tables html, and embed HTML tables using
    Aspose.Words.
  headline: How to save Word as markdown with HTML tables in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Markdown
- HTML tables
title: Πώς να αποθηκεύσετε το Word ως markdown με πίνακες HTML σε Java
url: /el/java/document-conversion-and-export/how-to-save-word-as-markdown-with-html-tables-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε το Word ως markdown με πίνακες HTML σε Java

Αν χρειάζεστε να **αποθηκεύσετε το Word ως markdown** διατηρώντας σύνθετους πίνακες, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε. Χρησιμοποιώντας το Aspose.Words for Java μπορείτε να **convert docx to markdown** και **export word tables html** ώστε οι πίνακες να αποδίδονται σωστά στο παραγόμενο αρχείο markdown.

Η μετατροπή εγγράφων είναι μια συνηθισμένη εργασία όταν θέλετε να δημοσιεύσετε περιεχόμενο σε γεννήτριες static‑site ή πύλες τεκμηρίωσης που καταλαβαίνουν μόνο markdown. Αυτός ο οδηγός σας καθοδηγεί βήμα προς βήμα, από τη φόρτωση ενός αρχείου `.docx` μέχρι τη διαμόρφωση του `MarkdownSaveOptions` ώστε οι πίνακες να εμφανίζονται ως HTML. Στο τέλος θα έχετε ένα πλήρως λειτουργικό αρχείο markdown που περιλαμβάνει τους αρχικούς πίνακες του Word ως ενσωματωμένο HTML.

## Τι θα μάθετε

* Πώς να φορτώσετε ένα έγγραφο Word και να το προετοιμάσετε για μετατροπή.  
* Πώς να ορίσετε το `MarkdownSaveOptions` ώστε **export tables as html**.  
* Πώς να **convert docx to markdown** και να επαληθεύσετε το αποτέλεσμα.  
* Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως ένθετοι πίνακες ή μεγάλες εικόνες.

### Προαπαιτούμενα

| Απαίτηση | Αιτιολόγηση |
|----------|-------------|
| Java 17 ή νεότερη | Το Aspose.Words for Java απαιτεί Java 8+· η χρήση της τελευταίας LTS εξασφαλίζει συμβατότητα. |
| Βιβλιοθήκη Aspose.Words for Java (v23.10 ή νεότερη) | Παρέχει τις κλάσεις `Document`, `MarkdownSaveOptions` και `MarkdownExportAsHtml`. |
| Ένα αρχείο `.docx` που περιέχει τουλάχιστον έναν πίνακα | Δείχνει τη λειτουργία **export word tables html**. |
| Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) | Για τη μεταγλώττιση και εκτέλεση του παραδείγματος κώδικα. |

Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` (Maven) ή στο `build.gradle` (Gradle) πριν προχωρήσετε.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Βήμα 1: Φορτώστε το πηγαίο έγγραφο Word – αποθηκεύστε το Word ως markdown

Το πρώτο βήμα είναι να δημιουργήσετε μια παρουσία `Aspose.Words.Document` που αντιπροσωπεύει το `.docx` που θέλετε να μετατρέψετε. Αυτό το αντικείμενο είναι το σημείο εισόδου για όλες τις επόμενες λειτουργίες.

```java
import com.aspose.words.*;

public class ExportTablesAsHtmlDemo {
    public static void main(String[] args) throws Exception {
        // Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί είναι σημαντικό:* Η φόρτωση του εγγράφου σας δίνει πρόσβαση στην εσωτερική του δομή (παράγραφοι, πίνακες, εικόνες). Χωρίς μια κατάλληλη παρουσία `Document` δεν μπορείτε να εφαρμόσετε τις επιλογές **convert docx to markdown**.

## Βήμα 2: Διαμορφώστε το MarkdownSaveOptions – export word tables html

Το Aspose.Words σας επιτρέπει να ελέγξετε πώς θα αποδίδεται κάθε στοιχείο κατά τη μετατροπή. Ορίζοντας το `MarkdownExportAsHtml.TABLES` λέτε στη μηχανή να αποδίδει κάθε πίνακα Word ως ετικέτα HTML `<table>` μέσα στο αρχείο markdown.

```java
        // Set Markdown save options to export tables as HTML
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        // Tables will be rendered as raw HTML inside the markdown output
        saveOptions.setExportAsHtml(MarkdownExportAsHtml.TABLES);
```

*Γιατί είναι σημαντικό:* Το Markdown έχει περιορισμένη σύνταξη πινάκων και δεν μπορεί να αναπαραστήσει αξιόπιστα συγχωνευμένα κελιά ή σύνθετες διατάξεις. Με το **export tables as html**, διατηρείτε την αρχική εμφάνιση, κάτι που είναι ιδιαίτερα χρήσιμο για τεχνική τεκμηρίωση ή blogs που υποστηρίζουν ενσωματωμένο HTML.

## Βήμα 3: Αποθηκεύστε το έγγραφο – convert docx to markdown

Τώρα καλείτε τη μέθοδο `save`, περνώντας το όνομα του αρχείου markdown-στόχου και τις διαμορφωμένες επιλογές. Η βιβλιοθήκη γράφει ένα αρχείο `.md` όπου το κανονικό κείμενο εμφανίζεται ως markdown και κάθε πίνακας εμφανίζεται ως απόσπασμα HTML.

```java
        // Save the document as a Markdown file with embedded HTML tables
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Όταν το πρόγραμμα ολοκληρωθεί, το `output.md` θα περιέχει κάτι όπως:

```markdown
# Sample Document

This is a paragraph from the original Word file.

<table>
  <tr>
    <th>Header 1</th>
    <th>Header 2</th>
  </tr>
  <tr>
    <td>Row 1, Cell 1</td>
    <td>Row 1, Cell 2</td>
  </tr>
</table>

Another paragraph follows the table.
```

*Γιατί είναι σημαντικό:* Το βήμα **convert docx to markdown** ολοκληρώθηκε, και έχετε ένα αρχείο markdown που μπορεί να αποδοθεί από οποιαδήποτε γεννήτρια static‑site που επιτρέπει ακατέργαστο HTML.

## Βήμα 4: Επαληθεύστε το αποτέλεσμα (προαιρετικό αλλά συνιστάται)

Ανοίξτε το `output.md` σε έναν προβολέα markdown που υποστηρίζει HTML (π.χ., προεπισκόπηση VS Code, GitHub ή MkDocs). Θα πρέπει να δείτε τον πίνακα να αποδίδεται ακριβώς όπως εμφανίστηκε στο Word.

Αν ο πίνακας δεν εμφανίζεται σωστά:

* Βεβαιωθείτε ότι ο προβολέας σας επιτρέπει HTML μέσα στο markdown. Ορισμένες πλατφόρμες (π.χ., ορισμένοι αποτυπωτές README του GitHub) αφαιρούν το HTML για λόγους ασφαλείας.
* Ελέγξτε ότι το αρχικό `.docx` δεν περιέχει μη υποστηριζόμενα στοιχεία όπως ένθετοι πίνακες· το Aspose.Words θα τα εξακολουθήσει να εξάγει ως HTML, αλλά το περιβάλλον markdown μπορεί να χρειάζεται χειροκίνητες προσαρμογές.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Εξήγηση | Διόρθωση |
|----------|----------|----------|
| **Οι πίνακες εξαφανίζονται** | Ο προβολέας αφαίρεσε τις ετικέτες HTML. | Χρησιμοποιήστε έναν προβολέα που επιτρέπει HTML ή ενεργοποιήστε τη σημαία `allowHtml` εάν η πλατφόρμα σας την παρέχει. |
| **Τα συγχωνευμένα κελιά γίνονται ξεχωριστά κελιά** | Ορισμένοι μεταγλωττιστές markdown αγνοούν τα `colspan`/`rowspan`. | Επειδή **export tables as html**, το HTML διατηρεί αυτά τα χαρακτηριστικά· απλώς βεβαιωθείτε ότι ο επεξεργαστής markdown τα σέβεται. |
| **Οι μεγάλες εικόνες διαταράσσουν τη διάταξη** | Οι εικόνες αποθηκεύονται ως ξεχωριστά αρχεία και αναφέρονται με σχετικές διαδρομές. | Τοποθετήστε τις εικόνες στον ίδιο φάκελο με το αρχείο markdown ή προσαρμόστε τις διαδρομές εικόνας στο παραγόμενο markdown. |
| **Μείωση απόδοσης σε τεράστια έγγραφα** | Η μετατροπή ενός αρχείου Word 500 σελίδων μπορεί να απαιτεί πολύ μνήμη. | Επεξεργαστείτε το έγγραφο σε ενότητες ή αυξήστε το μέγεθος του heap της JVM (`-Xmx2g`). |

## Συμβουλή: Επαναχρησιμοποίηση των ίδιων επιλογών για πολλαπλά έγγραφα

Αν χρειάζεται να μετατρέψετε μαζικά πολλά αρχεία Word, δημιουργήστε μια βοηθητική μέθοδο που επιστρέφει μια προ‑διαμορφωμένη παρουσία `MarkdownSaveOptions`. Αυτό εξασφαλίζει ότι το **export tables as html** εφαρμόζεται σταθερά.

```java
private static MarkdownSaveOptions getMarkdownOptions() {
    MarkdownSaveOptions options = new MarkdownSaveOptions();
    options.setExportAsHtml(MarkdownExportAsHtml.TABLES);
    return options;
}
```

Στη συνέχεια καλέστε `doc.save(outputPath, getMarkdownOptions());` για κάθε αρχείο.

## Επόμενα βήματα

* **Convert Word tables to other formats** – Το Aspose.Words υποστηρίζει επίσης εξαγωγή πινάκων ως CSV ή απλό κείμενο μέσω του `MarkdownExportAsHtml.NONE` σε συνδυασμό με προσαρμοσμένη μετα‑επεξεργασία.  
* **Customize styling** – Χρησιμοποιήστε κλάσεις CSS μέσα στους παραγόμενους πίνακες HTML για να ταιριάζουν με το σχεδιασμό του ιστότοπού σας.  
* **Integrate with static site generators** – Αυτοματοποιήστε τη μετατροπή ως μέρος της CI pipeline ώστε κάθε νέο `.docx` να μετατρέπεται αυτόματα σε σελίδα markdown με τέλεια απόδοση πινάκων.

---

### Συμπέρασμα

Τώρα ξέρετε πώς να **save Word as markdown** σε Java ενώ **exporting tables as html**. Διαμορφώνοντας το `MarkdownSaveOptions` με `MarkdownExportAsHtml.TABLES`, μπορείτε αξιόπιστα να **convert docx to markdown**, να διατηρήσετε τους σύνθετους πίνακες ανέπαφους και να τους ενσωματώσετε απευθείας στην έξοδο markdown. Εφαρμόστε τις παραπάνω συμβουλές για να διαχειριστείτε ειδικές περιπτώσεις, και θα έχετε μια ισχυρή διαδικασία για τη δημοσίευση περιεχομένου βασισμένου σε Word σε οποιαδήποτε πλατφόρμα φιλική προς το markdown.

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να εξάγετε LaTeX από το Word: Μετατροπή DOCX σε Markdown & Αποθήκευση ως PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)
- [Μετατροπή Word σε HTML και Διαχωρισμός Εγγράφων σε Σελίδες HTML με Aspose.Words for Java](/words/english/java/document-manipulation/splitting-documents-into-html-pages/)
- [Πώς να φορτώσετε HTML και να αποθηκεύσετε ως DOCX χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}