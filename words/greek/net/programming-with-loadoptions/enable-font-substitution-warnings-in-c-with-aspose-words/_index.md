---
category: general
date: 2026-06-20
description: Ενεργοποιήστε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών σε C#
  χρησιμοποιώντας το Aspose.Words. Μάθετε πώς να διαμορφώσετε τις LoadOptions, να
  καταγράψετε τις προειδοποιήσεις και να διαχειριστείτε αποτελεσματικά τις ελλείπουσες
  γραμματοσειρές.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: el
og_description: Ενεργοποιήστε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών σε
  C# με το Aspose.Words. Αυτός ο οδηγός δείχνει πώς να ρυθμίσετε το LoadOptions, να
  διαβάσετε το WarningInfo και να εμφανίσετε μηνύματα για ελλιπείς γραμματοσειρές.
og_title: Ενεργοποίηση Προειδοποιήσεων Υποκατάστασης Γραμματοσειρών σε C# – Πλήρης
  Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Ενεργοποίηση προειδοποιήσεων αντικατάστασης γραμματοσειρών σε C# με το Aspose.Words
url: /el/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών σε C# με Aspose.Words

Έχετε αναρωτηθεί ποτέ πώς να **ενεργοποιήσετε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών** όταν ένα έγγραφο Word αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή; Δεν είστε οι μόνοι. Οι ελλιπείς γραμματοσειρές μπορούν σιωπηρά να αλλοιώσουν τη διάταξη των παραγόμενων PDF ή εικόνων, και ο μόνος τρόπος να το εντοπίσετε νωρίς είναι να ακούτε τις προειδοποιήσεις που εκδίδει το Aspose.Words.

Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό παράδειγμα που δείχνει ακριβώς πώς να ενεργοποιήσετε αυτές τις προειδοποιήσεις, να τις εξάγετε από τη συλλογή `WarningInfo` και να εκτυπώσετε χρήσιμα μηνύματα στην κονσόλα. Στο τέλος θα ξέρετε πώς να ρυθμίσετε **Aspose.Words LoadOptions**, να διαχειριστείτε **C# font substitution warnings**, και να διατηρήσετε την αλυσίδα επεξεργασίας εγγράφων σας αδιάλειπτη.

Θα αγγίξουμε επίσης μερικές ακραίες περιπτώσεις — τι συμβαίνει αν καταστέλλετε τις προειδοποιήσεις ή αν χρειάζεται να τις καταγράψετε αντί για εκτύπωση — και θα σας δώσουμε ένα πλήρες, έτοιμο για αντιγραφή‑και‑επικόλληση δείγμα κώδικα που λειτουργεί με την πιο πρόσφατη έκδοση του Aspose.Words for .NET (έκδοση 24.10).

## Τι Θα Χρειαστείτε

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+)
- Μια αναφορά NuGet στο `Aspose.Words` (εγκατάσταση μέσω `dotnet add package Aspose.Words`)
- Ένα αρχείο Word που αναφέρει μια γραμματοσειρά που **δεν** έχετε εγκατεστημένη (π.χ., `DocumentWithMissingFont.docx`)
- Ένα καλό IDE (Visual Studio, Rider ή VS Code)

Αυτό είναι όλο — χωρίς πρόσθετες υπηρεσίες, χωρίς ιδιόκτητα εργαλεία. Έτοιμοι; Ας βουτήξουμε.

## Βήμα 1: Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών

Το πρώτο που πρέπει να κάνετε είναι να ενημερώσετε το Aspose.Words ότι θέλετε να ειδοποιηθείτε όταν αντικαθιστά μια ελλιπή γραμματοσειρά. Αυτό γίνεται μέσω της ιδιότητας `FontSettings` ενός αντικειμένου `LoadOptions`. Από προεπιλογή, οι προειδοποιήσεις είναι **απενεργοποιημένες** για να μην «θορυβούν» το API, οπότε πρέπει να ενεργοποιήσουμε τη λειτουργία μας.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Γιατί λειτουργεί:** Όταν το `FontSettings` δεν είναι `null`, η βιβλιοθήκη αυτόματα γεμίζει το `Document.WarningInfo` με οποιεσδήποτε καταχωρήσεις `WarningType.FontSubstitution` συναντά κατά τη φόρτωση ενός εγγράφου. Σκεφτείτε το ως ενεργοποίηση μιας «λειτουργίας αποσφαλμάτωσης» για τις γραμματοσειρές.

## Βήμα 2: Φόρτωση του Εγγράφου με τις Ρυθμισμένες Επιλογές

