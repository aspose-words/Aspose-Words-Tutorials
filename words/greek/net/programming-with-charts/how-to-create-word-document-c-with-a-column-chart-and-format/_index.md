---
category: general
date: 2026-09-21
description: Μάθετε πώς να δημιουργήσετε έγγραφο Word με C# και να εισάγετε ένα ραβδόγραμμα,
  να ορίσετε τη θέση των ετικετών και να εμφανίσετε τις τιμές χρησιμοποιώντας το Aspose.Words
  σε έναν οδηγό βήμα‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: el
lastmod: 2026-09-21
og_description: Δημιουργία εγγράφου Word C# με το Aspose.Words. Αυτό το σεμινάριο
  δείχνει πώς να εισάγετε ένα γράφημα στήλης, να ορίσετε τη θέση της ετικέτας και
  να εμφανίσετε τις τιμές.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Δημιουργία εγγράφου Word C# – εισαγωγή διαγράμματος στήλης, ορισμός ετικέτας,
  εμφάνιση τιμών
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Πώς να δημιουργήσετε έγγραφο Word σε C# με γράφημα στήλης και μορφοποιημένες
  ετικέτες
url: /el/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο Word C# με ένα γράφημα στήλης και μορφοποιημένες ετικέτες

Αν χρειάζεστε **create Word document C#** που περιλαμβάνει ένα γράφημα, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα μάθετε πώς να εισάγετε ένα **column chart**, να τοποθετήσετε την ετικέτα δεδομένων του και να εμφανίσετε τις τιμές της ετικέτας—όλα με το Aspose.Words for .NET.

Η δημιουργία ενός αρχείου Word με ενσωματωμένο γράφημα απαιτούσε παλαιότερα χειροκίνητη εργασία στο Microsoft Word. Με τα βήματα **how to insert chart** που περιγράφονται εδώ, μπορείτε να αυτοματοποιήσετε όλη τη διαδικασία από τον κώδικα, κάνοντας τη δημιουργία αναφορών γρήγορη και επαναλήψιμη. Το tutorial καλύπτει επίσης τις ιδιότητες **how to set label** και **how to display values** ώστε το γράφημα να είναι έτοιμο για τους τελικούς χρήστες.

Στο τέλος αυτού του άρθρου θα έχετε ένα πλήρες, εκτελέσιμο πρόγραμμα C# που δημιουργεί ένα αρχείο `.docx` που περιέχει ένα γράφημα στήλης με ετικέτες δεδομένων που εμφανίζονται μέσα σε κάθε στήλη και δείχνουν τις αριθμητικές τους τιμές.

## Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Αδειοδοτημένη έκδοση του **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για δοκιμές)  
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code  

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από το `Aspose.Words`.

## Βήμα 1: Ρύθμιση του έργου και προσθήκη του Aspose.Words

Δημιουργήστε ένα νέο έργο κονσόλας και προσθέστε το πακέτο Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Η εντολή `dotnet add package` κατεβάζει την πιο πρόσφατη σταθερή έκδοση του **Aspose.Words**, η οποία περιλαμβάνει το API γραφήματος που χρησιμοποιείται στο παράδειγμα **insert column chart word**.

## Βήμα 2: Δημιουργία νέου κενού εγγράφου Word

