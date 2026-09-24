---
category: general
date: 2026-02-18
description: Μάθετε πώς να καταγράφετε προειδοποιήσεις γραμματοσειρών και να εντοπίζετε
  ελλιπείς γραμματοσειρές σε C# χρησιμοποιώντας το Aspose.Words. Ακολουθήστε αυτόν
  τον βήμα‑βήμα οδηγό για να διαχειρίζεστε αποτελεσματικά τις ελλιπείς γραμματοσειρές.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: el
og_description: Καταγράψτε προειδοποιήσεις γραμματοσειρών σε C# και μάθετε πώς να
  εντοπίζετε ελλείπουσες γραμματοσειρές, να τις διαχειρίζεστε και να τις καταγράφετε
  με ένα πλήρες παράδειγμα κώδικα.
og_title: Καταγραφή Προειδοποιήσεων Γραμματοσειράς σε C# – Πλήρης Οδηγός
tags:
- Aspose.Words
- C#
- Font Management
title: Καταγραφή προειδοποιήσεων γραμματοσειράς σε C# – Πλήρης οδηγός προγραμματισμού
url: /el/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταγραφή Προειδοποιήσεων Γραμματοσειρών σε C# – Πλήρης Οδηγός Προγραμματισμού

Έχετε αναρωτηθεί ποτέ πώς να **καταγράψετε προειδοποιήσεις γραμματοσειρών** όταν ένα έγγραφο αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή; Δεν είστε ο μόνος. Σε πολλές επιχειρησιακές εφαρμογές, η έλλειψη γραμματοσειρών προκαλεί προβλήματα διάταξης, και ο μόνος αξιόπιστος τρόπος για να τις εντοπίσετε είναι ακούγοντας τις προειδοποιήσεις που εκδίδει η βιβλιοθήκη.  

Σε αυτό το tutorial θα σας δείξουμε μια έτοιμη προς εκτέλεση λύση που όχι μόνο **καταγράφει προειδοποιήσεις γραμματοσειρών** αλλά επίσης **ανιχνεύει ελλιπείς γραμματοσειρές**, **χειρίζεται ελλιπείς γραμματοσειρές** και ακόμη **καταγράφει τις ελλιπείς γραμματοσειρές** ώστε να αποφασίσετε αν θα τις αντικαταστήσετε, θα τις ενσωματώσετε ή θα ειδοποιήσετε τον χρήστη. Δεν χρειάζεται εξωτερική τεκμηρίωση — απλώς αντιγράψτε, επικολλήστε και τρέξτε.

## Τι Θα Μάθετε

- Πώς να διαμορφώσετε το `LoadOptions` ώστε να ενεργοποιήσετε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών.  
- Τον ακριβή κώδικα που χρειάζεστε για να φορτώσετε ένα DOCX και να εξάγετε κάθε προειδοποίηση.  
- Γιατί κάθε βήμα είναι σημαντικό, συμπεριλαμβανομένων των παραμέτρων απόδοσης.  
- Διαχείριση ακραίων περιπτώσεων όπως έγγραφα με γραμματοσειρές μικτής γραφής ή προσαρμοσμένους φακέλους γραμματοσειρών.  

**Προαπαιτούμενα**: .NET 6+ (ή .NET Framework 4.6+), μια αναφορά στο πακέτο **Aspose.Words** μέσω NuGet, και βασική γνώση της C#. Αν δεν έχετε χρησιμοποιήσει ποτέ το Aspose.Words, μην ανησυχείτε — αυτός ο οδηγός σας καθοδηγεί βήμα‑βήμα.

![Διάγραμμα που δείχνει τη ροή καταγραφής προειδοποιήσεων γραμματοσειρών](image.png){alt="διάγραμμα καταγραφής προειδοποιήσεων γραμματοσειρών"}

## Καταγραφή Προειδοποιήσεων Γραμματοσειρών – Γιατί Είναι Σημαντικό

Όταν το Aspose.Words φορτώνει ένα έγγραφο, αντικαθιστά σιωπηλά κάθε μη διαθέσιμη γραμματοσειρά με μια εναλλακτική. Αυτή η εναλλακτική διατηρεί τη λειτουργία φόρτωσης, αλλά το οπτικό αποτέλεσμα μπορεί να είναι εντελώς λανθασμένο. Ενεργοποιώντας τη σημαία **SubstitutionWarningLevel.All**, η βιβλιοθήκη προσθέτει μια καταχώρηση `WarningInfo` για κάθε ελλιπή γραμματοσειρά, επιτρέποντάς σας να **ανιχνεύσετε ελλιπείς γραμματοσειρές** πριν το έγγραφο αποδοθεί ή αποθηκευτεί.

> **Συμβουλή επαγγελματία:** Αν επεξεργάζεστε εκατοντάδες αρχεία σε μια παρτίδα, η καταγραφή αυτών των προειδοποιήσεων σε κεντρικό αποθηκευτικό χώρο μπορεί να σας εξοικονομήσει ώρες χειροκίνητου QA αργότερα.

## Βήμα 1: Ρύθμιση του Έργου Σας

1. Ανοίξτε το αγαπημένο σας IDE (Visual Studio, Rider, VS Code).  
2. Δημιουργήστε ένα νέο έργο console:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Προσθέστε το πακέτο Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Αυτό είναι όλο — χωρίς επιπλέον DLLs, χωρίς COM interop. Η βιβλιοθήκη περιλαμβάνει όλα όσα χρειάζεστε για να **χειριστείτε ελλιπείς γραμματοσειρές**.

