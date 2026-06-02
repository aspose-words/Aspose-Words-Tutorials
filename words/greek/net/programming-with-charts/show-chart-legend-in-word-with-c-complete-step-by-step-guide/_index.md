---
category: general
date: 2026-06-02
description: Εμφανίστε το υπόμνημα του διαγράμματος σε έγγραφο Word χρησιμοποιώντας
  C#. Μάθετε πώς να προσθέσετε υπόμνημα, να εφαρμόσετε προεπιλεγμένο στυλ διαγράμματος
  και να προσαρμόσετε τα οπτικά στοιχεία του διαγράμματος Word σε λίγα λεπτά.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: el
og_description: Εμφανίστε τη λεζάντα του διαγράμματος σε ένα έγγραφο Word άμεσα. Αυτός
  ο οδηγός σας καθοδηγεί στη προσθήκη λεζάντας, στην εφαρμογή προεπιλεγμένου στυλ
  διαγράμματος και στη διαχείριση ειδικών περιπτώσεων.
og_title: Εμφάνιση Υπόμνησης Διαγράμματος στο Word – Πλήρης Εκπαίδευση C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Εμφάνιση Υπόμνησης Διαγράμματος στο Word με C# – Πλήρης Οδηγός Βήμα‑Βήμα
url: /el/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εμφάνιση Υπόμνησης Γραφήματος σε Word με C# – Πλήρης Οδηγός Βήμα‑Βήμα

Έχετε αναρωτηθεί ποτέ **πώς να προσθέσετε υπόμνηση** σε ένα γράφημα που βρίσκεται μέσα σε ένα έγγραφο Word; Δεν είστε οι μόνοι. Σε πολλές αναφορές, η έλλειψη υπόμνησης κάνει τα δεδομένα να φαίνονται ασαφή, και η διόρθωσή της δεν πρέπει να είναι πρόβλημα.  

Σε αυτό το tutorial θα **εμφανίσουμε την υπόμνηση του γραφήματος** σε ένα αρχείο Word χρησιμοποιώντας το Aspose.Words for .NET, θα εφαρμόσουμε ένα προεπιλεγμένο στυλ γραφήματος και θα εξασφαλίσουμε ότι η υπόμνηση εμφανίζεται ακριβώς εκεί που τη χρειάζεστε. Στο τέλος θα έχετε ένα έτοιμο δείγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο C#.

## Τι Καλύπτει Αυτός Ο Οδηγός

Θα περάσουμε από όλη τη διαδικασία:

1. Φόρτωση ενός υπάρχοντος *.docx* που περιέχει ήδη ένα γράφημα.  
2. Ανάκτηση του πρώτου γραφήματος (ή οποιουδήποτε γραφήματος στοχεύετε).  
3. **Εφαρμογή προεπιλεγμένου στυλ γραφήματος** για επαγγελματική εμφάνιση.  
4. **Εμφάνιση υπόμνησης γραφήματος**, τοποθέτησή της στα δεξιά και διαχείριση ειδικών περιπτώσεων όπως τα Waterfall γραφήματα.  
5. Αποθήκευση του τροποποιημένου εγγράφου.

Καμία εξωτερική εργαλειοθήκη, καμία χειροκίνητη παρέμβαση στο UI—απλώς καθαρός κώδικας. Η μόνη προϋπόθεση είναι μια αναφορά στο πακέτο NuGet Aspose.Words (έκδοση 23.10 ή νεότερη) και μια βασική κατανόηση της C#.

---

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το δείγμα λειτουργεί και με .NET Framework 4.7.2).  
- Βιβλιοθήκη Aspose.Words for .NET εγκατεστημένη (`Install-Package Aspose.Words`).  
- Αρχείο Word (`input.docx`) που περιέχει τουλάχιστον ένα γράφημα.  
- Visual Studio, Rider ή οποιοδήποτε IDE προτιμάτε.

---

## Βήμα 1: Ρύθμιση του Έργου και Φόρτωση του Εγγράφου

