---
category: general
date: 2026-03-01
description: Δημιουργήστε FontSettings σε C# για να εντοπίζετε ελλείποντες γραμματοσειρές,
  να καταγράφετε μηνύματα γραμματοσειρών και να διαχειρίζεστε τις ελλείποντες γραμματοσειρές
  με το Aspose.Words. Οδηγός βήμα‑βήμα για προγραμματιστές.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: el
og_description: Δημιουργήστε FontSettings σε C# για να εντοπίζετε ελλείποντες γραμματοσειρές,
  να καταγράφετε μηνύματα γραμματοσειρών και να διαχειρίζεστε ελλείποντες γραμματοσειρές
  χρησιμοποιώντας το Aspose.Words. Πλήρης οδηγός με κώδικα.
og_title: Δημιουργία FontSettings σε C# – Εντοπισμός Ελλειπουσών Γραμματοσειρών &
  Καταγραφή Μηνυμάτων Γραμματοσειρών
tags:
- Aspose.Words
- C#
- Font Management
title: Δημιουργία FontSettings σε C# – Ανίχνευση Ελλειπόντων Γραμματοσειρών & Καταγραφή
  Μηνυμάτων Γραμματοσειράς
url: /el/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create FontSettings in C# – Detect Missing Fonts & Capture Font Messages

Έχετε ποτέ χρειαστεί να **create FontSettings** σε ένα έργο .NET αλλά δεν ήσασταν σίγουροι πώς να εντοπίσετε τις γραμματοσειρές που δεν είναι εγκατεστημένες στο στόχο; Δεν είστε μόνοι. Σε πολλές πραγματικές εφαρμογές—σκεφτείτε αυτόματους δημιουργούς αναφορών ή μετατροπείς εγγράφων—οι ελλειπούσες γραμματοσειρές μπορούν σιωπηρά να διαταράξουν τη διάταξη, και δεν θα το καταλάβετε μέχρι το PDF να φαίνεται παραμορφωμένο.  

Τι θα λέγατε αν μπορούσατε να **detect missing fonts**, **capture font messages**, και **handle missing fonts** πριν χαλάσουν το αποτέλεσμα σας; Τα καλά νέα είναι ότι το Aspose.Words το κάνει παιχνιδάκι. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, από τη ρύθμιση του αντικειμένου `FontSettings` μέχρι τη σύνδεση ενός callback προειδοποίησης που σας λέει ακριβώς ποιοι χαρακτήρες αντικαταστάθηκαν.

> **TL;DR:** Στο τέλος θα έχετε μια έτοιμη για εκτέλεση εφαρμογή κονσόλας C# που καταγράφει κάθε αντικατάσταση γραμματοσειράς, επιτρέποντάς σας να αποφασίσετε αν θα ενσωματώσετε μια εναλλακτική ή θα ειδοποιήσετε τον χρήστη.

---

## Προαπαιτούμενα

- .NET 6 SDK (ή οποιαδήποτε πρόσφατη έκδοση .NET)  
- Visual Studio 2022 ή VS Code με επεκτάσεις C#  
- Άδεια Aspose.Words for .NET (η δωρεάν δοκιμή λειτουργεί για αυτήν την επίδειξη)  
- Ένα δείγμα DOCX που αναφέρεται σε γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., *Comic Sans MS* σε Linux μηχάνημα)  

Δεν απαιτούνται ειδικά πακέτα NuGet πέρα από το `Aspose.Words`.

## Βήμα 1 – Εγκατάσταση Aspose.Words και Ρύθμιση του Έργου

Πρώτα απ' όλα, δημιουργήστε ένα νέο έργο κονσόλας και προσθέστε τη βιβλιοθήκη Aspose.Words.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

**Pro tip:** Αν ήδη έχετε μια λύση, απλώς προσθέστε το πακέτο μέσω του UI του NuGet Package Manager—καθιστά την παρακολούθηση εκδόσεων πιο εύκολη.

## Βήμα 2 – Create FontSettings (Primary Keyword Appears Here)

