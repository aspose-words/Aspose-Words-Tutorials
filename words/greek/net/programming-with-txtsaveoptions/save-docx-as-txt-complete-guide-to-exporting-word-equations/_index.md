---
category: general
date: 2026-03-27
description: Αποθηκεύστε το docx ως txt με το Aspose.Words και μετατρέψτε το Word
  σε LaTeX. Μάθετε πώς να εξάγετε εξισώσεις, να διατηρείτε απλό κείμενο και να λαμβάνετε
  σήμανση LaTeX σε λίγα λεπτά.
draft: false
keywords:
- save docx as txt
- convert word to latex
- how to export equations
- save word plain text
- export equations to latex
language: el
og_description: Αποθηκεύστε το docx ως txt χρησιμοποιώντας το Aspose.Words. Αυτός
  ο οδηγός δείχνει πώς να μετατρέψετε το Word σε LaTeX, να εξάγετε εξισώσεις και να
  διατηρήσετε το έγγραφό σας σε απλό κείμενο.
og_title: Αποθήκευση docx ως txt – Εξαγωγή εξισώσεων Word σε LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
- Document Conversion
title: Αποθήκευση docx ως txt – Πλήρης οδηγός για την εξαγωγή εξισώσεων Word σε LaTeX
url: /el/net/programming-with-txtsaveoptions/save-docx-as-txt-complete-guide-to-exporting-word-equations/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση docx ως txt – Εξαγωγή Εξισώσεων Word σε LaTeX

Κάποτε χρειάστηκε να **αποθηκεύσετε docx ως txt** αλλά ανησυχείτε ότι θα χάσετε τα εκλεπτυσμένα μαθηματικά που κρύβονται μέσα στο αρχείο Word; Δεν είστε μόνοι. Σε πολλές επιστημονικές ροές εργασίας η έκδοση απλού κειμένου ενός εγγράφου είναι απαραίτητη, όμως θέλετε οι εξισώσεις να παραμείνουν ως καθαρό markup LaTeX.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς διαδικασίες για **μετατροπή Word σε LaTeX** χρησιμοποιώντας το Aspose.Words for .NET, ώστε οι εξισώσεις σας να εξαχθούν σωστά ενώ το υπόλοιπο του εγγράφου να γίνει τακτικό απλό κείμενο. Στο τέλος θα ξέρετε πώς να **εξάγετε εξισώσεις σε LaTeX**, να διατηρήσετε το υπόλοιπο αρχείο ως απλό κείμενο, και να αποφύγετε τις συνήθεις παγίδες που συναντούν οι αρχάριοι.

## Τι Θα Μάθετε

- Πώς να φορτώσετε ένα αρχείο *.docx* που περιέχει Office Math.  
- Πώς να ορίσετε τις σωστές `TxtSaveOptions` ώστε το Aspose να εξάγει LaTeX για κάθε εξίσωση.  
- Πώς να αποθηκεύσετε το αποτέλεσμα ως **απλό κείμενο Word** αρχείο που μπορείτε να τροφοδοτήσετε σε σύστημα ελέγχου εκδόσεων, CI pipelines ή οποιοδήποτε downstream εργαλείο.  
- Κοινές ακραίες περιπτώσεις — τι να κάνετε όταν ένα έγγραφο συνδυάζει εικόνες και εξισώσεις, ή όταν χρειάζεστε διατήρηση χαρακτήρων Unicode.  
- Ένα πλήρες, έτοιμο‑για‑εκτέλεση δείγμα κώδικα που μπορείτε να ενσωματώσετε σε μια console εφαρμογή.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+).  
- Ένα αδειοδοτημένο αντίγραφο του **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για δοκιμές).  
- Visual Studio 2022 ή οποιοδήποτε IDE που μπορεί να μεταγλωττίσει έργα C#.  
- Ένα έγγραφο Word (`input.docx`) που ήδη περιέχει κάποια αντικείμενα Office Math.

> **Pro tip:** Αν δεν έχετε ακόμη άδεια, μπορείτε να ζητήσετε ένα προσωρινό κλειδί από την ιστοσελίδα της Aspose — απλώς αντικαταστήστε το placeholder στον κώδικα με το κλειδί σας πριν το τρέξετε.

## Βήμα 1 – Εγκατάσταση Aspose.Words μέσω NuGet

Πρώτο πράγμα: χρειάζεστε τη βιβλιοθήκη στο έργο σας. Ανοίξτε το **Package Manager Console** και εκτελέστε:

```powershell
Install-Package Aspose.Words
```

Αυτή η μοναδική γραμμή φέρνει όλα όσα χρειάζεστε, συμπεριλαμβανομένου του namespace `Saving` όπου βρίσκεται η `TxtSaveOptions`. Χωρίς επιπλέον DLLs, χωρίς εγγενείς εξαρτήσεις — απλώς καθαρός managed κώδικας.

## Βήμα 2 – Φόρτωση του Πηγαίου Εγγράφου Word

