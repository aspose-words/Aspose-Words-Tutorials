---
category: general
date: 2026-01-08
description: Μάθετε πώς να φορτώνετε αρχεία DOCX σε C# και να εντοπίζετε ελλιπείς
  γραμματοσειρές με προειδοποιήσεις. Περιλαμβάνει βήμα‑βήμα κώδικα για την καταγραφή
  των προειδοποιήσεων και τη διαχείριση της αντικατάστασης γραμματοσειρών.
draft: false
keywords:
- how to load docx
- load word document
- detect missing fonts
- how to list warnings
- how to detect missing fonts
language: el
og_description: Πώς να φορτώσετε DOCX σε C# και να εντοπίσετε ελλείπουσες γραμματοσειρές
  χρησιμοποιώντας προειδοποιήσεις. Ακολουθήστε αυτόν τον οδηγό για ένα πλήρες, εκτελέσιμο
  παράδειγμα.
og_title: Πώς να φορτώσετε DOCX και να εντοπίσετε ελλιπείς γραμματοσειρές – Εγχειρίδιο
  C#
tags:
- C#
- Aspose.Words
- DocumentProcessing
title: Πώς να φορτώσετε DOCX και να εντοπίσετε ελλιπείς γραμματοσειρές – Πλήρης οδηγός
  C#
url: /el/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Φορτώσετε DOCX και να Εντοπίσετε Ελλείπουσες Γραμματοσειρές – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί ποτέ **πώς να φορτώσετε docx** αρχεία σε μια εφαρμογή .NET χωρίς να χάνετε σιωπηρά πληροφορίες γραμματοσειράς; Δεν είστε ο μόνος. Όταν ένα έγγραφο Word αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή, το Aspose.Words (ή οποιαδήποτε παρόμοια βιβλιοθήκη) θα την αντικαταστήσει, και μπορεί να μην το παρατηρήσετε ποτέ, εκτός αν ζητήσετε προειδοποιήσεις.  

Σε αυτό το tutorial θα απαντήσουμε σε αυτήν την ερώτηση, θα σας δείξουμε **πώς να φορτώσετε docx**, και θα περάσουμε τη διαδικασία **εντοπισμού ελλείπουσων γραμματοσειρών** καταγράφοντας τις παραγόμενες προειδοποιήσεις. Στο τέλος θα έχετε ένα έτοιμο προς εκτέλεση πρόγραμμα κονσόλας που εκτυπώνει κάθε προειδοποίηση αντικατάστασης γραμματοσειράς, ώστε να αποφασίσετε αν θα ενσωματώσετε τη λείπουσα γραμματοσειρά, θα την αντικαταστήσετε ή θα ειδοποιήσετε τον χρήστη.

> **Τι θα λάβετε:** ένα πλήρες δείγμα κώδικα, εξήγηση κάθε γραμμής, συμβουλές για πραγματικά έργα, και απαντήσεις σε κοινά σενάρια “τι θα γίνει αν” όπως η διαχείριση πολλαπλών ελλείπουσων γραμματοσειρών ή η καταστολή προειδοποιήσεων όταν δεν τις χρειάζεστε.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το δείγμα χρησιμοποιεί top‑level statements για συντομία)
- Aspose.Words for .NET (δωρεάν δοκιμή ή έκδοση με άδεια)
- Ένα αρχείο DOCX που σκόπιμα αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., “Comic Sans MS” σε διακομιστή Linux)
- Visual Studio, VS Code, ή οποιονδήποτε επεξεργαστή προτιμάτε

Δεν απαιτούνται άλλα πακέτα.

## Βήμα 1 – Εγκατάσταση Aspose.Words

Πρώτα απ' όλα, χρειάζεστε τη βιβλιοθήκη που μπορεί να διαβάσει αρχεία Word και να εκθέτει πληροφορίες προειδοποιήσεων.

```bash
dotnet add package Aspose.Words
```

Αυτή η εντολή παίρνει το πιο πρόσφατο σταθερό πακέτο NuGet. Αν χρησιμοποιείτε CI pipeline, βεβαιωθείτε ότι το βήμα επαναφοράς εκτελείται πριν από τη μεταγλώττιση.

## Βήμα 2 – Ενεργοποίηση Λεπτομερών Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς

Από προεπιλογή, το Aspose.Words καταγράφει τις προειδοποιήσεις μόνο εσωτερικά. Για να τις εμφανίσετε, πρέπει να ενεργοποιήσετε τη σημαία `FontSubstitutionWarnings` σε ένα αντικείμενο `LoadOptions`.

```csharp
// Step 2: Create LoadOptions with font‑substitution warnings enabled
var loadOptions = new Aspose.Words.LoadOptions
{
    FontSubstitutionWarnings = true
};
```

**Γιατί;** Χωρίς αυτή τη σημαία η βιβλιοθήκη θα αντικαταστήσει σιωπηρά τις ελλείπουσες γραμματοσειρές με εναλλακτική, και δεν θα γνωρίζετε ποτέ ότι κάτι άλλαξε. Η ενεργοποίηση της σημαίας λέει στη μηχανή: «Γειά, ενημερώστε με όταν το κάνετε αυτό».

## Βήμα 3 – Φόρτωση του Αρχείου DOCX

Τώρα πραγματικά **φορτώνουμε το docx** χρησιμοποιώντας τις επιλογές που μόλις διαμορφώσαμε.

```csharp
// Step 3: Load the document (replace the path with your own file)
string docPath = @"C:\Docs\MissingFont.docx";
var document = new Aspose.Words.Document(docPath, loadOptions);
```

Αν το αρχείο δεν βρεθεί, θα ριχθεί εξαίρεση—οπότε ίσως θελήσετε να το τυλίξετε σε try/catch σε κώδικα παραγωγής. Για το σκοπό αυτού του οδηγού το κρατάμε απλό.

## Βήμα 4 – Επανάληψη Στο WarningInfo για Εύρεση Αντικαταστάσεων Γραμματοσειράς

Το Aspose.Words αποθηκεύει κάθε προειδοποίηση στη συλλογή `Document.WarningInfo`. Θα φιλτράρουμε για `WarningType.FontSubstitution` και θα εκτυπώσουμε ένα φιλικό μήνυμα.

```csharp
// Step 4: List all font‑substitution warnings
foreach (var warning in document.WarningInfo)
{
    if (warning.Type == Aspose.Words.WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Description}");
    }
}
```

**Τι θα δείτε:** κάτι σαν  
`⚠️ Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".`

Αυτή η γραμμή σας λέει ακριβώς ποια γραμματοσειρά λείπει και ποια εναλλακτική χρησιμοποιήθηκε.

## Βήμα 5 – Πλήρες, Εκτελέσιμο Παράδειγμα (Top‑Level Statements)

Συνδυάζοντας όλα, εδώ είναι ένα πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα νέο έργο κονσόλας (`dotnet new console`). Συγκεντρώνεται και εκτελείται όπως είναι.

```csharp
// ------------------------------------------------------------
// Complete example: how to load docx and detect missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;

try
{
    // 1️⃣ Enable detailed font‑substitution warnings
    var loadOptions = new LoadOptions { FontSubstitutionWarnings = true };

    // 2️⃣ Load the Word document (adjust the path as needed)
    string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
    var doc = new Document(docPath, loadOptions);

    // 3️⃣ Walk through all warnings and print font‑substitution entries
    bool anyMissing = false;
    foreach (var warning in doc.WarningInfo)
    {
        if (warning.Type == WarningType.FontSubstitution)
        {
            anyMissing = true;
            Console.WriteLine($"⚠️ Font substituted: {warning.Description}");
        }
    }

    if (!anyMissing)
    {
        Console.WriteLine("✅ No missing fonts detected – all fonts are available.");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"❌ Error: {ex.Message}");
}
```

### Αναμενόμενο Αποτέλεσμα

- Αν το έγγραφο αναφέρει μια μη εγκατεστημένη γραμματοσειρά:  

  ```
  ⚠️ Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
  ```

- Αν όλες οι γραμματοσειρές είναι παρούσες:  

  ```
  ✅ No missing fonts detected – all fonts are available.
  ```

## Βήμα 6 – Συνηθισμένες Παραλλαγές και Ακραίες Περιπτώσεις

### Φόρτωση Εγγράφου από Stream

Μερικές φορές λαμβάνετε ένα DOCX μέσω API αντί για διαδρομή αρχείου. Οι ίδιες `LoadOptions` λειτουργούν με ένα `MemoryStream`.

