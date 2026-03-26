---
category: general
date: 2026-03-25
description: Δημιουργήστε κλήση προειδοποίησης για τη φόρτωση εγγράφου Word και την
  ανίχνευση ελλιπών γραμματοσειρών. Μάθετε πώς να ρυθμίσετε τις ρυθμίσεις γραμματοσειρών
  στο Aspose.Words για .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: el
og_description: Δημιουργήστε κλήση επιστροφής προειδοποίησης για τη φόρτωση εγγράφου
  Word ενώ εντοπίζετε ελλιπείς γραμματοσειρές. Αυτός ο οδηγός δείχνει πώς να ρυθμίσετε
  τις ρυθμίσεις γραμματοσειράς στο Aspose.Words.
og_title: Δημιουργία κλήσης προειδοποίησης – Φόρτωση εγγράφου Word & ανίχνευση ελλιπών
  γραμματοσειρών
tags:
- Aspose.Words
- C#
- Font handling
title: Δημιουργία προειδοποιητικής συνάρτησης επιστροφής για τη φόρτωση εγγράφων Word
  – Πλήρης Οδηγός
url: /el/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία callback προειδοποίησης – Φόρτωση εγγράφου Word & ανίχνευση ελλιπών γραμματοσειρών

Έχετε χρειαστεί ποτέ να **δημιουργήσετε callback προειδοποίησης** κατά τη φόρτωση ενός εγγράφου Word και να αναρωτηθείτε γιατί ορισμένες γραμματοσειρές εξαφανίζονται; Δεν είστε ο μόνος. Σε πολλές επιχειρηματικές εφαρμογές, οι ελλιπείς γραμματοσειρές προκαλούν καταστροφές διάταξης, και χωρίς ένα σωστό callback μπορεί να μην παρατηρήσετε καν το πρόβλημα.  

Τα καλά νέα; Με το Aspose.Words for .NET μπορείτε να **φορτώσετε έγγραφο Word**, **ανιχνεύσετε ελλιπείς γραμματοσειρές**, και **ρυθμίσετε τις ρυθμίσεις γραμματοσειρών** όλα σε λίγες καθαρές γραμμές κώδικα. Σε αυτό το tutorial θα περάσουμε από ένα πλήρες, εκτελέσιμο παράδειγμα, θα εξηγήσουμε γιατί κάθε μέρος είναι σημαντικό, και θα σας δείξουμε πώς να επαληθεύσετε ότι το callback προειδοποίησης κάνει τη δουλειά του.

> **Τι θα αποκομίσετε**  
> * Ένα πλήρες πρόγραμμα C# που φορτώνει ένα DOCX, αναφέρει τυχόν αντικαταστάσεις γραμματοσειρών, και σας επιτρέπει να προσαρμόσετε τις διαδρομές αναζήτησης γραμματοσειρών.  
> * Κατανόηση των κλάσεων `FontSettings`, `LoadOptions` και `IWarningCallback`.  
> * Συμβουλές για τη διαχείριση edge‑cases όπως ενσωματωμένες γραμματοσειρές ή φάκελοι γραμματοσειρών σε ολόκληρο το σύστημα.

---

## Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.7.2+) με μεταγλωττιστή C#.  
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Ένα δείγμα αρχείου Word (`input.docx`) που χρησιμοποιεί τουλάχιστον μία γραμματοσειρά που δεν είναι εγκατεστημένη στο μηχάνημα (π.χ., *Calibri Light* σε ένα ελάχιστο Windows container).  
- Βασική εξοικείωση με εφαρμογές κονσόλας C#.

Δεν απαιτούνται πρόσθετες βιβλιοθήκες· όλα ζουν μέσα στο Aspose.Words.

## Βήμα 1: Δημιουργία callback προειδοποίησης για ανίχνευση ελλιπών γραμματοσειρών

