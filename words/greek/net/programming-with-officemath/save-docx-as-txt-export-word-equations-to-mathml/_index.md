---
category: general
date: 2026-06-24
description: Αποθηκεύστε το docx ως txt και μετατρέψτε εύκολα τα μαθηματικά του Word
  σε LaTeX ή εξάγετε τις εξισώσεις του Word σε MathML για επεξεργασία σε επόμενα στάδια.
  Οδηγός βήμα‑βήμα.
draft: false
keywords:
- save docx as txt
- convert word math to latex
- export word equations mathml
- extract equations from word
language: el
og_description: Αποθηκεύστε το docx ως txt και εξάγετε τις εξισώσεις του Word σε MathML
  (ή LaTeX) με ένα πλήρες παράδειγμα κώδικα. Μάθετε πώς να εξάγετε εξισώσεις από το
  Word.
og_title: αποθήκευση docx ως txt – Εξαγωγή εξισώσεων Word σε MathML
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: save docx as txt and easily convert word math to LaTeX or export word
    equations MathML for downstream processing. Step‑by‑step guide.
  headline: save docx as txt – Export Word Equations to MathML
  type: TechArticle
- description: save docx as txt and easily convert word math to LaTeX or export word
    equations MathML for downstream processing. Step‑by‑step guide.
  name: save docx as txt – Export Word Equations to MathML
  steps:
  - name: – Load the source document
    text: First we need to bring the `.docx` into memory. The `Document` class does
      all the heavy lifting.
  - name: – Choose how to export the equations
    text: Aspose.Words lets you decide whether you want **MathML** (ideal for web
      rendering) or **LaTeX** (perfect for scientific pipelines). This is controlled
      via the `OfficeMathExportMode` property of `TxtSaveOptions`.
  - name: – Save the document as plain‑text
    text: Now we write the file. The `Save` method respects the options we just set,
      so every equation is replaced by its chosen markup.
  - name: – Verify the output (optional but recommended)
    text: It’s good practice to read the file back and confirm that the markup appears
      where you expect it.
  - name: Multiple equations on the same line
    text: 'Word sometimes stores several `OfficeMath` objects in a single paragraph.
      Aspose.Words will serialize each one sequentially, preserving whitespace. If
      you need a custom separator, you can post‑process the text:'
  - name: Documents without any equations
    text: '`TxtSaveOptions` still works—your output will be a faithful plain‑text
      copy of the original document. No special handling required, but you might want
      to log a warning:'
  - name: Large files and memory usage
    text: 'For massive Word files, consider using the **LoadOptions** constructor
      that streams the document instead of loading it entirely into memory:'
  type: HowTo
tags:
- Aspose.Words
- .NET
- document-conversion
title: Αποθήκευση docx ως txt – Εξαγωγή εξισώσεων Word σε MathML
url: /el/net/programming-with-officemath/save-docx-as-txt-export-word-equations-to-mathml/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# αποθήκευση docx ως txt – Εξαγωγή Εξισώσεων Word σε MathML

Έχετε αναρωτηθεί ποτέ πώς να **αποθηκεύσετε docx ως txt** διατηρώντας εκείνες τις επίμονες εξισώσεις ανέπαφες; Δεν είστε ο μόνος. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν πρέπει να εξάγουν μαθηματικά από ένα αρχείο Word και να τα δώσουν σε έναν επεξεργαστή που καταλαβαίνει μόνο απλό κείμενο.

Το θέμα είναι: μπορείτε να το κάνετε σε μερικές γραμμές C# χωρίς να γράψετε τον δικό σας parser. Σε αυτό το tutorial θα περάσουμε από τη μετατροπή ενός αρχείου `.docx` σε αρχείο `.txt`, εξάγοντας τις εξισώσεις είτε ως **MathML** είτε ως **LaTeX** — ακριβώς ό,τι χρειάζεστε για **να εξάγετε εξισώσεις από το Word** και να τις κρατήσετε χρήσιμες.

