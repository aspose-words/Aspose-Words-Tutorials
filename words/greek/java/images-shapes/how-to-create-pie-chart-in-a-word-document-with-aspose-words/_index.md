---
category: general
date: 2026-10-20
description: Δημιουργία διαγράμματος πίτας σε έγγραφο Word χρησιμοποιώντας το Aspose.Words
  – βήμα‑βήμα οδηγός που δείχνει πώς να ορίσετε χρώμα, να αποσπάσετε φέτα και να αποθηκεύσετε
  το έγγραφο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: el
lastmod: 2026-10-20
og_description: Δημιουργήστε διάγραμμα πίτας σε ένα έγγραφο Word με το Aspose.Words.
  Μάθετε πώς να ορίσετε χρώμα, να αποσπάσετε φέτα και να αποθηκεύσετε το έγγραφο Word
  σε ένα ενιαίο, εκτελέσιμο παράδειγμα.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Δημιουργήστε ένα διάγραμμα πίτας σε έγγραφο Word – πλήρης οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Πώς να δημιουργήσετε διάγραμμα πίτας σε έγγραφο Word με το Aspose.Words
url: /el/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε διάγραμμα πίτας σε έγγραφο Word με το Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε διάγραμμα πίτας** μέσα σε ένα αρχείο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα δείτε πώς να ορίσετε προσαρμοσμένο χρώμα, να απομονώσετε ένα τμήμα για έμφαση, και τελικά **να αποθηκεύσετε το έγγραφο Word** με το διάγραμμα ενσωματωμένο.

Η δημιουργία διαγραμμάτων προγραμματιστικά αφαιρεί τα χειροκίνητα βήματα του ανοίγματος του Word, της εισαγωγής διαγράμματος και της ρύθμισης της εμφάνισής του. Στο τέλος αυτού του tutorial θα έχετε μια πλήρη, εκτελέσιμη εφαρμογή C# console που δημιουργεί ένα διάγραμμα πίτας, το προσαρμόζει και γράφει το αποτέλεσμα στο δίσκο.

## Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερο εγκατεστημένο  
* Ένα έγκυρο άδεια Aspose.Words for .NET (ή δωρεάν κλειδί αξιολόγησης)  
* Ένα IDE όπως το Visual Studio 2022 ή το VS Code  

Δεν απαιτούνται επιπλέον πακέτα NuGet πέρα από το `Aspose.Words`.

## Πώς να δημιουργήσετε διάγραμμα πίτας σε έγγραφο Word

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document` και ενός `DocumentBuilder`. Ο builder σας δίνει πρόσβαση σε υψηλού επιπέδου δυνατότητες του Word, συμπεριλαμβανομένης της εισαγωγής διαγράμματος.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Σε αυτό το σημείο το έγγραφο περιέχει ήδη ένα βασικό διάγραμμα πίτας. Οι επόμενες ενότητες εξηγούν **πώς να απομονώσετε τμήμα**, **πώς να ορίσετε χρώμα**, και **πώς να αποθηκεύσετε το έγγραφο Word**.

## Πώς να απομονώσετε τμήμα για έμφαση

Η απομόνωση ενός τμήματος το διαχωρίζει από το υπόλοιπο της πίτας, τραβώντας το βλέμμα του αναγνώστη. Το Aspose.Words API σας επιτρέπει να καθορίσετε απόσταση απομόνωσης σε points.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Γιατί να απομονώσετε το τμήμα; Σε αναφορές που επισημαίνουν μια συγκεκριμένη κατηγορία — όπως “Κορυφαίο προϊόν πωλήσεων” — ο οπτικός διαχωρισμός κάνει το δεδομένο άμεσα αναγνωρίσιμο.

## Πώς να ορίσετε χρώμα σε τμήμα διαγράμματος

Τα προσαρμοσμένα χρώματα βελτιώνουν τη συνέπεια του brand και την αναγνωσιμότητα. Μπορείτε να αναθέσετε οποιοδήποτε `System.Drawing.Color` σε ένα συγκεκριμένο σημείο δεδομένων.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Δεν περιορίζεστε σε προκαθορισμένα χρώματα· μπορείτε να δημιουργήσετε μια τιμή `Color.FromArgb` για ακριβείς αποχρώσεις.

## Πώς να αποθηκεύσετε έγγραφο Word με το διάγραμμα

Μόλις το διάγραμμα φαίνεται όπως θέλετε, η αποθήκευση του αρχείου είναι απλή. Η μέθοδος `Document.Save` γράφει το έγγραφο στη μορφή που καθορίζετε — εδώ χρησιμοποιούμε το προεπιλεγμένο `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `PieChart.docx`. Το άνοιγμα του αρχείου στο Microsoft Word εμφανίζει ένα διάγραμμα πίτας όπου το πρώτο τμήμα είναι απομονωμένο και χρωματισμένο κόκκινο, ακριβώς όπως ορίζει ο κώδικας.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο Word με όνομα **PieChart.docx** στον φάκελο `C:\Temp`.  
* Το έγγραφο περιέχει ένα μόνο διάγραμμα πίτας, μεγέθους 400 × 300 points.  
* Το τμήμα 0 είναι μετατοπισμένο κατά 20 points και γεμισμένο με κόκκινο, ενώ τα άλλα τμήματα διατηρούν το προεπιλεγμένο χρώμα.  

