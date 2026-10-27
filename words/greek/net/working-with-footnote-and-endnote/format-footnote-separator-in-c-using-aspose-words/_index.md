---
category: general
date: 2026-08-10
description: Διαμορφώστε το διαχωριστικό υποσημειώσεων σε C# με το Aspose.Words για
  να προσαρμόσετε τις γραμμές υποσημειώσεων και σημειώσεων τέλους. Μάθετε τη μορφοποίηση
  υποσημειώσεων σε C# σε λίγα λεπτά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: el
lastmod: 2026-08-10
og_description: Διαμορφώστε το διαχωριστικό υποσημειώσεων σε C# με το Aspose.Words.
  Ακολουθήστε αυτό το σεμινάριο για να μορφοποιήσετε γρήγορα και αξιόπιστα τα διαχωριστικά
  υποσημειώσεων και σημειώσεων τέλους.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Διαμόρφωση διαχωριστικού υποσημειώσεων σε C# – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Διαμόρφωση διαχωριστικού υποσημειώσεων σε C# με τη χρήση του Aspose.Words
url: /el/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μορφοποίηση διαχωριστή υποσημειώσεων σε C# χρησιμοποιώντας το Aspose.Words

Αν χρειάζεστε **μορφοποίηση διαχωριστή υποσημειώσεων** σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με το Aspose.Words για .NET. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που αλλάζει την ευθυγράμμιση και το χρώμα της παραγράφου του διαχωριστή, και θα μάθετε πώς να εφαρμόζετε την ίδια τεχνική και στους διαχωριστές σημειώσεων τέλους.

Το tutorial καλύπτει κάθε βήμα—από τη φόρτωση του αρχικού αρχείου μέχρι την αποθήκευση του τροποποιημένου εγγράφου—ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε τον κώδικα στο δικό σας έργο χωρίς πρόσθετη έρευνα.

## Τι θα χρειαστείτε

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
* Ένα έγκυρο άδεια Aspose.Words για .NET (η δωρεάν δοκιμή λειτουργεί για αξιολόγηση)
* Ένα αρχείο Word που περιέχει τουλάχιστον μία υποσημείωση ή σημείωση τέλους (π.χ., `Footnotes.docx`)
* Visual Studio 2022 ή οποιοδήποτε IDE C# προτιμάτε

Έχοντας αυτά τα στοιχεία έτοιμα, μπορείτε να εστιάσετε στη λογική **μορφοποίησης υποσημειώσεων C#** αντί στη ρύθμιση του περιβάλλοντος.

## Βήμα 1: Φόρτωση του εγγράφου που περιέχει υποσημειώσεις και σημειώσεις τέλους

Η πρώτη ενέργεια είναι η δημιουργία ενός αντικειμένου `Document` που δείχνει στο αρχείο προέλευσης σας. Το Aspose.Words διαβάζει ολόκληρο το πακέτο DOCX στη μνήμη, παρέχοντάς σας πλήρη πρόσβαση στους κόμβους υποσημειώσεων και σημειώσεων τέλους.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου είναι προαπαιτούμενο για οποιαδήποτε επεξεργασία. Αν η διαδρομή του αρχείου είναι λανθασμένη, το Aspose.Words ρίχνει `FileNotFoundException`, επομένως ελέγξτε τη διαδρομή πριν προχωρήσετε.

## Βήμα 2: Ανάκτηση των κόμβων διαχωριστή και διαχωριστή συνέχειας

