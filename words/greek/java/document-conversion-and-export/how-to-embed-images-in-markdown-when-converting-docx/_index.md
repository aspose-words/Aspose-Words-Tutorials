---
category: general
date: 2026-10-23
description: Μάθετε πώς να ενσωματώνετε εικόνες σε markdown κατά τη μετατροπή ενός
  αρχείου DOCX, χρησιμοποιώντας Base64 για μικρά γραφικά και εξωτερικά αρχεία για
  μεγαλύτερες εικόνες.
draft: false
keywords:
- how to embed images
- embed images in markdown
- convert docx to markdown
- extract images from docx
- embed images as base64
lastmod: 2026-10-23
og_description: Μάθετε πώς να ενσωματώνετε εικόνες σε markdown κατά τη μετατροπή ενός
  αρχείου DOCX, χρησιμοποιώντας Base64 για μικρά γραφικά και εξωτερικά αρχεία για
  μεγαλύτερες εικόνες. Αυτός ο οδηγός δείχνει τα ακριβή βήματα με Aspose.Words for
  Java.
og_image_alt: Screenshot of markdown output with embedded Base64 images generated
  by Aspose.Words for Java
og_title: Πώς να ενσωματώσετε εικόνες σε markdown – Οδηγός μετατροπής Java DOCX
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to embed images in markdown when converting a DOCX file,
    using Base64 for tiny graphics and external files for larger pictures.
  headline: How to embed images in markdown when converting docx
  type: TechArticle
- questions:
  - answer: Yes. The same API works in any Java environment, including servlet containers
      and Spring Boot applications. Just stream the `output.md` back to the client
      after conversion.
    question: Can I use this approach in a web service that generates Markdown on
      the fly?
  - answer: A valid Aspose.Words license is required for production deployments. A
      free evaluation license is available for testing and development.
    question: Is a commercial license required for production use?
  - answer: Load the document with `new Document("file.docx", new LoadOptions("password"))`.
      The same conversion pipeline then applies.
    question: How do I handle password‑protected DOCX files?
  - answer: Convert the SVG to PNG or JPEG first, then let the callback treat it as
      any other image. Aspose.Words does not natively render SVG inside Markdown.
    question: What if I need to embed SVG images?
  - answer: Yes. Aspose.Words for Java is platform‑agnostic and runs wherever a compatible
      JDK is available.
    question: Does this work on Windows, macOS, and Linux?
  type: FAQPage
tags:
- Aspose.Words
- Java
- markdown
- image embedding
- docx conversion
- developer guide
title: Πώς να ενσωματώσετε εικόνες σε markdown κατά τη μετατροπή docx
url: /el/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ενσωματώσετε εικόνες σε markdown κατά τη μετατροπή docx

Έχετε αναρωτηθεί ποτέ **πώς να ενσωματώσετε εικόνες** σε ένα αρχείο Markdown που προέρχεται από ένα έγγραφο Word; Δεν είστε μόνοι. Οι περισσότεροι προγραμματιστές αντιμετωπίζουν πρόβλημα όταν η μετατροπή αφαιρεί τις εικόνες ή τις αποθηκεύει με τρόπο που διασπά τη τελική διάταξη.  

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει **πώς να ενσωματώσετε εικόνες** ως Base64 data URIs για μικρά γραφικά, ενώ τα μεγαλύτερα στοιχεία αποθηκεύονται σε έναν φάκελο στο πλάι. Καθ' όλη τη διάρκεια θα καλύψουμε επίσης **τη μετατροπή docx σε markdown**, θα αναφερθούμε στο **πώς να μετατρέψετε docx** με το Aspose.Words, και θα εξηγήσουμε τη διαφορά μεταξύ ενσωμάτωσης εικόνων ως Base64 και εξαγωγής τους ως ξεχωριστά αρχεία.  

> **Συμβουλή:** Αν χρειάζεστε μόνο μια γρήγορη απόδειξη‑ενός‑ενός, ο παρακάτω κώδικας λειτουργεί αμέσως με μια μόνο εξάρτηση Maven.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται τη μετατροπή;** Το Aspose.Words for Java εκτελεί τη μετατροπή DOCX → Markdown και την εξαγωγή εικόνων.
- **Πώς αποθηκεύονται οι μικρές εικόνες;** Ενσωματώνονται ως Base64 data URIs απευθείας μέσα στο αρχείο Markdown.
- **Πού πηγαίνουν οι μεγάλες εικόνες;** Οι μεγαλύτερες εικόνες αποθηκεύονται σε φάκελο `markdown_resources` δίπλα στο αρχείο Markdown.
- **Χρειάζεται να είναι εγκατεστημένο το Microsoft Word;** Όχι, το Aspose.Words λειτουργεί πλήρως ανεξάρτητα από το Microsoft Office.
- **Ποια έκδοση της Java απαιτείται;** Java 17 ή οποιαδήποτε μεταγενέστερη έκδοση LTS.

