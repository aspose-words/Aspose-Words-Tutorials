---
title: Εισαγωγή σχήματος οριζόντιας γραμμής σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
weight: 110
limit:
description: Οδηγός βήμα‑βήμα για την εισαγωγή σχήματος οριζόντιας γραμμής σε έγγραφο Word με το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή σχήματος οριζόντιας γραμμής σε έγγραφο Word χρησιμοποιώντας το Aspose.Words
Μάθετε πώς να χρησιμοποιείτε το Aspose.Words for .NET για να εισάγετε ένα σχήμα οριζόντιας γραμμής σε έγγραφο Word. Αυτό το σεμινάριο σας καθοδηγεί στη δημιουργία νέου εγγράφου, την προσθήκη μιας γραμμής κειμένου, την τοποθέτηση σχήματος οριζόντιας γραμμής με το DocumentBuilder και την αποθήκευση του αρχείου. Η οριζόντια γραμμή παρέχει έναν απλό οπτικό διαχωριστή για το περιεχόμενό σας.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: Μπορώ να αλλάξω την εμφάνιση (χρώμα, πάχος) της οριζόντιας γραμμής που εισήχθη με το DocumentBuilder.InsertHorizontalRule();**
A: Το InsertHorizontalRule δημιουργεί ένα ενσωματωμένο σχήμα οριζόντιας γραμμής με προεπιλεγμένη μορφοποίηση· για να τροποποιήσετε την εμφάνισή του πρέπει να ανακτήσετε το εισαχθέν αντικείμενο Shape (builder.CurrentParagraph.LastChild) και να προσαρμόσετε τις ιδιότητες LineFormat.

**Q: Τι συμβαίνει αν καλέσω το InsertHorizontalRule() μετά από μια παράγραφο που ήδη τελειώνει με αλλαγή γραμμής;**
A: Η μέθοδος εισάγει τη γραμμή ως ξεχωριστή παράγραφο, έτσι οποιαδήποτε προηγούμενη αλλαγή γραμμής δημιουργεί απλώς μια κενή παράγραφο πριν από τη γραμμή· η γραμμή θα εμφανιστεί ακόμη στη δική της γραμμή.

**Q: Είναι δυνατόν να εισάγετε περισσότερες από μία οριζόντιες γραμμές στο ίδιο έγγραφο χρησιμοποιώντας το DocumentBuilder;**
A: Ναι, κάθε κλήση στο builder.InsertHorizontalRule() προσθέτει ένα νέο σχήμα οριζόντιας γραμμής στη τρέχουσα θέση του δρομέα, επιτρέποντας πολλαπλές γραμμές σε όλο το έγγραφο.

**Q: Λειτουργεί το InsertHorizontalRule() όταν αποθηκεύετε το έγγραφο σε μορφές διαφορετικές από DOCX, όπως PDF;**
A: Η οριζόντια γραμμή αποθηκεύεται ως σχήμα στο μοντέλο του εγγράφου, έτσι όταν αποθηκεύετε σε PDF, XPS ή άλλες υποστηριζόμενες μορφές, η γραμμή αποδίδεται σωστά στο αποτέλεσμα.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}