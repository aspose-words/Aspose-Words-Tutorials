---
category: general
date: 2026-09-11
description: Εκπαιδευτικό σεμινάριο επεξεργασίας ετικέτας διαγράμματος που δείχνει
  πώς να αλλάξετε τη θέση της ετικέτας διαγράμματος, να προσαρμόσετε την ετικέτα δεδομένων
  του διαγράμματος, να κρύψετε το όνομα κατηγορίας του διαγράμματος και να εμφανίσετε
  την τιμή της ετικέτας διαγράμματος με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: el
lastmod: 2026-09-11
og_description: Το σεμινάριο επεξεργασίας ετικέτας διαγράμματος σας καθοδηγεί στη
  αλλαγή της θέσης της ετικέτας, στην προσαρμογή της ετικέτας δεδομένων, στην απόκρυψη
  του ονόματος κατηγορίας και στην εμφάνιση της τιμής της ετικέτας χρησιμοποιώντας
  το Aspose.Words για .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Οδηγός επεξεργασίας ετικέτας διαγράμματος – προσαρμογή ετικετών διαγραμμάτων
  Word σε C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Μάθημα επεξεργασίας ετικετών γραφήματος – τροποποίηση ετικετών γραφήματος Word
  σε C#
url: /el/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εκμάθηση επεξεργασίας ετικετών διαγράμματος – τροποποίηση ετικετών διαγράμματος Word σε C#

Αν χρειάζεστε **edit chart label tutorial** για ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να αλλάξετε τη θέση της ετικέτας διαγράμματος, να προσαρμόσετε την ετικέτα δεδομένων διαγράμματος, να κρύψετε το όνομα κατηγορίας διαγράμματος και να εμφανίσετε την τιμή της ετικέτας διαγράμματος χρησιμοποιώντας το Aspose.Words for .NET. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο C#.

Η εργασία με ετικέτες διαγράμματος είναι μια συχνή απαίτηση κατά τη δημιουργία αναφορών, τιμολογίων ή ταμπλό προγραμματιστικά. Αυτό το tutorial καλύπτει κάθε βήμα—από τη φόρτωση του εγγράφου μέχρι την αποθήκευση των αλλαγών—ώστε να μπορείτε να παράγετε επαγγελματικά διαγράμματα χωρίς χειροκίνητη επεξεργασία.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο εγκατεστημένο  
* Ένα έγκυρο άδεια Aspose.Words for .NET (ή προσωρινό κλειδί αξιολόγησης)  
* Visual Studio 2022 ή οποιοδήποτε IDE συμβατό με C#  
* Ένα αρχείο Word (`Chart.docx`) που περιέχει τουλάχιστον ένα διάγραμμα  

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από το `Aspose.Words`.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή χώρων ονομάτων

Δημιουργήστε μια νέα εφαρμογή κονσόλας και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Ανοίξτε το `Program.cs` και εισάγετε τους απαιτούμενους χώρους ονομάτων:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Αυτοί οι χώροι ονομάτων σας δίνουν πρόσβαση στην κλάση `Document` για τη διαχείριση αρχείων Word και στις κλάσεις `Chart` για τη διαχείριση στοιχείων διαγράμματος.

## Βήμα 2: Φόρτωση του εγγράφου Word που περιέχει διάγραμμα

Η πρώτη ενέργεια φορτώνει το πηγαίο έγγραφο. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή όπου βρίσκεται το `Chart.docx`.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Η φόρτωση του εγγράφου δημιουργεί μια αναπαράσταση στη μνήμη που μπορείτε να περιηγηθείτε και να τροποποιήσετε.

## Βήμα 3: Ανάκτηση του πρώτου διαγράμματος στο έγγραφο

Τα διαγράμματα αποθηκεύονται ως παιδικοί κόμβοι τύπου `NodeType.Chart`. Η μέθοδος `GetChild` αναζητά στο δέντρο του εγγράφου και επιστρέφει το διάγραμμα που θέλετε να επεξεργαστείτε.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Αν το έγγραφο περιέχει πολλαπλά διαγράμματα, μπορείτε να αλλάξετε το δείκτη για να στοχεύσετε ένα διαφορετικό.

## Βήμα 4: Πρόσβαση και προσαρμογή της ετικέτας δεδομένων της πρώτης σειράς

Κάθε σειρά διαγράμματος έχει ένα αντικείμενο `DataLabel` που ελέγχει την εμφάνιση της ετικέτας. Ο κώδικας παρακάτω δείχνει τις τέσσερις βασικές προσαρμογές που απαιτούνται από τις δευτερεύουσες λέξεις-κλειδιά του tutorial.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Γιατί αυτές οι ρυθμίσεις είναι σημαντικές**

* `DataLabelPosition.Center` μετακινεί την ετικέτα από την προεπιλεγμένη θέση εκτός σημείου στη μέση του σημείου δεδομένων, κάνοντας το διάγραμμα πιο ευανάγνωστο όταν τα σημεία είναι πυκνά τοποθετημένα.  
* Ορισμός προσαρμοσμένου `Separator` σας επιτρέπει να ελέγξετε πώς συνδυάζονται το όνομα σειράς, η τιμή και άλλα μέρη.  
* Απόκρυψη του ονόματος κατηγορίας (`ShowCategoryName = false`) μειώνει το οπτικό άσκοπο όταν η κατηγορία είναι ήδη εμφανής από τον άξονα.  
* Η ενεργοποίηση του `ShowValue` εξασφαλίζει ότι η πραγματική τιμή δεδομένων είναι ορατή, κάτι που συχνά απαιτείται για οικονομικές ή στατιστικές αναφορές.

