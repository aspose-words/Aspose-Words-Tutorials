---
category: general
date: 2026-07-19
description: Αποσπάστε φέτα διαγράμματος πίτας χρησιμοποιώντας το Aspose.Words για
  C#. Μάθετε πώς να αποσπάσετε τη φέτα της πίτας, να ρυθμίσετε το μέγεθος της τρύπας
  του δακτυλίου και να αλλάξετε γρήγορα τα σημεία δεδομένων του διαγράμματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: el
lastmod: 2026-07-19
og_description: Αναπτύξτε τμήμα διαγράμματος πίτας με το Aspose.Words για C#. Αυτός
  ο οδηγός σας δείχνει πώς να αποσπάσετε τμήμα πίτας, να ρυθμίσετε το μέγεθος της
  τρύπας του δακτυλίου και να αλλάξετε αποδοτικά τα σημεία δεδομένων του διαγράμματος.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Αποσπασμός του τμήματος του διαγράμματος πίτας σε C# – Εκπαιδευτικό Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Αποσπασμένη Φέτα Διαγράμματος Πίτας σε C# με Aspose.Words – Πλήρης Οδηγός
url: /el/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εκρήγνυμε το Τμήμα Πίτας σε C# με Aspose.Words – Πλήρης Οδηγός

Σας έχει αναρωτηθεί ποτέ πώς να **εκρήγνυτε τμήμα πίτας** σε ένα έγγραφο Word χρησιμοποιώντας C#; Δεν είστε ο μόνος. Είτε προετοιμάζετε μια παρουσίαση πωλήσεων είτε οπτικοποιείτε αποτελέσματα έρευνας, ένα εκραγμένο τμήμα μπορεί να τραβήξει τα βλέμματα ακριβώς εκεί που θέλετε. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — φόρτωση εγγράφου, ανάκτηση του διαγράμματος, εκρήγνυση του πρώτου τμήματος, ρύθμιση της τρύπας του δακτυλίου και ακόμη αλλαγή των σημείων δεδομένων του διαγράμματος.

Θα προσθέσουμε επίσης τις δευτερεύουσες έννοιες που ίσως ψάχνετε: **πώς να εκρήγνυτε τμήμα πίτας**, **προσαρμογή μεγέθους τρύπας δακτυλίου**, και **αλλαγή σημείων δεδομένων διαγράμματος**. Χωρίς περιττές πληροφορίες, μόνο μια πλήρης, έτοιμη για αντιγραφή λύση.

---

## Τι Θα Χρειαστείτε

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- **Aspose.Words for .NET** (η πιο πρόσφατη έκδοση μέχρι 2026‑07‑19). Μπορείτε να το κατεβάσετε από το NuGet με `Install-Package Aspose.Words`.
- Ένα έργο **.NET 6+** (ή .NET Framework 4.7.2+ αν χρησιμοποιείτε παλαιότερο).
- Ένα αρχείο Word (`Chart.docx`) που περιέχει ήδη ένα διάγραμμα πίτας ή δακτυλίου. Αν δεν το έχετε, δημιουργήστε γρήγορα ένα διάγραμμα στο Word και αποθηκεύστε το.

Αυτό είναι όλο — χωρίς επιπλέον βιβλιοθήκες, χωρίς COM interop, μόνο καθαρός διαχειριζόμενος κώδικας.

---

## Εκρήγνυμε το Τμήμα Πίτας – Υλοποίηση Βήμα‑Βήμα

Παρακάτω χωρίζουμε την εργασία σε μικρά βήματα. Κάθε ενότητα έχει σαφή επικεφαλίδα, απόσπασμα κώδικα και σύντομη εξήγηση του *γιατί* κάνουμε ό,τι κάνουμε.

### Βήμα 1: Εγκατάσταση και Αναφορά του Aspose.Words

Πρώτα απ' όλα, προσθέστε το πακέτο Aspose.Words στο έργο σας. Στο Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Pro tip:** Αν χρησιμοποιείτε το ενσωματωμένο UI του NuGet στο Visual Studio, αναζητήστε το “Aspose.Words” και πατήστε Install. Αυτό εξασφαλίζει ότι θα έχετε τις τελευταίες διορθώσεις σφαλμάτων και τη δυνατότητα εργασίας με διαγράμματα αμέσως.

