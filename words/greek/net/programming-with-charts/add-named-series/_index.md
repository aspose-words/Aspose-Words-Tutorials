---
title: Προσθήκη ονομαστικής σειράς δεδομένων σε διάγραμμα ιστογράμματος στο Word χρησιμοποιώντας το Aspose.Words for .NET
weight: 610
limit:
description: Μάθετε πώς να ενσωματώσετε ένα διάγραμμα ιστογράμματος σε ένα έγγραφο Word και να προσθέσετε μια ονομαστική σειρά δεδομένων με το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Μάθετε πώς να ενσωματώσετε ένα διάγραμμα ιστογράμματος σε ένα έγγραφο
    Word και να προσθέσετε μια ονομαστική σειρά δεδομένων με το Aspose.Words for .NET.
  headline: Προσθήκη ονομαστικής σειράς δεδομένων σε διάγραμμα ιστογράμματος στο Word
    χρησιμοποιώντας το Aspose.Words for .NET
  type: TechArticle
- description: Μάθετε πώς να ενσωματώσετε ένα διάγραμμα ιστογράμματος σε ένα έγγραφο
    Word και να προσθέσετε μια ονομαστική σειρά δεδομένων με το Aspose.Words for .NET.
  name: Προσθήκη ονομαστικής σειράς δεδομένων σε διάγραμμα ιστογράμματος στο Word
    χρησιμοποιώντας το Aspose.Words for .NET
  steps:
  - name: Δημιουργήστε ένα νέο κενό έγγραφο Word και ένα DocumentBuilder για να το
      επεξεργαστείτε.
    text: Δημιουργήστε ένα νέο κενό έγγραφο Word και ένα DocumentBuilder για να το
      επεξεργαστείτε.
  - name: Εισάγετε ένα σχήμα διαγράμματος ιστογράμματος μεγέθους 500×300 στο έγγραφο
      και αποκτήστε το αντικείμενο Chart του.
    text: Εισάγετε ένα σχήμα διαγράμματος ιστογράμματος μεγέθους 500×300 στο έγγραφο
      και αποκτήστε το αντικείμενο Chart του.
  - name: Αφαιρέστε τη προεπιλεγμένη σειρά placeholder που προσθέτει το Aspose.Words
      στα νέα διαγράμματα.
    text: Αφαιρέστε τη προεπιλεγμένη σειρά placeholder που προσθέτει το Aspose.Words
      στα νέα διαγράμματα.
  - name: Προσθέστε μια ονομαστική σειρά με το όνομα "Demo Series" και τα καθορισμένα
      σημεία δεδομένων στο διάγραμμα ιστογράμματος.
    text: Προσθέστε μια ονομαστική σειρά με το όνομα "Demo Series" και τα καθορισμένα
      σημεία δεδομένων στο διάγραμμα ιστογράμματος.
  - name: Αποθηκεύστε το έγγραφο σε αρχείο .docx που περιέχει την επισημασμένη σειρά
      διαγράμματος.
    text: Αποθηκεύστε το έγγραφο σε αρχείο .docx που περιέχει την επισημασμένη σειρά
      διαγράμματος.
  type: HowTo
