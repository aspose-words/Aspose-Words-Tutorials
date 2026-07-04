---
category: general
date: 2026-04-10
description: πώς να ορίσετε το dpi όταν μετατρέπετε το Word σε PNG. Μάθετε πώς να
  εξάγετε το Word σε PNG με προσαρμοσμένη διάταξη πλέγματος και υψηλή ανάλυση.
draft: false
keywords:
- how to set dpi
- convert word to png
- how to export word
- export word to png
- create png grid
language: el
og_description: πώς να ορίσετε το dpi κατά την εξαγωγή ενός εγγράφου Word. Αυτό το
  σεμινάριο δείχνει πώς να μετατρέψετε το Word σε PNG, να εξάγετε το Word σε PNG και
  να δημιουργήσετε πλέγμα PNG με C#.
og_title: πώς να ορίσετε dpi – Πλήρης οδηγός για εξαγωγή Word σε PNG
tags:
- C#
- Aspose.Words
- ImageExport
title: πώς να ορίσετε dpi – Εξαγωγή Word σε PNG Grid με C#
url: /el/net/programming-with-imagesaveoptions/how-to-set-dpi-export-word-to-png-grid-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να ορίσετε dpi – Εξαγωγή Word σε PNG Πλέγμα σε C#

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε dpi** για μια μετατροπή Word‑σε‑PNG χωρίς να τσακίζετε τα μαλλιά σας; Δεν είστε οι μόνοι. Σε πολλά έργα—σκεφτείτε αυτόματους δημιουργούς αναφορών ή pipelines μικρογραφιών—χρειάζεστε ένα καθαρό PNG που σέβεται ένα συγκεκριμένο DPI, και συχνά θέλετε επίσης πολλές σελίδες να πακετάρονται σε μια ενιαία εικόνα πλέγματος. Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από μια πλήρη, έτοιμη‑για‑εκτέλεση λύση που **μετατρέπει Word σε PNG**, σας επιτρέπει να **εξάγετε Word σε PNG** με ρυθμό 300 DPI, και ακόμη **δημιουργεί ένα PNG πλέγμα** με μία εντολή.

> **Γρήγορο κέρδος:** Στο τέλος αυτού του άρθρου θα έχετε μια μόνο γραμμή C# που παίρνει το `input.docx` και παράγει το `output.png` στα 300 DPI, διατεταγμένο σε πλέγμα 2 × 2. Χωρίς επιπλέον εργαλεία, χωρίς χειροκίνητη επεξεργασία εικόνας.

## Τι Θα Μάθετε

- Πώς να **ορίσετε DPI** χρησιμοποιώντας το Aspose.Words `ImageSaveOptions`.
- Τα ακριβή βήματα για **εξαγωγή Word σε PNG** με προσαρμοσμένη διάταξη σελίδων.
- Πώς να **δημιουργήσετε ένα PNG πλέγμα** (τέσσερις σελίδες ανά σειρά/στήλη) σε ένα μόνο αρχείο.
- Συνηθισμένα προβλήματα κατά τη μετατροπή μεγάλων εγγράφων και πώς να τα αποφύγετε.
- Μια σειρά παραλλαγών: εξαγωγή μεμονωμένων σελίδων, αλλαγή μεγέθους πλέγματος, και αντικατάσταση PNG με JPEG.

### Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντική |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 ή νεότερη) | Παρέχει τις κλάσεις `Document` και `ImageSaveOptions` που χρησιμοποιούμε. |
| **.NET 6+** (ή .NET Framework 4.7.2) | Εξασφαλίζει συμβατότητα με την πιο πρόσφατη API. |
| **Βασικές γνώσεις C#** | Θα χρειαστεί να κατανοήσετε namespaces και διαδρομές αρχείων. |
| **Ένα αρχείο Word** (`input.docx`) | Το πηγαίο έγγραφο που θα μετατρέψουμε. |

Αν δεν έχετε εγκαταστήσει ακόμη το Aspose.Words, εκτελέστε:

```bash
dotnet add package Aspose.Words
```

Τώρα που όλα είναι έτοιμα, ας βουτήξουμε στον κώδικα.

## Βήμα 1 – Φόρτωση του Πηγαίου Εγγράφου (how to export word)

Το πρώτο πράγμα που κάνετε είναι να φορτώσετε το αρχείο Word στη μνήμη. Εδώ αρχίζει το **how to export word**.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source .docx
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Συμβουλή:** Χρησιμοποιήστε απόλυτη διαδρομή ή `Path.Combine` για να αποφύγετε εκπλήξεις σε διαφορετικά λειτουργικά συστήματα.

## Βήμα 2 – Διαμόρφωση των Επιλογών Αποθήκευσης Εικόνας (how to set dpi & create png grid)

