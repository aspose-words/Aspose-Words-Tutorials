---
category: general
date: 2025-12-18
description: Μάθετε πώς να μετονομάζετε τις εικόνες κατά τη μετατροπή ενός εγγράφου
  Word σε Markdown, καθώς και βήμα‑βήμα οδηγίες για τη μετατροπή του docx σε markdown
  και την αποδοτική εξαγωγή του docx σε markdown.
draft: false
keywords:
- how to rename images
- convert word to markdown
- export docx to markdown
- how to convert docx
- how to extract images
language: el
og_description: Ανακαλύψτε πώς να μετονομάζετε τις εικόνες κατά τη μετατροπή από Word
  σε Markdown, με πλήρη παραδείγματα κώδικα για την εξαγωγή docx σε markdown και την
  εξαγωγή εικόνων.
og_title: πώς να μετονομάσετε εικόνες – οδηγός μετατροπής Word σε Markdown
tags:
- Aspose.Words
- C#
- Markdown conversion
title: πώς να μετονομάζετε εικόνες κατά τη μετατροπή από Word σε Markdown – πλήρης
  οδηγός
url: /el/java/document-conversion-and-export/how-to-rename-images-when-converting-word-to-markdown-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να μετονομάσετε εικόνες – Πλήρης Εκπαίδευση για τη Μετατροπή Word σε Markdown

Έχετε αναρωτηθεί ποτέ **πώς να μετονομάσετε εικόνες** όταν μετατρέπετε ένα Word .docx σε καθαρό Markdown; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν τα προεπιλεγμένα ονόματα εικόνων γίνονται ένα μπερδεμένο σύνολο GUID, καθιστώντας το τελικό Markdown δύσκολο στην ανάγνωση και συντήρηση.  

Σε αυτόν τον οδηγό θα περάσουμε από μια πλήρη, εκτελέσιμη λύση που όχι μόνο **πώς να μετονομάσετε εικόνες**, αλλά επίσης δείχνει **convert word to markdown**, **export docx to markdown**, και ακόμη **how to extract images** για ξεχωριστή επεξεργασία. Στο τέλος θα έχετε ένα ενιαίο script C# που κάνει τα πάντα — χωρίς επιπλέον εργαλεία, χωρίς χειροκίνητη μετονομασία.

> **Γρήγορη προεπισκόπηση:** Θα χρησιμοποιήσουμε το Aspose.Words για .NET, θα ρυθμίσουμε ένα callback `MarkdownSaveOptions`, και θα μετονομάσουμε κάθε ενσωματωμένη εικόνα σε ένα μοναδικό, ανθρώπινα αναγνώσιμο όνομα αρχείου. Όλος ο κώδικας είναι έτοιμος για αντιγραφή‑επικόλληση.

---

## Τι Θα Μάθετε

- **Γιατί η μετονομασία εικόνων είναι σημαντική** – αναγνωσιμότητα, SEO και έλεγχος εκδόσεων.  
- **Πώς να μετατρέψετε Word σε Markdown** χρησιμοποιώντας το Aspose.Words.  
- **Πώς να εξάγετε DOCX σε Markdown** με προσαρμοσμένο χειρισμό πόρων.  
- **Πώς να εξάγετε εικόνες** από ένα DOCX και να τις αποθηκεύσετε σε φάκελο της επιλογής σας.  
- Πρακτικές συμβουλές, διαχείριση edge‑case, και ένα πλήρες, εκτελέσιμο παράδειγμα.

**Προαπαιτούμενα**

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί με .NET Core και .NET Framework).  
- Βιβλιοθήκη Aspose.Words για .NET (δωρεάν δοκιμή ή άδεια).  
- Βασικές γνώσεις C# – αν μπορείτε να γράψετε ένα `Console.WriteLine`, είστε έτοιμοι.

---

## Πώς να Μετονομάσετε Εικόνες Κατά τη Μετατροπή Word σε Markdown

Αυτή είναι η καρδιά του tutorial. Το `MarkdownSaveOptions.ResourceSavingCallback` μας δίνει ένα hook για κάθε ενσωματωμένο πόρο (εικόνες, ήχο, κλπ.). Μέσα στο callback δημιουργούμε ένα νέο όνομα αρχείου, γράφουμε το stream στο δίσκο, και λέμε στο Aspose ποιο είναι το νέο όνομα.

![Παράδειγμα μετονομασίας εικόνων – στιγμιότυπο οθόνης με μετονομασμένα αρχεία εικόνας](/images/how-to-rename-images-example.png "how to rename images during conversion")

### Βήμα 1: Εγκατάσταση Aspose.Words

Προσθέστε το πακέτο NuGet στο έργο σας:

```bash
dotnet add package Aspose.Words
```

Ή μέσω του Package Manager Console:

```powershell
Install-Package Aspose.Words
```

### Βήμα 2: Προετοιμασία του MarkdownSaveOptions με Callback Μετονομασίας

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Define the folder where images will be saved
string imageFolder = Path.Combine(Environment.CurrentDirectory, "myImages");
Directory.CreateDirectory(imageFolder);

