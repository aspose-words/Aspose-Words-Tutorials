---
category: general
date: 2026-05-29
description: Μάθετε πώς να ορίζετε το FontSettings στο Aspose.Words και να διαχειρίζεστε
  τις ελλείπουσες γραμματοσειρές με χάρη. Οδηγός βήμα-βήμα με πλήρη κώδικα και βέλτιστες
  πρακτικές.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: el
og_description: Πώς να ορίσετε το FontSettings στο Aspose.Words και να διαχειριστείτε
  γρήγορα τις ελλείπουσες γραμματοσειρές. Ακολουθήστε αυτόν τον οδηγό για μια πλήρη,
  εκτελέσιμη λύση.
og_title: Πώς να ορίσετε τις ρυθμίσεις γραμματοσειράς – Διαχείριση ελλιπών γραμματοσειρών
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Πώς να ορίσετε τις ρυθμίσεις γραμματοσειράς – Διαχείριση ελλειπούσων γραμματοσειρών
url: /el/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε το FontSettings – Διαχείριση Ελλειπουσών Γραμματοσειρών

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε το FontSettings** όταν εργάζεστε με το Aspose.Words και ξαφνικά αντιμετωπίζετε ένα έγγραφο που αναφέρει μια γραμματοσειρά που δεν έχετε εγκαταστήσει; Είναι ένα κοινό πρόβλημα, ειδικά όταν επεξεργάζεστε αρχεία που παρέχονται από πελάτες σε έναν διακομιστή που διαθέτει μόνο ένα ελάχιστο σύνολο γραμματοσειρών. Τα καλά νέα; Μπορείτε να εντοπίσετε αυτά τα κενά και **να διαχειριστείτε τις ελλειπούσες γραμματοσειρές** χωρίς η εφαρμογή σας να καταρρεύσει ή να παράγει άσχημα PDF.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό σενάριο: φόρτωση ενός DOCX που ζητά “Calibri” ενώ το Linux container σας περιλαμβάνει μόνο “DejaVu Sans”. Θα δείτε ακριβώς πώς να ρυθμίσετε το FontSettings, να εγγραφείτε σε προειδοποιήσεις αντικατάστασης και να παρέχετε εναλλακτικές γραμματοσειρές ώστε το έγγραφο να αποδίδεται όπως προοριζόταν ο δημιουργός. Χωρίς περιττά – μόνο ο κώδικας που μπορείτε να ενσωματώσετε στο πρότζεκτ σας σήμερα.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το API λειτουργεί το ίδιο σε .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 ή νεότερο (το όνομα του πακέτου NuGet είναι `Aspose.Words`)
- Ένα βασικό περιβάλλον ανάπτυξης C# (Visual Studio, Rider ή VS Code)

Αν τα έχετε, ας βουτήξουμε.

## Βήμα 1: Δημιουργία FontSettings και Παρακολούθηση Συμβάντων Αντικατάστασης

Η καρδιά της λύσης είναι το αντικείμενο `FontSettings`. Συνδέοντας έναν χειριστή στο συμβάν `FontSubstitutionWarning` θα λαμβάνετε μια ζωντανή αναφορά κάθε φορά που το Aspose.Words πρέπει να αντικαταστήσει μια ελλιπή γραμματοσειρά.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Γιατί αυτό είναι σημαντικό:**  
Όταν η μηχανή δεν μπορεί να εντοπίσει το *Calibri*, μπορεί σιωπηρά να πέσει στο *Arial*. Ακούγοντας την προειδοποίηση, διατηρείτε ένα διαυγές αρχείο ελέγχου – ιδανικό για αποσφαλμάτωση ή αναφορές συμμόρφωσης.

> **Pro tip:** Αν τρέχετε αυτό σε διακομιστή CI, κατευθύνετε την έξοδο σε αρχείο καταγραφής ώστε να μπορείτε να ελέγξετε ποιες γραμματοσειρές λείπουν μετά από μια παρτίδα εκτέλεσης.

## Βήμα 2: Σύνδεση FontSettings με LoadOptions

Το `LoadOptions` είναι η πύλη ελέγχου του τρόπου ανάλυσης ενός εγγράφου. Αναθέτοντας το `FontSettings` που μόλις διαμορφώσαμε, κάθε επόμενη φόρτωση `Document` θα σέβεται τη λογική αντικατάστασης που ορίσαμε.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Τι συμβαίνει στο παρασκήνιο;**  
Κατά τον κατασκευαστή του `Document`, το Aspose.Words διαβάζει το XML του DOCX, επιλύει τις αναφορές γραμματοσειρών και—αν δεν βρεθεί μια γραμματοσειρά—ενεργοποιεί την προειδοποίηση που ρυθμίσαμε νωρίτερα. Χωρίς αυτό το hook, δεν θα γνωρίζετε ποτέ ότι έγινε αντικατάσταση.

## Βήμα 3: Φόρτωση του Εγγράφου και (Προαιρετικά) Ορισμός Εναλλακτικών Γραμματοσειρών

Τώρα φέρνουμε τελικά το αρχείο στη μνήμη. Αν έχετε ήδη έναν φάκελο εναλλακτικών γραμματοσειρών (π.χ. έναν κατάλογο OpenType γραμματοσειρών που συνοδεύει την εφαρμογή σας), ενημερώστε το `FontSettings` πού να ψάξει. Αυτό το βήμα είναι προαιρετικό αλλά συχνά ο πιο καθαρός τρόπος για *να διαχειριστείτε τις ελλειπούσες γραμματοσειρές*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Ειδοποίηση ειδικής περίπτωσης:**  
Αν το έγγραφο περιέχει μια προσαρμοσμένη γραμματοσειρά ενσωματωμένη ως δυαδική ροή, το Aspose.Words θα τη χρησιμοποιήσει αυτόματα—χωρίς ανάγκη αντικατάστασης. Η προειδοποίηση ενεργοποιείται μόνο για *ελλιπείς* συστημικές γραμματοσειρές.

