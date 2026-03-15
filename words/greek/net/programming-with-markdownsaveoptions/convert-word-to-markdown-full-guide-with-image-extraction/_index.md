---
category: general
date: 2026-03-14
description: Μετατρέψτε το Word σε Markdown γρήγορα ενώ εξάγετε εικόνες από docx χρησιμοποιώντας
  το Aspose.Words. Παράδειγμα C# βήμα‑βήμα για προγραμματιστές.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: el
og_description: Μετατρέψτε το Word σε Markdown και εξάγετε εικόνες από αρχεία docx
  με το Aspose.Words. Ακολουθήστε αυτόν τον λεπτομερή οδηγό για μια χωρίς προβλήματα
  μετατροπή.
og_title: Μετατροπή Word σε Markdown – Πλήρης Εγχειρίδιο C#
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Μετατροπή Word σε Markdown – Πλήρης Οδηγός με Εξαγωγή Εικόνων
url: /el/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή Word σε Markdown – Πλήρες C# Tutorial

Έχετε ποτέ χρειαστεί να **convert Word to Markdown** αλλά δεν ήσασταν σίγουροι πώς να διατηρήσετε τις ενσωματωμένες εικόνες; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν το πρόβλημα όπου το κείμενο μετατρέπεται, αλλά οι εικόνες εξαφανίζονται. Τα καλά νέα; Με λίγες γραμμές C# και τη δυνατή βιβλιοθήκη Aspose.Words, μπορείτε να **convert Word to Markdown** *και* **extract images from docx** σε μια ομαλή λειτουργία.

Σε αυτό το tutorial θα περάσουμε από όλα όσα χρειάζεστε: από την εγκατάσταση του πακέτου NuGet, τη φόρτωση ενός αρχείου `.docx`, τη ρύθμιση του markdown saver, μέχρι τη σύνδεση ενός callback που αποθηκεύει κάθε εικόνα σε έναν προσαρμοσμένο φάκελο και ξαναγράφει τους συνδέσμους εικόνας. Στο τέλος θα έχετε ένα έτοιμο προς χρήση αρχείο Markdown και έναν τακτοποιημένο φάκελο `resources` που περιέχει κάθε εικόνα από το αρχικό έγγραφο Word.

## Τι Θα Μάθετε

- Πώς να ρυθμίσετε το Aspose.Words για .NET σε ένα έργο C#.
- Ο ακριβής κώδικας που απαιτείται για **convert Word to Markdown** διατηρώντας τις εικόνες.
- Γιατί το `ResourceSavingCallback` είναι απαραίτητο για **extract images from docx**.
- Κοινά προβλήματα (π.χ., διαχωριστές διαδρομών, διπλά ονόματα αρχείων) και πώς να τα αποφύγετε.
- Γρήγορα βήματα επαλήθευσης για να βεβαιωθείτε ότι το παραγόμενο Markdown αποδίδει σωστά.

### Προαπαιτούμενα

