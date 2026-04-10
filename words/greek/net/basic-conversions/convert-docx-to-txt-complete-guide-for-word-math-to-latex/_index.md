---
category: general
date: 2026-04-10
description: Μετατρέψτε γρήγορα το docx σε txt και επίσης μετατρέψτε τα μαθηματικά
  του Word σε LaTeX. Μάθετε πώς να εξάγετε απλό κείμενο από το Word με βήμα‑βήμα κώδικα
  C#.
draft: false
keywords:
- convert docx to txt
- convert word math
- plain text from word
- word to plain text
- how to convert docx
language: el
og_description: Μετατρέψτε docx σε txt και μετατρέψτε τα μαθηματικά του Word σε LaTeX.
  Αυτός ο οδηγός σας δείχνει ακριβώς πώς να εξάγετε απλό κείμενο από αρχεία Word.
og_title: Μετατροπή docx σε txt – Πλήρης οδηγός C#
tags:
- C#
- Aspose.Words
- Document Conversion
title: Μετατροπή docx σε txt – Πλήρης οδηγός για Word Math σε LaTeX
url: /el/net/basic-conversions/convert-docx-to-txt-complete-guide-for-word-math-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή docx σε txt – Πλήρες Tutorial C#

Έχετε χρειαστεί ποτέ να **μετατρέψετε docx σε txt** αλλά δεν ήξερες πώς να διατηρήσετε τις μαθηματικές εξισώσεις αναγνώσιμες; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν προσπαθούν να εξάγουν απλό κείμενο από ένα έγγραφο Word που περιέχει αντικείμενα Office Math. Τα καλά νέα; Με μερικές γραμμές C# και τις σωστές επιλογές αποθήκευσης, μπορείτε όχι μόνο να πάρετε *απλό κείμενο από το Word* αλλά και να εξάγετε αυτές τις εξισώσεις ως LaTeX.  

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: φόρτωση ενός αρχείου *.docx*, ρύθμιση του `TxtSaveOptions` για **μετατροπή word math**, και τέλος εγγραφή του αποτελέσματος σε αρχείο `.txt`. Στο τέλος θα έχετε ένα έτοιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET. Χωρίς εξωτερικά scripts, χωρίς χειροκίνητη αντιγραφή‑επικόλληση — μόνο καθαρή, προγραμματιστική μετατροπή.

## Τι Θα Μάθετε

- Πώς να **μετατρέψετε docx σε txt** χρησιμοποιώντας το Aspose.Words for .NET.  
- Τον ρόλο του `OfficeMathExportMode` και γιατί το LaTeX είναι συχνά η καλύτερη επιλογή για εξισώσεις.  
- Συμβουλές για τη διαχείριση αλλαγών γραμμής, κωδικοποίησης και μεγάλων εγγράφων.  
- Πώς να επαληθεύσετε ότι το αποτέλεσμα είναι πραγματικά *απλό κείμενο από το Word* και όχι ένα ακατάστατο σύνολο χαρακτήρων.  

**Προαπαιτούμενα** – Θα χρειαστείτε:

1. .NET 6+ (ή .NET Framework 4.7.2+) εγκατεστημένο.  
2. Αναφορά στο πακέτο NuGet `Aspose.Words` (`Install-Package Aspose.Words`).  
3. Ένα δείγμα `.docx` που περιέχει τουλάχιστον ένα αντικείμενο Office Math (το tutorial χρησιμοποιεί το `input.docx`).  

Τα έχετε; Τέλεια — ας βουτήξουμε.

