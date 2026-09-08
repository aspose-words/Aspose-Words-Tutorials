---
category: general
date: 2026-09-08
description: Ανακτήστε το διαχωριστικό των σημειώσεων τέλους και εμφανίστε το διαχωριστικό
  των υποσημειώσεων όταν φορτώνετε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words
  για .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: el
lastmod: 2026-09-08
og_description: Ανακτήστε το διαχωριστικό σημειώσεων τέλους και εμφανίστε το διαχωριστικό
  υποσημειώσεων όταν φορτώνετε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words για
  .NET.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: Ανάκτηση διαχωριστικού υποσημειώσεων κατά τη φόρτωση ενός εγγράφου Word
  σε C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: Ανάκτηση διαχωριστικού υποσημειώσεων κατά τη φόρτωση εγγράφου Word σε C#
url: /el/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση διαχωριστικού σημειώσεων τέλους κατά τη φόρτωση ενός εγγράφου Word σε C#

Αν χρειάζεστε να **ανακτήσετε το διαχωριστικό σημειώσεων τέλους** από ένα αρχείο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα μάθετε επίσης πώς να **φορτώσετε έγγραφο Word** με το Aspose.Words και να **εμφανίσετε το κείμενο του διαχωριστικού υποσημειώσεων** στην κονσόλα, όλα σε ένα ενιαίο, εκτελέσιμο παράδειγμα.

Η εργασία με υποσημειώσεις και σημειώσεις τέλους είναι συχνή απαίτηση για νομικές, ακαδημαϊκές ή εκδοτικές εφαρμογές. Αυτό το tutorial καλύπτει όλα όσα χρειάζεστε—από το άνοιγμα του αρχείου μέχρι τη διαχείριση περιπτώσεων όπου λείπει το διαχωριστικό—ώστε να ενσωματώσετε τη λύση σε οποιοδήποτε .NET project χωρίς εικασίες.

## Τι καλύπτει αυτός ο οδηγός

* Πώς να **φορτώσετε έγγραφο Word** χρησιμοποιώντας το API Aspose.Words.  
* Πώς να **ανακτήσετε το διαχωριστικό σημειώσεων τέλους** και γιατί το διαχωριστικό είναι σημαντικό.  
* Πώς να **εμφανίσετε το διαχωριστικό υποσημειώσεων** στην κονσόλα για αποσφαλμάτωση ή καταγραφή.  
* Διαχείριση ακραίων περιπτώσεων όταν ένα έγγραφο δεν περιέχει υποσημειώσεις ή σημειώσεις τέλους.  
* Ένα πλήρες, έτοιμο για αντιγραφή-επικόλληση δείγμα κώδικα που εκτελείται σε .NET 6 ή νεότερο.

### Προαπαιτούμενα

