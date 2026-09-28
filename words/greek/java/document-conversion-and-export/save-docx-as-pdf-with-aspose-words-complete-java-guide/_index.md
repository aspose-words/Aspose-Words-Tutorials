---
category: general
date: 2026-02-10
description: Αποθηκεύστε το docx ως pdf γρήγορα χρησιμοποιώντας το Aspose.Words σε
  Java. Μάθετε πώς να μετατρέπετε το Word σε pdf, να ελέγχετε τις επιλογές αποθήκευσης
  pdf του Aspose και να διαχειρίζεστε τα αιωρούμενα σχήματα.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- save word as pdf
- java convert word pdf
- pdf save options aspose
language: el
og_description: Αποθηκεύστε το docx ως pdf χρησιμοποιώντας το Aspose.Words for Java.
  Αυτός ο οδηγός δείχνει πώς να μετατρέψετε το Word σε pdf, να προσαρμόσετε τις επιλογές
  αποθήκευσης pdf του Aspose και να εξάγετε τα αιωρούμενα σχήματα ως ενσωματωμένες
  ετικέτες.
og_title: Αποθήκευση docx ως pdf με το Aspose.Words – Εγχειρίδιο Java
tags:
- Aspose.Words
- Java
- PDF conversion
title: Αποθήκευση docx ως pdf με το Aspose.Words – Πλήρης οδηγός Java
url: /el/java/document-conversion-and-export/save-docx-as-pdf-with-aspose-words-complete-java-guide/
---

preserve markdown table formatting.

Now produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση docx ως pdf με Aspose.Words – Πλήρης Οδηγός Java

Έχετε χρειαστεί ποτέ να **αποθηκεύσετε docx ως pdf** αλλά δεν ήσασταν σίγουροι ποια βιβλιοθήκη θα σας προσφέρει λεπτομερή έλεγχο; Δεν είστε μόνοι. Στον κόσμο της Java, το Aspose.Words είναι το εργαλείο επιλογής για τη μετατροπή εγγράφων Word σε PDF, και ακόμη σας επιτρέπει να αποφασίσετε πώς θα αποδίδονται τα αιωρούμενα σχήματα.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα που όχι μόνο **convert word to pdf**, αλλά επίσης δείχνει πώς να χρησιμοποιήσετε **pdf save options aspose** για να εξάγετε τα αιωρούμενα σχήματα ως ενσωματωμένα `<span>` tags. Στο τέλος, θα έχετε ένα έτοιμο‑για‑εκτέλεση πρόγραμμα Java που αποθηκεύει ένα DOCX ως PDF ακριβώς όπως χρειάζεστε.

## Τι Θα Μάθετε

- Πώς να φορτώσετε ένα αρχείο DOCX με Aspose.Words for Java.  
- Πώς να διαμορφώσετε **pdf save options aspose** για να ελέγχετε την έξοδο των αιωρούμενων σχημάτων.  
- Πώς να **save word as pdf** χρησιμοποιώντας μια μόνο κλήση μεθόδου.  
- Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως ελλιπή αρχεία ή μη υποστηριζόμενοι τύποι σχημάτων.  

### Προαπαιτούμενα

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο και ρυθμισμένο.  
- Maven ή Gradle για τη διαχείριση εξαρτήσεων (θα δείξουμε Maven).  
- Ένα έγκυρο άδεια Aspose.Words for Java (ή τη δωρεάν λειτουργία αξιολόγησης).  
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον μία αιωρούμενη εικόνα ή πλαίσιο κειμένου.

> **Pro tip:** Αν έχετε περιορισμένο προϋπολογισμό, η έκδοση αξιολόγησης προσθέτει υδατογράφημα αλλά λειτουργεί τέλεια για εκπαιδευτικούς σκοπούς.

## Βήμα 1 – Προσθέστε το Aspose.Words στο Έργο σας

Πρώτα, προσθέστε τη βιβλιοθήκη στο αρχείο κατασκευής σας. Με το Maven είναι τόσο απλό όσο η προσθήκη αυτής της εξάρτησης:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Γιατί είναι σημαντικό:** Χωρίς τη σωστή έκδοση μπορεί να λείπει το API `setExportFloatingShapesAsInlineTag`, το οποίο εισήχθη στο Aspose.Words 23.5.

## Βήμα 2 – Φορτώστε το Πηγαίο DOCX

Τώρα θα δημιουργήσουμε ένα αντικείμενο `Document` που αντιπροσωπεύει το αρχείο Word που θέλετε να μετατρέψετε. Αυτό το βήμα είναι απλό, αλλά θα προσθέσουμε επίσης ένα μικρό δίχτυ ασφαλείας για να πιάσουμε το `FileNotFoundException`.

