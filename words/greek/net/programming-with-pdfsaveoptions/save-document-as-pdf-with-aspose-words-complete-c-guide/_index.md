---
category: general
date: 2026-05-01
description: Μάθετε πώς να αποθηκεύσετε το έγγραφο ως PDF χρησιμοποιώντας το Aspose.Words
  σε C#. Το σεμινάριο καλύπτει επίσης τη μετατροπή Word σε PDF, την εξαγωγή μαθηματικών
  σε LaTeX και τη διαχείριση ελλιπών γραμματοσειρών.
draft: false
keywords:
- save document as pdf
- convert word to pdf
- export math latex
- handle missing fonts
language: el
og_description: Αποθηκεύστε το έγγραφο ως PDF χωρίς κόπο με το Aspose.Words. Αυτός
  ο οδηγός δείχνει επίσης πώς να μετατρέψετε το Word σε PDF, να εξάγετε μαθηματικό
  LaTeX και να διαχειριστείτε τις ελλιπείς γραμματοσειρές.
og_title: Αποθήκευση εγγράφου ως PDF με το Aspose.Words – Πλήρης οδηγός C#
tags:
- Aspose.Words
- C#
- PDF generation
title: Αποθήκευση εγγράφου ως PDF με το Aspose.Words – Πλήρης οδηγός C#
url: /el/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου ως PDF με Aspose.Words – Πλήρης Οδηγός C# 

Έχετε αναρωτηθεί ποτέ **πώς να αποθηκεύσετε το έγγραφο ως pdf** απευθείας από ένα αρχείο Word χωρίς να χάσετε τα χαρακτηριστικά προσβασιμότητας; Δεν είστε μόνοι—οι προγραμματιστές ζητούν συνεχώς έναν αξιόπιστο τρόπο για να μετατρέψουν το Word σε PDF διατηρώντας τις μαθηματικές εξισώσεις και αντιμετωπίζοντας με χάρη τις ελλιπείς γραμματοσειρές.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια λύση που όχι μόνο **αποθηκεύει το έγγραφο ως pdf** αλλά επίσης δείχνει **convert word to pdf**, **export math latex**, και **handle missing fonts** χρησιμοποιώντας την πιο πρόσφατη έκδοση του Aspose.Words για .NET. Στο τέλος θα έχετε ένα έτοιμο προς εκτέλεση πρόγραμμα C# που παράγει αρχεία συμβατά με PDF/UA‑2, ιδανικά για ελέγχους προσβασιμότητας.

## Τι Θα Χρειαστείτε

- .NET 6 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Core και .NET Framework)  
- Aspose.Words for .NET 25.10 ή νεότερο – μπορείτε να κατεβάσετε μια δωρεάν δοκιμή από την ιστοσελίδα Aspose  
- Ένα απλό έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα αιωρούμενο σχήμα και μια μαθηματική εξίσωση (για να δείτε τη λειτουργία export‑math‑latex σε δράση)  
- Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε)

> **Συμβουλή επαγγελματία:** Αν βρίσκεστε σε CI/CD pipeline, προσθέστε το πακέτο NuGet Aspose.Words στο αρχείο του έργου σας:

```xml
<PackageReference Include="Aspose.Words" Version="25.10.0" />
```

Τώρα ας βουτήξουμε στον κώδικα.

## Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου με Αυτόματη Ανάκτηση

Κατά την επεξεργασία πραγματικών αρχείων Word μπορεί να συναντήσετε κατεστραμμένα τμήματα ή ελλιπείς πόρους. Η ενεργοποίηση της αυτόματης ανάκτησης εξασφαλίζει ότι η διαδικασία φόρτωσης δεν θα πετάξει ποτέ εξαίρεση.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Saving;

// LoadOptions tells Aspose how to behave while reading the file.
LoadOptions loadOptions = new LoadOptions
{
    // If the document is partially damaged, Aspose will try to fix it.
    RecoveryMode = RecoveryMode.AutoRecover
};

// Replace "YOUR_DIRECTORY" with the folder that holds your .docx.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Γιατί είναι σημαντικό:**  
`RecoveryMode.AutoRecover` προστατεύει το pipeline σας από κατάρρευση σε εσφαλμένα δεδομένα, κάτι που είναι ιδιαίτερα χρήσιμο όταν **convert word to pdf** μαζικά.

