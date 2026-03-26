---
category: general
date: 2026-03-25
description: Μετατρέψτε το DOCX σε Markdown γρήγορα, εξάγοντας εικόνες από το Word
  με το Aspose.Words. Μάθετε βήμα‑βήμα με πλήρη κώδικα.
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: el
og_description: Μετατρέψτε DOCX σε Markdown και εξάγετε εικόνες από το Word με το
  Aspose.Words. Ακολουθήστε αυτό το πλήρες σεμινάριο για μια έτοιμη προς εκτέλεση
  λύση.
og_title: Μετατροπή DOCX σε Markdown σε C# – Οδηγός βήμα‑προς‑βήμα
tags:
- Aspose.Words
- C#
- Markdown
title: Μετατροπή DOCX σε Markdown σε C# – Πλήρης Οδηγός
url: /el/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή DOCX σε Markdown με Aspose.Words

Έχετε χρειαστεί ποτέ να **μετατρέψετε DOCX σε markdown** αλλά δεν ήξερες πώς να διατηρήσετε τις ενσωματωμένες εικόνες; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν προσπαθούν να μεταφέρουν περιεχόμενο Word σε έναν static‑site generator ή σε ένα αποθετήριο τεκμηρίωσης.  
Το καλό νέο είναι ότι το Aspose.Words for .NET μπορεί να κάνει το δύσκολο μέρος για εσάς, και με μια μικρή callback μπορείτε επίσης να **εξάγετε εικόνες από αρχεία Word** ταυτόχρονα.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα που φορτώνει ένα `.docx`, το αποθηκεύει ως αρχείο Markdown και γράφει κάθε εικόνα σε έναν αφιερωμένο φάκελο. Στο τέλος θα έχετε μια έτοιμη για εκτέλεση εφαρμογή console που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

> **Συμβουλή:** Αν χρειάζεστε μόνο το κείμενο και δεν σας ενδιαφέρουν οι εικόνες, μπορείτε να παραλείψετε εντελώς το `ResourceSavingCallback` – ο κώδικας θα παράγει ακόμη καθαρό Markdown.

## Τι Θα Χρειαστείτε

- **Aspose.Words for .NET** (η πιο πρόσφατη έκδοση, π.χ. 24.12). Μπορείτε να το κατεβάσετε από το NuGet: `Install-Package Aspose.Words`.
- **.NET 6.0** ή νεότερο (το API λειτουργεί και σε .NET Framework, αλλά το .NET 6 προσφέρει την καλύτερη απόδοση).
- Ένα απλό project console ή οποιονδήποτε host C# προτιμάτε.
- Ένα αρχείο Word εισόδου (`input.docx`) που περιέχει τουλάχιστον μία εικόνα ώστε να δούμε την εξαγωγή σε δράση.

Αυτό είναι όλο—χωρίς πρόσθετες βιβλιοθήκες, χωρίς περίπλοκα εργαλεία γραμμής εντολών. Ας ξεκινήσουμε.

![convert docx to markdown example](images/convert-docx-to-markdown.png)

*Image alt text: convert docx to markdown example*

## Βήμα 1 – Ρύθμιση του Project και Προσθήκη Aspose.Words

Για να κρατήσουμε τα πράγματα τακτοποιημένα, δημιουργήστε μια νέα εφαρμογή console:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

Ανοίξτε το `Program.cs` και διαγράψτε τον αυτόματα παραγόμενο κώδικα. Θα επικολλήσουμε τη πλήρη λύση αργότερα, αλλά προς το παρόν βεβαιωθείτε ότι το project κατασκευάζεται.

## Βήμα 2 – Φόρτωση του Πηγαίου DOCX

Το πρώτο που κάνουμε είναι να πούμε στο Aspose.Words να διαβάσει το αρχείο Word. Αυτή η λειτουργία είναι **γρήγορη**—η βιβλιοθήκη αναλύει τη δομή του εγγράφου χωρίς να ανοίξει το Word.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

Γιατί τυλίγουμε τη διαδρομή με `Path.Combine`; Κάνει τον κώδικα φορητό μεταξύ Windows, macOS και Linux—κάτι που θα εκτιμήσετε όταν μεταφέρετε το project σε pipeline CI.

## Βήμα 3 – Διαμόρφωση των Markdown Save Options με Callback Πόρων

