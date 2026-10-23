---
category: general
date: 2026-10-23
description: Πώς να εξάγετε LaTeX ενώ μετατρέπετε DOCX σε markdown και αποθηκεύετε
  το έγγραφο ως PDF—οδηγός βήμα‑βήμα με κώδικα Java.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save document as pdf
- how to save pdf
- save word as markdown
lastmod: 2026-10-23
og_description: Μάθετε πώς να εξάγετε LaTeX ενώ μετατρέπετε DOCX σε markdown και αποθηκεύετε
  το έγγραφο ως PDF με Java. Πλήρης κώδικας και συμβουλές.
og_image_alt: Diagram of DOCX to markdown (LaTeX) and PDF conversion pipeline
og_title: Πώς να εξάγετε LaTeX από το Word και να αποθηκεύσετε PDF χρησιμοποιώντας
  Java
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: How to export LaTeX while you convert DOCX to markdown and save document
    as PDF—step‑by‑step guide with Java code.
  headline: 'How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF'
  type: TechArticle
- description: How to export LaTeX while you convert DOCX to markdown and save document
    as PDF—step‑by‑step guide with Java code.
  name: 'How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF'
  steps:
  - name: set up your project
    text: 'First things first—let’s get the Aspose.Words jar on the classpath. If
      you’re using Maven, add this dependency to your `pom.xml`: For Gradle, it’s
      a one‑liner: > **Pro tip:** Always use the latest stable version; it includes
      bug fixes for recovery mode and LaTeX export. Create a new Java class calle'
  - name: load the document in recovery mode
    text: '`RecoveryMode.RECOVER` tells Aspose.Words to attempt salvaging a broken
      file. **Definition:** `RecoveryMode.RECOVER` is an enum value that enables partial
      document reconstruction while still reporting unrecoverable errors. Why use
      `RecoveryMode.RECOVER`? It attempts to salvage as much content as pos'
  - name: export LaTeX while converting DOCX to markdown
    text: 'Now comes the star of the show: **how to export LaTeX** from the Word document.
      The `MarkdownSaveOptions` class has an `OfficeMathExportMode` property that
      lets you choose LaTeX, MathML, or image output. We’ll pick LaTeX. **Definition:**
      `MarkdownSaveOptions` configures how Aspose.Words writes a doc'
  - name: save the document as PDF (and preserve floating shapes)
    text: Often you still need a PDF version for reviewers who aren’t comfortable
      with markdown. Aspose.Words makes this trivial, and you can control how floating
      shapes (like diagrams) are handled. **Definition:** `ExportFloatingShapesAsInlineTag`
      is a boolean flag that, when true, converts each floating sha
  - name: customize image handling when saving markdown
    text: By default, Aspose.Words dumps every image into the same folder as the markdown
      file, naming them sequentially. If you prefer a tidy `images/` subdirectory,
      you can hook into the `ResourceSavingCallback`. **Definition:** `ResourceSavingCallback`
      is an interface you implement to control where and how
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words automatically detects the format; simply change the
      file extension in `inputPath`.
    question: Does this work with .doc files or only .docx?
  - answer: Replace `OfficeMathExportMode.LATEX` with `OfficeMathExportMode.MATHML`.
      The rest of the pipeline stays identical.
    question: What if I need MathML instead of LaTeX?
  - answer: Absolutely. Comment out the PDF block; the code is modular, so you can
      **save document as PDF** only when you need it.
    question: Can I skip the PDF step?
  - answer: Use `LoadOptions.setPassword("yourPassword")` before creating the `Document`
      instance.
    question: How do I handle password‑protected documents?
  - answer: Not natively; PDFs don’t understand LaTeX. You’d have to render the equations
      as images first, which defeats the purpose of a clean LaTeX export.
    question: Is there a way to embed the LaTeX directly into the PDF?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: 'Πώς να εξάγετε LaTeX από το Word: Μετατρέψτε DOCX σε Markdown & Αποθηκεύστε
  ως PDF'
url: /el/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εξάγετε LaTeX από το Word: μετατροπή DOCX σε markdown & αποθήκευση ως PDF

