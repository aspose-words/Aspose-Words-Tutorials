---
category: general
date: 2026-09-21
description: Πώς να δημιουργήσετε ιστόγραμμα στο Word με το Aspose.Words. Μάθετε πώς
  να ορίζετε τα διαστήματα του ιστογράμματος και να τα διαμορφώνετε για ακριβή οπτικοποίηση
  δεδομένων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: el
lastmod: 2026-09-21
og_description: Πώς να δημιουργήσετε ιστόγραμμα στο Word με το Aspose.Words. Αυτό
  το σεμινάριο σας δείχνει πώς να ορίσετε τα bins του ιστογράμματος και να τα διαμορφώσετε
  για ακριβή διαγράμματα.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: Δημιουργήστε ένα ιστόγραμμα στο Word με το Aspose.Words – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: Πώς να δημιουργήσετε ιστόγραμμα στο Word με το Aspose.Words
url: /el/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ιστόγραμμα στο Word με Aspose.Words

Αν χρειάζεστε να δημιουργήσετε ένα ιστόγραμμα στο Word, το Aspose.Words κάνει τη διαδικασία απλή. Αυτός ο οδηγός σας καθοδηγεί βήμα‑βήμα, από τη ρύθμιση του έργου μέχρι τη διαμόρφωση των κουβάδων του ιστογράμματος για σαφή παρουσίαση των δεδομένων. Θα δείτε επίσης πώς να ορίσετε τους κουβάδες του ιστογράμματος και να τους διαμορφώσετε ώστε να ταιριάζουν με τις απαιτήσεις αναφοράς σας.

## Πώς να δημιουργήσετε ιστόγραμμα στο Word – συνολική ροή εργασίας

Η συνολική ροή εργασίας αποτελείται από τέσσερις λογικές φάσεις:

1. Προετοιμάστε το περιβάλλον ανάπτυξης.  
2. Δημιουργήστε ένα κενό έγγραφο Word και αποκτήστε ένα `DocumentBuilder`.  
3. Εισάγετε ένα γράφημα ιστόγραμμα και προσαρμόστε τις ιδιότητές του.  
4. Αποθηκεύστε το έγγραφο και επαληθεύστε το αποτέλεσμα.

Κάθε φάση καλύπτεται λεπτομερώς παρακάτω, και ο πλήρης κώδικας πηγής παρέχεται στο τέλος του άρθρου.

## Ρύθμιση του περιβάλλοντος ανάπτυξης

Πριν γράψετε οποιονδήποτε κώδικα, βεβαιωθείτε ότι διαθέτετε τα παρακάτω προαπαιτούμενα:

| Προαπαιτούμενο | Λόγος |
|----------------|-------|
| .NET 6.0 ή νεότερο | Παρέχει το runtime για έργα C#. |
| Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει .NET) | Σας επιτρέπει να μεταγλωττίσετε και να εντοπίσετε σφάλματα του δείγματος. |
| Πακέτο NuGet Aspose.Words για .NET | Παρέχει τις κλάσεις `Document`, `DocumentBuilder` και τα γραφήματα. |

Μπορείτε να προσθέσετε το πακέτο Aspose.Words με το NuGet CLI:

```bash
dotnet add package Aspose.Words
```

> **Συμβουλή:** Χρησιμοποιήστε μια σταθερή έκδοση (π.χ., `23.9.0`) στην παραγωγή για να αποφύγετε απροσδόκητες αλλαγές που σπάζουν.

## Εισαγωγή γραφήματος ιστόγραμμα

Με το περιβάλλον έτοιμο, δημιουργήστε ένα νέο έργο κονσόλας και ανοίξτε το αρχείο `Program.cs`. Οι πρώτες δύο γραμμές κώδικα δημιουργούν ένα κενό έγγραφο και ένα `DocumentBuilder` που σας επιτρέπει να χειριστείτε το έγγραφο:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Στη συνέχεια, καλέστε το `InsertChart` για να προσθέσετε ένα ιστόγραμμα. Η μέθοδος απαιτεί τον τύπο γραφήματος, το πλάτος και το ύψος σε points:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

