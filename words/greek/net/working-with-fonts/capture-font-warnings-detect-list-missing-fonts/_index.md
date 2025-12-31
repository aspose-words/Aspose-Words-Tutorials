---
category: general
date: 2025-12-31
description: Καταγράψτε τις προειδοποιήσεις γραμματοσειρών στο Aspose.Words για να
  εντοπίσετε τις ελλιπείς γραμματοσειρές και να τις παραθέσετε στην εφαρμογή .NET
  σας. Μάθετε μια βήμα‑βήμα λύση σε C#.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: el
og_description: Καταγράψτε τις προειδοποιήσεις γραμματοσειρών στο Aspose.Words για
  να εντοπίσετε ελλιπείς γραμματοσειρές και να τις απαριθμήσετε. Πλήρης οδηγός C#
  με κώδικα και συμβουλές.
og_title: Καταγραφή Προειδοποιήσεων Γραμματοσειρών – Εντοπισμός & Λίστα Ελλειπουσών
  Γραμματοσειρών
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Καταγραφή Προειδοποιήσεων Γραμματοσειρών – Εντοπισμός & Καταγραφή Ελλειπουσών
  Γραμματοσειρών
url: /el/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταγραφή Προειδοποιήσεων Γραμματοσειρών – Εντοπισμός & Λίστα Ελλειπουσών Γραμματοσειρών

Έχετε ποτέ χρειαστεί να **καταγράψετε προειδοποιήσεις γραμματοσειρών** κατά τη φόρτωση ενός εγγράφου Word αλλά δεν ήξερτε πώς να εμφανίσετε τις λεπτομέρειες των ελλειπουσών γραμματοσειρών; Δεν είστε μόνοι. Σε πολλά πραγματικά έργα, οι ελλείπουσες γραμματοσειρές προκαλούν προβλήματα διάταξης, και χωρίς τις κατάλληλες προειδοποιήσεις καταλήγετε να κυνηγάτε φανταστικά σφάλματα.  

Σε αυτό το tutorial θα σας δείξουμε πώς να **εντοπίσετε ελλείπουσες γραμματοσειρές** και να **καταγράψετε ελλείπουσες γραμματοσειρές** χρησιμοποιώντας το Aspose.Words for .NET. Στο τέλος θα έχετε ένα έτοιμο προς εκτέλεση απόσπασμα C# που εκτυπώνει κάθε προειδοποίηση αντικατάστασης, ώστε να μπορείτε να το καταγράψετε, να το ειδοποιήσετε ή ακόμη και να αντικαταστήσετε τις γραμματοσειρές αυτόματα.

---

## Γιατί η Καταγραφή Προειδοποιήσεων Γραμματοσειρών Είναι Σημαντική

Όταν το Aspose.Words ανοίγει ένα DOCX που αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή, αντικαθιστά σιωπηρά με εναλλακτική. Το έγγραφο φαίνεται εντάξει, αλλά η οπτική πιστότητα υποβαθμίζεται — σκεφτείτε ένα εταιρικό λογότυπο που εμφανίζεται με λάθος γραμματοσειρά.  

Η καταγραφή αυτών των προειδοποιήσεων σας επιτρέπει να:

* **Διατηρήσετε τη συνοχή της μάρκας** – ξέρετε ακριβώς ποιες γραμματοσειρές λείπουν.  
* **Αυτοματοποιήσετε την αποκατάσταση** – αντικαταστήστε τις ελλείπουσες γραμματοσειρές προγραμματιστικά.  
* **Ελέγξετε τη συμμόρφωση** – δημιουργήστε αναφορές για νομικές ή σχεδιαστικές αξιολογήσεις.  

Με λίγα λόγια, η **καταγραφή προειδοποιήσεων γραμματοσειρών** είναι η πρώτη γραμμή άμυνας ενάντια στην σιωπηρή αντικατάσταση γραμματοσειρών.

---

## Ρύθμιση LoadOptions για Εντοπισμό Ελλειπουσών Γραμματοσειρών

