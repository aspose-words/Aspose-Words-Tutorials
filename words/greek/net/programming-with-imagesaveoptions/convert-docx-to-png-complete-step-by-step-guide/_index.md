---
category: general
date: 2026-06-02
description: Μετατρέψτε docx σε png και αποθηκεύστε τις εικόνες σε φάκελο χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να εξάγετε τις σελίδες του Word ως εικόνες, να ορίσετε
  την ανάλυση εικόνας στα 300 dpi και να αποθηκεύσετε τις σελίδες του Word ως png.
draft: false
keywords:
- convert docx to png
- save images to folder
- export word pages as images
- set image resolution 300 dpi
- save word pages as png
language: el
og_description: Μετατρέψτε docx σε png σε C# με το Aspose.Words. Αυτό το σεμινάριο
  δείχνει πώς να εξάγετε σελίδες Word ως εικόνες, να αποθηκεύσετε τις εικόνες σε φάκελο
  και να ορίσετε ανάλυση εικόνας 300 dpi.
og_title: Μετατροπή docx σε png – Πλήρης Οδηγός Βήμα‑Βήμα
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Convert docx to png and save images to folder using Aspose.Words. Learn
    how to export word pages as images, set image resolution 300 dpi, and save word
    pages as png.
  headline: Convert docx to png – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Convert docx to png and save images to folder using Aspose.Words. Learn
    how to export word pages as images, set image resolution 300 dpi, and save word
    pages as png.
  name: Convert docx to png – Complete Step‑by‑Step Guide
  steps:
  - name: Why Each Property Is Important
    text: '| Property | Purpose | Relevance to Keywords | |----------|---------|-----------------------|
      | `PageSet` | Limits conversion to the first ten pages. | Helps you **export
      word pages as images** selectively. | | `PageSavingCallback` | Gives each PNG
      a friendly, sequential name. | Directly impacts **s'
  - name: Converting All Pages
    text: 'If you want to **convert docx to png** for the entire document, simply
      omit the `PageSet` assignment:'
  - name: Changing the Output Format
    text: 'Aspose supports JPEG, BMP, and TIFF as well. Swap `SaveFormat.Png` with
      `SaveFormat.Jpeg` and adjust the file extension in the callback:'
  - name: Handling Large Documents
    text: 'For documents with hundreds of pages, consider streaming the output to
      avoid memory pressure:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Conversion
title: Μετατροπή docx σε png – Πλήρης οδηγός βήμα‑προς‑βήμα
url: /el/net/programming-with-imagesaveoptions/convert-docx-to-png-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή docx σε png – Πλήρης Οδηγός Βήμα‑Βήμα

Ποτέ χρειάστηκε να **convert docx to png** αλλά δεν ήξερες ποια κλήση API να χρησιμοποιήσεις; Δεν είσαι μόνος—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν πρέπει να δημιουργήσουν μικρογραφίες για αναφορές Word ή να ενσωματώσουν εικόνες σελίδα‑με‑σελίδα σε μια διαδικτυακή γκαλερί.  

Τα καλά νέα είναι ότι με το Aspose.Words μπορείτε να **export word pages as images**, να ελέγχετε το DPI και αυτόματα να **save images to folder** σε μια ενιαία, τακτοποιημένη διαδικασία. Σε αυτόν τον οδηγό θα περάσουμε από κάθε γραμμή κώδικα, θα εξηγήσουμε γιατί κάθε ρύθμιση είναι σημαντική και θα σας δείξουμε πώς να καταλήξετε σε καθαρές PNG εικόνες 300 dpi έτοιμες για επόμενη επεξεργασία.

Στο τέλος αυτού του σεμιναρίου θα μπορείτε να **save word pages as png**, να τις τοποθετήσετε σε πλέγμα και να προσαρμόσετε την ανάλυση εξόδου χωρίς να σηκώσετε δάχτυλο πέρα από τα παρακάτω αποσπάσματα κώδικα. Χωρίς εξωτερικά εργαλεία, χωρίς χειροκίνητη λήψη στιγμιότυπων—απλώς καθαρό C#.

## Τι Θα Χρειαστείτε

- **Aspose.Words for .NET** (v23.12 ή νεότερο). Το πακέτο NuGet είναι `Aspose.Words`.
- Ένα περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή VS Code με την επέκταση C#).
- Ένα αρχείο DOCX που θέλετε να μετατρέψετε—οποιοδήποτε έγγραφο Word αρκεί.
- Μια διαδρομή φακέλου όπου θα πρέπει να γραφτούν τα αρχεία PNG.

