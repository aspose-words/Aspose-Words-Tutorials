---
category: general
date: 2026-02-28
description: Μάθετε πώς να διαχειρίζεστε τις προειδοποιήσεις γραμματοσειρών και να
  εντοπίζετε τις ελλείπουσες γραμματοσειρές στο Aspose.Words χρησιμοποιώντας C#. Πλήρης
  οδηγός βήμα‑βήμα με ολοκληρωμένο κώδικα.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: el
og_description: Διαχειριστείτε τις προειδοποιήσεις γραμματοσειρών στο Aspose.Words
  και εντοπίστε τις ελλιπείς γραμματοσειρές με ένα έτοιμο παράδειγμα C#. Ακολουθήστε
  τα βήματα και δείτε το αποτέλεσμα.
og_title: Διαχείριση προειδοποιήσεων γραμματοσειρών στο Aspose.Words – Πλήρης οδηγός
tags:
- Aspose.Words
- C#
- Document Loading
title: Διαχείριση προειδοποιήσεων γραμματοσειρών στο Aspose.Words – Ανίχνευση ελλιπών
  γραμματοσειρών
url: /el/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαχείριση Προειδοποιήσεων Γραμματοσειρών στο Aspose.Words – Ανίχνευση Ελλειπούσας Γραμματοσειράς

Έχετε ποτέ χρειαστεί να **διαχειριστείτε προειδοποιήσεις γραμματοσειρών** κατά τη φόρτωση ενός εγγράφου Word και να αναρωτηθήκατε γιατί κάποιο κείμενο φαίνεται παράξενο; Δεν είστε μόνοι. Οι ελλειπούσες γραμματοσειρές προκαλούν προειδοποιήσεις αντικατάστασης που μπορούν σιωπηρά να διαφθοράσουν τη οπτική διάταξη, και αν δεν **ανιχνεύσετε ελλειπούσες γραμματοσειρές** δεν θα ξέρετε ποτέ τι πήγε στραβά.

Σε αυτό το tutorial θα σας δείξουμε έναν πρακτικό τρόπο να **διαχειριστείτε προειδοποιήσεις γραμματοσειρών** χρησιμοποιώντας το `IWarningCallback` του Aspose.Words. Στο τέλος του οδηγού θα μπορείτε να εντοπίζετε κάθε συμβάν αντικατάστασης γραμματοσειράς, να το καταγράφετε και ακόμη να αποφασίζετε αν θα ακυρώσετε τη φόρτωση. Χωρίς εξωτερικά έγγραφα, μόνο ένα παράδειγμα έτοιμο για αντιγραφή‑επικόλληση.

## Τι Θα Μάθετε

- Ρύθμιση ενός προσαρμοσμένου χειριστή προειδοποιήσεων που αντιδρά μόνο σε ειδοποιήσεις αντικατάστασης γραμματοσειράς.  
- Σύνδεση του χειριστή με το `LoadOptions` ώστε κάθε φόρτωση εγγράφου να περνά από αυτόν.  
- Επαλήθευση της εξόδου στην κονσόλα και κατανόηση του τι σημαίνει κάθε προειδοποίηση.  

**Προαπαιτούμενα**

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).  
- Aspose.Words for .NET εγκατεστημένο μέσω NuGet (`Install-Package Aspose.Words`).  
- Ένα αρχείο Word που αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον υπολογιστή σας (π.χ., μια προσαρμοσμένη εταιρική γραμματοσειρά).  

Αν λείπει κάποιο από τα παραπάνω, αποκτήστε το τώρα—διαφορετικά, ας ξεκινήσουμε.

## Πώς να Διαχειριστείτε Προειδοποιήσεις Γραμματοσειρών στο Aspose.Words

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα. Περιλαμβάνει όλα, από τις δηλώσεις `using` μέχρι τη μέθοδο `Main`, ώστε να το τοποθετήσετε σε μια εφαρμογή console και να πατήσετε **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Αναμενόμενη έξοδος κονσόλας** (υπόθεση ότι το έγγραφο χρησιμοποιεί μια γραμματοσειρά που δεν έχετε εγκατεστημένη):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Αν το έγγραφο δεν περιέχει **ελλειπούσες γραμματοσειρές**, η γραμμή προειδοποίησης δεν εμφανίζεται ποτέ—έτσι έχετε **ανιχνεύσει ελλειπούσες γραμματοσειρές** μόνο όταν χρειάζεται.

### Γιατί Λειτουργεί Αυτό

Το Aspose.Words εκδίδει ένα `WarningInfo` για κάθε μη‑κριτική προβληματική κατάσταση που συναντά κατά την ανάλυση ενός αρχείου. Υλοποιώντας το `IWarningCallback` αποκτάτε ένα hook σε αυτή τη διαδικασία. Η σημαία `WarningType.FontSubstitution` σας λέει ακριβώς πότε η βιβλιοθήκη έπρεπε να αντικαταστήσει τη ζητούμενη γραμματοσειρά με μια εναλλακτική. Αυτός είναι ο πιο αξιόπιστος τρόπος να **διαχειριστείτε προειδοποιήσεις γραμματοσειρών**, επειδή εκτελείται *κατά τη διάρκεια* της φόρτωσης, πριν καν αγγίξετε το μοντέλο αντικειμένων του εγγράφου.

