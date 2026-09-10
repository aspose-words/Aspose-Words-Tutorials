---
category: general
date: 2026-01-08
description: Πώς να μετονομάσετε τις εικόνες κατά τη μετατροπή DOCX σε markdown. Εξάγετε
  τις εικόνες από το docx, αποθηκεύστε το Word ως markdown και διατηρήστε τους πόρους
  σας τακτικούς χρησιμοποιώντας το Aspose.Words.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- extract images from docx
- save word as markdown
- how to extract images
language: el
og_description: Πώς να μετονομάζετε τις εικόνες κατά τη μετατροπή DOCX σε markdown.
  Μάθετε πώς να εξάγετε εικόνες από docx και να αποθηκεύσετε το Word ως markdown με
  καθαρή δομή φακέλων.
og_title: Πώς να μετονομάσετε τις εικόνες κατά τη μετατροπή από DOCX σε Markdown
tags:
- Aspose.Words
- C#
- Document Conversion
title: Πώς να μετονομάσετε τις εικόνες κατά τη μετατροπή από DOCX σε Markdown
url: /el/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Μετονομάσετε τις Εικόνες Κατά τη Μετατροπή DOCX σε Markdown

**How to rename images** είναι ένα συχνό εμπόδιο όταν μετατρέπετε ένα έγγραφο Word (DOCX) σε Markdown. Έχετε ανοίξει ποτέ ένα παραγόμενο αρχείο `.md` και βρήκατε ένα χαοτικό σύνολο ονομάτων εικόνων όπως `image1.png`, `image2.jpeg`, και αναρωτηθήκατε πώς να τους δώσετε σημασιολογικά ονόματα;  

Σε αυτό το tutorial θα μάθετε έναν καθαρό, επαναλήψιμο τρόπο να εξάγετε εικόνες από ένα αρχείο DOCX, να μετονομάζετε κάθε εικόνα καθώς αποθηκεύεται, και να καταλήξετε με ένα τακτοποιημένο έγγραφο Markdown που αναφέρεται στα νέα ονόματα αρχείων. Θα αγγίξουμε επίσης πώς να **convert docx to markdown**, **extract images from docx**, και **save word as markdown** χρησιμοποιώντας τη δυνατή βιβλιοθήκη Aspose.Words για .NET.

> **Συμβουλή επαγγελματία:** Αν ήδη χρησιμοποιείτε το Aspose.Words για άλλες εργασίες εγγράφων, μπορείτε να επαναχρησιμοποιήσετε το ίδιο αντικείμενο `Document` – χωρίς επιπλέον εξαρτήσεις.

---

## Τι Θα Χρειαστεί

- **.NET 6+** (ή .NET Framework 4.7.2+ – ο κώδικας λειτουργεί το ίδιο)
- **Aspose.Words for .NET** πακέτο NuGet (`Install-Package Aspose.Words`)
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον μία εικόνα
- Ένας φάκελος όπου θέλετε να αποθηκευτούν το markdown και οι εξαγόμενες εικόνες  

Δεν χρειάζονται πρόσθετα εργαλεία, δεν χρειάζονται εξωτερικοί μετατροπείς. Μόνο μερικές γραμμές C#.

