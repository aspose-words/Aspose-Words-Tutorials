---
title: Εισαγωγή σχήματος οριζόντιας γραμμής σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
weight: 110
limit:
description: Μάθετε πώς να προσθέσετε ένα σχήμα οριζόντιας γραμμής σε έγγραφο Word με το Aspose.Words for .NET χρησιμοποιώντας το DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή σχήματος οριζόντιας γραμμής σε έγγραφο Word χρησιμοποιώντας το Aspose.Words
Σε αυτό το σεμινάριο θα μάθετε πώς να εισάγετε προγραμματιστικά ένα σχήμα οριζόντιας γραμμής σε έγγραφο Word με το Aspose.Words for .NET. Χρησιμοποιώντας τις κλάσεις Document και DocumentBuilder δημιουργούμε ένα νέο έγγραφο, προσθέτουμε μια παράγραφο κειμένου και, στη συνέχεια, τοποθετούμε ένα σχήμα οριζόντιας γραμμής στην επιθυμητή θέση. Η οριζόντια γραμμή παρέχει έναν οπτικό διαχωριστή που μπορεί να είναι χρήσιμος για διακοπές ενότητας ή οπτική έμφαση.

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

**Q: Πού ακριβώς τοποθετεί η μέθοδος `builder.InsertHorizontalRule()` τη γραμμή στο έγγραφο;**  
A: `InsertHorizontalRule` εισάγει ένα σχήμα οριζόντιας γραμμής στη τρέχουσα θέση του δρομέα του `DocumentBuilder`; εάν θέλετε να βρίσκεται σε ξεχωριστή γραμμή, καλέστε `builder.Writeln()` πριν από την εισαγωγή.

**Q: Μπορώ να αλλάξω το πάχος, το χρώμα ή το πλάτος της εισαχθείσας οριζόντιας γραμμής;**  
A: `InsertHorizontalRule` προσθέτει μια προεπιλεγμένη γραμμή και δεν εκθέτει επιλογές μορφοποίησης· για να προσαρμόσετε αυτές τις ιδιότητες, πρέπει να εισάγετε ένα `Shape` χειροκίνητα (π.χ., `builder.InsertShape(ShapeType.HorizontalLine)`) και στη συνέχεια να ορίσετε τις ιδιότητες `LineFormat` του.

**Q: Είναι δυνατόν να προσθέσετε περισσότερες από μία οριζόντιες γραμμές στο ίδιο έγγραφο;**  
A: Ναι—απλώς καλέστε `builder.InsertHorizontalRule()` κάθε φορά που χρειάζεστε μια νέα γραμμή· κάθε κλήση δημιουργεί ένα ξεχωριστό σχήμα στη τρέχουσα θέση του builder.

**Q: Θα είναι ορατή η οριζόντια γραμμή όταν το αποθηκευμένο .docx ανοίξει στο Microsoft Word;**  
A: Απόλυτα· η γραμμή αποθηκεύεται ως σχήμα μέσα στο αρχείο .docx, έτσι το Word την εμφανίζει ακριβώς όπως εμφανίζεται στο παραγόμενο έγγραφο.

**Q: Τι συμβαίνει αν ο φάκελος `dataDir` δεν υπάρχει πριν κληθεί η μέθοδος `doc.Save(...)`;**  
A: `doc.Save` θα ρίξει μια `DirectoryNotFoundException`; βεβαιωθείτε ότι ο προορισμός υπάρχει ή δημιουργήστε τον προγραμματιστικά πριν από την αποθήκευση.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}