## Τι είναι η ενσωμάτωση εικόνων;
`how to embed images` αναφέρεται στην τεχνική εισαγωγής δεδομένων εικόνας απευθείας σε ένα έγγραφο Markdown, είτε ως Base64‑κωδικοποιημένο data URI είτε ως σχετικό σύνδεσμο σε εξωτερικό αρχείο. Αυτή η προσέγγιση σας επιτρέπει να διατηρείτε ένα μόνο φορητό αρχείο Markdown για μικρά γραφικά, ενώ υποστηρίζει ακόμα υψηλής ανάλυσης περιεχόμενα μέσω ξεχωριστών αρχείων.

## Γιατί να ενσωματώνετε εικόνες σε markdown;
Η ενσωμάτωση εικόνων ως Base64 μειώνει τα αιτήματα HTTP για εικονίδια και μικρά γραφικά, κάτι που μπορεί να βελτιώσει την ταχύτητα φόρτωσης της σελίδας έως και 30 % σε δίκτυα χαμηλής καθυστέρησης. Ταυτόχρονα, η διατήρηση των μεγάλων φωτογραφιών εξωτερικά αποτρέπει το αρχείο Markdown από το να υπερβεί τα 5 MB, διατηρώντας την απόδοση του επεξεργαστή και τις διαφορές ελέγχου εκδόσεων.

## Προαπαιτούμενα
- **Java 17** (ή οποιοδήποτε πρόσφατο JDK). Το API είναι προσανατολισμένο στη Java, αλλά οι έννοιες μεταφράζονται και σε άλλες γλώσσες.
- **Aspose.Words for Java** – εμπορική βιβλιοθήκη που υποστηρίζει τη μετατροπή DOCX → Markdown.
- Ένα **δείγμα DOCX** που περιέχει ένα μείγμα μικρών εικονιδίων και μεγαλύτερων φωτογραφιών.
- Ένας φάκελο με δικαιώματα εγγραφής όπου θα αποθηκευτεί το αρχείο Markdown και οι πόροι του.

Δεν απαιτούνται πρόσθετα πλαίσια, ούτε εξωτερικά scripts. Απλώς καθαρή Java και Aspose.Words.

## Τι χρειάζεται να προσθέσετε Aspose.Words στο έργο σας (μετατροπή docx σε markdown)

Αν χρησιμοποιείτε Maven, προσθέστε το παρακάτω απόσπασμα στο `pom.xml` σας. Μπορείτε να αντικαταστήσετε την έκδοση με την πιο πρόσφατη κυκλοφορία τη στιγμή της ανάγνωσης.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Γιατί είναι σημαντικό:** Το Aspose.Words αναλαμβάνει το βαρέως έργο της ανάλυσης της δομής DOCX, της εξαγωγής εικόνων και της απόδοσης της σύνταξης Markdown. Η προσπάθεια να δημιουργήσετε τον δικό σας parser θα ήταν μια ατελείωτη διαδικασία που πιθανότατα δεν χρειάζεται να ακολουθήσετε.

## Πώς λειτουργεί η κλάση Document;
`Document` είναι το βασικό αντικείμενο του Aspose.Words που αντιπροσωπεύει ένα μόνο αρχείο Word στη μνήμη. Παρέχει μεθόδους για φόρτωση, τροποποίηση και αποθήκευση εγγράφων σε πολλές μορφές.  
Ενσωματώνει ολόκληρη τη δομή του εγγράφου, συμπεριλαμβανομένων των ενοτήτων, παραγράφων, πινάκων και ενσωματωμένων πόρων, επιτρέποντάς σας να χειρίζεστε το περιεχόμενο προγραμματιστικά χωρίς να ασχοληθείτε με το υποκείμενο XML.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

