---
category: general
date: 2026-03-19
description: Μάθετε πώς να καταγράφετε προειδοποιήσεις στο Aspose.Words, να ορίζετε
  προεπιλεγμένες ρυθμίσεις γραμματοσειράς και να εντοπίζετε ελλιπείς γραμματοσειρές
  κατά τη φόρτωση ενός εγγράφου Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: el
og_description: Πώς να καταγράψετε προειδοποιήσεις στο Aspose.Words, να ορίσετε προεπιλεγμένες
  ρυθμίσεις γραμματοσειράς και να εντοπίσετε ελλιπείς γραμματοσειρές κατά τη φόρτωση
  ενός εγγράφου Word.
og_title: Πώς να καταγράψετε προειδοποιήσεις – Ορίστε τις προεπιλεγμένες ρυθμίσεις
  γραμματοσειράς
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να καταγράψετε προειδοποιήσεις – Ορίστε τις προεπιλεγμένες ρυθμίσεις γραμματοσειράς
url: /el/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Καταγράψετε Προειδοποιήσεις – Ορισμός Προεπιλεγμένων Ρυθμίσεων Γραμματοσειράς

**Πώς να καταγράψετε προειδοποιήσεις** είναι μια συχνή ανάγκη όταν εργάζεστε με Aspose.Words, ειδικά αν τα έγγραφά σας εξαρτώνται από συγκεκριμένες γραμματοσειρές που μπορεί να μην είναι διαθέσιμες στο μηχάνημα-στόχο. Έχετε ανοίξει ποτέ ένα DOCX και αναρωτηθεί γιατί η διάταξη φαίνεται λανθασμένη; Η απάντηση συχνά κρύβεται σε μια προειδοποίηση για ελλιπή γραμματοσειρά.  

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από το **πώς να καταγράψετε προειδοποιήσεις** ενώ **φορτώνετε έγγραφο Word**, θα διαμορφώσουμε **ορισμό προεπιλεγμένων ρυθμίσεων γραμματοσειράς**, και τελικά θα **ανιχνεύσουμε ελλιπείς γραμματοσειρές** ώστε να αντιδράσετε προγραμματιστικά. Χωρίς περιττές πληροφορίες—μόνο ένα πλήρες, εκτελέσιμο παράδειγμα και η λογική πίσω από κάθε γραμμή.

> *Συμβουλή:* Η καταγραφή προειδοποιήσεων νωρίς σας σώζει από το να εντοπίζετε μυστηριώδεις προβλήματα διάταξης αργότερα.

---

## Τι Θα Χρειαστεί

- **Aspose.Words for .NET** (τελευταία έκδοση έως το 2026).  
- Περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή VS Code).  
- Ένα δείγμα DOCX που αναφέρει μια γραμματοσειρά που *δεν* έχετε εγκαταστήσει (π.χ., *Comic Sans MS* σε Linux).  

Αυτό είναι όλο. Δεν απαιτούνται πρόσθετα πακέτα NuGet εκτός από το Aspose.Words.

---

## Βήμα 1 – Κατανόηση του Γιατί Χρειάζεστε την Καταγραφή Προειδοποιήσεων

Όταν το Aspose.Words αναλύει ένα έγγραφο, μπορεί να συναντήσει γραμματοσειρές που δεν είναι διαθέσιμες στο σύστημα. Από προεπιλογή η βιβλιοθήκη αντικαθιστά σιωπηλά με μια εφεδρική γραμματοσειρά, κάτι που μπορεί να αλλάξει τις αλλαγές γραμμής, το διάστημα και ακόμη να κάνει κείμενο να εξαφανιστεί.  

Η χρήση του **WarningCallback** μαζί με ένα αντικείμενο **FontSettings** σας προσφέρει δύο πράγματα:

1. **Ορατότητα** – λαμβάνετε μια καταχώρηση `WarningInfo` για κάθε αντικατάσταση.  
2. **Έλεγχος** – μπορείτε να προ‑ρυθμίσετε μια προεπιλεγμένη γραμματοσειρά ώστε να μειώσετε τις οπτικές εκπλήξεις.

Σκεφτείτε το σαν την εγκατάσταση ενός “watchdog” που φωνάζει κάθε φορά που η μηχανή αλλάζει ένα εξάρτημα κάτω από το καπό.

---

