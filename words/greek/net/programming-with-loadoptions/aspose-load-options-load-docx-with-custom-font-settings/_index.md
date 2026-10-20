---
category: general
date: 2025-12-29
description: Οι επιλογές φόρτωσης Aspose σάς επιτρέπουν να φορτώνετε αρχεία DOCX προσαρμόζοντας
  τις ρυθμίσεις γραμματοσειράς και εντοπίζοντας τις ελλιπείς γραμματοσειρές. Μάθετε
  πώς να φορτώνετε docx με πλήρη έλεγχο.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: el
og_description: Οι επιλογές φόρτωσης Aspose σάς επιτρέπουν να φορτώνετε αρχεία DOCX
  προσαρμόζοντας τις ρυθμίσεις γραμματοσειράς και ανιχνεύοντας ελλείπουσες γραμματοσειρές.
  Μάθετε πώς να φορτώνετε docx με πλήρη έλεγχο.
og_title: Επιλογές Φόρτωσης Aspose – Φόρτωση DOCX με Προσαρμοσμένες Ρυθμίσεις Γραμματοσειράς
tags:
- Aspose.Words
- C#
- Document Processing
title: Επιλογές Φόρτωσης Aspose – Φόρτωση DOCX με Προσαρμοσμένες Ρυθμίσεις Γραμματοσειράς
url: /el/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Φόρτωση DOCX με Προσαρμοσμένες Ρυθμίσεις Γραμματοσειράς

Έχετε αναρωτηθεί ποτέ πώς να φορτώσετε ένα αρχείο DOCX σε C# χωρίς να αντιμετωπίσετε ελλείπουσες γραμματοσειρές; Δεν είστε μόνοι. **Aspose Load Options** σας δίνουν τη δυνατότητα να ελέγχετε ακριβώς πώς ανοίγεται ένα έγγραφο Word, επιτρέποντάς σας να ορίσετε προσαρμοσμένες ρυθμίσεις γραμματοσειράς και ακόμη να εντοπίσετε ελλείπουσες γραμματοσειρές πριν γίνουν πρόβλημα.

> **Προαπαιτούμενο** – Χρειάζεστε το Aspose.Words for .NET (τελευταία έκδοση) αναφορά στο πρότζεκτ σας και βασική εξοικείωση με τη C#. Δεν απαιτούνται άλλες βιβλιοθήκες.

## Τι Θα Μάθετε

- Πώς να δημιουργήσετε ένα αντικείμενο `LoadOptions` και να συνδέσετε μια συνάρτηση ειδοποίησης.  
- Πώς να ρυθμίσετε το `FontSettings` για **custom font settings**.  
- Πώς να **φορτώσετε docx** και να επαληθεύσετε ότι οι ελλείπουσες γραμματοσειρές αναφέρονται.  
- Συμβουλές για τη διαχείριση edge‑cases όπως ενσωματωμένες γραμματοσειρές ή φάκελοι γραμματοσειρών μέσω δικτύου.

## Βήμα 1: Εγκατάσταση Aspose.Words και Προετοιμασία του Έργου

Πρώτα απ' όλα, βεβαιωθείτε ότι το Aspose.Words είναι εγκατεστημένο. Ο πιο εύκολος τρόπος είναι μέσω NuGet:

```bash
dotnet add package Aspose.Words
```

Μόλις προστεθεί το πακέτο, δημιουργήστε ένα νέο C# console project (ή ενσωματώστε τον κώδικα σε οποιαδήποτε υπάρχουσα εφαρμογή). Ο κώδικας που θα γράψουμε λειτουργεί με .NET 6+ και .NET Framework 4.7.2+, έτσι καλύπτεστε και στις δύο περιπτώσεις.

> **Συμβουλή επαγγελματία:** Αν στοχεύετε σε .NET Core, προσθέστε `using System;` στην αρχή του αρχείου· το IDE συνήθως το προσθέτει αυτόματα.

## Βήμα 2: Διαμόρφωση Aspose Load Options με Callback Προειδοποίησης

Τώρα φτάνουμε στην ουσία—**aspose load options**. Η κλάση `LoadOptions` σας επιτρέπει να προσαρμόσετε τον τρόπο ανάλυσης ενός εγγράφου. Θα τη χρησιμοποιήσουμε για:

1. Συνδέστε ένα callback που ενεργοποιείται κάθε φορά που ο φορτωτής δεν μπορεί να βρει τη ζητούμενη γραμματοσειρά.  
2. Αναθέστε ένα αντικείμενο `FontSettings` που μπορεί αργότερα να προσαρμοστεί για **custom font settings**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Γιατί είναι σημαντικό:** Χωρίς ένα callback προειδοποίησης, το Aspose αντικαθιστά σιωπηλά τις ελλείπουσες γραμματοσειρές, κάτι που μπορεί να προκαλέσει εκπλήξεις στη διάταξη αργότερα. Συνδέοντας το callback, **εντοπίζετε νωρίς τις ελλείπουσες γραμματοσειρές** και μπορείτε να αποφασίσετε αν θα ενσωματώσετε εναλλακτική ή θα ζητήσετε από τον χρήστη να εγκαταστήσει τη λείπουσα γραμματοσειρά.

