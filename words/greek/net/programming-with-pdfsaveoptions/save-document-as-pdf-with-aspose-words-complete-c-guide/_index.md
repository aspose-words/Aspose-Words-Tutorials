---
category: general
date: 2026-03-24
description: Αποθήκευση εγγράφου ως PDF χρησιμοποιώντας το Aspose.Words σε C#. Μάθετε
  πώς να μετατρέπετε το Word σε PDF και να ορίζετε προσαρμοσμένες ρυθμίσεις γραμματοσειράς
  για άψογη έξοδο.
draft: false
keywords:
- save document as pdf
- convert word to pdf
- set custom font settings
- Aspose.Words PDF conversion
- C# document automation
language: el
og_description: Αποθηκεύστε το έγγραφο ως PDF με το Aspose.Words. Αυτός ο οδηγός δείχνει
  πώς να μετατρέψετε το Word σε PDF και να ορίσετε προσαρμοσμένες ρυθμίσεις γραμματοσειράς
  για αξιόπιστα αποτελέσματα.
og_title: Αποθήκευση εγγράφου ως PDF – Πλήρης οδηγός C#
tags:
- Aspose.Words
- C#
- PDF
- Font Management
title: Αποθήκευση εγγράφου ως PDF με το Aspose.Words – Πλήρης οδηγός C#
url: /el/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου ως PDF με Aspose.Words – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί ποτέ πώς να **αποθηκεύσετε ένα έγγραφο ως PDF** χωρίς να αντιμετωπίζετε μυστηριώδεις προειδοποιήσεις αντικατάστασης γραμματοσειράς; Δεν είστε μόνοι. Σε πολλά έργα πρέπει να **μετατρέψουμε το Word σε PDF** διασφαλίζοντας ότι η ακριβής τυπογραφία που επέλεξε ο συγγραφέας εμφανίζεται στο τελικό αρχείο.  

Τα καλά νέα; Με μερικές γραμμές C# και Aspose.Words μπορείτε να κάνετε και τα δύο—**να αποθηκεύσετε το έγγραφο ως PDF** και **να ορίσετε προσαρμοσμένες ρυθμίσεις γραμματοσειράς** ώστε το αποτέλεσμα να ταιριάζει με τις προσδοκίες σας. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα, θα εξηγήσουμε γιατί κάθε κομμάτι είναι σημαντικό και θα σας δώσουμε ένα έτοιμο‑για‑εκτέλεση δείγμα κώδικα.

## Τι Θα Κερδίσετε

- Μια πλήρη, εκτελέσιμη εφαρμογή C# console που φορτώνει ένα `.docx`, εφαρμόζει προσαρμοσμένη διαχείριση γραμματοσειρών και **αποθηκεύει το έγγραφο ως PDF**.  
- Κατανόηση της αλυσίδας **convert Word to PDF** και του σημείου όπου μπορεί να εμφανιστεί αντικατάσταση γραμματοσειράς.  
- Συμβουλές για την αντιμετώπιση ελλιπών γραμματοσειρών, τη διαμόρφωση ιδιωτικών φακέλων γραμματοσειρών και την καταγραφή προειδοποιήσεων προγραμματιστικά.  

**Προαπαιτούμενα** – θα χρειαστείτε .NET 6+ (ή .NET Framework 4.7.2+), Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε) και ενεργή άδεια Aspose.Words (η δωρεάν δοκιμή λειτουργεί για αυτή τη demo). Δεν απαιτούνται άλλες βιβλιοθήκες τρίτων.

![Διάγραμμα που απεικονίζει τη ροή φόρτωσης αρχείου Word, εφαρμογής προσαρμοσμένων ρυθμίσεων γραμματοσειράς και αποθήκευσης ως PDF](/images/save-document-as-pdf-flow.png "Διάγραμμα ροής αποθήκευσης εγγράφου ως PDF")

---

## Εγκατάσταση Aspose.Words για .NET

Πριν γράψουμε κώδικα, βεβαιωθείτε ότι το πακέτο Aspose.Words είναι αναφορά στο έργο σας.

```bash
dotnet add package Aspose.Words.NET
```

> **Pro tip:** Αν χρησιμοποιείτε Visual Studio, κάντε δεξί‑κλικ στο project → *Manage NuGet Packages* → ψάξτε για *Aspose.Words.NET* και εγκαταστήστε την πιο πρόσφατη σταθερή έκδοση (ως Μάρτιο 2026 είναι η 24.9).

