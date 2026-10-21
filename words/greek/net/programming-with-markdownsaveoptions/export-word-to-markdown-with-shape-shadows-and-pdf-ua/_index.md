---
category: general
date: 2026-03-28
description: Μάθετε πώς να εξάγετε το Word σε markdown, να προσθέσετε σκιά σε σχήμα
  και να αποθηκεύσετε PDF/UA χρησιμοποιώντας το Aspose.Words σε C# – βήμα‑βήμα οδηγός.
draft: false
keywords:
- export word to markdown
- add shape shadow
- save pdf ua
- Aspose.Words markdown
- C# document conversion
language: el
og_description: Εξαγωγή Word σε markdown, προσθήκη σκιάς σχήματος και αποθήκευση PDF/UA
  με το Aspose.Words σε C#. Πλήρης οδηγός με κώδικα και συμβουλές.
og_title: Εξαγωγή Word σε Markdown – Προσθήκη Σκιάς Σχήματος & Αποθήκευση PDF/UA
tags:
- Aspose.Words
- C#
- Markdown
- PDF/UA
title: Εξαγωγή Word σε Markdown με σκιές σχήματος και PDF/UA
url: /el/net/programming-with-markdownsaveoptions/export-word-to-markdown-with-shape-shadows-and-pdf-ua/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή Word σε Markdown με Σκιές Σχημάτων και PDF/UA

Κάποτε χρειάστηκε να **εξάγετε Word σε markdown** αλλά και να διατηρήσετε εκείνες τις εντυπωσιακές σκιές σχημάτων και να παραμείνετε συμβατοί με PDF/UA; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν δυσκολίες όταν προσπαθούν να διατηρήσουν την οπτική πιστότητα ενώ αλλάζουν μορφές, ειδικά όταν η προσβασιμότητα (PDF/UA) είναι απαραίτητη.

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από ένα πλήρες, εκτελέσιμο παράδειγμα που δείχνει πώς να **εξάγετε Word σε markdown**, **προσθέσετε σκιά σε σχήμα** σε ένα drawing, και τέλος **αποθηκεύσετε PDF/UA** με τα αιωρούμενα σχήματα να γίνονται ενσωματωμένα. Θα χρησιμοποιήσουμε το Aspose.Words for .NET, τη βιβλιοθήκη‑αναφορά για αξιόπιστη μετατροπή εγγράφων. Χωρίς εξωτερικά scripts, χωρίς χειροκίνητους parsers—απλός κώδικας C# που μπορείτε να ενσωματώσετε σε μια εφαρμογή console σήμερα.

> **Συμβουλή:** Αν δεν έχετε εγκαταστήσει ακόμη το Aspose.Words, πάρτε το τελευταίο πακέτο NuGet (`Install-Package Aspose.Words`) – λειτουργεί με .NET 6+, .NET Framework 4.8, και ακόμη και .NET Core.

## Τι Θα Χρειαστεί

- **Visual Studio 2022** (ή οποιοδήποτε IDE που υποστηρίζει .NET 6+)
- **Aspose.Words for .NET** (έκδοση NuGet 23.8 ή νεότερη)
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον ένα σχήμα (π.χ. ένα ορθογώνιο)
- Βασικές γνώσεις C# – θα κρατήσουμε τη σύνταξη απλή

Με αυτά τα προαπαιτούμενα εκτός του δρόμου, ας βουτήξουμε.

![Διάγραμμα που δείχνει τη ροή εξαγωγής word σε markdown](export_word_to_markdown_diagram.png){alt="παράδειγμα εξαγωγής word σε markdown"}

## Βήμα 1: Φόρτωση του Εγγράφου Word σε Λειτουργία Ανάκτησης  

Πριν μπορέσουμε να τροποποιήσουμε οτιδήποτε, χρειάζεται το έγγραφο στη μνήμη. Η φόρτωση με **RecoveryMode.Recover** καταγράφει τυχόν προειδοποιήσεις αντικατάστασης γραμματοσειρών, κάτι χρήσιμο όταν η πηγή χρησιμοποιεί γραμματοσειρές που δεν έχετε εγκαταστήσει.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

// 1️⃣ Load the document while collecting warnings
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover,
    WarningCallback = new WarningInfoCollection()
};

Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Γιατί RecoveryMode;*  
Αν το αρχικό αρχείο αναφέρει γραμματοσειρές που λείπουν, το Aspose θα τις αντικαταστήσει και θα εμφανίσει προειδοποίηση. Καταγράφοντας αυτές τις προειδοποιήσεις μπορούμε να τις καταγράψουμε αργότερα—χρήσιμο για εντοπισμό σφαλμάτων και για αναφορές συμμόρφωσης.

