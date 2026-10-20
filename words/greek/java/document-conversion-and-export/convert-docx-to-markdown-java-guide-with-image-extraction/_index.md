---
category: general
date: 2026-10-12
description: Μετατροπή DOCX σε Markdown σε Java, εξαγωγή εικόνων από αρχεία Word.
  Αυτός ο οδηγός βήμα‑βήμα δείχνει τη χρήση του Aspose.Words για απρόσκοπτη μετατροπή.
draft: false
keywords:
- docx to markdown java
- extract images from docx
- aspose words java
- markdown embedded images
- aspose words maven
lastmod: 2026-10-12
og_description: Ο οδηγός Docx to markdown java δείχνει πώς να μετατρέψετε αρχεία DOCX
  σε Markdown ενώ εξάγετε εικόνες χρησιμοποιώντας το Aspose.Words. Ακολουθήστε τα
  βήματα για αξιόπιστα αποτελέσματα.
og_image_alt: 'Developer guide: Convert DOCX to Markdown in Java with image extraction'
og_title: Docx to markdown java – μετατροπή DOCX με εξαγωγή εικόνων
schemas:
- author: Aspose
  dateModified: '2026-10-12'
  description: Convert DOCX to Markdown in Java, extracting images from Word files.
    This step‑by‑step guide shows Aspose.Words usage for seamless conversion.
  headline: 'Docx to markdown java: convert DOCX to Markdown with image extraction'
  type: TechArticle
- questions:
  - answer: Yes, the library is distributed as a plain JAR and works with both Maven
      and Gradle build systems.
    question: Is the solution compatible with Maven and Gradle?
  - answer: Iterate over a directory, load each file with `new Document(path)`, and
      call `save` with the same `MarkdownSaveOptions` instance for each iteration.
    question: Can I convert a batch of DOCX files at once?
  - answer: The callback writes each image as it is encountered, so even very large
      images are streamed to disk without loading the entire document into memory.
    question: How are large images handled?
  - answer: By default images are saved as PNG, but you can preserve the original
      format by returning `args.getOriginalFileName()` in the callback’s `setFileName`
      method.
    question: Does the API support extracting images in their original format?
  - answer: Any version from 20.12 onward supports Markdown export and the `IResourceSavingCallback`
      interface.
    question: What version of Aspose.Words is required?
  type: FAQPage
tags:
- docx to markdown
- Aspose.Words
- Java document processing
title: 'Docx to markdown java: μετατροπή DOCX σε Markdown με εξαγωγή εικόνων'
url: /el/java/document-conversion-and-export/convert-docx-to-markdown-java-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Docx σε markdown java: μετατροπή DOCX σε Markdown με εξαγωγή εικόνων

Έχετε ποτέ χρειαστεί να μετατρέψετε DOCX σε Markdown σε Java αλλά δεν ήξερες πώς να διατηρήσεις τις εικόνες ανέπαφες; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν μεταφέρουν τεκμηρίωση από το Word σε στατικούς ιστότοπους. Αυτός ο οδηγός **docx to markdown java** σας δείχνει πώς να μετατρέψετε ένα έγγραφο Word σε καθαρό markdown **και** να εξάγετε αυτόματα κάθε ενσωματωμένη εικόνα χρησιμοποιώντας το Aspose.Words. Χωρίς εξωτερικές υπηρεσίες, χωρίς κόλπα γραμμής εντολών—απλώς καθαρός κώδικας Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

