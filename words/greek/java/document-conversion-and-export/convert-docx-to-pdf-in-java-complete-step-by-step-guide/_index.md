---
category: general
date: 2026-05-23
description: Μετατρέψτε το docx σε pdf με Java γρήγορα. Μάθετε πώς να αποθηκεύετε
  το Word ως pdf, να εξάγετε σωστά τα σχήματα και να χρησιμοποιείτε βιβλιοθήκες Java
  docx‑to‑pdf σε ένα ενιαίο σεμινάριο.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
- java docx to pdf
language: el
og_description: Μετατρέψτε το docx σε pdf χρησιμοποιώντας Java. Αυτός ο οδηγός δείχνει
  πώς να αποθηκεύσετε το Word ως pdf, να εξάγετε σχήματα ως στοιχεία μπλοκ και να
  διαχειριστείτε τις μετατροπές java docx σε pdf.
og_title: Μετατροπή docx σε pdf σε Java – Πλήρης Οδηγός Προγραμματισμού
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Convert docx to pdf with Java quickly. Learn how to save word as pdf,
    export shapes correctly, and use java docx to pdf libraries in a single tutorial.
  headline: Convert docx to pdf in Java – Complete Step‑by‑Step Guide
  type: TechArticle
tags:
- Java
- docx
- PDF
title: Μετατροπή docx σε pdf σε Java – Πλήρης Οδηγός Βήμα‑βήμα
url: /el/java/document-conversion-and-export/convert-docx-to-pdf-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή docx σε pdf σε Java – Πλήρης Οδηγός Βήμα‑βήμα

Έχετε αναρωτηθεί ποτέ πώς να **convert docx to pdf** χωρίς να πληρώσετε για μια ακριβή υπηρεσία τρίτου μέρους; Δεν είστε μόνοι. Πολλοί προγραμματιστές χρειάζονται να **save word as pdf** άμεσα—σκεφτείτε αυτόματους δημιουργούς αναφορών, μηχανές τιμολογίων ή απλούς προβολείς εγγράφων. Σε αυτό το tutorial θα περάσουμε από μια καθαρή, χωρίς περιττά στοιχεία προσέγγιση που όχι μόνο μετατρέπει αλλά και διασφαλίζει ότι τα αιωρούμενα σχήματα διατηρούν τη διάταξή τους.

Θα χρησιμοποιήσουμε τη βιβλιοθήκη Aspose.Words for Java, η οποία μας παρέχει λεπτομερή έλεγχο των επιλογών εξαγωγής PDF. Στο τέλος αυτού του οδηγού θα μπορείτε να τοποθετήσετε ένα αρχείο `.docx` στην εφαρμογή σας και να λάβετε ένα τέλεια αποδομένο PDF, πλήρες με σχήματα επιπέδου μπλοκ.

## Προαπαιτούμενα

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο και ορισμένο `JAVA_HOME`.
- Maven ή Gradle για διαχείριση εξαρτήσεων—το Maven χρησιμοποιείται στα παραδείγματα.
- Ένα έγκυρο άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για δοκιμές).
- Ένα εισερχόμενο έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα αιωρούμενο σχήμα (εικόνα, πλαίσιο κειμένου κ.λπ.).

Αν κάτι από αυτά σας φαίνεται άγνωστο, μην πανικοβληθείτε. Θα καλύψουμε σύντομα τη ρύθμιση Maven αργότερα, και τα υπόλοιπα είναι αρκετά τυπικά για οποιοδήποτε έργο Java.

## Βήμα 1: Ρύθμιση του Έργου και Προσθήκη Aspose.Words

Πρώτα απ' όλα: δημιουργήστε ένα νέο έργο Maven (ή ανοίξτε ένα υπάρχον) και προσθέστε την εξάρτηση Aspose.Words.

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>docx-to-pdf</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Αν χρησιμοποιείτε Gradle, το ισοδύναμο είναι `implementation 'com.aspose:aspose-words:23.12'`.  

Η προσθήκη της βιβλιοθήκης μας παρέχει τις κλάσεις `Document` και `PdfSaveOptions` που χρειάζονται για **convert docx to pdf** και τον έλεγχο της εξαγωγής σχήματος.

## Βήμα 2: Φόρτωση του Πηγαίου Εγγράφου