Εδώ βρίσκεται η καρδιά του tutorial. Λέμε στο Aspose.Words ακριβώς πώς θέλουμε να είναι το PNG: 300 DPI, μορφή PNG, και **διάταξη πλέγματος** που συγκεντρώνει τέσσερις σελίδες σε μία εικόνα.

```csharp
// Create PNG save options with a grid layout
ImageSaveOptions imgOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Arrange pages in a grid (2 columns × 2 rows = 4 pages)
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    
    // Number of columns in the grid – 2 columns => 2 rows for 4 pages
    PageCount = 4,
    
    // Set the DPI – this is where we *how to set dpi*
    HorizontalResolution = 300,
    VerticalResolution = 300
};
```

### Γιατί Αυτές οι Ρυθμίσεις Είναι Σημαντικές

- **`PageLayout = Grid`** – Χωρίς αυτό, κάθε σελίδα θα αποθηκευόταν ως ξεχωριστό PNG. Η επιλογή πλέγματος τις συγχωνεύει, εξοικονομώντας σας ένα βήμα επεξεργασίας.
- **`PageCount = 4`** – Καθορίζει πόσες σελίδες θα περιέχει το πλέγμα. Αν το έγγραφό σας έχει περισσότερες από τέσσερις σελίδες, το Aspose θα δημιουργήσει αυτόματα πρόσθετες σειρές.
- **Ρυθμίσεις DPI** – Τα `HorizontalResolution` και `VerticalResolution` είναι οι μπουλόνια που απαντούν στην ερώτηση **how to set dpi**. Μια εικόνα 300 DPI είναι έτοιμη για εκτύπωση και φαίνεται οξεία σε οθόνες retina.

## Βήμα 3 – Αποθήκευση του Εγγράφου ως Μία Μοναδική PNG (export word to png)

Τώρα εκτελούμε την ενέργεια αποθήκευσης. Αυτή η μοναδική γραμμή κάνει το σκληρό κομμάτι.

```csharp
// Save the document pages as one PNG image
doc.Save(@"YOUR_DIRECTORY\output.png", imgOptions);
```

Αφού εκτελεστεί αυτή η γραμμή, θα βρείτε το `output.png` στον καθορισμένο φάκελο. Ανοίξτε το και θα δείτε ένα πλέγμα 2 × 2 των πρώτων τεσσάρων σελίδων, καθεμία αποδομένη στα 300 DPI.