Με το τέλος αυτού του οδηγού θα μπορείτε να:

* Φορτώσετε οποιοδήποτε έγγραφο Word με Aspose.Words.
* Επιλέξετε τη λειτουργία εξαγωγής εξισώσεων (`MathML` ή `LaTeX`).
* Αποθηκεύσετε το αποτέλεσμα ως απλό‑κείμενο, διατηρώντας κάθε τύπο.
* Επαληθεύσετε το αποτέλεσμα και αντιμετωπίσετε κοινές περιπτώσεις άκρων.

Χωρίς περιττές πληροφορίες, μόνο μια πλήρης, εκτελέσιμη λύση που μπορείτε να αντιγράψετε‑επικολλήσετε στο έργο σας.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

* **.NET 6.0** (ή νεότερο) εγκατεστημένο – ο κώδικας εκτελείται σε Windows, Linux ή macOS.
* Πακέτο NuGet **Aspose.Words for .NET**. Εγκαταστήστε το με:

```bash
dotnet add package Aspose.Words
```

* Ένα έγγραφο Word (`.docx`) που περιέχει τουλάχιστον μία εξίσωση. Αν δεν έχετε κάποιο, δημιουργήστε ένα γρήγορο αρχείο στο Microsoft Word και εισάγετε μια εξίσωση μέσω **Insert → Equation**.

Αυτό είναι όλο. Δεν χρειάζονται πρόσθετες βιβλιοθήκες, δεν υπάρχει COM interop, και απολύτως καμία χειροκίνητη ανάλυση.

## αποθήκευση docx ως txt με Aspose.Words

Ο πυρήνας της λύσης βρίσκεται σε τρία απλά βήματα: φόρτωση, διαμόρφωση και αποθήκευση. Ας αναλύσουμε καθένα.

### Βήμα 1 – Φόρτωση του πηγαίου εγγράφου

Πρώτα πρέπει να φορτώσουμε το `.docx` στη μνήμη. Η κλάση `Document` κάνει όλη τη βαριά δουλειά.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file from disk
Document doc = new Document(@"C:\Temp\input.docx");
```

*Γιατί είναι σημαντικό*: Η `Document` αναλύει το πακέτο OpenXML, δημιουργεί ένα μοντέλο αντικειμένων και μας δίνει άμεση πρόσβαση σε κάθε στοιχείο — συμπεριλαμβανομένων των αντικειμένων `OfficeMath` που αντιπροσωπεύουν εξισώσεις.

### Βήμα 2 – Επιλογή τρόπου εξαγωγής των εξισώσεων

Το Aspose.Words σας επιτρέπει να αποφασίσετε αν θέλετε **MathML** (ιδανικό για απόδοση στο web) ή **LaTeX** (τέλειο για επιστημονικές ροές). Αυτό ελέγχεται μέσω της ιδιότητας `OfficeMathExportMode` του `TxtSaveOptions`.

```csharp
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Switch between MathML and LaTeX by changing the enum value
    OfficeMathExportMode = OfficeMathExportMode.MathML   // or OfficeMathExportMode.LaTeX
};
```

*Συμβουλή*: Αν τροφοδοτείτε το κείμενο σε μια μηχανή που καταλαβαίνει LaTeX (π.χ., Pandoc ή Jupyter notebook), ορίστε τη λειτουργία σε `LaTeX`. Για προβολείς στο web που καταλαβαίνουν MathML, μείνετε στο `MathML`.

### Βήμα 3 – Αποθήκευση του εγγράφου ως απλό‑κείμενο

Τώρα γράφουμε το αρχείο. Η μέθοδος `Save` σέβεται τις επιλογές που μόλις ορίσαμε, έτσι κάθε εξίσωση αντικαθίσταται με το επιλεγμένο markup.

```csharp
// Save as a .txt file; equations are now MathML or LaTeX strings
doc.Save(@"C:\Temp\Equations.txt", txtOptions);
```

Αυτή είναι ολόκληρη η διαδικασία. Όταν ανοίξετε το `Equations.txt` θα δείτε κάτι σαν:

```
This is a sample paragraph.

