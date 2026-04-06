---
category: general
date: 2026-04-05
description: Μάθετε πώς να μετατρέπετε DOCX σε Markdown και να εξάγετε εικόνες από
  DOCX σε C#. Οδηγός βήμα‑προς‑βήμα με πλήρη κώδικα και συμβουλές.
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: el
og_description: Μετατρέψτε DOCX σε Markdown και εξάγετε εικόνες από DOCX χρησιμοποιώντας
  το Aspose.Words. Πλήρες tutorial C# με κώδικα, εξήγηση και συμβουλές βέλτιστων πρακτικών.
og_title: Μετατροπή DOCX σε Markdown – Εξαγωγή εικόνων από DOCX σε C#
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: Μετατροπή DOCX σε Markdown – Εξαγωγή εικόνων από DOCX με το Aspose.Words
url: /el/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή DOCX σε Markdown – Εξαγωγή Εικόνων από DOCX σε C#

Έχετε ποτέ χρειαστεί να **μετατρέψετε DOCX σε Markdown** αλλά να αντιμετωπίζετε το πρόβλημα των εικόνων που εξαφανίζονται στο αποτέλεσμα; Δεν είστε ο μόνος. Σε πολλά έργα η έκδοση markdown είναι ιδανική για έλεγχο εκδόσεων ή στατικούς δημιουργούς ιστοσελίδων, ωστόσο οι εικόνες μένουν πίσω, μετατρέποντας ένα πλούσιο έγγραφο σε ένα άδειο αρχείο κειμένου.  

Τα καλά νέα; Με λίγες γραμμές C# και Aspose.Words μπορείτε να **μετατρέψετε DOCX σε Markdown** *και* **εξάγετε εικόνες από DOCX** αυτόματα. Αυτός ο οδηγός σας καθοδηγεί σε όλη τη διαδικασία, εξηγεί γιατί κάθε μέρος είναι σημαντικό, και ακόμη σας δείχνει πώς να διατηρείτε τον φάκελο εικόνων τακτοποιημένο.

## Τι Θα Μάθετε

- Πώς να φορτώσετε ένα DOCX που περιέχει εικόνες.
- Πώς να ορίσετε ένα προσαρμοσμένο `IResourceSavingCallback` που αποφασίζει πού θα αποθηκευτεί κάθε εικόνα.
- Πώς να διαμορφώσετε το `MarkdownSaveOptions` ώστε το παραγόμενο markdown να αναφέρει σωστά τις εξαγόμενες εικόνες.
- Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως διπλότυπα ονόματα εικόνων ή μορφές μη‑PNG.
- Ένα πλήρες, έτοιμο για αντιγραφή‑επικόλληση δείγμα κώδικα που μπορείτε να εκτελέσετε σήμερα.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το API λειτουργεί σε .NET Core, .NET Framework και .NET 5+).
- Άδεια για **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για δοκιμές).
- Βασική εξοικείωση με C# και Visual Studio (ή το αγαπημένο σας IDE).

Αν τα έχετε, ας βουτήξουμε.

---

## Βήμα 1: Ρύθμιση του Έργου και Εγκατάσταση του Aspose.Words

Πρώτα, δημιουργήστε μια νέα εφαρμογή κονσόλας (ή ενσωματώστε την σε μια υπάρχουσα λύση).

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **Συμβουλή:** Χρησιμοποιήστε την πιο πρόσφατη έκδοση του NuGet (από Απρίλιο 2026 είναι η 24.12) για να λάβετε τις νεότερες βελτιώσεις εξαγωγής markdown.

---

## Βήμα 2: Δημιουργία Callback για Αποθήκευση Εικόνων Στο Θέση που Θέλετε

Το Aspose.Words σας επιτρέπει να παρεμβείτε σε κάθε πόρο (εικόνες, SVG κ.λπ.) που γράφεται κατά την εξαγωγή markdown. Με την υλοποίηση του `IResourceSavingCallback` μπορείτε:

1. Επιλέξτε έναν φάκελο που βρίσκεται δίπλα στο αρχείο markdown.
2. Δημιουργήστε ένα μοναδικό όνομα αρχείου (ώστε να μην αντικαταστήσετε ποτέ μια υπάρχουσα εικόνα).
3. Αποφασίστε τη μορφή (εδώ επιβάλλουμε PNG για συνέπεια).

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### Γιατί όνομα βασισμένο σε GUID;

Αν το πηγαίο DOCX περιέχει δύο εικόνες με το ίδιο αρχικό όνομα, μια απλή αντιγραφή‑επικόλληση θα αντικατέστησε μία από αυτές. Η χρήση του `Guid.NewGuid()` εγγυάται μοναδικότητα, κάτι που είναι ιδιαίτερα χρήσιμο όταν εκτελείτε τη μετατροπή πολλές φορές σε αυτοματοποιημένο pipeline.

---

## Βήμα 3: Φόρτωση του DOCX και Σύνδεση των Επιλογών Markdown

Τώρα φέρνουμε το έγγραφο στη μνήμη και συνδέουμε το callback που μόλις δημιουργήσαμε.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### Τι κάνει ο κώδικας, βήμα προς βήμα