Τώρα που η εξάρτηση είναι στη θέση της, μπορούμε να φορτώσουμε ένα αρχείο Word. Αυτό είναι το σημείο όπου πολλά tutorials σταματούν, αλλά θα διατηρήσουμε τη ροή στενή.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class DocxToPdfConverter {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);
        // At this stage the document is fully parsed in memory.
    }
}
```

Παρατηρήστε πώς χρησιμοποιούμε απόλυτη ή σχετική διαδρομή—το Aspose.Words διαχειρίζεται και τα δύο. Αν το αρχείο δεν βρεθεί, ρίχνεται μια εξαίρεση, την οποία μπορείτε να πιάσετε για να παρουσιάσετε ένα φιλικό μήνυμα σφάλματος στον χρήστη.

## Βήμα 3: Διαμόρφωση Επιλογών Αποθήκευσης PDF – **How to Export Shapes** Σωστά

Η καρδιά αυτού του οδηγού βρίσκεται στο τμήμα **how to export shapes**. Από προεπιλογή, τα αιωρούμενα σχήματα (όπως εικόνες που είναι αγκυροβολημένα σε παραγράφους) μπορεί να εμφανιστούν ως ενσωματωμένα στοιχεία, κάτι που μπορεί να μετατοπίσει τη θέση τους. Για να διατηρήσουμε την αρχική διάταξη πρέπει να ορίσουμε την ιδιότητα `ExportFloatingShapesAsInlineTag` σε `BLOCK`.

```java
import com.aspose.words.PdfSaveOptions;

        // Step 2: Configure PDF save options to export floating shapes as block-level elements
        PdfSaveOptions pdfOpts = new PdfSaveOptions();
        pdfOpts.setExportFloatingShapesAsInlineTag(
            PdfSaveOptions.ExportFloatingShapesAsInlineTag.BLOCK);
        // This forces shapes to be treated as block elements, keeping their original placement.
```

Γιατί είναι σημαντικό; Φανταστείτε ένα φυλλάδιο μάρκετινγκ όπου μια εικόνα είναι αγκυροβολημένη στο δεξιό περιθώριο. Αν αυτή η εικόνα γίνει ενσωματωμένη, το κείμενο θα τυλίγεται αμήχανα, σπάζοντας το σχέδιο. Ορίζοντας την επιλογή σε `BLOCK` λέμε στον renderer PDF να κρατήσει το σχήμα στη δική του γραμμή, μιμούμενο τη διάταξη του Word.

## Βήμα 4: Αποθήκευση του Εγγράφου ως PDF – Το Τελικό Βήμα **Save Word as PDF**

Με το έγγραφο φορτωμένο και τις επιλογές ρυθμισμένες, απλώς καλούμε το `save`. Αυτή είναι η στιγμή όπου η λειτουργία **convert docx to pdf** πραγματοποιείται πραγματικά.

```java
        // Step 3: Save the document as PDF using the configured options
        String outputPath = "YOUR_DIRECTORY/Exported.pdf";
        doc.save(outputPath, pdfOpts);
        System.out.println("PDF created successfully at " + outputPath);
    }
}
```

Η εκτέλεση της μεθόδου `main` θα δημιουργήσει το `Exported.pdf` στον φάκελο προορισμού. Ανοίξτε το με οποιονδήποτε προβολέα PDF και θα δείτε ότι τα αιωρούμενα σχήματα διατηρούν την αρχική τους θέση σε μπλοκ.

## Αναμενόμενο Αποτέλεσμα

Όταν ανοίξετε το `Exported.pdf`, θα πρέπει να δείτε:

- Όλο το κείμενο από το `input.docx` αποδομένο πιστά.
- Εικόνες, πλαίσια κειμένου ή SmartArt που ήταν αιωρούμενα στο Word εμφανίζονται τώρα ως ξεχωριστά μπλοκ, όχι ενσωματωμένα μέσα σε παραγράφους.
- Αριθμοί σελίδων, κεφαλίδες και υποσέλιδα (αν υπάρχουν) διατηρούνται.

Αν το PDF φαίνεται πανομοιότυπο με το αρχικό αρχείο Word, έχετε καταφέρει με επιτυχία τη μετατροπή **java docx to pdf** με διαχείριση σχήματος.

## Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| Απώλεια σχημάτων | `ExportFloatingShapesAsInlineTag` παραμένει στην προεπιλογή (`INLINE`) και ο renderer αποφασίζει να τα αφαιρέσει. | Ορίστε την ιδιότητα σε `BLOCK` όπως φαίνεται στο Βήμα 3. |
| Το PDF είναι κενό | Λάθος διαδρομή αρχείου ή έλλειψη δικαιωμάτων ανάγνωσης στο εισερχόμενο `.docx`. | Επαληθεύστε το `inputPath` και βεβαιωθείτε ότι η διαδικασία Java έχει πρόσβαση ανάγνωσης. |
| Προειδοποίηση άδειας στην έξοδο | Χρήση της δοκιμαστικής έκδοσης χωρίς ορισμό άδειας. | Καλέστε `License license = new License(); license.setLicense("Aspose.Words.Java.lic");` πριν φορτώσετε το έγγραφο. |
| Οι γραμματοσειρές φαίνονται διαφορετικές | Το σύστημα όπου εκτελείται ο κώδικας δεν διαθέτει τις γραμματοσειρές που χρησιμοποιούνται στο αρχείο Word. | Εγκαταστήστε τις ελλιπείς γραμματοσειρές ή ενσωματώστε τις μέσω `PdfSaveOptions.setEmbedFullFonts(true)`. |

Η αντιμετώπιση αυτών των ειδικών περιπτώσεων κάνει τη λύση **convert docx to pdf** σας ανθεκτική για περιβάλλοντα παραγωγής.

## Πλήρες Παράδειγμα Εργασίας (Όλος ο Κώδικας σε Ένα Σημείο)

Παρακάτω βρίσκεται η πλήρης, έτοιμη‑για‑εκτέλεση κλάση. Αντιγράψτε‑επικολλήστε την στο IDE σας, προσαρμόστε τις διαδρομές και τρέξτε την.

```java
import com.aspose.words.Document;
import com.aspose.words.PdfSaveOptions;

