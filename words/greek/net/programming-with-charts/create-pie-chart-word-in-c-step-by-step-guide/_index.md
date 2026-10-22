---
category: general
date: 2026-08-07
description: Δημιουργήστε γρήγορα διάγραμμα πίτας σε C#. Μάθετε πώς να εισάγετε διάγραμμα
  πίτας, να προσθέτετε ετικέτες δεδομένων στη πίτα, να εμφανίζετε το ποσοστό στο διάγραμμα
  και να προσαρμόζετε τις ετικέτες δεδομένων του διαγράμματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: el
lastmod: 2026-08-07
og_description: Δημιουργήστε διάγραμμα πίτας σε Word με C# χρησιμοποιώντας το Aspose.Words.
  Αυτό το σεμινάριο δείχνει πώς να εισάγετε διάγραμμα πίτας, να προσθέσετε ετικέτες
  δεδομένων στο διάγραμμα πίτας και να εμφανίσετε το ποσοστό του διαγράμματος, ενώ
  προσαρμόζετε τις ετικέτες δεδομένων του διαγράμματος.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Δημιουργία διαγράμματος πίτας σε C# – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Δημιουργία λέξης διαγράμματος πίτας σε C# – οδηγός βήμα‑βήμα
url: /el/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία διαγράμματος πίτας σε Word με C# – οδηγός βήμα‑βήμα

Αν χρειάζεστε να **create pie chart word** έγγραφα σε C#, αυτός ο οδηγός παρέχει μια πλήρη, έτοιμη προς εκτέλεση λύση. Θα δείτε πώς να **insert pie chart**, **add data labels pie**, και **show percentage chart** ενώ **customize chart data labels** για ένα επαγγελματικό αποτέλεσμα.

Η δημιουργία διαγραμμάτων προγραμματιστικά σας εξοικονομεί το χειροκίνητο επεξεργαστικό έργο, ειδικά όταν οι αναφορές ή τα ταμπλό πρέπει να παραχθούν αυτόματα. Στις παρακάτω ενότητες θα μάθετε όλα όσα απαιτούνται για την ενσωμάτωση ενός πλήρως επισημασμένου διαγράμματος πίτας σε αρχείο Word χρησιμοποιώντας το Aspose.Words για .NET.

## Προαπαιτούμενα και ρύθμιση

* .NET 6.0 SDK ή νεότερο εγκατεστημένο.  
* Ένα έγκυρο άδεια Aspose.Words για .NET (ή προσωρινό κλειδί αξιολόγησης).  
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#).  

Προσθέστε το πακέτο NuGet Aspose.Words στο έργο σας:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Αν σκοπεύετε να δημιουργήσετε πολλά διαγράμματα, ενεργοποιήστε τη λειτουργία **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) για καλύτερη απόδοση.

## Δημιουργία διαγράμματος πίτας σε Word με Aspose.Words

Το πρώτο σημαντικό βήμα είναι η δημιουργία ενός κεννού εγγράφου Word και ενός `DocumentBuilder`. Αυτό το αντικείμενο καθοδηγεί όλες τις επόμενες εισαγωγές.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό*: `Document` αντιπροσωπεύει ολόκληρο το αρχείο `.docx`, ενώ `DocumentBuilder` παρέχει μια fluent API για την προσθήκη παραγράφων, πινάκων και διαγραμμάτων. Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζετε ότι δεν υπάρχει κρυφή μορφοποίηση που θα επηρεάσει τη διάταξη του διαγράμματος.

## Εισαγωγή διαγράμματος πίτας στο έγγραφο

Τώρα τοποθετούμε ένα διάγραμμα πίτας με το επιθυμητό μέγεθος. Η μέθοδος `InsertChart` επιστρέφει ένα αντικείμενο `Chart` που μπορούμε να διαμορφώσουμε περαιτέρω.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Γιατί είναι σημαντικό*: Η σημαία `ChartType.Pie` λέει στο Aspose.Words να δημιουργήσει ένα κυκλικό διάγραμμα. Το πλάτος (`400`) και το ύψος (`300`) εκφράζονται σε points, παρέχοντάς σας ακριβή έλεγχο του οπτικού αποτυπώματος.

