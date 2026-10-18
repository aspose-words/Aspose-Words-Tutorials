---
category: general
date: 2026-02-18
description: Δημιουργήστε markdown από έγγραφο με εύκολα βήματα για εξαγωγή του εγγράφου
  σε markdown και αποθήκευση των εικόνων σε υποφάκελο. Μάθετε πώς να αποθηκεύσετε
  το έγγραφο ως markdown σε C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: el
og_description: Δημιουργήστε markdown από έγγραφο σε C# και μάθετε πώς να εξάγετε
  το έγγραφο σε markdown ενώ αποθηκεύετε τις εικόνες σε υποφάκελο. Ακολουθήστε τον
  οδηγό βήμα‑προς‑βήμα.
og_title: Δημιουργία markdown από έγγραφο – Εξαγωγή και αποθήκευση εικόνων
tags:
- C#
- Aspose.Words
- Markdown export
title: Δημιουργία markdown από έγγραφο – Εξαγωγή και αποθήκευση εικόνων
url: /el/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία markdown από έγγραφο – Εξαγωγή και αποθήκευση εικόνων

Έχετε ποτέ χρειαστεί να **create markdown from document** αλλά δεν ήσασταν σίγουροι πώς να διατηρήσετε τις ενσωματωμένες εικόνες τακτικές; Δεν είστε μόνοι. Σε πολλά έργα δημιουργούμε αναφορές, εγχειρίδια ή προσχέδια blog προγραμματιστικά, και το τελευταίο που θέλουμε είναι ένα χάος αρχείων εικόνας που διασκορπίζονται στον φάκελο εξόδου.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα μια πλήρη, έτοιμη‑για‑εκτέλεση λύση που **exports document to markdown**, αποθηκεύει κάθε εικόνα σε έναν αφιερωμένο υπο‑φάκελο *md‑resources*, και τελικά **saves document as markdown** χρησιμοποιώντας το Aspose.Words for .NET API. Στο τέλος θα έχετε μια μοναδική μέθοδο που μπορείτε να ενσωματώσετε σε οποιοδήποτε κώδικα C#, καθώς και μια σειρά από συμβουλές για τη διαχείριση ειδικών περιπτώσεων.

> **Γρήγορη επισκόπηση:**  
> • Ρυθμίστε το `MarkdownSaveOptions`  
> • Παρέχετε ένα `IResourceSavingCallback` που ανακατευθύνει τις εικόνες σε έναν υπο‑φάκελο  
> • Καλέστε το `Document.Save` με τις ρυθμισμένες επιλογές  

Αν είστε περίεργοι γιατί επιλέγουμε ένα callback αντί για post‑processing, συνεχίστε την ανάγνωση – η λογική εξηγείται βήμα‑βήμα.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)  
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)  
- Ένα αντικείμενο `Document` προέλευσης (μπορεί να είναι .docx, .pdf, .rtf, κ.λπ.)  

Δεν απαιτούνται πρόσθετες βιβλιοθήκες· το callback API είναι ενσωματωμένο στο Aspose.Words.

## Βήμα 1: Create markdown from document – διαμόρφωση επιλογών αποθήκευσης

Το πρώτο που κάνουμε είναι να δημιουργήσουμε ένα αντικείμενο `MarkdownSaveOptions`. Αυτό το αντικείμενο λέει στο Aspose.Words πώς πρέπει να συμπεριφέρεται η μετατροπή, όπως ποια γεύση του Markdown να χρησιμοποιήσει, αν θα ενσωματώσει τις εικόνες ως Base64, και πού θα τοποθετήσει τα παραγόμενα αρχεία.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Γιατί είναι σημαντικό:**  
> Χωρίς την ρητή δημιουργία του `MarkdownSaveOptions`, η βιβλιοθήκη επιστρέφει στις προεπιλεγμένες ρυθμίσεις που ενσωματώνουν τις εικόνες απευθείας στο αρχείο Markdown ως αλφαριθμητικά Base64. Αυτό κάνει το αρχείο τεράστιο και αναιρεί τον σκοπό της ύπαρξης ενός καθαρού φακέλου *images*.

## Βήμα 2: Export document to markdown και ορισμός διαχείρισης πόρων

Τώρα λέμε στον αποθηκευτή **πού** να τοποθετήσει κάθε εικόνα. Η διεπαφή `IResourceSavingCallback` μας παρέχει ένα hook που ενεργοποιείται για κάθε πόρο (εικόνα, SVG, κ.λπ.) που εντοπίζεται κατά την εξαγωγή. Μέσα στο callback κάνουμε:

1. Εξασφαλίζουμε ότι ο φάκελος προορισμού υπάρχει (`md-resources/`).  
2. Ορίζουμε το `OutputFileName` στο φάκελο συν το αρχικό όνομα του πόρου.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Συχνή ερώτηση:** *Τι γίνεται αν θέλω να ενσωματώσω τις εικόνες αντί να τις αποθηκεύσω;*  
> Απλώς παραλείψτε το callback ή ορίστε `args.OutputFileName = null;` – ο αποθηκευτής θα ενσωματώσει την εικόνα ως αλφαριθμητικό Base64 αυτόματα.

> **Ειδική περίπτωση:** Ορισμένα παλαιότερα έγγραφα περιέχουν διπλά ονόματα εικόνων. Το παραπάνω callback θα αντικαταστήσει το προηγούμενο αρχείο. Για να το αποφύγετε, μπορείτε να προσθέσετε ένα GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

## Βήμα 3: Save document as markdown και επαλήθευση αποθηκευμένων εικόνων

Με τις επιλογές πλήρως διαμορφωμένες, η τελική κλήση είναι μια γραμμή κώδικα που γράφει το αρχείο Markdown και τις σχετικές εικόνες στο δίσκο.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Αν όλα πάνε καλά, θα δείτε:

- `MyReport.md` – η αναπαράσταση Markdown του πηγαίου σας εγγράφου.  
- `md-resources/` – ένας φάκελος δίπλα στο αρχείο .md που περιέχει κάθε εξαγόμενη εικόνα (π.χ., `image001.png`, `image002.jpg`).  

**Δείγμα αποσπάσματος Markdown** (αυτόματα δημιουργημένο από το Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Pro tip:** Ανοίξτε το παραγόμενο αρχείο `.md` στο VS Code ή σε οποιονδήποτε προβολέα Markdown· οι εικόνες θα εμφανιστούν αμέσως επειδή οι σχετικές διαδρομές ταιριάζουν με τη δομή του φακέλου.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα console που μπορείτε να επικολλήσετε σε ένα νέο έργο .NET και να το εκτελέσετε. Δημιουργεί ένα απλό έγγραφο Word, προσθέτει μια εικόνα, και στη συνέχεια **creates markdown from document** αποθηκεύοντας την εικόνα σε έναν υπο‑φάκελο.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Τι θα πρέπει να δείτε** μετά την εκτέλεση:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Ανοίξτε το `ExportedDoc.md` – η αναφορά στην εικόνα θα δείχνει στο `md-resources/sample-image.png`, και η εικόνα θα εμφανίζεται σωστά σε οποιονδήποτε προβολέα Markdown.

## Συχνά ζητούμενες παραλλαγές

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|----------------------|
| **Skip image export** (embed as Base64) | Παραλείψτε εντελώς το `ResourceSavingCallback`, ή ορίστε `args.OutputFileName = null;` μέσα στο callback. |
| **Change image format** (π.χ., όλα PNG) | Μέσα στο callback, τροποποιήστε το `args.ResourceFileName` και προαιρετικά μετατρέψτε το stream πριν τη γραφή. |
| **Custom folder name** | Αντικαταστήστε το `"md-resources/"` με οποιαδήποτε σχετική ή απόλυτη διαδρομή προτιμάτε. |
| **Multiple documents in a batch** | Επαναλάβετε πάνω σε μια συλλογή αντικειμένων `Document`, χρησιμοποιώντας την ίδια παρουσία `MarkdownSaveOptions` (απλώς βεβαιωθείτε ότι ο φάκελος είναι καθαρός ή έχει μοναδικό όνομα ανά εκτέλεση). |

## Συμπέρασμα

Μόλις σας δείξαμε **how to create markdown from document**, **export document to markdown**, και **save images to subfolder** χρησιμοποιώντας μια καθαρή, βασισμένη σε callback προσέγγιση. Τα κύρια συμπεράσματα είναι:

- Χρησιμοποιήστε το `MarkdownSaveOptions` για λεπτομερή έλεγχο της εξαγωγής.  
- Υλοποιήστε το `IResourceSavingCallback` για να κατευθύνετε τις εικόνες σε έναν αφιερωμένο φάκελο, διατηρώντας το Markdown σας τακτικό.  
- Το ίδιο μοτίβο λειτουργεί για άλλους τύπους πόρων (SVG, ήχο) – απλώς ελέγξτε το `args.ResourceType`.  

Στη συνέχεια, μπορείτε να εξερευνήσετε το **saving document as markdown** με προσαρμοσμένα στυλ επικεφαλίδων, ή να ενσωματώσετε αυτή τη διαδικασία σε ένα ASP.NET Web API που επιστρέφει ένα ZIP που περιέχει το αρχείο `.md` και τους πόρους του. Σε κάθε περίπτωση, τα δομικά στοιχεία είναι τώρα στο toolbox σας.

Έχετε ερωτήσεις ή εντοπίσατε μια περίπτωση που δεν καλύψαμε; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική!

![create markdown from document example](placeholder.png "create markdown from document example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}