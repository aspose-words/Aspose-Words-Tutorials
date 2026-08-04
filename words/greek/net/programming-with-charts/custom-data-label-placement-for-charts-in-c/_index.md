---
category: general
date: 2026-08-04
description: Η προσαρμοσμένη τοποθέτηση ετικετών δεδομένων για γραφήματα σε C# σάς
  επιτρέπει να κεντράρετε τις ετικέτες στα κομμάτια του γραφήματος. Ακολουθήστε αυτόν
  τον οδηγό βήμα‑προς‑βήμα χρησιμοποιώντας το API γραφημάτων Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: el
lastmod: 2026-08-04
og_description: Προσαρμοσμένη τοποθέτηση ετικετών δεδομένων για γραφήματα σε C# δείχνει
  πώς να κεντράρετε όλες τις ετικέτες δεδομένων σε κάθε φέτα ενός γραφήματος Word.
  Κατακτήστε τη θέση των ετικετών δεδομένων γραφήματος με το Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Προσαρμοσμένη τοποθέτηση ετικετών δεδομένων για γραφήματα σε C# – βήμα‑βήμα
  οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Προσαρμοσμένη τοποθέτηση ετικετών δεδομένων για διαγράμματα σε C#
url: /el/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσαρμοσμένη Τοποθέτηση Ετικετών Δεδομένων για Διαγράμματα σε C#

**Custom Data‑Label Placement for Charts** σας επιτρέπει να ελέγχετε ακριβώς πού εμφανίζεται κάθε ετικέτα σε ένα διάγραμμα μέσα σε ένα έγγραφο Word. Σε αυτό το tutorial θα μάθετε πώς να κεντράρετε όλες τις ετικέτες δεδομένων σε κάθε φέτα χρησιμοποιώντας C# και το Aspose.Words chart API.

Θα λάβετε ένα πλήρες, εκτελέσιμο παράδειγμα που φορτώνει ένα αρχείο `.docx`, προσπελάζει το πρώτο σχήμα διαγράμματος, αλλάζει το `Position` κάθε ετικέτας σε `Center` και αποθηκεύει το ενημερωμένο έγγραφο. Δεν απαιτούνται εξωτερικές αναφορές—μόνο η βιβλιοθήκη Aspose.Words for .NET και ένα βασικό περιβάλλον ανάπτυξης C#.

**Τι θα μάθετε**

* Πώς να φορτώσετε ένα έγγραφο Word που περιέχει διάγραμμα.  
* Πώς να εντοπίσετε το σχήμα του διαγράμματος με το Aspose.Words chart API.  
* Πώς να εφαρμόσετε **chart data label positioning** σε κάθε σειρά του διαγράμματος.  
* Πώς να αποθηκεύσετε το έγγραφο ώστε οι κεντραρισμένες ετικέτες να εμφανίζονται στο Word.  

**Προαπαιτούμενα**

