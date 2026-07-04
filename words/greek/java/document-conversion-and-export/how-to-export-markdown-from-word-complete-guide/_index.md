---
category: general
date: 2026-04-28
description: Πώς να εξάγετε markdown από αρχείο DOCX και να εξάγετε εικόνες. Μάθετε
  πώς να μετατρέπετε το docx σε markdown, να τοποθετείτε τις εικόνες σε φάκελο και
  να αποθηκεύετε το Word ως markdown.
draft: false
keywords:
- how to export markdown
- convert docx to markdown
- extract images from docx
- how to place images
- save word as markdown
language: el
og_description: Πώς να εξάγετε markdown από αρχείο DOCX σε Java. Αυτό το σεμινάριο
  σας δείχνει πώς να μετατρέψετε το docx σε markdown, να εξάγετε εικόνες και να τις
  οργανώσετε.
og_title: Πώς να εξάγετε Markdown από το Word – Πλήρης οδηγός
tags:
- Aspose.Words
- Java
- Markdown
- Document Conversion
title: Πώς να εξάγετε Markdown από το Word – Πλήρης οδηγός
url: /el/java/document-conversion-and-export/how-to-export-markdown-from-word-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εξάγετε Markdown από το Word – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να εξάγετε markdown** από ένα έγγραφο Word χωρίς να χάσετε καμία από τις ενσωματωμένες εικόνες; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν χρειάζονται ένα καθαρό αρχείο Markdown και έναν τακτοποιημένο φάκελο εικόνων για static‑site generators, ιστοσελίδες τεκμηρίωσης ή αρχεία README στο GitHub.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς διαδικασίες για **μετατροπή docx σε markdown**, εξαγωγή κάθε εικόνας από την πηγή, και **τοποθέτηση εικόνων** σε έναν υπο‑φάκελο `img` ώστε οι αναφορές στο παραγόμενο Markdown να παραμείνουν ακριβείς. Στο τέλος θα έχετε ένα έτοιμο προς δημοσίευση `output.md` μαζί με έναν φάκελο `img`—χωρίς να χρειάζεται χειροκίνητη αντιγραφή‑επικόλληση.

> **Τι θα πάρετε:** ένα εκτελέσιμο απόσπασμα Java χρησιμοποιώντας το Aspose.Words, μια σαφή εξήγηση του γιατί κάθε γραμμή είναι σημαντική, και συμβουλές για την αντιμετώπιση ειδικών περιπτώσεων όπως εικόνες SVG ή μεγάλα δυαδικά αρχεία.  

*Προαπαιτούμενα:* Java 8+ εγκατεστημένη, ένα IDE (IntelliJ IDEA, Eclipse ή VS Code), και μια έγκυρη άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί καλά για πειραματισμό).

---

## Πώς να Εξάγετε Markdown από Έγγραφο Word

### Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου  

Πριν μπορέσει να γίνει οποιαδήποτε μετατροπή, πρέπει να φορτώσουμε το αρχείο DOCX στη μνήμη. Το Aspose.Words αντιπροσωπεύει ένα αρχείο Word με την κλάση `Document`.  

```java
import com.aspose.words.Document;
import com.aspose.words.License;

// Load your license (optional for trial)
License license = new License();
license.setLicense("Aspose.Words.Java.lic");

// Step 1 – read the .docx file
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί είναι σημαντικό:* Η φόρτωση του αρχείου επικυρώνει τη μορφή του και μας δίνει πρόσβαση στο δέντρο του εγγράφου (παράγραφοι, runs, εικόνες). Αν το αρχείο είναι κατεστραμμένο, το Aspose θα ρίξει μια σαφή εξαίρεση, εξοικονομώντας πολύ χρόνο εντοπισμού σφαλμάτων αργότερα.

### Μετατροπή DOCX σε Markdown – Ρύθμιση των Επιλογών  

Το αντικείμενο `MarkdownSaveOptions` λέει στο Aspose πώς να σειριοποιήσει το έγγραφο. Η προεπιλεγμένη συμπεριφορά γράφει συνδέσμους εικόνων που δείχνουν στον ίδιο φάκελο με το αρχείο Markdown. Θα το αλλάξουμε στο επόμενο βήμα.

```java
import com.aspose.words.MarkdownSaveOptions;
import com.aspose.words.ResourceSavingArgs;
import com.aspose.words.IResourceSavingCallback;
import com.aspose.words.ResourceType;

// Step 2 – configure Markdown export
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

