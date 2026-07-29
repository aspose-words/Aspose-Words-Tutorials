---
category: general
date: 2026-07-29
description: Πώς να επεξεργαστείτε ένα γράφημα σε έγγραφο Word—μάθετε πώς να αλλάξετε
  τη θέση της ετικέτας του γραφήματος, να προσαρμόσετε τις ετικέτες των ραβδογραφημάτων,
  να τροποποιήσετε τις ετικέτες δεδομένων του γραφήματος και να αλλάξετε τη γραμματοσειρά
  της ετικέτας.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: el
lastmod: 2026-07-29
og_description: Πώς να επεξεργαστείτε γρήγορα ένα γράφημα στο Word. Κατακτήστε την
  αλλαγή της θέσης των ετικετών του γραφήματος, τη ρύθμιση των ετικετών των ραβδογραμμάτων,
  την τροποποίηση των ετικετών δεδομένων του γραφήματος και την αλλαγή της γραμματοσειράς
  των ετικετών του γραφήματος.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Πώς να επεξεργαστείτε το διάγραμμα στο Word – Αλλαγή ετικετών & γραμματοσειράς
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Πώς να επεξεργαστείτε το γράφημα στο Word: Αλλαγή θέσης ετικέτας, γραμματοσειράς
  & περισσότερα'
url: /el/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Επεξεργαστείτε Διάγραμμα στο Word: Αλλαγή Θέσης Ετικέτας, Γραμματοσειράς & Περισσότερα

Η επεξεργασία διαγράμματος σε ένα έγγραφο Word είναι συχνή ανάγκη όταν θέλετε οι αναφορές σας να φαίνονται επαγγελματικές. Έχετε ποτέ δυσκολευτεί να **αλλάξετε τη θέση της ετικέτας του διαγράμματος** ή να κάνετε τις ετικέτες ευανάγνωστες χωρίς να ψάχνετε σε ατέλειωτα μενού; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το εμπόδιο όταν αυτοματοποιούν τη δημιουργία αναφορών. Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από ένα πλήρες, εκτελέσιμο παράδειγμα που δείχνει ακριβώς πώς να **ρυθμίσετε τις ετικέτες ράβδων διαγράμματος**, **τροποποιήσετε τις ετικέτες δεδομένων του διαγράμματος**, και **αλλάξετε τη γραμματοσειρά της ετικέτας του διαγράμματος** χρησιμοποιώντας C# και τη βιβλιοθήκη Aspose.Words.

## Τι Θα Μάθετε

- Φόρτωση ενός αρχείου .docx που ήδη περιέχει ράβδο διάγραμμα.  
- Ανάκτηση του πρώτου σχήματος διαγράμματος και πρόσβαση στη συλλογή ετικετών δεδομένων.  
- **Αλλαγή θέσης ετικέτας διαγράμματος** ώστε οι ράβδοι να φαίνονται πιο καθαροί.  
- **Ρύθμιση μεγέθους γραμματοσειράς των ετικετών ράβδων διαγράμματος** για καλύτερη αναγνωσιμότητα.  
- Αποθήκευση του τροποποιημένου εγγράφου ξανά στο δίσκο.  

Καμία εξωτερική εργαλειοθήκη, κανένα χειροκίνητο βήμα UI—απλώς καθαρός κώδικας που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET. Στο τέλος θα έχετε μια αυτόνομη λύση που μπορείτε να επαναχρησιμοποιήσετε σε δεκάδες έγγραφα.

> **Προαπαιτούμενα**  
> - .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+).  
> - Aspose.Words for .NET (διαθέσιμο μέσω NuGet).  
> - Ένα αρχείο Word (`BarChart.docx`) που ήδη περιέχει ράβδο διάγραμμα.  

Αν σας λείπει κάποιο από τα παραπάνω, κατεβάστε το τελευταίο πακέτο Aspose.Words τώρα:

```bash
dotnet add package Aspose.Words
```

---

## Πώς να Επεξεργαστείτε Διάγραμμα: Ανάκτηση του Διαγράμματος από το Έγγραφο Word

