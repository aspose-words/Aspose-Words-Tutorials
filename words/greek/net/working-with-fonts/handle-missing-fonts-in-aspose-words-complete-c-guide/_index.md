---
category: general
date: 2026-03-14
description: Handle missing fonts quickly with Aspose.Words. Learn how to capture
  font substitution warnings, configure LoadOptions, and avoid rendering issues.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: el
og_description: Διαχειριστείτε τις ελλείπουσες γραμματοσειρές στο Aspose.Words χρησιμοποιώντας
  έναν συλλέκτη προειδοποιήσεων. Αυτό το σεμινάριο δείχνει βήμα‑προς‑βήμα πώς να εντοπίσετε
  και να καταγράψετε τις αντικαταστάσεις γραμματοσειρών.
og_title: Διαχείριση Ελλειπουσών Γραμματοσειρών στο Aspose.Words – Πλήρης Οδηγός C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Διαχείριση Ελλειπουσών Γραμματοσειρών στο Aspose.Words – Πλήρης Οδηγός C#
url: /el/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαχείριση Ελλειπουσών Γραμματοσειρών στο Aspose.Words – Πλήρης Οδηγός C#

Έχετε ποτέ χρειαστεί να **διαχειριστείτε ελλειπούσες γραμματοσειρές** κατά τη φόρτωση ενός εγγράφου Word και αναρωτηθήκατε γιατί το PDF ή η εικόνα εξόδου φαίνεται παραμορφωμένη; Δεν είστε μόνοι. Τα ελλείποντα αρχεία γραμματοσειρών είναι ένας σιωπηλός προβληματιστής που μπορεί να μετατρέψει μια τέλεια σχεδιασμένη αναφορά σε ένα ακατάστατο χάος.  

Τα καλά νέα; Το Aspose.Words σας παρέχει έναν καθαρό τρόπο να εντοπίζετε αυτά τα γεγονότα αντικατάστασης γραμματοσειρών, να τα καταγράφετε και ακόμη να αντικαθιστάτε με μια εφεδρική γραμματοσειρά αν το θέλετε. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει ακριβώς πώς να ρυθμίσετε έναν συλλέκτη προειδοποιήσεων, να τον συνδέσετε με το `LoadOptions` και να φορτώσετε ένα έγγραφο που μπορεί να περιέχει ελλειπούσες γραμματοσειρές.

Στο τέλος αυτού του οδηγού θα μπορείτε να:

* Ανιχνεύσετε κάθε αντικατάσταση γραμματοσειράς που συμβαίνει κατά τη φόρτωση του εγγράφου.  
* Εμφανίσετε ένα φιλικό μήνυμα στην κονσόλα (ή το δρομολογήσετε σε logger) για κάθε ελλειπούσα γραμματοσειρά.  
* Επεκτείνετε τη λύση ώστε να αντικαθιστά γραμματοσειρές, εάν χρειάζεται.  

**Προαπαιτούμενα** – θα χρειαστείτε:

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Core και .NET Framework).  
* Το πακέτο NuGet Aspose.Words for .NET (τρέχουσα έκδοση 23.11).  
* Ένα αρχείο Word που σκόπιμα αναφέρεται σε μια γραμματοσειρά που δεν έχετε εγκατεστημένη – θα το ονομάσουμε `doc-with-missing-font.docx`.  

Αν είστε ήδη άνετοι με τη C# και έχετε ένα έργο έτοιμο, μπορείτε να περάσετε κατευθείαν στον κώδικα. Διαφορετικά, συνεχίστε την ανάγνωση· θα καλύψουμε πρώτα τα μικρά βήματα ρύθμισης.

---

## Γιατί η Διαχείριση Ελλειπουσών Γραμματοσειρών Είναι Σημαντική

Όταν το Aspose.Words φορτώνει ένα έγγραφο, προσπαθεί να αντιστοιχίσει κάθε γλύφο σε μια γραμματοσειρά εγκατεστημένη στο μηχάνημα. Αν δεν βρει την ακριβή γραμματοσειρά, αντικαθιστά σιωπηλά την πιο κοντινή. Αυτή η αντικατάσταση μπορεί να αλλάξει το ύψος των γραμμών, το kerning και ακόμη να κάνει χαρακτήρες να εξαφανιστούν. Καταγράφοντας το συμβάν `WarningType.FontSubstitution` παίρνετε μια διαφανή εικόνα του **τι** αντικαταστάθηκε και **γιατί**, κάτι που είναι ουσιώδες για:

* Διατήρηση της συνέπειας του brand (η εταιρική σας γραμματοσειρά πρέπει να εμφανίζεται ακριβώς όπως σχεδιάστηκε).  
* Εντοπισμό προβλημάτων μετατροπής PDF—συχνά ο ένοχος είναι μια ελλειπούσα γραμματοσειρά.  
* Δημιουργία αυτοματοποιημένων pipelines εγγράφων όπου χρειάζεται να σηματοδοτήσετε προβληματικά αρχεία για χειροκίνητη ανασκόπηση.

Τώρα που το «γιατί» είναι σαφές, ας βουτήξουμε στο **πώς**.

---

## Βήμα 1 – Ρύθμιση του Συλλέκτη Προειδοποιήσεων

Το πρώτο που χρειαζόμαστε είναι ένα αντικείμενο που μπορεί να ακούει τις προειδοποιήσεις του Aspose.Words. Το `DocumentWarnings` υλοποιεί το `IWarningCallback`, επιτρέποντάς μας να αντιδράμε όποτε η βιβλιοθήκη εκκινεί μια προειδοποίηση.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Τι συμβαίνει;**  
* Το `DocumentWarnings` είναι ένα ελαφρύ wrapper γύρω από τη διεπαφή callback.  
* Η λήψη ελέγχει το `e.WarningType` ώστε να αγνοούμε άσχετες προειδοποιήσεις (π.χ. παρωχημένες δυνατότητες).  
* Το `e.WarningInfo` περιέχει το όνομα της ελλειπούσας γραμματοσειράς, το οποίο τυπώνουμε στην κονσόλα.  

*Συμβουλή*: Αντικαταστήστε το `Console.WriteLine` με έναν δομημένο logger (Serilog, NLog) σε παραγωγικό περιβάλλον—έτσι θα έχετε αυτόματα timestamps και επίπεδα καταγραφής.

---

## Βήμα 2 – Σύνδεση του Συλλέκτη με το LoadOptions

Το `LoadOptions` είναι ο φύλακας για κάθε έγγραφο που ανοίγετε με το Aspose.Words. Αναθέτοντας το στιγμιότυπο `fontWarnings` στην ιδιότητα `WarningCallback`, διασφαλίζουμε ότι ο συλλέκτης είναι ενεργός κατά τη διαδικασία φόρτωσης.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Γιατί χρησιμοποιούμε το LoadOptions;**  
Εκτός από τις προειδοποιήσεις, το `LoadOptions` σας επιτρέπει να ελέγχετε τον χειρισμό κωδικών πρόσβασης, την κωδικοποίηση και ακόμη την προσαρμοσμένη φόρτωση πόρων. Εδώ εστιάζουμε στην πλευρά των προειδοποιήσεων, αλλά το ίδιο μοτίβο λειτουργεί και για άλλες callbacks.

---

## Βήμα 3 – Φόρτωση του Εγγράφου με τις Ρυθμισμένες Επιλογές

Τώρα φέρνουμε το έγγραφο στη μνήμη. Αν λείπει κάποια γραμματοσειρά, ο συλλέκτης μας θα ενεργοποιηθεί και θα δείτε μια γραμμή στην κονσόλα για κάθε αντικατάσταση.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Αν εκτελέσετε αυτό το απόσπασμα με ένα έγγραφο που αναφέρει, π.χ., *Calibri Light* ενώ η δοκιμαστική σας μηχανή έχει μόνο *Calibri*, θα λάβετε έξοδο παρόμοια με:

```
Font 'Calibri Light' was substituted.
```

Αυτή είναι η πλήρης λούπα ανίχνευσης—απλή, αλλά ισχυρή.

---

## Βήμα 4 – (Προαιρετικό) Αντικατάσταση Ελλειπουσών Γραμματοσειρών με Γνωστή Εναλλακτική

