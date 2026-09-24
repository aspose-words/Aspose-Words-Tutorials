---
category: general
date: 2026-01-11
description: Ενεργοποιήστε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών για να
  εντοπίζετε τις ελλείπουσες γραμματοσειρές στα .NET έγγραφά σας. Μάθετε πώς να λαμβάνετε
  το όνομα της ελλείπουσας γραμματοσειράς και να παραθέτετε τις ελλείπουσες γραμματοσειρές
  με το Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: el
og_description: Ενεργοποιήστε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών στο
  Aspose.Words για να εντοπίζετε ελλείπουσες γραμματοσειρές, να λαμβάνετε το όνομα
  της ελλείπουσας γραμματοσειράς και να καταγράφετε τις ελλείπουσες γραμματοσειρές
  στα έγγραφά σας.
og_title: Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών – Βήμα‑βήμα Μαθήματα
  C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών στο Aspose.Words
  – Πλήρης Οδηγός
url: /el/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ενεργοποίηση Προειδοποιήσεων Υποκατάστασης Γραμματοσειρών – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ γιατί ένα έγγραφο Word φαίνεται ελαφρώς διαφορετικό μετά τη φόρτωσή του σε έναν διακομιστή; Οι πιθανότητες είναι ότι μια γραμματοσειρά που χρησιμοποίησε ο αρχικός δημιουργός δεν είναι διαθέσιμη στο μηχάνημά σας, και το Aspose.Words την αντικατέστησε σιωπηλά με την πιο κοντινή. **Ενεργοποιήστε τις προειδοποιήσεις υποκατάστασης γραμματοσειρών** και θα μάθετε αμέσως ποιες γραμματοσειρές λείπουν, με τι αντικαταστάθηκαν, και πώς να δράσετε με βάση αυτές τις πληροφορίες.

Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό, ολοκληρωμένο παράδειγμα που δείχνει πώς να **ανιχνεύσετε τις ελλιπείς γραμματοσειρές**, να ανακτήσετε το **get missing font name**, και ακόμη να **καταγράψετε τις ελλιπείς γραμματοσειρές** για αναφορά. Χωρίς περιττά, μόνο μια σαφής λύση που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET σήμερα.

---

## Τι Θα Μάθετε

- Πώς να διαμορφώσετε το `LoadOptions` ώστε το Aspose.Words να εκδίδει λεπτομερείς προειδοποιήσεις.
- Ο ακριβής κώδικας που απαιτείται για τη φόρτωση ενός εγγράφου και την απαρίθμηση των προειδοποιήσεων σχετικών με τις γραμματοσειρές.
- Τρόποι εξαγωγής του ονόματος της ελλιπούς γραμματοσειράς και της αντικατάστασής της, και στη συνέχεια η δημιουργία μιας καθαρής αναφοράς.
- Συμβουλές για τη διαχείριση ειδικών περιπτώσεων, όπως έγγραφα με δεκάδες ελλιπείς γραμματοσειρές ή προσαρμοσμένους φακέλους γραμματοσειρών.

### Προαπαιτούμενα

