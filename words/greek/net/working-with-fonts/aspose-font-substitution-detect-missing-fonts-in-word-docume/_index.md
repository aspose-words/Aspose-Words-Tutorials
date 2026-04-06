---
category: general
date: 2026-04-05
description: Οδηγός αντικατάστασης γραμματοσειρών Aspose για την ανίχνευση ελλιπών
  γραμματοσειρών κατά τη φόρτωση ενός εγγράφου Word. Μάθετε πώς να διαμορφώσετε τις
  ρυθμίσεις γραμματοσειρών και να διαχειρίζεστε αποτελεσματικά τις ελλιπείς γραμματοσειρές.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: el
og_description: Οδηγός αντικατάστασης γραμματοσειρών Aspose για την ανίχνευση ελλιπών
  γραμματοσειρών κατά τη φόρτωση ενός εγγράφου Word. Μάθετε πώς να διαμορφώσετε τις
  ρυθμίσεις γραμματοσειρών και να διαχειριστείτε αποτελεσματικά τις ελλιπείς γραμματοσειρές.
og_title: Αντικατάσταση γραμματοσειρών Aspose – Εντοπισμός ελλιπών γραμματοσειρών
  σε έγγραφα Word
tags:
- Aspose.Words
- C#
- Font Management
title: Αντικατάσταση Γραμματοσειρών Aspose – Εντοπισμός Ελλειπουσών Γραμματοσειρών
  σε Έγγραφα Word
url: /el/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Εντοπισμός Ελλειπόντων Γραμματοσειρών σε Έγγραφα Word

Έχετε ποτέ αντιμετωπίσει ένα αρχείο Word που φαίνεται τέλειο σε έναν υπολογιστή αλλά εμφανίζει περίεργες αλλαγές γραμματοσειράς σε άλλο; Αυτό είναι το κλασικό πρόβλημα **aspose font substitution**, και συνήθως σημαίνει ότι λείπουν κάποιες γραμματοσειρές στο σύστημα-στόχο. Σε αυτό το tutorial θα σας δείξουμε, βήμα‑βήμα, πώς να **εντοπίσετε ελλειπούσες γραμματοσειρές** όταν **φορτώνετε ένα έγγραφο Word**, πώς να **ρυθμίσετε τις ρυθμίσεις γραμματοσειράς**, και τι να κάνετε για να **χειριστείτε τις ελλειπούσες γραμματοσειρές** με χάρη.

Θα περάσουμε από ένα πλήρες, εκτελέσιμο παράδειγμα C#, θα εξηγήσουμε γιατί κάθε γραμμή είναι σημαντική, και ακόμη θα σας δείξουμε την έξοδο της κονσόλας που πρέπει να περιμένετε. Στο τέλος θα μπορείτε να εντοπίζετε τις αντικαταστάσεις γραμματοσειρών τη στιγμή που φορτώνεται ένα έγγραφο — χωρίς εικασίες.

## Τι Θα Μάθετε

- Πώς να ενεργοποιήσετε τον διαγνωστικό συλλέκτη του Aspose.Words για προειδοποιήσεις γραμματοσειρών.  
- Ο ακριβής κώδικας που απαιτείται για **φόρτωση ενός εγγράφου Word** με προσαρμοσμένες **ρυθμίσεις γραμματοσειράς**.  
- Πώς να επαναλάβετε τα αντικείμενα `WarningInfo` για να καταγράψετε κάθε αντικατεστημένη γραμματοσειρά.  
- Συμβουλές για την καταστολή ανεπιθύμητων προειδοποιήσεων ή την παροχή εναλλακτικών γραμματοσειρών.  
- Ένα έτοιμο προς εκτέλεση δείγμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο Visual Studio.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το API λειτουργεί το ίδιο και στο .NET Framework).  
- Aspose.Words για .NET (πακέτο NuGet `Aspose.Words`).  
- Ένα αρχείο Word που αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., `MissingFont.docx`).  

Αν τα έχετε, ας βουτήξουμε.

## Βήμα 1 – Ενεργοποίηση του Διαγνωστικού Συλλέκτη (Ρύθμιση Ρυθμίσεων Γραμματοσειράς)

