---
category: general
date: 2026-03-06
description: Καταγράψτε τις προειδοποιήσεις γραμματοσειρών κατά τη φόρτωση ενός εγγράφου
  Word σε C#. Μάθετε πώς να εντοπίζετε τις ελλιπείς γραμματοσειρές, να ελέγχετε τις
  γραμματοσειρές του εγγράφου και να διαχειρίζεστε αποτελεσματικά τις ελλιπείς γραμματοσειρές.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: el
og_description: Καταγράψτε τις προειδοποιήσεις γραμματοσειρών κατά τη φόρτωση ενός
  εγγράφου Word σε C#. Αυτό το σεμινάριο δείχνει πώς να εντοπίσετε ελλείπουσες γραμματοσειρές,
  να ελέγξετε τις γραμματοσειρές του εγγράφου και να διαχειριστείτε τις ελλείπουσες
  γραμματοσειρές.
og_title: Καταγραφή Προειδοποιήσεων Γραμματοσειράς σε C# – Πλήρης Οδηγός
tags:
- Aspose.Words
- C#
- Font Management
title: Καταγραφή Προειδοποιήσεων Γραμματοσειράς σε C# – Πλήρης Οδηγός
url: /el/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταγραφή Προειδοποιήσεων Γραμματοσειρών σε C# – Πλήρης Οδηγός

Έχετε χρειαστεί ποτέ να **καταγράψετε προειδοποιήσεις γραμματοσειρών** κατά την επεξεργασία ενός εγγράφου Word; Η καταγραφή προειδοποιήσεων γραμματοσειρών είναι απαραίτητη για **την ανίχνευση ελλιπών γραμματοσειρών** και για να διασφαλίσετε ότι το τελικό αποτέλεσμα φαίνεται ακριβώς όπως το θέλετε.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πρακτικό, ολοκληρωμένο παράδειγμα που φορτώνει ένα αρχείο `.docx`, παρακολουθεί τη διαδικασία φόρτωσης και αναφέρει τυχόν αντικαταστάσεις γραμματοσειρών. Στο τέλος θα ξέρετε πώς να **φορτώνετε ασφαλώς ένα έγγραφο Word**, **να ελέγχετε τις γραμματοσειρές του εγγράφου** και **να διαχειρίζεστε ελλιπείς γραμματοσειρές** χωρίς ανεπιθύμητα σφάλματα χρόνου εκτέλεσης.

## Τι Θα Μάθετε

- Πώς να συνδέσετε έναν συλλέκτη προειδοποιήσεων σε ένα `Document` του Aspose.Words.  
- Ποιοι τύποι προειδοποιήσεων υποδεικνύουν ελλιπή ή αντικατεστημένη γραμματοσειρά.  
- Τρόποι καταγραφής ή αντίδρασης σε αυτές τις προειδοποιήσεις σε μια εφαρμογή παραγωγικού επιπέδου.  
- Συμβουλές για τη ρύθμιση προσαρμοσμένων πηγών γραμματοσειρών εάν χρειάζεται να **διαχειριστείτε ελλιπείς γραμματοσειρές** με χάρη.

> **Προαπαιτούμενο:** Διαθέτετε έγκυρη άδεια Aspose.Words for .NET (ή χρησιμοποιείτε τη δωρεάν δοκιμή) και περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή VS Code). Δεν απαιτούνται άλλες βιβλιοθήκες.

---

## Καταγραφή Προειδοποιήσεων Γραμματοσειρών – Βήμα‑Βήμα

Παρακάτω βρίσκεται ο πλήρης, εκτελέσιμος κώδικας. Κάθε τμήμα είναι χωρισμένο σε δικό του βήμα ώστε να μπορείτε να το αντιγράψετε‑επικολλήσετε, να πειραματιστείτε και να επεκτείνετε τη λογική.

![Καταγραφή προειδοποιήσεων γραμματοσειρών](image.png "Διάγραμμα που δείχνει τη συλλογή προειδοποιήσεων"){: alt="καταγραφή προειδοποιήσεων γραμματοσειρών"}

