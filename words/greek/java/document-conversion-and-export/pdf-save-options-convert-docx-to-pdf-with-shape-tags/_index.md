---
category: general
date: 2026-04-04
description: Μάθετε πώς να χρησιμοποιείτε τις επιλογές αποθήκευσης PDF στη Java για
  να μετατρέψετε docx σε pdf και να εξάγετε σχήματα ως ενσωματωμένες ετικέτες. Οδηγός
  βήμα‑προς‑βήμα για την αποθήκευση του docx ως pdf.
draft: false
keywords:
- pdf save options
- convert docx to pdf
- how to export shapes
- save docx as pdf
- convert word to pdf
language: el
og_description: Ανακαλύψτε τις επιλογές αποθήκευσης PDF στη Java για τη μετατροπή
  docx σε pdf και την εξαγωγή σχημάτων ως ενσωματωμένες ετικέτες. Πλήρης οδηγός για
  την αποθήκευση docx ως pdf.
og_title: 'επιλογές αποθήκευσης pdf: Μετατροπή DOCX σε PDF με ετικέτες σχήματος'
tags:
- Aspose.Words
- Java
- PDF generation
title: 'επιλογές αποθήκευσης PDF: Μετατροπή DOCX σε PDF με ετικέτες σχήματος'
url: /el/java/document-conversion-and-export/pdf-save-options-convert-docx-to-pdf-with-shape-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# pdf save options – Μετατροπή DOCX σε PDF και Εξαγωγή Σχημάτων ως Inline Tags

Έχετε αναρωτηθεί ποτέ πώς οι **pdf save options** μπορούν να σας βοηθήσουν να **convert docx to pdf** διατηρώντας τα αιωρούμενα σχήματα τακτοποιημένα; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν τα έγγραφα Word τους περιέχουν εικόνες, πλαίσια κειμένου ή αντικείμενα σχεδίασης που μετακινούνται μετά τη μετατροπή.  

Τα καλά νέα; Με λίγες γραμμές κώδικα Java μπορείτε να πείτε στο Aspose.Words να αντιμετωπίζει αυτά τα αιωρούμενα σχήματα ως inline `<span>` tags, παρέχοντάς σας ένα καθαρό PDF που σέβεται την αρχική διάταξη. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, από τη φόρτωση ενός αρχείου `.docx` μέχρι τη ρύθμιση των **pdf save options**, και τέλος την αποθήκευση του αποτελέσματος ως PDF. Στο τέλος, θα γνωρίζετε ακριβώς **how to export shapes** σωστά, και θα είστε έτοιμοι να **save docx as pdf** σε οποιοδήποτε έργο Java.

## Τι θα μάθετε

- Πώς να **convert docx to pdf** χρησιμοποιώντας το Aspose.Words for Java.  
- Ο ρόλος των **pdf save options** στη διαμόρφωση του τελικού αποτελέσματος.  
- Τα ακριβή βήματα **how to export shapes** ως inline tags.  
- Συμβουλές για την αντιμετώπιση κοινών παγίδων όταν **convert word to pdf**.  
- Ένα πλήρες, εκτελέσιμο δείγμα κώδικα που μπορείτε να ενσωματώσετε στο IDE σας σήμερα.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

1. **Java Development Kit (JDK) 8 ή νεότερο** – ο κώδικας εκτελείται σε οποιοδήποτε πρόσφατο JDK.  
2. Βιβλιοθήκη **Aspose.Words for Java** (έκδοση 23.10 ή νεότερη). Μπορείτε να την κατεβάσετε από το Maven Central:

   ```xml
   <dependency>
       <groupId>com.aspose</groupId>
       <artifactId>aspose-words</artifactId>
       <version>23.10</version>
   </dependency>
   ```

3. Ένα **Word document** (`shapes.docx`) που περιέχει αιωρούμενα σχήματα που θέλετε να εξάγετε.  
4. Ένα αγαπημένο IDE (IntelliJ IDEA, Eclipse, VS Code…) – ό,τι σας βολεύει.

> **Pro tip:** Αν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση στο `pom.xml` και αφήστε το IDE να διαχειριστεί τη λήψη. Δεν απαιτείται χειροκίνητη διαχείριση αρχείων JAR.

## Step‑by‑Step Implementation

Παρακάτω χωρίζουμε τη λύση σε τέσσερα λογικά βήματα. Κάθε βήμα είναι ενσωματωμένο σε μια επικεφαλίδα H2 – ένα από αυτά περιέχει ακόμη και τη βασική λέξη-κλειδί **pdf save options** για βελτιστοποίηση SEO.

