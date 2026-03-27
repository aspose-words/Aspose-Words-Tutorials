---
category: general
date: 2026-03-27
description: 'Η αντικατάσταση γραμματοσειρών Aspose έγινε εύκολη: μάθετε πώς να ρυθμίζετε
  τις ρυθμίσεις γραμματοσειρών, να καταγράφετε προειδοποιήσεις και να διαχειρίζεστε
  τις ελλείπουσες γραμματοσειρές στις .NET εφαρμογές σας.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: el
og_description: Κατακτήστε την αντικατάσταση γραμματοσειρών Aspose διαμορφώνοντας
  τις ρυθμίσεις γραμματοσειρών και διαχειριζόμενοι τις ελλειπούσες γραμματοσειρές
  με κλήση προειδοποίησης. Πλήρης οδηγός C#.
og_title: Αντικατάσταση γραμματοσειρών Aspose – Διαμόρφωση ρυθμίσεων γραμματοσειράς
  σε C#
tags:
- Aspose.Words
- C#
- Font Management
title: Αντικατάσταση Γραμματοσειρών Aspose – Πώς να Διαμορφώσετε τις Ρυθμίσεις Γραμματοσειράς
  σε C#
url: /el/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Πλήρης Οδηγός για τη Διαμόρφωση Ρυθμίσεων Γραμματοσειρών

Έχετε συναντήσει ποτέ ένα έγγραφο που ξαφνικά αντικαθιστά την προσαρμοσμένη γραμματοσειρά σας με κάτι γενικό; Αυτό είναι η **aspose font substitution** που κάνει τη δουλειά της—αντικαθιστώντας τις ελλείπουσες γραμματοσειρές με το πιο κοντινό αντίστοιχο που μπορεί να βρει. Είναι χρήσιμη, αλλά αν χρειάζεστε να γνωρίζετε *ακριβώς* ποια γραμματοσειρά αντικαταστάθηκε, πρέπει να αξιοποιήσετε το σύστημα προειδοποιήσεων της βιβλιοθήκης και να διαμορφώσετε τις ρυθμίσεις γραμματοσειρών μόνοι σας.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό σενάριο: φόρτωση ενός DOCX που αναφέρεται σε γραμματοσειρά που δεν έχετε, καταγραφή του γεγονότος αντικατάστασης και εκτύπωση ενός φιλικού μηνύματος στην κονσόλα. Στο τέλος θα είστε άνετοι με **configure font settings**, τη σύνδεση ενός **Aspose.Words warning callback**, και την επέκταση του παραδείγματος για οποιαδήποτε ροή εργασίας.

