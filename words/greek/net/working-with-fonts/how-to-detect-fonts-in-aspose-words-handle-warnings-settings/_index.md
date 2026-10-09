---
category: general
date: 2026-01-03
description: Πώς να εντοπίσετε τις γραμματοσειρές στο Aspose.Words και να διαχειριστείτε
  τις προειδοποιήσεις χρησιμοποιώντας τις ρυθμίσεις γραμματοσειρών του Aspose – ένας
  οδηγός βήμα‑βήμα για προγραμματιστές.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: el
og_description: Πώς να εντοπίσετε γραμματοσειρές στο Aspose.Words και να διαμορφώσετε
  προειδοποιήσεις με τις ρυθμίσεις γραμματοσειρών του Aspose. Μάθετε ολόκληρη τη ροή
  εργασίας σε λίγα λεπτά.
og_title: Πώς να εντοπίσετε τις γραμματοσειρές στο Aspose.Words – Διαχείριση προειδοποιήσεων
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να ανιχνεύσετε τις γραμματοσειρές στο Aspose.Words – Διαχείριση προειδοποιήσεων
  & ρυθμίσεων
url: /el/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ανιχνεύσετε γραμματοσειρές στο Aspose.Words – Διαχείριση προειδοποιήσεων & Ρυθμίσεων

Έχετε αναρωτηθεί ποτέ **πώς να ανιχνεύσετε γραμματοσειρές** σε ένα έγγραφο Word πριν το βγάλει στην παραγωγή; Δεν είστε οι μόνοι. Οι ελλιπείς γραμματοσειρές μπορούν να προκαλέσουν εφιάλτες διάταξης, και χωρίς τις κατάλληλες προειδοποιήσεις μπορεί να παραδώσετε ένα κατεστραμμένο PDF ή DOCX χωρίς καν να το συνειδητοποιήσετε.  

Σε αυτό το tutorial θα περάσουμε από **πώς να ανιχνεύσετε γραμματοσειρές** χρησιμοποιώντας το Aspose.Words, θα δείξουμε **πώς να διαχειριστείτε προειδοποιήσεις**, και θα ρυθμίσουμε **τις ρυθμίσεις γραμματοσειρών του Aspose** ώστε να μπορείτε να **ρυθμίσετε τις προειδοποιήσεις** ακριβώς όπως τις χρειάζεστε. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση snippet που εκτυπώνει κάθε αντικατάσταση που κάνει το Aspose, και θα ξέρετε πώς να το προσαρμόσετε στα δικά σας έργα.

## Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.6+).  
- Aspose.Words for .NET εγκατεστημένο μέσω NuGet (`Install-Package Aspose.Words`).  
- Ένα αρχείο Word που σκόπιμα αναφέρει μια ελλιπή γραμματοσειρά (π.χ., *DocumentWithMissingFonts.docx*).  

Αν τα έχετε ήδη, υπέροχα—ας βουτήξουμε.

