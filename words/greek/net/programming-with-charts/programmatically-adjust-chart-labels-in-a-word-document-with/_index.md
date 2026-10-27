---
category: general
date: 2026-10-13
description: Μάθετε πώς να προσαρμόζετε προγραμματιστικά τις ετικέτες διαγραμμάτων
  σε ένα έγγραφο Word χρησιμοποιώντας C#. Αυτός ο οδηγός καλύπτει τη διαχείριση διαγραμμάτων
  με το Aspose.Words και την ευθυγράμμιση των ετικετών.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: el
lastmod: 2026-10-13
og_description: Προγραμματιστικά προσαρμόστε τις ετικέτες των γραφημάτων σε έγγραφο
  Word χρησιμοποιώντας C#. Ακολουθήστε αυτό το πλήρες σεμινάριο για να αλλάξετε τη
  θέση των ετικετών, την ευθυγράμμιση και άλλα.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Προγραμματιστική προσαρμογή ετικετών διαγραμμάτων στο Word – Οδηγός βήμα‑βήμα
  για C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Προγραμματιστική προσαρμογή ετικετών διαγράμματος σε έγγραφο Word με C#
url: /el/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προγραμματιστική προσαρμογή ετικετών διαγράμματος σε έγγραφο Word με C#

Αν χρειάζεστε να **προγραμματιστικά προσαρμόσετε τις ετικέτες των διαγραμμάτων** σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με C#. Είτε δημιουργείτε αναφορές, αυτοματοποιείτε πίνακες ελέγχου ή προσαρμόζετε πρότυπα, θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που αλλάζει τη θέση και την ευθυγράμμιση των ετικετών ενός διαγράμματος μέσα σε αρχείο .docx.

Θα μάθετε επίσης πώς να χρησιμοποιήσετε τεχνικές **Aspose.Words chart manipulation**, να διαχειριστείτε πολλαπλές σειρές και να αποφύγετε κοινά προβλήματα όταν εργάζεστε με αντικείμενα **C# chart data label**.

## Προαπαιτούμενα

