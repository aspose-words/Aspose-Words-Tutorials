---
category: general
date: 2026-06-24
description: Πώς να χρησιμοποιήσετε το IWarningCallback για να εντοπίσετε ελλείποντες
  γραμματοσειρές σε έγγραφα Aspose.Words. Μάθετε ένα πλήρες, εκτελέσιμο παράδειγμα
  και τις βέλτιστες πρακτικές.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: el
og_description: Πώς να χρησιμοποιήσετε το IWarningCallback για να εντοπίσετε ελλείπουσες
  γραμματοσειρές στο Aspose.Words. Ακολουθήστε τον οδηγό βήμα‑βήμα για μια πλήρη,
  έτοιμη για παραγωγή λύση.
og_title: Πώς να χρησιμοποιήσετε το IWarningCallback – Εντοπισμός ελλιπών γραμματοσειρών
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να χρησιμοποιήσετε το IWarningCallback – Εντοπισμός ελλιπών γραμματοσειρών
  με το Aspose.Words
url: /el/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να χρησιμοποιήσετε το IWarningCallback – Εντοπισμός ελλειπόντων γραμματοσειρών με το Aspose.Words

Η χρήση του **IWarningCallback** είναι απαραίτητη όταν εργάζεστε με το Aspose.Words και χρειάζεται να **εντοπίσετε ελλείπουσες γραμματοσειρές** σε ένα αρχείο DOCX. Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από ένα πλήρες παράδειγμα αντιγραφής‑και‑επικόλλησης που δείχνει ακριβώς πώς να χρησιμοποιήσετε το IWarningCallback για να συλλάβετε προειδοποιήσεις αντικατάστασης γραμματοσειρών, γιατί είναι σημαντικό και τι να κάνετε μόλις τις καταγράψετε.

Αν έχετε ανοίξει ποτέ ένα έγγραφο και έχετε δει ακατάληπτο κείμενο επειδή μια προσαρμοσμένη γραμματοσειρά δεν ήταν εγκατεστημένη, ξέρετε την απογοήτευση. Στο τέλος αυτού του σεμιναρίου θα έχετε έναν αξιόπιστο τρόπο να εντοπίζετε αυτά τα προβλήματα προγραμματιστικά, να τα καταγράφετε ή ακόμη και να εφαρμόζετε αυτόματα μια εναλλακτική γραμματοσειρά.

## Τι θα μάθετε

- Τον σκοπό του **IWarningCallback** και πότε να το χρησιμοποιήσετε.  
- Πώς να υλοποιήσετε έναν προσαρμοσμένο συλλέκτη προειδοποιήσεων που απομονώνει τα γεγονότα **εντοπισμού ελλειπόντων γραμματοσειρών**.  
- Πώς να ενσωματώσετε τον συλλέκτη στα **LoadOptions** ώστε κάθε φόρτωση εγγράφου να παρακολουθείται.  
- Πώς να επαληθεύσετε την έξοδο και να διαχειριστείτε ειδικές περιπτώσεις (πολλές ελλείπουσες γραμματοσειρές, σιωπηλές προειδοποιήσεις κ.λπ.).  

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.6+).  
- Aspose.Words for .NET εγκατεστημένο μέσω NuGet (`Install-Package Aspose.Words`).  
- Ένα αρχείο DOCX που αναφέρει μια γραμματοσειρά που δεν υπάρχει στη μηχανή (π.χ., `DocumentWithMissingFont.docx`).  

Δεν απαιτούνται πρόσθετες βιβλιοθήκες — όλα βρίσκονται μέσα στο Aspose.Words.

---

## Πώς να χρησιμοποιήσετε το IWarningCallback για να εντοπίσετε ελλείπουσες γραμματοσειρές στο Aspose.Words

Παρακάτω βρίσκεται το **πλήρες, εκτελέσιμο πρόγραμμα**. Αντιγράψτε το σε ένα νέο έργο console, προσαρμόστε τη διαδρομή του αρχείου και τρέξτε το. Θα δείτε την έξοδο της κονσόλας για κάθε προειδοποίηση ελλειπούσας γραμματοσειράς.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Αναμενόμενη έξοδος

Αν το `DocumentWithMissingFont.docx` αναφέρει μια γραμματοσειρά με όνομα *“MyFancyFont”* που δεν είναι εγκατεστημένη, θα δείτε κάτι όπως:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Κάθε γραμμή που αρχίζει με **[Missing Font]** παράγεται από την υλοποίηση του **IWarningCallback**, αποδεικνύοντας ότι εντοπίσαμε επιτυχώς **ελλείπουσες γραμματοσειρές**.

---

## Βήμα 1: Υλοποίηση της διεπαφής IWarningCallback

Γιατί χρειάζεται μια προσαρμοσμένη κλάση; Το Aspose.Words εγείρει **προειδοποιήσεις** για διάφορους λόγους — προβλήματα μορφής αρχείου, παρωχημένες λειτουργίες και, πιο σημαντικό για εμάς, αντικατάσταση γραμματοσειρών. Υλοποιώντας το `IWarningCallback`, λαμβάνουμε ένα hook που δέχεται κάθε προειδοποίηση τη στιγμή που συμβαίνει. Φιλτράροντας για `WarningType.FontSubstitution` απομονώνουμε το συγκεκριμένο σενάριο όπου μια γραμματοσειρά λείπει.

**Συμβουλή:** Αν θέλετε να καταγράψετε *όλες* τις προειδοποιήσεις για διαγνωστικούς σκοπούς, απλώς αφαιρέστε τον έλεγχο `if` και καταγράψτε κάθε `info.Type`.

---

