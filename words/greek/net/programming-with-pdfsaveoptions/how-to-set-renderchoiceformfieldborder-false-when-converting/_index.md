---
category: general
date: 2026-09-21
description: Μάθετε πώς να ορίσετε το RenderChoiceFormFieldBorder σε false στο Aspose.Words
  για να εξάγετε πεδία φόρμας Word χωρίς περιγράμματα. Περιλαμβάνει πλήρες κώδικα
  και συμβουλές.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set renderchoiceformfieldborder false
- Aspose.Words PDF conversion
- disable choice field border
- PdfSaveOptions configuration
- Word form fields
- convert Word to PDF
language: el
lastmod: 2026-09-21
og_description: Ορίστε το RenderChoiceFormFieldBorder σε false για να αφαιρέσετε τα
  σύνορα από τα πεδία επιλογής φόρμας κατά τη μετατροπή του Word σε PDF με το Aspose.Words.
og_image_alt: PDF preview showing choice form fields without borders after setting
  RenderChoiceFormFieldBorder false
og_title: Ορίστε το RenderChoiceFormFieldBorder σε false για καθαρή εξαγωγή PDF
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  headline: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  type: TechArticle
- description: Learn how to set RenderChoiceFormFieldBorder false in Aspose.Words
    to export Word form fields without borders. Includes full code and tips.
  name: How to set RenderChoiceFormFieldBorder false when converting Word to PDF
  steps:
  - name: Additional PdfSaveOptions you may want to set
    text: '| Option | Typical value | When to use it | |----------------------------|---------------|----------------|
      | `Compliance` | `PdfCompliance.PdfA1b` | For archival PDFs | | `EmbedStandardFonts`
      | `true` | To avoid font substitution on other machines | | `SaveFormat` | `SaveFormat.Pdf`
      | Explicitly st'
  - name: Verifying the result
    text: Open `NoBorderChoice.pdf` in any PDF viewer (Adobe Acrobat, Foxit Reader,
      or the browser). You should see the drop‑down or combo‑box fields rendered as
      plain text placeholders—no gray rectangle is visible. The fields remain interactive;
      clicking on them still displays the list of choices.
  - name: Sample code for checking form fields
    text: '```csharp int choiceFieldCount = 0; foreach (FormField field in doc.Range.FormFields)
      { if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
      choiceFieldCount++; } Console.WriteLine($"Document contains {choiceFieldCount}
      choice form fields."); ```'
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- C#
- Form fields
title: Πώς να ορίσετε το RenderChoiceFormFieldBorder σε false κατά τη μετατροπή του
  Word σε PDF
url: /el/net/programming-with-pdfsaveoptions/how-to-set-renderchoiceformfieldborder-false-when-converting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε το RenderChoiceFormFieldBorder σε false κατά τη μετατροπή Word σε PDF

Αν χρειάζεται να **ορίσετε το RenderChoiceFormFieldBorder σε false** κατά την εξαγωγή ενός εγγράφου Word που περιέχει πεδία επιλογής φόρμας, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Απενεργοποιώντας την απόδοση του περιγράμματος, το παραγόμενο PDF φαίνεται πιο καθαρό και ταιριάζει με τη διάταξη του αρχικού εγγράφου.

Σε αυτό το σεμινάριο θα μάθετε πώς να διαμορφώσετε το **PdfSaveOptions** στο Aspose.Words, γιατί είναι σημαντική αυτή η ρύθμιση και πώς να αντιμετωπίσετε κοινές ακραίες περιπτώσεις, όπως έγγραφα χωρίς πεδία φόρμας. Η λύση λειτουργεί με την πιο πρόσφατη έκδοση του Aspose.Words for .NET (v23.10 τη στιγμή της συγγραφής) και απαιτεί μόνο λίγες γραμμές κώδικα C#.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη.
* Έγκυρη άδεια Aspose.Words for .NET (ή κλειδί δωρεάν αξιολόγησης).
* Έγγραφο Word (`.docx`) που περιέχει πεδία επιλογής φόρμας (π.χ., λίστες πτυσσόμενων ή κουτιά συνδυασμού).
* Visual Studio 2022 (ή οποιοδήποτε IDE C#).

## Βήμα 1: Φόρτωση του πηγαίου εγγράφου Word

Το πρώτο βήμα είναι να δημιουργήσετε ένα αντικείμενο `Document` που αντιπροσωπεύει το πηγαίο αρχείο σας. Το Aspose.Words διαβάζει το αρχείο στη μνήμη, επιτρέποντάς σας να ελέγξετε ή να τροποποιήσετε το περιεχόμενό του πριν από τη μετατροπή.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word document that contains choice form fields
Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");
```

**Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου σας δίνει πρόσβαση στη συλλογή πεδίων φόρμας, την οποία μπορείτε αργότερα να ελέγξετε για να επιβεβαιώσετε ότι το αρχείο περιέχει πραγματικά πεδία επιλογής. Εάν το έγγραφο δεν έχει τέτοια πεδία, η ρύθμιση `RenderChoiceFormFieldBorder` δεν έχει οπτικό αποτέλεσμα, αλλά ο κώδικας εκτελείται με ασφάλεια.

## Βήμα 2: Διαμόρφωση του PdfSaveOptions και ορισμός του RenderChoiceFormFieldBorder σε false

`PdfSaveOptions` ελέγχει κάθε πτυχή της εξόδου PDF, από την ποιότητα εικόνας μέχρι την απόδοση των πεδίων φόρμας. Ορίζοντας το `RenderChoiceFormFieldBorder` σε `false` λέτε στον renderer να παραλείψει το γκρι ορθογώνιο που συνήθως περιβάλλει τα πεδία πτυσσόμενων λιστών και κουτιών συνδυασμού.

```csharp
// Create PDF save options and disable the rendering of choice field borders
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false
};
```

**Γιατί είναι σημαντικό:** Από προεπιλογή, το Aspose.Words σχεδιάζει ένα λεπτό περίγραμμα γύρω από τα πεδία επιλογής φόρμας ώστε οι χρήστες να βλέπουν πού να αλληλεπιδράσουν. Σε πολλές περιπτώσεις δημοσίευσης—όπως εκτυπώσιμες φόρμες ή επαγγελματικές αναφορές—το περίγραμμα είναι ανεπιθύμητο. Η σημαία `RenderChoiceFormFieldBorder` παρέχει έναν απλό τρόπο για να το απενεργοποιήσετε.

### Πρόσθετες ρυθμίσεις PdfSaveOptions που μπορεί να θέλετε να ορίσετε

| Επιλογή | Τυπική τιμή | Πότε να τη χρησιμοποιήσετε |
|---|---|---|
| `Compliance` | `PdfCompliance.PdfA1b` | Για αρχειοθετημένα PDFs |
| `EmbedStandardFonts` | `true` | Για αποφυγή αντικατάστασης γραμματοσειρών σε άλλα μηχανήματα |
| `SaveFormat` | `SaveFormat.Pdf` | Δηλώνει ρητά τη μορφή προορισμού (προαιρετικό) |

Μπορείτε να συνδυάσετε αυτές τις ρυθμίσεις με τη σημαία του περιγράμματος:

```csharp
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    RenderChoiceFormFieldBorder = false,
    Compliance = PdfCompliance.PdfA1b,
    EmbedStandardFonts = true
};
```

## Βήμα 3: Αποθήκευση του εγγράφου ως PDF χρησιμοποιώντας τις διαμορφωμένες επιλογές

Τώρα που οι επιλογές έχουν οριστεί, καλέστε το `Document.Save` με τη διαδρομή προορισμού και το αντικείμενο `PdfSaveOptions`.

```csharp
// Save the document as a PDF using the configured options
doc.Save("YOUR_DIRECTORY/NoBorderChoice.pdf", pdfOptions);
```

**Γιατί είναι σημαντικό:** Η μέθοδος `Save` εκτελεί την πραγματική μετατροπή. Επειδή το `pdfOptions` περιέχει `RenderChoiceFormFieldBorder = false`, το παραγόμενο PDF θα περιέχει τα πεδία επιλογής **χωρίς** το περιβάλλον περίγραμμα.

### Επαλήθευση του αποτελέσματος

Ανοίξτε το `NoBorderChoice.pdf` σε οποιονδήποτε προβολέα PDF (Adobe Acrobat, Foxit Reader ή το πρόγραμμα περιήγησης). Θα πρέπει να δείτε τα πεδία πτυσσόμενης λίστας ή κουτιού συνδυασμού να εμφανίζονται ως απλοί δείκτες κειμένου—δεν είναι ορατό το γκρι ορθογώνιο. Τα πεδία παραμένουν διαδραστικά· κάνοντας κλικ σε αυτά εμφανίζεται η λίστα επιλογών.

## Διαχείριση ακραίων περιπτώσεων

| Κατάσταση | Συνιστώμενη προσέγγιση |
|---|---|
| **Το έγγραφο δεν έχει πεδία επιλογής φόρμας** | Η σημαία του περιγράμματος δεν έχει αποτέλεσμα. Μπορείτε προαιρετικά να ελέγξετε το `doc.Range.FormFields.Count` πριν από τη μετατροπή για να παραλείψετε περιττές ρυθμίσεις. |
| **Αρχείο Word με προστασία κωδικού** | Φορτώστε το έγγραφο με ένα αντικείμενο `LoadOptions` που περιλαμβάνει τον κωδικό, και στη συνέχεια εφαρμόστε το ίδιο `PdfSaveOptions`. |
| **Μεγάλα έγγραφα (> 100 MB)** | Χρησιμοποιήστε τις επιλογές `MemoryOptimization` στο `PdfSaveOptions` για να μειώσετε την κατανάλωση μνήμης κατά τη μετατροπή. |
| **Απαιτείται διατήρηση του περιγράμματος για συγκεκριμένα πεδία** | Μετά τη φόρτωση του εγγράφου, επαναλάβετε πάνω από τα `doc.Range.FormFields`, ορίστε το `FieldType` σε `FieldType.FieldFormDropDown` ή `FieldFormComboBox`, και προσαρμόστε την ιδιότητα `Border` χειροκίνητα πριν από την αποθήκευση. |

### Παράδειγμα κώδικα για έλεγχο πεδίων φόρμας

```csharp
int choiceFieldCount = 0;
foreach (FormField field in doc.Range.FormFields)
{
    if (field.Type == FieldType.FieldFormDropDown || field.Type == FieldType.FieldFormComboBox)
        choiceFieldCount++;
}
Console.WriteLine($"Document contains {choiceFieldCount} choice form fields.");
```

Αν το `choiceFieldCount` είναι μηδέν, μπορείτε να παραλείψετε εντελώς τη ρύθμιση του περιγράμματος, κάτι που εξοικονομεί ελάχιστο χρόνο επεξεργασίας.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα που συνδυάζει όλα τα παραπάνω. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή στο σύστημά σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/FormWithChoices.docx");

        // Optional: verify that the document contains choice fields
        int choiceCount = 0;
        foreach (FormField field in doc.Range.FormFields)
        {
            if (field.Type == FieldType.FieldFormDropDown ||
                field.Type == FieldType.FieldFormComboBox)
                choiceCount++;
        }
        Console.WriteLine($"Found {choiceCount} choice form fields.");

        // 2️⃣ Configure PdfSaveOptions and set RenderChoiceFormFieldBorder false
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            RenderChoiceFormFieldBorder = false,
            // Example of additional options you might need
            Compliance = PdfCompliance.PdfA1b,
            EmbedStandardFonts = true
        };

        // 3️⃣ Save the PDF
        string outputPath = "YOUR_DIRECTORY/NoBorderChoice.pdf";
        doc.Save(outputPath, pdfOptions);
        Console.WriteLine($"PDF saved to {outputPath} with borders disabled.");
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα**

```
Found 3 choice form fields.
PDF saved to C:\MyProjects\NoBorderChoice.pdf with borders disabled.
```

Όταν ανοίξετε το `NoBorderChoice.pdf`, τα πεδία πτυσσόμενης λίστας εμφανίζονται χωρίς το προεπιλεγμένο γκρι περίγραμμα, δίνοντας στο έγγραφο πιο καθαρή εμφάνιση ενώ διατηρείται η διαδραστικότητα.

## Συμβουλές επαγγελματιών και κοινές παγίδες

* **Συμβουλή επαγγελματία:** Εάν δημιουργείτε PDFs σε μια υπηρεσία web, ορίστε ρητά το `pdfOptions.SaveFormat = SaveFormat.Pdf` για να αποφύγετε τυχαία προβλήματα ανίχνευσης μορφής.
* **Προσοχή:** Οι παλαιότερες εκδόσεις του Aspose.Words (πριν την v20) δεν εκθέτουν το `RenderChoiceFormFieldBorder`. Αναβαθμίστε στην πιο πρόσφατη έκδοση για να χρησιμοποιήσετε αυτή τη σημαία.
* **Συμβουλή απόδοσης:** Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `PdfSaveOptions` όταν μετατρέπετε πολλά έγγραφα σε παρτίδα· η δημιουργία νέου αντικειμένου κάθε φορά προσθέτει περιττό φόρτο.
* **Συμβουλή δοκιμών:** Συμπεριλάβετε μια μονάδα ελέγχου που φορτώνει ένα γνωστό `.docx` με πτυσσόμενη λίστα, εκτελεί τη μετατροπή και ελέγχει ότι το παραγόμενο ρεύμα PDF δεν περιέχει την σημείωση `/Border` για αυτά τα πεδία.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να ορίσετε το RenderChoiceFormFieldBorder σε false** για τη δημιουργία PDFs χωρίς περιγράμματα πεδίων επιλογής χρησιμοποιώντας το Aspose.Words. Η λύση καλύπτει τη φόρτωση του εγγράφου, τη διαμόρφωση του `PdfSaveOptions`, την αποθήκευση του PDF και τη διαχείριση ακραίων περιπτώσεων όπως η έλλειψη πεδίων φόρμας ή πηγές προστατευμένες με κωδικό.  

Στη συνέχεια, μπορείτε να εξερευνήσετε συναφή θέματα όπως **απενεργοποίηση περιγράμματος πεδίου επιλογής** για άλλους τύπους πεδίων φόρμας, ή να μάθετε πώς να **μετατρέψετε Word σε PDF** με προσαρμοσμένη ανάλυση εικόνας χρησιμοποιώντας το `ImageSaveOptions`. Και τα δύο θέματα ενισχύουν την εξειδίκευσή σας στην **μετατροπή PDF με Aspose.Words** και σας δίνουν πλήρη έλεγχο της τελικής εμφάνισης του εγγράφου.

Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετικότατα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε περαιτέρω λειτουργίες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [μετατροπή word σε pdf σε C# χρησιμοποιώντας Aspose.Words – Οδηγός](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [Αποθήκευση Word ως PDF με Aspose Words – Πλήρης οδηγός C#](/words/hindi/net/programming-with-pdfsaveoptions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Μετατροπή Word σε PDF με Aspose.Words για Java](/words/english/java/document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}