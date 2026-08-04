---
category: general
date: 2026-08-04
description: Αλλάξτε το διαχωριστικό υποσημειώσεων σε C# χρησιμοποιώντας το Aspose.Words
  – μάθετε πώς να επεξεργάζεστε το διαχωριστικό υποσημειώσεων και να αλλάζετε το διαχωριστικό
  σημειώσεων τέλους σε έγγραφα Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: el
lastmod: 2026-08-04
og_description: Αλλάξτε το διαχωριστικό υποσημειώσεων σε C# με το Aspose.Words. Αυτός
  ο οδηγός σας δείχνει πώς να επεξεργαστείτε το διαχωριστικό υποσημειώσεων, να προσαρμόσετε
  το διαχωριστικό σημειώσεων τέλους και να αποθηκεύσετε το ενημερωμένο έγγραφο.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Αλλαγή διαχωριστικού υποσημειώσεων σε C# – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Αλλαγή διαχωριστικού υποσημειώσεων σε C# χρησιμοποιώντας το Aspose.Words
url: /el/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αλλαγή διαχωριστικού υποσημειώσεων σε C# χρησιμοποιώντας το Aspose.Words

Αν χρειάζεστε **αλλαγή διαχωριστικού υποσημειώσεων** σε ένα έγγραφο Word, αυτό το tutorial σας οδηγεί βήμα‑βήμα με το Aspose.Words για .NET. Είτε θέλετε να αντικαταστήσετε την προεπιλεγμένη γραμμή με ένα σύμβολο, είτε να εφαρμόσετε διαφορετικό στυλ στα διαχωριστικά σημειώσεων τέλους, ο παρακάτω κώδικας καλύπτει όλη τη διαδικασία.

Θα μάθετε επίσης πώς να **επεξεργαστείτε το διαχωριστικό υποσημειώσεων** και τη σχετική λειτουργία **αλλαγής διαχωριστικού σημειώσεων τέλους**, ώστε το ίδιο έγγραφο να έχει συνεπή στυλ για υποσημειώσεις και σημειώσεις τέλους. Δεν απαιτούνται εξωτερικά εργαλεία—μόνο λίγες γραμμές C#.

## Τι θα πετύχετε

* Φορτώστε ένα υπάρχον αρχείο *.docx* που περιέχει υποσημειώσεις και σημειώσεις τέλους.  
* Προσπελάστε τους κόμβους διαχωριστικού για υποσημειώσεις, συνέχειες υποσημειώσεων και σημειώσεις τέλους.  
* Αντικαταστήστε το χαρακτήρα διαχωριστικού (π.χ., αλλάξτε την προεπιλεγμένη γραμμή σε αστερίσκο).  
* Αποθηκεύστε το τροποποιημένο έγγραφο χωρίς να χάσετε κανένα άλλο περιεχόμενο.  

Το tutorial υποθέτει ότι έχετε βασική κατανόηση της C# και έχετε εγκαταστήσει το **Aspose.Words** NuGet package (έκδοση 24.9 ή νεότερη).  

---

## Προαπαιτούμενα

| Απαίτηση | Αιτία |
|-------------|--------|
| .NET 6.0+ ή .NET Framework 4.7.2+ | Απαιτούμενο runtime για το Aspose.Words |
| Aspose.Words for .NET library | Παρέχει τα API `Document` και `FootnoteOptions` |
| Ένα αρχείο Word εισόδου (`input.docx`) με τουλάχιστον μία υποσημείωση ή σημείωση τέλους | Δείχνει την αλλαγή του διαχωριστικού |

Μπορείτε να προσθέσετε το Aspose.Words στο έργο σας με την παρακάτω εντολή CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Βήμα 1: Φόρτωση του εγγράφου που περιέχει υποσημειώσεις

