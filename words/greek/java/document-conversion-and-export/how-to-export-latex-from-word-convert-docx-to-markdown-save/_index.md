---
category: general
date: 2025-12-25
description: Πώς να εξάγετε LaTeX ενώ μετατρέπετε DOCX σε markdown και αποθηκεύετε
  το έγγραφο ως PDF—βήμα‑βήμα οδηγός με κώδικα Java.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save document as pdf
- how to save pdf
- save word as markdown
language: el
og_description: Μάθετε πώς να εξάγετε LaTeX ενώ μετατρέπετε DOCX σε markdown και αποθηκεύετε
  το έγγραφο ως PDF με Java. Πλήρης κώδικας και συμβουλές.
og_title: Πώς να εξάγετε LaTeX από το Word – Μετατροπή DOCX σε Markdown & Αποθήκευση
  PDF
tags:
- Aspose.Words
- Java
- Document Conversion
title: 'Πώς να εξάγετε LaTeX από το Word: Μετατροπή DOCX σε Markdown & Αποθήκευση
  ως PDF'
url: /el/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εξάγετε LaTeX από το Word: Μετατροπή DOCX σε Markdown & Αποθήκευση ως PDF

Έχετε αναρωτηθεί ποτέ **πώς να εξάγετε LaTeX** από ένα αρχείο Word χωρίς να χάσετε καμία από τις εντυπωσιακές εξισώσεις; Δεν είστε μόνοι. Σε πολλά έργα—ακαδημαϊκές εργασίες, τεχνικά blogs ή εσωτερικά έγγραφα—χρειάζεται να εξάγετε LaTeX από ένα `.docx`, να μετατρέψετε όλο το περιεχόμενο σε markdown και να διατηρήσετε μια καθαρή έκδοση PDF για διανομή.  

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: **μετατροπή docx σε markdown**, **εξαγωγή LaTeX**, και **αποθήκευση εγγράφου ως PDF** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words for Java. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση πρόγραμμα Java που κάνει τα πάντα, καθώς και μια σειρά πρακτικών συμβουλών που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στον κώδικά σας.

## Τι Θα Μάθετε

- Φορτώστε ένα πιθανώς κατεστραμμένο έγγραφο Word σε λειτουργία ανάκτησης.  
- Εξάγετε τις εξισώσεις Office Math ως LaTeX κατά την αποθήκευση σε markdown.  
- Αποθηκεύστε το ίδιο έγγραφο ως PDF ενώ διαχειρίζεστε τα αιωρούμενα σχήματα ως ενσωματωμένες ετικέτες.  
- Προσαρμόστε τη διαχείριση εικόνων κατά την εξαγωγή σε markdown (αποθηκεύστε τις εικόνες σε αφιερωμένο φάκελο).  
- Πώς να **αποθηκεύσετε το word ως markdown** και να διατηρήσετε ακόμη μια υψηλής ποιότητας αντίγραφο PDF.  

**Προαπαιτούμενα**: Java 17 ή νεότερη, Maven ή Gradle, και άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για πειραματισμό). Δεν απαιτούνται άλλες βιβλιοθήκες τρίτων.

---

## Βήμα 1: Ρυθμίστε το Έργο σας

Πρώτα απ’ όλα—ας προσθέσουμε το jar του Aspose.Words στο classpath. Αν χρησιμοποιείτε Maven, προσθέστε αυτήν την εξάρτηση στο `pom.xml` σας:

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

> **Συμβουλή:** Πάντα χρησιμοποιείτε την πιο πρόσφατη σταθερή έκδοση· περιλαμβάνει διορθώσεις σφαλμάτων για τη λειτουργία ανάκτησης και την εξαγωγή LaTeX.

Δημιουργήστε μια νέα κλάση Java με όνομα `DocxProcessor.java`. Θα εισάγουμε όλα όσα χρειάζονται:

```java
import com.aspose.words.*;

import java.io.File;
import java.io.IOException;
```

## Βήμα 2: Φόρτωση του Εγγράφου σε Λειτουργία Ανάκτησης

Τα κατεστραμμένα αρχεία συμβαίνουν—ιδιαίτερα όταν μεταφέρονται μέσω email ή συγχρονισμού cloud. Το Aspose.Words σας επιτρέπει να τα ανοίξετε σε *λειτουργία ανάκτησης* ώστε να μην χάσετε ολόκληρο το έγγραφο.

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

