---
category: general
date: 2026-09-21
description: Πώς να μορφοποιήσετε τις σειρές σε ένα γράφημα γραμμής του Word χρησιμοποιώντας
  C#. Μάθετε πώς να δημιουργήσετε ένα έγγραφο Word, να εισάγετε ένα γράφημα γραμμής
  και να εφαρμόσετε προσαρμοσμένη μορφή αριθμού.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: el
lastmod: 2026-09-21
og_description: Πώς να μορφοποιήσετε σειρές σε γράφημα γραμμής του Word χρησιμοποιώντας
  C#. Αυτό το σεμινάριο σας δείχνει πώς να δημιουργήσετε ένα έγγραφο Word, να εισάγετε
  ένα γράφημα γραμμής και να εφαρμόσετε προσαρμοσμένη μορφή αριθμού.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Πώς να μορφοποιήσετε τις σειρές σε γράφημα γραμμής του Word με C# – βήμα‑βήμα
  οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Πώς να μορφοποιήσετε τις σειρές σε ένα διάγραμμα γραμμής του Word με C#
url: /el/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μορφοποιήσετε σειρές σε γράφημα γραμμής Word με C#

Αν χρειάζεστε **πώς να μορφοποιήσετε σειρές** σε γράφημα γραμμής Word, αυτός ο οδηγός σας παρέχει μια πλήρη, έτοιμη‑για‑εκτέλεση λύση. Θα δείτε πώς να **δημιουργήσετε ένα έγγραφο Word**, **εισάγετε γράφημα γραμμής**, και **εφαρμόσετε προσαρμοσμένη μορφή αριθμού** στις τιμές Y—όλα με το Aspose.Words for .NET.

Η αυτοματοποίηση του Word γίνεται απλή μόλις κατανοήσετε το μοντέλο αντικειμένων του γραφήματος. Στο τέλος αυτού του tutorial θα έχετε ένα αρχείο Word που περιέχει ένα γράφημα γραμμής των δεδομένων των σειρών να εμφανίζονται ως ποσοστά με δύο δεκαδικά ψηφία.

## Τι θα πετύχετε

* Δημιουργία ενός κεντρικού αρχείου `.docx` προγραμματιστικά.  
* Προσθήκη γραφήματος γραμμής μεγέθους 400 × 300 points.  
* Πρόσβαση στην πρώτη σειρά δεδομένων του γραφήματος.  
* Εφαρμογή του κώδικα μορφής `#,##0.00%` ώστε οι τιμές Y να εμφανίζονται ως ποσοστά.  

Δεν απαιτούνται εξωτερικά εργαλεία πέρα από το πακέτο NuGet του Aspose.Words.

## Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερο.  
* Visual Studio 2022 (ή οποιοδήποτε IDE C#).  
* Aspose.Words for .NET 23.10 ή νεότερο – εγκατάσταση μέσω `dotnet add package Aspose.Words`.  

Ο κώδικας λειτουργεί σε Windows, Linux και macOS επειδή το Aspose.Words είναι ανεξάρτητο από πλατφόρμα.

## Δημιουργία εγγράφου Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Γιατί είναι σημαντικό*: Το `Document` είναι το σημείο εισόδου για όλες τις λειτουργίες επεξεργασίας Word. Χωρίς αυτό δεν μπορείτε να προσθέσετε παραγράφους, πίνακες ή γραφήματα.

## Εισαγωγή γραφήματος γραμμής στο έγγραφο

Ένας `DocumentBuilder` γράφει περιεχόμενο στο `Document`. Καλώντας το `InsertChart` δημιουργείται ένα σχήμα γραφήματος στην τρέχουσα σελίδα.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Γιατί είναι σημαντικό*: Το `InsertChart` επιστρέφει ένα αντικείμενο `Chart` που σας δίνει πλήρη έλεγχο πάνω στις σειρές, τους άξονες και τη μορφοποίηση. Οι παράμετροι μεγέθους εκφράζονται σε points (1 point = 1/72 inch).

## Πρόσβαση στην πρώτη σειρά δεδομένων

Κάθε γράφημα περιέχει μία ή περισσότερες `ChartSeries`. Η πρώτη σειρά βρίσκεται στο δείκτη 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Γιατί είναι σημαντικό*: Το αντικείμενο `ChartSeries` κρατά τις τιμές Y, τις τιμές X και τις επιλογές μορφοποίησης για μια μόνο γραμμή σε γράφημα γραμμής. Η τροποποίηση αυτού του αντικειμένου αλλάζει την οπτική αναπαράσταση των δεδομένων.

## Εφαρμογή προσαρμοσμένης μορφής αριθμού στη σειρά

Η ιδιότητα `FormatCode` ελέγχει πώς εμφανίζονται οι αριθμητικές τιμές. Ορίζοντάς την σε `#,##0.00%` λέτε στο Word να αντιμετωπίζει τις τιμές ως ποσοστά με δύο δεκαδικά ψηφία.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Γιατί είναι σημαντικό*: Χωρίς προσαρμοσμένη μορφή, το Word εμφανίζει ακατέργαστους δεκαδικούς αριθμούς (π.χ., `0.15`). Ο κώδικας μορφής τους μετατρέπει σε `15.00%`, κάτι που συχνά απαιτείται σε επιχειρηματικές αναφορές.

## Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Όταν ανοίξετε το `FormattedSeriesLineChart.docx` στο Microsoft Word, θα δείτε ένα γράφημα γραμμής όπου οι ετικέτες του άξονα Y εμφανίζουν `15.00%`, `30.00%`, `45.00%`, και `60.00%`. Το μέγεθος του γραφήματος ταιριάζει με τις διαστάσεις που δόθηκαν στο `InsertChart`.

### Αναμενόμενη λήψη οθόνης

> *Εικόνα: Μια σελίδα εγγράφου Word που εμφανίζει ένα γράφημα γραμμής με τιμές άξονα Y μορφοποιημένες ως ποσοστά.*  
> *(Alt text: Screenshot of a Word document showing a line chart with percentage‑formatted Y‑axis values)*

## Κοινές παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Προσαρμογή |
|-----------|------------|
| **Πολλαπλές σειρές** | Επανάληψη μέσω `chart.Series` και ορισμός `FormatCode` για κάθε σειρά. |
| **Διαφορετικός τύπος γραφήματος** | Αντικατάσταση `ChartType.Line` με `ChartType.Column`, `ChartType.Pie`, κ.λπ. |
| **Διαχωριστές ειδικές για τοπική γλώσσα** | Χρήση μορφών συμβολοσειρών που λαμβάνουν υπόψη το `CultureInfo`, π.χ., `"# ##0,00 %"` για γαλλικές τοπικές ρυθμίσεις. |
| **Δυναμική πηγή δεδομένων** | Συμπλήρωση του `series.YValues` από βάση δεδομένων ή αρχείο CSV πριν την εφαρμογή της μορφής. |

**Συμβουλή:** Εφαρμόστε πάντα τη μορφή **μετά** την προσθήκη των τιμών Y. Η αλλαγή της μορφής πρώτα και η προσθήκη των τιμών λειτουργεί επίσης, αλλά η εφαρμογή της αργότερα εγγυάται ότι η μορφή εφαρμόζεται στο τελικό σύνολο δεδομένων.

## Ανακεφαλαίωση

Τώρα ξέρετε **πώς να μορφοποιήσετε σειρές** σε γράφημα γραμμής Word χρησιμοποιώντας C#. Το tutorial κάλυψε:

* Δημιουργία εγγράφου Word (`create word document`).  
* Εισαγωγή γραφήματος γραμμής (`insert line chart`, `add chart to word`).  
* Πρόσβαση στην πρώτη σειρά του γραφήματος.  
* Εφαρμογή προσαρμοσμένης μορφής αριθμού (`apply custom number format`) για εμφάνιση ποσοστών.

## Επόμενα βήματα

* Πειραματιστείτε με διαφορετικές τιμές `ChartType` για να δείτε πώς συμπεριφέρονται άλλες οπτικοποιήσεις.  
* Προσθέστε τίτλους, ετικέτες άξονα και υπομνήματα χρησιμοποιώντας `chart.Title`, `chart.AxisX.Title` και `chart.AxisY.Title`.  
* Εξάγετε το γράφημα ως εικόνα (`chart.Save` με `SaveFormat.Png`) για χρήση σε διαδικτυακές αναφορές.

Νιώστε ελεύθεροι να προσαρμόσετε αυτό το μοτίβο για τη δημιουργία dashboards, οικονομικών αναφορών ή οποιουδήποτε εγγράφου που χρειάζεται προγραμματισμένη δημιουργία γραφημάτων. Καλό κώδικα!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}