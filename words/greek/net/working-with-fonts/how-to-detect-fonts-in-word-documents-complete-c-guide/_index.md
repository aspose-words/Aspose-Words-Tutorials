---
category: general
date: 2026-02-24
description: Πώς να εντοπίσετε τις γραμματοσειρές σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να ορίσετε την κλήση επιστροφής και να φορτώσετε το
  έγγραφο Word με πλήρες παράδειγμα κώδικα.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: el
og_description: Πώς να εντοπίσετε γραμματοσειρές σε ένα έγγραφο Word χρησιμοποιώντας
  μια κλήση προειδοποίησης. Αυτός ο οδηγός δείχνει πώς να ορίσετε την κλήση προειδοποίησης
  και να φορτώσετε το έγγραφο Word με το Aspose.Words.
og_title: Πώς να ανιχνεύσετε γραμματοσειρές σε έγγραφα Word – Βήμα‑βήμα οδηγός C#
tags:
- C#
- Aspose.Words
- Document Processing
title: Πώς να ανιχνεύσετε γραμματοσειρές σε έγγραφα Word – Πλήρης οδηγός C#
url: /el/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ανιχνεύσετε γραμματοσειρές σε έγγραφα Word – Πλήρης οδηγός C#

Έχετε αναρωτηθεί ποτέ **πώς να ανιχνεύσετε γραμματοσειρές** που λείπουν όταν φορτώνετε ένα αρχείο Word; Ίσως έχετε συναντήσει ένα έγγραφο που φαίνεται εντάξει στον επεξεργαστή, αλλά το PDF που δημιουργείτε αντικαθιστά μερικές γραμματοσειρές στο παρασκήνιο. Αυτό είναι ένα κλασικό σύμπτωμα αντικατάστασης γραμματοσειράς, και η έγκαιρη ανίχνευσή του μπορεί να σας σώσει από δυσάρεστες εκπλήξεις διάταξης.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα μια πρακτική λύση: χρησιμοποιώντας το **Aspose.Words** για να φορτώσετε ένα `.docx`, να επισυνάψετε μια callback προειδοποίησης, και **πώς να ορίσετε callback** που αναφέρει κάθε αντικατάσταση γραμματοσειράς. Στο τέλος δεν θα γνωρίζετε μόνο **πώς να ανιχνεύσετε γραμματοσειρές** προγραμματιστικά, αλλά θα κατανοήσετε επίσης **πώς να ορίσετε callback** σωστά και **να φορτώσετε έγγραφο word** με ασφάλεια — όλα σε ένα ενιαίο, εκτελέσιμο παράδειγμα C#.

> **Τι θα λάβετε**
> * Ένα πλήρες, έτοιμο για αντιγραφή‑επικόλληση δείγμα κώδικα  
> * Εξήγηση βήμα‑βήμα για κάθε γραμμή  
> * Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως πολλαπλές ελλιπείς γραμματοσειρές ή προσαρμοσμένοι φάκελοι γραμματοσειρών  
> * Αναμενόμενη έξοδος κονσόλας ώστε να μπορείτε να επαληθεύσετε ότι όλα λειτουργούν

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Core)  
- Πακέτο NuGet Aspose.Words για .NET (`Install-Package Aspose.Words`)  
- Ένα αρχείο Word που σκόπιμα αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., `MissingFont.docx`)  
- Visual Studio, Rider ή οποιονδήποτε επεξεργαστή προτιμάτε  

Δεν χρειάζονται άλλες βιβλιοθήκες· όλα τα υπόλοιπα είναι μέρος του τυπικού .NET runtime.

## Πώς να ανιχνεύσετε γραμματοσειρές σε έγγραφο Word

### Βήμα 1: Δημιουργία Load Options και επισύναψη Warning Callback