Σε αυτό το σημείο το έγγραφο περιέχει έναν κενό χώρο κράτησης για ιστόγραμμα. Όταν ανοίξετε το παραγόμενο αρχείο *.docx*, θα δείτε μια γκρι περιοχή γραφήματος έτοιμη για δεδομένα.

![Histogram placeholder in Word document](/images/histogram-placeholder.png){: .img-fluid alt="Στιγμιότυπο οθόνης ενός εγγράφου Word που εμφανίζει έναν χώρο κράτησης γραφήματος ιστόγραμμα δημιουργημένο με Aspose.Words"}

## Πώς να ορίσετε τους κουβάδες του ιστογράμματος

Ένα ιστόγραμμα οπτικοποιεί την κατανομή αριθμητικών δεδομένων ομαδοποιώντας τις τιμές σε *κουβάδες*. Η ιδιότητα `HistogramBins` ελέγχει πόσες κουβάδες εμφανίζει το γράφημα. Ορίζοντας αυτήν την ιδιότητα πριν προσθέσετε δεδομένα, εξασφαλίζετε ότι το γράφημα διατηρεί τον σωστό αριθμό ράβδων.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

Μπορείτε να προσαρμόσετε τον αριθμό των κουβάδων ώστε να ταιριάζει με την λεπτομέρεια του συνόλου δεδομένων σας. Για παράδειγμα, ένα σύνολο δεδομένων από 0 έως 100 με αριθμό κουβάδων 10 δημιουργεί διαστήματα των 10 μονάδων το καθένα (0‑9, 10‑19, …, 90‑100).

> **Γιατί είναι σημαντικό:** Η επιλογή πολύ λίγων κουβάδων μπορεί να κρύψει σημαντικά μοτίβα, ενώ πολύ πολλοί κουβάδες μπορεί να δημιουργήσουν θορυβώδες γράφημα. Δοκιμάστε μερικές τιμές για να βρείτε το ιδανικό σημείο για τα συγκεκριμένα σας δεδομένα.

## Διαμόρφωση των κουβάδων του ιστογράμματος για καλύτερη αναγνωσιμότητα

Πέρα από τον αριθμό των κουβάδων, συχνά θέλετε να επισημάνετε κάθε κουβά ώστε οι αναγνώστες να βλέπουν τον ακριβή αριθμό. Η ιδιότητα `ShowBinLabels` εναλλάσσει την ορατότητα αυτών των ετικετών:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

Όταν η `ShowBinLabels` ορίζεται σε `true`, το Word εμφανίζει μια αριθμητική ετικέτα πάνω από κάθε ράβδο. Αυτό το μικρό βήμα διαμόρφωσης βελτιώνει σημαντικά την ερμηνευσιμότητα του γραφήματος, ειδικά σε αναφορές όπου το κοινό μπορεί να μην διαθέτει το αρχικό σύνολο δεδομένων.

Μπορείτε επίσης να προσαρμόσετε την εμφάνιση της ετικέτας, όπως το μέγεθος γραμματοσειράς ή το χρώμα, μέσω του αντικειμένου `HistogramLabel` (διαθέσιμο σε μεταγενέστερες εκδόσεις του Aspose.Words). Το παρακάτω απόσπασμα δείχνει μια κοινή προσαρμογή:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **Ακραία περίπτωση:** Εάν ορίσετε το `HistogramBins` σε τιμή μεγαλύτερη από τον αριθμό των διακριτών σημείων δεδομένων, ορισμένες κουβάδες θα εμφανιστούν κενές. Το γράφημα θα εξακολουθεί να αποδίδεται σωστά, αλλά η οπτική εντύπωση μπορεί να φαίνεται αραιή. Σκεφτείτε να μειώσετε τον αριθμό των κουβάδων σε τέτοιες περιπτώσεις.

## Προσθήκη σειράς δεδομένων στο ιστόγραμμα

Ένα ιστόγραμμα απαιτεί μια μόνο σειρά δεδομένων που αντιπροσωπεύει τις υποκείμενες αριθμητικές τιμές. Μπορείτε να γεμίσετε τη σειρά χρησιμοποιώντας έναν πίνακα, μια `List<double>` ή οποιαδήποτε συλλογή που μπορεί να επαναληφθεί. Παρακάτω υπάρχει ένα σύντομο παράδειγμα που προσθέτει ένα τυχαίο σύνολο δεδομένων:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