![Διάγραμμα Μετονομασίας Εικόνων](https://example.com/placeholder.png "Διάγραμμα που δείχνει πώς οι εικόνες μετονομάζονται και αποθηκεύονται")

## Βήμα 1: Ρύθμιση Callback Αποθήκευσης Πόρων (Primary Keyword Here)

Η καρδιά της λύσης είναι μια προσαρμοσμένη υλοποίηση του `IResourceSavingCallback`. Αυτό το callback σας δίνει πλήρη έλεγχο πάνω στο όνομα αρχείου και τη θέση κάθε ενσωματωμένου πόρου—ακριβώς αυτό που χρειάζεστε για **rename images** σε πραγματικό χρόνο.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that renames each extracted image and places it in a dedicated folder.
/// </summary>
class MyImageRenamer : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the folder exists – creates it if missing.
        string resourceFolder = "output/markdown_resources";
        Directory.CreateDirectory(resourceFolder);

        // Build a deterministic, readable name: img_0.png, img_1.jpg, …
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Combine folder and new name, then hand it back to Aspose.
        args.FileName = Path.Combine(resourceFolder, newFileName);

        // (Optional) If you need to modify the stream, you can replace args.Stream here.
    }
}
```

**Γιατί είναι σημαντικό:**  
Αντί να αφήνετε το Aspose να δημιουργεί τυχαία ονόματα αρχείων βασισμένα σε GUID, το callback σας επιτρέπει να εφαρμόσετε ένα σχήμα ονοματοδοσίας που είναι εύκολο να κατανοηθεί αργότερα—ιδανικό για έλεγχο εκδόσεων ή pipelines τεκμηρίωσης.

## Βήμα 2: Διαμόρφωση του MarkdownSaveOptions για Χρήση του Callback

Τώρα λέμε στο Aspose ότι όταν αποθηκεύει ένα έγγραφο ως Markdown, πρέπει να καλέσει το `MyImageRenamer` μας.

```csharp
// Create save options and plug in the callback.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyImageRenamer()
};
```

Παρατηρήστε ότι δεν τροποποιήσαμε καμία άλλη επιλογή. Αν χρειαστεί να ρυθμίσετε τα επίπεδα επικεφαλίδων ή το στυλ των μπλοκ κώδικα, η κλάση `MarkdownSaveOptions` διαθέτει δεκάδες ιδιότητες—να πειραματιστείτε ελεύθερα.

## Βήμα 3: Φόρτωση του DOCX και Εκτέλεση της Μετατροπής

Με το callback συνδεδεμένο, η μετατροπή γίνεται με μία μόνο γραμμή κώδικα.

```csharp
// Load the source Word document that contains images.
Document doc = new Document("input/input.docx");

// Save as Markdown; images are automatically renamed and stored.
doc.Save("output/output.md", markdownOptions);
```

After this runs, you’ll find:

- `output/output.md` – το αρχείο Markdown με συνδέσμους εικόνων όπως `![Image](markdown_resources/img_0.png)`
- `output/markdown_resources/` – ένας φάκελος που περιέχει `img_0.png`, `img_1.jpg`, κ.λπ.

Αυτή είναι η πλήρης ροή εργασίας **save word as markdown**, με ενσωματωμένη μετονομασία εικόνων.

## Βήμα 4: Επαλήθευση του Αποτελέσματος (How to Extract Images)

Ανοίξτε το παραγόμενο `output.md` σε οποιονδήποτε επεξεργαστή κειμένου. Θα πρέπει να δείτε τη σύνταξη εικόνας markdown που δείχνει στα μετονομασμένα αρχεία:

```markdown
![Image](markdown_resources/img_0.png)
![Diagram](markdown_resources/img_1.jpg)
```

Αν ανοίξετε το φάκελο `markdown_resources`, οι εικόνες θα είναι εκεί με το μοτίβο `img_#`. Αυτό δείχνει ότι εξάγαμε επιτυχώς **extracted images from docx** και τους δώσαμε προβλέψιμα ονόματα.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειάζομαι τα αρχικά ονόματα εικόνας;

Αντικαταστήστε τη γραμμή που δημιουργεί το `newFileName` με κάτι που προέρχεται από το `args.FileName` (το αρχικό όνομα) ή από το κείμενο ALT της εικόνας αν υπάρχει:

```csharp
string cleanName = Path.GetFileNameWithoutExtension(args.FileName)
                     .Replace(" ", "_")
                     .ToLowerInvariant();
string newFileName = $"{cleanName}{Path.GetExtension(args.FileName)}";
```

### Πώς να διαχειριστείτε διπλότυπα ονόματα;

Προσθέστε το `args.Index` ως επίθημα, ή διατηρήστε ένα `HashSet<string>` μέσα στο callback για να εγγυηθείτε μοναδικότητα.

### Μπορώ να αλλάξω τη μορφή της εικόνας (π.χ., PNG → JPEG);

Ναι. Μπορείτε να διαβάσετε το `args.Stream`, να μετατρέψετε την εικόνα χρησιμοποιώντας `System.Drawing` ή `ImageSharp`, στη συνέχεια να αντιστοιχίσετε ένα νέο stream στο `args.Stream` και να προσαρμόσετε το `args.FileName` αναλόγως.

