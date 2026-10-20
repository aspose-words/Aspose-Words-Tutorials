---
category: general
date: 2026-06-02
description: πώς να διαχειρίζεστε τις γραμματοσειρές στο .NET – ανιχνεύστε τις ελλιπείς
  γραμματοσειρές και παρακολουθήστε τις αλλαγές γραμματοσειρών χρησιμοποιώντας LoadOptions
  και FontSettings. Μάθετε μια πλήρη, εκτελέσιμη λύση.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: el
og_description: πώς να διαχειριστείτε τις γραμματοσειρές στο .NET – εντοπίστε τις
  ελλιπείς γραμματοσειρές και παρακολουθήστε τις αλλαγές γραμματοσειρών. Ακολουθήστε
  αυτόν τον οδηγό βήμα‑βήμα για μια πλήρη, έτοιμη για εκτέλεση λύση.
og_title: πώς να διαχειριστείτε τις γραμματοσειρές στο .NET – εντοπίστε τις ελλείπουσες
  γραμματοσειρές
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: πώς να διαχειριστείτε τις γραμματοσειρές στο .NET – εντοπισμός ελλιπών γραμματοσειρών
url: /el/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να διαχειριστείτε τις γραμματοσειρές σε .NET – ανίχνευση ελλιπών γραμματοσειρών

Έχετε αναρωτηθεί **πώς να διαχειριστείτε τις γραμματοσειρές** όταν ένα έγγραφο Word αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο μηχάνημα; Δεν είστε οι μόνοι. Οι ελλιπείς γραμματοσειρές μπορούν να μετατρέψουν μια καλοσχεδιασμένη αναφορά σε ακατάστατο χάος, και χωρίς κατάλληλες προειδοποιήσεις μπορεί να μην καταλάβετε ποτέ τι αντικαταστάθηκε.

Σε αυτό το tutorial θα σας δείξουμε ακριβώς **πώς να διαχειριστείτε τις γραμματοσειρές** ανιχνεύοντας ελλιπείς γραμματοσειρές **και** παρακολουθώντας τις αλλαγές γραμματοσειρών σε χρόνο εκτέλεσης. Στο τέλος θα έχετε μια αυτόνομη εφαρμογή console που καταγράφει κάθε αντικατάσταση, ώστε να μην εκπλαγείτε ποτέ από ένα μυστηριώδες Helvetica που εμφανίζεται εκεί που θα έπρεπε να είναι Times New Roman.

> **Τι θα πάρετε:** ένα πλήρες, έτοιμο για αντιγραφή‑επικόλληση δείγμα κώδικα, εξήγηση κάθε γραμμής, συμβουλές για πραγματικά έργα, και μια γρήγορη ματιά σε edge‑cases που μπορεί να συναντήσετε.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το δείγμα χρησιμοποιεί ένα top‑level `Program.cs` για συντομία)  
- Aspose.Words for .NET 23.9 ή νεότερο – μπορείτε να το προσθέσετε από το NuGet με `dotnet add package Aspose.Words`  
- Ένα έγγραφο Word που σκόπιμα αναφέρει μια γραμματοσειρά που δεν έχετε (π.χ., `MissingFont.docx`)  

Δεν απαιτούνται άλλες βιβλιοθήκες.