## Συμπλήρωση του διαγράμματος με δεδομένα

Ένα διάγραμμα πίτας χρειάζεται τουλάχιστον μία σειρά αριθμητικών τιμών. Εδώ προσθέτουμε τρεις κατηγορίες: “Apples”, “Bananas” και “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Γιατί είναι σημαντικό*: Κάθε κλήση `AddCategory` δημιουργεί ένα τμήμα. Η αριθμητική τιμή καθορίζει το μέγεθος του τμήματος, ενώ η ετικέτα γίνεται το όνομα της κατηγορίας που εμφανίζεται όταν ενεργοποιηθούν οι ετικέτες δεδομένων.

## Προσθήκη ετικετών δεδομένων στο διάγραμμα πίτας και εμφάνιση ποσοστών

Για να γίνει το διάγραμμα ενημερωτικό, ενεργοποιούμε τις ετικέτες δεδομένων, τις τοποθετούμε έξω από τα τμήματα και ζητάμε από το Aspose.Words να εμφανίσει τόσο το όνομα της κατηγορίας όσο και το ποσοστό.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Γιατί είναι σημαντικό*: Ο ορισμός του `Position` σε `OutsideEnd` βελτιώνει την αναγνωσιμότητα, ειδικά όταν τα τμήματα είναι μικρά. Η ενεργοποίηση των `ShowCategoryName` και `ShowPercentage` ικανοποιεί την απαίτηση **show percentage chart** και εκπληρώνει τον στόχο **add data labels pie**.

## Προσαρμογή ετικετών διαγράμματος περαιτέρω (προαιρετικό)

Μπορεί να θέλετε να αλλάξετε τη γραμματοσειρά, να προσθέσετε γραμμή οδηγό ή να κρύψετε το υπόμνημα. Το παρακάτω απόσπασμα δείχνει κοινές προσαρμογές:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Γιατί είναι σημαντικό*: Η προσαρμογή της εμφάνισης της ετικέτας εξασφαλίζει ότι το διάγραμμα ταιριάζει με το στυλ του εγγράφου σας. Η αφαίρεση του υπομνήματος μειώνει το οπτικό άσπασμα όταν οι ετικέτες δεδομένων ήδη μεταφέρουν την ίδια πληροφορία.

## Αποθήκευση του εγγράφου με το προσαρμοσμένο διάγραμμα

Τέλος, γράψτε το έγγραφο στο δίσκο. Επιλέξτε μια διαδρομή στην οποία έχετε δικαίωμα εγγραφής.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Όταν ανοίξετε το `ChartWithCustomLabels.docx` στο Microsoft Word, θα δείτε ένα διάγραμμα πίτας όπου κάθε τμήμα είναι επισημασμένο με το όνομα της κατηγορίας και το ποσοστό του, τοποθετημένο έξω από το τμήμα, και μορφοποιημένο με τις προσαρμοσμένες ρυθμίσεις γραμματοσειράς.

### Αναμενόμενο αποτέλεσμα

| Τμήμα   | Τιμή | Ποσοστό | Ετικέτα που εμφανίζεται στο Word |
|---------|------|----------|-----------------------------------|
| Apples  | 40    | 40 %       | Apples – 40 %       |
| Bananas | 35    | 35 %       | Bananas – 35 %      |
| Cherries| 25    | 25 %       | Cherries – 25 %     |

Το διάγραμμα θα πρέπει να μοιάζει με την παρακάτω εικονογράφηση:

![Έγγραφο Word που εμφανίζει διάγραμμα πίτας με ετικέτες ποσοστών έξω από κάθε τμήμα](pie-chart-word.png "Παράδειγμα δημιουργίας διαγράμματος πίτας σε Word")

*Το κείμενο alt της εικόνας περιλαμβάνει τη βασική λέξη-κλειδί για SEO.*