```csharp
using var stream = new FileStream(docPath, FileMode.Open);
var docFromStream = new Document(stream, loadOptions);
```

### Καταστολή Όλων των Προειδοποιήσεων Εκτός από την Αντικατάσταση Γραμματοσειράς

Αν σας ενδιαφέρουν μόνο οι ελλείπουσες γραμματοσειρές, μπορείτε να διαγράψετε τις άλλες προειδοποιήσεις μετά τη φόρτωση:

```csharp
doc.WarningInfo.Clear(); // Clears everything
foreach (var warning in doc.WarningInfo) { /* ... */ } // Now only font warnings remain
```

### Διαχείριση Πολλαπλών Ελλείπουσων Γραμματοσειρών

Ο βρόχος που χρησιμοποιήσαμε ήδη συγκεντρώνει κάθε προειδοποίηση αντικατάστασης, έτσι θα δείτε μια γραμμή για κάθε ελλείπουσα γραμματοσειρά. Σε μια μεγάλη εργασία batch ίσως θέλετε να τις συλλέξετε σε λίστα και να τις γράψετε σε CSV για μεταγενέστερη ανάλυση.

```csharp
var missingFonts = new List<string>();
foreach (var warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        missingFonts.Add(warning.Description);
}
File.WriteAllLines("MissingFontsReport.txt", missingFonts);
```

### Αυτόματη Ενσωμάτωση Ελλείπουσων Γραμματοσειρών

Το Aspose.Words μπορεί να ενσωματώσει γραμματοσειρές αν παρέχετε ένα φάκελο που περιέχει τα ελλείποντα αρχεία:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);
```

Με αυτόν τον τρόπο το παραγόμενο έγγραφο δεν θα χρειάζεται τη γραμματοσειρά εγκατεστημένη στον προορισμό.

## Επαγγελματικές Συμβουλές & Πιθανά Προβλήματα

- **Pro tip:** Πάντα ενεργοποιείτε το `FontSubstitutionWarnings` σε περιβάλλον staging. Είναι φθηνό και μπορεί να σας προστατεύσει από δυσάρεστες εκπλήξεις διάταξης στην παραγωγή.
- **Watch out for:** ευαίσθητα σε πεζά/κεφαλαία ονόματα γραμματοσειρών στο Linux. “Times New Roman” vs “times new roman” μπορεί να θεωρηθεί ως διαφορετικές γραμματοσειρές.
- **Performance note:** Η φόρτωση μεγάλων αρχείων DOCX με ενεργές προειδοποιήσεις προσθέτει μικρή επιβάρυνση (≈2‑3 %). Σε υπηρεσία υψηλής διαμεριστικής ροής ίσως θέλετε να το ενεργοποιείτε ανά αίτηση αντί για παγκοσμίως.
- **Version check:** Ο παραπάνω κώδικας λειτουργεί με Aspose.Words 23.10 και νεότερο. Αν χρησιμοποιείτε παλαιότερη έκδοση, η ιδιότητα `WarningInfo` μπορεί να ονομάζεται `Warnings`. Προσαρμόστε αναλόγως.

## Συμπέρασμα

Τώρα ξέρετε **πώς να φορτώσετε docx** σε C#, να ενεργοποιήσετε λεπτομερείς προειδοποιήσεις, και **να εντοπίσετε ελλείπουσες γραμματοσειρές** καταγράφοντας κάθε αντικατάσταση. Το πλήρες παράδειγμα δείχνει ένα πραγματικό πρότυπο που μπορείτε να ενσωματώσετε σε οποιαδήποτε εφαρμογή κονσόλας, web API ή υπηρεσία παρασκηνίου.

Επόμενα βήματα; Δοκιμάστε να συνδυάσετε αυτήν την προσέγγιση με CI pipeline που επικυρώνει κάθε εισερχόμενο αρχείο Word, ή επεκτείνετε τη λογική για αυτόματη ενσωμάτωση ελλείπουσων γραμματοσειρών για απρόσκοπτη κατανάλωση. Αν χρειάζεται να **φορτώσετε word document** από cloud blob, απλώς αντικαταστήστε τη διαδρομή αρχείου με ένα `MemoryStream`—τα υπόλοιπα παραμένουν τα ίδια.

Καλό κώδικα, και εύχομαι τα έγγραφά σας πάντα να αποδίδουν ακριβώς όπως προορίζεται!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}