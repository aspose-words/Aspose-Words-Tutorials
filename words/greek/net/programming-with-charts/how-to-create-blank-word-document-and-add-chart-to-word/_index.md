---
category: general
date: 2026-09-08
description: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε γράφημα στο Word με
  το Aspose.Words. Μάθετε πώς να εισάγετε ραδάριο γράφημα, να ενεργοποιήσετε τις κλίμακες
  και να αποθηκεύσετε το αρχείο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: el
lastmod: 2026-09-08
og_description: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε διάγραμμα στο Word
  χρησιμοποιώντας το Aspose.Words. Αυτό το σεμινάριο δείχνει πώς να εισαγάγετε διάγραμμα
  ραντάρ, να διαμορφώσετε τους άξονες και να αποθηκεύσετε το έγγραφο.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα διάγραμμα ραντάρ –
  βήμα-βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Πώς να δημιουργήσετε κενό έγγραφο Word και να προσθέσετε γράφημα στο Word
url: /el/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο Word και να προσθέσετε γράφημα στο Word

Αν χρειάζεστε να **δημιουργήσετε κενό έγγραφο Word** για μια αναφορά, πρότυπο ή αυτοματοποιημένη συγχώνευση αλληλογραφίας, αυτός ο οδηγός σας καθοδηγεί σε όλη τη διαδικασία με C# και Aspose.Words. Θα μάθετε επίσης πώς να **προσθέσετε γράφημα στο Word**, συγκεκριμένα πώς να **εισάγετε ραδάρικο γράφημα**, να ενεργοποιήσετε τις graduations, και να αποθηκεύσετε το αποτέλεσμα ως αρχείο .docx.

Αυτό το tutorial καλύπτει τα πάντα, από τη ρύθμιση του έργου μέχρι το τελικό βήμα επαλήθευσης. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο απόσπασμα κώδικα που μπορεί να ενσωματωθεί σε οποιαδήποτε εφαρμογή .NET. Δεν απαιτείται προγενέστερη εμπειρία με Aspose.Words, αλλά θα πρέπει να έχετε βασικές γνώσεις C# και ένα πρόσφατο .NET SDK εγκατεστημένο.

## Προαπαιτούμενα

- .NET 6.0 SDK ή νεότερο  
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)  
- Ένα IDE όπως το Visual Studio 2022 ή το VS Code  
- Δικαιώματα εγγραφής στο φάκελο όπου θα αποθηκευτεί το έγγραφο  

Μπορείτε να εγκαταστήσετε τη βιβλιοθήκη με την ακόλουθη εντολή:

```bash
dotnet add package Aspose.Words
```

## Βήμα 1: Δημιουργία κενού εγγράφου Word

Το πρώτο βήμα είναι να **δημιουργήσετε κενό έγγραφο Word** στη μνήμη. Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο, ενώ η `DocumentBuilder` παρέχει μια fluent API για την προσθήκη περιεχομένου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` ξεκινά κενό, έτσι έχετε έναν καθαρό καμβά για να τοποθετήσετε το γράφημα. Η διατήρηση του εγγράφου κενό σε αυτό το στάδιο καθιστά εύκολη την επαναχρησιμοποίηση του ίδιου κώδικα για διαφορετικά πρότυπα.

## Βήμα 2: Προσθήκη γραφήματος στο Word

Στη συνέχεια, **προσθέτουμε γράφημα στο Word** καλώντας το `InsertChart`. Η μέθοδος απαιτεί τον τύπο του γραφήματος και τις επιθυμητές διαστάσεις σε points (1 point = 1/72 ίντσα).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` λέει στο Aspose.Words να δημιουργήσει ένα radial chart, το οποίο είναι ιδανικό για την εμφάνιση πολυμεταβλητών δεδομένων σε κυκλική διάταξη. Οι τιμές μεγέθους (400 × 300) λειτουργούν καλά για τις περισσότερες σελίδες πορτραίτου, αλλά μπορείτε να τις προσαρμόσετε ώστε να ταιριάζουν στη διάταξή σας.

## Βήμα 3: Εισαγωγή ραδάρικου γραφήματος και διαμόρφωση των graduations

Τώρα **εισάγουμε ραδάρικο γράφημα** και ενεργοποιούμε τις graduations (ticks) και στους άξονες κατηγορίας (X) και τιμής (Y). Οι graduations βελτιώνουν την αναγνωσιμότητα δείχνοντας τις ακριβείς θέσεις για κάθε σημείο δεδομένων.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Ορίζοντας το `HasGraduations` σε `true` σχεδιάζει τα σημεία σήμανσης (tick marks) στους άξονες. Το προαιρετικό `GraduationStep` ελέγχει το διάστημα μεταξύ των ticks στον ακτινικό άξονα· ένα βήμα 10 σημαίνει tick κάθε 10 μοίρες.

### Συμβουλή επαγγελματία
Αν χρειάζεστε να εμφανίσετε ετικέτες δεδομένων, καλέστε `radarChart.Series[0].HasDataLabel = true;`. Αυτό προσθέτει την αριθμητική τιμή δίπλα σε κάθε σημείο, κάτι που είναι χρήσιμο για παρουσιάσεις.

## Βήμα 4: Συμπλήρωση του γραφήματος με δείγμα δεδομένων (προαιρετικό)

Ένα ραδάρικο γράφημα χωρίς δεδομένα είναι αόρατο. Παρακάτω υπάρχει ένας γρήγορος τρόπος για να προσθέσετε μια σειρά δειγματικών τιμών. Μπορείτε να αντικαταστήσετε αυτό το τμήμα με τη δική σας πηγή δεδομένων.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Κάθε κλήση στο `Add` εισάγει ένα σημείο στη σειρά. Η σειρά των σημείων αντιστοιχεί στις γωνιακές θέσεις γύρω από τον κύκλο.

## Βήμα 5: Αποθήκευση του εγγράφου που περιέχει το γράφημα

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Η μέθοδος `Save` γράφει αυτόματα το αρχείο .docx, διατηρώντας το γράφημα και όλη τη μορφοποίηση.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί ένα **κενό έγγραφο Word** που τώρα περιέχει ένα πλήρως λειτουργικό ραδάρικο γράφημα. Ανοίξτε το αρχείο στο Microsoft Word για να δείτε το αποτέλεσμα.

![Ραδάρικο γράφημα σε έγγραφο Word](radar_chart.png){alt="Ραδάρικο γράφημα που εισήχθη σε κενό έγγραφο Word"}

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Τι να αλλάξετε |
|-----------|----------------|
| **Διαφορετικό μέγεθος γραφήματος** | Ρυθμίστε τις παραμέτρους πλάτους/ύψους του `InsertChart`. |
| **Άλλοι τύποι γραφήματος** | Αντικαταστήστε το `ChartType.Radar` με `ChartType.Column`, `ChartType.Pie`, κ.λπ., και διατηρήστε την ίδια λογική των graduations. |
| **Αποθήκευση σε ροή** | Χρησιμοποιήστε `document.Save(Stream, SaveFormat.Docx)` |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή διαγράμματος περιοχής σε έγγραφο Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Δημιουργία διαγράμματος scatter σε Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Εισαγωγή διαγράμματος στήλης σε Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}