- questions:
  - answer: '`InsertChart` δημιουργεί μια προεπιλεγμένη σειρά placeholder· η εκκαθάριση
      της αφαιρεί αυτή τη κενή σειρά ώστε το διάγραμμα να εμφανίζει μόνο τα δεδομένα
      που προσθέτετε με το `Series.Add`.'
    question: Γιατί πρέπει να καλέσω το `histogramChart.Series.Clear()` πριν προσθέσω
      τη δική μου σειρά;
  - answer: Ναι, καλέστε το `histogramChart.Series.Add` πολλές φορές, κάθε φορά με
      διαφορετικό όνομα και τιμές `double[]`; κάθε σειρά θα εμφανίζεται στη λεζάντα
      του διαγράμματος με το παρεχόμενο όνομα.
    question: Μπορώ να προσθέσω περισσότερες από μία σειρές χρησιμοποιώντας την ίδια
      υπερφόρτωση και θα εμφανίζεται η καθεμία με τη δική της ετικέτα;
  - answer: Η υπερφόρτωση αναμένει ένα `double[]`; εάν έχετε `int[]` ή άλλους αριθμητικούς
      πίνακες, μετατρέψτε ή μεταcast τους σε `double[]` πριν τους περάσετε.
    question: Είναι το όρισμα `double[]` ο μοναδικός τύπος που δέχεται το API για
      τα σημεία δεδομένων;
  - answer: Η συμβολοσειρά που περνιέται ως πρώτο όρισμα (π.χ., "Demo Series") χρησιμοποιείται
      ως τίτλος της σειράς και εμφανίζεται στην λεζάντα του διαγράμματος εξ ορισμού.
    question: Θα εμφανιστεί αυτόματα στο διάγραμμα το όνομα της σειράς που παρέχω;
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Προσθήκη ονομαστικής σειράς σε διάγραμμα ιστογράμματος Word
og_description: Επισημάνετε γρήγορα μια σειρά διαγράμματος στο Word με το Aspose.Words και δείτε την να αποδίδεται άμεσα.
og_image_alt: Στιγμιότυπο οθόνης που δείχνει ένα έγγραφο Word με διάγραμμα ιστογράμματος που περιλαμβάνει μια επισημασμένη σειρά δεδομένων, δημιουργημένη με το Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη ονομαστικής σειράς δεδομένων σε διάγραμμα ιστογράμματος στο Word χρησιμοποιώντας το Aspose.Words
Αυτό το σεμινάριο δείχνει πώς να δημιουργήσετε ένα έγγραφο Word με το Aspose.Words for .NET, να εισάγετε ένα διάγραμμα ιστογράμματος και να προσθέσετε μια επισημασμένη σειρά δεδομένων χρησιμοποιώντας την υπερφόρτωση ChartSeriesCollection.Add που δέχεται ένα όνομα και τιμές. Ονομάζοντας τη σειρά, μπορείτε να αναγνωρίζετε σαφώς κάθε σύνολο δεδομένων μέσα στο διάγραμμα, καθιστώντας την οπτική έξοδο πιο εύκολη στην ανάγνωση και ερμηνεία.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: Γιατί πρέπει να καλέσω το `histogramChart.Series.Clear()` πριν προσθέσω τη δική μου σειρά;**  
A: `InsertChart` δημιουργεί μια προεπιλεγμένη σειρά placeholder· η εκκαθάριση της αφαιρεί αυτή τη κενή σειρά ώστε το διάγραμμα να εμφανίζει μόνο τα δεδομένα που προσθέτετε με το `Series.Add`.

**Q: Μπορώ να προσθέσω περισσότερες από μία σειρές χρησιμοποιώντας την ίδια υπερφόρτωση και θα εμφανίζεται η καθεμία με τη δική της ετικέτα;**  
A: Ναι, καλέστε το `histogramChart.Series.Add` πολλές φορές, κάθε φορά με διαφορετικό όνομα και τιμές `double[]`; κάθε σειρά θα εμφανίζεται στη λεζάντα του διαγράμματος με το παρεχόμενο όνομα.

**Q: Είναι το όρισμα `double[]` ο μοναδικός τύπος που δέχεται το API για τα σημεία δεδομένων;**  
A: Η υπερφόρτωση αναμένει ένα `double[]`; εάν έχετε `int[]` ή άλλους αριθμητικούς πίνακες, μετατρέψτε ή μεταcast τους σε `double[]` πριν τους περάσετε.

**Q: Θα εμφανιστεί αυτόματα στο διάγραμμα το όνομα της σειράς που παρέχω;**  
A: Η συμβολοσειρά που περνιέται ως πρώτο όρισμα (π.χ., "Demo Series") χρησιμοποιείται ως τίτλος της σειράς και εμφανίζεται στην λεζάντα του διαγράμματος εξ ορισμού.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}