Μερικές φορές δεν θέλετε μόνο να καταγράψετε το πρόβλημα· θέλετε να επιβάλετε μια εφεδρική γραμματοσειρά ώστε το παραγόμενο αποτέλεσμα να είναι συνεπές. Το Aspose.Words σας επιτρέπει να παρέχετε ένα προσαρμοσμένο αντικείμενο `FontSettings` που αντιστοιχίζει τις ελλειπούσες γραμματοσειρές σε μια αντικατάσταση.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Επεξήγηση**  
* Το σύμβολο μπαλαντέρ `"*"` λέει στο Aspose.Words να αντιμετωπίζει *κάθε* ελλειπούσα γραμματοσειρά με τον ίδιο τρόπο.  
* Μπορείτε επίσης να αντιστοιχίσετε συγκεκριμένες γραμματοσειρές ξεχωριστά αν χρειάζεστε πιο λεπτομερή έλεγχο.  
* Αφού ορίσετε το `document.FontSettings`, οποιαδήποτε επακόλουθη απόδοση (PDF, εικόνα, HTML) θα σέβεται την αντικατάσταση.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια εφαρμογή console. Περιλαμβάνει όλες τις απαραίτητες δηλώσεις `using`, διαχείριση σφαλμάτων και σχόλια για σαφήνεια.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Αναμενόμενη έξοδος** (όταν εντοπιστεί ελλειπούσα γραμματοσειρά):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Αν το πηγαίο έγγραφο περιέχει ήδη όλες τις απαιτούμενες γραμματοσειρές, η γραμμή προειδοποίησης απλώς δεν θα εμφανιστεί—δεν υπάρχει τίποτα για ανησυχία.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι κάνω αν θέλω μόνο να καταγράψω, όχι να αντικαταστήσω γραμματοσειρές;** | Παραλείψτε εντελώς το τμήμα `FontSettings`; ο μόνος συλλέκτης προειδοποιήσεων είναι αρκετός. |
| **Μπορώ να ανακατευθύνω τις προειδοποιήσεις σε αρχείο;** | Ναι—αντικαταστήστε το `Console.WriteLine` με `File.AppendAllText("font-warnings.log", …)`. |
| **Λειτουργεί για DOC, DOCX και ODT;** | Απόλυτα. Το `LoadOptions` ισχύει για όλες τις μορφές που υποστηρίζει το Aspose.Words. |
| **Τι γίνεται με προσαρμοσμένες γραμματοσειρές ενσωματωμένες στο έγγραφο;** | Οι ενσωματωμένες γραμματοσειρές παρακάμπτουν τον μηχανισμό αντικατάστασης· χρησιμοποιούνται όπως είναι. |
| **Υπάρχει κάποια επίπτωση στην απόδοση;** | Το κόστος είναι ελάχιστο—ένας callback ανά ελλειπούσα γραμματοσειρά. Για μεγάλες δέσμες, σκεφτείτε να συγκεντρώνετε τις προειδοποιήσεις αντί να γράφετε ανά συμβάν. |

---

## Συμπέρασμα

Σας δείξαμε **πώς να διαχειριστείτε ελλειπούσες γραμματοσειρές** στο Aspose.Words, συνδέοντας έναν συλλέκτη `DocumentWarnings` με το `LoadOptions`, προαιρετικά αντικαθιστώντας με εφεδρική γραμματοσειρά, και αποθηκεύοντας το αποτέλεσμα. Αυτό το μοτίβο σας δίνει πλήρη ορατότητα στα γεγονότα αντικατάστασης γραμματοσειρών, βοηθώντας σας να διατηρήσετε την οπτική ακεραιότητα σε μετατροπές PDF, εικόνας ή HTML.

Επόμενα βήματα που μπορείτε να εξερευνήσετε:

* Ενσωμάτωση του συλλέκτη προειδοποιήσεων σε ένα κεντρικό σύστημα logging.  
* Δημιουργία πίνακα ελέγχου UI που καταγράφει έγγραφα με ελλειπούσες γραμματοσειρές για μαζική επεξεργασία.  
* Συνδυασμός αυτής της προσέγγισης με το Aspose.PDF για επαλήθευση ότι τα παραγόμενα PDF χρησιμοποιούν πραγματικά τη εφεδρική γραμματοσειρά.  

Μη διστάσετε να πειραματιστείτε—αλλάξτε το `"Arial"` σε `"Tahoma"` ή φορτώστε διαφορετικό σύνολο εγγράφων. Η βασική ιδέα παραμένει η ίδια: καταγράψτε την προειδοποίηση, ενεργήστε ανάλογα, και κρατήστε τα έγγραφά σας ακριβώς όπως προορίζονται.

Καλή προγραμματιστική! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}