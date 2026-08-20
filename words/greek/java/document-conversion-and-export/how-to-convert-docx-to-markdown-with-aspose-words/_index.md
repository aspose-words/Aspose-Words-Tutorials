---
category: general
date: 2026-08-20
description: Μάθετε πώς να μετατρέπετε αρχεία docx σε markdown και να εξάγετε πίνακες
  Word ως html χρησιμοποιώντας το Aspose.Words. Οδηγός βήμα‑βήμα για αξιόπιστη μετατροπή
  Word‑σε‑Markdown.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to markdown
- how to convert word to markdown
- export word tables as html
language: el
lastmod: 2026-08-20
og_description: Μετατρέψτε το docx σε markdown και εξάγετε τους πίνακες του Word ως
  html με το Aspose.Words. Αυτό το σεμινάριο δείχνει τον ακριβή κώδικα που χρειάζεστε.
og_image_alt: Screenshot of a DOCX file being saved as a Markdown file with HTML tables
og_title: Μετατροπή docx σε markdown – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to convert docx to markdown and export word tables as html
    using Aspose.Words. Step‑by‑step guide for reliable Word‑to‑Markdown conversion.
  headline: How to convert docx to markdown with Aspose.Words
  type: TechArticle
- description: Learn how to convert docx to markdown and export word tables as html
    using Aspose.Words. Step‑by‑step guide for reliable Word‑to‑Markdown conversion.
  name: How to convert docx to markdown with Aspose.Words
  steps:
  - name: '**Path variables** – Change `YOUR_DIRECTORY` to the folder that holds your
      DOCX file.'
    text: '**Path variables** – Change `YOUR_DIRECTORY` to the folder that holds your
      DOCX file.'
  - name: '**`Document` constructor** – Reads the Word file into memory.'
    text: '**`Document` constructor** – Reads the Word file into memory.'
  - name: '**`MarkdownSaveOptions`** – Sets the crucial `setExportAsHtml` flag so
      tables become HTML.'
    text: '**`MarkdownSaveOptions`** – Sets the crucial `setExportAsHtml` flag so
      tables become HTML.'
  - name: '**`save` call** – Writes the final Markdown file.'
    text: '**`save` call** – Writes the final Markdown file.'
  - name: '**Exception handling** – Catches any IO or Aspose.Words errors and prints
      a helpful message.'
    text: '**Exception handling** – Catches any IO or Aspose.Words errors and prints
      a helpful message.'
  type: HowTo
tags:
- docx conversion
- markdown export
- Aspose.Words
title: Πώς να μετατρέψετε το docx σε markdown με το Aspose.Words
url: /el/java/document-conversion-and-export/how-to-convert-docx-to-markdown-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μετατρέψετε docx σε markdown με Aspose.Words

Αν χρειάζεστε **convert docx to markdown**, αυτό το tutorial σας δείχνει έναν αξιόπιστο τρόπο για να το κάνετε χρησιμοποιώντας το Aspose.Words for Java. Θα δείτε πώς να φορτώσετε ένα έγγραφο Word, να διαμορφώσετε τις επιλογές αποθήκευσης Markdown ώστε οι πίνακες να εξαχθούν ως HTML, και να γράψετε το αποτέλεσμα σε ένα αρχείο .md. Στο τέλος θα έχετε ένα έτοιμο προς χρήση αρχείο Markdown που διατηρεί πολύπλοκες διατάξεις πινάκων.

Η μετατροπή αρχείων Word σε μορφές ελαφρού markup είναι μια συχνή απαίτηση για static‑site generators, pipelines τεκμηρίωσης και μεταφορές διαχείρισης περιεχομένου. Αυτός ο οδηγός καλύπτει όλα όσα χρειάζεστε — προαπαιτήσεις, πλήρες κώδικα, διαχείριση edge‑case, και συμβουλές για προσαρμογή της εξόδου.

## Προαπαιτήσεις

- Java 8 ή νεότερη έκδοση εγκατεστημένη.
- Ένα έργο Maven ή Gradle όπου μπορείτε να προσθέσετε την εξάρτηση Aspose.Words for Java.
- Ένα αρχείο DOCX που θέλετε να μετατρέψετε (το παράδειγμα χρησιμοποιεί `input.docx`).
- Βασική εξοικείωση με την ανάπτυξη Java και IDEs όπως IntelliJ IDEA ή Eclipse.

Προσθέστε τη βιβλιοθήκη Aspose.Words στο έργο σας (παράδειγμα Maven):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Συμβουλή:** Αν χρησιμοποιείτε Gradle, αντικαταστήστε το XML block με `implementation 'com.aspose:aspose-words:24.9'`.

## Βήμα 1: Φόρτωση του πηγαίου εγγράφου DOCX

Η πρώτη λειτουργία είναι η ανάγνωση του αρχείου Word σε ένα αντικείμενο `Document`. Αυτό το αντικείμενο σας δίνει πλήρη πρόσβαση στη δομή, τα στυλ και το περιεχόμενο του αρχείου.

