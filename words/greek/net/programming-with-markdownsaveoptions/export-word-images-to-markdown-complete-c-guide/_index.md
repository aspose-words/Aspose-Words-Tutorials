---
category: general
date: 2025-12-31
description: Εξαγωγή εικόνων Word σε Markdown γρήγορα. Μάθετε πώς να μετατρέψετε το
  Word σε Markdown, να εξάγετε εικόνες από docx και να ορίσετε το DPI των εικόνων
  σε ένα μόνο σεμινάριο.
draft: false
keywords:
- export word images
- convert word to markdown
- extract images from docx
- how to convert docx to markdown
- how to set image dpi
language: el
og_description: Εξαγωγή εικόνων Word σε Markdown με το Aspose.Words. Αυτός ο οδηγός
  δείχνει πώς να μετατρέψετε docx σε markdown, να εξάγετε εικόνες και να ορίσετε το
  DPI της εικόνας.
og_title: Εξαγωγή εικόνων Word σε Markdown – Αναλυτικό σεμινάριο C#
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: Εξαγωγή εικόνων Word σε Markdown – Πλήρης οδηγός C#
url: /el/net/programming-with-markdownsaveoptions/export-word-images-to-markdown-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή εικόνων Word σε Markdown – Πλήρης Οδηγός C#

Έχετε ποτέ χρειαστεί να **export word images** σε Markdown αλλά δεν ήξερες από πού να ξεκινήσεις; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το εμπόδιο όταν προσπαθούν να μεταφέρουν τεκμηρίωση από μια εταιρική ροή εργασίας Word σε έναν static‑site generator. Σε αυτό το tutorial θα περάσουμε βήμα-βήμα από μια ενιαία, αυτόνομη λύση που **converts a DOCX file to Markdown**, εξάγει κάθε ενσωματωμένη εικόνα στα 300 DPI, και ακόμη μετατρέπει τις εξισώσεις Office Math σε LaTeX.

Γιατί είναι σημαντικό; Οι εικόνες υψηλής ανάλυσης διατηρούν τα διαγράμματα σας καθαρά στο web, ενώ οι εξισώσεις LaTeX αποδίδονται όμορφα στις περισσότερες προβολές Markdown. Στο τέλος θα έχετε ένα έτοιμο για δημοσίευση αρχείο `.md` και ένα φάκελο με PNGs τέλειου μεγέθους, όλα παραγόμενα από κώδικα C#.

## Τι Θα Μάθετε

* Πώς να **convert word to markdown** χρησιμοποιώντας Aspose.Words.
* Τα ακριβή βήματα για **extract images from docx** ενώ ελέγχετε το DPI.
* Τρόποι για να απαντήσετε στο “**how to set image dpi**” στον κώδικα.
* Συμβουλές για τη διαχείριση μεγάλων εγγράφων, ελλιπών εικόνων και προσαρμοσμένων φακέλων εξόδου.
* Ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

### Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+).
* Ένα ενεργό license Aspose.Words for .NET (μπορείτε να ξεκινήσετε με τη δωρεάν evaluation).
* Βασική εξοικείωση με C# και τη γραμμή εντολών.
* Έ αρχείο DOCX που περιέχει τουλάχιστον μία εικόνα ή μια εξίσωση—το δείγμα μας `input.docx` αρκεί.

> **Συμβουλή επαγγελματία:** Αν βρίσκεστε σε CI/CD pipeline, κρατήστε το αρχείο license εκτός ελέγχου έκδοσης και φορτώστε το από μια μεταβλητή περιβάλλοντος.

## Βήμα 1 – Εγκατάσταση Aspose.Words και Ρύθμιση του Έργου

Πρώτα απ' όλα, χρειάζεστε τη βιβλιοθήκη που κάνει τη βαριά δουλειά.

```bash
dotnet new console -n WordToMarkdown
cd WordToMarkdown
dotnet add package Aspose.Words
```

Αυτό δημιουργεί μια ελάχιστη εφαρμογή console με όνομα **WordToMarkdown** και κατεβάζει το πιο πρόσφατο πακέτο Aspose.Words από το NuGet.

> **Γιατί Aspose.Words;** Υποστηρίζει εξαγωγή εικόνων χωρίς απώλειες, κλιμάκωση DPI και εγγενή εξαγωγή LaTeX για Office Math—χαρακτηριστικά που οι περισσότερες δωρεάν βιβλιοθήκες δεν έχουν.

