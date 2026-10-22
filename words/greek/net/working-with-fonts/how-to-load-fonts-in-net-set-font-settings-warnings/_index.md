---
category: general
date: 2026-06-30
description: Μάθετε πώς να φορτώνετε γραμματοσειρές στο .NET χρησιμοποιώντας το LoadOptions,
  να ορίζετε ρυθμίσεις γραμματοσειράς, να ενεργοποιείτε προσαρμοσμένες γραμματοσειρές
  και να ανιχνεύετε ελλείπουσες γραμματοσειρές με κλήσεις επιστροφής προειδοποίησης.
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: el
og_description: Πώς να φορτώσετε γραμματοσειρές στο .NET; Αυτός ο οδηγός σας δείχνει
  πώς να ρυθμίσετε τις ρυθμίσεις γραμματοσειράς, να ενεργοποιήσετε προσαρμοσμένες
  γραμματοσειρές και να εντοπίσετε ελλείπουσες γραμματοσειρές με κλήσεις επιστροφής
  προειδοποίησης.
og_title: Πώς να φορτώσετε γραμματοσειρές στο .NET – Ορίστε ρυθμίσεις γραμματοσειράς
  & προειδοποιήσεις
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Πώς να φορτώσετε γραμματοσειρές στο .NET – Ορίστε ρυθμίσεις γραμματοσειράς
  & προειδοποιήσεις
url: /el/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να φορτώσετε γραμματοσειρές σε .NET – Ορισμός ρυθμίσεων γραμματοσειράς & προειδοποιήσεων

Έχετε αναρωτηθεί ποτέ **πώς να φορτώσετε γραμματοσειρές** σε ένα έγγραφο .NET χωρίς να τσακίζετε τα μαλλιά σας; Δεν είστε ο μόνος. Η έλλειψη γλυφών, οι σιωπηλές εναλλακτικές και οι ακατανόητες προειδοποιήσεις μπορούν να μετατρέψουν έναν απλό δημιουργό αναφορών σε εφιάλτη.  

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει **πώς να φορτώσετε γραμματοσειρές**, να διαμορφώσετε **ρυθμίσεις γραμματοσειράς**, **να ενεργοποιήσετε προσαρμοσμένες γραμματοσειρές**, και **να εντοπίσετε ελλιπείς γραμματοσειρές** χειρίζοντας προειδοποιήσεις. Στο τέλος θα έχετε ένα σταθερό μοτίβο που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Aspose.Words ή παρόμοιας βιβλιοθήκης.

> **Γρήγορη επισκόπηση:** θα δημιουργήσουμε ένα αντικείμενο `LoadOptions`, θα συνδέσουμε μια callback προειδοποίησης, και θα φορτώσουμε ένα DOCX που σκόπιμα αναφέρει μια ελλιπή γραμματοσειρά. Η κονσόλα θα εκτυπώσει ένα σαφές μήνυμα κάθε φορά που η μηχανή αντικαθιστά μια γραμματοσειρά.

## Τι Θα Χρειαστεί

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.6+)  
- Aspose.Words for .NET (το δωρεάν trial πακέτο NuGet είναι εντάξει)  
- Ένα αρχείο DOCX που αναφέρει μια γραμματοσειρά που *δεν* έχετε εγκατεστημένη (π.χ., `MissingFont.docx`)  

Αυτό είναι όλο—χωρίς επιπλέον υπηρεσίες, χωρίς ασαφή αρχεία ρυθμίσεων. Αν έχετε αυτά τα τρία στοιχεία, είστε έτοιμοι να προχωρήσετε.

