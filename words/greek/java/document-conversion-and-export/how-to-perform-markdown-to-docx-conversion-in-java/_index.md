---
category: general
date: 2026-08-20
description: Μετατροπή markdown σε docx σε Java εύκολη – μάθετε πώς να μετατρέπετε
  markdown, να ενεργοποιείτε την υπογράμμιση και να διατηρείτε τη μορφοποίηση κειμένου
  στο τελικό DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- markdown to docx conversion
- how to convert markdown
- how to enable underline
- preserve text formatting
- convert markdown docx
language: el
lastmod: 2026-08-20
og_description: Η μετατροπή markdown σε docx στην Java σας επιτρέπει να διατηρήσετε
  την υπογράμμιση και άλλες μορφοποιήσεις. Ακολουθήστε αυτό το πλήρες σεμινάριο για
  να μετατρέψετε αρχεία markdown σε DOCX αξιόπιστα.
og_image_alt: Diagram illustrating the flow from a Markdown file to a formatted DOCX
  document
og_title: Μετατροπή Markdown σε DOCX σε Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: markdown to docx conversion in Java made easy – learn how to convert
    markdown, enable underline, and preserve text formatting in the resulting DOCX.
  headline: How to perform markdown to docx conversion in Java
  type: TechArticle
- description: markdown to docx conversion in Java made easy – learn how to convert
    markdown, enable underline, and preserve text formatting in the resulting DOCX.
  name: How to perform markdown to docx conversion in Java
  steps:
  - name: Add the required dependency
    text: If you are using Maven, add the following to your `pom.xml`. Replace `VERSION`
      with the latest release (e.g., `23.7`).
  - name: Create load options and enable underline
    text: The **how to enable underline** feature is controlled through `LoadOptions`.
      By default, underline formatting is ignored, so you must turn it on explicitly.
  - name: Load the Markdown file using the configured options
    text: '```java import com.groupdocs.viewer.Document; import java.nio.file.Paths;'
  - name: Save the document as DOCX while preserving formatting
    text: '```java import com.groupdocs.viewer.options.SaveOptions; import com.groupdocs.viewer.options.SaveFormat;'
  - name: Verify the result (optional but recommended)
    text: '```java import java.io.File; import java.awt.Desktop;'
  type: HowTo
tags:
- markdown
- docx
- java
- text formatting
title: Πώς να εκτελέσετε τη μετατροπή markdown σε docx σε Java
url: /el/java/document-conversion-and-export/how-to-perform-markdown-to-docx-conversion-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εκτελέσετε τη μετατροπή markdown σε docx σε Java

Αν χρειάζεστε αξιόπιστη **μετατροπή markdown σε docx** σε Java, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα μάθετε επίσης **πώς να μετατρέπετε markdown** διατηρώντας **τη μορφοποίηση κειμένου**, συμπεριλαμβανομένου του υπογραμμισμένου κειμένου.

Η μετατροπή εγγράφων είναι μια συνηθισμένη εργασία όταν δημιουργείτε αναφορές, δημοσιεύετε τεχνική τεκμηρίωση ή προετοιμάζετε περιεχόμενο για μη‑τεχνικούς ενδιαφερόμενους. Αυτό το tutorial σας καθοδηγεί μέσα από τη πλήρη ροή εργασίας, από τη ρύθμιση των επιλογών μετατροπής μέχρι την αποθήκευση του τελικού αρχείου DOCX. Δεν απαιτείται εξωτερική τεκμηρίωση — όλα όσα χρειάζεστε περιλαμβάνονται παρακάτω.

## Τι θα επιτύχετε

* Μετατρέψτε οποιοδήποτε αρχείο `.md` σε αρχείο `.docx` χρησιμοποιώντας Java.
* Ενεργοποιήστε την εισαγωγή υπογράμμισης ώστε το υπογραμμισμένο κείμενο στο Markdown να εμφανίζεται υπογραμμισμένο στο DOCX.
* Διατηρήστε άλλες μορφοποιήσεις όπως έντονη, πλάγια και λίστες.
* Αντιμετωπίστε κοινές περιπτώσεις όπως ελλιπή αρχεία ή μη υποστηριζόμενα χαρακτηριστικά του Markdown.