Έχετε αναρωτηθεί ποτέ **πώς να εξάγετε LaTeX** από ένα αρχείο Word χωρίς να χάσετε καμία από τις εντυπωσιακές εξισώσεις; Δεν είστε μόνοι. Σε πολλά έργα—ακαδημαϊκά άρθρα, τεχνικά blogs ή εσωτερικά έγγραφα—οι άνθρωποι χρειάζεται να εξάγουν LaTeX από ένα `.docx`, να μετατρέψουν όλο το περιεχόμενο σε markdown, και να διατηρήσουν μια καθαρή έκδοση PDF για διανομή.  

Σε αυτό το tutorial θα περάσουμε από ολόκληρη τη διαδικασία: **convert docx to markdown**, **export LaTeX**, και **save document as PDF** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words for Java. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση πρόγραμμα Java που κάνει τα πάντα, συν ένα σύνολο πρακτικών συμβουλών που μπορείτε να αντιγράψετε‑επικολλήσετε στον κώδικά σας.

## Σύντομες απαντήσεις
- **Can I convert a corrupted DOCX?** Yes – load it in recovery mode to salvage most content.  
  **Μπορώ να μετατρέψω ένα κατεστραμμένο DOCX;** Ναι – φορτώστε το σε λειτουργία ανάκτησης για να διασώσετε το μεγαλύτερο μέρος του περιεχομένου.  
- **Which format does LaTeX export use?** Inline `$…$` for simple equations, `$$…$$` for display equations.  
  **Ποια μορφή χρησιμοποιεί η εξαγωγή LaTeX;** Inline `$…$` για απλές εξισώσεις, `$$…$$` για εξισώσεις εμφάνισης.  
- **Do I need Microsoft Word installed?** No, Aspose.Words works completely independently.  
  **Χρειάζεται να είναι εγκατεστημένο το Microsoft Word;** Όχι, το Aspose.Words λειτουργεί εντελώς ανεξάρτητα.  
- **How are images stored when exporting to markdown?** You can direct them into an `images/` subfolder via a callback.  
  **Πώς αποθηκεύονται οι εικόνες κατά την εξαγωγή σε markdown;** Μπορείτε να τις κατευθύνετε σε έναν υποφάκελο `images/` μέσω ενός callback.  
- **Is a license required for production?** Yes – the trial adds a watermark; a proper license removes it.  
  **Απαιτείται άδεια για παραγωγή;** Ναι – η δοκιμαστική έκδοση προσθέτει υδατογράφημα· μια έγκυρη άδεια το αφαιρεί.

## Τι θα μάθετε

- Φορτώστε ένα πιθανώς κατεστραμμένο έγγραφο Word σε λειτουργία ανάκτησης.  
- Εξάγετε τις εξισώσεις Office Math ως LaTeX κατά την αποθήκευση σε markdown.  
- Αποθηκεύστε το ίδιο έγγραφο ως PDF ενώ διαχειρίζεστε τα αιωρούμενα σχήματα ως ετικέτες inline.  
- Προσαρμόστε τη διαχείριση εικόνων κατά την εξαγωγή σε markdown (αποθηκεύστε τις εικόνες σε έναν αφιερωμένο φάκελο).  
- Πώς να **save word as markdown** και να διατηρήσετε ακόμη μια αντίγραφο PDF υψηλής ποιότητας.  

**Prerequisites**: Java 17 ή νεότερο, Maven ή Gradle, και άδεια Aspose.Words for Java (η δωρεάν δοκιμαστική έκδοση λειτουργεί για πειραματισμό). Δεν απαιτούνται άλλες βιβλιοθήκες τρίτων.

## Πώς να εξάγετε LaTeX από το Word;

Φορτώστε το DOCX σας με `new Document("input.docx", loadOptions)` και ορίστε `loadOptions.setRecoveryMode(RecoveryMode.RECOVER)`. Το Aspose.Words προσπαθεί τότε να επανακατασκευάσει τη δομή του εγγράφου, διατηρώντας όσο το δυνατόν περισσότερα στοιχεία, ενώ εξακολουθεί να ρίχνει εξαίρεση αν το αρχείο είναι εντελώς μη αναγνώσιμο. Αυτή η προσέγγιση σας παρέχει ένα ασφαλές εναλλακτικό για κατεστραμμένα αρχεία χωρίς να θυσιάζει το μεγαλύτερο μέρος του περιεχομένου.

