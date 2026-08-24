---
category: general
date: 2026-01-14
description: Μάθετε πώς να χρησιμοποιείτε callback σε C# για να μετατρέπετε DOCX σε
  markdown, να εξάγετε εικόνες από το Word και να δημιουργείτε μοναδικά ονόματα εικόνων.
draft: false
keywords:
- how to use callback
- convert docx to markdown
- extract images from word
- save word as markdown
- generate unique image names
language: el
og_description: Πώς να χρησιμοποιήσετε callback σε C# για τη μετατροπή DOCX σε markdown,
  την εξαγωγή εικόνων και τη δημιουργία μοναδικών ονομάτων εικόνων.
og_title: Πώς να χρησιμοποιήσετε το Callback σε C# – Μετατροπή DOCX σε Markdown
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: Πώς να χρησιμοποιήσετε το Callback σε C# – Μετατροπή DOCX σε Markdown
url: /el/net/programming-with-markdownsaveoptions/how-to-use-callback-in-c-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Χρησιμοποιήσετε Callback σε C# – Μετατροπή DOCX σε Markdown

Σας έχει αναρωτηθεί ποτέ **πώς να χρησιμοποιήσετε callback** όταν χρειάζεται να μετατρέψετε ένα έγγραφο Word σε καθαρό markdown; Δεν είστε μόνοι. Οι περισσότεροι προγραμματιστές συναντούν προβλήματα όταν η μετατροπή δημιουργεί μια σειρά από αρχεία εικόνας με συγκρουόμενα ονόματα ή όταν το markdown δείχνει σε λάθος φάκελο. Τα καλά νέα; Με ένα μικρό προσαρμοσμένο callback μπορείτε να ελέγχετε ακριβώς πού αποθηκεύεται κάθε πόρος, να δίνετε σε κάθε εικόνα ένα μοναδικό όνομα και να διατηρείτε το markdown σας τακτοποιημένο.

> **Προαπαιτούμενα**  
> • .NET 6+ (ή .NET Framework 4.7+) εγκατεστημένο  
> • Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
> • Βασική κατανόηση των κλάσεων C# και της διαχείρισης αρχείων I/O  

![διάγραμμα χρήσης callback](https://example.com/images/callback-diagram.png "Διάγραμμα που δείχνει πώς να χρησιμοποιήσετε callback για εξαγωγή εικόνων")

## Πώς να Χρησιμοποιήσετε Callback Κατά την Αποθήκευση Πόρων

Ο πυρήνας της λύσης βρίσκεται σε μια κλάση που υλοποιεί το `IResourceSavingCallback`. Το Aspose.Words καλεί αυτό το interface για κάθε εξωτερικό πόρο (όπως μια εικόνα) που χρειάζεται να γράψει στο δίσκο. Με την υπερισχύση του `ResourceSaving` αποκτούμε πλήρη έλεγχο της διαδρομής προορισμού και του ονόματος αρχείου.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that decides where each image extracted from a Word document will be saved.
/// </summary>
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Choose the folder where images will be stored.
        string folder = @"YOUR_DIRECTORY/Images/";

        // 2️⃣ Create a unique name – Guid guarantees no collisions.
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // 3️⃣ Combine folder and file name, then tell Aspose to use it.
        args.SavePath = Path.Combine(folder, uniqueName);
        args.Cancel = false; // Let Aspose perform the actual write.
    }
}
```

**Γιατί είναι σημαντικό:**  
- **Αντιληπτότητα** – Όλες οι εικόνες καταλήγουν στον ίδιο φάκελο, κάνοντας τις αναφορές markdown αξιόπιστες.  
- **Ονομασία χωρίς συγκρούσεις** – Η χρήση του `Guid.NewGuid()` σημαίνει ότι δεν θα αντικαταστήσετε ποτέ μια υπάρχουσα εικόνα, ακόμη και αν το πηγαίο έγγραφο περιέχει διπλότυπα ονόματα.  
- **Ευελιξία** – Αλλάξτε το `folder` ή το σχήμα ονομασίας χωρίς να επηρεάσετε τη λογική μετατροπής.

## Διαμόρφωση Επιλογών Αποθήκευσης Markdown (Αποθήκευση Word ως Markdown)

Τώρα ενσωματώνουμε το callback στο `MarkdownSaveOptions`. Αυτό το αντικείμενο λέει στο Aspose πώς να χειριστεί τη μετατροπή και ποιο callback να εκτελέσει.

```csharp
// Step 4: Hook our custom callback into the markdown options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

Μπορείτε επίσης να ρυθμίσετε άλλες επιλογές εδώ, όπως `ExportImagesAsBase64` (ορισμένο σε `false` επειδή θέλουμε ξεχωριστά αρχεία εικόνας) ή `ExportHeadersAsHtml` αν χρειάζεστε μεγαλύτερο έλεγχο της μορφοποίησης των τίτλων. Οι προεπιλεγμένες ρυθμίσεις παράγουν ήδη καθαρό markdown κατάλληλο για τους περισσότερους δημιουργούς στατικών ιστοσελίδων.

## Φόρτωση του Εγγράφου και Εκτέλεση της Μετατροπής (Μετατροπή DOCX σε Markdown)

Με τις επιλογές έτοιμες, το τελευταίο βήμα είναι απλό: φορτώστε το `.docx` και ζητήστε από το Aspose να το αποθηκεύσει ως markdown.

```csharp
// Step 5: Load the source DOCX and save it as Markdown.
Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

// The output markdown will reference the images saved by MyResourceSaver.
doc.Save(@"YOUR_DIRECTORY/output.md", mdOptions);
```