![διάγραμμα παραδείγματος φόρτωσης γραμματοσειρών](https://example.com/how-to-load-fonts-diagram.png)

*Κείμενο alt εικόνας: διάγραμμα παραδείγματος φόρτωσης γραμματοσειρών*

## Βήμα 1: Δημιουργία Load Options και Ενεργοποίηση Προσαρμοσμένων Ρυθμίσεων Γραμματοσειράς  

Το πρώτο πράγμα που κάνετε όταν θέλετε να **ορίσετε ρυθμίσεις γραμματοσειράς** είναι να δημιουργήσετε ένα αντικείμενο `LoadOptions`. Μέσα σε αυτό τοποθετείτε μια παρουσία `FontSettings` που δείχνει σε έναν φάκελο που περιέχει τυχόν προσαρμοσμένα αρχεία .ttf ή .otf που μπορεί να χρειαστείτε.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**Γιατί είναι σημαντικό:** Από προεπιλογή, το Aspose.Words ψάχνει μόνο τις γραμματοσειρές που είναι εγκατεστημένες στο σύστημα. Αν το έγγραφό σας χρησιμοποιεί μια εταιρική γραμματοσειρά που βρίσκεται σε κοινόχρηστο δίκτυο, πρέπει να πείτε στη βιβλιοθήκη πού να τη βρει. Αυτό είναι το νόημα του **ενεργοποίησης προσαρμοσμένων γραμματοσειρών**.

## Βήμα 2: Σύνδεση Handler Προειδοποίησης για Εντοπισμό Ελλιπών Γραμματοσειρών  

Αν παραλείψετε τη διαχείριση προειδοποιήσεων, οι ελλιπείς γλύφοι αντικαθίστανται σιωπηρά με μια εφεδρική γραμματοσειρά—συχνά Times New Roman. Αυτό μπορεί να διασπάσει την ταυτότητα ή ακόμη και να προκαλέσει αλλαγές διάταξης. Για **πώς να διαχειριστείτε προειδοποιήσεις**, συνδέστε μια callback που εξετάζει το `WarningType.FontSubstitution`.

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**Συμβουλή επαγγελματία:** Το `WarningCallback` ενεργοποιείται για *οποιαδήποτε* προειδοποίηση, όχι μόνο για ελλιπείς γραμματοσειρές. Το φιλτράρισμα με `WarningType.FontSubstitution` διατηρεί το αποτέλεσμα καθαρό και απαντά άμεσα στην ερώτηση **εντοπισμός ελλιπών γραμματοσειρών**.

## Βήμα 3: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές  

Τώρα που έχουμε προετοιμάσει τις επιλογές, μπορούμε τελικά να **φορτώσουμε γραμματοσειρές** στο έγγραφο. Ο κατασκευαστής `Document` δέχεται τη διαδρομή του αρχείου συν το `LoadOptions` που μόλις δημιουργήσαμε.

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

Αν το αρχείο προέλευσης αναφέρει μια γραμματοσειρά που δεν βρίσκεται στον φάκελο του συστήματος *ή* στον προσαρμοσμένο φάκελο που ορίσαμε νωρίτερα, η callback προειδοποίησης από το Βήμα 2 θα εκτυπώσει μια χρήσιμη γραμμή στην κονσόλα.

## Βήμα 4: Επαλήθευση του Σετ Φορτωμένων Γραμματοσειρών (Προαιρετικό αλλά Ενημερωτικό)  

Μερικές φορές θέλετε να ελέγξετε ξανά ποιες γραμματοσειρές επιλύθηκαν πραγματικά. Το Aspose.Words εκθέτει το `FontSettings` που περάσατε, ώστε να μπορείτε να απαριθμήσετε τις πηγές γραμματοσειρών που επιλύθηκαν.

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

Η εκτέλεση αυτού του αποσπάσματος μετά τη φόρτωση θα εκτυπώσει κάτι όπως:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

Η γραμμή προειδοποίησης επιβεβαιώνει ότι εντοπίσαμε επιτυχώς **ελλιπείς γραμματοσειρές**, ενώ η λίστα δείχνει ότι εξετάστηκαν τόσο οι φάκελοι του συστήματος όσο και οι προσαρμοσμένοι.

## Βήμα 5: Αποθήκευση ή Απόδοση του Εγγράφου  

Μόλις το έγγραφο φορτωθεί και έχετε επαληθεύσει τις γραμματοσειρές, μπορείτε να συνεχίσετε με οποιαδήποτε επεξεργασία—αποθήκευση ως PDF, απόδοση σε εικόνες, ή χειρισμό του DOM. Για πληρότητα, εδώ είναι μια εντολή μίας γραμμής που αποθηκεύει το αποτέλεσμα ως PDF:

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

Όταν ανοίξει το PDF, τυχόν ελλιπείς γλύφοι θα έχουν αντικατασταθεί από την εφεδρική γραμματοσειρά που είδατε στην έξοδο της κονσόλας. Αν προσθέσετε τη λείπουσα γραμματοσειρά στο `C:\MyCustomFonts`, εκτελέστε ξανά το πρόγραμμα και η προειδοποίηση θα εξαφανιστεί—απόδειξη ότι η **ενεργοποίηση προσαρμοσμένων γραμματοσειρών** λειτουργεί πραγματικά.

---

## Πλήρες Παράδειγμα Εργασίας

Αντιγράψτε ολόκληρο το παρακάτω μπλοκ σε ένα νέο έργο κονσόλας, προσθέστε το πακέτο NuGet Aspose.Words, και πατήστε **Run**. Προσαρμόστε τις διαδρομές αρχείων ώστε να ταιριάζουν με το περιβάλλον σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### Αναμενόμενη Έξοδος

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

Αν τοποθετήσετε το λείπον αρχείο `Papyrus.ttf` στο `C:\MyCustomFonts` και εκτελέσετε ξανά το πρόγραμμα, η γραμμή προειδοποίησης θα εξαφανιστεί, επιβεβαιώνοντας ότι ο προσαρμοσμένος φάκελος χρησιμοποιήθηκε σωστά.

---

## Συχνές Ερωτήσεις & Πιθανά Προβλήματα

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν δεν έχω callback προειδοποίησης;** | Το έγγραφο φορτώνεται ακόμη, αλλά δεν θα ξέρετε πότε έγινε αντικατάσταση. Η προσθήκη του callback είναι ο πιο απλός τρόπος για **πώς να διαχειριστείτε προειδοποιήσεις**. |
| **Μπορώ να φορτώσω γραμματοσειρές από αρχείο zip;** | Ναι—χρησιμοποιήστε `new FolderFontSource(zipPath, true)` ή υλοποιήστε ένα προσαρμοσμένο `IFontSource`. Αυτό εξακολουθεί να ανήκει στην **ενεργοποίηση προσαρμοσμένων γραμματοσειρών**. |
| **Πρέπει να ενσωματώσω τις γραμματοσειρές στο PDF;** | Ορίστε `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;` πριν από την αποθήκευση. Η ενσωμάτωση εγγυάται ότι το PDF φαίνεται το ίδιο σε οποιονδήποτε υπολογιστή. |
| **Τι γίνεται αν το έγγραφο χρησιμοποιεί μια γραμματοσειρά που είναι αδειοδοτημένη και δεν μπορεί να διανεμηθεί;** | Μπορείτε ακόμη να *εντοπίσετε* τη λείπουσα γραμματοσειρά μέσω προειδοποιήσεων, αλλά δεν πρέπει να την ενσωματώσετε εκτός εάν έχετε τα δικαιώματα. Σκεφτείτε την αντικατάσταση με μια παρόμοια ανοιχτού κώδικα γραμματοσειρά. |

---

## Σύνοψη

Καλύψαμε **πώς να φορτώσετε γραμματοσειρές** σε .NET με:

1. Δημιουργία `LoadOptions` και διαμόρφωση **ρυθμίσεων γραμματοσειράς**.  
2. **Ενεργοποίηση προσαρμοσμένων γραμματοσειρών** με την ένδειξη ενός φακέλου με επιπλέον τύπους γραμματοσειρών.  
3. **Πώς να διαχειριστείτε προειδοποιήσεις** με ένα `WarningCallback` που εκτυπώνει μηνύματα αντικατάστασης γραμματοσειράς.  
4. **Εντοπισμός ελλιπών γραμματοσειρών** φιλτράροντας το `WarningType.FontSubstitution`.  
5. Αποθήκευση του εγγράφου, επιβεβαιώνοντας ότι η εφεδρική

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Ορισμός Φακέλων Γραμματοσειρών Συστήματος Και Προσαρμοσμένου Φακέλου](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [Πώς να Εντοπίσετε Γραμματοσειρές στο Aspose.Words – Διαχείριση Προειδοποιήσεων & Ρυθμίσεων](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Πώς να Συλλέξετε Γραμματοσειρές στο Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}