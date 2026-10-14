---
category: general
date: 2026-10-13
description: Ορίστε τον αριθμό των κουβάδων του ιστογράμματος σε ένα γράφημα Word
  με C# και προσθέστε ετικέτες δεδομένων για να βελτιώσετε την αναγνωσιμότητα. Μάθετε
  πώς να φορτώνετε ένα έγγραφο Word με C# και να ενημερώνετε το γράφημα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set histogram bin count
- add data labels histogram
- how to update word chart
- enable chart data labels
- load word document c#
language: el
lastmod: 2026-10-13
og_description: Ορίστε τον αριθμό των κβαντών του ιστογράμματος σε ένα γράφημα Word
  χρησιμοποιώντας C# και ενεργοποιήστε τις ετικέτες δεδομένων για πιο σαφή οπτική
  παρουσίαση. Ακολουθήστε αυτό το πλήρες σεμινάριο για να φορτώσετε ένα έγγραφο Word
  με C# και να ενημερώσετε το γράφημα.
og_image_alt: Screenshot of a Word histogram chart after setting bin count and enabling
  data labels
og_title: Ορισμός αριθμού κβαντών ιστογράμματος σε γράφημα Word με C# – βήμα‑βήμα
  οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Set histogram bin count in a Word chart with C# and add data labels
    to improve readability. Learn how to load a Word document C# and update the chart.
  headline: How to set histogram bin count and add data labels in a Word chart using
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart manipulation
title: Πώς να ορίσετε τον αριθμό των κβανών του ιστογράμματος και να προσθέσετε ετικέτες
  δεδομένων σε γράφημα του Word χρησιμοποιώντας C#
url: /el/net/programming-with-charts/how-to-set-histogram-bin-count-and-add-data-labels-in-a-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε τον αριθμό των κβαντών ιστογράμματος και να προσθέσετε ετικέτες δεδομένων σε γράφημα Word χρησιμοποιώντας C#

Αν χρειάζεται να **ορίσετε τον αριθμό των κβαντών ιστογράμματος** σε ένα γράφημα Word, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με C#. Θα μάθετε επίσης πώς να **προσθέσετε ετικέτες δεδομένων στο ιστογράμμα** ώστε κάθε κβάν να εμφανίζει την τιμή του, καθιστώντας το γράφημα πιο ευανάγνωστο. Η λύση λειτουργεί με οποιοδήποτε αρχείο `.docx` που περιέχει γράφημα ιστογράμματος και χρησιμοποιεί τη βιβλιοθήκη Aspose.Words for .NET.

Η ενημέρωση ενός γραφήματος είναι μια συνηθισμένη εργασία όταν δημιουργείτε αναφορές αυτόματα. Στο τέλος αυτού του tutorial θα μπορείτε να **φορτώσετε έγγραφο Word C#**, να τροποποιήσετε τον αριθμό των κβαντών του ιστογράμματος, να ενεργοποιήσετε τις ετικέτες δεδομένων και να αποθηκεύσετε το αποτέλεσμα χωρίς χειροκίνητη επεξεργασία.

## Τι θα μάθετε

* Πώς να φορτώσετε ένα έγγραφο Word σε C# (`load word document c#`).
* Πώς να εντοπίσετε το πρώτο γράφημα ιστογράμματος μέσα στο έγγραφο (`how to update word chart`).
* Τα ακριβή βήματα για **ορισμό αριθμού κβαντών ιστογράμματος** και **ενεργοποίηση ετικετών δεδομένων γραφήματος**.
* Συμβουλές για διαχείριση πολλαπλών γραφημάτων, διαφορετικών τύπων γραφημάτων και κοινών παγίδων.

## Προαπαιτήσεις

