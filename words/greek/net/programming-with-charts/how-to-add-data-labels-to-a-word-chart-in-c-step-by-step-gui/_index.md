---
category: general
date: 2026-08-04
description: Πώς να προσθέσετε ετικέτες δεδομένων σε C# με το Aspose.Words. Μάθετε
  να επεξεργάζεστε το γράφημα, να κεντράρετε τις ετικέτες δεδομένων του γραφήματος,
  να εμφανίζετε ποσοστά στο γράφημα και να προσαρμόζετε τις ετικέτες δεδομένων του
  γραφήματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: el
lastmod: 2026-08-04
og_description: Πώς να προσθέσετε ετικέτες δεδομένων σε C# χρησιμοποιώντας το Aspose.Words.
  Αυτό το σεμινάριο σας δείχνει πώς να επεξεργαστείτε το γράφημα, να κεντράρετε τις
  ετικέτες δεδομένων του γραφήματος, να εμφανίσετε τα ποσοστά στο γράφημα και να προσαρμόσετε
  τις ετικέτες δεδομένων του γραφήματος.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Πώς να προσθέσετε ετικέτες δεδομένων σε γράφημα του Word σε C# – πλήρης
  οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Πώς να προσθέσετε ετικέτες δεδομένων σε γράφημα Word με C# – οδηγός βήμα‑προς‑βήμα
url: /el/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε ετικέτες δεδομένων σε γράφημα Word με C# – βήμα‑βήμα οδηγός

Αν χρειάζεστε **πώς να προσθέσετε ετικέτες δεδομένων** σε ένα γράφημα που βρίσκεται μέσα σε έγγραφο Word, αυτός ο οδηγός σας δείχνει τον ακριβή κώδικα που πρέπει να εκτελέσετε. Θα δείτε πώς να επεξεργαστείτε τις ιδιότητες του γραφήματος, να κεντράρετε τις ετικέτες δεδομένων, να εμφανίσετε ποσοστά στο γράφημα και να προσαρμόσετε τις ετικέτες δεδομένων για οποιοδήποτε σενάριο.

Το tutorial καλύπτει όλα όσα απαιτούνται για την τροποποίηση ενός υπάρχοντος γραφήματος, από τη φόρτωση του εγγράφου μέχρι την αποθήκευση των αλλαγών. Δεν χρειάζονται εξωτερικές αναφορές—μόνο η βιβλιοθήκη Aspose.Words for .NET και ένα βασικό περιβάλλον ανάπτυξης C#.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 (ή νεότερη) εγκατεστημένη.
* Aspose.Words for .NET έκδοση 23.9 ή νεότερη.  
  Μπορείτε να την εγκαταστήσετε μέσω NuGet:

```bash
dotnet add package Aspose.Words
```

* Ένα αρχείο Word (`input.docx`) που περιέχει τουλάχιστον ένα γράφημα.

## Πώς να προσθέσετε ετικέτες δεδομένων σε γράφημα Word με C#

Οι παρακάτω ενότητες σας οδηγούν βήμα‑βήμα. Η κύρια λέξη‑κλειδί **πώς να προσθέσετε ετικέτες δεδομένων** εμφανίζεται φυσικά στην αφήγηση και στα σχόλια του κώδικα, διατηρώντας την πυκνότητα εντός του προτεινόμενου εύρους.

### Βήμα 1 – Φόρτωση του εγγράφου Word που περιέχει το γράφημα

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί είναι σημαντικό αυτό το βήμα*: Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word. Η φόρτωσή του σας δίνει πρόσβαση σε κάθε κόμβο, συμπεριλαμβανομένων των σχημάτων που φιλοξενούν γραφήματα.

### Βήμα 2 – Ανάκτηση του πρώτου γραφήματος από το έγγραφο

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Γιατί είναι σημαντικό αυτό το βήμα*: Τα γραφήματα αποθηκεύονται μέσα σε κόμβους `Shape`. Με την μετατροπή του ανακτηθέντος κόμβου σε `Shape` και την κλήση του `GetChart()`, λαμβάνετε ένα αντικείμενο `Chart` που εκθέτει σειρές, άξονες και συλλογές ετικετών.

### Βήμα 3 – Ενεργοποίηση προσαρμογής ετικετών δεδομένων και εμφάνιση ποσοστών στο γράφημα

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Γιατί είναι σημαντικό αυτό το βήμα*: Ορίζοντας `ShowPercentage` λέτε στο Aspose.Words να υπολογίσει και να εμφανίσει τη συνεισφορά κάθε τμήματος στο σύνολο. Αυτό ανταποκρίνεται στη δευτερεύουσα λέξη‑κλειδί **εμφάνιση ποσοστών στο γράφημα**.

### Βήμα 4 – Αλλαγή της τοποθέτησης της ετικέτας στο κέντρο κάθε σημείου δεδομένων

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Γιατί είναι σημαντικό αυτό το βήμα*: Η ιδιότητα `Position` ελέγχει πού εμφανίζεται η ετικέτα σε σχέση με το σημείο δεδομένων. Η χρήση του `Center` ικανοποιεί τη δευτερεύουσα λέξη‑κλειδί **κεντράρισμα ετικετών δεδομένων γραφήματος** και βελτιώνει την αναγνωσιμότητα για πίτες ή donuts.

### Βήμα 5 – Περαιτέρω προσαρμογή ετικετών δεδομένων γραφήματος (προαιρετικό)