## Βήμα 2 – Φόρτωση του Πηγαίου Εγγράφου

Τώρα διαβάζουμε το αρχείο `.docx` που περιέχει τις εικόνες που θέλετε να εξάγετε.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Replace with the actual path on your machine
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document – this also parses all embedded resources
Document sourceDocument = new Document(inputPath);
```

Αν το αρχείο δεν βρεθεί, το Aspose ρίχνει `FileNotFoundException`. Η έγκαιρη σύλληψή του παρέχει πιο σαφές μήνυμα σφάλματος για τους τελικούς χρήστες.

```csharp
if (!File.Exists(inputPath))
{
    Console.Error.WriteLine($"❌ Cannot locate '{inputPath}'. Ensure the file exists.");
    return;
}
```

## Βήμα 3 – Ρύθμιση των Markdown Save Options (Συμπεριλαμβανομένου του DPI)

Εδώ απαντάμε στο **how to set image dpi**. Από προεπιλογή, το Aspose εξάγει εικόνες στα 96 DPI, κάτι που φαίνεται θολό σε οθόνες retina. Ορίζοντας το `ImageResolution` σε **300** παίρνετε εικόνες ποιότητας εκτύπωσης.

```csharp
// Configure the export settings
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // Export each image at 300 DPI – ideal for most web and print scenarios
    ImageResolution = 300,

    // Turn Office Math equations into LaTeX so they render nicely in Markdown
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: store images in a sub‑folder called "images"
    ImagesFolder = "images"
};
```

> **Γιατί LaTeX;** Οι περισσότεροι renderers Markdown (GitHub, GitLab, MkDocs) κατανοούν τη σύνταξη `$…$`, παρέχοντάς σας καθαρές, κλιμακώσιμες εξισώσεις χωρίς πρόσθετα plugins.

## Βήμα 4 – Αποθήκευση του Εγγράφου ως Markdown

Με τις επιλογές έτοιμες, μπορούμε τελικά να **export word images** και το υπόλοιπο περιεχόμενο.

```csharp
// Destination markdown file
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.md");

// Perform the conversion
sourceDocument.Save(outputPath, markdownOptions);

Console.WriteLine($"✅ Conversion complete! Markdown saved to '{outputPath}'.");
Console.WriteLine($"🖼️ Extracted images are in the '{markdownOptions.ImagesFolder}' folder.");
```

Η εκτέλεση του προγράμματος παράγει δύο τελικά προϊόντα:

1. `output.md` – η πλήρης αναπαράσταση σε Markdown του αρχικού αρχείου Word.
2. `images/` – ένας φάκελος που περιέχει κάθε εικόνα από το DOCX, τώρα σε PNG 300 DPI (ή στην αρχική μορφή αν ήταν ήδη υψηλής ανάλυσης).

## Βήμα 5 – Επαλήθευση του Αποτελέσματος (Προαιρετικό αλλά Συνιστάται)

Μια γρήγορη έλεγχος λογικής σας προστατεύει από δυσάρεστες εκπλήξεις αργότερα.

```csharp
// Verify that at least one image was extracted
int imageCount = Directory.GetFiles(markdownOptions.ImagesFolder).Length;
if (imageCount == 0)
{
    Console.WriteLine("⚠️ No images were found. Did the source DOCX contain pictures?");
}
else
{
    Console.WriteLine($"🔎 Found {imageCount} image(s) at 300 DPI.");
}
```

Ανοίξτε το `output.md` στον αγαπημένο σας επεξεργαστή. Θα πρέπει να δείτε ετικέτες εικόνας Markdown όπως:

```markdown
![Figure 1](images/Image_0.png)
```

Αν συμπεριλάβετε εξισώσεις, θα εμφανιστούν ως μπλοκ LaTeX:

```markdown
$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

## Περιπτώσεις Άκρων & Συχνές Ερωτήσεις

### Τι γίνεται αν το DOCX περιέχει πολύ μεγάλες εικόνες;

Το Aspose αυτόματα μειώνει το δείγμα των εικόνων που υπερβαίνουν το ζητούμενο DPI, αλλά μπορείτε να ελέγξετε το μέγιστο πλάτος/ύψος χρησιμοποιώντας την ιδιότητα `ImageSize` στο `MarkdownSaveOptions`. Παράδειγμα:

```csharp
markdownOptions.ImageSize = new Size(1200, 0); // 1200px wide, preserve aspect ratio
```