## Βήμα 5: Αποθήκευση του τροποποιημένου εγγράφου

Μετά την προσαρμογή των ιδιοτήτων της ετικέτας, αποθηκεύστε τις αλλαγές σε ένα νέο αρχείο:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Το νέο αρχείο (`CustomLabelChart.docx`) περιέχει την ίδια διάταξη διαγράμματος αλλά με την εμφάνιση ετικέτας που ορίσατε.

## Πλήρης κώδικας πηγής

Ακολουθεί το πλήρες, έτοιμο προς εκτέλεση πρόγραμμα. Αντιγράψτε το στο `Program.cs`, προσαρμόστε τις διαδρομές αρχείων και εκτελέστε το έργο.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `CustomLabelChart.docx` στο Microsoft Word. Θα πρέπει να δείτε την ετικέτα της πρώτης σειράς του διαγράμματος κεντραρισμένη σε κάθε σημείο δεδομένων, να εμφανίζει μόνο την αριθμητική τιμή και να χρησιμοποιεί το “; ” ως διαχωριστικό. Τα ονόματα κατηγοριών δεν θα εμφανίζονται πλέον δίπλα στις τιμές.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το έγγραφο δεν περιέχει διάγραμμα;** | Το παράδειγμα ελέγχει αν υπάρχει διάγραμμα `null` και εξέρχεται ήρεμα με ένα μήνυμα στην κονσόλα. |
| **Μπορώ να επεξεργαστώ ετικέτες για πολλαπλές σειρές;** | Ναι. Επανάληψη μέσω `chart.Series` και εφαρμογή των ίδιων ρυθμίσεων `DataLabel` σε κάθε `Series[i].DataLabel`. |
| **Πώς αλλάζω το στυλ γραμματοσειράς της ετικέτας;** | Χρησιμοποιήστε `label.Font` (π.χ., `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Υποστηρίζεται το `DataLabelPosition.Center` για όλους τους τύπους διαγράμματος;** | Οι περισσότεροι 2‑Δ τύποι διαγράμματος το υποστηρίζουν. Για 3‑Δ διαγράμματα, ορισμένες θέσεις μπορεί να αγνοηθούν από το Word. |
| **Χρειάζομαι άδεια για το Aspose.Words;** | Η λειτουργία αξιολόγησης λειτουργεί αλλά προσθέτει υδατογράφημα. Μια άδεια αφαιρεί το υδατογράφημα και ξεκλειδώνει πλήρη λειτουργικότητα. |

## Συμβουλές επαγγελματιών

* **Επεξεργασία κατά παρτίδες:** Τυλίξτε τη λογική φόρτωσης και αποθήκευσης σε μια μέθοδο που δέχεται διαδρομές εισόδου και εξόδου. Αυτό διευκολύνει την επεξεργασία δεκάδων εγγράφων σε βρόχο.  
* **Απόδοση:** Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` όταν τροποποιείτε πολλαπλά διαγράμματα στο ίδιο αρχείο για να αποφύγετε επαναλαμβανόμενες εισόδους/εξόδους.  
* **Δοκιμές:** Επαληθεύστε τις αλλαγές ετικετών αυτοματοποιώντας μια οπτική σύγκριση (π.χ., χρησιμοποιώντας έναν headless προβολέα Word) εάν χρειάζεται να επιβεβαιώσετε το αποτέλεσμα σε CI pipelines.  

## Επόμενα βήματα

Τώρα που μπορείτε να χειριστείτε τα βασικά του **edit chart label tutorial**, σκεφτείτε να εξερευνήσετε:

* **Αλλαγή θέσης ετικέτας διαγράμματος** για άλλες σειρές ή διαφορετικούς τύπους διαγράμματος  
* **Προσαρμογή μορφοποίησης ετικέτας δεδομένων διαγράμματος** όπως μορφές αριθμών, χρώματα γραμματοσειράς ή γεμίσματα φόντου  
* **Απόκρυψη ονόματος κατηγορίας διαγράμματος** ενώ εξακολουθεί να εμφανίζεται το όνομα σειράς για διαγράμματα πολλαπλών σειρών  
* **Εμφάνιση τιμής ετικέτας διαγράμματος** μαζί με ποσοστιαίες τιμές για διαγράμματα πίτας  

Αυτά τα θέματα ενισχύουν τον έλεγχο σας πάνω στην αισθητική των διαγραμμάτων Word και σας προετοιμάζουν για προχωρημένα σενάρια αναφορών.

---

*Καλό προγραμματισμό! Εάν βρήκατε αυτό το tutorial χρήσιμο, μοιραστείτε το με συναδέλφους ή συνεισφέρετε βελτιώσεις στο GitHub.*

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσαρμογή ετικέτας δεδομένων διαγράμματος](/words/english/net/programming-with-charts/chart-data-label/)
- [Ετικέτα δεδομένων διαγράμματος](/words/german/net/programming-with-charts/chart-data-label/)
- [Ετικέτα δεδομένων διαγράμματος](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}