---
category: general
date: 2025-12-23
description: Πώς να αποθηκεύσετε PDF από αρχείο Word χρησιμοποιώντας Java. Μάθετε
  πώς να μετατρέψετε docx σε PDF, να εξάγετε σχήματα και να αποθηκεύσετε το έγγραφο
  ως PDF σε ένα ενιαίο, αξιόπιστο βήμα.
draft: false
keywords:
- how to save pdf
- convert docx to pdf
- save document as pdf
- convert word to pdf
- how to export shapes
language: el
og_description: Μάθετε πώς να αποθηκεύσετε PDF από ένα αρχείο DOCX με ενσωματωμένα
  σχήματα χρησιμοποιώντας Java. Αυτός ο οδηγός καλύπτει τη μετατροπή του DOCX σε PDF,
  την εξαγωγή των σχημάτων και την αποθήκευση του εγγράφου ως PDF.
og_title: Πώς να αποθηκεύσετε PDF από DOCX – Πλήρης οδηγός βήμα‑προς‑βήμα
tags:
- Java
- Aspose.Words
- PDF conversion
title: Πώς να αποθηκεύσετε PDF από DOCX με ενσωματωμένα σχήματα – Πλήρης οδηγός προγραμματισμού
url: /el/java/document-conversion-and-export/how-to-save-pdf-from-docx-with-inline-shapes-complete-progra/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε PDF από DOCX με ενσωματωμένα σχήματα – Πλήρης Οδηγός Προγραμματισμού

Αν ψάχνετε για **πώς να αποθηκεύσετε pdf** από ένα έγγραφο Word, βρίσκεστε στο σωστό μέρος. Είτε χρειάζεστε να **μετατρέψετε docx σε pdf** για μια αλυσίδα αναφορών είτε απλώς θέλετε να αρχειοθετήσετε μια σύμβαση, αυτό το tutorial σας δείχνει τα ακριβή βήματα—χωρίς εικασίες.

Στις επόμενες λίγες λεπτά θα ανακαλύψετε πώς να **μετατρέψετε word σε pdf** διατηρώντας τα αιωρούμενα σχήματα, πώς να **αποθηκεύσετε το έγγραφο ως pdf** με μία μόνο κλήση μεθόδου, και γιατί η σημαία `setExportFloatingShapesAsInlineTag` είναι σημαντική. Χωρίς εξωτερικά εργαλεία, μόνο καθαρή Java και η βιβλιοθήκη Aspose.Words for Java.

---

![παράδειγμα αποθήκευσης pdf](image-placeholder.png "Εικονογράφηση του πώς να αποθηκεύσετε pdf με ενσωματωμένα σχήματα")

## Πώς να αποθηκεύσετε PDF χρησιμοποιώντας το Aspose.Words για Java

Το Aspose.Words είναι μια ώριμη, πλήρως εξοπλισμένη API που σας επιτρέπει να χειρίζεστε έγγραφα Word προγραμματιστικά. Η κύρια κλάση είναι `Document`, η οποία αντιπροσωπεύει ολόκληρο το αρχείο DOCX στη μνήμη. Χρησιμοποιώντας το `PdfSaveOptions` μπορείτε να ρυθμίσετε λεπτομερώς τη διαδικασία μετατροπής, συμπεριλαμβανομένων των ενοχλητικών αιωρούμενων σχημάτων.

### Γιατί να χρησιμοποιήσετε το `setExportFloatingShapesAsInlineTag`;

Οι αιωρούμενες εικόνες, τα πλαίσια κειμένου και το SmartArt αποθηκεύονται ως ξεχωριστά αντικείμενα σχεδίασης σε ένα DOCX. Όταν μετατρέπετε σε PDF, η προεπιλεγμένη συμπεριφορά είναι να τα αποδώσει ως ξεχωριστές στρώσεις, κάτι που μπορεί να προκαλέσει προβλήματα στοίχισης σε ορισμένους προβολείς. Η ενεργοποίηση του **πώς να εξάγετε σχήματα** αναγκάζει τη βιβλιοθήκη να ενσωματώσει αυτά τα αντικείμενα απευθείας στο ρεύμα περιεχομένου του PDF, εξασφαλίζοντας ότι ό,τι βλέπετε στο Word είναι ακριβώς αυτό που εμφανίζεται στο PDF.

