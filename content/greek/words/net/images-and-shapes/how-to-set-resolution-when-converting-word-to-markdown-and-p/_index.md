---
category: general
date: 2025-12-17
description: Πώς να ορίσετε την ανάλυση για εξαγωγή εικόνας κατά τη μετατροπή του
  Word σε Markdown και PDF. Μάθετε πώς να επαναφέρετε κατεστραμμένα αρχεία Word, να
  φορτώσετε docx και να μετατρέψετε docx σε PDF με το Aspose.Words.
draft: false
keywords:
- how to set resolution
- convert word to markdown
- recover corrupted word
- convert docx to pdf
- how to load docx
language: el
og_description: Πώς να ορίσετε την ανάλυση για εξαγωγή εικόνας κατά τη μετατροπή εγγράφων
  Word. Αυτός ο οδηγός δείχνει πώς να επαναφέρετε κατεστραμμένα αρχεία Word, να φορτώσετε
  docx και να τα μετατρέψετε σε Markdown και PDF.
og_title: Πώς να ορίσετε την ανάλυση – Οδηγός Word σε Markdown & PDF
tags:
- Aspose.Words
- C#
- Document Conversion
title: Πώς να ορίσετε την ανάλυση κατά τη μετατροπή του Word σε Markdown και PDF –
  Πλήρης οδηγός
url: /greek/net/images-and-shapes/how-to-set-resolution-when-converting-word-to-markdown-and-p/
---

{{< layout-start >}}

{{< layout-start >}}

# Πώς να ορίσετε την ανάλυση κατά τη μετατροπή Word σε Markdown και PDF

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε την ανάλυση** για τις εικόνες που εξάγονται από ένα έγγραφο Word; Ίσως να έχετε δοκιμάσει μια γρήγορη εξαγωγή, μόνο και μόνο για να καταλήξετε με θολές εικόνες στο Markdown ή το PDF σας. Αυτό είναι ένα κοινό πρόβλημα, ειδικά όταν το πηγαίο `.docx` είναι λίγο κακό ή ακόμη και μερικώς κατεστραμμένο.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια πλήρη, ολοκληρωμένη λύση που **ανακτά κατεστραμμένα Word** αρχεία, **φορτώνει docx**, και στη συνέχεια **μετατρέπει το Word σε Markdown** (με εικόνες υψηλής ανάλυσης) και **μετατρέπει το docx σε PDF** ενώ λαμβάνουμε υπόψη την προσβασιμότητα. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project—χωρίς να χρειάζεται να μαντεύετε την DPI των εικόνων ή να λείπουν πόροι.

> **Σύντομη ανασκόπηση:** θα χρησιμοποιήσουμε το Aspose.Words for .NET, θα ορίσουμε ανάλυση εικόνας 300 dpi, θα εξάγουμε το OfficeMath ως LaTeX, και θα δημιουργήσουμε ένα αρχείο συμβατό με PDF‑/UA. Όλα αυτά συμβαίνουν σε λίγες μόνο γραμμές C#.

---

## Τι θα χρειαστείτε

- **Aspose.Words for .NET** (v23.10 ή νεότερο). Το πακέτο NuGet είναι `Aspose.Words`.
- .NET 6+ (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7.2, αλλά τα νεότερα runtime προσφέρουν καλύτερη απόδοση).
- Ένα **κατεστραμμένο ή μερικώς κατεστραμμένο** `.docx` που θέλετε να σώσετε, ή ένα κανονικό αρχείο Word αν χρειάζεστε μόνο εικόνες υψηλής ανάλυσης.
- Ένας κενός φάκελος όπου θα αποθηκευτούν το Markdown, οι εικόνες και το PDF.  
  *(Μπορείτε να αλλάξετε τις διαδρομές στο παράδειγμα.)*

## Βήμα 1 – Πώς να φορτώσετε DOCX και να ανακτήσετε κατεστραμμένα Word αρχεία

