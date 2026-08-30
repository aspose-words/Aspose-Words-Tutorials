---
category: general
date: 2026-06-27
description: Μετατρέψτε docx σε markdown χρησιμοποιώντας το Aspose.Words για Java.
  Μάθετε πώς να ενσωματώνετε εικόνες ως base64 και να εξάγετε έγγραφο Word σε markdown
  χωρίς κόπο.
draft: false
keywords:
- convert docx to markdown
- embed images as base64
- how to embed images markdown
- export word document to markdown
- convert docx to markdown with images
language: el
og_description: Μετατρέψτε docx σε markdown με το Aspose.Words για Java. Αυτό το σεμινάριο
  δείχνει πώς να ενσωματώσετε εικόνες ως base64 και να εξάγετε ένα έγγραφο Word σε
  markdown σε μία ενιαία ροή.
og_title: Μετατροπή docx σε markdown με ενσωματωμένες εικόνες – Οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  headline: convert docx to markdown with embedded images – Java guide
  type: TechArticle
- description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  name: convert docx to markdown with embedded images – Java guide
  steps:
  - name: Read the image file into a byte array (`Files.readAllBytes`).
    text: Read the image file into a byte array (`Files.readAllBytes`).
  - name: Encode with `Base64.getEncoder().encodeToString`.
    text: Encode with `Base64.getEncoder().encodeToString`.
  - name: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
    text: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: Μετατροπή docx σε markdown με ενσωματωμένες εικόνες – Οδηγός Java
url: /el/java/document-conversion-and-export/convert-docx-to-markdown-with-embedded-images-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# μετατροπή docx σε markdown με ενσωματωμένες εικόνες – οδηγός Java

Έχετε ποτέ χρειαστεί να **convert docx to markdown** αλλά αντιμετωπίζετε πρόβλημα όταν οι εικόνες εξαφανίζονται ή μετατρέπονται σε σπασμένους συνδέσμους; Δεν είστε μόνοι. Σε πολλά έργα—στατικούς δημιουργούς ιστοσελίδων, pipelines τεκμηρίωσης ή γρήγορες προεπισκοπήσεις—η διατήρηση αυτών των εικόνων είναι απαραίτητη, και οι συνήθεις μετατροπείς συχνά τις παραλείπουν.  

Ευτυχώς, το Aspose.Words for Java μας παρέχει έναν καθαρό τρόπο να **ενσωματώσουμε εικόνες ως base64** απευθείας μέσα στο Markdown, ώστε το αρχείο εξόδου να είναι πραγματικά φορητό. Σε αυτόν τον οδηγό θα περάσουμε από όλη τη διαδικασία: φόρτωση ενός αρχείου Word, ρύθμιση των επιλογών αποθήκευσης Markdown, διαχείριση των πόρων εικόνας και τελικά αποθήκευση του αποτελέσματος. Στο τέλος θα γνωρίζετε ακριβώς **πώς να ενσωματώσετε εικόνες markdown** και θα έχετε ένα έτοιμο‑για‑εκτέλεση απόσπασμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

## Τι θα χρειαστείτε

- Java 17 ή νεότερη (το API λειτουργεί και με παλαιότερες εκδόσεις, αλλά η 17 είναι η ιδανική).
- Βιβλιοθήκη Aspose.Words for Java (μπορείτε να κατεβάσετε το τελευταίο JAR από το Maven Central: `com.aspose:aspose-words:23.12`).
- Ένα αρχείο `.docx` που θέλετε να μετατρέψετε (θα το ονομάσουμε `Report.docx`).
- Ένα καλό IDE (IntelliJ IDEA, Eclipse ή ακόμη και VS Code με επεκτάσεις Java).

Δεν απαιτούνται επιπλέον εργαλεία επεξεργασίας εικόνας—η βιβλιοθήκη διαχειρίζεται τα πάντα στο παρασκήνιο.

## Βήμα 1: Φόρτωση του εγγράφου Word – **convert docx to markdown** θεμέλιο

Το πρώτο πράγμα που κάνουμε είναι να δημιουργήσουμε μια παρουσία `Document` που δείχνει στο αρχείο προέλευσης. Σκεφτείτε αυτό το αντικείμενο ως την αναπαράσταση στη μνήμη του αρχείου Word, πλήρη με παραγράφους, πίνακες και, φυσικά, εικόνες.

```java
import com.aspose.words.*;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");
        // … we’ll configure options next
    }
}
```

> **Pro tip:** Αν διαβάζετε το docx από ροή (π.χ., ένα ανεβασμένο αρχείο), μπορείτε να περάσετε ένα `InputStream` στον κατασκευαστή `Document`—ιδανικό για web εφαρμογές.

## Βήμα 2: Ρύθμιση του MarkdownSaveOptions – **embed images as base64** μαγεία