## Βήμα 2: Προσθήκη Σκιάς σε Σχήμα  

Τώρα που το έγγραφο είναι φορτωμένο, ας βελτιώσουμε την εμφάνιση ενός σχήματος. Θα πάρουμε τον πρώτο κόμβο `Shape` και θα ενεργοποιήσουμε μια διακριτική σκιά.

```csharp
// 2️⃣ Find the first shape and enable its shadow
Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
shape.ShadowFormat.Visible = true;
shape.ShadowFormat.BlurRadius = 4;   // soft edges
shape.ShadowFormat.Distance = 2;    // how far the shadow is from the shape
shape.ShadowFormat.Angle = 30;      // direction of the light source
```

*Γιατί να τροποποιήσουμε τη σκιά;*  
Μια σκιά προσθέτει βάθος, κάνοντας το σχήμα να ξεχωρίζει τόσο στο Word όσο και στην εικόνα markdown (αν μετατρέψετε το σχήμα σε εικόνα). Είναι επίσης ένας γρήγορος τρόπος να ελέγξετε ότι οι οπτικές ιδιότητες διατηρούνται στη διαδικασία μετατροπής.

## Βήμα 3: Εξαγωγή του Εγγράφου σε Markdown (με LaTeX Math)  

Το Aspose.Words μπορεί να μετατρέψει ένα αρχείο Word σε καθαρό markdown. Εδώ επίσης του λέμε να εξάγει τυχόν εξισώσεις OfficeMath ως LaTeX, που είναι το de‑facto πρότυπο για επιστημονικά έγγραφα.

```csharp
// 3️⃣ Configure markdown export options
var markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Store all extracted images in a dedicated folder
    ResourceSavingCallback = (s, e) =>
    {
        string assetsFolder = "YOUR_DIRECTORY/assets";
        Directory.CreateDirectory(assetsFolder);
        e.FileName = Path.Combine(assetsFolder, e.FileName);
    }
};

// Save as markdown
doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

*Τι θα δείτε:*  
- Ένα αρχείο `output.md` με τυπική σύνταξη markdown.  
- Όλες οι ενσωματωμένες εικόνες (συμπεριλαμβανομένου του σχήματος που μόλις σκίασαμε) αποθηκευμένες στο φάκελο `assets/`.  
- Οποιαδήποτε εξίσωση εμφανίζεται ως μπλοκ LaTeX `$…$`, έτοιμη για απόδοση από MathJax ή KaTeX.

## Βήμα 4: Αποθήκευση του Ίδιου Εγγράφου ως PDF/UA  

Το PDF/UA (PDF/Universal Accessibility) εξασφαλίζει ότι το PDF πληροί το ISO 14289‑1. Θα αναγκάσουμε επίσης τα αιωρούμενα σχήματα να αποθηκεύονται ως ενσωματωμένες ετικέτες, κάτι που απλοποιεί την ετικετοποίηση προσβασιμότητας.

```csharp
// 4️⃣ Set up PDF/UA compliance and inline floating shapes
var pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUAX2,
    ExportFloatingShapesAsInlineTag = true
};

// Save the PDF/UA file
doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Γιατί PDF/UA;*  
Αν το κοινό σας περιλαμβάνει χρήστες αναγνώστη οθόνης ή χρειάζεται να πληρούνται νομικά πρότυπα προσβασιμότητας, το PDF/UA είναι η σωστή επιλογή. Η σημαία `ExportFloatingShapesAsInlineTag` αποτρέπει τα αιωρούμενα αντικείμενα να διαταράσσουν τη λογική σειρά ανάγνωσης.

## Βήμα 5: Ανασκόπηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών  

Μετά τα βήματα μετατροπής, είναι καλή πρακτική να εμφανίσετε τυχόν προειδοποιήσεις σχετικές με γραμματοσειρές που καταγράψατε στο **Βήμα 1**.

```csharp
// 5️⃣ List font‑substitution warnings (if any)
var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
foreach (var warning in warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"⚠️ {warning.Description}");
}
```

Αν δείτε μηνύματα όπως *«Η γραμματοσειρά 'Calibri' αντικαταστάθηκε με την 'Arial'»* τώρα ξέρετε ακριβώς ποιες γραμματοσειρές λείπουν και μπορείτε να αποφασίσετε αν θα ενσωματώσετε μια εναλλακτική ή θα διανείμετε τη λείπουσα γραμματοσειρά με την εφαρμογή σας.

