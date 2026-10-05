---
category: general
date: 2026-02-24
description: Μάθετε πώς να χρησιμοποιείτε τις επιλογές φόρτωσης Aspose για να ανακτήσετε
  κατεστραμμένα DOCX, να μετατρέψετε docx σε markdown και να μετατρέψετε το Word σε
  PDF με εξισώσεις LaTeX.
draft: false
keywords:
- aspose load options
- convert docx to markdown
- convert word to pdf
- recover corrupted docx
- export equations as latex
language: el
og_description: Κατακτήστε τις επιλογές φόρτωσης Aspose για την αποκατάσταση κατεστραμμένων
  αρχείων DOCX, τη μετατροπή docx σε markdown και την εξαγωγή εξισώσεων ως LaTeX,
  ενώ παράγετε αρχεία PDF/UA‑2.
og_title: Επιλογές Φόρτωσης Aspose – Μετατροπή DOCX σε Markdown & PDF
tags:
- Aspose.Words
- C#
- Document Conversion
title: Επιλογές Φόρτωσης Aspose – Μετατροπή DOCX σε Markdown & PDF
url: /el/net/programming-with-loadoptions/aspose-load-options-convert-docx-to-markdown-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Μετατροπή DOCX σε Markdown & PDF

Έχετε αναρωτηθεί ποτέ πώς οι **aspose load options** σας επιτρέπουν να διασώσετε ένα κατεστραμμένο αρχείο Word και να το μετατρέψετε σε καθαρό Markdown ή σε συμβατό PDF; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν προβλήματα όταν ένα DOCX έρχεται κατεστραμμένο ή όταν οι εξισώσεις εξαφανίζονται κατά τη μετατροπή. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια πλήρη, έτοιμη προς εκτέλεση λύση C# που όχι μόνο *recovers corrupted docx* αλλά επίσης **convert docx to markdown** και **convert word to pdf** ενώ **export equations as latex**.

Θα καλύψουμε τα πάντα, από τη ρύθμιση της λειτουργίας ανάκτησης έως τη μεταφόρτωση των εξαγόμενων εικόνων σε ένα cloud bucket, και τελικά τη δημιουργία ενός αρχείου PDF/UA‑2 που πληροί τα πρότυπα προσβασιμότητας. Στο τέλος, θα έχετε μια ενιαία βάση κώδικα που διαχειρίζεται και τις δύο μετατροπές με λίγες μόνο γραμμές ρυθμίσεων.

> **What you’ll get:**  
> • Ένα αξιόπιστο τρόπο φόρτωσης οποιουδήποτε DOCX, ακόμη και αν είναι μερικώς κατεστραμμένο.  
> • Έξοδος Markdown που διατηρεί τις εξισώσεις OfficeMath ως LaTeX.  
> • Έξοδος PDF/UA‑2 με τα αιωρούμενα σχήματα διατηρημένα ως inline tags.  
> • Μια επαναχρησιμοποιήσιμη callback για μεταφόρτωση εικόνων σε cloud storage.

---

## Prerequisites

- **Aspose.Words for .NET** (v23.12 ή νεότερη).  
- .NET 6+ (οποιοδήποτε πρόσφατο SDK λειτουργεί).  
- Ένα SDK cloud storage της επιλογής σας (το παράδειγμα χρησιμοποιεί μια placeholder μέθοδο).  
- Βασική εξοικείωση με C# και Visual Studio ή VS Code.

Αν δεν έχετε εγκαταστήσει ακόμη το Aspose.Words, εκτελέστε:

```bash
dotnet add package Aspose.Words
```

---

## Βήμα 1: Φόρτωση του Εγγράφου με Aspose Load Options

Το πρώτο που χρειάζεστε είναι ένας αξιόπιστος τρόπος ανοίγματος ενός πιθανώς κατεστραμμένου DOCX. Εδώ οι **aspose load options** δείχνουν την αξία τους—σας επιτρέπουν να πείτε στη βιβλιοθήκη να προσπαθήσει ανάκτηση αντί να πετάξει εξαίρεση.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Configure LoadOptions to recover corrupted documents.
LoadOptions loadOptions = new LoadOptions
{
    // RecoveryMode.Recover tells Aspose to salvage as much as possible.
    RecoveryMode = RecoveryMode.Recover
};

// Load the source file. Replace the path with your own.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Why this matters:**  
Όταν ένα αρχείο Word είναι κομμένο ή περιέχει κακοδιατυπωμένο XML, ο προεπιλεγμένος φορτωτής διακόπτει. Ενεργοποιώντας το `RecoveryMode.Recover`, το Aspose αναλύει ό,τι μπορεί, παραλείπει τα κατεστραμμένα τμήματα και σας δίνει ένα χρήσιμο αντικείμενο `Document`. Αυτό αποτελεί τη ραχοκοκαλιά του σεναρίου *recover corrupted docx*.

