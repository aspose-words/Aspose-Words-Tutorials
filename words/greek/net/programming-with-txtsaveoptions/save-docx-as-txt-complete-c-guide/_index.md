---
category: general
date: 2026-01-06
description: Αποθηκεύστε το docx ως txt χρησιμοποιώντας C# και Aspose.Words. Μάθετε
  πώς να εξάγετε εξισώσεις Word σε LaTeX, να μετατρέψετε τύπους σε απλό κείμενο και
  να διατηρήσετε τη μορφοποίηση ανέπαφη.
draft: false
keywords:
- save docx as txt
- save word plain text
- export word equations latex
- convert word formulas text
- save word file txt
language: el
og_description: Αποθηκεύστε το docx ως txt με το Aspose.Words σε C#. Εξαγωγή εξισώσεων
  Word σε LaTeX, μετατροπή τύπων σε απλό κείμενο και μετατροπή κύριου εγγράφου.
og_title: Αποθήκευση docx ως txt – Πλήρης Οδηγός C#
tags:
- C#
- Aspose.Words
- DocumentConversion
title: Αποθήκευση docx ως txt – Πλήρης οδηγός C#
url: /el/net/programming-with-txtsaveoptions/save-docx-as-txt-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση docx ως txt – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί ποτέ πώς να **αποθηκεύσετε docx ως txt** χωρίς να χάσετε τα μαθηματικά που πληκτρολογήσατε ώρες; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν χρειάζονται εκδόσεις απλού κειμένου αρχείων Word που διατηρούν σωστές αναπαραστάσεις LaTeX των εξισώσεων.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια καθαρή, ολοκληρωμένη λύση που όχι μόνο **αποθηκεύει plain text από Word** αλλά επίσης **εξάγει LaTeX εξισώσεων Word** και **μετατρέπει word formulas text** σε ένα τακτοποιημένο αρχείο `.txt`. Στο τέλος θα έχετε ένα έτοιμο κομμάτι κώδικα, μερικές πρακτικές συμβουλές και μια σαφή εικόνα για το πώς να προσαρμόσετε την προσέγγιση στα δικά σας έργα.

## Τι Θα Χρειαστείτε

- .NET 6+ (ή .NET Framework 4.6+).  
- Το πακέτο NuGet **Aspose.Words** – η βιβλιοθήκη που μας επιτρέπει να χειριζόμαστε αρχεία DOCX προγραμματιστικά.  
- Ένα δείγμα `input.docx` που περιέχει κανονικό κείμενο **και** εξισώσεις Office Math (του τύπου που δημιουργεί ο επεξεργαστής εξισώσεων του Word).  

Καμία επιπλέον εργαλειοθήκη, καμία πολύπλοκη εντολή γραμμής. Μόνο μερικές γραμμές C# και είστε έτοιμοι.

## Βήμα 1: Φόρτωση του πηγαίου εγγράφου

Πρώτα δημιουργούμε ένα αντικείμενο `Document` που δείχνει στο αρχείο Word μας. Σκεφτείτε το σαν άνοιγμα του αρχείου στη μνήμη ώστε να μπορούμε να ελέγξουμε ή να μετασχηματίσουμε το περιεχόμενό του.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 1: Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του αρχείου μας δίνει πλήρη πρόσβαση στο δέντρο του εγγράφου – παραγράφους, πίνακες και, το πιο σημαντικό, στους κόμβους `OfficeMath` που περιέχουν τις εξισώσεις που θέλουμε να εξάγουμε.

## Βήμα 2: Διαμόρφωση επιλογών αποθήκευσης κειμένου για εξαγωγή Office Math ως LaTeX

Το Aspose.Words μας επιτρέπει να αποφασίσουμε πώς θα αποδοθούν οι εξισώσεις όταν αποθηκεύουμε σε απλό κείμενο. Η απαρίθμηση `OfficeMathExportMode` έχει την επιλογή `LaTeX` που μετατρέπει κάθε εξίσωση στον κώδικα LaTeX της.

```csharp
        // Step 2: Configure text save options to export Office Math as LaTeX
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
```

> **Pro tip:** Αν χρειάζεστε τις εξισώσεις σε Unicode Math (για περιβάλλοντα που δεν καταλαβαίνουν LaTeX), αλλάξτε την απαρίθμηση σε `Unicode`. Αυτή η ευελιξία είναι ο λόγος που πολλοί επιλέγουν το Aspose.Words για εργασίες **convert word formulas text**.

## Βήμα 3: Αποθήκευση του εγγράφου ως αρχείο plain‑text με τις καθορισμένες επιλογές

Τώρα γράφουμε τα πάντα έξω. Το παραγόμενο αρχείο `.txt` θα περιέχει τις κανονικές παραγράφους αμετάβλητες, και κάθε εξίσωση θα εμφανίζεται ως απόσπασμα LaTeX, π.χ. `\int_{a}^{b} f(x)\,dx`.

```csharp
        // Step 3: Save the document as a plain‑text file with the specified options
        doc.Save("YOUR_DIRECTORY/formula.txt", txtSaveOptions);
    }
}
```

> **Τι θα δείτε:** Ανοίξτε το `formula.txt` και θα βρείτε κάτι όπως:

```
This is a regular paragraph.

\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
```

Το αρχείο plain‑text είναι τώρα έτοιμο για έλεγχο έκδοσης, εργαλεία diff ή οποιαδήποτε επόμενη διαδικασία που προτιμά ακατέργαστο LaTeX αντί για δυαδικό DOCX.

