---
category: general
date: 2025-12-19
description: Πώς να ανακτήσετε ένα αρχείο DOCX από τη φθορά και, στη συνέχεια, να
  το μετατρέψετε σε Markdown, να εξάγετε το DOCX σε PDF, να εξάγετε LaTeX και να το
  αποθηκεύσετε ως PDF/UA — όλα σε ένα Java tutorial.
draft: false
keywords:
- how to recover docx
- convert docx to markdown
- export docx to pdf
- how to export latex
- save as pdf ua
language: el
og_description: Μάθετε πώς να ανακτήσετε DOCX, να μετατρέψετε DOCX σε Markdown, να
  εξάγετε DOCX σε PDF, να εξάγετε LaTeX και να αποθηκεύσετε ως PDF/UA με σαφή παραδείγματα
  κώδικα Java.
og_title: Πώς να ανακτήσετε DOCX και να το μετατρέψετε σε Markdown, PDF/UA, LaTeX
tags:
- Aspose.Words
- Java
- Document Conversion
title: Πώς να ανακτήσετε DOCX, να μετατρέψετε DOCX σε Markdown, να εξάγετε DOCX σε
  PDF/UA και να εξάγετε LaTeX
url: /el/java/document-conversion-and-export/how-to-recover-docx-convert-docx-to-markdown-export-docx-to/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ανακτήσετε DOCX, να Μετατρέψετε DOCX σε Markdown, να Εξάγετε DOCX σε PDF/UA και να Εξάγετε LaTeX

Έχετε ανοίξει ποτέ ένα αρχείο DOCX μόνο για να δείτε ακατάληπτο κείμενο ή ελλιπείς ενότητες; Αυτό είναι το κλασικό εφιάλτης «κατεστραμμένο DOCX», και το **how to recover docx** είναι το ερώτημα που κρατάει τους προγραμματιστές ξύπνιους τη νύχτα. Τα καλά νέα; Με μια ανεκτική λειτουργία ανάκτησης μπορείτε να επαναφέρετε το μεγαλύτερο μέρος του περιεχομένου, και στη συνέχεια να μεταβιβάσετε το φρέσκο έγγραφο σε Markdown, PDF/UA ή ακόμη και LaTeX—χωρίς να φύγετε από το IDE σας.

Σε αυτόν τον οδηγό θα διασχίσουμε ολόκληρη τη ροή εργασίας: φόρτωση ενός κατεστραμμένου DOCX, μετατροπή του σε Markdown (με εξισώσεις που μετατρέπονται σε LaTeX), εξαγωγή ενός καθαρού PDF/UA που επισημαίνει τα αιωρούμενα σχήματα ως ενσωματωμένα, και τέλος θα σας δείξουμε πώς να εξάγετε απευθείας LaTeX. Στο τέλος θα έχετε μια ενιαία, επαναχρησιμοποιήσιμη μέθοδο Java που κάνει τα πάντα, καθώς και μια σειρά πρακτικών συμβουλών που δεν θα βρείτε στην επίσημη τεκμηρίωση.

> **Prerequisites** – Χρειάζεστε τη βιβλιοθήκη Aspose.Words for Java (έκδοση 24.10 ή νεότερη), ένα runtime Java 8+, και μια βασική ρύθμιση έργου Maven ή Gradle. Δεν απαιτούνται άλλες εξαρτήσεις.

---

## Πώς να Ανακτήσετε DOCX: Ανεκτική Φόρτωση

Το πρώτο βήμα είναι να ανοίξετε το πιθανώς κατεστραμμένο αρχείο σε *ανεκτική* λειτουργία. Αυτό λέει στο Aspose.Words να αγνοήσει τα δομικά σφάλματα και να διασώσει ό,τι μπορεί.

