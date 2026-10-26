---
category: general
date: 2026-10-26
description: Μετατρέψτε docx σε markdown σε Java χρησιμοποιώντας το Aspose.Words –
  μάθετε πώς να αποθηκεύετε το Word ως markdown, να εξάγετε πίνακες ως HTML και να
  λαμβάνετε ένα έτοιμο .md αρχείο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to markdown
- save word as markdown
- convert word to markdown
- save document as markdown
- export tables html
language: el
lastmod: 2026-10-26
og_description: Μετατροπή docx σε markdown σε Java με το Aspose.Words. Αυτό το σεμινάριο
  δείχνει πώς να αποθηκεύσετε το Word ως markdown, να εξάγετε πίνακες ως HTML και
  να δημιουργήσετε καθαρά αρχεία .md.
og_image_alt: Screenshot of generated Markdown file showing an HTML table
og_title: Μετατροπή docx σε markdown σε Java – πλήρης οδηγός με εξαγωγή πίνακα
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: convert docx to markdown in Java using Aspose.Words – learn how to
    save Word as markdown, export tables as HTML, and get a ready‑to‑use .md file.
  headline: How to convert docx to markdown in Java with table support
  type: TechArticle
tags:
- Java
- Aspose.Words
- Markdown
- Document conversion
title: Πώς να μετατρέψετε το docx σε markdown σε Java με υποστήριξη πινάκων
url: /el/java/document-conversion-and-export/how-to-convert-docx-to-markdown-in-java-with-table-support/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μετατρέψετε docx σε markdown σε Java με υποστήριξη πινάκων

Αν χρειάζεστε να **μετατρέψετε docx σε markdown** γρήγορα, αυτός ο οδηγός σας παρουσιάζει μια πλήρη λύση χρησιμοποιώντας το Aspose.Words for Java. Θα μάθετε πώς να **αποθηκεύσετε το Word ως markdown**, να διατηρήσετε τους πίνακες εξάγοντάς τους ως HTML, και να δημιουργήσετε ένα καθαρό αρχείο `.md` έτοιμο για γεννήτριες στατικών ιστοσελίδων ή αγωγούς τεκμηρίωσης.

Η μετατροπή εγγράφων Word σε markdown είναι ένα συνηθισμένο βήμα όταν μεταφέρετε περιεχόμενο από το Microsoft Office σε συστήματα τεκμηρίωσης ελεγχόμενα με εκδόσεις. Αυτό το tutorial καλύπτει όλα όσα χρειάζεστε — από τη φόρτωση του αρχείου προέλευσης μέχρι τη διαμόρφωση των επιλογών Markdown — ώστε να μπορείτε να αυτοματοποιήσετε τη διαδικασία στα δικά σας έργα.

## Τι θα επιτύχετε

* Φορτώστε ένα αρχείο `.docx` από οποιονδήποτε φάκελο.
* Διαμορφώστε τις επιλογές **save document as markdown** για εξαγωγή πινάκων ως HTML.
* Γράψτε το παραγόμενο αρχείο markdown στο δίσκο με μία κλήση μεθόδου.
* Επεκτείνετε τη λύση για προσαρμοσμένες δομές φακέλων ή πρόσθετες ρυθμίσεις εξαγωγής.

**Προαπαιτούμενα**

* Java 17 ή νεότερη (ο κώδικας συντάσσεται επίσης με Java 8).
* Βιβλιοθήκη Aspose.Words for Java (έκδοση 23.9 ή νεότερη). Προσθέστε την εξάρτηση Maven που φαίνεται παρακάτω.
* Βασική εξοικείωση με Java I/O και Maven.

```xml
<!-- Maven dependency for Aspose.Words -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Μετατροπή docx σε markdown με Aspose.Words

Το πρώτο σημαντικό βήμα είναι να δημιουργήσετε μια παρουσία `Document` που αντιπροσωπεύει το αρχείο προέλευσης `.docx`. Αυτό το αντικείμενο σας δίνει πρόσβαση σε ολόκληρο το μοντέλο αντικειμένων του Word, επιτρέποντάς σας να χειριστείτε ή να εξάγετε το περιεχόμενο σε πολλές μορφές.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;
import com.aspose.words.MdSaveOptions;
import com.aspose.words.MarkdownExportAsHtml;

/**
 * Demonstrates converting a DOCX file to Markdown while exporting tables as HTML.
 */
public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**Γιατί είναι σημαντικό:**  
Η φόρτωση του εγγράφου επικυρώνει τη μορφή του αρχείου και δημιουργεί μια αναπαράσταση στη μνήμη. Εάν το αρχείο λείπει ή είναι κατεστραμμένο, το Aspose.Words ρίχνει μια περιγραφική εξαίρεση, την οποία μπορείτε να πιάσετε για αξιόπιστη διαχείριση σφαλμάτων.

## Αποθήκευση Word ως markdown – διαμόρφωση επιλογών

Στη συνέχεια, πρέπει να πείτε στο Aspose.Words πώς να χειριστεί τους πίνακες κατά τη μετατροπή. Από προεπιλογή, οι πίνακες αποδίδονται ως απλό markdown, το οποίο μπορεί να χάσει την πολύπλοκη μορφοποίηση των κελιών. Ορίζοντας το `exportAsHtml` σε `MarkdownExportAsHtml.TABLES` εξαναγκάζει τους πίνακες να εκτυπώνονται ως ακατέργαστο HTML μέσα στο αρχείο markdown.

```java
        // Step 2: Configure Markdown save options to export tables as HTML
        MdSaveOptions mdOptions = new MdSaveOptions();
        mdOptions.setExportAsHtml(MarkdownExportAsHtml.TABLES);
