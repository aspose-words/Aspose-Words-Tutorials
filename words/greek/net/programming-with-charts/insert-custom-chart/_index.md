---
title: Εισαγωγή προσαρμοσμένου γραφήματος στήλης σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
weight: 310
limit:
description: Δημιουργήστε ένα αρχείο Word, εισάγετε ένα γράφημα στήλης, αντικαταστήστε τα δεδομένα του με έναν προσαρμοσμένο πίνακα, προσθέστε έναν τίτλο και αποθηκεύστε—όλα με το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Δημιουργήστε ένα αρχείο Word, εισάγετε ένα γράφημα στήλης, αντικαταστήστε
    τα δεδομένα του με έναν προσαρμοσμένο πίνακα, προσθέστε έναν τίτλο και αποθηκεύστε—όλα
    με το Aspose.Words for .NET.
  headline: Εισαγωγή προσαρμοσμένου γραφήματος στήλης σε έγγραφο Word χρησιμοποιώντας
    το Aspose.Words for .NET
  type: TechArticle
- description: Δημιουργήστε ένα αρχείο Word, εισάγετε ένα γράφημα στήλης, αντικαταστήστε
    τα δεδομένα του με έναν προσαρμοσμένο πίνακα, προσθέστε έναν τίτλο και αποθηκεύστε—όλα
    με το Aspose.Words for .NET.
  name: Εισαγωγή προσαρμοσμένου γραφήματος στήλης σε έγγραφο Word χρησιμοποιώντας
    το Aspose.Words for .NET
  steps:
  - name: Δημιουργήστε ένα νέο Document και ένα DocumentBuilder που είναι συνδεδεμένο
      σε αυτό.
    text: Δημιουργήστε ένα νέο Document και ένα DocumentBuilder που είναι συνδεδεμένο
      σε αυτό.
  - name: Εισάγετε ένα γράφημα στήλης μεγέθους 432x252 points στο έγγραφο και αποκτήστε
      το αντικείμενο Chart του.
    text: Εισάγετε ένα γράφημα στήλης μεγέθους 432x252 points στο έγγραφο και αποκτήστε
      το αντικείμενο Chart του.
  - name: Αφαιρέστε τις αυτόματα δημιουργημένες δείγματες σειρές από το γράφημα.
    text: Αφαιρέστε τις αυτόματα δημιουργημένες δείγματες σειρές από το γράφημα.
  - name: Ορίστε τις ετικέτες κατηγοριών του άξονα X και τις καταχωρήσεις του υπομνήματος
      για κάθε σειρά.
    text: Ορίστε τις ετικέτες κατηγοριών του άξονα X και τις καταχωρήσεις του υπομνήματος
      για κάθε σειρά.
  - name: Δημιουργήστε έναν δισδιάστατο πίνακα όπου κάθε γραμμή περιέχει τις τιμές
      για μία σειρά.
    text: Δημιουργήστε έναν δισδιάστατο πίνακα όπου κάθε γραμμή περιέχει τις τιμές
      για μία σειρά.
  - name: Επαναλάβετε για κάθε σειρά, εξάγετε τις τιμές της γραμμής από τον πίνακα
      και προσθέστε τη σειρά στο γράφημα με την αντίστοιχη καταχώρηση του υπομνήματος
      και τις ετικέτες του άξονα X.
    text: Επαναλάβετε για κάθε σειρά, εξάγετε τις τιμές της γραμμής από τον πίνακα
      και προσθέστε τη σειρά στο γράφημα με την αντίστοιχη καταχώρηση του υπομνήματος
      και τις ετικέτες του άξονα X.
  - name: Ορίστε το κείμενο του τίτλου του γραφήματος σε 'Half‑Yearly Revenue' και
      κάντε το ορατό.
    text: Ορίστε το κείμενο του τίτλου του γραφήματος σε 'Half‑Yearly Revenue' και
      κάντε το ορατό.
  - name: Αποθηκεύστε το έγγραφο που περιέχει το προσαρμοσμένο γράφημα σε αρχείο .docx.
    text: Αποθηκεύστε το έγγραφο που περιέχει το προσαρμοσμένο γράφημα σε αρχείο .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` αναμένει το μήκος του πίνακα τιμών να ισούται με τον
      αριθμό των ετικετών του άξονα X, και πρέπει να προσθέτετε ακριβώς μία σειρά
      ανά καταχώρηση υπομνήματος· μια ασυμφωνία θα προκαλέσει `ArgumentException`
      κατά την εκτέλεση.'
    question: Τι γίνεται αν οι γραμμές ή οι στήλες στο `dataMatrix` δεν ταιριάζουν
      με τα μήκη των `legendEntries` ή των `xLabels`;
  - answer: Ναι—αντικαταστήστε το `ChartType.Column` στο `docBuilder.InsertChart`
      με οποιοδήποτε άλλο `ChartType` (π.χ., `ChartType.Line`) και οι επόμενες κλήσεις
      `Series.Add` θα γεμίσουν το νέο γράφημα με τον ίδιο τρόπο.
    question: Μπορώ να χρησιμοποιήσω διαφορετικό τύπο γραφήματος, όπως ένα γράφημα
      γραμμής, με την ίδια λογική πληρωμής δεδομένων;
  - answer: Ρυθμίστε τις ιδιότητες `Width` και `Height` του `Shape` που επιστρέφεται
      από το `InsertChart` (π.χ., `chartContainer.Width = 500; chartContainer.Height
      = 300;`).
    question: Πώς μπορώ να αλλάξω το μέγεθος του γραφήματος μετά την εισαγωγή του;
  - answer: Ορίστε `chartObj.Series[i].HasDataLabel = true;` για κάθε σειρά μετά την
      προσθήκη της, ή κάντε βρόχο μέσω του `chartObj.Series` και ενεργοποιήστε το
      `HasDataLabel` για να εμφανίσετε τις τιμές στο γράφημα.
    question: Υπάρχει γρήγορος τρόπος να εμφανίσετε ετικέτες δεδομένων σε κάθε στήλη
      του γραφήματος;
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Προσθήκη προσαρμοσμένου γραφήματος στήλης σε έγγραφο Word
og_description: Αντικαταστήστε τα προεπιλεγμένα δεδομένα ενός γραφήματος με τον δικό σας πίνακα και ορίστε έναν τίτλο σε δευτερόλεπτα.
og_image_alt: Στιγμιότυπο οθόνης που δείχνει ένα έγγραφο Word με προσαρμοσμένο γράφημα στήλης που δημιουργήθηκε χρησιμοποιώντας το Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή προσαρμοσμένου γραφήματος στήλης σε έγγραφο Word χρησιμοποιώντας το Aspose.Words
Αυτό το σεμινάριο σας καθοδηγεί στη δημιουργία ενός εγγράφου Word, την εισαγωγή ενός γραφήματος στήλης, τη διαγραφή των προεπιλεγμένων δεδομένων του και την πλήρωση του γραφήματος με προσαρμοσμένες τιμές από έναν δισδιάστατο πίνακα—αντιστοιχίζοντας κάθε γραμμή σε μια σειρά και κάθε στήλη σε μια κατηγορία. Θα δείτε επίσης πώς να προσθέσετε έναν τίτλο γραφήματος πριν αποθηκεύσετε το αρχείο. Ακολουθήστε τα βήματα για να δημιουργήσετε ένα πλήρως προσαρμοσμένο γράφημα απευθείας στο αρχείο Word σας.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Τι γίνεται αν οι γραμμές ή οι στήλες στο `dataMatrix` δεν ταιριάζουν με τα μήκη των `legendEntries` ή των `xLabels`;**  
A: `Chart.Series.Add` αναμένει το μήκος του πίνακα τιμών να ισούται με τον αριθμό των ετικετών του άξονα X, και πρέπει να προσθέτετε ακριβώς μία σειρά ανά καταχώρηση υπομνήματος· μια ασυμφωνία θα προκαλέσει `ArgumentException` κατά την εκτέλεση.

**Q: Μπορώ να χρησιμοποιήσω διαφορετικό τύπο γραφήματος, όπως ένα γράφημα γραμμής, με την ίδια λογική πληρωμής δεδομένων;**  
A: Ναι—αντικαταστήστε το `ChartType.Column` στο `docBuilder.InsertChart` με οποιοδήποτε άλλο `ChartType` (π.χ., `ChartType.Line`) και οι επόμενες κλήσεις `Series.Add` θα γεμίσουν το νέο γράφημα με τον ίδιο τρόπο.

**Q: Πώς μπορώ να αλλάξω το μέγεθος του γραφήματος μετά την εισαγωγή του;**  
A: Ρυθμίστε τις ιδιότητες `Width` και `Height` του `Shape` που επιστρέφεται από το `InsertChart` (π.χ., `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Υπάρχει γρήγορος τρόπος να εμφανίσετε ετικέτες δεδομένων σε κάθε στήλη του γραφήματος;**  
A: Ορίστε `chartObj.Series[i].HasDataLabel = true;` για κάθε σειρά μετά την προσθήκη της, ή κάντε βρόχο μέσω του `chartObj.Series` και ενεργοποιήστε το `HasDataLabel` για να εμφανίσετε τις τιμές στο γράφημα.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}