Το πρώτο βήμα στο **πώς να επεξεργαστείτε διαγράμματα** είναι η φόρτωση του εγγράφου και η εντόπιση του σχήματος διαγράμματος. Η Aspose.Words αντιμετωπίζει τα διαγράμματα ως κόμβους `Shape`, οπότε μπορούμε να χρησιμοποιήσουμε το `GetChild` με `NodeType.Shape` για να πάρουμε το πρώτο διάγραμμα που συναντάμε.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Γιατί είναι σημαντικό:**  
> Με την άμεση πρόσβαση στο αντικείμενο `Chart`, αποφεύγετε το κόστος ανοίγματος του αρχείου στο Word και της χειροκίνητης ρύθμισης κάθε ετικέτας. Αυτό αποτελεί τη βάση κάθε αυτοματοποίησης **τροποποίησης ετικετών δεδομένων διαγράμματος**.

## Ρύθμιση Ετικετών Ράβδων Διαγράμματος: Αλλαγή Θέσης Ετικέτας Διαγράμματος

Τώρα που έχουμε το στιγμιότυπο `Chart`, ας διατρέξουμε τη `DataLabelCollection` του. Στόχος είναι η **αλλαγή θέσης ετικέτας διαγράμματος** ώστε κάθε ετικέτα να τοποθετείται όμορφα μέσα στη βάση της ράβδου, αντί να αιωρείται αμήχανα πάνω της.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> Η τιμή `InsideBase` λειτουργεί καλά για κάθετες ράβδους. Αν δουλεύετε με οριζόντιο διάγραμμα, δοκιμάστε `InsideEnd`. Η δοκιμή διαφορετικών θέσεων είναι φθηνή—απλώς τρέξτε ξανά τον κώδικα και ανοίξτε το αποθηκευμένο έγγραφο.

## Αλλαγή Γραμματοσειράς Ετικέτας Διαγράμματος: Ρύθμιση Μεγέθους για Αναγνωσιμότητα

Μία μικρή γραμματοσειρά είναι ο σιωπηλός δολοφόνος της σαφήνειας των αναφορών. Για να **αλλάξετε τη γραμματοσειρά της ετικέτας διαγράμματος**, απλώς ορίστε την ιδιότητα `Font.Size` σε κάθε `ChartDataLabel`. Θα την αυξήσουμε στα 9 pt, που είναι ένα βέλτιστο μέγεθος για τις περισσότερες εκτυπωμένες αναφορές.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Γιατί το κάνουμε:**  
> Η ρύθμιση του μεγέθους γραμματοσειράς αποτελεί μέρος των βέλτιστων πρακτικών **τροποποίησης ετικετών δεδομένων διαγράμματος**. Μεγαλύτερες γραμματοσειρές βελτιώνουν την προσβασιμότητα και μειώνουν την ανάγκη για χειροκίνητη επεξεργασία μετά.

## Αποθήκευση του Ενημερωμένου Εγγράφου

Αφού προσαρμόσουμε θέσεις και γραμματοσειρές, το τελευταίο βήμα στο **πώς να επεξεργαστείτε διάγραμμα** είναι η αποθήκευση των αλλαγών. Η Aspose.Words το κάνει με μία μόνο γραμμή κώδικα.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Ανοίξτε το `BarChartCustomLabels.docx` στο Word και θα δείτε τις ετικέτες να βρίσκονται άνετα μέσα στις ράβδους, αποδομένες με καθαρή γραμματοσειρά 9 pt. Τέλος, δεν θα χρειάζεται πλέον να στρέφεστε για μικρούς αριθμούς.

---

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα σε Ένα Αρχείο)

