---
category: general
date: 2026-05-23
description: Ορίστε την κλήση επιστροφής προειδοποίησης του Aspose για να καταγράψετε
  τις προειδοποιήσεις αντικατάστασης γραμματοσειρών στο Aspose.Words. Μάθετε για το
  LoadOptions, το FontSettings και την υλοποίηση του IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: el
og_description: Ορίστε την κλήση προειδοποίησης Aspose για την παρακολούθηση αντικατάστασης
  γραμματοσειρών στο Aspose.Words. Αυτό το σεμινάριο δείχνει τη χρήση των LoadOptions,
  FontSettings και την υλοποίηση του διαχειριστή προειδοποιήσεων.
og_title: Ορισμός της κλήσης προειδοποίησης aspose – Οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Ορισμός callback προειδοποίησης Aspose – Πλήρης Οδηγός για τη Φόρτωση Εγγράφων
  Word
url: /el/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός warning callback aspose – Πλήρης Οδηγός για Φόρτωση Εγγράφων Word

Έχετε αναρωτηθεί ποτέ πώς να **set warning callback aspose** ώστε να μην χάσετε ποτέ ξανά μια ειδοποίηση αντικατάστασης γραμματοσειράς; Δεν είστε μόνοι. Όταν ένα DOCX αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, το Aspose.Words την αντικαθιστά σιωπηλά, και χωρίς ένα κατάλληλο callback μπορεί να μην γνωρίζετε ποτέ ότι κάτι άλλαξε.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα ένα πλήρες, εκτελέσιμο παράδειγμα που δείχνει ακριβώς πώς να συλλάβετε αυτές τις προειδοποιήσεις. Στο τέλος θα κατανοήσετε **Aspose.Words LoadOptions**, πώς να ρυθμίσετε **FontSettings**, και γιατί η υλοποίηση του **IWarningCallback** είναι ο πιο καθαρός τρόπος να παραμένετε ενήμεροι. Χωρίς περιττά—απλώς ο κώδικας που μπορείτε να ενσωματώσετε σε ένα .NET project σήμερα.

## Τι Θα Μάθετε

- Πώς να **set warning callback aspose** σε ένα αντικείμενο `LoadOptions`.  
- Ο ρόλος του **Aspose.Words LoadOptions** κατά το άνοιγμα ενός εγγράφου.  
- Διαμόρφωση της διαχείρισης **Aspose fonts substitution** με `FontSettings`.  
- Γραφή μιας προσαρμοσμένης υλοποίησης **IWarningCallback** για την καταγραφή προβλημάτων γραμματοσειρών.  
- Φόρτωση ενός εγγράφου με ασφάλεια χρησιμοποιώντας τις βέλτιστες πρακτικές **Aspose document loading**.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.5+).  
- Ένα έγκυρο license Aspose.Words για .NET ή κλειδί δοκιμής.  
- Visual Studio, Rider ή οποιονδήποτε επεξεργαστή C# προτιμάτε.  
- Ένα δείγμα DOCX (`fontTest.docx`) που αναφέρει μια ελλιπή γραμματοσειρά (προαιρετικό αλλά χρήσιμο).

> **Pro tip:** Αν δεν έχετε ένα DOCX με ελλιπή γραμματοσειρά, απλώς μετονομάστε μια γραμματοσειρά στο στυλ του εγγράφου και παρακολουθήστε την προειδοποίηση.

## Πώς να ορίσετε το warning callback aspose για τη φόρτωση εγγράφου

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα. Αποθηκεύστε το ως `Program.cs`, επαναφέρετε τα πακέτα NuGet και τρέξτε το. Η κονσόλα θα εκτυπώσει κάθε προειδοποίηση αντικατάστασης γραμματοσειράς που δημιουργεί το Aspose.Words κατά τη φόρτωση του αρχείου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Αναμενόμενη έξοδος κονσόλας

Αν το `fontTest.docx` αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, θα δείτε κάτι όπως:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Αν όλες οι γραμματοσειρές είναι παρούσες, η μόνη γραμμή που θα εκτυπωθεί θα είναι *Document loaded successfully*—χωρίς προειδοποιήσεις, χωρίς θόρυβο.

![παράδειγμα set warning callback aspose](image.png "παράδειγμα set warning callback aspose")

## Κατανόηση του LoadOptions στο Aspose.Words

`LoadOptions` είναι η πύλη για κάθε ρύθμιση που μπορείτε να κάνετε στο **aspose document loading**. Σας επιτρέπει να:

1. **Καθορίσετε προσαρμοσμένο `FontSettings`** – χρήσιμο όταν η εφαρμογή σας παρέχει τις δικές της γραμματοσειρές.  
2. **Συνδέσετε ένα warning callback** – ακριβώς ό,τι κάναμε για να εντοπίσουμε τις αντικαταστάσεις γραμματοσειρών.  
3. Έλεγχο της ανίχνευσης μορφής εγγράφου, διαχείρισης κωδικών πρόσβασης και άλλα.

Επειδή το `LoadOptions` περνάει στον κατασκευαστή `Document`, οι ρυθμίσεις εφαρμόζονται **μια φορά**, ακριβώς τη στιγμή που το αρχείο αναλύεται. Γι' αυτό μπορούμε να εγγυηθούμε ότι ο διαχειριστής προειδοποιήσεων θα δει κάθε αντικατάσταση πριν το έγγραφο ακόμη και να δημιουργηθεί στη μνήμη.

### Πότε να χρησιμοποιήσετε προσαρμοσμένο LoadOptions

- **Batch processing** πολλών αρχείων όπου θέλετε μια ενιαία στρατηγική καταγραφής.  
- **Cloud services** που χρειάζεται να αναφέρουν τις ελλιπείς γραμματοσειρές στον καλούντα.  
- **Testing pipelines** που επαληθεύουν ότι τα έγγραφα τηρούν την εταιρική πολιτική γραμματοσειρών.