**Προαπαιτούμενα**

* Java 17 ή νεότερη εγκατεστημένη.
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* Η βιβλιοθήκη GroupDocs.Viewer for Java (ή οποιαδήποτε βιβλιοθήκη που παρέχει `LoadOptions` και `Document`). Τα αποσπάσματα κώδικα χρησιμοποιούν το GroupDocs, αλλά οι έννοιες ισχύουν για παρόμοια API.

---

## Βήμα‑βήμα μετατροπή markdown σε docx

Η μετατροπή αποτελείται από τρία λογικά βήματα: ρύθμιση των load options, φόρτωση του εγγράφου Markdown και αποθήκευση του ως DOCX. Κάθε βήμα εξηγείται λεπτομερώς.

### Βήμα 1: Προσθέστε την απαιτούμενη εξάρτηση

Αν χρησιμοποιείτε Maven, προσθέστε τα παρακάτω στο `pom.xml` σας. Αντικαταστήστε το `VERSION` με την πιο πρόσφατη έκδοση (π.χ., `23.7`).

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

Για Gradle, προσθέστε:

```gradle
implementation "com.groupdocs:groupdocs-viewer:VERSION"
```

Αυτές οι συντεταγμένες φέρνουν τα `LoadOptions`, `Document` και τις απαραίτητες μηχανές απόδοσης.

### Βήμα 2: Δημιουργήστε load options και ενεργοποιήστε την υπογράμμιση

Η δυνατότητα **ενεργοποίησης υπογράμμισης** ελέγχεται μέσω του `LoadOptions`. Από προεπιλογή, η μορφοποίηση υπογράμμισης αγνοείται, οπότε πρέπει να την ενεργοποιήσετε ρητά.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Create a LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Enable import of underline formatting from Markdown
loadOptions.setImportUnderlineFormatting(true);
```

**Γιατί είναι σημαντικό:** Όταν παραλείπεται το `setImportUnderlineFormatting(true)`, οποιαδήποτε ετικέτα HTML `<u>` που δημιουργείται από το Markdown (`__underlined__`) θα αντιμετωπίζεται ως κανονικό κείμενο, χάνοντας το οπτικό στοιχείο στο τελικό DOCX. Η ενεργοποίηση αυτής της σημαίας εξασφαλίζει μια ακριβή αντιστοίχιση μεταξύ της υπογράμμισης στο Markdown και της υπογράμμισης στο Word.

### Βήμα 3: Φορτώστε το αρχείο Markdown χρησιμοποιώντας τις ρυθμισμένες επιλογές

```java
import com.groupdocs.viewer.Document;
import java.nio.file.Paths;

// Path to the source Markdown file
String markdownPath = Paths.get("YOUR_DIRECTORY", "sample.md").toString();

// Load the document with the previously defined options
Document document = new Document(markdownPath, loadOptions);
```

**Εξήγηση:** Ο κατασκευαστής `Document` διαβάζει το αρχείο, αναλύει το Markdown και εφαρμόζει τις επιλογές φόρτωσης που ορίσαμε νωρίτερα. Αν το αρχείο δεν υπάρχει, το `Document` ρίχνει `FileNotFoundException`; θα το διαχειριστούμε στο επόμενο βήμα.

### Βήμα 4: Αποθηκεύστε το έγγραφο ως DOCX διατηρώντας τη μορφοποίηση

```java
import com.groupdocs.viewer.options.SaveOptions;
import com.groupdocs.viewer.options.SaveFormat;

// Define where the DOCX will be saved
String outputPath = Paths.get("YOUR_DIRECTORY", "result.docx").toString();

// Save the document in DOCX format
document.save(outputPath, SaveFormat.DOCX);
```

**Τι συμβαίνει στο παρασκήνιο:** Η βιβλιοθήκη μετατρέπει την εσωτερική αναπαράσταση του Markdown (συμπεριλαμβανομένης της υπογράμμισης, έντονης, πλάγιας, πινάκων και λιστών) σε Office Open XML. Επειδή ενεργοποιήσαμε την εισαγωγή υπογράμμισης, οποιαδήποτε υπογραμμισμένα τμήματα γράφονται ως `<w:u w:val="single"/>` στο markup του DOCX.

### Βήμα 5: Επαληθεύστε το αποτέλεσμα (προαιρετικό αλλά συνιστάται)

```java
import java.io.File;
import java.awt.Desktop;

