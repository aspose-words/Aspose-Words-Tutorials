---
category: general
date: 2026-03-01
description: Αποθηκεύστε το Word ως PDF γρήγορα χρησιμοποιώντας το Aspose.Words για
  Java. Μάθετε πώς να μετατρέψετε docx σε pdf και πώς το Aspose μετατρέπει docx σε
  pdf ενώ διαχειρίζεται αιωρούμενα σχήματα.
draft: false
keywords:
- save word as pdf
- convert docx to pdf
- aspose convert docx pdf
- aspose words pdf options
- floating shapes pdf
language: el
og_description: Αποθηκεύστε το Word ως PDF χρησιμοποιώντας το Aspose.Words για Java.
  Αυτός ο οδηγός δείχνει πώς να μετατρέψετε docx σε PDF και το Aspose μετατρέπει docx
  σε PDF με πλήρη κώδικα.
og_title: Αποθήκευση Word ως PDF με το Aspose.Words – Πλήρης οδηγός Java
tags:
- Aspose.Words
- Java
- PDF conversion
title: Αποθήκευση Word ως PDF με το Aspose.Words – Οδηγός Java βήμα‑βήμα
url: /el/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Word ως PDF με Aspose.Words – Πλήρης Java Tutorial

Έχετε ποτέ χρειαστεί να **save word as pdf** αλλά δεν ήσασταν σίγουροι ποια κλήση API θα διατηρήσει το σχεδιασμό σας ανέπαφο; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν το DOCX τους περιέχει αιωρούμενες εικόνες ή πλαίσια κειμένου, και η προεπιλεγμένη μετατροπή είτε αφαιρεί αυτά τα σχήματα είτε τα τοποθετεί λανθασμένα.  

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα μια συγκεκριμένη, ολοκληρωμένη λύση που όχι μόνο *convert docx to pdf* αλλά σας επιτρέπει επίσης να ελέγχετε πώς εξάγονται τα αιωρούμενα σχήματα—χρησιμοποιώντας την επιλογή `ExportFloatingShapesAsInlineTag` από το Aspose.Words. Στο τέλος θα έχετε ένα έτοιμο για εκτέλεση πρόγραμμα Java που **aspose convert docx pdf** αξιόπιστα, ανεξάρτητα από το πόσες εικόνες έχετε ενσωματώσει στο αρχείο Word.

## Τι Θα Χρειαστεί

- **Java Development Kit (JDK) 8+** – οποιαδήποτε πρόσφατη έκδοση λειτουργεί.
- **Aspose.Words for Java** βιβλιοθήκη (το Maven artifact `com.aspose:aspose-words`).  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version> <!-- check for the latest version -->
  </dependency>
  ```
- Ένα αρχείο DOCX (`input.docx`) που περιέχει τουλάχιστον ένα αιωρούμενο σχήμα (εικόνα, πλαίσιο κειμένου ή διάγραμμα).  
- Ένα IDE ή έναν απλό επεξεργαστή κειμένου και τη γραμμή εντολών.

Αυτό είναι όλο—χωρίς πρόσθετες βιβλιοθήκες PDF, χωρίς προβλήματα αδειοδότησης (η δωρεάν δοκιμή λειτουργεί για αυτήν την επίδειξη), και χωρίς ασαφείς αρχεία ρυθμίσεων.

## Επισκόπηση της Διαδικασίας

1. **Load** το πηγαίο έγγραφο Word.  
2. **Configure** `PdfSaveOptions` για να αποφασίσετε πώς θα αντιμετωπίζονται τα αιωρούμενα σχήματα.  
3. **Save** το έγγραφο ως αρχείο PDF.  
4. **Verify** ότι το PDF περιέχει τα σχήματα στην αναμενόμενη διάταξη.

Παρακάτω θα αναλύσουμε κάθε βήμα, θα εξηγήσουμε *γιατί* είναι σημαντικό, και θα δείξουμε τον ακριβή κώδικα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε.

![Diagram illustrating the save word as pdf workflow](/images/save-word-as-pdf-workflow.png "save word as pdf workflow diagram")

### Βήμα 1: Φόρτωση του DOCX που Περιέχει Αιωρούμενα Σχήματα

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

/**
 * Loads a DOCX file into an Aspose.Words Document object.
 *
 * @param path Path to the input DOCX file.
 * @return Loaded Document instance.
 * @throws Exception if the file cannot be read.
 */
public static Document loadDocument(String path) throws Exception {
    // The Document constructor automatically detects the file format.
    Document doc = new Document(path);
    System.out.println("Document loaded. Page count: " + doc.getPageCount());
    return doc;
}
```

