---
category: general
date: 2026-06-27
description: Καταχωρίστε τη λειτουργία κλήσης προειδοποίησης στο Aspose.Words για
  να εντοπίζετε αντικαταστάσεις γραμματοσειρών και προβλήματα φόρτωσης. Μάθετε τη
  χρήση του LoadOptions βήμα‑βήμα με το Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: el
og_description: Καταχωρίστε την κλήση επιστροφής προειδοποίησης στο Aspose.Words για
  να παρακολουθείτε τις αντικαταστάσεις γραμματοσειρών και άλλες προειδοποιήσεις φόρτωσης.
  Ακολουθήστε αυτό το πλήρες σεμινάριο για μια αξιόπιστη υλοποίηση.
og_title: Καταχώρηση Callback Προειδοποίησης στο Aspose.Words – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Καταχώρηση Callback Προειδοποίησης στο Aspose.Words – Πλήρης Οδηγός Προγραμματισμού
url: /el/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταχώρηση Callback Προειδοποίησης στο Aspose.Words – Πλήρης Οδηγός Προγραμματισμού

Σας έχει τύχει ποτέ να αναρωτηθείτε πώς να **register warning callback in Aspose.Words** ώστε να βλέπετε ακριβώς ποιες γραμματοσειρές αντικαθίστανται όταν φορτώνεται ένα έγγραφο; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν μια σιωπηλή αντικατάσταση γραμματοσειράς χαλάει τη διάταξη ενός παραγόμενου PDF ή αρχείου Word.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια πρακτική λύση που όχι μόνο καταχωρεί ένα warning callback στο Aspose.Words, αλλά εξηγεί επίσης *γιατί* θα θέλατε να το κάνετε, πώς λειτουργεί το callback εσωτερικά και ποιες περιπτώσεις άκρων μπορεί να συναντήσετε. Στο τέλος θα μπορείτε να καταγράφετε κάθε αντικατάσταση γραμματοσειράς, να εντοπίζετε άλλες προειδοποιήσεις φόρτωσης και να διατηρείτε τη διαδικασία επεξεργασίας εγγράφων διαφανή.

## Τι Θα Μάθετε

- Ρύθμιση **LoadOptions** για έλεγχο της συμπεριφοράς φόρτωσης εγγράφων.  
- Καταχώρηση **warning callback** που ενεργοποιείται για αντικατάσταση γραμματοσειράς και άλλους τύπους προειδοποιήσεων.  
- Φόρτωση ενός DOCX με τις ρυθμισμένες επιλογές και ερμηνεία της εξόδου του callback.  
- Συνηθισμένα προβλήματα (λείπουν γραμματοσειρές, προσαρμοσμένοι φάκελοι γραμματοσειρών, και ζητήματα απόδοσης).  