Η πρώτη ενέργεια είναι η ανάγνωση του αρχείου προέλευσης σε ένα αντικείμενο `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη και σας δίνει πρόσβαση σε όλους τους κόμβους του.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου είναι το σημείο εισόδου για οποιαδήποτε επεξεργασία. Εάν το αρχείο δεν βρεθεί, το Aspose.Words ρίχνει `FileNotFoundException`, γι' αυτό βεβαιωθείτε ότι η διαδρομή είναι σωστή πριν προχωρήσετε.

---

## Βήμα 2: Πρόσβαση στους κόμβους διαχωριστικού υποσημειώσεων και σημειώσεων τέλους

`Document.FootnoteOptions` εκθέτει τρεις κόμβους διαχωριστικού:

* `Separator` – η γραμμή που εμφανίζεται μετά τη συλλογή υποσημειώσεων στην πρώτη σελίδα.  
* `ContinuationSeparator` – η γραμμή που χρησιμοποιείται όταν οι υποσημειώσεις συνεχίζονται στην επόμενη σελίδα.  
* `EndnoteSeparator` – η γραμμή που χωρίζει το κύριο κείμενο από τη λίστα σημειώσεων τέλους.

Ανακτάτε αυτούς τους κόμβους ως γενικά αντικείμενα `Node`, έπειτα τους μετατρέπετε σε `Run` για να τροποποιήσετε το κείμενο.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Γιατί είναι σημαντικό:** Αυτοί οι κόμβοι είναι οι μόνες θέσεις όπου βρίσκεται ο οπτικός χαρακτήρας διαχωριστικού. Η αλλαγή οποιουδήποτε άλλου κόμβου (π.χ., μιας κανονικής παραγράφου) δεν θα επηρεάσει τη μορφοποίηση των υποσημειώσεων.

---

## Βήμα 3: Αλλαγή χαρακτήρα διαχωριστικού υποσημειώσεων

Η πιο συνηθισμένη απαίτηση είναι η αντικατάσταση της προεπιλεγμένης γραμμής με ένα σύμβολο όπως αστερίσκο (`*`). Επειδή το διαχωριστικό αποθηκεύεται ως `Run`, μπορείτε με ασφάλεια να τροποποιήσετε την ιδιότητα `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Γιατί είναι σημαντικό:** Η άμεση επεξεργασία του `Run.Text` ενημερώνει την οπτική αναπαράσταση στο τελικό έγγραφο χωρίς να επηρεάζει άλλο περιεχόμενο των υποσημειώσεων. Το ίδιο μοτίβο μπορεί να χρησιμοποιηθεί για οποιοδήποτε συμβολοσειρά, συμπεριλαμβανομένων των Unicode συμβόλων.

---

## Βήμα 4: Αλλαγή διαχωριστικού σημειώσεων τέλους (προαιρετικό)

Εάν χρειάζεστε επίσης **αλλαγή διαχωριστικού σημειώσεων τέλους**, η διαδικασία είναι παρόμοια με αυτή της υποσημείωσης. Αντικαταστήστε το κείμενο του `endnoteSeparator` με τον επιθυμητό χαρακτήρα.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Γιατί είναι σημαντικό:** Οι σημειώσεις τέλους συχνά μορφοποιούνται διαφορετικά από τις υποσημειώσεις. Ένα ξεχωριστό διαχωριστικό σας επιτρέπει να διατηρήσετε οπτική συνέπεια με τις οδηγίες σχεδίασης του εγγράφου σας.

---

## Βήμα 5: Αποθήκευση του τροποποιημένου εγγράφου

Μετά από όλες τις τροποποιήσεις, αποθηκεύστε τις αλλαγές χρησιμοποιώντας `Document.Save`. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να γράψετε σε νέα τοποθεσία.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Γιατί είναι σημαντικό:** Η `Save` γράφει την αναπαράσταση στη μνήμη στο δίσκο, διατηρώντας όλα τα άλλα στοιχεία (στυλ, εικόνες, πίνακες) αμετάβλητα.

---

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, ακολουθεί μια αυτόνομη εφαρμογή κονσόλας που δείχνει ολόκληρη τη ροή εργασίας:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το *ModifiedSeparators.docx* στο Microsoft Word. Η γραμμή διαχωριστικού υποσημειώσεων στο κάτω μέρος της πρώτης σελίδας υποσημειώσεων θα είναι τώρα ένας μοναδικός αστερίσκος (`*`). Εάν το έγγραφο περιέχει σημειώσεις τέλους, η γραμμή που χωρίζει το κύριο κείμενο από τη λίστα σημειώσεων τέλους θα εμφανίζεται ως παύλα (`-`). Όλο το υπόλοιπο περιεχόμενο (κείμενο, εικόνες, πίνακες) παραμένει άθικτο.

