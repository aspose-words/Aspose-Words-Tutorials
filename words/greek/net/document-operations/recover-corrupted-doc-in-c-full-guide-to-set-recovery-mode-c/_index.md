---
category: general
date: 2025-12-18
description: Ανακτήστε γρήγορα ένα κατεστραμμένο έγγραφο ενεργοποιώντας τη λειτουργία
  ανάκτησης, στη συνέχεια μετατρέψτε το Word σε Markdown, ανεβάστε τις εικόνες του
  Markdown και εξάγετε τα μαθηματικά σε LaTeX—όλα σε ένα μόνο σεμινάριο.
draft: false
keywords:
- recover corrupted doc
- set recovery mode
- convert word to markdown
- upload markdown images
- export math to latex
language: el
og_description: Ανακτήστε κατεστραμμένο έγγραφο με λειτουργία ανάκτησης, στη συνέχεια
  μετατρέψτε το Word σε markdown, ανεβάστε τις εικόνες markdown και εξάγετε τα μαθηματικά
  σε LaTeX σε C#.
og_title: Ανάκτηση Κατεστραμμένου Εγγράφου – Ορισμός Λειτουργίας Ανάκτησης, Μετατροπή
  σε Markdown & Εξαγωγή Μαθηματικών
tags:
- Aspose.Words
- C#
- Document Processing
title: Ανάκτηση Κατεστραμμένου Εγγράφου σε C# – Πλήρης Οδηγός για Ρύθμιση Λειτουργίας
  Ανάκτησης & Μετατροπή Word σε Markdown
url: /greek/net/document-operations/recover-corrupted-doc-in-c-full-guide-to-set-recovery-mode-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση Κατεστραμμένου Εγγράφου – Από Κατεστραμμένα Αρχεία Word σε Καθαρό Markdown με Μαθηματικά LaTeX

Έχετε ανοίξει ποτέ ένα αρχείο Word που αρνείται να φορτωθεί επειδή είναι κατεστραμμένο; Αυτή είναι η ακριβής στιγμή που θα θέλατε να έχετε ένα **recover corrupted doc** κόλπο στο χέρι σας. Σε αυτό το tutorial θα δούμε πώς να ορίσετε τη λειτουργία ανάκτησης, να διασώσετε το περιεχόμενο, και στη συνέχεια **να μετατρέψετε το Word σε markdown**, **να ανεβάσετε εικόνες markdown**, και **να εξάγετε μαθηματικά σε LaTeX** – όλα χρησιμοποιώντας το Aspose.Words για .NET.

Γιατί είναι σημαντικό; Ένα κατεστραμμένο `.docx` μπορεί να εμφανιστεί ως συνημμένο σε email, σε παλαιά αρχεία ή μετά από απρόσμενη κατάρρευση. Η απώλεια του κειμένου, των εικόνων και των εξισώσεων είναι πραγματικό πρόβλημα, ειδικά αν χρειάζεται να μεταφέρετε το αρχείο σε μια σύγχρονη ροή εργασίας. Στο τέλος αυτού του οδηγού θα έχετε μια ενιαία, αυτόνομη λύση που επαναφέρει το έγγραφο και το μετατρέπει σε καθαρό, φορητό Markdown.

## Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.7.2+) με Visual Studio 2022 ή οποιοδήποτε IDE προτιμάτε.  
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Προαιρετικά: Azure Blob Storage SDK αν θέλετε πραγματικά να ανεβάσετε εικόνες· ο κώδικας περιλαμβάνει ένα stub που μπορείτε να αντικαταστήσετε.

Δεν απαιτούνται πρόσθετες βιβλιοθήκες τρίτων.

---

## Βήμα 1: Φόρτωση του Κατεστραμμένου Εγγράφου με Λειτουργία Ανάκτησης

Το πρώτο που πρέπει να κάνετε είναι να πείτε στο Aspose.Words πόσο επιθετικά πρέπει να προσπαθήσει να διορθώσει το αρχείο. Η παράμετρος `LoadOptions.RecoveryMode` προσφέρει τρεις επιλογές:

| Λειτουργία | Συμπεριφορά |
|------------|--------------|
| **Recover** | Προσπαθεί να επανακατασκευάσει το έγγραφο, διατηρώντας όσο το δυνατόν περισσότερα. |
| **Ignore** | Παραλείπει τα κατεστραμμένα τμήματα και φορτώνει το υπόλοιπο. |
| **Strict** | Ρίχνει εξαίρεση σε οποιαδήποτε κατεργασία (χρήσιμο για επικύρωση). |

Για μια τυπική επιχείρηση διάσωσης επιλέγουμε **Recover**.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1 – configure load options to recover a broken .docx
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover // you could also use .Ignore or .Strict
};

Document corruptedDoc = new Document(@"C:\Docs\corrupt.docx", loadOptions);
```

**Γιατί είναι σημαντικό:** Χωρίς τον ορισμό του `RecoveryMode`, το Aspose.Words θα σταματήσει στην πρώτη ένδειξη προβλήματος και θα ρίξει εξαίρεση, αφήνοντάς σας χωρίς τίποτα για επεξεργασία. Επιλέγοντας `Recover`, δίνετε στη βιβλιοθήκη την άδεια να εικάσει τα ελλείποντα τμήματα και να διατηρήσει το υπόλοιπο του αρχείου ζωντανό.

> **Συμβουλή:** Αν σας ενδιαφέρει μόνο το κειμενικό περιεχόμενο και μπορείτε να απορρίψετε τις σπασμένες εικόνες, το `RecoveryMode.Ignore` μπορεί να είναι ταχύτερο.

---

## Βήμα 2: Μετατροπή του Επιδιορθωμένου Εγγράφου Word σε Markdown

Τώρα που το έγγραφο βρίσκεται στη μνήμη, μπορούμε να το εξάγουμε σε Markdown. Η κλάση `MarkdownSaveOptions` ελέγχει πώς αποδίδονται διάφορα στοιχεία του Word. Για μια καθαρή μετατροπή θα διατηρήσουμε τις προεπιλεγμένες ρυθμίσεις, αλλά μπορείτε αργότερα να προσαρμόσετε τίτλους, πίνακες κ.λπ.

```csharp
// Step 2 – basic conversion to Markdown
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
corruptedDoc.Save(@"C:\Docs\output_basic.md", mdOptions);
```

Ανοίξτε το `output_basic.md` – θα δείτε τίτλους, λιστές με κουκίδες και απλές εικόνες που αναφέρονται με σχετικές διαδρομές. Τα επόμενα βήματα δείχνουν πώς να βελτιώσετε αυτές τις αναφορές εικόνων και να μετατρέψετε τυχόν ενσωματωμένες εξισώσεις.

---

## Βήμα 3: Εξαγωγή Εξισώσεων Office Math σε LaTeX

Αν το αρχείο Word περιέχει εξισώσεις, πιθανότατα θέλετε να τις έχετε σε μορφή που συνεργάζεται άψογα με στατικούς δημιουργούς ιστοτόπων ή Jupyter notebooks. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX` κάνει το σκληρό έργο.

```csharp
// Step 3 – export equations as LaTeX while saving Markdown
MarkdownSaveOptions latexOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};

corruptedDoc.Save(@"C:\Docs\output_math.md", latexOptions);
```

Στο παραγόμενο Markdown θα δείτε μπλοκ όπως:

```markdown
$$
\frac{a}{b} = c
$$
```

Αυτή είναι η αναπαράσταση LaTeX, έτοιμη για απόδοση με MathJax ή KaTeX.

> **Γιατί LaTeX;** Είναι το de‑facto πρότυπο για επιστημονικά έγγραφα στο web, και οι περισσότεροι στατικοί δημιουργοί ιστοτόπων καταλαβαίνουν τη σύνταξη `$$…$$` από προεπιλογή.

---

## Βήμα 4: Ανέβασμα Εικόνων Markdown σε Cloud Storage

Από προεπιλογή, το Aspose.Words γράφει τις εικόνες στον ίδιο φάκελο με το αρχείο Markdown και τις αναφέρει με σχετική διαδρομή. Σε πολλές CI/CD pipelines θέλετε αυτές τις εικόνες να φιλοξενούνται σε CDN. Το `ResourceSavingCallback` σας δίνει ένα hook για να παρεμβείτε σε κάθε ροή εικόνας και να αντικαταστήσετε το URL.