## Βήμα 2: Ρύθμιση Επιλογών Αποθήκευσης PDF για Πλήρη Προσβασιμότητα

Το PDF/UA‑2 είναι το πρότυπο ISO για προσβάσιμα PDF. Με τη ρύθμιση μερικών σημάνσεων (flags) λαμβάνουμε ένα αρχείο που οι αναγνώστες οθόνης μπορούν να περιηγηθούν, και επίσης διασφαλίζουμε ότι οι μαθηματικές εξισώσεις εξάγονται ως κρυφό LaTeX.

```csharp
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // Enforce PDF/UA‑2 compliance.
    PdfCompliance = PdfCompliance.PdfUa2,

    // Floating shapes (like text boxes) become <Figure> tags – essential for accessibility.
    ExportFloatingShapesAsInlineTag = true,

    // Export Office Math as hidden LaTeX (requires Aspose.Words 25.10+).
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

**Κύρια σημεία:**  

- **ExportFloatingShapesAsInlineTag** – εξασφαλίζει ότι το παραγόμενο PDF σέβεται την αρχική διάταξη ενώ παραμένει σημασιολογικά σωστό.  
- **OfficeMathExportMode.LaTeX** – ικανοποιεί την απαίτηση **export math latex**, επιτρέποντας στα επόμενα εργαλεία να εξάγουν τις εξισώσεις αν χρειαστεί.

## Βήμα 3: Συλλογή Προειδοποιήσεων (π.χ., Ελλιπείς Γραμματοσειρές)

Οι ελλιπείς γραμματοσειρές είναι ένα κοινό πρόβλημα κατά τη μετατροπή εγγράφων. Το Aspose.Words μπορεί να αναφέρει αυτά τα ζητήματα μέσω ενός `WarningCallback`. Θα τα συλλέξουμε ώστε να μπορείτε να τα καταγράψετε ή να δράσετε αργότερα.

```csharp
// Simple collector that stores all warnings in a list.
public class WarningInfoCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        Warnings.Add(info);
    }
}

// Attach the collector to the document.
document.WarningCallback = new WarningInfoCollector();
```

**Γιατί σας ενδιαφέρει:**  
Αν η πηγή χρησιμοποιεί γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή, το PDF θα επιστρέψει σε προεπιλεγμένη γραμματοσειρά, ενδεχομένως να σπάσει τη διάταξη. Με το **handle missing fonts** μπορούμε να ειδοποιήσουμε τον χρήστη ή να ενσωματώσουμε μια εναλλακτική.

## Βήμα 4: Αποθήκευση του Εγγράφου ως Προσβάσιμο PDF

Τώρα η στιγμή της αλήθειας—να εκτελέσουμε πραγματικά τη μετατροπή.

```csharp
// Save the PDF to the output folder.
document.Save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);
```

Αν όλα πάνε ομαλά, θα έχετε ένα αρχείο PDF/UA‑2 που περιέχει κρυφό LaTeX για κάθε εξίσωση και σωστή σήμανση για τα αιωρούμενα σχήματα.

## Βήμα 5: Ανασκόπηση Συλλεγμένων Προειδοποιήσεων (Προαιρετικό αλλά Συνιστάται)

Μετά τη λειτουργία αποθήκευσης, μπορείτε να επαναλάβετε τις συλλεγμένες προειδοποιήσεις και να τις καταγράψετε.

```csharp
var collector = (WarningInfoCollector)document.WarningCallback;

foreach (var warning in collector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Η τυπική έξοδος μπορεί να μοιάζει με:

```
FontSubstitution: Font "Calibri" was not found. Substituted with "Arial".
```

Η έγκαιρη εμφάνιση αυτών των μηνυμάτων σας βοηθά να **handle missing fonts** πριν επηρεάσουν τους τελικούς χρήστες.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα, εδώ είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντικαταστήστε τις διαδρομές placeholder με τις δικές σας.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Saving;

// ------------------------------------------------------------
// Step 0: Helper class for warning collection (handles missing fonts)
// ------------------------------------------------------------
public class WarningInfoCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info) => Warnings.Add(info);
}