### Βήμα 2: Φόρτωση του Εγγράφου Word που Περιέχει το Διάγραμμα

Χρειαζόμαστε ένα αντικείμενο `Document` που δείχνει στο `.docx` με το διάγραμμα που θέλετε να τροποποιήσετε.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Γιατί είναι σημαντικό:** Το `Document` είναι το σημείο εισόδου για κάθε λειτουργία στο Aspose.Words. Ελέγχοντας για διαγράμματα νωρίς, αποφεύγουμε μια αναφορά σε null αργότερα όταν προσπαθούμε να εκρήγνυμε ένα τμήμα.

### Βήμα 3: Ανάκτηση του Πρώτου Κόμβου Διαγράμματος

Οι περισσότερες παραδείγματα υποθέτουν ένα μόνο διάγραμμα, οπότε θα πάρουμε το πρώτο. Αν έχετε πολλά διαγράμματα, προσαρμόστε το δείκτη ανάλογα.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Σημείωση:** Η μετατροπή σε `Chart` είναι ασφαλής αφού επιβεβαιώσαμε ότι υπάρχει διάγραμμα. Αυτό το αντικείμενο μας δίνει πρόσβαση σε σειρές, σημεία δεδομένων και ρυθμίσεις ειδικές για τον τύπο διαγράμματος.

### Βήμα 4: Εκρήγνυση του Πρώτου Τμήματος μιας Πίτας

Τώρα το αστέρι της παράστασης — **πώς να εκρήγνυτε τμήμα πίτας**. Θα ορίσουμε την ιδιότητα `Exploded` του πρώτου σημείου δεδομένων.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Γιατί λειτουργεί:** Η `Exploded` λέει στο Word να απομακρύνει αυτό το τμήμα από το κέντρο, δημιουργώντας το κλασικό “exploded pie” εφέ. Η ιδιότητα είναι boolean, οπότε το `true` κάνει τη δουλειά.

### Βήμα 5: Ρύθμιση του Μεγέθους της Τρύπας του Δακτυλίου (Αν είναι Δακτύλιος)

Αν το διάγραμμά σας είναι δακτύλιος, ίσως θέλετε να **ρυθμίσετε το μέγεθος της τρύπας του δακτυλίου**. Το μέγεθος της τρύπας είναι ποσοστό της ακτίνας του διαγράμματος.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Τι σημαίνει ο αριθμός:** Μια τιμή `30` σημαίνει ότι ο εσωτερικός κύκλος θα καταλαμβάνει το 30 % της συνολικής ακτίνας, αφήνοντας ένα πιο παχύ εξωτερικό δαχτυλίδι.

### Βήμα 6: Αλλαγή Σημείων Δεδομένων του Διαγράμματος (Προαιρετικό)

Μερικές φορές χρειάζεται να **αλλάξετε σημεία δεδομένων διαγράμματος** — ίσως έχετε ενημερώσει τους αριθμούς και θέλετε το οπτικό να αντανακλά αυτό.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Γιατί το κάνετε:** Η αλλαγή της τιμής ενός σημείου δεδομένων επανυπολογίζει αυτόματα τα ποσοστά των τμημάτων, διατηρώντας το διάγραμμα ακριβές χωρίς χειροκίνητη επεξεργασία στο Word.

### Βήμα 7: Αποθήκευση του Τροποποιημένου Εγγράφου

Τέλος, γράψτε τις αλλαγές στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να δημιουργήσετε νέο — όπως προτιμάτε.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Συμβουλή:** Χρησιμοποιήστε `SaveFormat.Docx` αν χρειάζεται να είστε ρητοί, αλλά το `Save(string)` ανιχνεύει αυτόματα τη μορφή από την επέκταση του αρχείου.

---

## Αναμενόμενο Αποτέλεσμα

Όταν ανοίξετε το `FormattedChart.docx` στο Microsoft Word, θα δείτε:

