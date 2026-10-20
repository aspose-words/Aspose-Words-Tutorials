---
category: general
date: 2026-02-15
description: Μάθετε πώς να καθορίζετε την επέκταση αρχείου κατά τη μετατροπή DOCX
  σε Markdown, να εξάγετε εικόνες, να αποθηκεύετε διαγράμματα ως SVG και να εξάγετε
  εικόνες ως PNG χρησιμοποιώντας το Aspose.Words.
draft: false
keywords:
- determine file extension
- convert docx to markdown
- how to extract images
- save charts as svg
- export images as png
language: el
og_description: Μάθετε πώς να καθορίζετε την επέκταση αρχείου, να εξάγετε εικόνες,
  να αποθηκεύετε διαγράμματα ως SVG και να εξάγετε εικόνες ως PNG κατά τη μετατροπή
  DOCX σε Markdown με το Aspose.Words.
og_title: Καθορίστε την επέκταση αρχείου κατά τη μετατροπή του DOCX σε Markdown
tags:
- Aspose.Words
- C#
- Document Conversion
title: Καθορισμός επέκτασης αρχείου κατά τη μετατροπή DOCX σε Markdown – Πλήρης Οδηγός
url: /el/net/programming-with-markdownsaveoptions/determine-file-extension-while-converting-docx-to-markdown-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καθορισμός επέκτασης αρχείου κατά τη μετατροπή DOCX σε Markdown – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ πώς να **determine file extension** για κάθε πόρο που προκύπτει από ένα DOCX όταν το μετατρέπετε σε Markdown; Δεν είστε οι μόνοι. Σε πολλά πραγματικά έργα πρέπει να **convert docx to markdown**, να εξάγουμε κάθε εικόνα και να διατηρήσουμε τα διαγράμματα ως καθαρά αρχεία SVG—χωρίς να καταλήξουμε με ένα μυστηριώδες “resource_3.bin”.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα μια πρακτική λύση που όχι μόνο **determines file extension** αυτόματα, αλλά επίσης σας δείχνει **how to extract images**, **save charts as SVG**, και **export images as PNG** χρησιμοποιώντας το Aspose.Words for .NET. Στο τέλος θα έχετε ένα έτοιμο προς εκτέλεση snippet που δημιουργεί ένα καθαρό αρχείο *.md* μαζί με έναν τακτοποιημένο φάκελο πόρων.

## Τι Θα Χρειαστεί

- .NET 6+ (ή .NET Framework 4.7.2+) – το API λειτουργεί το ίδιο και στα δύο.
- Aspose.Words for .NET (τελευταία έκδοση, π.χ., 23.9).
- Ένα αρχείο DOCX που περιέχει εικόνες, διαγράμματα ή οποιονδήποτε άλλο ενσωματωμένο πόρο.
- Ένα αγαπημένο IDE (Visual Studio, Rider ή VS Code).

Δεν απαιτούνται επιπλέον πακέτα NuGet εκτός από το Aspose.Words.

## Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου DOCX

Πρώτα απ' όλα—πάρτε το αρχείο Word που θέλετε να μετατρέψετε. Αυτό είναι το σημείο όπου ξεκινά η αλυσίδα μετατροπής.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source DOCX. Adjust the path to where your file lives.
Document doc = new Document(@"C:\Docs\Complex.docx");
```

*Γιατί είναι σημαντικό:* Το αντικείμενο `Document` είναι το σημείο εισόδου για κάθε λειτουργία του Aspose.Words. Αν το αρχείο δεν μπορεί να φορτωθεί, τίποτα άλλο δεν θα λειτουργήσει, γι' αυτό πάντα ελέγχετε τη διαδρομή και τα δικαιώματα του αρχείου.

## Βήμα 2: Προετοιμασία Φακέλου για τα Εξαγόμενα Πόρους

Όταν **determine file extension**, χρειαζόμαστε επίσης ένα μέρος για να αποθηκεύσουμε τα παραγόμενα PNG, SVG ή οποιαδήποτε άλλα δυαδικά αρχεία. Η δημιουργία του φακέλου εκ των προτέρων αποτρέπει εξαιρέσεις “directory not found” αργότερα.

```csharp
// Define where the extracted assets will live.
string resourcesFolder = @"C:\Docs\MarkdownResources";