Μπορείτε να επαληθεύσετε την απομόνωση και το χρώμα επιλέγοντας το διάγραμμα στο Word και εξετάζοντας τις ιδιότητες του τμήματος.

## Επαγγελματικές συμβουλές και κοινά προβλήματα

* **Pro tip:** Αν χρειάζεται να αλλάξετε τον τίτλο ή το υπόμνημα του διαγράμματος, χρησιμοποιήστε τις ιδιότητες `pieChart.Title.Text` και `pieChart.Legend` πριν το αποθηκεύσετε.  
* **Watch out for:** Η παράλειψη εκκαθάρισης των προεπιλεγμένων σημείων δεδομένων μπορεί να οδηγήσει σε επιπλέον, ανεπιθύμητα τμήματα. Πάντα καλέστε `Series[0].DataPoints.Clear()` πριν προσθέσετε τα δικά σας δεδομένα.  
* **Performance tip:** Για μεγάλα έγγραφα, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` αντί να δημιουργείτε πολλούς builders· αυτό μειώνει το φορτίο μνήμης.

## Πώς να δημιουργήσετε διάγραμμα χρησιμοποιώντας το Aspose.Words (πρόσθετο πλαίσιο)

Η μέθοδος `InsertChart` υποστηρίζει πολλούς τύπους διαγραμμάτων εκτός από τα διαγράμματα πίτας, όπως στήλης, γραμμής και περιοχής. Για να αλλάξετε σε διαφορετικό τύπο, αντικαταστήστε το `ChartType.Pie` με την επιθυμητή τιμή enum, π.χ., `ChartType.Column`. Τα υπόλοιπα βήματα προσαρμογής (απομόνωση τμημάτων, ορισμός χρωμάτων) ακολουθούν το ίδιο μοτίβο, αν και δεν εκθέτουν όλοι οι τύποι διαγραμμάτων την ιδιότητα “explosion”.

## Πώς να απομονώσετε τμήμα σε άλλους τύπους διαγραμμάτων

Μόνο τα διαγράμματα τύπου πίτας εκθέτουν τη μέθοδο `SetExplosion`. Αν προσπαθήσετε να την καλέσετε σε ένα γράφημα ράβδων, το API θα ρίξει `ArgumentException`. Σε αυτές τις περιπτώσεις, σκεφτείτε να χρησιμοποιήσετε ετικέτες δεδομένων ή callouts για να επισημάνετε μια συγκεκριμένη ράβδο.

## Πώς να ορίσετε χρώμα σε μια σειρά αντί για ένα μόνο τμήμα

Αν θέλετε κάθε τμήμα μιας σειράς να μοιράζεται το ίδιο χρώμα, κάντε βρόχο πάνω από τα σημεία δεδομένων:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Αυτή η προσέγγιση είναι χρήσιμη όταν χρειάζεστε ένα ενιαίο χρωματικό σχήμα σε πολλαπλά διαγράμματα.

## Πώς να αποθηκεύσετε έγγραφο Word σε άλλες μορφές

Το Aspose.Words μπορεί να εξάγει σε PDF, HTML και πολλές άλλες μορφές. Αλλάξτε την επέκταση αρχείου στη μέθοδο `Save` και προαιρετικά περάστε ένα αντικείμενο `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Η μηχανή απόδοσης του διαγράμματος μετατρέπει αυτόματα το διάγραμμα στη ζητούμενη μορφή, διατηρώντας τα χρώματα και τις ρυθμίσεις απομόνωσης.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε διάγραμμα πίτας** σε έγγραφο Word, να προσαρμόσετε την εμφάνισή του με **απομόνωση τμήματος** και **ορισμό χρώματος**, και τελικά να **αποθηκεύσετε το έγγραφο Word** με το διάγραμμα ενσωματωμένο. Αυτό το ολοκληρωμένο παράδειγμα σας παρέχει μια σταθερή βάση για την αυτοματοποίηση δημιουργίας αναφορών, dashboards ή οποιουδήποτε σεναρίου όπου χρειάζεται να εισαχθούν οπτικά δεδομένα προγραμματιστικά.

### Επόμενα βήματα

* Εξερευνήστε άλλους τύπους διαγραμμάτων (`ChartType.Column`, `ChartType.Line`) για να διευρύνετε το εργαλείο αναφορών σας.  
* Συνδυάστε πολλαπλά διαγράμματα σε ένα μόνο έγγραφο για να δημιουργήσετε ολοκληρωμένα dashboards.  
* Πειραματιστείτε με το `ChartDataLabel` για να εμφανίσετε ποσοστά ή τιμές απευθείας στα τμήματα.  

Αισθανθείτε ελεύθεροι να προσαρμόσετε τον κώδικα στις δικές σας πηγές δεδομένων — είτε αντλείτε τιμές από βάση δεδομένων, API ή αρχείο CSV, η ίδια ροή εργασίας του Aspose.Words ισχύει. Καλή δημιουργία διαγραμμάτων!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εκτοξευστε τμήμα διαγράμματος πίτας σε C# με Aspose.Words – Πλήρης Οδηγός](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Εισαγωγή προσαρμοσμένου διαγράμματος στήλης σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Ενημέρωση δεδομένων σειράς διαγράμματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}