### Επαλήθευση του Αποτελέσματος

Μετά τη φόρτωση, ίσως θέλετε να αποθηκεύσετε το έγγραφο σε PDF ή Word για να βεβαιωθείτε ότι όλα φαίνονται σωστά.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Όταν εκτελέσετε το πρόγραμμα, η κονσόλα θα εμφανίσει γραμμές όπως:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Αν δείτε αυτά τα μηνύματα, έχετε **επιτυχώς διαχειριστεί τις ελλειπούσες γραμματοσειρές** και ξέρετε ακριβώς ποιες αντικαταστάσεις πραγματοποιήθηκαν.

## Βήμα 4: Προχωρημένο – Προσαρμοσμένοι Κανόνες Αντικατάστασης Γραμματοσειρών (Προαιρετικό)

Μερικές φορές χρειάζεται καθοριστική αντιστοίχιση, π.χ. πάντα να αντικαθιστάτε το *Times New Roman* με το *Liberation Serif*. Αυτό μπορεί να επιτευχθεί με το `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Γιατί να ασχοληθείτε;**  
Οι ρητοί κανόνες σας δίνουν έλεγχο στην τυπογραφία, εξασφαλίζοντας συνέπεια του brand στα παραγόμενα PDF, ειδικά όταν παράγετε υλικό μάρκετινγκ.

## Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Σύμπτωμα | Διόρθωση |
|----------|----------|----------|
| **Καμία έξοδος προειδοποίησης** | Νομίζετε ότι οι γραμματοσειρές είναι εντάξει αλλά το έγγραφο φαίνεται λάθος. | Βεβαιωθείτε ότι το `FontSubstitutionWarning` είναι προσαρτημένο **πριν** τη φόρτωση του εγγράφου. |
| **Ο φάκελος εναλλακτικών γραμματοσειρών δεν σαρώθηκε** | Οι αντικαταστάσεις εξακολουθούν να επιστρέφουν στις προεπιλογές του συστήματος. | Καλέστε `SetFontsFolder(path, true)` με το δεύτερο όρισμα `true` για αναδρομική σάρωση υποφακέλων. |
| **Πτώση απόδοσης σε μεγάλες παρτίδες** | Η φόρτωση 10 χιλιάδων εγγράφων γίνεται αργή. | Αποθηκεύστε στην κρυφή μνήμη μια μόνο παρουσία `FontSettings` και επαναχρησιμοποιήστε την σε όλες τις φορτώσεις· αποφύγετε τη δημιουργία νέας κάθε φορά. |
| **Αγνοούνται οι ενσωματωμένες γραμματοσειρές** | Περιμένετε να χρησιμοποιηθεί μια προσαρμοσμένη ενσωματωμένη γραμματοσειρά, αλλά πραγματοποιείται αντικατάσταση. | Επαληθεύστε ότι το αρχικό DOCX ενσωματώνει πραγματικά τη γραμματοσειρά (ελέγξτε με το Word → Αρχείο → Πληροφορίες → Γραμματοσειρές). |

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες, έτοιμο προς αντιγραφή πρόγραμμα. Δείχνει τα πάντα, από τη διαχείριση συμβάντων μέχρι την αποθήκευση του τελικού PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Αναμενόμενη έξοδος κονσόλας** (παράδειγμα):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Τρέξτε το πρόγραμμα, ανοίξτε το `Output.pdf`, και θα δείτε το κείμενο να αποδίδεται με τις εναλλακτικές γραμματοσειρές—χωρίς τετράγωνα ελλιπών χαρακτήρων, χωρίς καταρρεύσεις.

## Συμπέρασμα

Τώρα έχετε ένα σταθερό, έτοιμο για παραγωγή πρότυπο για **πώς να ορίσετε το FontSettings** στο Aspose.Words και **να διαχειριστείτε τις ελλειπούσες γραμματοσειρές** με κομψότητα. Συνδέοντας το συμβάν `FontSubstitutionWarning`, δείχνοντας σε έναν φάκελο εναλλακτικών γραμματοσειρών και (αν χρειάζεται) ορίζοντας ρητούς κανόνες αντικατάστασης, αποκτάτε πλήρη διαφάνεια και έλεγχο στην τυπογραφία των αυτοματοποιημένων αγωγών εγγράφων.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να προσθέσετε μια συλλογή προσαρμοσμένων γραμματοσειρών για ειδικές γραμματοσειρές του brand, ή εξερευνήστε το API `FontSourceBase` για φόρτωση γραμματοσειρών από βάση δεδομένων ή αποθήκευση στο cloud. Οι ίδιες αρχές ισχύουν—απλώς συνδέστε μια διαφορετική πηγή στο `FontSettings`.

Έχετε ερωτήσεις για ειδικές περιπτώσεις, όπως η διαχείριση δεξιά‑προς‑αριστερά σεναρίων ή γραμματοσειρών emoji; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

- [Πώς να καταγράψετε τις γραμματοσειρές στο Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Πώς να εντοπίσετε τις γραμματοσειρές στο Aspose.Words – Διαχείριση Προειδοποιήσεων & Ρυθμίσεων](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Πώς να φορτώσετε DOCX και να εντοπίσετε ελλειπούσες γραμματοσειρές – Πλήρης Οδηγός C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}