---
category: general
date: 2026-03-30
description: Πώς να εξάγετε LaTeX από αρχείο DOCX και να μετατρέψετε DOCX σε TXT,
  εξάγοντας το κείμενο και τις εξισώσεις του Word ως MathML ή LaTeX.
draft: false
keywords:
- how to export latex
- convert docx to txt
- extract text from docx
- convert word equations
- save document as txt
language: el
og_description: Πώς να εξάγετε LaTeX από αρχείο DOCX, να μετατρέψετε το DOCX σε TXT
  και να εξάγετε εξισώσεις Word σε μια ομαλή ροή εργασίας.
og_title: Πώς να εξάγετε LaTeX από DOCX – Μετατροπή σε TXT
tags:
- Aspose.Words
- C#
- Document Conversion
title: Πώς να εξάγετε LaTeX από DOCX – Μετατροπή σε TXT
url: /el/net/basic-conversions/how-to-export-latex-from-docx-convert-to-txt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εξάγετε LaTeX από DOCX – Μετατροπή σε TXT

Έχετε αναρωτηθεί ποτέ **πώς να εξάγετε LaTeX** από ένα αρχείο Word *.docx* χωρίς να ανοίξετε το έγγραφο χειροκίνητα; Δεν είστε μόνοι. Σε πολλά έργα χρειάζεται να **μετατρέψουμε docx σε txt**, να πάρουμε το ακατέργαστο κείμενο και να διατηρήσουμε εκείνες τις επίμονες εξισώσεις OfficeMath ως καθαρό LaTeX ή MathML.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα C# που κάνει ακριβώς αυτό. Στο τέλος θα μπορείτε να εξάγετε κείμενο από docx, να μετατρέψετε τις εξισώσεις του Word και **να αποθηκεύσετε το έγγραφο ως txt** με μία μόνο κλήση μεθόδου. Χωρίς επιπλέον εργαλεία, μόνο Aspose.Words για .NET.

> **Pro tip:** Η ίδια προσέγγιση λειτουργεί με .NET 6+ και .NET Framework 4.7+. Απλώς βεβαιωθείτε ότι έχετε αναφερθεί στο τελευταίο πακέτο NuGet του Aspose.Words.