Το βήμα **create FontSettings** είναι η βάση κάθε ροής εργασίας σχετικής με γραμματοσειρές. Το `FontSettings` λέει στο Aspose.Words πού να ψάξει για γραμματοσειρές, αν θα χρησιμοποιήσει φακέλους συστήματος, και πώς να υποκαταστήσει όταν κάτι λείπει.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Γιατί είναι σημαντικό αυτό; Χωρίς ένα σωστά ρυθμισμένο `FontSettings`, η μηχανή αντικαθιστά σιωπηρά τα ελλειπούσες γλύφους με την προεπιλεγμένη γραμματοσειρά του συστήματος, και δεν θα δείτε ποτέ προειδοποίηση.

## Βήμα 3 – Σύνδεση LoadOptions με το FontSettings

Το `LoadOptions` σας επιτρέπει να περάσετε το `FontSettings` στον φορτωτή εγγράφων. Αυτή είναι η γέφυρα που επιτρέπει στη μηχανή να **detect missing fonts** κατά τη φάση κατασκευής του `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Τώρα, κάθε φορά που φορτώνετε ένα DOCX με `loadOptions`, το Aspose.Words θα συμβουλευτεί το `FontSettings` που ρυθμίσαμε νωρίτερα.

## Βήμα 4 – Προσθήκη Callback Προειδοποίησης για **Capture Font Messages**

Το Aspose.Words εκδίδει προειδοποιήσεις για διάφορες συνθήκες—η αντικατάσταση γραμματοσειράς είναι μια συχνή. Παρέχοντας μια υλοποίηση του `IWarningCallback`, μπορείτε να **capture font messages** σε πραγματικό χρόνο.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Η Κλάση Διαχειριστή Προειδοποίησης

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Το πεδίο `info.Description` περιέχει ένα ανθρώπινα αναγνώσιμο μήνυμα όπως *«Font 'Comic Sans MS' was not found. Substituted with 'Arial'.»* Αυτό είναι ακριβώς ο τύπος εξόδου που χρειάζεστε για να **handle missing fonts** με χάρη.

## Βήμα 5 – Φόρτωση του Εγγράφου και Εκτέλεση του Callback

Με όλα συνδεδεμένα, η φόρτωση του εγγράφου είναι απλή. Αν το αρχείο προέλευσης αναφέρει μια γραμματοσειρά που λείπει από το σύστημα, ο διαχειριστής προειδοποιήσεων μας θα ενεργοποιηθεί.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Όταν εκτελέσετε το πρόγραμμα, θα δείτε έξοδο κονσόλας παρόμοια με:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Αυτή η έξοδος είναι το τμήμα **capture font messages** της ροής εργασίας μας. Μπορείτε να επεκτείνετε τον διαχειριστή ώστε να καταγράφει σε αρχείο, να στέλνει τηλεμετρία, ή ακόμη και να ακυρώνει τη μετατροπή αν λείπουν κρίσιμες γραμματοσειρές.

## Βήμα 6 – Πλήρες Παράδειγμα Εργασίας (Όλα τα Μέρη Μαζί)

Παρακάτω υπάρχει ένα πλήρες, έτοιμο για αντιγραφή πρόγραμμα. Επικολλήστε το στο `Program.cs`, προσαρμόστε τις διαδρομές αρχείων, και τρέξτε `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Αναμενόμενη Έξοδος

