---
category: general
date: 2026-10-10
description: Μεταφράστε την παράγραφο στα γαλλικά και μάθετε πώς να αλλάξετε την ετικέτα
  δεδομένων του διαγράμματος, να προσαρμόσετε την ετικέτα δεδομένων του διαγράμματος
  και να αποθηκεύσετε το επεξεργασμένο αρχείο docx χρησιμοποιώντας το Aspose.Words
  AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: el
lastmod: 2026-10-10
og_description: Μεταφράστε την παράγραφο στα γαλλικά και μάθετε πώς να αλλάξετε την
  ετικέτα δεδομένων του διαγράμματος, να προσαρμόσετε την ετικέτα δεδομένων του διαγράμματος
  και να αποθηκεύσετε το επεξεργασμένο αρχείο docx χρησιμοποιώντας το Aspose.Words
  AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Μετάφραση παραγράφου στα γαλλικά και αλλαγή ετικέτας διαγράμματος στο Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Μετάφραση παραγράφου στα γαλλικά και αλλαγή ετικέτας διαγράμματος στο Word
url: /el/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετάφραση παραγράφου στα Γαλλικά και αλλαγή ετικέτας γραφήματος στο Word

Αν χρειάζεται να **μεταφράσετε μια παράγραφο στα Γαλλικά** ενώ ταυτόχρονα ενημερώνετε ένα γράφημα στο ίδιο έγγραφο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Χρησιμοποιώντας το Aspose.Words AI μπορείτε να μεταφράσετε κείμενο αυτόματα, να τροποποιήσετε την ετικέτα δεδομένων ενός γραφήματος και, τέλος, να αποθηκεύσετε το επεξεργασμένο αρχείο `.docx`—όλα σε λίγα απλά βήματα.

Το tutorial καλύπτει τα πάντα, από τη φόρτωση του αρχικού αρχείου μέχρι τη διατήρηση των αλλαγών. Στο τέλος θα μπορείτε να μεταφράζετε οποιαδήποτε παράγραφο, να προσαρμόζετε την ετικέτα δεδομένων ενός γραφήματος και να δημιουργείτε ένα νέο αρχείο Word έτοιμο για διανομή. Δεν απαιτούνται εξωτερικά scripts· όλη η ροή εργασίας βρίσκεται σε ένα μόνο πρόγραμμα C#.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Άδεια Aspose.Words for .NET (ή δωρεάν κλειδί αξιολόγησης)
- Πρόσβαση στο Internet για τον μεταφραστή Google AI (η κλάση `Translator` χρησιμοποιεί το API της Google)
- Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον μια παράγραφο και ένα γράφημα

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε μια νέα εφαρμογή console και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Τώρα συμπεριλάβετε τα απαιτούμενα namespaces στην αρχή του `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Αυτές οι εισαγωγές σας δίνουν πρόσβαση στη φόρτωση εγγράφων, τη μετάφραση AI και τη λειτουργικότητα επεξεργασίας γραφημάτων.

## Βήμα 2: Φόρτωση του πηγαίου εγγράφου Word

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Η φόρτωση του αρχείου δημιουργεί μια αναπαράσταση στη μνήμη που μπορείτε να ερωτήσετε και να τροποποιήσετε χωρίς να αγγίξετε το αρχικό αρχείο στο δίσκο.

## Βήμα 3: Μετάφραση της πρώτης παραγράφου στα Γαλλικά

Η πρώτη παράγραφος είναι συχνά ένας τίτλος ή μια εισαγωγική πρόταση, καθιστώντας την καλό υποψήφιο για μετάφραση. Η κλάση `Translator` αφαιρεί την κλήση στο μοντέλο AI της Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Γιατί λειτουργεί:**  
`paragraph.Runs.Clear()` αφαιρεί όλες τις υπάρχουσες ακολουθίες κειμένου, εξασφαλίζοντας ότι η νέα μετάφραση δεν θα συγχωνευτεί με το παλιό περιεχόμενο. `new Run(document, translatedText)` δημιουργεί μια νέα ακολουθία που κληρονομεί τη μορφοποίηση της παραγράφου.

## Βήμα 4: Εντοπισμός του πρώτου γραφήματος και προσαρμογή της ετικέτας δεδομένων

Τα γραφήματα αποθηκεύονται ως κόμβοι `Shape` τύπου `NodeType.Shape`. Το πρώτο γράφημα μπορεί να ληφθεί με `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Εξήγηση των βασικών βημάτων:**

- `GetChild(NodeType.Shape, 0, true)` εκτελεί αναζήτηση βάθους‑πρώτης και επιστρέφει το πρώτο σχήμα, που στην περίπτωσή μας είναι γράφημα.
- `ChartSeries` αντιπροσωπεύει μια συλλογή σημείων δεδομένων· η πρώτη σειρά (`Series[0]`) τυπικά αντιστοιχεί στο κύριο σύνολο δεδομένων.
- `ChartDataLabelPosition.OutsideEnd` μετακινεί την ετικέτα έξω από το άκρο της μπάρας, βελτιώνοντας την αναγνωσιμότητα.
- Ορίζοντας `dataLabel.Text` σε μια γαλλική συμβολοσειρά ευθυγραμμίζει την ετικέτα με τη μεταφρασμένη παράγραφο.

## Βήμα 5: Αποθήκευση του εγγράφου με τη μεταφρασμένη παράγραφο

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

Σε αυτό το σημείο το έγγραφο περιέχει τη γαλλική παράγραφο, αλλά διατηρεί ακόμα την αρχική διαμόρφωση του γραφήματος.

## Βήμα 6: Αποθήκευση του εγγράφου με το ενημερωμένο γράφημα

Μπορείτε να επαναχρησιμοποιήσετε την ίδια παρουσία `Document`—δεν χρειάζεται να το φορτώσετε ξανά—επειδή οι τροποποιήσεις του γραφήματος είναι ήδη στη μνήμη.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Και τα δύο αρχεία είναι τώρα έτοιμα για διανομή:

- **`translated.docx`** – περιέχει τη γαλλική παράγραφο.
- **`chart-updated.docx`** – περιέχει τη γαλλική παράγραφο *και* την προσαρμοσμένη ετικέτα γραφήματος.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο `Program.cs`. Συγκομποιείται και εκτελείται όπως είναι, εφόσον έχετε αντικαταστήσει το `YOUR_DIRECTORY` με πραγματική διαδρομή φακέλου.



## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να εξοικειωθείτε με πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Προσαρμογή ετικέτας δεδομένων γραφήματος](/words/english/net/programming-with-charts/chart-data-label/)
- [Μορφοποίηση αριθμού ετικέτας δεδομένων σε γράφημα](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Ετικέτα δεδομένων γραφήματος](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}