Το κλειδί για την εμφάνιση των προειδοποιήσεων είναι η ιδιότητα `LoadOptions.FontSubstitutionWarning`. Από προεπιλογή είναι ορισμένη σε `None`, πράγμα που σημαίνει ότι το Aspose.Words καταπίνει τα μηνύματα. Αλλάζοντάς την σε `All` λέτε στη βιβλιοθήκη να καταγράψει κάθε γεγονός αντικατάστασης.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Pro tip:** Αν έχετε ήδη έναν προσαρμοσμένο φάκελο γραμματοσειρών, αντιστοιχίστε τον με `FontSettings.SetFontsFolder("path")` πριν φορτώσετε το έγγραφο. Με αυτόν τον τρόπο μπορείτε να **εντοπίσετε ελλείπουσες γραμματοσειρές** που δεν βρίσκονται στον φάκελο του συστήματος.

---

## Φόρτωση του Εγγράφου και Καταγραφή Ελλειπουσών Γραμματοσειρών

Τώρα που τα `LoadOptions` είναι έτοιμα, το επόμενο βήμα είναι η φόρτωση του αρχείου Word. Ο κατασκευαστής δέχεται το αντικείμενο επιλογών, και κάθε αντικατάσταση θα καταγραφεί στη `WarningInfoCollection` του εγγράφου.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Αν το αρχείο αναφέρει γραμματοσειρές που δεν είναι διαθέσιμες, κάθε ελλείπουσα γραμματοσειρά δημιουργεί μια καταχώρηση `WarningInfo`. Μπορείτε να **καταγράψετε ελλείπουσες γραμματοσειρές** επαναλαμβάνοντας τη συλλογή αυτή.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Η τυπική έξοδος μοιάζει με:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Κάθε γραμμή σας λέει ακριβώς ποια γραμματοσειρά λείπει, ικανοποιώντας την απαίτηση **καταγραφής ελλειπουσών γραμματοσειρών**.

---

## Ανάγνωση και Ερμηνεία της WarningInfoCollection