/**
 * Demonstrates how to convert a DOCX file to PDF in Java while preserving
 * floating shapes as block‑level elements.
 */
public class DocxToPdfConverter {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // Configure PDF export options – how to export shapes correctly
            PdfSaveOptions pdfOpts = new PdfSaveOptions();
            pdfOpts.setExportFloatingShapesAsInlineTag(
                PdfSaveOptions.ExportFloatingShapesAsInlineTag.BLOCK);

            // Save as PDF – this is the actual save word as pdf step
            String outputPath = "YOUR_DIRECTORY/Exported.pdf";
            doc.save(outputPath, pdfOpts);

            System.out.println("Successfully converted docx to pdf: " + outputPath);
        } catch (Exception e) {
            System.err.println("Conversion failed: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

Εκτελέστε το πρόγραμμα και θα δείτε το μήνυμα στην κονσόλα που επιβεβαιώνει τη μετατροπή. Αυτό είναι—η αλυσίδα **java docx to pdf** σας είναι ενεργή.

## Περαιτέρω: Τι να Εξερευνήσετε Στη Σύντομη Μελλοντική

- **Batch conversion:** Επανάληψη σε έναν φάκελο `.docx` αρχείων και μετατροπή του καθενός.
- **Custom PDF settings:** Αλλαγή ποιότητας εικόνας, ενσωμάτωση γραμματοσειρών ή κρυπτογράφηση του PDF μέσω πρόσθετων ιδιοτήτων `PdfSaveOptions`.
- **Streaming conversion:** Χρήση `InputStream`/`OutputStream` για αποφυγή δημιουργίας ενδιάμεσων αρχείων—χρήσιμο για web services.
- **Alternative libraries:** Αν η άδεια Aspose δεν είναι επιλογή, δείτε το Apache POI + iText, αν και δεν διαθέτουν την ενσωματωμένη διαχείριση σχημάτων που δείξαμε.

Κάθε ένα από αυτά τα θέματα συνδέεται με τις βασικές έννοιες που καλύψαμε—**convert docx to pdf**, **save word as pdf**, και **how to export shapes**—οπότε η μετάβαση θα είναι ομαλή.

## Συμπέρασμα

Μόλις περάσαμε από έναν πλήρη, έτοιμο‑για‑παραγωγή τρόπο **convert docx to pdf** σε Java, αντιμετωπίζοντας το δύσκολο σενάριο **how to export shapes** και διασφαλίζοντας ότι το αποτέλεσμα ταιριάζει με την αρχική διάταξη του Word. Ακολουθώντας τα τέσσερα βήματα—ρύθμιση έργου, φόρτωση εγγράφου, διαμόρφωση εξαγωγής σχημάτων και τελική αποθήκευση—μπορείτε να ενσωματώσετε αυτή τη λογική σε οποιαδήποτε εφαρμογή Java που χρειάζεται να **save word as pdf** άμεσα.

Δοκιμάστε το, προσαρμόστε το `PdfSaveOptions` ώστε να ταιριάζει στις ανάγκες σας, και σύντομα θα μετατρέπετε δεκάδες έγγραφα ανά δευτερόλεπτο χωρίς καμία δυσκολία. Έχετε ερωτήσεις σχετικά με τις λεπτομέρειες του **java docx to pdf**; Αφήστε ένα σχόλιο παρακάτω, και καλό προγραμματισμό!

![Διάγραμμα που δείχνει τη ροή μετατροπής docx σε pdf: φόρτωση DOCX → ορισμός επιλογών PDF (εξαγωγή σχημάτων) → αποθήκευση ως PDF](convert-docx-to-pdf-flow.png "διάγραμμα ροής convert docx to pdf")

## Σχετικά Μαθήματα

- [How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)
- [aspose word to pdf – Convert DOCX to PDF in Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}