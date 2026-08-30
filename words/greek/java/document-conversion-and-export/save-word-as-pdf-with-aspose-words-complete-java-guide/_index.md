---
category: general
date: 2026-06-08
description: Αποθηκεύστε το Word ως PDF γρήγορα χρησιμοποιώντας το Aspose.Words for
  Java. Μάθετε πώς να μετατρέπετε docx σε pdf, να εξάγετε σχήματα και να χρησιμοποιείτε
  ετικέτες inline span σε ένα ενιαίο σεμινάριο.
draft: false
keywords:
- save word as pdf
- convert docx to pdf
- how to export shapes
- aspose word to pdf
- inline span tag
language: el
og_description: Αποθηκεύστε το Word ως PDF χρησιμοποιώντας το Aspose.Words for Java.
  Αυτός ο οδηγός δείχνει πώς να μετατρέψετε το docx σε pdf, να εξάγετε σχήματα ως
  ενσωματωμένες ετικέτες span και να αποφύγετε κοινά προβλήματα.
og_title: Αποθήκευση Word ως PDF με το Aspose.Words – Εκπαιδευτικό Java
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Save Word as PDF quickly using Aspose.Words for Java. Learn to convert
    docx to pdf, export shapes, and use inline span tags in one tutorial.
  headline: Save Word as PDF with Aspose.Words – Complete Java Guide
  type: TechArticle
- description: Save Word as PDF quickly using Aspose.Words for Java. Learn to convert
    docx to pdf, export shapes, and use inline span tags in one tutorial.
  name: Save Word as PDF with Aspose.Words – Complete Java Guide
  steps:
  - name: Why Each Step Matters
    text: 1. **Loading the Document** – `Document` parses the DOCX file and builds
      an in‑memory object model. If the file isn’t found, Aspose throws a clear `FileNotFoundException`,
      which you can catch for graceful error handling.
  - name: Running the Example
    text: '1. **Add the Aspose dependency** to your `pom.xml` (Maven) or `build.gradle`
      (Gradle). For Maven:'
  - name: Expected Output
    text: 'Open `FloatingShapes.pdf` with any PDF viewer. You’ll notice:'
  type: HowTo
- questions:
  - answer: Yes. Aspose converts SVG to a raster representation first, then wraps
      it in the inline `<span>`. The visual fidelity remains high, but file size may
      increase—consider enabling image compression if that’s a concern.
    question: Does this work for SVG images inside the Word file?
  - answer: Tables are treated as block elements, not spans. The `setExportFloatingShapesAsInlineTag`
      flag only affects shapes (pictures, text boxes, WordArt). For tables you might
      need to restructure the source DOCX or use `PdfSaveOptions.setExportDocumentStructure(true)`
      to retain proper flow.
    question: What if my document contains floating tables?
  - answer: 'Not directly via an option. You’d need to manipulate the document model—remove
      the shape’s `WrapType` or convert it to an inline picture before saving. ##
      Aspose Word to PDF – Edge Cases & Tips - **Large Documents**: For files >100
      MB, enable `pdfOptions.setMemoryOptimization(true)` to reduce heap u'
    question: Can I disable the inline conversion for a single shape?
  type: FAQPage
tags:
- Aspose.Words
- Java
- PDF conversion
title: Αποθήκευση Word ως PDF με το Aspose.Words – Πλήρης οδηγός Java
url: /el/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Word ως PDF – Πλήρης Οδηγός Java

Έχετε χρειαστεί ποτέ να **αποθηκεύσετε Word ως PDF** από μια εφαρμογή Java αλλά δεν ήσασταν σίγουροι ποια βιβλιοθήκη να εμπιστευτείτε; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν προβλήματα με τη μετατροπή αρχείων DOCX διατηρώντας τη διάταξη, ειδικά όταν υπάρχουν αιωρούμενα σχήματα.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πρακτικό παράδειγμα που **μετατρέπει docx σε pdf**, δείχνει **πώς να εξάγετε σχήματα** ως ενσωματωμένα `<span>` tags, και αξιοποιεί το ισχυρό **Aspose.Words for Java** API. Στο τέλος θα έχετε ένα έτοιμο πρόγραμμα που παράγει καθαρό PDF κάθε φορά.

## Τι Θα Μάθετε