Το πρώτο πράγμα που πρέπει να κάνετε είναι **να φορτώσετε το DOCX** με ασφάλεια. Το Aspose.Words προσφέρει μια σημαία `RecoveryMode` που λέει στη βιβλιοθήκη να αγνοεί τα κατεστραμμένα τμήματα αντί να ρίχνει εξαίρεση.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Load the potentially corrupted document using recovery mode
LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.IgnoreCorrupt };
Document document = new Document("YOUR_DIRECTORY/corrupt.docx", loadOptions);
```

> **Γιατί είναι σημαντικό:** Αν παραλείψετε το `RecoveryMode`, μια μόνο κατεστραμμένη παράγραφος μπορεί να διακόψει ολόκληρη τη μετατροπή. Το `IgnoreCorrupt` επιτρέπει στον parser να παραλείψει τα κακά τμήματα και να διατηρήσει το υπόλοιπο περιεχόμενο άθικτο—τέλειο για σενάρια «ανάκτηση κατεστραμμένου word».

## Βήμα 2 – Πώς να ορίσετε την ανάλυση για την εξαγωγή εικόνων κατά τη μετατροπή Word σε Markdown

Τώρα που το έγγραφο βρίσκεται στη μνήμη, πρέπει να πούμε στο Aspose.Words πόσο καθαρές θέλουμε να είναι οι εξαγόμενες εικόνες. Εδώ έρχεται στο προσκήνιο το **πώς να ορίσετε την ανάλυση**.

```csharp
// Prepare Markdown export options
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // Export OfficeMath as LaTeX for better compatibility with Markdown renderers
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Set a higher image resolution (300 DPI works well for most screens and print)
    ImageResolution = 300,

    // Store generated images in a dedicated folder and return the relative path
    ResourceSavingCallback = resourceInfo =>
    {
        string imageFolder = Path.Combine("YOUR_DIRECTORY/md_images");
        Directory.CreateDirectory(imageFolder); // Ensure folder exists
        string imagePath = Path.Combine(imageFolder, resourceInfo.FileName);
        File.WriteAllBytes(imagePath, resourceInfo.Content);
        // Return the path that will be written into the Markdown file
        return Path.Combine("md_images", resourceInfo.FileName);
    }
};
```

### Τι κάνει ο κώδικας

| Setting | Why it helps |
|---------|--------------|
| `OfficeMathExportMode = LaTeX` | Οι μαθηματικές εξισώσεις αποδίδονται καθαρά στα περισσότερα προβολείς Markdown. |
| `ImageResolution = 300` | Οι εικόνες 300 dpi είναι αρκετά οξίνες για PDFs και διατηρούν λογικό μέγεθος αρχείου. |
| `ResourceSavingCallback` | Σας δίνει πλήρη έλεγχο στο πού αποθηκεύονται οι εικόνες· μπορείτε ακόμη και να τις ανεβάσετε σε CDN αργότερα. |

> **Συμβουλή:** Αν χρειάζεστε υπερ‑υψηλή ποιότητα για εκτύπωση, αυξήστε το DPI στα 600. Απλώς θυμηθείτε ότι το μέγεθος του αρχείου θα αυξηθεί αναλογικά.

## Βήμα 3 – Μετατροπή Word σε Markdown (και επαλήθευση του αποτελέσματος)

Με τις επιλογές έτοιμες, η πραγματική μετατροπή είναι μια γραμμή κώδικα.

```csharp
// Save the document as Markdown
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

Μετά την εκτέλεση, θα βρείτε:

- `output.md` που περιέχει το κείμενο Markdown με συνδέσμους εικόνων όπως `![](md_images/Image_0.png)`.
- Έναν φάκελο `md_images` γεμάτο με αρχεία PNG στα 300 dpi.

Ανοίξτε το αρχείο Markdown στο VS Code ή σε οποιονδήποτε προεπισκόπηση για να επιβεβαιώσετε ότι οι εικόνες φαίνονται καθαρές και τα μαθηματικά εμφανίζονται ως μπλοκ LaTeX.

## Βήμα 4 – Πώς να μετατρέψετε DOCX σε PDF λαμβάνοντας υπόψη την προσβασιμότητα

Αν χρειάζεστε επίσης μια έκδοση PDF, το Aspose.Words σας επιτρέπει να ορίσετε τη συμμόρφωση PDF (PDF/UA για προσβασιμότητα) και να ελέγξετε πώς διαχειρίζονται τα αιωρούμενα σχήματα.

```csharp
// Configure PDF export for accessibility
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // PDF/UA ensures the file meets accessibility standards
    Compliance = PdfCompliance.PdfUa,

    // Export floating shapes as inline <span> tags for better screen‑reader support
    ExportFloatingShapesAsInlineTag = true
};

// Save the document as PDF
document.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

### Γιατί PDF/UA;

Το PDF/UA (Universal Accessibility) προσθέτει ετικέτες στο PDF με πληροφορίες δομής που βασίζονται οι βοηθητικές τεχνολογίες. Αν το κοινό σας περιλαμβάνει άτομα που χρησιμοποιούν προγράμματα ανάγνωσης οθόνης, αυτή η σημαία είναι απαραίτητη.

## Βήμα 5 – Πλήρες λειτουργικό παράδειγμα (Έτοιμο για αντιγραφή‑επικόλληση)

Παρακάτω είναι το πλήρες πρόγραμμα που ενώνει όλα τα παραπάνω. Μπορείτε να το ενσωματώσετε σε μια εφαρμογή console και να το εκτελέσετε.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the document (recover corrupted word) ----------
        LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.IgnoreCorrupt };
        Document doc = new Document("YOUR_DIRECTORY/corrupt.docx", loadOptions);

        // ---------- Step 2: Set resolution for Markdown image export ----------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ImageResolution = 300,
            ResourceSavingCallback = info =>
            {
                string imgFolder = Path.Combine("YOUR_DIRECTORY/md_images");
                Directory.CreateDirectory(imgFolder);
                string imgPath = Path.Combine(imgFolder, info.FileName);
                File.WriteAllBytes(imgPath, info.Content);
                // Relative path used inside the Markdown file
                return Path.Combine("md_images", info.FileName);
            }
        };

        // ---------- Step 3: Save as Markdown ----------
        doc.Save("YOUR_DIRECTORY/output.md", mdOptions);
        Console.WriteLine("Markdown export completed.");

        // ---------- Step 4: Configure PDF export (convert docx to pdf) ----------
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUa,
            ExportFloatingShapesAsInlineTag = true
        };

        // ---------- Step 5: Save as PDF ----------
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
        Console.WriteLine("PDF export completed.");
    }
}
```