```java
import com.aspose.words.*;

import java.nio.file.*;

public class PdfFloatingShapeTagTutorial {

    public static void main(String[] args) {
        // Define paths – adjust to your environment
        Path inputPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Path outputPath = Paths.get("YOUR_DIRECTORY/output.pdf");

        // Verify the input file exists
        if (!Files.exists(inputPath)) {
            System.err.println("❌ Input file not found: " + inputPath);
            return;
        }

        try {
            // Load the DOCX into an Aspose.Words Document
            Document document = new Document(inputPath.toString());

            // Continue with PDF conversion...
            convertToPdf(document, outputPath);
        } catch (Exception e) {
            System.err.println("⚠️ Something went wrong while loading the document:");
            e.printStackTrace();
        }
    }
```

> **Εξήγηση:** Το `Document` αφαιρεί την πλήρη δομή του αρχείου Word, δίνοντάς μας πρόσβαση σε παραγράφους, πίνακες, εικόνες και ακόμη και αιωρούμενα σχήματα. Το μπλοκ `try‑catch` εξασφαλίζει ότι το πρόγραμμα αποτυγχάνει ήρεμα αντί να καταρρεύσει με ένα stack trace.

## Βήμα 3 – Διαμορφώστε τις Ρυθμίσεις Αποθήκευσης PDF

Το Aspose.Words περιλαμβάνει μια κλάση `PdfSaveOptions` που σας επιτρέπει να ρυθμίσετε λεπτομερώς την έξοδο PDF. Η σημαία που μας ενδιαφέρει είναι `setExportFloatingShapesAsInlineTag`. Ορίζοντάς την σε `true` εξαναγκάζει τα αιωρούμενα σχήματα (όπως πλαίσια κειμένου ή εικόνες τοποθετημένες «πριν από το κείμενο») να γίνουν ενσωματωμένα `<span>` tags στο εσωτερικό XML του PDF, κάτι που μπορεί να είναι κρίσιμο για επεξεργασία σε επόμενα στάδια.

```java
    private static void convertToPdf(Document document, Path outputPath) {
        // Create a PdfSaveOptions instance
        PdfSaveOptions pdfOptions = new PdfSaveOptions();

        // true → <span>, false → <div>
        pdfOptions.setExportFloatingShapesAsInlineTag(true);

        // Optional: you can also adjust image quality, compliance level, etc.
        pdfOptions.setCompliance(PdfCompliance.PDF_A_1_B);
        pdfOptions.setJpegQuality(90);

        try {
            // Save the document as PDF using the configured options
            document.save(outputPath.toString(), pdfOptions);
            System.out.println("✅ PDF saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("⚠️ Failed to save PDF:");
            e.printStackTrace();
        }
    }
}
```

### Γιατί να Χρησιμοποιήσετε `setExportFloatingShapesAsInlineTag(true)`;

- **Καθαρότερο markup:** Κάποιοι PDF parser προτιμούν `<span>` αντί για `<div>` για ενσωματωμένα στοιχεία.  
- **Καλύτερη προσβασιμότητα:** Τα ενσωματωμένα tags διατηρούν τη σειρά ανάγνωσης πιο προβλέψιμη.  
- **Συνεπής στυλ:** Όταν μετατρέψετε αργότερα το PDF σε HTML, το `<span>` συχνά αντιστοιχεί πιο άμεσα σε στυλ CSS.

Αν ποτέ χρειαστείτε την παλιά συμπεριφορά (αιωρούμενα σχήματα ως block‑level `<div>`), απλώς αλλάξτε τη Boolean τιμή σε `false`.

## Βήμα 4 – Εκτελέστε το Πρόγραμμα και Επαληθεύστε το Αποτέλεσμα

Μεταγλωττίστε και εκτελέστε την κλάση:

```bash
mvn compile exec:java -Dexec.mainClass=PdfFloatingShapeTagTutorial
```

Μετά από μια επιτυχημένη εκτέλεση θα πρέπει να δείτε:

```
✅ PDF saved successfully to YOUR_DIRECTORY/output.pdf
```

Ανοίξτε το `output.pdf` σε οποιονδήποτε προβολέα. Αν το αρχικό DOCX περιείχε μια αιωρούμενη εικόνα, ελέγξτε τη δομή του PDF (π.χ., χρησιμοποιώντας το παράθυρο “Tags” του Adobe Acrobat) – θα παρατηρήσετε ότι η εικόνα είναι τώρα τυλιγμένη σε ένα στοιχείο `<span>`.

### Περιπτώσεις Όρια που Πρέπει να Λάβετε Υπόψη

