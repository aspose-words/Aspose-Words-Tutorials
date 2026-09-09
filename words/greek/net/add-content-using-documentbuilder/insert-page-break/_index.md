---
title: Εισαγωγή αλλαγής σελίδας σε έγγραφο Word με το Aspose.Words for .NET
weight: 110
limit:
description: Μάθετε να προσθέτετε αλλαγές σελίδας σε αρχείο Word με το Aspose.Words for .NET χρησιμοποιώντας το Document και το DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή αλλαγής σελίδας σε έγγραφο Word με το Aspose.Words
Σε αυτό το διαδραστικό σεμινάριο θα μάθετε πώς να προσθέτετε προγραμματιστικά αλλαγές σελίδας σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET. Δημιουργώντας ένα αντικείμενο Document και χρησιμοποιώντας το DocumentBuilder, μπορείτε να ελέγχετε πού αρχίζουν οι νέες σελίδες, κάτι που είναι απαραίτητο για τη μορφοποίηση αναφορών, τιμολογίων ή οποιουδήποτε εγγράφου πολλαπλών ενοτήτων. Ακολουθήστε το παράδειγμα βήμα‑βήμα για να δείτε τον κώδικα σε δράση και να προεπισκοπήσετε το παραγόμενο αρχείο.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: Μπορώ να χρησιμοποιήσω το InsertBreak για να προσθέσω αλλαγή γραμμής ή αλλαγή ενότητας αντί για αλλαγή σελίδας;**
A: Ναι, το InsertBreak δέχεται οποιαδήποτε τιμή του enum BreakType, όπως BreakType.LineBreak ή BreakType.SectionBreakContinuous, για να εισάγει την αντίστοιχη αλλαγή.

**Q: Πρέπει να καλέσω το InsertBreak πριν ή μετά τη γραφή του κειμένου για τη νέα σελίδα;**
A: Το InsertBreak πρέπει να καλείται μετά το περιεχόμενο που θέλετε στην τρέχουσα σελίδα· η επόμενη εντολή Writeln θα ξεκινήσει στη νέα σελίδα που δημιουργήθηκε από την αλλαγή.

**Q: Τι συμβαίνει αν η διαδρομή dataDir δεν λήγει με διαχωριστικό φακέλου;**
A: Αν στο dataDir λείπει το τελικό slash, το όνομα του αρχείου θα προσαρτηθεί απευθείας (π.χ., "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), κάτι που μπορεί να προκαλέσει μη έγκυρη διαδρομή· βεβαιωθείτε ότι η διαδρομή λήγει με "\\" ή χρησιμοποιήστε το Path.Combine.

**Q: Μπορώ να επαναχρησιμοποιήσω το ίδιο αντικείμενο DocumentBuilder για να εισάγω πολλαπλές αλλαγές σε όλο το έγγραφο;**
A: Ναι, το ίδιο DocumentBuilder μπορεί να χρησιμοποιηθεί επανειλημμένα· κάθε κλήση του InsertBreak εισάγει μια αλλαγή στη τρέχουσα θέση του κέρσορα του builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}