---
category: general
date: 2026-04-05
description: Αποθήκευση docx ως txt με το Aspose.Words – γρήγορη μετατροπή Word σε
  txt και μάθετε πώς να εξάγετε μαθηματικές εξισώσεις ως LaTeX. Απλός κώδικας C#,
  χωρίς επιπλέον εργαλεία.
draft: false
keywords:
- save docx as txt
- convert word to txt
- how to export math
- how to save txt
- convert word equations latex
language: el
og_description: Αποθηκεύστε το docx ως txt σε C# και δείτε πώς να εξάγετε μαθηματικά
  σε LaTeX. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να μετατρέψετε το Word σε txt
  με τις εξισώσεις αμετάβλητες.
og_title: Αποθήκευση docx ως txt – Εξαγωγή εξισώσεων Word σε LaTeX
tags:
- Aspose.Words
- C#
- Document Conversion
title: Αποθήκευση docx ως txt – Εξαγωγή εξισώσεων Word σε LaTeX με C#
url: /el/net/programming-with-txtsaveoptions/save-docx-as-txt-export-word-equations-to-latex-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# αποθήκευση docx ως txt – Εξαγωγή εξισώσεων Word σε LaTeX με C#

Έχετε ποτέ χρειαστεί να **αποθηκεύσετε docx ως txt** αλλά ανησυχείτε ότι οι εξισώσεις σας θα εξαφανιστούν ή θα μετατραπούν σε ακατανόητο χαοτικό κείμενο; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν προσπαθούν να **μετατρέψουν word σε txt** για downstream επεξεργασία, ειδικά όταν το αρχείο προέλευσης περιέχει αντικείμενα Office Math.

Τα καλά νέα; Με μερικές γραμμές C# και τις σωστές επιλογές, μπορείτε όχι μόνο να **μετατρέψετε Word σε txt**, αλλά και να διατηρήσετε κάθε εξίσωση ως καθαρό LaTeX markup. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, θα εξηγήσουμε γιατί κάθε ρύθμιση είναι σημαντική και θα σας δείξουμε πώς να επαληθεύσετε το αποτέλεσμα.

Θα καλύψουμε:

* Εγκατάσταση της βιβλιοθήκης Aspose.Words for .NET  
* Φόρτωση ενός `.docx` που περιέχει μαθηματικές εξισώσεις  
* Διαμόρφωση του `TxtSaveOptions` ώστε το **how to export math** να γίνει μια συμβολοσειρά φιλική προς LaTeX  
* Αποθήκευση του αρχείου και έλεγχος του αποτελέσματος  

Στο τέλος, θα έχετε ένα επαναχρησιμοποιήσιμο snippet που σας επιτρέπει να **αποθηκεύσετε docx ως txt** διατηρώντας κάθε τύπο ως LaTeX—ιδανικό για επιστημονικές pipelines, static site generators, ή οποιαδήποτε ροή εργασίας που χρειάζεται plain‑text μαθηματικά.

---

## Προαπαιτήσεις

Πριν βουτήξουμε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)  
* Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε)  
* Το πακέτο NuGet **Aspose.Words for .NET** – εγκαταστήστε το με  

```bash
dotnet add package Aspose.Words
```

Δεν απαιτούνται πρόσθετοι μετατροπείς ή εξωτερικά εργαλεία· το Aspose.Words διαχειρίζεται το βαρέως φορτίου εσωτερικά.

---

## Βήμα 1: Εγκατάσταση και αναφορά στο Aspose.Words

Πρώτα, προσθέστε τη βιβλιοθήκη στο project σας. Αν χρησιμοποιείτε τη γραμμή εντολών, εκτελέστε την παραπάνω εντολή. Στο Visual Studio μπορείτε επίσης να κάνετε δεξί‑κλικ στο **Dependencies → Manage NuGet Packages** και να αναζητήσετε το *Aspose.Words*.

```csharp
// Add the namespace at the top of your file
using Aspose.Words;
using Aspose.Words.Saving;
```

> **Pro tip:** Χρησιμοποιήστε την πιο πρόσφατη σταθερή έκδοση (από τον Απρίλιο 2026 είναι η 24.10). Οι νεότερες εκδόσεις φέρνουν διορθώσεις σφαλμάτων για τη διαχείριση του OfficeMath, ώστε να αποφύγετε την ξαφνική έλλειψη συμβόλων.

---

## Βήμα 2: Φόρτωση του πηγαίου εγγράφου

Τώρα φορτώνουμε το `.docx` που περιέχει τις εξισώσεις που θέλετε να διατηρήσετε. Η κλάση `Document` αφαιρεί την πλήρη δομή του αρχείου Word, παρέχοντάς σας πρόσβαση σε κείμενο, εικόνες και αντικείμενα Office Math.

```csharp
// Step 2: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – make sure the document actually loaded
if (doc == null || doc.PageCount == 0)
{
    throw new InvalidOperationException("The document could not be loaded or is empty.");
}
```

Γιατί να το φορτώσουμε πρώτα; Το Aspose.Words αναλύει το αρχείο σε ένα μοντέλο αντικειμένων, επιτρέποντάς μας να ελέγξουμε ή να τροποποιήσουμε το περιεχόμενο πριν αποφασίσουμε πώς θα το εξάγουμε. Εδώ οι αποφάσεις για το **how to export math** αρχίζουν να έχουν σημασία.

