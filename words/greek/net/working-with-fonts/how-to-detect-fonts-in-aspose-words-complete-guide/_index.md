---
category: general
date: 2026-04-07
description: Μάθετε πώς να εντοπίζετε γραμματοσειρές και πώς να καταγράφετε προειδοποιήσεις
  κατά τη διαχείριση ελλιπών γραμματοσειρών σε C# χρησιμοποιώντας το Aspose.Words.
  Συμπεριλαμβάνεται κώδικας βήμα‑βήμα.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: el
og_description: Πώς να εντοπίσετε τις γραμματοσειρές στο Aspose.Words; Ακολουθήστε
  αυτό το σεμινάριο για να καταγράψετε προειδοποιήσεις και να διαχειριστείτε τις ελλιπείς
  γραμματοσειρές με ευκολία.
og_title: Πώς να ανιχνεύσετε γραμματοσειρές στο Aspose.Words – Πλήρης οδηγός
tags:
- Aspose.Words
- C#
- Font handling
title: Πώς να ανιχνεύσετε γραμματοσειρές στο Aspose.Words – Πλήρης οδηγός
url: /el/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ανιχνεύσετε γραμματοσειρές στο Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να ανιχνεύσετε γραμματοσειρές** που λείπουν από ένα έγγραφο Word πριν το στείλετε στην παραγωγή; Δεν είστε μόνοι. Σε πολλές επιχειρησιακές περιπτώσεις, μια αχρείαστη γραμματοσειρά μπορεί να διακόψει τη διαδικασία μετατροπής PDF ή να προκαλέσει σφάλματα διάταξης που φαίνονται μη επαγγελματικά. Τα καλά νέα είναι ότι το Aspose.Words σας παρέχει έναν ενσωματωμένο τρόπο να εντοπίζετε αυτές τις απουσιάζουσες γραμματοσειρές και να εμφανίζει σαφείς προειδοποιήσεις.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα από το **πώς να ανιχνεύσετε γραμματοσειρές**, **πώς να καταγράψετε προειδοποιήσεις**, και τις βέλτιστες πρακτικές για **τη διαχείριση ελλιπών γραμματοσειρών** ώστε η εφαρμογή σας να παραμένει ανθεκτική. Χωρίς εξωτερικά εργαλεία, χωρίς εικασίες—απλός κώδικας C# που μπορείτε να ενσωματώσετε στο έργο σας αμέσως.

> **Γρήγορη προεπισκόπηση:** Στο τέλος θα έχετε έναν επαναχρησιμοποιήσιμο `FontSubstitutionWarningCollector` που συλλέγει κάθε μήνυμα αντικατάστασης γραμματοσειράς κατά τη φόρτωση του εγγράφου, και θα ξέρετε πώς να αντιδράτε όταν μια γραμματοσειρά δεν μπορεί να βρεθεί.

---

## Τι θα μάθετε

- Πώς να διαμορφώσετε το `LoadOptions` ώστε να ακούει προειδοποιήσεις αντικατάστασης γραμματοσειρών.  
- Πώς να καταγράψετε αυτές τις προειδοποιήσεις σε μια προσαρμοσμένη κλάση συλλογής.  
- Πώς να επεξεργαστείτε τις συλλεγμένες προειδοποιήσεις και να αποφασίσετε αν θα ακυρώσετε, καταγράψετε ή αντικαταστήσετε τις γραμματοσειρές.  
- Διαχείριση edge‑case για έγγραφα που αναφέρονται σε απομακρυσμένες ή ενσωματωμένες γραμματοσειρές.  

**Προαπαιτούμενα:** .NET 6+ (ή .NET Framework 4.6+), Aspose.Words for .NET (τελευταία έκδοση), και βασική εξοικείωση με C#. Αν δεν έχετε χρησιμοποιήσει ποτέ το Aspose.Words, μην ανησυχείτε—αυτός ο οδηγός υποθέτει μόνο λίγα λεπτά εγκατάστασης.

## Πώς να ανιχνεύσετε γραμματοσειρές χρησιμοποιώντας Aspose.Words LoadOptions

Το πρώτο βήμα για την ανίχνευση ελλιπών γραμματοσειρών είναι να πείτε στο Aspose.Words να τις αναφέρει. Αυτό γίνεται μέσω της ιδιότητας `LoadOptions.WarningCallback`, η οποία δέχεται οποιαδήποτε κλάση που υλοποιεί το `IWarningCallback`. Παρακάτω δημιουργούμε έναν μικρό συλλέκτη που αποθηκεύει κάθε προειδοποίηση για μετέπειτα έλεγχο.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Γιατί είναι σημαντικό:** Χωρίς callback προειδοποίησης, το Aspose.Words αντικαθιστά σιωπηλά τις ελλιπείς γραμματοσειρές με μια προεπιλεγμένη, και δεν γνωρίζετε ποτέ ότι υπάρχει πρόβλημα. Καταγράφοντας το `WarningType.FontSubstitution` αποκτάτε πλήρη διαφάνεια—ακριβώς τα δεδομένα που χρειάζεστε για να **ανιχνεύσετε γραμματοσειρές** που δεν είναι διαθέσιμες στο σύστημα.