// Open the generated DOCX automatically (works on most OSes)
File resultFile = new File(outputPath);
if (Desktop.isDesktopSupported()) {
    Desktop.getDesktop().open(resultFile);
}
```

Μετά την εκτέλεση του προγράμματος, ανοίξτε το `result.docx` στο Microsoft Word ή στο LibreOffice Writer. Θα πρέπει να δείτε τις αρχικές επικεφαλίδες Markdown, τις λίστες και το **υπογραμμισμένο** κείμενο να εμφανίζονται ακριβώς όπως εμφανίζονταν στο αρχείο προέλευσης.

## Πώς να ενεργοποιήσετε την υπογράμμιση σε άλλες περιπτώσεις

Η σημαία `setImportUnderlineFormatting` λειτουργεί για τον προεπιλεγμένο parser του Markdown, αλλά μπορεί να συναντήσετε προσαρμοσμένες επεκτάσεις (π.χ., υποσημειώσεις ή λίστες εργασιών). Σε αυτές τις περιπτώσεις:

1. **Παραμετροποίηση προσαρμοσμένου parser** – Ορισμένες βιβλιοθήκες σας επιτρέπουν να καταχωρήσετε έναν προσαρμοσμένο parser Markdown που ήδη μετατρέπει την υπογράμμιση σε ετικέτες HTML `<u>`. Ενεργοποιήστε αυτόν τον parser πριν δημιουργήσετε το `LoadOptions`.
2. **Μετα‑επεξεργασία** – Αν η βιβλιοθήκη δεν υποστηρίζει άμεσα την υπογράμμιση, μπορείτε να διασχίσετε το δέντρο κόμβων του εγγράφου μετά τη φόρτωση και να εφαρμόσετε χειροκίνητα στυλ υπογράμμισης σε τμήματα που περιέχουν το σύμβολο υπογράμμισης.

```java
// Example of post‑processing (pseudo‑code)
document.getPages().forEach(page -> {
    page.getParagraphs().forEach(paragraph -> {
        paragraph.getSpans().forEach(span -> {
            if (span.getText().contains("<u>") && span.getText().contains("</u>")) {
                span.setUnderline(true);
            }
        });
    });
});
```

**Συμβουλή:** Η προσέγγιση μετα‑επεξεργασίας προσθέτει επιπλέον φόρτο, γι' αυτό προτιμήστε το ενσωματωμένο `setImportUnderlineFormatting` όποτε είναι δυνατόν.

## Διατήρηση μορφοποίησης κειμένου πέρα από την υπογράμμιση

Αν και η κύρια εστίαση είναι η υπογράμμιση, η διαδικασία μετατροπής διατηρεί επίσης άλλες κοινές μορφές του Markdown:

| Markdown syntax | Rendered in DOCX |
|-----------------|------------------|
| `**bold**`      | Έντονο κείμενο |
| `*italic*`      | Πλάγιο κείμενο |
| `` `code` ``    | Γραμματοσειρά σταθερού πλάτους |
| `> blockquote`  | Εσοχή παραγράφου |
| `- list item`   | Λίστα με κουκίδες |
| `1. list item`  | Αριθμημένη λίστα |
| `| table |`     | Διάταξη πίνακα |

Αν χρειάζεστε **διατήρηση μορφοποίησης κειμένου** για πρόσθετα στοιχεία (π.χ., διακριτή γραμμή), ελέγξτε τα `LoadOptions` της βιβλιοθήκης για αντίστοιχες σημαίες όπως `setImportStrikethroughFormatting(true)`.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Issue | Symptom | Fix |
|-------|---------|-----|
| Missing file path | `FileNotFoundException` κατά την εκτέλεση | Επικυρώστε τη διαδρομή εισόδου πριν δημιουργήσετε το `Document`. |
| Unsupported Markdown extension | Το περιεχόμενο παραλείπεται στο DOCX | Ενεργοποιήστε τις κατάλληλες επεκτάσεις parser ή προ‑επεξεργαστείτε το Markdown σε υποστηριζόμενο υποσύνολο. |
| Underline not appearing | Το κείμενο φαίνεται κανονικό στο DOCX | Βεβαιωθείτε ότι το `loadOptions.setImportUnderlineFormatting(true)` καλείται **πριν** τη φόρτωση του εγγράφου. |
| Large files cause memory pressure | Σφάλματα out‑of‑memory | Χρησιμοποιήστε `LoadOptions.setPageLimit(int)` για επεξεργασία του εγγράφου σε τμήματα. |

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα πλήρες, αυτόνομο πρόγραμμα Java που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε. Περιλαμβάνει διαχείριση σφαλμάτων και εκτυπώνει μηνύματα κατάστασης στην κονσόλα.

```java
package com.example.markdowntodocx;