Το πρώτο κομμάτι κώδικα δημιουργεί ένα κενό έγγραφο και ένα `DocumentBuilder` που σας επιτρέπει να εισάγετε περιεχόμενο. Αυτό αποτελεί τη βάση για **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` αντιπροσωπεύει ολόκληρο το αρχείο `.docx`, ενώ το `DocumentBuilder` παρέχει μεθόδους όπως `InsertParagraph`, `InsertImage` και, κρίσιμα για αυτό το tutorial, `InsertChart`.

## Βήμα 3: Εισαγωγή γραφήματος στήλης (how to insert chart)

Τώρα εισάγουμε ένα **column chart**. Η μέθοδος `InsertChart` δέχεται τον τύπο γραφήματος, το πλάτος και το ύψος σε points.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

Σε αυτό το σημείο το γράφημα περιέχει μια προεπιλεγμένη σειρά δεδομένων με τιμές placeholder. Μπορείτε να αντικαταστήσετε τα δεδομένα της σειράς αν χρειάζεστε προσαρμοσμένους αριθμούς, αλλά για την επίδειξη του **how to set label** και του **how to display values**, τα προεπιλεγμένα δεδομένα είναι επαρκή.

## Βήμα 4: Τοποθέτηση της ετικέτας δεδομένων μέσα σε κάθε στήλη (how to set label)

Οι ετικέτες δεδομένων είναι το κείμενο που εμφανίζεται σε κάθε στήλη. Για να γίνει το γράφημα πιο ευανάγνωστο, μετακινούμε την ετικέτα μέσα στη στήλη και ενεργοποιούμε την αριθμητική της τιμή.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` τοποθετεί την ετικέτα στην κορυφή της στήλης αλλά ακόμη μέσα στο σχήμα της στήλης, κάτι που είναι κοινό στυλ παρουσίασης για αναφορές. Ορίζοντας το `ShowValue` σε `true` ικανοποιεί την απαίτηση **how to display values**.

## Βήμα 5: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Το αρχείο μπορεί να ανοιχθεί με το Microsoft Word, το LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει τη μορφή Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `output.docx` που περιέχει ένα γράφημα στήλης με ετικέτες δεδομένων τοποθετημένες μέσα σε κάθε στήλη και που εμφανίζουν τις τιμές τους.

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `output.docx`, θα πρέπει να δείτε ένα μόνο γράφημα στήλης παρόμοιο με την εικόνα παρακάτω. Κάθε στήλη έχει μια αριθμητική ετικέτα στην κορυφή της, μέσα στη στήλη, που εμφανίζει την τιμή της σειράς.

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *Γράφημα σε έγγραφο Word που δημιουργήθηκε με C# και δείχνει πώς να εισάγετε column chart word και να εμφανίσετε τιμές.*

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

### Προσθήκη προσαρμοσμένων δεδομένων στο γράφημα

Αν χρειάζεται να αντικαταστήσετε τα δεδομένα placeholder, μπορείτε να τροποποιήσετε τη συλλογή `Series` του γραφήματος:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Αλλαγή γραμματοσειράς και χρώματος ετικέτας

Μπορείτε να προσαρμόσετε περαιτέρω την εμφάνιση της ετικέτας:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Εισαγωγή πολλαπλών γραφημάτων

Το `DocumentBuilder` μπορεί να εισάγει όσες γραφήματα χρειάζεστε. Απλώς καλέστε ξανά το `InsertChart` μετά τη μετακίνηση του δρομέα με `builder.Writeln()` ή `builder.InsertParagraph()`.

## Συμβουλές επαγγελματιών

* **Pro tip:** Ορίστε `chart.HasTitle = true` και αναθέστε `chart.Title.Text` για να δώσετε στο γράφημα έναν περιγραφικό τίτλο. Αυτό βελτιώνει την προσβασιμότητα για προγράμματα ανάγνωσης οθόνης.
* **Watch out for:** Κατά την αποθήκευση σε κοινόχρηστο δίκτυο, βεβαιωθείτε ότι η εφαρμογή έχει δικαιώματα εγγραφής· διαφορετικά το `doc.Save` θα ρίξει `UnauthorizedAccessException`.
* **Performance tip:** Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` για πολλαπλές εισαγωγές· η δημιουργία νέου builder για κάθε λειτουργία προσθέτει περιττό φόρτο.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create Word document C#** που περιέχει ένα γράφημα στήλης, πώς να **insert chart** στοιχεία, **set label** θέσεις και **display values** μέσα σε κάθε στήλη. Το πλήρες παράδειγμα κώδικα παραπάνω είναι έτοιμο προς εκτέλεση και μπορείτε να το επεκτείνετε με προσαρμοσμένα δεδομένα, στυλ ή επιπλέον γραφήματα.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **how to insert picture**, **how to generate tables**, ή **how to apply document themes** για να κάνετε τις αυτοματοποιημένες αναφορές σας ακόμη πιο πλούσιες. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή γραφήματος στήλης στο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Εισαγωγή απλού γραφήματος στήλης στο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Εισαγωγή γραφήματος περιοχής σε έγγραφο Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}