---
category: general
date: 2026-10-07
description: Μάθετε πώς να δημιουργήσετε έγγραφο Word και να εισάγετε διάγραμμα πίτας
  χρησιμοποιώντας το Aspose.Words σε C#. Ο οδηγός δείχνει επίσης πώς να δημιουργήσετε
  αρχείο Word με προσαρμοσμένες ετικέτες διαγράμματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: el
lastmod: 2026-10-07
og_description: Δημιουργήστε έγγραφο Word και εισάγετε διάγραμμα πίτας σε C#. Ακολουθήστε
  αυτόν τον οδηγό βήμα‑βήμα για να δημιουργήσετε αρχείο Word με πλήρως προσαρμοσμένες
  ετικέτες διαγράμματος.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Δημιουργήστε ένα έγγραφο Word με προσαρμοσμένο διάγραμμα πίτας σε C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Πώς να δημιουργήσετε έγγραφο Word με προσαρμοσμένο διάγραμμα πίτας σε C#
url: /el/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο Word με προσαρμοσμένο γράφημα πίτας σε C#

Αν χρειάζεστε **να δημιουργήσετε έγγραφο Word** προγραμματιστικά, αυτό το tutorial σας δείχνει πώς να **εισάγετε γράφημα πίτας** και να προσαρμόσετε τις ετικέτες δεδομένων του χρησιμοποιώντας το Aspose.Words for .NET. Θα μάθετε επίσης πώς να **δημιουργήσετε αρχείο Word** που περιέχει ένα πλήρως μορφοποιημένο γράφημα, καλύπτοντας όλα από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού εγγράφου.

Ο οδηγός περνάει βήμα προς βήμα από όλα τα απαραίτητα βήματα για την προσθήκη ενός γραφήματος, την προσαρμογή των θέσεων των ετικετών, την ενεργοποίηση γραμμών οδηγού, και τέλος την αποθήκευση του αποτελέσματος ως αρχείο `.docx`. Δεν απαιτούνται εξωτερικά εργαλεία εκτός από τη βιβλιοθήκη Aspose.Words, και ο πλήρης κώδικας πηγής παρέχεται ώστε να μπορείτε να τον αντιγράψετε, επικολλήσετε και εκτελέσετε αμέσως.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερο εγκατεστημένο  
* Έγκυρη άδεια Aspose.Words for .NET (ή δωρεάν κλειδί αξιολόγησης)  
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code  

Θα χρειαστεί επίσης να προσθέσετε τα παρακάτω πακέτα NuGet στο έργο σας:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Αυτά τα πακέτα εκθέτουν τις κλάσεις `Document`, `DocumentBuilder` και τις κλάσεις σχετικές με γραφήματα που χρησιμοποιούνται στα παραδείγματα παρακάτω.

## Δημιουργία εγγράφου Word και προσθήκη γραφήματος

Το πρώτο βήμα είναι να **δημιουργήσετε έγγραφο Word** και να αποκτήσετε ένα `DocumentBuilder` που σας επιτρέπει να εισάγετε περιεχόμενο. Ο builder λειτουργεί όπως ένας κέρσορας τοποθετημένος μέσα στο έγγραφο.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` παρέχει μεθόδους όπως `InsertChart` που τοποθετούν αντικείμενα απευθείας στη ροή του εγγράφου.

## Εισαγωγή γραφήματος πίτας στο έγγραφο

Τώρα που ο builder είναι έτοιμος, μπορείτε να **εισάγετε γράφημα πίτας** με συγκεκριμένο μέγεθος. Το γράφημα προστίθεται στη τρέχουσα θέση του builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

Η `InsertChart` επιστρέφει ένα αντικείμενο `Chart` που μπορείτε να επεξεργαστείτε περαιτέρω. Τα δείγματα δεδομένων δημιουργούν τέσσερις φέτες που αντιπροσωπεύουν τις τριμηνιαίες πωλήσεις.

## Προσαρμογή ετικετών δεδομένων γραφήματος πίτας

Για να γίνει το γράφημα πιο ευανάγνωστο, συχνά χρειάζεται να **προσαρμόσετε τις ετικέτες του γραφήματος πίτας**—να τις τοποθετήσετε έξω από τις φέτες και να εμφανίσετε γραμμές οδηγού. Εδώ έρχεται η `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Ορίζοντας το `Position` σε `OutsideEnd` μετακινεί κάθε ετικέτα πέρα από την άκρη της φέτας, ενώ το `ShowLeaderLines` σχεδιάζει μια γραμμή που συνδέει την ετικέτα με τη φέτα της. Οι προαιρετικές σημαίες `ShowValue` και `ShowPercentage` παρέχουν στους αναγνώστες τόσο τις ακατέργαστες τιμές όσο και τα σχετικά ποσοστά.

