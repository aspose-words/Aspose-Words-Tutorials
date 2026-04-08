---
category: general
date: 2026-04-07
description: Αποθηκεύστε το Word ως Markdown και εξάγετε εικόνες από το docx χρησιμοποιώντας
  μια κλήση επιστροφής. Μάθετε πώς να χρησιμοποιείτε την κλήση επιστροφής για να αποθηκεύετε
  αποδοτικά το φάκελο εικόνων του Markdown.
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: el
og_description: Αποθηκεύστε το Word ως Markdown και εξάγετε εικόνες από docx χρησιμοποιώντας
  callback. Αυτός ο οδηγός δείχνει πώς να χρησιμοποιήσετε το callback για να δημιουργήσετε
  έναν φάκελο εικόνων markdown.
og_title: Αποθήκευση Word ως Markdown – Πλήρης Οδηγός Βήμα‑βήμα
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: Αποθήκευση του Word ως Markdown με Προσαρμοσμένο Φάκελο Εικόνων – Πλήρης Οδηγός
url: /el/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Word ως Markdown – Πλήρης Οδηγός Βήμα‑βήμα

Έχετε χρειαστεί ποτέ να **αποθηκεύσετε Word ως Markdown** αλλά δεν ήξερες τι να κάνετε με τις ενσωματωμένες εικόνες; Δεν είστε μόνοι. Σε πολλά έργα το αποτέλεσμα σε markdown φαίνεται τέλειο—*μέχρι* να συνειδητοποιήσετε ότι οι σύνδεσμοι εικόνων είναι σπασμένοι επειδή τα αρχεία δεν έφυγαν ποτέ από το πακέτο Word.  

Το καλό νέο είναι ότι το Aspose.Words σας παρέχει έναν καθαρό τρόπο να **εξάγετε εικόνες από docx** και να τις τοποθετήσετε ακριβώς εκεί που θέλετε, χρησιμοποιώντας ένα **callback** που σας επιτρέπει να ελέγχετε το φάκελο εικόνων του markdown. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, από τη φόρτωση ενός αρχείου `.docx` μέχρι το τελικό αποτέλεσμα: ένας τακτοποιημένος φάκελος PNG (ή όποια μορφή έχετε) και ένα αρχείο markdown που δείχνει σε αυτές.

Στο τέλος αυτού του οδηγού θα μπορείτε να:

* Μετατρέψετε οποιοδήποτε έγγραφο Word σε Markdown με μία μόνο γραμμή κώδικα.  
* Αυτόματα αποθηκεύσετε κάθε εικόνα σε έναν αφιερωμένο υπο‑φάκελο `images`.  
* Προσαρμόσετε τα ονόματα αρχείων ώστε να μην συγκρούονται, ακόμη και όταν η πηγή περιέχει δεκάδες εικόνες.  

Χωρίς εξωτερικά scripts, χωρίς χειροκίνητη αντιγραφή‑επικόλληση—μόνο καθαρό C# και Aspose.Words.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

* **Aspose.Words for .NET** (η πιο πρόσφατη σταθερή έκδοση· τη στιγμή της συγγραφής είναι η 24.9).  
* Ένα περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή το `dotnet` CLI).  
* Ένα έγγραφο Word (`.docx`) που περιέχει τουλάχιστον μία εικόνα—π.χ. `DocWithImages.docx`.  

Αν δεν έχετε χρησιμοποιήσει ποτέ το Aspose.Words, μην ανησυχείτε. Η βιβλιοθήκη είναι πλήρως διαχειριζόμενη, δεν απαιτεί COM interop και λειτουργεί σε .NET 6+ καθώς και σε .NET Framework 4.8.

## Βήμα 1 – Δημιουργία του Project και Εγκατάσταση του Πακέτου

Αρχικά, δημιουργήστε μια νέα εφαρμογή console (ή προσθέστε τον κώδικα σε υπάρχον project).

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **Συμβουλή:** Αν στοχεύετε .NET 6, το προεπιλεγμένο `Program.cs` χρησιμοποιεί ήδη top‑level statements, κάτι που κρατά το παράδειγμα σύντομο.

## Βήμα 2 – Δημιουργία Callback για Έλεγχο της Αποθήκευσης Εικόνων

Το Aspose.Words καλεί το `IResourceSavingCallback.ResourceSaving` για κάθε εξωτερικό πόρο που χρειάζεται να γράψει (εικόνες, CSS κ.λπ.). Υλοποιώντας αυτή τη διεπαφή αποκτούμε πλήρη εξουσία πάνω στο **πώς θα δημιουργηθεί ο φάκελος εικόνων του markdown**.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### Γιατί να χρησιμοποιήσετε ένα callback;