---

## Βήμα 2: Ρύθμιση της Μετατροπής σε Markdown (Export Equations as LaTeX)

Τώρα που το έγγραφο βρίσκεται στη μνήμη, μπορούμε να διαμορφώσουμε πώς θα αποθηκευτεί ως Markdown. Δύο πράγματα είναι κρίσιμα:

1. **OfficeMathExportMode.LaTeX** – εξασφαλίζει ότι κάθε μαθηματική εξίσωση μετατρέπεται σε αποσπάσματα LaTeX, διατηρώντας τη σημασιολογία τους.  
2. **ResourceSavingCallback** – ένα hook που μας επιτρέπει να ανεβάσουμε τις εξαγόμενες εικόνες σε cloud bucket αντί να τις γράψουμε τοπικά.

```csharp
using Aspose.Words.Saving;

// Prepare Markdown save options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This converts OfficeMath objects to LaTeX.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Hook to upload images to the cloud.
    ResourceSavingCallback = new CloudImageCallback()
};

// Save as Markdown.
document.Save("YOUR_DIRECTORY/result.md", markdownOptions);
```

**Pro tip:** Αν δεν χρειάζεστε LaTeX, αλλάξτε το `OfficeMathExportMode` σε `Image`. Αλλά για επιστημονικά έγγραφα, το LaTeX είναι πολύ πιο φορητό.

---

## Βήμα 3: Υλοποίηση του Cloud Image Callback

Το Aspose καλεί το `IResourceSavingCallback.ResourceSaving` για κάθε εξωτερικό πόρο (εικόνες, διαγράμματα κ.λπ.). Παρακάτω είναι μια ελάχιστη υλοποίηση που προσποιείται ότι ανεβάζει το stream σε CDN και επιστρέφει ένα δημόσιο URL.

```csharp
using Aspose.Words.Saving;
using System.IO;

public class CloudImageCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Upload the image stream to your cloud storage and get a URL.
        string url = UploadToCloud(args.Stream, args.FileName);

        // Point the Markdown image reference to the CDN URL.
        args.Uri = url;

        // Prevent Aspose from writing a local copy.
        args.KeepOriginalDocumentUri = false;
    }

    private string UploadToCloud(Stream data, string name)
    {
        // Replace this stub with your actual SDK call.
        // For demo purposes we just return a placeholder.
        return $"https://cdn.example.com/{name}";
    }
}
```

**What if you don’t have a cloud bucket?**  
Μπορείτε απλώς να ορίσετε `args.Uri = $"images/{args.FileName}"` και να αφήσετε το Aspose να γράψει τα αρχεία δίπλα στο αρχείο Markdown. Το callback σας δίνει πλήρη έλεγχο.

---

## Βήμα 4: Ρύθμιση της Μετατροπής σε PDF (Convert Word to PDF with UA‑2 Compliance)

Όταν το ίδιο έγγραφο πρέπει να γίνει PDF, ειδικά ένα που πρέπει να πληροί πρότυπα προσβασιμότητας, το Aspose προσφέρει το `PdfSaveOptions`. Δύο ρυθμίσεις είναι ουσιώδεις για καθαρή μετατροπή:

- **Compliance = PdfCompliance.PdfUa2** – παράγει ένα αρχείο PDF/UA‑2, το ISO πρότυπο για προσβάσιμα PDFs.  
- **ExportFloatingShapesAsInlineTag = true** – διατηρεί τα αιωρούμενα σχήματα (όπως πλαίσια κειμένου) στη σωστή σειρά.

```csharp
using Aspose.Words.Saving;

// Prepare PDF save options.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // Enforce PDF/UA‑2 compliance.
    Compliance = PdfCompliance.PdfUa2,

    // Preserve layout of floating shapes.
    ExportFloatingShapesAsInlineTag = true
};

// Save as PDF.
document.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
```

**Why this works:**  
Ορίζοντας το `Compliance` το Aspose ενσωματώνει τις απαιτούμενες ετικέτες, εναλλακτικό κείμενο και δομικά στοιχεία. Η σημαία `ExportFloatingShapesAsInlineTag` εξασφαλίζει ότι τα σχήματα που διαφορετικά θα «πλέουν» πάνω από το κείμενο αγκυροβολούνται inline, αποτρέποντας απρόσμενες αλλαγές διάταξης στο τελικό PDF.

---

## Βήμα 5: Πλήρες Παράδειγμα End‑to‑End

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το ολοκληρωμένο πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια console εφαρμογή.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Saving;