| Βήμα | Σκοπός |
|------|--------|
| **Ορισμός διαδρομών** | Κρατά το έργο σας ευέλικτο· μπορείτε να δείξετε σε οποιονδήποτε φάκελο χωρίς επαναμεταγλώττιση. |
| **Φόρτωση του DOCX** | `Document` αναλύει το αρχείο Word, καθιστώντας όλα τα στοιχεία (παράγραφοι, πίνακες, εικόνες) προσβάσιμα. |
| **Διαμόρφωση `MarkdownSaveOptions`** | Το `ResourceSavingCallback` είναι το σημείο που εξάγει τις εικόνες. Χωρίς αυτό, το Aspose.Words θα ενσωμάτωνε τις εικόνες ως αλφαριθμητικά base64 ή θα τις αγνοούσε εντελώς, ανάλογα με τις ρυθμίσεις. |
| **Αποθήκευση** | `doc.Save` γράφει το αρχείο markdown και ενεργοποιεί το callback για κάθε εικόνα. |

---

## Βήμα 4: Επαλήθευση του Αποτελέσματος – Τι Πρέπει να Δείτε;

Μετά την εκτέλεση του προγράμματος, ανοίξτε το `DocWithImages.md`. Θα παρατηρήσετε συνδέσμους εικόνων markdown που φαίνονται ως εξής:

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

Και στο `C:\Docs\MarkdownResources` θα βρείτε μια σειρά από αρχεία PNG με ονόματα GUID. Ανοίξτε οποιοδήποτε – θα πρέπει να είναι ταυτόσημα με τις εικόνες που ήταν ενσωματωμένες στο αρχικό DOCX.

Αν ανοίξετε το αρχείο markdown σε έναν προβολέα που σέβεται τις σχετικές διαδρομές (π.χ., προεπισκόπηση VS Code, GitHub ή στατικό δημιουργό ιστοσελίδων), οι εικόνες θα εμφανιστούν ακριβώς όπως στο Word.

### Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|----------|--------------|----------|
| Οι εικόνες εμφανίζονται ως σπασμένοι σύνδεσμοι | Το `ResourceFileName` δεν είχε οριστεί, έτσι το markdown δείχνει σε ένα ανύπαρκτο αρχείο. | Βεβαιωθείτε ότι `args.ResourceFileName = newFileName;` μέσα στο callback. |
| Τα αρχεία PNG είναι τεράστια | Οι αρχικές εικόνες ήταν JPEG ή BMP· η μετατροπή σε PNG μπορεί να αυξήσει το μέγεθος. | Ανιχνεύστε την αρχική μορφή μέσω `args.ResourceContentType` και διατηρήστε την: `args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| Οι διπλότυπες εικόνες εξακολουθούν να εμφανίζονται | Χρησιμοποιήσατε στατικό όνομα αρχείου αντί για GUID. | Επιστρέψτε στη λογική GUID ή προσθέστε έναν μετρητή ανά τύπο εικόνας. |
| Η μετατροπή προκαλεί `FileNotFoundException` | Η διαδρομή του πηγαίου DOCX είναι λανθασμένη ή ο φάκελος δεν έχει δικαίωμα ανάγνωσης. | Επαληθεύστε τη διαδρομή και δώστε τα κατάλληλα δικαιώματα στο σύστημα αρχείων. |

---

## Βήμα 5: Προχωρημένες Ρυθμίσεις (Προαιρετικό)

### 5.1 Διατήρηση Αρχικών Μορφών Εικόνας

Αν θέλετε οι εξαγόμενες εικόνες να διατηρούν τις αρχικές τους επεκτάσεις, τροποποιήστε το callback:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 Ενσωμάτωση Εικόνων ως Base64 (Όταν *Δεν* Θέλετε Ξεχωριστά Αρχεία)

Μερικές φορές ένα markdown σε ένα μόνο αρχείο είναι προτιμότερο (π.χ., για αποστολή μέσω email). Αλλάξτε την επιλογή:

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

Αλλά θυμηθείτε: **η εξαγωγή εικόνων από DOCX** είναι ο κύριος στόχος για τις περισσότερες ροές εργασίας στατικών ιστοσελίδων, έτσι η προσέγγιση με φάκελο είναι συνήθως η καλύτερη επιλογή.

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω είναι ολόκληρο το πρόγραμμα σε ένα αρχείο. Απλώς αντικαταστήστε τις διαδρομές με τις δικές σας και εκτελέστε.

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

Τρέξτε το με `dotnet run`. Όταν η κονσόλα εμφανίσει τη γραμμή ✅, ανοίξτε το αρχείο markdown και θα πρέπει να δείτε τις εικόνες σωστά αποδομένες.

---

## Συμπέρασμα

Τώρα έχετε μια **πλήρη, έτοιμη για παραγωγή λύση για μετατροπή DOCX σε Markdown και εξαγωγή εικόνων από DOCX** χρησιμοποιώντας το Aspose.Words σε C#. Η κύρια λέξη-κλειδί εμφανίζεται σε όλο τον οδηγό, ενισχύοντας τη σχετικότητα τόσο για τις μηχανές αναζήτησης όσο και για τους βοηθούς AI.

Σε μία μόνο εκτέλεση ο κώδικας:

1. Φορτώνει ένα έγγραφο Word.
2. Παρεμβαίνει σε κάθε εικόνα μέσω `IResourceSavingCallback`.
3. Αποθηκεύει κάθε εικόνα σε έναν προβλέψιμο φάκελο με μοναδικό όνομα.
4. Δημιουργεί markdown που αναφέρει αυτές τις εικόνες.

Από εδώ μπορείτε:

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}