Η εγκατάσταση του πακέτου σας δίνει πρόσβαση στις κλάσεις `Document`, `LoadOptions`, `FontSettings` και τις κλάσεις callback προειδοποιήσεων που θα χρειαστούμε για να **ορίσουμε προσαρμοσμένες ρυθμίσεις γραμματοσειράς** αργότερα.

---

## Ορισμός Προσαρμοσμένων Ρυθμίσεων Γραμματοσειράς και Handler Προειδοποιήσεων

Το Aspose.Words αντικαθιστά αυτόματα μια ελλιπή γραμματοσειρά με μια γενική εναλλακτική, κάτι που συχνά καταστρέφει τη διάταξη. Για να διατηρήσετε τον έλεγχο, δημιουργούμε ένα αντικείμενο `FontSettings` και συνδέουμε ένα warning callback που εμφανίζει τυχόν γεγονότα **font substitution**.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Receives warning callbacks from Aspose.Words.
/// Only prints font‑substitution warnings to the console.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        // React only to font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"[Font substitution] Original: {info.Description}");
        }
    }
}

// Step 1: Create FontSettings and attach the warning handler.
FontSettings fontSettings = new FontSettings();
fontSettings.SetWarningCallback(new FontSubstitutionWarningHandler());

// OPTIONAL: Point Aspose.Words to a folder that contains your custom fonts.
// This is where the **set custom font settings** magic really shines.
string customFontFolder = Path.Combine(Environment.CurrentDirectory, "MyFonts");
if (Directory.Exists(customFontFolder))
{
    fontSettings.SetFontsFolder(customFontFolder, /*recursive=*/ true);
    Console.WriteLine($"Custom font folder registered: {customFontFolder}");
}
```

**Γιατί είναι σημαντικό:**  
- Η διεπαφή `IWarningCallback` σας παρέχει ένα hook στην αλυσίδα μετατροπής. Όταν το Aspose.Words δεν μπορεί να βρει τη ζητούμενη γραμματοσειρά, εκκινεί μια προειδοποίηση `FontSubstitution`. Καταγράφοντάς την, γνωρίζετε αμέσως ποιες γραμματοσειρές πρέπει να προστεθούν στη ιδιωτική σας συλλογή.  
- Η καταχώρηση ιδιωτικού φακέλου γραμματοσειρών μέσω `SetFontsFolder` είναι ο πυρήνας του **set custom font settings**. Σας επιτρέπει να συσκευάσετε γραμματοσειρές με την εφαρμογή σας, κάνοντας την απόδοση PDF ανεξάρτητη από τις γραμματοσειρές που είναι εγκατεστημένες στο μηχάνημα-στόχο.

---

## Φόρτωση του Εγγράφου Word με FontSettings

Τώρα που το περιβάλλον γραμματοσειρών είναι έτοιμο, φορτώνουμε το πηγαίο `.docx` περνώντας το `FontSettings` μέσω του `LoadOptions`. Αυτό εξασφαλίζει ότι το έγγραφο θα αποδοθεί χρησιμοποιώντας τις γραμματοσειρές που μόλις καταχωρήσαμε.

```csharp
// Step 2: Prepare load options that carry our FontSettings.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};

// Path to the source Word file – replace with your actual file.
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; any missing fonts will trigger our warning handler.
Document document = new Document(inputPath, loadOptions);
Console.WriteLine($"Loaded '{Path.GetFileName(inputPath)}' successfully.");
```

**Διαχείριση ειδικών περιπτώσεων:**  
- Αν το `input.docx` αναφέρει μια γραμματοσειρά που δεν υπάρχει στο σύστημα **και** δεν βρίσκεται στο `MyFonts`, ο handler προειδοποιήσεων θα εκτυπώσει μήνυμα, αλλά η μετατροπή θα ολοκληρωθεί χρησιμοποιώντας εναλλακτική.  
- Για μεγάλα έγγραφα, σκεφτείτε να ορίσετε ρητά `LoadOptions.LoadFormat = LoadFormat.Docx` ώστε να αποφύγετε το κόστος αυτόματης ανίχνευσης.

---

## Αποθήκευση Εγγράφου ως PDF και Καταγραφή Αντικαταστάσεων

Με το έγγραφο στη μνήμη και τη δική μας διαμόρφωση γραμματοσειρών ενεργή, το τελευταίο βήμα είναι η πραγματική κλήση **save document as PDF**. Όλες οι προειδοποιήσεις αντικατάστασης γραμματοσειράς έχουν ήδη εκδοθεί κατά τη φάση φόρτωσης, αλλά μπορείτε επίσης να συλλάβετε προειδοποιήσεις που προκύπτουν κατά την αποθήκευση.

```csharp
// Step 3: Define the output PDF path.
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");