Παρακάτω υπάρχει ένα ελάχιστο παράδειγμα που προσποιείται την αποστολή της εικόνας στο Azure Blob Storage και στη συνέχεια ξαναγράφει το URL. Αντικαταστήστε τη μέθοδο `UploadToBlob` με τη δική σας υλοποίηση.

```csharp
// Step 4 – custom callback to upload images and replace URLs
MarkdownSaveOptions customResourceOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = (sender, args) =>
    {
        // args.ResourceName – original file name (e.g., image001.png)
        // args.Stream – a MemoryStream containing the image bytes

        // Replace this stub with your cloud upload logic.
        string uploadedUrl = UploadToBlob(args.ResourceName, args.Stream);
        args.ResourceUrl = uploadedUrl; // tells Aspose to write this URL in Markdown
    }
};

// Save again, now with cloud‑hosted image URLs
corruptedDoc.Save(@"C:\Docs\output_custom.md", customResourceOptions);
```

### Παράδειγμα Stub `UploadToBlob` (Αντικαταστήστε με πραγματικό κώδικα)

```csharp
private static string UploadToBlob(string fileName, Stream data)
{
    // In a real scenario you would:
    // 1. Authenticate to Azure Blob Storage.
    // 2. Upload the stream.
    // 3. Return the public URL (e.g., https://myaccount.blob.core.windows.net/docs/fileName)

    // For demo purposes we just return a placeholder URL.
    return $"https://example.com/assets/{fileName}";
}
```

Μετά την αποθήκευση, ανοίξτε το `output_custom.md`; θα δείτε συνδέσμους εικόνων όπως:

```markdown
![Image description](https://example.com/assets/image001.png)
```

Τώρα το Markdown σας είναι έτοιμο για οποιονδήποτε στατικό δημιουργό ιστοτόπων που τραβάει πόρους από CDN.

---

## Βήμα 5: Αποθήκευση του Εγγράφου ως PDF με Inline Tags για Floating Shapes

Μερικές φορές χρειάζεστε μια έκδοση PDF του ανακτημένου εγγράφου, ειδικά για νομικούς ή αρχειακούς σκοπούς. Τα floating shapes (πλαίσια κειμένου, WordArt) μπορεί να είναι δύσκολα· το Aspose.Words σας επιτρέπει να αποφασίσετε αν θα γίνουν block‑level tags ή inline tags. Τα inline tags διατηρούν τη διάταξη του PDF πιο συμπαγή, κάτι που προτιμούν πολλοί χρήστες.

```csharp
// Step 5 – PDF export with floating shapes as inline tags
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    ExportFloatingShapesAsInlineTag = true // set false for block‑level tagging
};

corruptedDoc.Save(@"C:\Docs\output.pdf", pdfOptions);
```

Ανοίξτε το PDF και ελέγξτε ότι όλα τα σχήματα εμφανίζονται στις σωστές θέσεις. Αν παρατηρήσετε ασυμφωνίες, αλλάξτε τη σημαία σε `false` και εξάγετε ξανά.

---

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα Συνδυασμένα)

