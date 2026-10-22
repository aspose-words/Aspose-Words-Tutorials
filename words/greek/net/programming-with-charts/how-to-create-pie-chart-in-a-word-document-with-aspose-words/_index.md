---
category: general
date: 2026-09-21
description: Μάθετε πώς να δημιουργήσετε διάγραμμα πίτας και να το εισάγετε σε Word
  χρησιμοποιώντας το Aspose.Words, να προσθέσετε ετικέτες δεδομένων στο διάγραμμα
  πίτας και να εμφανίσετε τα ποσοστά στο διάγραμμα πίτας σε λίγα μόνο βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: el
lastmod: 2026-09-21
og_description: Δημιουργήστε διάγραμμα πίτας στο Word χρησιμοποιώντας το Aspose.Words,
  εισάγετε το διάγραμμα στο Word, προσθέστε ετικέτες δεδομένων στο διάγραμμα πίτας
  και εμφανίστε τα ποσοστά στο διάγραμμα πίτας—όλα με σαφή παραδείγματα κώδικα.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Δημιουργήστε ένα διάγραμμα πίτας στο Word με το Aspose.Words – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Πώς να δημιουργήσετε διάγραμμα πίτας σε ένα έγγραφο Word με το Aspose.Words
url: /el/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε διάγραμμα πίτας σε έγγραφο Word με Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε διάγραμμα πίτας** προγραμματιστικά, το Aspose.Words το κάνει απλό. Σε αυτό το tutorial θα δείτε πώς να **εισάγετε διάγραμμα σε Word**, να διαμορφώσετε τις σειρές, **να προσθέσετε ετικέτες δεδομένων στο διάγραμμα πίτας**, και τελικά **να εμφανίσετε τα ποσοστά στο διάγραμμα πίτας** ώστε η οπτική παρουσίαση να μεταφέρει ακριβείς τιμές. Στο τέλος θα έχετε ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

Αυτός ο οδηγός καλύπτει όλα όσα χρειάζεστε: απαιτούμενα πακέτα NuGet, ο πλήρης κώδικας C#, εξηγήσεις για το γιατί κάθε κλήση API είναι σημαντική, και συμβουλές για την προσαρμογή του διαγράμματος. Δεν απαιτείται εξωτερική τεκμηρίωση — απλώς αντιγράψτε, εκτελέστε και προσαρμόστε.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη.  
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει .NET).  
* Άδεια Aspose.Words for .NET (η δωρεάν δοκιμή λειτουργεί για δοκιμές).  
* Βασική εξοικείωση με C# και τη δομή εγγράφων Word.

Αν έχετε ήδη όλα αυτά, μπορείτε να προχωρήσετε κατευθείαν στον κώδικα.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή του Aspose.Words

Δημιουργήστε ένα νέο έργο console και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Το πακέτο περιλαμβάνει το namespace `Aspose.Words.Drawing.Charts`, το οποίο περιέχει τις κλάσεις `Chart` και `ChartSeries` που θα χρησιμοποιήσουμε.

> **Pro tip:** Τοποθετήστε το αρχείο άδειας (`Aspose.Words.lic`) στη ρίζα του έργου και φορτώστε το κατά την εκκίνηση για να αποφύγετε τα υδατογραφήματα αξιολόγησης.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Βήμα 2: Δημιουργία κεντρικού εγγράφου και DocumentBuilder

Ένα `Document` αντιπροσωπεύει το αρχείο Word, ενώ το `DocumentBuilder` παρέχει μια fluent API για την εισαγωγή περιεχομένου.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:** Ο `DocumentBuilder` διατηρεί το τρέχον σημείο εισαγωγής, εξασφαλίζοντας ότι το διάγραμμα εμφανίζεται ακριβώς εκεί που το θέλετε στη ροή του εγγράφου.

## Βήμα 3: Εισαγωγή διαγράμματος πίτας στο έγγραφο Word

Τώρα **εισάγουμε διάγραμμα σε Word**. Η μέθοδος `InsertChart` δέχεται τον τύπο διαγράμματος, το πλάτος και το ύψος (σε points).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Σε αυτό το σημείο το διάγραμμα περιέχει μια προεπιλεγμένη σειρά δεδομένων με τιμές placeholder (25, 25, 25, 25). Μπορείτε να τις αντικαταστήσετε αργότερα αν χρειαστεί.

