---
category: general
date: 2026-04-07
description: Αποθηκεύστε το docx ως txt γρήγορα και μάθετε πώς να εξάγετε μαθηματικά
  σε LaTeX. Μετατρέψτε το Word σε txt, διαχειριστείτε το Office Math και διατηρήστε
  τις εξισώσεις ανέπαφες.
draft: false
keywords:
- save docx as txt
- convert word to txt
- how to export math
- how to convert docx
- how to save txt
language: el
og_description: Αποθήκευση docx ως txt με εξαγωγή μαθηματικών LaTeX. Ένας βήμα‑βήμα
  οδηγός C# που δείχνει πώς να μετατρέψετε το Word σε txt και να διατηρήσετε τις εξισώσεις.
og_title: Αποθήκευση docx ως txt – Οδηγός C# για εξαγωγή μαθηματικών του Word
tags:
- C#
- Aspose.Words
- DocumentConversion
title: Αποθήκευση docx ως txt – Εξαγωγή μαθηματικών Word σε LaTeX σε C#
url: /el/net/programming-with-officemath/save-docx-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση docx ως txt – Εξαγωγή μαθηματικών Word σε LaTeX με C#

Έχετε ποτέ χρειαστεί να **αποθηκεύσετε docx ως txt** αλλά ανησυχείτε ότι οι εξισώσεις σας θα μετατραπούν σε μια χαοτική σειρά συμβόλων; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν προσπαθούν να **μετατρέψουν word σε txt** για επεξεργασία σε επόμενα στάδια, ειδικά όταν η πηγή περιέχει αντικείμενα Office Math.

Τα καλά νέα; Με λίγες γραμμές C# και τις σωστές επιλογές αποθήκευσης, μπορείτε να διατηρήσετε κάθε εξίσωση ως καθαρό LaTeX, κάνοντας το αρχείο απλού κειμένου τόσο αναγνώσιμο από άνθρωπο όσο και έτοιμο για επιστημονικές ροές εργασίας. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, θα απαντήσουμε στο *πώς να εξάγετε μαθηματικά* από ένα αρχείο Word, και θα σας δείξουμε *πώς να μετατρέψετε docx* χωρίς να χάσετε την ακρίβεια των μαθηματικών.

## Τι Θα Μάθετε

- Φορτώστε ένα αρχείο `.docx` χρησιμοποιώντας το Aspose.Words (ή οποιαδήποτε συμβατή βιβλιοθήκη).
- Διαμορφώστε το `TxtSaveOptions` ώστε το Office Math να εξάγεται ως LaTeX.
- Αποθηκεύστε το έγγραφο ως αρχείο `.txt` που διατηρεί τις εξισώσεις ανέπαφες.
- Συμβουλές για τη διαχείριση ειδικών περιπτώσεων όπως κρυφές εξισώσεις ή μεγάλα έγγραφα.
- Ένα πλήρες, εκτελέσιμο δείγμα κώδικα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε αμέσως.

Χωρίς περίπλοκα εργαλεία κατασκευής, μόνο ένα .NET project και το πακέτο NuGet Aspose.Words. Ας ξεκινήσουμε.

---

## Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| .NET 6.0 ή νεότερο | Σύγχρονα χαρακτηριστικά της γλώσσας και καλύτερη απόδοση. |
| Aspose.Words for .NET (NuGet) | Παρέχει `Document`, `TxtSaveOptions` και `OfficeMathExportMode`. |
| Ένα αρχείο Word (`.docx`) που περιέχει εξισώσεις | Για να δείτε την εξαγωγή LaTeX σε δράση. |
| Βασικές γνώσεις C# | Θα ακολουθήσετε τον κώδικα γραμμή‑με‑γραμμή. |

Αν δεν έχετε προσθέσει ακόμη το Aspose.Words, εκτελέστε:

```bash
dotnet add package Aspose.Words
```

Αυτό είναι—δεν χρειάζεται επιπλέον διαμόρφωση.

## Βήμα 1: Φόρτωση του Αρχείου DOCX

Πρώτα, πρέπει να φέρουμε το πηγαίο έγγραφο στη μνήμη. Σκεφτείτε το ως το άνοιγμα ενός βιβλίου πριν αρχίσετε να διαβάζετε.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Συμβουλή:** Χρησιμοποιήστε απόλυτη διαδρομή κατά τη δοκιμή για να αποφύγετε εκπλήξεις «αρχείο δεν βρέθηκε». Σε παραγωγή πιθανότατα θα λαμβάνετε τη διαδρομή από αρχείο ρυθμίσεων ή από μεταφόρτωση χρήστη.

## Βήμα 2: Διαμόρφωση των Επιλογών Αποθήκευσης TXT για Εξαγωγή Μαθηματικών

