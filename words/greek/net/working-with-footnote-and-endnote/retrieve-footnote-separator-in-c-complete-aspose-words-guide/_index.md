---
category: general
date: 2026-08-07
description: Ανακτήστε το διαχωριστικό υποσημειώσεων χρησιμοποιώντας το Aspose.Words
  για .NET. Μάθετε πώς να εξάγετε τα διαχωριστικά υποσημειώσεων και σημειώσεων τέλους,
  να ελέγχετε τους τύπους κόμβων και να τα τροποποιείτε σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: el
lastmod: 2026-08-07
og_description: Ανάκτηση διαχωριστικού υποσημειώσεων με το Aspose.Words για .NET.
  Αυτός ο οδηγός δείχνει πώς να εξάγετε τα διαχωριστικά υποσημειώσεων και σημειώσεων
  τέλους, να ελέγξετε τους τύπους των κόμβων τους και να αποθηκεύσετε τις αλλαγές.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: Ανάκτηση διαχωριστικού υποσημειώσεων σε C# – βήμα‑βήμα οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Ανάκτηση διαχωριστικού υποσημειώσεων σε C# – πλήρης οδηγός Aspose.Words
url: /el/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση διαχωριστικού υποσημειώσεων σε C# – πλήρης οδηγός Aspose.Words

Αν χρειάζεστε **retrieve footnote separator** από ένα έγγραφο Word, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for .NET. Είτε δημιουργείτε μια υπηρεσία επεξεργασίας εγγράφων είτε καθαρίζετε τη μορφοποίηση των υποσημειώσεων, θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που εξάγει τόσο τα διαχωριστικά υποσημειώσεων όσο και τα διαχωριστικά σημειώσεων τέλους.

Σε αυτόν τον οδηγό θα μάθετε πώς να φορτώσετε ένα αρχείο `.docx`, να καλέσετε τις ιδιότητες `FootnoteSeparator` και `EndnoteSeparator`, να εξετάσετε τα επιστρεφόμενα αντικείμενα `Node`, και προαιρετικά να αντικαταστήσετε τη γραμμή διαχωριστικού. Δεν απαιτείται εξωτερική τεκμηρίωση — όλα όσα χρειάζεστε περιλαμβάνονται παρακάτω.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7.2)
* Πακέτο NuGet Aspose.Words for .NET (έκδοση 24.9 ή νεότερη)
* Ένα έγγραφο Word που περιέχει υποσημειώσεις και/ή σημειώσεις τέλους (π.χ., `Footnotes.docx`)

Μπορείτε να προσθέσετε το πακέτο Aspose.Words με την ακόλουθη εντολή CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε ένα νέο έργο console ή προσθέστε τον κώδικα σε ένα υπάρχον. Οι απαιτούμενες οδηγίες `using` παρατίθενται παρακάτω.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Αυτά τα namespaces σας δίνουν πρόσβαση στην κλάση `Document`, στην ιεραρχία `Node` και στην απαρίθμηση `NodeType` που απαιτούνται για τις λειτουργίες **retrieve footnote separator**.

## Βήμα 2: Φόρτωση του εγγράφου που περιέχει υποσημειώσεις και σημειώσεις τέλους

Η πρώτη ενέργεια σε οποιαδήποτε ροή εργασίας Aspose.Words είναι η φόρτωση του αρχείου προέλευσης. Αντικαταστήστε τη διαδρομή placeholder με την πραγματική θέση του `.docx` σας.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Η φόρτωση του αρχείου προετοιμάζει το εσωτερικό δέντρο κόμβων, το οποίο είναι απαραίτητο για **retrieve footnote separator** επειδή οι κόμβοι διαχωριστικού ζουν μέσα σε αυτό το δέντρο.

## Βήμα 3: Ανάκτηση του κόμβου διαχωριστικού υποσημειώσεων

Τώρα μπορείτε να **retrieve footnote separator** προσπελαύνοντας την ιδιότητα `FootnoteSeparator` του αντικειμένου `Document`. Αυτός ο κόμβος αντιπροσωπεύει τη γραμμή που διαχωρίζει τις υποσημειώσεις από το κύριο κείμενο.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

Το `NodeType` θα είναι `Paragraph` για μια τυπική γραμμή διαχωριστικού. Η γνώση του τύπου κόμβου σας βοηθά να αποφασίσετε αν χρειάζεται να τροποποιήσετε το διαχωριστικό ή να το αντικαταστήσετε εντελώς.

## Βήμα 4: Ανάκτηση του κόμβου διαχωριστικού σημειώσεων τέλους

Ανάλογα, μπορείτε να **retrieve endnote separator** χρησιμοποιώντας την ιδιότητα `EndnoteSeparator`. Αυτός ο κόμβος διαχωρίζει τις σημειώσεις τέλους από το κύριο περιεχόμενο.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Και οι δύο κόμβοι διαχωριστικού μοιράζονται τον ίδιο `NodeType` (`Paragraph`) στα περισσότερα έγγραφα, αλλά μπορούν να προσαρμοστούν ανεξάρτητα.