## Ανίχνευση Ελλειπούσας Γραμματοσειράς Χωρίς να Διακόψετε την Εφαρμογή Σας

Μερικές φορές μπορεί να θέλετε να θεωρήσετε μια ελλειπούσα γραμματοσειρά ως μοιραίο σφάλμα—ίσως οι οδηγίες branding σας απαγορεύουν οποιαδήποτε αντικατάσταση. Μπορείτε να τροποποιήσετε τον χειριστή ώστε να ρίχνει εξαίρεση αντί για απλή καταγραφή:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Τώρα το μπλοκ `try…catch` γύρω από το `new Document(...)` θα συλλάβει το πρόβλημα, επιτρέποντάς σας να αποφασίσετε αν θα ακυρώσετε, θα κάνετε fallback ή θα προτρέψετε τον χρήστη.

## Bonus: Οπτικοποίηση Προειδοποιήσεων σε Εφαρμογή UI

Αν δημιουργείτε μια εφαρμογή WinForms ή WPF, αντικαταστήστε το `Console.WriteLine` με μια κλήση φιλική προς το UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Με αυτόν τον τρόπο, οι τελικοί χρήστες βλέπουν τη προειδοποίηση αμέσως, και εσείς συνεχίζετε να **διαχειρίζεστε προειδοποιήσεις γραμματοσειρών** με συνέπεια σε όλες τις πλατφόρμες.

## Συνηθισμένα Πιθανά Σφάλματα & Pro Tips

- **Πιθανό σφάλμα:** Ξέχνατε να ορίσετε το `WarningCallback`. Η προεπιλεγμένη συμπεριφορά είναι να αγνοεί τις προειδοποιήσεις γραμματοσειρών, οπότε δεν θα τις δείτε ποτέ.  
  **Pro tip:** Δημιουργείτε πάντα ένα αντικείμενο `LoadOptions` ακόμη και αν χρειάζεστε μόνο τον χειριστή προειδοποιήσεων. Είναι φθηνό και σαφές.  

- **Πιθανό σφάλμα:** Χρήση λανθασμένου διαχωριστικού διαδρομής σε μη‑Windows OS.  
  **Pro tip:** Χρησιμοποιήστε `Path.Combine` ή ένα raw string literal (`@"C:\Docs\MissingFont.docx"` λειτουργεί στα Windows· σε Linux χρησιμοποιήστε `"/home/user/docs/MissingFont.docx"`).  

- **Πιθανό σφάλμα:** Υπόθεση ότι η προειδοποίηση θα ενεργοποιηθεί για ενσωματωμένες γραμματοσειρές.  
  **Pro tip:** Οι ενσωματωμένες γραμματοσειρές θεωρούνται παρούσες, επομένως δεν εμφανίζεται προειδοποίηση αντικατάστασης. Δοκιμάστε με πραγματικά *ελλειπούσες* γραμματοσειρές για να δείτε τον χειριστή σε δράση.  

- **Πιθανό σφάλμα:** Υπερβολική καταγραφή κάθε τύπου προειδοποίησης.  
  **Pro tip:** Φιλτράρετε με `WarningType.FontSubstitution` όπως φαίνεται—αυτό κρατά την κονσόλα καθαρή και εστιάζει στο σενάριο **ανίχνευσης ελλειπούσας γραμματοσειράς**.  

## Ανακεφαλαίωση Πλήρους Παραδείγματος Εργασίας

Εδώ είναι ξανά ολόκληρο το πρόγραμμα, αυτή τη φορά χωρίς σχόλια για όσους προτιμούν μια καθαρή προβολή:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Αντιγράψτε, επικολλήστε, τρέξτε—η κονσόλα σας θα **διαχειρίζεται προειδοποιήσεις γραμματοσειρών** και θα **ανιχνεύει ελλειπούσες γραμματοσειρές** αυτόματα.

## Επόμενα Βήματα

- **Καταγραφή σε αρχείο:** Αντικαταστήστε το `Console.WriteLine` με έναν logger (π.χ., NLog) για tracing επιπέδου παραγωγής.  
- **Επεξεργασία σε παρτίδες:** Περάστε σε βρόχο έναν φάκελο εγγράφων, συλλέγοντας όλα τα συμβάντα αντικατάστασης γραμματοσειράς σε μια αναφορά CSV.  
- **Αυτόματη εγκατάσταση γραμματοσειρών:** Συνδέστε τον χειριστή προειδοποιήσεων για να κατεβάζει ελλειπούσες γραμματοσειρές από ένα εταιρικό αποθετήριο πριν συνεχιστεί η φόρτωση.  

Κάθε μία από αυτές τις επεκτάσεις βασίζεται στην κεντρική ιδέα της **διαχείρισης προειδοποιήσεων γραμματοσειρών** με καθαρό, επαναχρησιμοποιήσιμο τρόπο.

---

*Καλή προγραμματιστική! Αν αντιμετωπίσετε οποιεσδήποτε ιδιομορφίες ενώ προσπαθείτε να **ανιχνεύσετε ελλειπούσες γραμματοσειρές**, αφήστε ένα σχόλιο παρακάτω. Θα χαρώ να σας βοηθήσω με την αντιμετώπιση προβλημάτων.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}