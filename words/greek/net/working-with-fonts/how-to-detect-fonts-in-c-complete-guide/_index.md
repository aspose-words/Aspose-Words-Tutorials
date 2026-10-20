---
category: general
date: 2026-04-02
description: Πώς να εντοπίζετε τις γραμματοσειρές σε έγγραφα C# χρησιμοποιώντας το
  Aspose.Words. Μάθετε πώς να διαμορφώνετε τις ρυθμίσεις γραμματοσειρών και να διαχειρίζεστε
  αποτελεσματικά τις ελλιπείς γραμματοσειρές.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: el
og_description: Πώς να εντοπίσετε τις γραμματοσειρές σε έγγραφα C# χρησιμοποιώντας
  το Aspose.Words. Αυτός ο οδηγός σας δείχνει πώς να διαμορφώσετε τις ρυθμίσεις γραμματοσειράς
  και να διαχειριστείτε τις ελλείπουσες γραμματοσειρές.
og_title: Πώς να ανιχνεύσετε γραμματοσειρές σε C# – Πλήρης οδηγός
tags:
- C#
- Aspose.Words
- Document Processing
title: Πώς να ανιχνεύσετε γραμματοσειρές σε C# – Πλήρης οδηγός
url: /el/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εντοπίσετε τις Γραμματοσειρές σε C# – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να εντοπίσετε τις γραμματοσειρές** που λείπουν ή αντικαθίστανται όταν φορτώνετε ένα έγγραφο Word σε .NET; Δεν είστε οι μόνοι—οι προγραμματιστές συχνά αντιμετωπίζουν το πρόβλημα όταν ένα έγγραφο αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή. Τα καλά νέα είναι ότι το Aspose.Words σας παρέχει έναν καθαρό, προγραμματιζόμενο τρόπο για να εντοπίσετε αυτά τα κενά.

Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό παράδειγμα που όχι μόνο δείχνει **πώς να εντοπίσετε τις γραμματοσειρές**, αλλά επίσης επιδεικνύει πώς να **ρυθμίσετε τις ρυθμίσεις γραμματοσειρών** και να **χειριστείτε τις ελλιπείς γραμματοσειρές** με χάρη. Στο τέλος θα έχετε ένα έτοιμο κομμάτι κώδικα που εκτυπώνει κάθε προειδοποίηση αντικατάστασης γραμματοσειράς, ώστε να μπορείτε να το καταγράψετε, να το ειδοποιήσετε ή να αντικαταστήσετε τις γραμματοσειρές όπως χρειάζεται.

---

## Τι Θα Χρειαστείτε

- **Aspose.Words for .NET** (η πιο πρόσφατη έκδοση λειτουργεί καλύτερα· ο κώδικας παρακάτω στοχεύει σε .NET 6+)
- Ένα περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή VS Code)
- Ένα δείγμα αρχείου `.docx` που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (τέλειο για δοκιμές)

Δεν απαιτούνται επιπλέον πακέτα NuGet εκτός από το Aspose.Words, και η λύση λειτουργεί σε Windows, Linux και macOS.

---

## Βήμα 1: Εγκατάσταση και Αναφορά του Aspose.Words

Πρώτα, προσθέστε τη βιβλιοθήκη στο έργο σας. Η εντολή NuGet είναι απλή:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Αν εργάζεστε σε διακομιστή CI, κλειδώστε την έκδοση του πακέτου για να αποφύγετε απρόσμενες αλλαγές που σπάζουν τον κώδικα.

---

## Βήμα 2: Ρύθμιση των Ρυθμίσεων Γραμματοσειράς (και Προετοιμασία Load Options)

Πριν ανοίξετε ένα έγγραφο, μπορείτε να πείτε στο Aspose.Words πού να ψάξει για εναλλακτικές γραμματοσειρές. Αυτό είναι το τμήμα **configure font settings** που αποτρέπει τη μηχανή από το να αντικαθιστά σιωπηρά γραμματοσειρές που δεν θέλετε.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Γιατί να το κάνετε; Αν το έγγραφο αναφέρει *Comic Sans* αλλά ο διακομιστής σας έχει μόνο *Calibri*, το Aspose.Words θα αντικαταστήσει το *Calibri* και θα δημιουργήσει μια προειδοποίηση. Με τη ρύθμιση της διαδρομής αναζήτησης, μειώνετε τις ανεπιθύμητες εκπλήξεις.

---

## Βήμα 3: Φόρτωση του Εγγράφου με τις Προετοιμασμένες Επιλογές

