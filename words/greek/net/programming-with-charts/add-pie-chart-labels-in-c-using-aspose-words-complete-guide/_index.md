---
category: general
date: 2026-07-20
description: Προσθέστε ετικέτες σε διάγραμμα πίτας με το Aspose.Words για .NET. Μάθετε
  πώς να αλλάζετε τις ετικέτες του διαγράμματος πίτας, να εμφανίζετε ετικέτες ποσοστών
  και να ενημερώνετε γρήγορα τις ετικέτες των σειρών του διαγράμματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: el
lastmod: 2026-07-20
og_description: Προσθέστε ετικέτες διαγράμματος πίτας σε C# με το Aspose.Words. Κατακτήστε
  την αλλαγή ετικετών διαγράμματος πίτας, την εμφάνιση ετικετών ποσοστών και την ενημέρωση
  ετικετών σειρών διαγράμματος σε λίγα μόνο βήματα.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Προσθήκη ετικετών διαγράμματος πίτας σε C# – Πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Προσθήκη ετικετών διαγράμματος πίτας σε C# με χρήση του Aspose.Words – Πλήρης
  Οδηγός
url: /el/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη ετικετών διαγράμματος πίτας σε C# χρησιμοποιώντας Aspose.Words – Πλήρης Οδηγός

Need to **add pie chart labels** to a Word document using C#? With Aspose.Words you can effortlessly **change pie chart labels** and **display pie chart percentages** right inside the file—no manual tweaking in Word required.  

In this tutorial we’ll walk through the exact steps to **show percentage labels**, reposition them, and even **update chart series labels** for dynamic data. By the end you’ll have a reusable snippet that you can drop into any .NET project.

> **Γρήγορη προεπισκόπηση:** After following the guide, opening the saved `.docx` will reveal a pie chart where each slice is labeled with its percentage, positioned outside the slice for maximum readability.

---

## Τι Θα Χρειαστεί

- **Aspose.Words for .NET** (η τελευταία έκδοση μέχρι το 2026). Μπορείτε να το αποκτήσετε από το NuGet: `Install-Package Aspose.Words`.
- Ένα **Word document** που ήδη περιέχει διάγραμμα πίτας ή δακτυλίου (θα το ονομάσουμε `Chart.docx`).
- Βασική εξοικείωση με **C#** και Visual Studio (ή το αγαπημένο σας IDE).

Αυτό είναι όλο — χωρίς επιπλέον βιβλιοθήκες, χωρίς COM interop, μόνο καθαρός διαχειριζόμενος κώδικας.

---

## Προσθήκη ετικετών διαγράμματος πίτας – Πλήρης Υλοποίηση

Below is a **complete, runnable** C# console program that loads a document, modifies the first pie chart, and saves the result. Every line is commented so you’ll understand **why** we’re doing what we’re doing, not just **what**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Αναμενόμενο Αποτέλεσμα

Open `ChartWithCustomLabels.docx` in Microsoft Word. You should see the pie chart **with percentage labels positioned outside each slice**. The labels look something like “35 %”, “20 %”, etc., making the chart instantly understandable.

---

## Αλλαγή ετικετών διαγράμματος πίτας: τοποθέτηση και μορφοποίηση

If you only need to **change pie chart labels** without showing percentages, you can adjust the `Position` property to one of the following:

| Enum Θέσης | Οπτικό Αποτέλεσμα |
|---------------|---------------|
| `InsideEnd`   | Οι ετικέτες βρίσκονται μέσα στη φέτα, ακριβώς στην άκρη. |
| `Center`      | Οι ετικέτες εμφανίζονται στη μέση της φέτας (κατάλληλο για μικρές πίτες). |
| `OutsideEnd`  | Οι ετικέτες είναι έξω από τη φέτα, συνδεδεμένες με γραμμή οδηγό (η προεπιλογή μας). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Συμβουλή:** `OutsideEnd` λειτουργεί καλύτερα όταν το διάγραμμα έχει πολλές φέτες· αποτρέπει την επικάλυψη κειμένου.

---

## Εμφάνιση ετικετών ποσοστών σε διάγραμμα πίτας

The property `ShowPercentage` is a **boolean flag**. Setting it to `true` tells Aspose.Words to calculate each slice’s contribution based on the underlying data source.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

You can also combine it with `ShowValue` if you need both raw numbers **and** percentages:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

When both flags are enabled, the label looks like “45 % (120)”.

---

## Ενημέρωση ετικετών σειρών διαγράμματος για δυναμικά δεδομένα

Often you’ll generate charts on the fly—think monthly sales or survey results. To **update chart series labels** programmatically, modify the `Series` collection before you touch the data labels:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

This snippet demonstrates how to **update chart series labels** for any series, not just the first one. It’s handy when you’re building reports that combine actual vs. forecast data.

---

## Ακραίες Περιπτώσεις & Συνηθισμένα Παγίδες

| Κατάσταση | Τι να Προσέξετε | Διόρθωση |
|-----------|-------------------|-----|
| **Το διάγραμμα δεν είναι πίτα/δακτύλιος** | `Position` μπορεί να μην έχει οπτικό αποτέλεσμα. | Επαληθεύστε ότι `chart.Type` είναι `ChartType.Pie` ή `ChartType.Doughnut`. |
| **Δεν βρέθηκε διάγραμμα** | `GetChild` επιστρέφει `null`. | Προσθέστε ρήτρα ελέγχου (δείτε τον κώδικα) και καταγράψτε ένα χρήσιμο μήνυμα. |
| **Παλαιότερη έκδοση Word** | Ορισμένες λειτουργίες ετικετών αγνοούνται. | Αποθηκεύστε ως `.docx` (τη σύγχρονη μορφή) για πλήρη υποστήριξη. |
| **Μεγάλος αριθμός φετών** | Οι ετικέτες μπορούν να επικαλύπτονται ακόμη και με `OutsideEnd`. | Σκεφτείτε να μειώσετε τον αριθμό φετών ή να αυξήσετε το μέγεθος του διαγράμματος. |

---

## Πλήρες Παράδειγμα Εργασίας (Αντιγραφή‑Επικόλληση)

Below is the **entire program** you can copy into a new console project. Just replace `YOUR_DIRECTORY` with the folder that holds `Chart.docx`.



## Τι Θα Μάθετε Στη Σύντομη Επόμενη

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Ορισμός Προεπιλεγμένων Επιλογών για Ετικέτες Δεδομένων σε Διάγραμμα](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Προσαρμογή Μίας Σειράς Διαγράμματος σε Διάγραμμα](/words/english/net/programming-with-charts/single-chart-series/)
- [Εισαγωγή Στήλης Διαγράμματος στο Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}