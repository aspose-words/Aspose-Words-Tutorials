---
category: general
date: 2026-03-30
description: πώς να καταγράψετε προειδοποιήσεις κατά τη φόρτωση ενός αρχείου DOCX
  – μάθετε πώς να εντοπίζετε ελλιπείς γραμματοσειρές, να διαμορφώνετε τις ρυθμίσεις
  γραμματοσειράς και να ορίζετε επιλογές φόρτωσης σε C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: el
og_description: πώς να εντοπίζετε προειδοποιήσεις κατά τη φόρτωση ενός αρχείου DOCX
  – βήμα‑βήμα οδηγός για τον εντοπισμό ελλιπών γραμματοσειρών και τη διαμόρφωση ρυθμίσεων
  γραμματοσειράς σε C#
og_title: πώς να καταγράψετε προειδοποιήσεις – ρυθμίστε τις επιλογές φόρτωσης για
  ελλείπουσες γραμματοσειρές
tags:
- Aspose.Words
- C#
- Font management
title: πώς να καταγράψετε προειδοποιήσεις – ρυθμίστε τις επιλογές φόρτωσης για ελλείποντα
  γραμματοσειρές
url: /el/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να καταγράψετε προειδοποιήσεις – ρυθμίστε επιλογές φόρτωσης για ελλιπείς γραμματοσειρές

Έχετε αναρωτηθεί ποτέ **πώς να καταγράψετε προειδοποιήσεις** που εμφανίζονται όταν ένα έγγραφο προσπαθεί να χρησιμοποιήσει μια γραμματοσειρά που δεν έχετε εγκαταστήσει; Είναι ένα σενάριο που παρενοχλεί πολλούς προγραμματιστές που εργάζονται με βιβλιοθήκες επεξεργασίας κειμένου, ειδικά όταν χρειάζεται να **ανιχνεύσετε ελλιπείς γραμματοσειρές** πριν διακόψουν τη διαδικασία εξαγωγής PDF.

Σε αυτό το tutorial θα σας δείξουμε μια πρακτική, έτοιμη‑για‑εκτέλεση λύση που **ρυθμίζει τις ρυθμίσεις γραμματοσειρών**, **ορίζει επιλογές φόρτωσης**, και εκτυπώνει κάθε προειδοποίηση αντικατάστασης στην κονσόλα. Στο τέλος θα γνωρίζετε ακριβώς πώς να **χειρίζεστε ελλιπείς γραμματοσειρές** με τρόπο που διατηρεί την εφαρμογή σας αξιόπιστη και τους χρήστες σας ευχαριστημένους.

## Τι θα μάθετε

- Πώς να **ορίσετε επιλογές φόρτωσης** ώστε η βιβλιοθήκη να αναφέρει προβλήματα γραμματοσειρών αντί να τις αντικαθιστά σιωπηρά.
- Τα ακριβή βήματα για **ρύθμιση των ρυθμίσεων γραμματοσειρών** για σύλληψη προειδοποιήσεων.
- Τρόπους **ανίχνευσης ελλιπών γραμματοσειρών** προγραμματιστικά και αντίδρασης ανάλογα.
- Ένα πλήρες, αντιγραφή‑επικόλληση παράδειγμα C# που λειτουργεί με την πιο πρόσφατη έκδοση του Aspose.Words for .NET (v24.10 τη στιγμή της συγγραφής).
- Συμβουλές για επέκταση της λύσης ώστε να καταγράφει προειδοποιήσεις, να χρησιμοποιεί προσαρμοσμένες γραμματοσειρές εναλλακτικά, ή να διακόπτει την επεξεργασία όταν λείπουν κρίσιμες γραμματοσειρές.

> **Προαπαιτούμενο:** Χρειάζεστε το πακέτο NuGet Aspose.Words for .NET εγκατεστημένο (`Install-Package Aspose.Words`). Δεν απαιτούνται άλλες εξωτερικές εξαρτήσεις.

---

## Βήμα 1: Εισαγωγή Namespaces και Προετοιμασία του Project