Αυτό είναι όλο. Αν έχετε ήδη αυτά, ας βουτήξουμε.

![παράδειγμα μετατροπής docx σε png](convert-docx-to-png.png "μετατροπή docx σε png")

## Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου – Προετοιμασία για Μετατροπή docx σε png

Πριν μπορέσει να γίνει οποιαδήποτε μετατροπή, πρέπει να φορτώσετε το αρχείο Word σε ένα αντικείμενο `Aspose.Words.Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρη τη δομή του DOCX, παρέχοντάς σας πρόσβαση σε σελίδες, ενότητες και άλλα.

```csharp
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**Γιατί είναι σημαντικό:**  
Η φόρτωση του αρχείου δημιουργεί μια αναπαράσταση στη μνήμη που το Aspose μπορεί να διασχίσει σελίδα‑με‑σελίδα. Η παράλειψη αυτού του βήματος θα σας άφηνε χωρίς πηγή για τη μετατροπή σε PNG.

## Βήμα 2: Δημιουργία PNG Image Save Options – Ορισμός Ρυθμίσεων Εξαγωγής

Η κλάση `ImageSaveOptions` λέει στο Aspose πώς θέλετε να φαίνεται η έξοδος. Εδώ καθορίζουμε το PNG ως μορφή, περιορίζουμε τις σελίδες που θα εξάγουμε και ρυθμίζουμε callbacks για την ονομασία κάθε αρχείου.

```csharp
// Step 2: Create PNG image save options
ImageSaveOptions imageOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Step 3: Export pages 1‑10 (zero‑based indices)
    PageSet = new PageSet(0, 9),

    // Step 4: Name each exported page file
    PageSavingCallback = (sender, args) =>
    {
        args.PageFileName = $"Page_{args.PageIndex + 1:D2}.png";
    },

    // Step 5: Arrange images in a grid layout (3 columns × 4 rows)
    Layout = ImageLayout.Grid,
    Columns = 3,
    Rows = 4,

    // Step 6: Set output resolution to 300 DPI
    ImageResolution = 300
};
```

### Γιατί Κάθε Ιδιότητα Είναι Σημαντική

| Ιδιότητα | Σκοπός | Σχετικότητα με Λέξεις‑Κλειδιά |
|----------|--------|-------------------------------|
| `PageSet` | Περιορίζει τη μετατροπή στις πρώτες δέκα σελίδες. | Σας βοηθά να **export word pages as images** επιλεκτικά. |
| `PageSavingCallback` | Δίνει σε κάθε PNG ένα φιλικό, διαδοχικό όνομα. | Επηρεάζει άμεσα το **save word pages as png** με προβλέψιμα ονόματα αρχείων. |
| `Layout`, `Columns`, `Rows` | Συσκευάζει πολλαπλές σελίδες σε μία εικόνα πλέγματος αν θέλετε ένα σύνθετο. | Προαιρετικό, αλλά δείχνει ευελιξία όταν **save images to folder** σε συγκεκριμένη διάταξη. |
| `ImageResolution` | Ελέγχει το DPI· 300 dpi είναι ποιότητα εκτύπωσης. | Ακριβώς η απαίτηση **set image resolution 300 dpi**. |

## Βήμα 3: Αποθήκευση των Εικόνων – Τελικά **save images to folder**

Τώρα που οι επιλογές είναι έτοιμες, η μέθοδος `Document.Save` κάνει τη βαριά δουλειά. Σημειώνετε έναν φάκελο και το Aspose γράφει κάθε αρχείο PNG σύμφωνα με το callback που ορίσατε.

```csharp
// Step 7: Save the pages as separate PNG files in the output folder
doc.Save("YOUR_DIRECTORY/Images", imageOptions);
```

**Τι θα δείτε:**  
Αν το πηγαίο έγγραφό σας έχει δέκα σελίδες, θα καταλήψετε με δέκα αρχεία ονομασμένα `Page_01.png` έως `Page_10.png` μέσα στο `YOUR_DIRECTORY/Images`. Κάθε εικόνα θα είναι 300 dpi, αρκετά καθαρή για εκτύπωση ή χρήση στο web υψηλής ανάλυσης.

## Κοινές Παραλλαγές & Ακραίες Περιπτώσεις

### Μετατροπή Όλων των Σελίδων

Αν θέλετε να **convert docx to png** για ολόκληρο το έγγραφο, απλώς παραλείψτε την ανάθεση του `PageSet`:

```csharp
imageOptions.PageSet = null; // null means “all pages”
```