| Κατάσταση | Τι Μπορεί να Συμβεί | Προτεινόμενη Διόρθωση |
|-----------|-------------------|---------------|
| Το Input DOCX είναι προστατευμένο με κωδικό | `InvalidOperationException` | Χρησιμοποιήστε `LoadOptions` με τον κωδικό πριν δημιουργήσετε το `Document`. |
| Το έγγραφο περιέχει μη υποστηριζόμενους τύπους σχημάτων (π.χ., SmartArt) | Shapes may be rasterized or omitted | Ορίστε `PdfSaveOptions.setRenderSmartArtAsBitmap(true)` αν προτιμάτε εναλλακτική bitmap. |
| Η διαδρομή εξόδου δείχνει σε φάκελο μόνο για ανάγνωση | `IOException` on save | Βεβαιωθείτε ότι ο φάκελος έχει δικαιώματα εγγραφής ή επιλέξτε άλλη τοποθεσία. |

## Βήμα 5 – Προχωρημένες Ρυθμίσεις (Προαιρετικό)

Αν δημιουργείτε μια υπηρεσία που μετατρέπει πολλά αρχεία, ίσως θέλετε να:

1. **Επαναχρησιμοποίηση μιας μόνο `License` instance** για να αποφύγετε επιπτώσεις στην απόδοση.  
2. **Ροή εξόδου** απευθείας σε `ByteArrayOutputStream` για απαντήσεις HTTP.  
3. **Επεξεργασία σε παρτίδες** πολλαπλών αρχείων DOCX χρησιμοποιώντας βρόχο και σωστή διαχείριση σφαλμάτων.  

Ακολουθεί ένα γρήγορο απόσπασμα για ροή:

```java
ByteArrayOutputStream pdfStream = new ByteArrayOutputStream();
document.save(pdfStream, pdfOptions);
byte[] pdfBytes = pdfStream.toByteArray();
// Now you can write pdfBytes to an HTTP response, S3 bucket, etc.
```

## Συνοπτικό Παράδειγμα Πλήρους Λειτουργίας

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση αρχείο Java. Αντιγράψτε‑και‑επικολλήστε το στο IDE σας, προσαρμόστε τις διαδρομές, και είστε έτοιμοι.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class PdfFloatingShapeTagTutorial {

    public static void main(String[] args) {
        Path inputPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Path outputPath = Paths.get("YOUR_DIRECTORY/output.pdf");

        if (!Files.exists(inputPath)) {
            System.err.println("❌ Input file not found: " + inputPath);
            return;
        }

        try {
            Document document = new Document(inputPath.toString());
            convertToPdf(document, outputPath);
        } catch (Exception e) {
            System.err.println("⚠️ Error loading document:");
            e.printStackTrace();
        }
    }

    private static void convertToPdf(Document document, Path outputPath) {
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setExportFloatingShapesAsInlineTag(true); // <span> instead of <div>
        pdfOptions.setCompliance(PdfCompliance.PDF_A_1_B);
        pdfOptions.setJpegQuality(90);

        try {
            document.save(outputPath.toString(), pdfOptions);
            System.out.println("✅ PDF saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("⚠️ Failed to save PDF:");
            e.printStackTrace();
        }
    }
}
```

Τρέξτε το, και μόλις **saved docx as pdf** ενώ ελέγχετε το markup των αιωρούμενων σχημάτων.

---

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **save docx as pdf** χρησιμοποιώντας το Aspose.Words for Java, από τη ρύθμιση της εξάρτησης μέχρι τη ρύθμιση των **pdf save options aspose** για ενσωματωμένα `<span>` tags. Το σύντομο πρόγραμμα δείχνει ολόκληρη τη ροή — φόρτωση, διαμόρφωση και εξαγωγή — ώστε να το ενσωματώσετε σε μεγαλύτερες εφαρμογές, web services ή εργασίες batch.

Αν είστε περίεργοι για τα επόμενα βήματα, σκεφτείτε να εξερευνήσετε:

- **convert word to pdf** με προσαρμοσμένο μέγεθος σελίδας ή κρυπτογράφηση.  
- **save word as pdf** εν κινήσει σε ένα Spring Boot REST endpoint.  
- Χρησιμοποιώντας **java convert word pdf** σε συνδυασμό με OCR για εξαγωγή αναζητήσιμου κειμένου.  

Δοκιμάστε τον κώδικα, δοκιμάστε διαφορετικές ρυθμίσεις `PdfSaveOptions`, και αφήστε τη βιβλιοθήκη να κάνει το σκληρό έργο. Καλή προγραμματιστική, και εύχομαι τα PDFs σας να αποδίδουν πάντα ακριβώς όπως το επιθυμείτε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}