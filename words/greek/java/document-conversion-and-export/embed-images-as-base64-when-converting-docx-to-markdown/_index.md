---
category: general
date: 2026-05-26
description: Ενσωματώστε εικόνες ως base64 ενώ μετατρέπετε docx σε markdown με το
  Aspose.Words for Java. Μάθετε πώς να μετατρέπετε το Word σε markdown, να αποθηκεύετε
  το Word ως markdown και να διαχειρίζεστε εικόνες.
draft: false
keywords:
- embed images as base64
- convert docx to markdown
- convert word to markdown
- convert images to base64
- save word as markdown
language: el
og_description: Ενσωματώστε εικόνες σε μορφή base64 κατά τη μετατροπή του docx σε
  markdown με το Aspose.Words for Java. Πλήρης οδηγός για τη μετατροπή του Word σε
  markdown και την αποθήκευση του Word ως markdown.
og_title: Ενσωμάτωση εικόνων ως Base64 κατά τη μετατροπή DOCX σε Markdown
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  headline: Embed Images as Base64 When Converting DOCX to Markdown
  type: TechArticle
- description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  name: Embed Images as Base64 When Converting DOCX to Markdown
  steps:
  - name: 'H3: Why Use `setSaveToMemory(true)`?'
    text: 'When `saveToMemory` is true, Aspose writes the image bytes to a memory
      stream instead of a file. The Markdown exporter then converts that stream to
      a Base64 string and inserts it directly into the Markdown image tag:'
  - name: Troubleshooting Checklist
    text: '| Issue | Likely Cause | Fix | |-------|--------------|-----| | Image appears
      as a broken link | `setSaveToMemory` was omitted | Ensure `args.setSaveToMemory(true);`
      is inside the callback | | Base64 string is truncated | Output file encoding
      mismatch | Save the Markdown using UTF‑8 (default for Asp'
  - name: Convert Only Selected Images
    text: 'If you only want to embed certain images (e.g., those larger than 100 KB),
      add a size check:'
  - name: Use a Different Image Format
    text: The `ResourceSavingArgs` gives you the raw bytes, so you could re‑encode
      JPEGs as PNGs before embedding—useful when the target Markdown consumer prefers
      PNG.
  type: HowTo
tags:
- Aspose.Words
- Java
- Markdown
- Base64
title: Ενσωμάτωση εικόνων ως Base64 κατά τη μετατροπή DOCX σε Markdown
url: /el/java/document-conversion-and-export/embed-images-as-base64-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ενσωμάτωση Εικόνων ως Base64 Κατά τη Μετατροπή DOCX σε Markdown

Έχετε αναρωτηθεί ποτέ πώς να **ενσωματώσετε εικόνες ως base64** ενώ **μετατρέπετε docx σε markdown**; Δεν είστε ο μόνος—οι προγραμματιστές ρωτούν συνεχώς πώς να διατηρούν τις εικόνες ενσωματωμένες χωρίς να διαχειρίζονται ξεχωριστά αρχεία. Τα καλά νέα είναι ότι το Aspose.Words for Java το κάνει εύκολο: μπορείτε να μετατρέψετε ένα έγγραφο Word σε Markdown και να ενσωματώσετε αυτόματα κάθε εικόνα ως συμβολοσειρά Base64.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία—από τη φόρτωση ενός `.docx` που περιέχει εικόνες, στη ρύθμιση ενός callback `MarkdownSaveOptions` που κάνει τη βαριά δουλειά, και τέλος την αποθήκευση του αποτελέσματος ως καθαρό αρχείο `.md`. Στο τέλος θα ξέρετε ακριβώς πώς να **convert word to markdown**, **convert images to base64**, και **save word as markdown** χωρίς να αφήνετε ανεπιθύμητους φακέλους εικόνων. Χωρίς εξωτερικά εργαλεία, χωρίς χειροκίνητη επεξεργασία—απλός κώδικας Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε project.

## Τι Θα Χρειαστείτε

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK) – ο κώδικας χρησιμοποιεί σύνταξη lambda, αλλά μπορείτε να τον προσαρμόσετε σε παλαιότερες εκδόσεις.  
- **Aspose.Words for Java** βιβλιοθήκη (τελευταία έκδοση του 2026). Προσθέστε την εξάρτηση Maven ή το JAR στο classpath σας.  
- Ένα δείγμα **DOCX** αρχείου που περιέχει τουλάχιστον μία εικόνα.  
- Ένα IDE ή έναν απλό επεξεργαστή κειμένου—Visual Studio Code, IntelliJ IDEA, ή ακόμη και `vim` αρκούν.