## Διαχείριση πολλαπλών σειρών και ειδικών περιπτώσεων

Το βασικό παράδειγμα χρησιμοποιεί μία μόνο σειρά, κάτι τυπικό για διάγραμμα πίτας. Αν χρειάζεται να εμφανίσετε πολλαπλές σειρές (π.χ., σύγκριση δύο ετών), πρέπει να:

1. Κλήση `chart.Series.Add()` για κάθε επιπλέον σειρά.  
2. Βεβαιωθείτε ότι κάθε σειρά χρησιμοποιεί τις ίδιες κατηγορίες· διαφορετικά, το Aspose.Words θα ρίξει `ArgumentException`.  
3. Προαιρετικά, ορίστε `labels.ShowSeriesName = true` για να διαφοροποιήσετε τα τμήματα.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Όταν υπάρχουν πολλαπλές σειρές, το διάγραμμα αποδίδεται αυτόματα ως **clustered pie** (επίσης γνωστό ως “pie of pies”). Ελέγξτε το αποτέλεσμα για να βεβαιωθείτε ότι οι ετικέτες παραμένουν αναγνώσιμες.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Οι ετικέτες επικαλύπτουν τα τμήματα | Μικρή περιοχή διαγράμματος ή πολλές κατηγορίες | Αυξήστε τις διαστάσεις του διαγράμματος (`InsertChart(width, height)`) ή αλλάξτε το `Position` σε `InsideEnd`. |
| Τα ποσοστά δεν αθροίζουν στο 100 % | Σφάλματα στρογγυλοποίησης στα δεδομένα | Χρησιμοποιήστε `labels.ShowPercentage = true` (το Aspose.Words κανονικοποιεί αυτόματα). |
| Το διάγραμμα εμφανίζεται κενό στο Word | Λείπει άδεια ή λήξη χρόνου αξιολόγησης | Βεβαιωθείτε ότι φορτώνεται έγκυρη άδεια Aspose.Words πριν τη δημιουργία του εγγράφου. |
| Τα χρώματα γραμματοσειράς διαφέρουν από το θέμα του Word | Προσαρμοσμένη γραμματοσειρά ορισμένη στον κώδικα | Αφαιρέστε τις προσαρμοσμένες ρυθμίσεις γραμματοσειράς ή ταιριάξτε τα χρώματα του θέματος του Word (`System.Drawing.Color.Black`). |

## Πλήρης κώδικας (εκτελέσιμος)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `ChartWithCustomLabels.docx`, το οποίο περιέχει ένα παράδειγμα **create pie chart word** που καλύπτει όλες τις απαιτήσεις που αναφέρονται στον οδηγό.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create pie chart word** έγγραφα σε C# χρησιμοποιώντας το Aspose.Words. Ο οδηγός κάλυψε την εισαγωγή διαγράμματος πίτας, **add data labels pie**, **show percentage chart**, και **customize chart data labels** για να επιτύχετε ένα επαγγελματικό, δεδομενο‑προσανατολισμένο αρχείο Word.  

Από εδώ μπορείτε να εξερευνήσετε συναφή θέματα όπως **insert pie chart** σε υπάρχουσες παραγράφους, δημιουργία διαγραμμάτων **bar** ή **line**, ή αυτοματοποίηση μαζικής δημιουργίας αναφορών με διαφορετικά σύνολα δεδομένων. Πειραματιστείτε με διαφορετικές θέσεις ετικετών, στυλ γραμματοσειράς και ρυθμίσεις πολλαπλών σειρών για να προσαρμόσετε το αποτέλεσμα στις συγκεκριμένες ανάγκες αναφοράς σας.

Καλές δημιουργίες διαγραμμάτων!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσαρμογή ετικέτας δεδομένων διαγράμματος](/words/english/net/programming-with-charts/chart-data-label/)
- [Ορισμός προεπιλεγμένων επιλογών για ετικέτες δεδομένων σε διάγραμμα](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Εισαγωγή διαγράμματος στήλης σε έγγραφο Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}