## Βήμα 3: Φόρτωση του DOCX Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Με το `LoadOptions` έτοιμο, η φόρτωση ενός DOCX γίνεται με μία γραμμή κώδικα. Ο κατασκευαστής `Document` δέχεται τη διαδρομή του αρχείου και τις επιλογές που μόλις δημιουργήσαμε.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Αν το πηγαίο αρχείο αναφέρει μια γραμματοσειρά που δεν υπάρχει στο σύστημα ή στον προσαρμοσμένο φάκελο, θα δείτε έξοδο όπως:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Αυτή η άμεση ανατροφοδότηση είναι ανεκτίμητη όταν δημιουργείτε μια αλυσίδα επεξεργασίας παρτίδας που πρέπει να εγγυάται οπτική πιστότητα.

## Βήμα 4: Επαλήθευση του Φορτωμένου Εγγράφου (Προαιρετικό αλλά Χρήσιμο)

Μετά τη φόρτωση, ίσως θέλετε να επιβεβαιώσετε ότι το περιεχόμενο του εγγράφου είναι προσβάσιμο. Για έναν γρήγορο έλεγχο, ας εμφανίσουμε το κείμενο της πρώτης παραγράφου.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Η εκτέλεση του προγράμματος τώρα θα δώσει:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Βήμα 5: Edge Cases & Προηγμένες Συμβουλές

### 5.1 Διαχείριση Ενσωματωμένων Γραμματοσειρών

Ορισμένα αρχεία DOCX ενσωματώνουν άμεσα τις απαιτούμενες γραμματοσειρές. Το Aspose.Words τις χρησιμοποιεί αυτόματα, έτσι δεν θα δείτε προειδοποιήσεις γι' αυτές. Ωστόσο, αν σκόπιμα **load word document** αρχεία που αφαιρούν τις ενσωματωμένες γραμματοσειρές (π.χ., μετά από μετατροπή), ίσως χρειαστεί να παρέχετε τις ελλείπουσες γραμματοσειρές μέσω `SetFontsFolder` όπως φαίνεται παραπάνω.

### 5.2 Χρήση Memory Stream Αντί για Διαδρομή Αρχείου

Αν το DOCX σας βρίσκεται σε βάση δεδομένων ή προέρχεται από αίτημα HTTP, μπορείτε να το φορτώσετε από ένα `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Οι ίδιες **aspose load options** ισχύουν, και το callback προειδοποίησης λειτουργεί ακόμη.

### 5.3 Παράκαμψη Υποκατάστασης Γραμματοσειράς Καθολικά

Αν προτιμάτε να αντικαθιστάτε τις ελλείπουσες γραμματοσειρές με μια συγκεκριμένη εναλλακτική (π.χ., Arial), μπορείτε να προσθέσετε έναν κανόνα υποκατάστασης:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Συνδυάστε αυτό με το callback προειδοποίησης για να καταγράετε το γεγονός υποκατάστασης και να διατηρήσετε τη συνέπεια της εξόδου.

## Βήμα 6: Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες πρόγραμμα, έτοιμο για αντιγραφή‑επικόλληση, που ενσωματώνει όλα τα παραπάνω βήματα. Αποθηκεύστε το ως `Program.cs`, επαναφέρετε τα πακέτα NuGet και τρέξτε.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Αναμενόμενη Έξοδος

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Αν δεν λείπουν γραμματοσειρές, οι γραμμές προειδοποίησης απλώς δεν θα εμφανιστούν.

## Οπτική Επισκόπηση

![aspose load options example](/images/aspose-load-options.png "Diagram showing Aspose Load Options workflow")

*Το διάγραμμα δείχνει πώς τα **Aspose Load Options** τοποθετούνται μεταξύ της πηγής του αρχείου σας και του αντικειμένου `Document`, διαχειριζόμενα την επίλυση γραμματοσειρών και την ανίχνευση ελλιπών γραμματοσειρών.*

## Συμπέρασμα

Διασχίσαμε μια πλήρη λύση για **aspose load options**, δείχνοντάς σας ακριβώς **πώς να φορτώσετε docx** εφαρμόζοντας **custom font settings** και **εντοπίζοντας ελλείπουσες γραμματοσειρές**. Με τη ρύθμιση ενός callback προειδοποίησης και προαιρετικά με την κατεύθυνση του Aspose σε έναν προσαρμοσμένο φάκελο γραμματοσειρών, αποκτάτε πλήρη ορατότητα στα προβλήματα γραμματοσειρών πριν επηρεάσουν την απόδοση.  

Από εδώ μπορείτε να εξερευνήσετε συναφή θέματα όπως η μετατροπή **load word document** σε PDF, η προσθήκη υδατογραφιών ή η επεξεργασία παρτίδας δεκάδων αρχείων σε φάκελο. Το ίδιο μοτίβο—δημιουργία `LoadOptions`, σύνδεση callbacks και κλήση `new Document(...)`—λειτουργεί σε όλο το API του Aspose.Words.

Έχετε ερωτήσεις για κάποιο συγκεκριμένο edge case, όπως η διαχείριση γλωσσών από δεξιά προς αριστερά ή κρυπτογραφημένωνείων DOCX; Αφήστε ένα σχόλιο ή ελέγξτε την τεκμηρίωση του Aspose.Words για πιο λεπτομερείς πληροφορίες. Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα ακριβώς όπως προορίζεται!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}