// Ensure the folder exists – CreateDirectory is idempotent.
Directory.CreateDirectory(resourcesFolder);
```

*Συμβουλή:* Κρατήστε το φάκελο πόρων **δίπλα** στο τελικό αρχείο Markdown· οι σχετικοί σύνδεσμοι γίνονται πολύ πιο καθαροί.

## Βήμα 3: Διαμόρφωση του MarkdownSaveOptions – Η Καρδιά της Διαδικασίας

Εδώ είναι που πραγματικά **determine file extension** για κάθε πόρο. Η κλάση `MarkdownSaveOptions` μας επιτρέπει να απενεργοποιήσουμε την ενσωμάτωση Base‑64 και να προσθέσουμε ένα `ResourceSavingCallback`. Μέσα σε αυτό το callback ελέγχουμε το `args.ResourceType` και αποφασίζουμε αν το αρχείο πρέπει να είναι `.png`, `.svg` ή κάτι άλλο.

```csharp
var mdOptions = new MarkdownSaveOptions
{
    // ExportImagesAsBase64 = false forces Aspose to write each image as a separate file.
    ExportImagesAsBase64 = false,

    // This callback runs for every external resource (image, chart, etc.).
    ResourceSavingCallback = (sender, args) =>
    {
        // ---- Step 3‑a: Determine a file extension based on the resource type ----
        string extension = args.ResourceType switch
        {
            // Images become PNG – this satisfies the “export images as png” requirement.
            ResourceType.Image => ".png",

            // Charts are saved as SVG – perfect for web‑friendly scaling.
            ResourceType.Chart => ".svg",

            // Anything else falls back to a generic binary.
            _ => ".bin"
        };

        // ---- Step 3‑b: Build a unique filename to avoid collisions ----
        string fileName = $"resource_{args.Index}{extension}";
        string fullPath = Path.Combine(resourcesFolder, fileName);

        // ---- Step 3‑c: Write the raw bytes to disk ----
        File.WriteAllBytes(fullPath, args.ResourceData);

        // ---- Step 3‑d: Tell the Markdown file where to find this asset ----
        // Use a relative path so the .md file stays portable.
        args.ResourceFileName = $"./MarkdownResources/{fileName}";
    }
};
```

### Γιατί Καθορίζουμε ρητά **determine file extension** Εδώ

- **Clarity:** Μια εικόνα `.png` είναι άμεσα αναγνωρίσιμη, ενώ ένα τυχαίο `.bin` μπερδεύει τους αναγνώστες.
- **Compatibility:** Πολλοί στατικοί δημιουργοί ιστοσελίδων (Hugo, Jekyll) αναμένουν τα αρχεία εικόνας να έχουν τυπικές επεκτάσεις.
- **Control:** Μπορείτε να επεκτείνετε την έκφραση `switch` για να διαχειριστείτε PDFs, αντικείμενα OLE κ.λπ., χωρίς να αγγίξετε τον υπόλοιπο κώδικα.

## Βήμα 4: Αποθήκευση του Εγγράφου ως Markdown

Τώρα που οι επιλογές έχουν οριστεί, η τελική κλήση είναι μια γραμμή κώδικα. Το Aspose θα καλέσει το callback για κάθε πόρο, θα γράψει τα αρχεία και θα δημιουργήσει ένα καθαρό έγγραφο Markdown που τα αναφέρει.

```csharp
// Save the Markdown file alongside the resources folder.
string markdownPath = @"C:\Docs\Complex.md";
doc.Save(markdownPath, mdOptions);
```

### Αναμενόμενο Αποτέλεσμα

- `Complex.md` – ένα αρχείο Markdown που περιέχει συνδέσμους εικόνων όπως `![](./MarkdownResources/resource_0.png)`.
- `C:\Docs\MarkdownResources\` – ένας φάκελος γεμάτος με:
  - `resource_0.png` (πρώτη εικόνα)
  - `resource_1.svg` (πρώτο διάγραμμα)
  - …και ούτω καθεξής για κάθε ενσωματωμένο αντικείμενο.

Ανοίξτε το αρχείο Markdown στο VS Code ή σε κάποιο πρόγραμμα προεπισκόπησης· θα πρέπει να δείτε τις εικόνες να εμφανίζονται σωστά. Αν ένα διάγραμμα εμφανίζεται ως θολό raster, ελέγξτε ξανά ότι η περίπτωση `ResourceType.Chart` αντιστοιχεί σε `.svg`—αυτό είναι το κλειδί για **save charts as svg**.

## Βήμα 5: Επαλήθευση και Ρύθμιση – Συνηθισμένα Πιθανά Προβλήματα & Ακραίες Περιπτώσεις

### 5.1 Ελλιπείς Εικόνες

Αν παρατηρήσετε σπασμένους συνδέσμους, βεβαιωθείτε ότι η σχετική διαδρομή (`./MarkdownResources/`) ταιριάζει ακριβώς με το όνομα του φακέλου. Τα Windows δεν διακρίνουν πεζά‑κεφαλαία, αλλά πολλοί στατικοί δημιουργοί ιστοσελίδων το κάνουν.

### 5.2 Μη‑Εικόνες Πόροι

Το Aspose μπορεί επίσης να αποκαλύψει ενσωματωμένα αντικείμενα όπως PDFs ή πακέτα OLE. Επεκτείνετε το `switch`:

```csharp
ResourceType.OleObject => ".pdf",
ResourceType.Unknown   => ".bin"
```

### 5.3 Μεγάλα Έγγραφα

Για αρχεία DOCX με δεκάδες εικόνες υψηλής ανάλυσης, ίσως θελήσετε να **downscale** πριν την εγγραφή στο δίσκο. Εισάγετε ένα βήμα πριν την αποθήκευση:

```csharp
if (args.ResourceType == ResourceType.Image)
{
    using var img = Image.Load(args.ResourceData);
    img.Resize(800, 0, ResizeMode.Max); // keep aspect ratio
    args.ResourceData = img.SaveToBytes(ImageSaveFormat.Png);
}
```

### 5.4 Εξαγωγή Εικόνων ως PNG vs. Αρχική Μορφή

Το παράδειγμα επιβάλλει PNG για κάθε εικόνα (`export images as png`). Αν προτιμάτε να διατηρήσετε την αρχική μορφή (π.χ., JPEG), αντικαταστήστε την επέκταση `.png` με `Path.GetExtension(args.ResourceFileName)`. Απλώς θυμηθείτε να προσαρμόσετε τον τύπο MIME στο Markdown αν χρειάζεται.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το πλήρες πρόγραμμα, έτοιμο για αντιγραφή‑επικόλληση. Συγκεντρώνεται ως κονσόλα στο .NET 6, αλλά μπορείτε να ενσωματώσετε τον κώδικα σε οποιονδήποτε τύπο έργου.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX.
            Document doc = new Document(@"C:\Docs\Complex.docx");

            // 2️⃣ Create a folder for external resources.
            string resourcesFolder = @"C:\Docs\MarkdownResources";
            Directory.CreateDirectory(resourcesFolder);

            // 3️⃣ Set up Markdown save options with a callback that determines file extensions.
            var mdOptions = new MarkdownSaveOptions
            {
                ExportImagesAsBase64 = false,
                ResourceSavingCallback = (sender, args) =>
                {
                    // Determine proper extension.
                    string extension = args.ResourceType switch
                    {
                        ResourceType.Image => ".png",   // export images as png
                        ResourceType.Chart => ".svg",   // save charts as svg
                        _ => ".bin"
                    };

                    // Unique name and full disk path.
                    string fileName = $"resource_{args.Index}{extension}";
                    string fullPath = Path.Combine(resourcesFolder, fileName);

                    // Write the bytes to disk.
                    File.WriteAllBytes(fullPath, args.ResourceData);

                    // Point the Markdown file to the saved resource.
                    args.ResourceFileName = $"./MarkdownResources/{fileName}";
                }
            };

            // 4️⃣ Save as Markdown.
            string markdownPath = @"C:\Docs\Complex.md";
            doc.Save(markdownPath, mdOptions);

            // 5️⃣ Inform the user.
            System.Console.WriteLine("Conversion complete!");
            System.Console.WriteLine($"Markdown file: {markdownPath}");
            System.Console.WriteLine($"Resources folder: {resourcesFolder}");
        }
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το `Complex.md`, και θα δείτε τη λογική **determine file extension** σε δράση—κάθε εικόνα είναι PNG, κάθε διάγραμμα SVG, και όλοι οι σύνδεσμοι δείχνουν στα σωστά αρχεία.

## Συμπέρασμα

Τώρα ξέρετε **how to determine file extension** για κάθε πόρο όταν **convert docx to markdown**, πώς να **extract images**, **save charts as SVG**, και **export images as PNG** χρησιμοποιώντας το Aspose.Words. Το κλειδί είναι το `ResourceSavingCallback` όπου αποφασίζετε την επέκταση, γράφετε τα bytes και ορίζετε έναν σχετικό σύνδεσμο.  

Από εδώ μπορείτε:

- Ενσωματώστε το αποτέλεσμα Markdown σε έναν static‑site generator.
- Επεκτείνετε το callback για να διαχειριστείτε PDFs, ήχο ή προσαρμοσμένες μορφές.
- Προσθέστε συμπίεση εικόνας ή υδατογράφημα πριν την εγγραφή στο δίσκο.

Μη διστάσετε να πειραματιστείτε—αντικαταστήστε το `.png` με `.jpg` αν το μέγεθος αρχείου είναι σημαντικό, ή τροποποιήστε τη διαχείριση διαγραμμάτων για να παράγετε PNG αντί για SVG. Το μοτίβο παραμένει το ίδιο: **determine file extension**, γράψτε το αρχείο και ενημερώστε το σύνδεσμο.

Έχετε ερωτήσεις σχετικά με ακραίες περιπτώσεις ή θέλετε να μοιραστείτε τις δικές σας προσαρμογές; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική!  

![determine file extension diagram](determine_file_extension.png){: .align-center alt="παράδειγμα καθορισμού επέκτασης αρχείου"}

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}