---
category: general
date: 2026-03-28
description: Πώς να καταγράψετε προειδοποιήσεις κατά τη φόρτωση ενός DOCX με το Aspose.Words
  και να λάβετε μηνύματα προειδοποίησης για ελλιπείς γραμματοσειρές. Μάθετε πώς να
  διαχειρίζεστε αποτελεσματικά τις ελλιπείς γραμματοσειρές.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: el
og_description: Πώς να καταγράψετε προειδοποιήσεις κατά τη φόρτωση ενός DOCX με το
  Aspose.Words, να λάβετε μηνύματα προειδοποίησης και να διαχειριστείτε τις ελλιπείς
  γραμματοσειρές με πρακτικά παραδείγματα κώδικα.
og_title: Πώς να καταγράψετε προειδοποιήσεις στο Aspose.Words – Πλήρης οδηγός C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να Συλλέξετε Προειδοποιήσεις στο Aspose.Words – Πλήρης Οδηγός C#
url: /el/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Συλλέξετε Προειδοποιήσεις στο Aspose.Words – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί **πώς να συλλέξετε προειδοποιήσεις** που εμφανίζονται όταν φορτώνετε ένα έγγραφο Word με το Aspose.Words; Ίσως βλέπετε παράξενες αλλαγές γραμματοσειράς και χρειάζεστε ακριβή εξήγηση. Συνοπτικά, μπορείτε να συνδέσετε στο σύστημα προειδοποιήσεων της βιβλιοθήκης, **να λάβετε μηνύματα προειδοποίησης** και ακόμη **να διαχειριστείτε τις ελλιπείς γραμματοσειρές** πριν καταστρέψουν τη διάταξη.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό σενάριο: φόρτωση ενός DOCX, συλλογή κάθε προειδοποίησης που εκδίδει η μηχανή, και εκτύπωση λεπτομερειών για τυχόν αντικατάσταση γραμματοσειράς. Στο τέλος θα έχετε ένα έτοιμο δείγμα κώδικα, θα κατανοήσετε το «γιατί» πίσω από κάθε βήμα και θα ξέρετε πώς να επεκτείνετε την προσέγγιση στα δικά σας έργα.

## Τι Θα Μάθετε

- Πώς να ρυθμίσετε το `LoadOptions` ώστε οι προειδοποιήσεις να συλλέγονται αυτόματα.  
- Τον ακριβή τρόπο **λήψης μηνυμάτων προειδοποίησης** από το `WarningInfoCollection`.  
- Πώς να εντοπίσετε και να αντιδράσετε σε **ελλιπείς γραμματοσειρές** μέσω της σημαίας `WarningType.FontSubstitution`.  
- Συμβουλές για την αντιμετώπιση ειδικών περιπτώσεων, όπως έγγραφα με ενσωματωμένες γραμματοσειρές ή προσαρμοσμένους φακέλους γραμματοσειρών.  

Δεν απαιτούνται εξωτερικές αναφορές – όλα όσα χρειάζεστε είναι εδώ.

---

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+).  
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Ένα δείγμα DOCX (`input.docx`) που είτε λείπουν κάποιες γραμματοσειρές είτε χρησιμοποιεί γραμματοσειρές που δεν είναι εγκατεστημένες στο σύστημά σας.  

Αυτό είναι όλο. Αν είστε ήδη άνετοι με C# και Visual Studio, μπορείτε να αντιγράψετε‑επικολλήσετε τον κώδικα και να τον εκτελέσετε αμέσως.

---

## Βήμα 1: Προετοιμασία Load Options και Callback Προειδοποίησης

Το πρώτο που κάνει το Aspose.Words όταν καλέσετε `new Document(path, loadOptions)` είναι η ανάλυση του αρχείου. Κατά την ανάλυση μπορεί να συναντήσει ελλιπείς γραμματοσειρές, μη υποστηριζόμενα χαρακτηριστικά ή παρωχημένο markup. Για να πιάσετε αυτά τα γεγονότα χρειάζεστε ένα αντικείμενο **warning callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Γιατί είναι σημαντικό:** Χωρίς callback, το Aspose.Words καταγράφει σιωπηλά τις προειδοποιήσεις στην κονσόλα (ή τις απορρίπτει), αφήνοντάς σας τυφλούς στις αντικαταστάσεις γραμματοσειρών που μπορούν να επηρεάσουν τη διάταξη. Παρέχοντας ένα `WarningInfoCollection`, αποκτάτε πλήρη ορατότητα.

