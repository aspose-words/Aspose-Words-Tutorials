---
category: general
date: 2026-02-10
description: Ορίστε την callback προειδοποίησης για να παρακολουθείτε τις αλλαγές
  γραμματοσειράς ενώ διαμορφώνετε την προεπιλεγμένη γραμματοσειρά και ορίζετε την
  προεπιλεγμένη γραμματοσειρά εισαγωγής στο Aspose.Words. Μάθετε τη πλήρη βήμα‑βήμα
  λύση.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: el
og_description: Ορίστε την κλήση επιστροφής προειδοποίησης για την παρακολούθηση αλλαγών
  γραμματοσειράς κατά τη ρύθμιση της προεπιλεγμένης γραμματοσειράς και της προεπιλεγμένης
  γραμματοσειράς εισαγωγής. Ακολουθήστε τον πλήρη οδηγό για το Aspose.Words.
og_title: Ορισμός callback προειδοποίησης σε C# – Πλήρης οδηγός
tags:
- Aspose.Words
- C#
- Document Import
title: Ορισμός callback προειδοποίησης σε C# – Πλήρης οδηγός διαχείρισης γραμματοσειρών
url: /el/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός callback προειδοποίησης σε C# – Πλήρης Οδηγός Διαχείρισης Γραμματοσειρών

Έχετε ποτέ χρειαστεί να **ορίσετε callback προειδοποίησης** κατά τη φόρτωση ενός εγγράφου Word και αναρωτηθήκατε πώς να *ρυθμίσετε την προεπιλεγμένη γραμματοσειρά* ταυτόχρονα; Δεν είστε μόνοι. Σε πολλά πραγματικά έργα—όπως αυτοματοποιημένοι δημιουργοί αναφορών ή αγωγοί μετατροπής εγγράφων—οι ελλιπείς γραμματοσειρές μπορούν σιωπηρά να διασπάσουν τη διάταξη, και ο μόνος τρόπος να εντοπίσετε αυτά τα προβλήματα είναι να **παρακολουθείτε τις αλλαγές γραμματοσειρών** μέσω ενός callback προειδοποίησης.

Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό παράδειγμα που δείχνει πώς να **ορίσετε callback προειδοποίησης**, **ρυθμίσετε προεπιλεγμένη γραμματοσειρά**, και ακόμη **ορίσετε προεπιλεγμένη γραμματοσειρά εισαγωγής** χρησιμοποιώντας το Aspose.Words for .NET. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση snippet, θα καταλάβετε γιατί κάθε μέρος είναι σημαντικό, και θα ξέρετε πώς να το προσαρμόσετε για ειδικές περιπτώσεις όπως προσαρμοσμένοι φάκελοι γραμματοσειρών ή σιωπηρές αντικαταστάσεις.

---

## Προαπαιτήσεις

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.6+)  
- Πακέτο NuGet Aspose.Words για .NET (`Install-Package Aspose.Words`)  
- Ένας φάκελος που περιέχει τη γραμματοσειρά εφεδρείας που θέλετε να χρησιμοποιήσετε (π.χ., `fonts/Arial.ttf`)  
- Βασική εξοικείωση με εφαρμογές κονσόλας C#  

Δεν απαιτούνται πρόσθετες βιβλιοθήκες.

---

## Βήμα 1: Δημιουργία LoadOptions και **ρύθμιση προεπιλεγμένης γραμματοσειράς**

Το πρώτο πράγμα που κάνετε όταν θέλετε να ελέγξετε τη διαχείριση γραμματοσειρών είναι να δημιουργήσετε μια παρουσία `LoadOptions`. Αυτό το αντικείμενο λέει στο Aspose.Words πώς να αντιμετωπίζει τις ελλιπείς γραμματοσειρές κατά την εισαγωγή.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Γιατί είναι σημαντικό:**  
Αν το πηγαίο έγγραφο αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή, το Aspose.Words θα κοιτάξει στον φάκελο που δώσατε. Αυτό είναι το βασικό στοιχείο του **set default import font**—σας λέει ρητά στη βιβλιοθήκη πού να βρει μια αντικατάσταση πριν εμφανιστούν προειδοποιήσεις.

