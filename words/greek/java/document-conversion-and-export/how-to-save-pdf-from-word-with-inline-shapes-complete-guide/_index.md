---
category: general
date: 2026-06-05
description: Πώς να αποθηκεύσετε PDF από ένα DOCX διατηρώντας τα αιωρούμενα σχήματα
  ως ενσωματωμένες ετικέτες. Μάθετε πώς να αποθηκεύετε το DOCX ως PDF, να μετατρέπετε
  το Word σε PDF και να εξάγετε τα σχήματα σωστά.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- save word pdf inline
language: el
og_description: Πώς να αποθηκεύσετε PDF από ένα έγγραφο Word ενώ εξάγετε τα αιωρούμενα
  σχήματα ως ενσωματωμένες ετικέτες. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να
  αποθηκεύσετε το docx ως pdf και να μετατρέψετε σωστά το Word σε pdf.
og_title: Πώς να αποθηκεύσετε PDF από το Word με ενσωματωμένα σχήματα – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  headline: How to Save PDF from Word with Inline Shapes – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  name: How to Save PDF from Word with Inline Shapes – Complete Guide
  steps:
  - name: Large Images
    text: 'If a floating shape contains a high‑resolution image, converting it to
      inline may cause the line height to expand dramatically. To keep the PDF tidy:'
  - name: Multiple Sections with Different Layouts
    text: 'When a document has sections with distinct page setups, you might need
      to apply the inline conversion only to a specific section:'
  - name: Converting Multiple DOCX Files in a Batch
    text: 'If you need to **convert word to pdf** for dozens of files, wrap the logic
      into a utility method:'
  - name: Expected Result
    text: Running the program should produce `inlineShapes.pdf`. Open it, and you’ll
      notice that any floating text boxes, callouts, or images now sit **inline**
      with the surrounding text, mirroring the layout you designed in Word.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF conversion
title: Πώς να αποθηκεύσετε PDF από το Word με ενσωματωμένα σχήματα – Πλήρης οδηγός
url: /el/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Αποθηκεύσετε PDF από το Word με Ενσωματωμένα Σχήματα – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να αποθηκεύσετε PDF** από ένα αρχείο Word χωρίς να χάσετε τη διάταξη των πλωτών εικόνων; Δεν είστε μόνοι. Σε πολλές εφαρμογές αναφοράς ή τιμολόγησης, αυτά τα πλωτά σχήματα—σκεφτείτε πλαίσια κειμένου, επεξηγήσεις ή διακοσμητικά εικονίδια—συχνά καταλήγουν σε λάθος θέση όταν απλώς κάνετε κλικ στο “Save As PDF.”  

Ευτυχώς, υπάρχει ένας καθαρός, προγραμματιστικός τρόπος να διατηρήσετε αυτά τα αντικείμενα ακριβώς εκεί που τα περιμένετε: ρυθμίστε την εξαγωγή PDF ώστε να μετατρέπει τα πλωτά σχήματα σε ετικέτες `<inline>`. Σε αυτόν τον οδηγό θα περάσουμε από **πώς να εξάγετε σχήματα**, **να αποθηκεύσετε docx ως pdf**, και **να μετατρέψετε word σε pdf** χρησιμοποιώντας λίγες γραμμές κώδικα Java. Στο τέλος, θα έχετε ένα έτοιμο‑για‑εκτέλεση απόσπασμα που παράγει ένα PDF με κάθε σχήμα αποδομένο ενσωματωμένα.

## Τι Θα Μάθετε

- Φορτώστε ένα αρχείο DOCX από δίσκο (ή οποιοδήποτε ρεύμα) με το Aspose.Words for Java.  
- Ενεργοποιήστε την επιλογή **save word pdf inline** ώστε τα πλωτά αντικείμενα να γίνουν ετικέτες inline.  
- Αποθηκεύστε το έγγραφο ως PDF χρησιμοποιώντας τις ρυθμισμένες `PdfSaveOptions`.  
- Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως μεγάλες εικόνες ή πολύπλοκοι πίνακες.  

