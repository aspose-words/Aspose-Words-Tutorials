---
category: general
date: 2026-03-25
description: Αποθηκεύστε τις εικόνες του Word ενώ μετατρέπετε το docx σε markdown
  χρησιμοποιώντας το Aspose.Words for Java. Μάθετε πώς να εξάγετε εικόνες από το Word
  και να δημιουργήσετε markdown από το docx σε λίγα λεπτά.
draft: false
keywords:
- save word images
- convert docx to markdown
- extract images from word
- export docx images
- create markdown from docx
language: el
og_description: Αποθηκεύστε τις εικόνες του Word κατά τη μετατροπή ενός αρχείου DOCX
  σε Markdown. Αυτός ο οδηγός σας καθοδηγεί στη διαδικασία εξαγωγής εικόνων από το
  Word και δημιουργίας markdown από docx χρησιμοποιώντας Java.
og_title: Αποθήκευση εικόνων Word – Μετατροπή DOCX σε Markdown με Java
tags:
- Aspose.Words
- Java
- Markdown
- Image Extraction
title: Αποθήκευση εικόνων Word – Μετατροπή DOCX σε Markdown με Java
url: /el/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εικόνων Word – Μετατροπή DOCX σε Markdown με Java

Χρειάζεστε **αποθήκευση εικόνων Word** όταν μετατρέπετε ένα αρχείο DOCX σε Markdown; Δεν είστε ο μόνος που αντιμετωπίζει αυτό το πρόβλημα. Πολλοί προγραμματιστές ρωτούν, *«Πώς μπορώ να εξάγω εικόνες από το Word και να έχω ταυτόχρονα ένα καθαρό αρχείο markdown;»* Σε αυτόν τον οδηγό θα σας καθοδηγήσουμε βήμα‑βήμα στη διαδικασία—φόρτωση ενός DOCX, ρύθμιση του Aspose.Words ώστε κάθε εικόνα να τοποθετείται σε φάκελο `assets/`, και τέλος δημιουργία ενός αρχείου markdown που αναφέρει αυτές τις εικόνες. Στο τέλος θα μπορείτε να **μετατρέψετε docx σε markdown**, **εξάγετε εικόνες docx**, και **δημιουργήσετε markdown από docx** με λίγες μόνο γραμμές Java.

Θα καλύψουμε επίσης κοινά προβλήματα (όπως ελλιπείς επεκτάσεις) και θα σας δώσουμε συμβουλές για τη διαχείριση διαγραμμάτων ή SVG που το Aspose.Words αντιμετωπίζει ως πόρους. Πάρτε το IDE σας και ας ξεκινήσουμε.

## Τι Θα Χρειαστεί

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK· το Aspose.Words υποστηρίζει 8+)
- **Aspose.Words for Java** JAR – μπορείτε να το κατεβάσετε από το αποθετήριο Maven Central ή να κατεβάσετε τη δοκιμαστική έκδοση από την ιστοσελίδα του Aspose.
- Ένα **DOCX** που περιέχει τουλάχιστον μία εικόνα (θα το ονομάσουμε `doc-with-images.docx`).
- Ένας φάκελος όπου θέλετε να αποθηκευτούν το markdown και τα assets (π.χ., `output/`).

Αυτό είναι όλο—χωρίς επιπλέον βιβλιοθήκες, χωρίς βαριά πλαίσια. Απλό, έτσι;

![παράδειγμα αποθήκευσης εικόνων word](image.png "παράδειγμα αποθήκευσης εικόνων word")

*Κείμενο εναλλακτικού κειμένου εικόνας: παράδειγμα αποθήκευσης εικόνων word που δείχνει το φάκελο assets με τις εξαγόμενες εικόνες.*

## Βήμα 1 – Ρύθμιση του Maven Project σας (ή Καθαρή Java)

