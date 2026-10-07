---
category: general
date: 2026-10-07
description: Μάθετε πώς να μετατρέψετε DOCX σε PDF σε Java, να εξάγετε floating shapes
  ως inline tags, και να κάνετε batch convert DOCX σε PDF αποδοτικά.
draft: false
keywords:
- how to convert docx to pdf java
- batch convert docx to pdf
- export floating shapes inline
lastmod: 2026-10-07
og_description: Μάθετε πώς να μετατρέψετε DOCX σε PDF σε Java, να εξάγετε floating
  shapes ως inline tags, και να κάνετε batch convert DOCX σε PDF αποδοτικά.
og_image_alt: 'Developer guide: Convert DOCX to PDF in Java with inline shape export'
og_title: Πώς να μετατρέψετε DOCX σε PDF σε Java – shape export guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to convert DOCX to PDF in Java, export floating shapes as
    inline tags, and batch convert DOCX to PDF efficiently.
  headline: How to convert DOCX to PDF in Java – shape export guide
  type: TechArticle
- questions:
  - answer: Yes—load the document with `LoadOptions` that include the password, then
      proceed with the same save logic.
    question: Does this work with password‑protected DOCX files?
  - answer: Aspose.Words rasterizes vector graphics by default; to keep them vector
      you can enable `pdfOptions.setVectorRasterizationMode(VectorRasterizationMode.VectorOnly)`.
    question: What about SVG or EMF images inside the Word file?
  - answer: Links are retained automatically when you use `PdfSaveOptions`. Avoid
      disabling tags, as that can drop the logical link structure.
    question: How do I preserve hyperlinks while converting?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("YOUR_DIRECTORY"))`, apply
      the same load‑configure‑save sequence to each file, and handle exceptions per
      file so one bad document doesn’t halt the whole run.
    question: Can I batch‑process a folder of DOCX files?
  - answer: Enable `pdfOptions.setMemoryOptimization(true)` and consider streaming
      the output to avoid loading the entire PDF into memory.
    question: How can I improve performance for very large documents?
  type: FAQPage
tags:
- convert docx to pdf
- Aspose.Words
- Java
- PDF conversion
- batch convert docx to pdf
title: Πώς να μετατρέψετε DOCX σε PDF σε Java – shape export guide
url: /el/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μετατρέψετε DOCX σε PDF σε Java – οδηγός εξαγωγής σχήματος

Αν αναρωτιέστε **πώς να μετατρέψετε DOCX σε PDF σε Java** ενώ διατηρείτε τα αιωρούμενα εικόνες ή πλαίσια κειμένου, βρίσκεστε στο σωστό μέρος. Σε πολλά έργα—σκεφτείτε αυτόματους δημιουργούς αναφορών ή δίκτυα επεξεργασίας παρτίδας—η διατήρηση της ακριβούς διάταξης ενός εγγράφου Word είναι αδιαπραγμάτευτη.

Παρακάτω θα δείτε ακριβώς **πώς να εξάγετε σχήματα** όπως θέλετε, συν ένα σύνολο συμβουλών που σας σώζουν από κοινά προβλήματα. Χωρίς εξωτερικές υπηρεσίες, χωρίς οδηγό UI—απλώς καθαρός κώδικας Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

## Σύντομες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται τη μετατροπή;** Aspose.Words for Java.
- **Μπορώ να μετατρέψω DOCX σε PDF παρτίδα;** Ναι—τυλίξτε την ίδια λογική σε έναν βρόχο πάνω σε έναν φάκελο.
- **Μένουν τα αιωρούμενα σχήματα στη θέση τους;** Ορίστε `setExportFloatingShapesAsInlineTag(true)` για να τα εξάγετε ως ετικέτες inline.
- **Απαιτείται άδεια;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.

## Πώς να μετατρέψετε DOCX σε PDF σε Java;

Φορτώστε το πηγαίο `.docx` με `new Document("input.docx")` και καλέστε `doc.save("output.pdf", pdfOptions)`—η Aspose.Words διαχειρίζεται αυτόματα γραμματοσειρές, εικόνες, πίνακες και σύνθετες διατάξεις. Με τη ρύθμιση του `PdfSaveOptions` μπορείτε να ελέγξετε αν τα αιωρούμενα σχήματα θα γίνουν ετικέτες inline ή θα παραμείνουν στοιχεία σε επίπεδο block, κάτι που είναι ουσιώδες για την προσβασιμότητα και τη σωστή σειρά ανάγνωσης.

Αυτό το μοτίβο δύο βημάτων λειτουργεί για μεμονωμένα αρχεία και επεκτείνεται σε **batch μετατροπή DOCX σε PDF** επαναλαμβάνοντας πάνω σε έναν φάκελο εγγράφων.

## Τι θα μάθετε
* Φορτώστε ένα αρχείο `.docx` από το δίσκο.  
* Ρυθμίστε το `PdfSaveOptions` ώστε τα αιωρούμενα σχήματα να εξάγονται ως ετικέτες inline.  
* Γράψτε το παραγόμενο PDF σε έναν φάκελο της επιλογής σας.  
* Κατανοήστε γιατί η σημαία `setExportFloatingShapesAsInlineTag` είναι σημαντική και πότε μπορεί να την αλλάξετε.  

## Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 or later) | Παρέχει τις κλάσεις `Document` και `PdfSaveOptions` που χρησιμοποιούνται στο παράδειγμα. |
| **JDK 8+** | Η βιβλιοθήκη είναι μεταγλωττισμένη για Java 8 και νεότερες εκδόσεις· παλαιότερα περιβάλλοντα θα ρίξουν `UnsupportedClassVersionError`. |
| **Αρχείο DOCX** με τουλάχιστον ένα αιωρούμενο σχήμα (εικόνα, πλαίσιο κειμένου, WordArt) | Για να δείτε το αποτέλεσμα της επιλογής εξαγωγής σχήματος, χρειάζεστε ένα έγγραφο που περιέχει πραγματικά αιωρούμενα αντικείμενα. |

Αν έχετε ήδη αυτά τα στοιχεία, τέλεια—ας ξεκινήσουμε.

## Βήμα 1 – Φόρτωση του πηγαίου εγγράφου  

Η κλάση `Document` είναι το κορυφαίο αντικείμενο της Aspose.Words που αντιπροσωπεύει ένα μόνο αρχείο Word στη μνήμη. Η δημιουργία της διαβάζει το αρχείο, αναλύει το πακέτο OpenXML και δημιουργεί ένα μοντέλο αντικειμένων που μπορείτε να χειριστείτε.

Αρχικά δημιουργούμε μια παρουσία της `Document` που δείχνει στο `.docx` που θέλετε να μετατρέψετε.  

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro tip:** Αν επεξεργάζεστε πολλά αρχεία σε βρόχο, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` μόνο αφού καλέσετε `doc.close()` (ή αφήστε τον garbage collector να το διαχειριστεί). Αυτό αποτρέπει διαρροές χειριστών αρχείων στα Windows.

