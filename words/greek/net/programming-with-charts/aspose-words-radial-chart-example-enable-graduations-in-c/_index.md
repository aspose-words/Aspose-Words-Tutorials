---
category: general
date: 2026-10-13
description: Παράδειγμα ακτινικού διαγράμματος Aspose.Words που δείχνει πώς να ενεργοποιήσετε
  τις βαθμίσεις σε ένα ακτινικό διάγραμμα χρησιμοποιώντας C# και Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: el
lastmod: 2026-10-13
og_description: Παράδειγμα κυκλικού διαγράμματος Aspose.Words που δείχνει την ενεργοποίηση
  των διαβαθμίσεων σε κυκλικό διάγραμμα με C# και τη νεότερη βιβλιοθήκη 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Παράδειγμα κυκλικού διαγράμματος Aspose.Words – ενεργοποίηση κλιμάκων σε
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Παράδειγμα κυκλικού διαγράμματος Aspose.Words: ενεργοποίηση βαθμίδων σε C#'
url: /el/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Παράδειγμα κυκλικού διαγράμματος Aspose.Words: ενεργοποίηση κλιμάκων σε C#

Αν ψάχνετε για ένα **aspose.words radial chart example**, βρίσκεστε στο σωστό μέρος. Αυτό το tutorial σας καθοδηγεί βήμα προς βήμα για το πώς να ενεργοποιήσετε τις κλιμάκους για ένα κυκλικό διάγραμμα χρησιμοποιώντας το Aspose.Words for .NET API.

Τα κυκλικά διαγράμματα είναι χρήσιμα για την απεικόνιση κυκλικών δεδομένων όπως μετρήσεις ώρας της ημέρας ή εποχιακές τάσεις. Από προεπιλογή, οι κλιμάκοι (τα σημεία σήμανσης γύρω από τον κυκλικό άξονα) είναι κρυφά, κάτι που μπορεί να κάνει το διάγραμμα πιο δύσκολο στην ανάγνωση. Η ενεργοποίησή τους απαιτεί μια αλλαγή μίας γραμμής, αλλά πρέπει να γνωρίζετε το σωστό object model και την έκδοση που υποστηρίζει τη δυνατότητα.

Σε αυτόν τον οδηγό θα μάθετε πώς να:

* Φορτώστε ένα έγγραφο Word που περιέχει ήδη ένα κυκλικό διάγραμμα.  
* Πρόσβαση στο σχήμα του διαγράμματος μέσω του Aspose.Words chart API.  
* Ενεργοποιήστε την **graduations visibility** (διαθέσιμη από την **Aspose.Words version 24.9**).  
* Αποθηκεύστε το τροποποιημένο έγγραφο και επαληθεύστε το αποτέλεσμα.

Ο πλήρης, εκτελέσιμος κώδικας περιλαμβάνεται, ώστε να μπορείτε να τον αντιγράψετε‑επικολλήσετε σε ένα νέο έργο console και να δείτε το αποτέλεσμα αμέσως.

