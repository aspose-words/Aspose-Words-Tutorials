---
category: general
date: 2026-07-26
description: Εισάγετε διάγραμμα πίτας σε έγγραφο Word χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να προσθέσετε διάγραμμα, να εκτοξεύσετε το τμήμα και να εμφανίσετε τα
  ποσοστά σε λίγα μόνο βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: el
lastmod: 2026-07-26
og_description: Εισάγετε διάγραμμα πίτας σε αρχείο Word με το Aspose.Words. Ακολουθήστε
  αυτόν τον οδηγό για να μάθετε πώς να προσθέσετε διάγραμμα, να απομονώσετε το τμήμα
  και να εμφανίσετε τα ποσοστά γρήγορα.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Εισαγωγή διαγράμματος πίτας στο Word – Βήμα-βήμα οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Εισαγωγή διαγράμματος πίτας στο Word με το Aspose.Words – Πλήρης οδηγός
url: /el/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή Διαγράμματος Πίτας σε Word με Aspose.Words – Πλήρης Οδηγός

Έχετε χρειαστεί ποτέ να **εισάγετε διάγραμμα πίτας** σε μια αναφορά Word αλλά δεν ήξερες από πού να ξεκινήσεις; Δεν είστε μόνοι. Σε πολλές επιχειρηματικές εφαρμογές η οπτική δύναμη ενός διαγράμματος πίτας κάνει τα δεδομένα άμεσα κατανοητά, και το Aspose.Words το καθιστά δυνατό με λίγες μόνο γραμμές κώδικα.

Σε αυτό το σεμινάριο θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για να **προσθέσετε διάγραμμα σε Word**, να εξαπολύσετε ένα τμήμα για έμφαση, και να εμφανίσετε τα ποσοστά στις ετικέτες δεδομένων. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

---

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί τόσο με .NET Core όσο και με .NET Framework)
- Το πακέτο NuGet Aspose.Words for .NET εγκατεστημένο  
  ```bash
  dotnet add package Aspose.Words
  ```
- Βασική κατανόηση της σύνταξης C# — δεν απαιτείται τίποτα περίπλοκο
- Ένα IDE της επιλογής σας (Visual Studio, Rider ή VS Code)

Αυτό είναι όλο. Ας βάλουμε τα χέρια μας στη δουλειά.

---

## Εισαγωγή Διαγράμματος Πίτας σε Έγγραφο Word