---

## Βήμα 1: Ρυθμίστε το Έργο σας

Πριν γράψετε οποιονδήποτε κώδικα, βεβαιωθείτε ότι έχετε τις σωστές εξαρτήσεις.

```xml
<!-- pom.xml snippet for Maven users -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```groovy
implementation 'com.aspose:aspose-words:23.10'
```

> **Pro tip:** Το Aspose.Words είναι εμπορική βιβλιοθήκη, αλλά μια δωρεάν δοκιμή 30 ημερών λειτουργεί τέλεια για εκμάθηση και πρωτοτυπία.

Δημιουργήστε ένα απλό έργο Java (IDEA, Eclipse ή VS Code) και προσθέστε την παραπάνω εξάρτηση. Αυτό είναι όλο το setup που χρειάζεστε για να **μετατρέψετε docx σε pdf**.

---

## Βήμα 2: Φορτώστε το Πηγαίο Έγγραφο

Η πρώτη γραμμή κώδικα φορτώνει το αρχείο Word που θέλετε να μετατρέψετε. Αντικαταστήστε το `YOUR_DIRECTORY` με μια απόλυτη ή σχετική διαδρομή στο σύστημά σας.

```java
import com.aspose.words.Document;

// Load the source DOCX
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Τι γίνεται αν το αρχείο δεν υπάρχει;**  
> Ο κατασκευαστής ρίχνει `java.io.FileNotFoundException`. Τυλίξτε την κλήση σε ένα μπλοκ `try/catch` και καταγράψτε ένα φιλικό μήνυμα—βοηθά όταν το tutorial χρησιμοποιείται σε παραγωγικές αλυσίδες.

---

## Βήμα 3: Ρυθμίστε τις Επιλογές Αποθήκευσης PDF (Εξαγωγή Σχημάτων)

Τώρα λέμε στο Aspose.Words πώς να αντιμετωπίσει τα αιωρούμενα αντικείμενα.

```java
import com.aspose.words.PdfSaveOptions;

// Create PDF save options and enable inline tags for floating shapes
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);
```

Η ρύθμιση `setExportFloatingShapesAsInlineTag(true)` είναι ο πυρήνας του **πώς να εξάγετε σχήματα**. Χωρίς αυτήν, τα σχήματα μπορεί να μετακινηθούν ή να εξαφανιστούν μετά τη μετατροπή, ειδικά όταν ο προορισμός PDF δεν υποστηρίζει πολύπλοκες στρώσεις σχεδίασης.

---

## Βήμα 4: Αποθηκεύστε το Έγγραφο ως PDF

Τέλος, γράψτε το PDF στο δίσκο.

```java
// Save the document as PDF using the configured options
doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfSaveOptions);
```

Όταν αυτή η γραμμή ολοκληρωθεί, θα έχετε ένα αρχείο με όνομα `inlineShapes.pdf` που μοιάζει ακριβώς με το `input.docx`, με όλες τις αιωρούμενες εικόνες. Αυτό ολοκληρώνει το τμήμα **αποθήκευσης εγγράφου ως pdf της ροής εργασίας.

---

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας τα πάντα, εδώ είναι μια έτοιμη‑για‑εκτέση κλάση που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο έργο σας.

