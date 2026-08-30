---
category: general
date: 2026-06-27
description: Μετατρέψτε γρήγορα DOCX σε PNG χρησιμοποιώντας το Aspose.Words for Java.
  Μάθετε πώς να εξάγετε όλες τις σελίδες σε PNG και να ορίσετε σειρές ανά σελίδα και
  στήλες ανά σελίδα σε μία ενέργεια.
draft: false
keywords:
- convert docx to png
- export all pages png
- how to set rows per page
- how to set columns per page
language: el
og_description: Μετατρέψτε DOCX σε PNG σε Java με το Aspose.Words. Αυτός ο οδηγός
  δείχνει πώς να εξάγετε όλες τις σελίδες σε PNG και να ρυθμίσετε τις σειρές ανά σελίδα
  και τις στήλες ανά σελίδα.
og_title: Μετατροπή DOCX σε PNG – Οδηγός εξαγωγής πλέγματος Java
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert DOCX to PNG quickly using Aspose.Words for Java. Learn to export
    all pages PNG and set rows per page and columns per page in one go.
  headline: Convert DOCX to PNG – Complete Java Guide with Grid Layout
  type: TechArticle
tags:
- Aspose.Words
- Java
- DOCX
- PNG
- Image conversion
title: Μετατροπή DOCX σε PNG – Πλήρης Οδηγός Java με Διάταξη Πλέγματος
url: /el/java/document-conversion-and-export/convert-docx-to-png-complete-java-guide-with-grid-layout/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή DOCX σε PNG – Πλήρης Οδηγός Java με Διάταξη Πλέγματος

Αναρωτηθήκατε ποτέ πώς να **μετατρέψετε DOCX σε PNG** χωρίς να αποθηκεύετε χειροκίνητα κάθε σελίδα; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν χρειάζονται μία εικόνα που να εμφανίζει πολλές σελίδες ταυτόχρονα, ειδικά για μικρογραφίες προεπισκόπησης ή γρήγορη κοινή χρήση.  

Καλή είδηση: με το Aspose.Words for Java μπορείτε να **εξάγετε όλες τις σελίδες PNG** με ένα μόνο βήμα, και ακόμη να αποφασίσετε **πώς να ορίσετε τις σειρές ανά σελίδα** και **πώς να ορίσετε τις στήλες ανά σελίδα**. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, από τη φόρτωση ενός εγγράφου Word μέχρι την παραγωγή μιας τακτοποιημένης εικόνας πλέγματος.

## Τι Καλύπτει Αυτό το Tutorial

Θα ξεκινήσουμε με την καταγραφή των προαπαιτήσεων, έπειτα θα χωρίσουμε τη λύση σε σαφή βήματα. Στο τέλος, θα μπορείτε:

* Να φορτώσετε οποιοδήποτε αρχείο `.docx` από το δίσκο.  
* Να διαμορφώσετε το `ImageSaveOptions` για να εξάγετε **όλες τις σελίδες PNG** ταυτόχρονα.  
* Να ορίσετε ένα πλέγμα 2 × 2 (ή οποιοδήποτε) χρησιμοποιώντας **πώς να ορίσετε τις σειρές ανά σελίδα** και **πώς να ορίσετε τις στήλες ανά σελίδα**.  
* Να αποθηκεύσετε το αποτέλεσμα ως ένα ενιαίο αρχείο PNG που μπορείτε να ενσωματώσετε οπουδήποτε.

Χωρίς εξωτερικά scripts, χωρίς εντολές γραμμής εντολών—απλώς καθαρός κώδικας Java που μπορείτε να ενσωματώσετε στο πρόγραμμά σας.

### Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| Java 8 or newer | Aspose.Words 23.9+ χρειάζεται τουλάχιστον Java 8. |
| Aspose.Words for Java JAR | Παρέχει τις κλάσεις `Document` και `ImageSaveOptions`. |
| A `.docx` file to test | Η πηγή που θα μετατρέψετε. |
| IDE or build tool (Maven/Gradle) | Για να μεταγλωττίσετε και να εκτελέσετε το παράδειγμα. |