// Save the document as PDF. Any additional warnings will flow through the same handler.
document.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to '{outputPath}'.");
```

Όταν τρέξετε το πρόγραμμα, η κονσόλα θα εμφανίσει γραμμές όπως:

```
[Font substitution] Original: "Calibri" (fallback: "Arial")
Custom font folder registered: C:\Projects\MyApp\MyFonts
Loaded 'input.docx' successfully.
PDF saved to 'C:\Projects\MyApp\output.pdf'.
```

Αν δείτε μηνύματα αντικατάστασης, απλώς τοποθετήστε το αρχείο της ελλιπούς γραμματοσειράς στο `MyFonts` και ξανατρέξτε—το PDF θα αποδοθεί τώρα με την επιθυμητή γραμματοσειρά.

---

## Επαλήθευση Αποτελέσματος και Αντιμετώπιση Συνηθισμένων Προβλημάτων

### Γρήγορος έλεγχος λογικής

Ανοίξτε το `output.pdf` σε οποιονδήποτε προβολέα PDF. Το κείμενο πρέπει να φαίνεται ακριβώς όπως στο αρχικό αρχείο Word, και οι γραμματοσειρές που εμφανίζονται στις ιδιότητες του εγγράφου πρέπει να ταιριάζουν με αυτές που τοποθετήσατε στο `MyFonts`.

### Τι κάνετε αν το PDF εξακολουθεί να εμφανίζει λάθος γραμματοσειρά;

1. **Επαληθεύστε το όνομα της γραμματοσειράς** – Το Aspose.Words είναι case‑sensitive. Το όνομα που χρησιμοποιείται στο αρχείο Word πρέπει να ταιριάζει με το όνομα του αρχείου (χωρίς επέκταση) της γραμματοσειράς που προσθέσατε.  
2. **Βεβαιωθείτε ότι το αρχείο γραμματοσειράς υποστηρίζεται** – Τα TrueType (`.ttf`) και OpenType (`.otf`) είναι ασφαλή· τα PostScript Type 1 μπορεί να απαιτούν πρόσθετη άδεια.  
3. **Καθαρίστε την cache γραμματοσειρών** – Περιστασιακά η βιβλιοθήκη αποθηκεύει στην cache πληροφορίες ελλιπών γραμματοσειρών. Διαγράψτε το φάκελο `Aspose.Words.Fonts` στον προσωρινό φάκελο του χρήστη (`%TEMP%`) και ξανατρέξτε.

### Προχωρημένο σενάριο: Χρήση πολλαπλών ιδιωτικών φακέλων γραμματοσειρών

Αν το έργο σας περιλαμβάνει γραμματοσειρές για διαφορετικές γλώσσες (π.χ. Λατινικά και Κυριλλικά), καταχωρήστε κάθε φάκελο:

```csharp
fontSettings.SetFontsFolder(@"C:\MyApp\Fonts\Latin", true);
fontSettings.SetFontsFolder(@"C:\MyApp\Fonts\Cyrillic", true);
```

Το Aspose.Words θα τα ψάξει με τη σειρά που προστέθηκαν, δίνοντάς σας ακριβή έλεγχο για το ποια έκδοση γραμματοσειράς θα προτεραιοποιηθεί.

---

## Πλήρες Παράδειγμα Εργασίας (Αντιγραφή‑Επικόλληση)

Ακολουθεί το **πλήρες πρόγραμμα** που μπορείτε να μεταγλωττίσετε και να εκτελέσετε. Δείχνει όλα όσα συζητήσαμε—from την εγκατάσταση του πακέτου NuGet μέχρι την **αποθήκευση του εγγράφου ως PDF** ενώ **ορίζετε προσαρμοσμένες ρυθμίσεις γραμματοσειράς** και διαχειρίζεστε προειδοποιήσεις.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------------------------------------------------------
        // 1️⃣ Set up custom font handling and warning callback.
        // ---------------------------------------------------------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetWarningCallback(new FontSubstitutionWarningHandler());

        // Register a private font folder (optional but recommended).
        string customFontFolder = Path.Combine(Environment.CurrentDirectory, "MyFonts");
        if (Directory.Exists(customFontFolder))
        {
            fontSettings.SetFontsFolder(customFontFolder, true);
            Console.WriteLine($"Custom font folder registered: {customFontFolder}");
        }

        // ---------------------------------------------------------
        // 2️⃣ Load the Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}