---
category: general
date: 2026-08-10
description: Δημιουργήστε έγγραφο Word με διάγραμμα πίτας χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να εισάγετε διάγραμμα, να προσαρμόσετε τα χρώματα του διαγράμματος πίτας
  και να αλλάξετε το χρώμα του τμήματος της πίτας σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: el
lastmod: 2026-08-10
og_description: Δημιουργήστε έγγραφο Word με διάγραμμα πίτας χρησιμοποιώντας το Aspose.Words.
  Αυτός ο οδηγός εξηγεί πώς να εισάγετε διάγραμμα, να προσαρμόσετε τα χρώματα του
  διαγράμματος πίτας και να αλλάξετε το χρώμα του τμήματος της πίτας σε μια εφαρμογή
  C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Δημιουργία εγγράφου Word με διάγραμμα πίτας – Οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Δημιουργία εγγράφου Word με διάγραμμα πίτας με το Aspose.Words
url: /el/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word με γράφημα πίτας χρησιμοποιώντας Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε έγγραφο Word με γράφημα πίτας** προγραμματιστικά, αυτό το tutorial σας δείχνει ακριβώς πώς. Θα περάσουμε από την εισαγωγή ενός γραφήματος, **την προσαρμογή χρωμάτων γραφήματος πίτας**, και **την αλλαγή χρώματος φέτας πίτας** χρησιμοποιώντας το Aspose.Words for .NET.

Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να αντιγράψετε στο Visual Studio, να τρέξετε και να ανοίξετε αμέσως το παραγόμενο *.docx* για να επαληθεύσετε το στυλιζαρισμένο γράφημα πίτας. Δεν απαιτείται εξωτερική τεκμηρίωση—όλα όσα χρειάζεστε είναι σε αυτόν τον οδηγό.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Ένα έγκυρο license του Aspose.Words for .NET (ή ένα προσωρινό κλειδί αξιολόγησης)  
* Visual Studio 2022 (ή οποιοδήποτε IDE για C#)  

Ο κώδικας χρησιμοποιεί μόνο τα namespaces `Aspose.Words` και `Aspose.Words.Drawing.Charts`, οπότε δεν απαιτούνται πρόσθετα πακέτα NuGet εκτός από τη βιβλιοθήκη Aspose.Words.

## Δημιουργία εγγράφου Word με γράφημα πίτας – πλήρες παράδειγμα

Το παρακάτω πρόγραμμα C# δημιουργεί ένα νέο έγγραφο Word, εισάγει ένα γράφημα πίτας, στυλιζάρει τις δύο πρώτες φέτες και αποθηκεύει το αρχείο. Κάθε βήμα εξηγείται λεπτομερώς.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Εξήγηση κάθε βήματος

| Βήμα | Τι κάνει | Γιατί είναι σημαντικό |
|------|----------|------------------------|
| **1** | Δημιουργεί ένα νέο `Document` και ένα `DocumentBuilder`. | Το `DocumentBuilder` παρέχει μεθόδους fluent για την εισαγωγή περιεχομένου, όπως γραφήματα, στο αρχείο Word. |
| **2** | Καλεί `InsertChart` με `ChartType.Pie` και σταθερό μέγεθος. | Η `InsertChart` είναι η **μέθοδος εισαγωγής γραφήματος**· ο καθορισμός πλάτους/ύψους εξασφαλίζει ότι το γράφημα ταιριάζει ωραία στη σελίδα. |
| **3** | Προσθέτει μια σειρά δεδομένων με τρεις κατηγορίες και αριθμητικές τιμές. | Ένα γράφημα πίτας χωρίς δεδομένα είναι αόρατο· η πληρότητά του δείχνει τα βήματα στυλιζάρισματος. |
| **4** | Ορίζει `Explosion` στο πρώτο σημείο. | Η «έκρηξη» μιας φέτας τραβάει την προσοχή σε ένα συγκεκριμένο τμήμα—χρήσιμο για την ανάδειξη βασικών δεδομένων. |
| **5** | Ορίζει `ForeColor` για τα δύο πρώτα σημεία. | Αυτό είναι ο πυρήνας της **προσαρμογής χρωμάτων γραφήματος πίτας**· μπορείτε να χρησιμοποιήσετε οποιοδήποτε `System.Drawing.Color`. |
| **6** | Δείχνει πώς να **αλλάξετε το χρώμα φέτας πίτας** για επιπλέον φέτες. | Αποδεικνύει ότι το στυλ δεν περιορίζεται μόνο στις δύο πρώτες φέτες· μπορείτε να χρωματίσετε κάθε φέτα ξεχωριστά. |
| **7** | Αποθηκεύει το έγγραφο ως `PieChartStyled.docx`. | Το τελικό αποτέλεσμα μπορεί να ανοιχθεί στο Microsoft Word, Google Docs ή οποιονδήποτε συμβατό προβολέα. |

#### Αναμενόμενο αποτέλεσμα

Ανοίγοντας το `PieChartStyled.docx` εμφανίζεται μια μοναδική σελίδα με γράφημα πίτας 400 × 300 pt:

* Η φέτα 1 (πορτοκαλί) είναι εκτοξευμένη προς τα έξω.  
* Η φέτα 2 (πράσινη) εμφανίζεται δίπλα στην εκτοξευμένη φέτα.  
* Η φέτα 3 (steel‑blue) γεμίζει το υπόλοιπο τμήμα.

Το γράφημα αντανακλά τις τιμές δεδομένων (30, 45, 25) και τα προσαρμοσμένα χρώματα που ορίσατε.

## Πώς να στυλιζάρετε την πίτα – πρόσθετες συμβουλές

* **Χρησιμοποιήστε χρώματα θέματος** – αντί για σκληρή κωδικοποίηση `Color.Orange`, μπορείτε να αντλήσετε χρώματα από το θέμα του εγγράφου:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Προσθέστε ετικέτες δεδομένων** – αν θέλετε να εμφανίζονται ποσοστά στο γράφημα:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Αλλάξτε το μέγεθος δυναμικά** – υπολογίστε το μέγεθος του γραφήματος βάσει των περιθωρίων της σελίδας:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Αυτές οι παραλλαγές δείχνουν την ευελιξία του **πώς να στυλιζάρετε την πίτα** πέρα από το βασικό παράδειγμα.

## Συχνές ερωτήσεις

**Ε: Λειτουργεί αυτό με .NET Core;**  
Α: Ναι. Το Aspose.Words for .NET είναι συμβατό με .NET Core, .NET 5, .NET 6 και μεταγενέστερες εκδόσεις. Απλώς αναφέρετε το ίδιο πακέτο NuGet.

**Ε: Τι γίνεται αν χρειάζομαι γράφημα δακτυλίου αντί για πίτα;**  
Α: Αντικαταστήστε το `ChartType.Pie` με `ChartType.Doughnut`. Τα ίδια API στυλ (`Explosion`, `ForeColor`) ισχύουν.

**Ε: Μπορώ να εισάγω το γράφημα σε υπάρχον έγγραφο;**  
Α: Ανοίξτε το υπάρχον αρχείο με `new Document("Existing.docx")`, δημιουργήστε ένα `DocumentBuilder` για αυτό το έγγραφο και καλέστε `InsertChart` στη θέση του κέρσορα που επιθυμείτε.

**Ε: Πώς να διαχειριστώ μεγάλα σύνολα δεδομένων;**  
Α: Τα γραφήματα πίτας είναι καλύτερα για περιορισμένο αριθμό κατηγοριών (συνήθως < 10). Για πολλές κατηγορίες, σκεφτείτε ένα γράφημα ράβδων ή στηλών.

## Ανακεφαλαίωση πλήρους κώδικα

Παρακάτω βρίσκεται το ολοκληρωμένο πρόγραμμα σε ένα μπλοκ για εύκολη αντιγραφή‑επικόλληση:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Η εκτέλεση αυτού του κώδικα παράγει το στυλιζαρισμένο γράφημα πίτας στο έγγραφο Word που περιγράφηκε παραπάνω.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε έγγραφα Word με γράφημα πίτας** χρησιμοποιώντας το Aspose.Words, **να προσαρμόσετε χρώματα γραφήματος πίτας**, και **να αλλάξετε το χρώμα φέτας πίτας** προγραμματιστικά. Ο οδηγός κάλυψε την εισαγωγή του γραφήματος, την προσθήκη δεδομένων, την εκτόξευση φέτας, την εφαρμογή προσαρμοσμένων χρωμάτων και την αποθήκευση του αποτελέσματος.  

Από εδώ μπορείτε να εξερευνήσετε σχετικές θεματικές όπως **πώς να εισάγετε άλλους τύπους γραφημάτων**, προσθήκη υπομνήματος, ή δημιουργία πολυσελιδικών αναφορών με πολλαπλά γραφήματα. Πειραματιστείτε με διαφορετικά σχήματα χρωμάτων και σύνολα δεδομένων για να ταιριάξουν στις ανάγκες αναφοράς σας.

Καλό προγραμματισμό!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}