Από προεπιλογή, το `TxtSaveOptions` αποθηκεύει απλό κείμενο και αφαιρεί το Office Math. Δεν το θέλουμε αυτό. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX` λέει στη βιβλιοθήκη να μεταφράσει κάθε εξίσωση στην αναπαράστασή της σε LaTeX.

```csharp
// Step 2: Create TXT save options and configure Office Math export to LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

### Γιατί LaTeX;

Το LaTeX είναι η κοινή γλώσσα της επιστημονικής δημοσίευσης. Όταν αργότερα τροφοδοτήσετε το `.txt` σε έναν επεξεργαστή markdown, Jupyter notebook ή οποιοδήποτε εργαλείο που υποστηρίζει LaTeX, οι εξισώσεις αποδίδονται τέλεια. Αν προτιμάτε απλά σύμβολα Unicode, μπορείτε να αλλάξετε σε `OfficeMathExportMode.Unicode`, αλλά το LaTeX σας δίνει τον μεγαλύτερο έλεγχο.

## Βήμα 3: Αποθήκευση του Εγγράφου ως Αρχείο Απλού Κειμένου

Τώρα συμβαίνει η μαγεία. Η μέθοδος `Save` γράφει το έγγραφο στο δίσκο χρησιμοποιώντας τις επιλογές που ορίσαμε.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save("YOUR_DIRECTORY/Math.txt", txtSaveOptions);
```

Μετά την εκτέλεση αυτής της γραμμής, το `Math.txt` θα περιέχει:

```
This is a sample paragraph.

Here is an equation in LaTeX:
\[
E = mc^{2}
\]

Another paragraph follows.
```

Παρατηρήστε πώς η εξίσωση εμφανίζεται μέσα σε `\[` και `\]` — ακριβώς αυτό που περιμένει το LaTeX.

## Πώς να Εξάγετε Μαθηματικά από Πολύπλοκα Έγγραφα

### Διαχείριση Κρυφών ή Ενσωματωμένων Εξισώσεων

Κάποια αρχεία Word αποθηκεύουν εξισώσεις μέσα σε κρυφά πλαίσια κειμένου. Το Aspose.Words τις αντιμετωπίζει όπως τις ορατές εξισώσεις, έτσι η εξαγωγή LaTeX λειτουργεί αυτόματα. Ωστόσο, αν παρατηρήσετε ότι λείπουν εξισώσεις, ελέγξτε ξανά ότι το αντικείμενο `Document` δεν είναι ρυθμισμένο να αγνοεί το κρυφό περιεχόμενο:

```csharp
doc.RemoveHiddenParagraphs = false; // Ensure hidden text is processed
```

### Μεγάλα Έγγραφα και Χρήση Μνήμης

Η αποθήκευση μιας διατριβής 500 σελίδων μπορεί να καταναλώσει πολύ RAM. Για να κρατήσετε το αποτύπωμα μνήμης χαμηλό, μπορείτε να κάνετε ροή της εξόδου:

```csharp
using (FileStream stream = new FileStream("YOUR_DIRECTORY/Math.txt", FileMode.Create, FileAccess.Write))
{
    doc.Save(stream, txtSaveOptions);
}
```

Η ροή γράφει τμήματα στο δίσκο καθώς παράγονται, αποτρέποντας το ολόκληρο αρχείο να παραμείνει στη μνήμη ταυτόχρονα.

## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Συμπτωμα | Διόρθωση |
|---------|---------|-----|
| Έλλειψη αγκυλών LaTeX | Οι εξισώσεις εμφανίζονται ως ακατέργαστος κώδικας (`E = mc^{2}`) | Βεβαιωθείτε ότι `OfficeMathExportMode = LaTeX`. |
| Κενό αρχείο εξόδου | Λάθος διαδρομή ή ανεπαρκή δικαιώματα | Επαληθεύστε ότι ο φάκελος εξόδου υπάρχει και είναι εγγράψιμος. |
| Παραμορφωμένοι χαρακτήρες | Το αρχείο κωδικοποιείται σε UTF‑8 χωρίς BOM σε σύστημα που αναμένει ANSI | Προσθέστε `txtSaveOptions.Encoding = Encoding.UTF8;` |
| Εξισώσεις εξαφανίζονται μετά τη μετατροπή | Το έγγραφο φορτώθηκε με `LoadOptions` που εξαιρούν τα μαθηματικά | Χρησιμοποιήστε προεπιλεγμένα `LoadOptions` ή ορίστε `LoadOptions.LoadFormat = LoadFormat.Docx`. |

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε. Περιλαμβάνει διαχείριση σφαλμάτων, επικύρωση διαδρομής και ένα μικρό μήνυμα κονσόλας ώστε να γνωρίζετε ότι όλα ολοκληρώθηκαν επιτυχώς.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Paths – change these to match your environment
        string inputPath  = @"YOUR_DIRECTORY\input.docx";
        string outputPath = @"YOUR_DIRECTORY\Math.txt";

        // Validate input
        if (!File.Exists(inputPath))
        {
            Console.WriteLine($"❌ Input file not found: {inputPath}");
            return;
        }

        try
        {
            // Load the source document
            Document doc = new Document(inputPath);

            // Configure TXT save options – export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                Encoding = System.Text.Encoding.UTF8   // ensures proper character handling
            };

            // Optional: keep hidden content
            doc.RemoveHiddenParagraphs = false;

            // Save as plain‑text
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Success! File saved to {outputPath}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❗ An error occurred: {ex.Message}");
        }
    }
}
```