Το Aspose.Words περιλαμβάνει μια κλάση `MarkdownSaveOptions` που μας επιτρέπει να ρυθμίσουμε τη συμπεριφορά της μετατροπής. Το κλειδί για τη διατήρηση των εικόνων είναι το `IResourceSavingCallback`. Μέσα στο callback παρεμβαίνουμε σε κάθε ροή εικόνας, τη μετατρέπουμε σε συμβολοσειρά Base64 και ξαναγράφουμε το όνομα του πόρου σε data URI.

```java
import java.io.ByteArrayOutputStream;
import java.util.Base64;
import com.aspose.words.*;

MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();

// Embed images directly as Base64 data URIs
markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) throws Exception {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Copy the image stream to a byte array
            ByteArrayOutputStream baos = new ByteArrayOutputStream();
            args.getStream().copyTo(baos);
            // Encode the bytes as Base64
            String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
            // Build a data URI (png assumed, adjust if needed)
            args.setResourceFileName("data:image/png;base64," + base64);
            // Close the original stream – we no longer need it
            args.setKeepResourceStreamOpen(false);
        }
    }
});
```

Γιατί να περάσουμε από αυτό το επιπλέον βήμα; Επειδή η **export word document to markdown** χωρίς callback θα αποθήκευε τις εικόνες σε ξεχωριστό φάκελο και θα τις αναφερόταν με σχετικές διαδρομές. Αυτές οι διαδρομές σπάζουν όταν μετακινήσετε το αρχείο Markdown, ειδικά σε pipelines CI. Ενσωματώνοντας την εικόνα ως συμβολοσειρά Base64, το Markdown γίνεται ένα ενιαίο, αυτόνομο τεχνούργημα—ιδανικό για GitHub READMEs ή στατικούς δημιουργούς ιστοσελίδων που δεν υποστηρίζουν εξωτερικά περιουσιακά στοιχεία.

### Διαχείριση διαφορετικών μορφών εικόνας

Το παραπάνω απόσπασμα υποθέτει PNG (`image/png`). Αν το αρχείο Word περιέχει JPEG, μπορείτε να ελέγξετε τον αρχικό τύπο περιεχομένου:

```java
String mime = args.getContentType(); // e.g., "image/jpeg"
args.setResourceFileName("data:" + mime + ";base64," + base64);
```

Αυτή η μικρή τροποποίηση εξασφαλίζει ότι το παραγόμενο Markdown θα αποδίδει σωστά ανεξάρτητα από την αρχική μορφή.

## Βήμα 3: Αποθήκευση του αρχείου – **export word document to markdown** τελικό βήμα

Τώρα που οι επιλογές είναι έτοιμες, απλώς καλούμε το `document.save`, περνώντας τη διαδρομή προορισμού και τις ρυθμισμένες `MarkdownSaveOptions`. Η βιβλιοθήκη κάνει το σκληρό έργο: διασχίζει το δέντρο του εγγράφου, μετατρέπει τις παραγράφους σε σύνταξη Markdown και ενσωματώνει τις Base64 εικόνες όπου χρειάζεται.

```java
// Save the document as Markdown with embedded Base64 images
document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
System.out.println("Conversion complete! Check Report.md");
```

Όταν ανοίξετε το `Report.md` σε οποιονδήποτε προβολέα Markdown (VS Code, GitHub, typora, κ.λπ.), θα δείτε τις εικόνες ενσωματωμένες inline, χωρίς επιπλέον αρχεία.

## Βήμα 4: Πλήρες, εκτελέσιμο παράδειγμα – **convert docx to markdown with images** σε ένα μέρος

Συνδυάζοντας όλα μαζί, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε, να μεταγλωττίσετε και να εκτελέσετε:

```java
import com.aspose.words.*;
import java.io.*;
import java.util.Base64;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");

        // 2️⃣ Set up Markdown save options with Base64 image embedding
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    ByteArrayOutputStream baos = new ByteArrayOutputStream();
                    args.getStream().copyTo(baos);
                    String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
                    String mime = args.getContentType(); // Preserve original MIME type
                    args.setResourceFileName("data:" + mime + ";base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                }
            }
        });

        // 3️⃣ Save as Markdown – this is where we **export word document to markdown**
        document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
        System.out.println("✅ convert docx to markdown with embedded images finished.");
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `Report.md` και θα πρέπει να δείτε κάτι σαν:

```markdown
# Sample Report

Here is an introductory paragraph.

![Image](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...==)

