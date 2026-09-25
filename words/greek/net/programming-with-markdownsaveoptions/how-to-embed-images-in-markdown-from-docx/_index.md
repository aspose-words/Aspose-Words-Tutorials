---
category: general
date: 2026-02-10
description: Μάθετε πώς να ενσωματώνετε εικόνες κατά τη μετατροπή DOCX σε Markdown,
  καθώς και συμβουλές για εξισώσεις και έξοδο υψηλής ανάλυσης.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- export word to markdown
- how to convert equations
- save word as markdown
language: el
og_description: Πώς να ενσωματώσετε εικόνες κατά τη μετατροπή ενός αρχείου DOCX σε
  Markdown, με εικόνες υψηλής ανάλυσης και εξαγωγή εξισώσεων LaTeX.
og_title: Πώς να ενσωματώσετε εικόνες στο Markdown από DOCX – Πλήρης Οδηγός
tags:
- Aspose.Words
- C#
- Document conversion
title: Πώς να ενσωματώσετε εικόνες σε Markdown από DOCX
url: /el/net/programming-with-markdownsaveoptions/how-to-embed-images-in-markdown-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ενσωματώσετε εικόνες σε Markdown από DOCX

Έχετε αναρωτηθεί ποτέ **πώς να ενσωματώσετε εικόνες** ενώ μετατρέπετε ένα αρχείο Word σε ένα καθαρό έγγραφο Markdown; Δεν είστε μόνοι—οι προγραμματιστές συχνά αντιμετωπίζουν προβλήματα όταν οι εικόνες χάνονται ή φαίνονται θολές μετά τη μετατροπή. Τα καλά νέα; Με λίγες γραμμές C# μπορείτε να διατηρήσετε κάθε εικόνα καθαρή, να εξάγετε μαθηματικά ως LaTeX και να καταλήξετε με ένα έτοιμο‑για‑δημοσίευση αρχείο `.md`.

Σε αυτό το tutorial θα αγγίξουμε επίσης **convert docx to markdown**, **export word to markdown**, και ακόμη το πιο δύσκολο **how to convert equations** ώστε να μπορείτε να **save word as markdown** χωρίς να θυσιάσετε την ποιότητα. Στο τέλος, θα έχετε ένα αυτόνομο, εκτελέσιμο παράδειγμα που μπορείτε να επικολλήσετε απευθείας στο έργο σας.

---

## Τι θα χρειαστείτε

- **Aspose.Words for .NET** (v23.9 ή νεότερη). Είναι μια εμπορική βιβλιοθήκη, αλλά μπορείτε να κατεβάσετε μια δωρεάν δοκιμή 30 ημερών από τον ιστότοπο της Aspose.  
- Ένα περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή VS Code με την επέκταση C#).  
- Ένα εισερχόμενο έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον μία εικόνα και μερικές εξισώσεις.  

Αυτό είναι όλο—χωρίς επιπλέον πακέτα NuGet, χωρίς εξωτερικούς μετατροπείς. Η βιβλιοθήκη κάνει όλη τη βαριά δουλειά.

## Μετατροπή βήμα‑βήμα

Παρακάτω χωρίζουμε τη διαδικασία σε μικρά βήματα. Κάθε επικεφαλίδα περιέχει μια λέξη‑κλειδί για να ικανοποιεί τόσο τις μηχανές αναζήτησης όσο και τους βοηθούς AI.

### ## Πώς να ενσωματώσετε εικόνες κατά τη μετατροπή DOCX σε Markdown

Το πρώτο πράγμα που πρέπει να κάνετε είναι να πείτε στο Aspose.Words πού βρίσκεται το αρχείο προέλευσης.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source document
Document doc = new Document(@"C:\Docs\input.docx");
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου δημιουργεί μια αναπαράσταση στη μνήμη για κάθε παράγραφο, εικόνα και εξίσωση. Αν παραλείψετε αυτό το βήμα, δεν υπάρχει τίποτα για μετατροπή και, συνεπώς, δεν υπάρχουν εικόνες για ενσωμάτωση.

> **Pro tip**: Χρησιμοποιήστε απόλυτη διαδρομή κατά τη δοκιμή, στη συνέχεια αλλάξτε σε σχετική (π.χ., `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "input.docx")`) για παραγωγή.

### ## Μετατροπή docx σε markdown με εικόνες υψηλής ανάλυσης

Τώρα διαμορφώνουμε το `MarkdownSaveOptions`. Εδώ ελέγχετε το DPI των εικόνων και τη λειτουργία εξαγωγής μαθηματικών.