Χωρίς εξωτερικά εργαλεία, χωρίς χειροκίνητη παρέμβαση στο UI του Word—απλώς καθαρός κώδικας που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java.

---

## Προαπαιτούμενα

Πριν βουτήξουμε, βεβαιωθείτε ότι έχετε:

| Απαίτηση | Γιατί είναι σημαντικό |
|----------|------------------------|
| **Java 17+** (ή οποιοδήποτε πρόσφατο JDK) | Το Aspose.Words for Java λειτουργεί σε σύγχρονα JDK. |
| **Aspose.Words for Java** βιβλιοθήκη (τελευταία έκδοση) | Παρέχει `Document`, `PdfSaveOptions` και τη μέθοδο `setExportFloatingShapesAsInlineTag`. |
| Ένα αρχείο **DOCX** που περιέχει πλωτά σχήματα (π.χ., ένα πλαίσιο κειμένου). | Χωρίς σχήματα δεν θα δείτε το αποτέλεσμα της ενσωματωμένης εξαγωγής. |
| Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) για τη διαχείριση των εξαρτήσεων. | Κάνει τη μεταγλώττιση άνετη. |

Αν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check for the latest version -->
</dependency>
```

---

## Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου

Το πρώτο πράγμα που χρειάζεστε είναι ένα αντικείμενο `Document` που αντιπροσωπεύει το αρχείο Word σας. Σκεφτείτε το ως τον καμβά που το Aspose.Words θα ζωγραφίσει αργότερα σε ένα PDF.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί είναι σημαντικό:* Η φόρτωση του αρχείου στη μνήμη σας δίνει πλήρη πρόσβαση στο μοντέλο αντικειμένων—παράγραφοι, runs, σχήματα, όλα. Αν η διαδρομή είναι λανθασμένη, θα λάβετε ένα `FileNotFoundException`, οπότε ελέγξτε ξανά ότι το αρχείο υπάρχει.

> **Συμβουλή:** Αν αντλείτε το DOCX από μια βάση δεδομένων ή μια υπηρεσία web, μπορείτε να χρησιμοποιήσετε τον κατασκευαστή `InputStream` αντί για διαδρομή αρχείου.

---

## Βήμα 2: Διαμόρφωση των Επιλογών Αποθήκευσης PDF για Εξαγωγή Πλωτών Σχημάτων ως Ετικέτες Inline

Από προεπιλογή, το Aspose.Words προσπαθεί να διατηρήσει τα πλωτά σχήματα πλωτά στο PDF, κάτι που μπορεί να προκαλέσει λανθασμένη ευθυγράμμιση όταν ο προβολέας PDF ερμηνεύει διαφορετικά τη διάταξη. Η κλάση `PdfSaveOptions` μας επιτρέπει να αλλάξουμε αυτή τη συμπεριφορά.

```java
// Step 2: Configure PDF save options to export floating shapes as <inline> tags
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

*Γιατί είναι σημαντικό:* Η ρύθμιση `setExportFloatingShapesAsInlineTag(true)` λέει στον εξαγωγέα να αντιμετωπίζει κάθε πλωτό σχήμα σαν να ήταν μέρος της γύρω παραγράφου. Το αποτέλεσμα είναι ένα PDF όπου το σχήμα κινείται μαζί με το κείμενο, εξαλείφοντας κενά ή επικαλυπτόμενα στοιχεία.

> **Κοινή ερώτηση:** *Τι γίνεται αν θέλω ακόμα κάποια σχήματα να παραμείνουν πλωτά;*  
> Μπορείτε να ορίσετε επιλεκτικά το `WrapType` των μεμονωμένων σχημάτων στο έγγραφο Word πριν από την εξαγωγή, ή να απενεργοποιήσετε τη μετατροπή σε inline για ολόκληρο το έγγραφο και να διαχειριστείτε αυτά τα σχήματα χειροκίνητα.

---

## Βήμα 3: Αποθήκευση του Εγγράφου ως PDF με τις Ρυθμισμένες Επιλογές

Τώρα που το έγγραφο είναι φορτωμένο και η συμπεριφορά εξαγωγής έχει ρυθμιστεί, ήρθε η ώρα να γράψετε το αρχείο PDF στο δίσκο.

