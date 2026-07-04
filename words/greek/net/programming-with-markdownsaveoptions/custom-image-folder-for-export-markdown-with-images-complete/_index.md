---
category: general
date: 2026-06-20
description: Προσαρμοσμένος φάκελος εικόνων σας επιτρέπει να εξάγετε markdown με εικόνες
  εύκολα. Μάθετε πώς να αποθηκεύετε εικόνες σε συγκεκριμένο κατάλογο και να αποθηκεύετε
  τις εικόνες markdown στο .NET.
draft: false
keywords:
- custom image folder
- export markdown with images
- save images specific directory
- save markdown images
language: el
og_description: Ο προσαρμοσμένος φάκελος εικόνων καθιστά εύκολη την εξαγωγή markdown
  με εικόνες. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να αποθηκεύσετε τις εικόνες
  σε συγκεκριμένο κατάλογο και να αποθηκεύσετε τις εικόνες του markdown.
og_title: προσαρμοσμένος φάκελος εικόνων – Εξαγωγή Markdown με εικόνες
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  headline: custom image folder for export markdown with images – Complete Guide
  type: TechArticle
- description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  name: custom image folder for export markdown with images – Complete Guide
  steps:
  - name: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
    text: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
  - name: Eliminates a second file‑system scan, which can be costly for large docs.
    text: Eliminates a second file‑system scan, which can be costly for large docs.
  - name: Gives you the flexibility to rename or compress images on the fly.
    text: Gives you the flexibility to rename or compress images on the fly.
  type: HowTo
tags:
- Aspose.Words
- Markdown
- .NET
title: Προσαρμοσμένος φάκελος εικόνων για εξαγωγή markdown με εικόνες – Πλήρης Οδηγός
url: /el/net/programming-with-markdownsaveoptions/custom-image-folder-for-export-markdown-with-images-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# προσαρμοσμένος φάκελος εικόνων – Εξαγωγή Markdown με εικόνες σε .NET

Έχετε ποτέ χρειαστεί έναν **προσαρμοσμένο φάκελο εικόνων** όταν εξάγετε markdown με εικόνες; Δεν είστε μόνοι που αντιμετωπίζετε αυτό το πρόβλημα. Είτε δημιουργείτε τεκμηρίωση, άρθρα blog ή οδηγούς API, η οργάνωση των εικόνων σας σε έναν αφιερωμένο φάκελο σας εξοικονομεί έναν ακατάστατο δένδρο αρχείων αργότερα.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια πλήρη, έτοιμη‑για‑εκτέλεση λύση που δείχνει **πώς να αποθηκεύετε εικόνες σε συγκεκριμένο φάκελο** ενώ δημιουργείτε ένα αρχείο markdown. Θα δείτε γιατί η χρήση ενός callback είναι ο πιο καθαρός τρόπος, και θα κλείσετε τον οδηγό με ένα πλήρες παράδειγμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

## Τι θα μάθετε

- Διαμόρφωση του Aspose.Words (ή οποιασδήποτε παρόμοιας βιβλιοθήκης) για ανακατεύθυνση της αποθήκευσης εικόνων.  
- Υλοποίηση ενός callback που γράφει κάθε εικόνα σε έναν **προσαρμοσμένο φάκελο εικόνων**.  
- Χρήση του `MarkdownSaveOptions` για να συνδέσετε όλα μαζί και **να αποθηκεύσετε τις εικόνες του markdown** σωστά.  
- Συμβουλές για την αντιμετώπιση ειδικών περιπτώσεων όπως διπλά ονόματα ή μεγάλα αρχεία.

### Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντική |
|----------|------------------------|
| .NET 6+ (ή .NET Framework 4.7+) | Ο κώδικας χρησιμοποιεί `FileStream` και `Guid`. |
| Aspose.Words for .NET (ή ένας συγκρίσιμος markdown εξαγωγέας) | Παρέχει `MarkdownSaveOptions` και το interface του callback. |
| Βασικές γνώσεις C# | Θα χρειαστεί να κατανοήσετε κλάσεις και streams. |
| Ένα υπάρχον αντικείμενο `Document` (`doc`) | Το tutorial υποθέτει ότι έχετε ήδη ένα γεμάτο έγγραφο. |

Δεν απαιτούνται εξωτερικά εργαλεία πέρα από αυτά—όλα εκτελούνται τοπικά.

## Βήμα 1: Ορισμός Callback που Αποθηκεύει Κάθε Εικόνα σε Προσαρμοσμένο Φάκελο Εικόνων

Η καρδιά της λύσης είναι μια κλάση που υλοποιεί το `IResourceSavingCallback`. Μέσα στη μέθοδο `ResourceSaving` δημιουργούμε ένα μοναδικό όνομα αρχείου, χτίζουμε τη πλήρη διαδρομή μέσα στον φάκελο που επιλέξατε και στη συνέχεια υποδεικνύουμε στη βιβλιοθήκη πού να γράψει την εικόνα.