```java
import com.aspose.words.Document;

// Step 1: Load the source DOCX document
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου δημιουργεί μια αναπαράσταση στη μνήμη που το Aspose.Words μπορεί να χειριστεί. Αν η διαδρομή του αρχείου είναι λανθασμένη, το `Document` ρίχνει `FileNotFoundException`, γι' αυτό ελέγξτε ξανά τη διαδρομή πριν τρέξετε τον κώδικα.

## Βήμα 2: Δημιουργία επιλογών αποθήκευσης Markdown και ρύθμιση εξαγωγής πινάκων

Το Aspose.Words παρέχει `MarkdownSaveOptions` για να ελέγξετε πώς συμπεριφέρεται η μετατροπή. Από προεπιλογή, οι πίνακες αποδίδονται με τη σύνταξη pipe του Markdown, η οποία μπορεί να χάσει πολύπλοκη μορφοποίηση. Για να διατηρήσετε την αρχική διάταξη, ορίστε τη λειτουργία εξαγωγής σε HTML για τους πίνακες.

```java
import com.aspose.words.MarkdownSaveOptions;
import com.aspose.words.MarkdownExportAsHtml;

// Step 2: Create Markdown save options and set tables to be exported as HTML
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
markdownOptions.setExportAsHtml(MarkdownExportAsHtml.TABLES);
```

**Γιατί είναι σημαντικό:** Η κλήση `setExportAsHtml` λέει στη μηχανή να τυλίξει κάθε πίνακα σε ένα στοιχείο `<table>` μέσα στο παραγόμενο Markdown. Αυτό διατηρεί συγχωνευμένα κελιά, προσαρμοσμένα πλάτη και στυλ που το απλό Markdown δεν μπορεί να εκφράσει. Αν παραλείψετε αυτή τη ρύθμιση, οι πίνακες θα μετατραπούν σε απλό format pipe, το οποίο μπορεί να φαίνεται σπασμένο για πολύπλοκες διατάξεις.

## Βήμα 3: Αποθήκευση του εγγράφου ως αρχείο Markdown

Με τις ρυθμισμένες επιλογές, μπορείτε να γράψετε το αποτέλεσμα Markdown στο δίσκο. Η μέθοδος `save` παίρνει τη διαδρομή προορισμού και το αντικείμενο επιλογών.

```java
// Step 3: Save the document as a Markdown file using the configured options
document.save("YOUR_DIRECTORY/output.md", markdownOptions);
```

Μετά την εκτέλεση, το `output.md` περιέχει την αναπαράσταση Markdown του αρχικού DOCX, με τυχόν πίνακες να αποδίδονται ως HTML.

## Αναμενόμενο αποτέλεσμα

Υποθέτοντας ότι το `input.docx` περιέχει μια απλή παράγραφο και έναν πίνακα δύο γραμμών, το παραγόμενο `output.md` θα μοιάζει με το παρακάτω:

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
  <tr>
    <td>Row 2, Cell 1</td>
    <td>Row 2, Cell 2</td>
  </tr>
</table>
```

Παρατηρήστε ότι ο πίνακας τυλίγεται σε τυπικές ετικέτες HTML ενώ το κείμενο γύρω παραμένει καθαρό Markdown. Αυτό το υβριδικό format λειτουργεί καλά με static‑site generators όπως Hugo ή Jekyll, που αποδίδουν HTML blocks μέσα σε αρχεία Markdown χωρίς πρόβλημα.

## Προχωρημένο: Προσαρμογή εξόδου Markdown

Αν χρειάζεστε μεγαλύτερο έλεγχο στη μετατροπή, το `MarkdownSaveOptions` προσφέρει επιπλέον ιδιότητες:

| Ιδιότητα | Περιγραφή | Τυπική χρήση |
|----------|-----------|--------------|
| `setExportImagesAsHtml` | Εξάγει εικόνες ως ετικέτες `<img>` αντί για base‑64 data URIs. | Μειώνει το μέγεθος του αρχείου Markdown όταν οι εικόνες είναι μεγάλες. |
| `setExportHeadersAsHtml` | Διατηρεί τα στυλ των επικεφαλίδων χρησιμοποιώντας HTML ετικέτες `<h1>`‑`<h6>`. | Διατηρεί την ακριβή ιεραρχία επικεφαλίδων από το Word. |
| `setDocumentStructureExportMode` | Επιλέξτε μεταξύ `DocumentStructureExportMode.FULL` ή `MINIMAL`. | Ελέγχει πόσο από το δέντρο του εγγράφου Word διατηρείται. |

Παράδειγμα ενεργοποίησης εξαγωγής εικόνων ως HTML:

```java
markdownOptions.setExportImagesAsHtml(MarkdownExportAsHtml.IMAGES);
```

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Σύμπτωμα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Οι πίνακες εμφανίζονται ως απλοί σωλήνες Markdown παρά τη ρύθμιση `setExportAsHtml`. | Χρήση παλαιότερης έκδοσης Aspose.Words που δεν περιλαμβάνει το enum `MarkdownExportAsHtml`. | Αναβαθμίστε στην πιο πρόσφατη βιβλιοθήκη (≥ 24.9). |
| Το αρχείο εξόδου είναι κενό. | Η διαδρομή προέλευσης είναι λανθασμένη ή το αρχείο είναι κλειδωμένο. | Επαληθεύστε τη διαδρομή, βεβαιωθείτε ότι το αρχείο δεν είναι ανοιχτό σε άλλο πρόγραμμα. |
| Οι εικόνες λείπουν στο αρχείο Markdown. | `setExportImagesAsHtml` προεπιλογή είναι η ενσωμάτωση εικόνων ως base‑64, κάτι που ορισμένοι αναλυτές αφαιρούν. | Κλήση `markdownOptions.setExportImagesAsHtml(MarkdownExportAsHtml.IMAGES);` και βεβαιωθείτε ότι τα αρχεία εικόνας είναι προσβάσιμα. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει μια αυτόνομη κλάση Java που μπορείτε να επικολλήσετε σε ένα νέο αρχείο (`DocxToMarkdown.java`) και να τρέξετε άμεσα.

```java
import com.aspose.words.*;

public class DocxToMarkdown {
    public static void main(String[] args) {
        // Adjust these paths to match your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.md";

        try {
            // Load the DOCX file
            Document document = new Document(inputPath);

            // Configure Markdown options: export tables as HTML
            MarkdownSaveOptions options = new MarkdownSaveOptions();
            options.setExportAsHtml(MarkdownExportAsHtml.TABLES);
            // Optional: export images as <img> tags
            // options.setExportImagesAsHtml(MarkdownExportAsHtml.IMAGES);

            // Save as Markdown
            document.save(outputPath, options);

            System.out.println("Conversion successful! Markdown file created at: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Επεξήγηση κάθε τμήματος**

1. **Path variables** – Αλλάξτε το `YOUR_DIRECTORY` στο φάκελο που περιέχει το DOCX αρχείο σας.  
2. **`Document` constructor** – Διαβάζει το αρχείο Word στη μνήμη.  
3. **`MarkdownSaveOptions`** – Ορίζει τη σημαντική σημαία `setExportAsHtml` ώστε οι πίνακες να γίνουν HTML.  
4. **`save` call** – Γράφει το τελικό αρχείο Markdown.  
5. **Exception handling** – Συλλαμβάνει τυχόν σφάλματα IO ή Aspose.Words και εκτυπώνει ένα χρήσιμο μήνυμα.

Η εκτέλεση αυτού του προγράμματος παράγει το ίδιο `output.md` που περιγράφηκε νωρίτερα.

## Πώς να μετατρέψετε word σε markdown σε άλλες περιπτώσεις

- **Batch conversion** – Τυλίξτε τη λογική μετατροπής σε βρόχο που επαναλαμβάνεται για όλα τα αρχεία `.docx` σε έναν φάκελο.  
- **Integration with CI/CD** – Προσθέστε την κλάση Java στην αλυσίδα κατασκευής σας ώστε οι ενημερώσεις τεκμηρίωσης να μετατρέπονται αυτόματα.  
- **Embedding in web services** – Εκθέστε τη μετατροπή ως REST endpoint χρησιμοποιώντας Spring Boot· επιστρέψτε το string Markdown στην HTTP απόκριση.

Όλες αυτές οι περιπτώσεις χρήσης βασίζονται στα ίδια βασικά βήματα: **load the document**, **configure `MarkdownSaveOptions`**, και **save**.

## Συμπέρασμα

Τώρα ξέρετε πώς να **convert docx to markdown** και **export word tables as html** χρησιμοποιώντας το Aspose.Words for Java. Η διαδικασία τριών βημάτων — φόρτωση, ρύθμιση, αποθήκευση — καλύπτει την πλειονότητα των πραγματικών αναγκών μετατροπής, και οι προαιρετικές ρυθμίσεις σας επιτρέπουν να βελτιώσετε την έξοδο για εικόνες, επικεφαλίδες και δομή εγγράφου. Δοκιμάστε το πλήρες παράδειγμα, πειραματιστείτε με batch processing, και ενσωματώστε τον κώδικα στη ροή εργασίας τεκμηρίωσης για αδιάλειπτες μετατροπές Word‑to‑Markdown.

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

- [Μετατροπή docx σε markdown – Οδηγός βήμα-βήμα C#](/words/english/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-step-by-step-c-guide/)
- [Μετατροπή Word σε Markdown – Πλήρης Οδηγός με Εξαγωγή Εικόνων](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-complete-guide-with-image-extractio/)
- [Αποθήκευση Εικόνων Word – Μετατροπή Word σε Markdown με Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}