* .NET 6.0 (ή νεότερο) εγκατεστημένο  
* Visual Studio 2022 (ή οποιοδήποτε IDE C#)  
* Το πακέτο NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα διάγραμμα  

Αυτά τα στοιχεία απαιτούνται για το **Word document chart example** που θα τροποποιήσουμε.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε ένα νέο έργο console και προσθέστε τις απαραίτητες δηλώσεις `using`. Αυτό προετοιμάζει το περιβάλλον για **προγραμματιστική προσαρμογή ετικετών διαγράμματος**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Γιατί αυτό το βήμα;*  
Η φόρτωση του εγγράφου σας δίνει πρόσβαση στο εσωτερικό δέντρο του **Word document chart example**, όπου τα διαγράμματα αποθηκεύονται ως κόμβοι σχήματος.

## Βήμα 2: Εντοπισμός του πρώτου σχήματος διαγράμματος

Τα διαγράμματα αποθηκεύονται ως κόμβοι `Shape`. Ο παρακάτω κώδικας ανακτά το πρώτο διάγραμμα στο έγγραφο, το οποίο είναι ο στόχος για τις προσαρμογές ετικετών μας.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Γιατί αυτό το βήμα;*  
Η μέθοδος `GetChild` αναζητά αναδρομικά (`true`) και επιστρέφει τον πρώτο κόμβο τύπου `Shape`. Η μετατροπή σε `Chart` μας επιτρέπει να δουλέψουμε με το API ειδικό για διαγράμματα.

## Βήμα 3: Πρόσβαση στην ετικέτα δεδομένων που θέλετε να τροποποιήσετε

Κάθε σειρά σε ένα διάγραμμα έχει μια συλλογή ετικετών δεδομένων. Για ένα απλό διάγραμμα, η πρώτη ετικέτα συχνά αρκεί. Ο κώδικας παρακάτω δείχνει πώς να την προσεγγίσετε.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Γιατί αυτό το βήμα;*  
Το `ChartSeries` αντιπροσωπεύει μια σειρά σημείων. Η `DataLabelCollection` περιέχει τις ετικέτες για αυτή τη σειρά, επιτρέποντας ακριβή έλεγχο της θέσης και της ευθυγράμμισης.

## Βήμα 4: Αλλαγή θέσης και ευθυγράμμισης ετικέτας

Τώρα **προγραμματιστικά προσαρμόζουμε τις ετικέτες διαγράμματος** ορίζοντας τη θέση, την οριζόντια ευθυγράμμιση και την κάθετη ευθυγράμμιση. Αυτές οι ιδιότητες αντιστοιχούν στις επιλογές που βλέπετε στη διεπαφή του Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Γιατί αυτές οι ρυθμίσεις;*  

* `OutsideEnd` τοποθετεί την ετικέτα ακριβώς έξω από το άκρο κάθε ράβδου ή στήλης, βελτιώνοντας την αναγνωσιμότητα.  
* `HorizontalAlignment.Center` διατηρεί το κείμενο κεντραρισμένο πάνω στο σημείο, ενώ `VerticalAlignment.Top` ευθυγραμμίζει το άνω άκρο της ετικέτας με το σημείο δεδομένων, αποτρέποντας την επικάλυψη με άλλα στοιχεία.

### Συμβουλή επαγγελματία
Αν ένα διάγραμμα έχει πολλαπλές σειρές, κάντε βρόχο μέσω `chart.Series` και εφαρμόστε τις ίδιες ρυθμίσεις σε κάθε `DataLabelCollection`. Αυτό εξασφαλίζει ένα συνεπές στυλ σε όλο το διάγραμμα.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Βήμα 5: Αποθήκευση του τροποποιημένου εγγράφου

Αφού προσαρμόσετε τις ετικέτες, αποθηκεύστε τις αλλαγές σε νέο αρχείο. Αυτό ολοκληρώνει τη διαδικασία **modify chart label position**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Όταν ανοίξετε το `output.docx`, θα δείτε ότι κάθε ετικέτα διαγράμματος έχει μετακινηθεί στο εξωτερικό άκρο του σημείου δεδομένων της, κεντραρισμένη οριζόντια και ευθυγραμμισμένη κατακόρυφα στην κορυφή.

## Περιπτώσεις άκρων και παραλλαγές

| Situation | What to watch for | Recommended approach |
|-----------|-------------------|----------------------|
| **Πολλαπλά διαγράμματα** στο ίδιο έγγραφο | `GetChild` επιστρέφει μόνο το πρώτο διάγραμμα. | Χρησιμοποιήστε `doc.GetChildNodes(NodeType.Shape, true)` για να επαναλάβετε όλα τα σχήματα διαγράμματος. |
| **Σειρές χωρίς ετικέτες δεδομένων** | `DataLabelCollection` μπορεί να είναι κενή. | Ελέγξτε `series.HasDataLabels` πριν προσπελάσετε τη συλλογή. |
| **Διαφορετικοί τύποι διαγραμμάτων** (pie, line, scatter) | Δεν είναι όλες οι τιμές του `DataLabelPosition` έγκυρες. | Χρησιμοποιήστε `DataLabelPosition.Auto` για διαγράμματα που αποφασίζουν αυτόματα την καλύτερη θέση. |
| **Τοπική προσαρμογή** | Οι σταθερές ευθυγράμμισης είναι ανεξάρτητες από τη γλώσσα, αλλά το κείμενο που εμφανίζεται μπορεί να χρειάζεται υποστήριξη από δεξιά προς αριστερά. | Ορίστε `dataLabel.TextDirection` εάν χρειάζεστε γλώσσες RTL. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε. Αντικαταστήστε το `YOUR_DIRECTORY` με πραγματική διαδρομή φακέλου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `output.docx` δείχνει κάθε ετικέτα διαγράμματος τοποθετημένη έξω από το σημείο δεδομένων, κεντραρισμένη οριζόντια και ευθυγραμμισμένη στην κορυφή—ακριβώς το αποτέλεσμα της **προγραμματιστικής προσαρμογής ετικετών διαγράμματος** που υλοποιήσατε.

## Συμπέρασμα

Τώρα ξέρετε πώς να **προγραμματιστικά προσαρμόσετε τις ετικέτες διαγράμματος** σε ένα έγγραφο Word χρησιμοποιώντας C#. Το σεμινάριο κάλυψε:

* Φόρτωση ενός εγγράφου με **Aspose.Words chart manipulation**  
* Πρόσβαση σε **C# chart data label**  
* Αλλαγή της **modify chart label position** και της ευθυγράμμισης  
* Αποθήκευση του αρχείου και διαχείριση κοινών περιπτώσεων άκρων  

Από εδώ μπορείτε να εξερευνήσετε πιο προχωρημένα σενάρια, όπως προσαρμογή γραμματοσειρών ετικετών, προσθήκη υπό όρους μορφοποίησης ή ενημέρωση πολλαπλών διαγραμμάτων σε μια διαδικασία παρτίδας. Πειραματιστείτε με τις διαφορετικές επιλογές `DataLabelPosition` για να βρείτε το στυλ που ταιριάζει καλύτερα στις αναφορές σας.

---

*Έτοιμοι να βελτιώσετε τη διαδικασία αυτοματοποιημένων αναφορών σας; Δοκιμάστε να προσθέσετε προσαρμοσμένες μορφές αριθμών στις ετικέτες ή να εξάγετε το διάγραμμα ως εικόνα για χρήση σε PDF.*

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}