## Βήμα 2 – Ορισμός Προεπιλεγμένων Ρυθμίσεων Γραμματοσειράς

Η πρώτη δευτερεύουσα λέξη‑κλειδί, **set default font settings**, εμφανίζεται ακριβώς εδώ. Δημιουργείτε μια παρουσία `FontSettings` και προαιρετικά την κατευθύνετε σε έναν φάκελο που περιέχει τις εφεδρικές γραμματοσειρές σας.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Γιατί;**  
> Εάν δεν ορίσετε εφεδρική γραμματοσειρά, το Aspose.Words επιλέγει την πρώτη συστημική γραμματοσειρά που ταιριάζει στο στυλ, η οποία μπορεί να είναι εντελώς διαφορετική. Ορίζοντας μια γνωστή προεπιλογή, εξασφαλίζετε συνεπή απόδοση σε όλα τα μηχανήματα.

---

## Βήμα 3 – Προετοιμασία Warning Callback για Καταγραφή Προειδοποιήσεων

Τώρα θα **πώς να καταγράψετε προειδοποιήσεις** προσθέτοντας ένα `WarningInfoCollection` στις επιλογές φόρτωσης. Αυτή η συλλογή θα αποθηκεύει κάθε προειδοποίηση που εκδίδεται κατά τη διαδικασία φόρτωσης.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

Το `WarningInfoCollection` υλοποιεί το `IWarningCallback`, έτσι το Aspose.Words σπρώχνει αυτόματα κάθε προειδοποίηση στο `warningInfos`. Δεν απαιτείται polling.

---

## Βήμα 4 – Φόρτωση Εγγράφου Word με τις Διαμορφωμένες Επιλογές

Εδώ η δεύτερη δευτερεύουσα λέξη‑κλειδί, **load word document**, παίρνει τη θέση της. Περνάμε τόσο το `FontSettings` όσο και το `WarningCallback` μέσω μιας παρουσίας `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Αν το έγγραφο αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, το callback προειδοποίησης θα καταγράψει μια καταχώρηση `WarningType.FontSubstitution`.

---

## Βήμα 5 – Ανίχνευση Ελλιπών Γραμματοσειρών από τις Συλλεγμένες Προειδοποιήσεις

Τέλος, απαντάμε στην τρίτη δευτερεύουσα λέξη‑κλειδί, **detect missing fonts**, διατρέχοντας τις συλλεγμένες προειδοποιήσεις.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Τυπική έξοδος μοιάζει με:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Αυτή η γραμμή σας λέει ακριβώς ποια γραμματοσειρά λείπει και ποια εφεδρική χρησιμοποιήθηκε—πληροφορίες που μπορείτε να καταγράψετε, να εμφανίσετε στον χρήστη ή ακόμη και να ενεργοποιήσετε μια προσαρμοσμένη διαδικασία εγκατάστασης γραμματοσειράς.

---

## Πλήρες Εκτελέσιμο Παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή κονσόλας. Δείχνει **πώς να καταγράψετε προειδοποιήσεις**, **να ορίσετε προεπιλεγμένες ρυθμίσεις γραμματοσειράς**, **να φορτώσετε έγγραφο Word**, και **να ανιχνεύσετε ελλιπείς γραμματοσειρές** όλα σε μία ροή.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Όταν το συγκεκριμένο DOCX αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, η κονσόλα εκτυπώνει μια προειδοποίηση για κάθε αντικατάσταση. Αν όλες οι γραμματοσειρές είναι παρούσες, η βρόχος δεν παράγει έξοδο.

---

## Συνηθισμένα Πιθανά Προβλήματα & Ακραίες Περιπτώσεις

| Κατάσταση | Γιατί συμβαίνει | Πώς να το αντιμετωπίσετε |
|-----------|----------------|--------------------------|
| **Δεν εμφανίζονται προειδοποιήσεις** παρόλο που η διάταξη φαίνεται λανθασμένη | Το έγγραφο μπορεί να χρησιμοποιεί *ενσωματωμένες* γραμματοσειρές, τις οποίες το Aspose.Words αποδίδει χωρίς αντικατάσταση. | Ελέγξτε το `Document.HasEmbeddedFonts` και σκεφτείτε την εξαγωγή των ενσωματωμένων γραμματοσειρών εάν τις χρειάζεστε σε άλλο μηχάνημα. |
| **Multiple warnings for the

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}