Τώρα ανοίγουμε πραγματικά το αρχείο. Οι `LoadOptions` που δημιουργήσαμε στο προηγούμενο βήμα περνιούνται απευθείας στον κατασκευαστή `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Αν το αρχείο δεν βρεθεί ή είναι κατεστραμμένο, θα ριχτεί εξαίρεση—γι' αυτό ίσως θελήσετε να το τυλίξετε σε try/catch σε κώδικα παραγωγής.

---

## Βήμα 4: Σάρωση των Προειδοποιήσεων του Εγγράφου για Αντικαταστάσεις Γραμματοσειρών

Το Aspose.Words συλλέγει μια λίστα προειδοποιήσεων κατά την ανάλυση. Μεταξύ αυτών, η `FontSubstitutionWarning` σας λέει ακριβώς ποια γραμματοσειρά αντικαταστάθηκε.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

Η συλλογή `Warnings` μπορεί επίσης να περιέχει άλλα στοιχεία (π.χ., `DocumentStructureWarning`). Η φιλτράρισμα για `FontSubstitutionWarning` εξασφαλίζει ότι αναφέρουμε μόνο το σενάριο **handle missing fonts** που μας ενδιαφέρει.

---

## Βήμα 5: Συνδυάστε Όλα – Ένα Πλήρες, Εκτελέσιμο Παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα. Αντιγράψτε‑και‑επικολλήστε το σε μια νέα εφαρμογή κονσόλας και τρέξτε το· θα δείτε κάθε ελλιπής γραμματοσειρά να εκτυπώνεται στην κονσόλα.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Αναμενόμενη έξοδος** (παράδειγμα):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Αν το έγγραφο χρησιμοποιεί μόνο γραμματοσειρές που υπάρχουν στο μηχάνημα, θα δείτε τη γραμμή “No font substitutions detected” αντί αυτού.

---

## Ακραίες Περιπτώσεις & Συχνές Ερωτήσεις

### Τι γίνεται αν το έγγραφο **δεν περιέχει καθόλου προειδοποιήσεις**;

Αυτό σημαίνει απλώς ότι κάθε αναφερόμενη γραμματοσειρά βρέθηκε στους φακέλους αναζήτησης που ρυθμίσατε. Η σημαία `anySubstitutions` στο παράδειγμα καλύπτει αυτήν την περίπτωση.

### Μπορώ να **καταγράψω** τις προειδοποιήσεις σε αρχείο αντί για την κονσόλα;

Απόλυτα. Αντικαταστήστε τις κλήσεις `Console.WriteLine` με έναν logger της επιλογής σας (Serilog, NLog κ.λπ.). Το αντικείμενο `WarningInfo` εκθέτει επίσης `WarningType` και `WarningMessage` αν χρειάζεστε περισσότερες λεπτομέρειες.

### Πώς μπορώ να **αγνοήσω** ορισμένες γραμματοσειρές, όπως μια εταιρική γραμματοσειρά που δεν πρέπει ποτέ να αντικατασταθεί;

Μπορείτε να προσθέσετε έναν προσαρμοσμένο κανόνα αντικατάστασης:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Τώρα το Aspose.Words θα αντικαθιστά μόνο το *MyBrandFont* με τις αναφερόμενες εναλλακτικές, και θα λαμβάνετε ακόμη μια προειδοποίηση που μπορείτε να επεξεργαστείτε.

### Λειτουργεί αυτό σε **Linux** containers;

Ναι—απλώς βεβαιωθείτε ότι έχετε προσαρτήσει έναν φάκελο με τα απαιτούμενα αρχεία `.ttf`/`.otf` και δείξτε το `SetFontsFolder` σε αυτόν. Το Aspose.Words δεν εξαρτάται από τις γραμματοσειρές που είναι εγκατεστημένες στο OS.

---

## Οπτική Επισκόπηση

![how to detect fonts flowchart](detect-fonts.png "Diagram showing the steps to detect fonts in a document")

*Image alt text:* **how to detect fonts** flowchart illustrating configuration, loading, and warning inspection.

---

## Ανακεφαλαίωση – Τι Μάθαμε

- **Πώς να εντοπίσετε τις γραμματοσειρές** που λείπουν ή αντικαθίστανται χρησιμοποιώντας τις προειδοποιήσεις του Aspose.Words.  
- Πώς να **ρυθμίσετε τις ρυθμίσεις γραμματοσειράς** ώστε να δείχνουν σε προσαρμοσμένους φακέλους γραμματοσειρών και να ορίσετε προεπιλεγμένη εναλλακτική.  
- Στρατηγικές για **χειρισμό ελλιπών γραμματοσειρών**, από καταγραφή μέχρι προσαρμοσμένους κανόνες αντικατάστασης.

Όλα αυτά ενσωματώνονται σε μια συμπαγή, αυτόνομη εφαρμογή κονσόλας που μπορείτε να ενσωματώσετε σε οποιαδήποτε λύση .NET.

---

## Επόμενα Βήματα & Σχετικά Θέματα

- **Ενσωμάτωση γραμματοσειρών** απευθείας στο τελικό έγγραφο για να αποφύγετε μελλοντικές αντικαταστάσεις (`SaveOptions` με `EmbedFullFonts`).  
- **Προγραμματική αντικατάσταση γραμματοσειρών** – αντικατάσταση ελλιπών γραμματοσειρών με συγκεκριμένη εναλλακτική πριν από την αποθήκευση.  
- **Βελτιστοποίηση απόδοσης** – cache το `FontSettings` όταν επεξεργάζεστε πολλά έγγραφα σε batch.  

Αν σας ενδιαφέρουν αυτά τα θέματα, αναζητήστε *configure font settings* και *handle missing fonts*—θα σας οδηγήσουν σε πιο βαθιές εξερευνήσεις της διαχείρισης γραμματοσειρών με το Aspose.Words.

---

Καλή προγραμματιστική! Έχετε κάποιο παράξενο edge case με γραμματοσειρές; Αφήστε ένα σχόλιο και θα το λύσουμε μαζί.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}