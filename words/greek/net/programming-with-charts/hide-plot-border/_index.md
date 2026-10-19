---
title: Απόκρυψη περιγράμματος περιοχής σχεδίασης σε γράφημα στήλης με Aspose.Words for .NET
weight: 410
limit:
description: Μάθετε πώς να κρύψετε το περίγραμμα της περιοχής σχεδίασης ενός γραφήματος ενώ διατηρείτε τις γραμμές των αξόνων ορατές σε γράφημα στήλης Word χρησιμοποιώντας Aspose.Words for .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Μάθετε πώς να κρύψετε το περίγραμμα της περιοχής σχεδίασης ενός γραφήματος
    ενώ διατηρείτε τις γραμμές των αξόνων ορατές σε γράφημα στήλης Word χρησιμοποιώντας
    Aspose.Words for .NET.
  headline: Απόκρυψη περιγράμματος περιοχής σχεδίασης σε γράφημα στήλης με Aspose.Words
    for .NET
  type: TechArticle
- description: Μάθετε πώς να κρύψετε το περίγραμμα της περιοχής σχεδίασης ενός γραφήματος
    ενώ διατηρείτε τις γραμμές των αξόνων ορατές σε γράφημα στήλης Word χρησιμοποιώντας
    Aspose.Words for .NET.
  name: Απόκρυψη περιγράμματος περιοχής σχεδίασης σε γράφημα στήλης με Aspose.Words
    for .NET
  steps:
  - name: Δημιουργήστε ένα νέο κενό έγγραφο Word και έναν DocumentBuilder για να το
      επεξεργαστείτε.
    text: Δημιουργήστε ένα νέο κενό έγγραφο Word και έναν DocumentBuilder για να το
      επεξεργαστείτε.
  - name: Εισάγετε ένα γράφημα στήλης 432×252 στο έγγραφο και αποκτήστε το αντικείμενο
      Chart.
    text: Εισάγετε ένα γράφημα στήλης 432×252 στο έγγραφο και αποκτήστε το αντικείμενο
      Chart.
  - name: Καθαρίστε τυχόν υπάρχουσες σειρές, ορίστε τρεις ετικέτες κατηγοριών και
      προσθέστε μια σειρά με δείγμα τιμών στο γράφημα.
    text: Καθαρίστε τυχόν υπάρχουσες σειρές, ορίστε τρεις ετικέτες κατηγοριών και
      προσθέστε μια σειρά με δείγμα τιμών στο γράφημα.
  - name: Ορίστε το βάρος του περιγράμματος (stroke) της περιοχής σχεδίασης σε μηδέν,
      αφαιρώντας το περίγραμμα ενώ οι γραμμές των αξόνων παραμένουν ορατές.
    text: Ορίστε το βάρος του περιγράμματος (stroke) της περιοχής σχεδίασης σε μηδέν,
      αφαιρώντας το περίγραμμα ενώ οι γραμμές των αξόνων παραμένουν ορατές.
  - name: Αποθηκεύστε το τροποποιημένο έγγραφο σε αρχείο .docx.
    text: Αποθηκεύστε το τροποποιημένο έγγραφο σε αρχείο .docx.
  type: HowTo