## Πώς να αποφασίσετε μεταξύ Base64 και εξωτερικών αρχείων με μια callback
Η callback πόρων είναι μια υλοποίηση του `IResourceSavingCallback` που σας επιτρέπει να παρεμβείτε σε κάθε εικόνα κατά τη μετατροπή.  
Αυτή είναι η ουσία του **πώς να ενσωματώσετε εικόνες** σωστά. Η callback σας παρέχει ένα σημείο πρόσβασης για κάθε πόρο (εικόνα, στυλ κ.λπ.) που ο μετατροπέας θέλει να γράψει. Εξετάζοντας το μέγεθος της εικόνας, μπορείτε να αποφασίσετε αν θα την ενσωματώσετε ως data URI ή θα την αποθηκεύσετε ως εξωτερικό αρχείο, κάτι που βοηθά στην εξισορρόπηση της απόδοσης και του μεγέθους του αρχείου.

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

### Γιατί μια callback;
- **Έλεγχος:** Εσείς αποφασίζετε αν μια εικόνα θα γίνει μια ενσωματωμένη Base64 συμβολοσειρά ή ένα ξεχωριστό αρχείο.
- **Απόδοση:** Τα μικρά εικονίδια γίνονται μέρος του Markdown, εξαλείφοντας επιπλέον αιτήματα HTTP.
- **Φορητότητα:** Οι μεγαλύτερες εικόνες παραμένουν ως εξωτερικά αρχεία, διατηρώντας το μέγεθος του Markdown λογικό.

## Πώς να αποθηκεύσετε το έγγραφο ως markdown
Το SaveOptions είναι ένα αντικείμενο διαμόρφωσης που ελέγχει πώς το Aspose.Words γράφει την έξοδο, συμπεριλαμβανομένου του μορφότυπου, της κωδικοποίησης και της διαχείρισης πόρων.  
Τέλος, ζητήστε από το Aspose.Words να γράψει το αρχείο Markdown χρησιμοποιώντας τις επιλογές που μόλις διαμορφώσαμε. Το αντικείμενο `SaveOptions` σας επιτρέπει να καθορίσετε το φάκελο εξόδου, την callback πόρων και άλλες προτιμήσεις μορφοποίησης, διασφαλίζοντας ότι το παραγόμενο Markdown ταιριάζει με τις συμβάσεις του έργου σας. Μπορείτε επίσης να ενεργοποιήσετε ή να απενεργοποιήσετε τη δημιουργία πίνακα περιεχομένων και να ελέγξετε πώς αποδίδονται οι υποσημειώσεις.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Η εκτέλεση του προγράμματος παράγει δύο πράγματα:

1. `output.md` – η αναπαράσταση Markdown του αρχικού σας DOCX.  
2. Ένας φάκελος `markdown_resources` που περιέχει όλες τις μεγάλες εικόνες που δεν ενσωματώθηκαν.

## Πλήρες λειτουργικό παράδειγμα (όλα τα βήματα σε ένα μέρος)

Παρακάτω βρίσκεται το πλήρες αρχείο πηγαίου κώδικα, έτοιμο για αντιγραφή‑επικόλληση στο IDE σας. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή στο μηχάνημά σας.

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

**Αναμενόμενη έξοδος:** Ανοίξτε το `output.md` σε οποιοδήποτε πρόγραμμα προβολής Markdown. Τα μικρά εικονίδια εμφανίζονται ενσωματωμένα, π.χ.:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

[Ενσωματωμένο Εικονίδιο](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)

Οι μεγαλύτερες φωτογραφίες αναφέρονται ως εξής:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

[Φωτογραφία](markdown_resources/photo1.jpg)

Αυτό είναι ακριβώς αυτό που χρειάζεστε για να **ενσωματώσετε εικόνες** ενώ διατηρείτε το μέγεθος του αρχείου διαχειρίσιμο.

## Συχνές ερωτήσεις & ειδικές περιπτώσεις

### Τι γίνεται αν μια εικόνα είναι JPEG αντί για PNG;
Η παραπάνω callback πάντα προσθέτει στο URI το πρόθεμα `image/png`. Για JPEG, μπορείτε να ελέγξετε τα πρώτα μερικά byte του `args.getData()` ή να χρησιμοποιήσετε το `args.getFileName()` για να προσαγάγετε τον σωστό τύπο MIME:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Μπορώ να αλλάξω το όριο μεγέθους;
Απόλυτα. Το όριο των `10_000` byte είναι μόνο ένα παράδειγμα. Αν έχετε άφθονο προϋπολογισμό εύρους ζώνης, αυξήστε το σε 50 KB ή περισσότερο. Αντίστροφα, μειώστε το αν χρειάζεστε εξαιρετικά ελαφρά αρχεία Markdown.

