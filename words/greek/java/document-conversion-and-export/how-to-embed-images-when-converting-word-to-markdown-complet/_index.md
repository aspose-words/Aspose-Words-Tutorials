---
category: general
date: 2026-02-28
description: Μάθετε πώς να ενσωματώνετε εικόνες ενώ μετατρέπετε ένα έγγραφο σε markdown.
  Εξάγετε markdown με εικόνες και λάβετε ενσωματωμένες εικόνες στο markdown χρησιμοποιώντας
  Java.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: el
og_description: Ανακαλύψτε πώς να ενσωματώνετε εικόνες κατά τη μετατροπή ενός εγγράφου
  Word σε Markdown. Αυτός ο οδηγός σας δείχνει πώς να εξάγετε markdown με εικόνες
  και να τις διατηρήσετε ενσωματωμένες.
og_title: Πώς να ενσωματώσετε εικόνες κατά τη μετατροπή του Word σε Markdown
tags:
- markdown
- java
- Aspose.Words
- image handling
title: Πώς να ενσωματώσετε εικόνες κατά τη μετατροπή του Word σε Markdown – Πλήρης
  Οδηγός
url: /el/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ενσωματώσετε Εικόνες Κατά τη Μετατροπή Word σε Markdown – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να ενσωματώσετε εικόνες** σε ένα αρχείο Markdown που δημιουργείτε από ένα έγγραφο Word; Ίσως έχετε δοκιμάσει μια γρήγορη εξαγωγή, μόνο για να καταλήξετε με μια σειρά από κρέμαστα αρχεία εικόνας και σπασμένους συνδέσμους. Αυτό είναι ένα κοινό πρόβλημα—ιδιαίτερα όταν χρειάζεστε ένα μοναδικό, φορητό `.md` που μπορείτε να τοποθετήσετε σε έναν static‑site generator ή σε ένα GitHub README.

Τα καλά νέα; Μπορείτε να πείτε στον εξαγωγέα να ενσωματώνει κάθε εικόνα ως μια αλφαριθμητική συμβολοσειρά Base64, ώστε το παραγόμενο Markdown να είναι αυτόνομο. Σε αυτόν τον οδηγό θα περάσουμε βήμα προς βήμα, θα σας δείξουμε τον πλήρη κώδικα Java και θα εξηγήσουμε γιατί κάθε μέρος είναι σημαντικό. Στο τέλος θα μπορείτε να **μετατρέψετε doc σε markdown** με ενσωματωμένες εικόνες, και θα δείτε επίσης πώς να προσαρμόσετε τη διαδικασία για άλλες περιπτώσεις όπως “εξαγωγή markdown με εικόνες” ή “ενσωμάτωση εικόνων σε markdown”.

## Τι Θα Μάθετε

- Οι απαιτούμενες βιβλιοθήκες και μια ελάχιστη ρύθμιση έργου.  
- Πώς να διαμορφώσετε το `MarkdownSaveOptions` ώστε οι εικόνες να γίνουν Base64 data URIs.  
- Γιατί η χρήση ενός `ResourceSavingCallback` είναι ο πιο καθαρός τρόπος ελέγχου της διαχείρισης εικόνων.  
- Πώς να επαληθεύσετε ότι το αρχείο Markdown περιέχει πραγματικά τις ενσωματωμένες εικόνες.  
- Συμβουλές για ειδικές περιπτώσεις (μεγάλες εικόνες, διαφορετικοί τύποι MIME και ζητήματα απόδοσης).  

Δεν απαιτείται προηγούμενη εμπειρία με το Aspose.Words· ένα βασικό υπόβαθρο σε Java είναι αρκετό.

---

## Προαπαιτούμενα

Πριν βουτήξουμε στον κώδικα, βεβαιωθείτε ότι έχετε:

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | Το API Aspose.Words for Java στοχεύει σε Java 8+, αλλά η χρήση του τελευταίου JDK σας παρέχει τις ενσωματωμένες χρήσιμες λειτουργίες `Base64`. |
| **Aspose.Words for Java** (latest version) | Αυτή η βιβλιοθήκη παρέχει το `MarkdownSaveOptions` και την υποδομή callbacks που θα χρησιμοποιήσουμε. |
| **A Word document** (`.docx`) that contains at least one image | Χρειαζόμαστε κάτι για μετατροπή· το παράδειγμα υποθέτει ένα αρχείο με όνομα `sample.docx`. |
| **An IDE or text editor** (IntelliJ, VS Code, etc.) | Για γρήγορη μεταγλώττιση και εκτέλεση του δείγματος. |