### Πώς να διαχειριστώ ένα DOCX χωρίς εικόνες;

Η μετατροπή λειτουργεί ακόμη· θα λάβετε απλώς ένα αρχείο Markdown χωρίς ετικέτες `![...]`. Το βήμα επαλήθευσης παραπάνω θα σας προειδοποιήσει, κάτι χρήσιμο για CI pipelines.

### Μπορώ να αλλάξω τη μορφή της εικόνας;

Ναι. Ορίστε `markdownOptions.ImageExportFormat` σε `ImageExportFormat.Jpeg`, `Png`, ή `Bmp`. Το PNG είναι προεπιλογή επειδή διατηρεί την ποιότητα χωρίς απώλειες.

### Απαιτείται το license για κλιμάκ;

Η δωρεάν evaluation license περιλαμβάνει κλιμάκωση DPI, αλλά προσθέτει μικρό υδατογράφημα στην πρώτη σελίδα. Για παραγωγική χρήση, αγοράστε license για να αφαιρέσετε το υδατογράφημα και να ξεκλειδώσετε πλήρη απόδοση.

### Πώς να το τρέξω σε Linux/macOS;

Η ίδια εφαρμογή .NET console λειτουργεί δια-πλατφόρμα. Απλώς εγκαταστήστε το .NET SDK για το λειτουργικό σας σύστημα και εκτελέστε `dotnet run`. Βεβαιωθείτε ότι οι εγγενείς εξαρτήσεις του Aspose.Words είναι διαθέσιμες· το πακέτο NuGet περιλαμβάνει όλα όσα χρειάζεστε.

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω βρίσκεται ολόκληρο το `Program.cs` που μπορείτε να ενσωματώσετε σε ένα νέο console project. Δεν λείπει κανένα τμήμα.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣  Load the source DOCX
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        if (!File.Exists(inputPath))
        {
            Console.Error.WriteLine($"❌ Cannot locate '{inputPath}'.");
            return;
        }

        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // 2️⃣  Configure Markdown export options
        // -------------------------------------------------
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            ImageResolution = 300,                     // How to set image DPI
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ImagesFolder = "images",                   // Extracted images go here
            ImageExportFormat = ImageExportFormat.Png   // Keep lossless quality
        };

        // -------------------------------------------------
        // 3️⃣  Save as Markdown
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.md");
        sourceDocument.Save(outputPath, markdownOptions);
        Console.WriteLine($"✅ Markdown saved to '{outputPath}'.");
        Console.WriteLine($"🖼️ Images saved to folder '{markdownOptions.ImagesFolder}'.");

        // -------------------------------------------------
        // 4️⃣  Quick verification (optional)
        // -------------------------------------------------
        if (Directory.Exists(markdownOptions.ImagesFolder))
        {
            int imageCount = Directory.GetFiles(markdownOptions.ImagesFolder).Length;
            Console.WriteLine(imageCount > 0
                ? $"🔎 Found {imageCount} image(s) at 300 DPI."
                : "⚠️ No images were extracted.");
        }
    }
}
```

Αποθηκεύστε το ως `Program.cs`, τρέξτε `dotnet run`, και παρακολουθήστε τη μαγεία.

## Συμπέρασμα

Μόλις σας δείξαμε πώς να **export word images** σε Markdown, **convert word to markdown**, και **extract images from docx** ελέγχοντας με ακρίβεια το DPI. Τα βασικά βήματα—εγκατάσταση Aspose.Words, φόρτωση του εγγράφου, ρύθμιση του `MarkdownSaveOptions` και αποθήκευση—είναι αρκετά απλά για ένα γρήγορο script αλλά αρκετά ισχυρά για παραγωγικές pipelines.

Από εδώ μπορείτε:

* Να περάσετε το παραγόμενο Markdown σε static‑site generator όπως Hugo ή MkDocs.
* Να προσθέσετε βήμα post‑process που μετονομάζει τις εικόνες σε πιο περιγραφικά ονόματα αρχείων.
* Να ενσωματώσετε αυτόν τον κώδικα σε Azure Function για μετατροπή εγγράφων κατά απαίτηση.

Νιώστε ελεύθεροι να πειραματιστείτε με διαφορετικές τιμές DPI, μορφές εικόνας, ή ακόμη και προρμοσμένο CSS για το παραγόμενο Markdown. Αν αντιμετωπίσετε προβλήματα, αφήστε ένα σχόλιο παρακάτω—καλή μετατροπή!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}