| Απαίτηση | Γιατί είναι σημαντική |
|-------------|----------------|
| .NET 6.0 ή νεότερο | Παρέχει το runtime για το Aspose.Words. |
| Aspose.Words for .NET (v23.9 ή νεότερο) | Προσφέρει το API `Chart` που χρησιμοποιείται για την τροποποίηση γραφημάτων Word. |
| Ένα αρχείο Word (`input.docx`) που περιέχει γράφημα ιστογράμματος | Ο κώδικας λειτουργεί σε υπάρχον ιστογράμμα· μπορείτε να δημιουργήσετε ένα χειροκίνητα στο Word για δοκιμή. |
| Visual Studio 2022 (ή οποιοδήποτε IDE C#) | Καθιστά εύκολη τη μεταγλώττιση και εκτέλεση του δείγματος. |

Εγκαταστήστε το πακέτο NuGet με την παρακάτω εντολή:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Αν σκοπεύετε να επεξεργαστείτε πολλά έγγραφα, ενεργοποιήστε την άδεια χρήσης του Aspose.Words για να αφαιρέσετε τα υδατογραφήματα αξιολόγησης.

## Βήμα 1: Φορτώστε το έγγραφο Word (load word document c#)

Η πρώτη ενέργεια είναι το άνοιγμα του αρχείου `.docx` που περιέχει το ιστογράμμα. Η χρήση του `Document.Load` εξασφαλίζει ότι όλα τα τμήματα του εγγράφου, συμπεριλαμβανομένων των γραφημάτων, είναι διαθέσιμα στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Path to the source document
string inputPath = @"C:\Docs\input.docx";

// Load the Word document
Document doc = new Document(inputPath);
```

> **Γιατί είναι σημαντικό αυτό το βήμα:** Η φόρτωση του εγγράφου αποτελεί τη βάση για οποιαδήποτε τροποποίηση. Αν το αρχείο δεν μπορεί να ανοιχθεί, τα επόμενα βήματα θα αποτύχουν με `FileNotFoundException`.

## Βήμα 2: Εντοπίστε το γράφημα ιστογράμματος (how to update word chart)

Το Word αποθηκεύει τα γραφήματα ως κόμβους `Shape`. Πρέπει να βρούμε το πρώτο `Shape` και να το μετατρέψουμε σε `Chart`. Αν το έγγραφό σας περιέχει πολλαπλά γραφήματα, μπορείτε να διατρέξετε όλα τα `Shape` και να ελέγξετε το `chart.ChartType`.

```csharp
// Retrieve the first shape in the document (depth‑first search)
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Ensure the shape really is a chart
if (shape?.Chart == null)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Cast the shape to a Chart object
Chart histogramChart = shape.Chart;
```

> **Edge case:** Αν το έγγραφο δεν περιέχει γράφημα, η μέθοδος `GetChild` επιστρέφει `null`. Ο έλεγχος παραπάνω αποτρέπει το `NullReferenceException`.

## Βήμα 3: Ορίστε τον αριθμό των κβαντών ιστογράμματος (set histogram bin count)

Η οπτική λεπτομέρεια ενός ιστογράμματος ελέγχεται από την ιδιότητα `BinCount`. Ορίζοντάς την σε υψηλότερη τιμή δημιουργείτε περισσότερες στήλες, κάτι που μπορεί να αποκαλύψει πιο λεπτομερή κατανομή των δεδομένων.

```csharp
// Verify that the chart is a histogram
if (histogramChart.ChartType != ChartType.Histogram)
{
    throw new InvalidOperationException("The selected chart is not a histogram.");
}

// Set the desired number of bins (e.g., 15)
histogramChart.HistogramChart.BinCount = 15;
```

> **Γιατί το χρειάζεστε:** Η προσαρμογή του αριθμού των κβαντών σας επιτρέπει να προσαρμόσετε το γράφημα στο κοινό. Ένας μικρός αριθμός κβαντών απλοποιεί την εμφάνιση, ενώ ένας μεγαλύτερος παρέχει περισσότερες λεπτομέρειες.

## Βήμα 4: Ενεργοποιήστε τις ετικέτες δεδομένων του γραφήματος (add data labels histogram / enable chart data labels)

Οι ετικέτες δεδομένων κάνουν την τιμή κάθε κβάν ορατή απευθείας στο γράφημα. Αυτό είναι ιδιαίτερα χρήσιμο όταν το ιστογράμμα εκτυπώνεται ή εξάγεται σε PDF.

```csharp
// Turn on data labels for each bin
histogramChart.HistogramChart.ShowLabels = true;

// Optional: customize label format (e.g., show percentage)
histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";
```

> **Practical tip:** Αν προτιμάτε ποσοστά αντί για ακατέργαστους αριθμούς, ορίστε `NumberFormat = "0%"` και ενεργοποιήστε `ShowPercentage = true`.

## Βήμα 5: Αποθηκεύστε το τροποποιημένο έγγραφο

Μετά τις αλλαγές, γράψτε το έγγραφο ξανά στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να δημιουργήσετε ένα νέο.

```csharp
// Path to the output document
string outputPath = @"C:\Docs\output.docx";

// Save the updated document
doc.Save(outputPath);
```

Ανοίγοντας το `output.docx` στο Microsoft Word τώρα θα δείτε ένα ιστογράμμα με 15 κβάν και ορατές ετικέτες δεδομένων.

## Βήμα 6: Επαληθεύστε το αποτέλεσμα (expected output)

Για να βεβαιωθείτε ότι η λειτουργία ολοκληρώθηκε επιτυχώς χωρίς οπτικό έλεγχο, μπορείτε να διαβάσετε προγραμματιστικά τις ιδιότητες:

```csharp
// Reload the saved file for verification
Document verifyDoc = new Document(outputPath);
Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
```

Η κονσόλα θα πρέπει να εμφανίσει:

```
BinCount: 15
ShowLabels: True
```

Αν οι τιμές ταιριάζουν, το ιστογράμμα έχει ενημερωθεί σωστά.

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // ---------- Step 2: Locate the histogram chart ----------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape?.Chart == null)
            throw new InvalidOperationException("No chart found in the document.");

        Chart histogramChart = shape.Chart;

        // ---------- Step 3: Set histogram bin count ----------
        if (histogramChart.ChartType != ChartType.Histogram)
            throw new InvalidOperationException("The chart is not a histogram.");

        histogramChart.HistogramChart.BinCount = 15;

        // ---------- Step 4: Enable chart data labels ----------
        histogramChart.HistogramChart.ShowLabels = true;
        histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";

        // ---------- Step 5: Save the modified document ----------
        string outputPath = @"C:\Docs\output.docx";
        doc.Save(outputPath);

        // ---------- Step 6: Verify the changes ----------
        Document verifyDoc = new Document(outputPath);
        Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

        Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
        Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
    }
}
```

Τρέξτε το πρόγραμμα, έπειτα ανοίξτε το `output.docx` για να δείτε το ενημερωμένο ιστογράμμα.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το έγγραφο περιέχει περισσότερα από ένα γράφημα;** | Χρησιμοποιήστε `doc.GetChildNodes(NodeType.Shape, true)` για να λάβετε μια συλλογή, στη συνέχεια διατρέξτε και ελέγξτε το `Chart.ChartType` του καθενός. |
| **Μπορώ να αλλάξω το πλάτος του κβάν αντί για τον αριθμό;** | Ναι. Χρησιμοποιήστε `histogramChart.HistogramChart.BinWidth` για να ορίσετε σταθερό πλάτος· η ρύθμιση `BinCount` θα αγνοηθεί. |
| **Είναι το API συμβατό με .NET Core;** | Το Aspose.Words for .NET υποστηρίζει .NET Core, .NET 5+ και .NET Framework. Ο ίδιος κώδικας λειτουργεί σε όλα τα υποστηριζόμενα runtime. |
| **Πώς κρύβω το υπόμνημα μετά την προσθήκη ετικετών;** | Ορίστε `histogramChart.Legend.Visible = false;`. Αυτό διατηρεί το γράφημα καθαρό όταν οι ετικέτες ήδη μεταφέρουν τα δεδομένα. |

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **ορίσετε τον αριθμό των κβαντών ιστογράμματος** και να **προσθέσετε ετικέτες δεδομένων** σε γράφημα Word χρησιμοποιώντας C#. Φορτώνοντας το έγγραφο, εντοπίζοντας το ιστογράμμα, προσαρμόζοντας το `BinCount`, ενεργοποιώντας το `ShowLabels` και αποθηκεύοντας το αρχείο, μπορείτε να αυτοματοποιήσετε τις ενημερώσεις γραφημάτων σε οποιοδήποτε pipeline αναφορών.  

Από εδώ μπορείτε να εξερευνήσετε:

* **πώς να ενημερώσετε χρώματα και στυλ γραφήματος Word**,  
* **ενεργοποίηση ετικετών δεδομένων** για άλλους τύπους γραφημάτων (πίτα, στήλη, γραμμή),  
* Δημιουργία γραφημάτων από ακατέργαστα δεδομένα με Aspose.Words ή Aspose.Cells,  
* Ενσωμάτωση του ενημερωμένου εγγράφου σε PDF χρησιμοποιώντας Aspose.PDF.

Δοκιμάστε διαφορετικούς αριθμούς κβαντών και μορφές ετικετών για να βρείτε την οπτική ισορροπία που εξυπηρετεί καλύτερα το κοινό σας. Καλή προγραμματιστική δουλειά!  

![Word histogram after


## Τι πρέπει να μάθετε στη συνέχεια;


Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}