| Requirement | Reason |
|-------------|--------|
| .NET 6 SDK ή νεότερο | Παρέχει το runtime για το παράδειγμα C#. |
| Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`) | Η βιβλιοθήκη που εκθέτει `Document.Footnotes` και `Document.Endnotes`. |
| Αρχείο Word (`Footnotes.docx`) που περιέχει τουλάχιστον μια υποσημείωση ή σημείωση τέλους | Δείχνει τα διαχωριστικά. |
| Οποιοδήποτε IDE (Visual Studio, Rider, VS Code) | Για να μεταγλωττίσετε και να εκτελέσετε το πρόγραμμα. |

> **Συμβουλή:** Αν δεν έχετε έγγραφο με υποσημειώσεις, δημιουργήστε ένα γρήγορα στο Microsoft Word: Insert → Footnote → πληκτρολογήστε κάποιο κείμενο, έπειτα αποθηκεύστε ως `Footnotes.docx`.

## Φόρτωση εγγράφου Word με Aspose.Words

Το πρώτο βήμα είναι να **φορτώσετε έγγραφο Word** στη μνήμη. Το Aspose.Words διαβάζει τη μορφή του αρχείου και δημιουργεί ένα μοντέλο αντικειμένων που μπορείτε να ερωτήσετε.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου είναι προαπαιτούμενο για οποιαδήποτε περαιτέρω επεξεργασία. Αν η διαδρομή του αρχείου είναι λανθασμένη, το `Document` ρίχνει `FileNotFoundException`, οπότε ελέγξτε τη διαδρομή πριν την εκτέλεση.

## Ανάκτηση παραγράφου διαχωριστικού υποσημειώσεων

Το διαχωριστικό υποσημειώσεων είναι η παράγραφος που χωρίζει οπτικά το κύριο κείμενο από τη λίστα των υποσημειώσεων. Η ανάκτηση του σας επιτρέπει να ελέγξετε ή να τροποποιήσετε τη μορφοποίησή του.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Γιατί είναι σημαντικό*: **Η εμφάνιση του διαχωριστικού υποσημειώσεων** σας βοηθά να επαληθεύσετε ότι η σωστή παράγραφος προσπελάστηκε, ειδικά όταν χρειάζεται να εφαρμόσετε προσαρμοσμένο στυλ (π.χ., μια γραμμή ή συγκεκριμένη γραμματοσειρά).

## Ανάκτηση παραγράφου διαχωριστικού σημειώσεων τέλους

Τώρα **ανακτούμε το διαχωριστικό σημειώσεων τέλους**. Η διαδικασία είναι παρόμοια με αυτή των υποσημειώσεων, αλλά χρησιμοποιεί τη συλλογή `Endnotes`.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Γιατί είναι σημαντικό*: Το βήμα **ανακτήστε το διαχωριστικό σημειώσεων τέλους** είναι ουσιώδες όταν χρειάζεται να προσαρμόσετε το οπτικό κενό μεταξύ του κύριου περιεχομένου και της λίστας των σημειώσεων τέλους—συνηθισμένο στην ακαδημαϊκή έκδοση όπου οι σημειώσεις τέλους εμφανίζονται στο τέλος ενός κεφαλαίου.

### Διαχείριση ελλιπών διαχωριστικών

Τanto `Footnotes.Separator` όσο και `Endnotes.Separator` επιστρέφουν `null` όταν το έγγραφο δεν ορίζει διαχωριστικό. Πάντα ελέγχετε για `null` πριν καλέσετε `GetText()` ώστε να αποφύγετε `NullReferenceException`. Αν χρειάζεστε προεπιλεγμένο διαχωριστικό, μπορείτε να δημιουργήσετε ένα:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

Αυτός ο κώδικας εισάγει ένα ελάχιστο διαχωριστικό ώστε η επόμενη επεξεργασία να μπορεί να βασιστεί στην ύπαρξή του.

## Αναμενόμενη έξοδος κονσόλας

Όταν το δείγμα εκτελείται εναντίον ενός εγγράφου που περιέχει μία υποσημείωση και μία σημείωση τέλους, θα πρέπει να δείτε κάτι παρόμοιο με:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

Αν το έγγραφο δεν έχει υποσημειώσεις ή σημειώσεις τέλους, το πρόγραμμα εκτυπώνει τα αντίστοιχα μηνύματα “not found”, δείχνοντας ευγενική διαχείριση σφαλμάτων.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε σε ένα νέο C# console project. Δεν απαιτείται επιπλέον κώδικας.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

Αποθηκεύστε το αρχείο ως `Program.cs`, προσθέστε το πακέτο NuGet Aspose.Words (`dotnet add package Aspose.Words`) και τρέξτε `dotnet run`. Το πρόγραμμα θα εκτυπώσει τα κείμενα των διαχωριστικών ή θα σας ενημερώσει αν λείπουν.

## Συνηθισμένες παραλλαγές και σενάρια what‑if

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Πολλαπλά προσαρμοσμένα διαχωριστικά** | Χρησιμοποιήστε `doc.Footnotes.Separator` για να αντικαταστήσετε το προεπιλεγμένο, μετά προσθέστε επιπλέον παραγράφους διαχωριστικού χειροκίνητα με `doc.Footnotes.Add(separatorParagraph)`. |
| **Αλλαγή στυλ διαχωριστικού** | Αφού ανακτήσετε το διαχωριστικό, τροποποιήστε το `ParagraphFormat` του (π.χ., `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Εργασία με αρχεία .doc** | Το ίδιο API λειτουργεί· απλώς βεβαιωθείτε ότι η διαδρομή του αρχείου τελειώνει σε `.doc`. |
| **Επεξεργασία πολλών εγγράφων** | Τυλίξτε τη φόρτωση και την ανάκτηση του διαχωριστικού σε βρόχο `foreach`; επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` μόνο αν το επαναρυθμίσετε με `doc = new Document(path)`. |

## Λίστα ελέγχου βέλτιστων πρακτικών

- ✅ **Πάντα ελέγχετε για `null`** πριν προσπελάσετε το κείμενο του διαχωριστικού.  
- ✅ **Κόψτε** (Trim) το αποτέλεσμα του `GetText()` για να αφαιρέσετε κρυφούς χαρακτήρες αλλαγής γραμμής.  
- ✅ **Αποδεσμεύστε** (Dispose) μεγάλα αντικείμενα `Document` αν επεξεργάζεστε πολλά αρχεία σε παρτίδα (χρησιμοποιήστε `using` ή καλέστε `doc.Dispose()`).  
- ✅ **Καταγράψτε** το κείμενο του διαχωριστικού μόνο στην ανάπτυξη· αποφύγετε την εμφάνισή του σε καταγραφές παραγωγής εκτός αν απαιτείται.  

## Συμπέρασμα

Τώρα ξέρετε πώς να **ανακτήσετε το διαχωριστικό σημειώσεων τέλους** ενώ **φορτώνετε έγγραφο Word** και **εμφανίζετε το διαχωριστικό υποσημειώσεων** σε μια .NET console εφαρμογή. Το πλήρες παράδειγμα δείχνει τη φόρτωση, την ερώτηση και τη ασφαλή διαχείριση ελλιπών διαχωριστικών, παρέχοντάς σας μια σταθερή βάση για οποιαδήποτε εργασία με υποσημειώσεις ή σημειώσεις τέλους.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* **Προσαρμογή μορφοποίησης υποσημειώσεων/σημειώσεων τέλους** – προσαρμόστε γραμματοσειρές, περιγράμματα ή στυλ αρίθμησης.  
* **Εξαγωγή περιεχομένου υποσημειώσεων/σημειώσεων τέλους** – επαναλάβετε τις συλλογές `doc.Footnotes` ή `doc.Endnotes`.  
* **Αποθήκευση του τροποποιημένου εγγράφου** – χρησιμοποιήστε `doc.Save("output.docx")` για να αποθηκεύσετε τις αλλαγές.  

Μη διστάσετε να πειραματιστείτε με διαφορετικά αρχεία Word, στυλ διαχωριστικών και δυνατότητες του Aspose.Words. Καλή προγραμματιστική!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να φορτώσετε έγγραφα Word χρησιμοποιώντας Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Λήψη διαχωριστικού στυλ παραγράφου σε έγγραφο Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Δημιουργία και μορφοποίηση εγγράφου Word στο Aspose.Words για .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}