---
category: general
date: 2026-02-18
description: Μετατρέψτε το Word σε Markdown και εξάγετε εικόνες από docx χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να δημιουργείτε markdown από το Word με ένα πλήρες παράδειγμα
  C#.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: el
og_description: Μετατρέψτε το Word σε Markdown και εξάγετε εικόνες από docx με το
  Aspose.Words. Αυτός ο οδηγός δείχνει πώς να δημιουργήσετε markdown από το Word βήμα‑βήμα.
og_title: Μετατροπή Word σε Markdown – Εξαγωγή εικόνων σε C#
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Μετατροπή Word σε Markdown – Εξαγωγή εικόνων σε C#
url: /el/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή Word σε Markdown – Εξαγωγή Εικόνων σε C#

Έχετε αναρωτηθεί ποτέ πώς να **convert Word to Markdown** εξάγοντας κάθε εικόνα από ένα αρχείο `.docx`; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές συναντούν εμπόδια όταν χρειάζονται μια καθαρή έκδοση markdown ενός συμβολαίου, μιας ανάρτησης blog ή ενός τεχνικού προδιαγραφικού που αρχικά δημιουργήθηκε στο Word. Τα καλά νέα; Με το Aspose.Words for .NET μπορείτε να το κάνετε σε λίγες γραμμές κώδικα, και θα έχετε ένα αρχείο markdown *συν* έναν φάκελο γεμάτο τις αρχικές εικόνες.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα C# που **generates markdown from Word**, εξάγει εικόνες από docx και αποθηκεύει τα πάντα στο δίσκο. Στο τέλος θα ξέρετε ακριβώς πώς να **convert docx to markdown**, πώς να **extract images from docx**, και πώς να προσαρμόσετε τη διαδικασία για τα δικά σας έργα.

## Τι Θα Χρειαστείτε

- **Aspose.Words for .NET** (v23.10 ή νεότερη). Μπορείτε να κατεβάσετε ένα δωρεάν trial πακέτο NuGet με `Install-Package Aspose.Words`.
- .NET 6+ SDK (οποιαδήποτε πρόσφατη έκδοση λειτουργεί άψογα).
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον μία εικόνα.
- Έναν φάκελο όπου θέλετε να αποθηκευτούν το markdown και τα αρχεία εικόνων.

Δεν απαιτούνται άλλες βιβλιοθήκες τρίτων. Ο κώδικας παρακάτω περιλαμβάνει κάθε `using` οδηγία που χρειάζεστε, ώστε να μπορείτε να το αντιγράψετε‑και‑επικολλήσετε σε μια εφαρμογή console και να πατήσετε **F5**.

![Παράδειγμα μετατροπής Word σε Markdown](/images/convert-word-to-markdown.png "μετατροπή word σε markdown")

*Image alt text: εικονογράφηση μετατροπής word σε markdown που δείχνει ένα αρχείο Word να μετατρέπεται σε αρχείο Markdown με εικόνες.*

---

## Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου Word

Το πρώτο βήμα είναι να κατευθύνετε το Aspose.Words στο αρχείο που θέλετε να μετασχηματίσετε. Σκεφτείτε το `Document` ως την πύλη σε όλα όσα περιέχονται μέσα στο `.docx`—κείμενο, πίνακες, εικόνες, ό,τι θέλετε.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **Why this matters:** Η φόρτωση του εγγράφου μία φορά διατηρεί τη χρήση μνήμης χαμηλή και επιτρέπει στη βιβλιοθήκη να εξετάσει τη δομή του εσωτερικού πακέτου, κάτι που είναι απαραίτητο για την επακόλουθη εξαγωγή εικόνων.

---

## Βήμα 2: Ορισμός Τρόπου Αποθήκευσης ως Markdown

Το Aspose.Words παρέχει την κλάση `MarkdownSaveOptions`. Σας επιτρέπει να ελέγχετε τα πάντα, από τα line endings μέχρι τον φάκελο όπου θα τοποθετηθούν οι εξωτερικοί πόροι (όπως οι εικόνες).

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **Why a callback?** Το `ResourceSavingCallback` σας δίνει πλήρη έλεγχο πάνω στο όνομα αρχείου και την τοποθεσία κάθε εξαγόμενης εικόνας. Χωρίς αυτό, το Aspose θα έριχνε όλα τα αρχεία στον ίδιο φάκελο με γενικά ονόματα, κάτι που μπορεί να γίνει ακατάστατο σε μεγαλύτερα έργα.

---

## Βήμα 3: Αποθήκευση του Εγγράφου ως Markdown

Τώρα που οι επιλογές έχουν οριστεί, η αποθήκευση είναι μια γραμμή κώδικα. Η βιβλιοθήκη κάνει το βαρέως τύπου έργο: μετατρέπει παραγράφους, επικεφαλίδες, λίστες, πίνακες και—ευχαριστώντας το callback—γράφει κάθε εικόνα στον φάκελο που καθορίσατε.

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Το `output.md` περιέχει σύνταξη markdown (π.χ., `![Image](markdown-resources/img_1234.png)`).
- Ο φάκελος `markdown-resources` περιέχει κάθε εικόνα από το αρχικό αρχείο Word, καθεμία με μοναδικό όνομα.