```java
// Step 3: Save the document as a PDF with the configured options
doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);
```

*Γιατί είναι σημαντικό:* Η μέθοδος `save` παίρνει τόσο τη διαδρομή εξόδου όσο και το αντικείμενο `PdfSaveOptions`, διασφαλίζοντας ότι η ρύθμιση inline‑shape θα τηρηθεί. Αν παραλείψετε τις επιλογές, θα επιστρέψετε στην προεπιλεγμένη συμπεριφορά (τα πλωτά σχήματα παραμένουν πλωτά).

> **Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `inlineShapes.pdf` σε οποιονδήποτε προβολέα PDF. Όλα τα προηγούμενα πλωτά πλαίσια κειμένου ή εικόνες θα πρέπει τώρα να εμφανίζονται **inline** με το κείμενο της παραγράφου, διατηρώντας τη οπτική διάταξη που είδατε στο Word.

---

## Διαχείριση Ειδικών Περιπτώσεων και Παραλλαγών

### Μεγάλες Εικόνες

Αν ένα πλωτό σχήμα περιέχει εικόνα υψηλής ανάλυσης, η μετατροπή του σε inline μπορεί να προκαλέσει δραματική αύξηση του ύψους της γραμμής. Για να διατηρήσετε το PDF τακτοποιημένο:

```java
// Reduce image size before export (optional)
Shape shape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
shape.getImageData().setImageBytes(resizeImage(shape.getImageData().getImageBytes(), 800, 600));
```

*Εξήγηση:* Η αλλαγή μεγέθους της εικόνας μειώνει τις διαστάσεις της, αποτρέποντας υπερμεγέθη γραμμές στο τελικό PDF.

### Πολλαπλές Ενότητες με Διαφορετικές Διατάξεις

Όταν ένα έγγραφο έχει ενότητες με διαφορετικές ρυθμίσεις σελίδας, ίσως χρειαστεί να εφαρμόσετε τη μετατροπή σε inline μόνο σε συγκεκριμένη ενότητα:

```java
for (Section sec : doc.getSections()) {
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(sec.getPageSetup().getPaperSize() == PaperSize.A4);
    doc.save("section_" + sec.getId() + ".pdf", opts);
}
```

*Γιατί λειτουργεί:* Ο βρόχος δημιουργεί ξεχωριστό PDF ανά ενότητα, εφαρμόζοντας τη μετατροπή σε inline υπό όρους βάσει του μεγέθους του χαρτιού.

### Μετατροπή Πολλών Αρχείων DOCX σε Παρτίδα

Αν χρειάζεται να **convert word to pdf** για δεκάδες αρχεία, τυλίξτε τη λογική σε μια βοηθητική μέθοδο:

```java
public static void convertDocxToPdfInline(String inputPath, String outputPath) throws Exception {
    Document doc = new Document(inputPath);
    PdfSaveOptions options = new PdfSaveOptions();
    options.setExportFloatingShapesAsInlineTag(true);
    doc.save(outputPath, options);
}
```

Μπορείτε στη συνέχεια να καλέσετε αυτή τη μέθοδο μέσα σε ένα ρεύμα `Files.list(Paths.get("batch_folder"))`.

---

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα Συνδυασμένα)

Παρακάτω είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα Java που δείχνει **πώς να αποθηκεύσετε pdf** με ενσωματωμένα σχήματα από ένα αρχείο DOCX.