Παρακάτω υπάρχει ένα πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα κονσόλας που δείχνει ολόκληρη τη ροή—από τη φόρτωση του εγγράφου μέχρι την αποθήκευση της ενημερωμένης έκδοσης. Αντιγράψτε‑και‑επικολλήστε το σε ένα νέο .NET project κονσόλας και πατήστε **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα** όταν τρέξετε το πρόγραμμα:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Ανοίξτε το παραγόμενο αρχείο και θα δείτε τις **ρυθμισμένες ετικέτες ράβδων διαγράμματος** τοποθετημένες μέσα στις ράβδους με άνετο μέγεθος γραμματοσειράς.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν το έγγραφο περιέχει πολλά διαγράμματα;

Ο παραπάνω κώδικας παίρνει το *πρώτο* διάγραμμα (`GetChild(NodeType.Shape, 0, true)`). Για να επεξεργαστείτε όλα τα διαγράμματα, αντικαταστήστε την ενιαία ανάκτηση με βρόχο:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Πώς να **αλλάξετε τη γραμματοσειρά ετικέτας διαγράμματος** μόνο για μια συγκεκριμένη σειρά;

Κάθε `ChartSeries` έχει τη δική του `DataLabelCollection`. Στοχεύστε μια σειρά με βάση τον δείκτη:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Λειτουργεί αυτό με διαγράμματα πίτας ή γραμμής;

Ναι—το `ChartDataLabelPosition` υποστηρίζει τιμές όπως `InsideEnd`, `OutsideEnd` και `BestFit`. Για διάγραμμα πίτας ίσως προτιμήσετε το `OutsideEnd` ώστε οι ετικέτες να είναι ευανάγνωστες.

### Τι γίνεται με τον εντοπισμό (π.χ., διαφορετικούς δεκαδικούς διαχωριστές);

Η Aspose.Words σέβεται τις ρυθμίσεις τοπικότητας του εγγράφου. Αν χρειάζεται να επιβάλετε συγκεκριμένη μορφή, προσαρμόστε το `label.NumberFormat` πριν αποθηκεύσετε.

---

## Ανακεφαλαίωση & Επόμενα Βήματα

Καλύψαμε **πώς να επεξεργαστείτε αντικείμενα διαγράμματος** σε ένα έγγραφο Word από την αρχή μέχρι το τέλος: φόρτωση του αρχείου, ανάκτηση του διαγράμματος, **αλλαγή θέσης ετικέτας διαγράμματος**, **ρύθμιση ετικετών ράβδων διαγράμματος**, **τροποποίηση ετικετών δεδομένων διαγράμματος**, και τέλος **αλλαγή γραμματοσειράς ετικέτας διαγράμματος** πριν την αποθήκευση. Το πλήρες παράδειγμα είναι έτοιμο για παραγωγή και μπορεί να ενσωματωθεί σε οποιοδήποτε pipeline αυτοματοποίησης.

Έτοιμοι για επόμενη βελτίωση; Σκεφτείτε τις παρακάτω ιδέες:

- **Προσθήκη χρωμάτων στις ετικέτες δεδομένων** (`dataLabel.Font.Color = Color.Blue;`).  
- **Εμφάνιση τιμών ως ποσοστά** (`dataLabel.NumberFormat = "0%";`).  
- **Δημιουργία διαγραμμάτων προγραμματιστικά** αντί της φόρτωσης υπαρχόντων.  

Όλα αυτά βασίζονται στην ίδια API που χρησιμοποιήσαμε σήμερα, οπότε θα νιώσετε άνετα.

Αν αντιμετωπίσατε δυσκολίες, αφήστε ένα σχόλιο παρακάτω ή ελέγξτε την τεκμηρίωση Aspose.Words για πιο προχωρημένες επιλογές προσαρμογής διαγραμμάτων. Καλό κώδικα και απολαύστε τα όμορφα ετικετοποιημένα διαγράμματα!

## Τι Πρέπει Να Μάθετε Στη Σύντομη Επόμενη

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Προσαρμογή Ετικετών Δεδομένων Διαγράμματος](/words/english/net/programming-with-charts/chart-data-label/)
- [Μορφοποίηση Αριθμού Ετικέτας Δεδομένων Σε Διάγραμμα](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Ετικέτα Δεδομένων Διαγράμματος](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}