## Βήμα 2 – Ρύθμιση επιλογών αποθήκευσης PDF για εξαγωγή σχημάτων  

`PdfSaveOptions` είναι το αντικείμενο διαμόρφωσης που καθορίζει τη συμπεριφορά της μετατροπής. Η ρύθμιση `setExportFloatingShapesAsInlineTag(true)` αναγκάζει κάθε αιωρούμενο σχήμα να αντιμετωπίζεται ως στοιχείο *inline* στη δομή ετικετών του PDF, βελτιώνοντας την προσβασιμότητα και τη σειρά ανάγνωσης.

Η κλάση `PdfSaveOptions` ελέγχει τη διάταξη, την ενσωμάτωση γραμματοσειρών, τα επίπεδα συμμόρφωσης και πολλές ρυθμίσεις απόδοσης.  

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**Πότε θα το θέσετε σε `false`;**  
Αν το PDF προορίζεται μόνο για εκτύπωση και θέλετε τα σχήματα να διατηρήσουν την αρχική τους θέση χωρίς να επηρεάσουν τη λογική σειρά ανάγνωσης, μπορεί να προτιμήσετε ετικετοθέτηση σε επίπεδο block. Η προεπιλογή είναι `false`, γι' αυτό ενεργοποιούμε ρητά τη συμπεριφορά inline για αυτό το tutorial.

## Βήμα 3 – Αποθήκευση του εγγράφου ως PDF  

