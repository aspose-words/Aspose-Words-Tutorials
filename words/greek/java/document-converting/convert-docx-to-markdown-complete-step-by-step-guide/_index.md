---
category: general
date: 2026-06-20
description: Μετατρέψτε το docx σε markdown με εικόνες και εξισώσεις LaTeX. Μάθετε
  πώς να αποθηκεύετε ένα έγγραφο Word ως markdown χρησιμοποιώντας το Aspose.Words
  σε λίγα λεπτά.
draft: false
keywords:
- convert docx to markdown
- convert word to markdown with images
- save word document as markdown
- export word equations as latex
language: el
og_description: Μετατρέψτε το docx σε markdown γρήγορα. Αυτός ο οδηγός δείχνει πώς
  να αποθηκεύσετε ένα έγγραφο Word ως markdown, να ενσωματώσετε εικόνες και να εξάγετε
  εξισώσεις ως LaTeX.
og_title: Μετατροπή docx σε markdown – Πλήρης Οδηγός Προγραμματισμού
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: convert docx to markdown with images and LaTeX equations. Learn how
    to save word document as markdown using Aspose.Words in minutes.
  headline: convert docx to markdown – Complete Step‑by‑Step Guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Markdown
- DocumentConversion
title: Μετατροπή docx σε markdown – Πλήρης Οδηγός Βήμα‑βήμα
url: /el/java/document-converting/convert-docx-to-markdown-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# μετατροπή docx σε markdown – Πλήρης Οδηγός Βήμα‑Βήμα

Έχετε αναρωτηθεί ποτέ πώς να **convert docx to markdown** χωρίς να χάσετε ούτε μία εικόνα ή εξίσωση; Δεν είστε οι μόνοι· οι προγραμματιστές χρειάζονται συνεχώς έναν αξιόπιστο τρόπο να μετατρέπουν αρχεία Word σε καθαρό, φιλικό προς τον έλεγχο εκδόσεων markdown. Σε αυτό το tutorial θα περάσουμε από μια πρακτική λύση που όχι μόνο *convert word to markdown with images* αλλά και *export word equations as latex* ώστε τα επιστημονικά σας έγγραφα να παραμείνουν αμετάβλητα.

Η σύντομη απάντηση: χρησιμοποιώντας το Aspose.Words for Java μπορείτε να φορτώσετε ένα `.docx`, να ρυθμίσετε μερικές `MarkdownSaveOptions` και να καλέσετε `document.save(...)`. Χωρίς εξωτερικούς μετατροπείς, χωρίς χειροκίνητο copy‑pasting, και σίγουρα χωρίς ελλιπείς εικόνες. Ας βουτήξουμε.

## Τι Θα Χρειαστείτε

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα παρακάτω προαπαιτούμενα:

| Προαπαιτούμενο | Γιατί είναι σημαντικό |
|--------------|----------------|
| **Java 17+** (ή οποιοδήποτε πρόσφατο JDK) | Το Aspose.Words λειτουργεί σε Java 8+· τα νεότερα JDK προσφέρουν καλύτερη απόδοση. |
| **Aspose.Words for Java** βιβλιοθήκη (κατεβάστε από το Aspose ή χρησιμοποιήστε Maven) | Παρέχει τις κλάσεις `Document`, `MarkdownSaveOptions` και `OfficeMathExportMode`. |
| **Ένα δείγμα `.docx`** που περιέχει κείμενο, εικόνες και τουλάχιστον μία εξίσωση | Σας επιτρέπει να επαληθεύσετε ότι η μετατροπή διαχειρίζεται όλα τα στοιχεία. |
| **IDE ή κειμενογράφο** (IntelliJ, VS Code κ.λπ.) | Κάνει την επεξεργασία και εκτέλεση του κώδικα εύκολη. |

Αν έχετε ήδη ένα Maven project, προσθέστε την εξάρτηση:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- check for the latest version -->
</dependency>
```

> **Συμβουλή:** Η δωρεάν δοκιμή λειτουργεί για τις περισσότερες περιπτώσεις, αλλά μια πλήρης άδεια αφαιρεί το υδατογράφημα αξιολόγησης από το παραγόμενο markdown.

## Βήμα 1 – Φόρτωση του Πηγαίου Εγγράφου

Το πρώτο πράγμα που πρέπει να κάνετε είναι να ανοίξετε το αρχείο Word που θέλετε να μετατρέψετε. Σκεφτείτε την κλάση `Document` ως ένα wrapper γύρω από ολόκληρο το πακέτο `.docx`.

```java
import com.aspose.words.Document;

// Load the source .docx
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου σας δίνει πρόσβαση σε κάθε μέρος του αρχείου—παραγράφους, πίνακες, εικόνες και ακόμη και στα κρυφά αντικείμενα Office Math που αντιπροσωπεύουν εξισώσεις.

## Βήμα 2 – Διαμόρφωση των Επιλογών Αποθήκευσης Markdown