* **Ακριβής έλεγχος** – εσείς αποφασίζετε τη δομή φακέλων και το σχήμα ονοματοδοσίας.  
* **Απόδοση** – γράφετε το stream μία φορά, αποφεύγοντας το fallback διπλής εγγραφής της βιβλιοθήκης.  
* **Ευελιξία** – μπορείτε να προσθέσετε logging, βελτιστοποίηση εικόνων ή ακόμη και ανέβασμα σε cloud storage σε αυτό το σημείο.

## Βήμα 3 – Φόρτωση του Εγγράφου Word

Τώρα που το callback είναι έτοιμο, αρκεί να κατευθύνουμε το Aspose.Words στο αρχείο προέλευσης.

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **Τι γίνεται αν το αρχείο δεν βρεθεί;**  
> Το `Document` θα ρίξει `FileNotFoundException`. Τυλίξτε τη φόρτωση σε `try/catch` αν χρησιμοποιείτε δυναμικές διαδρομές.

## Βήμα 4 – Ρύθμιση του MarkdownSaveOptions

Η κλάση `MarkdownSaveOptions` μας επιτρέπει να συνδέσουμε το callback που μόλις δημιουργήσαμε. Επίσης ορίζουμε το φάκελο όπου θα ζήσουν οι εικόνες, σχετικό με το αρχείο markdown.

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

Η ιδιότητα `ImagesFolder` λέει στο Aspose να δημιουργήσει συνδέσμους markdown όπως `![Alt text](images/img_123.png)`. Επειδή επίσης ορίσαμε `ResourceFileName` μέσα στο callback, το πραγματικό αρχείο αποθηκεύεται ακριβώς εκεί.

## Βήμα 5 – Αποθήκευση ως Markdown και Έλεγχος του Αποτελέσματος

Τέλος, γράφουμε το αρχείο markdown. Το callback θα έχει ήδη γεμίσει τον υπο‑φάκελο `images`.

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος θα εμφανίσει κάτι σαν:

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

Ανοίξτε το `Doc.md` σε οποιονδήποτε προβολέα markdown· θα δείτε συνδέσμους εικόνων που δείχνουν σωστά στον φάκελο `images`.

---

## Συχνές Ερωτήσεις (FAQ)

### Πώς να **εξάγετε εικόνες από docx** χωρίς μετατροπή σε markdown;

Μπορείτε να επαναχρησιμοποιήσετε το ίδιο `MyMarkdownResourceCallback`, αλλά να το περάσετε στο `doc.Save("images.zip", SaveFormat.Zip)`. Το callback θα ενεργοποιείται για κάθε εικόνα, επιτρέποντάς σας να τις τοποθετήσετε όπου θέλετε.

### Τι γίνεται αν χρειάζομαι **διαφορετικές μορφές εικόνων**;

Το `args.FileName` περιέχει ήδη την αρχική επέκταση (`.png`, `.jpg`, κ.λπ.). Αν πρέπει να μετατρέψετε όλες τις εικόνες σε μία μορφή, προσθέστε βήμα μετατροπής μέσα στο `ResourceSaving` πριν γράψετε το stream.

### Μπορώ να **προσαρμόσω το φάκελο εικόνων markdown** ανά έγγραφο;

Απόλυτα. Το callback λαμβάνει τη διαδρομή φακέλου μέσω του constructor, οπότε μπορείτε να δημιουργήσετε ένα νέο callback με διαφορετικό φάκελο για κάθε έγγραφο σε batch διαδικασία.

### Λειτουργεί αυτό με **μεγάλα έγγραφα** (εκατοντάδες εικόνες);

Ναι. Το callback μεταφέρει την εικόνα απευθείας στο δίσκο, κρατώντας τη χρήση μνήμης χαμηλή. Απλώς βεβαιωθείτε ότι ο προορισμός έχει αρκετό χώρο και ότι δεν υπερβαίνετε τα όρια ανοιγμάτων αρχείων του λειτουργικού συστήματος.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το ολοκληρωμένο πρόγραμμα, έτοιμο για αντιγραφή‑και‑επικόλληση. Αντικαταστήστε το `YOUR_DIRECTORY` με μια απόλυτη ή σχετική διαδρομή που ταιριάζει στο περιβάλλον σας.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

Εκτελέστε το πρόγραμμα (`dotnet run`) και θα δείτε ένα φρέσκο `Doc.md` δίπλα σε έναν υπο‑φάκελο `images` που περιέχει

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}