### Βήμα 1: Φόρτωση του Εγγράφου Word

Πρώτα, πρέπει να **φορτώσετε ένα έγγραφο Word** που μπορεί να περιέχει γραμματοσειρές που δεν είναι εγκατεστημένες στο τρέχον μηχάνημα. Ο κατασκευαστής `Document` κάνει το βαριά έργο, αλλά θα κρατήσουμε την κλήση απομονωμένη ώστε να μπορείτε να την αντικαταστήσετε με stream ή byte array αργότερα, αν χρειαστεί.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Γιατί είναι σημαντικό:** Η φόρτωση ενός εγγράφου χωρίς χειριστή προειδοποιήσεων σημαίνει ότι οποιαδήποτε αντικατάσταση γραμματοσειράς αγνοείται σιωπηλά. Ορίζοντας το `WarningCallback` *πριν* τη φόρτωση, εγγυόμαστε ότι θα δούμε κάθε προειδοποίηση `FontSubstitution` που συμβαίνει.

### Βήμα 2: Σύνδεση Συλλέκτη Προειδοποιήσεων

Η κλάση `WarningInfoCollector` είναι μια ενσωματωμένη υλοποίηση του `IWarningCallback`. Απλώς αποθηκεύει κάθε προειδοποίηση σε μια λίστα που μπορούμε να εξετάσουμε αργότερα.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Pro tip:** Εάν χρειάζεται να **διαχειριστείτε ελλιπείς γραμματοσειρές** πιο επιθετικά (π.χ. να διακόψετε τη φόρτωση ή να αντικαταστήσετε με συγκεκριμένη εναλλακτική), μπορείτε να αντικαταστήσετε το `Console.WriteLine` με προσαρμοσμένη λογική — να ρίξετε εξαίρεση, να καταγράψετε σε αρχείο ή ακόμη και να προσθέσετε προσαρμοσμένη πηγή γραμματοσειράς.

### Βήμα 3: Επαλήθευση του Αποτελέσματος

Τρέξτε το πρόγραμμα από τη γραμμή εντολών. Εάν το `input.docx` χρησιμοποιεί μια γραμματοσειρά που δεν είναι εγκατεστημένη, θα δείτε γραμμές όπως:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Αν δεν εμφανιστεί έξοδος, το έγγραφο είτε χρησιμοποίησε μόνο γραμματοσειρές που είναι ήδη διαθέσιμες **ή** το Aspose.Words βρήκε μια ταιριαστή γραμματοσειρά στη ενσωματωμένη συλλογή εναλλακτικών. Σε κάθε περίπτωση, έχετε **ελέγξει τις γραμματοσειρές του εγγράφου** με επιτυχία.

---

## Ανίχνευση Ελλιπών Γραμματοσειρών Χωρίς Άδεια (Δωρεάν Δοκιμή)

Ακόμη και αν χρησιμοποιείτε τη δοκιμαστική έκδοση 30 ημερών, ο μηχανισμός προειδοποιήσεων λειτουργεί ακριβώς το ίδιο. Η μόνη διαφορά είναι ότι η δοκιμή προσθέτει υδατογράφημα στο παραγόμενο αρχείο, το οποίο **δεν** επηρεάζει τη συλλογή προειδοποιήσεων. Έτσι μπορείτε με ασφάλεια να **ανιχνεύσετε ελλιπείς γραμματοσειρές** πριν αποφασίσετε να αγοράσετε πλήρη άδεια.

---

## Διαχείριση Ελλιπών Γραμματοσειρών – Προχωρημένες Επιλογές

Μερικές φορές θέλετε να παρέχετε τα δικά σας αρχεία γραμματοσειρών (π.χ. εταιρικές γραμματοσειρές) ώστε η αντικατάσταση να μην συμβαίνει ποτέ. Το Aspose.Words σας επιτρέπει να καταχωρίσετε προσαρμοσμένους φακέλους γραμματοσειρών:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Τοποθετήστε τον παραπάνω κώδικα **πριν** φορτώσετε το έγγραφο εάν θέλετε ο φορτωτής να λάβει υπόψη αυτές τις γραμματοσειρές κατά το αρχικό στάδιο ανάλυσης. Αυτή είναι η πιο αξιόπιστη μέθοδος για **διαχείριση ελλιπών γραμματοσειρών** χωρίς να εξαρτάστε από τις προεπιλεγμένες συστημικές γραμματοσειρές.

