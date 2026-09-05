---
category: general
date: 2026-09-05
description: Δημιουργήστε διάγραμμα ραντάρ στο Word χρησιμοποιώντας C#. Μάθετε πώς
  να δημιουργείτε ένα κενό έγγραφο Word, να προσθέτετε διάγραμμα ραντάρ, να ορίζετε
  το μέγεθος του διαγράμματος και να ενεργοποιείτε τα σημεία σήμανσης γρήγορα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: el
lastmod: 2026-09-05
og_description: Δημιουργήστε διάγραμμα ραντάρ στο Word χρησιμοποιώντας C#. Αυτός ο
  οδηγός σας δείχνει πώς να δημιουργήσετε ένα κενό έγγραφο Word, να προσθέσετε ένα
  διάγραμμα ραντάρ, να ορίσετε το μέγεθος του διαγράμματος και να ενεργοποιήσετε τις
  γραμμές σήμανσης — όλα σε λίγα λεπτά.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Δημιουργία διαγράμματος ραντάρ στο Word – βήμα‑βήμα οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Πώς να δημιουργήσετε διάγραμμα ραντάρ και να προσθέσετε το διάγραμμα στο Word
  με C#
url: /el/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε διάγραμμα ραντάρ και να προσθέσετε διάγραμμα στο Word με C#

Αν χρειάζεστε **create radar chart** μέσα σε αρχείο Word, αυτός ο οδηγός σας καθοδηγεί σε όλη τη διαδικασία. Θα μάθετε πώς να **generate blank word document**, να εισάγετε ένα διάγραμμα ραντάρ, **set chart size word**, και να ενεργοποιήσετε τις διαβάσεις του άξονα—όλα με λίγες γραμμές κώδικα C#.