- questions:
  - answer: Η ιδιότητα `Stroke` ανήκει στη συνολική μορφοποίηση του αντικειμένου `Chart`,
      η οποία σχεδιάζει το ορθογώνιο περίγραμμα γύρω από την περιοχή σχεδίασης· οι
      γραμμές των αξόνων είναι ξεχωριστά αντικείμενα `Axis` και δεν επηρεάζονται από
      τις ρυθμίσεις `Stroke` του γραφήματος.
    question: Γιατί η ρύθμιση `columnChart.Format.Stroke.Weight = 0` αφαιρεί το περίγραμμα
      της περιοχής σχεδίασης αλλά αφήνει τις γραμμές των αξόνων ορατές;
  - answer: Όχι, η ιδιότητα `Stroke` ελέγχει ολόκληρο το περίγραμμα της περιοχής σχεδίασης
      ως ένα ενιαίο ορθογώνιο, επομένως δεν είναι δυνατόν να κρυφτούν μερικά τμήματα
      του περιγράμματος μέσω Aspose.Words· θα πρέπει να προσθέσετε προσαρμοσμένα σχήματα
      ή να επεξεργαστείτε το γράφημα χειροκίνητα.
    question: Μπορώ να κρύψω μόνο μία πλευρά του περιγράμματος της περιοχής σχεδίασης
      (π.χ. την αριστερή) ενώ διατηρώ τις άλλες τρεις πλευρές ορατές;
  - answer: Ναι, η ιδιότητα `Stroke` είναι ανεξάρτητη από το `ChartType`, επομένως
      ο καθορισμός του `Weight` σε 0 αφαιρεί το περίγραμμα της περιοχής σχεδίασης
      για Γραμμή, Πίτα ή οποιονδήποτε άλλο υποστηριζόμενο τύπο γραφήματος.
    question: Αν αλλάξω τον τύπο του γραφήματος σε Γραμμή ή Πίτα, θα εξακολουθεί η
      ρύθμιση `columnChart.Format.Stroke.Weight = 0` να κρύβει το περίγραμμα της περιοχής
      σχεδίασης;
  - answer: Δεν απαιτείται πρόσθετη ανανέωση· η εκκαθάριση των σειρών και η προσθήκη
      μιας νέας ενημερώνει το γράφημα εσωτερικά, και το `wordDoc.Save(...)` γράφει
      την τρέχουσα κατάσταση στο αρχείο .docx.
    question: Μετά την κλήση `columnChart.Series.Clear()`, χρειάζεται να ανανεώσω
      το γράφημα πριν αποθηκεύσω το έγγραφο;
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Απόκρυψη περιγράμματος περιοχής σχεδίασης σε γράφημα στήλης Word
og_description: Αφαιρέστε το περίγραμμα της περιοχής σχεδίασης ενώ διατηρείτε τις γραμμές των αξόνων ορατές σε γράφημα στήλης Word χρησιμοποιώντας Aspose.Words for .NET.
og_image_alt: Οδηγός που δείχνει ένα έγγραφο Word με γράφημα στήλης όπου το περίγραμμα της περιοχής σχεδίασης είναι κρυμμένο αλλά οι γραμμές των αξόνων παραμένουν ορατές, χρησιμοποιώντας Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Απόκρυψη περιγράμματος περιοχής σχεδίασης σε γράφημα στήλης με Aspose.Words
Σε αυτό το σεμινάριο θα μάθετε πώς να δημιουργήσετε ένα έγγραφο Word, να εισάγετε ένα γράφημα στήλης, να το γεμίσετε με δείγμα δεδομένων και στη συνέχεια να κρύψετε το περίγραμμα της περιοχής σχεδίασης του γραφήματος ενώ διατηρείτε τις γραμμές των αξόνων ορατές. Ο κώδικας βήμα‑βήμα δείχνει κάθε λειτουργία και ολοκληρώνεται με την αποθήκευση του εγγράφου, ώστε να δείτε το αποτέλεσμα αμέσως.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: Γιατί η ρύθμιση `columnChart.Format.Stroke.Weight = 0` αφαιρεί το περίγραμμα της περιοχής σχεδίασης αλλά αφήνει τις γραμμές των αξόνων ορατές;**  
A: Η ιδιότητα `Stroke` ανήκει στη συνολική μορφοποίηση του αντικειμένου `Chart`, η οποία σχεδιάζει το ορθογώνιο περίγραμμα γύρω από την περιοχή σχεδίασης· οι γραμμές των αξόνων είναι ξεχωριστά αντικείμενα `Axis` και δεν επηρεάζονται από τις ρυθμίσεις `Stroke` του γραφήματος.

**Q: Μπορώ να κρύψω μόνο μία πλευρά του περιγράμματος της περιοχής σχεδίασης (π.χ. την αριστερή) ενώ διατηρώ τις άλλες τρεις πλευρές ορατές;**  
A: Όχι, η ιδιότητα `Stroke` ελέγχει ολόκληρο το περίγραμμα της περιοχής σχεδίασης ως ένα ενιαίο ορθογώνιο, επομένως δεν είναι δυνατόν να κρυφτούν μερικά τμήματα του περιγράμματος μέσω Aspose.Words· θα πρέπει να προσθέσετε προσαρμοσμένα σχήματα ή να επεξεργαστείτε το γράφημα χειροκίνητα.

**Q: Αν αλλάξω τον τύπο του γραφήματος σε Γραμμή ή Πίτα, θα εξακολουθεί η ρύθμιση `columnChart.Format.Stroke.Weight = 0` να κρύβει το περίγραμμα της περιοχής σχεδίασης;**  
A: Ναι, η ιδιότητα `Stroke` είναι ανεξάρτητη από το `ChartType`, επομένως ο καθορισμός του `Weight` σε 0 αφαιρεί το περίγραμμα της περιοχής σχεδίασης για Γραμμή, Πίτα ή οποιονδήποτε άλλο υποστηριζόμενο τύπο γραφήματος.

**Q: Μετά την κλήση `columnChart.Series.Clear()`, χρειάζεται να ανανεώσω το γράφημα πριν αποθηκεύσω το έγγραφο;**  
A: Δεν απαιτείται πρόσθετη ανανέωση· η εκκαθάριση των σειρών και η προσθήκη μιας νέας ενημερώνει το γράφημα εσωτερικά, και το `wordDoc.Save(...)` γράφει την τρέχουσα κατάσταση στο αρχείο .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}