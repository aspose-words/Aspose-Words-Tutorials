---
title: Αλλαγή μεγέθους Chart αναλογικά κατά την αλλαγή μεγέθους σελίδας στο Word χρησιμοποιώντας Aspose.Words for .NET
weight: 210
limit:
description: Μάθετε πώς να αλλάζετε αυτόματα το μέγεθος ενός Word column chart όταν αλλάζετε το έγγραφο σε A4 χρησιμοποιώντας Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Μάθετε πώς να αλλάζετε αυτόματα το μέγεθος ενός Word column chart όταν
    αλλάζετε το έγγραφο σε A4 χρησιμοποιώντας Aspose.Words for .NET.
  headline: Αλλαγή μεγέθους Chart αναλογικά κατά την αλλαγή μεγέθους σελίδας στο Word
    χρησιμοποιώντας Aspose.Words for .NET
  type: TechArticle
- description: Μάθετε πώς να αλλάζετε αυτόματα το μέγεθος ενός Word column chart όταν
    αλλάζετε το έγγραφο σε A4 χρησιμοποιώντας Aspose.Words for .NET.
  name: Αλλαγή μεγέθους Chart αναλογικά κατά την αλλαγή μεγέθους σελίδας στο Word
    χρησιμοποιώντας Aspose.Words for .NET
  steps:
  - name: Δημιουργήστε ένα νέο αντικείμενο Document και ένα DocumentBuilder για να
      το επεξεργαστείτε.
    text: Δημιουργήστε ένα νέο αντικείμενο Document και ένα DocumentBuilder για να
      το επεξεργαστείτε.
  - name: Εισάγετε ένα column chart μεγέθους 432×252 points και αποκτήστε το αντικείμενο
      Chart του.
    text: Εισάγετε ένα column chart μεγέθους 432×252 points και αποκτήστε το αντικείμενο
      Chart του.
  - name: Ορίστε το κείμενο του τίτλου του chart σε "Quarterly Revenue" και κάντε
      το ορατό.
    text: Ορίστε το κείμενο του τίτλου του chart σε "Quarterly Revenue" και κάντε
      το ορατό.
  - name: Αποθηκεύστε το έγγραφο σε ένα αρχείο που εμφανίζει το αρχικό μέγεθος του
      chart.
    text: Αποθηκεύστε το έγγραφο σε ένα αρχείο που εμφανίζει το αρχικό μέγεθος του
      chart.
  - name: Αλλάξτε το μέγεθος χαρτιού του εγγράφου σε A4 και ανανεώστε τη διάταξη.
    text: Αλλάξτε το μέγεθος χαρτιού του εγγράφου σε A4 και ανανεώστε τη διάταξη.
  - name: Υπολογίστε ένα νέο πλάτος chart ίσο με 80 % του πλάτους της σελίδας, διατηρώντας
      την αρχική αναλογία διαστάσεων.
    text: Υπολογίστε ένα νέο πλάτος chart ίσο με 80 % του πλάτους της σελίδας, διατηρώντας
      την αρχική αναλογία διαστάσεων.
  - name: Εάν το shape περιέχει ένα chart, εφαρμόστε το υπολογισμένο πλάτος και ύψος
      για να το αλλάξετε σε μέγεθος.
    text: Εάν το shape περιέχει ένα chart, εφαρμόστε το υπολογισμένο πλάτος και ύψος
      για να το αλλάξετε σε μέγεθος.
  - name: Αποθηκεύστε το έγγραφο μετά την αλλαγή μεγέθους του chart ώστε να αντανακλά
      το νέο μέγεθος σελίδας.
    text: Αποθηκεύστε το έγγραφο μετά την αλλαγή μεγέθους του chart ώστε να αντανακλά
      το νέο μέγεθος σελίδας.
  type: HowTo