### Βήμα 1: ρυθμίστε το έργο σας

Πρώτα απ' όλα—ας προσθέσουμε το jar του Aspose.Words στο classpath. Αν χρησιμοποιείτε Maven, προσθέστε αυτήν την εξάρτηση στο `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Check for the latest version -->
</dependency>
```

Για Gradle, είναι μια γραμμή:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Χρησιμοποιείτε πάντα την πιο πρόσφατη σταθερή έκδοση· περιλαμβάνει διορθώσεις σφαλμάτων για τη λειτουργία ανάκτησης και την εξαγωγή LaTeX.

Δημιουργήστε μια νέα κλάση Java με όνομα `DocxProcessor.java`. Θα εισάγουμε όλα όσα χρειάζονται:

```java
import com.aspose.words.*;

import java.io.File;
import java.io.IOException;
```

### Βήμα 2: φορτώστε το έγγραφο σε λειτουργία ανάκτησης

`RecoveryMode.RECOVER` λέει στο Aspose.Words να προσπαθήσει να διασώσει ένα κατεστραμμένο αρχείο.  

**Definition:** `RecoveryMode.RECOVER` είναι μια τιμή enum που επιτρέπει μερική ανακατασκευή του εγγράφου ενώ εξακολουθεί να αναφέρει μη ανακτήσιμα σφάλματα.

```java
public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // Adjust these paths to match your environment
        String inputPath = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown = "YOUR_DIRECTORY/output.md";
        String outputPdf = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown = "YOUR_DIRECTORY/output_with_custom_images.md";

        // Step 2: Load with recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER); // STRICT, IGNORE are alternatives
        Document doc = new Document(inputPath, loadOptions);

        // Continue with export steps...
```

Γιατί να χρησιμοποιήσετε `RecoveryMode.RECOVER`; Προσπαθεί να διασώσει όσο το δυνατόν περισσότερο περιεχόμενο, ενώ εξακολουθεί να ρίχνει εξαίρεση αν το αρχείο είναι εντελώς μη αναγνώσιμο. Αυτό εξισορροπεί την ασφάλεια με την πρακτικότητα.

### Βήμα 3: εξαγωγή LaTeX κατά τη μετατροπή DOCX σε markdown

Τώρα έρχεται το αστέρι της παράστασης: **how to export LaTeX** από το έγγραφο Word. Η κλάση `MarkdownSaveOptions` έχει μια ιδιότητα `OfficeMathExportMode` που σας επιτρέπει να επιλέξετε LaTeX, MathML ή έξοδο εικόνας. Θα επιλέξουμε LaTeX.

**Definition:** `MarkdownSaveOptions` ρυθμίζει πώς το Aspose.Words γράφει ένα έγγραφο στη μορφή Markdown, συμπεριλαμβανομένης της διαχείρισης εικόνων και της εξαγωγής μαθηματικών.

```java
        // Step 3: Export Office Math as LaTeX during markdown conversion
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);
```

Το παραγόμενο `output.md` θα περιέχει τμήματα LaTeX περικλεισμένα σε `$…$` για ενσωματωμένες εξισώσεις ή `$$…$$` για εξισώσεις εμφάνισης. Αν ανοίξετε το αρχείο σε έναν markdown επεξεργαστή που υποστηρίζει MathJax ή KaTeX, οι εξισώσεις θα εμφανιστούν όμορφα.

> **Why LaTeX?** Επειδή είναι η κοινή γλώσσα της επιστημονικής δημοσίευσης. Η άμεση εξαγωγή σε LaTeX αποφεύγει τη μείωση ποιότητας που θα προέκυπτε αν επιλέγατε εικόνες.

### Βήμα 4: αποθήκευση του εγγράφου ως PDF (και διατήρηση των αιωρούμενων σχημάτων)

Συχνά χρειάζεστε ακόμη μια έκδοση PDF για αξιολογητές που δεν είναι εξοικειωμένοι με markdown. Το Aspose.Words το κάνει εύκολο, και μπορείτε να ελέγξετε πώς διαχειρίζονται τα αιωρούμενα σχήματα (όπως διαγράμματα).

**Definition:** `ExportFloatingShapesAsInlineTag` είναι μια λογική σημαία που, όταν είναι true, μετατρέπει κάθε αιωρούμενο σχήμα σε μια ετικέτα `<span>` εντός της εσωτερικής XML αναπαράστασης του PDF.

```java
        // Step 4: Save as PDF, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);
