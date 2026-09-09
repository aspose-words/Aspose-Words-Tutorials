---
category: general
date: 2026-01-11
description: Μάθετε πώς να ενσωματώνετε εικόνες στο Markdown κατά τη μετατροπή ενός
  αρχείου DOCX, χρησιμοποιώντας Base64 για μικρές εικόνες και αποθηκεύοντας μεγαλύτερους
  πόρους ξεχωριστά.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: el
og_description: Μάθετε πώς να ενσωματώνετε εικόνες σε Markdown κατά τη μετατροπή ενός
  αρχείου DOCX, χρησιμοποιώντας Base64 για μικρές εικόνες και αποθηκεύοντας μεγαλύτερους
  πόρους ξεχωριστά.
og_title: Πώς να ενσωματώσετε εικόνες στο Markdown κατά τη μετατροπή DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: Πώς να ενσωματώσετε εικόνες στο Markdown κατά τη μετατροπή DOCX
url: /el/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ενσωματώσετε Εικόνες σε Markdown Κατά τη Μετατροπή DOCX

Έχετε αναρωτηθεί ποτέ **πώς να ενσωματώσετε εικόνες** σε ένα αρχείο Markdown που προέρχεται από ένα έγγραφο Word; Δεν είστε μόνοι. Οι περισσότεροι προγραμματιστές αντιμετωπίζουν πρόβλημα όταν η μετατροπή αφαιρεί τις εικόνες ή τις αποθηκεύει με τρόπο που διασπά τη τελική διάταξη.  

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει **πώς να ενσωματώσετε εικόνες** ως Base64 data URIs για μικρά γραφικά, ενώ τα μεγαλύτερα περιουσιακά στοιχεία γράφονται σε έναν φάκελο στο πλάι. Κατά τη διάρκεια, θα καλύψουμε επίσης **convert docx to markdown**, θα αναφέρουμε **how to convert docx** με το Aspose.Words, και θα εξηγήσουμε τη διαφορά μεταξύ ενσωμάτωσης εικόνων ως Base64 και εξαγωγής τους ως ξεχωριστά αρχεία.  

> **Pro tip:** Αν χρειάζεστε μόνο μια γρήγορη απόδειξη‑ενός‑ενός, ο κώδικας παρακάτω λειτουργεί αμέσως με μια μόνο εξάρτηση Maven.

---

## Τι Θα Χρειαστείτε

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK) – το API είναι προσανατολισμένο στη Java, αλλά οι έννοιες μεταφράζονται σε άλλες γλώσσες.
- **Aspose.Words for Java** – μια εμπορική βιβλιοθήκη που υποστηρίζει τη μετατροπή DOCX → Markdown.
- Ένα **sample DOCX** που περιέχει ένα μείγμα μικρών εικονιδίων και μεγαλύτερων φωτογραφιών.
- Ένα φάκελο όπου θέλετε να αποθηκευτεί το Markdown και οι πόροι του.

Καμία πρόσθετη πλατφόρμα, κανένα εξωτερικό script. Απλώς καθαρή Java και Aspose.Words.

## Βήμα 1 – Προσθήκη Aspose.Words στο Έργο Σας (convert docx to markdown)

Αν χρησιμοποιείτε Maven, προσθέστε το παρακάτω απόσπασμα στο `pom.xml` σας. Μπορείτε να αντικαταστήσετε την έκδοση με την πιο πρόσφατη έκδοση τη στιγμή της ανάγνωσης.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Why this matters:** Το Aspose.Words αναλαμβάνει το βαριά έργο της ανάλυσης της δομής DOCX, εξαγωγής εικόνων και δημιουργίας σύνταξης Markdown. Η προσπάθεια να φτιάξετε τον δικό σας parser θα ήταν μια ατελείωτη διαδικασία που πιθανώς δεν χρειάζεται να ακολουθήσετε.

## Βήμα 2 – Φόρτωση του Πηγαίου Εγγράφου DOCX

Πρώτα, δείξτε το API στο αρχείο Word που θέλετε να μετατρέψετε. Ο κατασκευαστής `Document` κάνει όλη τη δουλειά — δεν απαιτείται χειροκίνητη ανάλυση XML.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Παρατηρήστε ότι το σχόλιο εξηγεί *γιατί* αυτή η γραμμή είναι κρίσιμη: χωρίς ένα αντικείμενο `Document` δεν υπάρχει τίποτα για μετατροπή.

## Βήμα 3 – Προετοιμασία MarkdownSaveOptions με Callback Αποθήκευσης Πόρων

