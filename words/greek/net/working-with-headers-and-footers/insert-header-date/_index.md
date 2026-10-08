---
title: Εισαγωγή Δυναμικής Ημερομηνίας στην Κεφαλίδα σε Έγγραφο Word με χρήση Aspose.Words for .NET
weight: 110
limit:
description: Μάθετε πώς να προσθέσετε ένα δυναμικό πεδίο DATE στην κύρια κεφαλίδα ενός εγγράφου Word με το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Μάθετε πώς να προσθέσετε ένα δυναμικό πεδίο DATE στην κύρια κεφαλίδα
    ενός εγγράφου Word με το Aspose.Words for .NET.
  headline: Εισαγωγή Δυναμικής Ημερομηνίας στην Κεφαλίδα σε Έγγραφο Word με χρήση
    Aspose.Words for .NET
  type: TechArticle
- description: Μάθετε πώς να προσθέσετε ένα δυναμικό πεδίο DATE στην κύρια κεφαλίδα
    ενός εγγράφου Word με το Aspose.Words for .NET.
  name: Εισαγωγή Δυναμικής Ημερομηνίας στην Κεφαλίδα σε Έγγραφο Word με χρήση Aspose.Words
    for .NET
  steps:
  - name: Δημιουργήστε ένα νέο Document και ένα DocumentBuilder για να το επεξεργαστείτε.
    text: Δημιουργήστε ένα νέο Document και ένα DocumentBuilder για να το επεξεργαστείτε.
  - name: Μετακινήστε τον κέρσορα του builder στην κύρια κεφαλίδα ώστε οι επόμενες
      εισαγωγές να επηρεάζουν την κεφαλίδα.
    text: Μετακινήστε τον κέρσορα του builder στην κύρια κεφαλίδα ώστε οι επόμενες
      εισαγωγές να επηρεάζουν την κεφαλίδα.
  - name: Γράψτε την στατική ετικέτα και εισάγετε ένα πεδίο DATE μορφοποιημένο ως
      “MMMM d, yyyy” στην κεφαλίδα, δημιουργώντας μια δυναμική ημερομηνία.
    text: Γράψτε την στατική ετικέτα και εισάγετε ένα πεδίο DATE μορφοποιημένο ως
      “MMMM d, yyyy” στην κεφαλίδα, δημιουργώντας μια δυναμική ημερομηνία.
  - name: Επιστρέψτε στο κύριο σώμα και προσθέστε μια δείγμα παράγραφο, δείχνοντας
      κανονικό περιεχόμενο εγγράφου μαζί με την κεφαλίδα.
    text: Επιστρέψτε στο κύριο σώμα και προσθέστε μια δείγμα παράγραφο, δείχνοντας
      κανονικό περιεχόμενο εγγράφου μαζί με την κεφαλίδα.
  - name: Αποθηκεύστε το έγγραφο σε αρχείο .docx.
    text: Αποθηκεύστε το έγγραφο σε αρχείο .docx.
  type: HowTo
