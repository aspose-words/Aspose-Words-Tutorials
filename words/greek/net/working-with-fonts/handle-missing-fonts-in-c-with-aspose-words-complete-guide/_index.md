---
category: general
date: 2026-02-26
description: Διαχειριστείτε τις ελλείπουσες γραμματοσειρές σε C# χρησιμοποιώντας το
  Aspose.Words. Μάθετε πώς να καταγράφετε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών,
  να υλοποιείτε το IWarningCallback και να διατηρείτε τα έγγραφά σας σωστά.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: el
og_description: Αντιμετωπίστε γρήγορα τα ελλείποντα γραμματοσειρά στο C#. Αυτός ο
  οδηγός δείχνει πώς να καταγράψετε προειδοποιήσεις αντικατάστασης γραμματοσειρών
  με το Aspose.Words, να υλοποιήσετε το IWarningCallback και να επαληθεύσετε τα αποτελέσματα.
og_title: Διαχείριση Ελλειπουσών Γραμματοσειρών σε C# – Βήμα‑βήμα Εγχειρίδιο Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Διαχείριση Ελλειπόντων Γραμματοσειρών σε C# με το Aspose.Words – Πλήρης Οδηγός
url: /el/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαχείριση Ελλειπόντων Γραμματοσειρών σε C# με Aspose.Words – Πλήρης Οδηγός

Έχετε χρειαστεί ποτέ να **διαχειριστείτε ελλείπουσες γραμματοσειρές** κατά τη φόρτωση ενός εγγράφου Word σε C# και να αναρωτηθήκατε γιατί το αποτέλεσμα φαίνεται παράξενο; Δεν είστε μόνοι. Όταν ένα αρχείο πηγής αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημα, το Aspose.Words αντικαθιστά σιωπηλά μια άλλη, κάτι που μπορεί να διαταράξει τη διάταξη ή το branding σας.

Τα καλά νέα; Με τη ρύθμιση ενός **warning callback**, μπορείτε να συλλάβετε κάθε συμβάν αντικατάστασης γραμματοσειράς, να το καταγράψετε και να αποφασίσετε αν θα παρέχετε μια αντικατάσταση. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — από τη ρύθμιση του έργου μέχρι την επαλήθευση της εξόδου της κονσόλας — ώστε να μην εκπλαγείτε ξανά από μια αόρατη γραμματοσειρά.

> **Τι θα λάβετε**: Μια έτοιμη‑για‑εκτέλεση C# κονσόλα εφαρμογή που αναφέρει κάθε ελλείπουσα γραμματοσειρά, εξηγεί γιατί εμφανίζεται η προειδοποίηση και σας δείχνει πώς να επεκτείνετε τον χειριστή για προσαρμοσμένη λογική.

---

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί τόσο σε .NET Core όσο και σε .NET Framework)
- Visual Studio 2022 (ή οποιοδήποτε IDE C# προτιμάτε)
- Μια **άδεια** για Aspose.Words for .NET (η δωρεάν δοκιμή λειτουργεί για δοκιμές)
- Ένα έγγραφο Word που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., *Comic Sans MS* σε Linux)

Αν τα έχετε αυτά, ας βουτήξουμε.

## Βήμα 1: Δημιουργήστε ένα Νέο Console Project και Προσθέστε το Aspose.Words

Για να διατηρήσετε τα πράγματα οργανωμένα, ξεκινήστε με ένα νέο console project.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Συμβουλή**: Χρησιμοποιήστε τη σημαία `--framework net6.0` αν θέλετε να στοχεύσετε ένα συγκεκριμένο runtime.

Αυτό κατεβάζει το πιο πρόσφατο πακέτο NuGet του Aspose.Words, το οποίο περιέχει τους τύπους `LoadOptions` και `IWarningCallback` που θα χρειαστούμε.

## Βήμα 2: Υλοποιήστε έναν Warning Handler (IWarningCallback)

Το Aspose.Words δημιουργεί ένα αντικείμενο `WarningInfo` για κάθε μη‑κριτική προβληματική κατάσταση που συναντά κατά τη φόρτωση ενός εγγράφου. Με την υλοποίηση του `IWarningCallback`, αποφασίζετε τι θα κάνετε με αυτές τις προειδοποιήσεις.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Γιατί είναι σημαντικό**: Χωρίς έναν χειριστή, οι προειδοποιήσεις αντικατάστασης γραμματοσειράς αγνοούνται σιωπηρά. Εκτυπώνοντάς τες, έχετε άμεση ορατότητα σε ποιες γραμματοσειρές λείπουν και τι χρησιμοποίησε το Aspose.Words αντί αυτού.

## Βήμα 3: Διαμορφώστε το LoadOptions με το Warning Callback

Τώρα συνδέουμε τον χειριστή στη διαδικασία φόρτωσης του εγγράφου. Το `LoadOptions` σας επιτρέπει να ενσωματώσετε το callback πριν το αρχείο αναλυθεί.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Σημείωση**: Αντικαταστήστε το `YOUR_DIRECTORY` με το πραγματικό φάκελο που περιέχει το δοκιμαστικό `.docx`. Η παρουσία του `LoadOptions` πρέπει να περάσει στον κατασκευαστή `Document`; διαφορετικά ενεργοποιείται η προεπιλεγμένη σιωπηρή συμπεριφορά.