---

## Βήμα 2: **Ορισμός callback προειδοποίησης** για **παρακολούθηση αλλαγών γραμματοσειρών**

Το Aspose.Words εκδίδει ένα `WarningInfoCollection` όποτε πρέπει να αντικαταστήσει μια γραμματοσειρά, μεταξύ άλλων. Συνδέοντας έναν χειριστή, μπορείτε να καταγράψετε ή να αντιδράσετε σε κάθε αντικατάσταση.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Γιατί είναι σημαντικό:**  
Απλώς **ρυθμίζοντας προεπιλεγμένη γραμματοσειρά** δεν αρκεί αν χρειάζεται να ελέγξετε ποιες γραμματοσειρές αντικαταστάθηκαν πραγματικά. Το callback σας παρέχει μια καταγραφή σε πραγματικό χρόνο, ικανοποιώντας την απαίτηση **monitor font changes** και βοηθώντας σας να εντοπίσετε απρόσμενες εναλλακτικές νωρίς σε μια CI pipeline.

---

## Βήμα 3: Φόρτωση του εγγράφου με τις προετοιμασμένες επιλογές

Τώρα που οι επιλογές φόρτωσης είναι πλήρως προετοιμασμένες, μπορείτε με ασφάλεια να φορτώσετε οποιοδήποτε αρχείο `.docx`. Το callback ενεργοποιείται αυτόματα αν συμβεί αντικατάσταση.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Τι θα δείτε:**  
Αν η πηγή χρησιμοποιεί μια γραμματοσειρά που δεν υπάρχει, η κονσόλα θα εκτυπώσει κάτι όπως:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Αυτή η έξοδος επιβεβαιώνει ότι έχετε επιτυχώς **ορίσει callback προειδοποίησης** και ότι η **default import font** έπαιξε ρόλο.

---

## Βήμα 4: (Προαιρετικό) Λεπτομερής ρύθμιση συμπεριφοράς αντικατάστασης γραμματοσειρών

Μερικές φορές μπορεί να θέλετε να αντικαταστήσετε *όλες* τις ελλιπείς γραμματοσειρές με μία μόνο οικογένεια, ανεξάρτητα από το αρχικό αίτημα. Το Aspose.Words σας επιτρέπει να ορίσετε μια *fallback font* παγκοσμίως.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Πότε να το χρησιμοποιήσετε:**  
Αν δημιουργείτε PDFs για μια μάρκα που επιτρέπει μόνο περιορισμένο σύνολο γραμματοσειρών, αυτό εξασφαλίζει συνέπεια σε κάθε έγγραφο, ακόμη και αν η πηγή προσπαθήσει να χρησιμοποιήσει κάτι εξωτικό.

---

## Βήμα 5: Αποθήκευση ή περαιτέρω επεξεργασία του εγγράφου

Μετά τη φόρτωση, μπορείτε να συνεχίσετε με οποιαδήποτε επεξεργασία χρειάζεστε—επεξεργασία, μετατροπή σε PDF, εξαγωγή κειμένου κ.λπ. Ακολουθεί ένα γρήγορο παράδειγμα αποθήκευσης του εγγράφου ως PDF ενώ διατηρούνται οι αντικατεστημένες γραμματοσειρές.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Το παραγόμενο PDF θα εμφανίζει τη γραμματοσειρά εφεδρείας όπου και αν έγινε αντικατάσταση, δίνοντάς σας οπτική επιβεβαίωση ότι το **set warning callback** λειτούργησε όπως αναμενόταν.

---

