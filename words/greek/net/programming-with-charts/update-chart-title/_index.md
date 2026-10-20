---
title: Ενημέρωση του τίτλου του διαγράμματος και εναλλαγή της ορατότητας του υπομνήματος στο Word χρησιμοποιώντας το Aspose.Words for .NET
weight: 810
limit:
description: Μάθετε να αλλάζετε τον τίτλο ενός διαγράμματος και να ελέγχετε την ορατότητα του υπομνήματος σε ένα έγγραφο Word με το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Μάθετε να αλλάζετε τον τίτλο ενός διαγράμματος και να ελέγχετε την
    ορατότητα του υπομνήματος σε ένα έγγραφο Word με το Aspose.Words for .NET.
  headline: Ενημέρωση του τίτλου του διαγράμματος και εναλλαγή της ορατότητας του
    υπομνήματος στο Word χρησιμοποιώντας το Aspose.Words for .NET
  type: TechArticle
- description: Μάθετε να αλλάζετε τον τίτλο ενός διαγράμματος και να ελέγχετε την
    ορατότητα του υπομνήματος σε ένα έγγραφο Word με το Aspose.Words for .NET.
  name: Ενημέρωση του τίτλου του διαγράμματος και εναλλαγή της ορατότητας του υπομνήματος
    στο Word χρησιμοποιώντας το Aspose.Words for .NET
  steps:
  - name: Ορίστε τον τίτλο του διαγράμματος που παρέχεται από τον χρήστη και αν πρέπει
      να εμφανίζεται το υπόμνημα.
    text: Ορίστε τον τίτλο του διαγράμματος που παρέχεται από τον χρήστη και αν πρέπει
      να εμφανίζεται το υπόμνημα.
  - name: Δημιουργήστε ένα νέο έγγραφο Word και ένα DocumentBuilder για να προσθέσετε
      περιεχόμενο.
    text: Δημιουργήστε ένα νέο έγγραφο Word και ένα DocumentBuilder για να προσθέσετε
      περιεχόμενο.
  - name: Εισάγετε ένα διάγραμμα στήλης 432 × 252 pt στο έγγραφο και επαληθεύστε ότι
      το σχήμα περιέχει πραγματικά ένα διάγραμμα.
    text: Εισάγετε ένα διάγραμμα στήλης 432 × 252 pt στο έγγραφο και επαληθεύστε ότι
      το σχήμα περιέχει πραγματικά ένα διάγραμμα.
  - name: Ανακτήστε το αντικείμενο chart, ορίστε το κείμενο του τίτλου του στην τιμή
      που δόθηκε από τον χρήστη και εξασφαλίστε ότι ο τίτλος εμφανίζεται.
    text: Ανακτήστε το αντικείμενο chart, ορίστε το κείμενο του τίτλου του στην τιμή
      που δόθηκε από τον χρήστη και εξασφαλίστε ότι ο τίτλος εμφανίζεται.
  - name: 'Διαμορφώστε το υπόμνημα: εμφανίστε το στα δεξιά αν ζητηθεί, διαφορετικά
      κρύψτε το, και επιτρέψτε του να επικαλύπτει την περιοχή σχεδίασης.'
    text: 'Διαμορφώστε το υπόμνημα: εμφανίστε το στα δεξιά αν ζητηθεί, διαφορετικά
      κρύψτε το, και επιτρέψτε του να επικαλύπτει την περιοχή σχεδίασης.'
  - name: Αποθηκεύστε το τροποποιημένο έγγραφο στο δίσκο ως CustomChart.docx.
    text: Αποθηκεύστε το τροποποιημένο έγγραφο στο δίσκο ως CustomChart.docx.
  type: HowTo