Τώρα που η συλλογή προειδοποιήσεων είναι ενεργή, φορτώστε το έγγραφό σας χρησιμοποιώντας το `LoadOptions` που μόλις προετοιμάσαμε. Αν το έγγραφο περιέχει μια ελλιπή γραμματοσειρά, το Aspose.Words θα αντικαταστήσει μια εναλλακτική και θα προσθέσει μια προειδοποίηση στη λίστα `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro tip:** Αν επεξεργάζεστε πολλά αρχεία σε βρόχο, επαναχρησιμοποιήστε το ίδιο αντικείμενο `LoadOptions` — η δημιουργία του μία φορά εξοικονομεί μερικά χιλιοστά του δευτερολέπτου ανά επανάληψη.

## Βήμα 3: Επανάληψη πάνω από το WarningInfo και Εμφάνιση Μηνυμάτων Αντικατάστασης Γραμματοσειρών

Μόλις φορτωθεί το έγγραφο, η συλλογή `WarningInfo` περιέχει κάθε προειδοποίηση που συνέβη κατά τη φόρτωση. Ενδιαφερόμαστε μόνο για `WarningType.FontSubstitution`, οπότε φιλτράρουμε ανάλογα.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Τρέχοντας το παραπάνω απόσπασμα έναντι ενός εγγράφου που αναφέρει τη λείπουσα γραμματοσειρά “Papyrus” μπορεί να παραγάγει έξοδο όπως:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Αυτά είναι τα **μηνύματα αντικατάστασης γραμματοσειρών** που ψάχνατε — σαφή, ενέργεια-προσαρμοσμένα και έτοιμα για καταγραφή ή αποστολή σε σύστημα ειδοποιήσεων.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα κονσόλας που συνδυάζει όλα τα παραπάνω. Αντιγράψτε‑και‑επικολλήστε το σε ένα νέο `.csproj` και πατήστε **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Αναμενόμενο Έξοδος

Αν το έγγραφο αναφέρει γραμματοσειρές που δεν είναι εγκατεστημένες, θα δείτε κάτι παρόμοιο με:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Αν κάθε γραμματοσειρά είναι παρούσα στο σύστημα, το πρόγραμμα θα εκτυπώσει απλώς:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Συνηθισμένα Προβλήματα & Pro Tips

| Πρόβλημα | Γιατί Συμβαίνει | Πώς να Διορθώσετε / Αποφύγετε |
|----------|----------------|------------------------------|
| **Οι προειδοποιήσεις εξαφανίζονται** | Καθαρίσατε το `FontSettings` ή χρησιμοποιήσατε `LoadOptions` χωρίς αυτό. | Πάντα δημιουργείτε `FontSettings` ακόμη και αν δεν τροποποιείτε ιδιότητες. |
| **Πάρα πολλές προειδοποιήσεις** | Το έγγραφο χρησιμοποιεί πολλές εξωτικές γραμματοσειρές. | Προσθέστε έναν προσαρμοσμένο φάκελο γραμματοσειρών στο `FontSettings` μέσω `SetFontsFolder` για να μειώσετε τις αντικαταστάσεις. |
| **Πτώση απόδοσης σε βρόχο** | Η επανδημιουργία του `LoadOptions` σε κάθε επανάληψη προσθέτει επιβάρυνση. | Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `LoadOptions` για όλα τα έγγραφα. |
| **Απουσία εξόδου κονσόλας** | Εκτέλεση μέσα σε GUI εφαρμογή όπου το `Console.WriteLine` αγνοείται. | Ανακατευθύνετε τις προειδοποιήσεις σε logger (`ILogger`) ή γράψτε σε αρχείο. |

### Διαχείριση Προειδοποιήσεων σε Πραγματική Υπηρεσία

Σε ένα web API πιθανότατα δεν θέλετε να γράφετε στην κονσόλα. Αντ' αυτού, διοχετεύστε τις προειδοποιήσεις σε δομημένο log:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Με αυτόν τον τρόπο διατηρείτε τη **διαχείριση προειδοποιήσεων εγγράφου** ενώ η υπηρεσία σας παραμένει καθαρή.

## Επέκταση του Παραδείγματος

- **Καταγραφή άλλων τύπων προειδοποιήσεων** (π.χ., `WarningType.UnknownFileFormat`) αφαιρώντας το φίλτρο `if`.
- **Αποθήκευση αναφοράς** όλων των προειδοποιήσεων σε JSON για downstream analytics.
- **Εξαναγκασμός συγκεκριμένης εναλλακτικής γραμματοσειράς** ορίζοντας `FontSettings.SubstitutionSettings.DefaultFontName`.

Όλα αυτά είναι φυσικές επεκτάσεις μόλις κυριαρχήσετε στην **ενεργοποίηση προειδοποιήσεων αντικατάστασης γραμματοσειρών**.

## Συμπέρασμα

Σας δείξαμε πώς να **ενεργοποιήσετε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών** σε C# χρησιμοποιώντας το Aspose.Words, από τη ρύθμιση του `LoadOptions` μέχρι την επανάληψη στο `WarningInfo` και την εκτύπωση φιλικών μηνυμάτων. Ακολουθώντας τα παραπάνω βήματα μπορείτε να προστατεύσετε τις γραμμές επεξεργασίας εγγράφων σας από σιωπηλές αλλαγές διάταξης που προκαλούνται από ελλιπείς γραμματοσειρές.

Στη συνέχεια, δοκιμάστε να προσθέσετε έναν προσαρμοσμένο φάκελο γραμματοσειρών, να καταγράψετε τις προειδοποιήσεις σε αρχείο ή ακόμη και να τις στείλετε σε πίνακα παρακολούθησης. Το ίδιο μοτίβο λειτουργεί για οποιοδήποτε σενάριο **διαχείρισης προειδοποιήσεων εγγράφου**, είτε μετατρέπετε σε PDF, αποδίδετε εικόνες ή εκτελείτε mail‑merge.

Έχετε ερωτήσεις σχετικά με **C# font substitution warnings** ή θέλετε να μοιραστείτε μια έξυπνη λύση; Αφήστε ένα σχόλιο παρακάτω — καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών σε Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Πώς να Εντοπίσετε Γραμματοσειρές σε Aspose.Words – Διαχείριση Προειδοποιήσεων & Ρυθμίσεων](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών σε Java με Aspose.Words – Πλήρης Οδηγός](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}