---
category: general
date: 2026-09-21
description: Δημιουργήστε ένα κενό έγγραφο Word και μάθετε πώς να εισάγετε διάγραμμα
  ραντάρ σε ένα αρχείο Word χρησιμοποιώντας το DocumentBuilder – βήμα‑βήμα οδηγός.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: el
lastmod: 2026-09-21
og_description: Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε διάγραμμα ραντάρ σε
  ένα αρχείο Word με το Aspose.Words. Ακολουθήστε αυτό το σεμινάριο για να δημιουργήσετε
  γρήγορα ένα διάγραμμα σε έγγραφο Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα διάγραμμα ραντάρ –
  πλήρης οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Πώς να δημιουργήσετε ένα κενό έγγραφο Word και να προσθέσετε ένα διάγραμμα
  ραντάρ σε C#
url: /el/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα κενό έγγραφο Word και να προσθέσετε ένα ραδάριο γράφημα σε C#

Αν χρειάζεστε **δημιουργήσετε ένα κενό έγγραφο Word** και να ενσωματώσετε ένα ραδάριο (ακτινικό) γράφημα, αυτό το tutorial παρέχει μια έτοιμη προς εκτέλεση λύση. Θα δείτε πώς να χρησιμοποιήσετε το Aspose.Words .NET για να δημιουργήσετε το αρχείο, να εισάγετε το γράφημα και να αποθηκεύσετε το αποτέλεσμα—όλα σε λίγα σύντομα βήματα.

Ένα κενό έγγραφο παρέχει έναν καθαρό καμβά για οποιοδήποτε σενάριο αυτοματοποιημένης αναφοράς, και η προσθήκη ραδάριου γραφήματος σας επιτρέπει να οπτικοποιήσετε πολυδιάστατα δεδομένα απευθείας μέσα στο Word. Στο τέλος αυτού του οδηγού θα μπορείτε να δημιουργήσετε ένα γράφημα σε έγγραφο Word χωρίς χειροκίνητη επεξεργασία.

## What you’ll learn

* Πώς να **δημιουργήσετε κενό έγγραφο Word** προγραμματιστικά με C#.
* Ο ακριβής κώδικας για **πώς να εισάγετε ραδάριο γράφημα** χρησιμοποιώντας το `DocumentBuilder`.
* Τρόποι για **εισαγωγή γραφήματος σε αρχείο Word** και προσαρμογή του μεγέθους.
* Πώς να **δημιουργήσετε γράφημα σε έγγραφο Word** και να επαληθεύσετε το αποτέλεσμα.
* Συμβουλές για **προσθήκη ακτινικού γραφήματος σε Word** αρχεία, συμπεριλαμβανομένων κοινών παγίδων.

### Prerequisites

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).
* Aspose.Words for .NET (πακέτο NuGet `Aspose.Words` έκδοση 23.9 ή νεότερη).
* Βασική εξοικείωση με C# και Visual Studio ή το προτιμώμενο IDE σας.

## Create a blank Word document with C#

Το πρώτο βήμα είναι η δημιουργία ενός κενών αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα εντελώς κενό αρχείο `.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` δημιουργεί τη δομή του αρχείου αλλά δεν περιέχει ακόμη ενότητες ή σελίδες. Το Aspose.Words προσθέτει αυτόματα μια προεπιλεγμένη ενότητα όταν αρχίσετε να προσθέτετε περιεχόμενο, γι' αυτό το επόμενο βήμα λειτουργεί χωρίς επιπλέον ρυθμίσεις.

## How to insert a radar chart into the Word file