```

**Γιατί είναι σημαντικό:**  
Πολλοί αναλυτές markdown (π.χ., GitHub, MkDocs) κατανοούν τα ακατέργαστα HTML blocks, διατηρώντας τις ενοποιήσεις στηλών, τα συγχωνευμένα κελιά και το στυλ που το απλό markdown δεν μπορεί να εκφράσει. Αυτή η επιλογή εξασφαλίζει ότι οι πίνακές σας θα φαίνονται ταυτόσημοι μετά τη μετατροπή.

## Εξαγωγή πινάκων ως HTML κατά τη μετατροπή

Αν θέλετε επίσης να ελέγξετε τις αλλαγές γραμμής, τα μπλοκ κώδικα ή τη διαχείριση εικόνων, το `MdSaveOptions` παρέχει πρόσθετες ιδιότητες. Παρακάτω είναι μια ελάχιστη αλλά επεκτάσιμη διαμόρφωση:

```java
        // Optional: preserve original line breaks
        mdOptions.setExportLineBreaks(true);
        // Optional: export images as base64 strings (useful for single‑file docs)
        mdOptions.setExportImagesAsBase64(true);
```

Αυτές οι ρυθμίσεις είναι βελτιώσεις **save document as markdown** που πολλές ομάδες βρίσκουν χρήσιμες όταν το markdown θα εμφανίζεται σε προβολείς ιστού.

## Βήμα 3: Αποθήκευση του εγγράφου ως αρχείο Markdown

Τέλος, καλέστε το `doc.save` με την επέκταση `.md` και τις διαμορφωμένες επιλογές. Το Aspose.Words γράφει το αρχείο σε κωδικοποίηση UTF‑8 εξ ορισμού.

```java
        // Step 3: Save the document as a Markdown file
        doc.save("YOUR_DIRECTORY/out.md", mdOptions);
        System.out.println("Conversion completed: out.md");
    }
}
```

**Γιατί είναι σημαντικό:**  
Η μέθοδος `save` αφαιρεί την ανάγκη χειρισμού ρεύματος χαμηλού επιπέδου, εγγυώμενη ότι η έξοδος σέβεται τις επιλογές που ορίσατε. Το παραγόμενο `out.md` περιέχει κείμενο markdown, και τυχόν πίνακες εμφανίζονται ως μπλοκ HTML `<table>`.

### Αναμενόμενη έξοδος

Ανοίξτε το `out.md` σε οποιονδήποτε επεξεργαστή κειμένου. Θα πρέπει να δείτε κάτι όπως:

```markdown
# Sample Document

This is a paragraph taken from the original Word file.

<table>
  <tr>
    <th>Header 1</th>
    <th>Header 2</th>
  </tr>
  <tr>
    <td>Cell A1</td>
    <td>Cell B1</td>
  </tr>
</table>