Γιατί να χρησιμοποιήσετε το `RecoveryMode.RECOVER`; Προσπαθεί να διασώσει όσο το δυνατόν περισσότερο περιεχόμενο, ενώ εξακολουθεί να ρίχνει εξαίρεση αν το αρχείο είναι εντελώς αδιάβαστο. Αυτό εξισορροπεί την ασφάλεια με την πρακτικότητα.

## Βήμα 3: Εξαγωγή LaTeX Κατά τη Μετατροπή DOCX σε Markdown

Τώρα έρχεται το αστέρι της παράστασης: **πώς να εξάγετε LaTeX** από το έγγραφο Word. Η κλάση `MarkdownSaveOptions` διαθέτει την ιδιότητα `OfficeMathExportMode` που σας επιτρέπει να επιλέξετε LaTeX, MathML ή έξοδο εικόνας. Θα επιλέξουμε LaTeX.

```java
        // Step 3: Export Office Math as LaTeX during markdown conversion
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        doc.save(outputMarkdown, mdOptions);
```

Το παραγόμενο `output.md` θα περιέχει τμήματα LaTeX περικυκλωμένα με `$…$` για ενσωματωμένες εξισώσεις ή `$$…$$` για εξισώσεις εμφάνισης. Αν ανοίξετε το αρχείο σε έναν επεξεργαστή markdown που υποστηρίζει MathJax ή KaTeX, οι εξισώσεις θα εμφανιστούν όμορφα.

> **Γιατί LaTeX;** Επειδή είναι η κοινή γλώσσα της επιστημονικής δημοσίευσης. Η άμεση εξαγωγή σε LaTeX αποφεύγει τη μείωση ποιότητας που θα προέκυπτε αν επιλέγατε εικόνες.

## Βήμα 4: Αποθήκευση του Εγγράφου ως PDF (και Διατήρηση Αιωμενων Σχημάτων)

Συχνά χρειάζεστε ακόμη μια έκδοση PDF για αξιολογητές που δεν είναι εξοικειωμένοι με το markdown. Το Aspose.Words το κάνει αυτό εύκολο, και μπορείτε να ελέγξετε πώς διαχειρίζονται τα αιωρούμενα σχήματα (όπως διαγράμματα).

```java
        // Step 4: Save as PDF, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save(outputPdf, pdfOptions);
```

Ορίζοντας το `ExportFloatingShapesAsInlineTag` σε `true` μετατρέπει κάθε αιωρούμενο σχήμα σε ενσωματωμένη ετικέτα `<span>` στην εσωτερική δομή του PDF, κάτι που μπορεί να είναι χρήσιμο για επεξεργασία downstream (π.χ., εργαλεία προσβασιμότητας PDF).

## Βήμα 5: Προσαρμογή Διαχείρισης Εικόνων Κατά την Αποθήκευση Markdown

Από προεπιλογή, το Aspose.Words αποθηκεύει κάθε εικόνα στον ίδιο φάκελο με το αρχείο markdown, ονομάζοντάς τες διαδοχικά. Αν προτιμάτε έναν τακτοποιημένο υποφάκελο `images/`, μπορείτε να συνδέσετε το `ResourceSavingCallback`.

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

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το πλήρες αρχείο `DocxProcessor.java` που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

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

### Αναμενόμενο Αποτέλεσμα

- `output.md` – αρχείο markdown με εξισώσεις LaTeX (`$…$` και `$$…$$`).  
- `output.pdf` – PDF υψηλής ανάλυσης, τα αιωρούμενα σχήματα μετατράπηκαν σε ενσωματωμένες ετικέτες.  
- `output_with_custom_images.md` – ίδιο markdown αλλά όλες οι εικόνες αποθηκεύονται στο `images/`.  

Ανοίξτε το markdown στο VS Code με την επέκταση *Markdown Preview Enhanced* και θα δείτε τις εξισώσεις να εμφανίζονται ακριβώς όπως εμφανίστηκαν στο αρχικό αρχείο Word.

## Συχνές Ερωτήσεις (FAQs)

**Ε: Λειτουργεί αυτό με αρχεία .doc ή μόνο .docx;**  
Α: Ναι. Το Aspose.Words ανιχνεύει αυτόματα τη μορφή. Απλώς αλλάξτε την επέκταση του αρχείου στο `inputPath`.