Αν έχετε ήδη όλα αυτά, υπέροχα—ας ξεκινήσουμε αμέσως.

## Βήμα 1: Φόρτωση του Εγγράφου Word

Πρώτα δημιουργούμε μια παρουσία `Document` που δείχνει στο αρχείο προέλευσης. Αυτό είναι το ίδιο βήμα είτε **convert docx to markdown** είτε απλώς διαβάζετε το αρχείο για άλλους σκοπούς.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX that contains images
        Document doc = new Document("YOUR_DIRECTORY/doc-with-images.docx");
```

> **Why this matters:** Το αντικείμενο `Document` είναι το σημείο εισόδου για κάθε λειτουργία του Aspose. Κρατά όλη τη δομή του Word—συμπεριλαμβανομένων εικόνων, πινάκων και στυλ—ώστε το callback που θα ακολουθήσει να μπορεί να εξετάσει κάθε πόρο.

## Βήμα 2: Δημιουργία MarkdownSaveOptions και Καταχώρηση Callback Αποθήκευσης Πόρων

Η μαγεία βρίσκεται στο `MarkdownSaveOptions`. Συνδέοντας ένα `IResourceSavingCallback` αποκτούμε έλεγχο πάνω στο πώς γράφεται κάθε εξωτερικός πόρος (όπως μια εικόνα).

```java
        // Configure Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // Register the callback that will embed images as Base64
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // The callback fires for every resource Aspose wants to write
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Tell Aspose we don’t want a separate image file
                    args.setKeepResourceOriginalName(false);
                    // Give the image a predictable name (optional)
                    args.setResourceFileName("image_" + args.getResourceFileName());
                    // Force in‑memory saving – this triggers Base64 embedding
                    args.setSaveToMemory(true);
                }
            }
        });