> **Pro tip:** Αν σας ενδιαφέρουν μόνο οι προειδοποιήσεις σχετικές με γραμματοσειρές, μπορείτε να φιλτράρετε αργότερα – αλλά η συλλογή *όλων* των προειδοποιήσεων σας δίνει ένα δίχτυ ασφαλείας για μελλοντικά ζητήματα.

---

## Βήμα 2: Φόρτωση του Εγγράφου με τις Ρυθμισμένες Επιλογές

Τώρα που το callback είναι έτοιμο, φορτώστε το αρχείο. Ο κατασκευαστής `Document` θα καλέσει αυτόματα το callback για τυχόν προβλήματα που εντοπίζει.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Τι συμβαίνει στο παρασκήνιο;** Το Aspose.Words αναλύει το Open XML, επιλύει τα στυλ και προσπαθεί να αντιστοιχίσει κάθε αναφορά γραμματοσειράς σε μια γραμματοσειρά που είναι εγκατεστημένη στο σύστημα. Αν δεν βρεθεί αντιστοιχία, δημιουργεί μια καταχώρηση `WarningInfo` τύπου `FontSubstitution`.

---

## Βήμα 3: Ανάκτηση και Εξέταση των Συλλεγμένων Προειδοποιήσεων

Μετά την ολοκλήρωση της φόρτωσης, το `warningCollector` περιέχει κάθε προειδοποίηση που συνέβη. Ας τις εξάγουμε και ας εστιάσουμε στα μηνύματα αντικατάστασης γραμματοσειράς.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Δειγματική έξοδος** (η κονσόλα σας μπορεί να εμφανίσει κάτι τέτοιο):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Αν θέλετε *όλες* τις προειδοποιήσεις, απλώς αφαιρέστε τον έλεγχο `if` ή καταγράψτε το `warning.Type` για κάθε καταχώρηση.

---

## Βήμα 4: Διαχείριση Ελλιπών Γραμματοσειρών – Πέρα από την Απλή Καταγραφή

Η συλλογή προειδοποιήσεων είναι χρήσιμη, αλλά συχνά χρειάζεται να **διαχειριστείτε προγραμματιστικά τις ελλιπείς γραμματοσειρές**. Ακολουθούν δύο κοινές στρατηγικές:

### 4.1 Αντικατάσταση Ελλιπών Γραμματοσειρών με Συγκεκριμένο Fallback

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Τώρα οποιαδήποτε ελλιπής γραμματοσειρά θα αντικατασταθεί με *Calibri* αντί για το προεπιλεγμένο fallback της βιβλιοθήκης.

### 4.2 Ενσωμάτωση Αντικαταστάτη Γραμματοσειράς Δυναμικά

Αν έχετε ένα προσαρμοσμένο αρχείο γραμματοσειράς (π.χ. `MyFallback.ttf`) μπορείτε να το καταχωρίσετε κατά το χρόνο εκτέλεσης:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Αυτή η προσέγγιση είναι χρήσιμη όταν διανέμετε μια συγκεκριμένη εταιρική γραμματοσειρά με την εφαρμογή σας.

> **Edge case:** Έγγραφα που ήδη ενσωματώνουν τη ζητούμενη γραμματοσειρά θα αγνοήσουν τους κανόνες αντικατάστασης του συστήματος. Σε αυτήν την περίπτωση, η συλλογή προειδοποιήσεων θα είναι κενή για εκείνη τη γραμματοσειρά, που είναι ακριβώς αυτό που θέλετε.

---

## Βήμα 5: Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που δείχνει τα πάντα από την αρχή μέχρι το τέλος. Απλώς αντικαταστήστε το `YOUR_DIRECTORY/input.docx` με τη διαδρομή του δοκιμαστικού σας αρχείου.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Τι να περιμένετε**

- Η κονσόλα εκτυπώνει κάθε προειδοποίηση αντικατάστασης γραμματοσειράς, προεπισημασμένη με emoji προειδοποίησης για μεγαλύτερη ορατότητα.  
- Το παραγόμενο DOCX (`output.docx`) χρησιμοποιεί *Calibri* όπου εντοπίστηκε ελλιπής γραμματοσειρά.  
- Δεν θα υπάρξουν μη διαχειριζόμενες εξαιρέσεις – το σύστημα προειδοποιήσεων διαχειρίζεται ομαλά τυχόν άγνωστες γραμματοσειρές.

---

## Συχνές Ερωτήσεις & Απαντήσεις