**Why this step?**  
Aspose.Words αφαιρεί την πολυπλοκότητα της μορφής DOCX βασισμένης σε ZIP, εκθέτοντας ένα υψηλού επιπέδου μοντέλο αντικειμένων (`Document`). Η φόρτωση του αρχείου είναι η πρώτη προϋπόθεση για οποιαδήποτε μετατροπή. Εάν το αρχείο λείπει ή είναι κατεστραμμένο, ο κατασκευαστής ρίχνει μια εξαίρεση—έτσι λαμβάνετε άμεση ανατροφοδότηση αντί για σιωπηλή αποτυχία αργότερα στη διαδικασία.

### Βήμα 2: Διαμόρφωση Επιλογών Αποθήκευσης PDF – Έλεγχος Αιωρούμενων Σχημάτων

```java
import com.aspose.words.PdfSaveOptions;
import com.aspose.words.ExportFloatingShapesAsInlineTag;

/**
 * Prepares PDF save options, especially how floating shapes are rendered.
 *
 * @return Configured PdfSaveOptions instance.
 */
public static PdfSaveOptions configurePdfOptions() {
    PdfSaveOptions options = new PdfSaveOptions();

    // The BLOCK setting wraps each floating shape in a <block> tag.
    // Alternatives: INLINE (default) or NONE.
    options.setExportFloatingShapesAsInlineTag(ExportFloatingShapesAsInlineTag.BLOCK);

    // Optional: set the PDF compliance level (e.g., PDF/A-1b for archiving)
    // options.setCompliance(PdfCompliance.PDF_A_1B);

    System.out.println("PDF options configured: ExportFloatingShapesAsInlineTag = BLOCK");
    return options;
}
```

**Why this matters:**  
Όταν *convert docx to pdf*, το Aspose.Words μπορεί είτε να ενσωματώσει τα αιωρούμενα σχήματα απευθείας εκεί που εμφανίζονται, είτε να τα τοποθετήσει σε ξεχωριστό στρώμα, είτε να τα αγνοήσει. Το enum `ExportFloatingShapesAsInlineTag` σας δίνει λεπτομερή έλεγχο. Χρησιμοποιώντας το `BLOCK` εξασφαλίζει ότι κάθε σχήμα τυλίγεται σε ετικέτα επιπέδου block, διατηρώντας τη θέση του σε σχέση με τις γύρω παραγράφους—ιδανικό για αναφορές όπου η πιστότητα της διάταξης είναι αδιαπραγμάτευτη.

### Βήμα 3: Αποθήκευση του Εγγράφου ως PDF Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

```java
/**
 * Saves the given Document as a PDF file with the supplied options.
 *
 * @param doc     The Aspose.Words Document to be saved.
 * @param outPath Destination path for the PDF file.
 * @param options PDF save options prepared earlier.
 * @throws Exception if the save operation fails.
 */
public static void saveAsPdf(Document doc, String outPath, PdfSaveOptions options) throws Exception {
    doc.save(outPath, options);
    System.out.println("PDF saved successfully to: " + outPath);
}
```

Συνδυάζοντας όλα τα παραπάνω:

```java
public class ExportFloatingShapesAsInlineTagExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source DOCX that contains floating shapes
        Document doc = loadDocument("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create PDF save options and specify how floating shapes should be represented
        PdfSaveOptions pdfOptions = configurePdfOptions();

        // 3️⃣ Save the document as PDF using the configured options
        saveAsPdf(doc, "YOUR_DIRECTORY/output.pdf", pdfOptions);

        // 4️⃣ Inform the user that the PDF has been created
        System.out.println("PDF saved with floating shapes tagged as BLOCK.");
    }
}
```

**Why this step is the crux of the tutorial:**  
Η κλήση `doc.save` είναι όπου συμβαίνει η μαγεία του **aspose convert docx pdf**. Με τη μεταβίβαση των `PdfSaveOptions` καθορίζετε ακριβώς πώς θα συμπεριφέρεται η μετατροπή. Εάν παραλείψετε τις επιλογές, το Aspose θα επιστρέψει στις προεπιλογές του, οι οποίες μπορεί να μην σεβαστούν τα αιωρούμενα σχήματα όπως χρειάζεστε.

### Βήμα 4: Επαλήθευση του Αποτελέσματος – Γρήγοροι Έλεγχοι που Μπορείτε να Κάνετε Προγραμματιστικά