> **Τι θα χρειαστείτε**  
> • .NET 6+ (ή .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (τελευταίο NuGet)  
> • Ένα DOCX που αναφέρει μια ελλείπουσα γραμματοσειρά (θα το ονομάσουμε `MissingFont.docx`)  

Ας βουτήξουμε.

---

## Step 1: Install Aspose.Words and Prepare the Project

Πριν γράψουμε κώδικα, βεβαιωθείτε ότι το πακέτο Aspose.Words είναι αναφορά:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Χρησιμοποιήστε την πιο πρόσφατη σταθερή έκδοση· από τον Μάρτιο 2026 είναι η 23.11.0. Οι νεότερες εκδόσεις βελτιώνουν τους αλγόριθμους αντιστοίχισης γραμματοσειρών και προσθέτουν επιπλέον τύπους προειδοποιήσεων.

Δημιουργήστε μια νέα εφαρμογή console (ή ενσωματώστε τον κώδικα σε υπάρχον έργο) και προσθέστε τις συνηθισμένες οδηγίες `using`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Αυτοί οι χώροι ονομάτων μας δίνουν πρόσβαση στα `Document`, `LoadOptions` και στις κλάσεις σχετικές με τις γραμματοσειρές που θα χρειαστούμε.

---

## Step 2: Configure Font Settings with LoadOptions

Η καρδιά του ελέγχου **aspose font substitution** βρίσκεται στο `LoadOptions.FontSettings`. Παρέχοντας ένα κενό αντικείμενο `FontSettings` λέμε στην Aspose να χρησιμοποιήσει τις προεπιλεγμένες διαδρομές αναζήτησης *και* να αναφέρει οποιαδήποτε αντικατάσταση μέσω μιας προειδοποίησης.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Γιατί να μην βασιστούμε μόνο στις προεπιλογές; Επειδή η προσθήκη μιας προειδοποίησης (βήμα επόμενο) λειτουργεί μόνο όταν η ιδιότητα `FontSettings` δεν είναι `null`. Αυτή η μικρή γραμμή μας δίνει ένα σημείο πρόσβασης στη διαδικασία αντικατάστασης χωρίς να αλλάζει τη συμπεριφορά αναζήτησης γραμματοσειρών.

---

## Step 3: Attach a Warning Callback to Capture Substitutions

Η Aspose.Words υλοποιεί τη διεπαφή `IWarningCallback`. Όποτε συμβαίνει κάτι αξιοσημείωτο—όπως μια ελλείπουσα γραμματοσειρά—καλεί τη μέθοδο `Warning`. Θα υλοποιήσουμε έναν μικρό χειριστή που φιλτράρει για `WarningType.FontSubstitution` και εκτυπώνει την περιγραφή.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Και ο ίδιος ο χειριστής:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Γιατί είναι σημαντικό** – Χωρίς την προειδοποίηση, η Aspose αντικαθιστά σιωπηλά τις γραμματοσειρές και δεν ξέρετε ποια χρησιμοποιήθηκε. Η προειδοποίηση κάνει τη διαδικασία διαφανή, κάτι που είναι απαραίτητο για αναφορές συμμόρφωσης ή για εντοπισμό προβλημάτων διάταξης.

---

## Step 4: Load the Document Using the Configured Options

Τώρα φορτώνουμε το έγγραφο, περνώντας το `loadOptions` που μόλις προετοιμάσαμε. Αν το αρχείο πηγής αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, ο χειριστής μας θα ενεργοποιηθεί.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή όπου βρίσκεται το `MissingFont.docx`. Όταν εκτελέσετε το πρόγραμμα, θα δείτε έξοδο παρόμοια με:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Αυτή η γραμμή σας λέει ακριβώς ποια γραμματοσειρά έλειπε και ποια εναλλακτική επέλεξε η Aspose.

---

## Step 5: (Optional) Fine‑Tune Font Search Paths

Αν έχετε έναν ιδιωτικό φάκελο με εταιρικές γραμματοσειρές, μπορείτε να πείτε στην Aspose πού να ψάξει πριν επιστρέψει στις συστημικές γραμματοσειρές. Αυτό είναι μια προχωρημένη χρήση του **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Ορίζοντας `recursive: true` η Aspose θα σαρώσει και τους υποφακέλους. Τώρα η βιβλιοθήκη θα δοκιμάσει πρώτα τις ιδιωτικές σας γραμματοσειρές, μειώνοντας την πιθανότητα ανεπιθύμητης αντικατάστασης.

---

## Full Working Example

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Αναμενόμενη έξοδος** (όταν εντοπιστεί ελλείπουσα γραμματοσειρά):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Αν όλες οι γραμματοσειρές υπάρχουν, το πρόγραμμα εκτελείται σιωπηλά (χωρίς προειδοποιήσεις) και παράγει το PDF.

---

## Common Questions & Edge Cases

### What if I need to *prevent* substitution altogether?

Ορίστε το `FontSettings.SubstitutionSettings` σε `null` ή χρησιμοποιήστε το `FontSettings.FontSubstitutionSettings` για να ελέγξετε τη συμπεριφορά. Για παράδειγμα:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Τώρα η Aspose θα ρίξει εξαίρεση αντί να αντικαθιστά σιωπηλά, η οποία μπορεί να πιαστεί και να διαχειριστεί.

### Does this work with other file formats (e.g., .doc, .rtf)?

Απόλυτα. Το ίδιο αντικείμενο `LoadOptions` μπορεί να περάσει σε οποιονδήποτε κατασκευαστή `Document` που δέχεται διαδρομή αρχείου. Η προειδοποίηση θα ενεργοποιηθεί για όλες τις μορφές που εξαρτώνται από γραμματοσειρές.

### Can I capture the *exact* fallback font name?

Ναι. Η συμβολοσειρά `info.Description` περιέχει τόσο τη λείπουσα γραμματοσειρά όσο και την αντικατάσταση. Αν χρειάζεστε το όνομα προγραμματιστικά, μπορείτε να το αναλύσετε ή να χρησιμοποιήσετε το αντικείμενο `FontInfo` (διαθέσιμο σε νεότερες εκδόσεις).

### How does this behave in a multi‑threaded environment?

Το `FontSettings` **δεν** είναι thread‑safe. Δημιουργήστε ξεχωριστό `LoadOptions` (με το δικό του `FontSettings`) ανά νήμα, ή προστατεύστε την πρόσβαση με κλείδωμα.

---

## Conclusion

Καλύψαμε όλα όσα χρειάζεστε για να κυριαρχήσετε στην **aspose font substitution** και στη **configure font settings** σε εφαρμογή C#:

1. Εγκαταστήστε το Aspose.Words και προσθέστε τις απαραίτητες δηλώσεις `using`.  
2. Δημιουργήστε ένα αντικείμενο `LoadOptions` με νέο `FontSettings`.  
3. Συνδέστε ένα προσαρμοσμένο `IWarningCallback` για να εμφανίζετε γεγονότα αντικατάστασης.  
4. Φορτώστε το έγγραφο, αφήνοντας τον χειριστή να αναφέρει τυχόν ελλείπουσες γραμματοσειρές.  
5. (Προαιρετικά) Επεκτείνετε τη διαδρομή αναζήτησης ή απενεργοποιήστε εντελώς την αντικατάσταση.

Με αυτό το μοτίβο μπορείτε να καταγράψετε ελλείπουσες γραμματοσειρές για συμμόρφωση, να ειδοποιήσετε χρήστες σε UI, ή να ενσωματώσετε αυτόματα εναλλακτικές γραμματοσειρές πριν τη δημοσίευση. Στο επόμενο βήμα, εξερευνήστε τις **Aspose.Words font substitution policies** ή ενσωματώστε τη ροή εργασίας σε ένα μεγαλύτερο pipeline επεξεργασίας εγγράφων.

Καλή προγραμματιστική δουλειά, και ας εμφανίζονται πάντα τα έγγραφά σας με τη σωστή γραμματοσειρά!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}