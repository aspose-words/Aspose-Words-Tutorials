---
title: Δημιουργία Πίνακα με Περιστρεφόμενο Κείμενο σε Έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
weight: 110
limit:
description: Μάθετε να δημιουργείτε έναν πίνακα Word με σταθερά πλάτη στηλών, περιστρεφόμενο κείμενο, ακριβή ύψη γραμμών και γεμάτα κελιά χρησιμοποιώντας το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Μάθετε να δημιουργείτε έναν πίνακα Word με σταθερά πλάτη στηλών, περιστρεφόμενο
    κείμενο, ακριβή ύψη γραμμών και γεμάτα κελιά χρησιμοποιώντας το Aspose.Words for
    .NET.
  headline: Δημιουργία Πίνακα με Περιστρεφόμενο Κείμενο σε Έγγραφο Word χρησιμοποιώντας
    το Aspose.Words for .NET
  type: TechArticle
- description: Μάθετε να δημιουργείτε έναν πίνακα Word με σταθερά πλάτη στηλών, περιστρεφόμενο
    κείμενο, ακριβή ύψη γραμμών και γεμάτα κελιά χρησιμοποιώντας το Aspose.Words for
    .NET.
  name: Δημιουργία Πίνακα με Περιστρεφόμενο Κείμενο σε Έγγραφο Word χρησιμοποιώντας
    το Aspose.Words for .NET
  steps:
  - name: Δημιουργήστε ένα νέο Document και ένα DocumentBuilder που θα χρησιμοποιηθούν
      για την κατασκευή του πίνακα.
    text: Δημιουργήστε ένα νέο Document και ένα DocumentBuilder που θα χρησιμοποιηθούν
      για την κατασκευή του πίνακα.
  - name: Ξεκινήστε έναν νέο πίνακα, εισάγετε το πρώτο κελί και ορίστε σταθερά τα
      πλάτη των στηλών ώστε να μην προσαρμόζονται αυτόματα.
    text: Ξεκινήστε έναν νέο πίνακα, εισάγετε το πρώτο κελί και ορίστε σταθερά τα
      πλάτη των στηλών ώστε να μην προσαρμόζονται αυτόματα.
  - name: Στοίχιση του περιεχομένου κατακόρυφα στο κέντρο του τρέχοντος κελιού και
      εγγραφή του κειμένου του πρώτου κελιού της πρώτης γραμμής.
    text: Στοίχιση του περιεχομένου κατακόρυφα στο κέντρο του τρέχοντος κελιού και
      εγγραφή του κειμένου του πρώτου κελιού της πρώτης γραμμής.
  - name: Εισάγετε το δεύτερο κελί της πρώτης γραμμής και γράψτε το κείμενό του.
    text: Εισάγετε το δεύτερο κελί της πρώτης γραμμής και γράψτε το κείμενό του.
  - name: Κλείστε την πρώτη γραμμή, ολοκληρώνοντας τη διάταξή της.
    text: Κλείστε την πρώτη γραμμή, ολοκληρώνοντας τη διάταξή της.
  - name: Ξεκινήστε το πρώτο κελί της δεύτερης γραμμής, ορίστε το ύψος της γραμμής
      σε ακριβώς 100 σημεία, περιστρέψτε το κείμενο προς τα πάνω και γράψτε το κείμενο
      του κελιού.
    text: Ξεκινήστε το πρώτο κελί της δεύτερης γραμμής, ορίστε το ύψος της γραμμής
      σε ακριβώς 100 σημεία, περιστρέψτε το κείμενο προς τα πάνω και γράψτε το κείμενο
      του κελιού.
  - name: Εισάγετε το δεύτερο κελί της δεύτερης γραμμής, περιστρέψτε το κείμενό του
      προς τα κάτω και γράψτε το κείμενο του κελιού.
    text: Εισάγετε το δεύτερο κελί της δεύτερης γραμμής, περιστρέψτε το κείμενό του
      προς τα κάτω και γράψτε το κείμενο του κελιού.
  - name: Κλείστε τη δεύτερη γραμμή, ολοκληρώνοντας τη δεύτερη σειρά του πίνακα.
    text: Κλείστε τη δεύτερη γραμμή, ολοκληρώνοντας τη δεύτερη σειρά του πίνακα.
  - name: Τερματίστε την κατασκευή του πίνακα, κλειδώνοντας τη δομή του.
    text: Τερματίστε την κατασκευή του πίνακα, κλειδώνοντας τη δομή του.
  - name: Αποθηκεύστε το ολοκληρωμένο έγγραφο σε αρχείο .docx.
    text: Αποθηκεύστε το ολοκληρωμένο έγγραφο σε αρχείο .docx.
  type: HowTo