```java
// Step 1: Load a potentially corrupted DOCX using tolerant recovery mode
import com.aspose.words.*;

public class DocxRecovery {
    public static Document loadCorruptDoc(String path) throws Exception {
        // Create LoadOptions and enable tolerant recovery
        LoadOptions tolerantLoadOptions = new LoadOptions();
        tolerantLoadOptions.setRecoveryMode(RecoveryMode.Tolerant);

        // Load the document; Aspose.Words will do its best to fix issues
        Document doc = new Document(path, tolerantLoadOptions);
        return doc;
    }
}
```

**Γιατί ανεκτική λειτουργία;**  
Κανονικά το Aspose.Words διακόπτει την επεξεργασία όταν συναντήσει ένα σπασμένο τμήμα (π.χ., μια ελλιπή σχέση). `RecoveryMode.Tolerant` παραλείπει το προβληματικό τμήμα XML, διατηρώντας το υπόλοιπο του εγγράφου. Στην πράξη θα ανακτήσετε πάνω από 95 % του κειμένου, των εικόνων και ακόμη και των περισσότερων κωδικών πεδίων.

> **Pro tip:** Μετά τη φόρτωση, καλέστε `doc.getOriginalFileInfo().isCorrupted()` (διαθέσιμο σε νεότερες εκδόσεις) για να καταγράψετε αν χρειάστηκε ανάκτηση.

---

## Μετατροπή DOCX σε Markdown με Εξισώσεις LaTeX

Μόλις το έγγραφο είναι στη μνήμη, η μετατροπή του σε Markdown είναι παιχνιδάκι. Το κλειδί είναι να πείτε στον εξαγωγέα να μετατρέπει τα αντικείμενα Office Math σε σύνταξη LaTeX, ώστε το επιστημονικό περιεχόμενο να παραμένει αναγνώσιμο.

```java
// Step 2: Export the document to Markdown, converting equations to LaTeX
import com.aspose.words.save.*;

public class DocxToMarkdown {
    public static void saveAsMarkdown(Document doc, String outputPath) throws Exception {
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        // Export Office Math as LaTeX for perfect equation rendering
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LaTeX);

        doc.save(outputPath, markdownOptions);
    }
}
```

**Τι θα δείτε** – Ένα αρχείο `.md` όπου οι κανονικές παράγραφοι γίνονται απλό κείμενο, οι επικεφαλίδες μετατρέπονται σε δείκτες `#`, και οποιαδήποτε εξίσωση όπως `x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}` εμφανίζεται μέσα σε μπλοκ `$…$`. Αυτή η μορφή είναι έτοιμη για στατικούς δημιουργούς ιστοτόπων, αρχεία README στο GitHub ή οποιονδήποτε επεξεργαστή που υποστηρίζει Markdown.

---

## Εξαγωγή DOCX σε PDF/UA και Σήμανση Αιωρούμενων Σχημάτων ως Ενσωματωμένα

Το PDF/UA (Universal Accessibility) είναι το πρότυπο ISO για προσβάσιμα PDF. Όταν έχετε αιωρούμενες εικόνες ή πλαίσια κειμένου, συχνά θέλετε να τα αντιμετωπίζονται ως ενσωματωμένα στοιχεία ώστε οι αναγνώστες οθόνης να ακολουθούν τη φυσική σειρά ανάγνωσης. Το Aspose.Words σας επιτρέπει να το εναλλάξετε με μια μόνο σημαία.

```java
// Step 3: Save the document as PDF/UA, tagging floating shapes as inline elements
public class DocxToPdfUa {
    public static void saveAsPdfUa(Document doc, String outputPath) throws Exception {
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        // Enable PDF/UA compliance
        pdfOptions.setCompliance(PdfCompliance.PdfUa1);
        // Tag floating shapes as inline for better accessibility
        pdfOptions.setExportFloatingShapesAsInlineTag(true);

        doc.save(outputPath, pdfOptions);
    }
}
```