Η μέθοδος `AddRange` μετατρέπει κάθε τιμή σε κουβά σύμφωνα με το προηγουμένως ορισμένο `HistogramBins`. Μετά από αυτό το βήμα, το γράφημα εμφανίζει ένα πλήρως γεμάτο ιστόγραμμα.

## Αποθήκευση και προβολή του τελικού εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιαδήποτε τοποθεσία στην οποία η εφαρμογή σας έχει πρόσβαση. Η παρακάτω γραμμή αποθηκεύει το αρχείο ως `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

Ανοίξτε το `output.docx` στο Microsoft Word για να δείτε ένα ιστόγραμμα με δέκα κουβάδες, επισημασμένες τιμές, και τα δείγματα δεδομένων που παρείχατε. Το γράφημα θα μοιάζει με την εικόνα παρακάτω:

![Completed histogram in Word](/images/histogram-complete.png){: .img-fluid alt="Έγγραφο Word που εμφανίζει ένα ολοκληρωμένο γράφημα ιστόγραμμα με δέκα κουβάδες και ετικέτες"}

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα μέρη, εδώ είναι ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `output.docx` εμφανίζει ένα ιστόγραμμα με δέκα ομοιόμορφα κατανεμημένες ράβδους, η κάθε μία επισημασμένη με τον αριθμό της. Το γράφημα αντανακλά την κατανομή του πίνακα `data`, κάνοντας τις τάσεις άμεσα ορατές.

## Συχνές ερωτήσεις και αντιμετώπιση προβλημάτων

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν χρειάζομαι περισσότερες από μία σειρές δεδομένων;* | Τα ιστόγραμμα συνήθως αντιπροσωπεύουν μία μόνο κατανομή. Εάν χρειάζεστε πολλαπλές σειρές, σκεφτείτε να χρησιμοποιήσετε ένα γράφημα στήλης αντίγερμα. |
| *Μπορώ να αλλάξω το μέγεθος του γραφήματος μετά την εισαγωγή;* | Ναι. Προσαρμόστε τις ιδιότητες `histogram.Width` και `histogram.Height`, ή καλέστε ξανά το `builder.InsertChart` με διαφορετικές διαστάσεις. |
| *Λειτουργεί αυτό με .NET Framework 4.8;* | Απόλυτα. Το Aspose.Words υποστηρίζει .NET Framework 4.5 και μεταγενέστερα, οπότε ο ίδιος κώδικας εκτελείται αμετάβλητος. |
| *Πώς μπορώ να εξάγω το γράφημα ως εικόνα;* | Χρησιμοποιήστε το `histogram.ToImage()` για να λάβετε ένα `System.Drawing.Image`, στη συνέχεια αποθηκεύστε το με `image.Save("chart.png")`. |

## Συμπέρασμα

Τώρα ξέρετε πώς να δημιουργήσετε ιστόγραμμα στο Word χρησιμοποιώντας το Aspose.Words, πώς να ορίσετε τους κουβάδες του ιστογράμματος και πώς να τους διαμορφώσετε για καθαρή, επισημασμένη έξοδο. Το πλήρες παράδειγμα δείχνει μια έτοιμη για παραγωγή προσέγγιση που μπορείτε να προσαρμόσετε σε οποιοδήποτε σενάριο αναφοράς βασισμένο σε δεδομένα.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **πώς να δημιουργήσετε πίτες γραφήματα στο Word**, **προσαρμογή χρωμάτων γραφήματος**, και **ενσωμάτωση πηγών δεδομένων Excel**. Κάθε ένα από αυτά βασίζεται στην ίδια ροή εργασίας `DocumentBuilder`, ώστε να μπορείτε να επεκτείνετε τη λύση με ελάχιστη προσπάθεια.

Καλή δημιουργία γραφημάτων!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε γράφημα στήλης χρησιμοποιώντας το Aspose.Words για Java](/words/english/java/document-conversion-and-export/using-charts/)
- [πώς να δημιουργήσετε pdf από Word – Πλήρης οδηγός C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Πώς να φορτώσετε έγγραφα Word χρησιμοποιώντας το Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}