---
category: general
date: 2026-01-14
description: Καταγράψτε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών κατά τη
  φόρτωση εγγράφων Word με το Aspose.Words. Μάθετε πώς να ανιχνεύετε τις ελλείπουσες
  γραμματοσειρές και πώς να τις καταγράφετε σε C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: el
og_description: Καταγράψτε προειδοποιήσεις αντικατάστασης γραμματοσειρών κατά τη φόρτωση
  εγγράφων Word με το Aspose.Words. Ανακαλύψτε πώς να εντοπίζετε ελλείπουσες γραμματοσειρές
  και να τις καταγράφετε σε C#.
og_title: Προειδοποιήσεις Υποκατάστασης Γραμματοσειρών Καταγραφής – Πλήρης Οδηγός
  Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών – Πλήρης Οδηγός Aspose.Words
url: /el/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς – Πλήρης Οδηγός Aspose.Words

Η καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειρών είναι απαραίτητη όταν πρέπει να διασφαλίσετε ότι ένα έγγραφο Word φαίνεται ακριβώς το ίδιο μετά τη φόρτωσή του από το Aspose.Words. Αν ποτέ αναρωτηθήκατε πώς να **ανιχνεύσετε ελλιπείς γραμματοσειρές** ή θέλετε να μάθετε **πώς να καταγράψετε ελλιπείς γραμματοσειρές**, βρίσκεστε στο σωστό μέρος.  

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό σενάριο, θα σας δείξουμε τον πλήρη κώδικα C# και θα εξηγήσουμε γιατί κάθε γραμμή είναι σημαντική. Στο τέλος θα μπορείτε να καταγράφετε κάθε συμβάν αντικατάστασης γραμματοσειράς και να ενεργείτε ανάλογα — χωρίς μυστικές προειδοποιήσεις.

![Παράδειγμα καταγραφής προειδοποιήσεων αντικατάστασης γραμματοσειράς](/images/font-warnings.png "Στιγμιότυπο οθόνης που δείχνει την έξοδο της κονσόλας για την καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειράς")

## Τι Θα Μάθετε

- Πώς να διαμορφώσετε το `LoadOptions` ώστε το Aspose.Words να δημιουργεί προειδοποιήσεις τύπου για την αντικατάσταση γραμματοσειράς.  
- Τα ακριβή βήματα για **ανίχνευση ελλιπών γραμματοσειρών** κατά τη φόρτωση του εγγράφου.  
- Ένας καθαρός τρόπος για **καταγραφή ελλιπών γραμματοσειρών** και την εγγραφή τους στο δικό σας αρχείο καταγραφής ή σύστημα παρακολούθησης.  
- Διαχείριση ακραίων περιπτώσεων (π.χ., όταν ένα έγγραφο περιέχει γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή).  

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).  
- Έγκυρη άδεια Aspose.Words for .NET (ή η δωρεάν δοκιμή).  
- Βασική εξοικείωση με C# και εφαρμογές κονσόλας.  

Αν τα έχετε ήδη, ας ξεκινήσουμε.

## Βήμα 1 – Ρύθμιση LoadOptions για Ανάδειξη Προειδοποιήσεων Τύπου

Η καρδιά της λύσης βρίσκεται στο `LoadOptions.FontSubstitutionWarning`. Με την αλλαγή του σε `RaiseTypedWarnings` λέτε στο Aspose.Words να ενεργοποιεί ένα γεγονός **κάθε φορά** που δεν μπορεί να βρει την ακριβή γραμματοσειρά που ζητήσατε.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Γιατί αυτό είναι σημαντικό:**  
> Η προεπιλεγμένη συμπεριφορά αντικαθιστά σιωπηλά μια ελλιπή γραμματοσειρά με την πιο κοντινή αντιστοιχία, κάτι που μπορεί να προκαλέσει προβλήματα διάταξης που δεν προβλέπετε. Η ενεργοποίηση προειδοποιήσεων τύπου σας δίνει πλήρη διαφάνεια.

## Βήμα 2 – Εγγραφή στο Γεγονός Προειδοποίησης

Τώρα συνδέουμε στο `loadOptions.FontSubstitutionWarning`. Η λήψη (lambda) λαμβάνει ένα αντικείμενο `e` που μας λέει ακριβώς ποια γραμματοσειρά λείπει και ποια χρησιμοποιήθηκε αντί αυτής.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** Αν τρέχετε αυτόν τον κώδικα σε web server, αντικαταστήστε το `Console.WriteLine` με έναν δομημένο logger (Serilog, NLog, κ.λπ.) ώστε να μπορείτε να ερωτήσετε τα δεδομένα αργότερα.

## Βήμα 3 – Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Με τον μηχανισμό προειδοποίησης σε θέση, απλώς φορτώστε το έγγραφο όπως θα κάνατε κανονικά. Το γεγονός ενεργοποιείται αυτόματα για κάθε ελλιπή γραμματοσειρά.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Αναμενόμενη Έξοδος Κονσόλας

Αν το `input.docx` αναφέρει μια γραμματοσειρά που ονομάζεται *MyFancyFont* και δεν είναι εγκατεστημένη, θα δείτε:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Κάθε γραμμή αντιστοιχεί σε ένα γεγονός **ανίχνευσης ελλιπών γραμματοσειρών**, παρέχοντάς σας πλήρη καταγραφή.