```csharp
// Step 1: Define a callback that stores each image in a custom folder
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique file name for the image
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Build the full path inside the desired resources directory
        var fullPath = Path.Combine("YOUR_DIRECTORY", fileName);

        // Redirect the saving stream to the new location
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;   // close after save

        // Update the markdown reference to point to the new file name
        args.ResourceFileName = fileName;
    }
}
```

**Γιατί λειτουργεί αυτό:**  
- `Guid.NewGuid()` εγγυάται ένα μοναδικό όνομα, αποτρέποντας συγκρούσεις όταν το πηγαίο έγγραφο περιέχει πολλές εικόνες με το ίδιο αρχικό όνομα αρχείου.  
- Αντικαθιστώντας το `args.Stream` λέμε στον εξαγωγέα ακριβώς πού να γράψει τα δυαδικά δεδομένα.  
- Η ενημέρωση του `args.ResourceFileName` διασφαλίζει ότι η αναφορά markdown (`![](img_…​)`) δείχνει στο αρχείο που τώρα βρίσκεται στον **προσαρμοσμένο φάκελο εικόνων**.

> **Pro tip:** Αντικαταστήστε το `"YOUR_DIRECTORY"` με μια διαδρομή που δημιουργείται από `Path.Combine(Environment.CurrentDirectory, "Images")` αν θέλετε ο φάκελος να τοποθετηθεί αυτόματα δίπλα στο αρχείο markdown.

## Βήμα 2: Σύνδεση του Callback στις Επιλογές Αποθήκευσης Markdown

Στη συνέχεια δημιουργούμε ένα αντικείμενο `MarkdownSaveOptions` και του αναθέτουμε το callback μας. Αυτό λέει στον εξαγωγέα να καλέσει το `ImageSavingCallback` για κάθε ενσωματωμένο πόρο που συναντά.

```csharp
// Step 2: Configure Markdown save options to use the callback
var markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ImageSavingCallback()
};
```

**Τι συμβαίνει στο παρασκήνιο;**  
Όταν εκτελείται το `doc.Save`, το Aspose.Words διασχίζει το δέντρο κόμβων του εγγράφου. Κάθε φορά που συναντά μια εικόνα, πυροδοτεί το `ResourceSaving`. Το callback μας παρεμβάλλεται σε αυτό το γεγονός, ανακατευθύνει το ρεύμα της εικόνας και ενημερώνει τον σύνδεσμο markdown. Το αποτέλεσμα; Όλες οι εικόνες καταλήγουν στον φάκελο που καθορίσατε, και το αρχείο markdown τις αναφέρει σωστά.

## Βήμα 3: Αποθήκευση του Εγγράφου ως Markdown – Οι Εικόνες Αποθηκεύονται μέσω του Callback

Τέλος, καλούμε το `Save` με το αντικείμενο επιλογών. Η βιβλιοθήκη κάνει το βαρέως τύπου έργο· το callback μας φροντίζει τη σωστή τοποθέτηση των αρχείων.

```csharp
// Step 3: Save the document as Markdown; images are saved via the callback
doc.Save("YOUR_DIRECTORY/DocWithImages.md", markdownOptions);
```

Αν το `"YOUR_DIRECTORY"` είναι `C:\Docs\MyProject`, θα δείτε:

```
C:\Docs\MyProject\DocWithImages.md
C:\Docs\MyProject\img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png
C:\Docs\MyProject\img_7e8f9a0b‑c1d2‑3e4f‑5g6h‑7i8j9k0l1m2n.jpg
```

Το αρχείο markdown περιέχει γραμμές όπως:

```markdown
![Image](img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png)
```

Αυτό είναι ακριβώς αυτό που χρειάζεστε για να **αποθηκεύσετε τις εικόνες του markdown** σε μια προβλέψιμη θέση.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται μια αυτόνομη εφαρμογή console που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο Visual Studio. Δημιουργεί ένα απλό έγγραφο με μια εικόνα και, στη συνέχεια, το εξάγει χρησιμοποιώντας την προσέγγιση του προσαρμοσμένου φακέλου.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, markdown with images!");
        builder.InsertImage("sample.jpg"); // Ensure sample.jpg exists next to the exe

        // 2️⃣ Define the callback (same as earlier)
        var options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback()
        };

        // 3️⃣ Choose output folder (feel free to change)
        string outputDir = Path.Combine(Environment.CurrentDirectory, "Exported");
        Directory.CreateDirectory(outputDir); // creates if missing

        // 4️⃣ Save markdown and images
        string mdPath = Path.Combine(outputDir, "Document.md");
        doc.Save(mdPath, options);

        Console.WriteLine($"Markdown saved to: {mdPath}");
        Console.WriteLine("Images stored in the same folder.");
    }
}

