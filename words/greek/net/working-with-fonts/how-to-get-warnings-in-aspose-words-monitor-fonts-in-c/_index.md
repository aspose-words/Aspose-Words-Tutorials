---
category: general
date: 2026-01-06
description: Μάθετε πώς να λαμβάνετε προειδοποιήσεις κατά τη φόρτωση εγγράφων και
  πώς να παρακολουθείτε τις γραμματοσειρές χρησιμοποιώντας το Aspose.Words. Αυτός
  ο οδηγός καλύπτει τις κλήσεις επιστροφής προειδοποιήσεων και την παρακολούθηση αντικατάστασης
  γραμματοσειρών.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: el
og_description: Πώς να λαμβάνετε προειδοποιήσεις στο Aspose.Words; Ακολουθήστε αυτό
  το βήμα‑βήμα οδηγό για να παρακολουθείτε τις γραμματοσειρές και να καταγράφετε μηνύματα
  αντικατάστασης κατά τη φόρτωση εγγράφων.
og_title: Πώς να λαμβάνετε προειδοποιήσεις στο Aspose.Words – Παρακολούθηση γραμματοσειρών
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Πώς να λαμβάνετε προειδοποιήσεις στο Aspose.Words – Παρακολούθηση γραμματοσειρών
  σε C#
url: /el/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Λάβετε Προειδοποιήσεις στο Aspose.Words – Παρακολούθηση Γραμματοσειρών σε C#

Έχετε αναρωτηθεί ποτέ **πώς να λάβετε προειδοποιήσεις** όταν ένα έγγραφο Word περιέχει γραμματοσειρές που δεν έχετε εγκαταστήσει; Είναι ένα συνηθισμένο πρόβλημα—η εφαρμογή σας αντικαθιστά σιωπηλά τις ελλείπουσες γραμματοσειρές και δεν ξέρετε ποτέ τι άλλαξε. Τα καλά νέα είναι ότι μπορείτε να συνδεθείτε στο σύστημα προειδοποιήσεων του Aspose.Words και να **παρακολουθείτε τις γραμματοσειρές** σε πραγματικό χρόνο.

> **Συμβουλή:** Αν δημιουργείτε μια αλυσίδα μετατροπής εγγράφων, η καταγραφή των ελλείπουσων γραμματοσειρών νωρίς σας εξοικονομεί από δυσάρεστες εκπλήξεις διάταξης στο μέλλον.

## Τι Θα Χρειαστεί

- **Aspose.Words for .NET** (τελευταία έκδοση· το API δεν έχει αλλάξει από την v23.10)
- Ένα περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή VS Code με την επέκταση C#)
- Ένα δείγμα `.docx` που αναφέρει μια γραμματοσειρά που δεν έχετε εγκαταστήσει (π.χ., **“NonExistentFont”**)

Αυτό είναι όλο—χωρίς επιπλέον πακέτα NuGet εκτός από το Aspose.Words.

## Βήμα 1 – Ρύθμιση Συλλέκτη Προειδοποιήσεων (Primary Keyword in Header)

Το πρώτο πράγμα που χρειάζεστε είναι ένας χώρος για αποθήκευση των προειδοποιήσεων καθώς συμβαίνουν. Το Aspose.Words παρέχει την ιδιότητα `WarningCallback` στο `LoadOptions` ακριβώς για αυτόν τον σκοπό.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Γιατί είναι σημαντικό:**  
Όταν η βιβλιοθήκη συναντήσει μια ελλείπουσα γραμματοσειρά, δεν πετάει εξαίρεση· εκδίδει ένα αντικείμενο `WarningInfo`. Συνδέοντας έναν συλλέκτη, αποκτάτε πλήρη ορατότητα σε κάθε συμβάν αντικατάστασης, επιτρέποντάς σας να **παρακολουθείτε τις γραμματοσειρές** χωρίς να μολύνει την κονσόλα σας με άσχετα μηνύματα.