![στιγμιότυπο εντοπισμού γραμματοσειρών](https://example.com/detect-fonts.png "παράδειγμα εξόδου εντοπισμού γραμματοσειρών")

## Πώς να ανιχνεύσετε γραμματοσειρές με το Aspose.Words

Το πρώτο βήμα είναι να ενημερώσετε το Aspose.Words ότι σας ενδιαφέρουν τα γεγονότα αντικατάστασης γραμματοσειρών. Αυτό γίνεται παρέχοντας μια προσαρμοσμένη callback προειδοποίησης μέσω των **ρυθμίσεων γραμματοσειρών του Aspose**. Η callback λαμβάνει ένα αντικείμενο `WarningInfo` για κάθε αντικατάσταση, επιτρέποντάς σας να **ανιχνεύσετε γραμματοσειρές** σε χρόνο εκτέλεσης.

### Βήμα 1: Δημιουργία κλάσης Callback προειδοποίησης

Υλοποιήστε τη διεπαφή `IWarningCallback`. Μέσα στη μέθοδο `Warning`, φιλτράρετε για `WarningType.FontSubstitution` και καταγράψτε τις λεπτομέρειες.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Συμβουλή:** Η συμβολοσειρά `info.Description` περιέχει τόσο το όνομα της ελλιπούς γραμματοσειράς όσο και την αντικατάσταση που επέλεξε το Aspose. Μπορείτε να την αναλύσετε αν χρειάζεστε μια δομημένη αναφορά.

### Βήμα 2: Διαμόρφωση LoadOptions με τις ρυθμίσεις γραμματοσειρών του Aspose

Δημιουργήστε ένα αντικείμενο `LoadOptions`, συνδέστε ένα νέο αντικείμενο `FontSettings`, και ορίστε το `WarningCallback` στον χειριστή που μόλις δημιουργήσαμε. Αυτό ενημερώνει το Aspose **πώς να ρυθμίσει τις προειδοποιήσεις**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Αν έχετε έναν ιδιωτικό φάκελο γραμματοσειρών, μπορείτε να τον προσθέσετε ως εξής:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Αυτή η γραμμή δείχνει μια άλλη πλευρά των **ρυθμίσεων γραμματοσειρών του Aspose**—εσείς ελέγχετε ακριβώς πού ψάχνει το Aspose για γραμματοσειρές πριν αποφασίσει να αντικαταστήσει.

### Βήμα 3: Φόρτωση του εγγράφου και ενεργοποίηση της Callback

Τώρα φορτώστε το στοχευόμενο έγγραφο με το `loadOptions`. Καθώς το Aspose αναλύει το αρχείο, οποιαδήποτε ελλιπής γραμματοσειρά ενεργοποιεί τον χειριστή προειδοποίησης, ανιχνεύοντας έτσι **γραμματοσειρές** σε πραγματικό χρόνο.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Όταν εκτελέσετε το πρόγραμμα, θα δείτε έξοδο παρόμοια με:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Βήμα 4: (Προαιρετικό) Συλλογή προειδοποιήσεων για μελλοντική χρήση

Αν χρειάζεται να αποθηκεύσετε τα δεδομένα αντικατάστασης για μια αναφορά, τροποποιήστε τον χειριστή ώστε να συγκεντρώνει τα μηνύματα σε μια λίστα.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Αργότερα μπορείτε να γράψετε το `handler.Substitutions` σε ένα αρχείο JSON, να το στείλετε σε μια υπηρεσία καταγραφής, ή να το εμφανίσετε σε ένα UI.

### Βήμα 5: Επαλήθευση του αποτελέσματος προγραμματιστικά

Μερικές φορές θέλετε να επιβεβαιώσετε ότι *καμία* αντικατάσταση δεν συνέβη (π.χ., σε μια κατασκευή CI). Εδώ είναι ένας γρήγορος έλεγχος:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Αυτό το snippet δείχνει **πώς να διαχειριστείτε προειδοποιήσεις** με καθορισμένο τρόπο, δίνοντάς σας πλήρη έλεγχο πάνω στη διαδικασία κατασκευής.

## Συχνές Ερωτήσεις (και Ακραίες Περιπτώσεις)

**Τι γίνεται αν χρειάζεται να αγνοήσω ορισμένες αντικαταστάσεις;**  
Μπορείτε να προσθέσετε λογική υπό συνθήκη μέσα στο `Warning` και απλώς να επιστρέψετε χωρίς καταγραφή για τις γραμματοσειρές που θεωρείτε αποδεκτές.

**Μπορώ να καταστέψω όλες τις προειδοποιήσεις και να λάβω μόνο ένα boolean αποτέλεσμα;**  
Ναι—ορίστε `loadOptions.WarningCallback = null` και μετά ελέγξτε το `doc.FontInfo` μετά τη φόρτωση (αν και θα χάσετε την λεπτομερή καταγραφή).

**Λειτουργεί αυτό με τη μετατροπή σε PDF;**  
Απόλυτα. Ο ίδιος μηχανισμός προειδοποίησης ενεργοποιείται όταν καλείτε `doc.Save("out.pdf")`. Η callback θα συλλάβει οποιεσδήποτε ανταλλαγές γραμματοσειρών πραγματοποιούνται κατά το βήμα μετατροπής.

**Υπάρχει κάποια επίπτωση στην απόδοση;**  
Το κόστος είναι ελάχιστο—μόνο μερικές επιπλέον κλήσεις μεθόδων ανά ελλιπή γραμματοσειρά. Για μεγάλες δόσεις, ίσως θελήσετε να αποθηκεύσετε τα αποτελέσματα στην cache.

## Συμπέρασμα: Τι καλύψαμε

- **Πώς να ανιχνεύσετε γραμματοσειρές** υλοποιώντας ένα προσαρμοσμένο `IWarningCallback`.  
- **Πώς να διαχειριστείτε προειδοποιήσεις** μέσω του `LoadOptions.WarningCallback`.  
- Ρύθμιση των **ρυθμίσεων γραμματοσειρών του Aspose** (προσθήκη προσαρμοσμένων φακέλων γραμματοσειρών, ενεργοποίηση/απενεργοποίηση προειδοποιήσεων).  
- **Πώς να ρυθμίσετε τις προειδοποιήσεις** για άμεση έξοδο στην κονσόλα και για μελλοντική ανάλυση.  

Με αυτά τα στοιχεία στη θέση τους, μπορείτε με σιγουριά να επεξεργάζεστε έγγραφα Word, να εγγυάστε ότι οι ελλιπείς γραμματοσειρές εντοπίζονται, και να διατηρήσετε την έξοδό σας συνεπή σε όλα τα περιβάλλοντα.

## Επόμενα Βήματα

- Εξερευνήστε το `FontSettings.SubstitutionSettings` για πιο λεπτομερή έλεγχο (π.χ., αντιστοίχιση συγκεκριμένων ελλιπών γραμματοσειρών με επιλεγμένες αντικαταστάσεις).  
- Συνδυάστε αυτήν την προσέγγιση με το Aspose.PDF για τη δημιουργία PDF που διατηρούν ακριβή τυπογραφία.  
- Αυτοματοποιήστε τον έλεγχο προειδοποιήσεων σε μια CI/CD pipeline για να εμποδίζετε κυκλοφορίες που περιέχουν προβλήματα γραμματοσειρών—ιδανικό για ομάδες που **διαχειρίζονται προειδοποιήσεις** ως μέρος των πύλες ποιότητας.  

Έχετε περισσότερες ερωτήσεις σχετικά με τις **ρυθμίσεις γραμματοσειρών του aspose** ή χρειάζεστε βοήθεια για την ενσωμάτωση αυτού σε μια μεγαλύτερη υπηρεσία; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}