Παρακάτω υπάρχει ένα πλήρες πρόγραμμα που μπορείτε να επικολλήσετε σε μια console εφαρμογή. Δείχνει όλη τη ροή εργασίας από τη φόρτωση ενός σπασμένου αρχείου μέχρι την παραγωγή Markdown με εξισώσεις LaTeX, εικόνες σε cloud και τελικό PDF.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class RecoverAndConvert
{
    static void Main()
    {
        // 1️⃣ Load corrupted DOCX with recovery mode
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"C:\Docs\corrupt.docx", loadOptions);

        // 2️⃣ Export to Markdown (basic)
        doc.Save(@"C:\Docs\output_basic.md", new MarkdownSaveOptions());

        // 3️⃣ Export to Markdown with LaTeX equations
        var latexOpts = new MarkdownSaveOptions { OfficeMathExportMode = OfficeMathExportMode.LaTeX };
        doc.Save(@"C:\Docs\output_math.md", latexOpts);

        // 4️⃣ Upload images and rewrite URLs
        var imgOpts = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string url = UploadToBlob(args.ResourceName, args.Stream);
                args.ResourceUrl = url;
            }
        };
        doc.Save(@"C:\Docs\output_custom.md", imgOpts);

        // 5️⃣ Save as PDF with inline floating shapes
        var pdfOpts = new PdfSaveOptions { ExportFloatingShapesAsInlineTag = true };
        doc.Save(@"C:\Docs\output.pdf", pdfOpts);

        Console.WriteLine("All files generated successfully.");
    }

    // Dummy uploader – replace with real cloud logic
    private static string UploadToBlob(string name, Stream data)
    {
        // TODO: Implement actual upload (Azure, AWS S3, etc.)
        return $"https://example.com/assets/{name}";
    }
}
```

Η εκτέλεση αυτού του προγράμματος παράγει:

| Αρχείο | Σκοπός |
|--------|--------|
| `output_basic.md` | Απλή μετατροπή σε Markdown |
| `output_math.md` | Markdown με LaTeX μαθηματικά |
| `output_custom.md` | Markdown όπου οι εικόνες δείχνουν σε CDN |
| `output.pdf` | PDF με floating shapes ως inline tags |

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

**Τι γίνεται αν το αρχείο είναι εντελώς ακατάγνωστο;**  
Ακόμη και με `RecoveryMode.Recover`, κάποια αρχεία είναι πέρα από την επισκευή. Σε αυτήν την περίπτωση θα λάβετε ένα κενό αντικείμενο `Document`. Ελέγξτε `doc.GetText().Length` μετά τη φόρτωση· αν είναι μηδέν, καταγράψτε την αποτυχία και ειδοποιήστε τον χρήστη.

**Πρέπει να ορίσω άδεια για το Aspose.Words;**  
Ναι. Σε παραγωγικό περιβάλλον πρέπει να εφαρμόσετε έγκυρη άδεια για να αποφύγετε το υδατογράφημα αξιολόγησης. Προσθέστε `new License().SetLicense("Aspose.Words.lic");` πριν τη φόρτωση του εγγράφου.

**Μπορώ να διατηρήσω την αρχική μορφή εικόνας (π.χ., SVG);**  
Το Aspose.Words μετατρέπει τις εικόνες σε PNG από προεπιλογή όταν αποθηκεύει σε Markdown. Αν χρειάζεστε SVG, πρέπει να εξάγετε το αρχικό stream από το `ResourceSavingCallback` και να το ανεβάσετε αμετάβλητο, στη συνέχεια να ορίσετε το `args.ResourceUrl` αναλόγως.

**Πώς διαχειρίζομαι πίνακες που περιέχουν εξισώσεις;**  
Οι πίνακες εξάγονται αυτόματα ως πίνακες Markdown. Οι εξισώσεις μέσα σε κελιά πίνακα θα μετατραπούν σε LaTeX αν έχετε ενεργοποιήσει το `OfficeMathExportMode.LaTeX`.

---

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **ανακτήσετε κατεστραμμένα doc** αρχεία, **ορίσετε λειτουργία ανάκτησης**, **μετατρέψετε Word σε markdown**, **ανεβάσετε εικόνες markdown**, και **εξάγετε μαθηματικά σε LaTeX**—όλα σε ένα ενιαίο, εύκολο‑ακολουθήσιμο πρόγραμμα C#. Εκμεταλλευόμενοι τις ευέλικτες επιλογές φόρτωσης και αποθήκευσης του Aspose.Words, μπορείτε να μετατρέψετε ένα σπασμένο `.docx` σε καθαρό, έτοιμο για web περιεχόμενο χωρίς χειροκίνητη αντιγραφή‑επικόλληση.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να ενσωματώσετε αυτή τη διαδικασία σε μια CI pipeline που παρακολουθεί έναν φάκελο για νέες ανεβάσεις `.docx`, τα αυτόματα διασώζει και σπρώχνει το παραγόμενο Markdown σε αποθετήριο Git. Μπορείτε επίσης να εξερευνήσετε τη μετατροπή του Markdown σε HTML με έναν στατικό δημιουργό ιστοτόπων όπως Hugo ή Jekyll, ολοκληρώνοντας τη ροή από άκρο σε άκρο.

Έχετε περισσότερα σενάρια—όπως διαχείριση αρχείων με κωδικό πρόσβασης ή εξαγωγή ενσωματωμένων γραμματοσειρών; Αφήστε ένα σχόλιο και θα εμβαθύνουμε μαζί. Καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}