Οι διαχωριστές υποσημειώσεων και σημειώσεων τέλους αποθηκεύονται ως ειδικοί κόμβοι μέσα στις συλλογές `Footnotes` και `Endnotes`. Κάθε συλλογή εκθέτει τις ιδιότητες `Separator` και `ContinuationSeparator` που επιστρέφουν μια αναφορά `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Γιατί είναι σημαντικό*: Ο κόμβος `Separator` αντιπροσωπεύει τη γραμμή που οπτικά διαχωρίζει το κύριο κείμενο από το μπλοκ υποσημειώσεων. Με την απόκτηση μιας αναφοράς, μπορείτε να τροποποιήσετε τη μορφοποίηση παραγράφου, τη γραμματοσειρά ή ακόμη και να αντικαταστήσετε εντελώς τον κόμβο.

## Βήμα 3: Αλλαγή του οπτικού στυλ του διαχωριστή υποσημειώσεων

Στα περισσότερα έγγραφα Word, ο διαχωριστής είναι μια μοναδική παράγραφος που περιέχει μια παύλα ή ένα αστερίσκο. Ο παρακάτω κώδικας ελέγχει αν ο διαχωριστής είναι `Paragraph` και, αν ναι, τον κεντράρει και αλλάζει το χρώμα του κειμένου σε γκρι.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Στυλιζάρισμα του διαχωριστή συνέχειας (προαιρετικό)

Ο διαχωριστής συνέχειας εμφανίζεται όταν μια υποσημείωση εκτείνεται σε πολλές σελίδες. Μπορείτε να το στυλιζάρετε παρόμοια:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Γιατί είναι σημαντικό*: Η ευθυγράμμιση του διαχωριστή βελτιώνει την αναγνωσιμότητα, και η αλλαγή του χρώματος τον διακρίνει από το κανονικό κείμενο παραγράφου. Μπορείτε να αντικαταστήσετε το `ParagraphAlignment.Center` με `Left` ή `Right` για να ταιριάζει με τις οδηγίες σχεδίασης του εγγράφου σας.

## Βήμα 4: Αποθήκευση του τροποποιημένου εγγράφου

Αφού εφαρμόσετε το επιθυμητό στυλ, γράψτε το έγγραφο ξανά στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να δημιουργήσετε μια νέα έκδοση.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Όταν ανοίξετε το `Footnotes_Styled.docx` στο Microsoft Word, ο διαχωριστής υποσημειώσεων εμφανίζεται κεντραρισμένος και γκρι, ακριβώς όπως καθορίζεται από τον κώδικα.

## Προχωρημένες παραλλαγές

### Μορφοποίηση του διαχωριστή σημειώσεων τέλους

Αν το έγγραφό σας χρησιμοποιεί επίσης σημειώσεις τέλους, μπορείτε να εφαρμόσετε την ίδια λογική στη συλλογή `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Χρήση προσαρμοσμένης συμβολοσειράς για τον διαχωριστή

Μερικές φορές θέλετε ο διαχωριστής να είναι μια σειρά αστερίσκων (`***`). Αντικαταστήστε τα υπάρχοντα runs με ένα νέο run:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Διαχείριση εγγράφων χωρίς κόμβο διαχωριστή

Μια σπάνια περίπτωση είναι ένα έγγραφο που παραλείπει τον κόμβο διαχωριστή (π.χ., όταν ο συγγραφέας τον διέγραψε). Σε αυτήν την περίπτωση το `document.Footnotes.Separator` επιστρέφει `null`. Προφυλάξτε το:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Ο διαχωριστής δεν είναι `Paragraph`** | Κάποια πρότυπα Word χρησιμοποιούν `Table` ή `Shape` ως διαχωριστή. | Ελέγξτε τον τύπο του κόμβου με `is Paragraph` πριν κάνετε cast. |
| **Η συλλογή `Runs` είναι κενή** | Ο διαχωριστής μπορεί να είναι μια κενή παράγραφος. | Επαληθεύστε ότι `Runs.Count > 0` πριν προσπελάσετε το `Runs[0]`. |
| **Δεν έχει εφαρμοστεί άδεια** | Χωρίς άδεια, το Aspose.Words εισάγει υδατογράφημα και μπορεί να περιορίσει τη χρήση του API. | Καλέστε `License license = new License(); license.SetLicense("Aspose.Words.lic");` στην αρχή του προγράμματός σας. |
| **Αποθήκευση σε φάκελο μόνο για ανάγνωση** | Η μέθοδος `Save` ρίχνει `UnauthorizedAccessException`. | Βεβαιωθείτε ότι ο προορισμός έχει δικαιώματα εγγραφής. |

Η αντιμετώπιση αυτών των ζητημάτων νωρίς αποτρέπει εξαιρέσεις χρόνου εκτέλεσης και εξασφαλίζει μια ομαλή εμπειρία **τροποποίησης διαχωριστή υποσημειώσεων**.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει μια αυτόνομη εφαρμογή κονσόλας που δείχνει κάθε βήμα που συζητήθηκε παραπάνω. Αντιγράψτε τον κώδικα σε ένα νέο .NET έργο κονσόλας, αντικαταστήστε τις διαδρομές αρχείων και τρέξτε το.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα**  

Όταν ανοίξετε το `Footnotes_Styled.docx`:

* Η γραμμή διαχωριστή υποσημειώσεων είναι κεντραρισμένη κάτω από το κύριο κείμενο.
* Το χρώμα της εμφανίζεται ως ανοιχτό γκρι, κάνοντάς την οπτικά διακριτή.
* Αν το έγγραφο περιέχει σημειώσεις τέλους, οι διαχωριστές τους είναι επίσης κεντραρισμένες και χρωματισμένες γκρι (ή σκούρο γκρι

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Επεξεργασία Λέξεων με Υποσημειώσεις και Σημειώσεις Τέλους](/words/english/net/working-with-footnote-and-endnote/)
- [Ορισμός Θέσης Υποσημειώσεων Και Σημειώσεων Τέλους](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Εργασία Με Υποσημειώσεις Και Σημειώσεις Τέλους](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}