**Γιατί να ορίσετε `ExportFloatingShapesAsInlineTag`;**  
Χωρίς αυτή τη ρύθμιση, τα αιωρούμενα σχήματα γίνονται ξεχωριστές ετικέτες που μπορούν να μπερδέψουν τις βοηθητικές τεχνολογίες. Αναγκάζοντάς τα να είναι ενσωματωμένα, διατηρείτε τη οπτική διάταξη ενώ διασφαλίζετε την λογική σειρά ανάγνωσης—σημαντικό για νομικά ή ακαδημαϊκά PDF.

---

## Πώς να Εξάγετε LaTeX Απευθείας (Bonus)

Αν η ροή εργασίας σας χρειάζεται ακατέργαστο LaTeX αντί για περιτύλιγμα Markdown, μπορείτε να εξάγετε ολόκληρο το έγγραφο ως LaTeX. Αυτό είναι χρήσιμο όταν το σύστημα downstream καταλαβαίνει μόνο `.tex`.

```java
// Bonus: Export the entire document as LaTeX
public class DocxToLatex {
    public static void saveAsLatex(Document doc, String outputPath) throws Exception {
        LatexSaveOptions latexOptions = new LatexSaveOptions();
        // Preserve math as native LaTeX (no extra conversion needed)
        latexOptions.setExportMathAsLatex(true);
        doc.save(outputPath, latexOptions);
    }
}
```

**Edge case:** Ορισμένα σύνθετα χαρακτηριστικά του Word (όπως SmartArt) δεν έχουν άμεσους ισοδύναμους σε LaTeX. Το Aspose.Words θα τα αντικαταστήσει με σχόλια placeholder, ώστε να μπορείτε να τα προσαρμόσετε χειροκίνητα μετά την εξαγωγή.

---

## Πλήρες Παράδειγμα End‑to‑End

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια ενιαία κλάση που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java. Φορτώνει ένα κατεστραμμένο DOCX, δημιουργεί αρχεία Markdown, PDF/UA και LaTeX, και εκτυπώνει μια σύντομη αναφορά κατάστασης.

