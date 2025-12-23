---
category: general
date: 2025-12-23
description: Μάθετε πώς να ανακτήσετε κατεστραμμένα αρχεία docx, να χρησιμοποιήσετε
  τη λειτουργία ανάκτησης, να εξάγετε εξισώσεις σε LaTeX και να δημιουργείτε μοναδικά
  ονόματα εικόνων σε C#. Κώδικας βήμα‑προς‑βήμα με εξηγήσεις.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: el
og_description: Ανακτήστε κατεστραμμένα αρχεία docx, χρησιμοποιήστε τη λειτουργία
  ανάκτησης, εξάγετε εξισώσεις σε LaTeX και δημιουργήστε μοναδικά ονόματα εικόνων
  με το Aspose.Words σε C#.
og_title: Ανάκτηση κατεστραμμένου docx – Πλήρης οδηγός C#
tags:
- Aspose.Words
- C#
- Document Recovery
title: Ανάκτηση κατεστραμμένου docx – Πλήρης Οδηγός για την Επιδιόρθωση, Εξαγωγή Μαθηματικών
  σε LaTeX & Δημιουργία Μοναδικών Ονομάτων Εικόνων
url: /el/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση κατεστραμμένου docx – Πλήρης Οδηγός για Επιδιόρθωση, Εξαγωγή Μαθηματικών σε LaTeX & Δημιουργία Μοναδικών Ονομάτων Εικόνων

Έχετε ανοίξει ποτέ ένα **.docx** που αρνείται να φορτωθεί επειδή είναι κατεστραμμένο; Δεν είστε μόνοι. Σε πολλά πραγματικά έργα, ένα σπασμένο αρχείο Word μπορεί να σταματήσει ολόκληρη τη ροή εργασίας, αλλά το καλό νέο είναι ότι μπορείτε να **ανακτήσετε κατεστραμμένα docx** προγραμματιστικά.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για **ανάκτηση κατεστραμμένου docx**, θα δείξουμε **πώς να χρησιμοποιήσετε τη λειτουργία αποκατάστασης**, θα επιδείξουμε **εξαγωγή εξισώσεων σε LaTeX**, και τέλος **δημιουργία μοναδικών ο εικόνων** κατά την αποθήκευση σε Markdown. Στο τέλος θα έχετε ένα ενιαίο, εκτελέσιμο πρόγραμμα C# που διαχειρίζεται όλες αυτές τις εργασίες χωρίς προβλήματα.

## Προαπαιτούμενα

- .NET 6 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).  
- Aspose.Words for .NET (δωρεάν δοκιμή ή άδεια έκδοση). Εγκατάσταση μέσω NuGet:

```bash
dotnet add package Aspose.Words
```

- Βασική εξοικείωση με C# και I/O αρχείων.  
- Ένα κατεστραμμένο αρχείο `corrupt.docx` για δοκιμή (μπορείτε να προσομοιώσετε την κατεστραμμένη κατάσταση περικόπτοντας ένα έγκυρο αρχείο).

> **Συμβουλή:** Κρατήστε αντίγραφο ασφαλείας του αρχικού αρχείου πριν ξεκινήσετε — η ανάκτηση είναι καταστροφική μόνο αν αντικαταστήσετε την πηγή.

## Βήμα 1 – Ανάκτηση του κατεστραμμένου DOCX χρησιμοποιώντας τη Λειτουργία Recovery Mode

Το πρώτο που πρέπει να κάνουμε είναι να πούμε στο Aspose.Words να αντιμετωπίσει το εισερχόμενο αρχείο ως πιθανώς κατεστραμμένο. Εδώ μπαίνει σε παιχνίδι **πώς να χρησιμοποιήσετε τη λειτουργία αποκατάστασης**.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Γιατί είναι σημαντικό:**  
Όταν είναι ενεργοποιημένο το `RecoveryMode.Recover`, το Aspose.Words προσπαθεί να ξαναχτίσει το εσωτερικό δέντρο του εγγράφου, παραλείποντας τα μη αναγνώσιμα τμήματα ενώ διατηρεί όσο το δυνατόν περισσότερο περιεχόμενο. Χωρίς αυτό, ο κατασκευαστής `Document` θα πετάξει εξαίρεση και θα χάσετε κάθε ευκαιρία διάσωσης του αρχείου.

> **Τι γίνεται αν το αρχείο είναι ακατάσβεστο;**  
> Η βιβλιοθήκη θα επιστρέψει ακόμη ένα αντικείμενο `Document`, αλλά ορισμένοι κόμβοι μπορεί να λείπουν. Μπορείτε να ελέγξετε `doc.GetChildNodes(NodeType.Any, true).Count` για να δείτε πόσα στοιχεία επιβίωσαν.

## Βήμα 2 – Εξαγωγή εξισώσεων Office Math σε LaTeX κατά την αποθήκευση ως Markdown

Πολλά τεχνικά έγγραφα περιέχουν εξισώσεις γραμμένες με Office Math. Αν χρειάζεστε αυτές τις εξισώσεις σε LaTeX — για παράδειγμα, για δημοσίευση σε επιστημονικό blog — μπορείτε να ζητήσετε από το Aspose.Words να κάνει τη μετατροπή για εσάς.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**Πώς λειτουργεί:**  
`OfficeMathExportMode.LaTeX` λέει στον αποθηκευτή να αντικαταστήσει κάθε κόμβο `OfficeMath` με την αναπαράστασή του σε LaTeX, τυλιγμένη σε `$…$` (inline) ή `$$…$$` (display). Το παραγόμενο αρχείο Markdown μπορεί να τροφοδοτηθεί απευθείας σε στατικούς δημιουργούς ιστοτόπων όπως Hugo ή Jekyll.