- questions:
  - answer: Όταν το `displayLegend` είναι `true`, ο κώδικας ορίζει το `chartLegend.Position`
      σε `LegendPosition.Right`, καθιστώντας το υπόμνημα ορατό στη δεξιά πλευρά της
      περιοχής σχεδίασης· η ιδιότητα `Overlay` παραμένει `true`, ώστε το υπόμνημα
      να μπορεί να επικαλύπτει το διάγραμμα για εξοικονόμηση χώρου.
    question: Τι αλλάζει η ρύθμιση του `displayLegend` σε `true` στο παραγόμενο διάγραμμα;
  - answer: Ορίστε `chartTitle.Show = false` (ή απλώς παραλείψτε τον ορισμό του `Show`
      σε `true`) μετά την ανάθεση του `chartTitle.Text`; ο τίτλος δεν θα αποδοθεί
      στο έγγραφο Word.
    question: Πώς μπορώ να κρύψω τον τίτλο του διαγράμματος αν ο χρήστης δεν παρέχει
      κάποιον;
  - answer: Ναι—το `InsertChart` επιστρέφει ένα `Shape` που θα πρέπει να περιέχει
      ένα διάγραμμα, αλλά η επαλήθευση του `HasChart` διασφαλίζει ότι το σχήμα πραγματικά
      κρατά ένα αντικείμενο `Chart`; διαφορετικά ο κώδικας ρίχνει ένα `InvalidOperationException`.
    question: Είναι απαραίτητο να ελέγξετε το `chartContainer.HasChart` μετά την κλήση
      του `InsertChart`;
  - answer: Απολύτως· ορίστε οποιαδήποτε τιμή από το enum `LegendPosition` (π.χ.,
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) στο `chartLegend.Position`
      για να μετατοπίσετε το υπόμνημα όπως απαιτείται.
    question: Μπορώ να τοποθετήσω το υπόμνημα κάπου εκτός της δεξιάς πλευράς;
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Αλλαγή τίτλου διαγράμματος & υπομνήματος στο Word
og_description: Μάθετε να ορίζετε έναν προσαρμοσμένο τίτλο διαγράμματος και να ελέγχετε την εμφάνιση του υπομνήματος σε ένα έγγραφο Word με το Aspose.Words for .NET.
og_image_alt: Οδηγός που δείχνει κώδικα που ενημερώνει τον τίτλο ενός διαγράμματος και εναλλάσσει το υπόμνημα σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ενημέρωση του τίτλου του διαγράμματος και εναλλαγή της ορατότητας του υπομνήματος στο Word χρησιμοποιώντας το Aspose.Words
Αυτό το σεμινάριο δείχνει πώς να τροποποιήσετε προγραμματιστικά ένα διάγραμμα μέσα σε ένα έγγραφο Word με το Aspose.Words for .NET. Θα μάθετε να εισάγετε ένα διάγραμμα στήλης, να αντικαταστήσετε τον τίτλο του με κείμενο που παρέχεται από τον χρήστη και να ελέγξετε την ορατότητα και την επικάλυψη του υπομνήματος βάσει των προτιμήσεων του χρήστη. Αυτά τα βήματα σας επιτρέπουν να προσαρμόζετε την παρουσίαση του διαγράμματος δυναμικά χωρίς χειροκίνητη επεξεργασία.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Τι αλλάζει η ρύθμιση του `displayLegend` σε `true` στο παραγόμενο διάγραμμα;**  
A: Όταν το `displayLegend` είναι `true`, ο κώδικας ορίζει το `chartLegend.Position` σε `LegendPosition.Right`, καθιστώντας το υπόμνημα ορατό στη δεξιά πλευρά της περιοχής σχεδίασης· η ιδιότητα `Overlay` παραμένει `true`, ώστε το υπόμνημα να μπορεί να επικαλύπτει το διάγραμμα για εξοικονόμηση χώρου.

**Q: Πώς μπορώ να κρύψω τον τίτλο του διαγράμματος αν ο χρήστης δεν παρέχει κάποιον;**  
A: Ορίστε `chartTitle.Show = false` (ή απλώς παραλείψτε τον ορισμό του `Show` σε `true`) μετά την ανάθεση του `chartTitle.Text`; ο τίτλος δεν θα αποδοθεί στο έγγραφο Word.

**Q: Είναι απαραίτητο να ελέγξετε το `chartContainer.HasChart` μετά την κλήση του `InsertChart`;**  
A: Ναι—το `InsertChart` επιστρέφει ένα `Shape` που θα πρέπει να περιέχει ένα διάγραμμα, αλλά η επαλήθευση του `HasChart` διασφαλίζει ότι το σχήμα πραγματικά κρατά ένα αντικείμενο `Chart`; διαφορετικά ο κώδικας ρίχνει ένα `InvalidOperationException`.

**Q: Μπορώ να τοποθετήσω το υπόμνημα κάπου εκτός της δεξιάς πλευράς;**  
A: Απολύτως· ορίστε οποιαδήποτε τιμή από το enum `LegendPosition` (π.χ., `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) στο `chartLegend.Position` για να μετατοπίσετε το υπόμνημα όπως απαιτείται.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}