Τώρα ενσωματώνουμε τον συλλέκτη στο `LoadOptions` και φορτώνουμε ένα έγγραφο:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Συμβουλή:** Αν εργάζεστε με πολλά έγγραφα σε παρτίδα, επαναχρησιμοποιήστε την ίδια παρουσία `FontSubstitutionWarningCollector`, αλλά θυμηθείτε να καλέσετε `Clear()` μεταξύ των φορτώσεων για να αποφύγετε το μίξιμο προειδοποιήσεων από διαφορετικά αρχεία.

## Καταγραφή προειδοποιήσεων κατά τη φόρτωση του εγγράφου

Μετά τη φόρτωση του εγγράφου, ο συλλέκτης ήδη κρατά κάθε προειδοποίηση σχετική με γραμματοσειρές. Η επόμενη λογική ερώτηση είναι: *Πώς να καταγράψω τις προειδοποιήσεις* με τρόπο που να είναι εύκολο να τις καταγράψετε ή να τις εμφανίσετε;

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Η τυπική έξοδος μοιάζει με:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Τι σας λέει αυτό:** Κάθε γραμμή αποκαλύπτει το αρχικό όνομα γραμματοσειράς και την εναλλακτική που επέλεξε το Aspose.Words. Εξοπλισμένοι με αυτές τις πληροφορίες, μπορείτε να αποφασίσετε αν η εναλλακτική είναι αποδεκτή ή αν χρειάζεται να ενσωματώσετε τη λείπουσα γραμματοσειρά χειροκίνητα.

## Διαχείριση ελλιπών γραμματοσειρών με χάρη

Η ανίχνευση και η καταγραφή προειδοποιήσεων είναι μόνο το ήμισυ του αγώνα. Η πραγματική αξία έρχεται όταν **διαχειρίζεστε ελλιπείς γραμματοσειρές** με τρόπο έτοιμο για παραγωγή. Παρακάτω τρεις κοινές στρατηγικές:

1. **Καταγραφή και συνέχιση** – Κατάλληλο για επεξεργασία παρτίδας όπου χρειάζεστε μόνο ένα αποτύπωμα ελέγχου.  
2. **Ακύρωση σε κρίσιμες γραμματοσειρές** – Ρίξτε εξαίρεση εάν λείπει μια συγκεκριμένη γραμματοσειρά (π.χ., μια γραμματοσειρά ειδική για το brand).  
3. **Ενσωμάτωση της γραμματοσειράς εν κινήσει** – Φορτώστε τη λείπουσα γραμματοσειρά από έναν γνωστό φάκελο και καταχωρίστε την στο Aspose.Words πριν ξαναφορτώσετε το έγγραφο.

### Παράδειγμα: Ακύρωση σε κρίσιμη γραμματοσειρά

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Παράδειγμα: Αυτόματη ενσωμάτωση ελλιπών γραμματοσειρών

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Γιατί αυτά τα μοτίβα βοηθούν:** Αποφασίζοντας ρητά τι να κάνετε όταν λείπει μια γραμματοσειρά, εξαλείφετε τις σιωπηλές εναλλακτικές που θα μπορούσαν να επηρεάσουν το branding ή την αναγνωσιμότητα. Αυτό είναι η ουσία της **διαχείρισης ελλιπών γραμματοσειρών** με ελεγχόμενο τρόπο.

## Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας όλα, εδώ είναι ένα ενιαίο, έτοιμο‑για‑εκτέλεση πρόγραμμα που δείχνει **πώς να ανιχνεύσετε γραμματοσειρές**, **πώς να καταγράψετε προειδοποιήσεις**, και μια απλή πολιτική για **τη διαχείριση ελλιπών γραμματοσειρών** μέσω καταγραφής.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Όταν εκτελείτε το πρόγραμμα εναντίον ενός εγγράφου που αναφέρει μια γραμματοσειρά που δεν υπάρχει στο σύστημα, η κονσόλα θα εμφανίσει κάθε προειδοποίηση αντικατάστασης. Εάν κάποια προειδοποίηση αφορά μια γραμματοσειρά από το σύνολο `critical`, το πρόγραμμα τερματίζει νωρίς, αποτρέποντας τη δημιουργία ελαττωματικού PDF.

## Συχνές Ερωτήσεις (FAQs)

| Ερώτηση | Απάντηση |
|----------|--------|
| *Χρειάζομαι άδεια για το Aspose.Words για να χρησιμοποιήσω αυτόν τον κώδικα;* | Ναι, μια έγκυρη άδεια Aspose.Words αφαιρεί τα υδατογράμματα αξιολόγησης και ξεκλειδώνει τη πλήρη λειτουργικότητα. |
| *Μπορεί αυτή η προσέγγιση να εντοπίσει ενσωματωμένες γραμματοσειρές;* | Οι ενσωματωμένες γραμματοσειρές είναι ήδη μέρος του αρχείου, έτσι το Aspose.Words δεν θα εμφανίσει προειδοποίηση αντικατάστασης. Μπορείτε να ελέγξετε το `Document.FontInfos` για να απαριθμήσετε τις ενσωματωμένες γραμματοσειρές εάν χρειάζεται. |
| *Τι γίνεται αν η λείπουσα γραμματοσειρά είναι συστημική στο Windows αλλά όχι στο Linux;* | Η ίδια προειδοποίηση θα ενεργοποιηθεί στο Linux επειδή η γραμματοσειρά δεν είναι εγκατεστημένη εκεί. Χρησιμοποιήστε τη στρατηγική “διαχείριση ελλιπών γραμματοσειρών” για να στείλετε τα απαιτούμενα αρχεία `.ttf` με την εφαρμογή σας. |
| *Is the warning collector thread

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}