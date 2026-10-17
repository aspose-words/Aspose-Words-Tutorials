---
category: general
date: 2026-03-17
description: Πώς να εντοπίσετε γραμματοσειρές σε C# χρησιμοποιώντας το Aspose.Words
  και μια κλήση προειδοποίησης. Μάθετε πώς να χρησιμοποιείτε την κλήση προειδοποίησης
  για να καταγράψετε τις αντικαταστάσεις ελλειπούσας γραμματοσειράς κατά τη φόρτωση
  εγγράφων.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: el
og_description: Πώς να εντοπίσετε γραμματοσειρές σε C# χρησιμοποιώντας το Aspose.Words.
  Αυτός ο οδηγός δείχνει πώς να χρησιμοποιήσετε callback για να καταγράψετε προειδοποιήσεις
  για ελλιπείς γραμματοσειρές κατά τη φόρτωση ενός εγγράφου.
og_title: Πώς να ανιχνεύσετε γραμματοσειρές σε C# – Χρησιμοποιήστε Callback με το
  Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να ανιχνεύσετε γραμματοσειρές σε C# – Χρησιμοποιήστε Callback με το Aspose.Words
url: /el/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εντοπίσετε Γραμματοσειρές σε C# – Χρησιμοποιήστε Callback με το Aspose.Words

Έχετε χρειαστεί ποτέ **πώς να εντοπίσετε γραμματοσειρές** σε ένα έγγραφο Word προγραμματιστικά και αναρωτηθήκατε γιατί ορισμένοι χαρακτήρες φαίνονται περίεργοι μετά τη μετατροπή; Δεν είστε μόνοι. Σε πολλά πραγματικά έργα—γεννήτριες τιμολογίων, εξαγωγείς αναφορών ή δίαυλοι επεξεργασίας παρτίδας—η έλλειψη γραμματοσειρών προκαλεί σιωπηλά προβλήματα διάταξης που είναι δύσκολο να εντοπιστούν.

Τα καλά νέα; Το Aspose.Words σας παρέχει έναν καθαρό τρόπο να εμφανίσετε αυτά τα προβλήματα μέσω μιας callback προειδοποίησης. Σε αυτό το tutorial θα δείτε **πώς να χρησιμοποιήσετε callback** για να συλλάβετε κάθε αντικατάσταση γραμματοσειράς που εκτελεί το Aspose κατά τη φόρτωση ενός εγγράφου, και θα αποκτήσετε ένα έτοιμο παράδειγμα που εκτυπώνει μια σαφή αναφορά των ελλιπών γραμματοσειρών.

Θα καλύψουμε:

* Τα ελάχιστα προαπαιτούμενα (ένα .NET project και το πακέτο NuGet Aspose.Words).  
* Πώς να υλοποιήσετε το `IWarningCallback` για να ακούτε το `WarningType.FontSubstitution`.  
* Πώς να ενσωματώσετε το callback στα `LoadOptions` και να φορτώσετε ένα έγγραφο.  
* Πώς φαίνεται η έξοδος, μαζί με μερικές πρακτικές συμβουλές για κώδικα παραγωγής.

Στο τέλος, θα μπορείτε αυτόματα **να εντοπίζετε γραμματοσειρές** σε οποιοδήποτε αρχείο DOCX, DOC ή RTF και να ενεργείτε με βάση τις πληροφορίες ελλιπών γραμματοσειρών—είτε πρόκειται για καταγραφή, ειδοποίηση χρήστη ή αντικατάσταση με εφεδρική γραμματοσειρά.

---

