---
title: Εισαγωγή Ευθυγραμμισμένου HTML σε Έγγραφο Word Χρησιμοποιώντας το Aspose.Words for .NET
weight: 210
limit:
description: Μάθετε πώς να εισάγετε ακατέργαστο HTML με ευθυγράμμιση αριστερά, κέντρο ή δεξιά σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή Ευθυγραμμισμένου HTML σε Έγγραφο Word Χρησιμοποιώντας το Aspose.Words
Αυτό το διαδραστικό σεμινάριο δείχνει πώς να ενσωματώσετε ακατέργαστο HTML σε ένα έγγραφο Word ενώ ελέγχετε την ευθυγράμμισή του — αριστερά, κέντρο ή δεξιά — χρησιμοποιώντας το Aspose.Words for .NET. Εκμεταλλευόμενοι τα Document και DocumentBuilder, μπορείτε να εισάγετε μια συμβολοσειρά HTML και να εφαρμόσετε την επιθυμητή ευθυγράμμιση παραγράφου με λίγες μόνο γραμμές κώδικα. Το παράδειγμα είναι ιδανικό όταν χρειάζεται να διατηρήσετε τη μορφοποίηση HTML και να τοποθετήσετε το περιεχόμενο ακριβώς μέσα στο έγγραφό σας.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: Τι συμβαίνει αν η συμβολοσειρά HTML που περνάται στο DocumentBuilder.InsertHtml περιέχει ετικέτες που δεν υποστηρίζει το Aspose.Words, όπως <script> ή <iframe>;**
A: Οι μη υποστηριζόμενες ετικέτες αγνοούνται· το Aspose.Words αναλύει μόνο το υποσύνολο του HTML που μπορεί να αποδώσει, έτσι οι <script>, <iframe> και παρόμοια στοιχεία αφαιρούνται, ενώ το υπόλοιπο περιεχόμενο εισάγεται.

**Q: Θα διατηρηθούν τα ενσωματωμένα στυλ CSS (π.χ., <span style=\"color:red;\">) όταν χρησιμοποιείται το InsertHtml;**
A: Ναι, το InsertHtml σέβεται πολλές ενσωματωμένες ιδιότητες CSS όπως το χρώμα, το μέγεθος γραμματοσειράς και το φόντο, μετατρέποντάς τες στην αντίστοιχη μορφοποίηση του Word.

**Q: Δημιουργεί το InsertHtml αυτόματα μια νέα παράγραφο για στοιχεία επιπέδου block όπως <div> ή <h1>;**
A: Τα στοιχεία επιπέδου block αντιστοιχίζονται σε παραγράφους του Word, έτσι κάθε <div>, <p>, <h1> κ.λπ., γίνεται ξεχωριστή παράγραφος στο έγγραφο.

**Q: Πώς μπορώ να εισάγω HTML σε συγκεκριμένη θέση σε ένα υπάρχον έγγραφο αντί στην αρχή;**
A: Μετακινήστε τον κέρσορα του DocumentBuilder στον επιθυμητό κόμβο (π.χ., builder.MoveToDocumentEnd() ή builder.MoveToParagraph(index)) πριν καλέσετε το InsertHtml· το HTML θα εισαχθεί στην τρέχουσα θέση του κέρσορα.

**Q: Αν το έγγραφο περιέχει ήδη κείμενο, θα αντικαταστήσει το InsertHtml το υπάρχον περιεχόμενο;**
A: Όχι, το InsertHtml εισάγει το αναλυμένο HTML στη τρέχουσα θέση του builder χωρίς να διαγράψει υπάρχοντες κόμβους, εκτός αν μετακινήσετε ρητά τον κέρσορα μέσα σε αυτούς ή τους διαγράψετε εκ των προτέρων.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}