Η προσθήκη οπτικών δεδομένων σε αναφορές είναι κοινή απαίτηση, και η χρήση του Aspose.Words το καθιστά απλό. Στα παρακάτω βήματα καλύπτουμε επίσης πώς να **add chart to word** έγγραφα προγραμματιστικά, ώστε να μπορείτε να αυτοματοποιήσετε πίνακες ελέγχου, οικονομικές περιλήψεις ή οποιοδήποτε περιεχόμενο βασισμένο σε δεδομένα.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη  
* Άδεια Aspose.Words for .NET (ή δωρεάν δοκιμή) – η βιβλιοθήκη παρέχει τα `Document`, `DocumentBuilder` και τα API διαγραμμάτων που χρησιμοποιούνται σε αυτόν τον οδηγό  
* Visual Studio 2022 (ή οποιοδήποτε IDE C#)  

> **Pro tip:** Αν κάνετε δοκιμές, τοποθετήστε το Aspose.Words DLL στο φάκελο `bin` του έργου σας και αναφερθείτε σε αυτό μέσω NuGet (`Install-Package Aspose.Words`).

## Πώς να δημιουργήσετε διάγραμμα ραντάρ σε έγγραφο Word

Το πρώτο βήμα είναι να **generate blank word document** που θα φιλοξενήσει το διάγραμμα. Αυτό σας παρέχει ένα καθαρό καμβά και σας επιτρέπει να ελέγξετε τα μεταδεδομένα του εγγράφου πριν προστεθεί οποιοδήποτε περιεχόμενο.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Γιατί είναι σημαντικό:* Ένα κενό αντικείμενο `Document` εξασφαλίζει ότι δεν υπάρχουν κρυφά στυλ ή ενότητες που να επηρεάζουν τη διάταξη του διαγράμματος. Επίσης σας επιτρέπει να ορίσετε ιδιότητες εγγράφου (συγγραφέας, τίτλος) αργότερα αν χρειαστεί.

## Πώς να προσθέσετε διάγραμμα στο Word χρησιμοποιώντας Aspose.Words

Στη συνέχεια, δημιουργήστε ένα `DocumentBuilder`. Ο builder είναι το κεντρικό εργαλείο που σας επιτρέπει να εισάγετε κείμενο, εικόνες και διαγράμματα στο έγγραφο.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Τώρα μπορείτε να **add radar chart** απευθείας στη θέση όπου βρίσκεται ο κέρσορας. Η μέθοδος `InsertChart` δέχεται μια παράμετρο enum `ChartType`, πλάτος και ύψος σε points.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Γιατί 400 × 300;* Αυτές οι διαστάσεις παρέχουν ένα καθαρό, ευανάγνωστο διάγραμμα σε τυπική σελίδα A4. Μπορείτε να προσαρμόσετε το μέγεθος αργότερα με το βήμα **set chart size word** εάν η διάταξή σας απαιτεί διαφορετική αναλογία διαστάσεων.

## Ορισμός μεγέθους διαγράμματος στο Word

Αν χρειάζεται να ρυθμίσετε ακριβώς το μέγεθος μετά την εισαγωγή, μπορείτε να τροποποιήσετε τις ιδιότητες `Width` και `Height` του διαγράμματος. Αυτό είναι χρήσιμο όταν το περιβάλλον κείμενο ή τα περιθώρια της σελίδας απαιτούν διαφορετική οπτική ισορροπία.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Σημείωση:** Η υπερφόρτωση της `InsertChart` ορίζει ήδη το μέγεθος, έτσι ο παραπάνω κώδικας είναι προαιρετικός και εμφανίζεται για πληρότητα.

## Ενεργοποίηση σημείων σήμανσης στον ακτινικό άξονα

Ένα διάγραμμα ραντάρ είναι πιο χρήσιμο όταν ο ακτινικός άξονας εμφανίζει σαφείς διαβάσεις. Οι παρακάτω ρυθμίσεις ενεργοποιούν τα σημεία σήμανσης και ορίζουν το διάστημα σε 30 μοίρες, που ευθυγραμμίζεται με τυπικές οθόνες ραντάρ τύπου πυξίδας.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Γιατί είναι σημαντικό:* Οι διαβάσεις βοηθούν τους αναγνώστες να εκτιμήσουν τις τιμές σε κάθε γωνία, βελτιώνοντας την αναγνωσιμότητα για τα ενδιαφερόμενα μέρη που δεν είναι εξοικειωμένα με τα δεδομένα.

## Αποθήκευση του εγγράφου που περιέχει το διάγραμμα

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιονδήποτε φάκελο θέλετε· απλώς βεβαιωθείτε ότι η διαδρομή υπάρχει.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Όταν ανοίξετε το `RadialChart.docx` στο Microsoft Word, θα δείτε ένα πλήρως αποδομημένο διάγραμμα ραντάρ κεντραρισμένο στη σελίδα, με το μέγεθος όπως ορίστηκε, και σημεία σήμανσης κάθε 30 μοίρες.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο `.docx` με όνομα **RadialChart.docx**  
* Η πρώτη σελίδα περιέχει ένα διάγραμμα ραντάρ μεγέθους 400 × 300 points  
* Ο άξονας X (ακτινικός άξονας) εμφανίζει σημεία σήμανσης στα 0°, 30°, 60°, …, 330°  

Τώρα μπορείτε να αντικαταστήσετε τη σειρά δεδομένων placeholder με τις δικές σας τιμές προσπελαύνοντας το `radarChart.Series` – αλλά αυτό υπερβαίνει το πεδίο αυτού του βασικού οδηγού **add radar chart**.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Scenario | Adjustment |
|----------|------------|
| **Different chart type** | Replace `ChartType.Radar` with `ChartType.Column`, `ChartType.Pie`, etc. |
| **Multiple charts** | Call `InsertChart` repeatedly; each call positions the new chart after the previous one. |
| **Large data sets** | Use `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` to populate many points. |
| **Saving as PDF** | Call `document.Save("RadialChart.pdf", SaveFormat.Pdf);` after the chart is added. |
| **Running on .NET Core** | Ensure you reference `Aspose.Words.NETCore` package; API usage is identical. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή κονσόλας. Περιλαμβάνει όλα τα βήματα, προαιρετικές ρυθμίσεις μεγέθους, και σχόλια για σαφήνεια.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο αρχείο, και θα δείτε το διάγραμμα ραντάρ ακριβώς όπως περιγράφεται.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create radar chart** και **add chart to Word** έγγραφα χρησιμοποιώντας C#. Ο οδηγός κάλυψε τη δημιουργία ενός **blank word document**, την εισαγωγή διαγράμματος ραντάρ, **set chart size word**, και την ενεργοποίηση των διαβάσεων του άξονα. Με αυτή τη βάση μπορείτε να επεκτείνετε τη λύση σε πολλαπλά διαγράμματα, προσαρμοσμένες σειρές δεδομένων ή εξαγωγή σε PDF.

### Επόμενα βήματα

* Εξερευνήστε άλλους τύπους διαγραμμάτων με `ChartType` (π.χ., `Bar`, `Line`) – δείτε τη λέξη-κλειδί **add radar chart** για σχετικά παραδείγματα.

## Τι Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}