## Βήμα 4: Πρόσβαση στην πρώτη σειρά και προσαρμογή ετικετών δεδομένων

Ένα διάγραμμα πίτας συνήθως έχει μία σειρά. Για να **προσθέσετε ετικέτες δεδομένων στο διάγραμμα πίτας**, την ανακτούμε και ενεργοποιούμε την εμφάνιση ποσοστών.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Γιατί ορίζουμε `ShowPercentage`:** Αυτή η σημαία λέει στο Aspose.Words να υπολογίσει τη συνεισφορά κάθε φέτας και να την αποδώσει ως ποσοστό. Η ιδιότητα `Position` εξασφαλίζει ότι η ετικέτα δεν επικαλύπτεται με τη φέτα, βελτιώνοντας την αναγνωσιμότητα — ειδικά όταν οι φέτες είναι μικρές.

## Βήμα 5: (Προαιρετικό) Αντικατάσταση των placeholder δεδομένων

Αν θέλετε συγκεκριμένες τιμές, αντικαταστήστε τα προεπιλεγμένα σημεία:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Τα ποσοστά που εμφανίζονται θα προσαρμοστούν αυτόματα ώστε να αντικατοπτρίζουν τις νέες τιμές.

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Η επέκταση καθορίζει τη μορφή· το `.docx` δημιουργεί ένα σύγχρονο αρχείο Word.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Η εκτέλεση του προγράμματος παράγει ένα αρχείο με όνομα **PieChart.docx** στον φάκελο εξόδου. Ανοίγοντάς το στο Microsoft Word, θα δείτε ένα διάγραμμα πίτας με κάθε φέτα να φέρει το ποσοστό της, τοποθετημένο εκτός των φετών.

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το παραγόμενο έγγραφο, θα πρέπει να δείτε:

* Ένα μόνο διάγραμμα πίτας, 400 × 300 pt σε μέγεθος.  
* Τέσσερις φέτες (ή όσες σημεία έχετε προσθέσει).  
* Ετικέτες ποσοστών όπως “40 %”, “30 %”, κ.λπ., εμφανιζόμενες εκτός κάθε φέτας.

Αν οι ετικέτες εμφανίζονται μέσα στις φέτες, ελέγξτε ξανά ότι η τιμή `ChartDataLabelPosition.OutsideEnd` έχει οριστεί σωστά.

## Βήμα 7: Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

### Προσθήκη τίτλου στο διάγραμμα

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Αλλαγή χρωμάτων φετών

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Διαχείριση κενής σειράς

Αν η πηγή δεδομένων σας μπορεί να είναι κενή, προστατέψτε το πρόγραμμα από `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Εξαγωγή σε PDF αντί για Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

Η ίδια λογική απόδοσης διαγράμματος εφαρμόζεται· το Aspose.Words μετατρέπει αυτόματα τη διάταξη Word σε PDF.

## Πλήρης λίστα κώδικα

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντιγράψτε το στο `Program.cs` και εκτελέστε `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε διάγραμμα πίτας** σε αρχείο Word χρησιμοποιώντας το Aspose.Words, **να εισάγετε διάγραμμα σε Word**, **να προσθέσετε ετικέτες δεδομένων στο διάγραμμα πίτας**, και **να εμφανίσετε τα ποσοστά στο διάγραμμα πίτας**. Το παράδειγμα δείχνει ολόκληρη τη ροή εργασίας — από τη ρύθμιση του έργου μέχρι το τελικό έγγραφο — ώστε να το προσαρμόσετε για dashboards, αναφορές ή αυτοματοποιημένη δημιουργία τιμολογίων.  

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **πώς να εμφανίσετε ποσοστά σε υπομνήματα διαγράμματος**, προσαρμογή χρωμάτων διαγράμματος, ή μετατροπή του εγγράφου Word σε PDF για διανομή. Πειραματιστείτε με διαφορετικούς τύπους διαγραμμάτων (Bar, Line) χρησιμοποιώντας την ίδια μέθοδο `InsertChart` για να επεκτείνετε τις δυνατότητες αυτοματοποίησής σας.

Καλή δημιουργία διαγραμμάτων!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}