![Πώς να εντοπίσετε γραμματοσειρές σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words warning callback](https://example.com/images/detect-fonts.png "πώς να εντοπίσετε γραμματοσειρές σε ένα έγγραφο Word")

## Τι Θα Χρειαστείτε

* **.NET 6.0** ή νεότερη έκδοση (το παράδειγμα μεταγλωττίζεται επίσης με .NET Framework 4.6+).  
* **Aspose.Words for .NET** – εγκαταστήστε μέσω NuGet: `Install-Package Aspose.Words`.  
* Ένα δείγμα αρχείου Word που αναφέρει σκόπιμα μια γραμματοσειρά που δεν έχετε εγκαταστήσει (π.χ., `MissingFont.docx`).  

Δεν απαιτούνται πρόσθετες βιβλιοθήκες· όλα βρίσκονται μέσα στο namespace Aspose.

---

## Πώς να Εντοπίσετε Γραμματοσειρές με Callback Προειδοποίησης

### Βήμα 1: Δημιουργήστε μια κλάση callback προειδοποίησης

Το callback υλοποιεί το `IWarningCallback`. Όταν το Aspose.Words συναντήσει μια γραμματοσειρά που δεν μπορεί να βρει, δημιουργεί ένα `WarningInfo` με `WarningType.FontSubstitution`. Η κλάση μας απλώς γράφει μια φιλική γραμμή στην κονσόλα.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Γιατί είναι σημαντικό:** Φιλτράροντας με `WarningType.FontSubstitution` αποφεύγουμε θορυβώδεις προειδοποιήσεις (όπως παρωχημένες λειτουργίες) και κρατάμε το log εστιασμένο στο ακριβές πρόβλημα που προσπαθείτε να λύσετε—**την εντόπιση γραμματοσειρών** που δεν υπάρχουν στο σύστημα.

---

### Βήμα 2: Συνδέστε το callback στα `LoadOptions`

Τα `LoadOptions` σας επιτρέπουν να προσαρμόσετε τον τρόπο ανάλυσης ενός εγγράφου. Ανάθεση του `FontWarningCollector` στην ιδιότητα `WarningCallback` λέει στο Aspose να το καλέσει όποτε εντοπιστεί μια ελλιπής γραμματοσειρά.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Συμβουλή:** Μπορείτε επίσης να ορίσετε το `LoadOptions.FontSettings` εδώ αν θέλετε να παρέχετε προγραμματιστικά μια εφεδρική γραμματοσειρά. Αυτό είναι ένα πιο προχωρημένο σενάριο που θα αναφέρουμε αργότερα.

---

### Βήμα 3: Φορτώστε το έγγραφο και παρακολουθήστε την έξοδο

Τώρα φορτώνουμε το αρχείο. Μόλις το Aspose αναλύσει το έγγραφο, κάθε γραμματοσειρά που δεν μπορεί να εντοπίσει ενεργοποιεί το callback μας.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Αναμενόμενη έξοδος στην κονσόλα** (υποθέτοντας ότι το έγγραφο αναφέρει *Comic Sans MS* που δεν είναι εγκατεστημένο):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Αν το έγγραφο περιέχει πολλαπλές ελλιπείς γραμματοσειρές, θα δείτε μία γραμμή ανά γραμματοσειρά—ακριβώς τις πληροφορίες **πώς να εντοπίσετε γραμματοσειρές** που χρειάζεστε.

---

## Πώς να Χρησιμοποιήσετε το Callback για Πιο Πολύπλοκα Σενάρια

### Καταγραφή σε αρχείο αντί για την κονσόλα

Σε παραγωγή πιθανότατα θέλετε ένα μόνιμο log. Αντικαταστήστε το `Console.WriteLine` με ένα `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Συλλογή προειδοποιήσεων για μεταγενέστερη ανάλυση

Μερικές φορές χρειάζεται η λίστα των ελλιπών γραμματοσειρών μετά τη φόρτωση του εγγράφου, ίσως για να εμφανίσετε ένα διάλογο UI. Αποθηκεύστε τις προειδοποιήσεις σε ένα `List<string>` και εκθέστε το:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Παροχή εφεδρικής γραμματοσειράς προγραμματιστικά

Αν έχετε μια εταιρική γραμματοσειρά που θέλετε να επιβάλετε, μπορείτε να την προσθέσετε στο `FontSettings` πριν τη φόρτωση:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Τώρα το Aspose αντικαθιστά τις ελλιπείς γραμματοσειρές με *Arial Unicode MS* ενώ εξακολουθεί να αναφέρει την αντικατάσταση μέσω του callback. Αυτός είναι ένας έξυπνος τρόπος να **χρησιμοποιήσετε το callback** τόσο για εντόπιση όσο και για αυτόματη διόρθωση.

---

## Συνηθισμένα Πιθανά Σφάλματα και Επαγγελματικές Συμβουλές

| Πιθανό Σφάλμα | Γιατί Συμβαίνει | Πώς να το Αποφύγετε |
|---------------|----------------|---------------------|
| **Ξεχάσατε να αναφέρετε το `Aspose.Words.Warnings`** | Η διεπαφή `IWarningCallback` βρίσκεται εκεί. | Προσθέστε `using Aspose.Words.Warnings;` στην αρχή. |
| **Φορτώνετε ένα έγγραφο χωρίς `LoadOptions`** | Ο προεπιλεγμένος φορτωτής αντικαθιστά σιωπηλά τις γραμματοσειρές χωρίς ειδοποίηση. | Πάντα δημιουργείτε μια παρουσία `LoadOptions` και αναθέτετε το callback σας. |
| **Εκτέλεση σε διακομιστή με περιορισμένα δικαιώματα** | Η εγγραφή σε αρχείο log μπορεί να προκαλέσει `UnauthorizedAccessException`. | Χρησιμοποιήστε φάκελο με δικαιώματα εγγραφής (π.χ., τον φάκελο δεδομένων της εφαρμογής) ή περιοριστείτε σε συλλογές στη μνήμη. |
| **Πολλαπλά νήματα που μοιράζονται τον ίδιο collector** | Το `FontWarningCollector` δεν είναι thread‑safe από προεπιλογή. | Δημιουργήστε ξεχωριστό collector ανά νήμα ή προστατέψτε τη λίστα με κλείδωμα. |
| **Υποθέτετε ότι το callback ενεργοποιείται για ενσωματωμένες γραμματοσειρές** | Οι ενσωματωμένες γραμματοσειρές είναι ήδη παρούσες στο έγγραφο· δεν εκβάλλεται προειδοποίηση. | Αν χρειάζεται να ελέγξετε την ακεραιότητα των ενσωματωμένων γραμματοσειρών, εξετάστε το `FontInfo` μέσω του `FontSettings`. |

---

## Πλήρες Παράδειγμα Εργασίας (Αντιγράψτε‑Κολλήστε)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Τι θα δείτε** (υποθέτοντας ότι το αρχείο αναφέρει δύο απουσιάζουσες γραμματοσειρές):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Αν το αρχείο χρησιμοποιεί μόνο εγκατεστημένες γραμματοσειρές, η κονσόλα εκτυπώνει απλώς:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Συμπεράσματα

Διασχίσαμε πώς να **εντοπίσετε γραμματοσειρές** σε ένα έγγραφο Word συνδέοντας ένα προσαρμοσμένο callback προειδοποίησης στο Aspose.Words. Η προσέγγιση είναι ελαφριά, απαιτεί

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}