```java
import com.aspose.words.*;

public class InlineShapePdfExporter {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Set PDF options to export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF
            doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);

            System.out.println("PDF saved successfully with inline shapes!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### Αναμενόμενο Αποτέλεσμα

Η εκτέλεση του προγράμματος θα πρέπει να παράγει το `inlineShapes.pdf`. Ανοίξτε το και θα παρατηρήσετε ότι οποιαδήποτε πλωτά πλαίσια κειμένου, επεξηγήσεις ή εικόνες τώρα βρίσκονται **inline** με το κείμενο γύρω τους, αντικατοπτρίζοντας τη διάταξη που σχεδιάσατε στο Word.

---

## Συχνές Ερωτήσεις

| Ερώτηση | Απάντηση |
|----------|----------|
| **Λειτουργεί αυτό με αρχεία .doc;** | Ναι. Το Aspose.Words μπορεί να φορτώσει παλαιότερες μορφές `.doc`; οι ίδιες `PdfSaveOptions` ισχύουν. |
| **Μπορώ να κρατήσω κάποια σχήματα πλωτά;** | Θα χρειαστεί να προσαρμόσετε το `WrapType` του σχήματος σε `INLINE` χειροκίνητα πριν από την εξαγωγή, ή να εκτελέσετε δεύτερη εξαγωγή χωρίς τη σημαία inline για αυτές τις ενότητες. |
| **Υπάρχει κάποιος αντίκτυπος στην απόδοση;** | Το επιπλέον βήμα μετατροπής προσθέτει αμελητέο κόστος—συνήθως μερικά χιλιοστά του δευτερολέπτου ανά έγγραφο. |
| **Τι γίνεται με προστατευμένο με κωδικό DOCX;** | Φορτώστε το έγγραφο με `LoadOptions` που περιλαμβάνουν τον κωδικό, και συνεχίστε κανονικά. |
| **Θα λειτουργήσει αυτό σε Linux/macOS;** | Απολύτως. Το Aspose.Words for Java είναι ανεξάρτητο από την πλατφόρμα. |

---

## Επόμενα Βήματα & Σχετικά Θέματα

Τώρα που έχετε κατακτήσει **πώς να εξάγετε σχήματα** και **να αποθηκεύσετε docx ως pdf**, σκεφτείτε να εξερευνήσετε:

- **Στυλιζάρισμα PDF** – χρησιμοποιήστε `PdfSaveOptions.setCompliance(PdfCompliance.PDF_A_1_B)` για PDF αρχειοθέτησης.  
- **Προσθήκη Υδατογραφήματος** – εισάγετε αντικείμενα `Watermark` πριν την αποθήκευση.  
- **Μετατροπή σε άλλες μορφές** – δοκιμάστε `doc.save("output.html", SaveFormat.HTML)` για έξοδο έτοιμο για web.  
- **Επεξεργασία παρτίδας** – συνδυάστε τη βοηθητική μέθοδο με έναν χρονοπρογραμματιστή για αυτοματοποιημένες ροές εγγράφων.  

Κάθε ένα από αυτά βασίζεται στο θεμέλιο που μόλις θέσατε, επεκτείνοντας τη δυνατότητά σας να **convert word to pdf** με εξελιγμένους τρόπους.

---

## Συμπέρασμα

Καλύψαμε **πώς να αποθηκεύσετε pdf** από ένα έγγραφο Word διασφαλίζοντας ότι τα πλωτά σχήματα γίνονται ετικέτες inline, μια τεχνική που εξαλείφει τις εκπλήξεις διάταξης στο τελικό PDF. Φορτώνοντας το DOCX, διαμορφώνοντας τις `PdfSaveOptions` με `setExportFloatingShapesAsInlineTag(true)` και αποθηκεύοντας το αποτέλεσμα, λαμβάνετε μια καθαρή, αξιόπιστη μετατροπή—ιδανική για αναφορές, τιμολόγια ή οποιαδήποτε αυτοματοποιημένη ροή εγγράφων.

Δοκιμάστε το, προσαρμόστε τις επιλογές, και θα δείτε γρήγορα γιατί αυτή η προσέγγιση είναι η προτιμώμενη λύση για προγραμματιστές που χρειάζονται να **save word pdf inline** χωρίς προβλήματα. Καλή κωδικοποίηση, και τα PDF σας να φαίνονται πάντα ακριβώς όπως το θέλετε!

## Τι Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [aspose word to pdf – Μετατροπή DOCX σε PDF σε Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)
- [Πώς να Μετατρέψετε Word σε PDF Χρησιμοποιώντας το Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [αποθήκευση docx ως pdf με Aspose.Words – Πλήρης Οδηγός C#](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}