## Βήμα 2: Προετοιμασία Load Options για Καταγραφή Όλων των Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών

Για να κάνει η μηχανή **καταγραφή προειδοποιήσεων γραμματοσειρών**, πρέπει να της πείτε να καταγράψει κάθε αντικατάσταση. Το παρακάτω απόσπασμα δημιουργεί ένα αντικείμενο `LoadOptions`, ενεργοποιεί το επίπεδο προειδοποίησης και (προαιρετικά) δείχνει στη μηχανή έναν φάκελο που περιέχει προσαρμοσμένες γραμματοσειρές που ίσως θέλετε να χρησιμοποιήσετε.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Γιατί είναι σημαντικό:**  
- Το `SubstitutionWarningLevel.All` εξασφαλίζει ότι **κάθε** συμβάν ελλιπής γραμματοσειράς καταγράφεται, όχι μόνο το πρώτο.  
- Χωρίς αυτή τη σημαία, το Aspose.Words αντικαθιστά σιωπηλά τη γραμματοσειρά και δεν γνωρίζετε ποτέ ότι υπάρχει πρόβλημα.

## Βήμα 3: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Τώρα ανοίγουμε πραγματικά το αρχείο. Αντικαταστήστε το `DocumentWithMissingFonts.docx` με τη διαδρομή του δοκιμαστικού σας εγγράφου.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Αν το αρχείο περιέχει αναφορές σε γραμματοσειρές που δεν υπάρχουν στο σύστημα (ή στον προαιρετικό φάκελο που προσθέσατε), η συλλογή `document.WarningInfoCollection` θα γεμίσει.

## Βήμα 4: Εύρεση και Εμφάνιση Οποιεσδήποτε Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών

Αυτή είναι η καρδιά του tutorial: η επανάληψη πάνω στη `WarningInfoCollection` για **καταγραφή ελλιπών γραμματοσειρών**. Θα φιλτράρουμε με `WarningType.FontSubstitution` και θα εκτυπώσουμε ένα φιλικό μήνυμα.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Αναμενόμενη Έξοδος

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Αν το έγγραφο χρησιμοποιεί μόνο εγκατεστημένες γραμματοσειρές, θα δείτε τη γραμμή “✅ No missing fonts detected”.

## Βήμα 5: Προχωρημένο – Πώς να **Χειριστείτε Ελλιπείς Γραμματοσειρές** Προγραμματιστικά

Η απλή εκτύπωση μιας λίστας μπορεί να αρκεί για ένα εργαλείο διάγνωσης, αλλά πολλά παραγωγικά συστήματα χρειάζονται να **χειρίζονται ελλιπείς γραμματοσειρές** αυτόματα. Παρακάτω παρουσιάζονται δύο κοινές στρατηγικές:

### 5.1 Αντικατάσταση με Γνωστή Εναλλακτική

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Ενσωμάτωση Προσαρμοσμένης Γραμματοσειράς Κατά τη Διάρκεια Εκτέλεσης

Αν έχετε ένα εταιρικό αρχείο γραμματοσειράς (`MyBrand.ttf`), μπορείτε να το ενσωματώσετε όταν εντοπιστεί μια ελλιπής γραμματοσειρά:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Σημείωση:** Η ενσωμάτωση γραμματοσειρών μπορεί να αυξήσει το μέγεθος του αρχείου εξόδου, οπότε ζυγίστε το trade‑off μεταξύ πιστότητας και εύρους ζώνης.

## Συνηθισμένα Πιθανά Σφάλματα και Πώς να τα Αποφύγετε

| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|---------|--------------|-----|
| Δεν εμφανίζονται προειδοποιήσεις παρόλο που το έγγραφο φαίνεται λανθασμένο | `SubstitutionWarningLevel` δεν έχει οριστεί σε `All` | Βεβαιωθείτε ότι το βήμα 2 ορίζει τη σημαία ακριβώς όπως φαίνεται |
| Η λίστα προειδοποιήσεων εμφανίζει την ίδια γραμματοσειρά πολλές φορές | Το έγγραφο περιέχει τη γραμματοσειρά σε πολλά στυλ | Απο-διπλοτυπώστε αν χρειάζεστε μόνο μοναδική λίστα: `fontWarnings.Select(w => w.Description).Distinct()` |
| Η εφαρμογή καταρρέει σε μεγάλα αρχεία DOCX | Φόρτωση με προεπιλεγμένες ρυθμίσεις μνήμης | Χρησιμοποιήστε `LoadOptions.LoadFormat` ή κάντε streaming του αρχείου για να μειώσετε την πίεση μνήμης |

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Τρέξτε το πρόγραμμα με `dotnet run`. Θα πρέπει να δείτε τη λίστα των ελλιπών γραμματοσειρών στην κονσόλα, επιβεβαιώνοντας ότι έχετε **καταγράψει επιτυχώς προειδοποιήσεις γραμματοσειρών**.

## Συμπέρασμα

Τώρα έχετε ένα πλήρες, έτοιμο για παραγωγή πρότυπο για **καταγραφή προειδοποιήσεων γραμματοσειρών**, **ανίχνευση ελλιπών γραμματοσειρών**, **χειρισμό ελλιπών γραμματοσειρών** και **καταγραφή ελλιπών γραμματοσειρών** χρησιμοποιώντας το Aspose.Words σε C#. Η προσέγγιση είναι ελαφριά, απαιτεί μόνο λίγες γραμμές κώδικα και μπορεί να ενσωματωθεί σε οποιοδήποτε υπάρχον pipeline — είτε εσείς

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}