Αυτό είναι η καρδιά του **how to embed images** σωστά. Το callback σας παρέχει ένα σημείο προσάρτησης για κάθε πόρο (εικόνα, στυλ κ.λπ.) που ο μετατροπέας θέλει να γράψει.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Γιατί ένα callback;

- **Control:** Εσείς αποφασίζετε αν μια εικόνα γίνεται μια ενσωματωμένη Base64 συμβολοσειρά ή ξεχωριστό αρχείο.
- **Performance:** Τα μικρά εικονίδια γίνονται μέρος του Markdown, εξαλείφοντας επιπλέον αιτήματα HTTP.
- **Portability:** Οι μεγαλύτερες εικόνες παραμένουν ως εξωτερικά αρχεία, διατηρώντας το μέγεθος του Markdown λογικό.

## Βήμα 4 – Αποθήκευση του Εγγράφου ως Markdown

Τέλος, πείτε στο Aspose.Words να γράψει το αρχείο Markdown χρησιμοποιώντας τις επιλογές που μόλις διαμορφώσαμε.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Η εκτέλεση του προγράμματος παράγει δύο πράγματα:

1. `output.md` – η αναπαράσταση Markdown του αρχικού DOCX.
2. Ένας φάκελος `markdown_resources` που περιέχει τυχόν μεγάλες εικόνες που δεν ενσωματώθηκαν.

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα σε Ένα Σημείο)

Ακολουθεί το πλήρες αρχείο πηγαίου κώδικα, έτοιμο για αντιγραφή‑επικόλληση στο IDE σας. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή στο μηχάνημά σας.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `output.md` σε οποιονδήποτε προβολέα Markdown. Τα μικρά εικονίδια εμφανίζονται ενσωματωμένα, π.χ.:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Οι μεγαλύτερες εικόνες αναφέρονται ως εξής:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

Αυτό είναι ακριβώς ό,τι χρειάζεστε για **embed images** ενώ διατηρείτε το μέγεθος του αρχείου διαχειρίσιμο.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν μια εικόνα είναι JPEG αντί για PNG;

Το παραπάνω callback πάντα προσθέτει πρόθεμα `image/png` στο URI. Για JPEGs, μπορείτε να εξετάσετε τα πρώτα μερικά byte του `args.getData()` ή να χρησιμοποιήσετε το `args.getFileName()` για να υποθέσετε τον σωστό τύπο MIME:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Μπορώ να αλλάξω το όριο μεγέθους;

Απολύτως. Το όριο των `10_000` byte είναι μόνο ένα παράδειγμα. Αν έχετε άφθονο προϋπολογισμό εύρους ζώνης, αυξήστε το σε 50 KB ή περισσότερο. Αντίστροφα, μειώστε το αν χρειάζεστε εξαιρετικά ελαφριά αρχεία Markdown.

### Λειτουργεί αυτό με πίνακες ή άλλα αντικείμενα Word;

Ναι. Το Aspose.Words μετατρέπει αυτόματα πίνακες, λίστες και ακόμη και υποσημειώσεις σε Markdown. Το callback πόρων παρεμβάλλεται μόνο στις εικόνες, οπότε δεν χρειάζεστε επιπλέον κώδικα για άλλα στοιχεία.

### Τι γίνεται με ονόματα αρχείων που δεν είναι ASCII;

Το API κωδικοποιεί με ασφάλεια ονόματα αρχείων Unicode όταν γράφει στον φάκελο `markdown_resources`. Απλώς βεβαιωθείτε ότι το σύστημα αρχείων σας υποστηρίζει UTF‑8 (τα περισσότερα σύγχρονα λειτουργικά συστήματα το κάνουν).

## Συμβουλές Pro για Ομαλή Μετατροπή

- **Keep the output folder clean.** Εκτελέστε `Files.createDirectories` μόνο μία φορά ανά μετατροπή, ή διαγράψτε το φάκελο πριν από κάθε εκτέλεση αν θέλετε μια φρέσκια αρχή.
- **Validate the Markdown.** Εργαλεία όπως το `markdownlint` μπορούν να εντοπίσουν αχρείαστους χαρακτήρες που εισάγονται από κακοδιατυπωμένες Base64 συμβολοσειρές.
- **Version lock Aspose.Words.** Μια συγκεκριμένη έκδοση εξασφαλίζει ότι ο κώδικάς σας θα συνεχίσει να λειτουργεί ακόμη και μετά από μια σημαντική έκδοση που αλλάζει τη προεπιλεγμένη συμπεριφορά.
- **Use a .gitignore** entry for `markdown_resources/

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}