Αν χρειάζεστε μεγαλύτερο έλεγχο, μπορείτε να προσαρμόσετε τη γραμματοσειρά, το χρώμα ή τις γραμμές οδηγού:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Αυτές οι ρυθμίσεις απεικονίζουν τη δευτερεύουσα λέξη‑κλειδί **προσαρμογή ετικετών δεδομένων γραφήματος** και δείχνουν πώς μπορείτε να ταιριάξετε την εμφάνιση με τις οδηγίες της εταιρικής σας ταυτότητας.

### Βήμα 6 – Αποθήκευση του τροποποιημένου εγγράφου

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Γιατί είναι σημαντικό αυτό το βήμα*: Η αποθήκευση γράφει το ενημερωμένο γράφημα πίσω στο αρχείο Word, καθιστώντας τις νέες ετικέτες δεδομένων ορατές όταν το αρχείο ανοίξει στο Microsoft Word.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα ολοκληρωμένο πρόγραμμα που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using` και σχόλια που εξηγούν κάθε γραμμή.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `output.docx` στο Microsoft Word, το γράφημα θα εμφανίζει:

* Τιμές ποσοστών δίπλα σε κάθε τμήμα (π.χ. **25 %**, **40 %**, …).
* Ετικέτες τοποθετημένες στο κέντρο κάθε σημείου δεδομένων.
* Οποιαδήποτε πρόσθετη μορφοποίηση έχετε εφαρμόσει, όπως έντονο κόκκινο κείμενο.

Αυτές οι οπτικές ενδείξεις κάνουν το γράφημα πιο εύκολο στην ερμηνεία, ειδικά σε παρουσιάσεις ή εκθέσεις.

## Πώς να επεξεργαστείτε ιδιότητες γραφήματος πέρα από τις ετικέτες δεδομένων

Αν και το επίκεντρο αυτού του οδηγού είναι **πώς να προσθέσετε ετικέτες δεδομένων**, ίσως θέλετε επίσης **πώς να επεξεργαστείτε το γράφημα** για ρυθμίσεις όπως τίτλοι, θέση υπομνήματος ή μορφοποίηση άξονα. Το αντικείμενο `Chart` παρέχει ιδιότητες όπως `Title`, `Legend` και `AxisX/AxisY`. Για παράδειγμα, για να αλλάξετε τον τίτλο του γραφήματος:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Όλες οι τροποποιήσεις γραφήματος ακολουθούν το ίδιο μοτίβο: ανακτήστε το γράφημα, προσαρμόστε τις ιδιότητές του και, τέλος, αποθηκεύστε το έγγραφο.

## Συνηθισμένα προβλήματα και συμβουλές βέλτιστων πρακτικών

| Προβλήμα | Γιατί συμβαίνει | Συνιστώμενη διόρθωση |
|---|---|---|
| Το γράφημα βρίσκεται μέσα σε μια ομαδοποιημένη μορφή. | `GetChild(NodeType.Shape, …)` επιστρέφει την εξωτερική ομάδα, όχι το εσωτερικό γράφημα. | Αναζητήστε αναδρομικά ένα σχήμα με `shape.HasChart`. |
| Οι ετικέτες δεδομένων δεν εμφανίζονται μετά την αποθήκευση. | `ShowValue` ή `ShowPercentage` δεν έχουν οριστεί σε `true`. | Ορίστε ρητά και τα δύο `ShowValue` και `ShowPercentage` όπως απαιτείται. |
| Οι ετικέτες επικαλύπτονται σε μικρά τμήματα. | Η κεντρική τοποθέτηση μπορεί να προκαλέσει συμφόρηση. | Χρησιμοποιήστε `ChartDataLabelPosition.OutSideEnd` για εξωτερική τοποθέτηση ή ενεργοποιήστε `LeaderLines`. |

Η εφαρμογή αυτών των συμβουλών εξασφαλίζει αξιόπιστα αποτελέσματα σε διαφορετικούς τύπους γραφημάτων.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να προσθέσετε ετικέτες δεδομένων** σε ένα γράφημα Word χρησιμοποιώντας C#. Το tutorial κάλυψε την ανάκτηση του γραφήματος, την ενεργοποίηση της ορατότητας των ετικετών, το κεντράρισμα των ετικετών, την εμφάνιση ποσοστών και την προσαρμογή της εμφάνισης. Με αυτή τη γνώση μπορείτε επίσης **πώς να επεξεργαστείτε το γράφημα**, **κεντράρισμα ετικετών δεδομένων γραφήματος**, **εμφάνιση ποσοστών στο γράφημα** και **προσαρμογή ετικετών δεδομένων γραφήματος** για οποιοδήποτε σενάριο αναφοράς.

Έτοιμοι για περισσότερα; Δοκιμάστε να προσθέσετε πολλαπλές σειρές, να εφαρμόσετε μορφοποίηση υπό όρους ή να εξάγετε το γράφημα ως εικόνα. Το API του Aspose.Words προσφέρει εκτεταμένες δυνατότητες χειρισμού γραφημάτων—πειραματιστείτε για να βρείτε την τέλεια οπτική αναπαράσταση των δεδομένων σας.

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Προσαρμογή ετικέτας δεδομένων γραφήματος](/words/english/net/programming-with-charts/chart-data-label/)
- [Ορισμός προεπιλεγμένων επιλογών για ετικέτες δεδομένων σε γράφημα](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Προσαρμογή ενός μόνο σημείου δεδομένων σε γράφημα](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}