| Απαίτηση | Λόγος |
|-------------|--------|
| .NET 6.0 or later (or .NET Framework 4.7+) | Το Aspose.Words υποστηρίζει και τα δύο· οι νεότερες εκδόσεις χρόνου εκτέλεσης προσφέρουν καλύτερη απόδοση. |
| Visual Studio 2022 (or any C# IDE) | Διευκολύνει τον εντοπισμό σφαλμάτων και τη διαχείριση πακέτων. |
| Internet connection for NuGet restore | Η βιβλιοθήκη λαμβάνεται από την επίσημη πηγή. |
| A sample `input.docx` that contains text **and** images | Για να δείτε την εξαγωγή εικόνων σε δράση. |

Δεν απαιτούνται πρόσθετα εργαλεία τρίτων—το Aspose.Words διαχειρίζεται τα πάντα στο παρασκήνιο.

---

## Βήμα 1: Εγκατάσταση Aspose.Words μέσω NuGet

Πρώτα, προσθέστε το πακέτο Aspose.Words στο έργο σας. Ανοίξτε το **Package Manager Console** και εκτελέστε:

```powershell
Install-Package Aspose.Words
```

Εναλλακτικά, χρησιμοποιήστε το UI: δεξί‑κλικ στο έργο → *Manage NuGet Packages* → αναζητήστε “Aspose.Words” → κάντε κλικ στο **Install**. Αυτό προσθέτει τα βασικά DLLs και το namespace `Saving` που θα χρειαστούμε αργότερα.

> **Συμβουλή:** Κλειδώστε την έκδοση (π.χ., `22.12.0`) για να αποφύγετε απρόσμενες αλλαγές που σπάζουν τη λειτουργία όταν η βιβλιοθήκη ενημερώνεται αυτόματα.

---

## Βήμα 2: Φόρτωση του Πηγαίου Εγγράφου Word

Τώρα που η βιβλιοθήκη είναι έτοιμη, μπορούμε να φορτώσουμε το αρχείο `.docx`. Χρησιμοποιήστε απόλυτη ή σχετική διαδρομή που δείχνει στο πηγαίο έγγραφό σας.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Γιατί είναι σημαντικό:** Η `Document` αναλύει ολόκληρο το πακέτο Word, παρέχοντάς μας πρόσβαση σε παραγράφους, πίνακες και στα κρυφά τμήματα εικόνων που θα εξάγουμε αργότερα.

---

## Βήμα 3: Δημιουργία Markdown Save Options

Το Aspose.Words περιλαμβάνει την κλάση `MarkdownSaveOptions` που μας επιτρέπει να ρυθμίσουμε τη συμπεριφορά της μετατροπής. Τουλάχιστον τη δημιουργούμε· αργότερα θα συνδέσουμε ένα callback.

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

Μπορείτε να προσαρμόσετε ιδιότητες όπως `ExportImagesAsBase64` (ορίστε σε `false` επειδή θέλουμε ξεχωριστά αρχεία εικόνας) ή `ExportHeadersFooters` εάν χρειάζεστε αυτές τις ενότητες στο Markdown.

---

## Βήμα 4: Διαμόρφωση του ResourceSavingCallback – Εξαγωγή Εικόνων από DOCX

Αυτή είναι η καρδιά του tutorial. Το `ResourceSavingCallback` ενεργοποιείται για **κάθε πόρο** (εικόνες, γραμματοσειρές κ.λπ.) που ο αποθηκευτής θέλει να γράψει. Παρέχοντας το δικό μας χειριστή, αποφασίζουμε πού θα αποθηκευτεί η εικόνα και πώς το αρχείο Markdown θα την αναφέρει.

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### Τι Κάνει Αυτό

1. **Δημιουργεί** έναν υπο‑φάκελο `resources` αν δεν υπάρχει ήδη.  
2. **Αντιγράφει** κάθε εισερχόμενο ρεύμα εικόνας σε αυτόν το φάκελο, διατηρώντας το αρχικό όνομα αρχείου για να αποφευχθεί η σύγχυση.  
3. **Ενημερώνει** τον σύνδεσμο Markdown (`![alt](resources/Image1.png)`) ώστε οι αναγνώστες να βλέπουν την εικόνα όταν το αρχείο εμφανίζεται.

> **Περίπτωση άκρης:** Εάν δύο εικόνες έχουν το ίδιο όνομα, η δεύτερη θα αντικαταστήσει την πρώτη. Για να το αποφύγετε, μπορείτε να προσθέσετε ένα GUID ή να χρησιμοποιήσετε `Path.GetUniqueFileName` (ένα προσαρμοσμένο βοηθητικό) πριν την αποθήκευση.

---

## Βήμα 5: Αποθήκευση του Εγγράφου ως Markdown

Με το callback συνδεδεμένο, το τελευταίο βήμα είναι μια εντολή μίας γραμμής που γράφει το αρχείο Markdown.

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

Μετά την ολοκλήρωση αυτής της κλήσης, θα έχετε:

- `output.md` που περιέχει κείμενο Markdown και συνδέσμους εικόνας όπως `![Image1](resources/Image1.png)`.  
- Έναν φάκελο `resources` γεμάτο με κάθε εικόνα που εξήχθη από το αρχικό `.docx`.

---

## Βήμα 6: Επαλήθευση του Αποτελέσματος

Ανοίξτε το `output.md` σε οποιονδήποτε προβολέα Markdown (VS Code, GitHub, Typora). Θα πρέπει να δείτε τις επικεφαλίδες, τις λίστες και τις **εικόνες να αποδίδονται σωστά** του αρχικού εγγράφου. Εάν λείπει μια εικόνα:

1. Ελέγξτε ότι ο φάκελος `resources` περιέχει το αρχείο.  
2. Βεβαιωθείτε ότι η σχετική διαδρομή στο Markdown (`resources/<filename>`) ταιριάζει ακριβώς με το όνομα του φακέλου (διάκριση πεζών/κεφαλαίων σε Linux).  
3. Επιβεβαιώστε ότι το αρχείο εικόνας δεν είναι κατεστραμμένο – ανοίξτε το απευθείας σε προβολέα εικόνας.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντικαταστήστε το placeholder `YOUR_DIRECTORY` με την πραγματική διαδρομή του φακέλου σας.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `output.md` και θα δείτε κάτι όπως:

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

Όλες οι εικόνες εμφανίζονται δίπλα-δίπλα με το κείμενο, όπως συνέβαινε στο αρχικό αρχείο Word.

---

## Συχνές Ερωτήσεις & Προβλήματα

**Ε: Μπορώ να αλλάξω τη μορφή της εικόνας κατά την εξαγωγή;**  
Α: Ναι. Μέσα στο callback μπορείτε να ξανακωδικοποιήσετε το ρεύμα (π.χ., σε PNG) πριν το γράψετε. Χρησιμοποιήστε `System.Drawing` ή `ImageSharp` για να χειριστείτε το `args.Stream`.

**Ε: Τι γίνεται αν το έγγραφο Word περιέχει εικόνες SVG ή EMF;**  
Α: Το Aspose.Words μετατρέπει τις περισσότερες διανυσματικές μορφές σε raster PNG εξ ορισμού. Εάν χρειάζεστε το αρχικό διάνυσμα, ορίστε `mdOptions.ExportImageResolution` και χειριστείτε το ρεύμα αναλόγως.

**Ε: Λειτουργεί αυτό σε .NET Core σε Linux;**  
Α: Απόλυτα. Απλώς βεβαιωθείτε ότι η διαδρομή `resources` χρησιμοποιεί κάθετες γραμμές (`/`) ή `Path.Combine` όπως φαίνεται. Θυμηθείτε ότι τα συστήματα αρχείων Linux είναι διακριτικά ως προς πεζά/κεφαλαία, οπότε διατηρήστε τα ονόματα φακέλων συνεπή.

**Ε: Πώς μπορώ να αποκρύψω υποσημειώσεις ή σχόλια;**  
Α: Ρυθμίστε τις ιδιότητες `mdOptions.ExportFootnotes` ή `mdOptions.ExportComments` πριν την αποθήκευση.

---

## Συμπέρασμα

Μόλις καλύψαμε μια **πλήρη, από‑αρχή‑μέχρι‑τέλος λύση για convert Word to Markdown** ενώ εξάγουμε αξιόπιστα **εικόνες από docx**. Χρησιμοποιώντας το `MarkdownSaveOptions` του Aspose.Words και το `ResourceSavingCallback`, αποκτάτε λεπτομερή έλεγχο τόσο της μετατροπής κειμένου όσο και της διαχείρισης εικόνων. Ο κώδικας είναι αυτόνομος, λειτουργεί σε οποιαδήποτε πλατφόρμα .NET και μπορεί να ενσωματωθεί σε υπάρχουσες διαδικασίες με ελάχιστη τριβή.

Έτοιμοι για το επόμενο βήμα; Σκεφτείτε την αυτοματοποίηση μαζικών μετατροπών, την ενσωμάτωση αυτής της λογικής σε ένα ASP.NET API, ή την επέκταση του callback για δημιουργία μικρογραφιών για κάθε εξαγόμενη εικόνα. Ο ουρανός είναι το όριο μόλις έχετε την κύρια μετατροπή υπό έλεγχο.

![παράδειγμα μετατροπής word σε markdown](convert-word-to-markdown.png "παράδειγμα μετατροπής word σε markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}