## Βήμα 4: Επαλήθευση του αποτελέσματος (προαιρετικό αλλά συνιστάται)

Μια γρήγορη επιβεβαίωση σας σώζει από προβλήματα αργότερα. Φορτώστε ξανά το αρχείο στον επεξεργαστή σας και ψάξτε για τον χαρακτήρα ανάστροφης καθέτου (`\`) – αυτό είναι καλός δείκτης ότι οι εξισώσεις εξήχθησαν.

```csharp
using System.IO;

string txtContent = File.ReadAllText("YOUR_DIRECTORY/formula.txt");
bool containsLatex = txtContent.Contains("\\");
Console.WriteLine($"LaTeX export successful? {containsLatex}");
```

Αν η κονσόλα εμφανίσει `True`, έχετε ολοκληρώσει με επιτυχία το **save word file txt** με εξισώσεις ενεργοποιημένες σε LaTeX.

## Συνηθισμένες Παραλλαγές & Ακραίες Περιπτώσεις

| Σενάριο | Πώς να Προσαρμόσετε |
|----------|---------------|
| **Μόνο plain text, χωρίς LaTeX** | Ορίστε `OfficeMathExportMode = OfficeMathExportMode.Text` για να λάβετε μια ανθρώπινα αναγνώσιμη περιγραφή της εξίσωσης. |
| **Διατήρηση των αλλαγών γραμμής ακριβώς όπως στο Word** | Χρησιμοποιήστε `txtSaveOptions.PreserveTableLayout = true;` – χρήσιμο όταν μετατρέπετε πίνακες μαζί με τύπους. |
| **Μαζική μετατροπή πολλών αρχείων DOCX** | Τυλίξτε τη λογική τριών βημάτων μέσα σε ένα βρόχο `foreach (var file in Directory.GetFiles(..., "*.docx"))`. |
| **Μεγάλα έγγραφα (>100 MB)** | Ενεργοποιήστε το streaming: `txtSaveOptions.UseEncoding = Encoding.UTF8;` και εξετάστε το `doc.UpdatePageLayout();` πριν την αποθήκευση για να αποφύγετε αιχμές μνήμης. |

## Pro Tips για Απρόσκοπτη Εμπειρία

- **Εγκατάσταση NuGet:** `dotnet add package Aspose.Words` – η έκδοση community λειτουργεί για τις περισσότερες μη‑εμπορικές περιπτώσεις.  
- **Διαδρομές αρχείων:** Χρησιμοποιήστε `Path.Combine(Environment.CurrentDirectory, "input.docx")` για να αποφύγετε σκληρά κωδικοποιημένους διαχωριστές.  
- **Κωδικοποίηση:** Η προεπιλογή είναι UTF‑8, αλλά μπορείτε να εξαναγκάσετε άλλη κωδικοποίηση με `txtSaveOptions.Encoding = Encoding.Unicode;` αν χρειάζεστε BOM.  
- **Απόδοση:** Η επαναχρησιμοποίηση μιας μόνο παρουσίας `TxtSaveOptions` σε πολλαπλές αποθηκεύσεις μειώνει το κόστος κατανομής μνήμης.

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό με αρχεία .doc (δυαδικά);**  
Α: Απόλυτα. Το Aspose.Words ανιχνεύει αυτόματα τη μορφή, οπότε μπορείτε να καλέσετε `new Document("file.doc")` και η ίδια αλυσίδα ενεργειών ισχύει.

**Ε: Τι γίνεται αν οι εξισώσεις μου περιέχουν προσαρμοσμένα σύμβολα;**  
Α: Η εξαγωγή LaTeX θα συμπεριλάβει τα σύμβολα εφόσον είναι μέρος του σχήματος Office Math. Για πραγματικά προσαρμοσμένα γλύφους, σκεφτείτε εξαγωγή σε MathML (`OfficeMathExportMode.MathML`) και στη συνέχεια μετατροπή σε LaTeX με κάποιο εργαλείο τρίτου μέρους.

**Ε: Μπορώ να ενσωματώσω το παραγόμενο `.txt` ξανά σε έγγραφο Word;**  
Α: Ναι – απλώς φορτώστε το κείμενο με `Document doc = new Document();` και εισάγετέ το μέσω `DocumentBuilder.InsertParagraph(txtContent);`. Τα αποσπάσματα LaTeX θα εμφανιστούν ως απλό κείμενο εκτός αν τα επεξεργαστείτε με κάποιο πρόσθετο Word που αποδίδει LaTeX.

## Συμπέρασμα

Τώρα ξέρετε **πώς να αποθηκεύσετε docx ως txt** διατηρώντας τις εξισώσεις σε LaTeX, **πώς να αποθηκεύσετε plain text από Word** για επεξεργασία downstream, και **πώς να μετατρέψετε word formulas text** σε μια καθαρή, αναζητήσιμη μορφή. Το τριβήμα‑κώδικα παραπάνω είναι μια πλήρης, εκτελέσιμη λύση που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να εξάγετε το ίδιο έγγραφο σε **Markdown** (`.md`) χρησιμοποιώντας `MarkdownSaveOptions`, ή εξερευνήστε τη μετατροπή σε **PDF** διατηρώντας τα αποσπάσματα LaTeX. Οι ίδιες αρχές—φόρτωση, διαμόρφωση, αποθήκευση—εφαρμόζονται σε όλες τις μορφές, οπότε θα βρείτε το μοτίβο εύκολο στην επαναχρησιμοποίηση.

Καλό coding, και οι μετατροπές σας να είναι πάντα χωρίς απώλειες!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}