```csharp
// Step 2: Configure Markdown save options
MarkdownSaveOptions mdSave = new MarkdownSaveOptions
{
    // 300 DPI gives you print‑ready quality while still keeping file size reasonable
    ImageResolution = 300,

    // Export equations as LaTeX so they render nicely on GitHub, GitLab, or static site generators
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Uncomment the line below if you prefer Base64‑embedded images (makes the .md file self‑contained)
    // ExportImagesAsBase64 = true,
};
```

*Γιατί είναι σημαντικό*: Το `ImageResolution` καθορίζει πώς αποθηκεύονται οι ραστερικές εικόνες. Η προεπιλογή (96 DPI) συχνά φαίνεται θολή σε οθόνες retina. Ορίζοντας το σε **300 DPI** διατηρεί τις λεπτομέρειες χωρίς να αυξάνει υπερβολικά το μέγεθος του αρχείου. Το `OfficeMathExportMode.LaTeX` εξασφαλίζει ότι οποιαδήποτε εξίσωση Word μετατρέπεται σε καθαρό κώδικα LaTeX, που καταλαβαίνουν οι περισσότεροι renderers Markdown.

### ## Εξαγωγή word σε markdown και επαλήθευση του αποτελέσματος

Τέλος, γράψτε το αρχείο Markdown στο δίσκο.

```csharp
// Step 3: Save the document as Markdown
string outputPath = @"C:\Docs\HighRes.md";
doc.Save(outputPath, mdSave);
Console.WriteLine($"✅ Document saved to {outputPath}");
```

*Γιατί είναι σημαντικό*: Η μέθοδος `Save` εφαρμόζει όλες τις επιλογές που ορίσαμε νωρίτερα. Μετά από αυτήν την κλήση θα βρείτε ένα αρχείο `.md` όπου κάθε ετικέτα εικόνας φαίνεται ως:

```markdown
![Image 1](HighRes.md_files/Image_0.png)
```

Αν ενεργοποιήσετε το `ExportImagesAsBase64`, η ετικέτα θα περιέχει αντί αυτού μια μακριά συμβολοσειρά `data:image/png;base64,…`, καθιστώντας το αρχείο Markdown φορητό.

---

## Πώς να μετατρέψετε εξισώσεις χωρίς να χάσετε πιστότητα

Οι εξισώσεις είναι συχνά το πιο δύσκολο μέρος μιας ροής εργασίας Word‑σε‑Markdown. Το Aspose.Words προσφέρει δύο λειτουργίες εξαγωγής:

| Mode | Αποτέλεσμα | Πότε να χρησιμοποιηθεί |
|------|------------|------------------------|
| **LaTeX** (`OfficeMathExportMode.LaTeX`) | Καθαρή σύνταξη LaTeX (`\frac{a}{b}`) | Εμφανίζετε το Markdown σε πλατφόρμες που υποστηρίζουν MathJax ή KaTeX. |
| **Image** (`OfficeMathExportMode.Image`) | Ενσωματωμένη εικόνα PNG όπως οποιαδήποτε άλλη εικόνα | Ο προορισμός δεν υποστηρίζει μαθηματικά (π.χ., απλό GitHub README). |

Αν χρειάζεστε **και τα δύο**—LaTeX για σύγχρονους αναγνώστες *και* μια εναλλακτική εικόνα για παλαιότερα εργαλεία—μπορείτε να εκτελέσετε τη μετατροπή δύο φορές, κάθε φορά με διαφορετικό `OfficeMathExportMode`, και στη συνέχεια να συγχωνεύσετε τα αποτελέσματα χειροκίνητα. Είναι λίγο επιπλέον δουλειά, αλλά εγγυάται μέγιστη συμβατότητα.

## Αποθήκευση word ως markdown – διαχείριση ειδικών περιπτώσεων

### Μεγάλες εικόνες

Όταν μια εικόνα υπερβαίνει τα 5 MB, η προεπιλεγμένη `ImageResolution` μπορεί ακόμη να παράγει ένα τεράστιο PNG. Για να διατηρήσετε το μέγεθος του αρχείου υπό έλεγχο, μπορείτε να μειώσετε την ανάλυση επιλεκτικά:

```csharp
if (new FileInfo(@"C:\Docs\input.docx").Length > 10_000_000) // >10 MB DOCX
{
    mdSave.ImageResolution = 150; // half the DPI for huge docs
}
```

### Ελλιπείς γραμματοσειρές

Αν το αρχείο Word χρησιμοποιεί προσαρμοσμένη γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή, η ραστερική εικόνα μπορεί να φαίνεται λανθασμένη. Η πιο ασφαλής λύση είναι να **ενσωματώσετε τη γραμματοσειρά** στο DOCX πριν από τη μετατροπή (File → Options → Save → Embed fonts) ή να προεγκαταστήσετε τη γραμματοσειρά στο μηχάνημα που εκτελεί τον κώδικα.