- Φόρτωση εγγράφου Word (`.docx`) με Aspose.Words.  
- Διαμόρφωση `PdfSaveOptions` για έλεγχο της εξόδου PDF.  
- Ενεργοποίηση της δυνατότητας **inline span tag** ώστε τα αιωρούμενα σχήματα να γίνονται ενσωματωμένα στοιχεία HTML‑style.  
- Αποθήκευση του αποτελέσματος ως αρχείο PDF στο δίσκο.  
- Εντοπισμός κοινών παγίδων κατά τις μετατροπές **aspose word to pdf**.

Καμία εξωτερική υπηρεσία, κανένα περίπλοκο κόλπο—απλός κώδικας Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

## Προαπαιτούμενα

- Java 8 ή νεότερη (ο κώδικας λειτουργεί επίσης σε Java 11+).  
- Βιβλιοθήκη Aspose.Words for Java (μπορείτε να κατεβάσετε το τελευταίο JAR από το Maven Central: `com.aspose:aspose-words:23.12` τη στιγμή της συγγραφής).  
- Ένα απλό αρχείο Word (`FloatingShapes.docx`) που περιέχει μερικές αιωρούμενες εικόνες ή πλαίσια κειμένου—αυτό θα μας επιτρέψει να δούμε το **πώς να εξάγετε σχήματα** σε δράση.  
- Ένα IDE ή κειμενογράφο με το οποίο αισθάνεστε άνετα (IntelliJ IDEA, Eclipse, VS Code…).

> **Pro tip:** Αν δεν έχετε άδεια, η Aspose προσφέρει δωρεάν δοκιμή 30 ημερών που λειτουργεί τέλεια για ανάπτυξη και δοκιμές.

![Διάγραμμα που δείχνει τη ροή αποθήκευσης ενός εγγράφου Word ως PDF χρησιμοποιώντας Aspose.Words – η κύρια λέξη-κλειδί εμφανίζεται στο κείμενο alt](image-placeholder.png "παράδειγμα αποθήκευσης word ως pdf με Aspose.Words")

## Αποθήκευση Word ως PDF – Υλοποίηση Java Βήμα‑βήμα

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα. Κάθε γραμμή σχολιάζεται ώστε να βλέπετε *γιατί* κάνουμε ό,τι κάνουμε, όχι μόνο *τι* κάνουμε.

```java
import com.aspose.words.*;

public class PdfFloatingShapeTagDemo {

    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Load the source Word document (convert docx to pdf starts here)
        // -------------------------------------------------
        // Replace the path with the location of your DOCX file.
        Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

        // -------------------------------------------------
        // Step 2: Create PDF save options – this is where
        // we tell Aspose.Words how we want the PDF to look.
        // -------------------------------------------------
        PdfSaveOptions pdfOptions = new PdfSaveOptions();

        // -------------------------------------------------
        // Step 3: Export floating shapes as inline <span> tags.
        // This is the key setting for the "how to export shapes"
        // requirement. It turns each floating image or textbox
        // into an inline HTML‑style element, which many HTML‑to‑PDF
        // pipelines understand natively.
        // -------------------------------------------------
        pdfOptions.setExportFloatingShapesAsInlineTag(true);

        // -------------------------------------------------
        // Step 4: Save the document as PDF using the configured options.
        // This is the final act of the save word as pdf process.
        // -------------------------------------------------
        doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

        System.out.println("PDF created successfully at YOUR_DIRECTORY/FloatingShapes.pdf");
    }
}
```

### Γιατί Κάθε Βήμα Είναι Σημαντικό

1. **Φόρτωση του Εγγράφου** – Το `Document` αναλύει το αρχείο DOCX και δημιουργεί ένα μοντέλο αντικειμένων στη μνήμη. Αν το αρχείο δεν βρεθεί, η Aspose ρίχνει ένα σαφές `FileNotFoundException`, το οποίο μπορείτε να πιάσετε για ευγενική διαχείριση σφαλμάτων.

2. **PdfSaveOptions** – Αυτό το αντικείμενο είναι η καρδιά της προσαρμογής **aspose word to pdf**. Μπορείτε να ορίσετε συμπίεση εικόνων, ενσωμάτωση γραμματοσειρών ή ακόμη και να ελέγξετε την έκδοση PDF εδώ. Στην περίπτωσή μας αλλάζουμε μόνο μία σημαία, αλλά η κλάση είναι επεκτάσιμη για μελλοντικές ανάγκες.