---

## Συχνές ερωτήσεις & αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το έγγραφο δεν έχει υποσημειώσεις;** | `FootnoteOptions.Separator` εξακολουθεί να επιστρέφει έναν κόμβο `Run`, αλλά το κείμενό του μπορεί να είναι κενό. Ο κώδικας ελέγχει με ασφάλεια τον τύπο του κόμβου πριν τον τροποποιήσει. |
| **Μπορώ να χρησιμοποιήσω συμβολοσειρά πολλαπλών χαρακτήρων (π.χ., "***");** | Ναι. Η ιδιότητα `Run.Text` δέχεται οποιαδήποτε συμβολοσειρά, συμπεριλαμβανομένων των Unicode χαρακτήρων. |
| **Θα επηρεάσει η αλλαγή του διαχωριστικού την υπάρχουσα αρίθμηση υποσημειώσεων;** | Όχι. Το διαχωριστικό είναι ανεξάρτητο από το σύστημα αρίθμησης. |
| **Πρέπει να απελευθερώσω το αντικείμενο `Document`;** | Το `Document` υλοποιεί έμμεσα το `IDisposable` μέσω του `Node`. Σε μια σύντομη εφαρμογή κονσόλας είναι προαιρετικό, αλλά για υπηρεσίες μακράς διάρκειας μπορείτε να το τυλίξετε σε μπλοκ `using`. |
| **Πώς λειτουργεί αυτό με .NET Core vs .NET Framework;** | Το API είναι ταυτόσημο σε όλα τα runtime· μόνο η έκδοση του target framework έχει σημασία (πρέπει να υποστηρίζεται από το πακέτο Aspose.Words). |

**Pro tip:** Εάν χρειάζεστε διαφορετικά διαχωριστικά για διαφορετικές ενότητες, μπορείτε να επαναλάβετε μέσω `doc.GetChildNodes(NodeType.Footnote, true)` και να προσαρμόσετε το `Separator` κάθε υποσημείωσης ξεχωριστά. Πρόκειται για πιο προχωρημένη τεχνική, αλλά χρήσιμη σε σύνθετα έγγραφα.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **αλλάξετε το διαχωριστικό υποσημειώσεων** και **το διαχωριστικό σημειώσεων τέλους** σε ένα αρχείο Word χρησιμοποιώντας το Aspose.Words για C#. Ο οδηγός κάλυψε τη φόρτωση του εγγράφου, την πρόσβαση στους σχετικούς κόμβους διαχωριστικού, την τροποποίηση του κειμένου τους και την αποθήκευση του αποτελέσματος—όλα σε ένα ενιαίο, αυτόνομο πρόγραμμα.

Από εδώ μπορείτε να εξερευνήσετε συναφή θέματα όπως **επεξεργασία στυλ διαχωριστικού υποσημειώσεων**, προσαρμογή αρίθμησης υποσημειώσεων ή εφαρμογή υπό όρους μορφοποίησης βάσει διάταξης σελίδας. Το ίδιο μοτίβο (ανάκτηση κόμβου, μετατροπή σε `Run`, τροποποίηση `Text`) λειτουργεί σε πολλές άλλες περιπτώσεις επεξεργασίας Word.

Καλή προγραμματιστική, και μη διστάσετε να πειραματιστείτε με διαφορετικά σύμβολα ή ακόμη και να ενσωματώσετε εικόνες ως διαχωριστικά για ένα πραγματικά μοναδικό στυλ εγγράφου!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Επεξεργασία κειμένου με υποσημειώσεις και σημειώσεις τέλους](/words/english/net/working-with-footnote-and-endnote/)
- [Λήψη διαχωριστικού στυλ παραγράφου σε έγγραφο Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Εισαγωγή διαχωριστικού στυλ εγγράφου στο Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}