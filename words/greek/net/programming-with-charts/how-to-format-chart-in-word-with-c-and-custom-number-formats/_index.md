---
category: general
date: 2026-10-13
description: Πώς να μορφοποιήσετε ένα γράφημα στο Word με C# εφαρμόζοντας προσαρμοσμένη
  μορφή αριθμού, όπως το νόμισμα, στους άξονες του γραφήματος. Περιλαμβάνεται παράδειγμα
  κώδικα βήμα‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: el
lastmod: 2026-10-13
og_description: Πώς να μορφοποιήσετε ένα γράφημα στο Word με C# σάς επιτρέπει να εφαρμόσετε
  προσαρμοσμένη μορφή αριθμού στους άξονες του γραφήματος, εξασφαλίζοντας ότι οι τιμές
  εμφανίζονται ως νόμισμα, ποσοστά ή οποιοδήποτε μοτίβο χρειάζεστε. Ακολουθήστε τον
  οδηγό βήμα‑προς‑βήμα.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Πώς να μορφοποιήσετε γράφημα στο Word με C# – προσαρμοσμένες μορφές αριθμών
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Πώς να μορφοποιήσετε ένα γράφημα στο Word με C# και προσαρμοσμένες μορφές αριθμών
url: /el/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μορφοποιήσετε γράφημα στο Word με C# και προσαρμοσμένες μορφές αριθμών

Η μορφοποίηση γραφήματος στο Word με C# είναι μια συχνή απαίτηση όταν χρειάζεται να παρουσιάσετε δεδομένα επαγγελματικά. Αυτός ο οδηγός σας δείχνει πώς να εφαρμόσετε μια προσαρμοσμένη μορφή αριθμού στον άξονα ενός γραφήματος χρησιμοποιώντας **Aspose.Words for .NET**, ώστε οι τιμές να εμφανίζονται ακριβώς όπως αναμένετε.

Θα μάθετε πώς να φορτώσετε ένα αρχείο DOCX, να εντοπίσετε το πρώτο γράφημα, να διαβάσετε την τρέχουσα μορφή και στη συνέχεια να ορίσετε ένα νέο μοτίβο, όπως το νόμισμα με δύο δεκαδικά. Το tutorial καλύπτει επίσης πώς να αλλάξετε τη μορφή του άξονα του γραφήματος για πρόσθετες σειρές και πώς να επαναφέρετε τη μορφή εάν χρειαστεί.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη  
* Ένα έργο Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει .NET)  
* Το πακέτο NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα γράφημα

Μπορείτε να προσθέσετε το πακέτο με την ακόλουθη εντολή:

```bash
dotnet add package Aspose.Words
```

## Πώς να μορφοποιήσετε γράφημα στο Word χρησιμοποιώντας Aspose.Words

Το παρακάτω πλήρες πρόγραμμα δείχνει κάθε βήμα που απαιτείται για να **μορφοποιήσετε** τις τιμές του άξονα του γραφήματος. Αποθηκεύστε το αρχείο ως `Program.cs` και εκτελέστε το από τη γραμμή εντολών ή το IDE σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Εξήγηση κάθε βήματος

| Βήμα | Γιατί είναι σημαντικό | Κύριος κώδικας |
|------|-----------------------|----------------|
| **Φόρτωση του εγγράφου** | Χρειάζεστε ένα αντικείμενο `Document` για να εργαστείτε με το αρχείο Word. | `new Document("input.docx")` |
| **Ανάκτηση του γραφήματος** | Τα αντικείμενα `Chart` αποθηκεύονται ως κόμβοι `Shape`; η μετατροπή τύπου σας επιτρέπει να χρησιμοποιήσετε API ειδικά για γραφήματα. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Πρόσβαση στις τιμές X** | Η μορφοποίηση του άξονα εφαρμόζεται στη συλλογή τιμών μιας σειράς δεδομένων. | `chart.ChartData.Series[0].XValues` |
| **Ανάγνωση τρέχουσας μορφής** | Η γνώση του υπάρχοντος `FormatCode` σας βοηθά να αποφασίσετε αν θα το αντικαταστήσετε ή θα το επεκτείνετε. | `xValues.FormatCode` |
| **Ορισμός προσαρμοσμένης μορφής** | Η ιδιότητα `FormatCode` δέχεται οποιοδήποτε μοτίβο συμβατό με το Excel, επιτρέποντας νόμισμα, ποσοστά, ημερομηνίες κ.λπ. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Αποθήκευση του εγγράφου** | Η αποθήκευση των αλλαγών γράφει τη νέα μορφή του άξονα πίσω στο αρχείο DOCX. | `doc.Save("output_formatted.docx")` |

Η εκτέλεση του προγράμματος δημιουργεί το `output_formatted.docx`. Ανοίξτε το στο Word και θα δείτε τις τιμές του άξονα X του γραφήματος να εμφανίζονται ως **$1,234.00**, **$2,345.00**, … αντί για απλούς αριθμούς.

## Εφαρμογή προσαρμοσμένης μορφής αριθμού στον άξονα του γραφήματος

Εάν χρειάζεται να **εφαρμόσετε προσαρμοσμένη μορφή αριθμού** στον άξονα Y ή σε πρόσθετες σειρές, η διαδικασία είναι ίδια — απλώς στοχεύστε μια διαφορετική συλλογή:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Συμβουλή:** Χρησιμοποιήστε διπλά εισαγωγικά μέσα στη συμβολοσειρά μορφής για να ενσωματώσετε κυριολεκτικούς χαρακτήρες (π.χ., `"$"` για νόμισμα). Αποφύγετε τα εισαγωγικά όπως φαίνεται παραπάνω.