## Βήμα 2: Ενσωμάτωση του Callback στα LoadOptions

Το `LoadOptions` είναι η πύλη που λέει στο Aspose.Words πώς να αντιμετωπίσει το εισερχόμενο έγγραφο. Ορίζοντας το `WarningCallback` σε μια παρουσία του συλλέκτη μας εξασφαλίζει ότι το callback είναι ενεργό για ολόκληρη τη διαδικασία φόρτωσης. Μπορείτε να επαναχρησιμοποιήσετε το ίδιο αντικείμενο `LoadOptions` για πολλά έγγραφα, κάτι που είναι χρήσιμο σε pipelines μαζικής επεξεργασίας.

**Συχνή ερώτηση:** *Τι γίνεται αν φορτώσω ένα έγγραφο χωρίς να ορίσω LoadOptions;*  
Απάντηση: Το Aspose.Words θα εξακολουθήσει να εγείρει προειδοποιήσεις εσωτερικά, αλλά χωρίς callback αυτές θα απορριφθούν σιωπηλά, και χάνετε την ευκαιρία να **εντοπίσετε ελλείπουσες γραμματοσειρές**.

---

## Βήμα 3: Φόρτωση εγγράφου και σύλληψη προειδοποιήσεων ελλειπούσας γραμματοσειράς

Ο κατασκευαστής `Document` που δέχεται διαδρομή αρχείου και `LoadOptions` κάνει τη βαριά δουλειά. Καθώς το αρχείο αναλύεται, κάθε ελλείπουσα γραμματοσειρά ενεργοποιεί τη μέθοδο `FontWarningCollector.Warning`. Η έξοδος της κονσόλας αποδεικνύει ότι ο μηχανισμός λειτουργεί.

**Περίπτωση άκρης:** Ένα μόνο έγγραφο μπορεί να αναφέρει πολλές απουσίες γραμματοσειρών. Το callback εκτελείται μία φορά ανά ελλείπουσα γραμματοσειρά, έτσι θα δείτε πολλές γραμμές — ιδανικό για τη δημιουργία μιας ολοκληρωμένης αναφοράς.

---

## Γιατί να χρησιμοποιήσετε το IWarningCallback αντί για χειροκίνητους ελέγχους γραμματοσειρών;

Θα μπορούσατε να σαρώσετε χειροκίνητα τις ιδιότητες `Run.Font` του εγγράφου μετά τη φόρτωση, αλλά αυτό απαιτεί το έγγραφο να φορτωθεί επιτυχώς πρώτα — κάτι που αποτυγχάνει αν η γραμματοσειρά λείπει εντελώς. Το σύστημα προειδοποιήσεων λειτουργεί **πριν** γίνει οποιαδήποτε αντικατάσταση, δίνοντάς σας μια ακριβή εικόνα του τι λείπει.

Επιπλέον, το callback εκτελείται **ως μέρος της διαδικασίας φόρτωσης**, πράγμα που σημαίνει ότι μπορείτε να τερματίσετε νωρίς, να αντικαταστήσετε γραμματοσειρές επί τόπου ή να καταγράψετε λεπτομερή διαγνωστικά χωρίς επιπλέον περάσματα στο δέντρο του εγγράφου.

---

## Διαχείριση πολλαπλών ελλειπούσων γραμματοσειρών με χάρη

Αν προβλέπετε πολλές ελλείπουσες γραμματοσειρές, σκεφτείτε να τις συγκεντρώσετε σε μια συλλογή:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Μετά τη φόρτωση, μπορείτε να διατρέξετε το `MissingFonts` και, για παράδειγμα, να τα γράψετε σε ένα αρχείο CSV για την ομάδα σχεδίασης.

---

## Bonus: Καταγραφή προειδοποιήσεων σε αρχείο

Η έξοδος στην κονσόλα είναι επαρκής για demos, αλλά ο κώδικας παραγωγής συνήθως καταγράφει σε μόνιμο αποθηκευτικό χώρο. Αντικαταστήστε την κλήση `Console.WriteLine` με κάτι όπως:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Τώρα έχετε ένα αρχείο ελέγχου που μπορεί να ελεγχθεί αργότερα, ικανοποιώντας απαιτήσεις συμμόρφωσης.

---

## Συμπέρασμα

Καλύψαμε **πώς να χρησιμοποιήσετε το IWarningCallback** για να **εντοπίσετε ελλείπουσες γραμματοσειρές** στο Aspose.Words, από την υλοποίηση του callback μέχρι την ενσωμάτωσή του στα `LoadOptions` και τη διαχείριση των προειδοποιήσεων. Αυτή η προσέγγιση σας παρέχει άμεση εικόνα για προβλήματα σχετιζόμενα με γραμματοσειρές, επιτρέποντάς σας να καταγράψετε, να αντικαταστήσετε ή να ειδοποιήσετε τους χρήστες πριν το έγγραφο αποδοθεί.

Επόμενα βήματα που μπορείτε να εξερευνήσετε:

- **Fallback fonts:** προγραμματιστική ανάθεση προεπιλεγμένης γραμματοσειράς όταν συμβαίνει αντικατάσταση.  
- **Batch processing:** επανάληψη σε φάκελο εγγράφων, επαναχρησιμοποίηση του ίδιου `AggregatingFontCollector`.  
- **User feedback:** εμφάνιση προειδοποιήσεων ελλειπούσας γραμματοσειράς σε UI αντί για την κονσόλα.

Δοκιμάστε το στο δικό σας έργο — τέλος στις μυστηριώδεις ακατανόητες γραμμές, μόνο σαφείς, ενέργειες διαγνωστικές. Καλό coding!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας projects.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}