Η μέθοδος `save` γράφει το επεξεργασμένο έγγραφο στο δίσκο χρησιμοποιώντας τις επιλογές που δώσατε. Διαχειρίζεται τη διάταξη, την ενσωμάτωση γραμματοσειρών και τη δημιουργία ετικετών στο παρασκήνιο.

Η μέθοδος `save` στην κλάση `Document` γράφει το αρχείο PDF στην προορισμένη θέση χρησιμοποιώντας τις ρυθμισμένες `PdfSaveOptions`.  

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

Μετά το τέλος της κλήσης, θα βρείτε το `shapes.pdf` στον καθορισμένο φάκελο. Ανοίξτε το στο Adobe Acrobat ή σε οποιονδήποτε προβολέα PDF που εμφανίζει ετικέτες (συνήθως κάτω από **File → Properties → Tags**) και θα δείτε ότι το αιωρούμενο σχήμα εμφανίζεται ως ετικέτα inline.

## Γιατί αυτή η προσέγγιση είναι σημαντική

Η Aspose.Words for Java υποστηρίζει **πάνω από 50 μορφές εισόδου και εξόδου** και μπορεί να επεξεργαστεί ένα έγγραφο 500 σελίδων σε λιγότερο από **5 δευτερόλεπτα** σε έναν τυπικό διακομιστή, χωρίς να απαιτείται Microsoft Word. Εξάγοντας τα αιωρούμενα σχήματα ως ετικέτες inline, τηρείτε πρότυπα προσβασιμότητας όπως το PDF/UA, και αποφεύγετε την παραμόρφωση διάταξης όταν το PDF προβάλλεται σε διαφορετικές συσκευές.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα, εδώ είναι μια αυτόνομη κλάση Java που μπορείτε να μεταγλωττίσετε και να εκτελέσετε. Βεβαιωθείτε ότι το JAR της Aspose.Words βρίσκεται στο classpath σας.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
- Το αρχείο PDF περιέχει το ίδιο κειμενικό περιεχόμενο με το αρχικό DOCX.  
- Όλες οι αιωρούμενες εικόνες ή πλαίσια κειμένου είναι τώρα ετικετοποιημένα *inline*, πράγμα που σημαίνει ότι εμφανίζονται στη σειρά ανάγνωσης αντί ως ξεχωριστά blocks.  
- Αν ανοίξετε το πάνελ **Tags** του PDF, θα δείτε ένα στοιχείο `<Figure>` ενσωματωμένο μέσα σε ένα `<Paragraph>`—ακριβώς αυτό που εγγυάται το `setExportFloatingShapesAsInlineTag(true)`.

## Συχνές ερωτήσεις & ειδικές περιπτώσεις  

**Ε: Λειτουργεί αυτό με αρχεία DOCX προστατευμένα με κωδικό;**  
Ναι—φορτώστε το έγγραφο με `LoadOptions` που περιλαμβάνει τον κωδικό, και στη συνέχεια προχωρήστε με την ίδια λογική αποθήκευσης.  

**Ε: Τι γίνεται με εικόνες SVG ή EMF μέσα στο αρχείο Word;**  
Η Aspose.Words μετατρέπει τα διανυσματικά γραφικά σε raster εξ ορισμού· για να τα διατηρήσετε ως διανύσματα, μπορείτε να ενεργοποιήσετε `pdfOptions.setVectorRasterizationMode(VectorRasterizationMode.VectorOnly)`.  

**Ε: Πώς διατηρώ τους υπερσυνδέσμους κατά τη μετατροπή;**  
Οι σύνδεσμοι διατηρούνται αυτόματα όταν χρησιμοποιείτε `PdfSaveOptions`. Αποφύγετε την απενεργοποίηση των ετικετών, καθώς αυτό μπορεί να αφαιρέσει τη λογική δομή των συνδέσμων.  

**Ε: Μπορώ να επεξεργαστώ παρτίδα έναν φάκελο αρχείων DOCX;**  
Απόλυτα. Επαναλάβετε πάνω σε `Files.list(Paths.get("YOUR_DIRECTORY"))`, εφαρμόστε την ίδια ακολουθία φόρτωσης‑ρύθμισης‑αποθήκευσης σε κάθε αρχείο, και διαχειριστείτε τις εξαιρέσεις ανά αρχείο ώστε ένα κακό έγγραφο να μην σταματήσει ολόκληρη τη διαδικασία.  