Όταν ζητάτε από το Aspose.Words να αποθηκεύσει ως Markdown, κανονικά ενσωματώνει τις εικόνες ως συμβολοσειρές Base64. Αυτό είναι εντάξει για μικρά εικονίδια, αλλά για μεγαλύτερες φωτογραφίες αυξάνει δραματικά το μέγεθος του αρχείου. Αντί αυτού, προσθέτουμε ένα **resource‑saving callback** που γράφει κάθε εικόνα στο δίσκο και ενημερώνει το σύνδεσμο στο Markdown.

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

Παρατηρήστε ότι περνάμε το `resourcesDir` στον κατασκευαστή του callback—αυτό κρατά τη λογική διαδρομής εκτός του callback και κάνει την κλάση επαναχρησιμοποιήσιμη.

## Βήμα 4 – Υλοποίηση του Resource‑Saving Callback

Το callback υλοποιεί το `IResourceSavingCallback`. Για κάθε εικόνα που το Aspose.Words θέλει να γράψει, μας παρέχει ένα αντικείμενο `ResourceSavingArgs`. Εμείς αποφασίζουμε **πού** θα αποθηκευτεί το αρχείο, του δίνουμε ένα μοναδικό όνομα και στη συνέχεια λέμε στη μηχανή να παραλείψει τη προεπιλεγμένη συμπεριφορά αποθήκευσης.

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**Γιατί είναι σημαντικό:** Ορίζοντας το `args.Uri` ελέγχουμε ακριβώς πώς θα αναφέρεται η εικόνα στο τελικό αρχείο `.md`. Η σχετική διαδρομή `Resources/img_0.png` λειτουργεί είτε ανοίξετε το Markdown σε VS Code, GitHub ή σε static‑site generator.

## Βήμα 5 – Αποθήκευση του Εγγράφου ως Markdown

Τώρα το τελευταίο κομμάτι: ζητήστε από το Aspose.Words να γράψει το αρχείο Markdown. Το callback που συνδέσαμε θα ενεργοποιηθεί αυτόματα για κάθε εικόνα.

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

Όταν η γραμμή ολοκληρωθεί, θα έχετε:

- `output.md` – μια καθαρή αναπαράσταση Markdown του αρχικού περιεχομένου Word.
- Φάκελο `Resources/` – που περιέχει κάθε εικόνα που εξήχθη από το DOCX.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω είναι το **πλήρες, έτοιμο για αντιγραφή** πρόγραμμα. Αντικαταστήστε το `YOUR_DIRECTORY` με την απόλυτη ή σχετική διαδρομή που περιέχει το `input.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `Output/output.md` σε οποιονδήποτε προβολέα Markdown και θα δείτε κάτι σαν:

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

Ο φάκελος `Resources` θα περιέχει `img_0.png`, `img_1.jpg`, κ.λπ., αντιστοιχίζοντας τις εικόνες που ήταν αρχικά ενσωματωμένες στο `input.docx`.

## Συχνές Ερωτήσεις (FAQ)

**Λειτουργεί αυτό με αρχεία .doc;**  
Ναι. Το Aspose.Words μπορεί να φορτώσει `.doc`, `.docx`, `.rtf` και πολλές άλλες μορφές. Απλώς αλλάξτε την επέκταση αρχείου στο `inputPath`.

**Τι γίνεται αν χρειάζομαι απόλυτες URL για τις εικόνες;**  
Αντικαταστήστε το `args.Uri = $"Resources/{fileName}";` με κάτι όπως `args.Uri = $"https://mycdn.com/docs/{fileName}";`. Το Markdown θα αναφέρεται τότε στην απομακρυσμένη τοποθεσία.

**Μπορώ να ελέγξω την ποιότητα ή τη μορφή της εικόνας;**  
Το callback λαμβάνει το αρχικό ρεύμα εικόνας. Αν θέλετε να μετατρέψετε PNG σε JPEG, μπορείτε να φορτώσετε το ρεύμα σε `System.Drawing.Image`, να το επανακωδικοποιήσετε και να γράψετε τα νέα bytes πριν ορίσετε το `args.Uri`.

**Είναι το `ResourceSavingCallback` thread‑safe;**  
Το Aspose.Words καλεί το callback διαδοχικά για κάθε πόρο, έτσι

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}