---
title: Αφαίρεση σειράς γραφήματος (Chart Series) από έγγραφο Word χρησιμοποιώντας το Aspose.Words για .NET
weight: 510
limit:
description: Μάθετε πώς να διαγράψετε μια συγκεκριμένη σειρά δεδομένων από ένα γράφημα στήλης σε έγγραφο Word με το Aspose.Words για .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Μάθετε πώς να διαγράψετε μια συγκεκριμένη σειρά δεδομένων από ένα γράφημα
    στήλης σε έγγραφο Word με το Aspose.Words για .NET.
  headline: Αφαίρεση σειράς γραφήματος (Chart Series) από έγγραφο Word χρησιμοποιώντας
    το Aspose.Words για .NET
  type: TechArticle
- description: Μάθετε πώς να διαγράψετε μια συγκεκριμένη σειρά δεδομένων από ένα γράφημα
    στήλης σε έγγραφο Word με το Aspose.Words για .NET.
  name: Αφαίρεση σειράς γραφήματος (Chart Series) από έγγραφο Word χρησιμοποιώντας
    το Aspose.Words για .NET
  steps:
  - name: Δημιουργήστε ένα νέο Word Document και έναν DocumentBuilder που είναι συνδεδεμένος
      με αυτό.
    text: Δημιουργήστε ένα νέο Word Document και έναν DocumentBuilder που είναι συνδεδεμένος
      με αυτό.
  - name: Εισάγετε ένα γράφημα στήλης μεγέθους 432×252 σημεία και αποκτήστε το αντικείμενο
      Chart για περαιτέρω επεξεργασία.
    text: Εισάγετε ένα γράφημα στήλης μεγέθους 432×252 σημεία και αποκτήστε το αντικείμενο
      Chart για περαιτέρω επεξεργασία.
  - name: Ορίστε το μηδενικό (zero‑based) δείκτη της σειράς που πρέπει να αφαιρεθεί
      (η δεύτερη σειρά).
    text: Ορίστε το μηδενικό (zero‑based) δείκτη της σειράς που πρέπει να αφαιρεθεί
      (η δεύτερη σειρά).
  - name: Αν ο δείκτης είναι έγκυρος, καλέστε τη μέθοδο RemoveAt στη συλλογή Series
      του γραφήματος για να διαγράψετε αυτή τη σειρά.
    text: Αν ο δείκτης είναι έγκυρος, καλέστε τη μέθοδο RemoveAt στη συλλογή Series
      του γραφήματος για να διαγράψετε αυτή τη σειρά.
  - name: Αποθηκεύστε το ενημερωμένο έγγραφο σε αρχείο .docx.
    text: Αποθηκεύστε το ενημερωμένο έγγραφο σε αρχείο .docx.
  type: HowTo
- questions:
  - answer: Ο έλεγχος `if` (`targetSeriesIdx < columnChart.Series.Count`) θα αποτύχει,
      έτσι η `RemoveAt` δεν θα κληθεί ποτέ και το γράφημα θα παραμείνει αμετάβλητο.
    question: Τι συμβαίνει αν περάσω έναν δείκτη που είναι ίσος με τον αριθμό των
      σειρών στο γράφημα;
  - answer: Ναι, μετά το `columnChart.Series.RemoveAt` το υπόμνημα αναδημιουργείται
      ώστε να αντικατοπτρίζει τις υπόλοιπες σειρές, έτσι η αφαιρεθείσα καταχώρηση
      εξαφανίζεται από το υπόμνημα.
    question: Η αφαίρεση μιας σειράς ενημερώνει αυτόματα το υπόμνημα (legend) του
      γραφήματος;
  - answer: Ο κώδικας λειτουργεί για οποιονδήποτε τύπο γραφήματος που υποστηρίζει
      μια συλλογή `Series`; απλώς αλλάξτε το `ChartType.Column` στον επιθυμητό τύπο
      κατά την εισαγωγή του γραφήματος.
    question: Μπορώ να χρησιμοποιήσω τον ίδιο κώδικα για να διαγράψω μια σειρά από
      γράφημα γραμμής ή πίτας;
  - answer: Ένα γράφημα με μηδενικές σειρές παραμένει έγκυρο `Shape` και θα αποθηκευτεί,
      αλλά θα εμφανίζεται κενό στο τελικό έγγραφο.
    question: Αν αφαιρέσω τη μοναδική σειρά σε ένα γράφημα, θα αποθηκευτεί το γράφημα
      σωστά;
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Διαγραφή σειράς γραφήματος (Chart Series) σε έγγραφο Word
og_description: Οδηγός βήμα‑βήμα για την αφαίρεση μιας σειράς δεδομένων από γράφημα Word χρησιμοποιώντας το Aspose.Words για .NET.
og_image_alt: Οδηγός που δείχνει πώς να διαγράψετε μια συγκεκριμένη σειρά δεδομένων από ένα γράφημα στήλης σε έγγραφο Word χρησιμοποιώντας το Aspose.Words για .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αφαίρεση σειράς γραφήματος (Chart Series) από έγγραφο Word χρησιμοποιώντας το Aspose.Words για .NET
Αυτό το σεμινάριο δείχνει πώς να δημιουργήσετε ένα έγγραφο Word, να προσθέσετε ένα γράφημα στήλης με το DocumentBuilder και στη συνέχεια να διαγράψετε μια συγκεκριμένη σειρά δεδομένων από το γράφημα χρησιμοποιώντας τη μέθοδο ChartSeriesCollection.RemoveAt. Στο τέλος, θα έχετε ένα αποθηκευμένο έγγραφο με την ανεπιθύμητη σειρά αφαιρεμένη, παρέχοντάς σας ακριβή έλεγχο του περιεχομένου του γραφήματος απευθείας από κώδικα .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Τι συμβαίνει αν περάσω έναν δείκτη που είναι ίσος με τον αριθμό των σειρών στο γράφημα;**  
A: Ο έλεγχος `if` (`targetSeriesIdx < columnChart.Series.Count`) θα αποτύχει, έτσι η `RemoveAt` δεν θα κληθεί ποτέ και το γράφημα θα παραμείνει αμετάβλητο.

**Q: Η αφαίρεση μιας σειράς ενημερώνει αυτόματα το υπόμνημα (legend) του γραφήματος;**  
A: Ναι, μετά το `columnChart.Series.RemoveAt` το υπόμνημα αναδημιουργείται ώστε να αντικατοπτρίζει τις υπόλοιπες σειρές, έτσι η αφαιρεθείσα καταχώρηση εξαφανίζεται από το υπόμνημα.

**Q: Μπορώ να χρησιμοποιήσω τον ίδιο κώδικα για να διαγράψω μια σειρά από γράφημα γραμμής ή πίτας;**  
A: Ο κώδικας λειτουργεί για οποιονδήποτε τύπο γραφήματος που υποστηρίζει μια συλλογή `Series`; απλώς αλλάξτε το `ChartType.Column` στον επιθυμητό τύπο κατά την εισαγωγή του γραφήματος.

**Q: Αν αφαιρέσω τη μοναδική σειρά σε ένα γράφημα, θα αποθηκευτεί το γράφημα σωστά;**  
A: Ένα γράφημα με μηδενικές σειρές παραμένει έγκυρο `Shape` και θα αποθηκευτεί, αλλά θα εμφανίζεται κενό στο τελικό έγγραφο.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}