3. **ExportFloatingShapesAsInlineTag** – Από προεπιλογή, τα αιωρούμενα σχήματα γίνονται ξεχωριστά αντικείμενα στο PDF, κάτι που μπορεί να διακόψει ροές HTML‑to‑PDF. Ορίζοντας αυτή τη σημαία, η Aspose τα αποδίδει ως στοιχεία `<span>` με κατάλληλο CSS, διατηρώντας τη οπτική διάταξη ενώ κάνει το PDF πιο φιλικό στο web.

4. **Αποθήκευση του PDF** – Η μέθοδος `save` γράφει τα τελικά bytes στο δίσκο. Μπορείτε επίσης να ρέξετε απευθείας σε ένα `OutputStream` αν χρειάζεται να επιστρέψετε το PDF από μια web υπηρεσία.

### Εκτέλεση του Παραδείγματος

1. **Προσθέστε την εξάρτηση Aspose** στο `pom.xml` (Maven) ή στο `build.gradle` (Gradle). Για Maven:

   ```xml
   <dependency>
       <groupId>com.aspose</groupId>
       <artifactId>aspose-words</artifactId>
       <version>23.12</version>
   </dependency>
   ```

2. **Αντικαταστήστε το `YOUR_DIRECTORY`** με μια απόλυτη ή σχετική διαδρομή που υπάρχει στο σύστημά σας.

3. **Συμπιέστε και τρέξτε**:

   ```bash
   mvn compile exec:java -Dexec.mainClass=PdfFloatingShapeTagDemo
   ```

   Θα πρέπει να δείτε το μήνυμα στην κονσόλα που επιβεβαιώνει την επιτυχία, και ένα αρχείο `FloatingShapes.pdf` να εμφανίζεται στο φάκελο προορισμού.

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `FloatingShapes.pdf` με οποιονδήποτε προβολέα PDF. Θα παρατηρήσετε:

- Όλο το κανονικό κείμενο εμφανίζεται ακριβώς όπως στο αρχικό έγγραφο Word.  
- Οι αιωρούμενες εικόνες ή τα πλαίσια κειμένου εμφανίζονται πλέον ενσωματωμένα, διατηρώντας τη θέση τους σε σχέση με τις γύρω παραγράφους.  
- Δεν λείπουν γραμματοσειρές ή δεν διασπάζεται η διάταξη—η Aspose ενσωματώνει αυτόματα τις απαιτούμενες γραμματοσειρές.

Αν εξετάσετε τη δομή του PDF (χρησιμοποιώντας εργαλείο όπως `pdfinfo` ή έναν PDF debugger), θα δείτε τα σχήματα να εμφανίζονται ως αντικείμενα τύπου `<span>`, που αποτελεί το χαρακτηριστικό της τεχνικής **inline span tag**.

## Μετατροπή DOCX σε PDF με Aspose.Words – Πέρα από τα Βασικά

Ο παραπάνω κώδικας είναι μια ελάχιστη εικονογράφηση, αλλά τα σενάρια **convert docx to pdf** συχνά απαιτούν επιπλέον ρυθμίσεις:

| Απαίτηση | Ρύθμιση Aspose | Γιατί Βοηθά |
|----------|----------------|--------------|
| Μείωση μεγέθους αρχείου | `pdfOptions.setCompressImages(true);` | Συμπιέζει τις ενσωματωμένες εικόνες χωρίς ορατή απώλεια. |
| Διατήρηση υπερσυνδέσμων | `pdfOptions.setExportDocumentStructure(true);` | Κρατά τις κλικ-συνδέσμους λειτουργικές. |
| Ενσωμάτωση όλων των γραμματοσειρών | `pdfOptions.setEmbedFullFonts(true);` | Εγγυάται ομοιόμορφη απόδοση σε οποιονδήποτε υπολογιστή. |
| Προσθήκη μεταδεδομένων PDF | `pdfOptions.setCustomProperties(...);` | Βελτιώνει την αναζητησιμότητα και τη συμμόρφωση. |