Τώρα διαβάζουμε το αρχείο που περιέχει τις εξισώσεις. Η κλάση `Document` αφαιρεί την πλήρη δομή *.docx*, ώστε να το αντιμετωπίζετε σαν ένα υψηλού επιπέδου αντικείμενο μοντέλου.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// If you have a license file, load it here
// var license = new License();
// license.SetLicense("Aspose.Words.lic");

// Step 2: Load the source Word document that contains equations
Document document = new Document(@"C:\MyProjects\Docs\input.docx");

// Quick sanity check – make sure the document actually has Office Math
if (document.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
{
    Console.WriteLine("Warning: No equations found. The output will be plain text only.");
}
```

**Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου νωρίς σας επιτρέπει να ελέγξετε το δέντρο κόμβων του. Αν παραλείψετε τον έλεγχο και το αρχείο δεν έχει εξισώσεις, θα πάρετε ένα καθαρό txt αρχείο — αλλά δεν θα ξέρετε γιατί η έξοδος LaTeX είναι κενή.

## Βήμα 3 – Διαμόρφωση TxtSaveOptions για Εξαγωγή LaTeX

Το Aspose σας δίνει λεπτομερή έλεγχο του τρόπου απόδοσης του Office Math. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX`, κάθε εξίσωση μετατρέπεται στην ισοδύναμη LaTeX αντί να αφαιρεθεί ή να μετατραπεί σε εικόνα.

```csharp
// Step 3: Create text save options and set Office Math export mode to LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This tells Aspose to emit LaTeX markup for each equation
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: preserve Unicode characters (useful for symbols like α, β, etc.)
    Encoding = Encoding.UTF8,

    // Optional: add a line break after each paragraph for readability
    AddBidiMarks = false
};
```

**Γιατί είναι σημαντικό:** Η προεπιλεγμένη λειτουργία εξαγωγής θα έριχνε τις εξισώσεις εντελώς. Η αλλαγή σε `LaTeX` διατηρεί την μαθηματική πρόθεση, κάτι που χρειάζεστε όταν αργότερα τροφοδοτείτε το αρχείο σε έναν LaTeX compiler ή σε έναν markdown επεξεργαστή που καταλαβαίνει τη σύνταξη `$…$`.

## Βήμα 4 – Αποθήκευση του Εγγράφου ως Απλό Κείμενο

Με τις επιλογές ρυθμισμένες, η αποθήκευση του αρχείου γίνεται με μια γραμμή κώδικα. Η έξοδος θα είναι ένα αρχείο `.txt` όπου κάθε εξίσωση εμφανίζεται ως κώδικας LaTeX περικλεισμένος σε οριοθέτες `$` (μπορείτε να το αλλάξετε αργότερα αν προτιμάτε μπλοκ `\[` … `\]`).

```csharp
// Step 4: Save the document as a plain‑text file; equations are exported as LaTeX markup
string outputPath = @"C:\MyProjects\Docs\output.txt";
document.Save(outputPath, txtSaveOptions);

Console.WriteLine($"Success! The file has been saved to {outputPath}");
```

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `output.txt` σε οποιονδήποτε επεξεργαστή και θα δείτε κάτι σαν:

```
This is a sample paragraph with an equation.

$E = mc^2$

Another paragraph follows the equation.

$ \int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2} $
```

Παρατηρήστε πώς το κανονικό κείμενο παραμένει ακριβώς όπως ήταν, ενώ οι εξισώσεις έχουν μετατραπεί σε καθαρές συμβολοσειρές LaTeX. Μπορείτε να τις αντιγράψετε‑και‑επικολλήσετε απευθείας σε ένα LaTeX έγγραφο, σε ένα Jupyter notebook ή σε οποιοδήποτε εργαλείο που αποδίδει μαθηματικά.

## Βήμα 5 – Διαχείριση Ακραίων Περιπτώσεων

### Μικτό Περιεχόμενο (Εικόνες + Εξισώσεις)

Αν το αρχείο Word περιέχει επίσης εικόνες, το Aspose θα τις αγνοήσει όταν χρησιμοποιείτε `TxtSaveOptions`. Αυτό είναι συνήθως αποδεκτό για μια ροή **απλού κειμένου Word**, αλλά αν χρειάζεστε τις εικόνες ως placeholders μπορείτε:

1. Εξάγετε το έγγραφο πρώτα σε HTML (`HtmlSaveOptions`) για να συλλάβετε τις εικόνες ως ετικέτες `<img>`.  
2. Εκτελέστε δεύτερο πέρασμα με `TxtSaveOptions` για να πάρετε τις εξισώσεις σε LaTeX.  
3. Συγχωνεύστε τα δύο αποτελέσματα χειροκίνητα ή με ένα μικρό script.

### Σύμβολα Unicode

Κάποιες εξισώσεις χρησιμοποιούν ειδικούς χαρακτήρες Unicode (π.χ. ελληνικά γράμματα). Ορίζοντας `Encoding = Encoding.UTF8` στις `TxtSaveOptions` (όπως φαίνεται στο Βήμα 3) διασφαλίζει ότι αυτά τα σύμβολα παραμένουν μετά τη μετατροπή.

### Μεγάλα Έγγραφα

Για τεράστια αρχεία (> 100 MB), σκεφτείτε τη ροή αποθήκευσης:

```csharp
using (FileStream fs = new FileStream(outputPath, FileMode.Create, FileAccess.Write))
{
    document.Save(fs, txtSaveOptions);
}
```

Η ροή αποφεύγει τη φόρτωση ολόκληρης της εξόδου στη μνήμη, κάτι που μπορεί να σώσει τη ζωή σας σε agents με περιορισμένη μνήμη.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω είναι το πλήρες, έτοιμο‑για‑αντιγραφή πρόγραμμα που ενώνει όλα τα παραπάνω. Απλώς αντικαταστήστε τις διαδρομές αρχείων και, αν έχετε, τη γραμμή άδειας.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load your Aspose.Words license here
        // -------------------------------------------------
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Load the source document
        // -------------------------------------------------
        string inputPath = @"C:\MyProjects\Docs\input.docx";
        Document doc = new Document(inputPath);

        // -------------------------------------------------
        // Step 2: Verify that the document contains equations
        // -------------------------------------------------
        int equationCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
        if (equationCount == 0)
        {
            Console.WriteLine("No Office Math found – the output will be plain text only.");
        }

        // -------------------------------------------------
        // Step 3: Configure TxtSaveOptions for LaTeX export
        // -------------------------------------------------
        TxtSaveOptions options = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            Encoding = Encoding.UTF8,
            AddBidiMarks = false
        };

        // -------------------------------------------------
        // Step 4: Save as .txt (plain text + LaTeX equations)
        // -------------------------------------------------
        string outputPath = @"C:\MyProjects\Docs\output.txt";
        doc.Save(outputPath, options);

        Console.WriteLine($"File saved successfully to: {outputPath}");
    }
}
```

Τρέξτε το πρόγραμμα (`dotnet run` αν χρησιμοποιείτε console project) και ελέγξτε το `output.txt`. Μόλις **αποθηκεύσατε docx ως txt** διατηρώντας κάθε εξίσωση ως LaTeX — χωρίς χειροκίνητη αντιγραφή‑επικόλληση.

## Συχνές Ερωτήσεις

**Ε: Μπορώ να αλλάξω τον οριοθέτη από `$…$` σε `\(...\)`;**  
Α: Ναι. Μετά την αποθήκευση, εκτελέστε μια απλή αντικατάσταση στο αρχείο: `output = output.Replace("$", @"\(").Replace("$", @"\)");` — προσοχή όμως να μην αντικαταστήσετε τα ενσωματωμένα `$` που ανήκουν στο αρχικό κείμενο.

**Ε: Λειτουργεί αυτό με αρχεία Word 2007‑2019;**  
Α: Απόλυτα. Το Aspose.Words υποστηρίζει `.doc`, `.docx`, `.docm` και ακόμη και την πιο πρόσφατη οικογένεια `.dotx`. Ο ίδιος κώδικας λειτουργεί σε όλες τις εκδόσεις.

**Ε: Τι κάνω αν θέλω να διατηρήσω την αρχική μορφοποίηση παραγράφων (tabs, πολλαπλά κενά);**  
Α: Ορίστε `txtSaveOptions.PreserveTableLayout = true;` και `txtSaveOptions.PreserveSpace = true;` για να διατηρηθούν τα κενά.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **αποθηκεύσετε docx ως txt** ενώ **εξάγετε εξισώσεις σε LaTeX** χρησιμοποιώντας το Aspose.Words. Τα βασικά βήματα είναι η φόρτωση του εγγράφου, η διαμόρφωση των `TxtSaveOptions` με `OfficeMathExportMode.LaTeX`, και η αποθήκευση του αποτελέσματος. Με αυτές τις τρεις γραμμές κώδικα μπορείτε αξιόπιστα να **μετατρέψετε word σε latex**, να διατηρήσετε το έγγραφό σας ως **απλό κείμενο Word**, και να αποφύγετε την απώλεια μαθηματικών συμβόλων.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να συνδυάσετε αυτή τη ροή με έναν markdown generator για να παραγάγετε ένα πλήρες αρχείο `.md` που περιλαμβάνει τόσο κείμενο όσο και LaTeX — τέλεια για τεκμηρίωση με Git ή static‑site generators. Ή εξερευνήστε τα `PdfSaveOptions` του Aspose για να αποκτήσετε μια έκδοση PDF παράλληλα με το απλό κείμενο.

Αν αντιμετωπίσετε δυσκολίες, αφήστε ένα σχόλιο παρακάτω. Καλό coding, και απολαύστε την απλότητα της μετατροπής εξισώσεων Word σε καθαρό LaTeX! 

![Εικονογράφηση αποθήκευσης DOCX ως TXT με εξισώσεις LaTeX](placeholder-image.png "παράδειγμα αποθήκευσης docx ως txt")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}