// ------------------------------------------------------------
// Main conversion routine
// ------------------------------------------------------------
class Program
{
    static void Main()
    {
        // 1️⃣ Load the source .docx with auto‑recovery.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.AutoRecover };
        var document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Configure PDF/UA‑2 options (export math as LaTeX, handle floating shapes).
        var pdfOptions = new PdfSaveOptions
        {
            PdfCompliance = PdfCompliance.PdfUa2,
            ExportFloatingShapesAsInlineTag = true,
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 3️⃣ Attach warning collector to capture missing‑font alerts.
        document.WarningCallback = new WarningInfoCollector();

        // 4️⃣ Perform the conversion.
        document.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // 5️⃣ (Optional) Print any warnings to the console.
        var collector = (WarningInfoCollector)document.WarningCallback;
        foreach (var w in collector.Warnings)
        {
            Console.WriteLine($"{w.Type}: {w.Description}");
        }

        Console.WriteLine("✅ Conversion complete! PDF saved as output.pdf");
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
- `output.pdf` συμμορφώνεται με PDF/UA‑2.  
- Όλα τα αιωρούμενα σχήματα είναι σημειωμένα ως ενσωματωμένες εικόνες.  
- Κάθε αντικείμενο Office Math εμφανίζεται ως κρυφό LaTeX (ορατό όταν ελέγχετε τη δομή του PDF).  
- Οποιοδήποτε πρόβλημα σχετικό με γραμματοσειρές εκτυπώνεται στην κονσόλα, δίνοντάς σας την ευκαιρία να **handle missing fonts** πριν τη διανομή του αρχείου.

![Διάγραμμα που δείχνει τη ροή από Word → Aspose.Words → Προσβάσιμο PDF (save document as pdf)](conversion-diagram.png "Διάγραμμα ροής για την αποθήκευση εγγράφου ως pdf")

*Κείμενο alt εικόνας:* **Διάγραμμα του πώς να αποθηκεύσετε το έγγραφο ως pdf χρησιμοποιώντας το Aspose.Words**

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρησιμοποιώ παλαιότερη έκδοση του Aspose.Words;

Η σημαία `OfficeMathExportMode.LaTeX` εισήχθη στην έκδοση 25.10. Για παλαιότερες εκδόσεις μπορείτε ακόμη να **convert word to pdf**, αλλά τα μαθηματικά θα είναι rasterized αντί να εξαχθούν ως LaTeX. Αναβαθμίστε για τη βέλτιστη προσβασιμότητα.

### Μπορώ να ενσωματώσω προσαρμοσμένες γραμματοσειρές για να αποφύγω την εναλλακτική;

Ναι. Ορίστε `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll` πριν καλέσετε το `Save`. Αυτό επίσης βοηθά το **handle missing fonts** εξαναγκάζοντας το PDF να περιέχει τα απαιτούμενα γλύφους.

### Πώς μπορώ να επαληθεύσω τη συμμόρφωση PDF/UA‑2;

Ανοίξτε το αρχείο στο Adobe Acrobat Pro → “Print Production” → “Preflight”. Επιλέξτε το προφίλ “PDF/A‑2b” ή “PDF/UA‑2”; το Acrobat θα αναφέρει τυχόν παραβάσεις.

### Τι γίνεται με αρχεία Word προστατευμένα με κωδικό;

Φορτώστε το έγγραφο με ένα `LoadOptions` που περιλαμβάνει `Password`. Παράδειγμα:

```csharp
var loadOptions = new LoadOptions { Password = "mySecret" };
var doc = new Document("protected.docx", loadOptions);
```

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **save document as pdf** χρησιμοποιώντας το Aspose.Words σε C#. Το tutorial επίσης έδειξε πώς να **convert word to pdf**, **export math latex**, και **handle missing fonts**—όλα ενώ παράγουμε ένα προσβάσιμο αρχείο PDF/UA‑2.  

Δοκιμάστε τον κώδικα, πειραματιστείτε με διαφορετικές `PdfSaveOptions` (π.χ., συμπίεση εικόνας, PDF/A‑2b), και ενσωματώστε το στην υπηρεσία επεξεργασίας εγγράφων σας. Αν χρειάζεστε περισσότερα, εξετάστε τη βιβλιοθήκη PDF‑specific της Aspose για μετα-επεξεργασία ή ψηφιακές υπογραφές.  

Έχετε περισσότερα σενάρια που θέλετε να αντιμετωπίσετε; Μη διστάσετε να αφήσετε ένα σχόλιο ή να δείτε τις άλλες οδηγίες μας για **PDF manipulation**, **image extraction**, και **batch conversion**. Καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}