- questions:
  - answer: Αφού ορίσετε σταθερά τα πλάτη των στηλών, αναθέστε ένα πλάτος σε κάθε
      κελί χρησιμοποιώντας `builder.CellFormat.Width = <valueInPoints>;` πριν εισάγετε
      το επόμενο κελί· ο πίνακας θα διατηρήσει αυτά τα ακριβή πλάτη.
    question: Πώς μπορώ να ορίσω συγκεκριμένα πλάτη στηλών μετά την κλήση του `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`;
  - answer: '`builder.CellFormat.VerticalAlignment` είναι ρύθμιση σε επίπεδο κελιού,
      επομένως πρέπει να το ορίσετε ξανά για τα κελιά της δεύτερης γραμμής (π.χ.,
      `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) πριν
      γράψετε το περιεχόμενό τους.'
    question: Γιατί η κατακόρυφη στοίχιση επηρεάζει μόνο την πρώτη γραμμή και όχι
      τη δεύτερη γραμμή;
  - answer: Ναι — ορίστε `builder.RowFormat.Height` και `builder.RowFormat.HeightRule
      = HeightRule.Exactly` πριν από κάθε κλήση του `builder.EndRow();`; η επόμενη
      γραμμή μπορεί να έχει διαφορετική τιμή ύψους.
    question: Μπορώ να δώσω σε κάθε γραμμή διαφορετικό ακριβές ύψος, και αν ναι, πώς;
  - answer: Επαναφέρετε τον προσανατολισμό αναθέτοντας `builder.CellFormat.Orientation
      = TextOrientation.Horizontal;` πριν γράψετε στο επόμενο κελί.
    question: Πώς μπορώ να επαναφέρω τον προσανατολισμό κειμένου στην προεπιλογή μετά
      τη χρήση του `TextOrientation.Upward` ή `Downward`;
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Δημιουργία Πίνακα με Περιστρεφόμενο Κείμενο σε Word με το Aspose.Words
og_description: Βήμα‑βήμα κώδικας για τη δημιουργία πίνακα σταθερού πλάτους με κατακόρυφα περιστρεφόμενο κείμενο και ακριβή ύψη γραμμών.
og_image_alt: Στιγμιότυπο που δείχνει ένα έγγραφο Word με έναν πίνακα που έχει σταθερά πλάτη στηλών, περιστρεφόμενο κείμενο στα κελιά και καθορισμένα ύψη γραμμών, δημιουργημένο με το Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Πίνακα με Περιστρεφόμενο Κείμενο σε Έγγραφο Word χρησιμοποιώντας το Aspose.Words
Αυτό το σεμινάριο δείχνει πώς να δημιουργήσετε ένα έγγραφο Word και να προσθέσετε έναν πίνακα του οποίου οι στήλες έχουν σταθερά πλάτη, οι γραμμές ακριβές ύψη και το κείμενο των κελιών περιστρέφεται κατακόρυφα. Θα μάθετε πώς να ορίζετε κατακόρυφη στοίχιση, να εφαρμόζετε προσανατολισμό κειμένου, να γεμίζετε κάθε κελί με περιεχόμενο και, τέλος, να αποθηκεύετε το έγγραφο — όλα με το Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Πώς μπορώ να ορίσω συγκεκριμένα πλάτη στηλών μετά την κλήση του `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`;**  
A: Αφού ορίσετε σταθερά τα πλάτη των στηλών, αναθέστε ένα πλάτος σε κάθε κελί χρησιμοποιώντας `builder.CellFormat.Width = <valueInPoints>;` πριν εισάγετε το επόμενο κελί· ο πίνακας θα διατηρήσει αυτά τα ακριβή πλάτη.

**Q: Γιατί η κατακόρυφη στοίχιση επηρεάζει μόνο την πρώτη γραμμή και όχι τη δεύτερη γραμμή;**  
A: `builder.CellFormat.VerticalAlignment` είναι ρύθμιση σε επίπεδο κελιού, επομένως πρέπει να το ορίσετε ξανά για τα κελιά της δεύτερης γραμμής (π.χ., `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) πριν γράψετε το περιεχόμενό τους.

**Q: Μπορώ να δώσω σε κάθε γραμμή διαφορετικό ακριβές ύψος, και αν ναι, πώς;**  
A: Ναι — ορίστε `builder.RowFormat.Height` και `builder.RowFormat.HeightRule = HeightRule.Exactly` πριν από κάθε κλήση του `builder.EndRow();`; η επόμενη γραμμή μπορεί να έχει διαφορετική τιμή ύψους.

**Q: Πώς μπορώ να επαναφέρω τον προσανατολισμό κειμένου στην προεπιλογή μετά τη χρήση του `TextOrientation.Upward` ή `Downward`;**  
A: Επαναφέρετε τον προσανατολισμό αναθέτοντας `builder.CellFormat.Orientation = TextOrientation.Horizontal;` πριν γράψετε στο επόμενο κελί.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}