Αν έχετε ήδη όλα αυτά, υπέροχα—ας ξεκινήσουμε.

## Βήμα 1: Ρυθμίστε το Έργο σας και Εισάγετε το Aspose.Words

Πρώτα, προσθέστε την εξάρτηση του Aspose.Words. Αν χρησιμοποιείτε Maven, επικολλήστε αυτό στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Για Gradle, είναι ως εξής:

```groovy
implementation 'com.aspose:aspose-words:23.9'
```

Μόλις η βιβλιοθήκη βρίσκεται στο classpath, μπορείτε να αρχίσετε τον κώδικα. Η δήλωση εισαγωγής είναι απλή:

```java
import com.aspose.words.*;
```

> **Pro tip:** Κρατήστε τα JAR του Aspose σε φάκελο `libs/` και προσθέστε τα στο build path αν δεν χρησιμοποιείτε διαχειριστή εξαρτήσεων.

## Βήμα 2: Φορτώστε το Πηγαίο Έγγραφο

Η φόρτωση ενός DOCX είναι τόσο απλή όσο το να περάσετε τη διαδρομή στο κατασκευαστή `Document`. Αυτό είναι το πρώτο συγκεκριμένο βήμα στο **convert docx to png**.

```java
// Step 2: Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Αντικαταστήστε το `YOUR_DIRECTORY` με τον πραγματικό φάκελο όπου βρίσκεται το αρχείο Word. Αν το αρχείο δεν βρεθεί, το Aspose ρίχνει `FileNotFoundException`, οπότε βεβαιωθείτε ότι η διαδρομή είναι σωστή.

## Βήμα 3: Δημιουργήστε Image Save Options για PNG

Τώρα λέμε στο Aspose ότι θέλουμε έξοδο PNG. Η κλάση `ImageSaveOptions` μας επιτρέπει να ρυθμίσουμε τη μετατροπή, συμπεριλαμβανομένης της κρίσιμης σημαίας **export all pages png**.

```java
// Step 3: Create image save options for PNG format
ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
```

Σε αυτό το σημείο το αντικείμενο options είναι έτοιμο, αλλά δεν έχουμε ακόμη καθορίσει *πώς* θα διαχειριστούμε πολλές σελίδες.

## Βήμα 4: Εξαγωγή Όλων των Σελίδων PNG

Από προεπιλογή, το Aspose αποθηκεύει κάθε σελίδα ως ξεχωριστό αρχείο. Για να τις ενσωματώσετε μαζί, ορίστε `pageCount` σε `0`. Στο λεξιλόγιο του Aspose, το `0` σημαίνει “όλες οι σελίδες”.

```java
// Step 4: Export all pages (0 means all pages)
pngOptions.setPageCount(0);
```

Τώρα η βιβλιοθήκη ξέρει ότι θέλετε **export all pages PNG** σε μια μόνο εκτέλεση. Αν θέλετε μόνο τις πρώτες τρεις σελίδες, θα χρησιμοποιούσατε `pngOptions.setPageCount(3);`.

## Βήμα 5: Τακτοποιήστε τις Σελίδες σε Διάταξη Πλέγματος

Εδώ μπαίνει η μαγεία του **πώς να ορίσετε τις σειρές ανά σελίδα** και **πώς να ορίσετε τις στήλες ανά σελίδα**. Θα ζητήσουμε από το Aspose να τοποθετήσει τις σελίδες σε πλέγμα, παρόμοιο με ένα contact sheet.

```java
// Step 5: Arrange pages in a grid layout
pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);
```

Η διάταξη `GRID` λέει στη μηχανή να τοποθετήσει τις σελίδες οριζόντια και κάθετα σύμφωνα με τις διαστάσεις που θα ορίσουμε στη συνέχεια.

## Βήμα 6: Ορίστε τις Διαστάσεις του Πλέγματος (Σειρές × Στήλες)

Μπορείτε να επιλέξετε οποιονδήποτε συνδυασμό ταιριάζει στις ανάγκες σας. Το παρακάτω παράδειγμα δημιουργεί πλέγμα 2 × 2, αλλά μπορείτε εύκολα να το αλλάξετε σε 3 × 4 ή ακόμη και σε μία μόνο σειρά.

```java
// Step 6: Define the grid dimensions (2 rows × 2 columns)
pngOptions.setRowsPerPage(2);      // how to set rows per page
pngOptions.setColumnsPerPage(2);   // how to set columns per page
```

Αν έχετε περισσότερες σελίδες από τα κελιά, το Aspose θα συνεχίσει αυτόματα στην επόμενη σειρά. Αν έχετε λιγότερες σελίδες, τα κενά κελιά παραμένουν διαφανή.

## Βήμα 7: Αποθηκεύστε το Έγγραφο ως Μία Μοναδική Εικόνα PNG

Τέλος, λέμε στο Aspose να γράψει την ενωμένη εικόνα στο δίσκο. Το όνομα του αρχείου μπορεί να είναι ό,τι θέλετε· απλώς κρατήστε την επέκταση `.png`.

```java
// Step 7: Save the document as a single PNG image using the grid layout
document.save("YOUR_DIRECTORY/Grid.png", pngOptions);
```

Όταν το πρόγραμμα ολοκληρωθεί, θα βρείτε το `Grid.png` στον ίδιο φάκελο. Ανοίξτε το και θα δείτε τις πρώτες τέσσερις σελίδες του `input.docx` τακτοποιημένες σε ένα κομψό πλέγμα 2 × 2.

### Αναμενόμενο Αποτέλεσμα

| Σελίδα | Θέση στο Πλέγμα |
|------|------------------|
| 1    | Πάνω‑αριστερά |
| 2    | Πάνω‑δεξιά |
| 3    | Κάτω‑αριστερά |
| 4    | Κάτω‑δεξιά |

Αν το πηγαίο έγγραφο έχει περισσότερες από τέσσερις σελίδες, η πέμπτη σελίδα θα ξεκινήσει μια νέα σειρά (αν αυξήσετε το `rowsPerPage`) ή θα παραλειφθεί (αν κρατήσετε το πλέγμα 2 × 2). Το PNG θα διατηρήσει τις αρχικές διαστάσεις των σελίδων, έτσι το τελικό μέγεθος της εικόνας είναι `rows × pageHeight` επί `columns × pageWidth`.

## Πλήρες Παράδειγμα Λειτουργικού Κώδικα

Παρακάτω είναι το ολοκληρωμένο, έτοιμο‑για‑εκτέλεση πρόγραμμα Java. Αντιγράψτε‑και‑επικολλήστε το σε μια κλάση με όνομα `DocxToPngGrid.java`, προσαρμόστε τις διαδρομές και εκτελέστε.

```java
import com.aspose.words.*;