Another paragraph follows.
```

Η μακριά συμβολοσειρά Base64 αντιπροσωπεύει τα δεδομένα της εικόνας. Οι περισσότερες επεξεργαστές την περικοπούν στο UI, αλλά η εικόνα αποδίδει τέλεια στην προεπισκόπηση.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|------|----------------|-----|
| Οι εικόνες εμφανίζονται ως σπασμένοι σύνδεσμοι | Το callback δεν εκτελέστηκε επειδή έλειπε ο έλεγχος `ResourceType`. | Βεβαιωθείτε ότι το `if (args.getResourceType() == ResourceType.IMAGE)` περιβάλλει τη λογική σας. |
| Το αρχείο εξόδου είναι τεράστιο | Το Base64 αυξάνει τα δεδομένα κατά ~33%. | Αποδεχτείτε την ανταλλαγή για φορητότητα, ή μεταβείτε σε εξωτερικές εικόνες αν το μέγεθος είναι πρόβλημα. |
| Λάθος μορφή εικόνας | Σκληροκωδικοποιημένο `image/png` για JPEGs. | Χρησιμοποιήστε `args.getContentType()` για να διατηρήσετε τον αρχικό τύπο MIME. |
| Έλλειψη μνήμης για μεγάλα έγγραφα | Φόρτωση ενός τεράστιου DOCX στη μνήμη. | Επεξεργαστείτε το έγγραφο σε τμήματα ή αυξήστε τη μνήμη heap της JVM (`-Xmx2g`). |

## Όταν χρειάζεστε **how to embed images markdown** σε άλλα συμφραζόμενα

Αν δεν χρησιμοποιείτε το Aspose.Words αλλά θέλετε ακόμη να ενσωματώσετε εικόνες Base64, η αρχή παραμένει η ίδια:

1. Διαβάστε το αρχείο εικόνας σε έναν πίνακα byte (`Files.readAllBytes`).
2. Κωδικοποιήστε με `Base64.getEncoder().encodeToString`.
3. Εισάγετε το data URI στη συμβολοσειρά Markdown: `![alt](data:image/png;base64,${base64})`.

Η βιβλιοθήκη απλώς αυτοματοποιεί αυτό για κάθε εικόνα που συναντά, εξοικονομώντας σας το γράψιμο ενός βρόχου.

## Επόμενα βήματα – επέκταση της μετατροπής

Τώρα που έχετε κατακτήσει το **convert docx to markdown with images**, σκεφτείτε αυτές τις βελτιώσεις:

- **Διατήρηση στυλ**: Χρησιμοποιήστε πρώτα `HtmlSaveOptions`, έπειτα μετατρέψτε το HTML σε Markdown με ένα εργαλείο όπως το flexmark‑java για πιο πλούσια μορφοποίηση.
- **Διαχείριση πινάκων**: Το Aspose ήδη μετατρέπει πίνακες, αλλά μπορείτε να ρυθμίσετε λεπτομερώς την ευθυγράμμιση των στηλών μέσω `markdownOptions.setTableAlignment`.
- **Επεξεργασία σε παρτίδες**: Τυλίξτε τον παραπάνω κώδικα σε σαρωτή καταλόγου για να μετατρέψετε αυτόματα δεκάδες αναφορές.
- **Ενσωμάτωση με CI**: Προσθέστε το JAR στο pipeline κατασκευής σας και δημιουργήστε τεκμηρίωση σε κάθε commit.

Κάθε μία από αυτές τις ιδέες βασίζεται στις ίδιες βασικές έννοιες που καλύψαμε, ώστε να νιώσετε άνετα προσαρμόζοντας τον κώδικα.

## Συμπέρασμα

Μόλις περάσαμε από μια πλήρη, ολοκληρωμένη λύση για **convert docx to markdown** διασφαλίζοντας ότι κάθε εικόνα παραμένει ενσωματωμένη ως συμβολοσειρά Base64. Τα βασικά βήματα—φόρτωση του εγγράφου, ρύθμιση του `MarkdownSaveOptions` με ένα προσαρμοσμένο `IResourceSavingCallback`, και αποθήκευση του αρχείου—είναι απλά, και ο κώδικας λειτουργεί αμέσως με το Aspose.Words for Java.  

Με αυτή τη γνώση, μπορείτε τώρα να αυτοματοποιήσετε pipelines τεκμηρίωσης, να δημιουργήσετε φορητές αναφορές Markdown, ή απλώς να διατηρήσετε μια καθαρή, μονοαρχική έκδοση του περιεχομένου Word σας. Αν σας ενδιαφέρουν περαιτέρω προσαρμογές—όπως η διαχείριση SVG ή η προσαρμογή επιπέδων επικεφαλίδων—εξερευνήστε τα έγγραφα API του Aspose.Words· είναι γεμάτα παραδείγματα που συμπληρώνουν ό,τι χτίσαμε εδώ.

Καλή προγραμματιστική, και ας παραμένει το Markdown σας πάντα πλούσιο σε εικόνες!  

![convert docx to markdown diagram](convert-docx-to-markdown.png "convert docx to markdown")

---

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να ενσωματώσετε εικόνες σε Markdown κατά τη μετατροπή DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Πώς να εξάγετε Markdown με Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-markdown/)
- [Μετατροπή docx σε markdown – Εξαγωγή μαθηματικών εξισώσεων σε LaTeX με Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}