### Base64 vs. εξωτερικά αρχεία

Η ενσωμάτωση εικόνων ως Base64 κάνει το αρχείο Markdown ένα ενιαίο, διαμοιραζόμενο αντικείμενο—ιδανικό για email ή γρήγορες επιδείξεις. Ωστόσο, το μέγεθος του αρχείου μπορεί να αυξηθεί σημαντικά (ένα PNG 200 KB γίνεται ~270 KB σε Base64). Αν σκοπεύετε να ανεβάσετε το Markdown σε αποθετήριο Git, παραμείνετε με εξωτερικά αρχεία εικόνας για πιο καθαρά diffs.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή console. Περιλαμβάνει όλους τους προαιρετικούς ελέγχους που συζητήθηκαν παραπάνω.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // ---- Configuration -------------------------------------------------
        string inputPath  = @"C:\Docs\input.docx";
        string outputPath = @"C:\Docs\HighRes.md";

        // Verify the source file exists
        if (!File.Exists(inputPath))
        {
            Console.Error.WriteLine($"❌ Input file not found: {inputPath}");
            return;
        }

        // Load the Word document
        Document doc = new Document(inputPath);

        // Set up save options
        MarkdownSaveOptions mdSave = new MarkdownSaveOptions
        {
            ImageResolution = 300,
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            // ExportImagesAsBase64 = true, // uncomment for a single‑file .md
        };

        // Adjust DPI for very large source files
        if (new FileInfo(inputPath).Length > 10_000_000) // >10 MB
        {
            mdSave.ImageResolution = 150;
            Console.WriteLine("🔧 Large DOCX detected – reducing image DPI to 150.");
        }

        // Perform the conversion
        doc.Save(outputPath, mdSave);
        Console.WriteLine($"✅ Markdown saved to: {outputPath}");

        // Quick verification: list generated images
        string imageFolder = Path.Combine(Path.GetDirectoryName(outputPath) ?? "", Path.GetFileNameWithoutExtension(outputPath) + "_files");
        if (Directory.Exists(imageFolder))
        {
            Console.WriteLine("🖼️ Images generated:");
            foreach (var img in Directory.GetFiles(imageFolder))
                Console.WriteLine($"   - {Path.GetFileName(img)}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα**: Μετά την εκτέλεση του προγράμματος, θα δείτε το `HighRes.md` δίπλα σε έναν φάκελο `HighRes_files` που περιέχει κάθε εικόνα ως αρχείο PNG (ή μια ενιαία συμβολοσειρά Base64 αν ενεργοποιήσατε αυτήν την επιλογή). Όλες οι εξισώσεις εμφανίζονται ως μπλοκ LaTeX όπως:

```markdown
$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

Ανοίξτε το αρχείο `.md` στο VS Code, στην προεπισκόπηση του GitHub ή σε οποιονδήποτε προβολέα Markdown που υποστηρίζει MathJax και θα δείτε μια πιστή αναπαραγωγή του αρχικού εγγράφου Word.

## Συμπέρασμα

Μόλις περάσαμε από το **πώς να ενσωματώσετε εικόνες** όταν **μετατρέπετε docx σε markdown**, καλύπτοντας τα πάντα από τις ρυθμίσεις DPI μέχρι την εξαγωγή εξισώσεων σε LaTeX. Το σύντομο πρόγραμμα παραπάνω σας επιτρέπει να **export word to markdown** σε ένα μόνο βήμα, παρέχοντάς σας πλήρη έλεγχο της ποιότητας των εικόνων και της μορφοποίησης των εξισώσεων.

Αν είστε έτοιμοι να προχωρήσετε, σκεφτείτε:

- **Saving Word as Markdown** με προσαρμοσμένο CSS για στυλ.  
- Αυτοματοποίηση της διαδικασίας για παρτίδες αρχείων χρησιμοποιώντας `Directory.GetFiles`.  
- Προσθήκη παραμέτρου CLI για εναλλαγή ενσωμάτωσης Base64 σε πραγματικό χρόνο.  

Δοκιμάστε το, προσαρμόστε τις επιλογές, και αφήστε τα έγγραφα Markdown σας να φαίνονται τόσο επαγγελματικά όσο τα αρχικά αρχεία Word. Έχετε ερωτήσεις ή μια ιδιόρρυθμη περίπτωση; Αφήστε ένα σχόλιο—καλή κωδικοποίηση!

![παράδειγμα ενσωμάτωσης εικόνων](placeholder-image.png)   <!-- alt text includes primary keyword -->

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}