![πώς να ορίσετε dpi παράδειγμα](https://example.com/placeholder.png "πώς να ορίσετε dpi κατά την εξαγωγή Word σε PNG")

*Κείμενο alt εικόνας: πώς να ορίσετε dpi κατά την εξαγωγή Word σε PNG – δείχνει ένα PNG πλέγμα 2×2.*

## Βήμα 4 – Επαλήθευση του Αποτελέσματος (create png grid)

Μια γρήγορη επιβεβαίωση αποτρέπει προβλήματα αργότερα. Μπορείτε προγραμματιστικά να ελέγξετε το DPI και τις διαστάσεις:

```csharp
using System.Drawing;

// Load the generated PNG
using (Bitmap bmp = new Bitmap(@"YOUR_DIRECTORY\output.png"))
{
    Console.WriteLine($"Width: {bmp.Width}px, Height: {bmp.Height}px");
    Console.WriteLine($"Horizontal DPI: {bmp.HorizontalResolution}");
    Console.WriteLine($"Vertical DPI: {bmp.VerticalResolution}");
}
```

Αν η κονσόλα εμφανίσει `300` και για τις δύο τιμές DPI, έχετε ολοκληρώσει επιτυχώς το **how to set dpi**. Το πλάτος και το ύψος θα αντανακλούν το συνδυασμένο μέγεθος των τεσσάρων σελίδων.

## Προχωρημένες Παραλλαγές

### Μετατροπή Word σε PNG – Ένα Αρχείο ανά Σελίδα

Μερικές φορές χρειάζεστε ξεχωριστά αρχεία PNG αντί για πλέγμα. Απλώς αλλάξτε το `PageLayout` σε `SinglePage` και κάντε βρόχο στις σελίδες:

```csharp
for (int i = 0; i < doc.PageCount; i++)
{
    imgOptions.PageIndex = i;               // Export only this page
    imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.SinglePage;
    doc.Save($@"YOUR_DIRECTORY\page_{i + 1}.png", imgOptions);
}
```

Τώρα έχετε `page_1.png`, `page_2.png`, … – ιδανικό για γκαλερί μικρογραφιών.

### Εξαγωγή Word σε PNG με Διαφορετικό Μέγεθος Πλέγματος

Αν χρειάζεστε πλέγμα 3 × 3 (εννέα σελίδες), προσαρμόστε το `PageCount`:

```csharp
imgOptions.PageCount = 9;          // 3 columns × 3 rows
imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.Grid;
```

Το Aspose θα υπολογίσει αυτόματα τις απαραίτητες σειρές.

### Αντικατάσταση PNG με JPEG (αν το μέγεθος αρχείου μετρά)

Η αλλαγή μορφής είναι τόσο απλή όσο η αντικατάσταση του `SaveFormat.Png` με `SaveFormat.Jpeg`. Μπορείτε επίσης να ελέγξετε την ποιότητα JPEG:

```csharp
ImageSaveOptions jpegOptions = new ImageSaveOptions(SaveFormat.Jpeg)
{
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    PageCount = 4,
    HorizontalResolution = 300,
    VerticalResolution = 300,
    JpegQuality = 90   // 0‑100, higher = better quality
};

doc.Save(@"YOUR_DIRECTORY\output.jpg", jpegOptions);
```

### Διαχείριση Μεγάλων Εγγράφων

Όταν εργάζεστε με έγγραφα άνω των 100 σελίδων, σκεφτείτε τη ροή εξόδου (streaming) για να αποφύγετε πίεση μνήμης:

```csharp
using (FileStream fs = new FileStream(@"YOUR_DIRECTORY\large_output.png", FileMode.Create))
{
    doc.Save(fs, imgOptions);
}
```

Το streaming εξασφαλίζει ότι η διαδικασία παραμένει ελαφριά, ακόμη και σε μέτριους διακομιστές.

## Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Συμπτωμα | Αιτία | Διόρθωση |
|---------|-------|-----|
| Το PNG είναι θολό | Το DPI παραμένει στο προεπιλεγμένο 96 | **Ορίστε `HorizontalResolution` και `VerticalResolution` σε 300** (ή υψηλότερο). |
| Εμφανίζεται μόνο η πρώτη σελίδα | Το `PageLayout` είναι ακόμα `SinglePage` | Αλλάξτε σε `ImageSaveOptions.PageLayoutType.Grid`. |
| Το αρχείο εξόδου είναι τεράστιο | Η μορφή PNG με 300 DPI μπορεί να είναι βαριά | Χρησιμοποιήστε JPEG με `JpegQuality` < 90, ή μειώστε το DPI αν δεν απαιτείται εκτύπωση. |
| Το πλέγμα κόβει τα περιθώρια των σελίδων | Η προεπιλεγμένη διαχείριση περιθωρίων | Προσαρμόστε `ImageSaveOptions.PageMargins` αν χρειάζεται. |

## Ανακεφαλαίωση – Τι Καλύψαμε

- **how to set dpi** – ρυθμίζοντας τα `HorizontalResolution` και `VerticalResolution`.
- **convert word to png** – χρησιμοποιώντας `ImageSaveOptions` με `SaveFormat.Png`.
- **how to export word** – φορτώνοντας το έγγραφο με `Document` και καλώντας `Save`.
- **export word to png** – μία γραμμή που παράγει PNG υψηλής ανάλυσης.
- **create png grid** – ορίζοντας `PageLayout = Grid` και `PageCount` για έλεγχο διάταξης.

Όλα αυτά ενσωματώνονται σε ένα σύντομο, αυτόνομο snippet C# που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

## Τι Ακολουθεί;

- Πειραματιστείτε με **διαφορετικές τιμές DPI** (150, 600) για να δείτε πώς αλλάζει το μέγεθος του αρχείου.
- Συνδυάστε αυτήν την προσέγγιση με **Aspose.PDF** για να συγχωνεύσετε το PNG πλέγμα σε αναφορά PDF.
- Εξερευνήστε **μετατροπή χρωματικού χώρου** (RGB → CMYK) αν στέλνετε το PNG σε επαγγελματικό εκτυπωτή.
- Ρίξτε μια ματιά στην **ασύγχρονη αποθήκευση** (`doc.SaveAsync`) για εφαρμογές με UI που απαιτούν ανταπόκριση.

Έχετε ερωτήσεις για ειδικές περιπτώσεις—όπως εξαγωγή κρυπτογραφημένων αρχείων DOCX ή διαχείριση ενσωματωμένων γραμματοσειρών; Αφήστε ένα σχόλιο και θα εμβαθύνω.

---

*Καλό προγραμματισμό! Αν αυτό το tutorial σας βοήθησε να **how to set dpi** και να εξάγετε τα Word έγγραφά σας σε ένα κομψό PNG πλέγμα, δώστε του αστέρι ή μοιραστείτε το με έναν συνεργάτη που αντιμετωπίζει το ίδιο πρόβλημα.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}