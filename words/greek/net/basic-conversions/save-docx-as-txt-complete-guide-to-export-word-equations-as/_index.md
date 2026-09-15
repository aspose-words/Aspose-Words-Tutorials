---
category: general
date: 2026-02-17
description: Αποθηκεύστε το docx ως txt γρήγορα και μάθετε πώς να μετατρέψετε το docx
  σε LaTeX ή txt, καθώς και συμβουλές για εξαγωγή εξισώσεων Word σε LaTeX με μία κίνηση.
draft: false
keywords:
- save docx as txt
- convert docx to latex
- convert docx to txt
- save word plain text
- export word equations latex
language: el
og_description: Αποθηκεύστε το docx ως txt άμεσα· αυτός ο οδηγός δείχνει επίσης πώς
  να μετατρέψετε το docx σε LaTeX, να εξάγετε εξισώσεις Word σε LaTeX και να διατηρήσετε
  το κείμενό σας καθαρό.
og_title: Αποθήκευση docx ως txt – Βήμα‑βήμα Εξαγωγή σε Απλό Κείμενο & LaTeX
tags:
- Aspose.Words
- C#
- DocumentConversion
title: Αποθήκευση docx ως txt – Πλήρης οδηγός για την εξαγωγή εξισώσεων Word ως LaTeX
url: /el/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save docx as txt – Πώς να εξάγετε έγγραφα Word σε απλό κείμενο με εξισώσεις LaTeX

Έχετε χρειαστεί ποτέ να **save docx as txt** αλλά ανησυχείτε ότι θα χάσετε τις όμορφες εξισώσεις μέσα; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν αυτό το πρόβλημα όταν προσπαθούν να τροφοδοτήσουν το περιεχόμενο του Word σε ευρετήρια αναζήτησης ή σε static‑site generators. Τα καλά νέα; Με λίγες γραμμές C# μπορείτε όχι μόνο να **convert docx to txt**, αλλά και να **export word equations latex** ώστε τα μαθηματικά να παραμείνουν αναγνώσιμα.

Σε αυτό το tutorial θα περάσουμε από όλα όσα χρειάζεστε: το απαιτούμενο πακέτο NuGet, ένα πλήρως εκτελέσιμο δείγμα κώδικα, και μια σειρά πρακτικών συμβουλών. Στο τέλος θα μπορείτε να **convert docx to latex**, **save word plain text**, και ακόμη να διαχειριστείτε ειδικές περιπτώσεις όπως ενσωματωμένες εικόνες χωρίς πρόβλημα.

## What You’ll Need

- **.NET 6** (ή οποιοδήποτε πρόσφατο .NET runtime) – το API λειτουργεί το ίδιο και σε .NET Framework 4.7+.
- **Aspose.Words for .NET** – εμπορική βιβλιοθήκη που προσφέρει τη σημαία `OfficeMathExportMode` που χρησιμοποιούμε.
- Μια βασική κατανόηση του C# – ο κώδικας θα είναι αρκετά απλός για αρχάριους.
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον μία εξίσωση (αντικείμενο OfficeMath).

> **Pro tip:** Αν δεν έχετε ακόμη άδεια, η Aspose παρέχει ένα δωρεάν προσωρινό κλειδί που μπορείτε να χρησιμοποιήσετε για δοκιμές.

## Step 1: Install Aspose.Words and Set Up the Project

Πρώτα, προσθέστε τη βιβλιοθήκη στο έργο σας μέσω NuGet:

```bash
dotnet add package Aspose.Words
```

Στη συνέχεια δημιουργήστε μια νέα εφαρμογή console (ή τοποθετήστε τον κώδικα σε μια υπάρχουσα). Οι οδηγίες `using` είναι απαραίτητες για τις κλάσεις που θα χρησιμοποιήσουμε:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **Why this matters:** Ο χώρος ονομάτων `Aspose.Words` μας παρέχει το `Document`, ενώ το `Aspose.Words.Saving` περιέχει το `TxtSaveOptions` όπου ρυθμίζουμε τη λειτουργία εξαγωγής LaTeX.

## Step 2: Load the Source Document