<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mrow>
    <mi>x</mi>
    <mo>=</mo>
    <mfrac>
      <mn>‑b</mn>
      <mi>a</mi>
    </mfrac>
  </mrow>
</math>

Another paragraph with no equations.
```

Αν αλλάξετε σε `LaTeX`, το απόσπασμα θα είναι ως εξής:

```
This is a sample paragraph.

\[
x = \frac{-b}{a}
\]

Another paragraph with no equations.
```

### Βήμα 4 – Επαλήθευση του αποτελέσματος (προαιρετικό αλλά συνιστάται)

Είναι καλή πρακτική να διαβάσετε ξανά το αρχείο και να επιβεβαιώσετε ότι το markup εμφανίζεται όπου το περιμένετε.

```csharp
string txtContent = File.ReadAllText(@"C:\Temp\Equations.txt");

// Simple sanity check: look for a MathML tag or a LaTeX delimiter
bool containsMathML = txtContent.Contains("<math");
bool containsLaTeX = txtContent.Contains("\\[") && txtContent.Contains("\\]");

Console.WriteLine($"MathML detected: {containsMathML}");
Console.WriteLine($"LaTeX detected: {containsLaTeX}");
```

Αν η κονσόλα εκτυπώσει `true` για τη μορφή που επιλέξατε, έχετε επιτυχώς **μετατρέψει τα μαθηματικά του Word σε LaTeX** (ή MathML). Αν όχι, ελέγξτε ξανά την τιμή του `OfficeMathExportMode`.

## Διαχείριση κοινών περιπτώσεων άκρων

### Πολλαπλές εξισώσεις στην ίδια γραμμή

Το Word μερικές φορές αποθηκεύει πολλά αντικείμενα `OfficeMath` σε μία παράγραφο. Το Aspose.Words θα σειριοποιήσει το καθένα διαδοχικά, διατηρώντας τα κενά. Αν χρειάζεστε προσαρμοσμένο διαχωριστικό, μπορείτε να επεξεργαστείτε το κείμενο μετά:

```csharp
string processed = Regex.Replace(txtContent, @"(?<=\])\s+(?=\[)", "\n---\n");
File.WriteAllText(@"C:\Temp\ProcessedEquations.txt", processed);
```

### Έγγραφα χωρίς εξισώσεις

Το `TxtSaveOptions` λειτουργεί ακόμη — η έξοδός σας θα είναι ένα πιστό αντίγραφο απλού κειμένου του αρχικού εγγράφου. Δεν απαιτείται ειδική διαχείριση, αλλά ίσως θέλετε να καταγράψετε μια προειδοποίηση:

```csharp
if (!txtContent.Contains("<math") && !txtContent.Contains("\\["))
{
    Console.WriteLine("Warning: No equations were found in the source document.");
}
```

### Μεγάλα αρχεία και χρήση μνήμης

Για τεράστια αρχεία Word, σκεφτείτε να χρησιμοποιήσετε τον κατασκευαστή **LoadOptions** που μεταδίδει το έγγραφο αντί να το φορτώνει πλήρως στη μνήμη:

```csharp
LoadOptions loadOpts = new LoadOptions { LoadFormat = LoadFormat.Docx };
Document largeDoc = new Document(@"C:\Temp\bigfile.docx", loadOpts);
largeDoc.Save(@"C:\Temp\bigfile.txt", txtOptions);
```

Αυτή η προσέγγιση διατηρεί τη διαδικασία **εξαγωγής εξισώσεων από το Word** ελαφριά.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα, εδώ είναι ένα πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document
        string inputPath = @"C:\Temp\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Configure TXT save options – change to LaTeX if you prefer
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.MathML // or OfficeMathExportMode.LaTeX
        };

        // 3️⃣ Save as plain‑text with equations exported
        string outputPath = @"C:\Temp\Equations.txt";
        doc.Save(outputPath, txtOptions);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ Verify the result (optional)
        string txtContent = File.ReadAllText(outputPath);
        bool hasMathML = txtContent.Contains("<math");
        bool hasLaTeX = txtContent.Contains("\\[") && txtContent.Contains("\\]");

        Console.WriteLine($"MathML present: {hasMathML}");
        Console.WriteLine($"LaTeX present: {hasLaTeX}");

        // 5️⃣ Simple post‑processing example (add a visual separator)
        string processed = Regex.Replace(txtContent, @"(?<=\])\s+(?=\[)", "\n---\n");
        File.WriteAllText(@"C:\Temp\ProcessedEquations.txt", processed);
        Console.WriteLine("Post‑processed file created.");
    }
}
```