Το πρώτο που κάνουμε είναι να πούμε στο Aspose.Words ότι θέλουμε να ειδοποιούμαστε για τυχόν προβλήματα που προκύπτουν κατά τη φόρτωση του αρχείου. Εδώ έρχεται σε παιχνίδι **πώς να ορίσετε callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Γιατί είναι σημαντικό:**  
`LoadOptions` είναι η πύλη για την προσαρμογή της διαδικασίας φόρτωσης. Αναθέτοντας μια παρουσία του `FontWarningCollector` στο `WarningCallback`, το Aspose.Words θα καλέσει τη μέθοδο `Warning` κάθε φορά που αντικαθιστά μια ελλιπή γραμματοσειρά με εναλλακτική. Αυτό είναι ο πυρήνας του **πώς να ανιχνεύσετε γραμματοσειρές** που δεν υπάρχουν στο σύστημα.

### Βήμα 2: Προετοιμασία του αντικειμένου LoadOptions

Τώρα δημιουργούμε ένα αντικείμενο `LoadOptions` και συνδέουμε το callback μας.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Συμβουλή:** Αν χρειάζεται να ελέγξετε *πού* το Aspose ψάχνει για γραμματοσειρές αντικατάστασης, μπορείτε επίσης να ορίσετε το `loadOptions.FontSettings` εδώ. Αυτό είναι χρήσιμο όταν έχετε έναν ιδιωτικό φάκελο γραμματοσειρών στον διακομιστή.

### Βήμα 3: Φόρτωση του εγγράφου Word

Με τις επιλογές έτοιμες, τελικά **φορτώνουμε το έγγραφο word**. Αυτή είναι η στιγμή που το Aspose αναλύει το DOCX και, αν λείπουν γραμματοσειρές, ενεργοποιείται το callback μας.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Τι συμβαίνει στο παρασκήνιο;**  
Το Aspose.Words διαβάζει τα XML τμήματα του DOCX, επιλύει κάθε αναφορά `<w:font>` και ελέγχει τη συλλογή γραμματοσειρών του συστήματος. Όταν μια αναφορά δεν μπορεί να ικανοποιηθεί, αντικαθιστά τη πρώτη ταιριαστή εναλλακτική γραμματοσειρά και δημιουργεί μια προειδοποίηση `FontSubstitution`.

### Βήμα 4: Επαλήθευση της εξόδου

Εκτελέστε το πρόγραμμα και παρακολουθήστε την κονσόλα. Για κάθε ελλιπή γραμματοσειρά θα δείτε μια γραμμή όπως:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Αν το έγγραφο δεν περιέχει ελλιπείς γραμματοσειρές, η κονσόλα παραμένει σιωπηλή — σημαίνει ότι το **πώς να ανιχνεύσετε γραμματοσειρές** δεν επέστρεψε αποτελέσματα.

### Βήμα 5: Πλήρες λειτουργικό παράδειγμα (Console App)

Παρακάτω υπάρχει ένα αυτόνομο `Program.cs` που μπορείτε να προσθέσετε σε ένα νέο έργο console. Περιλαμβάνει όλα τα στοιχεία που συζητήσαμε, καθώς και έναν μικρό βοηθό για να κρατά το παράθυρο της κονσόλας ανοιχτό κατά το debugging.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Αναμενόμενη έξοδος κονσόλας** (παράδειγμα):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Αν αντικαταστήσετε το `MissingFont.docx` με ένα αρχείο που χρησιμοποιεί μόνο εγκατεστημένες γραμματοσειρές, θα δείτε μόνο τη γραμμή «Press any key…» — επιβεβαιώνοντας ότι η λογική ανίχνευσης λειτουργεί όπως προβλέπεται.

## Συχνές Ερωτήσεις & Ειδικές Περιπτώσεις

### Τι γίνεται αν χρειάζεται να συλλάβω *όλες* τις προειδοποιήσεις, όχι μόνο την αντικατάσταση γραμματοσειράς;

