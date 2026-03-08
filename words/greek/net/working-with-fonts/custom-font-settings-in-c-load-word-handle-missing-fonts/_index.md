---
category: general
date: 2026-03-08
description: Οι προσαρμοσμένες ρυθμίσεις γραμματοσειρών σάς επιτρέπουν να ορίσετε
  τις ρυθμίσεις γραμματοσειρών, να φορτώσετε με ασφάλεια έγγραφο Word και να διαχειριστείτε
  τις ελλείπουσες γραμματοσειρές με το Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: el
og_description: Οι προσαρμοσμένες ρυθμίσεις γραμματοσειράς σάς επιτρέπουν να ορίσετε
  ρυθμίσεις γραμματοσειράς, να φορτώσετε ασφαλώς έγγραφο Word και να διαχειριστείτε
  τις ελλιπείς γραμματοσειρές με το Aspose.Words.
og_title: Προσαρμοσμένες Ρυθμίσεις Γραμματοσειράς σε C# – Φόρτωση Word & Διαχείριση
  Ελλειπουσών Γραμματοσειρών
tags:
- Aspose.Words
- C#
- Font Management
title: Προσαρμοσμένες Ρυθμίσεις Γραμματοσειράς σε C# – Φόρτωση Word & Διαχείριση Ελλειπουσών
  Γραμματοσειρών
url: /el/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσαρμοσμένες Ρυθμίσεις Γραμματοσειράς σε C# – Φόρτωση Word & Διαχείριση Ελλειπουσών Γραμματοσειρών

Έχετε αναρωτηθεί ποτέ πώς λειτουργούν οι **custom font settings** όταν ένα αρχείο Word αναφέρει γραμματοσειρές που δεν έχετε εγκαταστήσει; Είναι ένα συνηθισμένο πρόβλημα—το έγγραφό σας φαίνεται σωστό σε έναν υπολογιστή, αλλά ξαφνικά κάθε παράγραφος αλλάζει σε μια εναλλακτική γραμματοσειρά σε έναν άλλο.  

Τα καλά νέα; Με το Aspose.Words μπορείτε να **set font settings**, **load Word document** περιεχόμενο, και **handle missing fonts** όλα σε μία καθαρή ροή. Παρακάτω θα βρείτε ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει ακριβώς πώς να το κάνετε, καθώς και το «γιατί» πίσω από κάθε βήμα.

## Τι Θα Μάθετε

Σε αυτόν τον οδηγό θα καλύψουμε:

* Δημιουργία ενός αντικειμένου `LoadOptions` και σύνδεση μιας παρουσίας `FontSettings`.  
* Καταχώρηση μιας callback προειδοποίησης ώστε να βλέπετε ποιες γραμματοσειρές αντικαθίστανται.  
* Φόρτωση ενός αρχείου DOCX που μπορεί να λείπουν γραμματοσειρές, και εκτύπωση των λεπτομερειών αντικατάστασης στην κονσόλα.  

Στο τέλος θα μπορείτε να διανείμετε την εφαρμογή C# με σιγουριά, γνωρίζοντας ότι κάθε σενάριο ελλιπούς γραμματοσειράς καταγράφεται και μπορεί να αντιμετωπιστεί αργότερα.

> **Prerequisite:** Aspose.Words for .NET (v23.12 ή νεότερο) εγκατεστημένο μέσω NuGet, και βασική εξοικείωση με εφαρμογές κονσόλας C#.

---

## Custom Font Settings – Configure LoadOptions

Το πρώτο πράγμα που χρειάζεστε είναι ένα αντικείμενο `LoadOptions`. Αυτό λέει στο Aspose.Words πώς να αντιμετωπίσει το εισερχόμενο αρχείο. Αναθέτοντας μια νέα παρουσία `FontSettings` δίνουμε στη βιβλιοθήκη ένα μέρος για να ψάξει για προσαρμοσμένες γραμματοσειρές.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Why this matters:**  
Αν παραλείψετε το `FontSettings`, το Aspose.Words επιστρέφει στη προεπιλεγμένη συλλογή γραμματοσειρών του συστήματος. Αυτό σημαίνει ότι οποιαδήποτε λείπει γραμματοσειρά θα αντικατασταθεί σιωπηρά, και δεν θα ξέρετε ποιες αντικαταστάθηκαν. Δημιουργώντας ένα ρητό κοντέινερ `FontSettings` αποκτάτε πλήρη έλεγχο της διαδικασίας αναζήτησης.

---

## Set Font Settings on LoadOptions

Τώρα που έχουμε ένα αντικείμενο `FontSettings`, ίσως αναρωτιέστε πού να το κατευθύνουμε. Συνήθως προσθέτετε έναν φάκελο που περιέχει τις γραμματοσειρές που διανέμετε με την εφαρμογή σας:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Αν δεν έχετε ιδιωτικό φάκελο, μπορείτε να παραλείψετε αυτό το μπλοκ—το Aspose.Words θα συνεχίσει να αναφέρει τις ελλιπείς γραμματοσειρές μέσω της callback προειδοποίησης.*