![How to export LaTeX from DOCX example](https://example.com/images/export-latex-docx.png "How to export LaTeX from DOCX")

## Τι Θα Μάθετε

- Φόρτωση αρχείου *.docx* προγραμματιστικά.  
- Διαμόρφωση του `TxtSaveOptions` ώστε τα αντικείμενα OfficeMath να εξάγονται ως **LaTeX** (ή MathML).  
- Αποθήκευση του αποτελέσματος ως αρχείο απλού κειμένου *.txt*, διατηρώντας τόσο το συνηθισμένο κείμενο όσο και τις εξισώσεις.  
- Επαλήθευση του αποτελέσματος και προσαρμογή της λειτουργίας εξαγωγής για διαφορετικές ανάγκες.  

### Προαπαιτούμενα

- .NET 6 SDK (ή οποιαδήποτε πρόσφατη έκδοση .NET Framework).  
- Visual Studio 2022 ή VS Code με επεκτάσεις C#.  
- Aspose.Words για .NET (εγκατάσταση μέσω `dotnet add package Aspose.Words`).  

Αν έχετε καλύψει αυτά τα βασικά, ας βουτήξουμε.

## Βήμα 1: Φόρτωση του Πηγής Εγγράφου

Το πρώτο που χρειαζόμαστε είναι μια παρουσία `Document` που δείχνει στο αρχείο Word που θέλουμε να επεξεργαστούμε. Αυτό είναι το θεμέλιο για **extract text from docx** αργότερα.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Replace with the actual path to your .docx file
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document – this reads the entire Word package into memory
Document doc = new Document(inputPath);
```

*Γιατί είναι σημαντικό:* Η φόρτωση του εγγράφου μας δίνει πρόσβαση στο εσωτερικό μοντέλο αντικειμένων, συμπεριλαμβανομένων των κόμβων `OfficeMath` που αντιπροσωπεύουν τις εξισώσεις. Χωρίς αυτό το βήμα δεν μπορούμε να **convert word equations**.

## Βήμα 2: Ρύθμιση Επιλογών Αποθήκευσης TXT – Επιλογή Λειτουργίας Εξαγωγής

Το Aspose.Words σας επιτρέπει να αποφασίσετε πώς θα αποδοθούν τα OfficeMath όταν αποθηκεύονται ως απλό κείμενο. Μπορείτε να επιλέξετε **MathML** (χρήσιμο για web) ή **LaTeX** (τέλειο για επιστημονική δημοσίευση). Δείτε πώς να διαμορφώσετε τον εξαγωγέα:

```csharp
// Create TxtSaveOptions and tell Aspose how to handle equations
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Switch to MathML if you prefer that format:
    // OfficeMathExportMode = OfficeMathExportMode.MathML

    // By default we export as LaTeX – the primary keyword in action
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

*Γιατί είναι σημαντικό:* Η σημαία `OfficeMathExportMode` είναι το κλειδί για **how to export latex** από ένα DOCX. Αλλάζοντάς την σε `MathML` θα λάβετε σήμανση βασισμένη σε XML αντί για LaTeX.

## Βήμα 3: Αποθήκευση του Εγγράφου ως Απλό Κείμενο

Τώρα που οι επιλογές έχουν οριστεί, απλώς καλούμε το `Save`. Το αποτέλεσμα είναι ένα αρχείο `.txt` που περιέχει κανονικές παραγράφους συν τα αποσπάσματα LaTeX για κάθε εξίσωση.

```csharp
// Define the output path – you can change the extension to .txt
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.txt");

// Save the document using the configured TxtSaveOptions
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document successfully saved to: {outputPath}");
```

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `output.txt` και θα δείτε κάτι όπως:

```
This is a regular paragraph from the original DOCX.

Here is an equation in LaTeX form:
\[
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
\]

Another paragraph follows...
```

Όλο το κανονικό κείμενο εμφανίζεται αμετάβλητο, ενώ κάθε αντικείμενο OfficeMath αντικαθίσταται από την LaTeX αναπαράστασή του. Αν είχατε επιλέξει `MathML`, θα δείτε ετικέτες `<math>` αντί.

## Βήμα 4: Επαλήθευση και Προσαρμογή (Προαιρετικό)

Είναι καλή συνήθεια να ελέγχετε ξανά ότι η μετατροπή έγινε όπως αναμενόταν, ειδικά όταν δουλεύετε με σύνθετες εξισώσεις.

```csharp
// Quick sanity check – read the first 200 characters
string sample = File.ReadAllText(outputPath).Substring(0, 200);
Console.WriteLine("Snippet of output:");
Console.WriteLine(sample);
```

Αν παρατηρήσετε ότι λείπουν εξισώσεις, βεβαιωθείτε ότι το αρχικό DOCX περιέχει πραγματικά αντικείμενα `OfficeMath` (εμφανίζονται ως “Equation” στο Word). Για παλαιότερες εξισώσεις που δημιουργήθηκαν με τον παλιό Equation Editor, ίσως χρειαστεί πρώτα να τις μετατρέψετε σε OfficeMath (δείτε την τεκμηρίωση του Aspose για `ConvertMathObjectsToOfficeMath`).

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Ερώτηση | Απάντηση |
|---|---|
| **Μπορώ να εξάγω τόσο LaTeX **και** MathML στο ίδιο αρχείο;** | Όχι άμεσα – χρειάζεται να εκτελέσετε την αποθήκευση δύο φορές με διαφορετικές τιμές `OfficeMathExportMode` και να συγχωνεύσετε τα αποτελέσματα χειροκίνητα. |
| **Τι γίνεται αν το DOCX περιέχει εικόνες;** | Οι εικόνες αγνοούνται όταν αποθηκεύετε σε απλό κείμενο· δεν θα εμφανιστούν στο `output.txt`. Αν χρειάζεστε δεδομένα εικόνας, σκεφτείτε αποθήκευση σε HTML ή PDF. |
| **Είναι η μετατροπή thread‑safe;** | Ναι, εφόσον κάθε νήμα δουλεύει με τη δική του παρουσία `Document`. Η κοινή χρήση ενός μόνο `Document` μεταξύ νημάτων μπορεί να προκαλέσει συνθήκες αγώνα. |
| **Χρειάζομαι άδεια για το Aspose.Words;** | Η βιβλιοθήκη λειτουργεί σε λειτουργία αξιολόγησης, αλλά το αποτέλεσμα θα περιέχει υδατογράφημα. Για παραγωγική χρήση, αποκτήστε άδεια ώστε να αφαιρέσετε το υδατογράφημα και να ξεκλειδώσετε πλήρη απόδοση. |

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```csharp
// ---------------------------------------------------------------
// Complete C# console app – Export LaTeX from DOCX to TXT
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document doc = new Document(inputPath);

        // 2️⃣ Configure TXT save options – export OfficeMath as LaTeX
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX   // change to MathML if needed
        };

        // 3️⃣ Save the document as a plain‑text file using the configured options
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.txt");
        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"✅ Success! File saved to: {outputPath}");

        // Optional: show a snippet of the result
        string snippet = File.ReadAllText(outputPath).Substring(0,
            Math.Min(200, (int)new FileInfo(outputPath).Length));
        Console.WriteLine("\n--- Output Preview ---");
        Console.WriteLine(snippet);
    }
}
```

Τρέξτε το πρόγραμμα και θα έχετε ένα καθαρό αρχείο `.txt` που **extracts text from docx** ενώ διατηρεί κάθε εξίσωση ως LaTeX.  

---

## Συμπέρασμα

Μόλις καλύψαμε **πώς να εξάγουμε LaTeX** από ένα αρχείο DOCX, μετατρέψαμε το έγγραφο σε απλό κείμενο και μάθαμε πώς να **convert docx to txt** διατηρώντας τις εξισώσεις ανέπαφες. Η τρι‑βήμα ροή — φόρτωση, διαμόρφωση, αποθήκευση — εκτελεί τη δουλειά με ελάχιστο κώδικα και μέγιστη ευελιξία.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να αλλάξετε το `OfficeMathExportMode.MathML` για να δημιουργήσετε MathML, ή συνδυάστε αυτήν την προσέγγιση με έναν επεξεργαστή batch που διασχίζει ολόκληρο φάκελο αρχείων Word. Μπορείτε επίσης να διοχετεύσετε το παραγόμενο `.txt` σε έναν static‑site generator για μια αναζητήσιμη βάση γνώσεων.

Αν βρήκατε αυτόν τον οδηγό χρήσιμο, δώστε του αστέρι στο GitHub, μοιραστείτε το με έναν συνάδελφο, ή αφήστε ένα σχόλιο παρακάτω με τις δικές σας συμβουλές. Καλό coding, και οι εξαγωγές LaTeX σας να είναι πάντα άψογες!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}