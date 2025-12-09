---
language: el
url: /greek/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Ανίχνευση Ελλειπουσών Γραμματοσειρών σε Έγγραφα Aspose.Words – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί ποτέ πώς να **ανιχνεύσετε ελλειπούσες γραμματοσειρές** όταν φορτώνετε ένα αρχείο Word με το Aspose.Words; Στην καθημερινή μου εργασία, αντιμετώπισα μερικά PDF που έδειχναν παράξενες εμφανίσεις επειδή το αρχικό έγγραφο χρησιμοποιούσε μια γραμματοσειρά που δεν είχα εγκατεστημένη. Τα καλά νέα; Το Aspose.Words μπορεί να σας πει ακριβώς πότε αντικαθιστά μια γραμματοσειρά, και μπορείτε να καταγράψετε αυτή την πληροφορία με ένα απλό callback προειδοποίησης.  

Σε αυτό το σεμινάριο θα περάσουμε βήμα‑βήμα από ένα **πλήρες, εκτελέσιμο παράδειγμα** που σας δείχνει πώς να καταγράψετε κάθε αντικατάσταση γραμματοσειράς, γιατί το callback είναι σημαντικό, και μερικά επιπλέον κόλπα για αξιόπιστη ανίχνευση ελλειπουσών γραμματοσειρών. Χωρίς περιττές πληροφορίες, μόνο ο κώδικας και η λογική που χρειάζεστε για να το κάνετε λειτουργικό σήμερα.

---

## Τι Θα Μάθετε

- Πώς να υλοποιήσετε **Aspose.Words warning callback** για να εντοπίζετε συμβάντα αντικατάστασης γραμματοσειράς.  
- Πώς να διαμορφώσετε **LoadOptions C#** ώστε το callback να κληθεί κατά τη φόρτωση ενός εγγράφου.  
- Πώς να επαληθεύσετε ότι η ανίχνευση ελλειπούσας γραμματοσειράς λειτούργησε πραγματικά και πώς φαίνεται η έξοδος της κονσόλας.  

**Prerequisites** – Χρειάζεστε μια πρόσφατη έκδοση του Aspose.Words για .NET (ο κώδικας δοκιμάστηκε με την 23.12), .NET 6 ή νεότερη, και βασική γνώση της C#. Αν τα έχετε, είστε έτοιμοι να ξεκινήσετε.

## Ανίχνευση Ελλειπουσών Γραμματοσειρών με ένα Warning Callback

Η καρδιά της λύσης είναι μια υλοποίηση του `IWarningCallback`. Το Aspose.Words δημιουργεί ένα αντικείμενο `WarningInfo` για πολλές καταστάσεις, αλλά μας ενδιαφέρει μόνο το `WarningType.FontSubstitution`. Ας δούμε πώς να το συνδέσουμε.

### Βήμα 1: Δημιουργία Συλλέκτη Προειδοποιήσεων Γραμματοσειράς

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Γιατί είναι σημαντικό*: Φιλτράροντας με βάση το `WarningType.FontSubstitution` αποφεύγουμε την ακαταστασία από άσχετες προειδοποιήσεις (όπως παρωχημένες λειτουργίες). Το `info.Description` περιέχει ήδη το αρχικό όνομα της γραμματοσειράς και την εναλλακτική που χρησιμοποιήθηκε, παρέχοντάς σας ένα σαφές ίχνος ελέγχου.

## Διαμόρφωση LoadOptions για Χρήση του Callback

Τώρα λέμε στο Aspose.Words να χρησιμοποιεί τον συλλέκτη μας όταν φορτώνει ένα αρχείο.

### Βήμα 2: Ρύθμιση LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Γιατί είναι σημαντικό*: Το `LoadOptions` είναι το μοναδικό σημείο όπου μπορείτε να ενσωματώσετε το callback, κωδικούς κρυπτογράφησης και άλλες συμπεριφορές φόρτωσης. Κρατώντας το ξεχωριστά από τον κατασκευαστή `Document` κάνει τον κώδικα επαναχρησιμοποιήσιμο για πολλά αρχεία.

## Φόρτωση του Εγγράφου και Καταγραφή Ελλειπουσών Γραμματοσειρών

Με το callback συνδεδεμένο, το επόμενο βήμα είναι απλώς η φόρτωση του εγγράφου.

### Βήμα 3: Φορτώστε το DOCX σας (ή οποιαδήποτε υποστηριζόμενη μορφή)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Όταν ο κατασκευαστής `Document` αναλύει το αρχείο, οποιαδήποτε ελλειπούσα γραμματοσειρά ενεργοποιεί τον `FontWarningCollector`. Η κονσόλα θα εμφανίσει γραμμές όπως:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Αυτή η γραμμή είναι η σαφής απόδειξη ότι η **ανίχνευση ελλειπουσών γραμματοσειρών** λειτούργησε.

## Επαλήθευση της Εξόδου – Τι να Περιμένετε