---

## Συνηθισμένα Πιθανά Προβλήματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Λύση |
|----------|----------------|------|
| **Συλλέκτης προειδοποιήσεων συνδέθηκε μετά τη φόρτωση** | Το έγγραφο έχει ήδη αναλυθεί, οπότε δεν καταγράφονται προειδοποιήσεις. | Συνδέστε το `WarningCallback` **πριν** καλέσετε `new Document(path)`. |
| **Εμφανίζονται μόνο γενικές προειδοποιήσεις** | Φιλτράρατε τον λάθος `WarningType`. | Χρησιμοποιήστε `WarningType.FontSubstitution` για να εστιάσετε στα ζητήματα γραμματοσειρών. |
| **Δεν υπάρχει έξοδος παρόλο που λείπουν γραμματοσειρές** | Το Aspose.Words βρήκε ενσωματωμένη εναλλακτική (π.χ. Arial). | Απενεργοποιήστε τις ενσωματωμένες εναλλακτικές μέσω `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Πτώση απόδοσης κατά το σκανάρισμα μεγάλων εγγράφων** | Η συλλογή κάθε προειδοποίησης μπορεί να είναι δαπανηρή. | Περιορίστε τη συλλογή μόνο σε `FontSubstitution`, ή επεξεργαστείτε τις προειδοποιήσεις σε παρτίδες. |

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα** (υποθέτοντας δύο ελλιπείς γραμματοσειρές):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Εάν η κονσόλα παραμείνει σιωπηλή εκτός από το μήνυμα “Document loaded successfully”, έχετε **ελέγξει τις γραμματοσειρές του εγγράφου** και δεν βρέθηκαν ελλιπείς.

---

## Συμπέρασμα

Σας δείξαμε πώς να **καταγράψετε προειδοποιήσεις γραμματοσειρών** σε C# χρησιμοποιώντας το Aspose.Words, έναν αξιόπιστο τρόπο για **ανίχνευση ελλιπών γραμματοσειρών**, **ασφαλή φόρτωση εγγράφου Word**, **έλεγχο γραμματοσειρών εγγράφου** και **διαχείριση ελλιπών γραμματοσειρών** μέσω προσαρμοσμένων πηγών γραμματοσειρών.  

Με αυτό το πρότυπο μπορείτε να ενσωματώσετε την επαλήθευση γραμματοσειρών σε οποιοδήποτε pipeline αυτοματοποίησης — είτε δημιουργείτε PDFs, μετατρέπετε σε HTML, είτε απλώς αρχειοθετείτε αρχεία Word.

### Τι Ακολουθεί;

- Εξερευνήστε το API **FontSettings.SubstitutionSettings** για να ορίσετε τους δικούς σας κανόνες εναλλακτικών.  
- Συνδυάστε τη συλλογή προειδοποιήσεων με ένα πλαίσιο καταγραφής (Serilog, NLog) για παρακολούθηση σε παραγωγικό περιβάλλον.  
- Χρησιμοποιήστε την ίδια προσέγγιση για να καταγράψετε άλλους τύπους προειδοποιήσεων, όπως ανάλυση εικόνας ή μη υποστηριζόμενες λειτουργίες.

Έχετε περισσότερες ερωτήσεις σχετικά με τη διαχείριση γραμματοσειρών ή το Aspose.Words γενικότερα; Αφήστε ένα σχόλιο ή επισκεφθείτε τα φόρουμ της κοινότητας Aspose. Καλό προγραμματισμό, και εύχομαι τα έγγραφά σας να εμφανίζονται πάντα με τις γραμματοσειρές που περιμένετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}