![Παράδειγμα κυκλικού διαγράμματος Aspose.Words με κλιμάκους](https://example.com/images/radial-chart-graduations.png "Παράδειγμα κυκλικού διαγράμματος Aspose.Words που δείχνει ενεργοποιημένες κλιμάκους")

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| .NET 6.0 or later | Το Aspose.Words for .NET 24.9+ στοχεύει στο .NET Standard 2.0 και λειτουργεί σε .NET 6+. |
| Aspose.Words for .NET **24.9** or newer | Η ιδιότητα `IsGraduationsVisible` εισήχθη στην έκδοση 24.9. Παλαιότερες εκδόσεις θα προκαλέσουν `MissingMemberException`. |
| A Word document (`RadialChart.docx`) that contains a radial chart | Το παράδειγμα τροποποιεί ένα υπάρχον διάγραμμα· η δημιουργία ενός από το μηδέν είναι ξεχωριστό θέμα. |
| A C# IDE (Visual Studio, Rider, VS Code) | Οποιοδήποτε IDE που μπορεί να μεταγλωττίσει έργα .NET θα λειτουργήσει. |
| NuGet package `Aspose.Words` | Εγκαταστήστε μέσω `dotnet add package Aspose.Words --version 24.9.0` (ή νεότερη). |

> **Pro tip:** Αν δεν μπορείτε να αναβαθμίσετε στην 24.9, μπορείτε ακόμη να τροποποιήσετε άλλες ιδιότητες του διαγράμματος, αλλά οι κλιμάκοι θα παραμείνουν κρυφά επειδή το API δεν εξέθεσε αυτή τη σημαία.

## Παράδειγμα κυκλικού διαγράμματος Aspose.Words – οδηγός βήμα‑βήμα

Οι παρακάτω ενότητες χωρίζουν τη διαδικασία σε διακριτά, εύκολα‑ακολουθήσιμα βήματα. Κάθε βήμα περιλαμβάνει τον ακριβή κώδικα που χρειάζεστε και μια σύντομη εξήγηση του *γιατί* υπάρχει το βήμα.

### Βήμα 1: Φορτώστε το έγγραφο που περιέχει ένα κυκλικό διάγραμμα

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Γιατί είναι σημαντικό:**  
`Document` είναι το σημείο εισόδου του **Aspose.Words chart API**. Φορτώνει το αρχείο DOCX στη μνήμη, δίνοντάς σας πρόσβαση σε κάθε κόμβο — παραγράφους, πίνακες και σχήματα διαγράμματος. Αν το αρχείο δεν βρεθεί, το `Document` ρίχνει `FileNotFoundException`, το οποίο θα πρέπει να διαχειριστείτε σε κώδικα παραγωγής.

### Βήμα 2: Ανακτήστε το πρώτο σχήμα διαγράμματος από το έγγραφο

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Γιατί είναι σημαντικό:**  
Τα διαγράμματα αποθηκεύονται ως κόμβοι `Shape`. Η μέθοδος `GetChild` με `NodeType.Shape` διασχίζει το DOM και επιστρέφει το πρώτο ταιριαστό σχήμα. Η μετατροπή σε `Chart` σας δίνει πρόσβαση σε ιδιότητες ειδικές για το διάγραμμα όπως `RadialChart`. Ο έλεγχος null εξασφαλίζει σαφή σφάλμα εάν το έγγραφο δεν περιέχει διάγραμμα, κάτι που είναι κοινό edge case όταν επαναχρησιμοποιούνται πρότυπα.

### Βήμα 3: Ενεργοποιήστε τις κλιμάκους στο κυκλικό διάγραμμα

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Γιατί είναι σημαντικό:**  
`IsGraduationsVisible` ελέγχει τις σημάνσεις γύρω από τον κυκλικό άξονα. Όταν οριστεί σε `true`, το διάγραμμα εμφανίζει κλιμάκους, βελτιώνοντας την αναγνωσιμότητα για χρήστες που χρειάζονται ακριβή εκτίμηση τιμών. Η ιδιότητα βρίσκεται κάτω από `RadialChart`, που είναι υποτύπος του `Chart`. Αν το δοκιμάσετε σε μη‑κυκλικό διάγραμμα (π.χ. ραβδόγραμμα), η ιδιότητα `RadialChart` θα είναι `null`, οπότε θα πρέπει να επαληθεύσετε τον τύπο διαγράμματος πρώτα σε πιο σύνθετα σενάρια.

#### Διαχείριση μη‑κυκλικών διαγραμμάτων (προαιρετικό)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Αυτό το έλεγχο καθιστά τον κώδικα ανθεκτικό όταν το πηγαίο έγγραφο μπορεί να περιέχει διαφορετικούς τύπους διαγραμμάτων.

### Βήμα 4: Αποθηκεύστε το τροποποιημένο έγγραφο

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Γιατί είναι σημαντικό:**  
Η κλήση `Save` γράφει το DOM στη μνήμη πίσω σε αρχείο .docx, αποθηκεύοντας την αλλαγή που κάνατε στο διάγραμμα. Το αρχείο εξόδου μπορεί να ανοιχτεί στο Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει DOCX. Θα δείτε το κυκλικό διάγραμμα με ορατές κλιμάκους.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να επικολλήσετε στο `Program.cs` ενός .NET console project.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `RadialChart_Graduations.docx` στο Word, το κυκλικό διάγραμμα θα εμφανίσει σημεία σήμανσης (κλιμάκους) γύρω από τον κυκλικό άξονα, παρόμοιο με το στιγμιότυπο οθόνης που εμφανίστηκε νωρίτερα. Το υπόλοιπο του διαγράμματος (σειρές δεδομένων, υπόμνημα, τίτλος) παραμένει αμετάβλητο.

## Συνηθισμένες παραλλαγές και περιπτώσεις edge case

| Κατάσταση | Λύση |
|-----------|------|
| **Older Aspose.Words version (< 24.9)** | Αναβαθμίστε στο πιο πρόσφατο πακέτο NuGet. Η ιδιότητα `IsGraduationsVisible` δεν υπάρχει σε παλαιότερες εκδόσεις. |
| **Multiple charts in the same document** | Χρησιμοποιήστε `doc.GetChild(NodeType.Shape, index, true)` με το κατάλληλο `index` ή επαναλάβετε μέσω `doc.GetChildNodes(NodeType.Shape, true)` και φιλτράρετε με `ChartType.Radial`. |
| **Chart created programmatically** | Χρησιμοποιήστε `DocumentBuilder` για να εισάγετε ένα διάγραμμα, στη συνέχεια ορίστε `RadialChart.IsGraduationsVisible` στο |

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remove a Chart Series from a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Hide Plot Area Border in a Column Chart with Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}