Προσθέστε την εξάρτηση Aspose στο `pom.xml` (Maven) ή στο `build.gradle` (Gradle). Εδώ είναι το απόσπασμα Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Αν προτιμάτε Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Συμβουλή:** Η Aspose προσφέρει δωρεάν δοκιμαστική έκδοση 30 ημερών. Πάρτε ένα προσωρινό κλειδί άδειας και καταχωρίστε το νωρίς για να αποφύγετε μηνύματα υδατογραφήματος.

---

## Βήμα 1: Δημιουργία των Επιλογών Αποθήκευσης Markdown

Το πρώτο που κάνουμε είναι να δημιουργήσουμε ένα αντικείμενο `MarkdownSaveOptions`. Αυτό το αντικείμενο λέει στην Aspose πώς θέλουμε να συμπεριφέρεται η μετατροπή—διαχείριση γραμματοσειρών, μορφοποίηση λιστών και, το πιο σημαντικό για εμάς, διαχείριση εικόνων.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

Στην Java η σύνταξη είναι ίδια· απλώς αντικαταστήστε τη λέξη-κλειδί `csharp` με `java` στο επόμενο μπλοκ κώδικα.  
Γιατί είναι σημαντικό: χωρίς προσαρμογή των επιλογών, η Aspose θα γράψει κάθε εικόνα σε ξεχωριστό αρχείο δίπλα στο `.md`. Προετοιμάζοντας το αντικείμενο επιλογών τώρα, δημιουργούμε ένα σημείο παρέμβασης στην προεπιλεγμένη συμπεριφορά.

---

## Βήμα 2: Παρεμβολή Πόρων Εικόνας και Κωδικοποίηση σε Base64

Η Aspose ενεργοποιεί ένα callback κάθε φορά που θέλει να γράψει έναν πόρο (εικόνα, CSS κλπ.). Υλοποιώντας το `IResourceSavingCallback` μπορούμε να αποφασίσουμε τι θα κάνουμε με κάθε πόρο. Το παρακάτω απόσπασμα ελέγχει αν ο πόρος είναι εικόνα, καθαρίζει το όνομα αρχείου (ώστε να μην δημιουργηθεί εξωτερικό αρχείο), κωδικοποιεί τα δυαδικά δεδομένα σε Base64 και ορίζει τον κατάλληλο τύπο MIME.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**Τι συμβαίνει στο παρασκήνιο;**

1. **`args.getResourceType()`** – Η Aspose ταξινομεί κάθε εξωτερικό blob. Εμείς ενδιαφερόμαστε μόνο για `ResourceType.IMAGE`.  
2. **`args.setResourceFileName(null)`** – Ορίζοντας το όνομα αρχείου σε null λέμε στη βιβλιοθήκη *να μην* γράψει φυσικό αρχείο.  
3. **`Base64.getEncoder().encodeToString(...)`** – Ο ακατέργαστος πίνακας byte μετατρέπεται σε συμβολοσειρά κειμένου που μπορεί να τοποθετηθεί με ασφάλεια σε ένα Markdown data URI.  
4. **`args.setResourceContentType("image/png")`** – Αυτό εξασφαλίζει ότι η παραγόμενη ετικέτα Markdown θα είναι της μορφής `![alt](data:image/png;base64,…)`. Αν το πηγαίο έγγραφο περιέχει JPEG, μπορείτε να ελέγξετε τα αρχικά bytes και να επιλέξετε `"image/jpeg"`.

> **Γιατί Base64;**  
> Οι επεξεργαστές Markdown που καταλαβαίνουν data URIs θα εμφανίσουν την εικόνα άμεσα, και το παραγόμενο αρχείο παραμένει φορητό—χωρίς επιπλέον πόρους προς αντιγραφή. Είναι ιδιαίτερα χρήσιμο για GitHub READMEs ή ιστοσελίδες τεκμηρίωσης που απαγορεύουν εξωτερικούς πόρους.

---

## Βήμα 3: Εκτέλεση της Μετατροπής

Τώρα που οι επιλογές είναι έτοιμες, απλώς φορτώστε το έγγραφο Word και καλέστε `save`. Η διαδρομή που θα δώσετε θα είναι η θέση του παραγόμενου αρχείου Markdown.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

Αυτό είναι—δύο γραμμές κώδικα για τη μετατροπή. Η βαριά δουλειά (ανάγνωση του DOCX, εξαγωγή εικόνων, μετατροπή παραγράφων) γίνεται εξ ολοκλήρου από την Aspose.

---

## Βήμα 4: Επαλήθευση του Αποτελέσματος – Εμφάνιση Ενσωματωμένων Εικόνων