namespace AsposeDocxConversion
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load with recovery.
            LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 2️⃣ Convert to Markdown (export equations as LaTeX, upload images).
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                ResourceSavingCallback = new CloudImageCallback()
            };
            doc.Save("YOUR_DIRECTORY/result.md", mdOptions);
            Console.WriteLine("✅ Markdown saved.");

            // 3️⃣ Convert to PDF/UA‑2 (preserve floating shapes).
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                Compliance = PdfCompliance.PdfUa2,
                ExportFloatingShapesAsInlineTag = true
            };
            doc.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
            Console.WriteLine("✅ PDF/UA‑2 saved.");
        }
    }

    // Callback for uploading images.
    public class CloudImageCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string url = UploadToCloud(args.Stream, args.FileName);
            args.Uri = url;
            args.KeepOriginalDocumentUri = false;
        }

        private string UploadToCloud(Stream data, string name)
        {
            // Insert real SDK code here.
            return $"https://cdn.example.com/{name}";
        }
    }
}
```

**Expected output:**  
Η εκτέλεση του προγράμματος δημιουργεί δύο αρχεία στο `YOUR_DIRECTORY`:

- `result.md` – ένα έγγραφο Markdown όπου κάθε εξίσωση εμφανίζεται ως `$$\LaTeX$$` και οι σύνδεσμοι εικόνων δείχνουν στο `https://cdn.example.com/...`.  
- `result.pdf` – ένα αρχείο PDF/UA‑2 συμβατό που μπορεί να ανοιχθεί στο Adobe Reader με τον έλεγχο προσβασιμότητας να περνάει.

Μπορείτε να ανοίξετε το Markdown σε οποιονδήποτε επεξεργαστή ή να το τροφοδοτήσετε σε static‑site generator, και το PDF μπορεί να διανεμηθεί σε χρήστες που χρειάζονται προσβάσιμη μορφή.

---

## Frequently Asked Questions & Edge Cases

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το DOCX είναι εντελώς ακατάγνωστο;** | Ακόμα και με `RecoveryMode.Recover`, ένα εντελώς κατεστραμμένο αρχείο μπορεί να ρίξει `FileCorruptedException`. Τυλίξτε την κλήση φόρτωσης σε `try/catch` και εμφανίστε μια φιλική σελίδα σφάλματος. |
| **Μπορώ να αλλάξω τη μορφή της εικόνας κατά το ανέβασμα;** | Ναι. Μέσα στη `UploadToCloud` μπορείτε να χρησιμοποιήσετε μια βιβλιοθήκη επεξεργασίας εικόνας (π.χ., ImageSharp) για αλλαγή μεγέθους ή μετατροπή σε WebP πριν την αποστολή στο CDN. |
| **Χρειάζεται άδεια για το Aspose.Words;** | Η δωρεάν δοκιμή λειτουργεί για έως 20 σελίδες. Για παραγωγική χρήση, μια εμπορική άδεια αφαιρεί το υδατογράφημα αξιολόγησης και ξεκλειδώνει όλες τις λειτουργίες. |
| **Τι αν θέλω να διατηρήσω τις εξισώσεις ως εικόνες αντί για LaTeX;** | Αλλάξτε το `OfficeMathExportMode` σε `Image` στα `MarkdownSaveOptions`. Το callback θα λάβει τότε ροές PNG που μπορείτε να ανεβάσετε. |
| **Πώς προσθέτω προσαρμοσμένα μεταδεδομένα στο PDF;** | Χρησιμοποιήστε `pdfOptions.CustomProperties.Add("Author", "Your Name")` πριν καλέσετε το `Save`. |

---

## 🎯 Wrap‑Up

Δείξαμε πώς οι **aspose load options** σας δίνουν τη δυνατότητα να **recover corrupted docx**, **convert docx to markdown**, και **convert word to pdf** ενώ **export equations as latex**. Η προσέγγιση είναι modular: μπορείτε να αντικαταστήσετε το image‑upload callback, να αλλάξετε το επίπεδο συμμόρφωσης, ή ακόμη και να προσθέσετε ένα βήμα DOCX‑to‑HTML με παρόμοιες επιλογές.

Επόμενα βήματα που μπορείτε να εξερευνήσετε:

- Ενσωμάτωση αυτού του pipeline σε ASP .NET Core API ώστε οι χρήστες να ανεβάζουν αρχεία και να λαμβάνουν αμέσως τόσο Markdown όσο και PDF.  
- Αντικατάσταση του placeholder CDN URL με κλήσεις Azure Blob Storage ή Amazon S3 SDK.  
- Προσθήκη βήματος post‑processing που τρέχει έναν Markdown linter για καθαρή έξοδο.  

Πειραματιστείτε—ίσως προσθέσετε εξαγωγή πίνακα σε CSV ή προσαρμοσμένο υποσέλιδο PDF. Το Aspose.Words API είναι αρκετά ευέλικτο για τις περισσότερες ανάγκες αυτοματοποίησης εγγράφων.

**Happy coding!** Αν αντιμετωπίσετε κάποιο πρόβλημα, αφήστε ένα σχόλιο παρακάτω ή απευθυνθείτε στα φόρουμ της κοινότητας Aspose.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}