import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;
import com.groupdocs.viewer.options.SaveFormat;

import java.awt.Desktop;
import java.io.File;
import java.io.IOException;
import java.nio.file.Path;
import java.nio.file.Paths;

public class MarkdownToDocx {

    public static void main(String[] args) {
        // Adjust these paths to match your environment
        Path inputPath = Paths.get("YOUR_DIRECTORY", "sample.md");
        Path outputPath = Paths.get("YOUR_DIRECTORY", "result.docx");

        // Step 1: Configure load options
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true); // enable underline import

        try {
            // Step 2: Load the Markdown document
            Document document = new Document(inputPath.toString(), loadOptions);

            // Step 3: Save as DOCX
            document.save(outputPath.toString(), SaveFormat.DOCX);
            System.out.println("Conversion succeeded: " + outputPath);

            // Optional: Open the resulting DOCX automatically
            openFile(outputPath);
        } catch (Exception e) {
            System.err.println("Conversion failed: " + e.getMessage());
            e.printStackTrace();
        }
    }

    /** Opens a file using the default desktop application, if supported. */
    private static void openFile(Path file) {
        if (Desktop.isDesktopSupported()) {
            try {
                Desktop.getDesktop().open(file.toFile());
            } catch (IOException e) {
                System.err.println("Unable to open the file automatically: " + e.getMessage());
            }
        }
    }
}
```

**Αναμενόμενη έξοδος**

```
Conversion succeeded: /path/to/YOUR_DIRECTORY/result.docx
```

Όταν ανοίξετε το `result.docx`, οποιοδήποτε υπογραμμισμένο κείμενο από το `sample.md` εμφανίζεται υπογραμμισμένο, και οι άλλες μορφοποιήσεις του Markdown διατηρούνται.

## Επόμενα βήματα και συναφή θέματα

* **Batch conversion** – Τυλίξτε τη λογική που παρουσιάστηκε σε έναν βρόχο για να επεξεργαστείτε έναν φάκελο αρχείων Markdown. Χρησιμοποιήστε `loadOptions.setPageLimit()` για να ελέγξετε τη χρήση μνήμης.
* **Convert markdown docx to PDF** – Αφού αποκτήσετε ένα DOCX, μπορείτε να καλέσετε `document.save("output.pdf", SaveFormat.PDF)` για να δημιουργήσετε PDF διατηρώντας την ίδια μορφοποίηση.
* **Custom styling** – Εφαρμόστε ένα πρότυπο στυλ Word στο παραγόμενο DOCX φορτώνοντας ένα αρχείο `.dotx` μέσω `LoadOptions.setTemplatePath(...)`.
* **Integration with Spring Boot** – Εκθέστε τη μετατροπή ως REST endpoint ώστε άλλες υπηρεσίες να μπορούν να ζητούν μετατροπή εν κινήσει.

## Συμπέρασμα

Τώρα έχετε μια στιβαρή, έτοιμη για παραγωγή λύση.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Πώς να εξάγετε LaTeX από το Word: Μετατροπή DOCX σε Markdown & Αποθήκευση ως PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)
- [Πώς να ενσωματώσετε εικόνες στο Markdown κατά τη μετατροπή DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Μετατροπή docx σε markdown – Εξαγωγή μαθηματικών εξισώσεων σε LaTeX με Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}