Ανοίξτε το `output/doc.md` σε οποιονδήποτε επεξεργαστή κειμένου. Θα πρέπει να δείτε κάτι όπως:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Αν επικολλήσετε το Markdown σε έναν προβολέα που υποστηρίζει data URIs (GitHub, προεπισκόπηση VS Code ή static‑site generator), η εικόνα θα εμφανιστεί χωρίς επιπλέον αρχεία.

**Γρήγορος έλεγχος λογικής**:  

- **Αναζητήστε `data:image/`** – Αν βρείτε μερικές μακριές συμβολοσειρές, η ενσωμάτωση λειτούργησε.  
- **Μετρήστε τα μοτίβα `![](`** – Θα πρέπει να ταιριάζουν με τον αριθμό των εικόνων στο αρχικό αρχείο Word.

---

## Διαχείριση Ειδικών Περιπτώσεων

### Μεγάλες Εικόνες

Το Base64 αυξάνει το αρχικό μέγεθος περίπου **33 %**. Για πολύ μεγάλες εικόνες (π.χ. φωτογραφίες υψηλής ανάλυσης), το αρχείο Markdown μπορεί να γίνει δύσκολο στη διαχείριση. Σκεφτείτε τις παρακάτω στρατηγικές:

| Strategy | When to use |
|----------|--------------|
| **Resize before conversion** – Use `java.awt.Image` to scale down. | Όταν το πηγαίο έγγραφο περιέχει πόρους υψηλής ανάλυσης που δεν χρειάζονται σε πλήρη μέγεθος. |
| **Switch to JPEG** – Change `args.setResourceContentType("image/jpeg")`. | Για φωτογραφίες όπου η απώλεια‑απώλεια μορφή PNG είναι υπερβολική. |
| **Chunk the document** – Split the Word file into sections and export each separately. | Όταν χρειάζεται να διατηρήσετε το αρχείο Markdown κάτω από ένα συγκεκριμένο όριο μεγέθους (π.χ. το όριο των 10 MB του GitHub). |

### Μη‑PNG Εικόνες

Αν το έγγραφο Word περιέχει μικτά φορμά, μπορείτε να ανιχνεύσετε δυναμικά τον τύπο MIME:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Η Aspose ήδη γεμίζει το `ResourceContentType`, οπότε συχνά δεν χρειάζεται να κωδικοποιήσετε σκληρά το `"image/png"`.

### Συμβουλές Απόδοσης

- **Επαναχρησιμοποίηση μιας μόνο εμφάνισης `Base64.Encoder`** εάν μετατρέπετε πολλές εικόνες σε βρόχο.  
- **Ενεργοποίηση `markdownSaveOptions.setExportImagesAsBase64(true)`** (αν η έκδοση του API το υποστηρίζει) για να αποφύγετε εντελώς το callback.  
- **Εκτέλεση της μετατροπής σε νήμα παρασκηνίου** όταν επεξεργάζεστε μαζικά έγγραφα σε περιβάλλον διακομιστή.

---

## Πλήρες Παράδειγμα Εργασίας (Όλα Μαζί)

Παρακάτω είναι ένα έτοιμο για αντιγραφή‑επικόλληση πρόγραμμα Java που περιλαμβάνει εισαγωγές, διαχείριση σφαλμάτων και τη πλήρη ροή που συζητήσαμε.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα**: ένα μοναδικό αρχείο `doc.md` που περιέχει ενσωματωμένες εικόνες Base64, έτοιμο για οποιοδήποτε εργαλείο που υποστηρίζει Markdown.

---

## Συχνές Ερωτήσεις

**Q1: Λειτουργεί αυτό με παλαιότερες εκδόσεις του Aspose.Words;**  
*Συνήθως ναι.* Το API callbacks είναι σταθερό από την έκδοση 19. Ωστόσο, η συντόμευση `setExportImagesAsBase64` εμφανίστηκε σε μεταγενέστερες εκδόσεις, έτσι αν χρησιμοποιείτε παλαιότερη έκδοση θα χρειαστείτε το ρητό callback που φαίνεται παραπάνω.

**Q2: Τι γίνεται αν χρειαστεί να εξάγω σε GitHub Flavored Markdown (GFM);**  
Το `MarkdownSaveOptions` της Aspose ήδη παράγει σύνταξη συμβατή με GFM. Το μόνο επιπλέον βήμα είναι να βεβαιωθείτε ότι η μηχανή απόδοσης του αποθετηρίου σας υποστηρίζει data URIs—το GitHub το κάνει.

**Q3: Μπορώ να χρησιμοποιήσω αυτήν την προσέγγιση για άλλες μορφές, όπως HTML;**  
Απολύτως. Το ίδιο `ResourceSavingCallback` λειτουργεί για `HtmlSaveOptions`. Απλώς αλλάξτε την κλάση επιλογών και διατηρήστε τη λογική Base64.

## 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}