- Το πρώτο τμήμα μιας πίτας **εκρηγμένο** προς τα έξω.
- Αν το διάγραμμα είναι δακτύλιος, η κεντρική τρύπα τώρα καταλαμβάνει **30 %** της ακτίνας.
- Οποιαδήποτε τροποποιημένα σημεία δεδομένων αντικατοπτρίζουν τις νέες τιμές που ορίσατε.

Παρακάτω υπάρχει μια εικονική αναπαράσταση του εκρηγμένου τμήματος (εικόνα μόνο για επεξήγηση).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Κείμενο alt:* **εκρηγμένο τμήμα πίτας** που δείχνει ένα τμήμα που έχει απομακρυνθεί σε έγγραφο Word.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

**Τι γίνεται αν το διάγραμμα δεν είναι πίτα ή δακτύλιος;**  
Ο κώδικας ελέγχει το `ChartType` πριν εφαρμόσει `Exploded` ή `HoleSize`. Για ραβδογράμματα, γραμμικά ή περιοχικά διαγράμματα αυτές οι ιδιότητες απλώς δεν υπάρχουν, οπότε η λογική παραλείπεται με ασφάλεια.

**Μπορώ να εκρήγνυσω πολλαπλά τμήματα;**  
Απόλυτα. Κάντε βρόχο μέσα στο `chart.PieChartData.Series[0].DataPoints` και ορίστε `Exploded = true` σε όποιον δείκτη θέλετε.

**Πρέπει να ανησυχήσω για μορφοποίηση αριθμών ανά πολιτισμό;**  
Το Aspose.Words αποθηκεύει αριθμητικές τιμές ως double, ανεξάρτητα από την τοπική ρύθμιση, οπότε δεν υπάρχει πρόβλημα με κόμματα vs τελείες.

**Τι γίνεται με διαγράμματα ενσωματωμένα σε κεφαλίδες/υποσέλιδα;**  
Χρησιμοποιήστε `doc.GetChildNodes(NodeType.Chart, true)` για να ανακτήσετε όλα τα διαγράμματα, μετά ελέγξτε το `ParentNode` κάθε κόμβου για να δείτε πού βρίσκεται. Η ίδια λογική εκρήγνυσης ισχύει.

---

## Συμπέρασμα

Τώρα έχετε μια σταθερή, έτοιμη για αντιγραφή λύση για το **πώς να εκρήγνυτε τμήμα πίτας** χρησιμοποιώντας Aspose.Words σε C#. Καλύψαμε όλο το workflow — από τη φόρτωση του εγγράφου, την ανάκτηση του διαγράμματος, την εκρήγνυση του τμήματος, **τη ρύθμιση του μεγέθους της τρύπας του δακτυλίου**, μέχρι την **αλλαγή σημείων δεδομένων διαγράμματος** και τέλος την αποθήκευση του αρχείου.

Πειραματιστείτε: δοκιμάστε να εκρήγνυτε διαφορετικό τμήμα, αλλάξτε το μέγεθος της τρύπας σε 45 %, ή ενημερώστε πολλά σημεία δεδομένων ταυτόχρονα. Το API του Aspose.Words κάνει αυτές τις προσαρμογές άνετες, και οι αλλαγές εμφανίζονται αμέσως όταν ανοίξετε το αρχείο Word.

---

### Τι Ακολουθεί;

- **Στυλιζάτε το εκρηγμένο τμήμα** (αλλάξτε χρώμα γεμίσματος, περίγραμμα ή προσθέστε ετικέτα δεδομένων). Αναζητήστε “Aspose.Words chart formatting”.
- **Αυτοματοποιήστε επεξεργασία παρτίδας** πολλαπλών εγγράφων — κάντε βρόχο σε φάκελο, εκρήγνυτε τμήματα και αποθηκεύστε νέες εκδόσεις.
- **Συνδυάστε με Aspose.Slides** αν χρειάζεστε το ίδιο διάγραμμα σε παρουσίαση PowerPoint.

Έχετε περισσότερες ερωτήσεις για τη διαχείριση διαγραμμάτων ή θέλετε να εμβαθύνετε σε άλλους τύπους διαγραμμάτων; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική!

## Τι Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}