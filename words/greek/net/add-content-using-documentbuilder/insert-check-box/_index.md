---
title: Προσθήκη πεδίου φόρμας τύπου πλαίσιο ελέγχου σε έγγραφο Word με το Aspose.Words for .NET
weight: 210
limit:
description: Μάθετε πώς να προσθέσετε προγραμματιστικά ένα πεδίο φόρμας τύπου πλαίσιο ελέγχου σε ένα νέο έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET και να αποθηκεύσετε το αρχείο.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη πεδίου φόρμας τύπου πλαίσιο ελέγχου σε έγγραφο Word με το Aspose.Words
Αυτό το σεμινάριο δείχνει πώς να δημιουργήσετε ένα νέο έγγραφο Word και να χρησιμοποιήσετε το DocumentBuilder του Aspose.Words for .NET για να εισάγετε ένα πεδίο φόρμας τύπου πλαίσιο ελέγχου. Ακολουθώντας τα βήματα, θα δείτε τον ακριβή κώδικα που απαιτείται για να προσθέσετε το διαδραστικό στοιχείο και στη συνέχεια να αποθηκεύσετε το έγγραφο σε αρχείο. Είναι ένας γρήγορος τρόπος να δημιουργήσετε προγραμματιστικά απλά αρχεία Word με ενεργοποιημένες φόρμες.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Τι αντιπροσωπεύει το τέταρτο όρισμα (0) στη μέθοδο InsertCheckBox;**
A: Καθορίζει το οπτικό μέγεθος του πλαισίου ελέγχου σε points· μια τιμή 0 λέει στο Aspose.Words να χρησιμοποιήσει το προεπιλεγμένο μέγεθος.

**Q: Μπορώ να εισάγω περισσότερα από ένα πλαίσια ελέγχου με το ίδιο όνομα;**
A: Όχι – κάθε όνομα πεδίου φόρμας πρέπει να είναι μοναδικό· η προσπάθεια εισαγωγής άλλου πλαισίου ελέγχου με όνομα "CheckBox" θα προκαλέσει ArgumentException.

**Q: Πώς μπορώ να προσθέσω ένα πλαίσιο ελέγχου σε ένα υπάρχον έγγραφο αντί για ένα νέο;**
A: Φορτώστε πρώτα το έγγραφο (π.χ., `Document doc = new Document("Existing.docx");`) έπειτα δημιουργήστε ένα DocumentBuilder για αυτό το έγγραφο και καλέστε το `InsertCheckBox` στη θέση του δρομέα που επιθυμείτε.

**Q: Πώς μπορώ να διαβάσω την κατάσταση του εισαχθέντος πλαισίου ελέγχου μετά την αποθήκευση του εγγράφου;**
A: Ανακτήστε το πεδίο φόρμας μέσω `doc.Range.FormFields["CheckBox"]` και ελέγξτε την ιδιότητα `Checked` του για να δείτε αν ήταν επιλεγμένο.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}