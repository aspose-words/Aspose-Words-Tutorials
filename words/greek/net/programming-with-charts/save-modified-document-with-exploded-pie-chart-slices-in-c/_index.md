---
category: general
date: 2026-10-13
description: 'Αποθήκευση του τροποποιημένου εγγράφου μετά την προσαρμογή ενός διαγράμματος
  πίτας: εκτόξευση φετών, αλλαγή γωνίας της πρώτης φέτας και εμφάνιση ετικετών ποσοστών
  σε C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: el
lastmod: 2026-10-13
og_description: Αποθηκεύστε το τροποποιημένο έγγραφο μετά την προσαρμογή ενός διαγράμματος
  πίτας σε C#. Μάθετε πώς να «εξερράγετε» τα κομμάτια του διαγράμματος, να αλλάξετε
  τη γωνία του πρώτου κομματιού και να εμφανίσετε ετικέτες ποσοστών.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Αποθήκευση τροποποιημένου εγγράφου με εξαπλωμένα τμήματα διαγράμματος πίτας
  – Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Αποθήκευση τροποποιημένου εγγράφου με εξαπλωμένα τμήματα διαγράμματος πίτας
  σε C#
url: /el/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση τροποποιημένου εγγράφου με εκτοξευμένα τμήματα πίτας σε C#

Αν χρειάζεται να **αποθηκεύσετε τροποποιημένο έγγραφο** μετά από προσαρμογή ενός διαγράμματος πίτας στο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα μάθετε να εκτοξεύετε τμήματα πίτας, να αλλάζετε τη γωνία του πρώτου τμήματος και να εμφανίζετε ετικέτες ποσοστών—όλα με λίγες γραμμές κώδικα C#.

Η προσαρμογή διαγραμμάτων είναι συχνή απαίτηση κατά τη δημιουργία αναφορών, τιμολογίων ή ταμπλό προγραμματιστικά. Στο τέλος αυτού του tutorial θα μπορείτε να φορτώσετε ένα αρχείο DOCX, να τροποποιήσετε την εμφάνιση του διαγράμματος και να **αποθηκεύσετε τροποποιημένο έγγραφο** έτοιμο για διανομή.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 ή νεότερο (δωρεάν δοκιμή ή αδειοδοτημένη έκδοση)
- Ένα αρχείο Word (`input.docx`) που περιέχει ένα μόνο διάγραμμα πίτας
- Visual Studio 2022 ή οποιοδήποτε IDE για C#

> **Συμβουλή:** Το πακέτο NuGet Aspose.Words προστίθεται με `dotnet add package Aspose.Words`.

## Βήμα 1: Φόρτωση του εγγράφου Word που περιέχει το διάγραμμα

Το πρώτο βήμα είναι το άνοιγμα του πηγαίου αρχείου DOCX. Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Η φόρτωση του εγγράφου σας δίνει πλήρη πρόσβαση σε κάθε κόμβο, συμπεριλαμβανομένων των σχήματος που φιλοξενούν διαγράμματα.

## Βήμα 2: Ανάκτηση του πρώτου σχήματος διαγράμματος από το έγγραφο