### Λειτουργεί αυτό με SVG ή άλλες διανυσματικές μορφές;

Το Aspose.Words θεωρεί το SVG ως πόρο εικόνας, οπότε ισχύει το ίδιο callback. Απλώς προσέξτε την επέκταση αρχείου όταν το μετονομάζετε.

### Σκέψεις απόδοσης;

Το callback εκτελείται μία φορά ανά πόρο, έτσι το κόστος είναι ελάχιστο. Αν επεξεργάζεστε χιλιάδες εικόνες, σκεφτείτε να δημιουργήσετε τον φάκελο προορισμού εκ των προτέρων εκτός του callback για να αποφύγετε επαναλαμβανόμενες κλήσεις `Directory.CreateDirectory` (αν και η μέθοδος είναι ήδη φθηνή).

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα που μπορείτε να ενσωματώσετε σε μια εφαρμογή κονσόλας. Περιλαμβάνει όλες τις δηλώσεις using, την κλάση callback και τη λογική μετατροπής.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdownRenamer
{
    /// <summary>
    /// Callback that renames each extracted image and stores it in a subfolder.
    /// </summary>
    class MyImageRenamer : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourceFolder = "output/markdown_resources";
            Directory.CreateDirectory(resourceFolder);

            // Example naming scheme: img_0.png, img_1.jpg, …
            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(resourceFolder, newFileName);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the DOCX that contains images.
            Document doc = new Document("input/input.docx");

            // 2️⃣ Set up Markdown options with our renamer.
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyImageRenamer()
            };

            // 3️⃣ Save as Markdown – images are renamed automatically.
            doc.Save("output/output.md", markdownOptions);

            Console.WriteLine("Conversion complete! Check the 'output' folder.");
        }
    }
}
```

Εκτελέστε το πρόγραμμα και θα δείτε το μήνυμα κονσόλας που επιβεβαιώνει τη μετατροπή. Ανοίξτε το `output/output.md` και θα παρατηρήσετε αμέσως τις καθαρές αναφορές εικόνων.

## Συμπέρασμα

Διασχίσαμε **πώς να μετονομάσετε τις εικόνες** όταν **convert docx to markdown** χρησιμοποιώντας το Aspose.Words. Εκμεταλλευόμενοι ένα προσαρμοσμένο `IResourceSavingCallback`, αποκτάτε πλήρη έλεγχο πάνω στα ονόματα αρχείων εικόνων, την οργάνωση φακέλων, και ακόμη και τη μετατροπή μορφής εικόνας αν χρειάζεται.  

Συνοπτικά:

- Υλοποιήστε ένα callback για να μετονομάσετε και να μετακινήσετε κάθε εικόνα.  
- Συνδέστε το callback στο `MarkdownSaveOptions`.  
- Φορτώστε το έγγραφο Word και αποθηκεύστε το ως Markdown.  

Τώρα μπορείτε με σιγουριά **extract images from docx**, να διατηρήσετε το markdown σας τακτοποιημένο, και να ενσωματώσετε τη διαδικασία σε μεγαλύτερα pipelines αυτοματοποίησης.  

**Επόμενα βήματα:**  
- Προσπαθήστε να προσαρμόσετε το σχήμα ονοματοδοσίας ώστε να περιλαμβάνει το αρχικό κείμενο της επικεφαλίδας (χρησιμοποιήστε `doc.GetChildNodes`).  
- Εξερευνήστε άλλες μορφές εξόδου του Aspose όπως HTML ή PDF ενώ επαναχρησιμοποιείτε το ίδιο πρότυπο callback.  
- Συνδυάστε αυτό με ένα pipeline CI/CD για να δημιουργείτε τεκμηρίωση αυτόματα από τα πηγαία αρχεία Word.  

Έχετε περισσότερες ερωτήσεις σχετικά με τη διαχείριση εικόνων, άλλες μορφές εγγράφων ή τεχνάσματα του Aspose; Αφήστε ένα σχόλιο παρακάτω—καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}