## Βήμα 5: Επιθεώρηση ή τροποποίηση του περιεχομένου του διαχωριστικού (προαιρετικό)

Αν χρειάζεστε να αλλάξετε την οπτική εμφάνιση του διαχωριστικού — όπως η αντικατάσταση μιας γραμμής παύλων με μια λεπτή γραμμή — μπορείτε να επεξεργαστείτε απευθείας τον κόμβο `Paragraph`. Παρακάτω υπάρχει ένα παράδειγμα που αντικαθιστά το προεπιλεγμένο κείμενο διαχωριστικού με μια προσαρμοσμένη συμβολοσειρά.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Μετά την τροποποίηση των κόμβων, μπορείτε να αποθηκεύσετε το έγγραφο για να δείτε τις αλλαγές να εμφανίζονται στο Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Αναμενόμενη έξοδος κονσόλας

Όταν εκτελέσετε το πρόγραμμα με το αρχικό `Footnotes.docx`, θα πρέπει να δείτε κάτι παρόμοιο με:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Αν ανοίξετε το `Footnotes_Updated.docx` στο Microsoft Word, τα διαχωριστικά υποσημειώσεων και σημειώσεων τέλους θα εμφανίσουν το προσαρμοσμένο κείμενο που εισάγατε.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

**Τι γίνεται αν το έγγραφο δεν έχει υποσημειώσεις;**  
Η ιδιότητα `FootnoteSeparator` εξακολουθεί να επιστρέφει έναν κόμβο `Paragraph` επειδή το Word πάντα περιλαμβάνει ένα placeholder διαχωριστικού. Ο κόμβος θα είναι κενός, έτσι μπορείτε με ασφάλεια να προσθέσετε περιεχόμενο ή να τον αφήσετε όπως είναι.

**Μπορώ να ανακτήσω το διαχωριστικό για συγκεκριμένο τμήμα;**  
Τα διαχωριστικά υποσημειώσεων και σημειώσεων τέλους ισχύουν για ολόκληρο το έγγραφο, όχι για συγκεκριμένα τμήματα. Αν χρειάζεστε έλεγχο σε επίπεδο τμήματος, πρέπει να εργαστείτε με `Section.FootnoteOptions` και `Section.EndnoteOptions` αντί για τους παγκόσμιους κόμβους διαχωριστικού.

**Λειτουργεί αυτό με .NET Core;**  
Ναι. Το Aspose.Words for .NET είναι δια‑πλατφορμικό, και ο ίδιος κώδικας εκτελείται σε Windows, Linux και macOS με .NET 6+.

**Τι τύπο κόμβου πρέπει να περιμένω;**  
Τanto `FootnoteSeparator` όσο και `EndnoteSeparator` επιστρέφουν έναν κόμβο `Paragraph` (`NodeType.Paragraph`). Αν συναντήσετε διαφορετικό τύπο, το έγγραφο μπορεί να είναι κατεστραμμένο, και θα πρέπει να το φορτώσετε ξανά ή να επικυρώσετε το αρχείο προέλευσης.

## Πλήρης πηγαίος κώδικας για γρήγορη αντιγραφή‑επικόλληση

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Αντιγράψτε τον κώδικα σε ένα αρχείο `Program.cs`, προσαρμόστε τις διαδρομές αρχείων και εκτελέστε `dotnet run`. Το πρόγραμμα επιδεικνύει τη πλήρη ροή εργασίας **retrieve footnote separator**, από τη φόρτωση του εγγράφου έως την αποθήκευση των αλλαγών.

## Συμπέρασμα

Τώρα ξέρετε πώς να **retrieve footnote separator** και **endnote separator retrieval** χρησιμοποιώντας το Aspose.Words for .NET, να επιθεωρήσετε τον `document node type` τους, και προαιρετικά να αντικαταστήσετε το περιεχόμενό τους. Αυτή η τεχνική σας επιτρέπει να αυτοματοποιήσετε τη μορφοποίηση των υποσημειώσεων, να δημιουργήσετε προσαρμοσμένες γραμμές διαχωριστικού ή να επικυρώσετε τη δομή του εγγράφου σε οποιαδήποτε εφαρμογή C#.

Στη συνέχεια, μπορείτε να εξερευνήσετε σχετικά θέματα όπως **C# footnote extraction** για μεμονωμένα κείμενα υποσημειώσεων, ή να μάθετε πώς να **modify footnote reference marks** χρησιμοποιώντας το `FootnoteOptions`. Και οι δύο έννοιες βασίζονται άμεσα στα θεμέλια του δέντρου κόμβων που καλύφθηκαν εδώ.

Καλό κώδικα, και μη διστάσετε να πειραματιστείτε με διαφορετικά στυλ διαχωριστικού ώστε να ταιριάζουν με το branding του έργου σας!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Επεξεργασία κειμένου με υποσημειώσεις και σημειώσεις τέλους](/words/english/net/working-with-footnote-and-endnote/)
- [Προσθήκη περιεχομένου χρησιμοποιώντας Document Builder στο Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Εργασία με υποσημειώσεις και σημειώσεις τέλους](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}