- questions:
  - answer: Ναι. Η αλλαγή του `docBuilder.PageSetup.PaperSize` δεν προσαρμόζει αυτόματα
      τα υπάρχοντα shapes, επομένως πρέπει να επαναϋπολογίσετε και να ορίσετε το `chartContainer.Width`
      και `Height` εσείς όπως φαίνεται.
    question: Χρειάζεται να αλλάξω χειροκίνητα το μέγεθος του chart μετά την αλλαγή
      του μεγέθους χαρτιού του εγγράφου;
  - answer: Αποθηκεύει `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      και στη συνέχεια υπολογίζει `newChartHeight = newChartWidth * originalAspectRatio`
      αφού καθορίσει το νέο πλάτος.
    question: Πώς διατηρεί ο κώδικας την αρχική αναλογία πλάτους‑προς‑ύψος του chart
      κατά την αλλαγή μεγέθους;
  - answer: '`UpdatePageLayout()` αναγκάζει τη μηχανή διάταξης να επανεκτιμήσει τις
      διαστάσεις της σελίδας, διασφαλίζοντας ότι το `docBuilder.PageSetup.PageWidth`
      αντικατοπτρίζει το νέο πλάτος A4 πριν επαναϋπολογιστεί το μέγεθος του chart.'
    question: Γιατί καλείται το `myDoc.UpdatePageLayout()` μετά τον ορισμό του μεγέθους
      χαρτιού σε A4;
  - answer: Η προϋπόθεση `if (chartContainer.HasChart)` αποτρέπει τον κώδικα από το
      να ορίσει `Width` και `Height` όταν δεν υπάρχει chart, αποφεύγοντας μια εξαίρεση
      χρόνου εκτέλεσης.
    question: Τι συμβαίνει αν το εισαχθέν shape δεν περιέχει στην πραγματικότητα ένα
      chart;
  - answer: Απολύτως—αντικαταστήστε τον πολλαπλασιαστή `0.8` με οποιαδήποτε αναλογία
      προτιμάτε· η υπόλοιπη λογική αλλαγής μεγέθους θα διατηρήσει ακόμα την αρχική
      αναλογία διαστάσεων.
    question: Μπορώ να αλλάξω τον παράγοντα κλιμάκωσης 80 % σε άλλη τιμή;
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Αλλαγή μεγέθους Word Chart κατά τη μετάβαση σε A4
og_description: Διατηρήστε το chart σας ανάλογο αλλάζοντας αυτόματα το μέγεθός του μετά την αλλαγή του εγγράφου σε A4.
og_image_alt: Στιγμιότυπο οθόνης που δείχνει ένα column chart να αλλάζει αυτόματα το μέγεθός του ώστε να ταιριάζει σε ένα έγγραφο Word μεγέθους A4 χρησιμοποιώντας Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αλλαγή μεγέθους Chart αναλογικά κατά την αλλαγή μεγέθους σελίδας στο Word χρησιμοποιώντας Aspose.Words
Αυτό το tutorial δείχνει πώς να εισάγετε ένα column chart σε ένα έγγραφο Word, να αλλάξετε το μέγεθος σελίδας του εγγράφου σε A4 και να κάνετε το chart να αλλάζει αυτόματα το μέγεθός του ώστε να παραμένει ανάλογο με το νέο πλάτος της σελίδας. Ακολουθώντας τα βήματα, θα δείτε το chart να προσαρμόζει τις διαστάσεις του χωρίς χειροκίνητη κλιμάκωση, εξασφαλίζοντας μια συνεπή διάταξη σε διαφορετικές μορφές σελίδας.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Χρειάζεται να αλλάξω χειροκίνητα το μέγεθος του chart μετά την αλλαγή του μεγέθους χαρτιού του εγγράφου;**  
A: Ναι. Η αλλαγή του `docBuilder.PageSetup.PaperSize` δεν προσαρμόζει αυτόματα τα υπάρχοντα shapes, επομένως πρέπει να επαναϋπολογίσετε και να ορίσετε το `chartContainer.Width` και `Height` εσείς όπως φαίνεται.

**Q: Πώς διατηρεί ο κώδικας την αρχική αναλογία πλάτους‑προς‑ύψος του chart κατά την αλλαγή μεγέθους;**  
A: Αποθηκεύει `originalAspectRatio = chartContainer.Height / chartContainer.Width` και στη συνέχεια υπολογίζει `newChartHeight = newChartWidth * originalAspectRatio` αφού καθορίσει το νέο πλάτος.

**Q: Γιατί καλείται το `myDoc.UpdatePageLayout()` μετά τον ορισμό του μεγέθους χαρτιού σε A4;**  
A: `UpdatePageLayout()` αναγκάζει τη μηχανή διάταξης να επανεκτιμήσει τις διαστάσεις της σελίδας, διασφαλίζοντας ότι το `docBuilder.PageSetup.PageWidth` αντικατοπτρίζει το νέο πλάτος A4 πριν επαναϋπολογιστεί το μέγεθος του chart.

**Q: Τι συμβαίνει αν το εισαχθέν shape δεν περιέχει στην πραγματικότητα ένα chart;**  
A: Η προϋπόθεση `if (chartContainer.HasChart)` αποτρέπει τον κώδικα από το να ορίσει `Width` και `Height` όταν δεν υπάρχει chart, αποφεύγοντας μια εξαίρεση χρόνου εκτέλεσης.

**Q: Μπορώ να αλλάξω τον παράγοντα κλιμάκωσης 80 % σε άλλη τιμή;**  
A: Απολύτως—αντικαταστήστε τον πολλαπλασιαστή `0.8` με οποιαδήποτε αναλογία προτιμάτε· η υπόλοιπη λογική αλλαγής μεγέθους θα διατηρήσει ακόμα την αρχική αναλογία διαστάσεων.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}