Τώρα έρχεται το διασκεδαστικό κομμάτι: λέμε στο Aspose πώς θέλουμε να φαίνεται η έξοδος markdown. Εδώ είναι που *convert word to markdown with images* και επίσης αποφασίζετε πώς θα αποδοθούν οι εξισώσεις.

```java
import com.aspose.words.MarkdownSaveOptions;
import com.aspose.words.OfficeMathExportMode;

// Create options object
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

// Export equations as LaTeX (crucial for scientific docs)
mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Optional: increase image DPI so embedded pictures stay sharp
mdOptions.setImageResolution(300);
```

### Τι κάνουν οι σημαίες

* `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – λέει στη βιβλιοθήκη να μετατρέπει κάθε εξίσωση Word σε απόσπασμα LaTeX τυλιγμένο σε `$…$` (inline) ή `$$…$$` (block). Αυτό ικανοποιεί την απαίτηση **export word equations as latex**.
* `setImageResolution(300)` – ελέγχει την πυκνότητα εικονοστοιχείων των ραστερ εικόνων που ενσωματώνονται ως base64 data URLs. Υψηλότερο DPI σημαίνει μεγαλύτερα αρχεία markdown αλλά πιο καθαρές εικόνες.

## Βήμα 3 – Αποθήκευση του Εγγράφου ως Markdown

Με τις επιλογές έτοιμες, το τελικό βήμα είναι μια μόνο γραμμή κώδικα που γράφει το αρχείο markdown στον δίσκο.

```java
// Save as .md using the configured options
document.save("YOUR_DIRECTORY/output.md", mdOptions);
```

Αυτό είναι όλο—το αρχείο Word σας είναι τώρα ένα έγγραφο markdown πλήρες με ενσωματωμένες εικόνες και εξισώσεις LaTeX.

## Επαλήθευση του Αποτελέσματος

Ανοίξτε το `output.md` σε οποιονδήποτε markdown viewer (VS Code, Typora, GitHub preview). Θα πρέπει να δείτε:

* Παραγράφους απλού κειμένου που αποδίδονται ως markdown.
* Εικόνες ενσωματωμένες ως `![Alt text](data:image/png;base64,…)` ή ως εξωτερικά αρχεία αν αλλάξατε τη λειτουργία διαχείρισης εικόνων.
* Εξισώσεις που εμφανίζονται ως `$E = mc^2$` ή `$$\int_{a}^{b} f(x)dx$$`.

Αν κάτι φαίνεται λανθασμένο, ελέγξτε ξανά το αρχικό `.docx` για μη υποστηριζόμενα χαρακτηριστικά (π.χ., SmartArt). Το Aspose.Words διαχειρίζεται την πλειονότητα των δομών του Word, αλλά μερικά εξωτικά αντικείμενα μπορεί να χρειάζονται προσαρμοσμένη επεξεργασία.

![ροή εργασίας μετατροπής docx σε markdown](convert-docx-to-markdown-workflow.png "Διάγραμμα που δείχνει τη διαδικασία μετατροπής από .docx σε .md με εικόνες και εξισώσεις LaTeX")

*Κείμενο εναλλακτικής εικόνας:* **convert docx to markdown** εικονογράφηση ροής εργασίας.

## Προχωρημένο: Έλεγχος Εξαγωγής Εικόνων

Από προεπιλογή το Aspose ενσωματώνει τις εικόνες απευθείας στο markdown χρησιμοποιώντας base64. Αν προτιμάτε ξεχωριστά αρχεία εικόνας (χρήσιμο για μεγάλα αποθετήρια), αλλάξτε το `ImageSavingCallback`:

```java
import com.aspose.words.ImageSavingArgs;
import com.aspose.words.IImageSavingCallback;
import java.io.File;

mdOptions.setImageSavingCallback(new IImageSavingCallback() {
    @Override
    public void imageSaving(ImageSavingArgs args) {
        String fileName = "images/" + args.getImageFileName();
        args.setImageFileName(fileName);
        args.setImageStream(new java.io.FileOutputStream(new File(fileName)));
        args.setKeepImageStreamOpen(false);
    }
});
```

Τώρα κάθε εικόνα τοποθετείται σε φάκελο `images/`, και το markdown τις αναφέρει με σχετικό μονοπάτι—ιδανικό για στατικούς δημιουργούς ιστοσελίδων όπως Hugo ή Jekyll.

## Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|---------|--------------|----------|
| Οι εικόνες εμφανίζονται ως σπασμένοι σύνδεσμοι | `setImageResolution` ορίστηκε πολύ χαμηλό ή το callback δεν γράφει αρχεία | Αυξήστε το DPI ή βεβαιωθείτε ότι το callback γράφει σε έναν φάκελο που υπάρχει. |
| Οι εξισώσεις εμφανίζονται ως απλό κείμενο | `OfficeMathExportMode` παραμένει στην προεπιλογή (`TEXT`) | Ορίστε σε `LATEX` όπως φαίνεται στο Βήμα 2. |
| Το markdown περιέχει οντότητες `&#...;` | Οι ειδικοί χαρακτήρες δεν διαφράχθηκαν | Χρησιμοποιήστε `mdOptions.setExportImagesAsBase64(true)` για να εξαναγκάσετε την κωδικοποίηση base64, αποφεύγοντας τις HTML οντότητες. |
| Το αρχείο εξόδου είναι κενό | Λάθος διαδρομή εισόδου ή αρχείο δεν βρέθηκε | Επαληθεύστε ότι το `input.docx` υπάρχει και η διαδρομή είναι απόλυτη ή σωστά σχετική με τον τρέχοντα φάκελο εργασίας. |

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται μια αυτόνομη κλάση Java που μπορείτε να αντιγράψετε‑επικολλήσετε στο project σας και να τρέξετε αμέσως.