**Ε: Θα λειτουργήσει αυτό με PDF που δημιουργούνται από το Word;**  
Α: Ναι. Το Aspose.Words αντιμετωπίζει τα PDF ως άλλη μορφή εξόδου. Η σύλληψη προειδοποιήσεων συμβαίνει κατά τη φάση *φόρτωσης*, επομένως είναι ανεξάρτητη από την τελική εξαγωγή.

**Ε: Τι γίνεται αν χρειαστεί να συλλέξω προειδοποιήσεις για **όλες** τις λειτουργίες εγγράφου (αποθήκευση, μετατροπή κ.λπ.);**  
Α: Μπορείτε να επαναχρησιμοποιήσετε το ίδιο `WarningInfoCollection` ορίζοντάς το στο `Document.WarningCallback` μετά τη δημιουργία του εγγράφου. Κάθε επακόλουθη λειτουργία θα προσθέτει νέες καταχωρήσεις στην ίδια συλλογή.

**Ε: Επηρεάζει η callback προειδοποιήσεων την απόδοση;**  
Α: Παρατηρείται αμελητέο αντίκτυπο. Η συλλογή αποθηκεύει απλώς αντικείμενα· εκτός αν επεξεργάζεστε χιλιάδες προειδοποιήσεις σε σφιχτό βρόχο, δεν θα παρατηρήσετε καθυστέρηση.

**Ε: Πώς μπορώ να καταστέψω προειδοποιήσεις που δεν με ενδιαφέρουν;**  
Α: Υλοποιήστε μια προσαρμοσμένη κλάση που κληρονομεί το `IWarningCallback` και φιλτράρετε μέσα στη μέθοδο `Warning`. Το ενσωματωμένο `WarningInfoCollection` απλώς αποθηκεύει, δεν φιλτράρει.

---

## Pro Tips & Πιθανά Πάγια

- **Pro tip:** Ελέγχετε πάντα το `Warning.Description` – περιέχει το ακριβές όνομα της γραμματοσειράς που λείπει. Αυτό μπορεί να σας βοηθήσει να αποφασίσετε αν θα συμπεριλάβετε τη γραμματοσειρά στην εφαρμογή σας.  
- **Προσοχή στις ενσωματωμένες γραμματοσειρές:** Αν το αρχικό DOCX έχει ήδη ενσωματωμένη τη ζητούμενη γραμματοσειρά, το Aspose.Words δεν θα εκδώσει προειδοποίηση αντικατάστασης, ακόμη κι αν η γραμματοσειρά δεν είναι εγκατεστημένη τοπικά.  
- **Ασφάλεια νήματος:** Το `WarningInfoCollection` δεν είναι thread‑safe. Αν φορτώνετε πολλά έγγραφα ταυτόχρονα, δώστε σε κάθε νήμα τη δική του συλλογή.  
- **Έλεγχος έκδοσης:** Το API προειδοποιήσεων είναι σταθερό από το Aspose.Words 20.8. Βεβαιωθείτε ότι χρησιμοποιείτε πρόσφατη έκδοση για να μην χάσετε νεότερους τύπους προειδοποιήσεων.

---

## Συμπέρασμα

Καλύψαμε **πώς να συλλέξετε προειδοποιήσεις** από το Aspose.Words, δείξαμε πώς να **λάβετε μηνύματα προειδοποίησης** και παρουσιάσαμε πρακτικούς τρόπους **διαχείρισης ελλιπών γραμματοσειρών** μέσω fallback ή προσαρμοσμένων φακέλων γραμματοσειρών. Το πλήρες παράδειγμα είναι έτοιμο να ενσωματωθεί σε οποιοδήποτε έργο .NET, και οι έννοιες κλιμακώνονται σε μεγαλύτερα pipelines αυτοματοποίησης.

Επόμενα βήματα:

- Χρήση του `Document.WarningCallback` για σύλληψη προειδοποιήσεων κατά τις **αποθηκεύσεις**.  
- Καταγραφή προειδοποιήσεων σε αρχείο ή σύστημα τηλεμετρίας για παρακολούθηση σε παραγωγή.  
- Επέκταση του callback ώστε να αντικαθιστά αυτόματα ελλιπείς γραμματοσειρές με εταιρικές γραμματοσειρές.

Πειραματιστείτε – αλλάξτε τη γραμματοσειρά fallback, προσθέστε περισσότερα έγγραφα στη δέσμη, ή ενσωματώστε τον συλλέκτη προειδοποιήσεων σε pipeline CI που επισημαίνει προβλήματα σχετιζόμενα με γραμματοσειρές. Καλό προγραμματισμό, και ας αποδίδουν πάντα τα έγγραφά σας ακριβώς όπως τα περιμένετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}