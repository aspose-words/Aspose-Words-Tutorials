---
category: general
date: 2026-07-03
description: Εξαγωγή πλωτών σχημάτων ενσωματωμένα κατά τη μετατροπή του Word σε PDF.
  Μάθετε πώς να ορίζετε επιλογές PDF και να αποθηκεύετε το Word ως PDF με επιλογές
  στην Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: el
og_description: Εξαγωγή πλωτών σχημάτων ενσωματωμένα όταν μετατρέπετε ένα έγγραφο
  Word σε PDF. Αυτό το σεμινάριο δείχνει πώς να ορίσετε τις επιλογές PDF και να αποθηκεύσετε
  το Word ως PDF.
og_title: Εξαγωγή Πλωτών Σχημάτων Ενσωματωμένα – Οδηγός Μετατροπής PDF σε Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Εξαγωγή πλωτών σχημάτων ενσωματωμένα – Πλήρης οδηγός μετατροπής σε PDF
url: /el/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή Πλωτών Σχημάτων Inline – Πλήρης Οδηγός για Μετατροπή σε PDF

Έχετε ποτέ χρειαστεί να **εξάγετε πλωτά σχήματα inline** όταν μετατρέπετε ένα έγγραφο Word σε PDF; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν τα διαγράμματα ή τα εικονίδια τους μετατοπίζονται μυστηριωδώς σε ξεχωριστά επίπεδα. Τα καλά νέα είναι ότι μια μόνο επιλογή PDF μπορεί να κρατήσει αυτά τα σχήματα στενά μέσα σε ετικέτες `<span>`, διατηρώντας τη διάταξη ακριβώς όπως τη βλέπετε στο Word.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από **πώς να ορίσετε επιλογές PDF** σε Java, θα σας δείξουμε τον ακριβή κώδικα για **αποθήκευση Word ως PDF options**, και θα εξηγήσουμε γιατί μπορεί να θέλετε να **μετατρέψετε Word σε PDF inline** αντί για την προεπιλεγμένη εξαγωγή σε επίπεδο block. Στο τέλος, θα έχετε ένα έτοιμο‑για‑εκτέλεση snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

## Τι Θα Μάθετε

- Η διαφορά μεταξύ εξαγωγής inline `<span>` και block `<div>` για πλωτά σχήματα.  
- Πώς να διαμορφώσετε το `PdfSaveOptions` για να επιβάλλετε την inline απόδοση.  
- Κώδικας βήμα‑βήμα που φορτώνει ένα `.docx`, εφαρμόζει την επιλογή και γράφει ένα PDF.  
- Κοινές παγίδες (έλλειψη γραμματοσειρών, μη υποστηριζόμενα σχήματα) και πώς να τις αποφύγετε.  
- Συμβουλές για δοκιμή του αποτελέσματος και επέκταση της προσέγγισης σε άλλα στοιχεία του εγγράφου.

**Προαπαιτούμενα** – θα χρειαστείτε Java 8 ή νεότερη, τη βιβλιοθήκη Aspose.Words for Java (ή οποιοδήποτε API που αντικατοπτρίζει την κλάση `PdfSaveOptions`), και ένα δείγμα αρχείου Word με πλωτά σχήματα (το tutorial χρησιμοποιεί το `FloatingShapes.docx`). Δεν απαιτούνται άλλα εξωτερικά εργαλεία.

---

## Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου Word

Το πρώτο που κάνετε είναι να ανοίξετε το `.docx` που θέλετε να μετατρέψετε. Αυτό είναι απλό, αλλά βεβαιωθείτε ότι η διαδρομή είναι απόλυτη ή ότι επιλύεται σωστά από το classpath σας.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Γιατί αυτό είναι σημαντικό:*  
Αν το έγγραφο δεν φορτωθεί σωστά, η επακόλουθη μετατροπή σε PDF θα ρίξει ένα `FileNotFoundException`. Η χρήση του `Document` εξασφαλίζει ότι το εσωτερικό μοντέλο αντικειμένων είναι πλήρως γεμάτο, συμπεριλαμβανομένων τυχόν πλωτών σχημάτων που υπάρχουν στη σελίδα.