// Callback class – identical to the earlier snippet
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
        var fullPath = Path.Combine("Exported", fileName);
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;
        args.ResourceFileName = fileName;
    }
}
```

**Αναμενόμενη έξοδος**

Τρέχοντας το πρόγραμμα εμφανίζεται κάτι σαν:

```
Markdown saved to: C:\MyApp\Exported\Document.md
Images stored in the same folder.
```

Ανοίξτε το `Document.md` και θα δείτε την αναφορά εικόνας markdown να δείχνει στο `img_…​`. Το αρχείο εικόνας βρίσκεται ακριβώς δίπλα στο αρχείο markdown, όπως ορίζει η στρατηγική του **προσαρμοσμένου φακέλου εικόνων**.

## Διαχείριση Συνηθισμένων Edge Cases

| Κατάσταση | Λύση |
|-----------|------|
| **Διπλά ονόματα αρχείων** | Η χρήση του `Guid` αποφεύγει ήδη τα διπλότυπα· αν προτιμάτε πιο αναγνώσιμα ονόματα, προσθέστε έναν μετρητή (`img_001.png`, `img_002.png`). |
| **Μεγάλα σύνολα εικόνων** | Μεταφέρετε απευθείας στο δίσκο όπως φαίνεται· αποφεύγετε τη φόρτωση ολόκληρης της εικόνας στη μνήμη. |
| **Διαφορετικοί φάκελοι εξόδου ανά εκτέλεση** | Περνάτε τον προορισμό ως όρισμα κατασκευής στο `ImageSavingCallback` αντί να σκληροκωδικοποιείτε το `"Exported"`. |
| **Έλλειψη δικαιωμάτων εγγραφής** | Βεβαιωθείτε ότι η εφαρμογή τρέχει με επαρκή δικαιώματα ή επιλέξτε φάκελο εγγραφής από τον χρήστη όπως το `%TEMP%`. |
| **Μη‑εικονογραφικοί πόροι (π.χ., CSS)** | Το callback πυροδοτείται για οποιονδήποτε πόρο· μπορείτε να ελέγξετε το `args.ResourceType` και να επεξεργαστείτε μόνο εικόνες. |

## Γιατί να Χρησιμοποιήσετε ένα Callback αντί για Post‑Processing;

Μπορεί να αναρωτιέστε, “Γιατί να μην δημιουργήσω πρώτα το markdown και μετά να μετακινήσω τις εικόνες;” Η προσέγγιση με callback:

1. Εγγυάται **ατομικότητα** – εικόνες και markdown γράφονται μαζί, αποτρέποντας σπασμένους συνδέσμους.  
2. Απομακρύνει ένα δεύτερο σκανάρισμα του συστήματος αρχείων, κάτι που μπορεί να είναι δαπανηρό για μεγάλα έγγραφα.  
3. Σας δίνει την ευελιξία να μετονομάσετε ή να συμπιέσετε τις εικόνες εν κινήσει.

Με λίγα λόγια, είναι ο πιο **αξιόπιστος τρόπος εξαγωγής markdown με εικόνες** ενώ όλα παραμένουν σε έναν **προσαρμοσμένο φάκελο εικόνων**.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **αποθηκεύσετε εικόνες σε συγκεκριμένο φάκελο** και να **αποθηκεύσετε τις εικόνες του markdown** χρησιμοποιώντας μια στρατηγική **προσαρμοσμένου φακέλου εικόνων**. Με την υλοποίηση του `IResourceSavingCallback`, τη διαμόρφωση του `MarkdownSaveOptions` και την κλήση του `doc.Save`, αποκτάτε μια καθαρή δομή φακέλων και αξιόπιστες αναφορές markdown—όλα σε μερικές δεκάδες γραμμές κώδικα.

Επόμενα βήματα που μπορείτε να εξερευνήσετε:

- Προσθήκη συμπίεσης εικόνας μέσα στο callback.  
- Δημιουργία ενός `README.md` που συνδέεται αυτόματα με το φάκελο.  
- Επέκταση του callback για διαχείριση άλλων τύπων πόρων όπως CSS ή scripts.

Δοκιμάστε το στην επόμενη διαδικασία τεκμηρίωσης—ο μελλοντικός σας εαυτός θα σας ευχαριστήσει για τη δομημένη δομή φακέλων.

Καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην δική σας υλοποίηση.

- [Αποθήκευση Εικόνων Word – Μετατροπή Word σε Markdown με Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Πώς να Μετονομάσετε Εικόνες Κατά τη Μετατροπή DOCX σε Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Αποθήκευση docx ως markdown – Πλήρης Οδηγός C# με Εξαγωγή Εικόνων](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}