## Συνηθισμένα προβλήματα & Pro Tips

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Η callback δεν ενεργοποιείται ποτέ** | `LoadOptions.WarningCallback` δεν είχε εκχωρηθεί *πριν* τη φόρτωση του εγγράφου. | Πάντα συνδέστε το callback **πριν** καλέσετε `new Document(...)`. |
| **Λάθος φάκελος γραμματοσειρών** | Λάθος διαδρομή ή έλλειψη δικαιωμάτων ανάγνωσης. | Επαληθεύστε ότι ο φάκελος υπάρχει και η εφαρμογή έχει πρόσβαση `Read`. Χρησιμοποιήστε απόλυτες διαδρομές για αξιοπιστία. |
| **Πολλαπλές αντικαταστάσεις, θορυβώδη έξοδο** | Μεγάλα έγγραφα με πολλές ελλιπείς γραμματοσειρές. | Φιλτράρετε τις προειδοποιήσεις με `WarningType.FontSubstitution` (όπως φαίνεται) ή γράψτε τις σε αρχείο καταγραφής αντί για την κονσόλα. |
| **Η γραμματοσειρά εφεδρείας δεν εφαρμόζεται** | Η γραμματοσειρά εφεδρείας δεν είναι εγκατεστημένη στο μηχάνημα. | Τοποθετήστε το αρχείο `.ttf`/`.otf` στον φάκελο που περάσατε στο `SetFontsFolder`. Το Aspose.Words το φορτώνει απευθείας, χωρίς ανάγκη εγκατάστασης στο OS. |

**Pro tip:** Όταν τρέχετε αυτό σε pipeline CI/CD, ανακατευθύνετε την έξοδο της κονσόλας σε ένα artifact κατασκευής. Έτσι έχετε ένα αποδεικτικό ίχνος για κάθε αντικατάσταση γραμματοσειράς που συνέβη κατά τη διάρκεια της κατασκευής.

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να ενσωματώσετε σε ένα νέο έργο Console App. Περιλαμβάνει όλα τα βήματα, τις δηλώσεις `using`, και τα σχόλια που χρειάζεστε.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενη έξοδος κονσόλας** (υποθέτοντας ότι η `Times New Roman` λείπει):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Τρέξτε το πρόγραμμα, ανοίξτε το `output.pdf`, και θα δείτε το έγγραφο να αποδίδεται με τη γραμματοσειρά εφεδρείας όπου χρειάζεται.

---

## Συμπέρασμα

Τώρα έχετε ένα σταθερό, έτοιμο για παραγωγή μοτίβο για το πώς να **ορίσετε callback προειδοποίησης** σε C#, **ρυθμίσετε προεπιλεγμένη γραμματοσειρά**, **παρακολουθείτε αλλαγές γραμματοσειρών**, και **ορίσετε προεπιλεγμένη γραμματοσειρά εισαγωγής** όταν εργάζεστε με το Aspose.Words. Συνδέοντας έναν συλλέκτη προειδοποιήσεων πριν τη φόρτωση, δείχνοντας το `FontSettings` σε έναν αξιόπιστο φάκελο γραμματοσειρών, και προαιρετικά επιβάλλοντας μια παγκόσμια εφεδρεία, αποκτάτε πλήρη ορατότητα και έλεγχο πάνω στην αντικατάσταση γραμματοσειρών—ακριβώς ό,τι χρειάζεται οποιοδήποτε αξιόπιστο pipeline επεξεργασίας εγγράφων.

Έτοιμοι για το επόμενο επίπεδο; Δοκιμάστε να συνδυάσετε αυτήν την προσέγγιση με:

- **Δυναμική φόρτωση γραμματοσειρών** από μια βάση δεδομένων (χρησιμοποιήστε `FontSettings.SetFontsFolder` κατά το runtime).  
- **Προσαρμοσμένους χειριστές προειδοποιήσεων** που γράφουν σε δομημένο αρχείο καταγραφής (JSON ή CSV) για αναλύσεις.  
- **Παράλληλη επεξεργασία εγγράφων** όπου κάθε νήμα λαμβάνει το δικό του `LoadOptions` ώστε να αποφεύγεται η αλληλεπίδραση.

Νιώστε ελεύθεροι να πειραματιστείτε, να προσαρμόσετε τον κώδικα στην αρχιτεκτονική σας, και να μοιραστείτε τυχόν ανακαλύψεις στα σχόλια. Καλός κώδικας!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}