**Ε: Πώς μπορώ να βελτιώσω την απόδοση για πολύ μεγάλα έγγραφα;**  
Ενεργοποιήστε `pdfOptions.setMemoryOptimization(true)` και σκεφτείτε τη ροή εξόδου (streaming) για να αποφύγετε τη φόρτωση ολόκληρου του PDF στη μνήμη.  

## Συμβουλές από το πεδίο  

* **Προσοχή στα ελλιπή γραμματοσειρές.** Αν το πηγαίο DOCX χρησιμοποιεί προσαρμοσμένη γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή, το PDF θα αντικαταστήσει με εφεδρική, ενδεχομένως διαταράσσοντας τη διάταξη. Χρησιμοποιήστε `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` για να εξαναγκάσετε την ενσωμάτωση.  
* **Δοκιμή προσβασιμότητας.** Μετά τη μετατροπή, εκτελέστε το **Accessibility Checker** του Acrobat. Η ετικετοθέτηση inline συνήθως βελτιώνει το σκορ, αλλά ίσως χρειαστεί να προσθέσετε εναλλακτικό κείμενο στις εικόνες χειροκίνητα.  
* **Συμβουλή απόδοσης:** Για μεγάλα έγγραφα (100+ σελίδες), ενεργοποιήστε `pdfOptions.setMemoryOptimization(true)` για να μειώσετε τη χρήση heap.  

## Οπτική επιβεβαίωση  

Παρακάτω είναι ένα γρήγορο στιγμιότυπο του PDF ανοιχτό στο Adobe Acrobat, που δείχνει το σχήμα με ετικέτα inline επισημασμένο στο πλαίσιο **Tags**.

![Παράδειγμα εξόδου μετατροπής DOCX σε PDF](image.png)

[Παράδειγμα εξόδου μετατροπής DOCX σε PDF](image.png)

*Alt text: παράδειγμα εξόδου μετατροπής docx σε pdf που δείχνει ετικέτες σχήματος inline.*

## Συμπεράσματα  

Τώρα γνωρίζετε **πώς να μετατρέψετε DOCX σε PDF σε Java** ελέγχοντας τον τρόπο εξαγωγής των αιωρούμενων αντικειμένων. Με την εναλλαγή του `setExportFloatingShapesAsInlineTag`, αποφασίζετε αν τα σχήματα θα γίνουν μέρος της σειράς ανάγνωσης ή θα παραμείνουν ως ανεξάρτητα blocks—σημαντικό τόσο για την προσβασιμότητα όσο και για την οπτική πιστότητα.  

Από εδώ μπορείτε:

* **Αποθήκευση Word ως PDF** μαζικά για αρχειοθέτηση.  
* Πειραματιστείτε με άλλες `PdfSaveOptions` όπως `setCompliance(PdfCompliance.PDF_A_1B)` για μακροπρόθεσμη διατήρηση.  
* Εμβαθύνετε στο **πώς να εξάγετε σχήματα** εξερευνώντας την πλήρη τεκμηρίωση της Aspose.Words ή δοκιμάζοντας τη σημαία `setExportDocumentStructure(true)` για πιο πλούσιες δομές ετικετών.

Δοκιμάστε το, προσαρμόστε τις επιλογές, και αφήστε τα PDFs σας να φαίνονται ακριβώς όπως τα χρειάζεστε. Καλό προγραμματισμό!

---

**Τελευταία ενημέρωση:** 2026-10-07  
**Δοκιμή με:** Aspose.Words for Java 23.12  
**Συγγραφέας:** Aspose  

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

```java
pdfOptions.setRasterizeTransformedElements(false);
```

## Σχετικά Μαθήματα

- [Οδηγός βήμα προς βήμα μετατροπής Docx σε Pdf σε Java](/words/java/document-converting/convert-docx-to-pdf-in-java-step-by-step-guide/)
- [Οδηγός πλήρους αποθήκευσης Docx ως Pdf με Java βήμα προς βήμα](/words/java/document-conversion-and-export/save-docx-as-pdf-with-java-complete-step-by-step-guide/)
- [Μετατροπή DOCX σε PDF σε Java με Aspose.Words – Χρήση Μετατροπής Εγγράφου](/words/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}