- questions:
  - answer: Η κλήση `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` τοποθετεί
      το builder στην υπάρχουσα κύρια κεφαλίδα, και οι μέθοδοι `Write`/`InsertField`
      απλώς προσθέτουν κείμενο σε ό,τι υπάρχει ήδη· δεν διαγράφουν το υπάρχον περιεχόμενο.
    question: Τι συμβαίνει αν το έγγραφο έχει ήδη μια κύρια κεφαλίδα – θα αντικαταστήσει
      ο κώδικάς μου αυτήν;
  - answer: Ναι – τροποποιήστε τη μορφή του διακόπτη στον κώδικα πεδίου που περνάται
      στο `InsertField`, π.χ. `builder.InsertField("DATE \\@ \"yyyy-MM-dd\"")` θα
      δημιουργήσει μια ημερομηνία όπως 2026-09-22.
    question: Μπορώ να αλλάξω τη μορφή ημερομηνίας που χρησιμοποιεί το πεδίο DATE,
      και πώς;
  - answer: Αντικαταστήστε το `HeaderFooterType.HeaderPrimary` με `HeaderFooterType.HeaderFirst`
      κατά την κλήση του `MoveToHeaderFooter`; το υπόλοιπο του κώδικα λειτουργεί το
      ίδιο.
    question: Αν χρειάζομαι το πεδίο ημερομηνίας στην κεφαλίδα της πρώτης σελίδας
      αντί για την κύρια κεφαλίδα, τι πρέπει να κάνω;
  - answer: Το πεδίο εισάγεται μόνο με το διακόπτη `\@`, ο οποίος λέει στο Word να
      εμφανίζει την τρέχουσα ημερομηνία κάθε φορά που το πεδίο ανανεώνεται (π.χ. κατά
      το άνοιγμα του αρχείου ή όταν πατήσετε Ctrl+Alt+F9).
    question: Ενημερώνεται αυτόματα το πεδίο DATE όταν ανοίγει το έγγραφο αργότερα;
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Προσθήκη Δυναμικής Ημερομηνίας σε Κεφαλίδα Word
og_description: Οδηγός βήμα‑βήμα για την ενσωμάτωση ενός ζωντανού πεδίου ημερομηνίας στην κεφαλίδα του Word σας με το Aspose.Words.
og_image_alt: Στιγμιότυπο οθόνης που δείχνει πώς να εισάγετε ένα δυναμικό πεδίο DATE στην κεφαλίδα εγγράφου Word χρησιμοποιώντας το Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή Δυναμικής Ημερομηνίας στην Κεφαλίδα σε Έγγραφο Word με χρήση Aspose.Words
Αυτό το σεμινάριο δείχνει πώς να χρησιμοποιήσετε τις κλάσεις Document και DocumentBuilder στο Aspose.Words for .NET για να εισάγετε ένα δυναμικό πεδίο DATE στην κύρια κεφαλίδα ενός εγγράφου Word. Το προστιθέμενο πεδίο ενημερώνεται αυτόματα στην τρέχουσα ημερομηνία κάθε φορά που ανοίγει το έγγραφο, εξασφαλίζοντας ότι η κεφαλίδα σας αντικατοπτρίζει πάντα την πιο πρόσφατη ημερομηνία. Ακολουθήστε τον κώδικα βήμα‑βήμα για να προσθέσετε το πεδίο και να αποθηκεύσετε το ενημερωμένο αρχείο.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Τι συμβαίνει αν το έγγραφο έχει ήδη μια κύρια κεφαλίδα – θα αντικαταστήσει ο κώδικάς μου αυτήν;**  
A: Η κλήση `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` τοποθετεί το builder στην υπάρχουσα κύρια κεφαλίδα, και οι μέθοδοι `Write`/`InsertField` απλώς προσθέτουν κείμενο σε ό,τι υπάρχει ήδη· δεν διαγράφουν το υπάρχον περιεχόμενο.

**Q: Μπορώ να αλλάξω τη μορφή ημερομηνίας που χρησιμοποιεί το πεδίο DATE, και πώς;**  
A: Ναι – τροποποιήστε τη μορφή του διακόπτη στον κώδικα πεδίου που περνάται στο `InsertField`, π.χ. `builder.InsertField("DATE \\@ \"yyyy-MM-dd\"")` θα δημιουργήσει μια ημερομηνία όπως 2026-09-22.

**Q: Αν χρειάζομαι το πεδίο ημερομηνίας στην κεφαλίδα της πρώτης σελίδας αντί για την κύρια κεφαλίδα, τι πρέπει να κάνω;**  
A: Αντικαταστήστε το `HeaderFooterType.HeaderPrimary` με `HeaderFooterType.HeaderFirst` κατά την κλήση του `MoveToHeaderFooter`; το υπόλοιπο του κώδικα λειτουργεί το ίδιο.

**Q: Ενημερώνεται αυτόματα το πεδίο DATE όταν ανοίγει το έγγραφο αργότερα;**  
A: Το πεδίο εισάγεται μόνο με το διακόπτη `\@`, ο οποίος λέει στο Word να εμφανίζει την τρέχουσα ημερομηνία κάθε φορά που το πεδίο ανανεώνεται (π.χ. κατά το άνοιγμα του αρχείου ή όταν πατήσετε Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}