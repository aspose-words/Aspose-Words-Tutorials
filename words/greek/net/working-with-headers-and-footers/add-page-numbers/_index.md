---
title: Προσθήκη αριθμών σελίδων στο υποσέλιδο ενός εγγράφου Word χρησιμοποιώντας το Aspose.Words για .NET
weight: 210
limit:
description: Προσθέστε αυτόματα ενημερωτικούς αριθμούς σελίδων στο κύριο υποσέλιδο ενός εγγράφου Word χρησιμοποιώντας το Aspose.Words για .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Προσθέστε αυτόματα ενημερωτικούς αριθμούς σελίδων στο κύριο υποσέλιδο
    ενός εγγράφου Word χρησιμοποιώντας το Aspose.Words για .NET.
  headline: Προσθήκη αριθμών σελίδων στο υποσέλιδο ενός εγγράφου Word χρησιμοποιώντας
    το Aspose.Words για .NET
  type: TechArticle
- description: Προσθέστε αυτόματα ενημερωτικούς αριθμούς σελίδων στο κύριο υποσέλιδο
    ενός εγγράφου Word χρησιμοποιώντας το Aspose.Words για .NET.
  name: Προσθήκη αριθμών σελίδων στο υποσέλιδο ενός εγγράφου Word χρησιμοποιώντας
    το Aspose.Words για .NET
  steps:
  - name: Δημιουργήστε ένα νέο αντικείμενο Document και ένα DocumentBuilder που είναι
      συνδεδεμένο με αυτό.
    text: Δημιουργήστε ένα νέο αντικείμενο Document και ένα DocumentBuilder που είναι
      συνδεδεμένο με αυτό.
  - name: Μετακινήστε τον κέρσορα του builder στο κύριο υποσέλιδο της πρώτης ενότητας.
    text: Μετακινήστε τον κέρσορα του builder στο κύριο υποσέλιδο της πρώτης ενότητας.
  - name: Ορίστε την στοίχιση της παραγράφου στο κέντρο ώστε το κείμενο του υποσέλιδου
      να κεντραριστεί.
    text: Ορίστε την στοίχιση της παραγράφου στο κέντρο ώστε το κείμενο του υποσέλιδου
      να κεντραριστεί.
  - name: Γράψτε την ετικέτα "Page " και εισάγετε ένα πεδίο PAGE που εμφανίζει τον
      τρέχοντα αριθμό σελίδας.
    text: Γράψτε την ετικέτα "Page " και εισάγετε ένα πεδίο PAGE που εμφανίζει τον
      τρέχοντα αριθμό σελίδας.
  - name: Γράψτε " of " και εισάγετε ένα πεδίο NUMPAGES που δείχνει το συνολικό αριθμό
      σελίδων.
    text: Γράψτε " of " και εισάγετε ένα πεδίο NUMPAGES που δείχνει το συνολικό αριθμό
      σελίδων.
  - name: Αποθηκεύστε το έγγραφο σε αρχείο .docx.
    text: Αποθηκεύστε το έγγραφο σε αρχείο .docx.
  type: HowTo
- questions:
  - answer: Όχι. Το `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` μετακινεί
      το builder μόνο στο κύριο υποσέλιδο της *πρώτης* ενότητας, έτσι τα πεδία εισάγονται
      μόνο εκεί.
    question: Αν το έγγραφο έχει περισσότερες από μία ενότητες, θα προσθέσει αυτός
      ο κώδικας αριθμούς σελίδων σε κάθε υποσέλιδο ενότητας;
  - answer: Ορίστε το `builder.ParagraphFormat.Alignment` σε άλλη τιμή `ParagraphAlignment`
      (π.χ., `ParagraphAlignment.Right`) πριν γράψετε τα πεδία.
    question: Πώς μπορώ να αλλάξω την στοίχιση της παραγράφου του αριθμού σελίδας
      στο υποσέλιδο;
  - answer: Η `InsertField` δέχεται τον κωδικό του πεδίου και ένα προαιρετικό αποτέλεσμα
      πεδίου· η μεταβίβαση `null` λέει στο Aspose.Words να αφήσει το Word να υπολογίσει
      το αποτέλεσμα κατά την εκτέλεση.
    question: Τι αντιπροσωπεύει το όρισμα `null` στη μέθοδο `InsertField("PAGE", null)`;
  - answer: Ναι—αντικαταστήστε το `HeaderFooterType.FooterPrimary` με το `HeaderFooterType.HeaderPrimary`
      (ή κάποιο άλλο τύπο κεφαλίδας) πριν εισάγετε τα πεδία.
    question: Μπορώ να τοποθετήσω τα ίδια πεδία "Page X of Y" στην κεφαλίδα αντί για
      το υποσέλιδο;
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Εισαγωγή αυτόματων αριθμών σελίδων στο υποσέλιδο του Word
og_description: Κώδικας βήμα‑βήμα για την προσθήκη ζωντανών αριθμών σελίδων σε υποσέλιδο Word με το Aspose.Words για .NET.
og_image_alt: Οδηγός που δείχνει πώς να προσθέσετε αυτόματους αριθμούς σελίδων σε υποσέλιδο εγγράφου Word χρησιμοποιώντας το Aspose.Words για .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη αριθμών σελίδων στο υποσέλιδο ενός εγγράφου Word χρησιμοποιώντας το Aspose.Words για .NET
Αυτό το σεμινάριο δείχνει πώς να χρησιμοποιήσετε το Aspose.Words Document και το DocumentBuilder για να εισάγετε αυτόματα ενημερωτικούς αριθμούς σελίδων στο κύριο υποσέλιδο ενός εγγράφου Word. Προσθέτοντας αριθμούς σελίδων προγραμματιστικά, εξασφαλίζετε συνεπή σελιδοποίηση σε όλο το αρχείο χωρίς χειροκίνητη επεξεργασία. Ο κώδικας παραδείγματος είναι έτοιμος να εκτελεστεί σε περιβάλλον .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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

**Q: Αν το έγγραφο έχει περισσότερες από μία ενότητες, θα προσθέσει αυτός ο κώδικας αριθμούς σελίδων σε κάθε υποσέλιδο ενότητας;**  
A: Όχι. Το `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` μετακινεί το builder μόνο στο κύριο υποσέλιδο της *πρώτης* ενότητας, έτσι τα πεδία εισάγονται μόνο εκεί.

**Q: Πώς μπορώ να αλλάξω την στοίχιση της παραγράφου του αριθμού σελίδας στο υποσέλιδο;**  
A: Ορίστε το `builder.ParagraphFormat.Alignment` σε άλλη τιμή `ParagraphAlignment` (π.χ., `ParagraphAlignment.Right`) πριν γράψετε τα πεδία.

**Q: Τι αντιπροσωπεύει το όρισμα `null` στη μέθοδο `InsertField("PAGE", null)`;**  
A: Η `InsertField` δέχεται τον κωδικό του πεδίου και ένα προαιρετικό αποτέλεσμα πεδίου· η μεταβίβαση `null` λέει στο Aspose.Words να αφήσει το Word να υπολογίσει το αποτέλεσμα κατά την εκτέλεση.

**Q: Μπορώ να τοποθετήσω τα ίδια πεδία "Page X of Y" στην κεφαλίδα αντί για το υποσέλιδο;**  
A: Ναι—αντικαταστήστε το `HeaderFooterType.FooterPrimary` με το `HeaderFooterType.HeaderPrimary` (ή κάποιο άλλο τύπο κεφαλίδας) πριν εισάγετε τα πεδία.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}