Μπορείτε να αλυσίδετε αυτές τις κλήσεις πριν από το βήμα `save`. Η βιβλιοθήκη είναι σχεδιασμένη να είναι fluent, ώστε να μην καταλήξετε με ένα ακατάστατο μίγμα ρυθμίσεων.

## Πώς να Εξάγετε Σχήματα ως Inline Span Tag – Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό για εικόνες SVG μέσα στο αρχείο Word;**  
Α: Ναι. Η Aspose μετατρέπει το SVG πρώτα σε ραστερική αναπαράσταση, έπειτα το τυλίγει σε ενσωματωμένο `<span>`. Η οπτική πιστότητα παραμένει υψηλή, αλλά το μέγεθος του αρχείου μπορεί να αυξηθεί—σκεφτείτε να ενεργοποιήσετε τη συμπίεση εικόνων αν αυτό αποτελεί πρόβλημα.

**Ε: Τι γίνεται αν το έγγραφο περιέχει αιωρούμενους πίνακες;**  
Α: Οι πίνακες αντιμετωπίζονται ως μπλοκ στοιχεία, όχι ως spans. Η σημαία `setExportFloatingShapesAsInlineTag` επηρεάζει μόνο σχήματα (εικόνες, πλαίσια κειμένου, WordArt). Για πίνακες ίσως χρειαστεί να αναδιαρθρώσετε το αρχικό DOCX ή να χρησιμοποιήσετε `PdfSaveOptions.setExportDocumentStructure(true)` για να διατηρήσετε τη σωστή ροή.

**Ε: Μπορώ να απενεργοποιήσω τη μετατροπή σε inline για ένα μόνο σχήμα;**  
Α: Δεν υπάρχει άμεση επιλογή. Θα πρέπει να χειριστείτε το μοντέλο του εγγράφου—να αφαιρέσετε το `WrapType` του σχήματος ή να το μετατρέψετε σε ενσωματωμένη εικόνα πριν την αποθήκευση.

## Aspose Word to PDF – Ακραίες Περιπτώσεις & Συμβουλές

- **Μεγάλα Έγγραφα**: Για αρχεία >100 MB, ενεργοποιήστε `pdfOptions.setMemoryOptimization(true)` για μείωση χρήσης heap.  
- **DOCX με Κωδικό Πρόσβασης**: Φορτώστε με `LoadOptions` που περιέχει τον κωδικό, μετά προχωρήστε κανονικά.  
- **Ασφάλεια Νήματος**: Τα αντικείμενα `Document` δεν είναι thread‑safe. Δημιουργήστε νέο instance ανά νήμα αν χτίζετε web υπηρεσία που διαχειρίζεται πολλές μετατροπές ταυτόχρονα.  
- **Φόρτωση Άδειας**: Τοποθετήστε το αρχείο `Aspose.Words.lic` στο classpath και καλέστε `License license = new License(); license.setLicense("Aspose.Words.lic");` πριν από οποιαδήποτε δημιουργία `Document` για να αποφύγετε το υδατογράφημα αξιολόγησης.

## Πλήρες Παράδειγμα – Όλα τα Τμήματα Μαζί

Παρακάτω βρίσκεται το τελικό, αυτόνομο πρόγραμμα που περιλαμβάνει προαιρετικές βελτιώσεις για παραγωγική μετατροπή.

```java
import com.aspose.words.*;

public class PdfFloatingShapeTagDemo {

    public static void main(String[] args) {
        try {
            // Load license (optional, removes evaluation watermark)
            // License license = new License();
            // license.setLicense("Aspose.Words.lic");

            // 1️⃣ Load the source DOCX
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // 2️⃣ Configure PDF options
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // how to export shapes
            pdfOptions.setCompressImages(true);                 // reduce size
            pdfOptions.setEmbedFullFonts(true);                 // ensure fidelity

            // 3️⃣ Save as PDF
            String outPath = "YOUR_DIRECTORY/FloatingShapes.pdf";
            doc.save(outPath, pdfOptions);

            System.out.println("PDF saved successfully: " + outPath);
        } catch (Exception ex) {
            System.err.println("Conversion failed: " + ex.getMessage());
            ex.printStackTrace();
        }
    }
}
```

Τρέξτε

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/exporting-documents-to-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}