Πρώτα απ' όλα: Το Aspose.Words καταγράφει προειδοποιήσεις αντικατάστασης γραμματοσειράς μόνο αν του το υποδείξετε. Αυτό γίνεται δημιουργώντας ένα αντικείμενο `FontSettings` και αντιστοιχίζοντάς το σε μια παρουσία `LoadOptions`. Σκεφτείτε το ως ενεργοποίηση των «φώτων εντοπισμού σφαλμάτων» για τη διαχείριση γραμματοσειρών.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Γιατί;**  
Χωρίς ένα αντικείμενο `FontSettings` ο συλλέκτης προειδοποιήσεων παραμένει σιωπηλός, και δεν θα ξέρετε ποτέ ποιες γραμματοσειρές αντικαταστάθηκαν. Αρχικοποιώντας το κενό, επιτρέπουμε στο Aspose να χρησιμοποιήσει τις προεπιλεγμένες γραμματοσειρές του συστήματος *και* να παρακολουθεί τυχόν αντικαταστάσεις.

> **Pro tip:** Αν γνωρίζετε ότι ένας συγκεκριμένος φάκελος περιέχει εταιρικές γραμματοσειρές, κατευθύνετε το `FontSettings` εκεί με `SetFontsFolder("path")`. Αυτό μπορεί να μειώσει τον αριθμό των προειδοποιήσεων ελλιπών γραμματοσειρών.

## Βήμα 2 – Φόρτωση του Εγγράφου με τις Διαμορφωμένες Επιλογές (Load Word Document)

Τώρα που ο συλλέκτης είναι ενεργός, φορτώστε το αρχείο `.docx` χρησιμοποιώντας τις ίδιες `LoadOptions`. Αυτή είναι η στιγμή που το Aspose σαρώνει το έγγραφο, ψάχνει για κάθε αναφορά γραμματοσειράς και αποφασίζει αν χρειάζεται αντικατάσταση.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Γιατί είναι σημαντικό;**  
Αν απλώς καλέσατε `new Document("MissingFont.docx")`, οι προεπιλεγμένες ρυθμίσεις θα εφαρμοστούν *και* η λίστα προειδοποιήσεων θα παραμείνει κενή. Η μεταβίβαση των `loadOptions` εγγυάται ότι ο διαγνωστικός συλλέκτης είναι συνδεδεμένος στη διαδικασία φόρτωσης.

## Βήμα 3 – Ανάκτηση και Εμφάνιση Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς (Detect Missing Fonts)

Αφού το έγγραφο είναι στη μνήμη, το Aspose αποθηκεύει τυχόν προειδοποιήσεις στο `document.WarningCallback.Warnings`. Περάστε τη συλλογή με βρόχο, φιλτράρετε για `WarningType.FontSubstitution` και εκτυπώστε την περιγραφή. Κάθε περιγραφή σας λέει ποια γραμματοσειρά έλειπε και ποια χρησιμοποιήθηκε αντί αυτής.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Αναμενόμενη έξοδος κονσόλας**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Αυτή η έξοδος σας λέει ακριβώς ποιες γραμματοσειρές λείπουν από το μηχάνημα που εκτελεί τον κώδικα. Τώρα μπορείτε να αποφασίσετε αν θα εγκαταστήσετε τις ελλιπείς γραμματοσειρές, θα τις ενσωματώσετε στο έγγραφο, ή θα διατηρήσετε την αντικατάσταση.

![Έξοδος κονσόλας που εμφανίζει προειδοποιήσεις αντικατάστασης γραμματοσειράς Aspose](/images/aspose-font-substitution-console.png)

*Κείμενο alt εικόνας:* αντικατάσταση γραμματοσειράς Aspose – έξοδος κονσόλας που καταγράφει τις αντικατεστημένες γραμματοσειρές

## Βήμα 4 – Προαιρετικό: Προσαρμογή της Συμπεριφοράς Αντικατάστασης (Handle Missing Fonts)