## Λέξη προσαρμοσμένης μορφής αριθμού – διαχείριση της τοπικής ρύθμισης του Word

Το Word σέβεται την τοπική ρύθμιση του εγγράφου όταν ερμηνεύει μορφές αριθμών. Εάν το έγγραφο χρησιμοποιεί τοπική ρύθμιση διαφορετική από τις ΗΠΑ, ίσως χρειαστεί να προσαρμόσετε τη συμβολοσειρά μορφής:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Η δοκιμή της μορφής σε έγγραφο με γερμανικές ρυθμίσεις γλώσσας επιβεβαιώνει ότι οι τιμές εμφανίζονται ως **€ 1.234,00**.

## Πώς να ορίσετε ιδιότητες γραφήματος προγραμματιστικά

Πέρα από τη μορφοποίηση του άξονα, συχνά θέλετε να **ορίσετε** τίτλους γραφήματος, υπομνήματα ή ετικέτες δεδομένων. Εδώ είναι ένα σύντομο απόσπασμα που δείχνει πώς να ορίσετε έναν τίτλο γραφήματος μετά τη μορφοποίηση του άξονα:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Ο συνδυασμός αυτού με την προσαρμοσμένη μορφή αριθμού σας δίνει ένα πλήρως επεξεργασμένο γράφημα έτοιμο για αναφορές.

## Αλλαγή μορφής άξονα γραφήματος δυναμικά βάσει εισόδου χρήστη

Σε πραγματικές εφαρμογές μπορεί να επιτρέψετε στους χρήστες να επιλέξουν μια μορφή κατά την εκτέλεση. Η παρακάτω μέθοδος ενσωματώνει τη λογική μορφοποίησης:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Μπορείτε να καλέσετε `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` για νόμισμα ή `SetAxisFormat(chart, 0, "0%")` για ποσοστά. Αυτή η προσέγγιση διατηρεί τον κύριο κώδικά σας καθαρό και υποστηρίζει μελλοντικές επεκτάσεις.

## Ακραίες περιπτώσεις και κοινά προβλήματα

| Κατάσταση | Σε τι να προσέξετε | Προτεινόμενη λύση |
|-----------|--------------------|-------------------|
| Το έγγραφο περιέχει **κανένα γράφημα** | `GetChild` επιστρέφει `null`, προκαλώντας εξαίρεση μετατροπής τύπου. | Ελέγξτε για `null` πριν τη μετατροπή (δείτε το παράδειγμα). |
| Πολλά γραφήματα στο ίδιο έγγραφο | Ο κώδικας πάντα παίρνει το πρώτο γράφημα (`index 0`). | Κάντε επανάληψη μέσω `doc.GetChildNodes(NodeType.Shape, true)` και φιλτράρετε με `ShapeType.Chart`. |
| Σειρές **χωρίς τιμές X** (π.χ., πίτες) | Η πρόσβαση στο `XValues` μπορεί να προκαλέσει `ArgumentOutOfRangeException`. | Επιβεβαιώστε ότι το `Series[i].XValues` δεν είναι κενό πριν τη μορφοποίηση. |
| Ασυμφωνία τοπικής ρύθμισης | Το σύμβολο νομίσματος μπορεί να εμφανιστεί λανθασμένα. | Ορίστε ρητά το `xValues.FormatCode` με τα κατάλληλα σύμβολα τοπικής ρύθμισης. |

## Αναμενόμενο αποτέλεσμα

Μετά την εκτέλεση του δείγματος προγράμματος, ανοίξτε το **output_formatted.docx**. Ο άξονας X του γραφήματος πρέπει να εμφανίζει αριθμούς στην επιλεγμένη προσαρμοσμένη μορφή. Για το παράδειγμα του νομίσματος, οι ετικέτες του άξονα φαίνονται ως:

```
$1,000.00
$2,000.00
$3,000.00
```

Εάν εφαρμόσατε τη μορφή ποσοστού στις τιμές Y, οι ετικέτες του άξονα Y εμφανίζονται ως:

```
10%
20%
30%
```

## Συμπέρασμα

Αυτό το tutorial σας έδειξε **πώς να μορφοποιήσετε γράφημα** στο Word με C# εφαρμόζοντας **προσαρμοσμένη μορφή αριθμού** στις τιμές του άξονα. Τώρα έχετε ένα επαναχρησιμοποιήσιμο πρότυπο για τον ορισμό νομίσματος, ποσοστών ή οποιουδήποτε άλλου αριθμητικού μοτίβου, καθώς και οδηγίες για τη διαχείριση τοπικών ρυθμίσεων, πολλαπλών σειρών και δυναμικής εισόδου χρήστη.

Στη συνέχεια, μπορείτε να εξερευνήσετε **πώς να ορίσετε** τίτλους γραφήματος, ετικέτες δεδομένων ή ακόμη και να εξάγετε το γράφημα ως εικόνα χρησιμοποιώντας το `ChartRenderer`. Αυτά τα θέματα βασίζονται άμεσα στις έννοιες που καλύφθηκαν εδώ και θα σας βοηθήσουν να δημιουργήσετε πλήρως αυτοματοποιημένες λύσεις αναφοράς.

---

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Μορφή Αριθμού Για Άξονα Σε Γράφημα](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Μορφοποίηση Αριθμού Ετικέτας Δεδομένων Σε Γράφημα](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Μορφοποίηση Δευτερεύοντος Άξονα X και Ορισμός Μονάδων Εμφάνισης σε Χιλιάδες σε Γραμμικά Γραφήματα Word Χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}