---

## Βήμα 3: Διαμόρφωση του TxtSaveOptions για εξαγωγή σε LaTeX

Η καρδιά της λύσης είναι η κλάση `TxtSaveOptions`. Από προεπιλογή, η αποθήκευση σε TXT αφαιρεί εντελώς το Office Math. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX` λέει στη βιβλιοθήκη να μεταφράσει κάθε εξίσωση στην LaTeX αναπαράστασή της.

```csharp
// Step 3: Create TxtSaveOptions and set the OfficeMath export mode to LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This makes every OfficeMath object become LaTeX code in the output file
    OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,

    // Optional: preserve line breaks as they appear in Word
    PreserveTableLayout = true,

    // Optional: ensure UTF‑8 encoding so special symbols survive
    Encoding = System.Text.Encoding.UTF8
};
```

**Γιατί LaTeX;** Η LaTeX είναι η lingua franca της επιστημονικής δημοσίευσης. Εξάγοντας τα μαθηματικά με αυτόν τον τρόπο, διατηρείτε τη σημασιολογία της εξίσωσης αντί για μια επίπεδη εικόνα ή μια ακατάληπτη συμβολοσειρά. Αν αργότερα τροφοδοτήσετε το TXT σε έναν επεξεργαστή Markdown που υποστηρίζει MathJax, οι εξισώσεις θα αποδοθούν τέλεια.

---

## Βήμα 4: Αποθήκευση του εγγράφου ως plain‑text

Με τις επιλογές διαμορφωμένες, το τελευταίο βήμα είναι μια εντολή μίας γραμμής που γράφει το αρχείο στο δίσκο.

```csharp
// Step 4: Save the document as plain‑text using the configured options
doc.Save("YOUR_DIRECTORY/MathSample.txt", txtOptions);
```

Αυτό είναι—το `.docx` σας είναι τώρα ένα αρχείο `.txt` όπου κάθε εξίσωση εμφανίζεται ως ένα απόσπασμα LaTeX, έτοιμο για downstream κατανάλωση.

---

## Επαλήθευση του αποτελέσματος (Πώς να αποθηκεύσετε σωστά txt)

Ανοίξτε το `MathSample.txt` σε οποιονδήποτε επεξεργαστή κειμένου. Θα πρέπει να δείτε κάτι όπως:

```
This is a sample paragraph.

Here is an equation in LaTeX:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]

Another line of regular text.
```

Αν εντοπίσετε ακατέργαστους χαρακτήρες ειδικούς του Word (π.χ., `?` ή ελλιπή σύμβολα), ελέγξτε ξανά ότι:

* Χρησιμοποιείτε μια πρόσφατη έκδοση του Aspose.Words (παλαιότερες εκδόσεις είχαν σφάλματα με το OfficeMath).  
* Το πηγαίο έγγραφο περιέχει πραγματικά αντικείμενα **OfficeMath**—όχι αντικείμενα του παλαιού Equation Editor. Για τα τελευταία, ίσως χρειαστεί να τα μετατρέψετε χειροκίνητα ή να χρησιμοποιήσετε τη μέθοδο `ConvertMathToOfficeMath` πριν από την αποθήκευση.

---

## Συνηθισμένες Παραλλαγές & Ακραίες Περιπτώσεις

| Situation | What to do |
|-----------|------------|
| **Legacy Equation Editor** αντικείμενα | Καλέστε `doc.ConvertMathToOfficeMath()` πριν από το βήμα 3. |
| **Χρειάζεστε plain Unicode math, όχι LaTeX** | Ορίστε `OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.Ununicode`. |
| **Μεγάλα έγγραφα (100 + MB)** | Χρησιμοποιήστε streaming στην αποθήκευση με `doc.Save(Stream, txtOptions)` για να αποφύγετε υψηλή χρήση μνήμης. |
| **Θέλετε να διατηρήσετε το αρχικό όνομα αρχείου** | Χρησιμοποιήστε `Path.GetFileNameWithoutExtension(inputPath) + ".txt"` κατά την κατασκευή της διαδρομής εξόδου. |

Αυτές οι προσαρμογές απαντούν στην ερώτηση “**how to export math**” για διαφορετικές pipelines, διασφαλίζοντας ότι η λύση σας είναι ανθεκτική ανεξάρτητα από την πηγή.

---

## Πλήρες Παράδειγμα Εργασίας (Όλα τα βήματα σε ένα μέρος)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Install Aspose.Words via NuGet before running this code.

        // 2️⃣ Load the .docx containing equations
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // Optional: Convert legacy equations to OfficeMath (covers edge cases)
        doc.ConvertMathToOfficeMath();

        // 3️⃣ Set up TXT save options – LaTeX export for math
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true,
            Encoding = System.Text.Encoding.UTF8
        };

        // 4️⃣ Define output path and save
        string outputPath = Path.Combine(
            Path.GetDirectoryName(inputPath),
            Path.GetFileNameWithoutExtension(inputPath) + ".txt");

        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"✅ Successfully saved '{outputPath}'.");
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο `.txt`, και θα δείτε τις LaTeX εξισώσεις ενσωματωμένες ακριβώς εκεί που ανήκαν. Αυτός είναι ο πιο απλός τρόπος να **convert

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}