*Pro tip:* Αν χρειάζεστε GitHub‑flavored Markdown, ορίστε `mdOptions.setExportImagesAsBase64(false);` για να κρατήσετε τις εικόνες ως ξεχωριστά αρχεία αντί για ενσωμάτωση ως data URIs.

### Εξαγωγή Εικόνων από το DOCX Κατά την Εξαγωγή  

Τώρα έρχεται το νόστιμο μέρος: η εξαγωγή κάθε εικόνας από το DOCX και η τοποθέτησή της σε φάκελο `img`. Το `IResourceSavingCallback` ενεργοποιείται για κάθε εξωτερικό πόρο (εικόνες, γραμματοσειρές κ.λπ.) που το Aspose γράφει κατά τη λειτουργία αποθήκευσης.

```java
// Step 3 – tell Aspose where to put image resources
mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Build a path like "img/picture1.png"
            String newName = "img/" + args.getResourceFileName();
            args.setResourceFileName(newName);

            // Optional: you could compress the image here
            // InputStream original = args.getResourceStream();
            // args.setResourceStream(compress(original));
        }
    }
});
```

*Γιατί χρησιμοποιούμε callback:* Χωρίς αυτό, το Aspose θα διασκορπίζει τις εικόνες στον ίδιο φάκελο με το `output.md`, κάνοντας το αποθετήριο ακατάστατο. Το callback μας δίνει πλήρη έλεγχο πάνω στην ονομασία, τη δομή των φακέλων, και ακόμη και σε επεξεργασίες μετά (π.χ., αλλαγή μεγέθους PNG).

### Αποθήκευση Word ως Markdown – Η Τελική Εγγραφή  

Με το έγγραφο φορτωμένο και τις επιλογές αποθήκευσης ρυθμισμένες, γράφουμε τελικά το αρχείο Markdown. Οι εικόνες αποθηκεύονται αυτόματα στον υπο‑φάκελο `img` που ορίσαμε.

```java
// Step 4 – write the Markdown file
doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

Αν όλα πάνε καλά, θα έχετε:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ img/
   ├─ image1.png
   ├─ image2.jpg
   └─ ...
```

Ανοίξτε το `output.md` σε οποιονδήποτε επεξεργαστή και θα δείτε σύνταξη εικόνας Markdown όπως `![Image 1](img/image1.png)`. Οι σύνδεσμοι είναι ήδη σχετικοί, οπότε λειτουργούν στο GitHub, στο MkDocs ή σε οποιονδήποτε static site generator.

---

## Πώς να Τοποθετήσετε Εικόνες σε Υπο‑Φάκελο (Προχωρημένες Επιλογές)

Μερικές φορές χρειάζεται πιο βαθιά ιεραρχία, όπως `assets/images/`. Απλώς τροποποιήστε το callback:

```java
String newName = "assets/images/" + args.getResourceFileName();
args.setResourceFileName(newName);
```

Ή, αν θέλετε να μετονομάσετε τα αρχεία σε κάτι πιο περιγραφικό (π.χ., βάσει της παραγράφου που τα περιβάλλει), μπορείτε να εξετάσετε `args.getResourceFileName()` και `args.getDocumentNode()` μέσα στο callback. Αυτή η ευελιξία είναι ο λόγος που η ερώτηση **πώς να τοποθετήσετε εικόνες** συχνά προκαλεί δυσκολίες—το Aspose σας δίνει το hook, εσείς παρέχετε τη λογική.

### Διαχείριση SVG ή Μη Υποστηριζόμενων Μορφών  

Το Aspose.Words μετατρέπει τις περισσότερες μορφές raster αμέσως. Για SVG, ίσως χρειαστεί πρώτα να το rasterize:

```java
if (args.getResourceFileName().endsWith(".svg")) {
    // Convert SVG to PNG on the fly (requires a third‑party lib)
    InputStream svgStream = args.getResourceStream();
    InputStream pngStream = convertSvgToPng(svgStream);
    args.setResourceStream(pngStream);
    args.setResourceFileName(args.getResourceFileName().replace(".svg", ".png"));
}
```

*Σημείωση περί ειδικής περίπτωσης:* Δεν υποστηρίζουν όλοι οι Markdown renderers SVG ενσωματωμένα. Η μετατροπή σε PNG εγγυάται συμβατότητα.

---

## Αποθήκευση Word ως Markdown – Πλήρες Παράδειγμα Εργασίας  

Παρακάτω είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντιγράψτε‑και‑επικολλήστε το σε ένα αρχείο `Main.java`, προσαρμόστε τις διαδρομές, και πατήστε **Run**.