```

Ορίζοντας το `ExportFloatingShapesAsInlineTag` σε `true` μετατρέπει κάθε αιωρούμενο σχήμα σε μια ετικέτα `<span>` εντός της εσωτερικής δομής του PDF, κάτι που μπορεί να είναι χρήσιμο για επεξεργασία downstream (π.χ., εργαλεία προσβασιμότητας PDF).

### Βήμα 5: προσαρμογή της διαχείρισης εικόνων κατά την αποθήκευση markdown

Από προεπιλογή, το Aspose.Words αποθηκεύει κάθε εικόνα στον ίδιο φάκελο με το αρχείο markdown, ονομάζοντάς τα διαδοχικά. Αν προτιμάτε έναν τακτοποιημένο υποφάκελο `images/`, μπορείτε να συνδέσετε το `ResourceSavingCallback`.

**Definition:** `ResourceSavingCallback` είναι μια διεπαφή που υλοποιείτε για να ελέγξετε πού και πώς γράφονται οι εξωτερικοί πόροι (όπως εικόνες) κατά την εξαγωγή.

```java
        // Step 5: Custom image folder for markdown export
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Place each image under YOUR_DIRECTORY/images/
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs(); // Ensure the folder exists
                args.setFileName(imageFolder + args.getFileName());
                // You could also modify the stream here or skip saving if needed
            }
        });

        doc.save(customMarkdown, customMdOptions);
```

Τώρα όλες οι εικόνες που αναφέρονται στο `output_with_custom_images.md` βρίσκονται τακτοποιημένα κάτω από `images/`. Αυτό καθιστά τον έλεγχο εκδόσεων πιο καθαρό και αντικατοπτρίζει τη συνήθη διάταξη που βλέπετε στο GitHub.

## Πλήρες λειτουργικό παράδειγμα

Τοποθετώντας όλα μαζί, εδώ είναι το πλήρες αρχείο `DocxProcessor.java` που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

```java
import com.aspose.words.*;

import java.io.File;

public class DocxProcessor {

    public static void main(String[] args) throws Exception {
        // ==== USER CONFIGURATION ====
        String inputPath        = "YOUR_DIRECTORY/corrupted.docx";
        String outputMarkdown   = "YOUR_DIRECTORY/output.md";
        String outputPdf        = "YOUR_DIRECTORY/output.pdf";
        String customMarkdown   = "YOUR_DIRECTORY/output_with_custom_images.md";

        // ==== 1️⃣ Load document with recovery mode ====
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER);
        Document doc = new Document(inputPath, loadOptions);