**Προαπαιτούμενα:** Visual Studio 2022 (ή οποιοδήποτε IDE C#), .NET 6+ runtime, και ενεργή άδεια Aspose.Words (η δωρεάν δοκιμή λειτουργεί για πειραματισμό). Δεν απαιτούνται επιπλέον πακέτα NuGet πέρα από `Aspose.Words`.

---

![Διάγραμμα που απεικονίζει τη ροή καταχώρησης ενός warning callback στο Aspose.Words και τη διαχείριση προειδοποιήσεων αντικατάστασης γραμματοσειράς](register-warning-callback-aspose-words.png "διάγραμμα καταχώρησης warning callback aspose.words")

## Βήμα 1: Δημιουργία LoadOptions – Το Σημείο Εισόδου για Διαχείριση Προειδοποιήσεων  

Πριν το callback μπορέσει να ενεργοποιηθεί, χρειάζεστε μια παρουσία του **LoadOptions**. Σκεφτείτε το ως τον πίνακα ελέγχου που παραδίδετε στο Aspose.Words όταν λέτε «φόρτωσε αυτό το αρχείο, αλλά ενημέρωσέ με αν κάτι φαίνεται λανθασμένο».  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Γιατί είναι σημαντικό:** Το `LoadOptions` σας επιτρέπει να ρυθμίσετε τα πάντα, από κωδικούς κρυπτογράφησης μέχρι καταλόγους γραμματοσειρών. Συνδέοντας ένα warning callback σε αυτό το αντικείμενο, μετατρέπετε μια σιωπηλή διαδικασία σε μια παρατηρήσιμη.

## Βήμα 2: Καταχώρηση του Warning Callback – Καταγραφή Αντικαταστάσεων Γραμματοσειρών  

Τώρα έρχεται το αστέρι της παράστασης: το **warning callback**. Θα καταχωρήσουμε μια ανώνυμη μέθοδο (ένα lambda) που το Aspose.Words καλεί για κάθε προειδοποίηση φόρτωσης. Μέσα στο callback φιλτράρουμε για `WarningType.FontSubstitution` και εκτυπώνουμε ένα φιλικό μήνυμα.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Pro tip:** Αν θέλετε επίσης να καταγράφετε ελλιπείς εικόνες ή μη υποστηριζόμενα χαρακτηριστικά, προσθέστε επιπλέον κλάδους `if` που ελέγχουν το `args.WarningType`. Έτσι η υλοποίηση **register warning callback in Aspose.Words** γίνεται ένα‑σταθμός για όλα τα διαγνωστικά φόρτωσης.

## Βήμα 3: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Ρυθμισμένες LoadOptions  

Με το callback συνδεδεμένο, το επόμενο βήμα είναι απλώς η φόρτωση του εγγράφου. Περνάτε την παρουσία `loadOptions` στον κατασκευαστή `Document`. Κάθε φορά που το Aspose.Words συναντά μια γραμματοσειρά που δεν μπορεί να βρει, το callback σας θα ενεργοποιηθεί και θα γράψει στην κονσόλα.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Τρέξτε το πρόγραμμα και θα δείτε έξοδο παρόμοια με:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Αυτή είναι η ουσία του **register warning callback aspose.words**—ένα τρι‑βήμα μοτίβο που μπορείτε να επαναχρησιμοποιήσετε σε οποιοδήποτε έργο.

## Βήμα 4: Επέκταση του Callback για Πραγματικές Σενάρια  

### 4.1 Καταγραφή σε Αρχείο Αντί για Κονσόλα  

Σε παραγωγή σπάνια θέλετε «σπάμ» στην κονσόλα. Αντικαταστήστε το `Console.WriteLine` με έναν logger (π.χ., `Serilog`, `NLog`) ή γράψτε σε αρχείο κειμένου:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Παροχή Προσαρμοσμένου Καταλόγου Γραμματοσειρών  

Αν το περιβάλλον σας χρησιμοποιεί εταιρικές γραμματοσειρές, ενημερώστε το Aspose.Words πού να ψάξει πριν καταφύγει στην αντικατάσταση:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Τώρα το callback μπορεί να ενεργοποιείται *λιγότερο* συχνά, επειδή η μηχανή βρίσκει τις σωστές γραμματοσειρές.

### 4.3 Διαχείριση Μη‑Γραμματοσειράς Προειδοποιήσεων  

Μπορείτε να επεκτείνετε το πεδίο ώστε να καταγράφετε οποιαδήποτε προειδοποίηση φόρτωσης:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Βήμα 5: Δοκιμή της Υλοποίησής Σας – Τι να Περιμένετε  

### 5.1 Επαλήθευση με Έγγραφο που Έχει Λείπουν Γραμματοσειρές  

Δημιουργήστε ένα μικρό DOCX που αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας (π.χ., “Comic Sans MS” σε διακομιστή Linux). Εκτελέστε τον φορτωτή· θα πρέπει να δείτε μήνυμα αντικατάστασης.  

### 5.2 Μέτρηση Επιβάρυνσης  

Το callback προσθέτει αμελητέο κόστος—περίπου μερικά μικροδευτερόλεπτα ανά προειδοποίηση. Αν φορτώνετε χιλιάδες έγγραφα, ίσως να ομαδοποιήσετε τις εγγραφές ή να απενεργοποιήσετε το callback για μη‑κριτικές εκτελέσεις.

### 5.3 Περιπτώσεις Άκρων  

- **Πολλαπλές Αντικαταστάσεις για την Ίδια Γραμματοσειρά:** Το Aspose.Words μπορεί να ενεργοποιήσει το callback πολλές φορές αν η ίδια λείπουσα γραμματοσειρά εμφανίζεται σε διαφορετικές σελίδες. Απομακρύνετε διπλότυπα στον logger αν χρειάζεται.  
- **Κρυπτογραφημένα Έγγραφα:** Αν το DOCX είναι προστατευμένο με κωδικό, πρέπει επίσης να ορίσετε `loadOptions.Password`. Το callback θα ενεργοποιηθεί μετά την αποκρυπτογράφηση.  
- **Ασύγχρονη Φόρτωση:** Το API είναι συγχρονικό, αλλά μπορείτε να τυλίξετε την κλήση φόρτωσης σε `Task.Run` για επεξεργασία στο παρασκήνιο· το callback παραμένει thread‑safe.

## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε  

| Πιθανό Σφάλμα | Γιατί Συμβαίνει | Λύση |
|---------------|------------------|------|
| **Καμία έξοδος καθόλου** | Το callback δεν έχει ανατεθεί *ή* το `WarningCallback` αντικαταστάθηκε αργότερα. | Βεβαιωθείτε ότι αναθέτετε το callback **μία φορά** πριν τη φόρτωση και μην επανα‑αναθέτετε το `loadOptions` μετά την ανάθεση. |
| **Λάθος εξαίρεση μετατροπής** | Προσπάθεια μετατροπής προειδοποίησης που δεν είναι `FontSubstitutionWarningInfo`. | Πάντα ελέγχετε το `args.WarningType` πριν κάνετε cast. |
| **Μείωση απόδοσης** | Συγχρονική καταγραφή σε αργό μέσο I/O. | Χρησιμοποιήστε ασύγχρονα frameworks καταγραφής ή buffer τις εγγραφές. |
| **Λείπουν προσαρμοσμένες γραμματοσειρές** | Ο φάκελος γραμματοσειρών δεν προστέθηκε στο `FontSettings`. | Προσθέστε `SetFontsFolder` όπως φαίνεται στο Βήμα 4.2. |

## Πλήρες Παράδειγμα – Αντιγράψτε‑Και‑Τρέξτε  

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε σε ένα νέο έργο Console App. Δείχνει ολόκληρη τη ροή από την αρχή μέχρι το τέλος.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα** (υπόθεση λείποντων γραμματοσειρών):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Τρέξτε το πρόγραμμα και θα δείτε ακριβώς ποιες γραμματοσειρές αντικαθιστά το Aspose.Words, προσφέροντάς σας πλήρη διαφάνεια στη διαδικασία φόρτωσης.

---

## Συμπέρασμα  

Μόλις καλύψαμε **πώς να καταχωρήσετε warning callback in Aspose.Words**, γιατί αποτελεί βέλτιστη πρακτική για κάθε ροή επεξεργασίας εγγράφων, και πώς να επεκτείνετε το μοτίβο για καταγραφή, προσαρμοσμένες γραμματοσειρές και ευρύτερη διαχείριση προειδοποιήσεων. Με μόλις τρεις γραμμές κώδικα μετατρέπετε μια μαύρο‑κουτί λειτουργία φόρτωσης σε ένα βήμα ελεγχόμενο, διαγνώσιμο—χωρίς μυστικές αλλαγές διάταξης.

Τι ακολουθεί; Δοκιμάστε να συνδυάσετε αυτό το callback με **Aspose.Words SaveOptions** για να καταγράφετε προειδοποιήσεις τόσο κατά τη φόρτωση *όσο* και την αποθήκευση, ή ενσωματώστε το callback σε ένα web API που επεξεργάζεται ανεβάσματα σε πραγματικό χρόνο. Μπορείτε επίσης να εξερευνήσετε τις δευτερεύουσες λέξεις‑κλειδιά που εισάγαμε—όπως *loadoptions font substitution warning*—για να βελτιστοποιήσετε την απόδοση ή να ενσωματώσετε το σύστημα σε πίνακα παρακολούθησης.

Έχετε ερωτήσεις ή δύσκολο σενάριο; Αφήστε ένα σχόλιο και ας το λύσουμε μαζί. Καλό κώδικα, και ας αποδίδουν πάντα τα PDFs σας με τις σωστές γραμματοσειρές!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}