**Pro tip:** Χρησιμοποιήστε τη σημαία `recursive: true` αν οι γραμματοσειρές σας είναι διασκορπισμένες σε υπο‑φακέλους. Σας εξοικονομεί το χειροκίνητο προσθήκη κάθε διαδρομής.

---

## Load Word Document with Custom Font Settings

Με τις επιλογές έτοιμες, η φόρτωση του εγγράφου γίνεται παιχνιδάκι. Ο κατασκευαστής `Document` δέχεται τη διαδρομή του αρχείου και το `LoadOptions` που μόλις δημιουργήσαμε.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**What’s happening under the hood?**  
Το Aspose.Words αναλύει το DOCX, ελέγχει κάθε αναφορά `<w:font>`, και συμβουλεύεται τις `FontSettings` που παρείχατε. Αν δεν βρεθεί μια γραμματοσειρά, ενεργοποιεί μια προειδοποίηση τύπου `FontSubstitution`. Ο προσαρμοσμένος χειριστής μας (που φαίνεται παρακάτω) θα πιάσει αυτές τις προειδοποιήσεις.

---

## Handle Missing Fonts with Warning Callback

Η διεπαφή `IWarningCallback` σας επιτρέπει να αντιδράτε σε τυχόν προβλήματα που προκύπτουν κατά τη φόρτωση. Η υλοποίησή της είναι απλή:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Όταν το έγγραφο φορτωθεί, κάθε ελλιπής γραμματοσειρά θα προκαλέσει μια γραμμή όπως:

```
Font substituted: Arial -> Liberation Sans
```

**Why you should log this:**  
Σε παραγωγή μπορείτε να ανακατευθύνετε αυτά τα μηνύματα σε αρχείο ή σύστημα τηλεμετρίας, καθιστώντας εύκολο τον εντοπισμό των γραμματοσειρών που πρέπει να ενσωματώσετε ή να αδειοδοτήσετε.

---

## Full Working Example

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα κονσόλας που ενώνει όλα τα παραπάνω. Αντιγράψτε‑και‑επικολλήστε το σε ένα νέο .NET Core project κονσόλας και πατήστε **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Expected output** (υποθέτοντας ότι το `input.docx` χρησιμοποιεί γραμματοσειρά που δεν έχετε):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Αν όλες οι γραμματοσειρές είναι παρούσες, θα δείτε μόνο τη τελική γραμμή επιβεβαίωσης.

---

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if I need to embed the missing fonts into the PDF?** | After loading, call `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` and then enable embedding with `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Can I suppress the warnings instead of logging them?** | Yes—set `loadOptions.WarningCallback = null;` or implement the callback to ignore non‑font warnings. |
| **Does this work with `.doc` and `.rtf` files?** | Absolutely. The same `LoadOptions` object applies to any format supported by Aspose.Words. |
| **Is the callback thread‑safe?** | The callback runs on the same thread that loads the document, so you can safely write to the console. For multi‑threaded scenarios, use a concurrent collection or logging framework. |

---

## Pro Tips & Pitfalls

* **Pro tip:** Αν διανέμετε μια γραμματοσειρά που δεν είναι εγκατεστημένη στον προορισμό, προσθέστε την στον φάκελο που περνάτε στο `SetFontsFolder`. Αυτό εγγυάται καθοριστική απόδοση.
* **Watch out for licensing:** Ορισμένες γραμματοσειρές απαιτούν εμπορικές άδειες για ενσωμάτωση. Πάντα ελέγχετε το EULA της γραμματοσειράς πριν τη συμπεριλάβετε.
* **Performance note:** Η φόρτωση μεγάλων βιβλιοθηκών γραμματοσειρών μπορεί να επιβραδύνει την ανάλυση του εγγράφου. Κρατήστε το φάκελο ελαφρύ—συμπεριλάβετε μόνο τις γραμματοσειρές που χρειάζεστε πραγματικά.
* **Edge case:** Όταν ένα έγγραφο αναφέρει μια γραμματοσειρά με το *PostScript name* αντί για το όνομα οικογένειας, το Aspose.Words την επιλύει εφόσον το αρχείο γραμματοσειράς υπάρχει στη διαδρομή αναζήτησης.

---

## Conclusion

Τώρα έχετε ένα πλήρες, έτοιμο‑για‑παραγωγή μοτίβο για τη χρήση **custom font settings** σε C#. Με τη διαμόρφωση του `LoadOptions`, την καταχώρηση μιας callback προειδοποίησης, και προαιρετικά την ανάθεση σε ιδιωτικό φάκελο γραμματοσειρών, μπορείτε να **set font settings**, **load Word document** περιεχόμενο αξιόπιστα

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}