**Τι θα δείτε:**  
- Το `output.md` περιέχει σύνταξη markdown (`![Alt text](Images/img_…png)`) που δείχνει στο φάκελο εικόνων που καθορίσατε.  
- Κάθε εικόνα που εξάγεται από το `input.docx` βρίσκεται στο `YOUR_DIRECTORY/Images/` με ένα μοναδικό όνομα βασισμένο σε GUID.

---

## Κοινές Παραλλαγές & Ακραίες Περιπτώσεις

### 1️⃣ Αλλαγή του Σχήματος Ονομασίας
Αν προτιμάτε αναγνώσιμα ονόματα (π.χ., `figure_1.png`) αντί για GUIDs, αντικαταστήστε τη γραμμή `uniqueName` με κάτι όπως:

```csharp
int counter = 0;
string uniqueName = $"figure_{++counter}{Path.GetExtension(args.ResourceFileName)}";
```

Απλώς θυμηθείτε να κάνετε το `counter` ένα static πεδίο ή να το περάσετε μέσω του κατασκευαστή του callback ώστε να παραμένει μεταξύ των κλήσεων.

### 2️⃣ Διαχείριση Υπο‑φακέλων
Κάποια έργα οργανώνουν τις εικόνες ανά κεφάλαιο. Μπορείτε να ελέγξετε το `args.ResourceFileName` ή ακόμη και το κείμενο της γύρω παραγράφου για να αποφασίσετε για έναν υπο‑φάκελο:

```csharp
string chapterFolder = Path.Combine(folder, $"Chapter_{args.ResourceFileName.Substring(0,1)}");
Directory.CreateDirectory(chapterFolder);
args.SavePath = Path.Combine(chapterFolder, uniqueName);
```

### 3️⃣ Παράλειψη Ορισμένων Εικόνων
Αν θέλετε να εξάγετε μόνο PNG, προσθέστε έναν έλεγχο:

```csharp
if (!args.ResourceFileName.EndsWith(".png", StringComparison.OrdinalIgnoreCase))
{
    args.Cancel = true; // Skip non‑PNG images.
    return;
}
```

### 4️⃣ Επαλήθευση του Αποτελέσματος
Μετά τη μετατροπή, μπορείτε προγραμματιστικά να επαληθεύσετε ότι κάθε εικόνα που αναφέρεται στο markdown υπάρχει πραγματικά:

```csharp
string markdown = File.ReadAllText(@"YOUR_DIRECTORY/output.md");
var matches = System.Text.RegularExpressions.Regex.Matches(markdown, @"!\[.*?\]\((.*?)\)");
foreach (System.Text.RegularExpressions.Match m in matches)
{
    string imgPath = Path.Combine(@"YOUR_DIRECTORY", m.Groups[1].Value);
    Console.WriteLine(File.Exists(imgPath) ? "OK" : $"Missing: {imgPath}");
}
```

---

## Επαγγελματικές Συμβουλές για Ομαλή Εμπειρία

- **Δημιουργήστε τον φάκελο Images εκ των προτέρων.** Το Aspose θα τον δημιουργήσει αυτόματα, αλλά η προδημιουργία αποφεύγει συνθήκες αγώνα σε πολυνηματικά σενάρια.  
- **Χρησιμοποιήστε το `Path.GetInvalidFileNameChars()`** εάν χρειαστεί ποτέ να καθαρίσετε ονόματα που προέρχονται από το αρχικό έγγραφο.  
- **Αποδεσμεύστε το `Document`** όταν τελειώσετε (τοποθετήστε το σε μπλοκ `using`) για να ελευθερώσετε άμεσα τους εγγενείς πόρους.  
- **Δοκιμάστε με ένα έγγραφο που περιέχει SVG.** Το Aspose τα μετατρέπει σε PNG εξ ορισμού· αν χρειάζεστε την αρχική μορφή, προσαρμόστε το callback αναλόγως.

---

## Αναμενόμενο Αποτέλεσμα

Η εκτέλεση του script σε ένα δείγμα `input.docx` που περιέχει δύο εικόνες δίνει:

**`output.md` (απόσπασμα)**
```markdown
# Sample Document

Here is the first image:

![Image 1](Images/img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png)

And here is the second one:

![Image 2](Images/img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg)
```

**Δομή φακέλου**
```
YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ Images/
   ├─ img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png
   └─ img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg
```

Όλες οι αναφορές εικόνων επιλύονται σωστά, και έχετε επιτυχώς **αποθηκεύσει το Word ως markdown** ενώ **εξάγετε εικόνες από το Word** και **δημιουργείτε μοναδικά ονόματα εικόνων**.

---

## Συμπέρασμα

Συζητήσαμε **πώς να χρησιμοποιήσετε callback** στο Aspose.Words για να μετατρέψετε ένα DOCX σε markdown, να εξάγετε κάθε ενσωματωμένη εικόνα και να δώσετε σε κάθε αρχείο ένα ξεχωριστό, χωρίς συγκρούσεις όνομα. Η προσέγγιση είναι ελαφριά, πλήρως προσαρμόσιμη και λειτουργεί με οποιαδήποτε έκδοση .NET που υποστηρίζει το Aspose.Words.

Επόμενα βήματα; Δοκιμάστε να το συνδέσετε με έναν δημιουργό στατικών ιστοσελίδων όπως Hugo ή Jekyll, ή αυτοματοποιήστε μαζικές μετατροπές για ολόκληρο φάκελο εγγράφων. Μπορείτε επίσης να πειραματιστείτε με την εξαγωγή πινάκων ως markdown ή να προσαρμόσετε το callback ώστε να ενσωματώνει εικόνες ως Base64 όταν το μέγεθος δεν αποτελεί πρόβλημα.

Έχετε μια ιδέα που σας ενδιαφέρει; Αφήστε ένα σχόλιο και ας το εξερευνήσουμε μαζί. Καλό κώδικα!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}