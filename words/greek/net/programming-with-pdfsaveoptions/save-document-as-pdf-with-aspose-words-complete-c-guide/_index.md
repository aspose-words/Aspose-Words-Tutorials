---
category: general
date: 2026-02-15
description: Αποθηκεύστε το έγγραφο ως PDF χρησιμοποιώντας το Aspose.Words σε C#.
  Μάθετε πώς να μετατρέπετε το Word σε PDF, να καταγράφετε προειδοποιήσεις γραμματοσειρών
  και να εξασφαλίζετε ακριβή έξοδο.
draft: false
keywords:
- save document as pdf
- convert word to pdf
- word to pdf conversion
- export word as pdf
- pdf conversion from word
language: el
og_description: Αποθηκεύστε το έγγραφο ως PDF χρησιμοποιώντας το Aspose.Words σε C#.
  Αυτός ο οδηγός δείχνει πώς να μετατρέψετε το Word σε PDF ενώ διαχειρίζεστε προειδοποιήσεις
  αντικατάστασης γραμματοσειρών.
og_title: Αποθήκευση εγγράφου ως PDF με το Aspose.Words – Πλήρης οδηγός C#
tags:
- Aspose.Words
- C#
- PDF generation
title: Αποθήκευση εγγράφου ως PDF με το Aspose.Words – Πλήρης οδηγός C#
url: /el/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφου ως PDF με Aspose.Words – Πλήρης οδηγός C# 

Έχετε χρειαστεί ποτέ να **αποθηκεύσετε έγγραφο ως PDF** αλλά δεν ήσασταν σίγουροι πώς να διατηρήσετε κάθε γραμματοσειρά αμετάβλητη; Δεν είστε μόνοι. Σε πολλά εταιρικά έργα τα αρχεία Word που λαμβάνουμε αναφέρονται σε γραμματοσειρές που απλώς δεν είναι εγκατεστημένες στον διακομιστή, και η μετατροπή τις αντικαθιστά σιωπηρά.  

Σε αυτό το tutorial θα περάσουμε από ένα σενάριο **convert Word to PDF** που όχι μόνο δημιουργεί ένα τέλειο PDF αλλά και σας λέει ακριβώς ποιες γραμματοσειρές αντικαταστάθηκαν. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση πρόγραμμα C#, μια σαφή κατανόηση του γιατί κάθε βήμα είναι σημαντικό, και μερικές επαγγελματικές συμβουλές που μπορείτε να ενσωματώσετε στον κώδικά σας.

> **Τι θα λάβετε:** μια πλήρη λίστα κώδικα, εξήγηση του warning callback, αναμενόμενη έξοδος κονσόλας, και προτάσεις για διαχείριση ειδικών περιπτώσεων όπως προσαρμοσμένοι φάκελοι γραμματοσειρών.

---

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- **.NET 6.0** (ή οποιαδήποτε πρόσφατη έκδοση .NET) – το Aspose.Words λειτουργεί με .NET Framework, .NET Core και .NET 5/6.  
- **Aspose.Words for .NET** πακέτο NuGet (`Install-Package Aspose.Words`) – η βιβλιοθήκη που κάνει τη βαριά δουλειά.  
- Ένα αρχείο Word που αναφέρει μια ελλιπή γραμματοσειρά (π.χ., `MissingFont.docx`). Αν δεν έχετε κάποιο, δημιουργήστε ένα απλό έγγραφο και αλλάξτε τη γραμματοσειρά σε κάτι που ξέρετε ότι δεν είναι εγκατεστημένο στο σύστημά σας, όπως “Papyrus”.  
- Ένα IDE με το οποίο αισθάνεστε άνετα – Visual Studio, Rider ή ακόμη και VS Code θα δουλέψουν.  

Αυτό είναι όλο. Χωρίς επιπλέον SDKs, χωρίς COM interop, μόνο ένα καθαρό έργο C#.

---

## Βήμα 1 – Φόρτωση του αρχείου Word (Πρώτο βήμα στο Convert Word to PDF)

Το πρώτο πράγμα που χρειαζόμαστε είναι ένα αντικείμενο `Document` που αντιπροσωπεύει το πηγαίο αρχείο Word. Το Aspose.Words διαβάζει το `.docx` (ή `.doc`) και δημιουργεί ένα μοντέλο στη μνήμη που μπορείτε να επεξεργαστείτε.

```csharp
using Aspose.Words;
using Aspose.Words.Warnings;

// Path to the source Word document that may reference missing fonts.
string sourcePath = @"C:\Docs\MissingFont.docx";

// Create the Document instance – this loads the file into memory.
Document document = new Document(sourcePath);
```