## Γρήγορες απαντήσεις
- **Μπορώ να το τρέξω χωρίς άδεια;** Ναι, το Aspose.Words προσφέρει δωρεάν λειτουργία αξιολόγησης που προσθέτει υδατογράφημα· μια άδεια το αφαιρεί για παραγωγή.
- **Ποια έκδοση Java απαιτείται;** Η Java 17 ή οποιοδήποτε JDK 8+ λειτουργεί επειδή το API είναι συμβατό προς τα πίσω.
- **Πώς αποθηκεύονται οι εικόνες;** Η βιβλιοθήκη γράφει κάθε εικόνα σε έναν φάκελο που ορίζετε, ονομάζοντάς τες διαδοχικά (π.χ., `img_0.png`).
- **Ποιοι μορφότυποι υποστηρίζονται;** Το Aspose.Words διαχειρίζεται πάνω από 35 μορφές εισόδου και εξόδου, συμπεριλαμβανομένων των DOCX, PDF, HTML και Markdown.
- **Είναι η λύση αποδοτική σε μνήμη;** Η κλήση αποθήκευσης πόρων επεξεργάζεται μία εικόνα τη φορά, διατηρώντας τη χρήση μνήμης χαμηλή ακόμη και για έγγραφα 1.000 σελίδων.

## Τι θα χρειαστείτε
- **Java 17** (ή οποιοδήποτε πρόσφατο JDK· το API λειτουργεί το ίδιο σε 8+)
- **Aspose.Words for Java** (Δωρεάν δοκιμή ή αδειοδοτημένο JAR)
- Ένα αρχείο **DOCX** που περιέχει τουλάχιστον μία εικόνα (θα το ονομάσουμε `input.docx`)
- Ένα IDE ή κειμενογράφο—IntelliJ IDEA, Eclipse, VS Code, ό,τι προτιμάτε

> **Συμβουλή:** Αν δεν έχετε προσθέσει ακόμη το Aspose.Words στο έργο σας, κατεβάστε το τελευταίο JAR από την ιστοσελίδα Aspose και τοποθετήστε το στον φάκελο `libs`, στη συνέχεια προσθέστε το στο classpath.

## Πώς να μετατρέψετε docx σε markdown σε Java;

Φορτώστε το DOCX με `new Document("input.docx")`. Η κλάση `Document` αντιπροσωπεύει ένα αρχείο Word που έχει φορτωθεί στη μνήμη. Διαμορφώστε ένα αντικείμενο `MarkdownSaveOptions` που περιλαμβάνει κλήση αποθήκευσης πόρων, και καλέστε `sourceDoc.save("output.md", markdownOptions)`. Η κλήση γράφει κάθε εικόνα σε έναν φάκελο της επιλογής σας, παρέχοντάς σας ένα έτοιμο προς δημοσίευση αρχείο markdown και έναν αντίστοιχο φάκελο εικόνων σε μόλις τρεις γραμμές κώδικα. Αυτή η προσέγγιση λειτουργεί για έγγραφα οποιουδήποτε μεγέθους και διατηρεί πίνακες, υποσημειώσεις και ενσωματωμένα γραφικά.

### Anchor ορισμού: κλάση Document
Η κλάση `Document` είναι το βασικό αντικείμενο του Aspose.Words που αντιπροσωπεύει ένα φορτωμένο αρχείο Word στη μνήμη.

## Βήμα 1: ρυθμίστε το έργο και εισάγετε τις εξαρτήσεις

Πρώτα, δημιουργήστε ένα απλό Maven module (ή Gradle αν είναι η προτίμησή σας). Εδώ είναι ένα ελάχιστο απόσπασμα `pom.xml` που ενσωματώνει το Aspose.Words:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>docx‑to‑markdown</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose‑words</artifactId>
            <version>23.12</version> <!-- check for the latest -->
        </dependency>
    </dependencies>
</project>
```

Αν δεν χρησιμοποιείτε Maven, βεβαιωθείτε ότι το `aspose-words-23.12.jar` (ή νεότερο) βρίσκεται στο classpath κατά τη μεταγλώττιση.

## Βήμα 2: φορτώστε το έγγραφο docx που περιέχει εικόνες

Τώρα ας γράψουμε την κλάση Java που κάνει τη βαριά δουλειά. Το πρώτο πράγμα που κάνουμε είναι να ανοίξουμε το αρχείο Word:

```java
import com.aspose.words.*;

public class MarkdownResourceCallbackDemo {