Πρώτα, προσθέστε τις απαραίτητες οδηγίες `using`. Αυτό δεν είναι απλώς boilerplate· λέει στον μεταγλωττιστή πού βρίσκονται τα `LoadOptions`, `FontSettings` και `Document`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Pro tip:** Αν χρησιμοποιείτε .NET 6+ μπορείτε να ενεργοποιήσετε τις *global using* δηλώσεις για να αποφύγετε την επανάληψη αυτών των γραμμών σε κάθε αρχείο.

---

## Βήμα 2: Ορισμός Load Options και Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών

Η ουσία του **πώς να καταγράψετε προειδοποιήσεις** βρίσκεται στο αντικείμενο `LoadOptions`. Δημιουργώντας μια νέα παρουσία `FontSettings` και συνδέοντας έναν χειριστή συμβάντος στο `SubstitutionWarning`, λέτε στη βιβλιοθήκη να σας ενημερώνει κάθε φορά που δεν μπορεί να βρει τη ζητούμενη γραμματοσειρά.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Γιατί είναι σημαντικό:** Χωρίς την εγγραφή του συμβάντος, το Aspose.Words επιστρέφει σιωπηλά σε μια προεπιλεγμένη γραμματοσειρά, και δεν ξέρετε ποια glyphs αντικαταστάθηκαν. Ακούγοντας το `SubstitutionWarning`, λαμβάνετε πλήρη ιστορικό – κρίσιμο για περιβάλλοντα με αυστηρές απαιτήσεις συμμόρφωσης.

---

## Βήμα 3: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Ρυθμισμένες Επιλογές

Τώρα που οι προειδοποιήσεις είναι συνδεδεμένες, φορτώστε το DOCX (ή οποιαδήποτε υποστηριζόμενη μορφή) με το `loadOptions` που μόλις προετοιμάσατε. Ο κατασκευαστής `Document` θα ενεργοποιήσει αμέσως τη λογική ελέγχου γραμματοσειρών.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Αν το αρχείο αναφέρει, για παράδειγμα, *“Comic Sans MS”* σε ένα σύστημα που διαθέτει μόνο *“Arial”*, θα δείτε κάτι σαν:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Αυτή η γραμμή εκτυπώνεται απευθείας στην κονσόλα λόγω του χειριστή που προσθέσαμε νωρίτερα.

---

## Βήμα 4: Επαλήθευση και Αντίδραση στις Καταγεγραμμένες Προειδοποιήσεις

Η σύλληψη προειδοποιήσεων είναι μόνο το ήμισυ του αγώνα· συχνά χρειάζεται να αποφασίσετε τι θα κάνετε στη συνέχεια. Παρακάτω υπάρχει ένα γρήγορο μοτίβο που αποθηκεύει τις προειδοποιήσεις σε λίστα για μεταγενέστερη ανάλυση—ιδανικό αν θέλετε να τις καταγράψετε σε αρχείο ή να διακόψετε την εισαγωγή όταν λείπει μια κρίσιμη γραμματοσειρά.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Διαχείριση ειδικών περιπτώσεων:**  
- **Πολλαπλές ελλιπείς γραμματοσειρές:** Η λίστα θα περιέχει μία καταχώρηση ανά αντικατάσταση, ώστε να μπορείτε να επαναλάβετε και να δημιουργήσετε λεπτομερή αναφορά.  
- **Προσαρμοσμένες γραμματοσειρές εναλλακτικά:** Αν έχετε τα δικά σας αρχεία γραμματοσειρών, προσθέστε τα στο `FontSettings` πριν τη φόρτωση: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Οι προειδοποιήσεις θα δείχνουν τότε την προσαρμοσμένη εναλλακτική αντί για την προεπιλογή του συστήματος.  

---

## Βήμα 5: Πλήρες Παράδειγμα (Έτοιμο για Αντιγραφή‑Επικόλληση)

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια αυτόνομη εφαρμογή κονσόλας που μπορείτε να μεταγλωττίσετε και να τρέξετε αμέσως.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα** (όταν το DOCX αναφέρει μια ελλιπή γραμματοσειρά):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Αν λείπει μια *κριτική* γραμματοσειρά όπως “Times New Roman”, θα δείτε το μήνυμα διακοπής αντίστοιχα.

---

## Συχνές Ερωτήσεις & Παράπλευρα Ζητήματα