### 1️⃣ Load the Source DOCX Document

Πρώτα, πρέπει να φορτώσουμε το αρχείο Word στη μνήμη. Το Aspose.Words το κάνει με μία μόνο γραμμή κώδικα.

```java
import com.aspose.words.*;

public class PdfShapeTagging {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source Word document
        Document wordDoc = new Document("YOUR_DIRECTORY/shapes.docx");
```

*Why this matters:* Η φόρτωση του εγγράφου είναι η βάση για οποιαδήποτε μετατροπή. Αν η διαδρομή είναι λανθασμένη, η υπόλοιπη αλυσίδα δεν εκτελείται και θα δείτε μια εξαίρεση τύπου “File not found”. Ελέγξτε ξανά το διαχωριστικό καταλόγου για το λειτουργικό σας σύστημα (`/` λειτουργεί σε Windows, macOS και Linux).

### 2️⃣ Configure PDF Save Options to Export Shapes Inline

Εδώ λάμπουν οι **pdf save options**. Από προεπιλογή, το Aspose αντιμετωπίζει τα αιωρούμενα σχήματα ως ξεχωριστά αντικείμενα, τα οποία μπορούν να μετακινηθούν κατά τη μετατροπή. Ορίζοντας `setExportFloatingShapesAsInlineTag(true)` λέτε στη μηχανή να τυλίγει κάθε σχήμα σε ένα inline `<span>` tag, διατηρώντας τη θέση του σε σχέση με το περιβάλλον κείμενο.

```java
        // Step 2: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
        pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);
```

*Why this matters:* Χωρίς αυτή τη σημαία, ένα αιωρούμενο πλαίσιο κειμένου μπορεί να εμφανιστεί σε διαφορετική σελίδα στο PDF, σπάζοντας τη διάταξη που περάσατε ώρες να τελειοποιήσετε. Αυτή η επιλογή είναι η κλειδί απάντηση στο ερώτημα **how to export shapes** όταν **convert docx to pdf**.

### 3️⃣ Save the Document as PDF Using the Configured Options

Τώρα γράφουμε πραγματικά το αρχείο PDF. Η μέθοδος `save` δέχεται τη διαδρομή προορισμού και το `PdfSaveOptions` που μόλις διαμορφώσαμε.

```java
        // Step 3: Save the document as a PDF using the configured options
        wordDoc.save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);
    }
}
```

*Why this matters:* Ο συνδυασμός του `Document.save` με τα προσαρμοσμένα `PdfSaveOptions` εξασφαλίζει ότι το τελικό PDF σέβεται τόσο τη ροή του κειμένου όσο και τη θέση των σχημάτων. Αυτός είναι ο οριστικός τρόπος να **save docx as pdf** όταν χρειάζεστε πιστότητα των σχημάτων.

### 4️⃣ Verify the Result – What to Expect

Μετά την εκτέλεση του προγράμματος, ανοίξτε το `output.pdf` σε οποιονδήποτε προβολέα PDF. Θα πρέπει να δείτε:

- Όλες οι παράγραφοι ακριβώς όπως εμφανίζονται στο αρχικό αρχείο Word.  
- Τα αιωρούμενα σχήματα (π.χ., πλαίσια κειμένου, εικόνες) αποδομένα **inline** μέσα στην περιβάλλουσα παράγραφο, τυλιγμένα σε αόρατα `<span>` tags (δεν θα δείτε τα tags, αλλά διατηρούν τη διάταξη).  
- Καμία απρόσμενη αλλαγή σελίδας ή μετακινημένα αντικείμενα.

Αν κάτι φαίνεται λανθασμένο, ελέγξτε ξανά ότι το πηγαίο έγγραφο χρησιμοποιεί πραγματικά αιωρούμενα σχήματα και ότι χρησιμοποιείτε μια πρόσφατη έκδοση του Aspose.Words. Παλαιότερες εκδόσεις μπορεί να αγνοούν τη σημαία `setExportFloatingShapesAsInlineTag`.

> **Common pitfall:** Κάποιοι προγραμματιστές προσπαθούν να **convert word to pdf** απλώς καλώντας `Document.save("out.pdf")` χωρίς να ορίσουν επιλογές. Αυτό λειτουργεί για απλό κείμενο αλλά συχνά καταστρέφει σύνθετες διατάξεις. Πάντα ρυθμίζετε τις κατάλληλες **pdf save options** όταν δουλεύετε με γραφικά.

## Full Working Example

