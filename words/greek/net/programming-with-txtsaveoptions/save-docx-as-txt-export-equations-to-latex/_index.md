---
category: general
date: 2026-03-13
description: Αποθηκεύστε το docx ως txt γρήγορα με C#. Μάθετε πώς να μετατρέπετε εξισώσεις
  σε LaTeX ενώ αποθηκεύετε το απλό κείμενο του Word σε ένα καθαρό βήμα.
draft: false
keywords:
- save docx as txt
- convert equations to latex
- convert docx to txt
- how to save text
- save word plain text
language: el
og_description: Αποθηκεύστε το docx ως txt άμεσα και μετατρέψτε τις εξισώσεις σε LaTeX.
  Ακολουθήστε αυτόν τον πλήρη οδηγό C# για εξαγωγή Word σε απλό κείμενο.
og_title: Αποθήκευση docx ως txt – Εξαγωγή εξισώσεων σε LaTeX
tags:
- C#
- Aspose.Words
- DocumentConversion
title: Αποθήκευση docx ως txt – Εξαγωγή εξισώσεων σε LaTeX
url: /el/net/programming-with-txtsaveoptions/save-docx-as-txt-export-equations-to-latex/
---

quote with > **Τι θα λάβετε:** ... Good.

Now produce final output with all content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save docx as txt – Export equations to LaTeX

Έχετε ποτέ χρειαστεί να **save docx as txt** αλλά να ανησυχείτε ότι τα μαθηματικά μέσα θα μετατραπούν σε ακατανόητο κείμενο; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν προσπαθούν να εξάγουν απλό κείμενο από αρχεία Word που περιέχουν αντικείμενα Office Math. Τα καλά νέα; Με λίγες γραμμές C# και τις σωστές επιλογές, μπορείτε να **convert equations to LaTeX** ενώ το υπόλοιπο του εγγράφου γίνεται απλό κείμενο.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία—χωρίς ασαφείς αναφορές, μόνο ένα συγκεκριμένο, εκτελέσιμο παράδειγμα. Στο τέλος θα γνωρίζετε ακριβώς **how to save text** από ένα αρχείο `.docx`, θα διατηρήσετε τις εξισώσεις σας αναγνώσιμες, και θα αποφύγετε τα συνηθισμένα προβλήματα που μετατρέπουν το αποτέλεσμα σε μια ακαταλαβίστικη μάζα συμβόλων.

> **Τι θα λάβετε:** ένα πλήρες δείγμα κώδικα, εξήγηση κάθε ρύθμισης, συμβουλές για ειδικές περιπτώσεις, και ένα γρήγορο βήμα επαλήθευσης ώστε να είστε σίγουροι ότι η μετατροπή λειτούργησε.

---

## Προαπαιτούμενα

* **.NET 6** (ή οποιοδήποτε πρόσφατο .NET runtime) εγκατεστημένο.
* Το πακέτο NuGet **Aspose.Words for .NET** – περιλαμβάνει την κλάση `Document` και το `TxtSaveOptions` που θα χρειαστούμε.
* Ένα αρχείο Word (`.docx`) που περιέχει τουλάχιστον μία εξίσωση Office Math. Αν δεν έχετε, δημιουργήστε ένα απλό έγγραφο με εξίσωση μέσω **Insert → Equation** στο Microsoft Word.

Αυτό είναι—χωρίς επιπλέον βιβλιοθήκες, χωρίς βαριές μετατροπείς PDF. Μόνο απλό C# και Aspose.Words.

---

## Βήμα 1 – Φόρτωση του εγγράφου Word

Πρώτα απ' όλα: χρειαζόμαστε μια παρουσία `Document` που να δείχνει στο πηγαίο `.docx`. Ο κατασκευαστής αναμένει μια διαδρομή αρχείου, οπότε αντικαταστήστε το placeholder με την πραγματική σας θέση.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX file
Document doc = new Document(@"C:\Docs\input.docx");
```

*Γιατί είναι σημαντικό:* Η φόρτωση του αρχείου μας δίνει πρόσβαση σε κάθε κόμβο μέσα στη δομή του Word, συμπεριλαμβανομένων των κρυφών αντικειμένων Office Math που οι περισσότεροι εξαγωγείς απλού κειμένου απλώς παραλείπουν.

---

## Βήμα 2 – Ενημερώστε το Aspose ότι θέλετε LaTeX για τις εξισώσεις

Η μαγεία συμβαίνει στο `TxtSaveOptions`. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX`, η βιβλιοθήκη μετατρέπει κάθε εξίσωση στην αναπαράστασή της σε LaTeX αντί να αποβάλλει το ακατέργαστο MathML ή να το αφαιρεί εντελώς.