## Διαμόρφωση FontSettings για την αντικατάσταση γραμματοσειρών Aspose

Το αντικείμενο `FontSettings` ελέγχει πώς το Aspose.Words εντοπίζει τις γραμματοσειρές. Από προεπιλογή ψάχνει στους φακέλους γραμματοσειρών του συστήματος, έπειτα επιστρέφει σε ενσωματωμένες εναλλακτικές. Μπορείτε να ρυθμίσετε λεπτομερώς αυτή τη συμπεριφορά:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Αυτές οι γραμμές είναι προαιρετικές για το βασικό σενάριο “set warning callback aspose”, αλλά δείχνουν πώς μπορείτε να **μειώσετε** τον αριθμό των προειδοποιήσεων αντικατάστασης παρέχοντας τις σωστές γραμματοσειρές εκ των προτέρων.

## Υλοποίηση IWarningCallback για προειδοποιήσεις αντικατάστασης γραμματοσειρών

Η διεπαφή `IWarningCallback` είναι μικρή—μόνο μια μέθοδος `Warning`. Παρόλα αυτά σας δίνει **πλήρη έλεγχο** πάνω στο πώς διαχειρίζεστε τις προειδοποιήσεις:

- **Καταγραφή σε αρχείο** αντί για την κονσόλα.  
- **Συλλογή προειδοποιήσεων** σε λίστα για μεταγενέστερη ανάλυση.  
- **Εκκίνηση εξαιρέσεων** για κρίσιμες προειδοποιήσεις (π.χ., όταν λείπει μια απαιτούμενη γραμματοσειρά).

Ακολουθεί ένα γρήγορο παράδειγμα που αποθηκεύει τις προειδοποιήσεις σε ένα `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Στη συνέχεια μπορείτε να ελέγξετε το `handler.Messages` μετά τη φόρτωση του εγγράφου για να αποφασίσετε αν θα ακυρώσετε την επεξεργασία.

## Φόρτωση εγγράφου με προσαρμοσμένο χειρισμό προειδοποιήσεων (πλήρης ροή εργασίας)

Συνδυάζοντας όλα, το τελικό μοτίβο που πιθανότατα θα επαναχρησιμοποιήσετε μοιάζει ως εξής:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Αυτό το απόσπασμα δείχνει τη ροή **aspose document loading** που θα χρησιμοποιήσετε στην παραγωγή: ρυθμίστε, φορτώστε, και μετά αντιδράστε. Το μοτίβο κλιμακώνεται άψογα είτε επεξεργάζεστε ένα μόνο αρχείο είτε επαναλαμβάνετε χιλιάδες.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

**Τι γίνεται αν το έγγραφο είναι προστατευμένο με κωδικό;**  
Προσθέστε `Password = "secret"` στον αρχικοποιητή `LoadOptions`. Το warning callback λειτουργεί ακόμη και μετά την αποκρυπτογράφηση του αρχείου.

**Θα ενεργοποιείται το callback για άλλους τύπους προειδοποιήσεων;**  
Ναι—`WarningInfo.Type` μπορεί να είναι `DocumentStructure`, `UnsupportedFileFormat`, κ.λπ. Στο παράδειγμά μας φιλτράρουμε για `FontSubstitution`, αλλά μπορείτε να καταγράψετε τα πάντα αφαιρώντας τον έλεγχο `if`.

**Επηρεάζει αυτό την απόδοση;**  
Απροσδόκητα. Το callback καλείται μόνο όταν προκύψει προειδοποίηση, κάτι που είναι πολύ λιγότερο συχνό από τα κανονικά βήματα ανάλυσης.

**Μπορώ να απενεργοποιήσω εντελώς την αντικατάσταση γραμματοσειρών;**  
Μπορείτε να ορίσετε `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` αλλά τότε το Aspose.Words θα ρίξει εξαίρεση για ελλιπείς γραμματοσειρές αντί να τις αντικαθιστά.

## Συμπέρασμα

Τώρα γνωρίζετε ακριβώς πώς να **set warning callback aspose** για την παρακολούθηση των γεγονότων αντικατάστασης γραμματοσειρών κατά την επεξεργασία **Aspose.Words LoadOptions**. Με τη ρύθμιση του `FontSettings`, την υλοποίηση ενός ελαφρού `IWarningCallback` και τη φόρτωση του εγγράφου με αυτές τις επιλογές, αποκτάτε πλήρη ορατότητα σε οποιεσδήποτε αλλαγές γραμματοσειρών κάνει το Aspose στο παρασκήνιο.

Από εδώ μπορείτε:

- Να επεκτείνετε τον διαχειριστή προειδοποιήσεων ώστε να γράφει σε μια κεντρική υπηρεσία καταγραφής.  
- Να συνδυάσετε το callback με μια προσαρμοσμένη στρατηγική εναλλακτικών γραμματοσειρών.  
- Να χρησιμοποιήσετε το μοτίβο κατά τη δημιουργία ενός cloud API που επαληθεύει έγγραφα που ανεβάζουν οι πελάτες.

Δοκιμάστε το με τα δικά σας αρχεία DOCX, τροποποιήστε το `FontSettings`, και παρακολουθήστε την κονσόλα να σας λέει ακριβώς ποιες γραμματοσειρές αντικαταστάθηκαν. Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να εμφανίζονται πάντα όπως προορίζεται!

## Σχετικά Tutorials

- [Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών σε Java με Aspose.Words – Πλήρης Οδηγός](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών στο Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Πώς να Ορίσετε LoadOptions στο Aspose.Words για Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}