Παρακάτω είναι το πλήρες, αυτόνομο πρόγραμμα Java που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα νέο αρχείο κλάσης. Αντικαταστήστε το `YOUR_DIRECTORY` με την απόλυτη διαδρομή προς τα αρχεία σας.

```java
import com.aspose.words.*;

public class PdfShapeTagging {
    public static void main(String[] args) throws Exception {
        // Load the source Word document (make sure the path is correct)
        Document wordDoc = new Document("YOUR_DIRECTORY/shapes.docx");

        // Create PDF save options and tell Aspose to export floating shapes as inline <span> tags
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
        pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);

        // Save the document as PDF using the configured options
        wordDoc.save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);

        System.out.println("Conversion complete! Check output.pdf to see the results.");
    }
}
```

**Expected console output:**

```
Conversion complete! Check output.pdf to see the results.
```

Ανοίξτε το `output.pdf` και θα παρατηρήσετε ότι κάθε σχήμα παραμένει ακριβώς στη θέση που τοποθετήσατε στο `shapes.docx`. Αυτή είναι η δύναμη των σωστών **pdf save options**.

## Frequently Asked Questions (FAQs)

**Q: Λειτουργεί αυτό με αρχεία DOCX προστατευμένα με κωδικό;**  
A: Ναι. Φορτώστε το έγγραφο με ένα αντικείμενο `LoadOptions` που περιλαμβάνει τον κωδικό, και στη συνέχεια εφαρμόστε τις ίδιες **pdf save options**.

**Q: Μπορώ να εξάγω τα σχήματα ως ξεχωριστές εικόνες αντί για inline tags;**  
A: Απόλυτα. Ορίστε `pdfSaveOptions.setExportFloatingShapesAsInlineTag(false)` και χρησιμοποιήστε `pdfSaveOptions.setExportEmbeddedImages(true)` για να τα διατηρήσετε ως εικόνες.

**Q: Τι γίνεται αν χρειαστεί να **convert docx to pdf** σε μια web υπηρεσία;**  
A: Ο ίδιος κώδικας ισχύει· απλώς ροή (stream) των εισόδων και εξόδων αντί για χρήση διαδρομών αρχείων. Το Aspose.Words λειτουργεί εξίσου καλά με `InputStream`/ `OutputStream`.

**Q: Υπάρχει τρόπος να ελέγξω το DPI των εξαγόμενων εικόνων;**  
A: Ναι. Χρησιμοποιήστε `pdfSaveOptions.setImageDpi(300)` (ή οποιαδήποτε τιμή χρειάζεστε) πριν καλέσετε το `save`.

## Next Steps and Related Topics

Τώρα που έχετε κατακτήσει τις **pdf save options** για τη διαχείριση σχημάτων, ίσως θέλετε να εξερευνήσετε:

- **How to export shapes** ως SVG για PDF πλούσια σε διανυσματικά στοιχεία.  
- Χρήση **convert docx to pdf** με προσαρμοσμένα περιθώρια σελίδας και κεφαλίδες/υποσέλιδα.  
- Επεξεργασία πολλαπλών αρχείων Word σε batch με μια μόνο ρουτίνα Java.  
- Ενσωμάτωση της μετατροπής σε ένα Spring Boot REST endpoint για **save docx as pdf** σε πραγματικό χρόνο.  

Κάθε ένα από αυτά βασίζεται στην ίδια θεμελιώδη προσέγγιση που καλύψαμε εδώ, οπότε η μετάβαση θα είναι ομαλή.

## Conclusion

Διασχίσαμε μια πλήρη, end‑to‑end λύση που δείχνει ακριβώς **how to export shapes** όταν **convert docx to pdf** χρησιμοποιώντας το Aspose.Words for Java. Ρυθμίζοντας τις **pdf save options** ώστε να αντιμετωπίζουν τα αιωρούμενα αντικείμενα ως inline tags, παίρνετε μια πιστή αναπαράσταση PDF χωρίς τις εκπλήξεις διάταξης που συχνά πλήττουν τις αφελείς μετατροπές.  

Δοκιμάστε το, προσαρμόστε τις επιλογές ώστε να ταιριάζουν στο έργο σας, και αφήστε τη βιβλιοθήκη να κάνει το βαρέως εργασίας. Αν αντιμετωπίσετε προβλήματα, επιστρέψτε στις FAQs ή ελέγξτε την επίσημη τεκμηρίωση του Aspose – είναι αξιόπιστη πηγή.

*Καλή προγραμματιστική!*  

---

![Διάγραμμα που απεικονίζει τις pdf save options σε δράση](image.png "Διάγραμμα pdf save options")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}