## Βήμα 4 – Διαχείριση Ακραίων Περιπτώσεων και Προχωρημένων Σεναρίων

### 4.1 Όταν Δεν Συμβαίνει Αντικατάσταση

Μερικές φορές ένα έγγραφο χρησιμοποιεί μόνο σύστημα γραμματοσειρών που είναι ήδη παρούσες. Σε αυτήν την περίπτωση το γεγονός προειδοποίησης δεν ενεργοποιείται ποτέ, και θα έχετε μια καθαρή κονσόλα χωρίς έξοδο. Αυτό είναι καλό σημάδι — το περιβάλλον σας έχει ήδη όλες τις απαιτούμενες γραμματοσειρές.

### 4.2 Καταγραφή Προειδοποιήσεων για Μεταγενέστερη Ανάλυση

Αν χρειάζεται να αποθηκεύσετε τις προειδοποιήσεις για μια νυχτερινή αναφορά, συγκεντρώστε τις σε μια λίστα:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Μετά τη φόρτωση, μπορείτε να μετατρέψετε το `missingFonts` σε JSON, να το γράψετε σε βάση δεδομένων ή να στείλετε σύνοψη μέσω email.

### 4.3 Εργασία με PDF ή Άλλα Μορφότυπα

Η ίδια προσέγγιση `LoadOptions` λειτουργεί για κλήσεις `Load` σε PDF, RTF και ακόμη και HTML αρχεία. Απλώς περάστε το ίδιο αντικείμενο επιλογών, και το Aspose.Words θα δημιουργεί προειδοποιήσεις για κάθε γραμματοσειρά που δεν μπορεί να ταιριάξει.

## Βήμα 5 – Επαλήθευση του Αποτελέσματος Προγραμματιστικά

Αν προτιμάτε ένα αυτοματοποιημένο τεστ αντί της οπτικής επιθεώρησης της κονσόλας, ελέγξτε ότι η λίστα περιέχει τις αναμενόμενες εγγραφές:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Αυτό το απόσπασμα δείχνει **πώς να καταγράψετε ελλιπείς γραμματοσειρές** στον κώδικα, όχι μόνο στα αρχεία καταγραφής.

## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| Ξεχάνοντας να ορίσετε `RaiseTypedWarnings` | Η προεπιλογή είναι `DoNotRaise`, οπότε δεν ενεργοποιούνται γεγονότα. | Ορίστε ρητά το `FontSubstitutionWarning` όπως φαίνεται στο Βήμα 1. |
| Χρήση του `Console.WriteLine` σε web εφαρμογή | Η έξοδος της κονσόλας εξαφανίζεται σε IIS/ASP.NET Core. | Αλλάξτε σε έναν μόνιμο logger (π.χ., Serilog). |
| Φόρτωση εγγράφου με σχετική διαδρομή | Ο τρέχων φάκελος μπορεί να διαφέρει κατά την εκτέλεση. | Χρησιμοποιήστε απόλυτες διαδρομές ή `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Αγνοώντας το `SubstitutedFontName` | Χάνετε πληροφορίες για το ποια εναλλακτική γραμματοσειρά επιλέχθηκε. | Πάντα να καταγράφετε τόσο το `FontName` όσο και το `SubstitutedFontName`. |

## Bonus: Αυτοματοποίηση Εγκατάστασης Γραμματοσειρών

Αν ελέγχετε το περιβάλλον ανάπτυξης, μπορείτε να προ‑εγκαταστήσετε τις ελλιπείς γραμματοσειρές χρησιμοποιώντας ένα PowerShell script:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Η εκτέλεση αυτού πριν ξεκινήσει η εφαρμογή σας εξαλείφει τις περισσότερες προειδοποιήσεις **ανίχνευσης ελλιπών γραμματοσειρών** εντελώς.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **καταγράψετε προειδοποιήσεις αντικατάστασης γραμματοσειράς** κατά τη φόρτωση εγγράφων Word με το Aspose.Words. Με τη διαμόρφωση του `LoadOptions`, την εγγραφή στο γεγονός προειδοποίησης και, προαιρετικά, την αποθήκευση των αποτελεσμάτων, μπορείτε αξιόπιστα να **ανιχνεύσετε ελλιπείς γραμματοσειρές** και να καταλάβετε **πώς να καταγράψετε ελλιπείς γραμματοσειρές** για οποιοδήποτε .NET project.

Πάρτε τον κώδικα, προσαρμόστε τον logger ώστε να ταιριάζει στο stack σας, και δεν θα εκπλαγείτε ξανά από μια σιωπηλή αντικατάσταση γραμματοσειράς. Τα επόμενα βήματα μπορεί να περιλαμβάνουν:

- Ενσωμάτωση της λίστας προειδοποιήσεων στο CI/CD pipeline σας για να αποτυγχάνουν τα builds όταν λείπουν κρίσιμες γραμματοσειρές.  
- Επέκταση της προσέγγισης για παρακολούθηση της χρήσης γραμματοσειρών σε ένα σύνολο εγγράφων.  
- Εξερεύνηση του API `FontSettings` του Aspose.Words για παροχή προσαρμοσμένων εναλλακτικών γραμματοσειρών.

Έχετε ερωτήσεις ή ένα δύσκολο σενάριο; Αφήστε ένα σχόλιο και ας το λύσουμε μαζί. Καλό coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}