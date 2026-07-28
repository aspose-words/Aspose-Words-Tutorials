---
category: general
date: 2026-01-11
description: Το εκπαιδευτικό σεμινάριο Aspose Word σε PDF δείχνει πώς να μετατρέψετε
  ένα docx σε pdf σε Java χρησιμοποιώντας το Aspose.Words, με επιλογές για εξαγωγή
  των αιωρούμενων σχημάτων ως ενσωματωμένες ετικέτες.
draft: false
keywords:
- aspose word to pdf
- convert docx to pdf
- convert word document pdf
- how save docx pdf
- java convert docx pdf
language: el
og_description: Μάθετε πώς να μετατρέψετε το Aspose Word σε PDF σε Java. Αυτός ο οδηγός
  σας καθοδηγεί στη μετατροπή docx σε pdf, στη διαχείριση των αιωρούμενων σχημάτων
  και στην αποθήκευση του αποτελέσματος.
og_title: aspose word to pdf – Μετατροπή DOCX σε PDF σε Java
tags:
- Aspose.Words
- Java
- PDF conversion
title: aspose word to pdf – Μετατροπή DOCX σε PDF σε Java
url: /el/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose word to pdf – Μετατροπή DOCX σε PDF με Java

Έχετε αναρωτηθεί ποτέ πώς να **aspose word to pdf** χωρίς να παλεύετε με βιβλιοθήκες PDF χαμηλού επιπέδου; Δεν είστε μόνοι. Πολλοί προγραμματιστές Java χρειάζονται να **convert docx to pdf** γρήγορα, ειδικά όταν εργάζονται με έγγραφα που περιέχουν αιωρούμενα σχήματα ή πολύπλοκες διατάξεις.  

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα ένα πλήρες, έτοιμο προς εκτέλεση παράδειγμα που δείχνει ακριβώς πώς να **convert word document pdf** χρησιμοποιώντας το Aspose.Words for Java, εξηγώντας επίσης *γιατί* κάθε ρύθμιση είναι σημαντική. Στο τέλος θα ξέρετε πώς να **how save docx pdf** αρχεία, να ρυθμίσετε τις επιλογές για αιωρούμενα αντικείμενα και να αποφύγετε κοινά προβλήματα.

> **Pro tip:** Το Aspose.Words λειτουργεί τόσο με .NET όσο και με Java, αλλά το Java API αντικατοπτρίζει το .NET σχεδόν 1:1, έτσι ο κώδικας που γράφετε εδώ μπορεί να μεταφερθεί αργότερα με ελάχιστες αλλαγές.

## Προαπαιτούμενα

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο και ορισμένο `JAVA_HOME`.
- **Maven** ή **Gradle** για διαχείριση εξαρτήσεων.
- Μια άδεια **Aspose.Words for Java** (η δωρεάν δοκιμή λειτουργεί για δοκιμές, αλλά προσθέτει υδατογράφημα).
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον ένα αιωρούμενο σχήμα (εικόνα, πλαίσιο κειμένου κ.λπ.) ώστε να δείτε το αποτέλεσμα της επιλογής `ExportFloatingShapesAsInlineTag`.

Αν κάτι από αυτά σας φαίνεται άγνωστο, μην πανικοβληθείτε—μπορείτε να αποκτήσετε μια δοκιμαστική άδεια από τον ιστότοπο της Aspose, και το Maven θα κατεβάσει τη βιβλιοθήκη αυτόματα.

## Βήμα 1: Ρύθμιση του Έργου και Προσθήκη του Aspose.Words

Πρώτα, δημιουργήστε ένα νέο έργο Maven (ή χρησιμοποιήστε το αγαπημένο σας εργαλείο κατασκευής). Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` σας:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- check for the latest version -->
    </dependency>
</dependencies>
```

> **Why this matters:** Η δήλωση της εξάρτησης εξασφαλίζει ότι θα ληφθούν τα σωστά JARs, και ο αριθμός έκδοσης εγγυάται τη συμβατότητα με τις τελευταίες δυνατότητες PDF.

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Βήμα 2: Φόρτωση του Αρχείου DOCX σας

Τώρα που η βιβλιοθήκη βρίσκεται στο classpath, μπορούμε να φορτώσουμε ένα αρχείο DOCX. Η κλάση `Document` είναι το σημείο εισόδου για κάθε λειτουργία.

```java
import com.aspose.words.*;

public class PdfFloatingShapeTag {
    public static void main(String[] args) throws Exception {
        // Step 2‑1: Point to the source DOCX containing floating shapes
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document document = new Document(inputPath);
```