Αν χρησιμοποιείτε Maven, προσθέστε το Aspose.Words ως εξάρτηση:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- check for the latest version -->
</dependency>
```

Αν προτιμάτε ένα απλό Java project, απλώς τοποθετήστε το `aspose-words-24.9.jar` στο classpath σας. Δεν χρειάζεται πλήρες σύστημα κατασκευής.

> **Συμβουλή:** Χρησιμοποιήστε την πιο πρόσφατη έκδοση για να λάβετε διορθώσεις σφαλμάτων για νεότερες μορφές εικόνων (WebP, HEIC, κλ.).

## Βήμα 2 – Φόρτωση του DOCX που Περιέχει Εικόνες

Το πρώτο πράγμα που κάνουμε είναι να διαβάσουμε το αρχείο προέλευσης. Η κλάση `Document` του Aspose.Words αφαιρεί την εξάρτηση από τη μορφή αρχείου, ώστε να μπορείτε να αντιμετωπίζετε ένα DOCX ακριβώς όπως ένα PDF ή ένα RTF.

```java
import com.aspose.words.*;

public class MarkdownResourceDemo {
    public static void main(String[] args) throws Exception {

        // Load the DOCX file that contains images
        Document document = new Document("output/doc-with-images.docx");
```

Γιατί να φορτώσουμε πρώτα το έγγραφο; Επειδή η μηχανή μετατροπής χρειάζεται το πλήρες μοντέλο αντικειμένων (παράγραφοι, runs, εικόνες) πριν μπορέσει να αποφασίσει πού θα τοποθετήσει κάθε πόρο. Η παράλειψη αυτού του βήματος θα έκανε αδύνατη την ενεργοποίηση του callback αργότερα.

## Βήμα 3 – Διαμόρφωση Επιλογών Αποθήκευσης Markdown με Callback Πόρων

Το Aspose.Words σας επιτρέπει να παρεμβείτε σε κάθε εξωτερικό πόρο μέσω του `IResourceSavingCallback`. Εδώ λέμε στη βιβλιοθήκη **πώς να ονομάσει και πού να αποθηκεύσει κάθε εξαγόμενη εικόνα**.

```java
        // Create Markdown save options
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();

        // Define how external resources (images, charts, etc.) should be saved
        markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Store each resource in the "assets/" folder, preserving its original name
                String extension = args.getResourceFileExtension(); // ".png", ".jpg", …
                String fileName = "assets/" + args.getResourceFileName() + extension;
                args.setResourceFileName(fileName);
            }
        });
```

### Γιατί ένα callback;

- **Έλεγχος ονομασίας** – Από προεπιλογή το Aspose μπορεί να δημιουργήσει GUIDs. Το callback σας επιτρέπει να διατηρήσετε το αρχικό όνομα αρχείου Word, το οποίο είναι πολύ πιο αναγνώσιμο.
- **Οργάνωση φακέλων** – Η τοποθέτηση όλων κάτω από `assets/` αντικατοπτρίζει τον τρόπο που πολλοί γεννήτορες στατικών ιστοτόπων αναμένουν τις εικόνες, καθιστώντας το markdown φορητό.
- **Ασφάλεια επέκτασης** – Ορισμένοι πόροι δεν έχουν επέκταση· η `getResourceFileExtension()` εγγυάται το κατάλληλο επίθημα, αποτρέποντας σπασμένους συνδέσμους εικόνας.

## Βήμα 4 – Αποθήκευση του Εγγράφου ως Markdown

Τώρα πραγματοποιούμε πραγματικά τη μετατροπή. Η μέθοδος `save` γράφει το αρχείο markdown και, χάρη στο callback, αποθηκεύει κάθε εικόνα στον υποφάκελο `assets/`.

```java
        // Save the document as Markdown, using the configured options
        document.save("output/doc.md", markdownSaveOptions);
    }
}
```

Όταν ολοκληρωθεί ο κώδικας, θα δείτε:

```
output/
 ├─ doc.md          ← the markdown file
 └─ assets/
      ├─ image1.png
      └─ chart1.svg
```

Ανοίξτε το `doc.md` σε οποιονδήποτε επεξεργαστή και θα παρατηρήσετε συνδέσμους εικόνας markdown όπως `![Image1](assets/image1.png)`. Αυτό είναι το αποτέλεσμα **αποθήκευσης εικόνων Word** που ζητούσατε.

## Βήμα 5 – Επαλήθευση της Εξαγωγής (Προαιρετικό αλλά Συνιστάται)

Μια γρήγορη επιβεβαίωση σας προστατεύει από εκπλήξεις αργότερα.

```java
import java.nio.file.*;