// Create Markdown save options
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

// Set up the callback that runs for each embedded resource
mdOptions.ResourceSavingCallback = (resource, stream) =>
{
    // Only act on images – other resources (like audio) are left untouched
    if (resource.Type == ResourceType.Image)
    {
        // Generate a friendly, unique name: img_<guid>.png
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Build the full path and copy the stream
        string fullPath = Path.Combine(imageFolder, newFileName);
        using (FileStream file = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            stream.CopyTo(file);
        }

        // Tell Aspose the new filename so the Markdown reference is correct
        resource.FileName = newFileName;
    }
};
```

**Γιατί λειτουργεί αυτό:**  
- Το callback λαμβάνει ένα αντικείμενο `ResourceSavingArgs` (`resource`) και ένα `Stream`.  
- Ελέγχοντας `resource.Type == ResourceType.Image` αποφεύγουμε την επεξεργασία μη‑εικόνων πόρων.  
- `Guid.NewGuid():N` δίνει μια αλφαριθμητική συμβολοσειρά 32 χαρακτήρων χωρίς παύλες, εξασφαλίζοντας μοναδικότητα.  
- Η ενημέρωση του `resource.FileName` ξαναγράφει τον σύνδεσμο εικόνας στο Markdown (`![](img_…png)`).

### Βήμα 3: Φόρτωση του DOCX και Αποθήκευση ως Markdown

```csharp
// Path to the source Word document
string docxPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document
Document doc = new Document(docxPath);