## Πλήρες Παράδειγμα Λειτουργίας  

Συνδυάζοντας όλα τα παραπάνω, ορίστε το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα νέο project console:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load with recovery mode and capture warnings
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            WarningCallback = new WarningInfoCollection()
        };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Add a shadow to the first shape
        Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.BlurRadius = 4;
        shape.ShadowFormat.Distance = 2;
        shape.ShadowFormat.Angle = 30;

        // Export to Markdown with LaTeX math and custom assets folder
        var markdownOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = (s, e) =>
            {
                string assetsFolder = "YOUR_DIRECTORY/assets";
                Directory.CreateDirectory(assetsFolder);
                e.FileName = Path.Combine(assetsFolder, e.FileName);
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);

        // Save as PDF/UA, forcing floating shapes inline
        var pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUAX2,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // Print any font‑substitution warnings
        var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
        foreach (var warning in warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ {warning.Description}");
        }
    }
}
```

### Αναμενόμενο Αποτέλεσμα  

- Το `output.md` περιέχει καθαρό markdown, εξισώσεις κωδικοποιημένες σε LaTeX, και συνδέσμους εικόνων όπως `![Shape](assets/shape0.png)`.  
- Το `output.pdf` είναι αρχείο συμβατό με PDF/UA που περνάει τον έλεγχο προσβασιμότητας του Adobe Acrobat.  
- Η έξοδος της κονσόλας καταγράφει τυχόν προειδοποιήσεις αντικατάστασης γραμματοσειρών, βοηθώντας σας να παρακολουθείτε τις ελλείπουσες γραμματοσειρές.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις  

**Τι γίνεται αν το έγγραφό μου έχει πολλά σχήματα;**  
Κάντε βρόχο μέσω `doc.GetChildNodes(NodeType.Shape, true)` και εφαρμόστε τις ρυθμίσεις σκιάς σε κάθε στοιχείο.  

**Μπορώ να αλλάξω το χρώμα της σκιάς;**  
Ναι—ορίστε `shape.ShadowFormat.Color = Color.Gray;` πριν την αποθήκευση.  

**Πρέπει να προσαρμόσω τη διαδρομή του φακέλου assets για web deployments;**  
Απόλυτα. Χρησιμοποιήστε σχετική διαδρομή ή ρυθμίστε ένα CDN URL στο `ResourceSavingCallback` για αποδοτική εξυπηρέτηση εικόνων.  

**Θα χάσει η εξαγωγή markdown κάποια χαρακτηριστικά που υπάρχουν μόνο στο Word;**  
Χαρακτηριστικά όπως αλλαγές παρακολούθησης, σχόλια ή πολύπλοκο SmartArt δεν αντιπροσωπεύονται στο markdown. Αν τα χρειάζεστε, διατηρήστε μια έκδοση PDF/UA ως εφεδρική λύση.

## Συμπέρασμα  

Μόλις μάθατε πώς να **εξάγετε Word σε markdown**, **προσθέτετε σκιά σε σχήμα**, και **αποθηκεύετε PDF/UA** χρησιμοποιώντας το Aspose.Words σε C#. Το πλήρες παράδειγμα κώδικα παρουσιάζει μια παραγωγική ροή εργασίας που διαχειρίζεται προειδοποιήσεις γραμματοσειρών, διαχείριση πόρων, και συμμόρφωση προσβασιμότητας—όλα σε ένα ενιαίο, εύκολο‑να‑διαβάσει script.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να αλλάξετε τις παραμέτρους σκιάς, πειραματιστείτε με διαφορετικές `MarkdownSaveOptions` (π.χ. `ExportImagesAsBase64`), ή ενσωματώστε αυτή τη διαδικασία σε ένα API ASP.NET Core που μετατρέπει αρχεία Word που ανεβάζουν οι χρήστες σε πραγματικό χρόνο. Και αν σας ενδιαφέρουν άλλες μορφές εξόδου, ρίξτε μια ματιά στις επιλογές εξαγωγής **HTML**, **EPUB**, ή **TIFF** του Aspose—κάθε μία ακολουθεί παρόμοιο μοτίβο.

Καλή προγραμματιστική, και ας αποδίδουν πάντα τα έγγραφά σας ακριβώς όπως τα φανταζόσασταν!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}