### Αλλαγή Μορφής Εξόδου

Το Aspose υποστηρίζει επίσης JPEG, BMP και TIFF. Αντικαταστήστε το `SaveFormat.Png` με `SaveFormat.Jpeg` και προσαρμόστε την επέκταση αρχείου στο callback:

```csharp
ImageSaveOptions imageOptions = new ImageSaveOptions(SaveFormat.Jpeg) { /* … */ };
args.PageFileName = $"Page_{args.PageIndex + 1:D2}.jpg";
```

### Διαχείριση Μεγάλων Εγγράφων

Για έγγραφα με εκατοντάδες σελίδες, σκεφτείτε τη ροή εξόδου (streaming) για να αποφύγετε την πίεση μνήμης:

```csharp
imageOptions.PageSavingCallback = (sender, args) =>
{
    using (FileStream fs = new FileStream(
        Path.Combine("YOUR_DIRECTORY/Images", $"Page_{args.PageIndex + 1:D2}.png"),
        FileMode.Create, FileAccess.Write))
    {
        args.PageStream = fs;
    }
};
```

## Επαγγελματικές Συμβουλές & Πιθανά Προβλήματα

- **Υπάρχουσα Φάκελος:** Το Aspose δεν θα δημιουργήσει αυτόματα τον προορισμό. Καλέστε `Directory.CreateDirectory` εκ των προτέρων για να διασφαλίσετε ότι η διαδρομή υπάρχει.

  ```csharp
  Directory.CreateDirectory("YOUR_DIRECTORY/Images");
  ```

- **DPI vs. διαστάσεις pixel:** 300 dpi δεν εγγυάται συγκεκριμένο μέγεθος pixel· κλιμακώνει την εικόνα βάσει των αρχικών διαστάσεων της σελίδας. Αν χρειάζεστε ακριβές πλάτος/ύψος σε pixel, υπολογίστε το από `doc.PageInfo` και ορίστε το `ImageSize` αναλόγως.

- **Συμβουλή απόδοσης:** Η επαναχρησιμοποίηση της ίδιας παρουσίας `ImageSaveOptions` για πολλαπλές αποθηκεύσεις (π.χ., μετατροπή πολλών αρχείων DOCX σε βρόχο) μειώνει το κόστος κατανομής.

- **Ασφάλεια νήματος:** Οι παρουσίες `Document` δεν είναι thread‑safe. Αν επεξεργάζεστε πολλά αρχεία παράλληλα, δημιουργήστε ξεχωριστό `Document` ανά νήμα.

## Αναμενόμενη Έξοδος

Εκτελώντας το πλήρες απόσπασμα παραπάνω με ένα δέκα‑σελίδων `input.docx` παράγει:

```
YOUR_DIRECTORY/Images/
│─ Page_01.png
│─ Page_02.png
│─ …
│─ Page_10.png
```

Κάθε PNG είναι ένα raster 300 dpi της αντίστοιχης σελίδας Word. Ανοίξτε οποιοδήποτε αρχείο σε προβολέα εικόνας και θα δείτε την ακριβή διάταξη, τις γραμματοσειρές και τα γραφικά του αρχικού DOCX.

## Συμπέρασμα

Διασχίσαμε μια πρακτική, ολοκληρωμένη λύση για **convert docx to png**, καλύπτοντας πώς να **export word pages as images**, **set image resolution 300 dpi**, και **save images to folder** με καθαρά ονόματα αρχείων. Ο κώδικας είναι πλήρως αυτόνομος, απαιτεί μόνο το Aspose.Words και μπορεί να ενσωματωθεί σε οποιοδήποτε έργο .NET.

Τι ακολουθεί; Δοκιμάστε να τροποποιήσετε το `Layout` για να δημιουργήσετε μία ενιαία εικόνα κολάζ, πειραματιστείτε με διαφορετικές τιμές DPI για web vs. εκτύπωση, ή συνδέστε την έξοδο PNG σε μια αλυσίδα OCR. Οι δυνατότητες είναι ατελείωτες, και τώρα έχετε μια σταθερή βάση για να χτίσετε πάνω της.

Αν αντιμετωπίσετε προβλήματα ή έχετε ιδέες για περαιτέρω βελτιώσεις, αφήστε ένα σχόλιο. Καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να Ορίσετε DPI Κατά τη Μετατροπή Word σε PNG – Πλήρης Οδηγός C#](/words/english/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/)
- [Αποθήκευση Εικόνων Word – Μετατροπή Word σε Markdown με Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Πώς να Μετατρέψετε DOCX σε PNG σε Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}