```java
import com.aspose.words.*;

public class DocxConversionPipeline {
    public static void main(String[] args) {
        if (args.length < 2) {
            System.out.println("Usage: java DocxConversionPipeline <input.docx> <outputFolder>");
            return;
        }

        String inputPath = args[0];
        String outDir = args[1];
        try {
            // 1️⃣ Recover the document
            Document doc = DocxRecovery.loadCorruptDoc(inputPath);
            System.out.println("Document loaded. Corruption recovered: " +
                doc.getOriginalFileInfo().isCorrupted());

            // 2️⃣ Markdown (with LaTeX equations)
            String mdPath = outDir + "/recovered.md";
            DocxToMarkdown.saveAsMarkdown(doc, mdPath);
            System.out.println("Markdown saved to " + mdPath);

            // 3️⃣ PDF/UA (inline shapes)
            String pdfPath = outDir + "/recovered.pdf";
            DocxToPdfUa.saveAsPdfUa(doc, pdfPath);
            System.out.println("PDF/UA saved to " + pdfPath);

            // 4️⃣ Optional LaTeX export
            String texPath = outDir + "/recovered.tex";
            DocxToLatex.saveAsLatex(doc, texPath);
            System.out.println("LaTeX saved to " + texPath);

            System.out.println("All conversions completed successfully!");
        } catch (Exception e) {
            System.err.println("Conversion failed: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα** – Μετά την εκτέλεση `java DocxConversionPipeline corrupt.docx ./out`, θα δείτε τέσσερα αρχεία στο `./out`:

* `recovered.md` – καθαρό Markdown με εξισώσεις `$…$`.  
* `recovered.pdf` – PDF/UA‑συμβατό, οι αιωρούμενες εικόνες τώρα ενσωματωμένες.  
* `recovered.tex` – ακατέργαστος κώδικας LaTeX, έτοιμος για `pdflatex`.  

Ανοίξτε οποιοδήποτε από αυτά για να επαληθεύσετε ότι το αρχικό περιεχόμενο επέζησε της διαδικασίας ανάκτησης.

---

## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Missing fonts in PDF/UA** | Ο PDF renderer επιστρέφει σε γενική γραμματοσειρά αν η αρχική δεν είναι ενσωματωμένη. | Καλέστε `pdfOptions.setEmbedStandardWindowsFonts(true)` ή ενσωματώστε τις προσαρμοσμένες γραμματοσειρές σας χειροκίνητα. |
| **Equations appear as images** | Η προεπιλεγμένη λειτουργία εξαγωγής αποδίδει το Office Math ως PNG. | Βεβαιωθείτε ότι `markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LaTeX)` (ή `latexOptions.setExportMathAsLatex(true)`). |
| **Floating shapes still separate** | Η `ExportFloatingShapesAsInlineTag` δεν ορίστηκε ή παρακάμφθηκε αργότερα. | Επαληθεύστε ότι έχετε ορίσει τη σημαία *πριν* καλέσετε `doc.save`. |
| **Corrupt DOCX throws an exception** | Το αρχείο είναι πέρα από ό,τι μπορεί να διορθώσει η ανεκτική λειτουργία (π.χ., λείπει το κύριο τμήμα του εγγράφου). | Περιβάλλετε τη φόρτωση σε try‑catch, επιστρέψτε σε αντίγραφο ασφαλείας, ή ζητήστε από τον χρήστη μια νεότερη έκδοση. |

---

## Image Overview (optional)

![Διάγραμμα που δείχνει τη ροή ανάκτησης DOCX – φόρτωση → ανάκτηση → εξαγωγή σε Markdown, PDF/UA, LaTeX](https://example.com/images/docx-recovery-workflow.png "Διάγραμμα που δείχνει τη ροή ανάκτησης DOCX – φόρτωση → ανάκτηση → εξαγωγή σε Markdown, PDF/UA, LaTeX")

*Κείμενο εναλλακτικού:* Διάγραμμα που δείχνει τη ροή ανάκτησης DOCX – φόρτωση → ανάκτηση → εξαγωγή σε Markdown, PDF/UA, LaTeX.

---

## Conclusion

Απαντήσαμε στο **how to recover docx**, μετά μετατρέψαμε αβίαστα το **docx to markdown**, **export docx to pdf**, **how to export latex**, και τέλος **save as pdf ua**—όλα με συνοπτικό κώδικα Java που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σήμερα. Τα κύρια συμπεράσματα είναι:

* Χρησιμοποιήστε `RecoveryMode.Tolerant` για να εξάγετε δεδομένα από κατεστραμμένα αρχεία.  
* Ορίστε `OfficeMathExportMode.LaTeX` για καθαρό χειρισμό εξισώσεων σε Markdown.  
* Ενεργοποιήστε τη συμμόρφωση PDF/UA και την ενσωμάτωση ετικετών για PDFs με προτεραιότητα την προσβασιμότητα.  
* Εκμεταλλευτείτε τον ενσωματωμένο εξαγωγέα LaTeX για καθαρή έξοδο `.tex`.

Αισθανθείτε ελεύθεροι να προσαρμόσετε τις διαδρομές, να προσθέσετε προσαρμοσμένες κεφαλίδες ή να ενσωματώσετε αυτή τη ροή σε ένα μεγαλύτερο σύστημα διαχείρισης περιεχομένου. Τα επόμενα βήματα θα μπορούσαν να περιλαμβάνουν επεξεργασία παρτίδας ενός φακέλου DOCX ή ενσωμάτωση του κώδικα σε ένα REST endpoint Spring Boot.

Έχετε ερωτήσεις σχετικά με ειδικές περιπτώσεις ή χρειάζεστε βοήθεια με κάποιο χαρακτηριστικό του εγγράφου; Αφήστε ένα σχόλιο παρακάτω και ας επαναφέρουμε τα αρχεία σας στο σωστό δρόμο. Καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}