Τα διαγράμματα αποθηκεύονται μέσα σε κόμβους `Shape`. Μπορείτε να εντοπίσετε το πρώτο διάγραμμα με `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Αν το έγγραφο περιέχει πολλά διαγράμματα, προσαρμόστε το δείκτη (`0`) ή επαναλάβετε τη συλλογή. Αυτή η γραμμή εξασφαλίζει ότι έχετε μια αναφορά στο αντικείμενο `Chart` που θα τροποποιήσετε.

## Βήμα 3: Εκτόξευση τμημάτων διαγράμματος πίτας

Η εκτόξευση ενός τμήματος το απομακρύνει από το υπόλοιπο της πίτας, κάνοντας το διάγραμμα πιο ευανάγνωστο. Η ιδιότητα `Explode` λειτουργεί για ολόκληρη τη σειρά.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Ορίζοντας `Explode` σε `true` **εκτοξεύει τμήματα διαγράμματος πίτας** για ολόκληρη τη σειρά, κάτι χρήσιμο όταν θέλετε κάθε τμήμα να ξεχωρίζει.

## Βήμα 4: Αλλαγή γωνίας του πρώτου τμήματος

Μερικές φορές χρειάζεται το πρώτο τμήμα να ξεκινά από προσαρμοσμένη γωνία, π.χ. για να ευθυγραμμιστεί με κάποιο σχεδιαστικό πρότυπο.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

Η ιδιότητα `FirstSliceAngle` **αλλάζει την προσανατολισμό του πρώτου τμήματος**, περιστρέφοντας ολόκληρη την πίτα ώστε το πρώτο τμήμα να αρχίζει στις 30 μοίρες.

## Βήμα 5: Εμφάνιση ετικετών ποσοστών στα τμήματα πίτας

Η εμφάνιση του αριθμητικού ποσοστού κάθε τμήματος είναι συχνή απαίτηση σε αναφορές. Η σημαία `DataLabel.ShowPercentage` ενεργοποιεί τις τιμές ποσοστών.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Αυτό το βήμα **εμφανίζει ετικέτες ποσοστών** απευθείας στο διάγραμμα, καλύπτοντας επίσης την απαίτηση **display percentages pie**.

## Βήμα 6: Αποθήκευση του τροποποιημένου εγγράφου

Αφού εφαρμοστούν όλες οι προσαρμογές, αποθηκεύστε τις αλλαγές σε νέο αρχείο. Η μέθοδος `Save` γράφει το ενημερωμένο DOCX στο δίσκο.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Τώρα έχετε ένα **save modified document** που περιέχει εκτοξευμένα τμήματα πίτας, ένα περιστραμμένο πρώτο τμήμα και ορατές ετικέτες ποσοστών.

![Save modified document showing exploded pie chart](/images/pie-chart-exploded.png "Save modified document with exploded pie chart slices and percentage labels")

*Το στιγμιότυπο οθόνης απεικονίζει το τελικό αποτέλεσμα μετά την αποθήκευση του εγγράφου.*

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, ακολουθεί το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα έργο κονσόλας:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίγοντας το `output.docx` θα δείτε ένα διάγραμμα πίτας όπου:

- Κάθε τμήμα είναι ελαφρώς διαχωρισμένο (**exploded pie chart slices**)
- Το πρώτο τμήμα ξεκινά με μετατόπιση 30 μοίρες (**change first slice**)
- Κάθε τμήμα εμφανίζει τη συνεισφορά του ως ποσοστό (**show percentage labels**, **display percentages pie**)
- Το αρχείο έχει **save modified document** χωρίς να τροποποιηθεί το αρχικό.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το έγγραφο δεν έχει διάγραμμα;** | Ο κώδικας ελέγχει για `null` μετά το `GetChild`. Αν δεν υπάρχει διάγραμμα, μπορείτε είτε να προσθέσετε ένα προγραμματιστικά είτε να τερματίσετε με σαφές μήνυμα. |
| **Μπορώ να εκτοξεύσω μόνο ένα τμήμα;** | Ναι. Χρησιμοποιήστε `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` όπου `i` είναι ο δείκτης του τμήματος. |
| **Πώς αλλάζω τη μορφή της ετικέτας (π.χ. να εμφανίζεται τιμή + %);** | Ορίστε `chart.PieChart.DataLabel.ShowValue = true;` και προαιρετικά `chart.PieChart.DataLabel.ShowPercentage = true;` για συνδυασμό και των δύο. |
| **Διατηρείται το στυλ του διαγράμματος μετά την αποθήκευση;** | Το Aspose.Words διατηρεί όλα τα στυλ, συμπεριλαμβανομένων χρωμάτων και γραμματοσειρών, όταν **save modified document**. |
| **Μπορώ να επεξεργαστώ πολλαπλά διαγράμματα στο ίδιο αρχείο;** | Επανάληψη σε όλους τους κόμβους `Shape` με `NodeType.Shape` και φιλτράρισμα με `shape.HasChart`. Εφαρμόστε τα ίδια βήματα σε κάθε διάγραμμα. |

## Συμπέρασμα

Τώρα ξέρετε πώς να **save modified document** μετά από προγραμματιστική προσαρμογή ενός διαγράμματος πίτας στο Word. Ο οδηγός κάλυψε την εκτόξευση τμημάτων πίτας, την αλλαγή γωνίας του πρώτου τμήματος και την εμφάνιση ετικετών ποσοστών—ικανοποιώντας τις απαιτήσεις **show percentage labels**, **explode pie chart slices**, **display percentages pie**, και **change first slice**.

Σκεφτείτε να εξερευνήσετε:

- Προσθήκη σειρών δεδομένων δυναμικά (`chart.Series.Add(...)`)  
- Προσαρμογή θέσης υπομνήματος και τίτλων διαγράμματος  
- Μετατροπή του DOCX σε PDF διατηρώντας το στυλ του διαγράμματος  

Πειραματιστείτε με διαφορετικές γωνίες, ρυθμίσεις εκτόξευσης ή μορφές ετικετών για να ταιριάξουν στις ανάγκες των αναφορών σας. Καλή προγραμματιστική διασκέδαση!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Πώς να αποθηκεύσετε επεξεργασμένο έγγραφο σε C# με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Ενημέρωση δεδομένων σειράς διαγράμματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Εισαγωγή διαγράμματος στήλης σε έγγραφο Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}