```csharp
// Configure export options: equations become LaTeX strings
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Optional: preserve line breaks as they appear in Word
    PreserveTableLayout = true
};
```

*Γιατί είναι σημαντικό:* Χωρίς αυτή τη σημαία, το αποτέλεσμα σας είτε θα χάσει εντελώς τις εξισώσεις είτε θα περιέχει μη αναγνώσιμο XML. Το LaTeX είναι ελαφρύ, ευρέως υποστηριζόμενο και ιδανικό για επεξεργασία σε επόμενα στάδια (π.χ., τροφοδοσία σε renderer Markdown).

---

## Βήμα 3 – Αποθήκευση του εγγράφου ως απλό κείμενο

Τώρα συνδυάζουμε το έγγραφο και τις επιλογές, και γράφουμε το αποτέλεσμα σε ένα αρχείο `.txt`. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική· το Aspose θα διαχειριστεί την κωδικοποίηση αυτόματα (UTF‑8 εξ ορισμού).

```csharp
// Export the document to a plain‑text file with LaTeX equations
doc.Save(@"C:\Docs\Equations.txt", txtOptions);
```

Όταν ανοίξετε το `Equations.txt`, θα δείτε κανονικές προτάσεις αναμεμειγμένες με αποσπάσματα LaTeX όπως `\int_{a}^{b} f(x)\,dx`. Αυτό ολοκληρώνει το βήμα **convert docx to txt**.

---

## Βήμα 4 – Επαλήθευση του αποτελέσματος (προαιρετικό αλλά συνιστάται)

Μια γρήγορη έλεγχος λογικής σας εξοικονομεί ώρες εντοπισμού σφαλμάτων αργότερα. Ανοίξτε το παραγόμενο αρχείο σε οποιονδήποτε επεξεργαστή κειμένου και ψάξτε για δύο πράγματα:

1. **Plain sentences** – πρέπει να ταιριάζουν με τις αρχικές παραγράφους του Word.
2. **LaTeX blocks** – κάθε εξίσωση πρέπει να ξεκινά με ανάστροφη κάθετο (`\`) και να φαίνεται ως έγκυρος κώδικας LaTeX.

```csharp
string output = File.ReadAllText(@"C:\Docs\Equations.txt");
Console.WriteLine(output.Substring(0, 500)); // preview first 500 chars
```

Αν η προεπισκόπηση περιλαμβάνει κάτι όπως `\frac{a}{b}` όπου περιμένατε μια εξίσωση, έχετε πετύχει.

---

## Συνηθισμένες Παραλλαγές & Ακραίες Περιπτώσεις

### Μετατροπή πολλαπλών αρχείων σε παρτίδα

Αν χρειάζεται να **convert docx to txt** για ολόκληρο φάκελο, τυλίξτε τη λογική σε βρόχο `foreach`. Θυμηθείτε να επαναχρησιμοποιήσετε το `TxtSaveOptions` για να αποφύγετε περιττές εκχωρήσεις.

```csharp
TxtSaveOptions batchOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};