- .NET 6+ (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 ή νεότερο (μπορείτε να το αποκτήσετε από το NuGet)
- Ένα δείγμα DOCX που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (θα το ονομάσουμε `MissingFont.docx`)

Αν έχετε αυτά τα βασικά, ας βουτήξουμε.

---

## Βήμα 1: Ρύθμιση LoadOptions για Ενεργοποίηση Προειδοποιήσεων Υποκατάστασης Γραμματοσειρών  

Το πρώτο πράγμα που πρέπει να κάνετε είναι να ενημερώσετε το Aspose.Words ότι σας ενδιαφέρουν οι ελλιπείς γραμματοσειρές. Από προεπιλογή η βιβλιοθήκη καταγράφει τις προειδοποιήσεις μόνο εσωτερικά. Ορίζοντας το `SubstitutionWarningLevel` σε `Typical` (ή `All` για την πιο αναλυτική έξοδο) ενεργοποιείται η λειτουργία.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Γιατί είναι σημαντικό:**  
Όταν ο `SubstitutionWarningLevel` είναι ορισμένος, κάθε φορά που το Aspose.Words δεν μπορεί να βρει μια αναφερόμενη γραμματοσειρά προσθέτει ένα `FontSubstitutionWarning` στη συλλογή `Warnings` του εγγράφου. Αυτή η συλλογή είναι ο μοναδικός αξιόπιστος τρόπος για **να ανιχνεύσετε ελλιπείς γραμματοσειρές** χωρίς να χρειάζεται να αναλύσετε το έγγραφο χειροκίνητα.

> **Pro tip:** Αν διαχειρίζεστε μια παρτίδα εγγράφων και θέλετε να είστε απολύτως σίγουροι ότι θα πιάσετε κάθε υποκατάσταση, χρησιμοποιήστε `FontSubstitutionWarningLevel.All`. Είναι λίγο πιο θορυβώδης, αλλά εγγυάται ότι καμία προειδοποίηση δεν θα περάσει απαρατήρητη.

## Βήμα 2: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές  

Τώρα που το σύστημα προειδοποιήσεων είναι έτοιμο, φορτώστε το DOCX σας με το `LoadOptions` που μόλις προετοιμάσαμε. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική· απλώς βεβαιωθείτε ότι το αρχείο υπάρχει.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Τι συμβαίνει στο παρασκήνιο;**  
Το Aspose.Words αναλύει το XML του εγγράφου, επιλύει κάθε στοιχείο `<w:font>` και ελέγχει τον κατάλογο γραμματοσειρών του συστήματος (συμπεριλαμβανομένων τυχόν προσαρμοσμένων φακέλων που έχετε προσθέσει στο `FontSettings`). Όταν δεν μπορεί να εντοπίσει μια γραμματοσειρά, καταγράφει μια προειδοποίηση — ακριβώς αυτό που χρειαζόμαστε για να **καταγράψουμε τις ελλιπείς γραμματοσειρές** αργότερα.

## Βήμα 3: Επανάληψη στις Προειδοποιήσεις και Εξαγωγή Λεπτομερειών Ελλιπούς Γραμματοσειράς  

Με το έγγραφο στη μνήμη, η συλλογή `Warnings` περιέχει κάθε `FontSubstitutionWarning`. Θα το διασχίσουμε, θα φιλτράρουμε τον σωστό τύπο και θα εκτυπώσουμε μια φιλική αναφορά.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Αναμενόμενη έξοδος** (υποθέτοντας ότι το πηγαίο έγγραφο αναφέρει το `MyCustomFont` που δεν είναι εγκατεστημένο):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Παρατηρήστε πώς κάθε καταχώρηση σας δίνει τόσο το **get missing font name** (`MyCustomFont`) όσο και την εναλλακτική (`Arial`). Αυτές είναι ακριβώς οι πληροφορίες που χρειάζεστε για να αποφασίσετε αν θα ενσωματώσετε την αρχική γραμματοσειρά, θα ζητήσετε από τον δημιουργό μια αντικατάσταση, ή απλώς θα αποδεχτείτε την υποκατάσταση.

## Βήμα 4: Προαιρετικά – Συλλογή των Δεδομένων σε Λίστα για Περαιτέρω Επεξεργασία  

Αν χρειάζεται να εξάγετε την αναφορά σε CSV, να τη στείλετε μέσω API, ή απλώς να τη διατηρήσετε στη μνήμη για αργότερα, μπορείτε να αποθηκεύσετε τις προειδοποιήσεις σε μια ισχυρά τυποποιημένη λίστα.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Τώρα έχετε **list missing fonts** σε μορφή που μπορεί να καταναλώσει οποιοδήποτε downstream σύστημα. Είτε τροφοδοτείτε ένα dashboard είτε δημιουργείτε αρχείο ελέγχου, τα δεδομένα είναι έτοιμα.

## Βήμα 5: Διαχείριση Ειδικών Περιπτώσεων και Συνηθισμένων Παγίδων  

### Πολλαπλές Ελλιπείς Γραμματοσειρές σε Μία Εκτέλεση  

Τα μεγάλα εταιρικά πρότυπα συχνά αναφέρουν δεκάδες προσαρμοσμένες γραμματοσειρές. Η συλλογή προειδοποιήσεων μπορεί να μεγαλώσει, αλλά το μοτίβο επανάληψης που παρουσιάστηκε παραπάνω κλιμακώνεται γραμμικά, οπότε η απόδοση δεν αποτελεί πρόβλημα. Απλώς θυμηθείτε να διατηρείτε την έξοδο αναγνώσιμη — η ομαδοποίηση ανά σελίδα ή στυλ μπορεί να είναι χρήσιμη αν χρειάζεστε πιο βαθιά ανάλυση.

### Προσαρμοσμένοι Φάκελοι Γραμματοσειρών  

Αν αποθηκεύετε γραμματοσειρές σε μη‑τυπικό φάκελο (π.χ. σε κοινόχρηστο δίκτυο), ενημερώστε το Aspose.Words πού να ψάξει:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Ορίζοντας αυτό *πριν* τη φόρτωση του εγγράφου δίνει στη βιβλιοθήκη την ευκαιρία να βρει τις γραμματοσειρές, κάτι που μπορεί να εξαλείψει εντελώς ορισμένες προειδοποιήσεις.

### Καταστολή Συγκεκριμένων Προειδοποιήσεων  

Μερικές φορές γνωρίζετε ότι μια συγκεκριμένη υποκατάσταση είναι αποδεκτή (π.χ. μια διακοσμητική γραμματοσειρά που δεν σας πειράζει να αντικατασταθεί). Μπορείτε να τις φιλτράρετε μετά το γεγονός:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Συμβατότητα Έκδοσης  

Το enum `FontSubstitutionWarningLevel` είναι σταθερό από το Aspose.Words 20.12. Αν χρησιμοποιείτε παλαιότερη έκδοση, ίσως χρειαστεί να κάνετε αναβάθμιση για να έχετε πρόσβαση στη λειτουργία επιπέδου προειδοποίησης.

## Πλήρες Παράδειγμα Λειτουργίας  

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα που ενσωματώνει όλα τα παραπάνω βήματα. Επικολλήστε το σε ένα νέο console project, προσθέστε το πακέτο NuGet Aspose.Words, και ορίστε το `docPath` σε ένα έγγραφο που αναφέρει μια ελλιπή γραμματοσειρά.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Η εκτέλεση αυτού του προγράμματος θα **ενεργοποιήσει τις προειδοποιήσεις υποκατάστασης γραμματοσειρών**, **ανιχνεύσει ελλιπείς γραμματοσειρές**, **get missing font name**, και **list missing fonts** τόσο στην κονσόλα όσο και σε αρχείο CSV.

## Συμπέρασμα  

Καλύψαμε όλα όσα χρειάζεστε για να **ενεργοποιήσετε τις προειδοποιήσεις υποκατάστασης γραμματοσειρών** στο Aspose.Words, από τη αρχική διαμόρφωση μέχρι την εξαγωγή μιας καθαρής λίστας ελλιπών γραμματοσειρών. Ακολουθώντας τα παραπάνω βήματα θα μπορείτε να ελέγχετε τα έγγραφά σας, να διασφαλίζετε την οπτική πιστότητα και να αποφεύγετε δυσάρεστες εκπλήξεις κατά την απόδοση σε διακομιστή.

Στη συνέχεια, ίσως θελήσετε να εξερευνήσετε:

- **Ενσωμάτωση ελλιπών γραμματοσειρών** απευθείας στο παραγόμενο PDF ή DOCX (χρησιμοποιήστε `FontSettings.EmbeddedFonts`).
- **Αυτοματοποίηση εγκατάστασης γραμματοσειρών** σε agents κατασκευής βάσει της παραγόμενης αναφοράς.
- **Ενσωμάτωση σε CI pipelines** ώστε να αποτυγχάνουν οι builds όταν λείπουν κρίσιμες γραμματοσειρές.

Δοκιμάστε τα και θα μετατρέψετε ένα απλό σύστημα προειδοποιήσεων σε μια πλήρη ροή διαχείρισης γραμματοσειρών.

Καλό coding, και ας βρεθούν όλες σας οι γραμματοσειρές!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}