Ανοίξτε το `output.md` σε οποιονδήποτε προβολέα markdown (VS Code, GitHub ή έναν static site generator) και θα δείτε το κείμενο και τις εικόνες ταυτόσημα με την αρχική διάταξη του Word—μόνο σε μια ελαφριά, φιλική προς το web μορφή.

---

## Βήμα 4: Συνηθισμένες Παραλλαγές & Ακραίες Περιπτώσεις

### 4.1 Διαχείριση Υπαρχόντων Φακέλων Πόρων

Αν εκτελείτε τη μετατροπή πολλές φορές, μπορεί να καταλήξετε με παλιές εικόνες. Μια γρήγορη guard clause μπορεί να καθαρίσει το φάκελο πριν από κάθε εκτέλεση:

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 Αλλαγή Μορφής Εικόνων

Μερικές φορές χρειάζεστε όλες τις εικόνες ως JPEG για βελτιστοποίηση web. Μέσα στο callback μπορείτε να επανακωδικοποιήσετε το stream:

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **Pro tip:** Το `System.Drawing.Common` λειτουργεί στα Windows· σε Linux/macOS ίσως προτιμήσετε το `ImageSharp` για διασταυρούμενη πλατφόρμα.

### 4.3 Διατήρηση Στυλ Πινάκων

Αν το Word έγγραφό σας εξαρτάται έντονα από τη μορφοποίηση πινάκων, μπορείτε να τροποποιήσετε το `MarkdownSaveOptions`:

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 Χρήση Διαφορετικού Καταλόγου Εξόδου

Η μέθοδος `Save` δέχεται οποιοδήποτε απόλυτο ή σχετικό μονοπάτι. Για CI pipelines μπορείτε να δείξετε σε έναν προσωρινό φάκελο build:

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## Συχνές Ερωτήσεις

**Q: Λειτουργεί αυτό με αρχεία `.doc` (δυαδικά) ;**  
A: Ναι. Το `new Document("file.doc")` ανιχνεύει αυτόματα τη μορφή, έτσι ο ίδιος κώδικας διαχειρίζεται τόσο `.doc` όσο και `.docx`.

**Q: Τι γίνεται αν το αρχείο Word περιέχει ενσωματωμένες SVG εικόνες ;**  
A: Το Aspose.Words τις εξάγει στην αρχική τους μορφή. Αν χρειάζεστε εκδοχές raster, θα πρέπει να μετατρέψετε το SVG stream μέσα στο callback (π.χ., χρησιμοποιώντας `Svg.Skia`).

**Q: Μπορώ να παραλείψω εντελώς την εξαγωγή εικόνων ;**  
A: Ορίστε `markdownOptions.ExportImagesAsBase64 = true;` για να ενσωματώσετε τις εικόνες απευθείας στο markdown χρησιμοποιώντας data URIs—χρήσιμο για δημιουργία ενός μοναδικού αρχείου README.

---

## Ανακεφαλαίωση & Επόμενα Βήματα

Μόλις καλύψαμε τη πλήρη ροή εργασίας **convert word to markdown**:

1. Φορτώστε το `.docx`.
2. Διαμορφώστε το `MarkdownSaveOptions` με ένα `ResourceSavingCallback`.
3. Αποθηκεύστε το έγγραφο, αφήνοντας το callback να γράψει κάθε εικόνα σε έναν αφιερωμένο φάκελο.

Αυτή είναι η ολοκληρωμένη λύση σε λιγότερο από 50 γραμμές C#.  

Αν είστε έτοιμοι να προχωρήσετε παραπέρα, σκεφτείτε:

- **Generating a static site**: Τροφοδοτήστε το markdown σε έναν γεννήτρια όπως Hugo ή Jekyll.
- **Batch processing**: Τυλίξτε τον κώδικα σε έναν βρόχο `foreach` για να επεξεργαστείτε δεκάδες αρχεία αυτόματα.
- **Advanced image handling**: Αλλάξτε μέγεθος, προσθέστε υδατογράφημα ή μετατρέψτε εικόνες εν κινήσει χρησιμοποιώντας το callback.

Νιώστε ελεύθεροι να πειραματιστείτε—αντικαταστήστε τη λογική του callback, προσαρμόστε τις επιλογές αποθήκευσης, ή ενσωματώστε το σε μια μεγαλύτερη pipeline εγγράφων. Ο ουρανός είναι το όριο, και τώρα έχετε μια σταθερή βάση για οποιοδήποτε **generate markdown from word** έργο.

Καλή προγραμματιστική, και ας είναι πάντα το markdown σας καθαρό και οι εικόνες σας πάντα εύρετες!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}