Η `WarningInfoCollection` μπορεί να περιέχει διαφορετικούς τύπους προειδοποιήσεων (π.χ., `DocumentStructure`, `ImageLoading`). Για να εστιάσετε αποκλειστικά σε προβλήματα γραμματοσειρών, φιλτράρετε με `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Γιατί να φιλτράρετε; Επειδή ένα μεγάλο έγγραφο μπορεί επίσης να δημιουργήσει προειδοποιήσεις για κατεστραμμένες εικόνες ή μη υποστηριζόμενες λειτουργίες. Περιορίζοντας τη συλλογή αποφεύγετε τον θόρυβο και διατηρείτε την έξοδο **καταγραφής προειδοποιήσεων γραμματοσειρών** καθαρή.

---

## Πλήρες Παράδειγμα – Καταγραφή Προειδοποιήσεων Γραμματοσειρών σε Δράση

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET console project. Δείχνει κάθε βήμα, από τη ρύθμιση των `LoadOptions` μέχρι την εκτύπωση μιας τακτοποιημένης λίστας ελλειπουσών γραμματοσειρών.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Αναμενόμενη έξοδος κονσόλας**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Αν το έγγραφο δεν περιέχει ελλείπουσες γραμματοσειρές, θα δείτε:

```
All referenced fonts are available – no warnings captured.
```

---

## Συνηθισμένες Ακραίες Περιπτώσεις & Πώς να τις Διαχειριστείτε

| Κατάσταση | Γιατί Συμβαίνει | Προτεινόμενη Διόρθωση |
|-----------|----------------|-----------------|
| **Το έγγραφο χρησιμοποιεί ενσωματωμένη γραμματοσειρά OpenType** | Το Aspose.Words μπορεί να διαβάσει ενσωματωμένες γραμματοσειρές, αλλά μόνο αν το αρχείο δεν είναι κατεστραμμένο. | Ελέγξτε το DOCX στο Word πρώτα· ενσωματώστε ξανά τη γραμματοσειρά αν χρειάζεται. |
| **Μεγάλος αριθμός προειδοποιήσεων** (π.χ., 200+ ελλείπουσες γραμματοσειρές) | Μαζικές εισαγωγές από παλαιά συστήματα συχνά αναφέρονται σε ευρεία παλέτα γραμματοσειρών. | Επεξεργαστείτε τις προειδοποιήσεις σε παρτίδες: αποθηκεύστε τις σε βάση δεδομένων, έπειτα εκτελέστε script εγκατάστασης γραμματοσειρών. |
| **Η WarningInfoCollection είναι κενή** | Είτε το έγγραφο έχει όλες τις γραμματοσειρές, είτε η `FontSubstitutionWarning` έμεινε σε `None`. | Επαληθεύστε τη ρύθμιση των `LoadOptions` και βεβαιωθείτε ότι φορτώνετε το σωστό αρχείο. |
| **Προσαρμοσμένες γραμματοσειρές σε δικτυακό κοινόχρηστο** | Η καθυστέρηση δικτύου μπορεί να προκαλέσει time‑outs κατά την αναζήτηση γραμματοσειρών. | Προφορτώστε τις γραμματοσειρές στο `FontSettings` με `SetFontsFolder` και ορίστε `CacheFontData = true`. |

---

## Εικονογράφηση

![παράδειγμα καταγραφής προειδοποιήσεων γραμματοσειρών](https://example.com/images/capture-font-warnings.png "παράδειγμα καταγραφής προειδοποιήσεων γραμματοσειρών")

*Το στιγμιότυπο δείχνει μια εκτέλεση κονσόλας όπου αναφέρονται δύο ελλείπουσες γραμματοσειρές.*

---

## Επόμενα Βήματα – Πέρα από την Απλή Αναφορά

Τώρα που μπορείτε να **καταγράψετε προειδοποιήσεις γραμματοσειρών**, σκεφτείτε την αυτοματοποίηση της αποκατάστασης:

1. **Αυτόματη Αντικατάσταση Γραμματοσειρών** – Αντικαταστήστε τις ελλείπουσες γραμματοσειρές με μια εγκεκριμένη εναλλακτική της εταιρείας τροποποιώντας το `FontSettings.SubstitutionSettings`.  
2. **Καταγραφή σε Σύστημα Παρακολούθησης** – Μεταφέρετε τα μηνύματα προειδοποίησης σε Serilog, ELK ή Azure Application Insights.  
3. **Αναφορές προς το Χρήστη** – Δημιουργήστε μια σύνοψη HTML ή PDF για τους σχεδιαστές ώστε να δουν ποιες γραμματοσειρές χρειάζεται να εγκατασταθούν.

Όλες αυτές οι επεκτάσεις βασίζονται στην ίδια θεμελιώδη διαδικασία που καλύψαμε: ρύθμιση των `LoadOptions`, φόρτωση του εγγράφου και ανάγνωση της `WarningInfoCollection`.

---

## Συμπέρασμα

Μόλις μάθατε πώς να **καταγράψετε προειδοποιήσεις γραμματοσειρών** στο Aspose.Words, **να εντοπίσετε ελλείπουσες γραμματοσειρές** και **να καταγράψετε ελλείπουσες γραμματοσειρές** με καθαρή έξοδο κονσόλας. Η προσέγγιση είναι απλή, απαιτεί μόνο λίγες γραμμές C# και λειτουργεί με οποιαδήποτε έκδοση .NET που υποστηρίζει το Aspose.Words 23.x ή νεότερη.  

Δοκιμάστε το σε ένα δείγμα DOCX που αναφέρει μια γραμματοσειρά που έχετε απεγκαταστήσει εκ προθέσεως – θα δείτε τις προειδοποιήσεις να εμφανίζονται αμέσως. Από εκεί μπορείτε να αποφασίσετε αν θα εγκαταστήσετε τις ελλείπουσες γραμματοσειρές, θα τις αντικαταστήσετε προγραμματιστικά ή απλώς θα καταγράψετε το ζήτημα για μελλοντική ανασκόπηση.

Καλή προγραμματιστική δουλειά, και οι εγγραφές σας να αποδίδουν πάντα με τις σωστές γραμματοσειρές!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}