```java
// Main.java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) throws Exception {
        // --------------------------------------------------------------------
        // 1️⃣ Load the DOCX file
        // --------------------------------------------------------------------
        License license = new License();
        // Uncomment the next line if you have a license file
        // license.setLicense("Aspose.Words.Java.lic");

        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // --------------------------------------------------------------------
        // 2️⃣ Prepare Markdown options
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        // Keep images as separate files (GitHub‑flavored)
        mdOptions.setExportImagesAsBase64(false);

        // --------------------------------------------------------------------
        // 3️⃣ Callback – extract and relocate images
        // --------------------------------------------------------------------
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Place every image in the "img" folder
                    String newName = "img/" + args.getResourceFileName();
                    args.setResourceFileName(newName);

                    // Example: compress PNGs (pseudo‑code)
                    // if (newName.endsWith(".png")) {
                    //     args.setResourceStream(compressPng(args.getResourceStream()));
                    // }
                }
            }
        });

        // --------------------------------------------------------------------
        // 4️⃣ Save as Markdown
        // --------------------------------------------------------------------
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        System.out.println("✅ Markdown export complete! Check the img folder for pictures.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** το `output.md` περιέχει καθαρό κείμενο Markdown, και κάθε αναφορά εικόνας δείχνει στο `img/<filename>`. Ανοίξτε το αρχείο στην προεπισκόπηση Markdown του VS Code για να βεβαιωθείτε ότι οι εικόνες εμφανίζονται σωστά.

---

## Συχνές Ερωτήσεις & Πιθανά Προβλήματα

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν το DOCX μου περιέχει ενσωματωμένες γραμματοσειρές;* | Ορίστε `mdOptions.setExportFontsAsBase64(true)` αν τις χρειάζεστε, αλλά οι περισσότεροι επεξεργαστές Markdown αγνοούν τις γραμματοσειρές. |
| *Μπορώ να εξάγω σε διαφορετική δομή φακέλων;* | Απόλυτα—αλλάξτε το string `newName` στο callback σε οποιοδήποτε μονοπάτι θέλετε. |
| *Λειτουργεί αυτό με αρχεία .doc;* | Ναι. Το Aspose.Words διαβάζει `.doc` με τον ίδιο τρόπο· απλώς αλλάξτε την επέκταση αρχείου στον κατασκευαστή `Document`. |
| *Τι γίνεται με μεγάλες εικόνες;* | Σκεφτείτε να προσθέσετε ένα βήμα συμπίεσης μέσα στο callback (π.χ., χρησιμοποιώντας `javax.imageio` για μείωση ποιότητας). |
| *Απαιτείται άδεια για παραγωγή;* | Η δωρεάν δοκιμή προσθέτει υδατογράφημα στην πρώτη σελίδα του αποτελέσματος. Για εμπορική χρήση, αποκτήστε άδεια ώστε να το αφαιρέσετε. |

---

## Συμπέρασμα

Τώρα ξέρετε **πώς να εξάγετε markdown** από ένα αρχείο Word, **πώς να μετατρέψετε docx σε markdown**, **πώς να εξάγετε εικόνες από docx**, και **πώς να τοποθετήσετε εικόνες** σε έναν αφιερωμένο φάκελο—όλα με λίγες γραμμές Java χρησιμοποιώντας το Aspose.Words. Το πλήρες παράδειγμα παραπάνω είναι έτοιμο να ενσωματωθεί σε οποιοδήποτε έργο, και μπορείτε να προσαρμόσετε το callback για προσαρμοσμένα σχήματα ονομασίας ή επιπλέον επεξεργασία.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να τροφοδοτήσετε το παραγόμενο Markdown σε έναν static‑site generator όπως το Jekyll ή το Hugo, πειραματιστείτε με διαφορετικές μορφές εικόνων, ή ενσωματώστε αυτή τη μετατροπή σε μια αυτοματοποιημένη CI pipeline. Το ίδιο μοτίβο λειτουργεί για PDF, HTML ή ακόμη και απλό κείμενο—απλώς αλλάξτε την κλάση `SaveOptions`.

Καλή προγραμματιστική δουλειά, και εύχομαι η τεκμηρίωσή σας να παραμένει πάντα καθαρή και πλούσια σε εικόνες!  

---  

![Διάγραμμα που απεικονίζει πώς να εξάγετε markdown από το Word – η ροή από DOCX σε Markdown με εικόνες σε υπο‑φάκελο](https://example.com/placeholder.png "διάγραμμα εξαγωγής markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}