    public static void main(String[] args) throws Exception {
        // Load the DOCX document that contains images
        Document sourceDoc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Γιατί είναι σημαντικό:** `Document` είναι το σημείο εισόδου για *οποιαδήποτε* λειτουργία του Aspose.Words. Αναλύει το DOCX, δημιουργεί ένα μοντέλο αντικειμένων στη μνήμη και μας δίνει πρόσβαση σε παραγράφους, πίνακες και, φυσικά, τα ενσωματωμένα μέσα.

## Βήμα 3: διαμορφώστε markdownsaveoptions με κλήση αποθήκευσης πόρων

Όταν το Aspose.Words μετατρέπει σε markdown, γράφει τα αρχεία εικόνας σε έναν φάκελο που καθορίζετε. Για να ελέγξετε το όνομα του φακέλου και το σχήμα ονομασίας των αρχείων, υλοποιούμε το `IResourceSavingCallback`. Η διεπαφή `IResourceSavingCallback` σας επιτρέπει να παρεμβείτε σε κάθε πόρο (όπως εικόνες) που γράφει το Aspose.Words.

```java
        // Create Markdown save options and define where images will be stored
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Store each image in a custom folder and give it a unique name
                args.setDirectory("YOUR_DIRECTORY/markdown-resources");
                args.setFileName("img_" + args.getIndex() + ".png");
            }
        });
```

### Anchor ορισμού: IResourceSavingCallback
`IResourceSavingCallback` είναι μια διεπαφή που σας επιτρέπει να παρεμβείτε σε κάθε πόρο (όπως εικόνες) που γράφει το Aspose.Words, επιτρέποντάς σας να επιλέξετε τη διαδρομή εξόδου και το όνομα αρχείου.

#### Τι κάνει η κλήση
- **`setDirectory`** λέει στο Aspose πού να αποθηκεύσει τα αρχεία εικόνας.  
- **`setFileName`** δημιουργεί ένα καθορισμένο όνομα (`img_0.png`, `img_1.png`, …) ώστε να μπορείτε να τα αναφέρετε από το markdown χωρίς εικασίες.

Αν χρειάζεστε διαφορετική μορφή εικόνας (π.χ., JPEG), απλώς αλλάξτε την επέκταση στο `setFileName` και το Aspose θα εκτελέσει τη μετατροπή για εσάς.

## Βήμα 4: αποθηκεύστε το έγγραφο ως markdown

Με τις επιλογές έτοιμες, το τελικό βήμα είναι μια εντολή μίας γραμμής:

```java
        // Save the document as Markdown using the configured options
        sourceDoc.save("YOUR_DIRECTORY/output.md", markdownOptions);
    }
}
```

Η εκτέλεση του προγράμματος παράγει δύο αντικείμενα:

1. `output.md` – η αναπαράσταση markdown του αρχικού περιεχομένου Word.  
2. `markdown-resources/` – ένας φάκελος που περιέχει κάθε εξαγόμενη εικόνα (`img_0.png`, `img_1.png`, …).

### Αναμενόμενο απόσπασμα markdown
Αν το `input.docx` περιείχε μια παράγραφο ακολουθούμενη από εικόνα, το παραγόμενο markdown μπορεί να μοιάζει με:

```markdown
Here is an introductory paragraph.

![Image 1](markdown-resources/img_0.png)

Another paragraph after the picture.
```

Παρατηρήστε πώς η αναφορά στην εικόνα χρησιμοποιεί μια σχετική διαδρομή που ταιριάζει με το φάκελο που δημιουργήσαμε. Αυτό είναι ακριβώς ό,τι χρειάζεστε για στατικούς δημιουργούς ιστοτόπων όπως Jekyll, Hugo ή MkDocs.

## Βήμα 5: επαληθεύστε το αποτέλεσμα και προσαρμόστε (προαιρετικό)

Μετά την εκτέλεση, ανοίξτε το `output.md` σε οποιονδήποτε επεξεργαστή κειμένου:

- **Ελέγξτε τις συνδέσεις εικόνων:** Πρέπει να δείχνουν στον φάκελο `markdown-resources`.  
- **Επικυρώστε την απόδοση markdown:** Ανοίξτε το αρχείο σε προεπισκόπηση markdown (VS Code, Typora ή το CI pipeline σας) για να βεβαιωθείτε ότι οι εικόνες εμφανίζονται όπως αναμένεται.  
- **Ρυθμίστε την ονομασία ή τη δομή φακέλου:** Αν προτιμάτε διαφορετική ιεραρχία, τροποποιήστε τη λογική της κλήσης αναλόγως.

### Διαχείριση ειδικών περιπτώσεων
- **Πίνακες με ενσωματωμένες εικόνες:** Το Aspose.Words εξάγει αυτόματα και αυτές τις εικόνες.  
- **Μεγάλα αρχεία DOCX:** Η κλήση εκτελείται ανά πόρο, έτσι η κατανάλωση μνήμης παραμένει χαμηλή ακόμη και για έγγραφα 1.000 σελίδων.  
- **Ελλιπείς εικόνες:** Αν μια εικόνα αποτύχει να εξαχθεί, το Aspose ρίχνει ένα `ResourceSavingException`. Τυλίξτε την κλήση `sourceDoc.save` σε μπλοκ try‑catch για να καταγράψετε το προβληματικό δείκτη.

```java
try {
    sourceDoc.save("YOUR_DIRECTORY/output.md", markdownOptions);
} catch (ResourceSavingException e) {
    System.err.println("Failed to save image at index: " + e.getArgs().getIndex());
    e.printStackTrace();
}
```

## Μπόνους: μετατροπή εικόνων word markdown για υπάρχουσες ιστοσελίδες

Αν έχετε ήδη έναν ιστότοπο markdown που αναμένει εικόνες σε συγκεκριμένο υπο‑φάκελο (π.χ., `assets/img/`), απλώς προσαρμόστε την κλήση:

```java
args.setDirectory("YOUR_DIRECTORY/assets/img");
args.setFileName("docx_image_" + args.getIndex() + ".png");
```

Αυτή η μικρή αλλαγή σας επιτρέπει να **μετατρέψετε εικόνες word markdown** χωρίς να τροποποιήσετε το παραγόμενο markdown—ιδανικό για CI pipelines όπου η δομή φακέλων είναι σταθερή.

![παράδειγμα μετατροπής docx σε markdown](placeholder-image.png "παράδειγμα μετατροπής docx σε markdown")

[παράδειγμα μετατροπής docx σε markdown](placeholder-image.png "παράδειγμα μετατροπής docx σε markdown")

[Εικόνα 1](markdown-resources/img_0.png)

*Το κείμενο alt της εικόνας περιλαμβάνει τη βασική λέξη-κλειδί για να ικανοποιήσει τις απαιτήσεις SEO.*

## Συχνές ερωτήσεις & παγίδες

- **Χρειάζομαι άδεια για να τρέξω αυτόν τον κώδικα;**  
  Το Aspose.Words προσφέρει δωρεάν λειτουργία αξιολόγησης που προσθέτει υδατογράφημα στην πρώτη σελίδα. Για παραγωγή, αγοράστε άδεια και καλέστε `License license = new License(); license.setLicense("Aspose.Words.lic");` πριν φορτώσετε το έγγραφο.

- **Τι γίνεται αν το DOCX μου περιέχει εικόνες SVG;**  
  Το Aspose.Words μετατρέπει SVG σε PNG εξ ορισμού όταν ζητάτε μορφή ραστερ όπως `.png`. Αν χρειάζεστε το αρχικό SVG, υλοποιήστε ένα προσαρμοσμένο `IResourceSavingCallback` που γράφει το `args.getOriginalFileName()` αμετάβλητο.

- **Μπορώ να ρέσω το markdown απευθείας σε απόκριση HTTP;**  
  Απόλυτα. Αντί να αποθηκεύετε στο δίσκο, χρησιμοποιήστε `ByteArrayOutputStream` και `markdownOptions.setSaveFormat(SaveFormat.MARKDOWN);` στη συνέχεια γράψτε το byte array στο ρεύμα εξόδου του servlet.

## Συχνές ερωτήσεις

**Q: Είναι η λύση συμβατή με Maven και Gradle;**  
A: Ναι, η βιβλιοθήκη διανέμεται ως απλό JAR και λειτουργεί και με τα συστήματα κατασκευής Maven και Gradle.

**Q: Μπορώ να μετατρέψω μια δέσμη αρχείων DOCX ταυτόχρονα;**  
A: Επανάληψη σε έναν φάκελο, φόρτωση κάθε αρχείου με `new Document(path)`, και κλήση `save` με το ίδιο αντικείμενο `MarkdownSaveOptions` για κάθε επανάληψη.

**Q: Πώς διαχειρίζονται μεγάλες εικόνες;**  
A: Η κλήση γράφει κάθε εικόνα καθώς εντοπίζεται, έτσι ακόμη και πολύ μεγάλες εικόνες μεταφέρονται στο δίσκο χωρίς να φορτώνεται ολόκληρο το έγγραφο στη μνήμη.

**Q: Υποστηρίζει το API την εξαγωγή εικόνων στην αρχική τους μορφή;**  
A: Από προεπιλογή οι εικόνες αποθηκεύονται ως PNG, αλλά μπορείτε να διατηρήσετε την αρχική μορφή επιστρέφοντας `args.getOriginalFileName()` στη μέθοδο `setFileName` της κλήσης.

**Q: Ποια έκδοση του Aspose.Words απαιτείται;**  
A: Οποιαδήποτε έκδοση από την 20.12 και μετά υποστηρίζει την εξαγωγή σε Markdown και τη διεπαφή `IResourceSavingCallback`.

## Συμπέρασμα

Τώρα έχετε μια **πλήρη, εκτελέσιμη λύση για τη μετατροπή DOCX σε markdown** ενώ εξάγετε καθαρά κάθε εικόνα χρησιμοποιώντας Java και Aspose.Words. Ο κώδικας διαχειρίζεται το σενάριο “java docx to markdown”, σέβεται τη ροή εργασίας **extract images from docx**, και σας δίνει πλήρη έλεγχο πάνω στην έξοδο **convert word markdown images**.

Από εδώ μπορείτε:

- Να ενσωματώσετε το εργαλείο σε ένα plugin Maven για αυτοματοποιημένες κατασκευές τεκμηρίωσης.  
- Να επεκτείνετε την κλήση για να μετονομάζει τις εικόνες βάσει του alt‑text ή της γύρω παραγράφου.  
- Να το συνδυάσετε με αλυσίδα μετατροπής PDF‑σε‑DOCX για παλαιά έγγραφα.

Δοκιμάστε το, προσαρμόστε τα ονόματα φακέλων ώστε να ταιριάζουν με τη ρύθμιση του static‑site σας, και αφήστε το markdown να ρέει στην επόμενη έκδοση. Καλή προγραμματιστική!

**Τελευταία ενημέρωση:** 2026-10-12  
**Δοκιμάστηκε με:** Aspose.Words 23.12 (Java)  
**Συγγραφέας:** Aspose

## Σχετικά Μαθήματα

- [Αποθήκευση Εικόνων από Word – Οδηγός Aspose.Words για Java](/words/java/document-loading-and-saving/)
- [Κατακτήστε τη Μετατροπή σε Markdown με Aspose.Words: Οδηγός Πινάκων & Εικόνων](/words/java/tables-lists/mastering-markdown-conversion-aspose-words-tables-images/)
- [Μετατροπή Docx σε Pdf σε Java – Οδηγός Βήμα προς Βήμα](/words/java/document-converting/convert-docx-to-pdf-in-java-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}