Μερικές φορές δεν θέλετε μόνο να ξέρετε *ότι* έγινε μια αντικατάσταση — θέλετε να ελέγξετε *πώς* συμβαίνει. Το Aspose.Words σας επιτρέπει να καταχωρήσετε έναν προσαρμοσμένο κανόνα `IFontSubstitutionRule`. Παρακάτω υπάρχει ένα γρήγορο παράδειγμα που αναγκάζει οποιαδήποτε ελλιπής γραμματοσειρά να υποκατασταθεί με `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Πότε θα το χρησιμοποιούσατε;**  
Αν δημιουργείτε PDF για μια υπηρεσία web και ξέρετε ότι κάθε πελάτης μπορεί να αποδώσει το `Tahoma`, η επιβολή της εναλλακτικής εξασφαλίζει οπτική συνέπεια χωρίς να χρειάζεται να στείλετε δεκάδες αρχεία γραμματοσειρών.

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα Συνδυασμένα)

Ακολουθεί ολόκληρο το πρόγραμμα που μπορείτε να επικολλήσετε σε ένα νέο έργο κονσόλας. Συγκεντρώνεται ακριβώς όπως είναι, υποθέτοντας ότι έχετε εγκαταστήσει το πακέτο NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Εκτελέστε το πρόγραμμα, παρακολουθήστε την κονσόλα, και θα δείτε κάθε συμβάν ελλιπούσας γραμματοσειράς να εκτυπώνεται. Από εκεί μπορείτε να αποφασίσετε αν θα εγκαταστήσετε τις ελλιπείς γραμματοσειρές, θα τις ενσωματώσετε, ή θα διατηρήσετε την εναλλακτική.

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό με μετατροπή PDF;**  
Ναι. Όταν αργότερα καλέσετε `doc.Save("output.pdf")`, οι γραμματοσειρές που αντικαταστάθηκαν κατά τη φόρτωση θα είναι αυτές που θα ενσωματωθούν στο PDF. Έτσι, η έγκαιρη σύλληψη των προειδοποιήσεων σας βοηθά να αποφύγετε απρόσμενες αλλαγές γραμματοσειράς στο τελικό PDF.

**Ε: Τι γίνεται αν έχω πολλά έγγραφα προς επεξεργασία;**  
Τυλίξτε τη λογική φόρτωσης σε ένα μπλοκ try‑catch και επαναχρησιμοποιήστε μια ενιαία παρουσία `FontSettings` για όλα τα έγγραφα. Αυτό μειώνει το κόστος και διατηρεί τον συλλέκτη προειδοποιήσεων ενεργό για κάθε αρχείο.

**Ε: Μπορώ να καταστέλλω εντελώς τις προειδοποιήσεις;**  
Μπορείτε να ορίσετε `loadOptions.WarningCallback = null;` πριν από τη φόρτωση, αλλά θα χάσετε τη δυνατότητα **εντοπισμού ελλιπών γραμματοσειρών** — κάτι που συνήθως δεν θέλετε.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να κυριαρχήσετε στο **aspose font substitution**: ενεργοποίηση του διαγνωστικού συλλέκτη, φόρτωση ενός αρχείου Word με προσαρμοσμένες **ρυθμίσεις γραμματοσειράς**, εξαγωγή της λίστας ελλιπών γραμματοσειρών, και ακόμη αντικατάσταση του προεπιλεγμένου κανόνα αντικατάστασης για **χειρισμό ελλιπών γραμματοσειρών** με τον δικό σας τρόπο. Με λίγες μόνο γραμμές C# αποκτάτε πλήρη ορατότητα σε προβλήματα γραμματοσειρών που διαφορετικά θα κρύβονταν πίσω από λεπτές αλλαγές διάταξης.

Επόμενα βήματα; Δοκιμάστε να ενσωματώσετε τις αρχικές γραμματοσειρές στο έγγραφο με `FontSettings.SetFontsFolder` ή εξερευνήστε το `FontSourceBase` για φόρτωση γραμματοσειρών από βάση δεδομένων. Μπορείτε επίσης να πειραματιστείτε με τη συλλογή `Document.BuiltInStyle` για να δείτε πώς διαδίδονται οι αλλαγές γραμματοσειράς σε επίπεδο στυλ.

Έχετε περισσότερες ερωτήσεις σχετικά με το Aspose.Words ή τη διαχείριση γραμματοσειρών; Αφήστε ένα σχόλιο, εξερευνήστε την επίσημη τεκμηρίωση του Aspose, ή ξεκινήστε ένα νέο έργο και πειραματιστείτε με τον παραπάνω κώδικα. Καλή προγραμματιστική, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα ακριβώς όπως προορίζεται!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}