## Βήμα 2: Δημιουργία PDF Save Options και Ορισμός Πλωτών Σχημάτων σε Inline

Εδώ συμβαίνει η μαγεία. Από προεπιλογή, το Aspose.Words εξάγει πλωτά σχήματα ως στοιχεία block‑level `<div>`, τα οποία μπορούν να διακόψουν τη ροή σε PDF βασισμένα σε HTML. Ορίζοντας `setExportFloatingShapesAsInlineTag(true)` λέτε στη μηχανή να τυλίγει κάθε σχήμα σε ένα inline `<span>`.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Γιατί αυτό είναι σημαντικό:*  
- **Ακρίβεια διάταξης** – Τα inline tags διατηρούν το σχήμα ευθυγραμμισμένο με το κείμενο γύρω, αποφεύγοντας ανεπιθύμητα κενά.  
- **Αναζητησιμότητα** – Τα inline στοιχεία είναι πιο πιθανό να ευρετηριαστούν σωστά από τους αναγνώστες PDF.  
- **Έλεγχος στυλ** – Μπορείτε να στοχεύσετε το `<span>` με CSS αν αργότερα μετατρέψετε το PDF ξανά σε HTML.

> **Συμβουλή:** Αν ποτέ χρειαστείτε την παλιά συμπεριφορά block για ένα συγκεκριμένο έγγραφο, απλώς περάστε `false` ή παραλείψτε την κλήση εντελώς.

## Βήμα 3: Αποθήκευση του Εγγράφου ως PDF Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Τώρα συνδυάζετε το φορτωμένο `Document` με το `PdfSaveOptions` και γράφετε το αρχείο. Αυτή η μονή γραμμή κάνει τη βαριά δουλειά.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Γιατί αυτό είναι σημαντικό:*  
Η μέθοδος `save` σέβεται κάθε σημαία που έχετε ορίσει στο `pdfOptions`. Αν ξεχάσετε να περάσετε τις επιλογές, θα επανέλθει στην προεπιλεγμένη εξαγωγή block, καταστρέφοντας τον σκοπό του **export floating shapes inline**.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα μαζί, εδώ είναι ένα συμπαγές πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε αμέσως. Αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή στο μηχάνημά σας.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα** – Μετά την εκτέλεση του προγράμματος, ανοίξτε το `FloatingShapes.pdf`. Θα πρέπει να δείτε τα σχήματα να είναι ενσωματωμένα με το κείμενο, χωρίς επιπλέον λευκό χώρο, και η HTML αναπαράσταση (αν εξετάσετε τη εσωτερική δομή του PDF) θα περιέχει ετικέτες `<span>` γύρω από κάθε σχήμα.