![Διάγραμμα που δείχνει πώς το LoadOptions ρέει στο FontSettings και το συμβάν προειδοποίησης αντικατάστασης – παράδειγμα πώς να διαχειριστείτε τις γραμματοσειρές σε .NET](https://example.com/images/font‑handling‑flow.png "πώς να διαχειριστείτε τις γραμματοσειρές σε .NET παράδειγμα")

## Βήμα 1: Ρύθμιση LoadOptions με FontSettings  

Το πρώτο που χρειάζεται είναι ένα αντικείμενο `LoadOptions` που λέει στο Aspose.Words να παρακολουθεί προβλήματα γραμματοσειρών.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Γιατί είναι σημαντικό:** Το `LoadOptions` είναι ο φάλαγγος όταν ένα έγγραφο διαβάζεται από το δίσκο. Παρέχοντας ένα προσαρμοσμένο `FontSettings` κερδίζουμε ένα hook στον εσωτερικό μηχανισμό επίλυσης γραμματοσειρών, που είναι ο μοναδικός τρόπος για **να ανιχνεύσετε ελλιπείς γραμματοσειρές** πριν το έγγραφο αποδοθεί.

## Βήμα 2: Εγγραφή στο συμβάν SubstitutionWarning  

Το Aspose.Words εκκινεί ένα συμβάν `SubstitutionWarning` κάθε φορά που δεν μπορεί να βρει την ακριβή γραμματοσειρά που ζητήσατε. Θα καταγράψουμε τις λεπτομέρειες ώστε να βλέπετε ποιες γραμματοσειρές ζητήθηκαν και ποιες χρησιμοποιήθηκαν πραγματικά.

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Γιατί το ακούουμε:** Χωρίς αυτόν τον ακροατή δεν θα γνωρίζετε ποτέ ότι έγινε αντικατάσταση. Το συμβάν σας δίνει ένα πλήρες ιστορικό ελέγχου, ικανοποιώντας την απαίτηση «παρακολούθηση αλλαγών γραμματοσειρών».

## Βήμα 3: Φόρτωση του Εγγράφου με τις Διαμορφωμένες Επιλογές  

Τώρα διαβάζουμε πραγματικά το αρχείο. Επειδή περάσαμε το `loadOptions`, το Aspose.Words θα ενεργοποιήσει το συμβάν προειδοποίησης για κάθε ελλιπή γραμματοσειρά που συναντήσει.

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

Αυτό ήταν – το έγγραφο είναι πλέον φορτωμένο, και τυχόν προβλήματα γραμματοσειρών έχουν ήδη εκτυπωθεί στην κονσόλα.

## Βήμα 4: (Προαιρετικό) Επαλήθευση των Αντικατεστημένων Γραμματοσειρών στο Έγγραφο  

Αν θέλετε να ελέγξετε ξανά ποιες γραμματοσειρές βρέθηκαν στο τελικό PDF ή DOCX, μπορείτε να περάσετε τη συλλογή γραμματοσειρών του εγγράφου:

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Η εκτέλεση αυτού μετά τη φόρτωση θα καταγράψει κάθε γραμματοσειρά που η μηχανή αποφάσισε να ενσωματώσει ή να αναφέρει. Χρήσιμο όταν χρειάζεται να δημιουργήσετε μια αναφορά για τις ομάδες QA.

## Πλήρες Παράδειγμα Λειτουργίας  

Αντιγράψτε το παρακάτω μπλοκ σε ένα νέο έργο console (`dotnet new console`) και τρέξτε το. Το πρόγραμμα θα εμφανίσει κάθε αντικατάσταση και στη συνέχεια θα απαριθμήσει τις γραμματοσειρές που επιβίωσαν τη φόρτωση.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Αναμενόμενη Έξοδος  

Αν το `MissingFont.docx` ζητάει *“Comic Sans MS”* (που δεν είναι εγκατεστημένο) θα δείτε κάτι όπως:

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

Η πρώτη γραμμή αποδεικνύει ότι **ανιχνεύουμε ελλιπείς γραμματοσειρές** και **παρακολουθούμε αλλαγές γραμματοσειρών**. Η δεύτερη γραμμή δείχνει μια αντικατάσταση που δεν χρειαζόταν (χωρίς προειδοποίηση, επειδή η γραμματοσειρά υπήρχε).

## Συνηθισμένα Πιθανά Προβλήματα & Επαγγελματικές Συμβουλές  

| Πρόβλημα | Τι Συμβαίνει | Πώς να Διορθώσετε / Αποφύγετε |
|----------|--------------|------------------------------|
| **Δεν ενεργοποιούνται συμβάντα προειδοποίησης** | Μπορεί να νομίζετε ότι το API είναι σπασμένο. | Βεβαιωθείτε ότι *αναθέτε* το `FontSettings` στο `LoadOptions` **πριν** τη φόρτωση του εγγράφου. Το hook του συμβάντος πρέπει να προσαρτηθεί **πριν** την κλήση `new Document(...)`. |
| **Οι αντικατεστημένες γραμματοσειρές εξακολουθούν να φαίνονται λανθασμένες** | Το Aspose.Words επιστρέφει μια γενική γραμματοσειρά που δεν ταιριάζει στο στυλ. | Παρέχετε έναν προσαρμοσμένο φάκελο γραμματοσειρών μέσω `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. Αυτό δίνει στη μηχανή περισσότερες επιλογές πριν προεπιλέξει μια γενική γραμματοσειρά. |
| **Πτώση απόδοσης σε μεγάλα έγγραφα** | Η σάρωση κάθε γραμματοσειράς μπορεί να προσθέσει μερικά χιλιοστά του δευτερολέπτου. | Κρατήστε στην μνήμη το αντικείμενο `FontSettings` αν φορτώνετε πολλά έγγραφα διαδοχικά. Η επαναχρησιμοποίηση της ίδιας παρουσίας αποφεύγει την επανάληψη ανάγνωσης των πινάκων γραμματοσειρών του συστήματος. |
| **Η έξοδος της κονσόλας χάθηκε σε εφαρμογές GUI** | Δεν θα δείτε τις προειδοποιήσεις. | Ανακατευθύνετε το συμβάν σε έναν logger (π.χ., `Serilog`) ή γράψτε σε αρχείο: `File.AppendAllText("font-warnings.log", …)`. |

## Επέκταση της Λύσης  

- **Εξαγωγή σε PDF με ενσωματωμένες γραμματοσειρές** – μετά τη φόρτωση, καλέστε `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` και βεβαιωθείτε ότι ορίζετε `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Επεξεργασία σε παρτίδες** – τυλίξτε τη λογική φόρτωσης μέσα σε ένα `foreach` πάνω από έναν φάκελο αρχείων DOCX. Καταγράψτε τις προειδοποιήσεις κάθε αρχείου σε CSV για σκοπούς ελέγχου.  
- **Φιλική προς το χρήστη UI** – εκθέστε την ίδια λογική πίσω από ένα κουμπί σε εφαρμογή WinForms/WPF, εμφανίζοντας τις προειδοποιήσεις σε ένα `ListBox`.

## Συμπέρασμα  

Διασχίσαμε **πώς να διαχειριστείτε τις γραμματοσειρές** σε .NET ρυθμίζοντας το `LoadOptions`, εγγράφοντας στο συμβάν `SubstitutionWarning`, και τελικά φορτώνοντας το έγγραφο. Το παράδειγμα όχι μόνο **ανιχνεύει ελλιπείς γραμματοσειρές** αλλά και **παρακολουθεί αλλαγές γραμματοσειρών** ώστε να μπορείτε να ελέγχετε κάθε αντικατάσταση.  

Δοκιμάστε το με τα δικά σας έγγραφα, προσαρμόστε τη διαδρομή του φακέλου γραμματοσειρών, και δεν θα σας πιάσει ποτέ ξαφνικά μια απρόσμενη αντικατάσταση γραμματοσειράς. Αν βρήκατε αυτόν τον οδηγό χρήσιμο, εξερευνήστε σχετικές θεματικές όπως *«ενσωμάτωση προσαρμοσμένων γραμματοσειρών σε PDF με Aspose.Words»* ή *«δημιουργία στρατηγικής fallback γραμματοσειρών για cross‑platform .NET εφαρμογές»*.  

Καλό coding, και οι εγγραφές σας να αποδίδουν πάντα ακριβώς όπως το θέλετε!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική Σας  

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}