**Αναμενόμενα αποτελέσματα**

- `output.md` – ένα καθαρό αρχείο Markdown με εικόνες PNG υψηλής ανάλυσης.
- `md_images/` – φάκελος που περιέχει PNG 300 dpi.
- `output.pdf` – ένα προσβάσιμο αρχείο PDF/UA που μπορεί να ανοιχθεί στο Adobe Reader χωρίς προειδοποιήσεις.

## Συχνές ερωτήσεις & Ακραίες περιπτώσεις

### Τι γίνεται αν το πηγαίο DOCX περιέχει ενσωματωμένες εικόνες EMF ή WMF;

Το Aspose.Words αυτόματα rasterizes αυτές τις διανυσματικές μορφές χρησιμοποιώντας το DPI που καθορίζετε. Αν χρειάζεστε πραγματικό διανυσματικό αποτέλεσμα στο PDF, ορίστε `PdfSaveOptions.VectorResources = true` και κρατήστε τη ανάλυση εικόνας χαμηλή—τα διανυσματικά γραφικά δεν θα υποστούν απώλεια DPI.

### Το έγγραφό μου έχει εκατοντάδες εικόνες· η μετατροπή είναι αργή.

Το bottleneck είναι συνήθως το βήμα rasterization των εικόνων. Μπορείτε να βελτιώσετε την ταχύτητα:

1. **Αύξηση του thread pool** (`Parallel.ForEach` πάνω από `ResourceSavingCallback`) – αλλά προσέξτε το I/O του δίσκου.
2. **Caching** (αποθήκευση) ήδη μετατρεπόμενων εικόνων αν εκτελείτε τη μετατροπή πολλές φορές στο ίδιο πηγαίο αρχείο.

### Πώς να διαχειριστώ αρχεία DOCX προστατευμένα με κωδικό;

Απλώς προσθέστε τον κωδικό στο `LoadOptions`:

```csharp
LoadOptions opts = new LoadOptions { Password = "mySecret" };
Document protected = new Document("secret.docx", opts);
```

### Μπορώ να εξάγω το Markdown απευθείας σε αποθετήριο συμβατό με GitHub;

Ναι. Μετά τη μετατροπή, κάντε commit το `output.md` και το φάκελο `md_images`. Οι σχετικοί σύνδεσμοι που δημιουργεί το Aspose.Words λειτουργούν τέλεια στο GitHub Pages.

## Συμβουλές για παραγωγικές γραμμές εργασίας

- **Καταγραφή της κατάστασης ανάκτησης.** Το `LoadOptions` παρέχει ένα `DocumentLoadingException` που μπορείτε να πιάσετε για να καταγράψετε ποια τμήματα παραλήφθηκαν.
- **Επικύρωση της συμμόρφωσης PDF/UA** χρησιμοποιώντας εργαλεία όπως το “Preflight” του Adobe Acrobat ή τη βιβλιοθήκη ανοιχτού κώδικα `veraPDF`.
- **Συμπίεση PNG** μετά την εξαγωγή αν η αποθήκευση είναι πρόβλημα. Εργαλεία όπως το `pngquant` μπορούν να κληθούν από C# μέσω `Process.Start`.
- **Παραμετροποίηση DPI** σε αρχείο ρυθμίσεων ώστε να μπορείτε να εναλλάσσετε μεταξύ “web” (150 dpi) και “print” (300 dpi) χωρίς αλλαγές κώδικα.

## Συμπέρασμα

Καλύψαμε **πώς να ορίσετε την ανάλυση** για την εξαγωγή εικόνων, παρουσιάσαμε έναν αξιόπιστο τρόπο για **ανάκτηση κατεστραμμένων Word** αρχείων, δείξαμε τα ακριβή βήματα για **φόρτωση docx**, και τελικά περάσαμε από το **μετατροπή word σε markdown** και το **μετατροπή docx σε pdf** με ρυθμίσεις προσβασιμότητας. Το πλήρες snippet κώδικα είναι έτοιμο για αντιγραφή, επικόλληση και εκτέλεση—χωρίς κρυφές εξαρτήσεις, χωρίς ασαφείς «δείτε τα docs» συντομεύσεις.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

- Εξαγωγή απευθείας σε **HTML** με τις ίδιες ρυθμίσεις ανάλυσης.
- Χρήση του **Aspose.PDF** για συγχώνευση του παραγόμενου PDF με άλλα έγγραφα.
- Αυτοματοποίηση αυτής της ροής εργασίας σε Azure Function ή AWS Lambda για μετατροπή κατά απαίτηση.

Δοκιμάστε το, προσαρμόστε το DPI ώστε να ταιριάζει στις ανάγκες σας, και αφήστε τις εικόνες υψηλής ανάλυσης να μιλήσουν από μόνες τους. Καλό κώδικα!

{{< layout-end >}}

{{< layout-end >}}