## Βήμα 4: Εκτελέστε την Εφαρμογή και Επαληθεύστε την Έξοδο

Συγκεντρώστε (compile) και τρέξτε:

```bash
dotnet run
```

Αν το έγγραφο αναφέρει μια γραμματοσειρά που δεν υπάρχει στο σύστημά σας (π.χ., *Papyrus*), θα δείτε κάτι όπως:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Αυτή η μοναδική γραμμή σας λέει ακριβώς ποια γραμματοσειρά λείπει και ποιο fallback επέλεξε το Aspose.Words. Τώρα μπορείτε να αποφασίσετε να ενσωματώσετε τη λείπουσα γραμματοσειρά, να αλλάξετε το πηγαίο έγγραφο ή να αποδεχτείτε την αντικατάσταση.

## Βήμα 5: Προχωρημένο – Συλλογή Προειδοποιήσεων για Μεταγενέστερη Χρήση

Μερικές φορές θέλετε να αποθηκεύσετε τις προειδοποιήσεις αντί να τις εκτυπώνετε αμέσως. Παρακάτω υπάρχει μια γρήγορη τροποποίηση του χειριστή που συγκεντρώνει τα μηνύματα σε μια λίστα.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

Και ενημερώστε το `Main` αναλόγως:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Τώρα έχετε μια επαναχρησιμοποιήσιμη λίστα που μπορείτε να γράψετε σε αρχείο καταγραφής, να στείλετε σε υπηρεσία παρακολούθησης ή να εμφανίσετε σε UI.

## Βήμα 6: Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Δεν εμφανίζονται προειδοποιήσεις** | Το callback δεν συνδέθηκε, ή το έγγραφο φορτώθηκε χωρίς `LoadOptions`. | Βεβαιωθείτε ότι το `LoadOptions.WarningCallback` έχει οριστεί **πριν** καλέσετε τον κατασκευαστή `Document`. |
| **Λάθος όνομα γραμματοσειράς στο μήνυμα** | Κάποιες γραμματοσειρές είναι ενσωματωμένες στο έγγραφο· το Aspose.Words αναφέρει το *αρχικό* όνομα, όχι το ενσωματωμένο. | Επαληθεύστε τις αναφορές γραμματοσειρών του πηγαίου αρχείου· η ενσωμάτωση γραμματοσειρών εξαλείφει εντελώς την προειδοποίηση. |
| **Επίδραση στην απόδοση** | Η συλλογή προειδοποιήσεων για χιλιάδες έγγραφα μπορεί να προσθέσει επιπλέον φόρτο. | Χρησιμοποιήστε ένα απλό `Console.WriteLine` για γρήγορο debugging· μεταβείτε σε συλλέκτη μόνο όταν χρειάζεστε τα δεδομένα. |

## Οπτική Σύνοψη

![Εικονογράφηση διαχείρισης ελλειπόντων γραμματοσειρών που δείχνει τη ροή του warning callback](/images/handle-missing-fonts.png "Διάγραμμα της διαχείρισης ελλειπόντων γραμματοσειρών με το Aspose.Words")

*Το διάγραμμα (το alt text περιλαμβάνει τη βασική λέξη-κλειδί) οπτικοποιεί πώς το warning callback παρεμβάλλεται σε γεγονότα αντικατάστασης γραμματοσειράς κατά τη φόρτωση του εγγράφου.*

## Συμπέρασμα

Τώρα ξέρετε **πώς να διαχειρίζεστε ελλείπουσες γραμματοσειρές** σε C# χρησιμοποιώντας το Aspose.Words. Με την ενσωμάτωση ενός `IWarningCallback` στο `LoadOptions`, αποκτάτε πλήρη ορατότητα σε κάθε γεγονός αντικατάστασης γραμματοσειράς, μπορείτε να το καταγράψετε ή να ενεργήσετε, και τελικά να διασφαλίσετε ότι τα παραγόμενα έγγραφά σας διατηρούν την προγραμματισμένη εμφάνιση και αίσθηση.

> **Σύντομη ανακεφαλαίωση**:  
> 1. Προσθέστε το Aspose.Words σε μια console εφαρμογή.  
> 2. Υλοποιήστε το `FontWarningHandler` (ή έναν συλλέκτη).  
> 3. Περάστε το μέσω `LoadOptions` κατά τη φόρτωση του εγγράφου.  
> 4. Επαληθεύστε την έξοδο της κονσόλας ή τις αποθηκευμένες προειδοποιήσεις.  

Από εδώ μπορείτε να εξερευνήσετε **την ενσωμάτωση ελλειπόντων γραμματοσειρών** (`FontSettings.SubstitutionSettings`) ή **την αυτόματη λήψη τους από έναν εταιρικό διακομιστή γραμματοσειρών** — και τα δύο φυσικές επεκτάσεις του μοτίβου που μόλις δημιουργήσαμε.

Έχετε περισσότερες ερωτήσεις σχετικά με **προειδοποίηση γραμματοσειρών Aspose.Words**, **C# LoadOptions**, ή **φόρτωση εγγράφου με ελλείπουσες γραμματοσειρές**; Αφήστε ένα σχόλιο, και καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}