public class DocxToPngGrid {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the DOCX file
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Prepare PNG save options
            ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
            pngOptions.setPageCount(0);                     // export all pages PNG
            pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);

            // 3️⃣ Configure grid (2 rows × 2 columns)
            pngOptions.setRowsPerPage(2);   // how to set rows per page
            pngOptions.setColumnsPerPage(2); // how to set columns per page

            // 4️⃣ Save the combined image
            document.save("YOUR_DIRECTORY/Grid.png", pngOptions);

            System.out.println("Conversion complete! Check Grid.png.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

Τρέξτε το με:

```bash
javac -cp "path/to/aspose-words-23.9.jar" DocxToPngGrid.java
java -cp ".:path/to/aspose-words-23.9.jar" DocxToPngGrid
```

Θα πρέπει να δείτε το μήνυμα `Conversion complete!` στην κονσόλα, και ένα αρχείο `Grid.png` να εμφανιστεί στον φάκελο προορισμού.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

**Τι γίνεται αν χρειάζομαι διαφορετική μορφή εικόνας;**  
Αντικαταστήστε το `SaveFormat.PNG` με `SaveFormat.JPEG` ή `SaveFormat.TIFF`. Το υπόλοιπο του κώδικα παραμένει ίδιο.

**Μπορώ να ελέγξω την ποιότητα της εικόνας;**  
Ναι. Για JPEG μπορείτε να καλέσετε `pngOptions.setJpegQuality(90);`. Το PNG δεν έχει ρύθμιση ποιότητας επειδή είναι lossless.

**Τι γίνεται με μεγάλα έγγραφα;**  
Όταν εργάζεστε με πολλές σελίδες, το παραγόμενο PNG μπορεί να γίνει τεράστιο (σε μνήμη). Σκεφτείτε να αυξήσετε το `rowsPerPage`/`columnsPerPage` ή να χωρίσετε το αποτέλεσμα σε πολλαπλές εικόνες.

**Χρειάζομαι άδεια;**  
Το Aspose.Words λειτουργεί σε λειτουργία αξιολόγησης χωρίς άδεια, αλλά το παραγόμενο PNG θα περιέχει υδατογράφημα. Αγοράστε άδεια για να το αφαιρέσετε.

## Pro Tips για Χρήση σε Παραγωγή

* **Επαναχρησιμοποίηση `ImageSaveOptions`** – Αν μετατρέπετε πολλά έγγραφα σε batch, δημιουργήστε τις επιλογές μία φορά και επαναχρησιμοποιήστε τις για να αποφύγετε περιττές δημιουργίες αντικειμένων.  
* **Έξοδος σε Stream** – Αντί να αποθηκεύετε σε αρχείο, μπορείτε να γράψετε σε `ByteArrayOutputStream` και να στείλετε το PNG μέσω HTTP.  
* **Ασφάλεια νήματος** – Τα αντικείμενα `Document` δεν είναι thread‑safe, οπότε δημιουργήστε ένα νέο `Document` ανά νήμα.  
* **Προφίλ μνήμης** – Για PDF πάνω από 100 σελίδες, παρακολουθήστε τη χρήση heap· ίσως χρειαστεί να αυξήσετε τη σημαία `-Xmx` της JVM.

## Συμπέρασμα

Διασχίσαμε έναν πρακτικό τρόπο να **convert docx to png** χρησιμοποιώντας το Aspose.Words for Java, καλύπτοντας τα πάντα—from τη φόρτωση του αρχείου μέχρι τη διαμόρφωση του **export all pages png**, και δείχνοντας **πώς να ορίσετε τις σειρές ανά σελίδα** και **πώς να ορίσετε τις στήλες ανά σελίδα** για διάταξη πλέγματος. Η τελική ενιαία εικόνα PNG σας δίνει μια συμπαγή οπτική σύνοψη ενός πολυσελιδικού εγγράφου Word—ιδανική για προεπισκοπήσεις, συνημμένα email ή γρήγορη κοινή χρήση.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να προσθέσετε υδατογράφημα σε κάθε σελίδα, ή πειραματιστείτε με διαφορετικά μεγέθη πλέγματος για να ταιριάζει στο UI σας. Μπορείτε επίσης να συνδυάσετε αυτή τη μετατροπή με έναν γεννήτορα PDF για να παράγετε πολυμορφικά αναφορές σε μία ροή εργασίας.

Αν αντιμετωπίσετε δυσκολίες, αφήστε ένα σχόλιο παρακάτω—καλή προγραμματιστική!  

![convert docx to png example](placeholder.png){alt="παράδειγμα μετατροπής docx σε png"}

## Τι Θα Μάθετε Στη Σειρά Επόμενη;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη κώδικα παραδειγμάτων με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Cómo convertir DOCX a PNG en Java – Aspose.Words](/words/spanish/java/document-converting/converting-documents-images/)
- [Wie man DOCX in PNG in Java konvertiert – Aspose.Words](/words/german/java/document-converting/converting-documents-images/)
- [Comment convertir DOCX en PNG en Java – Aspose.Words](/words/french/java/document-converting/converting-documents-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}