Εκτελέστε το πρόγραμμα από ένα τερματικό ή το Visual Studio. Εάν το πηγαίο έγγραφο περιέχει μια γραμματοσειρά που δεν έχετε εγκατεστημένη, θα δείτε τουλάχιστον μία γραμμή «Font substituted». Εάν το έγγραφο χρησιμοποιεί μόνο εγκατεστημένες γραμματοσειρές, το callback παραμένει σιωπηλό και θα λάβετε μόνο το μήνυμα «Document loaded successfully.».

**Tip**: Για διπλό έλεγχο, ανοίξτε το αρχείο Word στο Microsoft Word και κοιτάξτε τη λίστα γραμματοσειρών. Οποιαδήποτε γραμματοσειρά εμφανίζεται στο *Replace Fonts* κάτω από την ομάδα *Home → Font* είναι υποψήφια για αντικατάσταση.

## Προχωρημένο: Ανίχνευση Ελλειπουσών Γραμματοσειρών σε Μαζική Επεξεργασία

Συχνά χρειάζεται να σαρώσετε δεκάδες αρχεία. Το ίδιο μοτίβο κλιμακώνεται άψογα:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Επειδή ο `FontWarningCollector` γράφει στην κονσόλα κάθε φορά που καλείται, θα λάβετε μια αναφορά ανά αρχείο χωρίς πρόσθετο κώδικα. Για παραγωγικά σενάρια ίσως θέλετε να καταγράφετε σε αρχείο ή βάση δεδομένων – απλώς αντικαταστήστε το `Console.WriteLine` με τον προτιμώμενο logger σας.

## Συνηθισμένα Προβλήματα & Επαγγελματικές Συμβουλές

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|------------------|----------|
| **Δεν εμφανίζονται προειδοποιήσεις** | Το έγγραφο περιέχει μόνο εγκατεστημένες γραμματοσειρές. | Επαληθεύστε ανοίγοντας το αρχείο στο Word ή αφαιρώντας σκόπιμα μια γραμματοσειρά από το σύστημα. |
| **Το callback δεν κλήθηκε** | `LoadOptions.WarningCallback` δεν είχε ποτέ ανατεθεί ή χρησιμοποιήθηκε νέα παρουσία `LoadOptions` αργότερα. | Διατηρήστε ένα μόνο αντικείμενο `LoadOptions` και επαναχρησιμοποιήστε το για κάθε φόρτωση. |
| **Πάρα πολλές άσχετες προειδοποιήσεις** | Δεν φιλτράρατε με βάση το `WarningType.FontSubstitution`. | Προσθέστε την προστασία `if (info.Type == WarningType.FontSubstitution)` όπως φαίνεται. |
| **Μείωση απόδοσης σε τεράστια αρχεία** | Το callback εκτελείται για κάθε προειδοποίηση, που μπορεί να είναι πολλές σε μεγάλα έγγραφα. | Απενεργοποιήστε άλλους τύπους προειδοποιήσεων μέσω `LoadOptions.WarningCallback` ή ορίστε το `LoadOptions.LoadFormat` σε συγκεκριμένο τύπο αν το γνωρίζετε. |

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Αναμενόμενη έξοδος κονσόλας** (όταν εντοπιστεί ελλειπούσα γραμματοσειρά):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Εάν δεν γίνει αντικατάσταση, θα δείτε μόνο τη γραμμή επιτυχίας.

## Συμπέρασμα

Τώρα έχετε έναν **πλήρη, έτοιμο για παραγωγή τρόπο ανίχνευσης ελλειπουσών γραμματοσειρών** σε οποιοδήποτε έγγραφο επεξεργάζεται το Aspose.Words. Εκμεταλλευόμενοι το **Aspose.Words warning callback** και διαμορφώνοντας το **LoadOptions C#**, μπορείτε να καταγράψετε κάθε αντικατάσταση γραμματοσειράς, να εντοπίσετε προβλήματα διάταξης και να διασφαλίσετε ότι τα PDF σας διατηρούν την προοριζόμενη εμφάνιση.  

Από ένα μόνο αρχείο έως μια τεράστια δέσμη, το μοτίβο παραμένει το ίδιο — υλοποιήστε το `IWarningCallback`, ενσωματώστε το στο `LoadOptions`, και αφήστε το Aspose.Words να κάνει το δύσκολο έργο.  

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να συνδυάσετε αυτό με **font embedding** ή **fallback font families** για να διορθώσετε αυτόματα το πρόβλημα, ή εξερευνήστε το API **DocumentVisitor** για πιο βαθιά ανάλυση του περιεχομένου. Καλό προγραμματισμό, και εύχομαι όλες οι γραμματοσειρές σας να παραμένουν εκεί που τις περιμένετε!  

---

![Ανίχνευση ελλειπουσών γραμματοσειρών σε Aspose.Words – στιγμιότυπο εξόδου κονσόλας](https://example.com/images/detect-missing-fonts.png "εξαγωγή κονσόλας ανίχνευσης ελλειπουσών γραμματοσειρών")

{{< layout-end >}}

{{< layout-end >}}