![Παράδειγμα εξαγωγής πλωτών σχημάτων inline](https://example.com/export-inline.png "Στιγμιότυπο οθόνης που δείχνει πλωτά σχήματα αποδομένα inline στο PDF")

*Κείμενο alt εικόνας:* **export floating shapes inline** στιγμιότυπο PDF με inline σχήματα.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### 1. “Τι γίνεται αν το έγγραφό μου περιέχει πολύπλοκο SmartArt;”

Το SmartArt αντιμετωπίζεται ως αντικείμενο σχεδίασης. Η σημαία inline λειτουργεί για τα περισσότερα διανυσματικά σχήματα, αλλά πολύ πολύπλοκο SmartArt μπορεί ακόμη να αποδοθεί ως εικόνα. Σε αυτές τις περιπτώσεις, σκεφτείτε να επίπεδοποιήσετε το SmartArt στο Word πριν τη μετατροπή, ή χρησιμοποιήστε `pdfOptions.setExportSmartArtAsImage(true)` για να εξαναγκάσετε την εξαγωγή ως εικόνα.

### 2. “Μπορώ να συνδυάσω εξαγωγές inline και block στο ίδιο έγγραφο;”

Δυστυχώς, το API εφαρμόζει τη ρύθμιση παγκοσμίως. Αν χρειάζεστε μικτή συμπεριφορά, χωρίστε το έγγραφο σε ενότητες, εξάγετε κάθε ενότητα ξεχωριστά με διαφορετικές επιλογές, και στη συνέχεια συγχωνεύστε τα PDF χρησιμοποιώντας το `PdfMerger`.

### 3. “Επηρεάζει αυτό την ενσωμάτωση γραμματοσειρών;”

Όχι. Η ενσωμάτωση γραμματοσειρών ελέγχεται από το `pdfOptions.setEmbedFullFonts(true)` (προεπιλογή). Μπορείτε με ασφάλεια να το ενεργοποιήσετε ή να το απενεργοποιήσετε χωρίς να επηρεάσετε τη σημαία inline shape.

### 4. “Πώς μπορώ να επαληθεύσω ότι τα σχήματα είναι πραγματικά `<span>`;”

Ανοίξτε το παραγόμενο PDF σε ένα εργαλείο όπως **PDF.js** ή **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Θα δείτε το σχήμα τυλιγμένο σε ένα στοιχείο `<span>` στο υποκείμενο XML. Αν δείτε `<div>`, η επιλογή δεν εφαρμόστηκε.

## Επέκταση της Προσέγγισης – Σχετικές Επιλογές

Ενώ βρίσκεστε εδώ, ίσως θέλετε επίσης να εξερευνήσετε άλλες ρυθμίσεις μετατροπής PDF:

| Επιλογή | Τι κάνει | Τυπική χρήση |
|--------|--------------|------------------|
| `setCompressImages(true)` | Μειώνει το μέγεθος των εικόνων | Γρηγορότερο κατέβασμα |
| `setUseHighQualityRendering(true)` | Βελτιώνει την απόδοση διανυσματικών στοιχείων | PDF έτοιμα για εκτύπωση |
| `setExportDocumentStructure(true)` | Προσθέτει δομικές ετικέτες για προσβασιμότητα | Συμμόρφωση με WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Ορίζει ρητά τη μορφή (σπάνια χρειάζεται) | Διαδικασίες πολλαπλών μορφών |

Αυτές οι ρυθμίσεις ταιριάζουν καλά με σενάρια **convert word to pdf inline** όπου χρειάζεστε τόσο ακρίβεια διάταξης όσο και απόδοση.

## Δοκιμή της Μετατροπής Σας

1. **Οπτικός έλεγχος** – Ανοίξτε το PDF σε δύο προβολείς (Chrome και Adobe Reader) για να βεβαιωθείτε ότι τα σχήματα ευθυγραμμίζονται.  
2. **Αυτοματοποιημένη σύγκριση** – Χρησιμοποιήστε μια βιβλιοθήκη όπως `pdfbox` για να εξάγετε το XML και να ελέγξετε την παρουσία ετικετών `<span>`.  
3. **Δοκιμή απόδοσης** – Μετρήστε τον χρόνο που απαιτείται με και χωρίς το `setCompressImages` για να δείτε την ανταλλαγή.

Ένα γρήγορο παράδειγμα JUnit:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

## Συμπέρασμα

Τώρα έχετε μια σταθερή, ολοκληρωμένη λύση για **export floating shapes inline** όταν **convert Word to PDF inline**. Με τη διαμόρφωση του `PdfSaveOptions` ελέγχετε την ετικέτα HTML που χρησιμοποιείται για κάθε σχήμα, διατηρώντας τα PDF σας τακτοποιημένα και αναζητήσιμα. Θυμηθείτε να δοκιμάζετε το αποτέλεσμα, να προσαρμόζετε σχετικές επιλογές όπως η συμπίεση εικόνων, και να αντιμετωπίζετε ακραίες περιπτώσεις όπως πολύπλοκο SmartArt.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να εφαρμόσετε την ίδια τεχνική για **export floating tables inline** ή πειραματιστείτε με PDF με στυλ CSS χρησιμοποιώντας το `HtmlSaveOptions` της Aspose. Το ίδιο μοτίβο—φόρτωση, διαμόρφωση, αποθήκευση—ισχύει για σχεδόν κάθε σενάριο μετατροπής εγγράφου σε PDF.

Έχετε περισσότερες ερωτήσεις σχετικά με **how to set pdf options** ή χρειάζεστε βοήθεια με **save word as pdf options** για μια διαφορετική βιβλιοθήκη; Αφήστε ένα σχόλιο, και καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}