```java
import com.aspose.words.Document;
import com.aspose.words.PdfSaveOptions;

public class DocxToPdfConverter {

    public static void main(String[] args) {
        // Adjust these paths before running
        String inputPath  = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/inlineShapes.pdf";

        try {
            // Step 1: Load the DOCX file
            Document doc = new Document(inputPath);

            // Step 2: Prepare PDF options – this is where we answer how to export shapes
            PdfSaveOptions options = new PdfSaveOptions();
            options.setExportFloatingShapesAsInlineTag(true);

            // Step 3: Save as PDF – the core of how to save pdf
            doc.save(outputPath, options);

            System.out.println("Conversion successful! PDF created at: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `inlineShapes.pdf` σε οποιονδήποτε προβολέα PDF. Όλες οι εικόνες, τα πλαίσια κειμένου και το SmartArt που αιωρούνταν στο αρχικό αρχείο Word θα πρέπει τώρα να εμφανίζονται ενσωματωμένα, διατηρώντας την ακριβή διάταξη που σχεδιάσατε.

---

## Συνηθισμένες Παραλλαγές & Ακραίες Περιπτώσεις

| Κατάσταση | Τι να Προσαρμόσετε | Γιατί |
|-----------|-------------------|------|
| **Μεγάλα έγγραφα (>100 MB)** | Αυξήστε τη μνήμη heap της JVM (`-Xmx2g`) | Αποτρέπει το `OutOfMemoryError` κατά τη μετατροπή |
| **Απαιτούνται μόνο συγκεκριμένες σελίδες** | Χρησιμοποιήστε `PdfSaveOptions.setPageIndex()` και `setPageCount()` | Εξοικονομεί χρόνο και μειώνει το μέγεθος του αρχείου |
| **DOCX με προστασία κωδικού** | Φορτώστε με `LoadOptions.setPassword()` | Επιτρέπει τη μετατροπή χωρίς χειροκίνητο ξεκλείδωμα |
| **Απαιτούνται εικόνες υψηλής ανάλυσης** | Ορίστε `PdfSaveOptions.setImageResolution(300)` | Βελτιώνει την ποιότητα εικόνας με κόστος μεγαλύτερου PDF |
| **Εκτέλεση σε Linux χωρίς GUI** | Καμία επιπλέον ενέργεια – το Aspose.Words είναι headless | Ιδανικό για CI/CD pipelines |

Αυτές οι προσαρμογές δείχνουν μια πιο βαθιά κατανόηση των σεναρίων **μετατροπής word σε pdf**, καθιστώντας το tutorial χρήσιμο τόσο για αρχάριους όσο και για έμπειρους προγραμματιστές.

---

## Πώς να Επαληθεύσετε το Αποτέλεσμα

1. Ανοίξτε το παραγόμενο PDF σε Adobe Acrobat Reader ή σε οποιονδήποτε σύγχρονο φυλλομετρητή.  
2. Μεγέθυνση στο 100 % και ελέγξτε ότι κάθε αιωρούμενο σχήμα ευθυγραμμίζεται με το γύρω κείμενο.  
3. Χρησιμοποιήστε το παράθυρο “Properties” (συνήθως `Ctrl+D`) για να επιβεβαιώσετε ότι η έκδοση PDF είναι 1.7 ή υψηλότερη—το Aspose.Words προεπιλογή είναι η πιο πρόσφατη συμβατή έκδοση.  

Αν κάποιο σχήμα εμφανιστεί εκτός θέσης, ελέγξτε ξανά ότι κλήθηκε το `setExportFloatingShapesAsInlineTag(true)`. Αυτή η μικρή σημαία συχνά λύνει τα πιο επίμονα προβλήματα **πώς να εξάγετε σχήματα**.

---

## Συμπέρασμα

Διασχίσαμε το **πώς να αποθηκεύσετε pdf** από ένα αρχείο DOCX διατηρώντας τα αιωρούμενα γραφικά, καλύψαμε τα ακριβή βήματα για **μετατροπή docx σε pdf**, και εξηγήσαμε γιατί η επιλογή `setExportFloatingShapesAsInlineTag` είναι το μυστικό συστατικό για αξιόπιστη **εξαγωγή σχημάτων**. Το πλήρες, εκτελέσιμο παράδειγμα Java δείχνει ότι μπορείτε να **αποθηκεύσετε το έγγραφο ως pdf** με λίγες μόνο γραμμές κώδικα.

Τώρα, δοκιμάστε να πειραματιστείτε:  
- Αλλάξτε το `PdfSaveOptions` για ενσωμάτωση γραμματοσειρών (`setEmbedFullFonts(true)`).  
- Συνδυάστε πολλά αρχεία DOCX σε ένα ενιαίο PDF χρησιμοποιώντας `Document.appendDocument()`.  
- Εξερευνήστε άλλες μορφές εξόδου όπως XPS ή HTML χρησιμοποιώντας την ίδια μέθοδο `save`.

Έχετε ερωτήσεις σχετικά με τις ιδιαιτερότητες **μετατροπής word σε pdf** ή χρειάζεστε βοήθεια με κάποιο συγκεκριμένο σενάριο; Αφήστε ένα σχόλιο παρακάτω, και καλές προγραμματιστικές πρακτικές!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}