```java
package com.example.docx2md;

import com.aspose.words.*;

import java.io.File;
import java.io.FileOutputStream;

/**
 * Demonstrates how to convert a DOCX file to Markdown,
 * embed images, and export equations as LaTeX.
 */
public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // 1️⃣ Load the source Word document
        // -----------------------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -----------------------------------------------------------------
        // 2️⃣ Configure Markdown save options
        // -----------------------------------------------------------------
        MarkdownSaveOptions options = new MarkdownSaveOptions();

        // Export Word equations as LaTeX – fulfills export word equations as latex
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Set a high DPI for embedded images (convert word to markdown with images)
        options.setImageResolution(300);

        // OPTIONAL: Save images to external files instead of base64
        options.setImageSavingCallback(new IImageSavingCallback() {
            @Override
            public void imageSaving(ImageSavingArgs e) throws Exception {
                // Ensure the images folder exists
                File imagesDir = new File("YOUR_DIRECTORY/images");
                if (!imagesDir.exists()) imagesDir.mkdirs();

                String outPath = "YOUR_DIRECTORY/images/" + e.getImageFileName();
                e.setImageFileName(outPath);
                e.setImageStream(new FileOutputStream(outPath));
                e.setKeepImageStreamOpen(false);
            }
        });

        // -----------------------------------------------------------------
        // 3️⃣ Save as Markdown – this is where we actually convert docx to markdown
        // -----------------------------------------------------------------
        doc.save("YOUR_DIRECTORY/output.md", options);

        System.out.println("Conversion complete! Check output.md and the images folder.");
    }
}
```

### Αναμενόμενη Έξοδος

Η εκτέλεση της παραπάνω κλάσης παράγει δύο αντικείμενα:

1. **output.md** – ένα αρχείο markdown έτοιμο για Git, στατικούς δημιουργούς ιστοσελίδων ή οποιονδήποτε επεξεργαστή.
2. **images/** – φάκελο που περιέχει κάθε εικόνα που εξήχθη από το αρχικό αρχείο Word.

Ανοίξτε το `output.md` και θα δείτε κάτι σαν:

```markdown
# Sample Report

This is a paragraph with an inline equation $E = mc^2$.

![Diagram](images/image1.png)

$$\int_{0}^{\infty} e^{-x} dx = 1$$
```

## Περίληψη & Επόμενα Βήματα

Καλύψαμε όλα όσα χρειάζεστε για να **convert docx to markdown** διατηρώντας εικόνες και εξισώσεις LaTeX. Συνοπτικά:

* Φορτώστε το `.docx` με `Document`.
* Ρυθμίστε τις `MarkdownSaveOptions` για **save word document as markdown**, ορίστε DPI εικόνας και επιλέξτε εξαγωγή LaTeX.
* Καλέστε `document.save(...)` και τελειώσατε.

Τι ακολουθεί; Δοκιμάστε αυτές τις επεκτάσεις:

* **Custom CSS** – προσθέστε ένα μπλοκ στυλ στην αρχή για να ελέγξετε πώς αποδίδει το markdown στον ιστότοπό σας.
* **Batch conversion** – κάντε βρόχο σε έναν φάκελο με αρχεία Word και δημιουργήστε ολόκληρο σύστημα τεκμηρίωσης.
* **Table handling** – εξερευνήστε το `MarkdownSaveOptions.setTableConversionMode(...)` για πιο ακριβή έλεγχο της μορφοποίησης πινάκων.

Νιώστε ελεύθεροι να πειραματιστείτε· το Aspose API είναι αρκετά ευέλικτο για τις περισσότερες ακραίες περιπτώσεις.

---

*Καλό κώδικα! Αν αντιμετωπίσετε κάποιο πρόβλημα, αφήστε ένα σχόλιο παρακάτω ή ελέγξτε την τεκμηρίωση Aspose.Words Java για πιο βαθιές πληροφορίες.*

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Αποθήκευση Εικόνων Word – Μετατροπή Word σε Markdown με Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Μετατροπή docx σε markdown – Εξαγωγή Μαθηματικών Εξισώσεων σε LaTeX με Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Αποθήκευση docx ως markdown – Πλήρης Οδηγός C# με Εξισώσεις LaTeX](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-c-guide-with-latex-equations/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}