> **Explanation:** Ο κατασκευαστής διαβάζει το αρχείο στη μνήμη, αναλύοντας όλες τις παραγράφους, πίνακες, εικόνες και ναι—αιωρούμενα σχήματα. Αν το αρχείο λείπει, το Aspose ρίχνει ένα σαφές `FileNotFoundException`, το οποίο μπορείτε να πιάσετε για πιο φιλικό UI.

## Βήμα 3: Διαμόρφωση Επιλογών Αποθήκευσης PDF

Από προεπιλογή, το Aspose.Words θα αποδώσει τα αιωρούμενα σχήματα όπως εμφανίζονται στην αρχική διάταξη. Μερικές φορές χρειάζεται αυτά τα σχήματα να μετατραπούν σε κανονικές ενσωματωμένες ετικέτες `<span>`—ιδιαίτερα όταν το σύστημα downstream καταλαβαίνει μόνο απλό markup τύπου HTML. Εκεί έρχεται στο προσκήνιο η μέθοδος `PdfSaveOptions.setExportFloatingShapesAsInlineTag(true)`.

```java
        // Step 3‑1: Create PDF save options
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();

        // Step 3‑2: Export floating shapes as inline <span> tags
        pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);

        // Optional: tweak image quality (useful for large docs)
        pdfSaveOptions.setJpegQuality(90);
```

> **Why enable this option?** Κατά τη μετατροπή για προεπισκόπηση στο web ή για pipelines OCR, οι ενσωματωμένες ετικέτες απλοποιούν την επεξεργασία downstream. Χωρίς αυτήν, το PDF θα ενσωματώνει το σχήμα ως ξεχωριστό αντικείμενο, κάτι που μπορεί να διακόψει ορισμένους αναλυτές.

## Βήμα 4: Αποθήκευση του Εγγράφου ως PDF

Με τις επιλογές έτοιμες, το τελικό βήμα είναι μια εντολή μίας γραμμής που γράφει το PDF στο δίσκο.

```java
        // Step 4‑1: Define the output path
        String outputPath = "YOUR_DIRECTORY/output.pdf";

        // Step 4‑2: Perform the conversion
        document.save(outputPath, pdfSaveOptions);

        System.out.println("Conversion complete! PDF saved to: " + outputPath);
    }
}
```

Η εκτέλεση αυτής της κλάσης θα διαβάσει το `input.docx`, θα εφαρμόσει τη μετατροπή των αιωρούμενων σχημάτων και θα παραγάγει το `output.pdf`. Ανοίξτε το PDF—θα πρέπει να δείτε ότι οποιαδήποτε προηγούμενη αιωρούμενη εικόνα τώρα συμπεριφέρεται ως ενσωματωμένο στοιχείο (μπορείτε να το επαληθεύσετε επιλέγοντας το κείμενο γύρω του).

### Πλήρης Λίστα Πηγαίου Κώδικα

Για ευκολία, εδώ είναι ολόκληρη η κλάση σε ένα μπλοκ:

```java
import com.aspose.words.*;

public class PdfFloatingShapeTag {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX file containing floating shapes
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Create PDF save options and configure floating shapes to be exported as inline <span> tags
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
        pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);
        pdfSaveOptions.setJpegQuality(90); // optional quality tweak

        // Save the document as PDF using the configured options
        document.save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);

        System.out.println("Conversion complete! PDF saved to: YOUR_DIRECTORY/output.pdf");
    }
}
```

## Βήμα 5: Επαλήθευση του Αποτελέσματος (Τι να Αναζητήσετε)

Μετά το τέλος του προγράμματος:

1. **Ανοίξτε το `output.pdf`** σε οποιοδήποτε πρόγραμμα προβολής PDF. Τα αιωρούμενα σχήματα θα πρέπει τώρα να εμφανίζονται ενσωματωμένα με το γύρω κείμενο.
2. **Ελέγξτε για ελλιπείς γραμματοσειρές** – το Aspose.Words προσπαθεί να ενσωματώσει τις γραμματοσειρές αυτόματα, αλλά αν μια γραμματοσειρά δεν είναι αδειοδοτημένη, μπορεί να δείτε μια προειδοποίηση αντικατάστασης.
3. **Εξετάστε το μέγεθος του αρχείου** – η κλήση `setJpegQuality` μπορεί να μειώσει δραστικά το μέγεθος για έγγραφα με πολλές εικόνες.