![Διάγραμμα που δείχνει τη ροή από DOCX → μετατροπή C# → έξοδο TXT, επισημαίνοντας το βήμα εξαγωγής LaTeX.](convert-docx-to-txt-diagram.png "Ροή εργασίας μετατροπής docx σε txt")

## Βήμα 1: Φόρτωση του Αρχείου DOCX

Το πρώτο που χρειάζεται είναι ένα αντικείμενο `Document` που αντιπροσωπεύει το αρχείο προέλευσης. Αυτό το βήμα είναι απλό, αλλά αξίζει να σημειώσουμε γιατί *εγκαθιστούμε* τη φόρτωση του αρχείου αντί για τη χρήση ροής — έτσι εξασφαλίζουμε ότι τυχόν ενσωματωμένες γραμματοσειρές ή δεδομένα εξίσωσης έχουν αναλυθεί πλήρως.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of pages (optional)
Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
```

*Γιατί είναι σημαντικό*: Η πρώιμη φόρτωση του εγγράφου επιτρέπει στο Aspose.Words να δημιουργήσει το εσωτερικό μοντέλο αντικειμένων, το οποίο περιλαμβάνει κόμβους `OfficeMath`. Αυτοί οι κόμβοι είναι αυτοί που θα μετατρέψουμε αργότερα σε LaTeX.

## Βήμα 2: Ρύθμιση Επιλογών Αποθήκευσης TXT (Μετατροπή Word Math)

Τώρα έρχεται η μαγεία. Από προεπιλογή, το `TxtSaveOptions` θα αποτύπωνε το ακατέργαστο markup της εξίσωσης, το οποίο δεν μοιάζει καθόλου με αναγνώσιμα μαθηματικά. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX` λέμε στη βιβλιοθήκη να μεταφράσει κάθε αντικείμενο Office Math στην αναπαράστασή του σε LaTeX — ιδανικό για προγραμματιστές που χρειάζονται τις εξισώσεις αργότερα.

```csharp
// Step 2: Create TXT save options and set the Office Math export mode to LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes sure every equation becomes LaTeX code in the txt file
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: define the encoding (UTF‑8 works for most languages)
    Encoding = System.Text.Encoding.UTF8,

    // Optional: preserve line breaks as they appear in Word
    PreserveTableLayout = true
};
```

**Εξήγηση**:  
- `OfficeMathExportMode.LaTeX` → μετατρέπει εξισώσεις όπως `x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}`.  
- `Encoding.UTF8` → αποτρέπει ακατάστατους χαρακτήρες όταν η πηγή περιέχει μη‑ASCII κείμενο (σημαντικό για *απλό κείμενο από το Word* σε πολυγλωσσικά περιβάλλοντα).  
- `PreserveTableLayout` → διατηρεί τους πίνακες αναγνώσιμους ευθυγραμμίζοντας τις στήλες με κενά.

## Βήμα 3: Αποθήκευση του Εγγράφου ως Αρχείο Απλού Κειμένου

Με τις επιλογές έτοιμες, απλώς καλούμε το `Save`. Η μέθοδος σέβεται όλα όσα ορίσαμε, έτσι το παραγόμενο `.txt` είναι ένα καθαρό, αναζητήσιμο αρχείο που περιέχει ακόμη LaTeX για κάθε εξίσωση.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save("YOUR_DIRECTORY/output.txt", txtOptions);

Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY/output.txt");
```

**Αποτέλεσμα**: Ανοίξτε το `output.txt` σε οποιονδήποτε επεξεργαστή και θα δείτε κανονικές παραγράφους, κουκίδες, και — για κάθε εξίσωση — ένα απόσπασμα LaTeX περικλεισμένο σε `$...$` (ή μπλοκ `\begin{equation}`, ανάλογα με την αρχική διάταξη). Αυτό είναι ακριβώς αυτό που περιμένετε όταν *μετατρέπετε word math* για επόμενη επεξεργασία.

## Βήμα 4: Επαλήθευση του Αποτελέσματος (Απλό Κείμενο από το Word)

Είναι εύκολο να υποθέσουμε ότι η μετατροπή λειτούργησε, αλλά ένα γρήγορο βήμα επαλήθευσης εξοικονομεί ώρες εντοπισμού σφαλμάτων αργότερα. Εδώ είναι ένας μικρός βοηθός που μπορείτε να τρέξετε αμέσως μετά την αποθήκευση:

```csharp
// Verify that the txt file contains LaTeX equations
string[] lines = System.IO.File.ReadAllLines("YOUR_DIRECTORY/output.txt");
bool hasLatex = lines.Any(l => l.Contains(@"\\") || l.Contains("$"));

Console.WriteLine(hasLatex
    ? "LaTeX equations detected – conversion successful."
    : "No LaTeX found – double‑check OfficeMathExportMode.");
```

Αν δείτε το μήνυμα “LaTeX equations detected”, έχετε επιτυχώς **μετατρέψει docx σε txt** *και* **μετατρέψει word math** ταυτόχρονα.

## Συνηθισμένα Προβλήματα & Pro Tips (Word σε Απλό Κείμενο)

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Λείπουν εξισώσεις** | `OfficeMathExportMode` παραμένει στην προεπιλογή (`Text`) | Ορίστε ρητά `OfficeMathExportMode = OfficeMathExportMode.LaTeX` |
| **Ακατάστατοι χαρακτήρες** | Λάθος κωδικοποίηση αρχείου (π.χ. προεπιλογή ANSI) | Χρησιμοποιήστε `Encoding = Encoding.UTF8` στο `TxtSaveOptions` |
| **Οι πίνακες φαίνονται σαν τοίχος κειμένου** | `PreserveTableLayout` απενεργοποιημένο | Ενεργοποιήστε `PreserveTableLayout = true` |
| **Μεγάλα έγγραφα προκαλούν OutOfMemory** | Φόρτωση ολόκληρου αρχείου στη μνήμη | Διαβάστε το έγγραφο με ροή (`Document doc = new Document(new FileStream(...))`) και επεξεργαστείτε σε τμήματα αν χρειάζεται |
| **Χαμένη μορφοποίηση εξίσωσης** | Χρήση παλαιότερης έκδοσης Aspose.Words | Αναβαθμίστε στην πιο πρόσφατη έκδοση NuGet (υποστηρίζει OfficeMathExportMode) |

**Pro tip**: Αν χρειάζεστε μόνο το ακατέργαστο κείμενο της εξίσωσης (χωρίς LaTeX), αλλάξτε το `OfficeMathExportMode` σε `Text`. Η ίδια βάση κώδικα λειτουργεί και για τις δύο περιπτώσεις, καθιστώντας εύκολη τη **μετατροπή docx σε txt** στη μορφή που προτιμάτε.

## Ακραίες Περιπτώσεις: Διαχείριση Εικόνων και Υποσημειώσεων

- **Εικόνες**: Η μετατροπή σε απλό κείμενο αφαιρεί τις εικόνες αυτόματα. Αν χρειάζεστε αναφορές εικόνων, σκεφτείτε την εξαγωγή σε HTML πρώτα, έπειτα εξαγωγή των χαρακτηριστικών `src`.  
- **Υποσημειώσεις/Σημειώσεις τέλους**: Εμφανίζονται ενσωματωμένες στο txt, προεξοχή με αριθμό σε αγκύλες. Αν προτιμάτε να συγκεντρωθούν στο τέλος, θα χρειαστείτε έναν προσαρμοσμένο post‑processor που θα αναλύει τους κόμβους `Footnote` πριν την αποθήκευση.

## Πλήρες Παράδειγμα (Αντιγραφή‑Επικόλληση Έτοιμο)

Ακολουθεί ολόκληρο το πρόγραμμα, έτοιμο για μεταγλώττιση. Αντικαταστήστε το `YOUR_DIRECTORY` με το φάκελο που περιέχει το `.docx` σας.

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToTxtConverter
{
    static void Main()
    {
        // 1️⃣ Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        Console.WriteLine($"Loaded document – pages: {doc.PageCount}");

        // 2️⃣ Configure save options (convert word math to LaTeX)
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            Encoding = System.Text.Encoding.UTF8,
            PreserveTableLayout = true
        };

        // 3️⃣ Save as plain‑text file
        string outputPath = "YOUR_DIRECTORY/output.txt";
        doc.Save(outputPath, txtOptions);
        Console.WriteLine($"File saved to {outputPath}");

        // 4️⃣ Quick verification
        string[] lines = File.ReadAllLines(outputPath);
        bool hasLatex = lines.Any(l => l.Contains(@"\\") || l.Contains("$"));
        Console.WriteLine(hasLatex
            ? "✅ LaTeX equations detected – conversion successful."
            : "⚠️ No LaTeX found – check OfficeMathExportMode setting.");
    }
}
```

Τρέξτε αυτό το πρόγραμμα (`dotnet run` ή από το Visual Studio) και ανοίξτε το `output.txt`. Θα δείτε απλό κείμενο με ενσωματωμένα αποσπάσματα LaTeX, επιβεβαιώνοντας ότι έχετε **μετατρέψει docx σε txt** διατηρώντας τα μαθηματικά.

## Επόμενα Βήματα & Σχετικά Θέματα

- **Πώς να μετατρέψετε docx** σε άλλες μορφές (PDF, HTML) — η ίδια μέθοδος `Save` με διαφορετικές `SaveOptions`.  
- **Απλό κείμενο από το Word** για ευρετηρίαση — συνδυάστε αυτήν την προσέγγιση με tokenizer για δημιουργία ευρετηρίου.  
- **Εξαγωγή εξισώσεων σε MathML** — αλλάξτε το `OfficeMathExportMode` σε `MathML` αν χρειάζεστε XML‑βασισμένα μαθηματικά για ιστοσελίδες.  
- **Επεξεργασία σε παρτίδες** — τυλίξτε τον κώδικα σε βρόχο `foreach` για αυτόματη επεξεργασία δεκάδων αρχείων.

---

### TL;DR

Τώρα γνωρίζετε ακριβώς **πώς να μετατρέψετε docx σε txt** σε C#, συμπεριλαμβανομένου του κρίσιμου βήματος **convert word math** σε LaTeX. Η λύση είναι αυτοδυναμική, λειτουργεί με τη νεότερη βιβλιοθήκη Aspose.Words, και αντιμετωπίζει κοινές ακραίες περιπτώσεις όπως κωδικοποίηση και διάταξη πινάκων. Πειραματιστείτε — αλλάξτε το mode εξαγωγής, προσαρμόστε την κωδικοποίηση, ή ενσωματώστε τον κώδικα σε μεγαλύτερο pipeline αυτοματοποίησης. Καλή προγραμματιστική διασκέδαση!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}