Another paragraph follows the table.
```

Ο πίνακας HTML θα αποδοθεί σωστά σε πλατφόρμες που υποστηρίζουν ενσωματωμένο HTML, όπως αρχεία README του GitHub ή MkDocs.

## Συνηθισμένες παραλλαγές και ακραίες περιπτώσεις

| Κατάσταση | Πώς να το αντιμετωπίσετε |
|-----------|--------------------------|
| **Μεγάλα έγγραφα** ( > 100 MB ) | Χρησιμοποιήστε το `Document.save` με ένα `FileOutputStream` για να αποφύγετε τη φόρτωση ολόκληρου του αρχείου στη μνήμη. |
| **Πολλοί πίνακες χρειάζονται προσαρμοσμένο CSS** | Μετά τη μετατροπή, επεξεργαστείτε το αρχείο markdown για να ενσωματώσετε ένα μπλοκ `<style>` ή χρησιμοποιήστε μια αλυσίδα markdown‑σε‑HTML που προσθέτει CSS. |
| **Πρέπει να μετατρέψετε αρχεία .doc (δυαδικά)** | Το Aspose.Words ανιχνεύει αυτόματα τη μορφή· απλώς δείξτε το `new Document("file.doc")` στην πηγή. |
| **Θέλετε να διατηρήσετε τις εικόνες ως ξεχωριστά αρχεία** | Ορίστε `mdOptions.setExportImagesAsBase64(false)` και παρέχετε ένα `ImageSavingCallback` για να ελέγξετε το φάκελο εικόνων. |

### Συμβουλή επαγγελματία

Κατά τη μετατροπή πολλών αρχείων σε παρτίδα, επαναχρησιμοποιήστε μια μόνο παρουσία `MdSaveOptions`. Η δημιουργία του αντικειμένου επιλογών μία φορά μειώνει την πίεση στο GC και επιταχύνει τη διαδικασία κατά ~15 %.

```java
MdSaveOptions sharedOptions = new MdSaveOptions();
sharedOptions.setExportAsHtml(MarkdownExportAsHtml.TABLES);
// reuse sharedOptions for each document in the loop
```

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα IDE. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή φακέλου στο μηχάνημά σας.

```java
import com.aspose.words.Document;
import com.aspose.words.MdSaveOptions;
import com.aspose.words.MarkdownExportAsHtml;

/**
 * End‑to‑end conversion of a DOCX file to Markdown with HTML tables.
 * Requires Aspose.Words for Java (Maven artifact: com.aspose:aspose-words).
 */
public class DocxToMarkdown {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Configure conversion options
            MdSaveOptions mdOptions = new MdSaveOptions();
            mdOptions.setExportAsHtml(MarkdownExportAsHtml.TABLES);
            mdOptions.setExportLineBreaks(true);
            mdOptions.setExportImagesAsBase64(true); // optional

            // 3️⃣ Save as .md
            doc.save("YOUR_DIRECTORY/out.md", mdOptions);
            System.out.println("Successfully converted DOCX to Markdown.");
        } catch (Exception e) {
            System.err.println("Conversion failed: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

Εκτελέστε το πρόγραμμα, μετά ανοίξτε το `out.md`. Θα δείτε το κείμενο markdown με τυχόν πίνακες αποδομένους ως HTML, ικανοποιώντας την απαίτηση **convert word to markdown** διατηρώντας την πιστότητα της διάταξης.

## Συμπέρασμα

Τώρα έχετε μια αξιόπιστη μέθοδο για **μετατροπή docx σε markdown** σε Java, με πλήρη έλεγχο του τρόπου εξαγωγής των πινάκων ως HTML. Το tutorial κάλυψε τη φόρτωση του εγγράφου, τη διαμόρφωση των επιλογών **save document as markdown**, και τη γραφή του τελικού αρχείου. Μη διστάσετε να εξερευνήσετε πρόσθετες ιδιότητες του `MdSaveOptions` — όπως προσαρμοσμένα επίπεδα επικεφαλίδων ή διαχείριση υποσημειώσεων — για να προσαρμόσετε την έξοδο στη ροή εργασίας τεκμηρίωσής σας.

**Επόμενα βήματα**

* Δοκιμάστε να μετατρέψετε μια παρτίδα αρχείων επαναλαμβάνοντας έναν φάκελο και επαναχρησιμοποιώντας μια μόνο παρουσία `MdSaveOptions`.
* Ενσωματώστε τη μετατροπή σε μια CI pipeline που δημιουργεί αυτόματα τεκμηρίωση από πηγές Word.
* Εξερευνήστε άλλες μορφές εξαγωγής (π.χ., **save word as markdown** → PDF, HTML) χρησιμοποιώντας το εκτενές API του Aspose.Words.

Καλή προγραμματιστική δουλειά, και απολαύστε τη αδιάσπαστη γέφυρα από το Word στο markdown!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εξαγωγή και αποθήκευση εικόνων Word – Μετατροπή DOCX σε Markdown χρησιμοποιώντας το Aspose.Words for Java API](/words/english/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/)
- [Μετατροπή DOCX σε Markdown με Aspose.Words for Java – Αποθήκευση DOCX ως Markdown](/words/english/java/document-conversion-and-export/save-docx-as-markdown-convert-docx-to-markdown-using-aspose/)
- [Αποθήκευση Word ως Markdown – Εξαγωγή πινάκων σε HTML με Aspose.Words](/words/english/net/programming-with-markdownsaveoptions/save-word-as-markdown-export-tables-to-html-with-aspose-word/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}