> **Ακραία περίπτωση:** Αν το αρχικό έγγραφο περιέχει σύνθετα αντικείμενα εξίσωσης (π.χ. πίνακες), η μετατροπή σε LaTeX μπορεί να δημιουργήσει έξοδο πολλών γραμμών. Ελέγξτε το παραγόμενο `.md` ώστε να βεβαιωθείτε ότι ικανοποιεί τις προσδοκίες μορφοποίησής σας.

## Βήμα 3 – Αποθήκευση του εγγράφου ως PDF με έλεγχο ετικετών πλωτών σχημάτων

Μερικές φορές χρειάζεστε μια έκδοση PDF του ίδιου εγγράφου, αλλά σας ενδιαφέρει επίσης πώς οι πλωτές μορφές (εικόνες, πλαίσια κειμένου) ετικετοποιούνται για προσβασιμότητα. Η σημαία `ExportFloatingShapesAsInlineTag` σας δίνει αυτόν τον έλεγχο.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Γιατί να εναλλάξετε αυτή τη σημαία;**  
- `true` → Οι πλωτές μορφές γίνονται ετικέτες `<Figure>`, τις οποίες πολλοί αναγνώστες οθόνης αντιμετωπίζουν ως ξεχωριστές εικόνες με λεζάντες.  
- `false` → Οι μορφές τυλίγονται σε γενικές ετικέτες `<Div>`, που μπορεί να αγνοηθούν από βοηθητικές τεχνολογίες. Επιλέξτε ανάλογα με τις απαιτήσεις προσβασιμότητας.

## Βήμα 4 – Εξαγωγή σε Markdown με προσαρμοσμένη διαχείριση εικόνων (δημιουργία μοναδικών ονομάτων εικόνων)

Όταν αποθηκεύετε ένα έγγραφο Word σε Markdown, όλες οι ενσωματωμένες εικόνες γράφονται στο δίσκο. Από προεπιλογή λαμβάνουν το αρχικό όνομα αρχείου, κάτι που μπορεί να προκαλέσει συγκρούσεις αν επεξεργάζεστε πολλά έγγραφα στον ίδιο φάκελο. Ας συνδέσουμε τη διαδικασία αποθήκευσης και **να δημιουργούμε αυτόματα μοναδικά ονόματα εικόνων**.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**Τι συμβαίνει στο παρασκήνιο;**  
`ResourceSavingCallback` καλείται για κάθε εξωτερικό πόρο (εικόνες, SVG κ.λπ.) κατά τη διάρκεια της αποθήκευσης. Επιστρέφοντας μια πλήρη διαδρομή, καθορίζετε πού θα τοποθετηθεί το αρχείο και πώς θα ονομαστεί. Το GUID εξασφαλίζει **δημιουργία μοναδικών ονομάτων εικόνων** χωρίς χειροκίνητη διαχείριση.

> **Συμβουλή:** Αν χρειάζεστε ένα ντετερμινιστικό σχήμα ονοματοδοσίας (π.χ. βασισμένο στο alt text της εικόνας), αντικαταστήστε το `Guid.NewGuid()` με ένα hash του `resourceInfo.Name`.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας τα παραπάνω, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια εφαρμογή console:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### Αναμενόμενη Εξαγωγή

Η εκτέλεση του προγράμματος θα πρέπει να εμφανίσει μηνύματα κονσόλας παρόμοια με:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

Θα βρείτε τρία αρχεία:

| Αρχείο | Σκοπός |
|------|---------|
| `out.md` | Markdown όπου κάθε εξίσωση Office Math εμφανίζεται ως LaTeX (`$…$` ή `$$…$$`). |
| `out.pdf` | Έκδοση PDF με πλωτά σχήματα ετικετοποιημένα ως `<Figure>` για καλύτερη προσβασιμότητα. |
| `out2.md` + `md_images\*` | Markdown συν φάκελο με μοναδικά ονομασμένα αρχεία εικόνας (βάσει GUID). |

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το κατεστραμμένο αρχείο δεν έχει περιεχόμενο που μπορεί να ανακτηθεί;** | Το Aspose.Words θα επιστρέψει ακόμη ένα αντικείμενο `Document`, αλλά μπορεί να είναι κενό. Ελέγξτε `doc.GetChildNodes(NodeType.Paragraph, true).Count` πριν προχωρήσετε. |
| **Μπορώ να αλλάξω το διαχωριστικό LaTeX;** | Ναι — ορίστε `markdownMathOptions.MathDelimiter = "$$"` για να επιβάλετε διαχωριστικά εμφάνισης. |
| **Πρέπει να απελευθερώσω το αντικείμενο `Document`;** | Η κλάση `Document` υλοποιεί το `IDisposable`. Τυλίξτε το σε μπλοκ `using` αν επεξεργάζεστε πολλά αρχεία ώστε να ελευθερώνονται άμεσα οι εγγενείς πόροι. |
| **Πώς διατηρώ τα αρχικά ονόματα εικόνων;** | Επιστρέψτε `Path.Combine(imageFolder, resourceInfo.Name)` μέσα στην κλήση επιστροφής. Θυμηθείτε όμως τον κίνδυνο συγκρούσεων ονομάτων. |
| **Είναι η προσέγγιση με GUID ασφαλής για αποθετήρια ελεγχόμενα από έκδοση;** | Τα GUID είναι σταθερά μεταξύ εκτελέσεων, αλλά δεν είναι φιλικά για ανθρώπινη ανάγνωση. Αν χρειάζεστε επαναλήψιμα ονόματα, κάντε hash το αρχικό όνομα μαζί με ένα project‑wide salt. |

## Συμπέρασμα

Σας δείξαμε πώς να **ανακτήσετε κατεστραμμένα docx** αρχεία, πώς να **χρησιμοποιήσετε

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}