Απλώς αφαιρέστε την προστασία `if (info.Type == WarningType.FontSubstitution)`. Το αντικείμενο `WarningInfo` περιέχει ένα enum `Type` που μπορείτε να ελέγξετε για άλλες περιπτώσεις (π.χ., `DocumentStructure`, `ImageLoading`).

### Μπορώ να καταγράψω τις προειδοποιήσεις σε αρχείο αντί για την κονσόλα;

Απολύτως. Αντικαταστήστε το `Console.WriteLine` με οποιαδήποτε κλήση πλαισίου καταγραφής (`Serilog`, `NLog`, κλπ.). Το callback εκτελείται στο ίδιο νήμα που φορτώνει το έγγραφο, οπότε βεβαιωθείτε ότι ο καταγραφέας σας είναι thread‑safe.

### Πώς συμπεριφέρεται αυτό σε μια web εφαρμογή;

Σε ASP.NET Core συνήθως θα ενσωματώσετε μια υλοποίηση `IWarningCallback` ως singleton και θα τη περάσετε μέσω `LoadOptions`. Θυμηθείτε να αποφεύγετε την άμεση εγγραφή στο ρεύμα απόκρισης — καταγράψτε σε βάση δεδομένων ή σε συλλογή στη μνήμη που μπορείτε αργότερα να εκθέσετε μέσω ενός API endpoint.

### Τι γίνεται με προσαρμοσμένες γραμματοσειρές που αποθηκεύονται σε φάκελο εκτός του συστήματος;

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Τώρα το Aspose.Words θα ψάξει στο `C:\MyCustomFonts` πριν καταφύγει στις γραμματοσειρές του λειτουργικού συστήματος, μειώνοντας τον αριθμό των προειδοποιήσεων αντικατάστασης που βλέπετε.

## Οπτική Σύνοψη

![Ανίχνευση προειδοποίησης γραμματοσειρών μέσω callback στο Aspose.Words](/images/font-warning-callback.png "Πώς να ανιχνεύσετε γραμματοσειρές χρησιμοποιώντας μια callback προειδοποίησης")

*Η λήψη οθόνης δείχνει την έξοδο της κονσόλας όταν αντικαθίσταται μια ελλιπής γραμματοσειρά. Το κείμενο alt περιέχει τη βασική λέξη-κλειδί για SEO.*

## Συμπέρασμα

Τώρα έχετε ένα σταθερό, έτοιμο για παραγωγή μοτίβο για **πώς να ανιχνεύσετε γραμματοσειρές** σε οποιοδήποτε αρχείο Word φορτώνετε με το Aspose.Words. Με το **πώς να ορίσετε callback** αποκτάτε άμεση εικόνα για τις ελλιπείς ή αντικατεστημένες γραμματοσειρές, και έχετε μάθει τον σωστό τρόπο να **φορτώνετε έγγραφο word** διατηρώντας τον κώδικά σας καθαρό και συντηρήσιμο.

Επόμενα βήματα; Δοκιμάστε να επεκτείνετε το callback ώστε να συλλέγει τις προειδοποιήσεις σε μια λίστα, και στη συνέχεια να τις εμφανίζει σε UI ή σε αυτοματοποιημένη αναφορά. Μπορείτε επίσης να εξερευνήσετε το `FontSettings.SubstitutionSettings` για να ελέγξετε *ποιες* γραμματοσειρές θα επιλεγούν ως εναλλακτικές.

Μη διστάσετε να πειραματιστείτε — αντικαταστήστε το έγγραφο, προσθέστε περισσότερες ελλιπείς γραμματοσειρές ή ενσωματώστε τη λογική σε μια μεγαλύτερη αλυσίδα επεξεργασίας εγγράφων. Αν αντιμετωπίσετε προβλήματα, αφήστε ένα σχόλιο παρακάτω ή στείλτε μου μήνυμα στο GitHub.

Καλό προγραμματισμό, και εύχομαι τα έγγραφά σας να εμφανίζονται πάντα με τις γραμματοσειρές που περιμένετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}