foreach (string file in Directory.GetFiles(@"C:\Docs\Batch", "*.docx"))
{
    Document batchDoc = new Document(file);
    string txtPath = Path.ChangeExtension(file, ".txt");
    batchDoc.Save(txtPath, batchOptions);
}
```

### Διαχείριση μη‑λατινικών χαρακτήρων

Το Aspose προεπιλογή είναι UTF‑8, που καλύπτει τις περισσότερες γραφές. Αν στοχεύετε σε παλαιότερο σύστημα που αναμένει ANSI, ορίστε την κωδικοποίηση ρητά:

```csharp
txtOptions.Encoding = Encoding.GetEncoding("windows-1252");
```

### Όταν οι εξισώσεις είναι εικόνες, όχι Office Math

Αν το πηγαίο έγγραφο χρησιμοποιεί εξισώσεις με βάση εικόνες, το Aspose δεν μπορεί να τις μετατρέψει σε LaTeX (δεν υπάρχει τίποτα προς ανάλυση). Σε αυτή την περίπτωση θα λάβετε κείμενο placeholder όπως `[Equation]`. Σκεφτείτε να χρησιμοποιήσετε βιβλιοθήκη OCR ή να αντικαταστήσετε χειροκίνητα αυτές τις εικόνες.

---

## Επαγγελματικές Συμβουλές & Προειδοποιήσεις

* **Pro tip:** Ενεργοποιήστε το `PreserveTableLayout` (όπως φαίνεται στο Βήμα 2) αν το έγγραφό σας βασίζεται σε πίνακες για διάταξη. Διατηρεί το διάστημα των στηλών περίπου αμετάβλητο στην έξοδο απλού κειμένου.
* **Watch out for hidden sections:** Το Word μπορεί να αποθηκεύει κείμενο σε κεφαλίδες, υποσέλιδα ή ακόμη και σχόλια. Το `TxtSaveOptions` εξάγει αυτά εξ ορισμού, αλλά μπορείτε να τα απενεργοποιήσετε με `ExportHeadersFooters = false` αν χρειάζεστε μόνο το κυρίως περιεχόμενο.
* **Performance tip:** Για τεράστια έγγραφα (εκατοντάδες σελίδες), επαναχρησιμοποιήστε την ίδια παρουσία `TxtSaveOptions` και σκεφτείτε τη ροή εξόδου με `doc.Save(Stream, txtOptions)` για να μειώσετε την πίεση μνήμης.

![Save docx as txt example showing LaTeX output](/images/save-docx-as-txt.png "save docx as txt example")

*Alt text:* **save docx as txt example** – στιγμιότυπο του παραγόμενου αρχείου απλού κειμένου με εξισώσεις LaTeX.

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να ενσωματώσετε σε μια εφαρμογή κονσόλας. Περιλαμβάνει όλες τις δηλώσεις `using`, διαχείριση σφαλμάτων και σχόλια ώστε να μην χαθείτε.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Path to the source DOCX – change to your file location
        string sourcePath = @"C:\Docs\input.docx";

        // Path for the resulting TXT file
        string outputPath = @"C:\Docs\Equations.txt";

        try
        {
            // 1️⃣ Load the Word document
            Document doc = new Document(sourcePath);

            // 2️⃣ Configure export: equations become LaTeX
            TxtSaveOptions options = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true,
                // Optional: keep headers/footers out of the output
                // ExportHeadersFooters = false
            };

            // 3️⃣ Save as plain text
            doc.Save(outputPath, options);

            // 4️⃣ Quick verification
            Console.WriteLine("✅ Conversion finished!");
            Console.WriteLine("First 300 characters of the result:");
            Console.WriteLine(File.ReadAllText(outputPath).Substring(0, 300));
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Oops! Something went wrong: {ex.Message}");
        }
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το `Equations.txt`, και θα δείτε το περιεχόμενο του Word μαζί με μαθηματικά μορφοποιημένα σε LaTeX. Αυτό είναι ολόκληρη η ροή εργασίας **how to save text** σε ένα τακτοποιημένο script.

---

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **save docx as txt** διατηρώντας τις εξισώσεις σε LaTeX. Από τη φόρτωση του εγγράφου, τη ρύθμιση του `TxtSaveOptions`, μέχρι την αποθήκευση και επαλήθευση του αποτελέσματος, κάθε βήμα εξηγήθηκε με το «γιατί» πίσω από αυτό. Τώρα έχετε ένα αξιόπιστο πρότυπο για **convert equations to latex**, μια σταθερή βάση για **convert docx to txt** σε εργασίες παρτίδας, και μια σειρά από συμβουλές για να αποφύγετε κοινά προβλήματα.

Τι ακολουθεί; Δοκιμάστε να στείλετε το παραγόμενο `.txt` σε έναν επεξεργαστή Markdown που καταλαβαίνει LaTeX, ή να τροφοδοτήσετε τα αποσπάσματα LaTeX σε μια επιστημονική αλυσίδα δημοσίευσης. Μπορείτε επίσης να πειραματιστείτε με άλλες μορφές εξαγωγής (HTML, PDF) χρησιμοποιώντας παρόμοια αντικείμενα επιλογών—το Aspose το κάνει εύκολο.

Αν αντιμετωπίσατε προβλήματα, αφήστε ένα σχόλιο παρακάτω. Καλή προγραμματιστική, και απολαύστε την απλότητα του να μετατρέπετε το Word σε καθαρό, αναζητήσιμο απλό κείμενο!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}