public class VerifyExtraction {
    public static void main(String[] args) throws Exception {
        Path assets = Paths.get("output/assets");
        if (Files.isDirectory(assets)) {
            try (DirectoryStream<Path> stream = Files.newDirectoryStream(assets)) {
                System.out.println("Extracted resources:");
                for (Path p : stream) {
                    System.out.println("- " + p.getFileName());
                }
            }
        } else {
            System.out.println("No assets folder found. Did the callback run?");
        }
    }
}
```

Η εκτέλεση αυτού θα πρέπει να εκτυπώσει μια λίστα με κάθε εικόνα, διάγραμμα ή SVG που εξήχθη από το αρχικό DOCX. Αν η λίστα είναι κενή, ελέγξτε ξανά ότι το callback είναι σωστά συνδεδεμένο.

## Βήμα 6 – Περιπτώσεις Ορίων & Συνηθισμένα Προβλήματα

### 1. Εικόνες μέσα σε Πίνακες ή Κεφαλίδες

Το Aspose τα αντιμετωπίζει όπως τις ενσωματωμένες εικόνες, αλλά το markdown μπορεί να τις εμφανίσει διαφορετικά ανάλογα με τον προβολέα. Αν χρειάζεστε τη διατήρηση της διάταξης του πίνακα, σκεφτείτε να μετατρέψετε πρώτα σε HTML, έπειτα σε markdown με ένα εργαλείο όπως το `pandoc`.

### 2. Μη Υποστηριζόμενες Μορφές

Οι παλαιότερες εκδόσεις του Aspose.Words μπορεί να δυσκολεύονται με νεότερες μορφές όπως το WebP. Η αναβάθμιση στην πιο πρόσφατη έκδοση (ή η μετατροπή της εικόνας σε PNG εκ των προτέρων) λύνει το πρόβλημα.

### 3. Διπλά Ονόματα Αρχείων

Αν δύο εικόνες έχουν το ίδιο όνομα μέσα στο DOCX, το callback θα αντικαταστήσει την πρώτη. Μια γρήγορη λύση είναι να προσαρτήσετε ένα μοναδικό επίθημα:

```java
String uniqueName = args.getResourceFileName() + "_" + UUID.randomUUID();
String fileName = "assets/" + uniqueName + extension;
args.setResourceFileName(fileName);
```

### 4. Μεγάλα Έγγραφα

Για τεράστια αρχεία DOCX (εκατοντάδες MB), ίσως θέλετε να κάνετε streaming της εξόδου αντί να φορτώνετε ολόκληρο το αρχείο στη μνήμη. Το Aspose.Words προσφέρει `DocumentBuilder` και `LoadOptions` για να διαχειριστεί τέτοιες περιπτώσεις, αλλά αυτό είναι θέμα για άλλο tutorial.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα, εδώ είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα:

```java
// File: MarkdownResourceDemo.java
import com.aspose.words.*;
import java.util.UUID;

public class MarkdownResourceDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the DOCX file that contains images
        Document document = new Document("output/doc-with-images.docx");

        // 2️⃣ Create Markdown save options
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();

        // 3️⃣ Define how external resources (images, charts, etc.) should be saved
        markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Preserve original name, add a UUID if a duplicate might occur
                String extension = args.getResourceFileExtension(); // ".png", ".jpg", …
                String baseName = args.getResourceFileName();
                String uniqueName = baseName + "_" + UUID.randomUUID();
                String fileName = "assets/" + uniqueName + extension;
                args.setResourceFileName(fileName);
            }
        });

        // 4️⃣ Save the document as Markdown, using the configured options
        document.save("output/doc.md", markdownSaveOptions);

        System.out.println("Conversion complete! Check output/doc.md and the assets folder.");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- `output/doc.md` περιέχει σύνταξη markdown με αναφορές εικόνων όπως `![Image1](assets/Image1_3f9c2a4e-... .png)`.
- Όλες οι εξαγόμενες εικόνες βρίσκονται στο `output/assets/`.
- Δεν απαιτείται χειροκίνητη αντιγραφή αρχείων· το callback διαχειρίστηκε τα πάντα.

## Συμπέρασμα

Τώρα ξέρετε **πώς να αποθηκεύσετε εικόνες Word** ενώ **μετατρέπετε docx σε markdown** χρησιμοποιώντας το Aspose.Words για Java. Τα βασικά βήματα είναι η φόρτωση του εγγράφου, η διαμόρφωση ενός `Markdown

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}