Το **κύριο** κομμάτι αυτού του παζλ είναι μια κλάση που υλοποιεί το `IWarningCallback`. Το Aspose.Words θα καλέσει αυτό το callback όποτε αντιμετωπίσει μια κατάσταση που απαιτεί προειδοποίηση – η αντικατάσταση γραμματοσειράς είναι η πιο συνηθισμένη.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Γιατί είναι σημαντικό** – Χωρίς ένα callback θα πρέπει να ψάχνετε στα αρχεία καταγραφής μετά το γεγονός. Με τη διαχείριση των προειδοποιήσεων σε πραγματικό χρόνο μπορείτε να αποφασίσετε αν θα ακυρώσετε τη φόρτωση, θα αντικαταστήσετε τη λείπουσα γραμματοσειρά με εναλλακτική, ή απλώς να καταγράψετε το ζήτημα για μελλοντική ανασκόπηση.

## Βήμα 2: Διαμόρφωση FontSettings για προσαρμοσμένη διαχείριση γραμματοσειρών

Πριν πραγματικά φορτώσουμε το έγγραφο, ίσως θέλουμε να πούμε στο Aspose.Words πού να ψάξει για γραμματοσειρές που δεν υπάρχουν στο σύστημα. Εκεί έρχεται το `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Γιατί είναι σημαντικό** – Δείχνοντας στο Aspose.Words έναν φάκελο που περιέχει τις λείπουσες γραμματοσειρές, συχνά αποφεύγετε εντελώς την αντικατάσταση. Όταν αυτό δεν είναι δυνατό, ένα λογικό προεπιλεγμένο (όπως *Arial*) διατηρεί το έγγραφο αναγνώσιμο.

## Βήμα 3: Φόρτωση εγγράφου Word με το διαμορφωμένο callback προειδοποίησης

Τώρα συνδέουμε όλα μαζί: δημιουργούμε το `LoadOptions`, ενσωματώνουμε το `FontSettings` και το `FontWarningHandler` μας, και τέλος φορτώνουμε το έγγραφο.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Γιατί είναι σημαντικό** – Το `LoadOptions` είναι το μοναδικό σημείο όπου ρυθμίζετε *πώς* διαβάζεται ένα έγγραφο. Παρέχοντας τόσο τη διαμόρφωση γραμματοσειρών όσο και το callback προειδοποίησης, διασφαλίζουμε ότι οποιαδήποτε λείπουσα γραμματοσειρά θα αναζητηθεί στα σωστά μέρη **και** θα αναφερθεί αμέσως.

## Βήμα 4: Επαλήθευση της εξόδου – τι πρέπει να δείτε;

Εκτελέστε το πρόγραμμα από την κονσόλα. Αν το `input.docx` χρησιμοποιεί μια γραμματοσειρά που δεν είναι εγκατεστημένη και επίσης δεν βρίσκεται στο `C:\SharedFonts`, θα δείτε κάτι όπως:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Αν όλες οι γραμματοσειρές είναι διαθέσιμες, η γραμμή προειδοποίησης απλώς δεν εμφανίζεται. Αυτός ο άμεσος βρόχος ανάδρασης είναι ανεκτίμητος κατά τη διάρκεια αυτοματοποιημένων pipelines επεξεργασίας εγγράφων, όπου σιωπηλές αντικαταστάσεις γραμματοσειρών θα μπορούσαν να παραβιάσουν τις οδηγίες branding.

## Βήμα 5: Συνηθισμένα λάθη και συμβουλές βέλτιστων πρακτικών

| Πρόβλημα | Πώς να το αποφύγετε |
|----------|----------------------|
| **Ξεχάσατε να αναφέρετε το `Aspose.Words.Fonts`** | Βεβαιωθείτε ότι έχετε `using Aspose.Words.Fonts;` στην αρχή· διαφορετικά ο μεταγλωττιστής θα παραπονεθεί για ελλιπείς τύπους. |
| **Η διαδρομή του φακέλου γραμματοσειρών είναι λανθασμένη** | Ελέγξτε ξανά τη διαδρομή και ορίστε `recursive: true` αν έχετε υποφακέλους. Χρησιμοποιήστε `Path.GetFullPath` για αποσφαλμάτωση. |
| **Πολλαπλά callbacks προειδοποίησης** | Το Aspose.Words αναγνωρίζει μόνο το τελευταίο `WarningCallback` που ορίζετε. Διατηρήστε έναν ενιαίο χειριστή που θα αναθέτει αν χρειάζεστε πιο σύνθετη λογική. |
| **Εκτέλεση σε διακομιστή χωρίς UI** | Οι εγγραφές στην κονσόλα είναι εντάξει, αλλά για web εφαρμογές ίσως θέλετε να καταγράψετε σε αρχείο ή σύστημα παρακολούθησης αντί για `Console.WriteLine`. |
| **Μεγάλα έγγραφα προκαλούν μείωση απόδοσης** | Επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο `FontSettings` σε πολλαπλές φορτώσεις· η επαναλαμβανόμενη δημιουργία του μπορεί να είναι δαπανηρή. |

**Συμβουλή:** Αν χρειάζεται να *συλλέξετε* προειδοποιήσεις για μεταγενέστερη ανάλυση, αποθηκεύστε τις σε μια `List<string>` μέσα στον χειριστή αντί να τις εκτυπώνετε απευθείας.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Μπορείτε τότε να ελέγξετε το `handler.Messages` μετά τη φόρτωση του εγγράφου.

## Βήμα 6: Επέκταση της λύσης – τι γίνεται αν χρειαστεί να ενσωματώσω μια εναλλακτική γραμματοσειρά;

Μερικές φορές θέλετε η λείπουσα γραμματοσειρά να *ενσωματωθεί* στο παραγόμενο PDF ώστε οι επόμενοι προβολείς να δουν την ακριβή εμφάνιση. Μετά τη φόρτωση του εγγράφου, μπορείτε να εξαναγκάσετε την ενσωμάτωση:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Αυτό το απόσπασμα δείχνει πώς η ίδια προσέγγιση **διαμόρφωσης ρυθμίσεων γραμματοσειρών** μπορεί να επεκταθεί πέρα από τη φόρτωση.

## Πλήρες εκτελέσιμο παράδειγμα

Ακολουθεί το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα νέο έργο Console App. Περιλαμβάνει όλα τα κομμάτια που συζητήθηκαν παραπάνω.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Αναμενόμενη έξοδος** (όταν υπάρχει λείπουσα γραμματοσειρά):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Αν δεν γίνει αντικατάσταση, εμφανίζονται μόνο τα μηνύματα επιτυχίας.

## Συμπέρασμα

Μόλις **δημιουργήσαμε ένα callback προειδοποίησης** που εντοπίζει αξιόπιστα τις **ελλιπείς γραμματοσειρές** κατά τη **φόρτωση ενός εγγράφου Word** με το Aspose.Words, και δείξαμε πώς να **ρυθμίζουμε τις ρυθμίσεις γραμματοσειρών** για να ελέγχετε πού ψάχνει η βιβλιοθήκη για γραμματοσειρές και ποια εναλλακτική θα χρησιμοποιήσει. Συνδέοντας τα `FontSettings` και `LoadOptions`, αποκτάτε πλήρη ορατότητα στα ζητήματα που σχετίζονται με τις γραμματοσειρές — χωρίς σιωπηλές διαταραχές διάταξης.

Επόμενα βήματα; Δοκιμάστε να αντικαταστήσετε το `FontWarningHandler` με έναν καταγραφέα που γράφει σε βάση δεδομένων, ή πειραματιστείτε με **κανόνες αντικατάστασης γραμματοσειρών** για να αντιστοιχίσετε συγκεκριμένες ελλιπείς γραμματοσειρές σε εναλλακτικές εγκεκριμένες από το brand. Μπορείτε επίσης να εξερευνήσετε **δυναμική φόρτωση γραμματοσειρών** από αποθήκευση στο cloud αν η εφαρμογή σας τρέχει σε περιβάλλον container.

Έχετε ερωτήσεις για κάποιο συγκεκριμένο edge case — όπως η διαχείριση χαρακτηριστικών OpenType ή η αντιμετώπιση κρυπτογραφημένων αρχείων DOCX; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική!

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}