```java
import java.io.File;

/**
 * Simple verification that the PDF file exists and is non‑empty.
 *
 * @param pdfPath Path to the generated PDF.
 */
public static void verifyPdf(String pdfPath) {
    File pdfFile = new File(pdfPath);
    if (pdfFile.exists() && pdfFile.length() > 0) {
        System.out.println("Verification passed: PDF file is present and has size " + pdfFile.length() + " bytes.");
    } else {
        System.err.println("Verification failed: PDF file is missing or empty.");
    }
}
```

Προσθέστε `verifyPdf("YOUR_DIRECTORY/output.pdf");` στο τέλος της `main` εάν θέλετε έναν άμεσο έλεγχο λογικής.

## Διαχείριση Συνηθισμένων Ακραίων Περιπτώσεων

| Κατάσταση | Τι να κάνετε | Γιατί |
|-----------|--------------|-------|
| **Αρχείο εισόδου δεν βρέθηκε** | Τυλίξτε το `loadDocument` σε try‑catch και εμφανίστε ένα φιλικό μήνυμα. | Αποτρέπει ένα ασαφές stack trace και καθοδηγεί τον χρήστη στη σωστή διαδρομή. |
| **Το έγγραφο δεν περιέχει αιωρούμενα σχήματα** | Μπορείτε ακόμη να χρησιμοποιήσετε τον ίδιο κώδικα· η ετικέτα `BLOCK` απλώς δεν θα εμφανιστεί. | Το API είναι ανεκτικό—δεν απαιτείται επιπλέον κώδικας. |
| **Χρειάζεστε ενσωματωμένα σχήματα αντί για block** | Αλλάξτε σε `ExportFloatingShapesAsInlineTag.INLINE`. | Σας παρέχει πιο στενή ροή όταν τα σχήματα πρέπει να συμπεριφέρονται όπως το κανονικό κείμενο. |
| **Μεγάλα έγγραφα (εκατοντάδες σελίδες)** | Αυξήστε τη μνήμη heap της JVM (`-Xmx2g`) ή χρησιμοποιήστε το `doc.save` με `MemoryUsageSetting`. | Αποτρέπει `OutOfMemoryError` κατά τη μετατροπή. |
| **Απαιτείται συμμόρφωση PDF/A** | Αποσχολιάστε τη γραμμή `options.setCompliance(PdfCompliance.PDF_A_1B);`. | Εγγυάται μακροπρόθεσμη συμβατότητα αρχειοθέτησης. |

## Επαγγελματικές Συμβουλές & Προβλήματα

- **Pro tip:** Εάν μετατρέπετε πολλά αρχεία σε batch, επαναχρησιμοποιήστε μια μόνο παρουσία `PdfSaveOptions`. Είναι ελαφρύ και εξοικονομεί το κόστος δημιουργίας αντικειμένων.
- **Watch out for:** Η δωρεάν δοκιμή του Aspose.Words προσθέτει υδατογράφημα στις πρώτες 20 σελίδες. Αγοράστε άδεια για χρήση σε παραγωγή.
- **Tip:** Χρησιμοποιήστε `doc.updatePageLayout()` πριν από την αποθήκευση εάν έχετε επεξεργαστεί το έγγραφο προγραμματιστικά· εξαναγκάζει την επανυπολογισμό της διάταξης.
- **Remember:** Το enum `ExportFloatingShapesAsInlineTag` έχει τρεις τιμές—`BLOCK`, `INLINE` και `NONE`. Επιλέξτε ανάλογα με το πώς οι PDF αναγνώστες ερμηνεύουν τις ετικέτες.

## Συμπέρασμα

Μόλις παρουσιάσαμε έναν πλήρη, έτοιμο για παραγωγή τρόπο για **save word as pdf** χρησιμοποιώντας το Aspose.Words για Java, καλύπτοντας τα πάντα από τη φόρτωση του DOCX μέχρι τη διαμόρφωση του χειρισμού των αιωρούμενων σχημάτων και τελικά την επαλήθευση του αποτελέσματος. Αυτό το παράδειγμα δείχνει επίσης πώς να **convert docx to pdf** ενώ σας παρέχει την ευελιξία να **aspose convert docx pdf** με προσαρμοσμένες επιλογές.

Μη διστάσετε να πειραματιστείτε: αντικαταστήστε το `BLOCK` με `INLINE`, ενεργοποιήστε τη συμμόρφωση PDF/A, ή επεξεργαστείτε σε batch έναν φάκελο αρχείων Word. Το ίδιο μοτίβο κλιμακώνεται άψογα.

Έχετε ερωτήσεις για άλλα χαρακτηριστικά του Aspose.Words—όπως η διατήρηση υπερσυνδέσμων ή η ενσωμάτωση γραμματοσειρών; Αφήστε ένα σχόλιο και θα εμβαθύνουμε μαζί. Καλός κώδικας!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}