Ένα ραδάριο γράφημα (επίσης γνωστό ως ακτινικό γράφημα) οπτικοποιεί σημεία δεδομένων σε άξονες που ακτινοβολούν από ένα κεντρικό σημείο. Το Aspose.Words παρέχει τη μέθοδο `DocumentBuilder.insertChart` για αυτό το σκοπό.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` επιστρέφει ένα αντικείμενο `Chart` που μπορείτε να διαμορφώσετε περαιτέρω. Το γράφημα εμφανίζεται στην πρώτη σελίδα του κενών εγγράφου επειδή ο builder είναι τοποθετημένος στην αρχή του εγγράφου από προεπιλογή.

## Insert chart into a Word file – adding data series

Ένα γράφημα χωρίς δεδομένα είναι αόρατο. Συμπληρώστε το ραδάριο γράφημα με μία ή περισσότερες σειρές για να το κάνετε χρήσιμο.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Μπορείτε να προσθέσετε όσες σειρές χρειάζεστε. Κάθε σειρά μπορεί να έχει διαφορετικό όνομα, το οποίο εμφανίζεται στο υπόμνημα του γραφήματος. Τα σημεία δεδομένων αντιστοιχούν στους ακτινικούς άξονες· η σειρά με την οποία τα προσθέτετε καθορίζει τη θέση τους γύρω από τον κύκλο.

## Generate a Word document chart – saving the file

Αφού δημιουργήσετε το γράφημα, αποθηκεύστε το έγγραφο στο δίσκο. Επιλέξτε μια θέση στην οποία έχετε δικαίωμα εγγραφής.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Όταν ανοίξετε το παραγόμενο αρχείο `.docx` στο Microsoft Word, θα δείτε μια κενή σελίδα με ένα ραδάριο γράφημα διαστάσεων 400 × 300 points, γεμάτο με τα δείγμα δεδομένων.

### Expected output

* Ένα αρχείο `RadialChartExample.docx` στην επιφάνεια εργασίας σας.
* Η πρώτη σελίδα περιέχει ένα ραδάριο γράφημα με πέντε σημεία δεδομένων με την ετικέτα “Series 1”.
* Δεν εμφανίζεται επιπλέον κείμενο επειδή το έγγραφο ξεκίνησε κενό.

## Add radial chart word – handling common edge cases

### 1. Changing chart size after insertion

Αν οι αρχικές διαστάσεις δεν ταιριάζουν με τη διάταξή σας, αλλάξτε το μέγεθος του γραφήματος ως εξής:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Inserting the chart into a specific location

Μπορείτε να μετακινήσετε τον κέρσορα του builder σε σελιδοδείκτη, κελί πίνακα ή παράγραφο πριν καλέσετε το `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Customizing chart appearance

Το Aspose.Words εκθέτει ολόκληρο το μοντέλο αντικειμένων του γραφήματος, επιτρέποντάς σας να ορίσετε τίτλους, ετικέτες άξονα και χρώματα.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Dealing with missing fonts

Αν το περιβάλλον προορισμού δεν διαθέτει μια γραμματοσειρά που χρησιμοποιείται στο γράφημα, το Aspose.Words αντικαθιστά με προεπιλεγμένη γραμματοσειρά. Για να εξασφαλίσετε συνέπεια, ενσωματώστε τις απαιτούμενες γραμματοσειρές:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Exporting to other formats

Το ίδιο έγγραφο μπορεί να αποθηκευτεί ως PDF, HTML ή PNG χωρίς επιπλέον αλλαγές κώδικα:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Full, runnable example

Συνδυάζοντας όλα τα κομμάτια μαζί λαμβάνετε ένα ενιαίο πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και να εκτελέσετε.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Τρέξτε αυτό το πρόγραμμα, ανοίξτε το παραγόμενο αρχείο και θα δείτε ένα επαγγελματικό ραδάριο γράφημα έτοιμο για διανομή.

## Conclusion

Τώρα ξέρετε πώς να **δημιουργήσετε κενό έγγραφο Word**, **πώς να εισάγετε ραδάριο γράφημα**, και **να δημιουργήσετε γράφημα σε έγγραφο Word** χρησιμοποιώντας το Aspose.Words. Ακολουθώντας τα παραπάνω βήματα μπορείτε επίσης να **προσθέσετε ακτινικό γράφημα σε Word** αρχεία σε οποιοδήποτε αυτοματοποιημένο pipeline αναφορών, να προσαρμόσετε το μέγεθος, το στυλ και να εξάγετε σε επιπλέον μορφές.

**Next steps**

* Εξερευνήστε άλλους τύπους γραφημάτων (`ChartType.Column`, `ChartType.Pie`) για να διευρύνετε το εργαλείο αναφοράς σας.
* Συνδυάστε πολλαπλά γραφήματα σε μια σελίδα καλώντας το `InsertChart` επανειλημμένα.
* Ενσωματώστε δεδομένα από βάση δεδομένων ή αρχείο CSV για δυναμική πληρότητα των σειρών.
* Ανασκοπήστε την τεκμηρίωση του Aspose.Words για προχωρημένες επιλογές μορφοποίησης όπως υπό όρους ετικέτες δεδομένων και πρότυπα γραφημάτων.

Αισθανθείτε ελεύθεροι να πειραματιστείτε με τον κώδικα, να προσαρμόσετε τις διαστάσεις ή να αντικαταστήσετε τα δείγμα δεδομένων με πραγματικά επιχειρηματικά μετρικά. Καλή προγραμματιστική!

## What Should You Learn Next?

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή Στήλης Γραφήματος στο Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Δημιουργία Scatter Γραφήματος Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Εισαγωγή Bubble Γραφήματος στο Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}