**Ε: Τι γίνεται αν χρειάζομαι MathML αντί για LaTeX;**  
Α: Αντικαταστήστε το `OfficeMathExportMode.LATEX` με `OfficeMathExportMode.MATHML`. Το υπόλοιπο της διαδικασίας παραμένει αμετάβλητο.

**Ε: Μπορώ να παραλείψω το βήμα PDF;**  
Α: Απόλυτα. Απλώς σχολιάστε το τμήμα PDF. Ο κώδικας είναι modular, έτσι μπορείτε να **αποθηκεύσετε το έγγραφο ως PDF** μόνο όταν το χρειάζεστε.

**Ε: Πώς να διαχειριστώ έγγραφα με προστασία κωδικού;**  
Α: Χρησιμοποιήστε `LoadOptions.setPassword("yourPassword")` πριν δημιουργήσετε το αντικείμενο `Document`.

**Ε: Υπάρχει τρόπος να ενσωματώσω το LaTeX απευθείας στο PDF;**  
Α: Όχι εγγενώς· τα PDF δεν καταλαβαίνουν LaTeX. Θα πρέπει πρώτα να αποδώσετε τις εξισώσεις ως εικόνες, κάτι που αναιρεί το σκοπό μιας καθαρής εξαγωγής LaTeX.

## Περιπτώσεις Ορίων & Συμβουλές

- **Κατεστραμμένες Εικόνες**: Αν μια εικόνα δεν μπορεί να διαβαστεί, το Aspose.Words θα εισάγει έναν placeholder. Μπορείτε να το εντοπίσετε στο `ResourceSavingCallback` ελέγχοντας το `args.getStream().available()`.
- **Μεγάλα Έγγραφα**: Για αρχεία άνω των 100 MB, σκεφτείτε τη ροή εξόδου PDF (`doc.save(outputPdf, pdfOptions)` όπου `outputPdf` είναι ένα `FileOutputStream`) για να αποφύγετε την πίεση μνήμης.
- **Απόδοση**: Η ενεργοποίηση του `RecoveryMode.IGNORE` επιταχύνει τη φόρτωση αλλά μπορεί να χάσει περιεχόμενο. Χρησιμοποιήστε το `RECOVER` για μια ισορροπημένη προσέγγιση.
- **Επιβολή Άδειας**: Σε λειτουργία δοκιμής, κάθε αποθηκευμένο έγγραφο παίρνει υδατογράφημα. Καταχωρήστε μια άδεια για να το αφαιρέσετε—απλώς καλέστε `License license = new License(); license.setLicense("Aspose.Words.lic");` πριν από οποιαδήποτε επεξεργασία.

## Συμπέρασμα

Αυτά είναι—**πώς να εξάγετε LaTeX** από ένα αρχείο Word, **να μετατρέψετε docx σε markdown**, και **να αποθηκεύσετε το έγγραφο ως PDF** σε ένα ενιαίο, τακτοποιημένο πρόγραμμα Java. Καλύψαμε τη φόρτωση σε λειτουργία ανάκτησης, την εξαγωγή LaTeX, τη δημιουργία PDF με διαχείριση αιωρούμενων σχημάτων και προσαρμοσμένους φακέλους εικόνων για markdown.

Από εδώ μπορείτε να πειραματιστείτε με άλλες μορφές εξαγωγής (HTML, EPUB), να ενσωματώσετε αυτή τη λογική σε μια υπηρεσία web ή να αυτοματοποιήσετε την επεξεργασία δεκάδων αρχείων. Τα δομικά στοιχεία είναι όλα στη θέση τους, και το API του Aspose.Words καθιστά την επέκταση της ροής εργασίας εύκολη.

Αν βρήκατε αυτόν τον οδηγό χρήσιμο, δώστε του ένα αστέρι στο GitHub, μοιραστείτε τον με συναδέλφους ή αφήστε ένα σχόλιο παρακάτω με τις δικές σας προσαρμογές. Καλή προγραμματιστική δουλειά, και εύχομαι το LaTeX σας να εμφανίζεται πάντα άψογα!

![Διάγραμμα που δείχνει τη διαδικασία μετατροπής από DOCX → Markdown (με LaTeX) → PDF, εναλλακτικό κείμενο: "Πώς να εξάγετε LaTeX ενώ μετατρέπετε DOCX σε markdown και αποθηκεύετε ως PDF"]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}