```

### H3: Γιατί να Χρησιμοποιήσετε `setSaveToMemory(true)`;

Όταν το `saveToMemory` είναι true, το Aspose γράφει τα bytes της εικόνας σε ροή μνήμης αντί για αρχείο. Ο εξαγωγέας Markdown στη συνέχεια μετατρέπει αυτή τη ροή σε συμβολοσειρά Base64 και την ενσωματώνει απευθείας στην ετικέτα εικόνας του Markdown:

```markdown
![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Αυτό είναι το βασικό στοιχείο του **embed images as base64**.

## Βήμα 3: Αποθήκευση του Εγγράφου ως Markdown

Τώρα που το callback είναι σε θέση, το τελικό βήμα είναι απλώς η κλήση του `save`. Εδώ πραγματικά **convert word to markdown** και, λόγω του callback, επίσης **convert images to base64**.

```java
        // Save the document as Markdown – this triggers the callback
        doc.save("YOUR_DIRECTORY/out.md", mdOptions);
    }
}
```

> **Result:** Το `out.md` περιέχει κείμενο Markdown με κάθε εικόνα να αντιπροσωπεύεται ως `data:` URI. Δεν δημιουργούνται επιπλέον αρχεία εικόνας στο δίσκο, οπότε ο φάκελος παραμένει τακτοποιημένος.

## Βήμα 4: Επαλήθευση του Αποτελέσματος και Συνηθισμένα Προβλήματα

Ανοίξτε το παραγόμενο `out.md` σε οποιονδήποτε προβολέα Markdown (VS Code, GitHub, ή στατικό γεννήτρια ιστοτόπων). Θα πρέπει να δείτε κάτι σαν:

```markdown
# Sample Document

Here is an inline image:

![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

### Λίστα Ελέγχου Επίλυσης Προβλημάτων

| Πρόβλημα | Πιθανή Αιτία | Διόρθωση |
|----------|--------------|----------|
| Η εικόνα εμφανίζεται ως σπασμένος σύνδεσμος | `setSaveToMemory` παραλείφθηκε | Βεβαιωθείτε ότι το `args.setSaveToMemory(true);` βρίσκεται μέσα στο callback |
| Η συμβολοσειρά Base64 είναι κομμένη | Ασυμφωνία κωδικοποίησης αρχείου εξόδου | Αποθηκεύστε το Markdown χρησιμοποιώντας UTF‑8 (προεπιλογή για το Aspose) |
| Απρόσμενα ονόματα αρχείων | `setKeepResourceOriginalName(true)` | Θέστε το σε `false` για να επιβάλετε την προσαρμοσμένη λογική ονοματοδοσίας |

## Βήμα 5: Προχωρημένες Παραλλαγές (Προαιρετικό)

### Μετατροπή Μόνο Επιλεγμένων Εικόνων

Αν θέλετε να ενσωματώσετε μόνο ορισμένες εικόνες (π.χ. εκείνες μεγαλύτερες από 100 KB), προσθέστε έναν έλεγχο μεγέθους:

```java
if (args.getResourceType() == ResourceType.IMAGE) {
    if (args.getResourceData().length > 100_000) {
        args.setSaveToMemory(true);
    }
}
```

### Χρήση Διαφορετικής Μορφής Εικόνας

Το `ResourceSavingArgs` σας δίνει τα ακατέργαστα bytes, ώστε να μπορείτε να ξανακωδικοποιήσετε JPEG ως PNG πριν την ενσωμάτωση—χρήσιμο όταν ο καταναλωτής Markdown προτιμά PNG.

```java
if (args.getResourceFileName().endsWith(".jpg")) {
    // Convert JPEG bytes to PNG bytes (requires an image library)
    byte[] pngBytes = convertJpegToPng(args.getResourceData());
    args.setResourceData(pngBytes);
    args.setResourceFileName(args.getResourceFileName().replace(".jpg", ".png"));
    args.setSaveToMemory(true);
}
```

Αυτές οι προσαρμογές δείχνουν πόσο ευέλικτη είναι η προσέγγιση **embed images as base64** όταν **convert docx to markdown**.

## Συμπέρασμα

Μόλις μάθατε πώς να **ενσωματώσετε εικόνες ως base64** ενώ **μετατρέπετε docx σε markdown** χρησιμοποιώντας το Aspose.Words for Java. Συνδέοντας ένα απλό `IResourceSavingCallback`, η βιβλιοθήκη κάνει όλη τη βαριά δουλειά: **convert word to markdown**, **convert images to base64**, και τέλος **save word as markdown** με μία μόνο κλήση `save`.

Νιώστε ελεύθεροι να πειραματιστείτε—δοκιμάστε διαφορετικούς κανόνες φιλτραρίσματος εικόνων, μεταβείτε σε έξοδο HTML, ή συνδέστε αυτό το βήμα με μια στατική γεννήτρια ιστοτόπων. Το ίδιο μοτίβο λειτουργεί και για άλλες μορφές (HTML, EPUB), ώστε να μπορείτε να επαναχρησιμοποιήσετε το callback όπου χρειάζεστε ενσωματωμένους πόρους.

**Επόμενα βήματα:**  
- Εξερευνήστε το `HtmlSaveOptions` για HTML με εικόνες Base64.  
- Συνδυάστε το με μια CI pipeline για αυτοματοποίηση δημιουργίας τεκμηρίωσης.  
- Εμβαθύνετε στο `DocumentVisitor` του Aspose αν χρειάζεστε ακόμη πιο λεπτομερή έλεγχο της διαδικασίας μετατροπής.

Καλή προγραμματιστική δουλειά και απολαύστε τα καθαρά, αυτόνομα αρχεία Markdown σας!

## Σχετικά Μαθήματα

- [Πώς να Ενσωματώσετε Εικόνες σε Markdown Κατά τη Μετατροπή DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Μετατροπή docx σε markdown – Εξαγωγή Μαθηματικών Εξισώσεων σε LaTeX με Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Αποθήκευση Εικόνων από Word – Οδηγός Aspose.Words for Java](/words/english/java/document-loading-and-saving/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}