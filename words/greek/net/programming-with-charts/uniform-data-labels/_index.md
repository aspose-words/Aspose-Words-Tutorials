---
title: Ορισμός ομοιόμορφων ετικετών δεδομένων σε γράφημα στήλης με χρήση του Aspose.Words for .NET
weight: 110
limit:
description: Μάθετε πώς να δημιουργήσετε ένα γράφημα στήλης Word και να εφαρμόσετε ομοιόμορφο μέγεθος γραμματοσειράς και χρώμα ετικέτας δεδομένων σε όλες τις σειρές με το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Μάθετε πώς να δημιουργήσετε ένα γράφημα στήλης Word και να εφαρμόσετε
    ομοιόμορφο μέγεθος γραμματοσειράς και χρώμα ετικέτας δεδομένων σε όλες τις σειρές
    με το Aspose.Words for .NET.
  headline: Ορισμός ομοιόμορφων ετικετών δεδομένων σε γράφημα στήλης με χρήση του
    Aspose.Words for .NET
  type: TechArticle
- description: Μάθετε πώς να δημιουργήσετε ένα γράφημα στήλης Word και να εφαρμόσετε
    ομοιόμορφο μέγεθος γραμματοσειράς και χρώμα ετικέτας δεδομένων σε όλες τις σειρές
    με το Aspose.Words for .NET.
  name: Ορισμός ομοιόμορφων ετικετών δεδομένων σε γράφημα στήλης με χρήση του Aspose.Words
    for .NET
  steps:
  - name: Δημιουργήστε ένα νέο κενό έγγραφο Word και ένα DocumentBuilder για να το
      επεξεργαστείτε.
    text: Δημιουργήστε ένα νέο κενό έγγραφο Word και ένα DocumentBuilder για να το
      επεξεργαστείτε.
  - name: Εισάγετε ένα γράφημα στήλης 500×300 στο έγγραφο και αποκτήστε το αντικείμενο
      Chart.
    text: Εισάγετε ένα γράφημα στήλης 500×300 στο έγγραφο και αποκτήστε το αντικείμενο
      Chart.
  - name: Αφαιρέστε τη προεπιλεγμένη σειρά δείγματος που προσθέτει το Aspose.Words
      σε ένα νέο γράφημα.
    text: Αφαιρέστε τη προεπιλεγμένη σειρά δείγματος που προσθέτει το Aspose.Words
      σε ένα νέο γράφημα.
  - name: Ορίστε ετικέτες κατηγοριών και προσθέστε δύο σειρές δεδομένων (Item Alpha
      και Item Beta) με τις τιμές τους στο γράφημα.
    text: Ορίστε ετικέτες κατηγοριών και προσθέστε δύο σειρές δεδομένων (Item Alpha
      και Item Beta) με τις τιμές τους στο γράφημα.
  - name: Ορίστε το βασικό μέγεθος γραμματοσειράς και χρώμα που θα εφαρμοστούν σε
      όλες τις ετικέτες δεδομένων.
    text: Ορίστε το βασικό μέγεθος γραμματοσειράς και χρώμα που θα εφαρμοστούν σε
      όλες τις ετικέτες δεδομένων.
  - name: Ενεργοποιήστε τις ετικέτες δεδομένων για κάθε σειρά, εμφανίστε την αριθμητική
      τιμή και εφαρμόστε το προκαθορισμένο μέγεθος γραμματοσειράς και χρώμα.
    text: Ενεργοποιήστε τις ετικέτες δεδομένων για κάθε σειρά, εμφανίστε την αριθμητική
      τιμή και εφαρμόστε το προκαθορισμένο μέγεθος γραμματοσειράς και χρώμα.
  - name: Αποθηκεύστε το έγγραφο σε αρχείο .docx.
    text: Αποθηκεύστε το έγγραφο σε αρχείο .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` δημιουργεί ένα γράφημα με μια προεπιλεγμένη σειρά δείγματος·
      η εκκαθάριση της αφαιρεί αυτό το placeholder ώστε το γράφημα να εμφανίζει μόνο
      τις σειρές που προσθέτετε (`Item Alpha` και `Item Beta`).'
    question: Γιατί πρέπει να καλέσω το `chart.Series.Clear()` πριν προσθέσω τις δικές
      μου σειρές;
  - answer: Αντικαταστήστε το `Color.White` με οποιαδήποτε τιμή `System.Drawing.Color`,
      π.χ., `Color.Black` ή `Color.FromArgb(255, 30, 144, 255)`· το νέο χρώμα εφαρμόζεται
      μέσω του `series.DataLabels.Font.Color` μέσα στον βρόχο.
    question: Πώς μπορώ να αλλάξω το χρώμα της ετικέτας δεδομένων σε κάτι διαφορετικό
      από το λευκό;
  - answer: Οι ετικέτες δεδομένων θα κρυφτούν, έτσι οι ρυθμίσεις γραμματοσειράς που
      εφαρμόσατε θα γίνουν αόρατες· πρέπει να διατηρήσετε το `HasDataLabels` σε `true`
      ώστε οι ετικέτες (και το στυλ τους) να εμφανιστούν.
    question: Τι συμβαίνει αν ορίσω `series.HasDataLabels = false` μετά τη διαμόρφωση
      του μεγέθους γραμματοσειράς και του χρώματος;
  - answer: Ναι—κάθε `ChartSeries` έχει το δικό του αντικείμενο `DataLabels`, επομένως
      οποιαδήποτε σειρά προστεθεί μετά τον αρχικό βρόχο πρέπει επίσης να έχει ορισμένα
      `HasDataLabels`, `ShowValue` και τις ιδιότητες γραμματοσειράς, είτε επαναλαμβάνοντας
      τη βρόχο είτε εξάγοντας το στυλ σε μια βοηθητική μέθοδο.
    question: Πρέπει να επαναλάβω τη βρόχο στις σειρές αν προσθέσω άλλη σειρά αργότερα
      στον κώδικα;
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Εφαρμογή ομοιόμορφων ετικετών δεδομένων σε γράφημα Word
og_description: Δώστε γρήγορα σε κάθε ετικέτα γραφήματος το ίδιο μέγεθος γραμματοσειράς και χρώμα με το Aspose.Words for .NET.
og_image_alt: Οδηγός που δείχνει ένα έγγραφο Word με γράφημα στήλης όπου όλες οι ετικέτες δεδομένων μοιράζονται το ίδιο μέγεθος γραμματοσειράς και χρώμα, δημιουργημένο με το Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός ομοιόμορφων ετικετών δεδομένων σε γράφημα στήλης με χρήση του Aspose.Words
Αυτό το σεμινάριο δείχνει πώς να δημιουργήσετε ένα έγγραφο Word, να εισάγετε ένα γράφημα στήλης και να προσθέσετε προσαρμοσμένες σειρές δεδομένων με το Aspose.Words for .NET. Στη συνέχεια, δείχνει πώς να ορίσετε το προεπιλεγμένο μέγεθος γραμματοσειράς και χρώμα ετικέτας δεδομένων ώστε κάθε σειρά στο γράφημα να εμφανίζει ταυτόσημες ετικέτες. Εφαρμόζοντας ένα ενιαίο στυλ, εξασφαλίζετε συνεπή οπτική εμφάνιση σε όλο το γράφημα.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Γιατί πρέπει να καλέσω το `chart.Series.Clear()` πριν προσθέσω τις δικές μου σειρές;**  
A: `InsertChart` δημιουργεί ένα γράφημα με μια προεπιλεγμένη σειρά δείγματος· η εκκαθάριση της αφαιρεί αυτό το placeholder ώστε το γράφημα να εμφανίζει μόνο τις σειρές που προσθέτετε (`Item Alpha` και `Item Beta`).

**Q: Πώς μπορώ να αλλάξω το χρώμα της ετικέτας δεδομένων σε κάτι διαφορετικό από το λευκό;**  
A: Αντικαταστήστε το `Color.White` με οποιαδήποτε τιμή `System.Drawing.Color`, π.χ., `Color.Black` ή `Color.FromArgb(255, 30, 144, 255)`· το νέο χρώμα εφαρμόζεται μέσω του `series.DataLabels.Font.Color` μέσα στον βρόχο.

**Q: Τι συμβαίνει αν ορίσω `series.HasDataLabels = false` μετά τη διαμόρφωση του μεγέθους γραμματοσειράς και του χρώματος;**  
A: Οι ετικέτες δεδομένων θα κρυφτούν, έτσι οι ρυθμίσεις γραμματοσειράς που εφαρμόσατε θα γίνουν αόρατες· πρέπει να διατηρήσετε το `HasDataLabels` σε `true` ώστε οι ετικέτες (και το στυλ τους) να εμφανιστούν.

**Q: Πρέπει να επαναλάβω τη βρόχο στις σειρές αν προσθέσω άλλη σειρά αργότερα στον κώδικα;**  
A: Ναι—κάθε `ChartSeries` έχει το δικό του αντικείμενο `DataLabels`, επομένως οποιαδήποτε σειρά προστεθεί μετά τον αρχικό βρόχο πρέπει επίσης να έχει ορισμένα `HasDataLabels`, `ShowValue` και τις ιδιότητες γραμματοσειράς, είτε επαναλαμβάνοντας τη βρόχο είτε εξάγοντας το στυλ σε μια βοηθητική μέθοδο.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}