## Βήμα 2 – Φόρτωση του Εγγράφου με τις Επιλογές Ενεργοποιημένων Προειδοποιήσεων

Τώρα διαβάζουμε πραγματικά το αρχείο. Τα `LoadOptions` που προετοιμάσαμε στο προηγούμενο βήμα εξασφαλίζουν ότι τυχόν προειδοποιήσεις σχετικές με γραμματοσειρές καταγράφονται.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Τι συμβαίνει στο παρασκήνιο;**  
Το Aspose.Words αναλύει το αρχείο Word, επιλύει τις γραμματοσειρές και όποτε δεν μπορεί να βρει τη ζητούμενη γραμματοσειρά, επαναπροσαρμόζεται σε μια υποκατάστατη (συνήθως Arial). Η υποκατάσταση ενεργοποιεί μια προειδοποίηση `WarningType.FontSubstitution`, η οποία καταλήγει στο `warningCollector`.

## Βήμα 3 – Επιθεώρηση των Συλλεγμένων Προειδοποιήσεων (Primary Keyword Appears Again)

Αφού φορτωθεί το έγγραφο, απλώς διατρέχουμε το `warningCollector` και εκτυπώνουμε τυχόν μηνύματα αντικατάστασης γραμματοσειρών.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Αναμενόμενη έξοδος** (υποθέτοντας ότι η ελλείπουσα γραμματοσειρά είναι *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Αν το έγγραφο περιέχει πολλαπλές άγνωστες γραμματοσειρές, θα δείτε μία γραμμή ανά αντικατάσταση—ιδανικό για καταγραφή ή ειδοποίηση.

## Βήμα 4 – Προαιρετικό: Καταγραφή ή Αποθήκευση των Πληροφοριών Προειδοποίησης

Σε παραγωγή πιθανότατα θέλετε κάτι παραπάνω από ένα `Console.WriteLine`. Εδώ είναι ένα γρήγορο παράδειγμα που γράφει τις προειδοποιήσεις σε αρχείο JSON για μεταγενέστερη ανάλυση.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Τώρα έχετε ένα μόνιμο αρχείο που μπορείτε να τροφοδοτήσετε σε πίνακα παρακολούθησης, ή ακόμη και να ενεργοποιήσετε αυτόματο αίτημα για τα αρχεία των ελλείπουσων γραμματοσειρών.

## Βήμα 5 – Επαλήθευση του Αποτελέσματος και Καθαρισμός

Εκτελέστε το πρόγραμμα. Αν δείτε τα μηνύματα αντικατάστασης, έχετε επιτυχώς **λάβει προειδοποιήσεις** και τώρα ενεργά **παρακολουθείτε τις γραμματοσειρές**. Αν δεν εμφανιστεί τίποτα, ελέγξτε ξανά ότι το δοκιμαστικό έγγραφο πράγματι αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημα.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Ένας αριθμός μηδέν συνήθως σημαίνει είτε:

1. Όλες οι γραμματοσειρές επιλύθηκαν (ίσως η γραμματοσειρά *είναι* εγκατεστημένη τοπικά), ή
2. Το έγγραφο δεν περιείχε αναφορές γραμματοσειρών που χρειάζονταν αντικατάσταση.

## Συνηθισμένα Παγίδες & Πώς να τις Αποφύγετε

| Παγίδα | Γιατί Συμβαίνει | Διόρθωση |
|---------|----------------|-----|
| **Δεν εμφανίζονται προειδοποιήσεις** | Η γραμματοσειρά υπάρχει στην πραγματικότητα στο σύστημα, ή το έγγραφο χρησιμοποιεί μόνο ενσωματωμένες γραμματοσειρές. | Μετονομάστε τη γραμματοσειρά στο αρχείο προέλευσης σε κάτι αδύνατο (π.χ., `XYZ123`) και δοκιμάστε ξανά. |
| **Πάρα πολλές προειδοποιήσεις (θόρυβος)** | Φορτώνετε πολλά έγγραφα σε βρόχο χωρίς να καθαρίζετε τον συλλέκτη. | Δημιουργήστε ξανά το `WarningInfoCollection` για κάθε έγγραφο, ή καλέστε `warningCollector.Clear()` μετά την επεξεργασία. |
| **Επίπτωση στην απόδοση** | Η υπερβολική καταγραφή στο δίσκο μπορεί να επιβραδύνει την επεξεργασία παρτίδας. | Αποθηκεύστε τις προειδοποιήσεις στη μνήμη και γράψτε τες μαζικά, ή χρησιμοποιήστε ασύγχρονη I/O αρχείων. |
| **Λείπει `using Aspose.Words.Loading;`** | Η κλάση `LoadOptions` βρίσκεται σε αυτό το namespace. | Προσθέστε τη λείπουσα οδηγία `using`, όπως φαίνεται στο Βήμα 1. |

## Επέκταση της Λύσης – Παρακολούθηση Άλλων Τύπων Προειδοποιήσεων

Αν και η αντικατάσταση γραμματοσειρών είναι η πιο εμφανής, το Aspose.Words μπορεί να εκδώσει προειδοποιήσεις για:

- **Παρωχημένα χαρακτηριστικά** (`WarningType.Deprecated`),
- **Πιθανή απώλεια δεδομένων** (`WarningType.DataLoss`),
- **Μη υποστηριζόμενες μορφές αρχείων** (`WarningType.UnsupportedFileFormat`).

Μπορείτε να διευρύνετε το φίλτρο στο Βήμα 3 για να συλλάβετε και αυτά:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Με αυτόν τον τρόπο δεν πρόκειται μόνο για **πώς να παρακολουθείτε τις γραμματοσειρές**, αλλά και για **πώς να λαμβάνετε προειδοποιήσεις** για οποιοδήποτε σενάριο μπορεί να αντιμετωπίσει η εφαρμογή σας.

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Τρέξτε το:** Κατασκευάστε το έργο, εκτελέστε το, και θα δείτε τις προειδοποιήσεις να εκτυπώνονται και να αποθηκεύονται. Αυτή είναι η πλήρης απάντηση στο **πώς να λαμβάνετε προειδοποιήσεις** και **πώς να παρακολουθείτε τις γραμματοσειρές** με το Aspose.Words.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να λαμβάνετε προειδοποιήσεις** από το Aspose.Words, συγκεκριμένα για σενάρια αντικατάστασης γραμματοσειρών, και έχετε μάθει **πώς να παρακολουθείτε τις γραμματοσειρές** κατά τη διαδικασία φόρτωσης εγγράφων. Συνδέοντας ένα `WarningCallback`, διατρέχοντας τα συλλεγμένα αντικείμενα `WarningInfo` και προαιρετικά αποθηκεύοντας τα δεδομένα, αποκτάτε πλήρη διαφάνεια στα γεγονότα ελλείπουσων γραμματοσειρών—μια απαραίτητη δυνατότητα για οποιοδήποτε pipeline επεξεργασίας εγγράφων.

Επόμενα βήματα; Δοκιμάστε να επεκτείνετε το φίλτρο προειδοποιήσεων για να καλύψετε προειδοποιήσεις απώλειας δεδομένων ή παρωχημένων χαρακτηριστικών, ή ενσωματώστε το JSON log σε πίνακα παρακολούθησης όπως το Grafana. Το ίδιο μοτίβο λειτουργεί για όλους τους τύπους προειδοποιήσεων, έτσι θα είστε καλά εξοπλισμένοι για να παρακολουθείτε οποιοδήποτε πρόβλημα εκδίδει το Aspose.Words.

Καλό κώδικα, και εύχομαι τα έγγραφά σας πάντα να αποδίδουν ακριβώς όπως το περιμένετε! 

<img src="font-warnings.png" alt="πώς να λαμβάνετε προειδοποιήσεις στο Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}