**Αναμενόμενη έξοδος** (απόσπασμα από το `Math.txt`):

```
Linear regression model:

\[
y = \beta_{0} + \beta_{1}x
\]

The residual sum of squares is:
\[
RSS = \sum_{i=1}^{n}(y_i - \hat{y}_i)^2
\]
```

Τώρα μπορείτε να τροφοδοτήσετε αυτό το αρχείο σε οποιοδήποτε εργαλείο που υποστηρίζει LaTeX, και οι εξισώσεις θα αποδοθούν όμορφα.

## Πώς να Μετατρέψετε DOCX σε TXT Χωρίς Να Χάσετε Μορφοποίηση

Αν χρειάζεστε μόνο απλό κείμενο και δεν σας ενδιαφέρουν τα μαθηματικά, απλώς παραλείψτε τη γραμμή `OfficeMathExportMode`:

```csharp
TxtSaveOptions txtOnly = new TxtSaveOptions(); // defaults to plain text
doc.Save("plain.txt", txtOnly);
```

Αλλά θυμηθείτε, **πώς να εξάγετε μαθηματικά** είναι το διακριτικό στοιχείο για τις επιστημονικές ροές εργασίας. Η διατήρηση του LaTeX ανέπαφου είναι αυτό που κάνει τη μετατροπή πραγματικά χρήσιμη.

## Επόμενα Βήματα & Σχετικά Θέματα

- **Μετατροπή κατά παρτίδες:** Τυλίξτε τον κώδικα σε βρόχο `foreach` για να επεξεργαστείτε ολόκληρο φάκελο αρχείων `.docx`.
- **Δημιουργία Markdown:** Προσθέστε κεφαλίδες `#` ή κουκκίδες `*` στο κείμενο για να παραγάγετε έτοιμο προς δημοσίευση markdown.
- **Εξαγωγή PDF:** Χρησιμοποιήστε `PdfSaveOptions` για να δημιουργήσετε μια έκδοση PDF παράλληλα με το txt.
- **Προχωρημένη ρύθμιση LaTeX:** Μετά-επεξεργασία της εξόδου με regex για να αντικαταστήσετε `\[`/`\]` με `$...$` για ενσωματωμένες εξισώσεις.

Κάθε ένα από αυτά βασίζεται στην ίδια θεμελίωση — τη φόρτωση ενός `Document` και την επιλογή των κατάλληλων `SaveOptions`. Μη διστάσετε να πειραματιστείτε· το API είναι αρκετά ευέλικτο για τις περισσότερες περιπτώσεις αυτοματοποίησης εγγράφων.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **αποθηκεύσετε docx ως txt** διατηρώντας κάθε εξίσωση ως LaTeX. Από τη φόρτωση του πηγαίου αρχείου, τη διαμόρφωση του `TxtSaveOptions` για **πώς να εξάγετε μαθηματικά**, μέχρι τη δημιουργία του τελικού αρχείου απλού κειμένου, όλη η ροή εργασίας χωράει σε λίγες σύντομες δηλώσεις C#.

Τώρα μπορείτε να αυτοματοποιήσετε τη μετατροπή αναφορών Word, ακαδημαϊκών εργασιών ή οποιουδήποτε εγγράφου που συνδυάζει κείμενο και μαθηματικά, και να τροφοδοτήσετε το προκύπτον `.txt` σε επόμενα εργαλεία χωρίς να χάσετε καμία επιστημονική λεπτομέρεια.

Δοκιμάστε το, προσαρμόστε τις επιλογές για τη δική σας περίπτωση χρήσης, και ενημερώστε μας στα σχόλια πώς σας φάνηκε. Καλή προγραμματιστική!

![Diagram showing the conversion pipeline from DOCX → C# processing → TXT with LaTeX math](https://example.com/images/save-docx-as-txt.png "save docx as txt pipeline")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}