> **Γιατί είναι σημαντικό:** Η πρώιμη φόρτωση του αρχείου επιτρέπει στη βιβλιοθήκη να αναλύσει τις αναφορές γραμματοσειρών. Αν λείπει μια γραμματοσειρά, το Aspose.Words θα εκδώσει αργότερα μια προειδοποίηση `FontSubstitution`, την οποία μπορούμε να συλλάβουμε.

---

## Βήμα 2 – Προσθήκη Warning Callback για σύλληψη αντικαταστάσεων γραμματοσειρών

Το Aspose.Words εκδίδει προειδοποιήσεις μέσω ενός μηχανισμού callback. Αναθέτοντας ένα `WarningInfoCollection` στο `document.WarningCallback`, συλλέγουμε κάθε προειδοποίηση που συμβαίνει κατά την επεξεργασία.

```csharp
// Create a collection that will hold any warnings generated.
WarningInfoCollection warningCollection = new WarningInfoCollection();

// Register the collection as the document's warning callback.
document.WarningCallback = warningCollection;
```

> **Συμβουλή επαγγελματία:** Μπορείτε επίσης να υλοποιήσετε το `IWarningCallback` μόνοι σας αν χρειάζεστε προσαρμοσμένο logging ή θέλετε να διακόψετε σε ορισμένες προειδοποιήσεις. Η προσέγγιση με τη συλλογή είναι γρήγορη και τέλεια για τις περισσότερες περιπτώσεις.

---

## Βήμα 3 – Αποθήκευση εγγράφου ως PDF – Η βασική λειτουργία

Τώρα λέμε στο Aspose.Words να αποδώσει το περιεχόμενο του Word σε αρχείο PDF. Αυτή είναι η στιγμή που οποιαδήποτε ελλιπής γραμματοσειρά αντικαθίσταται, και η προειδοποίηση που ρυθμίσαμε νωρίτερα ενεργοποιείται.

```csharp
// Destination PDF path.
string pdfPath = @"C:\Docs\Result.pdf";

// Perform the conversion. This call may trigger FontSubstitution warnings.
document.Save(pdfPath);
```

> **Τι συμβαίνει στο παρασκήνιο;** Το Aspose.Words διασχίζει κάθε παράγραφο, αναζητά τη απαιτούμενη γραμματοσειρά, και αν δεν τη βρει, επιστρέφει σε μια προεπιλεγμένη αντικατάσταση (συνήθως Arial). Η προειδοποίηση σας λέει ακριβώς ποια γραμματοσειρά έλειπε και ποια χρησιμοποιήθηκε αντί αυτού.

---

## Βήμα 4 – Ανάλυση και αναφορά αντικαταστάσεων γραμματοσειρών

Μετά τη λειτουργία αποθήκευσης, επαναλαμβάνουμε τις συλλεγμένες προειδοποιήσεις. Αν κάποια προειδοποίηση είναι τύπου `FontSubstitution`, την μετατρέπουμε σε `FontSubstitutionWarning` για να εξάγουμε τα ονόματα της αρχικής και της αντικατεστημένης γραμματοσειράς.

```csharp
// Loop through all captured warnings.
foreach (WarningInfo warning in warningCollection)
{
    // We're only interested in font substitution warnings.
    if (warning.Type == WarningType.FontSubstitution)
    {
        var fontWarning = (FontSubstitutionWarning)warning;
        Console.WriteLine(
            $"Substituted '{fontWarning.OriginalFontName}' with '{fontWarning.SubstitutedFontName}'. Reason: {fontWarning.Reason}");
    }
}
```

**Δείγμα εξόδου κονσόλας**

```
Substituted 'Papyrus' with 'Arial Unicode MS'. Reason: Font not found on the system.
```

Αν το πηγαίο έγγραφο χρησιμοποιεί μόνο εγκατεστημένες γραμματοσειρές, η επανάληψη ολοκληρώνεται απλώς χωρίς να τυπώσει κάτι – ένα καθαρό σημάδι ότι η λειτουργία **save document as PDF** ολοκληρώθηκε χωρίς αντικαταστάσεις.

---

### Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας όλα, εδώ είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Επικολλήστε το σε ένα νέο έργο κονσόλας, προσαρμόστε τις διαδρομές αρχείων, και πατήστε **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that may reference missing fonts.
        string sourcePath = @"C:\Docs\MissingFont.docx";
        Document document = new Document(sourcePath);

        // 2️⃣ Prepare a warning collection to capture any font substitution messages.
        WarningInfoCollection warningCollection = new WarningInfoCollection();
        document.WarningCallback = warningCollection;

        // 3️⃣ Save the document as PDF – this step triggers the conversion.
        string pdfPath = @"C:\Docs\Result.pdf";
        document.Save(pdfPath);

        // 4️⃣ Review the warnings and report any font substitutions.
        foreach (WarningInfo warning in warningCollection)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                var fontWarning = (FontSubstitutionWarning)warning;
                Console.WriteLine(
                    $"Substituted '{fontWarning.OriginalFontName}' with '{fontWarning.SubstitutedFontName}'. Reason: {fontWarning.Reason}");
            }
        }

        Console.WriteLine("Conversion finished. Check the PDF and console output for details.");
    }
}
```

> **Αναμενόμενο αποτέλεσμα:** Ένα αρχείο `Result.pdf` εμφανίζεται στον φάκελο προορισμού, και η κονσόλα τυπώνει τυχόν αντικαταστάσεις γραμματοσειρών που συνέβησαν. Ανοίξτε το PDF σε έναν προβολέα – θα πρέπει να δείτε την ίδια διάταξη με το αρχικό αρχείο Word, εκτός από τις ελλιπείς γραμματοσειρές που αντικαταστάθηκαν.

---

## Διαχείριση ειδικών περιπτώσεων και κοινών παραλλαγών

### 1. Παροχή προσαρμοσμένου φακέλου γραμματοσειρών

Αν το περιβάλλον ανάπτυξης σας έχει μια ιδιωτική συλλογή εταιρικών γραμματοσειρών, μπορείτε να κατευθύνετε το Aspose.Words σε αυτόν τον φάκελο:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
document.FontSettings = fontSettings;
```

Τώρα η βιβλιοθήκη θα ψάξει το `C:\MyCompany\Fonts` πριν επιστρέψει στις συστημικές γραμματοσειρές, μειώνοντας την πιθανότητα ανεπιθύμητων αντικαταστάσεων.

### 2. Καταστολή προειδοποιήσεων όταν δεν τις χρειάζεστε

Μερικές φορές θέλετε απλώς μια σιωπηλή μετατροπή. Μπορείτε να αντικαταστήσετε το `WarningInfoCollection` με ένα κενό callback:

```csharp
document.WarningCallback = new WarningCallback(); // No‑op implementation
```

### 3. Μετατροπή πολλαπλών εγγράφων σε παρτίδα

Τυλίξτε τη λογική σε έναν βρόχο `foreach` πάνω σε έναν φάκελο με αρχεία `.docx`. Θυμηθείτε να επανεκκινήσετε το `WarningInfoCollection` για κάθε έγγραφο ώστε οι προειδοποιήσεις να παραμείνουν απομονωμένες.

```csharp
foreach (var file in Directory.GetFiles(@"C:\Docs\Batch", "*.docx"))
{
    Document doc = new Document(file);
    var warnings = new WarningInfoCollection();
    doc.WarningCallback = warnings;
    string outPdf = Path.ChangeExtension(file, ".pdf");
    doc.Save(outPdf);
    // Process warnings as shown earlier…
}
```

---

## Οπτική επισκόπηση

![Διάγραμμα ροής αποθήκευσης εγγράφου ως PDF που δείχνει τα βήματα φόρτωσης, σύλληψη προειδοποιήσεων, αποθήκευσης και αναφοράς](save-document-as-pdf-workflow.png)

*Alt text: Διάγραμμα που απεικονίζει τα βήματα για την αποθήκευση εγγράφου ως PDF ενώ καταγράφονται οι προειδοποιήσεις αντικατάστασης γραμματοσειρών.*

---

## Συμπέρασμα

Μόλις περάσαμε από μια ροή εργασίας **save document as PDF** που όχι μόνο μετατρέπει ένα αρχείο Word σε PDF αλλά και σας παρέχει πλήρη διαφάνεια σε οποιαδήποτε αντικατάσταση γραμματοσειράς συμβαίνει. Συνδέοντας ένα warning callback, μετατρέπετε μια σιωπηλή εναλλακτική λύση σε επεξεργάσιμες πληροφορίες — ιδανικό για περιβάλλοντα με αυστηρές απαιτήσεις συμμόρφωσης όπου κάθε γλύφη έχει σημασία.

Για να το συνοψίσουμε σε μία πρόταση: *Φορτώστε το αρχείο Word, συνδέστε μια συλλογή προειδοποιήσεων, αποθηκεύστε ως PDF, και στη συνέχεια επαναλάβετε τις προειδοποιήσεις για να καταγράψετε τυχόν αντικαταστάσεις γραμματοσειρών.*  

Αν ψάχνετε να **convert Word to PDF** σε άλλα πλαίσια, εξετάστε τις προχωρημένες επιλογές του Aspose.Words όπως `PdfSaveOptions` για συμπίεση εικόνων, συμμόρφωση PDF/A ή ψηφιακές υπογραφές

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}