**Συμβουλή:** Αν χρειάζεστε μορφοποίηση της γραμματοσειράς της ετικέτας, χρησιμοποιήστε `dataLabels.Font` για να ορίσετε μέγεθος, χρώμα και στυλ. Αυτό εξασφαλίζει ότι το γράφημα ταιριάζει με την εταιρική σας ταυτότητα.

## Αποθήκευση και δημιουργία αρχείου Word

Αφού το γράφημα είναι πλήρως διαμορφωμένο, μπορείτε να **δημιουργήσετε αρχείο Word** αποθηκεύοντας το στιγμιότυπο `Document` στο δίσκο. Επιλέξτε τη μορφή `.docx` για μέγιστη συμβατότητα με σύγχρονες εκδόσεις του Word.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Όταν ανοίξετε το `CustomPieChart.docx`, θα δείτε ένα γράφημα πίτας με τέσσερις φέτες, η καθεμία ετικετοποιημένη έξω από τη φέτα, συνδεδεμένη με γραμμές οδηγού, και εμφανίζοντας τόσο την τιμή όσο και το ποσοστό.

![Screenshot of a Word document that contains a customized pie chart created with C#](image-placeholder.png)

*Η εικόνα δείχνει το τελικό αποτέλεσμα του οδηγού **create word document**.*

## Κοινές παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|----------------------|
| **Πολλαπλές σειρές** | Προσθέστε επιπλέον αντικείμενα `ChartSeries` στο `pieChart.Series`. Κάθε σειρά μπορεί να έχει τη δική της συλλογή `DataLabels` για ανεξάρτητη μορφοποίηση. |
| **Διαφορετικό μέγεθος γραφήματος** | Αλλάξτε τις παραμέτρους πλάτους και ύψους στο `InsertChart(width, height)`. Οι τιμές είναι σε σημεία (1 pt ≈ 1/72 in). |
| **Τίτλος γραφήματος** | Χρησιμοποιήστε `pieChart.Title.Text = "Quarterly Sales"` για να προσθέσετε έναν περιγραφικό τίτλο. |
| **Εξαγωγή σε PDF** | Καλέστε `document.Save("Report.pdf", SaveFormat.Pdf);` μετά την κατασκευή του γραφήματος. |
| **Διαχείριση άδειας** | Τοποθετήστε το αρχείο άδειας (`Aspose.Words.lic`) στο φάκελο της εφαρμογής και φορτώστε το με `new License().SetLicense("Aspose.Words.lic");` πριν δημιουργήσετε το έγγραφο. |

Αυτές οι παραλλαγές σας επιτρέπουν να απαντήσετε στην ερώτηση **πώς να προσθέσετε γράφημα πίτας** σε πολλές πραγματικές περιπτώσεις, από απλές αναφορές μέχρι σύνθετα dashboards.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε έγγραφο Word**, **εισάγετε γράφημα πίτας**, και **προσαρμόσετε ετικέτες γραφήματος πίτας** χρησιμοποιώντας το Aspose.Words for .NET. Το πλήρες παράδειγμα δείχνει μια καθαρή ροή εργασίας: αρχικοποίηση του εγγράφου, προσθήκη γραφήματος, προσαρμογή θέσης ετικετών δεδομένων, ενεργοποίηση γραμμών οδηγού, και τέλος **δημιουργία αρχείου Word** που μπορεί να μοιραστεί με οποιονδήποτε.

Δοκιμάστε να επεκτείνετε αυτό το tutorial πειραματιζόμενοι με διαφορετικούς τύπους γραφημάτων (`ChartType.Column`, `ChartType.Line`) ή εφαρμόζοντας προσαρμοσμένες παλέτες χρωμάτων για να ταιριάζουν με το brand σας. Αν αντιμετωπίσετε προβλήματα, συμβουλευτείτε την τεκμηρίωση του Aspose.Words ή εξερευνήστε συναφή θέματα όπως “πώς να προσθέσετε γράφημα πίτας” με πολλαπλές σειρές και δυναμικές πηγές δεδομένων.

Καλό κώδικα, και μη διστάσετε να μοιραστείτε τα αποτελέσματά σας ή να θέσετε ερωτήσεις στα σχόλια!

## Τι Θα Μάθετε Στη Σύντομη Επόμενη Φάση;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή Γραφήματος Στήλης Σε Έγγραφο Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Εισαγωγή Γραφήματος Περιοχής Σε Έγγραφο Word](/words/english/net/programming-with-charts/insert-area-chart/)
- [Εισαγωγή Γραφήματος Διασποράς Σε Έγγραφο Word](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}