Αν κάτι φαίνεται λανθασμένο, εξετάστε τις παρακάτω προσαρμογές:

| Πρόβλημα | Διόρθωση |
|----------|----------|
| Missing images | Ensure `input.docx` references images with absolute or correctly resolved relative paths. |
| Garbled characters | Verify the source DOCX uses Unicode fonts; set `PdfSaveOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` if needed. |
| Watermark from trial | Apply a valid license: `License license = new License(); license.setLicense("Aspose.Words.lic");` |

## Κοινές Παραλλαγές & Ακραίες Περιπτώσεις

### Μετατροπή Πολλαπλών Αρχείων σε Παρτίδα

Αν χρειάζεται να **convert docx to pdf** για ολόκληρο φάκελο, τυλίξτε τη λογική σε ένα βρόχο:

```java
File folder = new File("YOUR_DIRECTORY");
for (File file : folder.listFiles((dir, name) -> name.toLowerCase().endsWith(".docx"))) {
    Document doc = new Document(file.getAbsolutePath());
    String pdfName = file.getName().replaceAll("(?i)\\.docx$", ".pdf");
    doc.save(new File(folder, pdfName).getAbsolutePath(), pdfSaveOptions);
}
```

### Διαχείριση Αρχείων DOCX με Κωδικό Πρόσβασης

Το Aspose.Words μπορεί να ανοίξει κρυπτογραφημένα αρχεία:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document protectedDoc = new Document("protected.docx", loadOptions);
```

### Μετατροπή Ροής (Χωρίς Εγγραφή σε Δίσκο)

Για υπηρεσίες web, ίσως θέλετε να **how save docx pdf** απευθείας σε ροή:

```java
ByteArrayOutputStream pdfStream = new ByteArrayOutputStream();
document.save(pdfStream, pdfSaveOptions);
byte[] pdfBytes = pdfStream.toByteArray();
// send pdfBytes as HTTP response
```

## Οπτικό Αποτέλεσμα

Παρακάτω είναι ένα στιγμιότυπο του παραγόμενου PDF (αιωρούμενο σχήμα αποδομένο ως ενσωματωμένο κείμενο).  
![aspose word to pdf output example](https://example.com/images/aspose-word-to-pdf-output.png)

*Το alt κείμενο της εικόνας περιέχει τη βασική λέξη-κλειδί, ικανοποιώντας τις απαιτήσεις SEO.*

## Σύνοψη & Επόμενα Βήματα

Καλύψαμε μια **complete aspose word to pdf** ροή εργασίας:

- Ρύθμιση ενός έργου Java με Aspose.Words.
- Φόρτωση ενός DOCX που περιέχει αιωρούμενα σχήματα.
- Διαμόρφωση του `PdfSaveOptions` ώστε να εξάγει αυτά τα σχήματα ως ενσωματωμένες ετικέτες `<span>`.
- Αποθήκευση του αποτελέσματος ως PDF και επαλήθευση του εξόδου.

Τώρα μπορείτε να **convert docx to pdf** μαζικά, να διαχειριστείτε κρυπτογραφημένα αρχεία ή να ρέξετε το PDF απευθείας σε έναν πελάτη.  

**Τι ακολουθεί;** Μπορείτε να εξερευνήσετε:

- **Προσθήκη κεφαλίδων/υποσέλιδων** πριν τη μετατροπή (`DocumentBuilder`).
- **Ενσωμάτωση προσαρμοσμένων γραμματοσειρών** για πολυγλωσσικά PDF.
- **Χρήση Aspose.PDF** για περαιτέρω επεξεργασία του παραγόμενου PDF (προσθήκη σελιδοδεικτών, ψηφιακών υπογραφών κ.λπ.).

Μη διστάσετε να πειραματιστείτε—αλλάξτε το `setExportFloatingShapesAsInlineTag(false)` για να δείτε τη προεπιλεγμένη συμπεριφορά, ή προσαρμόστε τις ρυθμίσεις συμπίεσης εικόνας για ελαφρύτερα αρχεία. Η βιβλιοθήκη είναι αρκετά ευέλικτη για σχεδόν κάθε σενάριο επεξεργασίας εγγράφων.

---

*Καλό προγραμματισμό! Αν αντιμετωπίσετε προβλήματα, αφήστε ένα σχόλιο παρακάτω ή ελέγξτε την επίσημη τεκμηρίωση Aspose.Words for Java για πιο λεπτομερείς πληροφορίες.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}