Πρώτα, δημιουργήστε μια εφαρμογή console (ή ενσωματώστε τον κώδικα σε υπάρχον έργο). Προσθέστε τις οδηγίες `using` και φορτώστε το αρχείο `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου είναι το θεμέλιο. Χωρίς ένα αντικείμενο `Document` δεν μπορείτε να προσεγγίσετε τα αντικείμενα γραφήματος που εκθέτει το Aspose.Words.

---

## Βήμα 2: Ανάκτηση του Στόχου Γραφήματος

Τα γραφήματα αποθηκεύονται ως κόμβοι μέσα στο δέντρο του εγγράφου. Η μέθοδος `GetChild` εκτελεί αναζήτηση σε βάθος, επιτρέποντάς μας να πάρουμε το πρώτο γράφημα ανεξάρτητα από το πού βρίσκεται (κεφαλίδα, σώμα, υποσέλιδο κ.λπ.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Συμβουλή:** Αν έχετε πολλά γραφήματα, αλλάξτε το δείκτη `0` σε `1`, `2`, … ή επαναλάβετε μέσω `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Βήμα 3: Εφαρμογή Προεπιλεγμένου Οπτικού Στυλ

Ένα καλό γράφημα ξεκινά συχνά με ένα στυλ. Το Aspose.Words περιλαμβάνει δεκάδες ενσωματωμένα στυλ· το `ChartStyle.Style12` είναι μια καθαρή, σύγχρονη επιλογή.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Πώς λειτουργεί:** Η ιδιότητα `Style` αντιστοιχεί στα ενσωματωμένα στυλ γραφήματος του Word που βλέπετε στη διεπαφή. Η επιλογή ενός προεπιλεγμένου στυλ σας εξοικονομεί την ανάγκη χειροκίνητης ρύθμισης χρωμάτων, γραμματοσειρών και σημείων.

---

## Βήμα 4: Ενεργοποίηση της Υπόμνησης και Τοποθέτησή της

Τώρα έρχεται το αστέρι της παράστασης—**εμφάνιση υπόμνησης γραφήματος**. Ενεργοποιούμε την υπόμνηση και τη στεγάζουμε στη δεξιά πλευρά του γραφήματος.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Γιατί δεξιά;** Η τοποθέτηση της υπόμνησης στα δεξιά διατηρεί την περιοχή δεδομένων ευρύχωρη, κάτι που είναι ιδιαίτερα χρήσιμο για γραφήματα ράβδων ή στηλών.

---

## Βήμα 5: Διαχείριση Waterfall Γραφημάτων (Ειδική Περίπτωση)

Τα Waterfall γραφήματα συμπεριφέρονται λίγο διαφορετικά· η υπόμνηση μπορεί να είναι κρυμμένη από προεπιλογή. Η παρακάτω συνθήκη εξασφαλίζει ότι η υπόμνηση είναι ορατή όταν ο τύπος γραφήματος είναι Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Σημείωση για άκρες περιπτώσεις:** Ορισμένες παλαιότερες εκδόσεις του Word αγνοούν το `HasLegend` για Waterfall γραφήματα, οπότε ο ρητός ορισμός του `Legend.Show` εγγυάται την ορατότητα.

---

## Βήμα 6: Αποθήκευση του Τροποποιημένου Εγγράφου

Τέλος, γράψτε τις αλλαγές στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να δημιουργήσετε ένα νέο.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Η εκτέλεση του προγράμματος θα παραγάγει το `output.docx` με μια ορατή υπόμνηση στα δεξιά, μορφοποιημένη με το `Style12`. Ανοίξτε το αρχείο στο Word για να επαληθεύσετε το αποτέλεσμα.

---

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα Συνδυασμένα)