Το πρώτο που χρειαζόμαστε είναι ένα νέο αντικείμενο `Document` και ένα `DocumentBuilder`. Σκεφτείτε το builder ως ένα στυλό που γράφει απευθείας στον καμβά του Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Γιατί είναι σημαντικό:** Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` μας παρέχει ένα βολικό API για την εισαγωγή στοιχείων όπως διαγράμματα, πίνακες και κείμενο. Αυτό αποτελεί τη βάση για κάθε λειτουργία **πώς να προσθέσετε διάγραμμα**.

---

## Πώς να Προσθέσετε Διάγραμμα σε Word

Τώρα που έχουμε ένα builder, μπορούμε πραγματικά να **εισάγουμε διάγραμμα πίτας**. Η μέθοδος `insertChart` δέχεται τον τύπο διαγράμματος και τις επιθυμητές διαστάσεις σε points (1 point = 1/72 ίντσα).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Συμβουλή:** Αν χρειάζεστε διαφορετικό μέγεθος, απλώς προσαρμόστε τις τιμές του πλάτους και του ύψους. Το διάγραμμα θα κλιμακωθεί αυτόματα ώστε να ταιριάζει στα περιθώρια της σελίδας.

---

## Πώς να Εξαπολύσετε Τμήμα για Έμφαση

Μια κοινή οπτική βελτίωση είναι να “εξαπολύσετε” ένα τμήμα ώστε να ξεχωρίζει από τον κύκλο. Αυτό τραβά το βλέμμα του αναγνώστη στο πιο σημαντικό τμήμα.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Γιατί να εξαπολύσετε ένα τμήμα;** Όταν θέλετε να τονίσετε μια συγκεκριμένη κατηγορία — π.χ., “Κέρδη Q1” σε μια οικονομική αναφορά — η εξαπόλυση του τμήματος το κάνει άμεσα εμφανές χωρίς επιπλέον κείμενο.

---

## Πώς να Εμφανίσετε Ποσοστά στις Ετικέτες Δεδομένων

Τα περισσότερα διαγράμματα πίτας φαίνονται καλύτερα όταν κάθε τμήμα εμφανίζει το ποσοστό του. Το Aspose.Words μας επιτρέπει να το ενεργοποιήσουμε με μια μόνο ιδιότητα.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Σύντομη σημείωση:** Η σημαία `ShowPercentage` λειτουργεί για όλα τα σημεία της σειράς, έτσι δεν χρειάζεται να τη ρυθμίσετε ανά τμήμα.

---

## Αποθήκευση του Εγγράφου που Περιέχει το Διάγραμμα

Τέλος, γράφουμε το έγγραφο στο δίσκο. Επιλέξτε οποιονδήποτε φάκελο θέλετε· απλώς βεβαιωθείτε ότι η διαδρομή υπάρχει.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Όταν ανοίξετε το `PieChart.docx` στο Microsoft Word, θα δείτε ένα τέλεια αποδομένο διάγραμμα πίτας με το πρώτο τμήμα εξαπολυμένο και τα ποσοστά εμφανισμένα — ακριβώς αυτό που θα περιμένατε από μια επαγγελματική επιχειρηματική αναφορά.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες, έτοιμο για αντιγραφή‑και‑επικόλληση πρόγραμμα. Εκτελέστε το ως εφαρμογή κονσόλας και επαληθεύστε το αρχείο εξόδου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το παραγόμενο `PieChart.docx`. Θα δείτε ένα διάγραμμα πίτας τριών τμημάτων με τίτλο “Sales Q1”, με το πρώτο τμήμα απομακρυσμένο και κάθε τμήμα να έχει ετικέτα “30 %”, “45 %”, και “25 %”. Η απεικόνιση ταιριάζει με τα δεδομένα που εισάγαμε.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

- **Τι γίνεται αν χρειάζομαι περισσότερες από μία σειρές;**  
  Απλώς προσθέστε επιπλέον αντικείμενα `ChartSeries` στο `chart.Series`. Κάθε σειρά μπορεί να έχει το δικό της σύνολο δεδομένων, χρώματα και ρυθμίσεις εξαπόλυσης.

- **Μπορώ να αλλάξω τα χρώματα του διαγράμματος;**  
  Ναι. Κάθε `ChartPoint` έχει την ιδιότητα `Format.Fill.ForeColor` που μπορείτε να ορίσετε σε οποιοδήποτε `System.Drawing.Color`.

- **Τι γίνεται με διαφορετικούς τύπους διαγραμμάτων;**  
  Το enum `ChartType` περιλαμβάνει μπάρα, γραμμή, δακτύλιο (doughnut) και πολλά άλλα. Αντικαταστήστε το `ChartType.Pie` με όποιον τύπο χρειάζεστε.

- **Είναι το διάγραμμα επεξεργάσιμο στο Word μετά την εισαγωγή;**  
  Απόλυτα. Το Word αντιμετωπίζει το διάγραμμα ως εγγενές Office διάγραμμα, έτσι οι χρήστες μπορούν να το διπλοκλικάρουν για να ανοίξουν τον ενσωματωμένο επεξεργαστή διαγραμμάτων.

---

## Συμπέρασμα

Τώρα γνωρίζετε ακριβώς πώς να **εισάγετε διάγραμμα πίτας** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words, **πώς να προσθέσετε διάγραμμα σε Word**, **πώς να εξαπολύσετε τμήμα**, και **πώς να εμφανίσετε ποσοστά** στις ετικέτες δεδομένων. Το πλήρες παράδειγμα παραπάνω είναι έτοιμο για εκτέλεση, και μπορείτε να το επεκτείνετε με προσαρμοσμένα δεδομένα, στυλ ή επιπλέον σειρές.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να αντικαταστήσετε το διάγραμμα πίτας με ένα δακτύλιο (doughnut), ή δημιουργήστε μια δέσμη αναφορών με διαφορετικά σύνολα δεδομένων αυτόματα. Αν σας ενδιαφέρουν άλλες οπτικοποιήσεις, ρίξτε μια ματιά στους οδηγούς μας για **πώς να προσθέσετε διάγραμμα** για γραφήματα μπάρας και γραμμής, ή εξερευνήστε την αναφορά API **add chart to word** για πιο βαθιές προσαρμογές.

Καλή προγραμματιστική, και εύχομαι τα έγγραφά σας να είναι πάντα τόσο καθαρά όσο ένα τέλεια κομμένο κομμάτι πίτας!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή Στήλης Διαγράμματος σε Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Εισαγωγή Διαγράμματος Περιοχής σε Έγγραφο Word | Aspose.Words για .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Δημιουργία Scatter Διαγράμματος Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}