Η εκτέλεση του προγράμματος σε μηχάνημα που δεν διαθέτει *Comic Sans MS* θα εκτυπώσει κάτι όπως:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Θα έχετε επίσης το `Result.pdf` που χρησιμοποιεί τις υποκατεστημένες γραμματοσειρές, εξασφαλίζοντας ότι η μετατροπή δεν θα καταρρεύσει.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Question | Answer |
|----------|--------|
| **Τι γίνεται αν θέλω η μετατροπή να αποτύχει αντί να υποκαθιστά;** | Στο `FontSubstitutionWarningHandler`, ρίξτε μια εξαίρεση όταν το `info.Description` περιέχει το όνομα μιας κρίσιμης γραμματοσειράς. |
| **Μπορώ να ενσωματώσω αυτόματα μια εναλλακτική γραμματοσειρά;** | Ναι. Αφού εντοπίσετε μια ελλιπή γραμματοσειρά, μπορείτε να φορτώσετε ένα εφεδρικό `FontInfo` από γνωστή διαδρομή και να το προσθέσετε στο `fontSettings` μέσω του `fontSettings.SetFontsFolder`. |
| **Λειτουργεί αυτό σε Linux/macOS;** | Απολύτως. Το `FontSettings` λειτουργεί δια-πλατφόρμα· απλώς βεβαιωθείτε ότι ο φάκελος εφεδρείας περιέχει τα κατάλληλα αρχεία `.ttf` ή `.otf`. |
| **Είναι το callback προειδοποίησης ασφαλές για νήματα;** | Το callback εκτελείται στο ίδιο νήμα που φορτώνει το έγγραφο, οπότε δεν χρειάζεται επιπλέον συγχρονισμός για την καταγραφή στην κονσόλα. Σε σενάρια πολλαπλών νημάτων, προστατέψτε τους κοινόχρηστους πόρους. |
| **Πώς μπορώ να καταγράψω τις προειδοποιήσεις σε αρχείο;** | Αντικαταστήστε το `Console.WriteLine` με `File.AppendAllText("font_warnings.log", ...)` ή χρησιμοποιήστε οποιοδήποτε πλαίσιο καταγραφής (Serilog, NLog). |

## Συμβουλές για Παραγωγική Διαχείριση Γραμματοσειρών

1. **Cache Font Lookups** – Η επαναχρησιμοποίηση της ίδιας παρουσίας `FontSettings` σε πολλαπλές φορτώσεις εγγράφων αποφεύγει επαναλαμβανόμενες σάρωση του συστήματος αρχείων.  
2. **Whitelist Critical Fonts** – Αν η μάρκα σας απαιτεί συγκεκριμένη γραμματοσειρά, επαληθεύστε την παρουσία της νωρίς και τερματίστε με σαφές μήνυμα σφάλματος.  
3. **Use `SetFontFolder` Recursively** – Ορίζοντας `recursive: true` εξασφαλίζει ότι θα σαρωθούν και οι υποφάκελοι, κάτι χρήσιμο όταν διανέμετε μια ολόκληρη συλλογή γραμματοσειρών.  
4. **Combine with `FontSubstitutionSettings`** – Μπορείτε να ρυθμίσετε λεπτομερώς τους κανόνες αντικατάστασης (π.χ., προτιμώντας γραμματοσειρές με το ίδιο όνομα οικογένειας).  

## Συμπέρασμα

Μόλις **created FontSettings**, ρυθμίσαμε το `LoadOptions` ώστε να **detect missing fonts**, προσθέσαμε ένα callback που **captures font messages**, και δείξαμε πώς να **handle missing fonts** με καθαρό, παραγωγικό τρόπο. Ολόκληρη η ροή χωράει σε μερικές δεκάδες γραμμές C#, αλλά σας παρέχει πλήρη ορατότητα στο τοπίο των γραμματοσειρών οποιουδήποτε DOCX επεξεργάζεστε.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

- **Embedding fallback fonts** απευθείας στο PDF εξόδου (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** βάσει κανόνων εταιρικής επωνυμίας.  
- **Integrating with a CI pipeline** για αυτόματη επισήμανση εγγράφων που χρησιμοποιούν μη εξουσιοδοτημένες γραμματοσειρές.  

Δοκιμάστε το, προσαρμόστε το διαχειριστή προειδοποιήσεων στις ανάγκες σας, και αφήστε τις γραμμές επεξεργασίας εγγράφων σας να λειτουργούν με σιγουριά—χωρίς περισσότερα μυστηριώδη σφάλματα διάταξης που προκαλούνται από αόρατες ανταλλαγές γραμματοσειρών.

Καλό κώδικα! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}