Παρακάτω βρίσκεται ο πλήρης, έτοιμος‑για‑εκτέλεση κώδικας. Αντιγράψτε‑και‑επικολλήστε το στο `Program.cs` (ή σε οποιοδήποτε αρχείο C#) και προσαρμόστε τις διαδρομές αρχείων.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `output.docx` εμφανίζει το αρχικό γράφημα με μια δεξιά‑ευθυγραμμισμένη υπόμνηση, μορφοποιημένη με το σύγχρονο `Style12`. Όλες οι σειρές δεδομένων είναι σαφώς επισημασμένες, καθιστώντας το γράφημα άμεσα κατανοητό.

---

## Συχνές Ερωτήσεις (FAQ)

### Πώς να προσθέσετε υπόμνηση σε συγκεκριμένο γράφημα (όχι το πρώτο);

Αντικαταστήστε τον δείκτη `0` στο `GetChild(NodeType.Chart, 0, true)` με τη θέση μηδενικής βάσης του στόχου σας, ή κάντε βρόχο σε όλους τους κόμβους γραφήματος:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Μπορώ να τοποθετήσω την υπόμνηση στο κάτω μέρος αντί για τα δεξιά;

Απολύτως. Απλώς αλλάξτε το enum `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Τι γίνεται αν το γράφημα έχει ήδη υπόμνηση αλλά θέλω να την κρύψω;

Ορίστε `HasLegend` σε `false`:

```csharp
chart.HasLegend = false;
```

### Λειτουργεί αυτό με Word 2010, 2016 και νεότερες εκδόσεις;

Ναι. Το Aspose.Words αφαιρεί την εξάρτηση από την υποκείμενη έκδοση του Word, έτσι ο ίδιος κώδικας λειτουργεί σε όλα τα σύγχρονα αρχεία .docx.

---

## Pro Συμβουλές & Συνηθισμένα Πιθανά Προβλήματα

- **Pro tip:** Μετά την εφαρμογή ενός στυλ, μπορείτε ακόμη να ρυθμίσετε μεμονωμένα στοιχεία (χρώματα, ετικέτες δεδομένων) μέσω της συλλογής `Chart.Series`. Το στυλ σας δίνει μια σταθερή βάση.  
- **Προσοχή:** Αν το γράφημα βρίσκεται μέσα σε κελί πίνακα, η υπόμνηση μπορεί να εμφανιστεί στενή. Σκεφτείτε να αυξήσετε το μέγεθος του γραφήματος (`chart.Width`, `chart.Height`) πριν τοποθετήσετε την υπόμνηση.  
- **Σημείωση απόδοσης:** Η φόρτωση μεγάλων εγγράφων (εκατοντάδες MB) μπορεί να καταναλώνει πολύ μνήμη. Χρησιμοποιήστε `LoadOptions` με `LoadFormat.Docx` για μείωση του φόρτου αν χρειάζεστε μόνο επεξεργασία γραφήματος.

---

## Επόμενα Βήματα

Τώρα που ξέρετε **πώς να προσθέσετε υπόμνηση** και **να εφαρμόσετε προεπιλεγμένο στυλ γραφήματος** σε Word, μπορείτε να εξερευνήσετε:

- **Προσαρμοσμένα χρώματα γραφήματος** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Μορφοποίηση ετικετών δεδομένων** (`chart.Series[i].HasDataLabel = true`).  
- **Εξαγωγή του γραφήματος ως εικόνα** (`chart.ToImage()`), χρήσιμο για ενσωμάτωση αλλού.  

Κάθε ένα από αυτά τα θέματα βασίζεται στο ίδιο μοντέλο αντικειμένων, οπότε η καμπύλη εκμάθησης παραμένει ήπια.

---

## Συμπέρασμα

Δείξαμε μια καθαρή, ολοκληρωμένη λύση για **εμφάνιση υπόμνησης γραφήματος** σε έγγραφο Word χρησιμοποιώντας C#. Φορτώνοντας το έγγραφο, ανακτώντας το γράφημα, εφαρμόζοντας ένα προεπιλεγμένο στυλ, ενεργοποιώντας την υπόμνηση και αντιμετωπίζοντας τις ιδιαιτερότητες των Waterfall, λαμβάνετε ένα επαγγελματικό γράφημα έτοιμο για οποιαδήποτε επιχειρηματική αναφορά.  

Μη διστάσετε να πειραματιστείτε με άλλες τιμές `ChartStyle` ή θέσεις υπόμνησης—οι οπτικοποιήσεις σας αξίζουν την καλύτερη παρουσίαση. Αν αντιμετωπίσετε δυσκολίες, αφήστε ένα σχόλιο παρακάτω· καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σειρά Επόμενη;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}