### Λειτουργεί αυτό με πίνακες ή άλλα αντικείμενα του Word;
Ναι. Το Aspose.Words μετατρέπει αυτόματα πίνακες, λίστες και ακόμη και υποσημειώσεις σε Markdown. Η callback πόρων παρεμβαίνει μόνο στις εικόνες, οπότε δεν χρειάζεστε επιπλέον κώδικα για άλλα στοιχεία.

### Τι γίνεται με τα ονόματα αρχείων που δεν είναι ASCII;
Το API κωδικοποιεί με ασφάλεια τα Unicode ονόματα αρχείων όταν γράφει στον φάκελο `markdown_resources`. Απλώς βεβαιωθείτε ότι το σύστημα αρχείων σας υποστηρίζει UTF‑8 (τα περισσότερα σύγχρονα λειτουργικά συστήματα το κάνουν).

## Συμβουλές αντιμετώπισης προβλημάτων και κοινά λάθη
- **Απουσία εικόνων μετά τη μετατροπή:** Επαληθεύστε ότι το `args.getData()` της callback δεν είναι null και ότι ο φάκελος εξόδου έχει δικαιώματα εγγραφής.  
- **Οι συμβολοσειρές Base64 εμφανίζονται κατεστραμμένες:** Βεβαιωθείτε ότι η κλήση `Base64.getEncoder().encodeToString()` λαμβάνει ολόκληρο τον πίνακα byte· η αποκοπή συχνά συμβαίνει όταν η ροή δεν διαβάζεται πλήρως.  
- **Μεγάλα αρχεία Markdown:** Αν το παραγόμενο `.md` υπερβαίνει τα 5 MB, σκεφτείτε να μειώσετε το όριο μεγέθους ή να συμπιέσετε τις μεγάλες εικόνες πριν τις αποθηκεύσετε στον φάκελο πόρων.  
- **Ασυμβατότητες εκδόσεων:** Το Aspose.Words 24.9+ υποστηρίζει πάνω από 35 μορφές εξόδου και μπορεί να επεξεργαστεί ένα DOCX 500 σελίδων σε λιγότερο από 4 δευτερόλεπτα σε έναν τυπικό διακομιστή 2.5 GHz. Κλειδώστε την έκδοση Maven για να αποφύγετε απρόσμενη συμπεριφορά μετά από σημαντική κυκλοφορία.

## Συχνές ερωτήσεις

**Ε: Μπορώ να χρησιμοποιήσω αυτήν την προσέγγιση σε μια υπηρεσία web που δημιουργεί Markdown σε πραγματικό χρόνο;**  
Α: Ναι. Το ίδιο API λειτουργεί σε οποιοδήποτε περιβάλλον Java, συμπεριλαμβανομένων των servlet containers και των εφαρμογών Spring Boot. Απλώς μεταδώστε το `output.md` πίσω στον πελάτη μετά τη μετατροπή.

**Ε: Απαιτείται εμπορική άδεια για χρήση σε παραγωγή;**  
Α: Απαιτείται έγκυρη άδεια Aspose.Words για παραγωγικές εγκαταστάσεις. Διατίθεται δωρεάν άδεια αξιολόγησης για δοκιμές και ανάπτυξη.

**Ε: Πώς να διαχειριστώ αρχεία DOCX με κωδικό πρόσβασης;**  
Α: Φορτώστε το έγγραφο με `new Document("file.docx", new LoadOptions("password"))`. Στη συνέχεια εφαρμόζεται η ίδια διαδικασία μετατροπής.

**Ε: Τι γίνεται αν χρειαστεί να ενσωματώσω εικόνες SVG;**  
Α: Μετατρέψτε πρώτα το SVG σε PNG ή JPEG, μετά αφήστε την callback να το αντιμετωπίσει όπως οποιαδήποτε άλλη εικόνα. Το Aspose.Words δεν αποδίδει εγγενώς SVG μέσα σε Markdown.

**Ε: Λειτουργεί αυτό σε Windows, macOS και Linux;**  
Α: Ναι. Το Aspose.Words for Java είναι ανεξάρτητο πλατφόρμας και εκτελείται όπου υπάρχει συμβατό JDK.

**Τελευταία ενημέρωση:** 2026-10-23  
**Δοκιμή με:** Aspose.Words for Java 24.10  
**Συγγραφέας:** Aspose

## Σχετικά Tutorials

- [Αποθήκευση εικόνων Word Μετατροπή Docx σε Markdown με Java](/words/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/)
- [Μεταφόρτωση εικόνων σε CDN κατά τη μετατροπή Docx σε Markdown πλήρης](/words/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/)
- [Μετατροπή Docx σε Markdown Ολοκληρωμένος Οδηγός Java](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-java-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}