// Export to Markdown, applying our custom resource handling
string markdownPath = Path.Combine(Environment.CurrentDirectory, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Conversion complete! Markdown saved to {markdownPath}");
Console.WriteLine($"Images saved to {imageFolder}");
```

Αυτό είναι όλο. Εκτελώντας το πρόγραμμα θα παραχθούν:

- `output.md` – καθαρό Markdown με αναφορές εικόνων όπως `![](img_1a2b3c4d5e6f7g8h9i0j1k2l3m4n5o6p.png)`.  
- Ένας φάκελος `myImages` που περιέχει κάθε αρχείο εικόνας με το ίδιο φιλικό όνομα.

---

## Convert Word to Markdown – Πλήρες Παράδειγμα

Αν προτιμάτε ένα script μονού αρχείου, αντιγράψτε το παρακάτω στο `Program.cs` και τρέξτε το:

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // ---------- Configuration ----------
        string inputDocx = "YOUR_DIRECTORY/input.docx";
        string outputMd = "YOUR_DIRECTORY/output.md";
        string imagesDir = Path.Combine("YOUR_DIRECTORY", "myImages");
        Directory.CreateDirectory(imagesDir);

        // ---------- Step 1: Set up Markdown options ----------
        var mdOptions = new MarkdownSaveOptions();
        mdOptions.ResourceSavingCallback = (resource, stream) =>
        {
            if (resource.Type == ResourceType.Image)
            {
                string uniqueName = $"img_{Guid.NewGuid():N}.png";
                string destPath = Path.Combine(imagesDir, uniqueName);
                using (var file = new FileStream(destPath, FileMode.Create, FileAccess.Write))
                    stream.CopyTo(file);
                resource.FileName = uniqueName;
            }
        };

        // ---------- Step 2: Load DOCX ----------
        var doc = new Document(inputDocx);

        // ---------- Step 3: Save as Markdown ----------
        doc.Save(outputMd, mdOptions);

        Console.WriteLine($"✅ Done! Markdown at {outputMd}");
        Console.WriteLine($"🖼️ Images saved in {imagesDir}");
    }
}
```

**Επεξήγηση κάθε τμήματος**

| Μπλοκ | Σκοπός |
|-------|--------|
| **Configuration** | Κεντρικοποιεί τις διαδρομές ώστε να τις επεξεργάζεστε μόνο μία φορά. |
| **Step 1** | Δημιουργεί το `MarkdownSaveOptions` και το callback μετονομασίας. |
| **Step 2** | Φορτώνει το `.docx` σε ένα αντικείμενο Aspose `Document`. |
| **Step 3** | Καλεί το `Save` με τις προσαρμοσμένες επιλογές, γράφοντας τόσο το Markdown όσο και τις μετονομασμένες εικόνες. |

Τρέξτε με:

```bash
dotnet run
```

Θα πρέπει να δείτε τα δύο μηνύματα κονσόλας που επιβεβαιώνουν την επιτυχία.

---

## Export DOCX to Markdown – Γιατί Αυτή η Προσέγγιση Ξεπερνά τα Χειροκίνητα Εργαλεία

- **Αυτοματοποίηση** – Δεν χρειάζεται να ανοίξετε το Word, να αντιγράψετε‑επικολλήσετε και να μετονομάσετε αρχεία με το χέρι.  
- **Συνέπεια** – Κάθε εικόνα παίρνει ένα προβλέψιμο, μοναδικό όνομα, κάτι που είναι εξαιρετικό για έλεγχο εκδόσεων (το Git δεν θα θεωρήσει ότι το αρχείο άλλαξε μόνο επειδή άλλαξε το GUID).  
- **Κλιμακωσιμότητα** – Λειτουργεί για έγγραφα με δεκάδες ή εκατοντάδες εικόνες· το callback εκτελείται αυτόματα για κάθε πόρο.  
- **Φορητότητα** – Το παραγόμενο Markdown λειτουργεί σε οποιονδήποτε static‑site generator (Jekyll, Hugo, MkDocs) επειδή οι σύνδεσμοι εικόνας είναι σχετικοί και καθαροί.

---

## How to Extract Images from a DOCX File (Bonus)

Μερικές φορές θέλετε μόνο τις ακατέργαστες εικόνες, όχι το αρχείο Markdown. Το ίδιο callback μπορεί να επαναχρησιμοποιηθεί, ή μπορείτε να χρησιμοποιήσετε άμεσα το API `Document` του Aspose:

```csharp
using Aspose.Words;
using System.IO;

// Load the document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Iterate over all shapes (including inline images)
int imgCount = 0;
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage)
    {
        imgCount++;
        string imgPath = Path.Combine("YOUR_DIRECTORY/extractedImages", $"extracted_{imgCount}.png");
        shape.ImageData.Save(imgPath);
    }
}
Console.WriteLine($"{imgCount} images extracted.");
```

**Βασικά σημεία**

- `NodeType.Shape` εντοπίζει τόσο τις πλωτές όσο και τις ενσωματωμένες εικόνες.  
- `shape.ImageData.Save` γράφει το δυαδικό αρχείο εικόνας απευθείας στο δίσκο.  
- Μπορείτε να συνδυάσετε αυτό το απόσπασμα με τη μετατροπή σε Markdown αν χρειάζεστε και τις δύο εξόδους.

---

## Πρακτικές Συμβουλές & Συνηθισμένα Πιθανά Προβλήματα

- **Σύγκρουση ονομάτων:** Η χρήση GUID ουσιαστικά εξαλείφει τις συγκρούσεις, αλλά αν χρειάζεστε ανθρώπινα αναγνώσιμα ονόματα (π.χ. `chapter1_figure2.png`), μπορείτε να τα παραγώγετε από το `resource.Name` ή το κείμενο της γειτονικής παραγράφου.  
- **Μεγάλα έγγραφα:** Τα streams αντιγράφονται απευθείας στο δίσκο· για τεράστια αρχεία σκεφτείτε buffering ή προσωρινή αποθήκευση πρώτα.  
- **Μη‑PNG εικόνες:** Το παραπάνω callback επιβάλλει επέκταση `.png`. Αν η πηγή είναι JPEG, ίσως θέλετε να διατηρήσετε την αρχική μορφή: `Path.GetExtension(resource.FileName)` ή `resource.ContentType`.  
- **Απόδοση:** Το callback εκτελείται συγχρονικά. Αν επεξεργάζεστε δεκάδες έγγραφα παράλληλα, τυλίξτε τη μετατροπή σε `Task.Run` ή χρησιμοποιήστε thread‑pool για να αποφύγετε το μπλοκάρισμα του UI.  
- **Άδεια χρήσης:** Το Aspose.Words λειτουργεί χωρίς άδεια σε λειτουργία αξιολόγησης, αλλά προσθέτει υδατογράφημα στο αποτέλεσμα. Εγκαταστήστε ένα αρχείο άδειας (`Aspose.Words.lic`) για καθαρό αποτέλεσμα.

---

## Συμπέρασμα

Καλύψαμε **πώς να μετονομάσετε εικόνες** κατά τη μετατροπή ενός εγγράφου Word σε Markdown, σας δείξαμε μια πλήρη ροή **convert word to markdown**, παρουσιάσαμε **export docx to markdown** με προσαρμοσμένο χειρισμό πόρων, και εξηγήσαμε **how to extract images** από αρχείο DOCX. Ο κώδικας είναι αυτόνομος, σύγχρονος και έτοιμος για παραγωγή.

Δοκιμάστε το — τοποθετήστε το `.docx` σας στον φάκελο, τρέξτε το script, και παρακολουθήστε το καθαρό Markdown και τα τακτοποιημένα αρχεία εικόνας να εμφανίζονται. Από εκεί μπορείτε να σπρώξετε το Markdown σε static‑site generator, να δεσμεύσετε τις εικόνες στο Git, ή να ενσωματώσετε το αποτέλεσμα σε pipeline τεκμηρίωσης.

Έχετε ερωτήσεις για edge‑cases ή θέλετε να το ενσωματώσετε σε υπηρεσία ASP.NET Core; Αφήστε ένα σχόλιο και θα εξερευνήσουμε μαζί αυτές τις περιπτώσεις. Καλή μετατροπή!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}