Θα διαβάσουμε το αρχείο Word από το δίσκο. Βεβαιωθείτε ότι η διαδρομή δείχνει σε ένα πραγματικό αρχείο `.docx`; διαφορετικά θα ριχθεί εξαίρεση.

```csharp
// Step 2: Load the source document
string inputPath = @"YOUR_DIRECTORY\input.docx";

if (!System.IO.File.Exists(inputPath))
{
    Console.WriteLine($"⚠️  File not found: {inputPath}");
    return;
}

Document doc = new Document(inputPath);
Console.WriteLine("✅  Document loaded successfully.");
```

> **What’s happening?** Το `Document` αναλύει ολόκληρο το πακέτο Word, συμπεριλαμβανομένου του κειμένου, των στυλ και των αντικειμένων OfficeMath. Αν το αρχείο περιέχει εξισώσεις, αυτές αποθηκεύονται ως κόμβοι `OfficeMath` που θα εξάγουμε αργότερα ως LaTeX.

## Step 3: Configure Text Save Options for LaTeX Export

Η μαγεία βρίσκεται στο `TxtSaveOptions`. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX`, κάθε εξίσωση μετατρέπεται στην LaTeX αναπαράστασή της αντί να αφαιρεθεί.

```csharp
// Step 3: Configure text save options to export OfficeMath as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag ensures equations become LaTeX code inside the txt file.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep the original line breaks from the Word document.
    PreserveTableLayout = true
};

Console.WriteLine("🔧  TxtSaveOptions configured (LaTeX export enabled).");
```

> **Why LaTeX?** Τα αρχεία plain‑text δεν μπορούν να ενσωματώσουν το πλούσιο MathML που χρησιμοποιεί το Word. Η LaTeX είναι το de‑facto πρότυπο για την αναπαράσταση μαθηματικών σημειώσεων σε απλό κείμενο, καθιστώντας την ιδανική για επεξεργασία downstream (π.χ., renderers Markdown).

## Step 4: Save the Document as Plain Text

Τώρα γράφουμε το αρχείο. Η έξοδος θα είναι ένα `.txt` όπου οι κανονικές παραγράφοι εμφανίζονται ως απλό κείμενο και οι εξισώσεις ως αποσπάσματα LaTeX περικλεισμένα σε `$…$` (inline) ή `$$…$$` (display) ανάλογα με την αρχική διάταξη.

```csharp
// Step 4: Save the document as a plain‑text file using the configured options
string outputPath = @"YOUR_DIRECTORY\Math.txt";

doc.Save(outputPath, txtSaveOptions);
Console.WriteLine($"💾  Document saved as txt at: {outputPath}");
```

### Expected Output

Ανοίξτε το `Math.txt` και θα δείτε κάτι όπως:

```
This is a sample paragraph.

Equation: $E = mc^2$

Another paragraph with a display equation:
$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

Αν το πηγαίο αρχείο περιέχει μόνο κείμενο, το αρχείο θα είναι απλώς ένα dump plain‑text — ακριβώς αυτό που θα περιμένατε από μια λειτουργία **convert docx to txt**.

## Step 5: Verify and Tweak (Optional)

### Verify the LaTeX

Μπορείτε γρήγορα να δοκιμάσετε τα αποσπάσματα LaTeX με έναν online renderer (π.χ., sandbox MathJax) για να βεβαιωθείτε ότι είναι σωστά. Αν παρατηρήσετε ελλείποντες αγκύλες ή χαρακτήρες escape, προσαρμόστε το `OfficeMathExportMode`:

```csharp
txtSaveOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeXMathML;
```

Το παραπάνω αλλάζει σε έξοδο συμβατό με MathML, χρήσιμο όταν σκοπεύετε να ενσωματώσετε το κείμενο σε HTML σελίδες που ήδη φορτώνουν MathJax.

### Handling Images

Το plain‑text δεν μπορεί να ενσωματώσει εικόνες, αλλά ίσως θέλετε να διατηρήσετε μια αναφορά σε αυτές. Η Aspose.Words σας επιτρέπει να εξάγετε τις εικόνες ξεχωριστά:

```csharp
int imageCount = 0;
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage)
    {
        string imgPath = $@"YOUR_DIRECTORY\image_{imageCount}{shape.ImageData.FileExtension}";
        shape.ImageData.Save(imgPath);
        Console.WriteLine($"📷 Extracted image to {imgPath}");
        imageCount++;
    }
}
```

Τώρα έχετε ένα αρχείο **save word plain text** μαζί με έναν φάκελο εξαγόμενων εικόνων — ιδανικό για static site generators που αναφέρονται σε εικόνες μέσω Markdown.

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Equations disappear | `OfficeMathExportMode` left at default (`PlainText`) | Set `OfficeMathExportMode = OfficeMathExportMode.LaTeX` |
| Garbled special characters | The source uses non‑ASCII symbols and the default encoding is UTF‑8 without BOM | Pass `Encoding = Encoding.UTF8` in `TxtSaveOptions` |
| Large documents cause OutOfMemoryException | Loading the whole file at once on low‑memory machines | Use `LoadOptions` with `LoadFormat.Docx` and `MemoryOptimization = true` |
| Images not extracted | You only called `doc.Save` without iterating over `Shape` nodes | Use the snippet in Step 5 to pull images out |

## Full Working Example (Copy‑Paste Ready)

```csharp
// ------------------------------------------------------------
// Full example: save docx as txt while exporting equations as LaTeX
// ------------------------------------------------------------
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣  Define paths
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        string outputPath = @"YOUR_DIRECTORY\Math.txt";

        // 2️⃣  Load the document
        if (!System.IO.File.Exists(inputPath))
        {
            Console.WriteLine($"⚠️  Cannot find {inputPath}");
            return;
        }

        Document doc = new Document(inputPath);
        Console.WriteLine("✅  Document loaded.");

        // 3️⃣  Set up TxtSaveOptions for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true,
            Encoding = Encoding.UTF8
        };
        Console.WriteLine("🔧  TxtSaveOptions ready.");

        // 4️⃣  Save as plain‑text
        doc.Save(outputPath, txtOptions);
        Console.WriteLine($"💾  Saved txt to {outputPath}");

        // 5️⃣  (Optional) Extract images
        int imgIdx = 0;
        foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
        {
            if (shape.HasImage)
            {
                string imgPath = $@"YOUR_DIRECTORY\image_{imgIdx}{shape.ImageData.FileExtension}";
                shape.ImageData.Save(imgPath);
                Console.WriteLine($"📷  Image saved: {imgPath}");
                imgIdx++;
            }
        }

        Console.WriteLine("🎉  All done! Your docx is now a clean txt with LaTeX equations.");
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το `Math.txt`, και θα δείτε μια καθαρή έκδοση plain‑text του αρχείου Word, πλήρη με μαθηματικά μορφοποιημένα σε LaTeX. 🎉

## Frequently Asked Questions

**Q: Does this work with .doc files?**  
A: Yes, Aspose.Words automatically detects the format. Just change the file extension in `inputPath`. The same `OfficeMathExportMode` applies.

**Q: Can I export to Markdown instead of plain text?**  
A: While there’s no built‑in Markdown saver, you can post‑process the txt file: replace line breaks with double spaces, wrap LaTeX blocks in triple backticks, etc.

**Q: What if my document contains both inline and display equations?**  
A: The library respects the original layout—inline equations become `$…$`, display equations become `$$…$$`. No extra work needed.

**Q: Is there a free alternative to Aspose.Words?**  
A: Open‑source libraries like `DocX` or `Open XML SDK` can read text, but they lack built‑in LaTeX conversion for OfficeMath. You’d need a custom parser, which is non‑trivial.

## Next Steps & Related Topics

- **convert docx to latex** — explore `doc.Save("output.tex")` for full LaTeX documents (including sections, tables, and styling).  
- **save word plain text** — experiment with `PlainText` mode if you don’t need equations.  
- **export word equations latex** — combine the txt output with a static‑site generator that renders LaTeX on the fly (e.g., Hugo + MathJax).  
- **Batch processing** — wrap the

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}