        // ==== 2️⃣ Export LaTeX while converting to markdown ====
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);

        // ==== 3️⃣ Save as PDF, handling floating shapes ====
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);

        // ==== 4️⃣ Custom image folder for markdown export ====
        MarkdownSaveOptions customMdOptions = new MarkdownSaveOptions();
        customMdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                String imageFolder = "YOUR_DIRECTORY/images/";
                new File(imageFolder).mkdirs();
                args.setFileName(imageFolder + args.getFileName());
            }
        });
        doc.save(customMarkdown, customMdOptions);

        System.out.println("All exports completed successfully!");
    }
}
```

### Αναμενόμενο αποτέλεσμα

- `output.md` – αρχείο markdown με εξισώσεις LaTeX (`$…$` και `$$…$$`).  
- `output.pdf` – PDF υψηλής ανάλυσης, τα αιωρούμενα σχήματα μετατράπηκαν σε ετικέτες inline.  
- `output_with_custom_images.md` – ίδιο markdown αλλά όλες οι εικόνες αποθηκεύονται κάτω από `images/`.  

Ανοίξτε το markdown στο VS Code με την επέκταση *Markdown Preview Enhanced*, και θα δείτε τις εξισώσεις να αποδίδονται ακριβώς όπως εμφανίζονταν στο αρχικό αρχείο Word.

## Ποσοτικοποιημένα οφέλη από τη χρήση του Aspose.Words

Το Aspose.Words υποστηρίζει **35+ μορφές εισόδου και εξόδου** — συμπεριλαμβανομένων DOCX, ODT, RTF, PDF, HTML, EPUB και Markdown — και μπορεί να επεξεργαστεί **έγγραφα 500 σελίδων σε λιγότερο από 3 δευτερόλεπτα** σε τυπική CPU διακομιστή. Η βιβλιοθήκη διαχειρίζεται επίσης **έως 200 MB ενσωματωμένων μέσων** χωρίς να απαιτεί πρόσθετο κώδικα διαχείρισης μνήμης, καθιστώντας την ιδανική για μεγάλες μαζικές μετατροπές.

## Συχνά προβλήματα & συμβουλές αντιμετώπισης

- **Corrupted images** – Αν μια εικόνα δεν μπορεί να διαβαστεί, το Aspose.Words εισάγει έναν placeholder. Ανιχνεύστε το στο `ResourceSavingCallback` ελέγχοντας `args.getStream().available()`.  
- **Large documents** – Για αρχεία πάνω από 100 MB, κάντε streaming την έξοδο PDF (`doc.save(outputPdf, pdfOptions)` όπου το `outputPdf` είναι `FileOutputStream`) για να διατηρήσετε τη χρήση μνήμης χαμηλή.  
- **Performance** – Η ενεργοποίηση του `RecoveryMode.IGNORE` επιταχύνει τη φόρτωση αλλά μπορεί να χάσει περιεχόμενο. Χρησιμοποιήστε `RECOVER` για μια ισορροπημένη προσέγγιση.  
- **License enforcement** – Σε δοκιμαστική λειτουργία, κάθε αποθηκευμένο έγγραφο παίρνει υδατογράφημα. Καταχωρίστε άδεια για να το αφαιρέσετε—απλώς καλέστε `License license = new License(); license.setLicense("Aspose.Words.lic");` πριν από οποιαδήποτε επεξεργασία.  

## Συχνές ερωτήσεις

**Q: Does this work with .doc files or only .docx?**  
A: Ναι. Το Aspose.Words ανιχνεύει αυτόματα τη μορφή· απλώς αλλάξτε την επέκταση αρχείου στο `inputPath`.

**Q: What if I need MathML instead of LaTeX?**  
A: Αντικαταστήστε το `OfficeMathExportMode.LATEX` με `OfficeMathExportMode.MATHML`. Το υπόλοιπο της διαδικασίας παραμένει ίδιο.

**Q: Can I skip the PDF step?**  
A: Απόλυτα. Σχολιάστε το μπλοκ PDF· ο κώδικας είναι modular, ώστε να μπορείτε να **save document as PDF** μόνο όταν το χρειάζεστε.

**Q: How do I handle password‑protected documents?**  
A: Χρησιμοποιήστε `LoadOptions.setPassword("yourPassword")` πριν δημιουργήσετε το αντικείμενο `Document`.

**Q: Is there a way to embed the LaTeX directly into the PDF?**  
A: Δεν είναι εγγενές· τα PDF δεν καταλαβαίνουν LaTeX. Θα πρέπει να αποδώσετε τις εξισώσεις ως εικόνες πρώτα, κάτι που αναιρεί το σκοπό μιας καθαρής εξαγωγής LaTeX.

---

**Τελευταία ενημέρωση:** 2026-10-23  
**Δοκιμάστηκε με:** Aspose.Words 24.12 for Java  
**Συγγραφέας:** Aspose

## Σχετικές οδηγίες

- [Πώς να εξάγετε LaTeX από Docx – Πλήρης οδηγός Java](/words/java/document-conversion-and-export/how-to-export-latex-from-docx-complete-java-guide/)
- [Μετατροπή Docx σε Markdown – Πλήρης οδηγός με εξαγωγή μαθηματικών](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-guide-with-math-export/)
- [Αποθήκευση Docx ως Txt με εξαγωγή LaTeX Math – Πλήρης οδηγός Java](/words/java/document-conversion-and-export/save-docx-as-txt-with-latex-math-export-complete-java-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}