| Ερώτηση | Απάντηση |
|----------|--------|
| **Πρέπει να καλέσω το `SetFontsFolder` για να καταγράψω προειδοποιήσεις;** | Όχι. Το συμβάν προειδοποίησης λειτουργεί με τις προεπιλεγμένες γραμματοσειρές του συστήματος. Χρησιμοποιήστε το `SetFontsFolder` μόνο όταν θέλετε να προσθέσετε επιπλέον εναλλακτικές γραμματοσειρές. |
| **Θα λειτουργήσει σε .NET Core / .NET 5+;** | Απόλυτα. Το Aspose.Words 24.10 υποστηρίζει όλα τα σύγχρονα .NET runtimes. Απλώς βεβαιωθείτε ότι το πακέτο NuGet ταιριάζει με το target framework σας. |
| **Τι αν θέλω να καταγράψω τις προειδοποιήσεις σε αρχείο αντί για την κονσόλα;** | Αντικαταστήστε το `Console.WriteLine(msg);` με οποιαδήποτε κλήση σε σύστημα logging, π.χ. `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Μπορώ να καταστέλλω προειδοποιήσεις για συγκεκριμένες γραμματοσειρές;** | Ναι. Μέσα στον χειριστή συμβάντος μπορείτε να φιλτράρετε: `if (e.FontName == "SomeFont") return;`. Έτσι έχετε λεπτομερή έλεγχο. |
| **Υπάρχει τρόπος να θεωρήσω τις ελλιπείς γραμματοσειρές ως σφάλματα;** | Ρίξτε μια εξαίρεση χειροκίνητα μέσα στον χειριστή όταν πληρούται μια συνθήκη, ή ορίστε μια σημαία και διακόψτε μετά τη δημιουργία του `Document`, όπως φαίνεται στο παράδειγμα. |

---

## Συμπέρασμα

Τώρα διαθέτετε ένα στέρεο, έτοιμο για παραγωγή μοτίβο για **πώς να καταγράψετε προειδοποιήσεις** που προκύπτουν κατά τη φόρτωση εγγράφων με ελλιπείς γραμματοσειρές. Με **ανίχνευση ελλιπών γραμματοσειρών**, **ρύθμιση των ρυθμίσεων γραμματοσειρών**, και **ορισμό load options** κατάλληλα, αποκτάτε πλήρη ορατότητα στα γεγονότα αντικατάστασης γραμματοσειρών και μπορείτε να αποφασίσετε αν θα τις καταγράψετε, θα χρησιμοποιήσετε εναλλακτικές ή θα διακόψετε τη διαδικασία.

Κάντε το επόμενο βήμα ενσωματώνοντας αυτή τη λογική στη γραμμή μετατροπής PDF, προσθέτοντας προσαρμοσμένες γραμματοσειρές εναλλακτικά, ή τροφοδοτώντας τη λίστα προειδοποιήσεων σε σύστημα παρακολούθησης. Η προσέγγιση κλιμακώνεται από μικρά βοηθητικά προγράμματα έως υπηρεσίες επεξεργασίας εγγράφων επιχειρησιακού επιπέδου.

---

### Περαιτέρω Ανάγνωση & Επόμενα Βήματα

- **Εξερευνήστε περισσότερες δυνατότητες του FontSettings** – ενσωμάτωση προσαρμοσμένων γραμματοσειρών, έλεγχος σειράς εναλλακτικών, και ζητήματα αδειοδότησης.  
- **Συνδυάστε με μετατροπή PDF** – μετά τη σύλληψη των προειδοποιήσεων, καλέστε `doc.Save("output.pdf");` και ελέγξτε ότι το PDF χρησιμοποιεί τις αναμενόμενες γραμματοσειρές.  
- **Αυτοματοποιήστε δοκιμές** – γράψτε unit tests που φορτώνουν έγγραφα με γνωστές ελλιπείς γραμματοσειρές και επαληθεύουν ότι η λίστα προειδοποιήσεων περιέχει τα αναμενόμενα μηνύματα.  

Αν αντιμετωπίσετε δυσκολίες ή έχετε ιδέες για βελτιώσεις, αφήστε ένα σχόλιο. Καλό κώδικα!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}