**Αναμενόμενο αποτέλεσμα** (όταν χρησιμοποιείται `OfficeMathExportMode.MathML`):

```
Document saved to C:\Temp\Equations.txt
MathML present: True
LaTeX present: False
Post‑processed file created.
```

Ανοίξτε το `Equations.txt` για να δείτε τις ακατέργαστες ετικέτες MathML· ανοίξτε το `ProcessedEquations.txt` για να δείτε το προσαρμοσμένο διαχωριστικό που έχει εισαχθεί μεταξύ οποιωνδήποτε διαδοχικών μπλοκ LaTeX.

## Συχνές ερωτήσεις

* **Μπορώ να εξάγω ταυτόχρονα MathML *και* LaTeX;**  
  Δεν είναι δυνατό άμεσα — το Aspose.Words σας επιτρέπει να επιλέξετε μία λειτουργία ανά αποθήκευση. Η λύση είναι να εκτελέσετε την αποθήκευση δύο φορές με διαφορετικές επιλογές και να συγχωνεύσετε τα αποτελέσματα εσείς.

* **Τι γίνεται με τις εξισώσεις μέσα σε πίνακες;**  
  Θεωρούνται ακριβώς όπως οποιοδήποτε άλλο αντικείμενο `OfficeMath`. Το markup θα εμφανίζεται ενσωματωμένο με το κείμενο των γύρω κελιών.

* **Είναι η βιβλιοθήκη δωρεάν;**  
  Το Aspose.Words προσφέρει δωρεάν δοκιμή με πλήρη λειτουργικότητα. Για παραγωγική χρήση θα χρειαστείτε άδεια, αλλά η διεπαφή API παραμένει η ίδια.

## Συμπέρασμα

Σας δείξαμε πώς να **αποθηκεύσετε docx ως txt** διατηρώντας κάθε τύπο, δίνοντάς σας τη δυνατότητα να **μετατρέψετε τα μαθηματικά του Word σε LaTeX** ή **να εξάγετε τις εξισώσεις του Word σε MathML** για οποιαδήποτε επόμενη ροή εργασίας. Η προσέγγιση είναι ελαφριά, απαιτεί μόνο το Aspose.Words και λειτουργεί σε όλες τις κύριες πλατφόρμες .NET.

Τι επόμενα; Δοκιμάστε να τροφοδοτήσετε το παραγόμενο MathML σε μια HTML σελίδα με MathJax, ή να περάσετε το LaTeX σε έναν static‑site generator που υποστηρίζει μαθηματικά. Μπορείτε επίσης να αυτοματοποιήσετε την επεξεργασία σε παρτίδες ολόκληρου φακέλου αρχείων Word — απλώς τυλίξτε τον κώδικα σε έναν βρόχο `foreach`.

Έχετε περισσότερα σενάρια στο μυαλό σας — όπως η εξαγωγή μόνο των εξισώσεων και η απόρριψη του περιβάλλοντος κειμένου; Μη διστάσετε να πειραματιστείτε με το `Document.GetChildNodes(NodeType.Office`

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to Export LaTeX from Word: Convert DOCX to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/how-to-export-latex-from-word-convert-docx-to-markdown-with/)
- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Save docx as markdown – Complete C# Guide with LaTeX Equations](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-c-guide-with-latex-equations/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}