* .NET 6.0 (ή νεότερη) εγκατεστημένη.  
* Visual Studio 2022 (ή οποιοδήποτε IDE C#).  
* Μία αναφορά στο πακέτο NuGet `Aspose.Words`.  
* Ένα αρχείο Word (`Chart.docx`) που περιέχει τουλάχιστον ένα διάγραμμα.

---

## Προσαρμοσμένη Τοποθέτηση Ετικετών Δεδομένων για Διαγράμματα – βήμα 1: φόρτωση του εγγράφου

Η πρώτη ενέργεια είναι να ανοίξετε το αρχείο Word που περιέχει το διάγραμμα. Η κλάση `Document` είναι το σημείο εισόδου για οποιαδήποτε επεξεργασία με το Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Γιατί αυτό το βήμα είναι σημαντικό*: Χωρίς τη φόρτωση του εγγράφου δεν μπορείτε να έχετε πρόσβαση στο αντικείμενο του διαγράμματος. Η επικύρωση εξασφαλίζει ότι λαμβάνετε σαφή σφάλμα εάν το αρχείο δεν περιέχει διάγραμμα, αποτρέποντας μια αναφορά null αργότερα.

---

## Χρήση του Aspose.Words chart API για πρόσβαση σε σχήματα διαγράμματος

Το Aspose.Words αντιμετωπίζει ένα διάγραμμα ως αντικείμενο `Chart` ενσωματωμένο μέσα σε ένα `Shape`. Το ανακτάτε κάνοντας cast το κατάλληλο παιδικό κόμβο.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Γιατί αυτό το βήμα είναι σημαντικό*: Η άμεση πρόσβαση στο `Chart` σας δίνει πλήρη έλεγχο πάνω στις σειρές, τα σημεία δεδομένων και τις ιδιότητες των ετικετών. Εάν το σχήμα δεν είναι διάγραμμα, ο κώδικας τερματίζει νωρίς με ένα ενημερωτικό μήνυμα.

---

## Ορισμός τοποθέτησης ετικετών δεδομένων διαγράμματος σε C#

Τώρα επαναλάβετε για κάθε σειρά και κάθε ετικέτα δεδομένων, ορίζοντας το `Position` σε `Center`. Αυτό είναι ο πυρήνας της **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Συμβουλή**: Εάν χρειάζεστε διαφορετική τοποθέτηση (π.χ., `InsideEnd` για στήλη), αλλάξτε την τιμή του enum ανάλογα. Το enum `ChartDataLabelPosition` καλύπτει όλες τις τυπικές θέσεις που υποστηρίζει το Word.

*Γιατί αυτό το βήμα είναι σημαντικό*: Η αλλαγή του `label.Position` ενημερώνει την υποκείμενη αναπαράσταση OOXML, έτσι ώστε η ετικέτα να εμφανίζεται κεντραρισμένη όταν το έγγραφο ανοίξει στο Microsoft Word.

---

## Αποθήκευση του εγγράφου Word με ενημερωμένες ετικέτες

Μετά την τροποποίηση του διαγράμματος, αποθηκεύστε τις αλλαγές σε αρχείο. Μπορείτε να αντικαταστήσετε το αρχικό ή να δημιουργήσετε νέο αντίγραφο.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Γιατί αυτό το βήμα είναι σημαντικό*: Η αποθήκευση γράφει το ενημερωμένο OOXML στο δίσκο. Ανοίγοντας το `ChartLabelsCentered.docx` στο Word θα δείτε κάθε ετικέτα φέτας κεντραρισμένη, επιβεβαιώνοντας ότι η **Custom Data‑Label Placement for Charts** ολοκληρώθηκε με επιτυχία.

---

## Περιπτώσεις άκρων και παραλλαγές

| Κατάσταση | Πώς να το αντιμετωπίσετε |
|-----------|--------------------------|
| **Πολλαπλά διαγράμματα** στο ίδιο έγγραφο | Κάντε επανάληψη με `doc.GetChildNodes(NodeType.Shape, true)` και ελέγξτε `shape.HasChart` για κάθε σχήμα. |
| **Διαφορετικοί τύποι διαγραμμάτων** (pie, doughnut, bar) | Το ίδιο `ChartDataLabelPosition.Center` λειτουργεί για διαγράμματα τύπου πίτας. Για γραμμικά/στήλες διαγράμματα μπορεί να προτιμήσετε `InsideEnd` ή `OutsideEnd`. |
| **Το κείμενο της ετικέτας χρειάζεται μορφοποίηση** | Πρόσβαση στο `label.TextProperties` για να ορίσετε μέγεθος γραμματοσειράς, χρώμα ή έντονη γραφή. |
| **Εκτέλεση σε .NET Core** | Βεβαιωθείτε ότι αναφέρεστε στην έκδοση .NET Standard του Aspose.Words· το API είναι ταυτόσημο. |

---

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή κονσόλας. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using` και διαχείριση σφαλμάτων.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα**: Ανοίξτε το `ChartLabelsCentered.docx` στο Microsoft Word. Κάθε φέτα του διαγράμματος εμφανίζει τώρα την ετικέτα δεδομένων ακριβώς στο κέντρο της φέτας, προσφέροντας πιο καθαρή οπτική εμφάνιση.

---

## Συμπέρασμα

Τώρα έχετε μια πλήρη λύση **Custom Data‑Label Placement for Charts** σε C#. Φορτώνοντας το έγγραφο, προσπελάζοντας το διάγραμμα μέσω του Aspose.Words chart API, ορίζοντας `ChartDataLabelPosition.Center` για κάθε ετικέτα και αποθηκεύοντας το αρχείο, μπορείτε να αυτοματοποιήσετε τη θέση των ετικετών για οποιοδήποτε διάγραμμα βασισμένο σε Word.

Στη συνέχεια, εξερευνήστε άλλες επιλογές **chart data label positioning** όπως `InsideEnd` ή `OutsideEnd`, ή πειραματιστείτε με **C# chart manipulation** για αλλαγή χρωμάτων, προσθήκη υπομνήματος ή δημιουργία διαγραμμάτων από το μηδέν. Αυτές οι επεκτάσεις βασίζονται άμεσα στις τεχνικές που καλύφθηκαν εδώ και επεκτείνουν τις δεξιότητές σας στην αυτοματοποίηση διαγραμμάτων σε έγγραφα Word. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Προσαρμογή Ετικέτας Δεδομένων Διαγράμματος](/words/english/net/programming-with-charts/chart-data-label/)
- [Μορφοποίηση Αριθμού Ετικετών Δεδομένων Σε Διάγραμμα](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Ετικέτα Δεδομένων Διαγράμματος](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}